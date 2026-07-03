# Suivi des candidatures

Tableau de bord unique de mes candidatures (industrie / logiciel). Source de vérité manuelle — pas de plugin requis.

> **Convention**
> - **Une ligne par candidature** dans le tableau ci-dessous ; on y met l'état *courant*.
> - **Chaque événement daté** (dépôt, relance, réponse, entretien…) va dans le **Journal** en bas, avec la date du jour au format `YYYY-MM-DD`.
> - **Statuts** : `À postuler` · `En attente` · `Déposée` · `Relancée` · `Entretien` · `Offre` · `Refus` · `Sans réponse` · `Abandonnée`.
> - **Prochaine action** : porter une date `📅 YYYY-MM-DD` pour ne rien oublier (relance ~J+10 par défaut).
> - **Rangement** : `00_to_process/` = annonces à traiter · `01_en_cours/` = candidatures **déposées** · `02_en attente/` = en attente / à postuler.

## Tableau de bord

| Entreprise | Poste | Prio | Statut | Déposée le | Canal | Prochaine action | Dossier |
|---|---|---|---|---|---|---|---|
| **Abylsen (ST/RA)** | Lead Dev C++/C# | 2 | Déposée | 2026-06-24 | Portail Abylsen (LinkedIn) + message recruteur | Relancer 📅 2026-07-04 | [[Strategie-Abylsen]] |
| **Effektiv → PRIM'X** | Dev Senior C/C++ | 1 | Déposée | 2026-06-25 | Formulaire Hellowork + message | Attendre retour Marguerite (répondu 2026-07-01) · Relancer si sans nouvelles 📅 2026-07-08 | [[Strategie-Effektiv-PRIMX]] |
| **Alstom** | Ing. Dev Logiciel (Télé-conduite) | — | Déposée | 2026-06-25 | Jobsite Alstom (Req 501727) | Relancer 📅 2026-07-05 | [[Strategie-Alstom]] |
| **Adsearch** | Lead Dev C++ | 3 | En attente | — | Hellowork + réseau consultant | En attente | [[Strategie-Adsearch]] |
| **LR Technologies** | Dev C++ | 4 | En attente | — | Hellowork (ESN) | En attente (arbitrer LR/Caveo) | [[Strategie-LR-Technologies]] |
| **Caveo Consulting** | Dev C/C++ | 5 | En attente | — | Hellowork (ESN) | En attente (arbitrer LR/Caveo) | [[Strategie-Caveo]] |
| **Externatic** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Externatic (externatic.fr) | Relancer 📅 2026-07-10 | [[message-externatic]] |
| **Skaelia** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Skaelia (skaelia.com) | Relancer 📅 2026-07-10 | [[message-skaelia]] |
| **Silkhom** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Silkhom (silkhom.com) | Relancer 📅 2026-07-10 | [[message-silkhom]] |
| **Seyos** | Candidature spontanée | — | Déposée | 2026-06-30 | Site Seyos (seyos.fr) | Relancer 📅 2026-07-10 | [[message-seyos]] |
| **Licorne Society** | Candidature spontanée | — | À postuler | — | Site Licorne (licornesociety.com) | ⚠️ Site buggé — retenter le dépôt 📅 2026-07-01 | [[message-licorne-society]] |

> ⚠️ **LR / Caveo** : annonces quasi identiques, probable même client final via deux ESN → n'en retenir qu'**une**. Voir [[Strategie-00-lot-Cpp-Lyon]].
>
> 📨 **Candidatures spontanées (Externatic, Skaelia, Silkhom, Seyos, Licorne Society)** : prises de contact recruteurs IT lyonnais pour décrocher un échange autour du pivot enseignement → ingénieur C++/temps réel. Dossiers `01_en_cours/<Cabinet> - Candidature spontanée/` (message + lettre HTML/PDF). Gabarits réutilisables dans `_modeles/` (`message-spontanee-recruteur.md`, `lettre-spontanee-recruteur.md`).

## Journal des événements

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
- **Rangement** — Les 7 dossiers de candidatures **déposées** (Abylsen, Effektiv/PRIM'X, Alstom, Externatic, Skaelia, Silkhom, Seyos) déplacés dans `01_en_cours/`. Les 4 dossiers en attente / à postuler (Adsearch, LR Technologies, Caveo, Licorne Society) déplacés dans `02_en attente/`. Chemins `../_assets/` des HTML corrigés en `../../_assets/`.

### 2026-07-01
- **Effektiv → PRIM'X** — Marguerite De Pury (recruteuse Effektiv) relance par email pour qualifier la candidature : poste recherché, XP, stack technique, rémunération, mobilité/télétravail, disponibilité/préavis. Réponse envoyée le jour même (15 ans+ XP, stack C++/C#/CMake/OpenCV, 50-52K€ brut, Lyon 8 mobile 45 min, hybride 2-3j télétravail, préavis 3 mois négociable). → Statut **Déposée** (échange en cours, pas encore d'entretien). Relance si sans nouvelles 📅 2026-07-08.

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
