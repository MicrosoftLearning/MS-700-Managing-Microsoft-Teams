---
lab:
    title: 'Lab 04: Manage teams'
    type: 'Answer Key'
    module: 'Module 4: Deploy and manage teams'
---

# **Lab 04: Manage teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership, and recovering deleted teams. In the second half of this lab, you will configure the guest access for your tenant and review access for both, internal and external users.

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

12. Close the PowerShell window.

13. Open the Teams Desktop Client from the taskbar. On the left side pane with all teams Joni is a member of the new **CA-Office** team, where you can see a private channel below, named "Administration".

14. Close all browser windows and the Teams Desktop Client.

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

10. In the **Microsoft Azure portal**, below the **Azure services** section, select **More services**.

11. On the **All services** page, select **Identity** from the left side navigation pane and **Azure Active Directory** from the main window.

12. On the **Contoso | Overview** page, select **Groups** from the left side pane.

13. On the **Groups | All groups** page, select **Deleted groups** in the left side pane.

14. Now you can see all deleted groups, including the **Sales** group.

15. Select the checkbox left from the **Sales** group and select **Restore group** from the top pane. Confirm the **Do you want to restore deleted groups dialog** by selecting **Yes**.

16. Connect to **Client 2 VM** again with the credentials that have been provided to you.

17. Back on the **Teams web client**, press **F5** to refresh the page.

18. The **Sales** team appears in the list of teams again. Select the three dots (…) right from the team name and select **Manage team**.

19. You can see the owner and all members again in the **Members** tab.

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

### **Exercise 2: Manage sharing and access**

In this exercise, you will test the guest access features in Office 365. To do so, you will configure guest access in Azure AD, add a new external guest user and revoke the guest access by using access reviews.

#### Task 1 - Configure guest access in Teams

