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

### Create the Azure AD App Id

Create an Azure AD app to Query the Message Center API.

1. Go in App Registrations view in Azure AD admin portal
    ![New App Registration](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture2.png)
    Register a New apps in your tenant.
2. Name it accordingly and keep the default configuration
   ![Naming the App](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture3.png)
3. Please keep the application ID and Tenant ID that will be needed for later use
   ![Save AppID and Tenant ID](https://github.com/ericsche/MCinTeams/blob/main/Screenshots/Picture3.png)
