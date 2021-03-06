# ASP.NET web app (OAuth sample)

This sample shows how to prompt a user to authorize a cloud service that can call APIs on Visual Studio Team Services on behalf of the user.

To learn more about OAuth in Visual Studio Team Services, see [Authorize access with OAuth 2.0](https://www.visualstudio.com/docs/integrate/get-started/authentication/oauth)

## How to setup

> These instructions assume you will be deploying this sample app to an Azure web site. To learn more and to get started, visit [Get started with Azure Web Sites and ASP.NET](http://azure.microsoft.com/documentation/articles/web-sites-dotnet-get-started).

1. Register an OAuth client app in Visual Studio Team Services (https://app.vsaex.visualstudio.com/app/register) 
   * The callback URL should be https://yoursite.azurewebsites.net/oauth/callback, where "yoursite" is the name of your Azure web site
2. Clone this repository
3. Open the solution (VstsOAuthSample.sln) in Visual Studio 2015 or later
4. Update the following settings in web.config to match the values in the app you just registered:
  *  App ID
  *  App Secret (use the "Client Secret" shown on the VSTS Application Settings page, not the App Secret)
  *  Scope (space separated)
  *  Callback URL
5. Build the solution (this will trigger a NuGet package restore, which will pull in all dependencies of the project)
6. Deploy the app to Azure

### Run the sample

1. Navigate to the deployed app (https://yoursite.azurewebsites.net)
2. Confirm your App ID, scope, and callback URL are displayed properly
   ![app](appstart.png)
3. Click **Start**
4. Sign in to Visual Studio Team Services (if prompted)
5. Review and accept the authorization request

If everything is setup properly, Visual Studio Team Services will issue an access token and refresh token and both values will be displayed. **You should keep these values secret**. Also a new authorization will appear in [your profile page](https://app.vssps.visualstudio.com/Profile/View).

With the access token you can invoke [Visual Studio Team Services REST APIs](https://www.visualstudio.com/docs/integrate/api/overview) by providing the access token in the Authorization header.

```
Authorization: Bearer {access token}
```
