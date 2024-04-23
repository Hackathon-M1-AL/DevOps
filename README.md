# DevOps

## CI/CD

Chaque repository contient un fichier `Dockerfile` qui permet de construire une image Docker de l'application.

Sur chaque repository, lors d'un push sur la branche `main`, une github action est déclenchée pour vérifier que l'applications build correctement et que les tests passent.

Sur chaque repository, lors d'une release, une github action est déclenchée pour construire l'image Docker et la pousser sur le registry GitHub. [Créer une release](#creer-une-release)

## Créer une release

Sur la page du repository, cliquer sur `Releases` puis sur `Draft a new release`.

Ensuite `Choose a tag` et remplir le champ.

Cliquer sur `Publish release`.

## Docker swarm

### Initialisation

Initialiser le swarm sur le manager:

```bash
docker swarm init
```

Récupérer la commande pour ajouter des workers:

```bash
docker swarm join-token worker
```

### Déploiement

Déployer le stack:

```bash
docker stack deploy -c docker-swarm.yml hackathon
```

Liste des services:

-   `nginx`: Reverse proxy / gateway
-   `auth`: Service d'authentification
-   `PostgreSQL`: Base de données pour le service d'authentification
-   `api`: API REST
-   `Mysql`: Base de données pour l'API REST

### Suppression

Supprimer le stack:

```bash
docker stack rm hackathon
```
