# Stratégie de candidature — eCential Robotics, Ingénieur Développement Logiciel C++ (BU Spine)

**Poste :** Ingénieur Développement Logiciel C++ BU Spine · CDI · Gières (proche Grenoble)
**Annonce :** voir `Annonce - eCential Robotics C++ Spine.md` (même dossier)
**Candidat :** Sébastien Albert — Lyon · C++ · temps réel · vision par ordinateur · IHM · 3D

---

## 1. Verdict de pertinence

**Le meilleur fit technique du lot actuel — mais la contrainte géographique est la plus dure.**

- **Fit technique excellent** : C++ moderne, CMake, Git, **géométrie 3D / transformations rigides / changements de repère** (cœur du métier de 15 ans de 3D temps réel), tests, design patterns, UML. La demande centrale de l'annonce — « modéliser et manipuler les transformations rigides et les changements de repère en 3D » — est une compétence **rare** que Sébastien possède nativement, là où beaucoup de devs C++ ne l'ont pas.
- **Domaine** : robotique chirurgicale = imagerie + temps réel + 3D + impact humain. Aligne parfaitement le récit « vision industrielle → simulation 3D → retour au dev produit à impact ».
- **Géographie** : Gières (38), campus de Grenoble. Depuis Lyon : ~1h30–1h45 en train (Part-Dieu → Grenoble + tram) ou ~1h20 en voiture hors bouchons. **Nettement hors du critère 45 min.** Télétravail non précisé dans l'annonce. → Poste crédible seulement avec un vrai volet télétravail ou un déménagement — à clarifier en premier échange.
- **Calibrage** : « jeunes diplômés bienvenus » → l'annonce ratisse du junior au confirmé ; risque de budget bas (voir §6).
- **Vigilance entreprise** : eCential Robotics a traversé des difficultés financières (procédure de redressement évoquée dans la presse en 2024). **Vérifier la situation actuelle** (societe.com, presse locale Dauphiné/Les Échos) avant d'investir du temps — et poser la question du financement en entretien.

**Estimation : dossier à préparer si (télétravail OU mobilité Grenoble) et (santé financière confirmée).** Techniquement, c'est la candidature la plus défendable du pipeline.

---

## 2. Forces à mettre en avant (toutes vérifiables)

| Atout | Preuve concrète | Pourquoi ça compte pour eCential |
| --- | --- | --- |
| **Géométrie 3D, transformations, repères** | 15 ans de 3D temps réel (Unity, simulateur SNCF) : matrices, quaternions, hiérarchies de repères au quotidien | **Exigence centrale et différenciante de l'annonce** |
| **C++ moderne, STL, CMake, Git** | PRESI (C++/OpenCV), enseignement C++ quotidien, CMake pratiqué | Socle outillage demandé, couvert |
| **Vision par ordinateur / imagerie** | PRESI : mesure micrométrique, traitement d'image C++/OpenCV | Produit eCential = imagerie 2D/3D + navigation ; passerelle directe |
| **Temps réel / systèmes interactifs** | Gebo (supervision temps réel), simulateur SNCF, IHM opérateur | « Navigation en temps réel », intégration robotique |
| **IHM** | Interfaces opérateur industrielles + 3D interactive | « Concevoir des interfaces utilisateur en Qt » — paradigmes acquis, API à apprendre |
| **Design patterns, architecture, UML** | Enseignement de l'architecture logicielle, projets modulaires (Event Bus, machines à états) | « Architecture distribuée, design patterns, UML » |
| **Qualité, revues, pédagogie du code** | Enseignant : revues de code, exigence de code clair et testé | « Code clair, maintenable et testé », revues de code |
| **Attrait médical sincère** | Continuité PRESI (mesure scientifique) → chirurgie | « Attiré par le domaine médical et les projets à fort impact humain » |
| **Anglais professionnel** | SAE Genève, documentation | Exigé |

---

## 3. Écarts réels et stratégie de compensation

> **Règle d'or : ne jamais revendiquer une compétence non maîtrisée.**

| Écart | État réel | Compensation |
| --- | --- | --- |
| **Qt6** | Non pratiqué | Paradigmes IHM acquis ; démonstrateur Qt à amorcer (mutualisable avec Amplitude) |
| **Google Test** | Framework non pratiqué | Culture tests unitaires réelle ; GTest = syntaxe, pas concept |
| **CI/CD (Jenkins/GitLab CI)** | Non pratiqué | Git maîtrisé ; CI = surcouche outillage, apprentissage court |
| **Normes IEC 62304 / ISO 14971** | Non pratiquées | Rigueur industrielle + posture d'apprentissage ; les normes s'apprennent en poste |
| **CUDA / DICOM / IPC** | Non | Explicitement « bonus » — OpenGL/GPU : concepts 3D déjà là |

**Leviers :** re-skilling prouvé (4 pivots) · le cœur dur (C++ + math 3D) est couvert, les écarts sont périphériques · repositionnement « ingénieur logiciel 3D temps réel », l'enseignement comme preuve de maîtrise des fondamentaux.

---

## 4. Mots-clés ATS

`C++ moderne` · `STL` · `CMake` · `Git` · `transformations rigides` · `changements de repère` · `géométrie 3D` · `algèbre linéaire` · `temps réel` · `IHM` · `Qt` (posture) · `design patterns` · `UML` · `tests unitaires` · `traitement d'image` · `OpenCV` · `imagerie` · `navigation`.

---

## 5. Actions concrètes recommandées

1. **Vérifier la santé financière d'eCential** (presse 2024–2026, societe.com) — préalable.
2. **Démonstrateur Qt + 3D** (mutualisé avec Amplitude) : petit visualiseur Qt/OpenGL manipulant des repères 3D (par ex. chaîne de transformations outil→patient→image, thème navigation chirurgicale). Coche Qt + illustre exactement la compétence centrale de l'annonce.
3. **Réseau** : chercher des contacts eCential / ex-eCential sur LinkedIn (bassin grenoblois très maillé).

---

## 6. Fourchette salariale (analyse)

- **Calibrage annonce** : « jeunes diplômés bienvenus » → bas de fourchette probable **38–42 K€** ; profil confirmé : **45–52 K€** ; senior : jusqu'à 55–58 K€ sur le bassin grenoblois medtech/robotique (marché tendu sur C++/3D).
- **Contexte entreprise** : si les difficultés financières se confirment, le budget salarial peut être contraint — un argument de plus pour vérifier avant.
- **Cible Sébastien (50–52 K€)** : défendable ici, car la compétence géométrie 3D + C++ est exactement leur cœur et rare sur le marché ; à positionner comme « confirmé/senior immédiatement productif sur la partie math 3D ».
- **Position de négociation** : 50–52 K€ annoncés, plancher à définir selon télétravail (un fort télétravail peut justifier de la souplesse).

---

## 7. Checklist

- [ ] Vérifier santé financière eCential (presse, societe.com)
- [ ] Clarifier politique télétravail (candidature ou premier échange)
- [ ] Trancher la question Grenoble
- [ ] Dupliquer `_modeles/cv-industrie.html` → `cv-ecential.html` (accent : math 3D, C++, imagerie, tests)
- [ ] Finaliser la lettre (`Lettre-motivation-eCential.md` → HTML → PDF)
- [ ] (Option) Démonstrateur Qt/3D (§5)
- [ ] Déposer + consigner dans `_suivi.md`
