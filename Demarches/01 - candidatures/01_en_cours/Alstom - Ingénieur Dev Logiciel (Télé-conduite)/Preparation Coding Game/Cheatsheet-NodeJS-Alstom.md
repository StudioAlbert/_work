# Cheatsheet Node.js (+ fondamentaux JavaScript) — Test technique Alstom

> **Enjeu : limiter la casse.** Point dur assumé — objectif : capter les questions de **concept** (event loop, async, npm) qui font la majorité des QCM Node. Les fondamentaux JS ci-dessous servent aussi la fiche [[Cheatsheet-React-Alstom]].
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 1. Fondamentaux JavaScript — socle commun Node/React

- **`var` / `let` / `const`** : `var` = portée **fonction** + hoisting (déclaré remonté, valeur `undefined`) ; `let`/`const` = portée **bloc**, zone morte temporelle (`ReferenceError` avant déclaration). `const` fige la **liaison**, pas l'objet (`const a = []; a.push(1)` est légal — analogue à un pointeur const C++).
- **`==` vs `===`** : `==` convertit les types (`'1' == 1` → true, `null == undefined` → true) ; **toujours `===`** en pratique. QCM adoré : `[] == false` → true.
- **Falsy** : `0`, `''`, `null`, `undefined`, `NaN`, `false`. `NaN === NaN` → **false** (utiliser `Number.isNaN`).
- **`this`** : dépend de **l'appel**, pas de la définition (fonction classique) ; les **fonctions fléchées** n'ont pas de `this` propre — elles capturent celui du contexte englobant. Piège n°1 du JS.
- **Closures** : une fonction capture les variables de son scope de définition — même mécanisme de piège que Python (boucle + callbacks : `var` dans un `for` → toutes les callbacks voient la dernière valeur ; `let` corrige).
- Tableaux : `map`, `filter`, `reduce`, `find`, `some/every`, `forEach` (ne retourne rien), spread `[...a, ...b]`, destructuring `const {x, y} = obj`.
- Template literals : `` `latence: ${ms} ms` ``.
- `JSON.parse` / `JSON.stringify`.

## 2. Le modèle d'exécution Node — question de cours n°1

- Node exécute le JS sur **un seul thread**, avec une **event loop** (libuv) ; l'I/O est **non bloquante** : les opérations longues (fichiers, réseau) sont déléguées, la callback revient plus tard.
- Conséquence : **ne jamais bloquer l'event loop** (boucle de calcul lourd = tout le serveur gèle). Calcul lourd → `worker_threads` ou processus séparé.
- Analogie utile pour toi : c'est une **boucle de jeu** mono-thread avec callbacks — même discipline que « ne pas bloquer la frame ».

### Micro/macro-tâches — LE piège QCM classique
```js
console.log('A');
setTimeout(() => console.log('B'), 0);   // macrotâche
Promise.resolve().then(() => console.log('C')); // microtâche
console.log('D');
// Sortie : A, D, C, B  — les microtâches (promesses) passent AVANT les timers
```

## 3. Asynchrone : callbacks → promesses → async/await

```js
// Promesse
fetch(url)
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// async/await (équivalent)
async function load() {
  try {
    const res = await fetch(url);
    const data = await res.json();
  } catch (err) { /* rejet capturé ici */ }
}
```
- Une fonction `async` retourne **toujours une promesse**.
- `await` suspend la fonction, **pas** le thread.
- États d'une promesse : *pending* → *fulfilled* ou *rejected* (définitif).
- `Promise.all([...])` : tout en parallèle, rejette dès le **premier échec** ; `Promise.allSettled` attend tout ; `Promise.race` : le premier réglé gagne.
- Piège : oublier `await` → on manipule une promesse, pas la valeur (`[object Promise]`).
- Convention callback Node : `(err, data) => {}` — l'erreur **en premier**.

## 4. Modules & npm

- **CommonJS** (historique Node) : `const fs = require('fs')` / `module.exports = {...}`.
- **ESM** (standard) : `import fs from 'fs'` / `export default` — activé par `"type": "module"` dans `package.json` ou extension `.mjs`. Savoir reconnaître les deux syntaxes suffit pour un QCM.
- **`package.json`** : métadonnées + `dependencies` (prod) vs `devDependencies` (outillage : tests, lint) + `scripts` (`npm run build`, `npm start`, `npm test`).
- **Semver `"^4.2.1"`** : `^` accepte les mises à jour **mineures/patch** (<5.0.0) ; `~4.2.1` : patch seulement (<4.3.0). Piège QCM récurrent.
- **`package-lock.json`** : fige l'arbre exact des versions → installations reproductibles (à committer). `npm ci` : installation stricte depuis le lock (CI).
- `node_modules` : jamais versionné (`.gitignore`).
- `npx` : exécute un binaire de paquet sans installation globale.

## 5. API Node à reconnaître

```js
const fs = require('fs');
fs.readFileSync('a.txt', 'utf8');          // BLOQUANT (sync)
fs.readFile('a.txt', 'utf8', (err, d) => {}); // non bloquant
const fsp = require('fs/promises');        // await fsp.readFile(...)
```
- Piège : les variantes `*Sync` **bloquent l'event loop** — à éviter dans un serveur.
- `process.env.PORT` (variables d'environnement — comme dans tes conteneurs Docker), `process.argv`, `__dirname` (CommonJS uniquement).
- `EventEmitter` : `on('event', cb)` / `emit('event', data)` — **c'est un Event Bus**, ton pattern Unity quotidien.
- Modules courants : `path`, `http`, `os`, `crypto`.

## 6. Express — le minimum reconnaissable

```js
const express = require('express');
const app = express();
app.use(express.json());                   // middleware : parse le body JSON

app.get('/api/trains/:id', (req, res) => {
  res.json({ id: req.params.id });         // req.params / req.query / req.body
});

app.use((err, req, res, next) => res.status(500).send()); // middleware d'erreur : 4 args

app.listen(3000);
```
- **Middleware** = fonction `(req, res, next)` exécutée dans l'ordre de déclaration ; `next()` passe au suivant ; en oubliant `next()` sans répondre, la requête **pend**. Piège QCM.
- Codes HTTP à réciter : 200 OK · 201 Created · 301/302 redirections · 400 Bad Request · 401 Unauthorized · 403 Forbidden · 404 Not Found · 500 Internal Server Error.
- Verbes REST : GET (lire, idempotent) · POST (créer) · PUT (remplacer, idempotent) · PATCH (modifier partiellement) · DELETE.

## 7. Micro-drills (à refaire J5)

1. Prédire l'ordre `setTimeout(0)` vs `Promise.then` — réciter A, D, C, B.
2. `const a = [1]; a.push(2);` — légal ou non ? Pourquoi ?
3. `^1.4.2` accepte-t-il `1.5.0` ? `2.0.0` ? → oui / non.
4. Pourquoi `readFileSync` est-il dangereux dans un handler Express ?
5. `dependencies` vs `devDependencies` : où va `jest` ? où va `express` ?
