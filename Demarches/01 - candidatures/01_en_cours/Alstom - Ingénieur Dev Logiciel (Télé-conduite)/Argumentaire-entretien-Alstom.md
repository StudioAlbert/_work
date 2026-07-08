# Argumentaire d'entretien — Alstom · SW Engineer Remote Driving System

> Fiche à relire juste avant l'entretien. Complète [[Strategie-Alstom]] (analyse de fond) — ici, du **prêt-à-dire**.
>
> **Docs de prépa liés :** [[Glossaire-technique-Alstom]] (ne pas se faire piéger sur un terme) · [[Remuneration-marche-Alstom]] (si la question tombe) · **démonstrateur** `demonstrateur-teleconduite/` (Python/MQTT/Docker/CI — voir son `README.md`).

## Logistique

- **Quand :** vendredi **2026-07-10** — **RDV confirmé** (reporté du 08/07). Durée ~**30 min** (court : aller à l'essentiel). *Revérifier l'heure exacte dans l'invitation.*
- **Où :** Microsoft Teams (lien + n° + code secret dans l'email `ALSTOM - Entretien visio…`). N° secours : +33 1 73 24 05 79, conf. 464 237 592#.
- **Qui :** **David GELIN — V&V Manager** (Validation & Vérification).
- **Nature :** entretien manager, mise en avant des **connaissances & compétences techniques** liées au poste.

## Décoder l'interlocuteur : un V&V Manager

Il ne dirige pas (que) le dev : il possède la **validation & vérification**. Ce qu'il valorise → **rigueur de test, robustesse, cas limites & modes de panne, traçabilité des exigences, latence maîtrisée, qualité**. Contexte **ferroviaire** = sûreté logicielle (normes CENELEC **EN 50128 / EN 50657**, niveaux **SIL**) — tu n'es pas expert du sujet, mais **connaître les mots** et **poser la question** montre que tu as fait tes devoirs.

➡️ **Fil rouge à tenir :** parler « **preuve, test, robustesse, mesure vérifiée** », pas seulement « je code ».

## Pitch d'ouverture (~90 s) — « Parlez-moi de vous »

> « Je suis développeur logiciel depuis plus de 20 ans, avec un cœur de métier **C++ et temps réel**. J'ai commencé en **informatique industrielle** — supervision et contrôle de production temps réel — puis en **vision par ordinateur** chez PRESI, où je développais un logiciel de **mesure micrométrique** en C++/OpenCV : un domaine où le logiciel doit être **validé et précis**, pas seulement fonctionnel. J'ai ensuite conçu des systèmes **3D interactifs temps réel**, dont un **simulateur de formation pour la SNCF** sur le système de freinage — d'où mon intérêt très concret pour votre projet de télé-conduite, à la croisée du **ferroviaire, du temps réel et de l'IHM**. Aujourd'hui j'enseigne la programmation C++/C# et j'encadre des projets, mais je souhaite **revenir au développement produit** sur un sujet à fort impact. Je connais bien C++ ; sur les briques plus récentes de votre stack — Python, Docker, MQTT — je suis en montée en compétence, et mon parcours montre que j'absorbe vite de nouvelles technos. »

## 3 messages clés (à replacer coûte que coûte)

1. **Ingénieur C++ temps réel** — pas un débutant : industriel + simulation + enseignement C++.
2. **Culture de la validation / mesure vérifiée** — l'angle qui parle à un V&V Manager (voir ci-dessous).
3. **Domaine ferroviaire déjà touché + apprenant rapide** — simulateur SNCF, re-skilling prouvé 4×.

## Ton atout spécial pour CE manager : la validation

- **PRESI — logiciel de mesure micrométrique (C++/OpenCV).** Un logiciel de mesure n'a de valeur que **vérifié** : exactitude, **calibration**, **répétabilité**, comparaison à des étalons. C'est de la **vérification par nature** → raconte comment on valide qu'une mesure est juste (références, tolérances, tests de non-régression).
- **Gebo — contrôle de production temps réel.** Robustesse en conditions réelles, gestion des états dégradés, supervision.
- **Enseignant.** Concevoir des **examens & barèmes** = concevoir des **tests et des critères de réussite** ; encadrer des projets = revue de code et exigence qualité.
- **Architecture.** Découplage (Event Bus, machines à états) = **testabilité** ; goût des systèmes robustes et de l'outillage.

## Traiter les écarts — honnêteté cadrée (ne jamais bluffer)

Formulation prête si on te pousse sur **Python / Docker / K8s / CI / Qt / MQTT-UDP** :

> « Ces briques ne sont pas encore à mon actif en production. Mais : je maîtrise **C++** et les fondamentaux temps réel ; **Git** est un quotidien, donc CI/CD et conteneurs sont une surcouche outillage logique ; **C# → Python** est un transfert court ; et MQTT/UDP relèvent de concepts réseau accessibles vu mon bagage temps réel et intégration matérielle. Mon parcours a déjà pivoté 4 fois de stack avec succès — j'ai un **plan d'appropriation clair sur 30/60/90 jours**. »

*(Option, si tu as le temps d'ici vendredi : amorcer le mini-démonstrateur Python + MQTT + Docker — cf. [[Strategie-Alstom]] §6 — pour passer de « je peux » à « j'ai commencé ».)*

## Questions probables → réponses prêtes

| Question                                                    | Ligne directrice                                                                                                                                                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parlez-moi de vous**                                      | Le pitch ci-dessus (90 s, pas plus).                                                                                                                                                            |
| **Pourquoi Alstom / la télé-conduite ?**                    | Croisée ferroviaire + temps réel + IHM ; impact mobilité ; le simulateur SNCF m'y a déjà connecté.                                                                                              |
| **Pourquoi quitter l'enseignement ?**                       | Revenir au **cœur du dev produit temps réel** ; l'enseignement a affûté rigueur et communication, je veux les remettre en production.                                                           |
| **Vous ne connaissez pas Python/Docker/MQTT ?**             | Réponse « écarts » ci-dessus : honnêteté + fondations solides + plan 30/60/90.                                                                                                                  |
| **Latence / jitter dans une boucle de contrôle distante ?** | Expérience temps réel industriel ; notions : **buffering, QoS/priorisation, horodatage, prédiction, dégradation gracieuse, watchdog**. Dire ce que je sais, demander leur approche.             |
| **Comment testez-vous / validez votre code ?**              | PRESI (mesure vérifiée, non-régression), revues de code, tests unitaires ; curiosité pour leur chaîne V&V (bancs, simulation, site).                                                            |
| **Un projet technique dont vous êtes fier ?**               | **Simulateur SNCF** (archi, boucle temps réel, IHM opérateur) *ou* **PRESI** (précision validée). Format STAR.                                                                                  |
| **Dispo / préavis / prétentions ?**                         | Lyon, mobile (Villeurbanne = proche) ; préavis **3 mois négociable** ; fourchette évoquée ailleurs **~50–52 K€** — mais **grand groupe = grille propre**, rester ouvert et demander leur cadre. |

## Questions à POSER (montrent l'alignement avec un V&V Manager)

- Comment est organisée la **V&V** sur la télé-conduite — **bancs de test, simulation, essais sur site** ? Quelle part d'automatisation ?
- Quelles **contraintes de sûreté** s'appliquent au remote driving (EN 50128 / SIL) à ce stade du produit ?
- Au quotidien, **quelle part réelle C++ vs Python** ? Quelle **chaîne CI / outillage** ?
- Où en est le produit (**prototype → industrialisation**) et quels sont **les défis actuels** de robustesse / latence ?
- Composition de l'**équipe**, place exacte du poste, et **prochaines étapes** du process ?

## Checklist avant vendredi

- [ ] Tester **le lien Teams + micro/caméra/écouteurs**, fond neutre, lieu calme, bonne lumière.
- [ ] Relire : l'**annonce**, cette fiche, le **CV** (`cv-alstom.md`) et [[Strategie-Alstom]].
- [ ] Préparer **2 anecdotes STAR** rodées : **simulateur SNCF** et **mesure PRESI**.
- [ ] 30 min de survol vocabulaire : **MQTT/UDP**, **Docker « hello world »**, pitch **Python vs C#**, notions **EN 50128 / SIL**.
- [ ] Avoir le **portfolio** prêt à montrer si on le demande (studioalbert.github.io/Portfolio).
- [ ] (Option) démarrer le **mini-démonstrateur** Python/MQTT/Docker.
- [ ] Reconfirmer **l'heure** de vendredi si pas encore fixée.

## Pièges à éviter

- **Ne pas bluffer** sur Python/Docker/MQTT — un V&V Manager le repère aussitôt.
- **Ne pas se survendre « jeu vidéo »** — recadrer systématiquement vers l'**ingénierie logicielle temps réel**.
- **Rester concis** (30 min) : messages clés + preuves, laisser de la place aux questions.
- **Écouter** : reformuler leurs enjeux avant de dérouler.
