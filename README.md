# Keycloak and oauth2-proxy demo
This is a helm chart to show how to use oauth2-proxy to authenticate users with Keycloak.

## Instructions
1.
    ```sh
    helm install -n oidc oidc
    ```
2. Login to Keycloak admin console at http://keycloak-7f000001.nip.io:31234 with admin/password.
3. Create a new realm named "test"
4. Create a new client called "oauth2-proxy", set frontend url to http://test-7f000001.nip.io:31234/auth. Set client's Access Type to confidential.
5. Replace clientSecret in values.yaml with client's secret from Keycloak console.
6. Run helm upgrade to apply the new client's secret.
    ```sh
    helm upgrade -n oidc oidc .
    ```
6. Create a new user in Keycloak.
7. Login to http://test-7f000001.nip.io:31234 using the newly created user.
