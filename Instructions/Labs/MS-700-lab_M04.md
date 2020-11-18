---
lab:
    title: 'Lab 04: Manage teams'
    module: 'Module 4: Deploy and manage teams'
---

# **Lab 04: Manage teams**

# **Student lab manual**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership and recovering deleted teams. In the second half of this lab, you will configure the guest access for your tenant and review access for both, internal and external users.

## **Objectives**

After you complete this lab, you will be able to:

- Create a Team from a Microsoft 365 Group

- Create a Team by using PowerShell

- Create a Team by using Microsoft Graph API

- Create a Team with dynamic membership

- Archive and unarchive Teams

- Delete and recover Teams

- Configure guest access in Azure and Teams

- Review Access to a resource

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage team resources**

#### Task 1 - Create a team from an existing Microsoft 365 Group

As part of your pilot project for Contoso, you need to modify the **"IT-Department"** Microsoft 365 Group, created in an earlier task of this lab, and add Teams features to it.

1. Sign in to the **Teams Desktop client** using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new team from existing Microsoft 365 group with the following settings:

	- Name: **IT-Department**

	- Create from existing Microsoft 365 group: **IT-Department**

	- Owners: **Joni Sherman**

	- Members: **Lynne Robbins**, **Megan Bowen**, **Allan Deyoung** and **Alex Wilber**

3. Close the Teams Desktop client.

You have successfully created a new team with the Teams Desktop client, by using an existing Microsoft 365 Group. Leave the Teams client open and continue with the next task.

#### Task 2 - Create a team by using PowerShell

In this task you will create via the Teams PowerShell a new team **"CA-Office"**. You will create the public channels **"Support"** and **"Recruiting"**. Additionally, you will create the private channel **"Administration"** via Teams PowerShell.

1. Open an elevated **Windows PowerShell (Admin)** window.

2. Check the Teams PowerShell module for the ability to create private channels:

   ```powershell
   If((Get-Command New-TeamChannel -ParameterName 'MembershipType' -ErrorAction Ignore) -eq $Null) {"Close PowerShell and install the Teams public preview module."} else {"Continue with the current module."}
   ```
   If the output of the command is "**Continue with the current module**", skip steps 3-6 and continue with step 7. If the output of the command is "**Close PowerShell and install the Teams public preview module.**", close the PowerShell window and continue with step 3.

3. If you need to install the Teams public preview module, first open an elevated PowerShell (Admin) window and uninstall the current PowerShell module by running the following cmdlet:

   ```powershell
   Uninstall-Module MicrosoftTeams
   ```

   **Note:** If the Uninstall-Module command fails, close the PowerShell window, open a new elevated PowerShell (Admin) window, and then repeat this step.

4. Install PowerShellGet module with the version 2.2.4.1:

   ```powershell
   Install-Module -Name PowerShellGet -RequiredVersion 2.2.4.1 -Force
   ```

5. Close and then re-open the elevated PowerShell (Admin) window and then install the Teams PowerShell public preview module:

   ```powershell
   Install-Module -Name MicrosoftTeams -RequiredVersion 1.1.5-preview -AllowPrerelease -AllowClobber  
   ```

6. Verify that the Teams PowerShell module supports creating private channels:

   ```powershell
   If ((Get-Command New-TeamChannel -ParameterName 'MembershipType' -ErrorAction Ignore) -eq $Null) {"Close PowerShell and install the Teams public preview module."} else {"Continue with the current module."}
   ```
   
7. Connect to Teams in your tenant:

   ```powershell
   Connect-MicrosoftTeams
   ``` 

8. Create a new team with the following settings, using the New-Team cmdlet:

	- Displayname: **CA-Office**

	- MailNickName: **CA-Office**

	- Visibility: **Public**


9. Use the GroupId from Get-Team and Add-TeamUser to add **Alex Wilbur** and **Allan Deyoung** as members to the team.

10. Use the GroupId from Get-Team and New-TeamChannel to create the regular channels **"Support"** and **"Recruiting"**.

11. Use the GroupId from Get-Team and New-TeamChannel to create the private channel **"Administration"**.

12. Close the PowerShell window.

You have successfully created a team named **CA-Office** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.

#### Task 3 - Create a team by using Graph API

In this task, you will test the Graph API capabilities for certain automation plans of your organization with Teams. For this task, you will create a new team, called **Early Adopters** with minimal settings, such as Public join options, and another team with multiple existing channels, called **Tech Meetings**.

