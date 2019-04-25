# gk-m365-workplacecloudstorage
M365 Workplace Cloud Storage Spec

## Deployment

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fglueckkanja%2Fgk-m365-workplacecloudstorage%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Enabling Easy Auth (Azure AD authentication)
- Open [Azure Portal](https://www.portal.azure.com) and navigate to the deployed **M365 Workplace Cloud Storage** app service. 
- Select **Authentication / Authorization** under **Settings** and enable **App Service Authentication**.
- Set **Action to take when request is not authenticated** to **Log in with Azure Active Directory**.
- ![Screenshot](./docs/images/1.png)
- Configure **Azure Active Directory** as the **Authentication Provider**
    - Set **Management mode** to **Express**.
    - Create a new AD App or select an existing if you have registeres an AD App for **M365 Workplace Cloud Storage**
    - ![Screenshot](./docs/images/2.png)
- Save the changes