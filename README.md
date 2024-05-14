# Course Express

## 9. Passport

We are gonna use github strategy to implement passport

### Overview of OAuth 2.0

- OAuth became to make to users to be easier to manage passwords (eliminating the necessity of an account and a password for each app)

- OAuth is more like a standard and a framework focused on _Access Delegation_

- Our app will interact with the delegated access company (in our case Github)

  - Client get to the login page in the app
  - App tells github:
    - clientID
    - Secret
    - Callback (url)
  - App sends client to github
    - Github recognized the app (via clientId) and the user (via your login)
      - Github validates with client the permissions to be given
    - Github gives client an access token and send the user to the callback url (the app specific route)
  - User is back to the app site
    - App takes the Access Token and the Secret, CLientId and send to Github
  - Github validates the secret and token, so send the requested data to the app

  - These are just concepts, passport strategies handle this

### Implementing the Github Strategy

-
