# KEYCLOAK AVEC DOCKER

Version: 18.0.1
<br>Ceci est une configuration pour installer keycloak avec docker.

### C'est quoi Keycloak

Keycloak est un logiciel open source qui permet le **single sign-on (SSO)** with **Identity and Access Management(IAM)** afin de sécuriser n'importe qu'elle application moderne.
<br>Depuis 2018; ce projet de la communauté **WildFly** (plus connus sous le nom de **JBOSS**) est sous la direction de **Red Hat** qui l'utilise comme projet pour son produit **RH-SSO**.
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

Pour les environnements windows, veuillez commenter ou supprimer la ligne suivante dans le `docker-compose.yml`:

    - --http-relative-path /auth

C'est un patch necessaire pour les environnements macs, mais pertubant pour les environnements windows.
<br>Puis:
    
    docker compose up -d

Pour fermer le container:

    docker compose down -v
