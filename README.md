# M365 Workplace Cloud Storage Spec

**!!! NOTE: This project is no longer actively maintained and replaced by a [native integration into RealmJoin](https://docs.realmjoin.com/workplace-cloud-storage).**

Please use [this guideline](https://docs.realmjoin.com/workplace-cloud-storage#migration-from-azure-web-app) for migration.

The feature of managing Enterprise Mode Site Lists is covered by Microsoft 365 admin center. So, existing or new site lists need to be added as described here: [Publish enterprise site list to the cloud](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode-cloud-site-list-mgmt#publish-enterprise-site-list-to-the-cloud-1). The resulting site list ID is then published via an Intune policy to Microsoft Edge.

---

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
2. Select **Authentication** under **Settings**

![image](https://user-images.githubusercontent.com/24998910/130623610-10fd623a-a7b8-4fd0-a75e-ec880efefeae.png)

3. Click on **Add Identity Provider**.
![image](https://user-images.githubusercontent.com/24998910/130623886-371c5dd8-bca1-49fb-a7b0-f59f53a66b67.png)

4. Select **Microsoft** as Identity Provider
![image](https://user-images.githubusercontent.com/24998910/130624544-8a9b1cb0-52a7-45d4-8e1b-5a93345d86b6.png)

5. Keep the default options and then click on **Add**
![image](https://user-images.githubusercontent.com/24998910/130625891-ff9dd451-f1b2-4610-b4e2-fd77182d0c58.png)

6. **Edit** newly created identity provider
![image](https://user-images.githubusercontent.com/24998910/130628190-e510b94d-e27d-4fac-9ad1-25af821a0801.png)

7. Click on **Permissions** and then click on **Click here to access API permissions**
![image](https://user-images.githubusercontent.com/24998910/130628471-de1e900a-bd13-435a-b5e6-f64b2bf944b9.png)

8. Click on **Grand admin consent for {{TENANT NAME}}** and then grant consent
![image](https://user-images.githubusercontent.com/24998910/130628925-b849d104-d740-4e43-9aa2-de690b854ccb.png)

9. The status would turn to **Granted**
![image](https://user-images.githubusercontent.com/24998910/130629162-81ac2589-797d-48e8-aebd-b4a993889472.png)

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
