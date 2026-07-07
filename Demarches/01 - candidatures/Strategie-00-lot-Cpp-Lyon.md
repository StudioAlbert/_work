# Stratégie de lot — 5 offres C/C++ Lyon (juin 2026)

Vue d'ensemble pour le lot d'annonces traité depuis `00_to_process`. Chaque offre a sa propre stratégie détaillée dans son dossier dédié (`Strategie-*.md`).

**Candidat :** Sébastien Albert — Lyon · C++ · temps réel · vision par ordinateur · C# · IHM
**Décisions cadre (validées) :** traiter les 5 avec priorisation · **pas de plancher salarial** · **éditeur/produit privilégié** vs régie ESN · Lead/IC indifférent.

---

## 1. Positionnement commun (réutilisable sur les 5)

> **Identité à projeter :** *ingénieur logiciel C++ / temps réel*. L'enseignement devient une **preuve de profondeur C++ / architecture / pédagogie technique**, pas l'identité principale. Ne jamais se vendre « prof de jeu vidéo ».

**Forces transverses, toutes vérifiables :**

- **C++** — PRESI (vision/traitement d'image, C++/OpenCV) + enseignement C++/SFML à SAE (programmation générale, mémoire/RAII, etc.).
- **Temps réel** — Gebo (supervision & contrôle de production temps réel), simulateur SNCF (freinage, 3D temps réel), systèmes interactifs.
- **C# / .NET** — LogSystem (C# .NET, conception BDD), enseignement C#/Unity. *Atout rare dans ce lot très « C++ pur » (décisif pour Abylsen).*
- **Vision par ordinateur** — OpenCV (PRESI).
- **Conduite de projet / coordination** — PRESI : « gestion de l'ensemble des projets du département informatique » ; coordination académique SAE ; suivi de projets de fin d'études. *Base crédible pour les rôles « Lead ».*
- **Fond bas niveau / matériel** — DUT GEII (génie électrique et informatique industrielle), informatique industrielle (Gebo), intégration Arduino.
- **Re-skilling prouvé** — 4 pivots de stack réussis (industriel C++ → 3D/VFX → C#/.NET → Unity/C++/enseignement). Méta-compétence d'apprentissage rapide.
- **Git** maîtrisé · 25+ ans d'expérience · Lyon (toutes les offres y sont).

**Écarts récurrents (à traiter en posture d'apprentissage, jamais affirmés) :**

| Écart | Concerne surtout |
| --- | --- |
| **C++ en production industrielle = ancien** (le plus récent est l'enseignement, PRESI s'arrête en 2010) | les 5 |
| **Python** | LR, Caveo |
| **Qt / QML** | Adsearch (cœur), LR/Caveo (annexe) |
| **Bas niveau récent / multithreading / drivers** | Caveo, LR, Effektiv |
| **Linux profond** | Adsearch, LR, Caveo |
| **C++ natif Windows / Win32** | Effektiv |
| **Cryptographie** | Effektiv (domaine produit, pas exigence dure) |
| **Angular / front web SPA** | Abylsen |
| **Management d'une équipe de dev (industriel)** | Adsearch, Abylsen |

---

## 2. Priorisation et effort

| Rang | Offre | Type | Fit | Effort recommandé | Pourquoi |
| --- | --- | --- | --- | --- | --- |
| 1 | **Effektiv → PRIM'X** | Éditeur (souveraineté/ANSSI) | Moyen+ | **Dossier travaillé** | Éditeur produit ✔, recruteur « réponse garantie / réactif 15j », exigences **fondées sur l'appétence** (passion > expérience). Réserve : C++ natif Windows mince. |
| 2 | **Abylsen** | ESN (Transport/ferroviaire) | **Bon (intrinsèque)** | **Dossier travaillé** | Meilleur fit technique du lot : **C# + C++** demandés ensemble + **ferroviaire** (réutilise l'angle simu SNCF d'Alstom). Freins : régie ESN, 40K (mais pas de plancher). |
| 3 | **Adsearch** | Cabinet → éditeur | Faible-moyen | **Effort moyen + réseau** | Éditeur ✔ et 55-65K, mais **Qt/QML cité 2× comme cœur**, Linux profond et **lead d'équipe de devs** = exigences dures non couvertes. À jouer sur lettre + réseau. |
| 4 | **LR Technologies** | ESN (mission produit IoT/IA) | Faible-moyen | **Dépôt ciblé léger** | Mission sur produit, mais **Python + bas niveau** centraux. Voir doublon ci-dessous. |
| 5 | **Caveo** | ESN | Faible | **Dépôt léger / arbitrage** | Quasi-jumelle de LR mais **plus exigeante** (drivers/HAL, multithreading, legacy). |

### ⚠️ Doublon LR Technologies / Caveo
Les deux annonces sont **quasi identiques** (produit IoT + **moteur d'inférence**, C/C++ bas niveau, Python/APIs/IPC, mêmes objectifs « réduire la dette technique »). Très probablement **le même client final atteint via deux ESN différentes**. Recommandation :
- **Ne pas postuler aux deux à l'identique le même jour** (risque de doublon visible côté client).
- Choisir l'ESN la plus réactive / la mieux-disante, ou espacer ; en entretien, ne mentionner qu'une seule démarche.

---

## 3. Actifs à préparer une fois, à réutiliser

1. **CV** — partir de `_modeles/cv-industrie.html` (variante logiciel), dupliquer dans chaque dossier et recibler les mots-clés par offre (cf. memoire workflow). Viser 1 page A4.
2. **Lettre socle** — un paragraphe « identité ingénieur C++/temps réel + re-skilling prouvé » réutilisable, + un paragraphe variable par offre (crochet spécifique).
3. **(Option) Mini-démonstrateur** — surtout pour LR/Caveo (modern C++ + un bout Python/IPC) et Effektiv (un composant bas niveau Windows) : transforme « je peux apprendre » en « j'ai commencé ». À mentionner, pas à présenter comme expérience pro.

## 4. Séquencement suggéré

1. **Effektiv** d'abord (recruteur réactif, retour rapide, calibrage du discours).
2. **Abylsen** en parallèle (réutilise massivement l'angle ferroviaire d'Alstom déjà rédigé).
3. **Adsearch** ensuite, en activant le réseau (Sciences-U Lyon) avant le dépôt ATS.
4. **LR ou Caveo** (une seule des deux en priorité), dépôt léger.

---

## 5. Extension du pipeline (juillet 2026)

Le lot initial de 5 offres a été complété au fil de l'eau. **Pipeline courant** (voir `_suivi.md` pour l'état vivant) :

- **Ajouts entreprises directes** : **Alstom** (Télé-conduite, angle ferroviaire aligné avec Abylsen) · **Amplitude** (C++ chirurgie, Valence) · **eCential Robotics** (C++ Spine, Gières). Amplitude & eCential portent un **risque géo** (>45 min) et pour eCential un **risque santé financière** à instruire avant tout engagement.
- **Lot spontanées cabinets IT Lyon (2026-06-30)** : Externatic · Skaelia · Silkhom · ~~Seyos~~ (refus 2026-07-06) · Licorne Society (dépôt raté, à retenter). Objectif : décrocher **un échange sur la lecture du marché C++/temps réel lyonnais**, pas un mandat immédiat. ROI attendu : 1 échange sur 5 au mieux — investir peu par relance.
- **Volet enseignement JV Lyon** (parallèle) : Gamagora, Gaming Campus, Bellecour, E-Artsup. Piste de repli professionnel si le pivot industriel tarde ; **ne pas laisser dériver l'identité** projetée sur les canaux industriels (cf. §1).

## 6. Signaux marché & journal stratégique

### 2026-07-06 — Refus Seyos (cabinet IT & Ingénierie industrielle)

**Signal** : refus template J+6, signé par le référent IT & Ingénierie industrielle (Dorian Ribeiro de Abreu). Message-type « pas d'adéquation avec les besoins actuels de nos clients », invitation à re-postuler.

**Interprétation** :
- Signal **faible sur le profil** (message générique, pas de retour qualitatif), **fort sur le mode cabinet** : le placement suit un mandat client, pas un vivier de profils atypiques. Un dépôt spontané chez un cabinet retourne peu de valeur si aucun mandat matché n'est ouvert au moment T.
- La décision est *informée* (signée du bon interlocuteur, pas d'un tri RH aveugle) → pas de rappel à faire chez Seyos avant qu'une offre C++ industriel précise sorte.

**Implications sur le reste du lot spontané (Externatic, Skaelia, Silkhom)** :
- Scénario probable pour 2/3 : silence radio ou refus template similaire.
- **Relance J+10 (📅 2026-07-10)** : format court, pivoter la demande sur *lecture du marché* (échange informationnel), pas re-pitch. Un consultant IT parle volontiers de son marché même sans mandat — ça amorce le vivier.
- Ne pas surinvestir : une seule bascule paie le lot.

**Actions dérivées** :
- **Veille active Seyos** : alerte offres seyos.fr + suivre Dorian Ribeiro de Abreu sur LinkedIn. Un dépôt ciblé futur sur *son* offre court-circuite la spontanée.
- **Pas de 2ᵉ lot spontanée cabinets** avant d'avoir mesuré le retour du 1ᵉʳ. Si 2ᵉ lot un jour, changer l'angle (ESN plutôt que cabinets pur recrutement, ou approche LinkedIn directe des référents plutôt que formulaire site).

### Prochains jalons de décision

- **2026-07-08** : retour Effektiv/Marguerite (échange en cours) → si sans nouvelles, relance douce.
- **2026-07-10** : relance lot spontanées (mode « lecture du marché »).
- **~2026-07-15** : **bilan intermédiaire** post-relances Abylsen/Effektiv/Alstom/spontanées. Arbitrages à trancher :
  - Réactivation Adsearch / arbitrage LR-Caveo ?
  - Décision Amplitude/eCential (géo + santé financière eCential) ?
  - Volet enseignement : signaux Gamagora / Gaming Campus / E-Artsup ?
- **2026-08-24** : relance Bellecour École si toujours sans nouvelles.

---

*Détail par offre : voir `Strategie-*.md` dans chaque dossier de candidature.*
*État vivant du pipeline : voir `_suivi.md` (tableau de bord + journal daté).*
