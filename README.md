# KEYCLOAK AVEC DOCKER

| Applications | Versions |
|--------------|----------|
| Keycloak     | 20.0.1   |
| Postgres     | 13.2     |
| PgAdmin      | 6.14     |

<br>Ceci est une configuration pour installer keycloak avec docker.

### C'est quoi Keycloak

Keycloak est un logiciel open source qui permet le **single sign-on (SSO)** avec **Identity and Access Management(IAM)** afin de sécuriser n'importe qu'elle application moderne.
<br>Depuis 2018, ce projet de la communauté **WildFly** (plus connus sous le nom de **JBOSS**) est sous la direction de **Red Hat** qui l'utilise comme projet pour son produit **RH-SSO**.
### Etape 1: Environnement (IMPORTANT)

Créé un fichier `.env` avec le `.env-example`.

- Unix, PowerShell ect...: 
```sh
cp .env-exemple .env
```
- cmd.exe (windows)
```sh
cp copy .env-exemple .env
```

### Etape 2: Containerisation

##### Pour rebuild le container de zéro au propre
```shell
sh reset.sh
```

##### Pour lancer le container simplement
```shell
docker-compose -f docker-compose.yml -f docker-compose-dev.yml up -d --force-recreate
```
ou
```shell
sh build-dev.sh
```

##### Pour fermer le container:

```shell
docker compose down -v
```    

| Serveurs  | Adresse                                        | Login           | Password  |
|-----------|------------------------------------------------|-----------------|-----------|
| Keycloak  | [http://localhost:8085](http://localhost:8085) | admin           | admin123  |
| PgAdmin   | [http://localhost:5050](http://localhost:5050) | admin@admin.com | admin     |

Ce sont les informations par défaut, vous pouvez changés ces informations à votre guise dans `.env` et le `docker-compose.yml`

     docker compose down -v && docker compose build --no-cache && docker compose up -d && echo "C'est bon..."
