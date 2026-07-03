# Stratégie de candidature — LR Technologies Groupe, Développeur C++

**Poste :** Développeur C++ expérimenté · mission chez un **client** (environnement **IoT** + inférence/IA) · Lyon 2e · CDI
**Source :** https://www.hellowork.com/fr-fr/emplois/77180094.html · Réf 3906467/28072280 D/69L · publiée 25/05/2026
**Conditions :** estimation Hellowork ~37,5-56,1K · TT partiel · exp. 3-7 ans
**Type :** ESN

> **Priorité n°4. Effort : dépôt ciblé léger.** ⚠️ Voir doublon avec **Caveo** (probable même client final).

---

## 1. Verdict de fit & doublon

Fit moyen-faible : C++ couvert, mais les axes centraux (**bas niveau C, performance, Python/IPC, moteur d'inférence**) tombent sur les zones les moins fortes du profil.

⚠️ **Annonce quasi identique à Caveo Consulting** (même produit IoT + **moteur d'inférence**, même C/C++ bas niveau, mêmes Python/APIs/IPC, mêmes objectifs « réduire la dette »). Très probablement **le même client final via deux ESN**. → Ne pas postuler aux deux à l'identique le même jour ; choisir l'ESN la plus réactive. *(Voir `Strategie-00-lot-Cpp-Lyon.md`.)*

---

## 2. Forces à mettre en avant (vérifiables)

| Atout | Preuve | Pourquoi ça compte |
| --- | --- | --- |
| **C++** | PRESI (C++/OpenCV) + enseignement C++/SFML (mémoire, perf) | Exigence centrale |
| **Performance / temps réel** | Gebo (temps réel), systèmes interactifs, traitement d'image | « garantir performance, fiabilité, stabilité » |
| **Diagnostic / debug** | Analyse d'algorithmes, enseignement du debug, dev industriel | « diagnostiquer et corriger des problèmes complexes » |
| **Algorithmique / décision** | IA de jeu (behaviour trees, A*), génération procédurale | Connexion *conceptuelle* aux « concepts d'IA » (cf. §3) |
| **Fond bas niveau** | DUT GEII, informatique industrielle | « composants bas niveau en C » |

---

## 3. Écarts réels & compensation (honnête)

| Écart | État réel | Compensation |
| --- | --- | --- |
| **Python** | Non pratiqué | Transfert court depuis C#/C++ ; à amorcer (mini-démonstrateur §5) |
| **Moteur d'inférence / IA (ML)** | IA *de jeu*, pas inférence ML/runtime de modèles | Honnêteté : littératie algorithmique/décision oui, runtime d'inférence ML à apprendre |
| **Bas niveau récent / système** | Ancien (Gebo) + base GEII | Posture d'apprentissage cadrée |
| **C++ production récent** | Enseignement surtout | Fondamentaux à jour + re-skilling prouvé |

---

## 4. Angle de lettre / pitch

- **Ingénieur C++ orienté performance et fiabilité**, avec un fond informatique industrielle (temps réel, bas niveau via GEII), qui veut revenir sur un produit C/C++ exigeant.
- **Honnêteté Python / inférence** : nommés comme objectifs d'apprentissage ; appuyer sur la capacité de re-skilling rapide.
- **ESN** : si la mission est sur un produit éditeur, le souligner (la cible « produit » reste pertinente même via régie).

## 5. Action concrète (option)

Mini-démonstrateur **C++ ⇄ Python via IPC** (un composant C++ performant exposé à un script Python, ou un petit pipeline de données). Coche Python + IPC + C/C++ de façon réelle. *À mentionner, pas à présenter comme expérience pro.*

## 6. Canal & réseau

1. **Postuler via Hellowork** (« envoyez votre candidature »). CV + lettre PDF.
2. **Arbitrer LR vs Caveo** avant d'envoyer : une seule des deux en priorité.
3. Contacter le recruteur ESN sur LinkedIn pour clarifier la mission/le client.

## 7. Checklist de dépôt

- [ ] Décider : **LR ou Caveo** en priorité (pas les deux à l'identique).
- [ ] CV `cv-lr` — C++, performance/temps réel, bas niveau/GEII, debug ; 1 page A4.
- [ ] Lettre — perf/fiabilité + honnêteté Python/inférence.
- [ ] Générer `CV_Sebastien_Albert_LR.pdf` + `Lettre_Sebastien_Albert_LR.pdf`.
- [ ] (Option) Démonstrateur C++/Python/IPC sur GitHub.
