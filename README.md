# Auth0 JavaScript Samples With an Auror Twist

  

This repository holds the quickstart samples using [auth0-spa-js](https://github.com/auth0/auth0-spa-js).

Read the [full tutorials on Auth0.com](https://auth0.com/docs/quickstart/spa/vanillajs).
### Index
List of available quickstarts
- [01 - Login](/01-Login/)
- [02 - Calling an API](/02-Calling-an-API/)

## Auror SPA app test quick start

01-Login will be the folder that we do all of our work in.
### Code 
1. Start by navigating to /01-Login and run `npm i` to install all of the _totally necessary_ packages. 
2. While you're there, rename `auth_config.json.example` to `auth_config.json`. Update the values to the following: (All of these values are for sandbox, if you want to test prod, then use production domains and audiences)
    1. domain: "login.au.sb.auror.io"
    2. clientId: This is the client ID of the application in Auth0. This is generated during provisioning.
    3. audience: "https://auror.fawkes.sb/open-api"
3. open up `/js/app.js` and in the Login function (Line 7), make sure that the options include a redirect URI
```js
 const options = {
      authorizationParams: {
        redirect_uri:"http://localhost:3000/"
      }
    };
```
4.  ConfigureClient (around line 51) should look like this. **Update the connection value.** 
```js
  auth0Client = await auth0.createAuth0Client({
    domain: config.domain,
    clientId: config.clientId,
    authorizationParams: {
      redirect_uri:"http://localhost:3000/",
      connection: 'secure-auth-test', //Replace this with the Auth0 Connection name
    }

  });
```
5. save the file and run `npm run dev`  to run the project. Open a browser and go to (http://localhost:3000). 
### Auth 0 Config
In a separate tab, open up Auth0. At this point, an integration should already have been provisioned. CLICK HERE TO PROVISION 
For this stage, we need to make sure that the integration has the correct settings.
1. Navigate to Applications > Applications in auth0. Click on the Single Page Application you are using. 
2. SPA apps should NOT have a 'Credentials' tab. If you see a Credentials tab, click on it and select 'None'. 
3. In 'Settings', navigate to 'Application URIs'. Put localhost in this field `http://localhost:3000/`
4. In 'Allowed Web Origins', also include localhost and include a wildcard. `http://localhost:3000/*`
5. Save the settings. 

### Testing 
Go back to (http://localhost:3000) and click on login. Go through the full flow and if you get all the way through, you should end up back on the localhost page with a profile icon in the top right. Congrats, it works! 
The Access Token should be visible in the console logs. 
  

## What is Auth0?
Auth0 helps you to:
- Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, among others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
- Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
- Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
- Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
- Analytics of how, when and where users are logging in.
- Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).
## Issue Reporting
If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.
## Author
[Auth0](auth0.com)
## License
This project is licensed under the MIT license. See the [LICENSE](LICENSE.txt) file for more info.