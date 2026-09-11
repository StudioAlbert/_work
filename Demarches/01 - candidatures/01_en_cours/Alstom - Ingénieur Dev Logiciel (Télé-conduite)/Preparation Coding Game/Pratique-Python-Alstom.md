# Pratique Python — QCM & exercices (test Alstom)

> Complète [[Cheatsheet-Python-Alstom]]. **Méthode :** réponds SANS regarder le corrigé (papier ou à voix haute), puis vérifie. Les prédictions de sortie sont le format n°1 du jour J.
> ★ = question plus retorse. Corrigé QCM tout en bas ; corrigés des exercices juste après chaque énoncé (cache-les si tu veux jouer le jeu).

---

## Partie A — QCM (22 questions)

**1.** Que produit `print(3 / 2)` ?
- a) `1`  b) `1.5`  c) `2`  d) `'1.5'`

**2.** Que produit `print(7 // 2, 7 % 2)` ?
- a) `3 1`  b) `3.5 1`  c) `3 0`  d) `4 1`

**3.** Laquelle de ces valeurs est **truthy** (vraie dans un `if`) ?
- a) `0`  b) `""`  c) `"0"`  d) `[]`

**4.** ```python
a = [1, 2, 3]
b = a
b.append(4)
print(len(a))
```
- a) `3`  b) `4`  c) `TypeError`  d) `2`

**5.** Que produit `print("abcde"[-2])` ?
- a) `d`  b) `e`  c) `b`  d) erreur

**6.** Que produit `print("bonjour"[1:4])` ?
- a) `onj`  b) `bon`  c) `onjo`  d) `onjour`

**7.** ★ ```python
def f(x=[]):
    x.append(1)
    return x
print(f(), f())
```
- a) `[1] [1]`  b) `[1] [1, 1]`  c) `[1, 1] [1, 1]`  d) `[] []`

**8.** Quel est le type de `(42)` ?
- a) `tuple`  b) `int`  c) `list`  d) erreur

**9.** Laquelle est **FAUSSE** ?
- a) `sorted(l)` retourne une nouvelle liste triée
- b) `l.sort()` trie la liste en place
- c) `l.sort()` retourne la liste triée
- d) `sorted(l, key=len)` trie selon la longueur

**10.** Avec `d = {"a": 1}`, laquelle **lève une exception** ?
- a) `d.get("b")`  b) `d["b"]`  c) `d.get("b", 0)`  d) `"b" in d`

**11.** Que produit `print(2 ** 10)` ?
- a) `20`  b) `100`  c) `1024`  d) `12`

**12.** Que produit `print([x * 2 for x in range(3)])` ?
- a) `[0, 2, 4]`  b) `[2, 4, 6]`  c) `[0, 1, 2]`  d) `[1, 2, 3]`

**13.** Que produit `print(list(range(1, 6, 2)))` ?
- a) `[1, 3, 5]`  b) `[1, 2, 3, 4, 5]`  c) `[1, 3, 5, 7]`  d) `[2, 4]`

**14.** À propos des chaînes, laquelle est **VRAIE** ?
- a) `"abc"[0] = "z"` modifie la chaîne
- b) les chaînes sont mutables
- c) `"abc"[0] = "z"` lève une `TypeError` (chaînes immuables)
- d) `"abc" + 1` vaut `"abc1"`

**15.** ```python
a = [1]; b = [1]
print(a == b, a is b)
```
- a) `True True`  b) `True False`  c) `False False`  d) `False True`

**16.** Que produit `print("a,b,c".split(","))` ?
- a) `"abc"`  b) `['a', 'b', 'c']`  c) `['a,b,c']`  d) `('a','b','c')`

**17.** Que produit `print(f"{3.14159:.2f}")` ?
- a) `3.14159`  b) `3.14`  c) `3.1`  d) `3`

**18.** Par défaut, `enumerate(seq)` commence l'index à…
- a) `1`  b) `0`  c) `-1`  d) la longueur de `seq`

**19.** ★ ```python
total = 0
def maj():
    total = total + 1
maj()
```
Que se passe-t-il ?
- a) `total` vaut `1`  b) `total` vaut `0`  c) `UnboundLocalError`  d) `NameError`

**20.** ★ Que vaut `bool("False")` ?
- a) `False`  b) `True`  c) `None`  d) erreur

