# Glossaire technique anti-piège — entretien Alstom (Remote Driving)

> But : **comprendre chaque terme** qui peut tomber, et savoir **quoi en dire honnêtement**.
> Légende : ✅ = tu maîtrises / peux en parler · 🟡 = à reconnaître, notions · 🔴 = à ne PAS bluffer (dire « pas encore pratiqué, mais… »).

---

## 1. Réseau & protocoles (cœur « flux trains ↔ centre »)

- **TCP (Transmission Control Protocol)** 🟡 — protocole réseau **fiable** : garantit que les données arrivent, dans l'ordre, sans perte (retransmission). Contrepartie : **plus de latence**. Bon pour un fichier, moins pour du flux temps réel.
- **UDP (User Datagram Protocol)** 🟡 — protocole **non fiable mais rapide** : envoie des paquets sans garantie d'arrivée ni d'ordre. Idéal quand **la fraîcheur prime sur l'exhaustivité** (vidéo, télémétrie temps réel) : mieux vaut la dernière position que l'ancienne re-transmise. *Ce que tu peux dire : « Pour de la télé-conduite, on privilégie souvent UDP/temps réel car une donnée en retard est inutile ; on gère la perte applicativement. »*
- **MQTT (Message Queuing Telemetry Transport)** 🟡 — protocole léger de **publication/abonnement** (pub/sub) très utilisé en IoT/télémétrie, au-dessus de TCP. Un **broker** central reçoit les messages publiés sur des **topics** et les distribue aux abonnés. *À dire : « C'est le pattern de mon démonstrateur : le train publie sa télémétrie sur un topic, la station s'y abonne. »*
- **Broker** 🟡 — le **serveur central** MQTT qui route les messages entre publishers et subscribers (ex. **Mosquitto**).
- **Topic** 🟡 — le « canal » nommé d'un message MQTT (ex. `train/telemetry`, `train/command`). Hiérarchique, avec wildcards (`train/#`).
- **Pub/Sub (publish/subscribe)** ✅ (concept) — modèle où les émetteurs (publishers) et récepteurs (subscribers) sont **découplés** via un intermédiaire. *Tu connais le pattern via ton **Event Bus** en Unity — c'est exactement la même idée, appliquée au réseau.*
- **QoS (Quality of Service)** 🟡 — niveau de garantie de livraison. En MQTT : **0** = « au plus une fois » (feu-et-oublie), **1** = « au moins une fois » (peut dupliquer), **2** = « exactement une fois » (le plus coûteux). Aussi, au sens réseau : priorisation/réservation de bande passante.
- **Latence** ✅ — délai entre l'émission d'une donnée et sa réception (ou entre une action et son effet). En télé-conduite, **la latence de bout en bout** (caméra → opérateur → commande → train) est LE paramètre critique.
- **Jitter (gigue)** 🟡 — la **variation** de la latence dans le temps. Une latence de 100 ms stable est plus gérable qu'une latence qui saute de 20 à 300 ms. On l'atténue par du **buffering**.
- **Bande passante / débit (bandwidth/throughput)** ✅ — quantité de données transportables par seconde (Mb/s).
- **Perte de paquets (packet loss)** 🟡 — paquets qui n'arrivent jamais (réseau saturé/instable). En UDP, l'appli doit **tolérer** la perte (dégradation gracieuse).
- **RTT (Round-Trip Time)** 🟡 — temps aller-retour d'un message (≈ 2× la latence one-way). Mesuré par un « ping ».
- **Buffering / mise en tampon** ✅ — accumuler quelques trames pour lisser le jitter, au prix d'un peu de latence. Compromis classique temps réel.
- **5G / réseau cellulaire** 🟡 — support probable de la liaison train↔centre (faible latence, forte bande passante). Bon sujet de **question** à leur poser.

---

## 2. DevOps & outillage (« pratiques DevOps, CI/CD »)

