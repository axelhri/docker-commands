# Docker Commands

## Informations Générales

| Commande           | Description                                  |
| ------------------ | -------------------------------------------- |
| `docker --version` | Affiche la version de Docker installée.      |
| `docker info`      | Affiche des informations système sur Docker. |

## Images

| Commande                                       | Description                                                        |
| ---------------------------------------------- | ------------------------------------------------------------------ |
| `docker pull [image]`                          | Télécharge une image depuis un registre Docker.                    |
| `docker push [image]`                          | Envoie une image vers un registre Docker.                          |
| `docker images`                                | Liste toutes les images Docker locales.                            |
| `docker rmi [image]`                           | Supprime une image Docker locale.                                  |
| `docker build -t [tag] [path]`                 | Construit une image Docker à partir d'un Dockerfile.               |
| `docker search [term]`                         | Recherche des images sur Docker Hub.                               |
| `docker save [image]`                          | Sauvegarde une image dans une archive tar.                         |
| `docker load`                                  | Charge une image à partir d'une archive tar.                       |
| `docker commit [container] [repository][:tag]` | Crée une nouvelle image à partir des modifications d'un conteneur. |

## Conteneurs

| Commande                                    | Description                                                                               |
| ------------------------------------------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `docker run [options] [image]`              | Crée et démarre un conteneur à partir d'une image.                                        |
| `docker ps`                                 | Liste les conteneurs en cours d'exécution.                                                |
| `docker ps -a`                              | Liste tous les conteneurs, y compris ceux qui sont arrêtés.                               |
| `docker stop [container]`                   | Arrête un conteneur en cours d'exécution.                                                 |
| `docker start [container]`                  | Démarre un conteneur arrêté.                                                              |
| `docker restart [container]`                | Redémarre un conteneur.                                                                   |
| `docker rm [container]`                     | Supprime un conteneur arrêté.                                                             |
| `docker logs [container]`                   | Affiche les logs d'un conteneur.                                                          |
| `docker exec -it [container] [command]`     | Exécute une commande dans un conteneur en cours d'exécution.                              |
| `docker inspect [container                  | image]`                                                                                   | Affiche des informations détaillées sur un conteneur ou une image.                |
| `docker top [container]`                    | Affiche les processus en cours d'exécution dans un conteneur.                             |
| `docker diff [container]`                   | Affiche les modifications apportées aux fichiers ou répertoires d'un conteneur.           |
| `docker port [container] [port]`            | Affiche le mappage des ports d'un conteneur.                                              |
| `docker rename [old_name] [new_name]`       | Renomme un conteneur.                                                                     |
| `docker update [container]`                 | Met à jour la configuration d'un conteneur.                                               |
| `docker wait [container]`                   | Bloque jusqu'à ce qu'un conteneur s'arrête, puis affiche son code de sortie.              |
| `docker export [container]`                 | Exporte le système de fichiers d'un conteneur sous forme d'archives tar.                  |
| `docker import [file                        | URL] [repository][:tag]`                                                                  | Importe le contenu d'une archive tar pour créer une image de système de fichiers. |
| `docker cp [container]:[path] [local_path]` | Copie des fichiers ou des répertoires entre un conteneur et le système de fichiers local. |

## Réseaux

| Commande                          | Description                    |
| --------------------------------- | ------------------------------ |
| `docker network ls`               | Liste tous les réseaux Docker. |
| `docker network create [network]` | Crée un nouveau réseau Docker. |
| `docker network rm [network]`     | Supprime un réseau Docker.     |

## Volumes

| Commande                        | Description                    |
| ------------------------------- | ------------------------------ |
| `docker volume ls`              | Liste tous les volumes Docker. |
| `docker volume create [volume]` | Crée un nouveau volume Docker. |
| `docker volume rm [volume]`     | Supprime un volume Docker.     |

## Docker Compose

| Commande              | Description                                                                   |
| --------------------- | ----------------------------------------------------------------------------- |
| `docker-compose up`   | Crée et démarre les conteneurs définis dans un fichier docker-compose.yml.    |
| `docker-compose down` | Arrête et supprime les conteneurs définis dans un fichier docker-compose.yml. |
| `docker-compose ps`   | Liste les conteneurs définis dans un fichier docker-compose.yml.              |
| `docker-compose logs` | Affiche les logs des conteneurs définis dans un fichier docker-compose.yml.   |

## Nettoyage

| Commande              | Description                                                     |
| --------------------- | --------------------------------------------------------------- |
| `docker system prune` | Supprime les conteneurs, images, réseaux et volumes inutilisés. |

## Authentification

| Commande        | Description                         |
| --------------- | ----------------------------------- |
| `docker login`  | Se connecte à un registre Docker.   |
| `docker logout` | Se déconnecte d'un registre Docker. |

## Surveillance

| Commande        | Description                                                                                |
| --------------- | ------------------------------------------------------------------------------------------ |
| `docker stats`  | Affiche les statistiques d'utilisation des ressources des conteneurs en cours d'exécution. |
| `docker events` | Affiche les événements en temps réel du démon Docker.                                      |
