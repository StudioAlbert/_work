---
description: Synchronise les tags `#envoye` des tâches Candidatures Lyon avec l'état réel des emails Gmail
allowed-tools: Read, Edit, mcp__62e47751-8da3-48b9-bc93-f5151a588eaa__search_threads, mcp__62e47751-8da3-48b9-bc93-f5151a588eaa__get_thread
---

# Sync Gmail → CardBoard

Synchronise l'état des tâches du fichier `Tasks/candidatures-ecoles-lyon.md` (et tout autre fichier de `Tasks/` listant des destinataires) avec l'état réel de la boîte Gmail connectée.

## Règle de transition

Pour chaque tâche contenant une adresse email :

| Dernier message dans le thread Gmail | État de la tâche |
|---|---|
| Aucun message échangé | `NOT_SENT` — laisser tel quel (pas de `#envoye`) |
| Dernier message est **de moi** vers l'école (`in:sent`) | `WAITING` — la tâche doit porter le tag `#envoye` |
| Dernier message est **de l'école** vers moi (`in:inbox`) | `REPLIED` — retirer `#envoye` (retour en To do, action à prendre) |

## Procédure

1. **Lire** `Tasks/candidatures-ecoles-lyon.md`.

2. **Extraire** pour chaque ligne de tâche (`- [ ] ...`) les adresses email avec la regex `[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}`. Ignorer les tâches sans email (préparation, LinkedIn génériques, relances).

3. **Pour chaque adresse email unique** trouvée, lancer en **parallèle** (un seul message, plusieurs tool calls) :
   - `search_threads` avec query : `to:<email> in:sent` (pageSize 3)
   - `search_threads` avec query : `from:<email> in:inbox` (pageSize 3)

4. **Décider l'état** de chaque adresse :
   - Si les deux résultats sont vides → `NOT_SENT`
   - Si seul `in:sent` a un résultat → `WAITING`
   - Si `in:inbox` a un résultat → comparer les dates du message le plus récent de chaque recherche. Si le plus récent vient de `in:inbox` → `REPLIED`. Sinon → `WAITING` (j'ai relancé après leur réponse).

5. **Appliquer les modifications** au markdown via `Edit` :
   - `WAITING` et la ligne ne contient pas `#envoye` → insérer ` #envoye` juste après le dernier tag existant de la ligne (ex. après `#gamagora`).
   - `REPLIED` et la ligne contient `#envoye` → retirer ` #envoye` (avec l'espace devant pour ne pas laisser de double espace).
   - `NOT_SENT` → ne rien faire.

6. **Rapport final** sous forme de tableau markdown :

   ```
   | École | Email | État | Action |
   |---|---|---|---|
   | Gamagora (Puzenat) | didier.puzenat@univ-lyon2.fr | WAITING | + #envoye |
   | Gaming Campus | contact@gamingcampus.fr | NOT_SENT | — |
   | ... | ... | ... | ... |
   ```

   Plus un récap : `X tâches passées en Doing, Y tâches revenues en To do, Z inchangées.`

## Garde-fous

- Ne touche **jamais** aux autres tags (`#lyon`, `#gamagora`, `#bellecour`, etc.).
- Ne touche **jamais** à la date (`📅 YYYY-MM-DD`).
- Ne coche **jamais** la case `[ ]` → `[x]` (réservé à l'utilisateur, marque la fin complète de la démarche).
- Si une recherche Gmail renvoie une erreur d'authentification → arrête et signale-le clairement (ne modifie rien).
- Si une même adresse apparaît dans plusieurs tâches (ex. les deux variantes Gamagora ont des destinataires différents — pas le cas ici, mais en général), traite chaque tâche indépendamment.

## Format attendu de tag dans une tâche

Une tâche bien tagguée avec `#envoye` ressemble à :
```
- [ ] #lyon #gamagora #envoye Envoyer email — Variante A : ... 📅 2026-06-08
```

Le tag `#envoye` est placé **entre les autres tags et le corps de la tâche**.
