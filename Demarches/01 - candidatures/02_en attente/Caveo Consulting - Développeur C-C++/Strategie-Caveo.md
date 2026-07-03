# Stratégie de candidature — Caveo Consulting, Développeur Informatique C / C++

**Poste :** Ingénieur logiciel C/C++ · produit logiciel complexe **IoT + AI** (drivers, optimisation perf, moteur d'inférence) · Lyon 3e · CDI
**Source :** https://www.hellowork.com/fr-fr/emplois/77400420.html · Réf 3921556/28156688 DI/69L · publiée 31/05/2026
**Conditions :** 45-50K · TT occasionnel · exp. 5 ans
**Type :** ESN (à taille humaine — écoute/transparence/loyauté)

> **Priorité n°5. Effort : dépôt léger / arbitrage avec LR.** La plus exigeante côté bas niveau du lot.

---

## 1. Verdict de fit & doublon

Fit faible : C++ couvert, mais l'annonce est la **plus dure du lot sur le bas niveau** — drivers/HAL, **multithreading/concurrence/synchronisation**, fuites mémoire, comportements non déterministes, code legacy, environnements de build. Ce sont précisément les zones les moins récentes du profil.

⚠️ **Quasi-jumelle de LR Technologies** (même produit IoT + **moteur d'inférence**, C/C++ bas niveau, Python/IPC, objectif « réduire la dette technique »). Très probablement **même client final via deux ESN**. → **Choisir LR *ou* Caveo**, pas les deux à l'identique. *(Voir `Strategie-00-lot-Cpp-Lyon.md`.)*

**Arbitrage LR vs Caveo :** LR formule des exigences un peu plus douces ; Caveo détaille davantage le bas niveau dur (drivers, HAL, multithreading, legacy) → **fit légèrement meilleur sur LR**. Caveo reste pertinente si son recruteur est plus réactif ou la mission mieux décrite.

---

## 2. Forces à mettre en avant (vérifiables)

| Atout | Preuve | Pourquoi ça compte |
| --- | --- | --- |
| **C/C++** | PRESI (C++/OpenCV) + enseignement C++/SFML (RAII, pointeurs, cycles de vie, erreurs classiques) | « maîtrise avancée C++ … erreurs classiques » — formulation proche du discours d'enseignant |
| **Fond bas niveau / matériel** | DUT GEII, informatique industrielle (Gebo) | « développements bas niveau en C », « couches d'abstraction matérielle » |
| **Debug / analyse** | Enseignement du debug, analyse d'algorithmes, dev industriel | « très bonnes compétences en debugging et analyse de code complexe » |
| **Architecture / systèmes complexes** | Patterns Unity, conception de systèmes temps réel | « compréhension des architectures et systèmes complexes » |
| **Linux & Windows** | Windows (.NET/desktop) ; notions Linux | « connaissance des OS (Linux, Windows) » — Windows ✔, Linux à nuancer |

---

## 3. Écarts réels & compensation (honnête)

| Écart | État réel | Compensation |
| --- | --- | --- |
| **Multithreading / concurrence / synchro** | Notions via temps réel, mais pas d'expérience récente affichée | **Écart central** — posture d'apprentissage ; ne pas survendre |
| **Drivers / HAL / bas niveau récent** | Ancien (Gebo) + base GEII | Fond crédible mais à actualiser ; honnêteté |
| **Code legacy à grande échelle** | Maintenance applicative (LogSystem) | Transposable partiellement |
| **Python / IPC** | Non pratiqué | À amorcer (démonstrateur §5) |
| **Moteur d'inférence (ML)** | IA *de jeu* uniquement | Littératie algorithmique, runtime ML à apprendre |

---

## 4. Angle de lettre / pitch

- **Atout pédagogique** : un enseignant C++ parle nativement « RAII, gestion mémoire, erreurs classiques, debug » — exactement le vocabulaire de l'annonce. En faire un point de crédibilité.
- **Fond bas niveau via GEII + industrie**, à réactualiser : honnêteté sur le multithreading/drivers récents.
- **ESN à taille humaine** : jouer la carte du dialogue (écoute/transparence affichées) pour expliquer le profil atypique.

## 5. Action concrète (option)

Si on garde Caveo plutôt que LR : un petit exemple **C++ multithread** propre (producteur/consommateur, synchronisation, détection de data race avec un sanitizer) sur GitHub — adresse directement l'écart le plus dur. *À mentionner, pas à présenter comme expérience pro.*

## 6. Canal & réseau

1. **Postuler via Hellowork** (« envoyez votre candidature »). CV + lettre PDF.
2. **Décider LR vs Caveo d'abord.**
3. Contacter le recruteur Caveo (LinkedIn) — ESN à taille humaine, dialogue plus facile a priori.

## 7. Checklist de dépôt

- [ ] Arbitrer **LR ou Caveo** (ne pas doublonner sur le même client final).
- [ ] CV `cv-caveo` — C/C++, bas niveau/GEII, debug, architecture ; 1 page A4.
- [ ] Lettre — vocabulaire C++ d'enseignant + honnêteté multithread/drivers.
- [ ] Générer `CV_Sebastien_Albert_Caveo.pdf` + `Lettre_Sebastien_Albert_Caveo.pdf`.
- [ ] (Option) Démonstrateur C++ multithread sur GitHub.
