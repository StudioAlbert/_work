# Cheatsheet React — Test technique Alstom

> **Enjeu : limiter la casse.** Prérequis : les fondamentaux JS de [[Cheatsheet-NodeJS-Alstom]] §1. Les QCM React tournent à 80 % autour de : props/state, `useState`, `useEffect`, `key`, règles des hooks — tout est ici.
> Modèle mental pour toi : **UI = f(state)**, re-rendu déclaratif — proche d'un pattern MVVM/data-binding, très loin du mode immédiat Unity.
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 1. Composants & JSX

```jsx
function TrainCard({ name, speed }) {          // composant = fonction, nom en Majuscule
  return (
    <div className="card">                     {/* className, pas class */}
      <h2>{name}</h2>                          {/* {expr} = expression JS */}
      {speed > 0 ? <p>{speed} km/h</p> : <p>À l'arrêt</p>}
    </div>
  );
}
export default TrainCard;
// Usage : <TrainCard name="TGV" speed={280} />   — nombre entre {}, chaîne entre ""
```
- JSX = sucre syntaxique sur `React.createElement` ; un composant retourne **un seul élément racine** (ou un fragment `<>...</>`).
- Pièges de syntaxe QCM : `className` (pas `class`), `htmlFor` (pas `for`), `onClick={handler}` en camelCase **sans parenthèses** (`onClick={f()}` appelle immédiatement au rendu — piège classique), `style={{ color: 'red' }}` (objet, double accolade).

## 2. Props vs State — la question centrale

- **Props** : données reçues **du parent**, **en lecture seule** — un composant ne modifie jamais ses props.
- **State** : données **propres** au composant, modifiées via le setter → déclenche un **re-rendu**.
- Flux de données **unidirectionnel** : parent → enfant via props ; enfant → parent via **callback passée en prop**.
- **Lifting state up** : quand deux composants partagent un état, il remonte dans leur parent commun.

## 3. `useState` — pièges garantis

```jsx
const [count, setCount] = useState(0);
```
- **Ne jamais muter le state directement** : `count++` ou `list.push(x)` ne re-rend **pas**. Toujours passer par le setter avec une **nouvelle** valeur/référence :
```jsx
setList([...list, x]);              // nouveau tableau
setUser({ ...user, name: 'Ada' }); // nouvel objet
```
- **Le setter est asynchrone (batché)** : lire `count` juste après `setCount(count + 1)` donne l'**ancienne** valeur.
```jsx
setCount(count + 1); setCount(count + 1);   // +1 seulement (même snapshot) — PIÈGE QCM n°1
setCount(c => c + 1); setCount(c => c + 1); // +2 : forme fonctionnelle
```
- L'argument de `useState(init)` n'est utilisé qu'au **premier rendu**.

## 4. `useEffect` — effets de bord

```jsx
useEffect(() => {
  const id = setInterval(poll, 1000);    // effet (abonnement, fetch, timer…)
  return () => clearInterval(id);        // cleanup : démontage OU avant ré-exécution
}, [url]);                               // tableau de dépendances
```
| Dépendances | Exécution |
| --- | --- |
| absentes | après **chaque** rendu |
| `[]` | une fois, au **montage** (+ cleanup au démontage) |
| `[a, b]` | au montage puis quand `a` ou `b` change |

- Piège : modifier dans l'effet un state listé dans ses dépendances → **boucle infinie**.
- Piège : oublier le cleanup d'un abonnement/timer → fuites, handlers multiples.
- `useEffect` s'exécute **après** le rendu (jamais pendant).

## 5. Règles des hooks — question quasi certaine

1. Appeler les hooks **uniquement au niveau supérieur** du composant — jamais dans un `if`, une boucle ou une fonction imbriquée (React s'appuie sur l'**ordre d'appel**).
2. Uniquement dans des **composants fonction** ou des hooks personnalisés (`useXxx`).

## 6. Listes & `key`

```jsx
{trains.map(t => <TrainCard key={t.id} {...t} />)}
```
- `key` : identifiant **stable et unique** permettant la réconciliation. **L'index est une mauvaise `key`** si la liste peut être réordonnée/filtrée (états mélangés) — piège QCM récurrent.

## 7. Formulaires contrôlés

```jsx
const [value, setValue] = useState('');
<input value={value} onChange={e => setValue(e.target.value)} />
```
- **Contrôlé** : le state React est la source de vérité (`value` + `onChange`). **Non contrôlé** : le DOM garde la valeur (`ref`). QCM : « composant contrôlé » = la définition ci-dessus.

## 8. Rendu & Virtual DOM (questions de cours)

- React maintient un **Virtual DOM** ; à chaque re-rendu il **diffe** l'ancien et le nouveau (réconciliation) et n'applique au DOM réel que le minimum.
- Un composant se re-rend quand : son **state** change, ses **props** changent, ou son **parent** se re-rend.
- Optimisations à reconnaître (pas à maîtriser) : `React.memo` (mémorise un composant), `useMemo` (mémorise un calcul), `useCallback` (mémorise une fonction), `useRef` (valeur persistante **sans** re-rendu / accès DOM), `useContext` (éviter le « prop drilling » — passage de props en cascade).

## 9. Écosystème (culture QCM)

- Bootstrapping : **Vite** (moderne) / Create React App (legacy). SSR/framework : **Next.js**.
- Routage : **React Router** (`<Route path="/trains/:id">`).
- État global : Context API, **Redux** (store unique, actions, reducers — connaître les mots).
- Tests : Jest + React Testing Library.
- React ne « voit » que ce qui passe par setters/props : une donnée mutée silencieusement n'actualise jamais l'UI — résume 80 % des bugs et des pièges.

## 10. Micro-drills (à refaire J5)

1. Pourquoi `setCount(count+1)` deux fois n'ajoute que 1 ? Corriger.
2. `list.push(x); setList(list);` — pourquoi rien ne se re-rend ? (même référence)
3. `useEffect(..., [])` vs sans tableau — différence exacte.
4. Pourquoi l'index est une mauvaise `key` ?
5. `onClick={handle()}` vs `onClick={handle}` — que se passe-t-il au rendu ?
