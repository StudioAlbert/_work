# Cheatsheet Git — Test technique Alstom

> **Enjeu : points quasi gratuits, à sécuriser à 100 %.** Tu pratiques quotidiennement — cette fiche cible uniquement les zones où les QCM piègent même les utilisateurs réguliers.
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 1. Modèle mental (questions de cours)

- Trois zones : **working directory → staging area (index) → repository**. `add` déplace vers l'index, `commit` fige l'index.
- Un commit = snapshot complet (pas un diff) + pointeur(s) parent(s) ; identifié par un SHA-1.
- **HEAD** = pointeur vers le commit courant (via une branche, normalement). **Detached HEAD** = HEAD pointe directement un commit (après `checkout <sha>`) — les commits faits là sont perdables si on repart sans créer de branche.
- Une **branche** n'est qu'un pointeur mobile vers un commit — création quasi gratuite. Réponse QCM récurrente.
- `origin` = nom par défaut du remote ; `origin/main` = **branche de suivi locale**, mise à jour par `fetch`, pas en temps réel.

## 2. Les trios pièges

### `reset` --soft / --mixed / --hard
| Option | HEAD | Index | Working dir |
| --- | --- | --- | --- |
| `--soft` | déplacé | conservé | conservé |
| `--mixed` (défaut) | déplacé | **réinitialisé** | conservé |
| `--hard` | déplacé | réinitialisé | **écrasé — travail non commité PERDU** |

### `reset` vs `revert` vs `checkout`
- `reset` : **déplace la branche** en arrière → réécrit l'historique. Interdit sur une branche partagée déjà poussée.
- `revert` : crée un **nouveau commit** qui annule un commit précédent → historique préservé. **La bonne réponse pour annuler sur une branche partagée.**
- `checkout <fichier>` / `git restore <fichier>` : écrase les modifications locales du fichier (perte).

### `fetch` vs `pull`
- `fetch` : télécharge sans toucher à la branche locale.
- `pull` = `fetch` + `merge` (ou + `rebase` avec `--rebase`). QCM classique : « quelle commande met à jour sans modifier ma branche ? » → `fetch`.

## 3. merge vs rebase

- **merge** : commit de fusion à 2 parents ; historique fidèle mais non linéaire. **Fast-forward** si la branche cible n'a pas divergé : simple déplacement de pointeur, aucun commit créé (`--no-ff` pour forcer un commit de merge).
- **rebase** : rejoue les commits sur une nouvelle base → historique **linéaire** mais **réécrit** (nouveaux SHA).
- **Règle d'or (question quasi certaine)** : ne jamais rebaser des commits **déjà poussés et partagés**.
- Conflit : marqueurs `<<<<<<<` / `=======` / `>>>>>>>` ; résoudre, `add`, puis `merge --continue` ou `rebase --continue`.

## 4. Commandes de rattrapage — différenciantes en QCM

- `git reflog` : journal des positions de HEAD → **récupérer un commit « perdu »** après un reset --hard ou un rebase raté. LA réponse aux questions « comment récupérer… ».
- `git stash` / `stash pop` / `stash list` : mettre de côté le travail en cours.
- `git cherry-pick <sha>` : appliquer un commit isolé sur la branche courante.
- `git bisect` : recherche dichotomique du commit qui a introduit un bug.
- `git blame <fichier>` : qui a modifié chaque ligne.
- `git commit --amend` : corriger le dernier commit (réécrit le SHA → même interdit qu'un rebase si déjà poussé).

## 5. Pièges divers à connaître

- Un fichier **déjà suivi** ajouté ensuite au `.gitignore` reste suivi → `git rm --cached <fichier>`.
- `HEAD~2` = 2 commits en arrière (1er parent) ; `HEAD^` = 1er parent ; `HEAD^2` = **2e parent d'un merge** (≠ `HEAD~2`, piège fin).
- `git push --force` écrase le remote (danger) ; `--force-with-lease` refuse si quelqu'un a poussé entre-temps — la « bonne » réponse moderne.
- `git tag` : léger (pointeur) vs annoté `-a` (objet avec message/date) ; les tags ne sont poussés qu'avec `--tags` ou explicitement.
- `git clone` copie tout l'historique ; `--depth 1` = shallow clone.
- `.git/` supprimé = plus de dépôt ; les fichiers de travail restent.
- `git diff` = working vs index ; `git diff --staged` = index vs HEAD.

## 6. Workflows (questions de culture)

- **Git Flow** : branches `main`/`develop` + `feature/`, `release/`, `hotfix/`.
- **GitHub/GitLab Flow** : branches courtes depuis `main` + merge/pull request + CI. Lien direct avec la pipeline GitLab CI de ton démonstrateur — voir [[Glossaire-technique-Alstom]] §2.
- Une **merge request** déclenche typiquement la CI (build, lint, tests) avant intégration.

## 7. Micro-drills (à refaire J5)

1. Annuler le dernier commit **poussé** sans réécrire l'historique → `revert`.
2. Récupérer une branche supprimée par erreur → `reflog` + `branch <nom> <sha>`.
3. Différence exacte des trois `reset` — réciter le tableau.
4. `HEAD~2` vs `HEAD^2` — expliquer.
5. Pourquoi `pull` peut créer un commit de merge inattendu et comment l'éviter (`pull --rebase` / `pull --ff-only`).
