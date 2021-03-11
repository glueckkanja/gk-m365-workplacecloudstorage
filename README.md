# M365 Workplace Cloud Storage Spec
## Abstract
Microsoft cloud managed Modern Workplace devices get all relevant policies and configurations via Microsoft Intune. Some of these settings rely on files available by URL. This application is intended to manage these files with an easy to use web based interface where administrators can create, upload and edit files and separate the content based on groups. Currently supported are the following types:

- Enterprise Mode Site List (XML)
- Favorites (HTML and JSON for Microsoft Edge ADMX)
- Backgrounds and other files

## Deployment

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fglueckkanja%2Fgk-m365-workplacecloudstorage%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Enabling Azure AD authentication
### Configure with express settings
1. Open [Azure Portal](https://www.portal.azure.com) and navigate to the deployed **M365 Workplace Cloud Storage** app service. 
2. Select **Authentication / Authorization** under **Settings** and enable **App Service Authentication**.
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/1.png)
3. Set **Action to take when request is not authenticated** to **Log in with Azure Active Directory**.
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/2.png)
4. Configure **Azure Active Directory** as the **Authentication Provider**
    - Set **Management mode** to **Express**.
    - Create a new AD App or select an existing if you have already registered an AD App for **M365 Workplace Cloud Storage**
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/3.png)
5. Save the changes
6. Navigate to **Overview** and click the URL of **M365 Workplace Cloud Storage**
7. If Service is not starting or Authentication fails wait a few moments
8. Accept requested permissions
9. Check **Consent on behalf of your organization** if you want to accept the requested permissions for all users within your organization
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/4.png)

### Configure with advanced settings
As an alternative to the Management mode "Express" you can also use "Advanced":
Please follow the guide provided by Microsoft in their [docs](https://docs.microsoft.com/en-us/azure/app-service/configure-authentication-provider-aad#advanced)

## Authorize users or groups
### Enable authorization for M365 Workplace Cloud Storage
1. Open [Azure Portal](https://www.portal.azure.com) and navigate to **Azure Active Directory**
2. Click **Enterprise applications** from the blade
3. Select the app you have created in the steps before
4. Click **Properties** from the **Manage** section
5. Set **User assignment required** to **Yes**

### Grant specific users and groups access to M365 Workplace Cloud Storage
1. Click **Users and groups** 
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/5.png)
2. Click **Add user**
3. You can grant access to the application to specific user or groups
![](https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/docs/images/6.png)

## Updates and Application Artifacts
To get continuous updates for M365 Workplace Cloud Storage you can point a configuration variable to the maintained GitHub repository. During every restart, the Azure Web App will do a check and update its sources if necessary.

1. Go to Azure
2. Choose the corresponding App Service
3. Click on "Configuration" (under "Settings")
3. Change the value of "WEBSITE_RUN_FROM_PACKAGE" to one of the following:

- Release channel:
  `https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/dist/m365wcs.zip`
- Beta channel:
  `https://github.com/glueckkanja/gk-m365-workplacecloudstorage/raw/master/dist/m365wcs-beta.zip`

5. In future, just perform a restart of the App Service to get the updated artifacts.