**21.** ★ ```python
g = (x for x in range(3))
print(list(g), list(g))
```
- a) `[0, 1, 2] [0, 1, 2]`  b) `[0, 1, 2] []`  c) `[] []`  d) erreur

**22.** À propos du **GIL** (CPython), laquelle est **VRAIE** ?
- a) `threading` accélère un calcul CPU pur
- b) `multiprocessing` contourne le GIL (vrais processus parallèles)
- c) le GIL empêche toute concurrence d'I/O
- d) Python ne propose pas de threads

**23.** `a, *b = [1, 2, 3, 4]` — que vaut `b` ?
- a) `2`  b) `[2, 3, 4]`  c) `(2, 3, 4)`  d) `[1, 2, 3, 4]`

**24.** Que produit `print(0 < 5 < 3)` ?
- a) `True`  b) `False`  c) erreur de syntaxe  d) `0`
```
---
## Partie B — Exercices de code (8 katas)

> Écris-les **de mémoire**, puis compare. Vise simple et correct.

### Ex. 1 — FizzBuzz
Écris `fizzbuzz(n)` qui retourne la **liste** des chaînes de 1 à `n` : multiples de 3 → `"Fizz"`, de 5 → `"Buzz"`, de 15 → `"FizzBuzz"`, sinon le nombre en chaîne.
*Indice : teste `% 15` en premier, ou construis la chaîne par accumulation.*

```python
def fizzbuzz(n):
    out = []
    for i in range(1, n + 1):
        s = ""
        if i % 3 == 0: s += "Fizz"
        if i % 5 == 0: s += "Buzz"
        out.append(s or str(i))   # s vide -> falsy -> str(i)
    return out
```

### Ex. 2 — Inverser l'ordre des mots
`reverse_words("le train roule")` → `"roule train le"`.
*Indice : `split()` puis `reversed`/slicing puis `join`.*

```python
def reverse_words(phrase):
    return " ".join(phrase.split()[::-1])
```

### Ex. 3 — Fréquence des mots
`count_words("a b a c b a")` → `{"a": 3, "b": 2, "c": 1}`.
*Indice : `dict.get(mot, 0) + 1`, ou `collections.Counter`.*

```python
def count_words(texte):
    freq = {}
    for mot in texte.split():
        freq[mot] = freq.get(mot, 0) + 1
    return freq
# Variante : from collections import Counter ; return dict(Counter(texte.split()))
```

### Ex. 4 — Palindrome
`is_palindrome("Radar")` → `True`, en ignorant la casse et les espaces.
*Indice : normaliser (minuscules, retirer espaces) puis comparer à l'inverse `[::-1]`.*

```python
def is_palindrome(s):
    t = s.lower().replace(" ", "")
    return t == t[::-1]
```

### Ex. 5 — Two-sum
`two_sum([2, 7, 11, 15], 9)` → `(0, 1)` : indices de deux nombres dont la somme vaut la cible.
*Indice : un `dict {valeur: index}` en un seul passage — pour chaque `x`, cherche `cible - x` déjà vu.*

```python
def two_sum(nums, cible):
    vus = {}                       # valeur -> index
    for i, x in enumerate(nums):
        if cible - x in vus:
            return (vus[cible - x], i)
        vus[x] = i
    return None
```

### Ex. 6 — Grouper les anagrammes
`group_anagrams(["aet", "eat", "tea", "bat"])` → regroupe par signature triée :
`{"aet": ["aet", "eat", "tea"], "abt": ["bat"]}` (clé = lettres triées).
*Indice : signature = `"".join(sorted(mot))` ; `defaultdict(list)`.*

```python
from collections import defaultdict
def group_anagrams(mots):
    groupes = defaultdict(list)
    for mot in mots:
        groupes["".join(sorted(mot))].append(mot)
    return dict(groupes)
```

### Ex. 7 — Classe `Pile` (Stack)
Implémente une pile LIFO : `push(x)`, `pop()`, `peek()`, `is_empty()`, `__len__`.
*Indice : une `list` fait tout — `append` / `pop`.*

```python
class Pile:
    def __init__(self):
        self._items = []
    def push(self, x):
        self._items.append(x)
    def pop(self):
        if self.is_empty():
            raise IndexError("pile vide")
        return self._items.pop()
    def peek(self):
        return self._items[-1]
    def is_empty(self):
        return len(self._items) == 0
    def __len__(self):
        return len(self._items)
