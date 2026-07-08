# Suivi des candidatures

Tableau de bord unique de mes candidatures (industrie / logiciel). Source de vérité manuelle — pas de plugin requis.

> **Convention**
> - **Une ligne par candidature** dans le tableau ci-dessous ; on y met l'état *courant*.
> - **Chaque événement daté** (dépôt, relance, réponse, entretien…) va dans le **Journal** en bas, avec la date du jour au format `YYYY-MM-DD`.
> - **Statuts** : `À postuler` · `En attente` · `Déposée` · `Relancée` · `Entretien` · `Offre` · `Refus` · `Sans réponse` · `Abandonnée`.
> - **Prochaine action** : porter une date `📅 YYYY-MM-DD` pour ne rien oublier (relance ~J+10 par défaut).
> - **Rangement** : `00_to_process/` = annonces à traiter · `01_en_cours/` = candidatures **déposées** · `02_en attente/` = en attente / à postuler · `03_terminees/` = candidatures **closes** (refus, sans réponse actés, abandonnées).

## Tableau de bord

| Entreprise | Poste | Prio | Statut | Déposée le | Canal | Prochaine action | Dossier |
|---|---|---|---|---|---|---|---|
| **Abylsen (ST/RA)** | Lead Dev C++/C# | 2 | Déposée | 2026-06-24 | Portail Abylsen (LinkedIn) + message recruteur | Relancer 📅 2026-07-04 | [[Strategie-Abylsen]] |
| **Effektiv → PRIM'X** | Dev Senior C/C++ | 1 | Déposée | 2026-06-25 | Formulaire Hellowork + message | Attendre retour Marguerite (répondu 2026-07-01) · Relancer si sans nouvelles 📅 2026-07-08 | [[Strategie-Effektiv-PRIMX]] |
| **Alstom** | Ing. Dev Logiciel (Télé-conduite) | — | **Entretien** | 2026-06-25 | Jobsite Alstom (Req 501727) | 🎥 Entretien Teams **confirmé 📅 2026-07-10** — D. Gelin (V&V) · prépa [[Argumentaire-entretien-Alstom]] · [[Glossaire-technique-Alstom]] · [[Remuneration-marche-Alstom]] · démonstrateur prêt | [[Strategie-Alstom]] |
| **Adsearch** | Lead Dev C++ | 3 | En attente | — | Hellowork + réseau consultant | En attente | [[Strategie-Adsearch]] |
| **LR Technologies** | Dev C++ | 4 | En attente | — | Hellowork (ESN) | En attente (arbitrer LR/Caveo) | [[Strategie-LR-Technologies]] |
| **Caveo Consulting** | Dev C/C++ | 5 | En attente | — | Hellowork (ESN) | En attente (arbitrer LR/Caveo) | [[Strategie-Caveo]] |
| **Externatic** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Externatic (externatic.fr) | Relancer 📅 2026-07-10 | [[message-externatic]] |
| **Skaelia** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Skaelia (skaelia.com) | Relancer 📅 2026-07-10 | [[message-skaelia]] |
| **Silkhom** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Silkhom (silkhom.com) | Relancer 📅 2026-07-10 | [[message-silkhom]] |
| **Seyos** | Candidature spontanée | — | Refus | 2026-06-30 | Site Seyos (seyos.fr) | — (clos 2026-07-06 · dossier `03_terminees/`) | [[message-seyos]] |
| **Amplitude** | Ing. Dev Logiciel C++ (Valence) | — | Déposée | 2026-07-03 | Portail Amplitude | Relancer 📅 2026-07-13 | [[Strategie-Amplitude]] |
| **eCential Robotics** | Ing. Dev C++ BU Spine (Gières) | — | Déposée | 2026-07-03 | Portail eCential | Relancer 📅 2026-07-13 · Vérifier santé financière | [[Strategie-eCential]] |
| **Licorne Society** | Candidature spontanée | — | À postuler | — | Site Licorne (licornesociety.com) | ⚠️ Site buggé — retenter le dépôt 📅 2026-07-01 | [[message-licorne-society]] |

### Volet enseignement — écoles de jeu vidéo (Lyon)

| École | Rôle visé | Statut | Contactée le | Canal | Prochaine action | Dossier |
|---|---|---|---|---|---|---|
| **Gamagora** (Univ. Lyon 2) | Intervenant prog/IA (M2 & LP) | Relancée | 2026-06-12 | Email responsables (Puzenat / Kerautret) | Relancée 2026-07-03 — attendre retour 📅 2026-07-13 | [[candidatures-ecoles-jeu-video-lyon]] |
| **Gaming Campus — G. Tech** | Intervenant prog + coordination | Déposée | 2026-06-12 | contact@gamingcampus.fr | Relancer 📅 2026-07-06 | [[candidatures-ecoles-jeu-video-lyon]] |
| **Bellecour École** | Intervenant prog/IA (retour) | En attente | 2026-06-12 | LinkedIn (M. Huliack) puis J. Saudemont | Réponse d'attente positive 2026-06-22 (besoins rentrée à l'étude) — relancer 📅 2026-08-24 si sans nouvelles | [[candidatures-ecoles-jeu-video-lyon]] |
| **E-Artsup** | Intervenant prog / creative coding (retour) | Déposée | 2026-06-12 | Campus Lyon / IONIS | Relancer 📅 2026-07-06 | [[candidatures-ecoles-jeu-video-lyon]] |

