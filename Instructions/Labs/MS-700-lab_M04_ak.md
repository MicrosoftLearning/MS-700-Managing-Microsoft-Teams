---
lab:
    title: 'Lab 04: Manage teams and collaboration settings for Teams'
    type: 'Answer Key'
    module: 'Module 4: Manage chat, teams, channels, and apps in Microsoft Teams'
---

# **Lab 04: Manage teams and collaboration settings for Teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership, and recovering deleted teams. 

In managing collaboration in Microsoft Teams, you will manage chat and collaboration experiences such as team settings or private channel creation policies. Finally, you will manage settings for Teams apps such as app setup policies, Apps, bots & connectors in Microsoft Teams or publish a custom app in Microsoft Teams.

## **Objectives**

After you complete this lab, you will be able to:

- Create a Team from a Microsoft 365 Group

- Create a Team by using PowerShell

- Create a Team by using Microsoft Graph API

- Create a Team with dynamic membership

- Archive and unarchive Teams

- Delete and recover Teams

- Create a messaging policy

- Manage private channels

- Disable third party storage providers

- Manage Policy packages

- Edit and test default org-wide app policy

- Edit and test default app permission policy


## **Lab Setup**

- **Estimated Time:** 120 minutes.

## **Instructions**

### **Exercise 1: Manage team resources**

#### Task 1 - Create a team from an existing Microsoft 365 Group

As part of your pilot project for Contoso, you need to modify the **"IT-Department"** Microsoft 365 Group, created in an earlier lab, and add Teams features to it.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams Desktop client and sign in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.OnMicrosoft.com).

3. The Microsoft Teams Desktop client will start. If a **Bring your team together**, or **Get the Teams mobile app** window appears, close both windows.

4. In the left-hand navigation pane, select **Teams**, select **Join or create a team**, and then select **Create team** from the middle of the window.

5. In the **Create a team** dialog , select **From a group or team**.

6. In the **Create a new team from something you already own** dialog, select **Microsoft 365 group**.

7. In the **Which Microsoft 365 group do you want to use?** dialog select the group **"IT-Department"**, then select **Create**. Wait until the **Creating the team…** process is done.

8. Select the three dots (**…**) right from the new team in the left pane and select **Manage team**.

9. Check, if **Joni Sherman** is still listed below Owners.

10. Select **Members and guests** and check that following members are still listed: **Lynne Robbins**, **Megan Bowen**, **Allan Deyoung** and **Alex Wilber**.

11. Select the **General** channel below the **IT-Department** teams.

12. Close the Teams Desktop client.

You have successfully created a new team with the Teams Desktop client, by using an existing Microsoft 365 Group. Leave the Teams client open and continue with the next task.

#### Task 2 - Create a team by using PowerShell

In this task you will create via the Teams PowerShell a new team **"CA-Office"**. You will create the public channels **"Support"** and **"Recruiting"**. Additionally, you will create the private channel **"Administration"** via Teams PowerShell.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell**.

3. Run the following cmdlet to connect to Microsoft Teams in your tenant:

   ```powershell
   Connect-MicrosoftTeams
   ```

