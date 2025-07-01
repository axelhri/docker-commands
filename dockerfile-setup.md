# Cheat Sheet Dockerfile

## Instructions de base

| Instruction  | Description                                                   | Exemple                                         |
| ------------ | ------------------------------------------------------------- | ----------------------------------------------- |
| `FROM`       | Spécifie l'image de base                                      | `FROM ubuntu:20.04`                             |
| `RUN`        | Exécute une commande dans le conteneur                        | `RUN apt-get update && apt-get install -y curl` |
| `CMD`        | Commande par défaut au lancement du conteneur                 | `CMD ["nginx", "-g", "daemon off;"]`            |
| `ENTRYPOINT` | Configure le conteneur pour qu'il soit exécutable             | `ENTRYPOINT ["python3"]`                        |
| `COPY`       | Copie des fichiers depuis le contexte vers l'image            | `COPY ./app /app`                               |
| `ADD`        | Copie des fichiers, permet aussi de décompresser              | `ADD archive.tar.gz /app`                       |
| `WORKDIR`    | Définit le répertoire de travail                              | `WORKDIR /app`                                  |
| `ENV`        | Définit une variable d'environnement                          | `ENV NODE_ENV=production`                       |
| `EXPOSE`     | Indique le port que le conteneur écoute                       | `EXPOSE 80`                                     |
| `USER`       | Définit l’utilisateur qui exécute les commandes               | `USER appuser`                                  |
| `VOLUME`     | Crée un point de montage pour un volume                       | `VOLUME /data`                                  |
| `ARG`        | Définit une variable disponible au build                      | `ARG VERSION=1.0`                               |
| `ONBUILD`    | Définit une instruction à exécuter lors d’un build descendant | `ONBUILD RUN ./install.sh`                      |

---

## Bonnes pratiques

- Utiliser une image de base légère (`alpine`, `scratch`) pour réduire la taille.
- Combiner les commandes `RUN` avec `&&` pour limiter le nombre de couches.
- Nettoyer les fichiers temporaires dans la même commande `RUN` (`apt-get clean`, `rm -rf /var/lib/apt/lists/*`).
- Spécifier un utilisateur non-root avec `USER` pour la sécurité.
- Utiliser `COPY` plutôt que `ADD` sauf si vous avez besoin de fonctionnalités spécifiques (extraction d’archives).

---

## Exemple simple

```dockerfile
FROM node:16-alpine

WORKDIR /app

COPY package.json yarn.lock ./
RUN yarn install --production

COPY . .

ENV NODE_ENV=production

EXPOSE 3000

CMD ["node", "server.js"]
```

## Comment utiliser ce Dockerfile

### Construire l'image

```bash
docker build -t my-api .
```

### Construire et lancer le contenaire

```bash
docker run -d --name con-name -p 3000:3000 my-api
```

**avec env :**

```bash
docker run -d --name con-name --env-file .env -p 3000:3000 my-api
```

### Push une image sur Docker hub

```bash
docker tag monapplication:v1.0 monusername/monapplication:v1.0
```

```bash
docker push monusername/monapplication:v1.0
```

## Exemples concrets

### Développement

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev"]
```

### Production

```dockerfile
FROM node:18-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

FROM node:18-alpine AS production

WORKDIR /app

RUN npm install -g serve

COPY --from=builder /app/dist ./dist

EXPOSE 4173

CMD ["serve", "-s", "dist", "-l", "4173"]
```

## Run une API avec une BDD Postgres

Créer un **network** :
```bash
docker network create my-app-network
```

Run une **image** de **postgres** :
```bash
docker run --name my-postgres-db --network my-app-network ` -e POSTGRES_DB=database -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=mypassword -v postgres_data:/var/lib/postgresql/data ` -d postgres
```

Run l'**image** de l'**API** :
```bash
docker run --name my-spring-app-container --network my-app-network -p 8080:8080 -d my-spring-app
```
