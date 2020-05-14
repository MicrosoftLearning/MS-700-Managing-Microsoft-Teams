--- 
lab: 
    title: 'Lab: Manage teams'
    type: 'Answer Key' 
    module: 'Module 04 : Deploy and manage teams' 
---

# Lab 04: Manage teams 
# Student lab answer key
## Lab Scenario  

In the labs of this course, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership and recovering deleted teams. In the second half of this lab, you will configure the guest access for your tenant and review access for both, internal and external users.
 
## Objectives

After you complete this lab, you will be able to:

- Create a Team from an Office 365 Group
- Create a Team by using PowerShell
- Create a Team with dynamic membership
- Delete and recover Teams
- Configure guest access in Azure and Teams
- Review Access to a resource 

## Lab Setup  

- **Estimated Time:** 90 minutes.

## Instructions



### Exercise 1: Manage team resources


#### Task 1 - Create a Team from the Office 365 Group 

As part of your pilot project for Contoso, you need to modify the **"IT-Department"** Office 365 Group, created in an earlier task of this lab, and add Teams features to it.
 
1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. After signing in, open **Teams Desktop client** from the icon in the taskbar.

3. If you are already signed with **Joni** in at the Teams Desktop client, you can continue with step 7. 

4. If you are not signed in already, you will be asked to **Enter your work, school or Microsoft account**., which is the UPN of Joni (JoniS@_YourTenant_.OnMicrosoft.com). Enter it and select **Sign in**. 

5. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

6. The Microsoft Teams Desktop client will start. If a **Bring your team together** window appears, or **Get the Teams mobile app**, close both windows.

7. In the left-hand navigation pane, select **Teams**, select **Join or create a team**, and then select **Create a team** from the middle of the window.

8. In the **Create your team** dialog Select **Create from…**, in the **Create a new team from something you already own** dialog select **Office 365 group**. 

9. In the **Which office 365 group do you want to use?** dialog select the group **“IT-Department”**, then select **Create**. Wait until the **Creating the team…** process is done.

10. Select the three dots (**…**) right from the new team in the left pane and select **Manage team**.

11. Check, if **Joni Sherman** is still listed below Owners

12. Select **Members and guests** and check that following members are still listed: **Lynne Robbins**, **Megan Bowen**, **Allan Deyoung** and **Alex Wilber**.

13. Select the **General** channel below the **IT-Department** teams.
 
You have successfully created a new team with the Teams Desktop client, by using an existing Office 365 Group. Leave the Teams client open and continue with the next task.


#### Task 2 - Create a new team by using PowerShell

In this task you will create via the Teams PowerShell a new team **"CA-Office"**. You will create the public channels **"Support"** and **"Recruiting"**. Additionally, you will create the private channel **"Administration"** via Teams PowerShell. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Right click on the Windows symbol in the lower left corner (Start) and select **Windows PowerShell (Admin)**.

3. Confirm the **User Account Control** dialog with **Yes**.

4. Check if the correct version of the MicrosoftTeams module is installed, by using the following cmdlet:

	```powershell
	Get-InstalledModule MicrosoftTeams
	```

5. If the Version equals **1.0.18** or above, continue with step 9. If no results are returned or an older version, uninstall the old PowerShell module first by running the following cmdlet (if required):

	```powershell
	Uninstall-Module MicrosoftTeams
	```

	 >**Note:** If the Uninstall-Module command fails, close the PowerShell window, repeat steps 2 and 3 above to open a new Windows PowerShell (Admin) window, and then repeat this step.

6. Now register the PSGalleryInt as trusted repository by using the following cmdlet. Confirm NuGet related install messages with **[Y] Yes**:

	```powershell
	Register-PSRepository -Name PSGalleryInt -SourceLocation https://www.poshtestgallery.com/ -InstallationPolicy Trusted
	``` 

7. Now you can install the required MicrosoftTeams PowerShell module, by using the following cmdlet:

	```powershell
	Install-Module MicrosoftTeams -Repository PSGalleryInt -Force
	```

8. Check again, if the required module is installed now, by using the following cmdlet:

	```powershell
	Get-InstalledModule MicrosoftTeams
	```

