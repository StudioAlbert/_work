# Argumentaire d'entretien — Alstom · SW Engineer Remote Driving System

> Fiche à relire juste avant l'entretien. Complète [[Strategie-Alstom]] (analyse de fond) — ici, du **prêt-à-dire**.
>
> **Docs de prépa liés :** [[Glossaire-technique-Alstom]] (ne pas se faire piéger sur un terme) · [[Remuneration-marche-Alstom]] (si la question tombe) · **démonstrateur** `demonstrateur-teleconduite/` (Python/MQTT/Docker/CI — **réalisé**, voir son `README.md`).

## Logistique

- **Quand :** vendredi **2026-07-10** — **RDV confirmé** (reporté du 08/07). Durée ~**30 min** (court : aller à l'essentiel). *Revérifier l'heure exacte dans l'invitation.*
- **Où :** Microsoft Teams (lien + n° + code secret dans l'email `ALSTOM - Entretien visio…`). N° secours : +33 1 73 24 05 79, conf. 464 237 592#.
- **Qui :** **David GELIN — V&V Manager** (Validation & Vérification).
- **Nature :** entretien manager, mise en avant des **connaissances & compétences techniques** liées au poste.

## Décoder l'interlocuteur : un V&V Manager

Il ne dirige pas (que) le dev : il possède la **validation & vérification**. Ce qu'il valorise → **rigueur de test, robustesse, cas limites & modes de panne, traçabilité des exigences, latence maîtrisée, qualité**. Contexte **ferroviaire** = sûreté logicielle (normes CENELEC **EN 50128 / EN 50657**, niveaux **SIL**) — tu n'es pas expert du sujet, mais **connaître les mots** et **poser la question** montre que tu as fait tes devoirs.

➡️ **Fil rouge à tenir :** parler « **preuve, test, robustesse, mesure vérifiée** », pas seulement « je code ». Et : **la testabilité est une propriété de l'architecture** — c'est ton angle fort avec lui (voir plus bas).

## Pitch d'ouverture (~90 s) — « Parlez-moi de vous »
### Présentation chronologique

> « Je suis développeur logiciel depuis plus de 20 ans, avec un cœur de métier **C++ et temps réel**. 
> 
> J'ai commencé en **informatique industrielle** — supervision et contrôle de production temps réel — puis en **vision par ordinateur** chez PRESI, où j'ai développé le **logiciel de pilotage d'un durométre** : un instrument de mesure de dureté associant un **microscope motorisé à tourelle multi-objectifs**, des **platines micrométriques** et une **caméra haute précision**. Le logiciel coordonnait le **contrôle matériel, l'acquisition caméra et la mesure par traitement d'image** en C++/OpenCV — un domaine où le code doit être **validé et précis**, pas seulement fonctionnel. 
> 
> J'ai ensuite conçu des systèmes **3D interactifs temps réel**, dont un **simulateur de formation pour la SNCF** sur le système de freinage — d'où mon intérêt très concret pour votre projet de télé-conduite, à la croisée du **ferroviaire, du temps réel et de l'IHM**. 
> 
> Aujourd'hui j'enseigne la programmation C++/C# et j'encadre des projets, mais je souhaite **revenir au développement produit** sur un sujet à fort impact : la **décarbonation de la mobilité par le ferroviaire**. Je connais bien C++ ; sur les briques plus récentes de votre stack — Python, Docker, MQTT — je suis en montée en compétence, que j'ai déjà **matérialisée par un démonstrateur** ; et mon parcours montre que j'absorbe vite de nouvelles technos. »

>« Je suis développeur logiciel depuis plus de 20 ans, actuellement en poste à la SAE de Geneve comme enseignant **C++ / C# et le moteur de jeu Unity**.»
>
>j'anticipe un repli du marché de l'emploi du JV, et par ricochet dans l'enseignement, cela a déclenché une recherche d'opportunité autour du C++ pratiqué depuis longtemps, notamment autour du C++ moderne et de la fiabilité exigée par le JV, et d'une motivation a trouver un poste très technique. 
>
>je n'ai pas hésité en voyant votre proposition 
>	Train : rappels de ce que j'appréciais dans l'industrie : Anecdote GEBO, grosses usines Vision Vision : PRESI, Travail créatif avec la Kinect, un peu de ML, de réalité augmentée 
>


*Note :* le durométre couche **trois cases d'un coup** pour ce poste — **perception** (caméra/vision), **pilotage matériel temps réel** (proche robotique / systèmes embarqués), **validation** (mesure vérifiée). C'est le proof-point le plus rentable du pitch : appuie dessus.

## 3 messages clés (à replacer coûte que coûte)

1. **Ingénieur C++ temps réel** — pas un débutant : industriel + simulation + enseignement C++.
2. **Culture de la validation / mesure vérifiée** — l'angle qui parle à un V&V Manager (voir ci-dessous).
3. **Domaine ferroviaire déjà touché + apprenant rapide** — simulateur SNCF, re-skilling prouvé 4×.
#### Mon objectif
##### Redevenir expert technique
je laisse derriere moi
- la creativite, mettre celle-ci a profit pour etre force de proposition technique, resoudre les problemes et decouvrir les solutions
- l'enseignement, ja' bcp appris de mes éléves et de l'expertise de mes collegues, je veux retourner dans l'action
##### Plan d'action
De la formation :
Rapide 30/60/90 pour fit le poste
Diplôme d'îngénieur
Assister a des confs

## Ton atout spécial pour CE manager : la validation

- **PRESI — pilotage d'un durométre (C++/OpenCV).** Un logiciel de **mesure** n'a de valeur que **vérifié** : exactitude, **calibration**, **répétabilité**, comparaison à des **étalons**. C'est de la **vérification par nature** → raconte comment on valide qu'une mesure est juste (références, tolérances, tests de non-régression), et comment on pilote un instrument matériel de façon fiable (asservissement des platines, synchronisation acquisition/mesure).
- **Gebo — contrôle de production temps réel.** Robustesse en conditions réelles, gestion des **états dégradés**, supervision.
- **Architecture = testabilité (ton point de vue à assumer).** Pour être testable, un programme doit être **architecturé pour** : **découplage** (Event Bus, machines à états — pratique affûtée notamment par le temps réel du jeu), **injection de dépendances**, modules isolables. *« L'architecture est au cœur de mes préoccupations, précisément parce qu'elle conditionne la testabilité. »* Mots-clés à placer : **tests unitaires**, **tests d'intégration**, **stress tests / tests de charge**, **essais in-situ** (ils en parlent : labo + site).
- **Enseignant.** Concevoir des **examens & barèmes** = concevoir des **tests et des critères de réussite** ; encadrer des projets = revue de code et exigence qualité.

## Traiter les écarts — honnêteté cadrée (ne jamais bluffer)

Formulation prête si on te pousse sur **Python / Docker / K8s / CI / Qt / MQTT-UDP** :

> « Ces briques ne sont pas encore à mon actif en production. Mais : je maîtrise **C++** et les fondamentaux temps réel ; **Git** est un quotidien, donc CI/CD et conteneurs sont une **surcouche outillage** logique ; **C# → Python** est un **transfert court** ; et MQTT/UDP relèvent de concepts réseau accessibles vu mon bagage temps réel et intégration matérielle. Mieux : j'ai **matérialisé** cette montée en compétence par un **démonstrateur** — un petit pipeline de télémétrie **Python + MQTT + Docker + CI** avec mesure de latence. Mon parcours a déjà pivoté **4 fois** de stack avec succès — et j'ai un **plan d'appropriation clair sur 30/60/90 jours**. »

**Pourquoi C# → Python est un transfert court (arguments détaillés, dans l'ordre de force) :**
1. **Le vrai pont, c'est OpenCV.** J'ai pratiqué **OpenCV en C++** à PRESI ; l'**API Python d'OpenCV est un quasi-miroir** de l'API C++ (mêmes fonctions, mêmes concepts). Mon expérience vision transfère **directement** vers le Python d'Alstom. *(Argument le plus fort et le plus vérifiable — à sortir en premier.)*
2. **Déjà polyglotte** (C++, C#, JS/P5) : jongler entre langages est une compétence en soi, exercée en continu.
3. **Le dur est déjà acquis** — algo, structures de données, POO, gestion d'erreurs, asynchrone. En Python, ce qui change c'est surtout la **syntaxe et l'écosystème**, pas les fondamentaux. *(Ne pas dire « c'est pareil » : Python est typé dynamiquement, C# statiquement — un technicien reprendrait.)*

**Le plan 30/60/90, concrètement** *(= plan d'intégration sur les 3 premiers mois, montre qu'on se projette)* :
- **30 j — comprendre :** codebase, équipe, produit télé-conduite, chaîne d'outils ; premières petites contributions ; Python/Docker mis en pratique **sur le vrai projet**.
- **60 j — contribuer :** premières features en semi-autonomie ; montée effective sur la stack manquante (un composant Python, un service dockerisé).
- **90 j — être autonome :** ownership d'un module, propositions d'architecture / de tests.

## Questions probables → réponses prêtes

| Question                                                    | Ligne directrice                                                                                                                                                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Parlez-moi de vous**                                      | Le pitch ci-dessus (90 s, pas plus).                                                                                                                                                            |
| **Pourquoi Alstom / la télé-conduite ?**                    | Croisée ferroviaire + temps réel + IHM ; **impact écologique** de la mobilité ferroviaire ; le simulateur SNCF m'y a déjà connecté.                                                             |
| **Pourquoi quitter l'enseignement ?**                       | Revenir au **cœur du dev produit temps réel** à forte exigence techno ; l'enseignement a affûté rigueur et communication, je veux les remettre en production.                                   |
| **Vous venez du jeu vidéo, non ?** *(le sujet va sortir)*   | Recadrer vers l'**ingénierie temps réel**, jamais « prof de JV » : **60/120 fps = budget de 16 / 8 ms par frame** (raisonnement en budget-temps, comme une boucle de contrôle) ; **fiabilité = immersion → robustesse** (un crash casse l'immersion ; ici il casserait la sécurité) ; **architecture découplée + patterns** nombreux ; **IA de décision** (behaviour trees, machines à états) = littératie algorithmique. *(Ne pas surjouer le lien avec leur robotique/perception : ça, c'est PRESI qui le couvre.)* |
| **Vous ne connaissez pas Python/Docker/MQTT ?**             | Réponse « écarts » ci-dessus : honnêteté + fondations solides + **démonstrateur réalisé** + plan 30/60/90. Détail C#→Python : angle **OpenCV** d'abord.                                          |
| **Latence / jitter dans une boucle de contrôle distante ?** | Expérience temps réel industriel ; notions : **buffering, QoS/priorisation, horodatage, prédiction, dégradation gracieuse, watchdog**. Dire ce que je sais, demander leur approche.             |
| **Comment testez-vous / validez votre code ?**              | **La testabilité découle de l'architecture** (découplage → modules isolables) ; **tests unitaires**, **tests d'intégration**, **stress tests**, non-régression (vécu à PRESI sur la mesure). Puis **renvoyer la question** : *« Par curiosité, quelle est votre philosophie pour atteindre les niveaux d'exigence de vos normes — EN 50128 / SIL — et du domaine lui-même ? »* |
| **Un projet technique dont vous êtes fier ?**               | **Simulateur SNCF** (archi, boucle temps réel, IHM opérateur) *ou* **PRESI** (pilotage instrument + précision validée). Format STAR.                                                            |
| **Dispo / préavis / prétentions ?**                         | Lyon, mobile (Villeurbanne = proche) ; préavis **3 mois négociable** ; fourchette évoquée ailleurs **~50–52 K€** — mais **grand groupe = grille propre** (cf. [[Remuneration-marche-Alstom]]), rester ouvert et demander leur cadre. |

## Questions à POSER (montrent l'alignement avec un V&V Manager)

- Au quotidien, **quelle part réelle C++ vs Python** ? Quelle **chaîne CI / outillage** (Docker confirmé côté annonce) ?
- Quels usages de la vision ? Détection auto, relais IHM augmenté ?
- Où en est le produit (**prototype → industrialisation**) et quels sont **les défis actuels** de robustesse / latence ?
- Comment est organisée la **V&V** sur la télé-conduite — **bancs de test, simulation, essais sur site** ? Quelle part d'automatisation ?
- Quelles **contraintes de sûreté** s'appliquent au remote driving (EN 50128 / SIL) à ce stade du produit ?
- Composition de l'**équipe**, place exacte du poste, et **prochaines étapes** du process ?

## Checklist avant vendredi

- [ ] Tester **le lien Teams + micro/caméra/écouteurs**, fond neutre, lieu calme, bonne lumière.
- [ ] Relire : l'**annonce**, cette fiche, le **CV** (`cv-alstom.md`) et [[Strategie-Alstom]].
- [ ] Préparer **2 anecdotes STAR** rodées : **simulateur SNCF** et **pilotage/mesure PRESI**.
- [ ] 30 min de survol vocabulaire : **MQTT/UDP**, **Docker « hello world »**, pitch **Python vs C# (angle OpenCV)**, notions **EN 50128 / SIL**.
- [ ] Avoir le **portfolio** prêt à montrer si on le demande (studioalbert.github.io/Portfolio).
- [x] **Démonstrateur** Python/MQTT/Docker/CI **prêt** — savoir le pitcher en 30 s (ce qu'il fait, latence mesurée) et l'ouvrir si on le demande.
- [x] Reconfirmer **l'heure** de vendredi si pas encore fixée.

## Pièges à éviter

- **Ne pas bluffer** sur Python/Docker/MQTT — un V&V Manager le repère aussitôt. La montée en compétence n'est **pas** encore aboutie : l'assumer, pivoter sur la **capacité d'apprentissage prouvée** (4 pivots) **adossée au démonstrateur**.
- **Ne pas se survendre « jeu vidéo »** — recadrer systématiquement vers l'**ingénierie logicielle temps réel**.
- **Compagne à la SNCF = anecdote, pas argument.** Ne jamais l'amener comme argument (odeur de pistonnage). Au mieux, si ça vient naturellement : une **familiarité avec la culture ferroviaire**. Le vrai crochet ferroviaire, c'est le **simulateur SNCF**.
- **Pas de ML à PRESI** — c'était du **traitement d'image de mesure** (métrologie), pas de l'apprentissage machine. Ne pas le laisser croire.
- **Rester concis** (30 min) : messages clés + preuves, laisser de la place aux questions.
- **Écouter** : reformuler leurs enjeux avant de dérouler.