```

### Ex. 8 — Parser une config
`parse_config(["# titre", "", "host = local", "port = 1883"])` →
`{"host": "local", "port": "1883"}` : ignorer lignes vides et commençant par `#`, découper sur `=`, enlever les espaces.
*Indice : `line.strip()`, sauter si vide ou débute par `#`, `split("=", 1)`, `.strip()` des deux côtés.*

```python
def parse_config(lignes):
    conf = {}
    for ligne in lignes:
        ligne = ligne.strip()
        if not ligne or ligne.startswith("#"):
            continue
        cle, _, valeur = ligne.partition("=")   # partition = split sûr même sans '='
        if _:                                    # '=' présent
            conf[cle.strip()] = valeur.strip()
    return conf
```

---

## Corrigé QCM

| Q | Rép | Explication express |
|---|---|---|
| 1 | **b** | `/` = division flottante → `1.5`. (`//` donnerait `1`.) |
| 2 | **a** | `//` division entière = `3` ; `%` reste = `1`. |
| 3 | **c** | `"0"` est une chaîne **non vide** → truthy. `0`, `""`, `[]` sont falsy. |
| 4 | **b** | `b = a` est un **alias** (même liste) → `append` visible via `a` → `4`. |
| 5 | **a** | index négatif : `-1`=`e`, `-2`=`d` → réponse `d`. **Voir note.** |
| 6 | **a** | `[1:4]` = indices 1,2,3, borne haute exclue → `onj`. |
| 7 | **c** | Défaut mutable évalué **une fois** ; les deux appels renvoient la **même** liste, mutée à chaque fois → `print(f(), f())` affiche `[1, 1] [1, 1]`. **Voir note piège.** |
| 8 | **b** | `(42)` = un `int` parenthésé. Un tuple à 1 élément = `(42,)`. |
| 9 | **c** | `l.sort()` retourne `None` (tri en place), pas la liste. |
| 10 | **b** | `d["b"]` sur clé absente → `KeyError`. `.get` renvoie `None`/défaut. |
| 11 | **c** | `**` = puissance → `2^10 = 1024`. |
| 12 | **a** | `x*2` pour `x` in 0,1,2 → `[0, 2, 4]`. |
| 13 | **a** | `range(1,6,2)` = 1,3,5 (pas de 2, borne 6 exclue). |
| 14 | **c** | Chaînes **immuables** → affectation d'un caractère = `TypeError`. |
| 15 | **b** | `==` compare les valeurs (`True`) ; `is` compare l'identité (2 objets distincts → `False`). |
| 16 | **b** | `split(",")` → liste `['a', 'b', 'c']`. |
| 17 | **b** | `:.2f` = 2 décimales → `3.14`. |
| 18 | **b** | `enumerate` démarre à `0` (option `start=` pour changer). |
| 19 | **c** | Affecter `total` **dans** la fonction la rend locale → lecture avant affectation = `UnboundLocalError`. (Fix : `global total`.) |
| 20 | **b** | `bool` d'une chaîne **non vide** = `True`, quel que soit son texte (« False » compris). |
| 21 | **b** | Un générateur s'épuise : 1er `list(g)` = `[0,1,2]`, 2e = `[]`. |
| 22 | **b** | `multiprocessing` lance de vrais processus → vrai parallélisme CPU ; `threading` reste bridé par le GIL (utile surtout pour l'I/O). |
| 23 | **b** | Unpacking étoilé : `a=1`, `b=[2,3,4]` (toujours une **liste**). |
| 24 | **b** | Comparaison chaînée `0<5 and 5<3` → `5<3` faux → `False`. |

> **Note Q5 :** `"abcde"` → indices `a`(0/-5) `b`(1/-4) `c`(2/-3) `d`(3/-2) `e`(4/-1). Donc `[-2]` = `d`. ⚠️ Si tu as répondu `e`, tu as pris `-1`. **Réponse correcte : a) `d`.**
> **Note Q7 (le piège le plus fréquent) :** le paramètre par défaut `[]` est créé **une seule fois** à la définition. `f()` renvoie **la même** liste, mutée à chaque appel. Comme les deux appels dans `print(f(), f())` sont évalués avant l'affichage, on voit `[1, 1] [1, 1]`. Correction idiomatique : `def f(x=None): x = [] if x is None else x`.

*(Q5 : la bonne case est **a**. Le tableau ci-dessus l'indique — ne te fie pas à ta première intuition sur les index négatifs, c'est exactement le type de piège du test.)*
