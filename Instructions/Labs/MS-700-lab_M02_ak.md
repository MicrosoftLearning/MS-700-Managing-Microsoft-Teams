---
lab:
    title: 'Lab 02: Configure security and compliance for teams and content'
    type: 'Answer Key'
    module: 'Module 2: Implement Microsoft Teams Governance, Security and Compliance'
---

# **Lab 02: Configure security and compliance for teams and content**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of the System Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. Before starting the deployment, IT department is gathering business requirements about Teams governance as well as data security and compliance, including how the data shared in Teams be regulated according to the organization’s compliance requirements. After you complete the planning process, you will configure Microsoft 365 Groups governance, protect Teams from threats, and configure Teams to meet your organization compliance requirements.

## **Objectives**

After you complete this lab, you will be able to:

- Activate, create and assign sensitivity labels

- Configure expiration policies

- Restrict creation of new teams to members of a security group

- Create naming policies

- Reset all Azure AD settings to defaults

- Activating ATP protection for SharePoint, OneDrive and Teams

- Create, configure and test retention policies

- Create and test a DLP policy to protect GDPR content

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Implement governance and lifecycle management for Microsoft Teams**

Your organization has started the planning process for Microsoft 365 services adoption. You are assigned as a Teams admin role to plan Teams governance. Since Teams relies on Microsoft 365 groups, you need to plan governance procedures for Microsoft 365 groups, including creating, configuring and assigning sensitivity labels, creating Microsoft 365 groups expiration policies, configuring Microsoft 365 Group creation policy permissions, configuring and test Microsoft 365 Groups naming policies.

#### Task 1 – Activate sensitivity labels for Teams 

You need to evaluate governance for Microsoft 365 Groups before deploying them in your organizations. In this task, you will activate the sensitivity labels for Teams in Azure AD, for being able to assign labels in a following task.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the User Account Control window with **Yes**.

4. Maximize the PowerShell window and enter the following cmdlet to install the **Azure AD Preview** module:
  
   ```powershell
   Install-Module AzureADPreview
   ```
5. When you are prompted to install from the untrusted repository, confirm by entering **Y** and pressing Enter.

6. Type in the following cmdlet to connect to Azure AD in your tenant:

   ```powershell
   Connect-AzureAD
   ```
7. A **Sign in** dialog box will open. Sign in as admin@&lt;YourTenant&gt;.onmicrosoft.com using the credentials provided to you.

8. To enable Microsoft 365 Groups and Teams for Sensitivity labels, you first need to load the Azure AD unified group template, by using the following cmdlet:

   ```powershell
   $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
   ```
9. Check if an Azure AD setting is already existing and load it, if yes. If not, create a blank Azure AD setting object. Run the following cmdlet to populate the "$Setting" variable:

   ```powershell
   if(!($Setting = Get-AzureADDirectorySetting | Where {$_.TemplateId -eq $Template.Id})) {$Setting = $Template.CreateDirectorySetting()}
   ```
10. Enable the Microsoft Identity Protection (MIP) support in your configuration:
    ```powershell
    $Setting["EnableMIPLabels"] = "True"
    ```
11. To verify the new configuration, run the following cmdlet:
    ```powershell
    $Setting.Values
    ```
12. Save the changes and apply the setting:

    ```powershell
    New-AzureADDirectorySetting -DirectorySetting $Setting
    ```
	**Note:** Since this is a new tenant, there’s no directory settings object in the tenant yet. You need to use ```New-AzureADDirectorySetting``` to create a directory settings object at the first time.

	If there’s an existing directory settings object, you will need to run the following cmdlet to update the directory setting in Azure Active Directory:

	```powershell
	Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
	```
13. Close the PowerShell window.

You have successfully changed your tenants Azure AD settings and activated sensitivity labels for Microsoft 365 Groups and Microsoft Teams.
   
#### Task 2 - Create sensitivity labels for Teams

After activating sensitivity labels for groups, you will now create three sensitivity labels. In this task, you will create three sensitivity labels "General," "Internal," and "Confidential." For each of them, you will create appropriate user and admin descriptions.

