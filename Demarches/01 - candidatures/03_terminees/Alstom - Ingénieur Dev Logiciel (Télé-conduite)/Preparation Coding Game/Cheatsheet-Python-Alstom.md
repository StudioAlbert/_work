# Cheatsheet Python — Test technique Alstom (départ de zéro)

> **Enjeu : priorité d'apprentissage n°1 de la semaine (~2 jours, mains sur le clavier).** Zéro Python ≠ zéro programmation : cette fiche s'appuie sur tes réflexes C#/C++ et signale à chaque fois ce qui diffère.
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 0. Démarrage express (J1 matin — 1 h)

1. Installer **Python 3.12+** (python.org ou `winget install Python.Python.3.12`). Vérifier : `python --version`.
2. Deux façons d'exécuter : le **REPL** (`python` seul — laboratoire interactif, s'en servir en continu) et les scripts : `python mon_script.py`.
3. Éditeur : VS Code + extension Python suffit.
4. **Écrire ces 5 scripts à la main** (pas copier-coller) :
   - FizzBuzz 1→100 ;
   - inverser une chaîne saisie par l'utilisateur ;
   - compter les occurrences de chaque mot d'une phrase (dict) ;
   - lire un fichier texte et afficher ses lignes numérotées ;
   - une classe `Train` avec vitesse, méthodes `accelerer`/`freiner`, et affichage.

## 1. Choc culturel C#/C++ → Python (à lire en premier)

| Habitude C#/C++ | En Python |
| --- | --- |
| Blocs `{ }` | **L'indentation EST le bloc** (4 espaces). Un `:` ouvre le bloc |
| `;` en fin de ligne | Rien |
| Types déclarés (`int x = 5;`) | `x = 5` — typage **dynamique mais fort** (`"1" + 1` → erreur, pas de conversion implicite) |
| `null` | `None` (tester avec `x is None`) |
| `true/false` | `True` / `False` (majuscule) |
| `&&`, `\|\|`, `!` | `and`, `or`, `not` |
| `switch` | `match` (3.10+) ou chaîne `if/elif/else` |
| `for (int i=0; …)` | `for i in range(10):` — on itère sur des séquences, pas des compteurs |
| `Console.WriteLine($"x={x}")` | `print(f"x={x}")` — les **f-strings** |
| surcharge de méthodes | N'existe pas — valeurs par défaut : `def f(a, b=0):` |
| `using` | `with open("f.txt") as f:` |
| compilation | Interprété — les erreurs de type sortent **à l'exécution** |
| camelCase | **snake_case** (`ma_fonction`, `ma_variable`) |

```python
def vitesse_moyenne(distances, duree=1.0):   # def, pas de types requis
    total = sum(distances)
    if duree <= 0:
        raise ValueError("durée invalide")
    return total / duree                      # / = flottant, // = division entière

for i, d in enumerate(distances):             # index + valeur
    print(f"tronçon {i}: {d} km")
```

## 2. Types & structures de base

- Immutables : `int`, `float`, `str`, `tuple`, `bool`, `None`. Mutables : `list`, `dict`, `set`.
- **`list`** `[1, 2, 3]` ≈ `List<T>` : `append`, `pop`, `len(l)`, `l[0]`, `l[-1]` (dernier !), tri `l.sort()` / `sorted(l)`.
- **`dict`** `{"id": 42}` ≈ `Dictionary` : `d["id"]` (KeyError si absent), `d.get("id", defaut)`, `for k, v in d.items():`. Ordre d'insertion conservé (≥ 3.7).
- **`tuple`** `(1, 2)` : liste immuable ; retour multiple `return a, b` ; le tuple à 1 élément s'écrit **`(1,)`** (piège : `(1)` est un int).
- **`set`** `{1, 2}` : unicité, appartenance O(1) — `if x in s:`.
- **Slicing** (partout) : `s[2:5]`, `s[:3]`, `s[-3:]`, `s[::-1]` (renversement). Borne haute **exclue**, comme `range(a, b)`.
- Chaînes **immuables** : `s[0] = 'a'` → erreur. Concaténer en boucle = O(n²) → `''.join(morceaux)`.
- Falsy : `0`, `''`, `[]`, `{}`, `None` → `if ma_liste:` teste « non vide ».
- Comparaisons chaînées légales : `0 < x < 10`.

## 3. Idiomes à reconnaître absolument (QCM + lecture de code)

