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
    ![Granted Admin Consent](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture11.png)

- Go in Certificates & Secrets section to generate a new Client secrets

    ![Cert & Secrets Section](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture12.png)

- Name it and choose an expiry date according to your security practice

    ![Secret creation](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture13.png)

- Save the Generated Secret for later use, it cannot be displayed again

    ![Secret generated](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture14.png)

### Create the Microsoft List in the team of your choosing

- Open in Teams the team (you are an owner of) you want the solution to be available in

    ![Teams Channel](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture16.png)

- Click the + sign and add Lists as a tab in the general channel

    ![Lists in Teams](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture17.png)
    ![Lists in Teams2](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture18.png)

- In the Lists Tab click Create a list

    ![Create List](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture19.png)

- Click the From Excel button and upload the list template you can find in the Lists Export folder

    ![From Excel](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture20.png)
    ![Select Excel](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture22.png)

- Make sure you configure the right column types for each one

    ![Colomn Types](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture23.png)

    Title > Title
    Product > Single line of text
    PublishedTime > Date and time
    LastUpdate Message > Multiple lines of text
    LastUpdate Time > Date and time
    MessageID > Single line of text
    MessageText > Multiple lines of text
