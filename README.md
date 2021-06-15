# Message Center in Teams

## Description

Message Center in Teams is a simple PowerAutomate Solution to gather Message Center Announcement and post them in a Teams Channel.
Its goal is to leverage Teams and SharePoint list to ease the access and simplify sharing of message center announcement.

![Message Center Post in Teams](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture1.png)

## Deployment steps

1. Create the Azure AD App ID to get your Tenant's Message Center posts
2. Create the Microsoft List in the team of your choosing
3. Import/Configure the Initiate MC PA.
4. Import/Configure the Get MC PA
5. Import/Configure the Post MC  

### PreReqs

- This solution require at least 1 PowerAutomate user license for the person that will import the flows, they use Premium Connector to query the management API.

- You will need Azure AD administrator priviledge to [register your app](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) and [consent permission for your app](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-in-app-registrations).

### Create the Azure AD App Id

Create an Azure AD app to Query the Message Center API.

- Go in App Registrations view in [Azure AD admin portal](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps)
    ![New App Registration](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture2.png)

    Click register a New apps in your tenant.
- Name it accordingly and keep the default configuration
   ![Naming the App](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture3.png)
- Please keep the application ID and Tenant ID that will be needed for later use
   ![Save AppID and Tenant ID](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture4.png)
- Open the API Permissions view and Click “+ Add a permission”
   ![Add a Permission](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture5.png)
- Choose Office 365 Management API
   ![Office 365 Management API](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture6.png)
- Choose Application permissions for later use in the Power Automate
   ![App Permission](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture7.png)
- Select ServiceHealth.Read
   ![ServiceHealth.Read Permission](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture8.png)
- Remove the Default Microsoft Graph Permission (User.Read)
   ![Remove Default Permission](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture9.png)
- Grant Admin Consent for your tenant (Extra permission Required see PreReqs)
  ![Grant Admin Consent](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture10.png)