- **Git** ✅ — gestionnaire de versions décentralisé. **Tu l'utilises au quotidien.**
- **GitLab CI/CD** 🔴→🟡 — **CI/CD** = *Continuous Integration / Continuous Delivery* : à chaque `push`, une **pipeline** automatique compile, teste, analyse et (éventuellement) déploie le code. GitLab l'exécute via un fichier `.gitlab-ci.yml`. *À dire : « Je pratique Git ; la CI/CD est la couche d'automatisation par-dessus — c'est dans mon démonstrateur (pipeline lint+tests). »*
- **Pipeline** 🟡 — la **suite d'étapes automatisées** (build → test → package → deploy) déclenchée par la CI.
- **Runner** 🟡 — la machine/agent qui **exécute** les jobs d'une pipeline GitLab.
- **Artefact (artifact)** 🟡 — fichier produit par un job (binaire, rapport de test) transmis aux étapes suivantes ou téléchargeable.
- **Docker** 🔴→🟡 — outil de **conteneurisation** : empaquette une appli **avec toutes ses dépendances** dans une **image** portable, qui tourne à l'identique partout (« ça marche sur ma machine » résolu). *À dire : « Pas encore en prod, mais je l'utilise dans mon démonstrateur — chaque service tourne dans son conteneur. »*
- **Image vs Conteneur** 🟡 — l'**image** est le modèle figé (comme une classe) ; le **conteneur** est une instance en cours d'exécution (comme un objet).
- **Dockerfile** 🟡 — recette texte décrivant comment **construire** une image (base, dépendances, code, commande de lancement).
- **Docker Compose** 🟡 — outil pour **orchestrer plusieurs conteneurs** ensemble (ex. broker + train + station) via un fichier `docker-compose.yml`. *C'est ce que fait ton démonstrateur.*
- **Kubernetes (K8s)** 🔴 — orchestrateur de conteneurs **à grande échelle** (scaling, répartition, auto-réparation) sur des clusters. *À dire : « Concept compris (orchestration/scaling au-dessus de Docker), pas pratiqué — dans mon plan de montée en compétence. »* Ne PAS bluffer.
- **Registry** 🟡 — dépôt d'images Docker (ex. Docker Hub, GitLab Container Registry).
- **YAML** 🟡 — format de fichier texte (indentation) utilisé par Docker Compose, GitLab CI, K8s. Pas un langage, juste de la configuration.

---

## 3. Langages & frameworks

