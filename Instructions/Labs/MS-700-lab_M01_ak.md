---
lab:
    title: 'Lab 01: Manage roles and create teams'
    type: 'Answer Key'
    module: 'Module 1: Microsoft Teams in Microsoft 365'
---

# **Lab 01: Manage roles and create teams**

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

- Import the Skype for Business Online PowerShell cmdlets

- Create Microsoft 365 Groups from the M365 admin center

- Create new teams using the Teams Desktop client

- Create new teams using the Teams web client

## **Lab Setup**

- **Estimated Time:** 60 minutes.

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

### **Exercise 1: Prepare team roles and licenses**

In the first exercise you will assign required administrative roles to users, check license assignments for the Teams license and then explore the Microsoft Teams admin center. To perform these tasks, you will use default tenant global admin and the Joni Sherman’s account (JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com).

#### **Task 1 - Assign Teams Admin Roles to users**

In this task you will use the default global admin to sign in to the Microsoft 365 admin center and assign several Teams admin roles to different users. This task is crucial for later tasks and exercises as you will perform most of the tasks in context of Joni Sherman’s account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge** and navigate to the **Office 365 Portal** at [**https://portal.office.com/**](https://portal.office.com/).

3. When the Sign in window is displayed, sign in as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) using the credentials provided to you.

4. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.

5. Close the password save dialog from the bottom with **Never**, not to save the default global admins credentials in your browser.

6. If a welcome screen is displayed, close it. If the Office 365 apps notification appear, also close it.

7. Select the app launcher icon in the upper-left and choose **Admin**.

8. If a welcome window is displayed, select **Get started** and close it.

9. Select the navigation menu in the upper-left and select **Users** and **Active users** from below it.

10. In the Active users list, search and select **Joni Sherman**, to open the right-side settings pane.

11. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

12. When the **Manage roles** pane opens, select **Admin center access** and scroll down to select **Show all by category** to reveal all avaliable roles. Select the **Teams service admin** and **Teams Device Administrator** roles.

13. Select **Save changes** to apply the role. When the **Admin roles updated** message is displayed on the upper part of the pane, close the window of Joni Sherman’s account with the **X** in the upper right to go back to the **Active users** list.

14. Search for **Allan Deyoung** in the list of users, and select his name to open another settings pane.

15. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

16. When the **Manage roles** pane opens, select **Admin center access** and scroll down to the end and select **Show all by category**. Then scroll further down and select the **Teams communication support engineer** role.

17. Select **Save changes** to apply the role. When the **Admin roles updated** message is displayed, close Allan’s profile pane and leave the client open at the Microsoft 365 admin center.

You have now successfully assigned the Teams service admin role to Joni Sherman and the Teams communications support engineer to Allan Deyoung. Proceed to the next task.

#### **Task 2 – Check license assignment of your users**

