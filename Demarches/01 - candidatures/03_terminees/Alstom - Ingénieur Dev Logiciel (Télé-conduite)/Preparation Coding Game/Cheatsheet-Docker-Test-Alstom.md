# Cheatsheet Docker — Test technique Alstom (départ de zéro)

> **Enjeu : priorité d'apprentissage n°2 (~1 jour + TP).** Zéro pratique acté — mais le dépôt `demonstrateur-teleconduite` existe et devient ton **terrain d'entraînement** : le faire tourner et le décortiquer est le TP le plus rentable de la semaine. Vocabulaire complémentaire : [[Glossaire-technique-Alstom]] §2.
> Liée à [[Strategie-Test-Technique-Alstom]].

---

## 0. Démarrage express (J2 après-midi — 1 h 30)

1. Installer **Docker Desktop** (Windows : backend WSL2 activé). Vérifier : `docker --version`.
2. Premiers pas, dans l'ordre, en lisant ce qui s'affiche :
```bash
docker run hello-world                 # télécharge une image, crée un conteneur, l'exécute
docker run -d -p 8080:80 nginx         # serveur web → http://localhost:8080
docker ps                              # le conteneur tourne
docker exec -it <id> bash              # entrer DANS le conteneur (ls, exit)
docker logs <id>                       # sa sortie
docker stop <id> && docker rm <id>     # arrêt + suppression
docker images                          # les images téléchargées restent
```
3. Constater le concept central : nginx a tourné **sans rien installer sur ta machine** — l'image embarque tout.

## 1. Concepts — formulations exactes attendues en QCM

- **Image** = modèle figé, en lecture seule, construit en **couches (layers)**. **Conteneur** = instance en exécution d'une image + une couche d'écriture. Analogie directe : **classe / objet**.
- Un conteneur **s'arrête quand son processus principal (PID 1) se termine**. (Réponse à « pourquoi mon conteneur s'arrête aussitôt ? »)
- **Conteneur vs VM** : le conteneur **partage le noyau de l'hôte** (isolation par namespaces + cgroups) ; la VM embarque un OS complet. Conteneur = léger, démarre en secondes.
- Les données écrites dans un conteneur sont **perdues à sa suppression** → volumes (§4).
- **Registry** (Docker Hub, GitLab Container Registry) : dépôt d'images ; `docker pull` / `push`. Le tag `latest` est juste le tag **par défaut** — il ne garantit pas « la plus récente » (piège).
- Pourquoi Docker existe : « ça marche sur ma machine » → l'image tourne **à l'identique partout** (dev, CI, prod).

## 2. Dockerfile — la recette de construction

```dockerfile
FROM python:3.12-slim          # image de base
WORKDIR /app                   # répertoire courant (créé si absent)
COPY requirements.txt .        # copier LES DÉPENDANCES d'abord (cache, cf. pièges)
RUN pip install -r requirements.txt   # exécuté AU BUILD → crée une couche
COPY . .                       # puis le code
EXPOSE 8000                    # documentation SEULEMENT — ne publie rien !
ENV MODE=prod
CMD ["python", "main.py"]      # commande de démarrage du conteneur
```
Construire puis lancer :
```bash
docker build -t monapp:1.0 .
docker run -d --name app -p 8080:8000 -e MODE=dev monapp:1.0
```

### Pièges QCM garantis
- **`RUN` vs `CMD`** : `RUN` s'exécute pendant le **build** (installe, compile) ; `CMD` définit la commande de **démarrage**. Plusieurs `RUN` possibles ; **seul le dernier `CMD` compte**.
- **`CMD` vs `ENTRYPOINT`** : les arguments de `docker run image <args>` **remplacent** `CMD` mais **s'ajoutent** à `ENTRYPOINT` (CMD sert alors d'arguments par défaut).
- **`EXPOSE` ne publie aucun port** — c'est `-p hôte:conteneur` qui publie. **Piège n°1 des QCM Docker.**
- **`COPY` vs `ADD`** : `ADD` sait en plus décompresser des archives et télécharger des URL ; bonne pratique = `COPY` sauf besoin précis.
- **Cache de build** : les couches sont réutilisées **dans l'ordre** ; une ligne modifiée invalide toutes les suivantes → d'où `COPY requirements.txt` **avant** `COPY . .` (le code change souvent, pas les dépendances). Question d'optimisation classique.
- **Multi-stage build** (`FROM … AS build` puis `COPY --from=build`) : image finale sans outillage de compilation → plus petite. Réponse aux questions « réduire la taille ».
- `ARG` = variable de **build** ; `ENV` = disponible **à l'exécution**.