9. If the correct version is displayed, type in the following cmdlet to connect to Microsoft Teams in your tenant:  

	```powershell
	Connect-MicrosoftTeams
	```

10. A **Sign in** dialog box will open. Enter the **UPN** of **Joni Sherman’s** O365 Credentials provided to you (for example, **JoniS@_YourTenant_.onmicrosoft.com**) and then select **Next**.  

11. In the **Enter password** dialog box, enter the **password** of **Joni Sherman’s** O365 Credentials provided to you and then select **Sign in**. 

12. Type the following cmdlet to the PowerShell window to create the new team **CA-Office**: 

	```powershell
	New-Team -Displayname “CA-Office” -MailNickName “CA-Office” -Visibility Public
	``` 

13. Write down the string displayed below **GroupId**, or copy them to your clipboard, because you will need it in the next steps (for example, **”d594c2da-4832-4b56-a3c0-f9252f8bb78a”**)

14. To add the user **Alex Wilber** to the team type the following cmdlet: 

	```powershell
	Add-TeamUser -GroupId <GroupID> -User AlexW@_YourTenant_.onmicrosoft.com
	```

15. To add the user **Allan Deyoung** to the team type the following cmdlet: 

	```powershell
	Add-TeamUser -GroupId <GroupID> -User AllanD@_YourTenant_.onmicrosoft.com
	```

16. Create a channel **Support** in the **CA-Office** team by using the following cmdlet:

	```powershell
	New-TeamChannel -GroupId <GroupID> -DisplayName "Support”
	``` 

17. Create another channel **Recruiting** in the **CA-Office** team by using the following cmdlet:

	```powershell
	New-TeamChannel -GroupId <GroupID> -DisplayName "Recruiting"
	``` 

18. Create a private channel **Administration** in the **CA-Office** team by using the following cmdlet:

	```powershell
	New-TeamChannel -GroupId <GroupID> -DisplayName "Administration" -MembershipType Private
	```

19. Close the PowerShell window.

20. Switch into the Teams Client again and, on the left side pane with all teams Joni is a member of, you should see the new **CA-Office** team.

You have successfully created a team named **CA-Office** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.


#### Task 3 - Delete and recover teams 

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. After signing in, open **Teams Desktop client** from the icon in the taskbar, if the client is not running already.

3. Make sure you are logged in as Joni Sherman and if not, sign in.

4. In the left-hand navigation pane of the Teams Desktop client, select the three dots (…) right to the IT-Department team and select **Delete the team** from the list.

5. In the **Delete “IT-Department” team**, select **I understand that everything will be deleted**. and select **Delete team**.

6. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com). 

7. Sign in with the account of Joni Sherman by entering her UPN (JoniS@_YourTenant_.OnMicrosoft.com) and select **Sign in**. 

8. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

9. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**

10. On the **Contoso – Overview** page, select **Groups** from the left side pane.

11. On the **Groups - All groups** page, select **Deleted groups** in the left side pane.

12. Now you can see all deleted groups, including the **IT-Department** group.

13. Select the checkbox left from the **IT-Department** group and select **Restore group** from the top pane. **Confirm** the **Do you want to restore deleted groups dialog** with selecting **Yes**.

14. Switch back to the **Teams Desktop client** browser and press **F5** to refresh.

15.  The IT-Department team appears in the list of teams again. Select the three dots (…) right from the team name and select **Manage team**.

16. You can see the owner and all members again in the **Members** tab.

You have successfully deleted and restored a via the Teams Desktop client and Azure Admin Portal.


#### Task 4 - Create team with dynamic membership

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com). 

3. When you see the **Pick an account** window, select the **MOD Administrator account** to get to the Sign in window. If the is no **MOD Administrator account**, select **Use another account** to get to the Sign in window.

4. In the **Sign in** window, enter the UPN of **MOD Administrator** (admin@m365xzzzzzz.onmicrosoft.com) and select **Next**.

5. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

6. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

7. Select **Groups** from the left side pane.

8. In the **Groups - All groups** window, search and select **CA-Office** group.

9. In the **Group** settings, select **Properties** from the left-hand navigation pane.

10. In the **Membership type**, change it from **Assigned** to **Dynamic User**. Select **Add dynamic query** below **Dynamic user members**.

