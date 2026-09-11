# Pratique React — QCM & exercices (test Alstom)

> Complète [[Cheatsheet-React-Alstom]]. Prérequis JS : [[Pratique-NodeJS-Alstom]] Partie A.
> Les QCM React tournent à 80 % autour de : props/state, `useState`, `useEffect`, `key`, règles des hooks. ★ = plus retors. Corrigé QCM en bas.

---

## Partie A — QCM (18 questions)

**1.** Quel nom de composant est **valide** (React le rendra) ?
- a) `function trainCard() {…}`  b) `function TrainCard() {…}`  c) `function train_card() {…}`  d) les trois

**2.** En JSX, l'attribut de classe CSS s'écrit…
- a) `class`  b) `className`  c) `css`  d) `classname`

**3.** Les **props** sont…
- a) modifiables par le composant  b) **en lecture seule** (reçues du parent)
- c) globales  d) stockées dans le DOM

**4.** Pour qu'un changement de donnée mette l'UI à jour, il faut…
- a) réassigner la variable  b) muter l'objet directement
- c) passer par le **setter de state** (nouvelle valeur/référence)  d) appeler `render()`

**5.** ★ ```jsx
const [count, setCount] = useState(0);
// dans un handler :
setCount(count + 1);
setCount(count + 1);
```
Après exécution, `count` augmente de…
- a) `2`  b) `1`  c) `0`  d) indéterminé

**6.** Pour incrémenter **deux fois** de façon fiable, on écrit…
- a) `setCount(count + 2)`  b) `setCount(c => c + 1)` deux fois
- c) `count = count + 2`  d) `setCount(count++); setCount(count++)`

**7.** `useEffect(fn, [])` (tableau de dépendances **vide**) exécute `fn`…
- a) après chaque rendu  b) **une seule fois, au montage**  c) jamais  d) au démontage seulement

**8.** `useEffect(fn)` **sans** tableau de dépendances exécute `fn`…
- a) une fois  b) **après chaque rendu**  c) jamais  d) avant le rendu

**9.** La fonction **retournée** par un `useEffect` sert à…
- a) rien  b) le **nettoyage** (démontage, ou avant ré-exécution)  c) retourner le JSX  d) déclencher un re-rendu

**10.** Une bonne `key` de liste est…
- a) l'index de la boucle  b) `Math.random()`  c) un **identifiant stable et unique**  d) facultative toujours

**11.** Un **input contrôlé** s'écrit…
- a) `<input />`  b) `<input value={v} onChange={e => setV(e.target.value)} />`
- c) `<input ref={r} />`  d) `<input defaultValue={v} />`

**12.** ★ Différence entre `onClick={handle}` et `onClick={handle()}` ?
- a) aucune
- b) `handle()` **appelle la fonction au rendu** (souvent un bug) ; `handle` passe la référence
- c) `handle` est invalide  d) `handle()` est recommandé

**13.** Les **règles des hooks** imposent de les appeler…
- a) n'importe où  b) dans des `if`/boucles  c) **au niveau supérieur** du composant, jamais conditionnellement  d) dans le JSX

**14.** Un composant se re-rend quand… (plusieurs vraies)
- a) son **state** change  b) ses **props** changent  c) son **parent** se re-rend  d) on déplace la souris

**15.** Le style inline correct est…
- a) `style="color: red"`  b) `style={color: 'red'}`  c) `style={{ color: 'red' }}`  d) `css={red}`

**16.** À quoi sert un **Fragment** `<>…</>` ?
- a) créer une div  b) **grouper des éléments sans nœud DOM supplémentaire**
- c) importer React  d) styliser

**17.** Deux composants frères doivent partager un état : on…
- a) duplique l'état dans chacun  b) **remonte l'état dans le parent commun** (lifting state up)
- c) utilise une variable globale  d) mute les props

**18.** ★ ```jsx
list.push(nouvel);
setList(list);
```
Pourquoi l'UI risque de **ne pas** se mettre à jour ?
- a) `push` est interdit  b) `setList` est asynchrone
- c) **même référence de tableau** → React ne détecte pas de changement  d) il manque une `key`

---

## Partie B — Exercices de code (4)

