# Cheatsheet C++ — Test technique Alstom

> **Enjeu : maximal.** C'est ta promesse centrale — viser l'excellence. Révision anti-pièges, pas apprentissage.
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 1. Mémoire & RAII

- **RAII** : la ressource est acquise dans le constructeur, libérée dans le destructeur. La durée de vie de l'objet = durée de vie de la ressource. C'est LE concept que les QCM C++ adorent.
- **Rule of 3/5/0** : si tu définis destructeur, copie ou affectation → définis les trois (3) ; avec move : les cinq (5) ; idéalement, aucun (0) en déléguant aux membres RAII.
- **Smart pointers** :
  - `std::unique_ptr` — propriété exclusive, non copiable, **movable**. Coût quasi nul.
  - `std::shared_ptr` — comptage de références (atomique, coût réel). Copie = incrément.
  - `std::weak_ptr` — observe sans posséder ; **casse les cycles** de `shared_ptr`.
  - `make_unique` / `make_shared` préférés à `new` (exception-safety, 1 allocation pour `make_shared`).

### Pièges QCM mémoire
- **Deux `shared_ptr` qui se référencent mutuellement → fuite** (le compteur ne tombe jamais à 0). Réponse : `weak_ptr`.
- `unique_ptr` **ne peut pas être copié** — `auto p2 = p1;` ne compile pas ; `auto p2 = std::move(p1);` oui, et `p1` devient nul.
- `delete` sur un pointeur **de base sans destructeur `virtual`** = **comportement indéfini (UB)**. Piège n°1 des QCM héritage.
- `new[]` doit être libéré par `delete[]`, pas `delete` (UB sinon).
- Un pointeur vers une variable locale retournée par une fonction = **dangling pointer** (UB).

## 2. Move semantics

```cpp
std::string a = "hello";
std::string b = std::move(a); // a est dans un état valide mais non spécifié
```
- `std::move` **ne déplace rien** : c'est un cast en rvalue reference. Le déplacement se fait dans le constructeur/opérateur de move appelé.
- Après move : l'objet source est valide mais son contenu est indéterminé — le réutiliser sans réassignation est un piège.
- **RVO/copy elision** : `return obj;` ne copie généralement pas — répondre « 0 copie » aux QCM sur le retour par valeur en C++17.

## 3. Héritage & polymorphisme

- Une méthode `virtual` est résolue **à l'exécution** via la vtable ; sans `virtual`, résolution **statique** (type déclaré du pointeur).
- **Destructeur virtuel obligatoire** dès qu'une classe est destinée à être dérivée et détruite polymorphiquement.
- `override` : erreur de compilation si la signature ne correspond pas — toujours l'utiliser.
- **Object slicing** : copier un `Derived` dans un `Base` **par valeur** tranche la partie dérivée. Le polymorphisme exige pointeur ou référence.
- **Appel de `virtual` dans un constructeur/destructeur** : c'est la version **de la classe en cours de construction** qui est appelée, pas celle du dérivé. Piège QCM récurrent.
- Classe abstraite = au moins une fonction **virtuelle pure** (`= 0`) ; non instanciable.

## 4. const & valeur/référence

- `const int* p` — pointeur vers const (donnée protégée) ; `int* const p` — pointeur const (adresse figée) ; `const int* const p` — les deux. Lire **de droite à gauche**.
- Méthode `const` : ne modifie pas l'objet ; seule appelable sur un objet `const`.
- Passage : gros objets → `const T&` ; à modifier → `T&` ; petits types (int, double, pointeurs) → valeur.
- `constexpr` : évaluable à la compilation. `const` : non modifiable (mais initialisable à l'exécution).

## 5. Initialisation — pièges garantis

- **Les membres sont initialisés dans l'ordre de leur déclaration dans la classe, PAS dans l'ordre de la liste d'initialisation.** QCM classique avec un membre initialisé à partir d'un autre.
- Variable locale non initialisée (`int x;`) = **valeur indéterminée** (UB si lue), contrairement à C# / Python.
- `static` local : initialisé **une seule fois**, au premier passage, thread-safe depuis C++11.
- `sizeof` d'une classe vide = **1** (jamais 0).

## 6. STL — complexités & invalidation

| Conteneur | Accès | Insertion | Recherche |
| --- | --- | --- | --- |
| `vector` | O(1) | O(1) amorti en fin ; O(n) ailleurs | O(n) |
| `map` (arbre) | — | O(log n) | O(log n), **trié** |
| `unordered_map` (hash) | — | O(1) moyen | O(1) moyen, **non trié** |
| `list` | O(n) | O(1) | O(n) |

- **Invalidation d'itérateurs** : `push_back` sur un `vector` peut **réallouer → tous les itérateurs/pointeurs invalidés**. Effacer dans une boucle : `it = v.erase(it);` (erase retourne l'itérateur suivant).
- `v[i]` ne vérifie pas les bornes (UB hors bornes) ; `v.at(i)` lance `std::out_of_range`.
- `map::operator[]` **insère une valeur par défaut si la clé est absente** — piège pour compter/tester la présence. Utiliser `find` ou `count`.
- Algorithmes : `std::sort` (O(n log n)), `std::find`, `std::accumulate`, lambdas comme comparateurs.

## 7. Concurrence

- **Data race** = deux threads accèdent à la même donnée, dont au moins une écriture, sans synchronisation → **UB**.
- `std::mutex` + `std::lock_guard` (RAII : déverrouillage automatique) ; `std::unique_lock` si besoin de flexibilité.
- `std::atomic<int>` pour compteurs simples sans mutex.
- **Deadlock** : deux mutex pris dans un ordre différent par deux threads. Réponse QCM : ordre d'acquisition constant ou `std::scoped_lock(m1, m2)`.

## 8. Divers à réponse rapide

- `++i` vs `i++` : préfixe n'a pas besoin de copie temporaire — préférer `++i` sur les itérateurs.
- Références : doivent être initialisées, ne peuvent pas être « nulles » ni rebindées.
- Surcharge résolue à la compilation ; redéfinition (`virtual`) à l'exécution.
- `nullptr` (typé) préféré à `NULL`/`0`.
- Une `struct` ≡ une `class` avec membres **publics** par défaut — seule différence.
- Exceptions : détruire les objets locaux pendant le déroulement de pile (stack unwinding) — d'où l'importance du RAII ; un destructeur ne doit **jamais** lancer d'exception.
- Templates : instanciés à la compilation ; erreur seulement si le code est effectivement instancié.

## 9. Micro-drills (à refaire J5)

1. Pourquoi ce code fuit-il ? → deux `shared_ptr` en cycle.
2. Que vaut `d` après `Base b = derived;` puis appel virtuel ? → slicing, version Base.
3. `std::move(x)` sur un `const T` ? → move impossible, retombe sur la **copie** (piège fin).
4. Effacer les éléments pairs d'un `vector` dans une boucle sans UB.
5. Écrire une classe RAII minimale autour d'un `FILE*`.