## 3. Commandes à connaître par cœur

```bash
docker ps / docker ps -a               # actifs / tous
docker logs -f <nom>                   # suivre la sortie
docker exec -it <nom> bash             # shell dans un conteneur EN COURS
docker run --rm -it image bash         # nouveau conteneur interactif, auto-supprimé
docker inspect <nom>                   # JSON complet (IP, env, mounts)
docker system prune                    # ménage
```
- Options de `run` : `-d` détaché · `-p` publie un port · `-v` volume · `-e` variable d'env · `--rm` supprime à l'arrêt · `--name` nomme.
- **`docker exec` vs `docker run`** : `exec` entre dans un conteneur **existant** ; `run` en **crée un nouveau**. Piège fréquent.

## 4. Volumes & réseau

- **Volume nommé** (`-v data:/var/lib/db`) : géré par Docker, **persiste** après suppression du conteneur. **Bind mount** (`-v $(pwd):/app`) : dossier de l'hôte monté dans le conteneur — idéal en dev (le code édité est vu en direct).
- Réseau par défaut : **bridge**. Sur un réseau défini par l'utilisateur — et **dans Compose** — les conteneurs se joignent **par leur nom de service** (DNS interne) : un service Python joint le broker via `broker:1883`, pas `localhost`. (Piège : `localhost` dans un conteneur = le conteneur lui-même, pas l'hôte.)

## 5. Docker Compose — et TP démonstrateur (J3 matin)

```yaml
services:
  broker:
    image: eclipse-mosquitto:2
    ports: ["1883:1883"]
  train:
    build: ./train
    depends_on: [broker]
    environment:
      - BROKER_HOST=broker      # ← nom de service = nom réseau
```
```bash
docker compose up -d --build    # construit et démarre tout
docker compose logs -f train
docker compose down             # (-v pour supprimer aussi les volumes)
```
- **`depends_on` contrôle l'ordre de démarrage, PAS la disponibilité réelle** (le broker peut ne pas être prêt) — piège QCM ; la réponse propre est `healthcheck` + `condition: service_healthy`.

### TP sur `demonstrateur-teleconduite` — dans l'ordre
1. `docker compose up --build` — le voir tourner, lire les logs de chaque service.
2. Ouvrir le `docker-compose.yml` : identifier services, ports publiés, variables d'env, `depends_on`.
3. Ouvrir chaque `Dockerfile` : retrouver FROM/COPY/RUN/CMD et l'ordre « dépendances avant code ».
4. Casser/réparer : changer un port publié, renommer un service (et constater l'échec de connexion), rebuilder.
5. `docker exec -it <service> sh` : regarder l'intérieur (fichiers copiés, env).
→ Après ce TP, chaque question QCM Docker correspondra à quelque chose de **vu de tes yeux** — et le discours d'entretien « démonstrateur » devient du vécu.

## 6. Écosystème (questions de culture)

- **Kubernetes** : orchestration à grande échelle (scaling, self-healing), au-dessus de la conteneurisation. Savoir situer — ne pas revendiquer ([[Glossaire-technique-Alstom]]).
- **CI/CD** : la pipeline construit l'image, la teste, la pousse au registry — c'est le rôle du `.gitlab-ci.yml` du démonstrateur.
- Bonnes pratiques citées en QCM : un processus par conteneur, images minimales (`slim`/`alpine`), pas de secrets dans l'image, utilisateur non-root, `.dockerignore`.

## 7. Micro-drills (à refaire J5)

1. `EXPOSE 80` sans `-p` : port accessible depuis l'hôte ? → **Non.**
2. `docker run image echo hi` : que devient `CMD` ? que devient `ENTRYPOINT` ?
3. Pourquoi copier `requirements.txt` avant le code ? → cache de couches.
4. `depends_on` garantit-il que la base est prête ? → Non, ordre de démarrage seulement.
5. Dans Compose, un service joint-il un autre via `localhost` ? → Non, via son **nom de service**.
6. Conteneur qui s'arrête aussitôt : cause générique ? → le processus PID 1 s'est terminé (vérifier `docker logs`).