- **C++** ✅ — ton socle. Attends-toi à des questions : **pointeurs/références, RAII, gestion mémoire, STL, `const`-correctness, templates, multithreading**, éventuellement C++11/14/17.
- **Python** 🔴 — langage de haut niveau, interprété, très lisible. Omniprésent en prototypage, scripts, IA, tests. *À dire : « Je ne l'ai pas pratiqué en prod, mais venant de C# et C++ le transfert est court ; c'est le langage de mon démonstrateur. »* Honnêteté.
- **Qt** 🔴 — framework **C++** pour créer des **interfaces graphiques (IHM)** desktop performantes (widgets, signals/slots). *À dire : « J'ai fait de l'IHM (industrielle, Unity UI), pas Qt spécifiquement ; le modèle signals/slots ressemble à l'event-driven que je pratique. »*
- **signals/slots** 🟡 — mécanisme Qt de communication entre objets (un « signal » émis déclenche un « slot »/handler). Encore un cousin du pub/sub / Event Bus. ✅ sur le concept.
- **.NET / C#** ✅ — ta seconde stack (jeu, outils, LogSystem).
- **CMake** ✅ — outil de génération de builds C++ multi-plateforme (tu l'as cité chez Effektiv).
- **RTOS (Real-Time Operating System)** 🟡 — OS spécialisé pour le **temps réel déterministe** (ex. FreeRTOS, VxWorks) sur cibles embarquées. *À reconnaître ; poser la question de leur cible (embarqué bord vs serveur Linux).*

---

## 4. Temps réel, contrôle & télé-conduite

- **Temps réel (dur / mou)** ✅ — **dur** : dépasser l'échéance = défaillance (freinage) ; **mou** : un retard dégrade la qualité sans catastrophe (affichage vidéo). *Tu as fait du temps réel industriel et interactif.*
- **Boucle de contrôle (control loop)** ✅ — cycle **perception → décision → action → retour** répété à haute fréquence. En télé-conduite : capteurs → opérateur/algorithme → commande → train → nouveaux capteurs.
- **Latence de bout en bout (glass-to-glass)** 🟡 — délai total caméra→écran (et retour commande). Le nerf de la guerre de la télé-conduite.
- **Watchdog** 🟡 — mécanisme de **sécurité** : si un composant ne « donne plus signe de vie » dans un délai, on déclenche un état sûr (ex. arrêt/freinage). *Très pertinent à mentionner côté robustesse.*
- **Dégradation gracieuse (graceful degradation / fail-safe / fallback)** ✅ (concept) — quand une entrée manque (perte réseau), le système passe dans un **état sûr** au lieu de planter (ex. freinage automatique). Argument fort côté V&V/sûreté.
- **Téléopération / télé-conduite** 🟡 — piloter une machine **à distance** via un lien de communication ; enjeux = latence, fiabilité du lien, retour sensoriel à l'opérateur, prise en main/rendu.
- **Train autonome — niveaux GoA (Grades of Automation)** 🟡 — échelle d'automatisation ferroviaire : **GoA1** (conduite manuelle assistée) → **GoA2** (conduite semi-auto, conducteur présent) → **GoA3** (sans conducteur, agent à bord) → **GoA4** (totalement sans personnel). *Bonne culture à afficher / question à poser.*
- **CBTC (Communications-Based Train Control)** 🟡 — système de signalisation ferroviaire moderne basé sur la communication continue train↔sol (métros automatiques). À reconnaître.
- **ATO (Automatic Train Operation)** 🟡 — automatisation de la conduite (accélération/freinage) ; brique du train autonome.
- **Fusion de capteurs (sensor fusion)** 🟡 — combiner plusieurs capteurs (caméra, LiDAR, radar, GPS, odométrie) pour une perception robuste de l'environnement.
- **LiDAR / Radar** 🟡 — capteurs de distance/obstacles (LiDAR = laser, nuage de points 3D ; radar = ondes). Complètent la caméra pour la perception.

---

## 5. Perception & vision (ton terrain fort ✅)

- **Vision par ordinateur (computer vision)** ✅ — extraire de l'information d'images (détection, mesure, suivi). *PRESI : mesure micrométrique par traitement d'image.*
- **OpenCV** ✅ — bibliothèque C++/Python de référence en vision. *Tu l'as utilisée en C++.*
- **Traitement d'image** ✅ — filtrage, seuillage, détection de contours, calibration… ton quotidien chez PRESI.
- **Calibration (caméra)** ✅ — déterminer les paramètres d'une caméra pour des mesures/positions correctes (distorsion, échelle). *Lié à la validation d'exactitude — angle V&V.*
- **Détection / segmentation / tracking** 🟡 — localiser des objets, séparer les régions, suivre dans le temps. Reconnais les termes.

---

## 6. Qualité, test & V&V (le domaine de ton interlocuteur — à soigner ✅🟡)

- **V&V (Vérification & Validation)** 🟡 — **Vérification** : « a-t-on construit le produit **correctement** ? » (conforme aux specs, via tests/revues) ; **Validation** : « a-t-on construit **le bon** produit ? » (répond au besoin réel, via essais). *Le poste de David Gelin.*
- **Test unitaire** ✅ (concept) — teste une **fonction isolée** ; automatisé (ex. `pytest`, GoogleTest). *Ton démonstrateur en contient.*
- **Test d'intégration** 🟡 — vérifie que plusieurs composants **fonctionnent ensemble**.
- **Test de non-régression** ✅ (concept) — rejouer les tests pour s'assurer qu'une modif **n'a rien cassé**.
- **Couverture de code (code coverage)** 🟡 — % du code exercé par les tests. Indicateur, pas une fin en soi.
- **TDD (Test-Driven Development)** 🟡 — écrire le **test avant** le code. Reconnais le terme.
- **HIL / SIL (Hardware/Software-in-the-Loop)** 🟡 — bancs de test où le logiciel tourne contre du **matériel réel (HIL)** ou un **modèle simulé (SIL)**. *Excellente question à poser sur leur chaîne de validation.* ⚠️ Ici **SIL = Software-in-the-Loop** (à ne pas confondre avec le SIL sûreté ci-dessous).
- **Banc de test (test bench)** 🟡 — environnement dédié pour tester un système hors production.

---

## 7. Sûreté ferroviaire (culture — à reconnaître, poser des questions 🟡)

- **EN 50128 / EN 50657** 🟡 — normes **CENELEC** du logiciel ferroviaire de sécurité (50128 historique « signalisation/contrôle-commande » ; 50657 « logiciel embarqué à bord »). Imposent process, traçabilité, tests selon la criticité. *Dire : « Je connais l'existence de ces normes, pas leur application détaillée — j'aimerais savoir comment elles cadrent le remote driving chez vous. »*
- **SIL (Safety Integrity Level)** 🟡 — niveau d'exigence de sécurité, **SIL 0 à SIL 4** (4 = le plus critique, ex. freinage). Détermine la rigueur du développement/test. ⚠️ homonyme du *Software-in-the-Loop* — le contexte tranche.
- **Traçabilité des exigences (requirements traceability)** 🟡 — lien démontré entre **chaque exigence** et le code + les tests qui la couvrent. Central en V&V ferroviaire.
- **Cybersécurité** 🟡 — l'annonce la cite : sécurisation des flux (chiffrement, authentification du lien train↔centre), surface d'attaque d'un système connecté. Reconnais l'enjeu.
- **Sûreté de fonctionnement (RAMS)** 🟡 — Reliability, Availability, Maintainability, Safety : le vocabulaire qualité du ferroviaire.

---

## 8. Architecture & API (« architecture modulaire et scalable, API »)

- **API (Application Programming Interface)** ✅ — contrat par lequel des composants/logiciels **s'interfacent** (fonctions, REST, messages).
- **Architecture modulaire** ✅ — découper en composants indépendants et remplaçables (faible couplage). *Ton Event Bus, tes machines à états.*
- **Scalable (passage à l'échelle)** 🟡 — capacité à supporter plus de charge/trains/opérateurs sans refonte.
- **Microservices** 🟡 — architecture en petits services indépendants communiquant par le réseau (souvent conteneurisés). Reconnais le terme.
- **Middleware** 🟡 — couche logicielle d'interconnexion entre systèmes hétérogènes (un broker MQTT en est une forme).
- **ROS (Robot Operating System)** 🟡 — **middleware robotique** standard (nœuds qui communiquent par topics pub/sub — encore le même pattern !). L'annonce parle d'« experts proches de la robotique ». *Bonne question : « Utilisez-vous ROS/ROS 2 ? »* Ne pas prétendre le maîtriser.

---

## Réflexes en cas de terme inconnu (anti-piège)

1. **Ne jamais bluffer.** Un « oui » creux se démonte en une question de suivi.
2. **Reformuler pour rattraper :** « Vous parlez bien de [ma compréhension] ? » — souvent tu connais le **concept** sous un autre nom.
3. **Faire le pont :** « Je ne l'ai pas pratiqué, mais c'est proche de [ce que tu connais] — ex. pub/sub ↔ mon Event Bus. »
4. **Transformer en curiosité :** « Je ne connais pas en détail, comment l'utilisez-vous ici ? » → tu apprends **et** tu montres de l'intérêt.
5. **Assumer + plan :** « Pas encore à mon actif ; c'est dans mon plan de montée en compétence 30/60/90. »
