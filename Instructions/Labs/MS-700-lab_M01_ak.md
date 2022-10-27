

# **Lab 01: Manage Microsoft Teams**

# **Student lab answer key**

## **Microsoft 365 user interface**

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual.

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## **Lab Scenario**

In the labs, of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. You are asked to ensure the required Teams admin roles are assigned to your pilot team members and check license assignment to users. As part of the Microsoft Teams rollout in Contoso, you need to make sure the pilot team members are well versed with the usage of Teams admin center, its menus and PowerShell cmdlets to handle day to day administrative tasks. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to test the creation Microsoft 365 Groups from the M365 admin center and new teams using Teams desktop and web clients. You will also enable access to explore Teams Preview features using Teams update policy. Once the pilot team completes exploring and testing the features in Teams admin center and Microsoft 365 admin center, you need to guide them to follow best practices in creating and configuring naming and expiration policies for the groups and teams while enforcing the restriction on the creation of teams. 

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman (JoniS@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams administrator**

- Patti Fernandez (PattiF@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams device administrator**

- Allan Deyoung (AllanD@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams communication support engineer**

- Alex Wilber (AlexW@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user from Canada**

- Lynne Robbins (LynneR@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user**

- Diego Siciliani (DiegoS@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user**

## **Objectives**

After you complete this lab, you will be able to:

- Assign Teams admin roles to users

- Check license assignment for users

- Understand the Teams admin center and its menus

- Install the Teams PowerShell module and explore its cmdlets

- Create Microsoft 365 Groups from the M365 admin center

- Create new teams using the Teams desktop client

- Create new teams using the Teams web client

- Configure expiration policies

- Restrict creation of new teams to members of a security group

- Create naming policies

- Enable access to Teams Preview features

## **Lab Setup**

- **Estimated Time:** 100 minutes.

## **Instructions**

### **Before you start**

The labs in this course have been prepared for a Microsoft Teams deployment at Contoso Ltd. Corporation. Contoso is running a Microsoft 365 cloud-only deployment. The lab environments have been specifically designed in this manner to give you experience managing Microsoft Teams in a Microsoft 365 deployment. You will be provided with two virtual machines and a Microsoft 365 tenant to complete the lab steps.

#### **1. Sign in to the lab virtual machines**

The labs in this course will use two virtual machines:

- Client 1 VM: a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

- Client 2 VM: a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

**Note:** Lab virtual machine sign-in instructions will be provided to you by your instructor.

**Important:** The exercises in the MS-700 labs are cloud-only deployments. A local administrator account has been created on the client VMs. You will log into the VMs as a local administrator instead of a domain account. Following your login, the desktop will indicate that you are logged in as either **CLIENT1* or** CLIENT2*, depending on which machine you are on.

#### **2. Review installed applications**

Once you signed in to the VM, observe the start menu, and verify following applications have been installed:

- Microsoft Teams

#### **3. Review Microsoft 365 tenant**

Besides two VMs, you will also be provided with a Microsoft 365 tenant with the following highlights:

- Office 365 E5 with Enterprise Mobility + Security E5.

- 15 licenses in total with 5 available of 15(10 used).

- One Global Administrator (MOD Administrator) and 9 standard users have been pre-created.

- **Note:** Microsoft 365 sign-in instructions will be provided to you by your instructor.

- The username of the Global Administrator (MOD Administrator) is **admin@&lt;YourTenant&gt;.onmicrosoft.com**.

- **&lt;YourTenant&gt;.onmicrosoft.com** - This is the domain associated with the Microsoft 365 tenant that was provided by the lab hosting provider. The first part of this domain name (&lt;YourTenant&gt;) is the unique tenant ID provided by the lab hosting provider. The &lt;YourTenant&gt; portion of the tenant ID, which is the tenant suffix ID, will be unique for each student.

- **IMPORTANT:** This is critical because, throughout this lab, you will be asked to enter the **&lt;YourTenant&gt;.onmicrosoft.com** domain name when signing into apps with a given username (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com). When doing so, you must enter the unique tenant suffix ID that is assigned to your tenant ID in place of the **&lt;YourTenant&gt;**.

- For example, if your Tenant Email is **admin@contosolab.onmicrosoft.com**, the unique tenant suffix ID (&lt;YourTenant&gt;) is **contosolab**. When signing in as Joni when entering this domain, you would replace &lt;YourTenant&gt; with contosolab (for example, JoniS@contosolab.onmicrosoft.com).

- **RECOMMENDATION:** You should write down your unique tenant suffix, mentioned as &lt;YourTenant&gt; in this lab and provided by your training provider. After a while, you will have this name or number memorized as you move through the labs in this course.

- **Use the new Microsoft 365 admin center**

- Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center, make sure the slider in the upper right corner is set to **The new admin center**. If you can read **Try the new admin center**, select the slider, and activate it.  
‎‎‎  
‎‎‎ **IMPORTANT:** The instructions that are provided in the lab exercise for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

### **Exercise 1: Prepare Teams admin roles and licenses**

In the first exercise, you will assign required administrative roles to users and check license assignments for the Teams license. To perform these tasks, you will use default tenant global admin.

#### **Task 1 - Assign Teams admin roles to users**

In this task, you will use the default global admin to sign in to the Microsoft 365 admin center and assign several Teams admin roles to different users. This task is crucial for later tasks and exercises as you will perform most of the tasks in the context of Joni Sherman’s account.

1. Browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.

	- Connect to the **Client 1 VM** with the credentials that have been provided to you.

	- Open **Microsoft Edge** and browse to the **Microsoft 365 admin center** at [**https://admin.microsoft.com/**](https://admin.microsoft.com/) with the Global admin credential ( **MOD Administrator** : admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. To assign **Teams admin** role to **Joni Sherman**

	- Select the navigation menu in the upper-left and select **Users** and **Active users** from below it.

	- In the Active user’s list, search and select **Joni Sherman**, to open the right-side settings pane.

	- In the settings below the Account tab, select **Manage roles**.

	- On the **Manage admin roles** pane, select **Admin center access** and scroll down to expand **Show all by category** to reveal all available roles.

	- Select **Teams Administrator** checkbox then select **Save changes**. You will see the message **Admin roles updated** on the upper part of the pane to confirm the update. Close the **Manage admin roles** pane by selecting the X button on the top right side of the pane.

3. To assign **Teams device admin** role to **Patti Fernandez**

	- Repeat the same steps as above, in the **Active users list**, search and select **Patti Fernandez** and assign **Teams Device Administrator** role to **Patti Fernandez**.

4. To assign **Teams communication Support engineer** role to **Allan Deyoung**

	- Repeat the same steps as above and assign **Teams communication support engineer** role to **Allan Deyoung**.

You have now successfully assigned the Teams admin roles.

- Teams Administrator: Joni Sherman

- Teams Devices Administrator: Patti Fernandez

- Teams communication support engineer: Allan Deyoung

Proceed to the next task.

#### **Task 2 – Check license assignment of your users**

In this task, you will check the license assignment of all users participating in the pilot. At the end of the task, you will confirm that all pilot users are licensed correctly and Alex Wilber’s location is updated to Canada as preparation for a later task.

1. Connect to the **Client 1 VM** and browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.

2. Update **Alex Wilber’s** location to **Canada**

	- On the **Users** > **Active users** page, select the name of **Alex Wilber**.

	- Select **Licenses and Apps** tab.

	- Select the dropdown menu under **Select location**, and update to **Canada**.

	- Select **Save changes**.

3. Check **Alex Wilber’s** licenses

	- On the same tab, under **Licenses** section, verify that **Enterprise Mobility + Security E5** and **Office 365 E5** are both selected.

	- Select **Apps** to expand All licenses.

	- Scroll down the list of all apps, and verify **Microsoft Teams** is selected.

4. You can repeat the same steps to check other users’ licenses. Do not change their locations.

You have successfully validated that all Users participating in the pilot own Teams licenses and are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task.

You have finished the first exercise, and you can continue with the next one.

### **Exercise 2: Explore Teams management tools**

In this exercise, you will explore the Teams admin center and install the Teams PowerShell module, required to manage teams, policy packages, calling features, and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center and the PowerShell. You can create scripts for automation and even access several settings not available in the GUI.

To perform these tasks, you will use Joni Sherman’s account (JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com).

#### **Task 1 - Explore Teams admin center**

You will review the available settings for managing Teams in the Teams admin center.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	**Note:** You can use **InPrivate window** of Microsoft Edge for logging in with different credentials.

2. In left navigation of the Teams admin center, select **Teams** > **Manage teams**. You will see the teams in your organization once created.

3. In left navigation of the Teams admin center, select **Teams** > **Teams policies**. You can see the default Teams policy named **Global (Org-wide default)**.

You can explore other settings to familiarize various controls in the Teams admin center.

You have successfully explored several available menus from the Teams admin center for managing teams and configuring policies in your tenant.

#### **Task 2 - Install and explore Teams PowerShell module**

In this task, you will install and connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system and do not need to download any executables via the browser.

1. Connect to the **Client 1 VM** with the VM credential that has been provided to you.

2. Open **Windows PowerShell** and run as Administrator.

	- Select **Start** and search for **Windows PowerShell (Admin)**, then right select **Run as administrator**.

	- Confirm the **User Account Control** window with **Yes**.

3. Install **Microsoft Teams PowerShell module**

	- In the PowerShell window, enter the following cmdlet and press **Enter:**

		- Install-Module -Name MicrosoftTeams

	- Enter **Y** and press **Enter** twice to confirm the installation of the NuGet provider and Untrusted repository.

4. Connect to your tenant.

	- Enter the following cmdlet in the PowerShell window and press **Enter**:

		- Connect-MicrosoftTeams

	- In the Sign-in window, sign in as the Teams admin - Joni Sherman (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	- When the sign-in was successful, several information about the signed-in user and the tenant are displayed.

5. Explore **Microsoft Teams PowerShell module**

	- To confirm the MicrosoftTeams module is loaded correctly, enter the following cmdlet and press **Enter** to view all available PowerShell modules:

		```Get-Module```

		**Note**: To the left of the **Name** column, the version of the PowerShell module is displayed.

	- To get an overview of the available Teams PowerShell cmdlets from the MicrosoftTeams module, enter the following cmdlet and then press **Enter**:

		```Get-Command -Module MicrosoftTeams```

	- The Get-Help cmdlet is used to explore the available cmdlets. For example, to get more information about how to create a team with PowerShell, enter the following cmdlet and press **Enter**:

		```Get-Help New-Team```

		**Note**: If you receive a message to update the help libraries, type **Y** for yes.

	- Disconnect from the Microsoft Teams environment.

		```Disconnect-MicrosoftTeams```

6. Close the PowerShell window and continue to the next task.

You have successfully used the Microsoft Teams PowerShell module to connect to Teams and explored available cmdlets.

### **Exercise 3: Create groups and teams**

In this exercise, you will create a Microsoft 365 group from the Microsoft 365 admin center and create a team from the Teams desktop client and the web client.

#### **Task 1 - Create a Microsoft 365 Group**

You will create a new Microsoft 365 Group named “IT-Department,” and then add the pilot members serving as a basis for your future teams and licensing.

1. Connect to the **Client 1 VM** and browse to the **Microsoft 365 admin center** (https://admin.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the Microsoft 365 admin center, select **Teams &amp; groups** > **Active teams &amp; groups**.

3. On the **Active teams and groups** page, select **Add a group**.

4. Follow the **Add a group** wizard with the following information:

	- Group type: Select **Microsoft 365 (recommended)**

		- Select **Next**  


	- Basics:

		- Name: **IT-Department**

		- Description: **All staff of the IT-Department**

		- Select **Next**

	- Owners:

		- Select **+ Assign owners**

		- Search and select **Joni Sherman**

		- Select **Add(1)**, and then select **Next**.

	- Members:

		- Select **+ Add Members**, and add the following users:

			- Patti Fernandez

			- Allan Deyoung

			- MOD Administrator

		- Select **Add(3)**, and then select **Next**.

	- Settings:

		- Enter **IT-Department** for Group email address.

		- Privacy: **Private**

		- Uncheck **Create a team for this group**.

		- Select **Next**

5. Select **Create group** > **Close**.

6. Wait a moment and select **Refresh** until the group is visible. You will see there is no Teams icon in the **Teams status** column.

7. Select the **IT-Department** group to review the settings and members.

The new Microsoft 365 Group with the name “IT-Department” was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a new team by using the desktop client**

To test the self-service capabilities of Teams, in this task, **Alex Wilber** will sign in to the Teams Desktop client, create a new team with the name **Teams Rollout** and add all members participating in the Teams evaluation project.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams, desktop client.

3. Select on **"Get Started"** and Sign in as **Alex Wilber** (AlexW@&lt;YourTenant&gt;.onmicrosoft.com). At the ‘Stay signed in to all your apps’ window, select **No, sign in to this app only**.

	**Note**: If you don’t have Alex's password, you can reset Alex's password with the following steps:
	
	1. Login to **Microsoft 365 Admin Center** as **MOD Administrator**. 
	2. On the **Users &gt; Active users** page, select the name of **Alex Wilber**. 
	3. Select **Reset password** from the top, then select **Automatically create a password** and uncheck **Require this user to change their password when they first sign in** and **Reset password**. 
	4. Use the password under column Password to login.

	**Note**: You might need to download and install the latest Teams, desktop client. If so, select **Update Teams** and follow the installation guideline - Select **Download for desktop** > **Download Teams** **Run**.

4. In the Teams desktop client, select **Teams** from the left menu.

5. Select **Join or create a team** from the lower-left corner.

6. Select **Create team** > **From scratch** > **Public**. Enter the team name **Teams Rollout** and select **Create**.

7. On the **Add members to Teams Rollout** window, enter the following names and select **Add**.

	- Joni Sherman

	- Lynne Robbins

	- Diego Siciliani

8. Select the dropdown menu next to Joni Sherman and switch from **Member** to **Owner**.

9. Select **Close**.

You have successfully created a new team from the Teams desktop client added the project team members, and you have made Joni Sherman a team owner.

#### **Task 3 - Create a new team by using the web client**

In this task, **Lynne Robbins** will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name **Sales**. She will also add **Alex Wilber** as a member.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Browse to the **Microsoft Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/) and sign in as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

3. Select **Use the Web app instead** if prompted to download the Teams Desktop app. At the ‘Stay signed in to all your apps’ window, select **No, sign in to this app only**.

4. Select **Join or create a team** from the lower-left corner.

5. Select **Create team** >**From scratch** > **Private**. Enter the team name **Sales** and select **Create**.

6. On the **Add members to Sales** window, enter the following names and select **Add** > **Close**.

	- Alex Wilber

The newly created team is displayed in the list of your teams. You have successfully created a new team with the Teams web client.

### **Exercise 4: Implement lifecycle management and governance for Microsoft Teams**

Your organization has started the planning process for Microsoft 365 services adoption. You are assigned a Teams admin role to plan Teams governance. Since Teams relies on Microsoft 365 groups, you need to plan governance procedures for Microsoft 365 groups, including creating **Microsoft 365 groups expiration policies**, configuring **Microsoft 365 Group creation policy permissions**, configuring and testing **Microsoft 365 Groups naming policies**.

#### Task 1 - Create and assign an expiration policy

Based on the organization’s requirement, unneeded groups should be deleted automatically after 90 days. To evaluate the expiration feature for Teams, you will configure a group expiration policy that will expire the **Teams Rollout** group after 90 days.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**.

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Expiration**.

4. On the **Groups | Expiration** page, configure the following settings:

	- In the dropdown menu of **Group lifetime (in days)**, select **Custom** and enter **90** to the text box.

	- In the text box right from **Email contact for groups with no owners**, enter (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	- Right from **Enable expiration for the Office 365 groups**, select **Selected**.

	- Select **+ Add** to open the **Select groups** right-side pane.

	- In the **Select groups** pane, type **Teams Rollout** into the textbox and select the group.

	- Use the **Select** button on the lower end of the right-side pane to apply the policy to the **Selected group**.

	- Back on the **Groups | Expiration** page, select **Save**.

You have successfully created a new expiration policy and configured the **Teams Rollout** team to expire after 90 days. If the team doesn’t have an owner after 90 days, Joni Sherman will be notified about the expiration.

#### Task 2 - Configure a group creation policy

You are an administrator for your Team’s organization. You need to limit which users can create Microsoft 365 groups. You will create a security group named **GroupCreators** which only the members of the group can create Microsoft 365 groups.

1. Connect to the **Client 1 VM** and browse to the **Microsoft 365 admin center** (https://admin.microsoft.com/) as the Global admin - MOD Administrator(admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the Microsoft 365 admin center, select **Teams &amp; groups** > **Active teams &amp; groups**.

3. On the **Active teams and groups** page, select **Add a group**.

4. Create a security group. 

	Follow the **Add a group** wizard with the following information:

	- Group type: Select **Security** > **Next**
	- Basics:

		- Name: **GroupCreators**
		- Description: **Users who can create Microsoft 365 Groups for new teams**
		- Select **Next**

	- Finish: Select **Create Group** and then select **Close**

	- Back to **Active teams &amp; group** page, select **Security** tab and Select on the security group **GroupCreators** you just created.

	- Select **Members** tab to configure the **Owners** and **Members**.

		- Owners: Select **View all and manage owners** and select **+ Add owners.** Select **MOD Administrator**.

		- Members: Select **View all and manage members** > **+ Add members**, and add the following users:

			- Joni Sherman
			- Alex Wilber

5. Restrict the Microsoft 365 groups creation to the security group.

    1. Open **Windows PowerShell** and run as Administrator.

    2. Install **Azure AD Preview module**

        In the PowerShell window, enter the following cmdlet and press **Enter**. Enter **Y** and press **Enter** to confirm the installation of an untrusted repository.

        ```powershell
        Install-Module -Name AzureADPreview
        ```

    3. Connect to your AAD tenant.

        Enter the following cmdlet in the PowerShell window and press **Enter**. In the Sign-in window, sign in as the Global admin - MOD Administrator(admin@&lt;YourTenant&gt;.onmicrosoft.com).

        ```powershell
        Connect-AzureAD
        ```

    4. Load the Azure AD unified group template, by using the following cmdlet:

        ```powershell
        $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
        ```
    5. Check if an Azure AD setting is already existing and load it, if yes. If not, create a blank Azure AD setting object. Run the following cmdlet to populate the "$Setting" variable:

        ```powershell
        if(!($Setting = Get-AzureADDirectorySetting | Where {$_.TemplateId -eq $Template.Id})) {$Setting = $Template.CreateDirectorySetting()}
        ```

    6. Run the following cmdlet to modify the group creation setting for your tenant with the "EnableGroupCreation" attribute:

        ```powershell
        $Setting["EnableGroupCreation"] = "False"
        ```
    7. Run the following cmdlet to add the just created security group **GroupCreators** as a permitted group to create groups, by their ObjectID:

        ```powershell
        $Setting["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString "GroupCreators").objectid
        ```
    8. Review the changes you have just configured with the following command:

        ```powershell
        $Setting.Values
        ```

    9. Save the changes and apply the setting:

        ```powershell
        New-AzureADDirectorySetting -DirectorySetting $Setting
        ```
        **Note:** Since this is a new tenant, there’s no directory settings object in the tenant yet. You need to use ```New-AzureADDirectorySetting``` to create a directory settings object for the first time.


6. Test the newly configured settings.

    1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

    2. Test as **Alex Willber** from Teams desktop client, notice when select **Join or create a team**, there are options for **Create team** and **Join a team with a code**.     

    3. Test as **Lynne Robbins** from Teams web client, notice when select **Join or create a team**, only one option **Join a team with a code** is available.

        **Note:** When you are still able to create a new team, wait several minutes for the new configuration to take effect on your users.


7. Revert the change for enabling users to create new teams.

    1. Connect to the **Client 1 VM** where you have **Windows PowerShell** opened.  
    
    2. Load the Azure AD unified group template, by using the following cmdlet:

        ```powershell
        $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
        ```
    3.	Create a blank Azure AD tenant settings object:

        ```powershell
        $Setting = $Template.CreateDirectorySetting()
        ```
  
    4.	Apply the configured settings, to revert previous changes:
         
        ```powershell
        Set-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where {$_.DisplayName -eq "Group.Unified"}).id -DirectorySetting $Setting
        ```
8. In the PowerShell window, enter the following cmdlet to disconnect the current session from your Azure Active Directory tenant.

    ```powershell
    Disconnect-AzureAD
    ``` 
	
9. Close the PowerShell window and continue to the next task.
	
	
In this task, you have successfully created a new security group and configured Azure AD settings to restrict the creation of new groups to members of this group only. At the end of the task, you have successfully tested the new group creation restrictions.

#### Task 3 - Configure a new naming policy

As part of your Teams planning project, you will configure the naming policy where each new Microsoft 365 group or team needs to comply with the organization’s regulations on naming objects. Each group name should start with the letters **Group** and end with the **Country** attribute of the owners’ location. Furthermore, there is an internal regulation that forbids using the following specific keywords in Teams names: **CEO**, **Payroll**, and **HR**.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Naming policy**.

4. Configure **Blocked words**

    1. Under the **Blocked words** tab on the **Groups | Naming policy** page, select **Download** to download a sample file. 
    
    2. Navigate and right-select the downloaded file **BlockedWords.csv** and select **Open with** > **Notepad**.

    3. Type **CEO,Payroll,HR** replacing the empty quotes in the Notepad window, and saving the file. 
    
    4. Back to the **Groups | Naming policy** page, upload the saved .csv file under **3. Upload your .csv file** by selecting **Select a file** box or the folder icon.

    5. Select **Save** to apply the new blocked words setting.

5. Configure **Group naming policy**
    
    1. On the **Groups | Naming policy** page, select the **Group naming policy** tab.

    2. Add **Group_** string as prefix 
        
        1. Select the checkbox **Add prefix**. 
        2. Select the dropdown menu of **Select the type of prefix** and choose **String**. 
        3. Enter **Group_** to the text box.

    3. Add **Country or region** string as the suffix 
        
        1. Select the checkbox **Add suffix**. 
        2. Select the dropdown menu of **Select the type of suffix**, choose **String**, and enter **_** to the text box. 
        3. Select the dropdown menu of **Select the type of suffix**, choose **Attribute**, and Select **Country or region** from the dropdown menu. 
        
    4. Select **Save** to apply the new blocked words setting.


In this task, you have configured a naming policy that will block specific words to be used in a Microsoft 365 group name, as well as you have configured a new naming policy for the names of Microsoft 365 groups and teams.

#### Task 4 - Test the new naming policy

You need to test the newly created naming policy to see its effects in your pilot environment. In the following task, you will try to create a new team and see the configured naming policy template completing the configured name for your new team.

**Note:** It can take up to 24 hours till the blocked words setting will take effect. Therefore, you will only test the configured naming policy, which takes effect immediately.

1. Connect to the **Client 2 VM** and open the **Teams desktop client** (https://teams.microsoft.com/) as **Alex Wilber** (AlexW@&lt;YourTenant&gt;.onmicrosoft.com)

2. In the Teams desktop client, select **Teams** from the left menu.

3. Select **Join or create a team** from the lower-left corner.

4. Select **Create team** > **From scratch** > **Public**.

5. Enter **Afterwork** for the **Team name**.

	Below the entered name, you can see the configured prefix and suffix for new teams.

6. Select **Create** to create the new team.

7. Add **Lynne Robbins** to the team member.

8. Review the name of the newly created team.

You have successfully tested the naming policy for managing the prefix and suffixes of user-created teams.

#### Task 5 - Delete the naming policy

You can remove the naming policy after the test. In the following task, you will remove the naming policy you just created.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**.

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Naming policy**.

4. On the **Groups | Naming policy** page, select **Delete policy** > **Yes**.

#### Task 6 – Manage policy packages

To avoid administrative overhead with managing large numbers of policies individually for groups of different users, you need to evaluate using policy packages to group policies into logical units. In this task, you need to review the default policy packages and change a default policy package for first-line workers.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation of the Teams admin center, select **Policy packages**.

3. On the **Policy packages** page, select **Frontline worker (default)** policy package.

	![Table Description automatically generated](media/MS-700-lab_M03_ak_image7.png)

4. Update Messaging policy in **Frontline worker** policy package.

	1. Select **Frontline_Worker** right from **Messaging policy**.
	2. Select **Edit** from the upper right corner.
	3. Turn **On** the setting - **Send urgent messages using priority notifications** and select **Save**. 

5. Update Calling policy in **Frontline worker** policy package.

	1. Back to **Policy packages** page.
	2. Select **Frontline worker (default)** from the list again. 
	3. Select **Frontline_worker** right from **Calling policy**.
	4. Turn **On** the setting - **Prevent toll bypass and send calls through the PSTN**.
	5. Update **Busy on busy when in a call** to **Enabled**.
	6. Select **Save**.

6. Navigate to **Policy Packages** from the left navigation pane.

7. Make sure **Frontline worker** policy package is checked.

8. Select **Manage users** from the top menu.

7. Type **Allan** into the search box, select **Add** right from **Allan Deyoung** and **Apply**.

8. Check the policy assignment.

	1. Select **Users** > **Manage users** from the left-side pane.

	2. Select **Allan Deyoung** and select **Policies** tab.

	3. You can see the **Frontline worker** under policy package section.

You have successfully modified included policies from an existing policy package and assigned the package to a single user. This will help you assign the same set of policies to a group of users working in the same role or requiring the same access.
 

### **Exercise 5: Enable access to Teams public preview features using Teams update policies**

In this exercise, you will configure users to explore and evaluate upcoming features using Teams update policies. Public preview is enabled on a per-user basis, and Update policies are used to manage Teams and Office preview users who will see pre-release or preview features in the Teams app.

#### Task 1 - Create a custom Update policy

1. Connect to the **CLIENT1 VM** and browse to **Teams Admin Center** [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) as **Joni Sherman** ([JoniS@&lt;YourTenant&gt;.onmicrosoft.com](mailto:JoniS@&lt;YourTenant&gt;.onmicrosoft.com))

	**Note**: You can use **InPrivate window** of Microsoft Edge for logging in with different credentials.

2. In left navigation of the Teams admin center, select **Teams** > **Teams update policies**. 

3. Select **+ Add**

4. Enter the following information:

	- Name: **Enable Preview features**
	- Description: **Enable Teams public preview**
	- Show preview features: select **Enabled** 
	- Select **Apply** 

You now completed creating a custom **Teams Update policy.**
 

#### Task 2 - Assign the custom Update policy to users

Now you need to assign the custom Update policy to specific users because it doesn’t over-write the global policy.

1. Go to **Teams admin center** > **Teams** > **Teams update policies**.

2. Select the custom Update policy **Enable Preview features**.

3. Select **Assign users**.

4. Search and select **Add** next to the following pilot users:

	* Alex Wilber 
	* Lynne Robbins 
	* Diego Siciliani 

5. Select **Apply** to assign the custom update policy created in task 1.

END OF LAB