```python
carres = [x*x for x in data if x > 0]      # list comprehension = boucle+filtre en 1 ligne
index = {v: i for i, v in enumerate(l)}    # dict comprehension
a, b = b, a                                # échange sans temporaire
a, *reste = [1, 2, 3]                      # unpacking
for x, y in zip(l1, l2):                   # parcours parallèle
sorted(trains, key=lambda t: t.vitesse, reverse=True)
"—".join(["a", "b"])  /  "a,b,c".split(",")
```

## 4. Pièges QCM garantis — les apprendre par cœur

```python
def f(x=[]):          # PIÈGE N°1 : le défaut est évalué UNE SEULE FOIS
    x.append(1)
    return x
f(); f()              # → [1, 1]   (pas [1])
# Correct : def f(x=None): x = [] if x is None else x
```
```python
a = [1, 2]; b = a     # b est un ALIAS (référence), pas une copie
b.append(3)           # a vaut aussi [1, 2, 3]
c = a[:]              # copie superficielle ; copy.deepcopy(a) : profonde
```
```python
l = l.sort()          # PIÈGE : sort() trie EN PLACE et retourne None → l vaut None
l = sorted(l)         # correct si on veut une nouvelle liste
```
- **`is` vs `==`** : `==` compare les valeurs, `is` l'identité d'objet. N'utiliser `is` que pour `is None`. (Piège : petits entiers internés → `a is b` parfois vrai « par accident ».)
- Assigner dans une fonction rend la variable **locale** → `UnboundLocalError` si lue avant ; `global`/`nonlocal` pour modifier au-delà.
- Lambdas dans une boucle : capture **tardive** — `[lambda: i for i in range(3)]` → toutes rendent 2. Correction : `lambda i=i: i`.
- `t = (1, 2, [3]); t[2].append(4)` est **légal** : le tuple est immuable, pas son contenu.
- Un générateur (`yield`) est **épuisable une seule fois**.

## 5. Classes — vu depuis C#

```python
class Train:
    compteur = 0                      # attribut de CLASSE (partagé — piège si mutable)

    def __init__(self, nom, vitesse=0):   # constructeur
        self.nom = nom                    # attributs d'INSTANCE, créés à la volée
        self.vitesse = vitesse
        Train.compteur += 1

    def accelerer(self, delta):           # self explicite partout
        self.vitesse += delta

    def __str__(self):                    # ≈ ToString()
        return f"{self.nom} à {self.vitesse} km/h"

class TGV(Train):                          # héritage
    def __init__(self, nom):
        super().__init__(nom, 0)
```
- Pas de `private` réel : convention `_x` (interne), `__x` (name mangling).
- Pas d'interfaces : **duck typing** — si l'objet a la méthode, ça marche.

## 6. Exceptions & fichiers

```python
try:
    v = int(texte)
except ValueError:        # du plus SPÉCIFIQUE au plus général (piège : ordre inverse = branche morte)
    v = 0
finally:
    ...                   # toujours exécuté

with open("data.txt", encoding="utf-8") as f:   # ferme automatiquement (≈ using)
    for ligne in f:
        ...
```

## 7. Questions de cours probables

- **GIL** : un seul thread exécute du bytecode Python à la fois → `threading` n'accélère pas le calcul pur (utile pour l'I/O) ; calcul parallèle réel → `multiprocessing`.
- Python est **interprété**, **multiplateforme**, à **typage dynamique fort**.
- Gestion mémoire : comptage de références + garbage collector — pas de `delete`.
- `pip install paquet` (+ `requirements.txt`) ; environnements virtuels `python -m venv .venv` (isolation des dépendances — l'équivalent conceptuel de ce que Docker fait au niveau système).
- `if __name__ == "__main__":` — le code n'est exécuté que si le fichier est lancé directement (pas importé).

## 8. Boîte à outils problème de code (si Python imposé)

```python
from collections import Counter, defaultdict, deque
Counter(mots).most_common(3)      # fréquences
defaultdict(list)                 # dict à valeur par défaut
deque()                           # file O(1) aux deux bouts
int("42"), str(42), ord('a'), chr(97), abs(), min(), max(), sum()
"".join(sorted(s))                # signature d'anagramme
f"{x:.2f}"                        # formatage
```
- Réflexes : `set` pour l'appartenance, `dict` pour associer, slicing pour les sous-chaînes.

## 9. Plan de travail J1-J2

- **J1 matin** : §0 (installation + 5 scripts) en s'aidant de §1-§2.
- **J1 après-midi** : §3-§4 + 3 katas faciles (Exercism piste Python, ou CodinGame Easy).
- **J2 matin** : §5-§7 + 3 katas ; réécrire de mémoire les pièges de §4.
- **J2 soir + J5** : relire uniquement §4 (pièges) et §7 (cours).