> ⚠️ **LR / Caveo** : annonces quasi identiques, probable même client final via deux ESN → n'en retenir qu'**une**. Voir [[Strategie-00-lot-Cpp-Lyon]].
>
> 📨 **Candidatures spontanées (Externatic, Skaelia, Silkhom, ~~Seyos~~ (refus 2026-07-06), Licorne Society)** : prises de contact recruteurs IT lyonnais pour décrocher un échange autour du pivot enseignement → ingénieur C++/temps réel. Dossiers `01_en_cours/<Cabinet> - Candidature spontanée/` (message + lettre HTML/PDF). Gabarits réutilisables dans `_modeles/` (`message-spontanee-recruteur.md`, `lettre-spontanee-recruteur.md`).

## Journal des événements

### 2026-06-12
- **Gamagora · E-Artsup · Gaming Campus** — Candidatures spontanées d'intervenant envoyées (emails cf. [[candidatures-ecoles-jeu-video-lyon]]). → Statut **Déposée**.
- **Bellecour École** — Prise de contact via LinkedIn avec **Mehdi Huliack**.

### 2026-06-19
- **Bellecour École** — Relance vers **Julie Saudemont**.

### 2026-06-22
- **Bellecour École** — **Réponse d'attente positive** de Julie Saudemont (Directrice Adjointe) : profil « a retenu toute notre attention » (enseignement + coordination Games Programming, C#/Unity, gameplay/IA) ; les besoins pédagogiques de la prochaine rentrée sont à l'étude, ils reviendront vers moi si opportunité. → Statut **En attente**. Relancer 📅 2026-08-24 si sans nouvelles. Email archivé dans `01_en_cours/Bellecour École - Intervenant Prog & IA jeu vidéo/`.

