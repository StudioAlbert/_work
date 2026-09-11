# Stratégie de candidature — Alstom, Ingénieur Développement Logiciel (Télé-conduite)

**Poste :** Ingénieur Développement Logiciel — Conduite à distance · **Req ID 501727** · Villeurbanne (69) · temps plein
**Annonce :** voir `Annonce - Alstom Télé-conduite.md` (même dossier)
**Candidat :** Sébastien Albert — Lyon · C++ · temps réel · vision par ordinateur · IHM

---

## 1. Verdict de pertinence

**Candidature « stretch » mais défendable.** Le poste est un rôle d'ingénieur dev logiciel orienté C++/Python, DevOps moderne et réseau temps réel, sur un produit de télé-conduite ferroviaire. Sur le papier, plusieurs prérequis « durs » ne sont pas couverts (Python, Docker/K8s/CI, Qt, MQTT/UDP). **Mais** :

- L'annonce pose explicitement : *« Nous accordons plus d'importance à la passion et à l'état d'esprit qu'à l'expérience […] nous n'attendons pas de vous que vous possédiez toutes les compétences. »* → les compétences listées sont **souhaitées, pas éliminatoires**.
- Le profil coche des cases **rares et exactement ciblées** : C++, **vision par ordinateur (perception)**, **temps réel**, **IHM/UX opérateur**, et un projet **ferroviaire** réel (simulateur SNCF).

**Estimation :** bon « fit motivation + domaine », fit « stack outillage » partiel. À jouer sur la lettre + le réseau plutôt que sur le seul dépôt ATS.

---

## 2. Forces à mettre en avant (toutes vérifiables)

| Atout | Preuve concrète | Pourquoi ça compte pour Alstom |
| --- | --- | --- |
| **C++** | PRESI (OpenCV), enseignement C++/SFML à SAE | Prérequis dur n°1 — pleinement couvert |
| **Vision par ordinateur / perception** | PRESI : mesure micrométrique & analyse par traitement d'image (C++/OpenCV) | L'annonce cite « perception (vision par ordinateur, etc.) » — touche directe et rare |
| **Temps réel / latence** | Gebo (supervision & contrôle production temps réel), simulateur SNCF, systèmes interactifs | Cœur de la télé-conduite : flux, réactivité, latence minimale |
| **Domaine ferroviaire** | Simulateur 3D temps réel de formation SNCF (freinage) | Motivation + culture métier crédibles, différenciant majeur |
| **IHM / UX opérateur** | 3D interactive Unity, IHM de pilotage industriel | « IHM de nouvelle génération », UX de pilotage à distance |
| **Architecture logicielle modulaire** | Studio Albert, projets Unity (Event Bus, machines à états) | « architecture logicielle modulaire et scalable » de l'annonce |
| **Intégration matérielle / systèmes hétérogènes** | Arduino + LEDs, postes industriels | « intégration de serveurs et composants logiciels hétérogènes », proche robotique |
| **Diplôme** | Master (systèmes images & sons) + **DUT GEII** | Satisfait « ingénieur ou master » ; DUT = base embarqué/électronique |
| **Géographie & langues** | Lyon (poste Villeurbanne), FR natif + EN pro | Disponibilité immédiate, contexte international |

---

## 3. Écarts réels et stratégie de compensation

> **Règle d'or : ne jamais revendiquer une compétence non maîtrisée.** Les écarts se traitent en **posture d'apprentissage cadrée**, pas en affirmation.

| Écart (exigé) | État réel | Compensation |
| --- | --- | --- |
| **Python** | Non pratiqué | Transfert court depuis C#/C++ ; à amorcer (voir §6) |
| **DevOps : Docker / K8s / GitLab CI/CD** | Non pratiqué | **Git déjà maîtrisé** → CI/CD est une surcouche outillage ; conteneurisation = étape suivante logique |
| **Qt** | Non (UI faite sous Unity / web) | Expérience IHM transférable (paradigmes UI/événements) ; Qt apprenable |
| **Réseau (TCP/UDP/MQTT)** | Non explicitement | Bagage temps réel + intégration matérielle → concepts accessibles |

**Leviers transversaux :**

