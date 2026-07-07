# Stratégie de candidature — Amplitude, Ingénieur Développement Logiciel C++

**Poste :** Ingénieur(e) Développement Logiciel C++ F/H · R&D Développement technologies · Valence (26) · CDI
**Annonce :** voir `Annonce - Amplitude C++ Chirurgie.md` (même dossier)
**Candidat :** Sébastien Albert — Lyon · C++ · temps réel · vision par ordinateur · IHM

---

## 1. Verdict de pertinence

**Fit technique correct, mais deux points structurants à trancher avant de postuler :**

1. **Géographie** — Valence (26), télétravail 2 j/semaine seulement. Depuis Lyon 8 : ~1h05 en TER (Part-Dieu → Valence Ville) ou ~35 min en TGV (Part-Dieu → Valence TGV, mais gare TGV excentrée) ; ~1h15 en voiture. **Hors du critère « mobile 45 min »** annoncé à Effektiv. 3 j/semaine sur site = contrainte réelle. À arbitrer : abonnement TGV, ou hors périmètre.
2. **Séniorité ciblée** — l'annonce vise « idéalement 2 ans minimum » : c'est un poste calibré **junior/confirmé**, pas senior. Risque de décalage salarial (voir §6) et de sur-qualification perçue.

**Sur le fond technique :** C++ excellent fit, 3D temps réel solide, domaine médical très porteur pour le profil (continuité avec la vision industrielle PRESI). Écarts nets sur Qt/QML et OpenGL direct.

**Estimation : à postuler seulement si la contrainte Valence est acceptée.** Sinon, garder l'annonce comme référence de marché medtech.

---

## 2. Forces à mettre en avant (toutes vérifiables)

| Atout | Preuve concrète | Pourquoi ça compte pour Amplitude |
| --- | --- | --- |
| **C++ (exigence n°1)** | PRESI (C++/OpenCV), enseignement C++/SFML quotidien à SAE | « Excellente maîtrise du C++ » — pleinement couvert |
| **Développement 3D temps réel** | Simulateur 3D SNCF, 15 ans de moteurs temps réel (Unity), notions pipeline graphique | L'annonce demande du dev 3D (OpenGL) — les concepts (transformations, caméra, rendu, shaders) sont acquis, seule l'API diffère |
| **Traitement d'image / mesure de précision** | PRESI : mesure micrométrique, analyse métallurgique C++/OpenCV | Très proche des besoins d'imagerie en chirurgie orthopédique (planification, mesure) |
| **Rigueur qualité / documentation** | Enseignement (spécifications, évaluation, docs), dev industriel | Environnement dispositif médical normé : documentation en anglais, tests, traçabilité |
| **Tests unitaires / bonnes pratiques** | Pratique et enseignement de l'architecture, du debug, des patterns | « Mettre en place et maintenir les tests unitaires et d'intégration » |
| **Git, multiplateforme** | Git quotidien ; dev Windows + ciblage multiplateforme Unity | Exigences outillage couvertes |
| **Anglais écrit** | Enseignement à SAE Genève (contexte international), docs techniques | « Bon niveau d'anglais écrit requis » |

---

## 3. Écarts réels et stratégie de compensation

> **Règle d'or : ne jamais revendiquer une compétence non maîtrisée.**

| Écart (exigé) | État réel | Compensation |
| --- | --- | --- |
| **Qt** | Non pratiqué | Expérience IHM réelle (Gebo, Unity) → paradigmes UI/événements transférables ; Qt = écart n°1 à nommer et à amorcer (voir §5) |
| **QML / JavaScript** | JS non pratiqué professionnellement | Atout, pas prérequis — posture d'apprentissage |
| **OpenGL direct** | Concepts 3D maîtrisés via moteurs, pas l'API brute | Reformuler honnêtement : « 15 ans de 3D temps réel, prêt à descendre au niveau API » |
| **Normes dispositifs médicaux (IEC 62304…)** | Non pratiquées | Rigueur industrielle + enseignement = terrain favorable ; normes = processus apprenable |
| **« Applications web »** (mention annonce) | Stack web non revendiquée | Point flou de l'annonce (C++/Qt vs web) — question à poser en entretien plutôt qu'écart à couvrir |

**Leviers transversaux :** re-skilling prouvé (4 pivots de stack) · enseignement = apprentissage continu · repositionnement « ingénieur logiciel temps réel/3D », pas « prof de jeu vidéo ».

---

## 4. Mots-clés ATS

`C++` · `Qt` (via posture) · `3D temps réel` · `OpenGL` (concepts) · `traitement d'image` · `OpenCV` · `tests unitaires` · `tests d'intégration` · `Git` · `multiplateforme` · `architecture logicielle` · `spécifications` · `documentation technique en anglais` · `dispositif médical`.

---

## 5. Action concrète recommandée

Transformer « je peux apprendre Qt » en « j'ai déjà commencé » :

- **Mini-démonstrateur Qt** (week-end) : petite appli Qt Widgets/QML affichant un rendu 3D simple (Qt + OpenGL) — par ex. visualiseur STL d'une pièce orthopédique. Versionné GitHub.
- Bénéfice : coche Qt + QML + OpenGL d'un coup, sur un objet évocateur du métier d'Amplitude.
- Réutilisable pour eCential Robotics (même écart Qt).

---

## 6. Fourchette salariale (analyse)

- **Calibrage de l'annonce :** « 2 ans minimum » → budget probable **38–48 K€ brut** (ingénieur junior/confirmé, bassin de Valence, coût de la vie plus bas que Lyon).
- **Marché medtech Drôme/Rhône-Alpes** pour un confirmé C++/Qt : ~42–52 K€ ; senior : 50–58 K€.
- **Cible Sébastien (50–52 K€)** : atteignable seulement si Amplitude requalifie le poste vers un profil expérimenté ; sinon décalage probable de 5–10 K€.
- Avantages annoncés (RTT, intéressement, participation, TR, mutuelle familiale) : à valoriser dans le package global.
- **Position de négociation :** annoncer la cible 50–52 K€ en assumant la séniorité C++ (25 ans), tout en écoutant le calibrage réel du poste.

---

## 7. Canal & checklist

1. Candidature via l'offre (LinkedIn/site Amplitude) — CV + lettre PDF à l'attention du service RH.
2. Repérer sur LinkedIn l'équipe « R&D Développement technologies » pour un contact direct.

- [ ] **Trancher la question Valence** (trajet/rythme) avant tout travail de CV
- [ ] Dupliquer `_modeles/cv-industrie.html` → `cv-amplitude.html` (accent : C++, 3D, image, qualité/tests)
- [ ] Finaliser la lettre (`Lettre-motivation-Amplitude.md` → HTML → PDF)
- [ ] (Option) Démonstrateur Qt (§5)
- [ ] Déposer + consigner dans `_suivi.md`
