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

Steps:

1. Install dependencies

   - npm install passport
     - Passport in an athenticationt middleware
   - npm install passport-github
     - Is the specific strategy to connect Passport middleware with github auth configuration

2. Config the app in Github

   - The authorization callback URL must match with our route

     - We will update it manually when in production

     * Saved the Id and Secret in a .env file

3. Set Up the Authentication

   1. In the app:

   - Check the passport Files (created the github Strategy class) and Passport config

   2. In the Routes

   - Created the login route (which called the passport authenticate)

4. Set Up Session

- Remembering, session is like the cookie, but session is stored in the server (in the client we only have a session id)
- Passport work with sessions, guaranteeing that the credential are used only once. So, the session is the identifier
- Steps:
  1.  install express-session
  2.  Add the sessoin config (check app.js)
  3.  Implement the serializeUser() and deserializeUser()