11. In the Dynamic membership rules window enter the following information to the fields:

	- **Property** accountEnabled
	- **Operator** Equals
	- **Value** true

12. After this select **+add expression** and enter the following information to the fields:

	- **Property** usageLocation
	- **Operator** Equals
	- **Value** CA

13. In the Dynamic membership rules window select **Save** in the top navigation pane.

14. In the **CA-Office– Properties** window select **Save** in the top navigation pane.

15. A warning message is displayed, that the membership will change according to the new dynamic membership rules. **Confirm** the message with selecting **Yes**.

16. Select **Overview** in the left-hand navigation pane of the **CA-Office** group window.

17. In the Overview window, locate **Membership processing status** field. Wait and refresh your browser, until the status says **Update complete**. It may take several minutes for the change to be processed. 

18. Then select **Members** in the left-hand navigation pane and then select **Refresh**. Verify that **Alex Wilber** is in the list of members, but that **Allan Deyoung** has been removed from the group. 

19. Select Owners from the left-hand navigation pane and verify, that Joni is still the Owner of the group, even if she does not match the dynamic group criteria.

You have successfully converted an Office 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation “Canada" is added automatically to the team. 



### Exercise 2: Manage sharing and access

In this exercise, you will test the guest access features in Office 365. To do so, you will configure guest access in Azure AD, add a new external guest user and revoke the guest access by using access reviews.


#### Task 1 - Configure guest access in Teams

In this task, you will configure the guest user access for Microsoft Teams in your tenant. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com) to access the **Microsoft Teams admin center**. 

3. On the **Pick an account** window, select admin@_YourTenant_.onmicrosoft.com and sign in.

4. On the **Microsoft Teams admin center** page, select the cogwheel from the lower left side pane and open the **Org-wide settings** menu. Select **Guest access** from the list.

5. On the **Guest access** page, use the slider right from **Allow guest access in Teams** by selecting it. When it is turned to **On**, scroll down and select **Save**.

You have now successfully activated guest user access in Teams for your tenant.


#### Task 2 - Configure guest access in the Azure AD (optional)

In this task, you will configure the guest user access in the Microsoft Azure Portal. You will change the default settings for inviting/creating guest users and then add your personal Outlook.com account as a guest user to your tenant.

