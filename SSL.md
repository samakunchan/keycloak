# Secure Locker Layer

Ref: https://www.ibm.com/docs/en/api-connect/10.0.1.x?topic=overview-generating-self-signed-certificate-using-openssl

Object: installer un certificat SSL pour un keycloak conteneuriser.

## CMD

    openssl req -newkey rsa:2048 -nodes -keyout /certs/key.pem -x509 -days 365 -out /certs/certificate.pem

Cette commande va poser plein de question qu'il faut répondre. Au bout du processus, deux fichiers seront créés.

## Config docker-compose.yml

Ref: https://www.keycloak.org/server/all-config#_httptls

    ...
    environnements:
      KC_HTTPS_CERTIFICATE_FILE: /opt/keycloak/certs/certificate.pem
      KC_HTTPS_CERTIFICATE_KEY_FILE: /opt/keycloak/certs/key.pem
    ...
    volumes:
      - ./certs:/opt/keycloak/certs
