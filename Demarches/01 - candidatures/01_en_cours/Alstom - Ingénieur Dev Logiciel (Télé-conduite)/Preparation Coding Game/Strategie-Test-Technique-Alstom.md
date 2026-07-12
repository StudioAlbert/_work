# Stratégie — Test technique Alstom (QCM + problème de code)

> Suite de l'entretien du 2026-07-10 avec David Gelin (V&V). Complète [[Argumentaire-entretien-Alstom]] et [[Glossaire-technique-Alstom]].
> **Topics annoncés :** Git · Docker · React · Node.js · C++ · Python. Format : **QCM + problème de code**.
> **Hypothèse de départ actée : Python et Docker partent de zéro en pratique** (le démonstrateur existe mais n'a pas encore été pris en main).
> Fiches liées : [[Cheatsheet-Cpp-Alstom]] · [[Cheatsheet-Python-Alstom]] · [[Cheatsheet-Git-Alstom]] · [[Cheatsheet-Docker-Test-Alstom]] · [[Cheatsheet-React-Alstom]] · [[Cheatsheet-NodeJS-Alstom]]

---

## 1. Lecture stratégique — révisée

Ce test vérifie le discours tenu en entretien : « C++ solide, Git quotidien, **Python/Docker en montée en compétence active** ». Point de vigilance franc : le démonstrateur a été présenté comme prêt. **Un score très faible en Python/Docker contredirait ce discours** — c'est le risque n°1 du test, davantage que React/Node (jamais revendiqués). D'où la hiérarchie suivante :

| Topic | Situation réelle | Score cible | Effort semaine |
| --- | --- | --- | --- |
| **C++** | Socle (25 ans) | **Excellent** | Révision anti-pièges — ½ journée |
| **Git** | Quotidien | **Excellent** | Révision anti-pièges — ½ journée |
| **Python** | **Zéro pratique** (C#/C++ en appui) | **Correct/fonctionnel** | **Apprentissage n°1 — ~2 jours, mains sur le clavier** |
| **Docker** | **Zéro pratique** (démonstrateur dispo) | **Notions solides** | **Apprentissage n°2 — ~1 jour, TP sur le démonstrateur** |
| **Node.js** | Notions JS | Plancher assumé | Lecture fiche — 2-3 h |
| **React** | Notions JS | Plancher assumé | Lecture fiche — 2-3 h |

**Arbitrage assumé :** React/Node sont sacrifiés au profit de Python/Docker. Un score moyen partout sur le front JS est cohérent (jamais revendiqué) ; un score nul en Python ne l'est pas.

**Le démonstrateur change de statut : il devient ton TP.** Le faire tourner (`docker compose up`), lire son `docker-compose.yml`, ses `Dockerfile`, son code Python, le casser et le réparer — c'est la voie la plus rapide vers un vrai vécu Python/Docker, et ça transforme rétroactivement « prêt » en « pratiqué ».

## 2. Planning (5 jours utiles)

| Jour | Matin (~3 h) | Après-midi (~2-3 h) |
| --- | --- | --- |
| **J1** | **Python §0-§4** : installer, REPL, écrire les 5 scripts de démarrage de la fiche | Python : structures, fonctions + 3 katas faciles (Exercism/CodinGame) |
| **J2** | **Python** : pièges, classes, exceptions + 3 katas | **Docker §0** : installer, hello-world, premiers `run/exec` |
| **J3** | **Docker TP démonstrateur** : `compose up`, lire les Dockerfile, modifier/reconstruire | Git — révision pièges (fiche) + C++ 1re passe |
| **J4** | C++ — pièges + 2 problèmes chronométrés **en C++** | Node.js puis React — lecture fiches, drills uniquement |
| **J5** | 2 problèmes chronométrés (C++, option 1 en Python si à l'aise) | Relecture des 6 fiches (sections pièges) — rien de neuf |

## 3. Problème de code : C++ par défaut

- **Si le langage est libre : C++.** Cinq jours ne suffisent pas pour coder sous chrono dans un langage parti de zéro — la vitesse et la sûreté priment. Python reste l'objectif d'apprentissage de la semaine, pas l'outil du jour J.
- Si Python est **imposé** : la fiche §9 (boîte à outils) donne le minimum vital ; viser une solution simple et correcte, pas idiomatique.
- Méthode (inchangée) : lire l'énoncé deux fois → entrées/sorties/contraintes → cas limites (vide, 1 élément, doublons, négatifs) → solution naïve qui passe les exemples → optimiser si temps → tester avant de soumettre. Code lisible : si un humain relit (probable côté V&V), c'est un critère.

## 4. Tactique QCM

- Deux passages : d'abord tout ce qui est sûr, marquer le reste.
- **Barème** : vérifier s'il y a des points négatifs dès réception du lien. Si oui : ne pas deviner sur React/Node ; si non : toujours répondre après élimination.
- Lire jusqu'au bout : « laquelle est FAUSSE », « toutes sauf », pluriels (réponses multiples).
- Chaque fiche a sa section « Pièges QCM » : si une question ressemble à un piège recensé, c'en est probablement un.
- Ne jamais dépasser 2× le temps moyen par question.

## 5. Cohérence avec le discours d'entretien

- Résultat visé : **fort en C++/Git, correct en Python, notions réelles en Docker, moyen en React/Node** — exactement le profil « socle solide + montée en compétence engagée ».
- Si un debrief suit le test, la formulation reste celle de l'argumentaire : montée en compétence **en cours** — et grâce au TP de la semaine, elle sera vraie en pratique, pas seulement sur le papier. La règle d'or ne change pas : ne rien revendiquer au-delà du réel.
- Front web : « React/Node ne sont pas mon terrain actuel — mais c'est de l'event-driven et du composant, des modèles que je pratique sous d'autres formes depuis des années. »

## 6. Checklist logistique

- [ ] Dès réception du lien : identifier la **plateforme** (CodinGame for Work, TestGorilla, HackerRank…) et s'échauffer sur ses exemples publics.
- [ ] Vérifier **durée, barème** (points négatifs ?), langue, et si le problème de code impose un langage.
- [ ] Installer Python 3 + Docker Desktop dès J1 (prérequis des TP).
- [ ] Cloner/mettre à jour `demonstrateur-teleconduite` pour le TP de J3.
- [ ] Jour J : poste fixe, connexion stable, silence ; kata d'échauffement 30 min avant. La veille : relecture pièges uniquement.