In this task, you will check the license assignment of all users participating in the pilot. You will continue where you left off in the last task, signed in as the MOD Administrator on Client 1 VM, with an open browser window in the Microsoft 365 admin center. At the end of the task you will confirm that all pilot users are licensed correctly and change Alex’s location to Canada as preparation for a later task.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You should still be signed in to the **Microsoft 365 admin center** ([https://admin.microsoft.com/](https://admin.microsoft.com/)) as the **MOD Administrator**. 

3. If you are not already on the **Active users** page, open the left side pane, select **Users** and **Active users** below.

4. In the Active users list, select **Alex Wilber** to open the right-side settings pane.

5. From the now visible tabs, select **Licenses and Apps**.

6. Check if the dropdown menu below **Select location** is set to **United States**. Change it to **Canada**. Then select **Save changes** at the end of the window and continue with the next step.

   Note: If you possibly receive an error message, deselect all licenses and select them again to process the assignment correctly and to make the location change work.

7. Below **Licenses**, verify that **Enterprise Mobility + Security E5** and **Office 365 E5** are both selected with a checkmark.

8. Select the dropdown arrow right beside **Apps** to open the view for the single licenses.

9. Scroll down the list of all apps to **Microsoft Teams** with **Office 365 E5** listed below it and validate this entry has a checkmark left of it. This indicates that the user has a valid Teams license from the Office 365 E5 subscription package assigned.

10. Close the window with the **X**, below the circle with the MA, which stands for the currently signed in user **MOD Administrator**.

11. Repeat the steps 3 to 9 for the users **Joni Sherman**, **Lynne Robbins**, **Allan Deyoung** and **Megan Bowen** to check their assigned licenses, but skip step 6 and do not change their location.

12. After checking the licenses of all users, leave the browser open with the Microsoft 365 admin center.

You have successfully validated that all users participating in the pilot own Teams licenses and are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task.

#### **Task 3 - Explore Teams Admin center**

You need to test access and review the available settings for administering Teams in the Teams admin center. As an administrator for Teams, it’s important to get to understand the different settings and policies available in the Microsoft Teams Admin Center. You will sign in with Joni Sherman’s account for this task:You assigned the Teams Service Administrator role in the first task.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

   **Note**: You should still be signed into Office 365 as **MOD Administrator**. You will sign out this user and sign in with Joni Sherman’s account, to perform this task.

2. In the browser window, select the circle with **MA** in the upper right corner, open the side pane and select **Sign out**.

3. Close your browser window and re-open **Microsoft Edge** again and navigate to [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) to open the Teams admin center.

4. When the **Pick an account** window is displayed, select **Use another account**. Sign in as (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) using the credentials provided to you.

5. The Microsoft Teams admin center **Dashboard** is displayed. If a **Welcome to the Teams admin** center message is displayed, select **Skip tour**. 

6. Select the navigation button in the upper-left to maximize the left-side pane and hover over the first symbol below, which is named **Teams**. Select **Manage Teams**. 

7. On the **Manage teams** page, the teams existing in your organization are displayed. Note that there is a single org-wide team named **Contoso** that is automatically created for organizations with less than 5000 users that are new to Teams.

8. Select **Teams policies** in the left navigation. In the middle of the screen, the Teams policies are displayed. Note that there is a single policy named **Global (Org-wide default)**. Select the **Global (Org-wide default)** policy to open a right-side settings pane and review the configured default global settings. Do not make any changes and then select **Cancel**.

9. Repeat the last steps for the other menus in the left navigation as you wish and explore the different default policies and settings. Do not make any changes and just explore the UI to understand the structure and options the Teams admin center provides.

10. When you are finished reviewing all settings from the Teams admin center, leave the client open as it is.

You have successfully explored several available menus from the Teams admin center, for managing teams and configuring policies in your tenant. You have finished the first exercise, and you can continue with the next one.

### **Exercise 2: Explore PowerShell cmdlets for Teams**

In this exercise you will install the Teams PowerShell module, required to manage teams, policy packages, calling features, and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center also in the PowerShell. You can create scripts for automation and even access several settings not available in the GUI.

#### **Task 1 - Install Teams PowerShell module**

Before you can connect to Teams from your tenant and perform any actions, you need to install the Teams PowerShell module. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system and do not need to download any executables via the browser.

**Note:** The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks when done on servers.
 
1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the **User Account Control** window with **Yes**.

4. In the PowerShell window, enter the following cmdlet and press **Enter**, to change the execution policy:

   ```powershell
   Set-ExecutionPolicy Unrestricted
   ```
5. Enter **Y** and press **Enter** to confirm the security dialog for **Executing Policy Change**.

6. To install the Microsoft Teams module from the PsGallery repository, in the PowerShell window, enter the following cmdlet and press **Enter:**

   ```powershell
   Install-Module -Name MicrosoftTeams
   ```
7. When you are prompted to install and import the NuGet provider, confirm by entering **Y** and pressing **Enter**.

8. When you are prompted to install from the Untrusted repository, also confirm by entering **Y** and pressing **Enter**.

9. Close the elevated PowerShell window and continue to the next task.

You have now successfully installed the latest available Microsoft Teams PowerShell module from the PSGallery repository. Continue with the next task.

#### **Task 2 - Explore Teams PowerShell cmdlets**

In this task, you will connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start** button and then select **Windows PowerShell**.

3. To connect to Microsoft Teams in your tenant, enter the following cmdlet in the PowerShell window and press **Enter**:

   ```powershell
   Connect-MicrosoftTeams
   ```
4. A **Sign in** dialog box will open. Sign in as (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) using the Credentials provided to you.

5. When the sign in was successful, several information about the signed in user and the tenant are displayed. To confirm the MicrosoftTeams module is loaded correctly, enter the following cmdlet and press **Enter** to view all available PowerShell modules:

   ```powershell
   Get-Module
   ```
   **Note**: To the left of the **Name** column, the version of the PowerShell module is displayed.

6. To get an overview of the available Teams PowerShell cmdlets from the MicrosoftTeams module for managing Teams, enter the following cmdlet and then press **Enter**:

   ```powershell
   Get-Command -Module MicrosoftTeams
   ```
7. The Get-Help cmdlet is used explore the available cmdlets. For example, to get more information about how to create a team with PowerShell, enter the following cmdlet and press **Enter**:

   ```powershell
   Get-Help New-Team
   ```
1. If you receive a message to update the help libraries, type **Y** for yes.

8. When you are finished with exploring the Microsoft Teams PowerShell cmdlets, leave the PowerShell window open and continue to the next task.

You have successfully used the Microsoft Teams PowerShell module to connect to Teams in your tenant and explored some available cmdlets.
  

### **Exercise 3: Create groups and teams**

In this exercise, you will create some resources required in later tasks. These include creating a Microsoft 365 Group from the Microsoft 365 admin center and creating a team in the Desktop client and then the web client.

#### **Task 1 - Create a Microsoft 365 Group**

In real world scenarios, the Microsoft 365 Groups would already exist and your task as Teams service admin would only be to enable their Teams functionality, but for this lab you need to create them manually.

You will create the new Microsoft 365 Group named "IT-Department," and then add the pilot members serving as a basis for your future teams and licensing.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 admin center** at [**https://admin.microsoft.com/**](https://admin.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. In the Microsoft 365 admin center, select the navigation menu in the upper-left, select **Groups** > **Active** **Groups**.

4. Select **Add a group** in the **Active** **groups** window to open the **Add a group** page.

5. Select the group type **Microsoft 365 (recommended)** and select **Next**.

6. Enter the following information to the text fields:

	- Name: **IT-Department**

	- Description: **All staff of the IT-Department**

 

7. Select **Next**.

8. In the Owners field type in the Name of **Joni Sherman**, select her from the **Users** list, and then select **Next**.

9. As the group email address type in **IT-Department**@&lt;YourTenant&gt;.onmicrosoft.com, set the privacy to **Private – Only members can see group content**, clear the **Create a team for this group** checkbox, and then select **Next**.

10. On the **Review** page, verify the settings and then select **Create group**.

11. When the **New group created** information appears, select **Close**.

12. Wait a moment and select **Refresh** until the group is visible. You will see there is no Teams icon in the **Teams status** column.

13. Select the **IT-Department** group to open the settings pane.

14. On the **Members** tab, select **View all and manage members**.

15. In the new window, select **+ Add members** from the top and select the checkbox before the following users: **Alex Wilber**, **Allan Deyoung**, **Lynne Robbins**, and **Megan Bowen**.

16. Select **Save,** then **Close** two times and close the IT-Department pane with the **X**.

17. Close the browser window.

The new Microsoft 365 Group with the name "IT-Department" was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a new team by using the desktop client**

To test the self-service capabilities of Teams, in this task, Megan Bowen will sign in to the Teams Desktop client, create a new team with the name "Teams Rollout" and add all members participating in the Teams evaluation project.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams Desktop client.

3. When prompted to **Enter your work, school or Microsoft account**. Sign in as (MeganB@&lt;YourTenant&gt;.onmicrosoft.com) using the O365 Credentials provided to you.

4. The Microsoft Teams Desktop client will start. If a **Bring your team together** window appears, or **Get the Teams mobile app**, or another message, close them with the **X** or **Try it now**.

5. If you are not already in the **Teams** overview, in the left-hand navigation pane, select **Teams.** Then, select **Join or create a team** from the lower end of the Teams list.

6. Select **Create team** in the middle of the window.

7. In the **Create your team** window, select **From scratch**, then select **Public**. Enter the team name **Teams Rollout** and select **Create**.

8. On the **Add members to Teams Rollout** window, enter the names of the desired team members and select their names to add them to the textbox: **Alex Wilber**, **Allan Deyoung**, **Joni Sherman**, and **Lynne Robbins**.

9. Select **Add** to add them to the team.

10. Wait for all four users to be listed on the **Add members to Teams Rollout** window as Members, and then change the status of Joni Sherman from **Member** to **Owner** with the dropdown menu.


12. Select **Close**.

You have successfully created a new team with the Teams Desktop client, added the project team members, and you have made Joni Sherman a second owner of the team. Close the Teams client and continue with the next task.

#### **Task 3 - Create a new team by using the web client**

In this task, Lynne Robbins will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name "Sales". She will also add Megan Bowen as a member.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/).

3. When the Sign in window is displayed, sign in as (LynneR@&lt;YourTenant&gt;.onmicrosoft.com) using the O365 credentials provided to you.

4. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.

5. Close the password save dialog from the bottom with **Never**, not to save the default global admins credentials in your browser.

6. A landing page with a **Download the Teams desktop app and stay better connected** message is displayed. Select **Use the web app instead** below this message.

7. Another welcome message is displayed. Close all messages with **Try it now** or the **X**.

8. Select **Teams** from the left-side pane if you are not already in the **Teams** overview.

9. Select **Join or create a team** from the lower end of the Teams list.

10. Select **Create team** from the middle of the window.

11. In the **Create your team** window, select **From scratch**, then select **Private**. Enter the team name **Sales** and select **Create**.

12. In the **Add members to Sales** dialog, enter **Megan Bowen** to add her as a team member.

13. Select **Add** to add her to the team.

14. After adding the members to the Sales team, verify that Megan Bowen has been added correctly as a **Member**.

15. Select **Close**.

16. The newly created team is displayed in the list of your teams.

17. Close the Microsoft Edge window.

You have successfully created a new team with the Teams web client. This is the end of lab 1. You can close all browser windows and proceed to the next lab.

END OF LAB
