# KEYCLOAK AVEC DOCKER

Ceci est une configuration pour installer keycloak avec docker.

### Etape 1: Environnement (IMPORTANT)

Créé un fichier `.env` avec le `.env-example`

- Unix, PowerShell ect...: 
```sh
cp .env-exemple .env
```
- cmd.exe (windows)
```sh
cp copy .env-exemple .env
```

### Etape 2: Containerisation

Pour les environnements windows, veuillez commenter ou supprimer la ligne suivante dans le `docker-compose.yml`:

    - --http-relative-path /auth

C'est un patch necessaire pour les environnements macs, mais pertubant pour les environnements windows.
    
    docker compose up -d

Pour fermer le container:

    docker compose down -v
