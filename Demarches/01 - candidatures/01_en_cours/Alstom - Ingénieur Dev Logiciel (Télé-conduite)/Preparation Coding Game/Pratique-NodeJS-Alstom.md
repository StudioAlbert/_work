# Pratique Node.js (+ JS core) — QCM & exercices (test Alstom)

> Complète [[Cheatsheet-NodeJS-Alstom]]. Le socle JS sert aussi à [[Pratique-React-Alstom]].
> Objectif assumé : **capter les questions de concept** (event loop, async, npm, `===`). ★ = plus retors. Corrigé QCM en bas.

---

## Partie A — QCM (20 questions)

**1.** `const a = [1]; a.push(2); console.log(a.length);`
- a) `1`  b) `2`  **c) `TypeError` (const)**  d) `undefined`

**2.** `console.log('1' == 1, '1' === 1);`
- a) `true true`  *b) `true false`*  c) `false false`  d) `false true`

**3.** ★ `console.log([] == false);`
- a) `false`  b) `true`  c) `TypeError`  d) `undefined`

**4.** `console.log(typeof NaN);`
- a) `"NaN"`  b) `"number"`  c) `"undefined"`  d) `"object"`

**5.** Laquelle est **truthy** ?
- a) `0`  b) `""`  c) `"0"`  d) `null`

**6.** ★ Ordre d'affichage ?
```js
console.log('A');
setTimeout(() => console.log('B'), 0);
Promise.resolve().then(() => console.log('C'));
console.log('D');
```
- a) `A B C D`  b) `A D C B`  c) `A D B C`  d) `A C D B`

**7.** À propos des **fonctions fléchées**, laquelle est VRAIE ?
- a) elles ont leur propre `this`
- b) elles n'ont pas de `this` propre (capturent celui du contexte englobant)
- c) elles ne peuvent pas prendre d'arguments
- d) elles retournent toujours `undefined`

**8.** `console.log([1, 2, 3].map(x => x * 2));`
- a) `[1, 2, 3]`  b) `[2, 4, 6]`  c) `6`  d) `[1, 4, 9]`

**9.** `console.log([1, 2, 3, 4].filter(x => x % 2 === 0));`
- a) `[1, 3]`  b) `[2, 4]`  c) `[1, 2, 3, 4]`  d) `2`

**10.** `console.log([1, 2, 3, 4].reduce((acc, x) => acc + x, 0));`
- a) `10`  b) `[1,2,3,4]`  c) `24`  d) `0`

**11.** Que retourne `arr.forEach(fn)` ?
- a) un nouveau tableau  b) `undefined`  c) le tableau  d) un booléen

**12.** Une fonction `async` retourne toujours…
- a) la valeur `return`  b) `undefined`  c) une **Promise**  d) un tableau

**13.** `Promise.all([p1, p2, p3])` **rejette**…
- a) jamais  b) si **toutes** rejettent  c) dès la **première** qui rejette  d) après un timeout

**14.** `const { x } = { x: 1, y: 2 }; console.log(x);`
- a) `1`  b) `{x:1}`  c) `undefined`  d) `2`

**15.** En semver, `"^1.4.2"` autorise l'installation de… (plusieurs vraies)
- a) `1.4.9`  b) `1.5.0`  c) `2.0.0`  d) `1.3.0`

**16.** Dans `package.json`, où placer **jest** (framework de test) ?
- a) `dependencies`  b) `devDependencies`  c) `scripts`  d) `peerDependencies`

**17.** Quelle syntaxe est du **CommonJS** (historique Node) ?
- a) `import fs from 'fs'`  b) `const fs = require('fs')`  c) `export default fs`  d) `using fs`

**18.** ★ Dans Express, un **middleware d'erreur** se reconnaît à…
- a) son nom `errorHandler`  b) ses **4 paramètres** `(err, req, res, next)`
- c) l'appel de `res.error()`  d) le décorateur `@error`

**19.** Pourquoi éviter `fs.readFileSync` dans un handler de serveur ?
- a) il n'existe pas  b) il **bloque l'event loop** (tout le serveur gèle)
- c) il est plus lent que `readFile` sur un seul fichier  d) il ne lit pas l'UTF-8

**20.** Le code HTTP **201** signifie…
- a) OK  b) Created  c) Not Found  d) Internal Server Error

---

## Partie B — Exercices de code (5)

### Ex. 1 — Total du stock
`totalInStock(produits)` : somme des `price` des produits dont `inStock === true`.
`[{price:10,inStock:true},{price:5,inStock:false},{price:3,inStock:true}]` → `13`.
*Indice : `filter` puis `reduce`.*

```js
function totalInStock(produits) {
  return produits
    .filter(p => p.inStock)
    .reduce((somme, p) => somme + p.price, 0);
}
```

