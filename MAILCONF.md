# Configuration des emails

Pour recevoir des emails importants de l'application (Ex: mot de passe oublié, validation de compte), il faut configurer Keycloak pour autoriser les envoies. Voici ci-dessous les étapes importantes à respecter.

## Choisir son fournisseur de SMTP.
Dans ce cas-ci, j'ai pris Mailjet. 

Configuration de Mailjet
- **Host** : `in-v3.mailjet.com`
- **Port** : `465 ou 587`
- **Encryption** : `On active le SSL`
- **Authentication** : Username => `[API_KEY]`, password Username => `[API_PASSWORD]`
- **Domain** : `devpapangue.com`.
- **Senders**: `secure-contact@devpapangue.com`.

Pour récupérer l'`API_KEY`, il faut aller dans `Account settings` > `API Keys`, puis en générer 1.

**Important** : Il faut ajouter le domain dans le DNS pour que les emails soient autorisés par Mailjet. Tout est indiqué par Mailjet normalement.