1. **Cadrage par l'annonce** — s'autoriser à postuler grâce à la phrase « passion & état d'esprit > expérience ».
2. **Re-skilling prouvé** — le parcours a déjà pivoté avec succès 4 fois (industriel C++ → 3D/VFX → C#/.NET → Unity/C++). Argument central : *« j'ai démontré ma capacité à absorber de nouvelles stacks rapidement »*.
3. **Métier d'enseignant** = veille et acquisition continues → méta-compétence d'apprentissage rapide.
4. **Repositionnement narratif** — se présenter en **ingénieur logiciel temps réel polyvalent (perception/IHM, appétence robotique/ferroviaire)**, pas en « prof de jeu vidéo ». L'enseignement devient une preuve de profondeur C++/architecture et de communication, pas l'identité principale.

---

## 4. Mapping exigences de l'annonce → preuves

- *« Concevoir les interfaces UX pour superviser/piloter à distance »* → IHM industrielle (Gebo) + 3D interactive temps réel (Studio Albert).
- *« Enjeux réseaux/télécom, flux trains↔centres, latence minimale »* → temps réel industriel + simulation ; **à renforcer** côté MQTT/UDP.
- *« Pratiques DevOps, CI/CD, architecture modulaire/scalable, API »* → architecture modulaire (Event Bus, ScriptableObjects), Git ; **à renforcer** côté Docker/K8s/CI.
- *« Experts proches robotique, communication inter-systèmes, intégration hétérogène »* → informatique industrielle, intégration matérielle Arduino, DUT GEII.
- *« Essais labo/site, algorithmes in-situ »* → mise au point de systèmes temps réel et démonstrateurs d'algorithmes (A* navigation).
- *« Test, assurance qualité, cybersécurité »* → rigueur architecture/tests issue de l'enseignement et du dev industriel.
- *« C++ et Python »* → **C++ couvert** ; Python à amorcer.

---

## 5. Mots-clés ATS à garder présents

`C++` · `temps réel` · `vision par ordinateur` · `OpenCV` · `traitement d'image` · `perception` · `IHM` / `UX` · `architecture logicielle` · `modulaire` / `scalable` · `Git` · `intégration de systèmes` · `informatique industrielle` · `simulation` · `ferroviaire` · `API`.
*(Tension ATS connue : `Python`, `Docker`, `Kubernetes`, `CI/CD`, `MQTT` absents — d'où l'importance du canal humain, §7.)*

---

## 6. Action concrète recommandée (avant/pendant la candidature)

Transformer « je peux apprendre » en « j'ai déjà commencé » :

- **Mini-démonstrateur télé-conduite** (week-end) : un petit pipeline de télémétrie **Python + MQTT (ou UDP) + Docker**, avec une IHM simple affichant un flux temps réel (latence mesurée). Versionné sur GitHub, dockerisé, avec un pipeline GitLab/GitHub CI minimal.
- Bénéfice : coche d'un coup Python + réseau + Docker + CI **de façon réelle**, et fournit un sujet d'entretien concret aligné sur leur produit.
- À mentionner en lettre/entretien, **pas à présenter comme une expérience professionnelle**.

---

## 7. Canaux de candidature & réseau

1. **Postuler sur le jobsite Alstom** (l'annonce LinkedIn précise « Réponses gérées en dehors de LinkedIn ») — lien officiel dans l'annonce. Déposer **CV + lettre PDF**.
2. **Activer le réseau Campus Sciences-U Lyon** : Sébastien a une **Licence Campus Sciences-U Lyon** ; LinkedIn affiche des **anciens Sciences-U Lyon** parmi les contacts liés à l'offre → chercher une mise en relation / un mot d'introduction (porte d'entrée chaude).
3. **Suivi LinkedIn** : un message court au recruteur ou à un ingénieur de l'équipe télé-conduite après dépôt, mentionnant le simulateur SNCF et l'appétence perception/temps réel.

---

## 8. Préparation entretien — angles & questions probables

**Angles à pousser :**
- Récit du **simulateur SNCF** : architecture, boucle temps réel, contraintes de latence, IHM.
- **Perception** : ce qu'on peut tirer d'OpenCV pour l'aide à la télé-conduite (détection, overlays).
- Vision d'une **IHM de pilotage à distance** : réactivité, charge cognitive de l'opérateur, retours sensoriels.

**Questions à anticiper :**
- *« Vous ne pratiquez pas Python/Docker/MQTT — comment comptez-vous monter en compétence ? »*
  → Réponse : track record de re-skilling + le mini-démonstrateur déjà amorcé + plan d'apprentissage à 30/60/90 jours.
- *« Pourquoi quitter l'enseignement pour l'industrie ? »*
  → Envie de revenir au cœur du dev produit temps réel, sur un sujet à fort impact (mobilité ferroviaire).
- *« Comment gérez-vous la latence/jitter dans une boucle de contrôle distante ? »*
  → S'appuyer sur l'expérience temps réel industriel + se documenter en amont (QoS réseau, buffering, prédiction).

**Questions à préparer pour préciser ses lacunes avant l'entretien :** ROS/robotique, contraintes safety ferroviaire (normes), stack télécom utilisée.

---

## 9. Points de vigilance

- **Honnêteté stricte** sur Python/DevOps/réseau : les nommer comme objectifs d'apprentissage, jamais comme acquis. Un recruteur technique le détectera immédiatement.
- **Ne pas se survendre « jeu vidéo »** : recadrer systématiquement vers l'ingénierie logicielle temps réel.
- **Salaire / séniorité** : 25+ ans d'expérience mais reconversion partielle de stack → discuter le positionnement (ingénieur confirmé sur les fondamentaux, en montée sur l'outillage).
- **Délai** : l'annonce est une republication (≈ 7 mois) — le poste peut être tendu/réouvert ; le canal réseau (§7) augmente nettement les chances par rapport au seul dépôt.

---

## 10. Checklist de dépôt

- [ ] Relire CV (`cv-alstom.md` / `.html`) — cohérence des faits, 1 page A4.
- [ ] Générer `CV_Sebastien_Albert_Alstom.pdf` et `Lettre_Sebastien_Albert_Alstom.pdf`.
- [ ] Déposer CV + lettre sur le jobsite Alstom (Req. 501727).
- [ ] Identifier 1–2 contacts Sciences-U Lyon / équipe télé-conduite sur LinkedIn.
- [ ] (Option) Démarrer le mini-démonstrateur Python/MQTT/Docker.
- [ ] Message de suivi LinkedIn après dépôt.