### Ex. 2 — Compteur (closure)
`makeCounter()` retourne une fonction qui renvoie 1, 2, 3… à chaque appel.
*Indice : une variable capturée dans la closure.*

```js
function makeCounter() {
  let count = 0;
  return () => ++count;   // ++count : pré-incrément, renvoie la nouvelle valeur
}
// const next = makeCounter(); next(); // 1  next(); // 2
```

### Ex. 3 — `groupBy`
`groupBy(mots, m => m.length)` sur `["a","bb","cc","d"]` → `{1:["a","d"], 2:["bb","cc"]}`.
*Indice : `reduce` vers un objet ; initialise le tableau si absent.*

```js
function groupBy(arr, keyFn) {
  return arr.reduce((acc, item) => {
    const cle = keyFn(item);
    if (!acc[cle]) acc[cle] = [];
    acc[cle].push(item);
    return acc;
  }, {});
}
```

### Ex. 4 — Async / `Promise.all`
Écris `delay(ms, valeur)` (promesse résolue après `ms`) et une fonction `async` qui lance **deux** délais **en parallèle** et retourne le tableau des résultats.
*Indice : `new Promise(resolve => setTimeout(...))` ; `await Promise.all([...])`.*

```js
function delay(ms, valeur) {
  return new Promise(resolve => setTimeout(() => resolve(valeur), ms));
}
async function lancer() {
  const resultats = await Promise.all([delay(10, 'a'), delay(5, 'b')]);
  return resultats;   // ['a', 'b'] : l'ordre suit le tableau, pas la vitesse
}
```

### Ex. 5 — Route Express
Écris une route `GET /api/trains/:id` qui renvoie `{ id }` en JSON.
*Indice : `req.params.id`, `res.json(...)`.*

```js
const express = require('express');
const app = express();
app.use(express.json());

app.get('/api/trains/:id', (req, res) => {
  res.json({ id: req.params.id });
});

app.listen(3000, () => console.log('en écoute sur 3000'));
```

---

## Corrigé QCM

| Q | Rép | Explication express |
|---|---|---|
| 1 | **b** | `const` fige la **liaison**, pas le contenu : muter le tableau est légal → `length` = `2`. |
| 2 | **b** | `==` convertit (`'1'==1` → `true`) ; `===` compare type+valeur (`'1'===1` → `false`). |
| 3 | **b** | `[] == false` : coercion → `[]`→`""`→`0`, `false`→`0`, `0==0` → **`true`**. (Toujours `===`.) |
| 4 | **b** | `typeof NaN` = `"number"` (NaN est un nombre spécial). `NaN === NaN` = `false`. |
| 5 | **c** | `"0"` = chaîne non vide → truthy. `0`, `""`, `null` sont falsy. |
| 6 | **b** | Synchrone d'abord (`A`, `D`), puis **microtâches** (Promise → `C`), puis **macrotâches** (setTimeout → `B`) → `A D C B`. |
| 7 | **b** | La fléchée capture le `this` englobant (pas de `this` propre) — d'où son usage dans les callbacks. |
| 8 | **b** | `map` applique `x*2` → `[2, 4, 6]`. |
| 9 | **b** | `filter` garde les pairs → `[2, 4]`. |
| 10 | **a** | `reduce` additionne → `10`. |
| 11 | **b** | `forEach` ne retourne rien (`undefined`) ; pour transformer, utiliser `map`. |
| 12 | **c** | Une `async` renvoie **toujours** une Promise (la valeur `return` la résout). |
| 13 | **c** | `Promise.all` rejette **dès la première** rejetée. (`allSettled` attend tout.) |
| 14 | **a** | Destructuring : `x` = `1`. |
| 15 | **a, b** | `^1.4.2` = `>=1.4.2 <2.0.0` → `1.4.9` ✅ et `1.5.0` ✅ ; `2.0.0` ❌ (majeure), `1.3.0` ❌ (< base). |
| 16 | **b** | Outillage (tests, lint) → `devDependencies`. `express` (runtime) → `dependencies`. |
| 17 | **b** | `require`/`module.exports` = CommonJS ; `import`/`export` = ESM. |
| 18 | **b** | Le middleware d'erreur a **4 paramètres** `(err, req, res, next)` — c'est la signature qui le désigne. |
| 19 | **b** | Les variantes `*Sync` **bloquent l'unique thread** → tout le serveur gèle. |
| 20 | **b** | `201 Created`. (200 OK, 404 Not Found, 500 Internal Server Error.) |

> **Q15 : réponses multiples** (`a` **et** `b`). Si le test compte les points négatifs, ne coche que ce dont tu es sûr ; sinon coche les deux.
> **Q6 (le classique) :** retiens la règle — *tout le synchrone, puis toutes les microtâches (promesses), puis les macrotâches (timers)*. `A D C B`.