### 2026-06-24
- **Abylsen** — Candidature déposée via le portail (offre LinkedIn). Message personnalisé au recruteur ajouté (angle double stack C++/C# + ferroviaire / simulateur SNCF). → Statut **Déposée**. Relance prévue 📅 2026-07-04.

### 2026-06-25
- **Alstom** — Candidature déposée (jobsite Alstom, Req 501727). → Statut **Déposée**. Relance prévue 📅 2026-07-05.
- **Adsearch · LR Technologies · Caveo** — Mises **En attente** (focus sur Abylsen, Alstom et Effektiv). À réactiver ensuite.
- **Effektiv → PRIM'X** — Message recruteur finalisé ([[Message-recruteur-Effektiv]]). Prêt à postuler.
- **Abylsen** — Message recruteur consigné ([[Message-recruteur-Abylsen]]).
- **Effektiv → PRIM'X** — Candidature déposée (formulaire Hellowork + [[Message-recruteur-Effektiv|message recruteur]]). → Statut **Déposée**. Relance prévue 📅 2026-07-05 (recruteur annoncé réactif ≤ 15 j).

### 2026-06-30
- **Candidatures spontanées — recruteurs IT Lyon** — Préparation et envoi d'un lot de 5 candidatures spontanées (message court + lettre HTML/PDF) à des cabinets IT lyonnais, angle pivot enseignement → ingénieur C++/temps réel. Contenus réorganisés en dossiers dédiés `<Cabinet> - Candidature spontanée/` (nomenclature alignée sur Abylsen, etc.) ; gabarits déplacés dans `_modeles/`.
  - **Externatic, Skaelia, Silkhom, Seyos** — Déposées. → Statut **Déposée**. Relance prévue 📅 2026-07-10.
  - **Licorne Society** — Dépôt **non abouti** (site du cabinet buggé). → Statut **À postuler**. Retenter 📅 2026-07-01.

### 2026-07-03
- **Amplitude · eCential Robotics** — Candidatures **déposées** sur les portails des deux entreprises (CV industrie + lettre). → Statut **Déposée**. Relance prévue 📅 2026-07-13. Dossiers déplacés dans `01_en_cours/`.
- **Gamagora** — **Relance** de la candidature d'intervenant (M2 Ingénierie JV / LP Métiers du Jeu Vidéo). → Statut **Relancée**. Attendre retour 📅 2026-07-13.
- **Volet enseignement jeu vidéo** — Les candidatures écoles de jeu vidéo (Gamagora, Gaming Campus, Bellecour, E-Artsup — cf. [[candidatures-ecoles-jeu-video-lyon]]) intègrent le pipeline de suivi habituel : nouvelle section « Volet enseignement » dans le tableau de bord ci-dessus.
- **Réseau** — Prise de contact avec **Manel** (voisine de palier, gestionnaire de projets) et **Romain Seraphine** (ami, product owner) : relais potentiels pour le pivot vers l'industrie (conseils, mise en relation).
- **Amplitude (Valence) · eCential Robotics (Grenoble)** — Analyse stratégique des 2 annonces de `00_to_process/` : dossiers créés avec `Strategie-*.md` + proposition de lettre. Points bloquants à trancher avant dépôt : **géographie** (Valence ~1h05 TER, Gières ~1h30 — hors critère 45 min) et, pour eCential, **santé financière à vérifier** (difficultés évoquées en 2024). → Restent en `00_to_process/` en attendant arbitrage.
- **Rangement** — Les 7 dossiers de candidatures **déposées** (Abylsen, Effektiv/PRIM'X, Alstom, Externatic, Skaelia, Silkhom, Seyos) déplacés dans `01_en_cours/`. Les 4 dossiers en attente / à postuler (Adsearch, LR Technologies, Caveo, Licorne Society) déplacés dans `02_en attente/`. Chemins `../_assets/` des HTML corrigés en `../../_assets/`.

### 2026-07-01
- **Effektiv → PRIM'X** — Marguerite De Pury (recruteuse Effektiv) relance par email pour qualifier la candidature : poste recherché, XP, stack technique, rémunération, mobilité/télétravail, disponibilité/préavis. Réponse envoyée le jour même (15 ans+ XP, stack C++/C#/CMake/OpenCV, 50-52K€ brut, Lyon 8 mobile 45 min, hybride 2-3j télétravail, préavis 3 mois négociable). → Statut **Déposée** (échange en cours, pas encore d'entretien). Relance si sans nouvelles 📅 2026-07-08.

### 2026-07-06
- **Seyos** — **Refus** reçu par email de **Dorian Ribeiro De Abreu** (Référent - Consultant en recrutement, IT & Ingénierie industrielle). Message-type poli : « qualité du profil et parcours » saluée, mais « pas d'adéquation avec les besoins actuels de nos clients ». Invitation à re-postuler à l'avenir et à consulter régulièrement les offres seyos.fr. Délai de réponse rapide : ~6 jours (dépôt 2026-06-30 → réponse 2026-07-06). → Statut **Refus**. Dossier déplacé dans `03_terminees/Seyos - Candidature spontanée/` (nouveau répertoire pour candidatures closes). Email de refus archivé dans le dossier.
- **Rangement** — Création de `03_terminees/` pour les candidatures closes (refus, sans réponse actés, abandonnées). Convention de rangement mise à jour en tête du document.

### 2026-07-07
- **Alstom** — **Invitation à un entretien visio** reçue de **David GELIN (V&V Manager)** pour le poste *SW Engineer Remote Driving System* (Req 501727). Créneau initialement proposé : **08/07/2026 10h–10h30** sur **Microsoft Teams** (lien + code dans l'email). → Statut **Entretien**. Email archivé dans le dossier (`ALSTOM - Entretien visio - Sebastien Albert.eml`). Argumentaire préparé : [[Argumentaire-entretien-Alstom]].

### 2026-07-08
- **Alstom** — Entretien **reporté à vendredi 2026-07-10**, désormais **calé/confirmé**. Préparation produite dans le dossier : [[Argumentaire-entretien-Alstom]], **glossaire technique anti-piège** ([[Glossaire-technique-Alstom]]), **recherche rémunération marché** ([[Remuneration-marche-Alstom]] — cible ~48–55 K€ base, package grand groupe en plus) et **démonstrateur** Python/MQTT/Docker/CI (`demonstrateur-teleconduite/`) pour matérialiser la montée en compétence. Restant à faire côté Sébastien : tester le lien/matériel Teams, répéter l'argumentaire, préparer les 2 anecdotes clés (simulateur SNCF, mesure PRESI).

<!--
Modèle d'entrée à recopier :

### YYYY-MM-DD
- **<Entreprise>** — <ce qui s'est passé : dépôt / relance / réponse reçue / entretien planifié / refus…>. → <nouveau statut si changé>.
-->

---

## (Option) Suivi structuré par dossier

Si tu préfères garder l'historique **au plus près de chaque candidature** plutôt que centralisé ici, ajoute en tête du `Strategie-*.md` (ou d'un `Suivi-*.md`) un bloc frontmatter :

```yaml
---
entreprise: Abylsen
poste: Lead Dev C++/C#
statut: deposee        # a_postuler | deposee | relancee | entretien | offre | refus | sans_reponse | abandonnee
priorite: 2
date_candidature: 2026-06-24
canal: Portail Abylsen
prochaine_action: 2026-07-04
---
```

…puis un `## Journal` daté dans le même fichier. Avantage : si tu installes un jour **Dataview**, ou via **Bases** (fonction native d'Obsidian récent), tu pourras régénérer ce tableau de bord automatiquement à partir du frontmatter — sans rien ressaisir.