4. A **Sign in** dialog box will open. Enter the **UPN** of **Joni Sherman’s** O365 Credentials provided to you (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and then select **Next**.

5. In the **Enter password** dialog box, enter the **password** of **Joni Sherman’s** O365 Credentials provided to you and then select **Sign in**.

6. Type the following cmdlet to the PowerShell window to create the new team **CA-Office**:

    ```powershell
    New-Team -Displayname "CA-Office" -MailNickName "CA-Office" -Visibility Public
    ```

7. To add the user **Alex Wilber** to the team type the following cmdlet (Replacing **&lt;YourTenant&gt;** with the name of the Microsoft 365 Tenant provided to you.):

    ```powershell
    Get-Team -Displayname "CA-Office" | Add-TeamUser -User AlexW@<YourTenant>.onmicrosoft.com
    ```

8. To add the user **Allan Deyoung** to the team type the following cmdlet (Replacing **&lt;YourTenant&gt;** with the name of the Microsoft 365 Tenant provided to you.):

    ```powershell
    Get-Team -Displayname "CA-Office" | Add-TeamUser -User AllanD@<YourTenant>.onmicrosoft.com
    ```

9. Create a channel **Support** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Support"
    ```

10. Create another channel **Recruiting** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Recruiting"
    ```

11. Create a private channel **Administration** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Administration" -MembershipType Private
    ```

12. Disconnect from the Microsoft Teams environment.  

        ```powershell
        Disconnect-MicrosoftTeams
        ```

13. Close the PowerShell window.

14. Open the Teams Desktop Client from the taskbar. On the left side pane with all teams Joni is a member of the new **CA-Office** team, where you can see a private channel below, named "Administration".

15. Close all browser windows and the Teams Desktop Client.

You have successfully created a team named **CA-Office** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.

#### Task 3 - Create a team by using Graph API

In this task, you will test the Graph API capabilities for certain automation plans of your organization with Teams. For this task, you will create a new team, called **Early Adopters** with minimal settings, such as Public join options, and another team with multiple existing channels, called **Tech Meetings**.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Graph Explorer** at: [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)

3. Select the **Sign in to Graph Explorer** button in the upper left of the page and sign in as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

4. If you access the Graph Explorer for the first time, you will see a **Permissions requested** page. Select **Accept**.

5. Select the **GET** button and select **POST** from the dropdown menu.

6. Do not change the **v1.0** from the box in the middle.

7. Enter the following to the text box next to the **Run query** button:

	- [https://graph.microsoft.com/v1.0/teams](https://graph.microsoft.com/v1.0/teams)

8. Select **Modify permissions** from the top pane.

9. Scroll to the right and select the **Consent** button for the permissions **Group.ReadWrite.All**.

10. Another **Permissions requested** page appears. Select **Accept**.

11. If you are redirected to the Microsoft Developers site, navigate back to the **Graph Explorer** at: [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)

12. Select the **Request body** tab and enter the following code:

    ```json
	{

	"template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('standard')",

	"displayName": "Early Adopters",

	"description": "The Early Adopters Workspace.",

	"visibility": "Public" 

	}
	```

13. Select **Run** **query** from the upper right of the page.

14. After a moment, you should see a green bar below the Request body window, with a checkmark and an **Accepted** message.

15. Remove the whole content of the textbox in the textbox of **Request body**, you just used to create a team and replace it with the following content:

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

16. Select **Run** **query** from the upper right of the page.

17. After a moment, you should see a green bar with a checkmark and **Accepted** inside again.

18. Navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/) to access the Microsoft Teams web client.

19. Select **Teams** and **Manage Teams** from the left-side pane and inspect the newly created teams "**Early Adopters"** and "**Tech Meetings**".

You have successfully created two teams via Graph API. Your test of the Graph functionality is complete, and you can advance to the next exercise.

#### Task 4 – Archive and unarchive a team

After creating the different teams in this lab, you also need to evaluate the different ways of removing teams again. In this task you will test the archiving function and change the Sales team to a non-activate state without deleting its content. This function is required for some company’s compliance requirements of retaining the stored data inside the teams. The only Teams administrative role with sufficient privilege for this task is the Teams Administrator, which is currently assigned to Joni Sherman, therefore you will use Joni’s account for this task.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Teams admin center**: [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/).

3. On the **Pick an account** page, select the **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Select **Teams** from the left-side pane and **Manage teams**.

5. Select the checkmark left from the **Sales** team and select **Archive** from the top pane.

6. Select the checkbox of **Make the SharePoint site read-only for team members** and select **Archive**.

7. The **Status** column should now have changed to **Archived**, written in orange color. Leave the browser open and proceed.

8. Connect to the **Client 2 VM** with the credentials that have been provided to you.

9. Open an Edge browser window and navigate to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/).

10. On the **Pick an account** page, select the **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

11. Select **Use the webapp instead** to open the Teams web client.

12. On the left side, below the teams Lynne is member or owner of, **Hidden teams** is now visible where team and channel names below are all written in italic. Select it to open the menu and select the **General** channel below the **Sales** team. **Note:** If **Hidden teams** is not visible, click the Manage Teams icon to the right of Join or create a team, expand Archived and click Sales.

13. Try to write a new conversation by selecting **New conversation** from the bottom.

14. You will see a message **This team was archived, so you can’t post more messages.** The archived status is also indicated by a small box icon, left from the three dots (…) menu, right from the team name.

15. Connect to the **Client 1 VM** again and use the credentials that have been provided to you.

16. Select the checkbox left from **Sales** again and select **Unarchive** from the top menu. The **Status** field should change to **Active** again.

17. Connect to the **Client 2 VM** again with the credentials that have been provided to you.

18. The text of the **Sales** team and the **General** channel changes back to normal after a moment, but the team is hidden. Select the three dots (…) right from the Sales team and select **Show**.

19. Leave the browser open and stay signed in.

You have successfully archived a team and reviewed the limited functionality of archived teams. This fulfils the first requirement of testing the archiving function of teams for compliance preservation policies and rules. After this test, you have unarchived the team again, making it fully operational again. 

#### Task 5 - Delete and recover teams

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/).

3. On the **Pick an account** page, select the **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In the left-hand navigation pane of the Teams web client, select the three dots (…) right from the **Sales** team and select **Delete the team** from the list.

5. In the **Delete "Sales" team**, select **I understand that everything will be deleted**. and select **Delete team**.

6. Leave the browser open and connect to **Client 1 VM** with the credentials that have been provided to you.

7. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal** at: [https://portal.azure.com](https://portal.azure.com/).

8. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

9. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

10. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

11. On the **Contoso | Overview** page, select **Groups** from the left side pane.

12. On the **Groups | All groups** page, select **Deleted groups** in the left side pane.

13. Now you can see all deleted groups, including the **Sales** group.

14. Select the checkbox left from the **Sales** group and select **Restore group** from the top pane. Confirm the **Do you want to restore deleted groups dialog** by selecting **Yes**.

15. Connect to **Client 2 VM** again with the credentials that have been provided to you.

16. Back on the **Teams web client**, press **F5** to refresh the page.

17. The **Sales** team appears in the list of teams again. Select the three dots (…) right from the team name and select **Manage team**.

18. You can see the owner and all members again in the **Members** tab.

**Note:** The full process of deleting and restoring a team can take up to 24 hours. If it does not appear again, check for it at a later point of this lab.

You have successfully deleted a team via the Teams web client and restored it with the Azure Portal.

#### Task 6 - Manage team members with dynamic membership

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal** at: [https://portal.azure.com](https://portal.azure.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

5. Select **Groups** from the left side pane.

6. In the **Groups | All groups** window, search and select **CA-Office** group.

7. In the **Group** settings, select **Properties** from the left-hand navigation pane.

8. In the **Membership type**, change it from **Assigned** to **Dynamic User**. Select **Add dynamic query** below **Dynamic user members**.

9. In the Dynamic membership rules window enter the following information to the fields:

	- Property: **accountEnabled**

	- Operator: **Equals**

	- Value: **true**

10. After this select **+add expression** and enter the following information to the fields:

	- Property: **usageLocation**

	- Operator: **Equals**

	- Value: **CA**

11. In the Dynamic membership rules window select **Save** in the top navigation pane.

12. In the **CA-Office| Properties** window select **Save** in the top navigation pane.

13. A warning message is displayed, that the membership will change according to the new dynamic membership rules. Select **Yes** to confirm the message.

14. Select **Overview** in the left-hand navigation pane of the **CA-Office** group window.

15. In the Overview window, locate **Membership processing status** field. Wait and refresh your browser, until the status says **Update complete**. It may take several minutes for the change to be processed.

16. Then select **Members** in the left-hand navigation pane and then select **Refresh**. Verify that **Alex Wilber** is in the list of members, but that **Allan Deyoung** has been removed from the group.

17. Select Owners from the left-hand navigation pane and verify, that Joni is still the Owner of the group, even if she does not match the dynamic group criteria.

You have successfully converted a Microsoft 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation "Canada" is added automatically to the team.


### **Exercise 2: Configure channel and message policies**

In this exercise you will configure policies to manage the creation of new private channels and the available tools for users in chat.

#### Task 1 - Create messaging policy for giphy, memes and stickers

In the past, some users of Contoso have used a lot of stickers, gif animations and similar pictures in their conversations, even with externals using other chat solutions. The new corporate guideline shall prohibit the use of graphic elements in corporate communication via Teams, because users shall not use them in conversations with external customers and clients. As a Teams service administrator, you must create a new message policy that prohibits its use and apply it to several users of your pilot project.

**Note:** After creating a messaging policy, it can take up to 24 hours for the settings to be applied to the users.

1. Connect to the Client 1 VM with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Teams admin center** at [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/).

3. On the **Pick an account** page, select the **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In the left-hand navigation pane, select the **Messaging policies**, then click on the **+ Add** at the right side of the page, to create a new messaging policy.

5. In the **New messaging policy** dialog enter the following information to the fields and set the following configuration:

	- **Name**: Regular users without fun stuff

	- **Description**: Policy to disable giphys, stickers, and memes in conversations

	- **Use Giphys in conversations**: off

	- **Use Memes in conversations**: off

	- **Use Stickers in conversations**: off

6. Leave the rest of the settings as default. Select **Save**.

7. In the Messaging policies overview, select the checkmark left to **Regular users without fun stuff**. Then select **Manage users** in the top navigation pane. If you cannot see **Manage users**, you may need to select the three dots first.

8. Type in **Lynne Robbins** and select **Add**, and then select **Apply**.

9. Stay in the Teams admin center and continue with the next task.

In this task, you have successfully configured a new messaging policy and assigned it to Lynne Robbins. It will now take some time for the policy to take effect. Continue with the next task.

#### Task 2 - Manage private channels in a team

As Teams administrator of Contoso, you will create a private channel "confidential" in the sales team that only allows some people to be able to access the information.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in as **Joni Sherman** in the **Microsoft Teams Admin center**.

3. In the left-hand navigation pane, select **Teams** to open the menu and **Manage teams** below.

4. Select the **Sales** team in the **Manage teams** overview window.

5. Select the **Channels** tab in the middle of the page. Select **+ Add** in the navigation pane below to get into the **Add channel** window.

6. In the **Add channel** window enter the following information:

	- **Name:** Confidential sales

	- **Description:** Confidential private sales channel

	- **Type:** Private

7. Enter to the field **Channel owner** the user **Lynne Robbins** and select her as owner.

8. Select **Apply** in the **Add channel** window.

9. Connect to the **Client 2 VM** with the credentials that have been provided to you.

10. Open the Edge browser with the icon from the taskbar.

11. In your browser, select the address bar and go to the **Teams Web Client** page by entering the following URL: [**https://teams.microsoft.com**](https://teams.microsoft.com/)

12. On the **Pick an account** page, select the **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

13. On the Microsoft Teams landing page click **Use the web app instead**.

14. On the team overview in the Teams web client, you should see the new private channel **Confidential sales** with a small padlock icon.

In this task you learned how to create a private channel in the Microsoft Teams Admin center and how to configure and check the access.

### **Exercise 3: Manage app settings**

#### Task 1 - Disable third party storage providers

In the past, users stored data at various locations, including third-party storage providers. Recently, the company deployed OneDrive for all users and would like to guide the users to use SharePoint and OneDrive as the primary data storage locations with Box as an alternative for all file collaborations. As the Teams admin, you are asked to deactivate all third-party storage providers except Box in Microsoft Teams to align with the direction.

**Note:** After disabling the third-party storage provider, it can take up to 24 hours for the settings to be applied to the teams.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in as **Joni Sherman** in the **Microsoft Teams Admin center**.

3. On the left-side navigation pane, select the **Org-wide settings** to open the menu, then select **Teams settings** below.

4. In the Teams settings overview go to the **Files** section. Configure the following file sharing and cloud file storage options.

	- **Citrix files:** Off

	- **DropBox:** Off

	- **Box:** On

	- **Google Drive:** Off

	- **Egnyte:** Off

5. After this scroll down and select **Save**.

In this task you have learned how to enable or disable third-party storage providers for your whole tenant.

#### Task 2 - Edit default org-wide app policy

In the pilot project, the company decided that Microsoft Planner is the default app for all (existing) teams. To do this, edit the default org-wide app policy. This task may take some time to propagate throughout the tenant.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in as **Joni Sherman** in the **Microsoft Teams Admin center**.

3. In the left-hand navigation pane, select the **Teams apps** to open the menu, then select **Setup policies**.

4. In the **App setup policies** window select **Global (Org-wide default)** name to open the org-wide app policy.

5. In the **Pinned apps** section select **+ Add apps** to open the **Add pinned apps** menu at the right side.

6. Select **Global** and type in the name **Planner**, mouseover the presented name and select **Add**. After this, select **Add** to return previous window.

7. Make sure that **Planner** is now listed in the **Pinned apps** section and select **Save**.

8. In the **App setup policies** window select **Global (Org-wide default)** and make sure there is a selected checkmark in the front of the name.

9. Then select **Manage users** in the top navigation pane to open the **Mange users** dialog. Enter the name of **Lynne Robbins** and mouseover the presented name and select **Add**. Then select **Apply**.

10. Connect to the **Client 2 VM** with the credentials that have been provided to you.

11. Open the Edge browser, select the address bar and go to the **Teams Web Client** page by entering the following URL: [**https://teams.microsoft.com**](https://teams.microsoft.com/)

12. On the **Pick an account** window, select LynneR@&lt;YourTenant&gt;.onmicrosoft.com and sign in.

13. On the Microsoft Teams landing page click **Use the web app instead**.

14. In the left-hand navigation pane, the **Planner** app should be displayed by default below the Files **menu**.

#### Task 3 - Edit default app permission policy

In this task you will edit the default app permission policy and block the Google Analytics app for all tenants

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in as **Joni Sherman** in the **Microsoft Teams Admin center**.

3. In the left-hand navigation pane, select the **Teams apps** to open the menu, then select **Permission policies**.

4. In the **App permission policies** window select **+ Add** to create a new policy.

5. After this the policy creation dialog appears, type in the policy name **Block Google Analytics** and expand the menu in the **Third-party app** section, and select **Block specific apps and allow all others**.

6. Select **Block apps** below the Notification **Add apps that you want to block** to open the right-side menu.

7. In the Add third party apps dialog, type in **Google Analytics**, mouseover the presented name and select **Add**. Repeat the same step for **Google Analytics Insights**. After this select **Block** to return to the **App permission policies** window. Select **Save**.

8. In the App permission policies overview, select the checkmark left to **Block Google Analytics**. Then select **Manage users** in the top navigation pane.

9. Type in **Lynne Robbins** and select **Add** by mouseover the presented name, then click **Apply**.

In this task you have learned how to block the Google Analytics app for your tenant.

#### Task 4 – Manage policy packages

To avoid administrative overhead with managing large numbers of policies individually for groups of different users, you need to evaluate using policy packages to group policies into logical units. In this task you need to review the default policy packages and change a default policy package for first line workers.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in as **Joni Sherman** in the **Microsoft Teams Admin center**.

3. In the left-hand navigation pane, select **Policy packages** to display existing policy packages.

4. Review the existing policy packages. Afterwards select **Frontline worker** to edit the policy package.

5. From the list of assigned policies, select **Frontline_Worker** right from **Messaging policy**.

6. Select **Edit** from the upper right corner to change the policy settings.

7. Select the switch right from **Send urgent messages using priority notifications** to **On** and select **Save**.

8. Back on the list of assigned policies, select **Frontline_Worker** right from **Calling policy**.

9. Select the switch right from **Prevent toll bypass and send calls through the PSTN** and **Busy on busy is available when in a call** to **On** and select **Save**.

10. Back on the list of assigned policies again, select **Back** to go to the Policy packages overview.

11. The checkmark left from the **Frontline worker** policy package is still active. Select **Manage users** from the top pane to open the **Manage users** right-side pane.

12.  Type "Allan" into the search bar, select **Add** right from **Allan Deyoung** and **Apply**.

13. Select **Users** from the left-side pane.

14. In the line of Allan Deyoung, select **View policies**.

15. Below Assigned policies you can now see the different **Frontline_Worker** policies and below **Policy package** the **Frontline worker** package.

You have successfully modified included policies from an existing policy package and assigned the package to a single user. This will help you assign the same set of policies to a group of users working in the same role or requiring the same access.



#### Task 5 - Built a flow using Power Automate in Teams

In this task, you will create an issue report system by using Power Automate in Teams. When users fill out the form from **Contoso** org-wide team, the flow will send a message to notify members in **Group_IT-Department_United State** team. 

1. Connect to the **Client 1 VM** and browse to Forms web client (https://www.office.com/launch/forms) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a from

	1. In the Froms web client, select **+ New Form**.

	2. Select on **Untitled form** and enter the following information:
	
		* Input your title here: **Submit a ticket**.
		* Enter a description: **Please provide the information. Our member from IT-Department will contact you as soon as possible.**

	2. Select **+ Add new** > **Text**.
	3. In the question textbox, enter **What is the issue?**

3. Install **Power Automate** in Teams. 

	1. Browse to Teams web client (https://teams.microsoft.com/) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	2. In left navigation of the Teams client, select **Apps** and search for **Power Automate**.

	3. Select **Power Automate** app, and select **Add**

4. Create a flow

	1. In left navigation of the Teams client, select **Power Automate**.

	2. Select **Create** tab from the top menu. 

	3. Select the template **Notify a team when a new Forms response is submitted** and select **Continue**

	4. Enter the flow name : **Report issue**. Select **Continue**.

	5. On the **Set up your flow** page, 
	
		* From the **The ID of the form you want to monitor** dropdown menu, select **Submit a ticket**. 

		* From the **Team to notify** dropdown menu, select **IT-Department**.

		* From the **Channel to notify** dropdown menu, select **General**.

	6. Select **Create flow** > **Done**

5. Add the form to the **General** channel of **Contoso** team.

	1. Go to the **General** channel of **Contoso** team.
	2. Add a tab by selecting **+** next to Wiki tab. 
	3. Select **Forms** from the **Add a tab** window. 
	4. Select **Add an existing form**, and select **Submit a ticket**.	
	5. Select **Save**.

6. Test the flow

	1. In the **General** channel of **Contoso** team, select **Fill|Submit a ticket** tab. 
	2. On the **Submit a ticket** page, enter the following to the textbox:
	
		*I need help to create a team for external partners.*  
	3. Select **Submit**.
	4. Go to the **General** channel of **Group_IT-Department_United State** team. You will see a post via Power Automate. 

In this task, you have successfully created a flow from Power Automate in Teams, which notify the members in IT department when users submit a request ticket. 

### **Exercise 3: Test configured policy settings**

In this exercise, you will test the configured policy settings on a client with the affected user Lynne Robbins and compare the settings to the available client settings of Joni Sherman.

#### Task 1 – Test the messaging policy and private channel access

In this task, you will test the **messaging policies** configured in exercise 1 and compare the difference between affected user (Lynne Robbins) vs regular user(Joni Sherman).

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Edge Browser** icon from the taskbar. In your browser, go to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

3. On the **Pick an account** page, select the **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. On the Microsoft Teams landing page click **Use the web app instead**.

5. Skip a potential welcome dialog by selecting on **x** in the right corner.

6. In the left-hand navigation pane, select **Chat**, then select the **Contacts** in the dropdown menu.

7. If there is no contact for **Joni Sherman**, then select **…** and select **Add a contact to this group**. Type in the name **Joni Sherman** and select her by mouseover the presented name. After this select **Add** to return to the **Contacts tab**.

8. In the **Contacts** tab, select **Joni Sherman**. Note that if the **giphy**, **memes** and **stickers** icons are missing below the conversation-bar, the **messaging policy** has taken effect.

9. In the left-hand navigation pane, select **Teams**.

10. Select the **Confidential sales** channel of the **Sales** team and add a comment to confirm that you have access to the private channel.

#### Task 2 – Test the app permission policy and storage providers

In this task, you will test the **app permission policies** configured in exercise 2 and compare the differences between affected user (Lynne Robbins) vs regular user (Joni Sherman).

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. You are still in the **Teams web client** and signed in as **Lynne Robbins**.

3. In the left-hand navigation select **Teams** and select the **IT-Department** channel **General**. Mouseover the presented name **General**, select **…** and then select **Connectors**.

4. In the **Connectors for "General"** window, enter **Google Analytics** into the search field.

5. If you can’t find **Google Analytics** as a search result and can’t add the app to the channel, the **app permission policy** has worked as desired.

6. In the left-hand navigation pane, select **Teams**, then select the **IT-Department** team. Select the **files** Tab on the middle of the Teams web client. Then select **+ Add cloud storage** in the navigation pane below.

7. If you only see SharePoint and Box as options, the cloud file storage settings in Teams settings worked as expected.

8. Sign out of Teams and close all open windows.

END OF LAB