**Note**: You need to have a personal Outlook.com account for this and the following tasks. If you don’t have an account like this, open your web browser, go to [**https://outlook.com**](https://outlook.com/) and create a new account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com). 

3. When you see the **Pick an account** window, select the **MOD Administrator account** to get to the Sign in window. If the is no **MOD Administrator account**, select **Use another account** to get to the Sign in window.

4. In the **Sign in** window, enter the UPN of **MOD Administrator** (admin@_YourTenant_.onmicrosoft.com) and select **Next**.

5. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

6. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

7. Select **Users** from the left side pane.

8. Select **User settings** in the left side navigation pane.

9. Scroll down if required and select **Manage external collaboration settings**.

10. In the **External collaboration settings** window make change **Guests can invite** to **Yes**. 

11. Select **Save** in the top navigation pane and select **User – User Settings** from the upper left navigation. 

12. On the **Users - User settings** page, select **All users** in the left-hand navigation pane.

13. In the **Users – All users** window, select **+ New guest user** from the top pane to create a new **Guest User**.

14. In the New user window select **Invite user** and enter the following information to the fields:

	- **Name**: *your full name*
	- **Email address**: *your Outlook.com email address*
	- **First name**: *your First name*
	- **Last name**: *your last name*
	- **Personal Message**: Hello Guest, Here is the link to access to our Contoso test organization. Best regards, Contoso admin.

15. In the Groups and roles section, select **0 groups selected**. In the Groups window on the right side, select the **IT-Department** group, scroll down and return to the New user window by choosing **Select**.

16. To finish the invitation process, select **Invite** from the lower left side of the window.

17. You can now see a new user on the **Users – All users** page, note that the **User type** is set to **Guest**.

18. Open a **New InPrivate window** in your browser and go to the **Outlook Web Portal** page by entering the following URL in the address bar: [**https://outlook.live.com/owa/**](https://outlook.live.com/owa/)

19. In the top right navigation pane, select **Sign In**. 

20. In the **Sign in** window, enter the **Email address** which you have created before.

21. In the **Enter password** dialog box, enter the password and select **Sign in**.

22. After signing in, open your **Inbox** and open the invitation Email with the topic **You're invited to the Contoso organization**.

23. When you select **Get Started** from the invitation Email, a new tab with a **Review permissions** message opens. Grant your consent to **Contoso** by selecting **Accept**.

24. Your personal outlook account has now been added to your test tenant of Contoso Ltd. and also to the “IT-Department” team.

25. Close the InPrivate window.

You have successfully changed the external collaboration settings, so guests can also invite new guests. Then you have added a personal outlook.com account as a guest to your tenant and as a member to the team “IT-Department”.
 

#### Task 3 - Review access to a resource with access reviews

As a part of your system administrator role, you need to review access to resources in your tenant on a regular basis. You can do that by using access reviews in Microsoft Teams. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [https://portal.azure.com](https://portal.azure.com). 

3. When you see the **Pick an account** window, select the **MOD Administrator account** to get to the Sign in window. If the is no **MOD Administrator account**, select **Use another account** to get to the Sign in window.

4. In the **Sign in** window, enter the UPN of **MOD Administrator** (admin@_YourTenant_.onmicrosoft.com) and select **Next**.

5. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

6. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

7. Select **Groups** from the left-hand navigation pane.

8. In the **Groups - All groups** window, select **Access reviews** in the left-hand navigation pane. 

9. If you see the option **Onboard now** in the middle of the Page, select it and proceed to the next step. Otherwise, skip to the step 15.

10. In the left-hand navigation pane select **Onboard**, to enable the **Access reviews** select **Onboard Now** at the bottom of the page.

11. After this you will return to the home of the **Azure Portal**. Select the **notification Bell** above the **navigation pane**. In the notification window you will see the message that the onboarding of the Access review was successful configured. 

12. Close the notification window by selecting **X** in the right corner.

13. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

14. Select **Groups** from the left-hand navigation pane and on the **Groups - All groups** window, select **Access reviews** in the left-hand navigation pane again.

15. In the middle of the page select **+New access review** to create a new Access review.

16. In the Create an access review window enter the following information to the fields:

	- **Review name**: Guest access review
	- **Description**: Reviewing guest access
	- **StartDate**: your current date 
	- **Frequency**: One time
	- **EndDate**: your current date + 7 days into the future
	- **Scope**: Guest users only
	- **Group**: IT-Department
	- **Reviewers**: Group owners 

17. Select **Upon completion settings** to expand the menu and set **Auto apply results to resource** to **enabled**.

18. Select **Start**. The system automatically creates an Email for the Access Reviewer.

19. In the browser window, select the circle with **MA** in the upper right corner, open the side pane and select **Sign out**.

20. Close your browser window and open it again by selecting the Edge browser icon from the taskbar.

21. In your browser, select the address bar and go to the **Outlook on the web** page by entering the following URL: [**https://outlook.office365.com**](https://outlook.office365.com)

22. When you see the **Pick an account** window, select the **Joni Sherman account** to get to the Sign in window. If there is no **Joni Sherman account**, select **Use another account** to get to the Sign in window.

23. In the **Sign in** window, enter the UPN of **Joni Sherman** (JoniS@_YourTenant_.onmicrosoft.com) and select **Next**.

24. In the **Enter password** dialog box, enter the password delivered by your training provider and select **Sign in**.

25. If a welcome screen appears, close it.

26. In the middle of the page, you will see an Email from **Microsoft Azure** with the topic **Action required: Review group access by &lt;local date + 7 days in the future&gt;**, then select this Email

27. Select the **Start review** button in this Email.

28. An additional browser tab will open.

29. In the Access Review Window, you can see an overview with configured settings and the configured guest user with your personal outlook.com email address.

30. Select your outlook.com guest and then select **Details** to review the guest statistics.

31. Select **Deny** from the available options and select **Submit**.

32. In the overview, your outlook.com guest user has now **Denied** access.


You have successfully created a new access review and blocked a guest user in your tenant. This is the end of lab 4. You can close all browser windows and proceed to the next lab.