### Ex. 1 — Lire & prédire
```jsx
function App() {
  const [n, setN] = useState(0);
  console.log("rendu", n);
  return <button onClick={() => setN(n + 1)}>{n}</button>;
}
```
Questions : qu'affiche le bouton au départ ? Que loggue la console au 1er clic ? Le composant se re-rend-il ?
*Réponse : bouton `0` au départ ; au clic, `setN(1)` → re-rendu → log `rendu 1`, bouton affiche `1`. Oui, tout changement de state re-rend.*

### Ex. 2 — Corriger le bug de state
Ce bouton devrait ajouter un élément à la liste, mais l'UI ne bouge pas. Corrige.
```jsx
const [items, setItems] = useState([]);
function add() {
  items.push("x");     // ❌ mutation, même référence
  setItems(items);
}
```
*Indice : créer une **nouvelle** référence de tableau.*

```jsx
function add() {
  setItems([...items, "x"]);   // ✅ nouveau tableau -> re-rendu
}
```

### Ex. 3 — Composant `Counter`
Écris un composant qui affiche un compteur et un bouton « +1 » qui l'incrémente de façon fiable.
*Indice : `useState` + forme fonctionnelle du setter.*

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Compteur : {count}</p>
      <button onClick={() => setCount(c => c + 1)}>+1</button>
    </div>
  );
}
export default Counter;
```

### Ex. 4 — Liste filtrée avec `key`
Affiche la liste des trains **en marche** (`running === true`), chacun avec une `key` stable.
`trains = [{id:1,name:"TGV",running:true},{id:2,name:"TER",running:false}]`
*Indice : `filter` puis `map` ; `key={t.id}`.*

```jsx
function TrainList({ trains }) {
  return (
    <ul>
      {trains
        .filter(t => t.running)
        .map(t => <li key={t.id}>{t.name}</li>)}
    </ul>
  );
}
```

---

## Corrigé QCM

| Q | Rép | Explication express |
|---|---|---|
| 1 | **b** | Un composant doit commencer par une **majuscule** (sinon JSX le prend pour une balise HTML). |
| 2 | **b** | `className` (`class` est un mot réservé JS). De même `htmlFor` au lieu de `for`. |
| 3 | **b** | Les props sont **en lecture seule** ; un composant ne modifie jamais ses props. |
| 4 | **c** | Seul le **setter** (avec une nouvelle valeur/référence) déclenche un re-rendu. |
| 5 | **b** | Les deux `setCount(count+1)` lisent le **même** `count` (snapshot) → +1 net. |
| 6 | **b** | Forme **fonctionnelle** `setCount(c => c + 1)` : chaque appel part de la valeur à jour → +2. |
| 7 | **b** | `[]` = exécuté **une fois au montage** (+ cleanup au démontage). |
| 8 | **b** | Sans tableau de deps → **après chaque rendu**. |
| 9 | **b** | La fonction retournée = **cleanup** (démontage ou avant ré-exécution de l'effet). |
| 10 | **c** | `key` = identifiant **stable et unique** ; l'index casse la réconciliation si la liste bouge. |
| 11 | **b** | Contrôlé = `value` piloté par le state + `onChange`. |
| 12 | **b** | `handle()` **exécute** la fonction au moment du rendu (bug fréquent) ; passer `handle` (la référence). |
| 13 | **c** | Hooks uniquement **au niveau supérieur**, jamais dans `if`/boucle (React se base sur l'ordre d'appel). |
| 14 | **a, b, c** | Re-rendu si **state**, **props** ou **parent** changent. Pas la souris. |
| 15 | **c** | `style={{ … }}` : accolades JSX + objet JS → double accolade. |
| 16 | **b** | Fragment = grouper sans ajouter de nœud DOM (un composant retourne une seule racine). |
| 17 | **b** | **Lifting state up** : l'état partagé remonte au parent commun. |
| 18 | **c** | `push` mute **la même référence** ; React compare les références → pas de changement détecté. Fix : `setList([...list, x])`. |

> **Q14 : réponses multiples** (`a`, `b`, `c`).
> **Fil rouge React :** *React ne « voit » que ce qui passe par les setters/props avec une **nouvelle référence**.* Les Q5, Q6 et Q18 sont trois visages du même piège.
