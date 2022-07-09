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

```sh
docker compose up -d
```

Pour fermer le container:

    docker compose down (-v si vous voulez supprimer les volumes en même temps)
