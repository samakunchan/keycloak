# Get started

## Access token

### - Pour toutes les requêtes de Keycloak 
Pour exécuter des requêtes, il faut dans un 1er temps le générer le token de Keycloak

    POST - http://localhost::8085/realms/{{realm_a_remplacer}}/protocol/openid-connect/token
    
    var myHeaders = new Headers();
    myHeaders.append("Content-Type", "application/x-www-form-urlencoded");
    
    var urlencoded = new URLSearchParams();
    urlencoded.append("client_id", "id_du_client");
    urlencoded.append("client_secret", "secret_a_generer_a_la_creation_du_client");
    urlencoded.append("grant_type", "client_credentials");
    
    var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: urlencoded,
        redirect: 'follow'
    };
    
    fetch("http://localhost::8085/realms/heroes/protocol/openid-connect/token", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));

### - Pour un utilisateur simple
Même code, même route, même méthode. Juste les params qui changent.

    POST - http://localhost::8085/realms/{{realm_a_remplacer}}/protocol/openid-connect/token

    ...
    urlencoded.append("client_id", "id_du_client");
    urlencoded.append("username", "username_de_lutilisateur");
    urlencoded.append("password", "password_de_lutilisateur");
    urlencoded.append("grant_type", "password");
    ...

## Créer un utilisateur

    POST - http://localhost::8085/admin/realms/{{realm_a_remplacer}}/users
    Content-Type application/json

    {
        "username": "Strange",
        "firstName": "Stephen",
        "lastName": "Strange",
        "email": "drstranger@marvel.com"
    }

Hé hop, ça ne marche pas. On a un `403 UnAuthorized`. La raison c'est qu'il faut configurer Keycloak pour permettre la gestion utilisateur.

1. Cliquez sur "Realm roles" dans la sidebar
2. Puis "Create role", nommez comme vous le voulez (Ex: "developer")
3. Sur la même page, cliquez sur le bouton "Action" en haut à gauche, puis "Add associated roles"
4. Selectionnez "Filter by client", puis recherchez "user"
5. Au minimum, il faut ajouter "manage-users" pour autoriser la création utilisateur. "Save".
6. Cliquez sur "Realm setting" dans la sidebar
7. Allez dans l'onglet "User registration" et ajoutez le role "developer".
8. Recréez le token Keycloak puis, recommencez la création de votre utilisateur

NB: La seule réponse qu'on verra c'est le status code 201, si c'est un succes.


## Login Page

NB: Il est recommandé de créer son propre realm et ne pas travailler sur le realm master.
<br>NB: Il faut absolument configurer le "Valid redirect URIs" (`Ex: http://localhost:4000/*`).

1. Cliquez sur "clients", puis cliquez sur votre application
2. Dans "settings", renseignez le "Valid redirect URIs"
3. Sur la même page:
   * Keycloak inférieur à v19: Tout en bas de la page, dans la section "Authentication Flow Overrides", selectionnez `Browser flow` à `browser` et `Direct Grant Flow` à `direct grant`.
   * A partir Keycloak v19: Cliquez sur l'onglet "Advanced", puis tout en bas "Authentication Flow Overrides", selectionnez `Browser flow` à `browser` et `Direct Grant Flow` à `direct grant`.


      Ex:
         realm_a_remplacer = demo
         id_du_client = mon_app
         redirect_uri = http://localhost:4000
      http://localhost:8085/realms/{{realm_a_remplacer}}/protocol/openid-connect/auth?response_type=code&client_id={{id_du_client}}&redirect_uri={{redirect_uri}}/authorization-code/callback