Now that you have explored the Teams admin center it is time to configure the first setting. Since this task will take some time to replicate through the tenant, you will configure the guest user access for Microsoft Teams right now, so it is available for later use.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Sign in to the **Teams admin center** [https://admin.teams.microsoft.com/](https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the **Microsoft Teams admin center** page, select the cogwheel from the lower left side pane and open the **Org-wide settings** menu. 

4. Select **Guest access** from the list.

5. On the **Guest access** page, use the drop box right of **Allow guest access in Teams** and select **On**. Scroll down and select **Save**.

6. Close all browser windows.

You have now successfully activated guest access for Teams in your tenant.

#### Task 2 - Configure guest access in the Azure AD (optional)

In this task, you will configure the guest user access in the Microsoft Azure Portal. You will change the default settings for inviting/creating guest users and then add your personal Outlook.com account as a guest user to your tenant.

**Note**: You need to have a personal Outlook.com account for this and the following tasks. If you don’t have an account like this, open your web browser, go to [**https://outlook.com**](https://outlook.com/) and create a new account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com/).

3. You should be still logged in as **MOD Administrator**. If not, on the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

5. Select **Users** from the left side pane.

6. In the **Users – All users** window, select **+ New guest user** from the top pane to create a new **Guest User**.

7. In the **New user** window select **Invite user** and enter the following information to the fields:

	- **Name**: your full name

	- **Email address**: your Outlook.com email address

	- **First name**: your First name

	- **Last name**: your last name

	- **Personal Message**: Hello Guest, Here is the link to access our Contoso test organization. Best regards, Contoso admin.

 

8. In the Groups and roles section, select **0 groups selected**. In the Groups window on the right side, select the **IT-Department** group, scroll down and return to the New user window by choosing **Select**.

9. To finish the invitation process, select **Invite** from the lower left side of the window.

10. You can now see a new user on the **Users – All users** page, note that the **User type** is set to **Guest**.

11. Open a **New InPrivate window** in your browser and go to the **Outlook Web Portal** page by entering the following URL in the address bar: [**https://outlook.live.com/owa/**](https://outlook.live.com/owa/)

12. In the top right navigation pane, select **Sign In**.

13. In the **Sign in** window, enter the **Email address** which you have created before.

14. In the **Enter password** dialog box, enter the password and select **Sign in**.

15. After signing in, open your **Inbox** and open the invitation Email with the topic **You’re invited to the Contoso organization**.

16. When you select **Get Started** from the invitation Email, a new tab with a **Review permissions** message opens. Grant your consent to **Contoso** by selecting **Accept**.

17. Your personal outlook account has now been added to both your test tenant of Contoso Ltd. and to the "IT-Department" team.

18. Close the InPrivate window.

You have successfully changed the external collaboration settings, so guests can also invite new guests. Then you have added a personal outlook.com account as a guest to your tenant and as a member to the team "IT-Department".

#### Task 3 – Test external access with sensitivity labels (optional)

Even with enabled guest access sensitivity labels can deny guest access for specific teams. In this task you will try to add a guest user to an internal team. Enabling guest access for teams can take up to 24 hours. If you cannot find the guest user in step 4 you should test it again the next day.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open the Microsoft Teams Desktop Client, where you are signed in as **Megan Bowen**.

3. On the Teams overview select the three dots (**…**) right next to the Team "**Teams Rollout"** then select **Add member** from the dropdown list.

4. On the **Add members to Teams Rollout** page, enter the name of the guest user you just invited.

5. You will not be able to find the guest user, because guest users are restricted from this team.

6. Perform the steps 3 and 4 for the **Contoso** team, where you can find and add the guest user to the **Contoso** team.

7. Select **Close.**

**Note:** It can take up to 24 hours after enabling, till guest access is available in teams. If you cannot add guest users to any team, return to this task at a later point of this lab.

You have successfully tested the sensitivity labels setting to prevent guest access to a protected team and you can confirm, the labels are working as predicted.

#### Task 4 - Review access to a resource with access reviews

As a part of your system administrator role, you need to review access to resources in your tenant on a regular basis. You can do that by using access reviews in Microsoft Teams.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

5. Select **Groups** from the left-hand navigation pane.

6. In the **Groups - All groups** window, select **Access reviews** in the left-hand navigation pane.

7. If you see the option **Onboard now** in the middle of the Page, select it and proceed to the next step. Otherwise, skip to step 13.

8. In the left-hand navigation pane select **Onboard**, to enable the **Access reviews** select **Onboard Now** at the bottom of the page.

9. After this you will return to the home of the **Azure Portal**. Select the **notification Bell** above the **navigation pane**. In the notification window you will see the message that the onboarding of the Access review was successful configured.

10. Close the notification window by selecting **X** in the right corner.

11. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

12. Select **Groups** from the left-hand navigation pane and on the **Groups - All groups** window, select **Access reviews** in the left-hand navigation pane again.

13. In the middle of the page select **+ New access review** and follow the steps below to create a new Access review.

	- On the **Review type** section of the **New access review** page, select the radio button beside **Select teams + Groups**
	- select **Select goroup(s)** and chose the Group: **IT-Department**
	- select the radio button beside **Guest users only**
	- select **Next:Reviews**

14. Under the **Reviews** section, follow the steps:

	- select **Group owner(s)** in the **Select reviewers** dropdown menu.
	- In the **Specify recurrence of review**, select **One time**, for **Duration (in days)** enter **7**, and use todays date for **Start date**  
	- select **Next:Settings**

15. Under the **Settings** section, follow the steps:

	- set **Auto apply results to resource** to **enabled**, and leave others settings as default. 
	- select **Next:Review+Create**

16. Under the **Review+Create** section, enter the following information to the fields:

	- Review name: **Guest access review**
	- Description: **Reviewing guest access**
	- Select **Create**. 

	The system automatically creates an Email for the Access Reviewer.

17. In the browser window, select the circle with **MA** in the upper right corner, open the side pane and select **Sign out**.

18. Close your browser window and open it again by selecting the Edge browser icon from the taskbar.

19. In your browser, select the address bar and go to the **Outlook on the web** page by entering the following URL: [**https://outlook.office365.com**](https://outlook.office365.com/)

20. When you see the **Pick an account** window, select the **Joni Sherman account** to get to the Sign in window. If there is no **Joni Sherman account**, select **Use another account** to get to the Sign in window.

21. In the **Sign in** window, enter the UPN of **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and select **Next**.

22. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

23. If a welcome screen appears, close it.

24. In the middle of the page, you will see an Email from **Microsoft Azure** with the topic **Action required: Review group access by &lt;local date + 7 days in the future&gt;**, then select this Email.

25. Select the **Start review** button in this Email.

26. An additional browser tab will open.

27. In the Access Review Window, you can see an overview with configured settings and the configured guest user with your personal outlook.com email address.

28. Select your outlook.com guest and then select **Details** to review the guest statistics.

29. Select **Deny** from the available options and select **Submit**.

30. In the overview, your outlook.com guest user has now **Denied** access.

31. Close all windows.

You have successfully created a new access review and blocked a guest user in your tenant. This is the end of lab 4. You can close all browser windows and proceed to the next lab.

END OF LAB
