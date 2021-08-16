---
lab:
    title: 'Lab 01: Manage Microsoft Teams '
    type: 'Answer Key'
    module: 'Module 1: Get started with managing Microsoft Teams '
---

# **Lab 01: Manage Microsoft Teams**

# **Student lab answer key**

## **Microsoft 365 user interface**

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual.

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## **Lab Scenario**

In the labs, of this course, you will assume the role of **Joni Sherman**, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to conduct a pilot project to test the implementation of Microsoft Teams against Contoso Ltd. business requirements.

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman (JoniS@&lt;YourTenant&gt;.OnMicrosoft.com) **Group coordinator / Teams admin**

- Alex Wilber (AlexW@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user from Canada**

- Lynne Robbins (LynneR@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user**

- Allan Deyoung (AllanD@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams communication support engineer**

- Megan Bowen (MeganB@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular employee**

## **Objectives**

After you complete this lab, you will be able to:

- Assign Teams admin roles to users

- Check license assignment for users

- Understand the Teams admin center and it’s menus

- Install the Teams PowerShell module and explore its cmdlets

- Create Microsoft 365 Groups from the M365 admin center

- Create new teams using the Teams Desktop client

- Create new teams using the Teams web client

- Configure expiration policies

- Restrict creation of new teams to members of a security group

- Create naming policies



## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Before you start**

The lab in this course have been prepared for a Microsoft Teams deployment at Contoso Ltd. Corporation. Contoso is running a Microsoft 365 cloud only deployment. The lab environments have been specifically designed in this manner to give you experience managing Microsoft Teams in a Microsoft 365 deployment. You will be provided with two virtual machines and a Microsoft 365 tenant to complete the lab steps.

#### **1. Sign in to the lab virtual machines**

The labs in this course will use two virtual machines:

- Client 1 VM : a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

- Client 2 VM : a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

**Note:** Lab virtual machine sign in instructions will be provided to you by your instructor.

**Important:** The exercises in the MS-700 labs are cloud-only deployments. A local administrator account has been created on the client VMs. You will log into the VMs as a local administrator instead of a domain account. Following your login, the desktop will indicate that you are logged in as either **CLIENT1\Admin** or **CLIENT2\admin**, depending on which machine you are on.

#### **2. Review installed applications**

Once you signed in to the VM, observe the start menu, and verify following applications have been installed:

- Microsoft Teams

#### **3. Review Microsoft 365 tenant**

Beside two VMs, you will also be provided with a Microsoft 365 tenant with following highlights:

- Office 365 E5 with Enterprise Mobility + Security E5.

- 15 licenses in total with 5 available of 15(10 used).

- One Global Administrator (MOD Administrator) and 9 standard users have been pre-created.

  **Note:** Microsoft 365 sign in instructions will be provided to you by your instructor.

- The username of the Global Administrator (MOD Administrator) is **admin@&lt;YourTenant&gt;.onmicrosoft.com**.

- **&lt;YourTenant&gt;.onmicrosoft.com** - This is the domain associated with the Microsoft 365 tenant that was provided by the lab hosting provider. The first part of this domain name (&lt;YourTenant&gt;) is the unique tenant ID provided by the lab hosting provider. The &lt;YourTenant&gt; portion of the tenant ID, which is the tenant suffix ID, will be unique for each student.

  **IMPORTANT:** This is critical because throughout this lab, you will be asked to enter the **&lt;YourTenant&gt;.onmicrosoft.com** domain name when signing into apps with a given username (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com). When doing so, you must enter the unique tenant suffix ID that is assigned to your tenant ID in place of the **&lt;YourTenant&gt;**.

  For example, if your Tenant Email is **admin@contosolab.onmicrosoft.com**, the unique tenant suffix ID (&lt;YourTenant&gt;) is **contosolab**. When signing in as Joni when entering this domain, you would replace &lt;YourTenant&gt; with contosolab (for example, JoniS@contosolab.onmicrosoft.com).

   **RECOMMENDATION:** You should write down your unique tenant suffix, mentioned as &lt;YourTenant&gt; in this lab and provided by your training provider. After a while, you will have this name or number memorized as you move through the labs in this course.

- **Use the new Microsoft 365 admin center** 

  Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center, make sure the slider in the upper right corner is set to **The new admin center**. If you can read **Try the new admin center**, select the slider and activate it.  
‎‎  
‎‎  **IMPORTANT:** The instructions that are provided in the lab exercises for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

### **Exercise 1: Prepare Teams admin roles and licenses**

In the first exercise you will assign required administrative roles to users and check license assignments for the Teams license. To perform these tasks, you will use default tenant global admin.

#### **Task 1 - Assign Teams admin roles to users**

In this task you will use the default global admin to sign in to the Microsoft 365 admin center and assign several Teams admin roles to different users. This task is crucial for later tasks and exercises as you will perform most of the tasks in context of Joni Sherman’s account.

1. Browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**. 

    1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

    2. Open **Microsoft Edge** and browse to the **Microsoft 365 admin center** at [**https://admin.microsoft.com/**](https://admin.microsoft.com/) with the Global admin credential ( **MOD Administrator** : admin@&lt;YourTenant&gt;.onmicrosoft.com) .

2. Assign **Teams admin** role to **Joni Sherman**

    1. Select the navigation menu in the upper-left and select **Users** and **Active users** from below it.

    2. In the Active users list, search and select **Joni Sherman**, to open the right-side settings pane.

    3. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

    4. On the **Manage admin roles** pane, select **Admin center access** and scroll down to select **Show all by category** to reveal all avaliable roles. 
    
    5. Select **Teams Administrator** checkbox then select **Save changes**. You will see the message **Admin roles updated** on the upper part of the pane to comfirm the update. 

3. Assign **Teams device admin** role to **Alex Wilber**

    Repeat the same steps and assign **Teams Device Administrator** role to **Alex Wilber**.

4. Assign **Teams communication admin** role to **Allan Deyoung**

    Repeat the same steps and assign **Teams communication admin** role to **Allan Deyoung**.

You have now successfully assigned the Teams admin roles.

* Teams Administrator: Joni Sherman
* Teams Devices Administrator: Alex Wilber
* Teams communication admin: Allan Deyoung 

Proceed to the next task.

#### **Task 2 – Check license assignment of your users**

In this task, you will check the license assignment of all users participating in the pilot. At the end of the task you will confirm that all pilot users are licensed correctly and Alex Wilber’s location is updated to Canada as preparation for a later task.

1. Connect to the **Client 1 VM** and browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.

2. Update **Alex Wilber's** location to **Canada**

    1. On the **Users** > **Active users** page, select the name of **Alex Wilber**.

    2. Select **Licenses and Apps** tab. 

    3. Select the dropdown menu under **Select location**, and update to **Canada**. 

    4. Select **Save changes**. 

3. Check **Alex Wilber's** licenses

    1. On the same tab, under **Licenses** section, verify that **Enterprise Mobility + Security E5** and **Office 365 E5** are both selected.

    2. Select **Apps** to expand All licenses.

    3. Scroll down the list of all apps, and verify **Microsoft Teams** is selected. 
    
4. You can repeat the same steps to check other users' licenses. Do not change their locations. 

You have successfully validated that all users participating in the pilot own Teams licenses and are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task. 

You have finished the first exercise, and you can continue with the next one.


### **Exercise 2: Explore Teams management tools**

In this exercise, you will explore Teams admin center and install the Teams PowerShell module, required to manage teams, policy packages, calling features, and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center and the PowerShell. You can create scripts for automation and even access several settings not available in the GUI.

To perform these tasks, you will use Joni Sherman’s account (JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com).

#### **Task 1 - Explore Teams admin center**

You will review the available settings for managing Teams in the Teams admin center.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

    **Note:** You can use **InPrivate window** of Microsoft Edge for logging in with different credentials. 

2. In left navigation of the Teams admin center, select **Teams** > **Manage teams**.

3. The **Manage teams** page show the existing teams in your organization. Note that there is an org-wide team named **Contoso** that is automatically created for new tenant with less than 5000 users.

4. In left navigation of the Teams admin center, select **Teams** > **Teams policies**. You can see the default Teams policy named **Global (Org-wide default)**.

You can explore other settings to familiarize various controls in the Teams admin center.

You have successfully explored several available menus from the Teams admin center for managing teams and configuring policies in your tenant. 


#### **Task 2 - Install and explore Teams PowerShell module**

In this task, you will install and connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system and do not need to download any executables via the browser.

1. Connect to the **Client 1 VM** with the VM credential that have been provided to you.

2. Open **Windows PowerShell** and run as Administrator.

    1. Select **Start** and search for **Windows PowerShell (Admin)**, then right select **Run as administrator**.

    2. Confirm the **User Account Control** window with **Yes**.

3. Install **Microsoft Teams PowerShell module**

    1. In the PowerShell window, enter the following cmdlet and press **Enter:**

        ```powershell
        Install-Module -Name MicrosoftTeams
        ```
    2. Enter **Y** and press **Enter** twice to confirm the installation of the NuGet provider and Untrusted repository.

4. Connect to your tenant.

    1. Enter the following cmdlet in the PowerShell window and press **Enter**:

        ```powershell
        Connect-MicrosoftTeams
        ```
    2. In the Sign in window, sign in as Teams admin - Joni Sherman (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

        When the sign in was successful, several information about the signed in user and the tenant are displayed. 
        
5. Explore **Microsoft Teams PowerShell module**

    1. To confirm the MicrosoftTeams module is loaded correctly, enter the following cmdlet and press **Enter** to view all available PowerShell modules:

        ```powershell
        Get-Module
        ```
        **Note**: To the left of the **Name** column, the version of the PowerShell module is displayed.

    2. To get an overview of the available Teams PowerShell cmdlets from the MicrosoftTeams module, enter the following cmdlet and then press **Enter**:

        ```powershell
        Get-Command -Module MicrosoftTeams
        ```

    3. The Get-Help cmdlet is used explore the available cmdlets. For example, to get more information about how to create a team with PowerShell, enter the following cmdlet and press **Enter**:

        ```powershell
        Get-Help New-Team
        ```

        If you receive a message to update the help libraries, type **Y** for yes.

    4. Disconnect from the Microsoft Teams environment.  

        ```powershell
        Disconnect-MicrosoftTeams
        ```
6. Close the PowerShell window and continue to the next task.

You have successfully used the Microsoft Teams PowerShell module to connect to Teams and explored available cmdlets.


### **Exercise 3: Create groups and teams**

In this exercise, you will create a Microsoft 365 Group from the Microsoft 365 admin center and creating a team from the Teams desktop client and the web client.

#### **Task 1 - Create a Microsoft 365 Group**

You will create a new Microsoft 365 Group named "IT-Department," and then add the pilot members serving as a basis for your future teams and licensing.


1. Connect to the **Client 1 VM** and browse to the **Microsoft 365 admin center** (https://admin.microsoft.com/) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the Microsoft 365 admin center, select **Groups** > **Active** **Groups**.

3. On the **Active groups** page, select **Add a group**.

4. Follow the **Add a group** wizard with the following information:

    * Group type : Select **Microsoft 365 (recommended)**.
    * Basics : 
    	- Name: **IT-Department**
    	- Description: **All staff of the IT-Department**
    
    * Owners : 
        - Select **+ Assign owners** 
        - Search and select **Joni Sherman**
        - Select **Add(1)**, and then select **Next**.

    * Members : 
        - Alex Wilber
        - Allan Deyoung
        - Lynne Robbins
        - Megan Bowen

    * Settings : 
        - Enter **IT-Department** for Group email address. 
        - Privacy : Private
        - Uncheck **Create a team for this group**.

5. Select **Create group** > **Close**.

6. Wait a moment and select **Refresh** until the group is visible. You will see there is no Teams icon in the **Teams status** column.

7. Select the **IT-Department** group to review the settings and members. 

The new Microsoft 365 Group with the name "IT-Department" was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a new team by using the desktop client**

To test the self-service capabilities of Teams, in this task, **Megan Bowen** will sign in to the Teams Desktop client, create a new team with the name **Teams Rollout** and add all members participating in the Teams evaluation project.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams Desktop client.

3. When prompted to **Enter your work, school or Microsoft account**. Sign in as **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

4. In the Teams client, select **Join or create a team** from the lower left corner. 

5. Select **Create team** >**From scratch** > **Public**. Enter the team name **Teams Rollout** and select **Create**.

6. On the **Add members to Teams Rollout** window, enter the following names and select **Add**. 

    * Alex Wilber
    * Allan Deyoung
    * Joni Sherman
    * Lynne Robbins

7. Select the dropdown menu next to Joni Sherman and switch from **Member** to **Owner**. 

8. Select **Close**.

You have successfully created a new team from the Teams desktop client, added the project team members, and you have made Joni Sherman a team owner. 

#### **Task 3 - Create a new team by using the web client**

In this task, **Lynne Robbins** will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name **Sales**. She will also add Megan Bowen as a member.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Browse to the **Microsoft Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/) and sign in as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

4. Select **Join or create a team** from the lower left corner. 

5. Select **Create team** >**From scratch** > **Private**. Enter the team name **Sales** and select **Create**.

6. On the **Add members to Sales** window, enter the following names and select **Add** > **Close**.

    * Megan Bowen

The newly created team is displayed in the list of your teams. You have successfully created a new team with the Teams web client. 



### **Exercise 4: Implement governance and lifecycle management for Microsoft Teams**

Your organization has started the planning process for Microsoft 365 services adoption. You are assigned as a Teams admin role to plan Teams governance. Since Teams relies on Microsoft 365 groups, you need to plan governance procedures for Microsoft 365 groups, including creating **Microsoft 365 groups expiration policies**, configuring **Microsoft 365 Group creation policy permissions**, configuring and test **Microsoft 365 Groups naming policies**.

#### Task 1 - Create and assign an expiration policy

Based on the organization requirement, unneeded groups should be deleted automatically after 90 days. To evaluate the expiration feature for Teams, you will configure a group expiration policy that will expire the **Teams Rollout** group after 90 days.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Expiration**.

5. On the **Groups | Expiration** page, configure the following settings:

	- In the dropdown menu of **Group lifetime (in days)**, select **Custom** and enter **90** to the text box.

	- In the text box right from **Email contact for groups with no owners**, enter (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

	- Right from **Enable expiration for the Office 365 groups**, select **Selected**.

	- Select **+ Add** to open the **Select groups** right-side pane. 

	- In the **Select groups** pane, type **Teams Rollout** into the textbox and select the group.

	- Use the **Select** button on the lower end of the right-side pane to apply the policy to the **Selected group**.

	- Back on the **Groups | Expiration** page, select **Save**.

You have successfully created a new expiration policy and configured the **Teams Rollout** team to expire after 90 days. If the team doesn't have an owner after 90 days, Joni Sherman will be notified about the expiration.

#### Task 2 - Configure a group creation policy

You are an administrator for your Teams organization. You need to limit which users are able to create Microsoft 365 groups. You will create a security group named **GroupCreators** which only the members of the group can create Microsoft 365 groups.

1. Connect to the **Client 1 VM** and browse to the **Microsoft 365 admin center** (https://admin.microsoft.com/) as the Global admin - MOD Administrator(admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a security group.

    1. In the Microsoft 365 admin center, select **Groups** > **Active** **Groups**.

    2. On the **Active groups** page, select **Add a group**.

    3. Follow the **Add a group** wizard with the following information:

    * Group type : Select **Security**.
    * Basics : 
    	- Name: **GroupCreators**
    	- Description: **Users who can create Microsoft 365 Groups for new teams**

    4. Back to **Active group** page, select the security group **GroupCreators** you just created. Select **Members** tab to configure the **Owners** and **Members**.

    * Owners : 
        - MOD Administrator

    * Members : 
        - Joni Sherman
        - Lynne Robbins

3. Open **Windows PowerShell** and run as Administrator.

4. Install **Azure AD Preview module**

    In the PowerShell window, enter the following cmdlet and press **Enter**. Enter **Y** and press **Enter** to confirm the installation of untrusted repository.

    ```powershell
    Install-Module -Name AzureADPreview
    ```

5. Connect to your AAD tenant.

    Enter the following cmdlet in the PowerShell window and press **Enter**. In the Sign in window, sign in as the Global admin - MOD Administrator(admin@&lt;YourTenant&gt;.onmicrosoft.com).

    ```powershell
    Connect-AzureAD
    ```
6. Load the Azure AD unified group template, by using the following cmdlet:

   ```powershell
   $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
   ```
7. Check if an Azure AD setting is already existing and load it, if yes. If not, create a blank Azure AD setting object. Run the following cmdlet to populate the "$Setting" variable:

   ```powershell
   if(!($Setting = Get-AzureADDirectorySetting | Where {$_.TemplateId -eq $Template.Id})) {$Setting = $Template.CreateDirectorySetting()}
   ```
8. Run following cmdlet to modify the group creation setting for your tenant with the "EnableGroupCreation" attribute:

   ```powershell
   $Setting["EnableGroupCreation"] = "False"
   ```
9. Run following cmdlet to add the just created security group **GroupCreators** as permitted group to create groups, by their ObjectID:

   ```powershell
   $Setting["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString "GroupCreators").objectid
   ```
10. Review the changes you have just configured with the following command:

    ```powershell
    $Setting.Values
    ```

11. Save the changes and apply the setting:

    ```powershell
    New-AzureADDirectorySetting -DirectorySetting $Setting
    ```
	**Note:** Since this is a new tenant, there’s no directory settings object in the tenant yet. You need to use ```New-AzureADDirectorySetting``` to create a directory settings object at the first time.

12. Disconnects the current session from an Azure Active Directory tenant and close the PowerShell window.

    ```powershell
    Disconnect-AzureAD
    ```

13. To test the newly configured settings, connect to the **Client 2 VM** with the credentials that have been provided to you.

    1. Test as **Megan Bowen** from Teams desktop client, notice when select **Join or create a team**, only one option **Join a team with a code** is available. 

    2. Test as **Lynne Robbins** from Teams web client, notice when select **Join or create a team**, there are options for **Create team** and **Join a team with a code**.

**Note:** When you are still able to create a new team, wait several minutes for the new configuration to take effect on your users.

In this task, you have successfully created a new security group and configured Azure AD settings to restrict the creation of new groups to members of this group only. At the end of the task, you have successfully tested the new group creation restrictions.

#### Task 3 - Configure a new naming policy

As part of your Teams planning project, you will configure the naming policy where each new Microsoft 365 Group or Team needs to comply with the organization’s regulations on naming objects. Each group name should start with letters **Group** and end with the **Country** attribute of the Owners location. Furthermore, there is an internal regulation that forbids using following specific keywords in Teams names: CEO, Payroll and HR.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Naming policy**.

4. Configure **Blocked words**

    1. Under **Blocked words** tab on the **Groups | Naming policy** page, select **Download** to download a sample file. 
    
    2. Nevigate and right-select the downloaded file **BlockedWords.csv** and select **Open with** > **Notepad**.

    3. Type **CEO,Payroll,HR** replacing the empty quotes in the Notepad window, and save the file. 
    
    4. Back to the **Groups | Naming policy** page, upload the saved .csv file under **3. Upload your .csv file** by selecting **Select a file** box or the folder icon.

    5. Select **Save** to apply the new blocked words setting.

5. Configure **Group naming policy**
    
    1. On the **Groups | Naming policy** page, select the **Group naming policy** tab.

    2. Add **Group_** string as prefix 
        
        1. Select the checkboxes **Add prefix**. 
        2. Select the dropdown menu of **Select the type of prefix** and choose **String**. 
        3. Enter the following to the empty text box: **Group_**

    3. Add **Country or region** string as suffix 
        
        1. Select the checkboxes **Add suffix**. 
        2. Select the dropdown menu of **Select the type of suffix**, choose **String**, and enter **_** to the text box. 
        3. Select the dropdown menu of **Select the type of suffix**, choose **Attribute**, and Select **Country or region** from the dropdown menu. 
        
    4. Select **Save** to apply the new blocked words setting.

In this task, you have configured a naming policy that will block specific words to be used in a Microsoft 365 Group name, as well as you have configured a new naming policy for Microsoft 365 Group and Teams names.

#### Task 4 - Test the new naming policy

You need to test the newly created naming policy to see its effects in your pilot environment. In the following task, you will try to create a new team and see the configured naming policy template completing the configured name for your new team.

**Note:** It can take up to 24 hours till the blocked words setting will take effect. Therefore, you will only test the configured naming policy, which takes effect immediately.

1. Connect to the **Client 2 VM** and browse to the **Teams web client** (https://teams.microsoft.com/) as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com)

2. Select **Create team** > **From scratch** > **Public**.

3. Enter **Afterwork** for the **Team name**.

    Below the entered name, you can see the configured prefix and suffix for new teams.

4. Select **Create** to create the new team.

5. Select **Skip** to not add any additional members.

6. Review the name of the newly created team.

You have successfully tested naming policy for managing the prefix and suffixes of user created teams.

#### Task 5 - Delete the naming policy

You can remove the naming policy after the test. In the following task, you will remove the naming policy you just created. 

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups** page, select **Naming policy**.

4. One the **Groups | Naming policy** page, select **Delete policy** > **Yes.**


END OF LAB