1. You are still connected to the **Client 1 VM**.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 compliance center** at [**https://compliance.microsoft.com/**](https://compliance.microsoft.com/).

3. On the **Pick an account** page, select the **MOD Administrator** ([admin@&lt;YourTenant&gt;.onmicrosoft.com](mailto:admin@%3cYourTenant%3e.onmicrosoft.com)) and sign in with the provided credentials.

4. In the **Microsoft 365 compliance center**, on the left navigation pane, scroll down and select …**Show all** and select **Information protection** from the expanded left side navigation pane.

5. On the top part of the page, you can see a warning message in a yellow box that states: Your organization has not turned on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint. You can turn on here, but note that additional configuration is required for Multi-Geo environments. Select **Turn on now** to activate content processing in Office online files.

6. Select **+ Create a label** to create a new sensitivity label.

7. On the **Name and create a tooltip for your label** page, enter the following information:

	- **Name**: General.

	- **Description for users**: General information without protection.

	- **Description for admins**: General information without encryption, marking or sharing restriction settings activated.

8. Select **Next**.

9. Select **Files &amp; emails** and **Groups &amp; Sites** on the **Scope** page and select **Next**.

10. Do not make any changes on the **Files &amp; emails** page and select **Next**.

11. Do not make any changes on the **Auto-labeling for Office apps** page and select **Next**.

12. On the **Group &amp; Sites** page, select both boxes **Privacy and external user access settings** and **Device access and external sharing settings** and select **Next**.

13. On the **Define privacy and external user access settings**  page select the following settings and then select **Next**:

	- **Privacy**: None-Team and group members can set the privacy settings themselves.

	- **External users access**: Select Let Microsoft 365 group owners add people outside the organization to the group.

14. On the **Define external sharing and device access settings** page select the following setting and then select **Next**.

	- **Unmanaged devices:** Allow full access from desktop apps, mobile apps, and the web.

15. Review your settings and select **Create label** to finish the new label creation.

16. When the **Your label was created** is displayed, select **Done**.

17. You should now see your newly created label "**General**" on the **Labels** dashboard. Select **+ Create a label** again, to create another sensitivity label.

18. On the **Name and create a tooltip for your label** page, enter the following information:

	- **Name**: Internal.

	- **Description for users**: Internal information with sharing protection.

	- **Description for admins**: Internal information with moderate encryption, marking and sharing restriction settings activated.

19. Select **Next**.

20. Select **Files &amp; emails** and **Groups &amp; Sites** on the **Define the scope for this label** page and select **Next.**

21. On the **Choose protection settings for files and emails** page, select both boxes **Encrypt files and emails** and **Mark the content of files** and select **Next**.

22. On the **Encryption** page, select **configure encryption settings** and perform the following configuration settings:

	- Assign permissions now or let users decide: **Assign permissions now**.

	- User access to content expires: **Never**.

	- Allow offline access: **Always**.

23. Select **Assign permissions** below **Assign permissions to specific users and groups**.

24. On the right-side pane, select **+ Add all users and groups in your organization**.

25. Select **Save** and **Next** to finish the Encryption settings.

26. On the **Content marking** page, select the slider and the checkbox **Add a watermark**.

27. Select **Customize text** to open the right-side pane.

28. Enter the following to the **Watermark text** box: **Internal use only**

29. Select **Save** and **Next**.

30. On the **Auto-labeling for Office apps** page, do not select the slider and select **Next**.

31. On the **Define protection settings for groups and sites** page, select both boxes **Privacy and external user access settings** and **Device access and external sharing settings** and select **Next**.

32. On the **Define privacy and external user access settings** page, select the following settings and then select **Next**:

	- **Privacy**: None-Team and group members can set the privacy settings themselves.

	- **External users access**: Leave the box unchecked.

33. On the **external sharing** page, select the following setting and then select **Next**:

	- **Unmanaged devices:** Allow limited, web-only access.

34. Select **Next**.

35. Review your settings and select **Create label** to finish the new label creation.

36. When the **Your label was created** is displayed, select **Done**.

37. You should now see your newly created label "**Internal"** on the **Labels** dashboard. Select **+ Create a label** again, to create another sensitivity label.

38. On the **Name and create a tooltip for your label** page, enter the following information:

	- **Name**: Confidential.

	- **Description for users**: Confidential information with all protection.

	- **Description for admins**: Confidential information with all restrictive encryption, marking and sharing settings activated.

39. Select **Next**.

40. Select **Files &amp; emails** and **Groups &amp; Sites** on the **Define the scope for this label** page and select **Next**.

41. On the **Choose protection settings for files and emails** page, check both boxes **Encrypt files and emails** and **Mark the content of files** and select **Next**.

42. On the **Encryption** page select **configure encryption settings**:

	- Assign permissions now or let users decide: **Assign permissions now**

	- User access to content expires: **Never**

	- Allow offline access: **Never**

43. Select **Assign permissions** below **Assign permissions to specific users and groups**.

44. On the right-side pane, select **+ Add all users and groups in your organization**.

45. Select **Choose permissions** and select **Reviewer** from the dropdown menu, to restrict permissions.

46. Select **Save** twice.

47. Select **Next** to finish the Encryption settings.

48. On the **Content marking** page, select the slider and the checkbox **Add a watermark**.

49. Select **Customize text** to open the right-side pane.

50. Enter the following to the **Watermark text** box: Confidential.

51. Select **Save** and **Next**.

52. On the **Auto-labeling for Office apps** page, do not select the slider and select **Next**.

53. On the **Define protection settings for groups and sites** page, check both boxes **Privacy and external user access settings** and **Device access and external sharing settings** and select **Next**.

54. On the **privacy &amp; external** **users**  page, select the following settings and then select **Next**:

	- **Privacy**: Private. Only team owners and members can access the group or team and, and only owners can add members.

	- **External users access**: Leave the box unchecked.

55. On the **external sharing** page select the following setting and then select **Next**:

	- **Unmanaged devices:** Allow limited, web-only access.

56. Select **Next**.

57. Review your settings and select **Create label** to finish the new label creation.

58. When the **Your label was created** is displayed, select **Done**.

59. Back on the **Information protection** page, select **Publish labels** from the top menu.

60. On the **Choose sensitivity labels to publish** page, select **Choose sensitivity labels to publish**.

61. Select the checkbox left from **Select all** and select **Add** to close the right-side pane.

62. Select **Next**.

63. On the **Publish to users and groups** page, do not make any changes to publish the label to all users. 

64. Select **Next**.

65. On the **Policy settings** page, open the dropdown menu below **Apply this label by default to documents and email** and select **General** to use it as the default label for document and email.

66. Below **Apply this label by default to groups and sites**, also select the dropdown and select **General**.

67. Select **Next**.

68. On the **Name you policy** page, enter the following:

	- **Name**: All company sensitivity labels

	- **Enter a description for your sensitivity label policy**: Default sensitivity labels for all users in the company.

69. Select **Next**.

70. Review your settings and select **Submit** to publish the labels.

71. When **New policy created** is displayed, select **Done**.

72. Close the browser window.

In this task, you have created and published three new sensitivity labels available for all users, which can be assigned to new and existing Teams.

#### Task 3 - Assign sensitivity labels to Teams

Once the sensitivity labels are created and published, users can now assign them to teams. Furthermore, users can modify assigned labels if needed. In this task, you will assign the "Internal" label to the "Teams Rollout" team.

**Note:** It can take several minutes till the newly created sensitivity labels are available to users.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

3. On the Teams overview select the three dots (**…**) on the right side next to the Team "**Teams Rollout,"** then select **Edit team** from the dropdown list.

4. On the **Edit** **"Teams Rollout" team** window, select the dropdown menu below Sensitivity and select **Internal**.

5. Select **Done** to save the changes.

You have successfully applied a sensitivity labels to an existing team. The configured settings of the Internal label are now applied to the Teams Rollout team. Continue with the next task.

#### Task 4 - Create and assign an expiration policy

Based on the organization requirement, unneeded groups should be deleted automatically after 90 days. To evaluate the expiration feature for teams, you will configure a group expiration policy that will expire the **Teams Rollout** group after 90 days.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

   Open **Microsoft Edge**, maximize the window and navigate to the **Azure Portal** at [**https://portal.azure.com**](https://portal.azure.com/). On the **Pick an account** page, select the global admin (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

2. If the **Welcome to Microsoft Azure** dialog box appears, select **Maybe later**. If an Azure Advisor recommendations window is displayed, close it with the **X**.

3. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

4. On the left navigation pane, select **Groups** and on the **Groups** page, on the left navigation pane, select **Expiration**.

5. In the **Groups | Expiration** page, configure the following settings:

	- In the dropdown menu of **Group lifetime (in days)**, select **Custom** and enter **90** to the text box.

	- In the text box right from **Email contact for groups with no owners**, enter (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	- Right from **Enable expiration for the Office 365 groups**, select **Selected**.

	- Select **+ Add** to open the **Select groups** right-side pane. 

	- In the **Select groups** pane, type **Teams Rollout** into the textbox and select the group.

	- Use the **Select** button on the lower end of the right-side pane to apply the policy to the **Selected group**.

	- Back on the **Groups | Expiration** page, select **Save**.

	- Select **Microsoft Azure** from the upper left in the Azure Portal and leave the Edge Browser window open.

You have successfully created a new expiration policy and configured the **Teams Rollout** team to expire after 90 days. If the team will not have an owner after 90 days, Joni Sherman is notified about the expiration if the team.

#### Task 5 - Configure a group creation policy

You are an administrator for your Teams organization. You need to limit which users are able to create Microsoft 365 groups. You will create a security group named **GroupCreators** which only the members of the group can create Microsoft 365 groups.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell**.

3. Connect to the Azure AD in your tenant with the following cmdlet:

   ```powershell
   Connect-AzureAD
   ```
4. A Sign in dialog box will open. Sign in as admin@&lt;YourTenant&gt;.onmicrosoft.com using the O365 Credentials provided to you.

5. Create a new security group "GroupCreators" with the following cmdlet:
   
   ```powershell
   New-AzureADGroup -DisplayName "GroupCreators" -SecurityEnabled:$true -MailEnabled:$false -MailNickName "GroupCreators"
   ```
6. Run following cmdlet to add **Lynne Robbins** to the new security group:
   ```powershell
   Get-AzureADGroup -SearchString "GroupCreators" | Add-AzureADGroupMember -RefObjectId (Get-AzureADUser -SearchString "Lynne Robbins").ObjectId
   ```
7. Fetch the current group settings for the Azure AD organization

   ```powershell
   $Setting = Get-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id
   ```
8. Run following cmdlet to modify the group creation setting for your tenant with the "EnableGroupCreation" attribute:
   ```powershell
   $Setting["EnableGroupCreation"] = "False"
   ```
9. Run following cmdlet to add the just created security group "GroupCreators" as permitted group to create groups, by their ObjectID:

   ```powershell
   $Setting["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString "GroupCreators").objectid
   ```
10. Review the changes you have just configured with the following command:

    ```powershell
    $Setting.Values
    ```
11. Then save the changes and apply the settings:

	```powershell
	Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
	```

12. Close the PowerShell window.

13. To test the newly configured settings, connect to the **Client 2 VM** with the credentials that have been provided to you.

14. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

15. You won’t see the option to **Create team** 

16. Leave the client open and continue with the next task.

**Note:** When you are still able to create a new team, wait several minutes for the new configuration to take effect on your users.

In this task, you have successfully created a new security group and configured Azure AD settings to restrict the creation of new groups to members of this group only. At the end of the task, you have successfully tested the new group creation restrictions.

#### Task 6 - Configure a new naming policy

As part of your Teams planning project, you will configure the naming policy where each new Microsoft 365 Group or Team needs to comply with the organization’s regulations on naming objects. Each group name should start with letters **Group** and end with the **Country** attribute of the Owners location. Furthermore, there is an internal regulation that forbids using following specific keywords in Teams names: CEO, Payroll and HR.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in to the **Azure Portal**. If not, open **Microsoft Edge**, maximize the window and navigate to the **Azure Portal** at [**https://portal.azure.com**](https://portal.azure.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Select the search box on top of the window, type in **Azure Active Directory** and then select **Azure Active Directory**.

5. In the **Azure Active Directory**, on the left navigation pane, select **Groups**.

6. On the **Groups | All groups** page, on the left navigation pane, select **Naming policy**.

7. Select **Download** from the main window to download a blocked words sample file. Select **Save** and select **Open folder** on the lower end of the Edge browser window.

8. Right-click the file **BlockedWords.csv** and select **Edit** to open **Notepad**.

9. Type **CEO,Payroll,HR** into the empty quotes in the Notepad window, select **File** and **Save**. Afterwards, close the Notepad file.

10. Back to the **Groups | Naming policy** page, under **Blocked words** section, scroll fown and below **Step 3. Upload your .csv file**, select the **folder** icon to open a file selection window.

11. Browse to **Downloads**, select the **BlockedWords.csv** file and select **Open**.

12. You can see a success message in the upper right of the **Azure Portal**.

13. On the **Group | Naming policy** page, select **Save** to apply the new blocked words setting.

14. Still on the **Groups | Naming policy** page, select the **Group naming policy** tab.

15. Below the **Group naming policy** section, scroll down to **Current policy** and select the checkbox next to **Add prefix**.

16. Select the dropdown textbox below with **Select the type of prefix** and choose **String**.

17. Enter the following to the empty text box: **Group_**

18. Select the checkbox next to **Add suffix.** 

19. Select the dropdown textbox and from the drop-down list, choose **Attribute**, and from the drop-down list choose **CountryOrRegion**.

20. On the **Groups - Naming policy** page, under **Current policy** section, preview the group name format listed as **Group_&lt;Group name&gt;&lt;CountryOrRegion&gt;**. GroupNaming Policy

21. Select **Save** to apply the new naming policy.

22. Close the browser window.

In this task, you have configured a naming policy that will block specific words to be used in a Microsoft 365 Group name, as well as you have configured a new naming policy for Microsoft 365 Group and Teams names.

#### Task 7 - Test the new naming policy

You need to test the newly created naming policy to see its effects in your pilot environment. In the following task, you will try to create a new team and see the configured naming policy template completing the configured name for your new team.

**Note:** It can take up to 24 hours till the blocked words setting will take effect. Therefore, you will only test the configured naming policy, which takes effect immediately.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Teams** **web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/).

3. When the Sign in window is displayed, sign in as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) using the O365 credentials provided to you.

4. Select **Join or create a team** from the bottom of the teams list.

5. Select **Create team** and **From scratch**.

6. Do not change the Sensitivity dropdown and select **Public**.

7. Enter **Afterwork** below **Team name**.

8. Below the entered name, you can see the configured prefix and suffix for new teams.

9. Select **Create** to create the new team.

10. Select **Skip** to not add any additional members.

11. Review the name of the newly created team.

You have successfully tested the configured naming policy for managing the prefix and suffixes of user created teams. Continue with the next task.

#### Task 8 – Reset Azure AD settings

You can revert any changes in Azure AD unified groups settings to the defaults again. You can do this by loading a blank template and replacing the current configuration with the template. To clean up your test environment after testing, you will now do this and reset all changes you did for Microsoft 365 Groups and Teams.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell**.

3. Connect to the Azure AD in your tenant with the following cmdlet:

   ```powershell
   Connect-AzureAD
   ```
4. When the Sign in window is displayed, sign in as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) using the O365 credentials provided to you.

5. To load the unifed group template, use the following cmdlet:

   ```powershell
   $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
   ```    
6. Create a blank Azure AD tenant settings object:
   ```powershell
   $Setting = $Template.CreateDirectorySetting()
   ```
7. Check the Azure AD tenant settings configured in the template:
   ```powershell
   $Setting.Values
   ```
8. Review the current configured Azure AD tenant settings for unified groups and note the differences to the values in the "$Setting" variable, that contains the default template settings:
   ```powershell
   (Get-AzureADDirectorySetting).Values
   ```
9. Because you will still need the sensitivity labels at a later point of this lab, activate only them in your settings variable again by using the following command:
   ```powershell
   $Setting["EnableMIPLabels"] = "True"
   ```
10. Apply the settings variable to your current configuration to revert all other changes:
    ```powershell
    Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
    ```
11. Review your configured Azure AD tenant settings again, which are all on default again:
    ```powershell
    (Get-AzureADDirectorySetting).Values 
    ```
12. Close the PowerShell window.

You have successfully reset all Azure AD tenant settings for Microsoft 365 Groups and Teams in your test tenant.

### **Exercise 2: Implement security for Microsoft Teams**

In this exercise, you will increase the security level in your organization by configuring an ATP policy to ensure that no malicious content is sent through documents shared in Teams by blocking attachments that contain malware.

#### Task 1 - Configure ATP for Microsoft Teams

Users in your organization are using Microsoft Teams for communication and collaboration. Business managers are concerned that documents that are shared within Microsoft Teams may contain malware. You will need to ensure that no malicious content is sent through documents shared in Teams by configuring ATP policy that blocks documents that contain malware.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Microsoft 365 Security center**: [**https://security.microsoft.com**](https://security.microsoft.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In the **Microsoft 365 Security center**, in the left navigation pane, select **Policies**.

5. On the **Policies** page, scroll to the **Threat protection** section and select **ATP safe attachments (Office 365)**.

6. On the **Safe attachments** page, select **Global settings** on the ribbon. If you cannot see **Global settings** select **…** first.

7. In the wizard, set **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** to **On**.

8. Select the **Save** button.

9. Close the Edge browser windows.

In this task, you have activated ATP safe attachments scanning for SharePoint, OneDrive, and Microsoft Teams that blocks block documents that contain malware.

### **Exercise 3: Implement compliance for Microsoft Teams**

Before deploying Microsoft Teams in your organization, you need to evaluate Microsoft Teams compliance features to meet organizations requirements. First, you will configure retention settings on data in Microsoft Teams. Next you will configure DLP policy that will search for GDPR related and credit card data and test a DLP policy in the end.

#### Task 1 - Create a new retention policy to retain content

Teams retention settings are very important for managing the lifecycle of company data, therefore, the capabilities of retention policies need to be evaluated in the Teams pilot. In this task, you will create a new retention policy that retains the Teams channel messages of the "Sales" Team for 7 years after last modification.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 compliance center** at [**https://compliance.microsoft.com/**](https://compliance.microsoft.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In **Office 365 Compliance center**, on the left navigation pane, select **policies**, scroll down to **Data** and select **Retention**.

5. On the **Retention** page, select **New retention policy** to open the **Create retention policy wizard.**

6. On the **Name your policy** page, enter the following and select **Next**: 

	- **Name**: Sales retention policy

	- **Description**: Retention policy for Sales department that will retain channel messages for 7 years.

7. On the **Decide if you want to retain content, delete it, or both** page, select **Next**.

8. On the **Choose locations to apply the policy** page, configure the following settings:

	- **Exchange email**: Off

	- **SharePoint sites**: Off

	- **OneDrive accounts**: Off

	- **Office 365 groups**: Off

	- **Skype for Business**: Off

	- **Exchange public folders**: Off

	- **Teams channel messages**: On

	- **Teams chats**: Off

9. Select **Choose teams** right from **Teams channel messages** to open the right-side pane.

10. Select **Choose teams** to get the list of existing teams. 

11. Select the checkbox left from **Sales** and select **Choose &gt; Done**.

12. Select **Next**

13. On the **Review your settings** page, review your settings and select **Create this policy**.

14. Leave the browser open for the next task.

In this this task, you have successfully created a new retention policy named **Sales retention policy** that retains the channel messages and chat of the **Sales** Team for **7 years after the last modification**.

#### Task 2 - Create a new retention policy to delete content

After configuring a retain policy to protect data from deletion, you also need to evaluate the capabilities of retention policies to delete content automatically. For demonstration purpose, you will set the deletion threshold to a single day and apply the retention policy to the "Teams Rollout" team, to remove all channel messages older than a day automatically.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in to the **Microsoft 365 Compliance center**, as **MOD Administrator** in the **Information governance** section and on the **Retention** tab.

3. Select **New retention policy** to open the **Create retention policy wizard.**

4. On the **Name your policy** page, enter the following and select **Next**: 

	- **Name**: Teams Rollout deletion policy

	- **Description**: Retention policy for the Teams Rollout team to delete messages older than a day.

5. On the **Decide if you want to retain content, delete it, or both** page, select **No, just delete content that’s older than** with the following information and then select **Next**:

	- **Delete items older than**: 1 days

	- **Delete the content based on**: when it was created

 

6. On the **Choose locations to apply the policy** page, configure the following settings and select **Next**:

	- **Exchange email**: Off

	- **SharePoint sites**: Off

	- **OneDrive accounts**: Off

	- **Office 365 groups**: Off

	- **Skype for Business**: Off

	- **Exchange public folders**: Off

	- **Teams channel messages**: On

	- **Teams chats**: Off

7. Select **Edit** right from **Teams channel messages** to open the right-side pane.

8. Select the checkbox left from **Teams Rollout** and select **Done**.

9. Select **Next**

10. On the **Review your settings** page, review your settings and select **Create this policy**.

11. Leave the browser open for the next task.

You have successfully created a second retention policy for testing the deletion capabilities to clean up the "Teams Rollout" team from all conversation messages older than a day.

#### Task 3 – Test the retention policy for deleting content (optional)

In this task you will test the retention policy for deleting content from the Teams Rollout team after a day. Before you can see the retention policy taking any effect, you must create some conversation content in the team.

**Note:** Because you need to wait for 24 hours till the retention policy deletes anything, this task is marked as optional. After creating content in the Teams Rollout team, you need to return to this task after waiting 24 hours to see the retention policies effect.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

3. Select the **Teams Rollout** team and the **General** channel.

4. Select **New conversation** from the lower end of the main window.

5. Write the following text to the text box:

	Hello world!

6. Leave the client open and add other content to the team, as you like.

7. Come back after 24 hours to see, the content has been deleted automatically.

You have added a conversation message to a team, which is deleted by the deletion retention policy after 24 hours.

#### Task 4 - Create a DLP policy for GDPR (PII) content from a template

According to your organization compliance requirements, you need to implement basic protection of PII data for European users. You will create a new DLP Policy named **GDPR DLP Policy** from the template "General Data Protection Regulation (GDPR)," The DLP policy you create will detect if GDPR sensitive content is shared with people outside of your organization. If the policy detects at least one occurrence of the GDPR sensitive information, it will send email to Joni Sherman and block people from sharing the content and restricting access to shared content. Furthermore, it will display a tip to users who tried to share the sensitive content, and it will allow them to override the policy with business justification. Since you are evaluating the DLP policies, you will create the DLP policy in a test mode with policy tips enabled.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 compliance center** at [**https://compliance.microsoft.com/**](https://compliance.microsoft.com/).

3. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In **Microsoft 365 compliance center**, on the left navigation pane, select **Show all** from the bottom of the navigation pane and then select **Data loss prevention**.

5. On the **Data loss prevention** page, select **+ Create policy**.

6. On the **Start with a template or create a custom policy** page, select the **Search for specific templates** search box and type: **GDPR**. The **General Data Protection Regulation (GDPR)** template will be preselected. 

7. Select **Next**

8. On the **Name your policy** page, change the default values to the following and select **Next**:

	- **Name**: GDPR DLP Policy

	- **Description**: Data loss prevention policy for GDPR regulations in Teams.

9. On the **Choose locations to apply the policy** page, apply the following selection and select **Next**:

	- **Exchange email**: Off

	- **SharePoint sites**: Off

	- **OneDrive accounts**: Off

	- **Teams chat and channel messages**: On

	- **Microsoft Cloud App Security**: Off

10. On the **Define** **policy settings** page, stay with the default selection from the template **Review and customize default settings from the template** and select **Next**.

11. On the **Info to protect** page, leave the default settings and select **Next**.

12. On the **Protection actions** page, ensure that the following settings are configured, and then select **Next**:

	- A checkbox is selected for: **Detect when a specific amount of sensitive info is being shared at one time**

		- In the **At least __ or more instances of the same sensitive info type** box, type: **1**

	- Select the checkbox for **Send incident reports in email**

	- Select **Choose what to include in the report and who receives it** to open the right-side pane

	- Select **Add or remove people**, select the checkbox for **Joni Sherman**

	- Select **Add** and **Save**

	- Select the checkbox for **Restrict access or encrypt the content**

13. On the **Customize access and override settings** page, ensure that the following settings are configured, and then select **Next**:

	- A checkbox is selected for: **Restrict access or encrypt the content in Microsoft 365 locations**

	- Select **Block users from accessing shared SharePoint, OneDrive, and Teams content**.

	- Select **Block only people outside your organization. Users inside your organization will continue to have access**.

	- Select **Override the rule automatically if they report it as false positive**.

14. On the **Test or turn on the policy** page, select **Yes, turn it on right away** and select Next.

15. On the Review your settings page, review your settings, select **Submit** then **Done**.

16. Stay on the **Data loss prevention page** and leave the browser opened.

After completing this task, you have created a DLP Policy from the template "General Data Protection Regulation (GDPR)" that detects if GDPR sensitive content is shared with people outside of your organization. The policy is extra sensitive for the configured threshold of 1 rule match and Joni Sherman will be notified if a matching occurs.

#### Task 5 - Create a DLP policy from scratch

After creating a DLP Policy for protecting GDPR relevant data, you will create another policy from scratch. Instead of using a template, you will configure rules directly with custom rules and actions.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You are still signed in to the **Microsoft 365 Compliance center**, as **MOD Administrator** in the **Data loss prevention** section and on the **Policies** tab.

3. In **Microsoft 365 compliance center**, on the left navigation pane, select **Show all** and then select **Data loss prevention**.

4. On the **Data loss prevention** page, select **+ Create policy**.

5. Select **Custom** and **Custom policy** below **Categories** and **Templates**, to create a blank policy and select **Next**.

6. On the **Name your policy** page, type the following values, and then select **Next**:

	- **Name**: Credit card data DLP Policy

	- **Description**: Data loss prevention policy for credit card data in Teams.

7. On the **Choose locations to apply the policy** page, apply the following selection and select **Next**:

	- **Exchange email**: Off

	- **SharePoint sites**: Off

	- **OneDrive accounts**: Off

	- **Teams chat and channel messages**: On

	- **Microsoft Cloud App Security**: Off

8. Leave the radio button selection unchanged on the **Define policy settings** page and select **Next**.

9. Select **+ Create rule** and enter the following information:

	- **Name**: Credit card numbers found

	- **Description**: Basic rule for protecting credit card numbers form being shared in Teams.

10. Below **Conditions**, select **+ Add condition** and **Content contains**.

11. Leave the group name of **Default**, select **Add** and **Sensitive information types**.

12. From the right-side pane, check the box left of **Credit Card Number** and select **Add**.

13. Leave the high **Accuracy** of 85 to 100 unchanged and do not change the **Instance count** of 1.

14. Below **Action**, select **+ Add an action** and **Restrict access or encrypt content in Microsoft 365 locations**.

15. Select the checkbox of **Restrict access or encrypt content in Microsoft 365 locations** again and select **Everyone. Only the content owner, the last modifier and the site admin will continue to have access.** 

16. Below **User notification**, select the slider to **On** and select **Customize the policy tip text**.

17. Enter the following text to the textbox: **Credit card numbers are not allowed to be shared!**

18. Below **Incident reports**, select the slider **Send an alert to admins when a rule match occurs** and select **Add or remove people**.

19. On the **Add or remove people** page, select the checkbox left from **Joni Sherman** and select **Add**.

20. Select **Save**.

21. Review the rule settings and select **Next**.

22. Select the radio button **Yes, turn it on right away** and select **Next**.

23. Review the policy settings again and select **Submit** and **Done**.

24. Leave the browser open.

You have successfully created a new custom DLP policy for protecting credit card numbers from being shared via Teams conversations.

#### Task 6 – Test the DLP Policies

To make sure your configured DLP policies are working as expected, you need to perform some testing with your pilot users.

**Note:** It can take up to 24 hours till new DLP policies take effect. If the steps does not work, continue with the lab, and perform task 6 at a later point of working through this lab.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

3. In the left-hand navigation pane, select **Teams**, and then select the **General** channel below **Teams Rollout**.

4. Select **New conversation** from the main window.

5. Enter the following lines to the textbox:

	- MasterCard: 5105105105105100

	- Visa: 4111111111111111

	- Visa: 4012888888881881

6. Select the arrow to the right from the lower-right corner below the text box to send the message.

7. After a moment, you should see a text in red above your new conversation message that states, "**This message was blocked.**" **Select What can I do?** To see the reason why this message was blocked.

8. Select **Report** to notify the admin about this DLP policy violation. Now you can see a different message above your conversation entry, that states **Blocked.** **You’ve reported this to your admin.**

9. Connect to the **Client 1 VM** with the credentials that have been provided to you.

10. You should still be logged in to the **Microsoft 365 Compliance center**. If not, open Microsoft Edge, maximize the browser, and navigate to the **Microsoft 365 Compliance center**: [**https://compliance.microsoft.com**](https://compliance.microsoft.com/).

11. Select **Reports** from the left-hand navigation pane and scroll down to **Organizational data**.

12. Below **DLP Policy Matches** and **DLP Incidents**, you can now see the DLP policy matches. Select **DLP Policy Matches** to open the detailed view.

13. On the **DLP Policy Matches** page, inspect the rule matches.

You have successfully tested your DLP policy to block sharing of credit card information via Teams chat and channel conversations.

END OF LAB