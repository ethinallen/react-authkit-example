#  authkit-react example

An example application demonstrating how to authenticate users with AuthKit's React SDK.

## Prerequisites

You will need a [WorkOS account](https://dashboard.workos.com/signup).

---

## Running the example

1. In the [WorkOS dashboard](https://dashboard.workos.com), head to the Redirects tab and create a [sign-in callback redirect](https://workos.com/docs/user-management/1-configure-your-project/configure-a-redirect-uri) for `http://localhost:5173`.

3. Navigate to the "Authentication" page and click the "Configure Sessions" button. Add `http://localhost:5173` to the list of origins to allow clients sessions from. Click "Save."

4. Navigate to the API keys tab and copy the _Client ID_. Rename the `.env.local.example` file to `.env.local` and supply your Client ID.

7. Run the following command and navigate to [http://localhost:5173](http://localhost:5173).

   ```bash
   npm run dev
   ```

---
## Configuring Okta SSO

Next, to configure Okta SSO you are going to need a few things:

1. [Sign in](https://login.okta.com) or [sign up](https://www.okta.com/free-trial/) for an Okta account

2. Follow the guide to [create an Okta SAML connection](https://workos.com/docs/integrations/okta-saml)
    - this will walk you through creating the SAML connection on both the Okta dashboard as well as in the WorkOS dashboard

3. Create users and add them to the application that you configured in Okta
    - Users with the domain that is linked to this Okta application will be redirected to the newly created Okta connection once entering their email into the login box


---
## Deploying to the internet

For this example, the code has already been deployed using Vercel. [Link to live demo](https://react-authkit-example.vercel.app/)


Deployment with Vercel is fairly straightforward, you can simply follow the guide [here](https://vercel.com/guides/deploying-react-with-vercel). In summary, you will need to:

1. Point the Vercel deployment at your repository URL. Vercel comes with Github integrations OOTB, meaning all you have to do is connect your Github and it will handle the deployment of the app

2. Add .env variables
    - Vercel maintains a section specifically for populating env variables for your deployment. Navigate to `[your-project] -> settings -> Environment Variables` to add the `clientID` that was in your local deployment's `.env.local` file

To deploy this, we only have to make a modification to the redirect URIs via the WorkOS dashboard. This is done by navigating to `Redirects` from the homepage of the dashboard and then clicking `Edit Redirect URIs` in the `Sign-in callback` section
    - This should be the url of the deployment; for my example this was `https://react-authkit-example.vercel.app/`

Once deployed, you should be able to navigate to your application's deployment URL and sign on just as you were able to do in your local deployment. With the Okta connection configured, users with the appropriate domain in their email will be redirected to Okta to complete sign-on before being returned back to the sample application. 