1. Sign in to the **Graph Explorer** ([https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. If you see a **Permissions requested** page, select **Accept**.

3. Enter the following to the text box next to the **Run query** button:

	- [https://graph.microsoft.com/v1.0/teams](https://graph.microsoft.com/v1.0/teams)

4. Select **Modify permissions** from the top pane.

5. Scroll to the right and select the **Consent** button for the permissions **Group.ReadWrite.All**. And accept the permissions.

6. Select the **Request body** tab and run the following code to create a new team:

   ```json
   {

	"template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('standard')",

	"displayName": "Early Adopters",

	"description": "The Early Adopters Workspace.",

	"visibility": "Public" 

	}
   ```
7. Run a second command in the **Request body** tab and create another team:
 
   ```json
   {

	"template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",

	"visibility": "Public",

	"displayName": "Tech Meetings",

	"description": "Space for all employees participating in the champions program, who want exchange each other about the newest features.",

	"channels": [

	{

	"displayName": "Welcome Hall",

	"isFavoriteByDefault": true,

	"description": "Channel for introducing yourself as a member of the tech meeting participants."

	},

	{

	"displayName": "Tech Lunch and Dinner",

	"isFavoriteByDefault": true,

	"description": "When will be the next tech lunch and who has any suggestions where to meet."

	},

	{

	"displayName": "Q&A",

	"description": "Questions and answers: Teams users giving a helping hand to other users.",

	"isFavoriteByDefault": true

	},

	{

	"displayName": "Issues and Feedback 🐞",

	"description": "Leave some feedback for the IT-Staff.",

	"isFavoriteByDefault": false

	}

	],

	"memberSettings": {

	"allowCreateUpdateChannels": true,

	"allowDeleteChannels": false,

	"allowAddRemoveApps": true,

	"allowCreateUpdateRemoveTabs": true,

	"allowCreateUpdateRemoveConnectors": true

	},

	"guestSettings": {

	"allowCreateUpdateChannels": true,

	"allowDeleteChannels": false

	},

	"funSettings": {

	"allowGiphy": true,

	"giphyContentRating": "Moderate",

	"allowStickersAndMemes": true,

	"allowCustomMemes": true

	},

	"messagingSettings": {

	"allowUserEditMessages": true,

	"allowUserDeleteMessages": true,

	"allowOwnerDeleteMessages": true,

	"allowTeamMentions": true,

	"allowChannelMentions": true

	},

	"discoverySettings": {

	"showInTeamsSearchAndSuggestions": true

	}

	}
	```

8. Navigate to the **Teams admin center** ([https://admin.teams.microsoft.com/](https://admin.teams.microsoft.com/)) and inspect the newly created teams **Early Adopters** and **Tech Meetings**.

You have successfully created two teams via Graph API. Your test of the Graph functionality is complete, and you can advance to the next exercise.

#### Task 4 – Archive and unarchive a team

After creating the different teams in this lab, you also need to evaluate the different ways of removing teams again. In this task you will test the archiving function and change the Sales team to a non-activate state without deleting its content. This function is required for some company’s compliance requirements of retaining the stored data inside the teams. The only Teams administrative role with sufficient privilege for this task is the Teams service admin, which is currently assigned to Joni Sherman, therefore you will use Joni’s account for this task.

1. Sign in to the **Teams admin center** [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In **Teams**, under **Manage teams**, select the **Sales** team and select **Archive**.

3. Select the checkbox of **Make the SharePoint site read-only for team members** and select **Archive**.

4. Inspect the **Status** of the team.

5. Connect to the **Client 2 VM** with the credentials that have been provided to you.

6. Sign in to **Microsoft Teams web client** ([https://teams.microsoft.com](https://teams.microsoft.com)) as user **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

7. In the **Microsoft Teams web client**, under **Hidden teams**, select the **Sales** team and start a new conversation in the **General** channel.

8. You will see a message **This team was archived, so you can’t post more messages.** The archived status is also indicated by a small box sign, left from the three dots (…) menu, right from the team name.

9.  Connect to the **Client 1 VM** again and use the credentials that have been provided to you.

10. In **Teams**, under **Manage teams**, select the **Sales** team and select **Unarchive**.

11. Connect to the **Client 2 VM** again with the credentials that have been provided to you.

12. Inspect the changes to the **Sales** team.

You have successfully archived a team and reviewed the limited functionality of archived teams. This fulfils the first requirement of testing the archiving function of teams for compliance preservation policies and rules. After this test, you have unarchived the team again, for making it fully operational again. 

#### Task 5 - Delete and recover teams

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Sign in to the **Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Delete the **Sales** team.

3. Sign in to the **Azure Portal** [https://portal.azure.com/](https://portal.azure.com/) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

4. Navigate to **Azure Active Directory** and **Deleted groups**.

5. Restore the **Sales** team.

6. Check the **Teams web client** for the recovered group.

**Note:** The full process of deleting and restoring a team can take up to 24 hours. If it does not appear again, check for it at a later point of this lab again.

You have successfully deleted and restored a via the Teams Desktop client and Azure Admin Portal.

#### Task 6 - Manage team members with dynamic membership

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Sign in to the **Azure Portal** [https://portal.azure.com/](https://portal.azure.com/) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **Azure Active Directory** and **Groups**.

3. Switch **CA-Office** to a group with Dynamic membership, using the following expression:

	- Property: **accountEnabled**

	- Operator: **Equals**

	- Value: **true**

4. Add a second expression:

	- Property: **usageLocation**

	- Operator: **Equals**

	- Value: **CA**

5. Check the **Membership processing status** for members with the correct usage location.

6. Close the Azure Portal.

You have successfully converted a Microsoft 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation "Canada" is added automatically to the team.

### **Exercise 2: Manage sharing and access**

In this exercise, you will test the guest access features in Office 365. To do so, you will configure guest access in Azure AD, add a new external guest user and revoke the guest access by using access reviews.

#### Task 1 - Configure guest access in Teams

In this task, you will configure the guest user access for Microsoft Teams in your tenant.

1. Sign in to the **Teams admin center** [https://admin.teams.microsoft.com/](https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Change the Org-wide settings and allow **Allow guest access in Teams**.

3. Close the Teams admin center.

You have now successfully activated guest user access in Teams for your tenant.

#### Task 2 - Configure guest access in the Azure AD (optional)

In this task, you will configure the guest user access in the Microsoft Azure Portal. You will change the default settings for inviting/creating guest users and then add your personal Outlook.com account as a guest user to your tenant.

**Note**: You need to have a personal outlook.com account for this and the following tasks. If you don’t have an account like this, open your web browser, go to https://outlook.com and create a new account.

1. Sign in to the **Azure Portal** [https://portal.azure.com/](https://portal.azure.com/) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **Azure Active Directory** and **Users**.

3. Create a new guest user with the following settings:

	- **Name:** your full name

	- **Email address:** your Outlook.com email address

	- **First name:** your First name

	- **Last name:** your last name

	- **Personal Message:** Hello Guest, here is the link to access to our Contoso test organization. Best regards, Contoso admin.

	- **Groups**: IT-Department

4. Sign in to the **Outlook Web Portal** ([https://outlook.live.com/owa/](https://outlook.live.com/owa/)) using your personal account.

5. Grant consent and explore the guest access.

You have successfully changed the external collaboration settings, so guests can also invite new guests. Then you have added a personal outlook.com account as a guest to your tenant and as a member to the team "IT-Department".

#### Task 3 – Test external access with sensitivity labels (optional)

Even with enabled guest access sensitivity labels can deny guest access for specific teams. In this task you will try to add a guest user to an internal team. Enabling guest access for teams can take up to 24 hours. If you cannot find the guest user in step 4, you should test it again the next day.

1. Sign in to the **Teams Desktop client** using **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

2. Add the guest user you just invited to the **Teams Rollout** team. You will not be able to find the guest user, because guest users are restricted from this team.

3. Add the guest user to the **Contoso** team and observe the differences.

**Note**: After enabling, it can take up to 24 hours before guest access is available in teams. If you cannot add guest users to any team, return to this task at a later point of this lab.

You have successfully tested the sensitivity labels setting to prevent guest access to a protected team and you can confirm, the labels are working as predicted.

#### Task 4 - Review access to a resource with access reviews

As a part of your system administrator role, you need to review access to resources in your tenant on a regular basis. You can do that by using access reviews in Microsoft Teams.

1. Sign in to the **Azure Portal** [https://portal.azure.com/](https://portal.azure.com/) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **Azure Active Directory** and **Groups**.

3. Onboard to **Access reviews** and create a new access review with the following settings:

	- Review name: **Guest access review**

	- Description: **Reviewing guest access**

	- StartDate: **your current date**

	- Frequency: **One time**

	- EndDate: **your current date + 7 days into the future**

	- Scope: **Guest users only**

	- Group: **IT-Department**

	- Reviewers: **Group owners**

4. Navigate to **Outlook on the web** [https://outlook.office365.com](https://outlook.office365.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

5. Review the access reviews mail and deny access for the guest user in the **IT-Department** team.

6. Close the Outlook on the web window.

You have successfully created a new access review and blocked a guest user in your tenant. This is the end of lab 4. You can close all browser windows and proceed to the next lab.

END OF LAB
