# 🐳 Docker Cheat Sheet

## 📦 Images

| Commande                                     | Description                               |
| -------------------------------------------- | ----------------------------------------- |
| `docker build -t <nom_image>:<tag> <chemin>` | Construire une image Docker               |
| `docker pull <image>:<tag>`                  | Télécharger une image depuis Docker Hub   |
| `docker push <image>:<tag>`                  | Envoyer une image vers un registre        |
| `docker images`                              | Lister les images disponibles localement  |
| `docker rmi <image>`                         | Supprimer une image                       |
| `docker tag <image_id> <nouveau_nom>:<tag>`  | Taguer une image (renommer ou versionner) |

---

## 🚢 Conteneurs

| Commande                                 | Description                                                         |
| ---------------------------------------- | ------------------------------------------------------------------- |
| `docker run <image>`                     | Lancer un conteneur                                                 |
| `docker run -it <image> /bin/bash`       | Lancer un conteneur en mode interactif avec un shell                |
| `docker run -d <image>`                  | Exécuter un conteneur en arrière-plan (détaché)                     |
| `docker run -p 8080:80 <image>`          | Mapper le port 80 du conteneur au port 8080 de l’hôte               |
| `docker run -v /hôte:/conteneur <image>` | Monter un volume entre l’hôte et le conteneur                       |
| `docker ps`                              | Lister les conteneurs en cours d’exécution                          |
| `docker ps -a`                           | Lister tous les conteneurs (actifs ou stoppés)                      |
| `docker stop <id>`                       | Stopper un conteneur                                                |
| `docker start <id>`                      | Démarrer un conteneur arrêté                                        |
| `docker restart <id>`                    | Redémarrer un conteneur                                             |
| `docker rm <id>`                         | Supprimer un conteneur                                              |
| `docker exec -it <id>`                   | Exécuter une commande dans un conteneur en cours (ex : accès shell) |
| `docker logs <id>`                       | Afficher les logs d’un conteneur                                    |

---

## 📁 Volumes

| Commande                             | Description            |
| ------------------------------------ | ---------------------- |
| `docker volume create <nom_volume>`  | Créer un volume Docker |
| `docker volume ls`                   | Lister les volumes     |
| `docker volume inspect <nom_volume>` | Détails d’un volume    |
| `docker volume rm <nom_volume>`      | Supprimer un volume    |

---

## 🌐 Réseaux

| Commande                                         | Description                          |
| ------------------------------------------------ | ------------------------------------ |
| `docker network ls`                              | Lister les réseaux                   |
| `docker network create <nom>`                    | Créer un réseau                      |
| `docker network inspect <nom>`                   | Inspecter un réseau                  |
| `docker network connect <réseau> <conteneur>`    | Connecter un conteneur à un réseau   |
| `docker network disconnect <réseau> <conteneur>` | Déconnecter un conteneur d’un réseau |

---

## 🧱 Dockerfile

| Instruction  | Description                          |
| ------------ | ------------------------------------ |
| `FROM`       | Image de base                        |
| `RUN`        | Exécuter une commande                |
| `COPY`       | Copier un fichier local dans l'image |
| `ADD`        | Ajouter un fichier ou dossier        |
| `CMD`        | Commande par défaut à l'exécution    |
| `ENTRYPOINT` | Point d’entrée principal             |
| `EXPOSE`     | Exposer un port                      |
| `ENV`        | Définir une variable d’environnement |
| `WORKDIR`    | Définir le dossier de travail        |

---

## 🧹 Nettoyage

| Commande                 | Description                          |
| ------------------------ | ------------------------------------ |
| `docker system prune`    | Supprimer tous les objets inutilisés |
| `docker image prune`     | Supprimer les images non utilisées   |
| `docker container prune` | Supprimer les conteneurs arrêtés     |
| `docker volume prune`    | Supprimer les volumes inutilisés     |
| `docker network prune`   | Supprimer les réseaux inutilisés     |

---

## 📋 Infos utiles

| Commande                 | Description                                      |
| ------------------------ | ------------------------------------------------ |
| `docker version`         | Afficher la version de Docker                    |
| `docker info`            | Détails sur l’environnement Docker               |
| `docker inspect <objet>` | Détails JSON d’un conteneur, image, volume, etc. |
