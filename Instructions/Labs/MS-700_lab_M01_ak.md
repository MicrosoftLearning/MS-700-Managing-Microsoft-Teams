--- 
lab: 
    title: 'Lab: Manage roles and create teams'
    type: 'Answer Key' 
    module: 'Module 01: Microsoft Teams in Microsoft 365' 
---

# Lab 01: Manage roles and create teams
# Student lab answer key
## Microsoft 365 user interface 

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual. 

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## Lab Scenario  

In the labs of this course you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to conduct a pilot project to test the implementation of Microsoft Teams against Contoso Ltd. business requirements. 

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman (JoniS@YourTenant.onmicrosoft.com) **Group coordinator / Teams admin**
- Alex Wilber (AlexW@YourTenant.onmicrosoft.com) **Regular pilot user from Canada**
- Lynne Robbins (LynneR@YourTenant.onmicrosoft.com) **Regular pilot user**
- Allan Deyoung (AllanD@YourTenant.onmicrosoft.com) **Teams communication support engineer**
- Megan Bowen (MeganB@YourTenant.OnMicrosoft.com) **Regular employee**

## Objectives

After you complete this lab, you will be able to:

- Assign Teams admin roles to users
- Check license assignment for users
- Understand the Teams admin center and it’s menus
- Install the Teams PowerShell module and explore its cmdlets
- Install the Skype for Business Online PowerShell module and explore its cmdlets
- Create Office 365 groups from the M365 admin center
- Create new teams using the Teams Desktop client
- Create new teams using the Teams web client
 
## Lab Setup  
- **Estimated Time:** 60 minutes.

## Instructions
### Before you start

The lab in this course have been prepared for a Microsoft Teams deployment at Contoso Ltd. Corporation. Contoso is running a Microsoft 365 cloud only deployment. The lab environments have been specifically designed in this manner to give you experience managing Microsoft Teams in a Microsoft 365 deployment. You will be provided with two virtual machines and a Microsoft 365 tenant to complete the lab steps. 

#### **1. Sign in to the lab virtual machines**

The labs in this course will use two virtual machines:

- Client 1 VM : a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

- Client 2 VM : a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

**Note:** Lab virtual machine sign in instructions will be provided to you by your instructor.

**Important:** A local administrator account has been created on the client VMs. These will be the accounts that you use to sign in to each VM. All MS700 lab exercises will use the admin account for sign-in. 

Since the MS700 lab scenario involves a cloud-only deployment, you will not be signing in into an on-premises domain, since no such domain exists. Following your sign-in, the desktop will indicate that you are signed in as either the local user **CLIENT01\Admin** or **CLIENT02\admin**, depending on which machine you are on.


#### **2. Review installed applications**

Once you signed in to the VM, observe the start menu, and verify following applications have been installed:

- Microsoft Teams

#### **3. Review Microsoft 365 tenant**

Beside two VMs, you will also be provided with a Microsoft 365 tenant with following highlights:

- Office 365 E5 with Enterprise Mobility + Security E5.
- 15 licenses in total with 5 available of 15(10 used).
- One Global Administrator (MOD Administrator) and 9 standard users have been pre-created.

     **Note:** Microsoft 365 sign in instructions will be provided to you by your instructor.
	  
- The username of the Global Administrator (MOD Administrator) is **admin@YourTenant.onmicrosoft.com**. 

- **@YourTenant.onmicrosoft.com -** This is the domain associated with the Office 365 tenant that was provided by the lab hosting provider. The first part of this domain name (YourTenant) is the unique tenant ID provided by the lab hosting provider. The YourTenant portion of the tenant ID, which is the tenant suffix ID, will be unique for each student. 

	**IMPORTANT:** This is critical because throughout this lab, you will be asked to enter the **YourTenant.onmicrosoft.com** domain name when signing into apps with a given username (for example, JoniS@YourTenant.onmicrosoft.com). When doing so, you must enter the unique tenant suffix ID that is assigned to your tenant ID in place of the **YourTenant**.

	For example, if your Tenant Email is **admin@contosolab.onmicrosoft.com**, the unique tenant suffix ID (YOURTENANT) is **contosolab**. When signing in as Joni when entering this domain, you would replace YOURTENANT with contosolab (for example, JoniS@contosolab.onmicrosoft.com). 

- **RECOMMENDATION:** You should write down your unique tenant suffix, mentioned as YOURTENANT in this lab and provided by your training provider. After a while, you will have this name or number memorized as you move through the labs in this course. 

- **Use the new Microsoft 365 admin center**
Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center, make sure the slider in the upper right corner is set to **The new admin center**. If you can read **Try the new admin center**, select the slider and activate it.   
‎  
‎**IMPORTANT:** The instructions that are provided in the lab exercises for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

### Exercise 1: Prepare team roles and licenses
In the first exercise you will assign required administrative roles to users, check license assignments for the Teams license and then explore the Microsoft Teams admin center. To perform these tasks, you will use default tenant global admin and the Joni Sherman ([JoniS@YourTenant.onmicrosoft.com](mailto:JoniS@m365xzzzzzz.onmicrosoft.com)) account.

#### **Task 1 - Assign a Teams Admin Role to a user**  
In this task you will use the default global admin to sign in to the Microsoft 365 admin center and assign several Teams admin roles to different users. This task is crucial for later tasks and exercises as you will perform most of the tasks in context of Joni Sherman’s account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to [**https://portal.office.com/**](https://portal.office.com/). 

3. When the Sign in window is displayed, sign in as **admin@YourTenant.onmicrosoft.com** using the O365 credentials provided to you. 

4. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **Yes.**

5. Close the password save dialog from the bottom with **Never**, not to save the default global admins credentials in your browser.

6. If a welcome screen is displayed, close it. If the Office 365 apps notification appear, also close it.

7. Select the **Admin** tile to go to the Microsoft 365 admin center, which opens in another tab.

8. If a welcome window is displayed, select **Get started** and close it.

9. Select **Users** from the left-side pane and **Active users** from below it.

10. In the Active users list, select **Joni Sherman**, to open the right-side pane.

11. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

12. When the **Manage roles** pane opens, select **Admin center access** and scroll down to select **Teams admin**.

13. Select **Save changes** to apply the role. When **Admin roles updated** is displayed, select the arrow pointing to the left.

14. Close the window of Joni Sherman’s account with the **X** in the upper right to go back to the **Active users** list.

15. Search for **Allan Deyoung** in the list of users and select his name.

16. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

17. When the **Manage roles** pane opens, select **Admin center access** and scroll down to the end and select **Show all by category**. Then scroll further down and select the **Teams communication support engineer** role.

18. Select **Save changes** to apply the role. When **Admin roles updated** is displayed, select the arrow pointing to the left.

19. Close Allan’s profile window and leave the client open at the Microsoft 365 admin center. 

You have now successfully assigned the Teams Service administrator role to Joni Sherman and the Teams communications support engineer to Allan Deyoung. Proceed to the next task.
 

#### **Task 2 – Check license assignment of your users**  

In this task, you will check the license assignment of all users participating in the pilot. You will continue where you left off in the last task, signed in as the MOD Administrator on Client 01, with an open browser window in the Microsoft 365 admin center. At the end of the task you will confirm that all pilot users are licensed correctly.
 
1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. You should still be signed in to the **Microsoft 365 admin center** as the **MOD Administrator**.

3. If you are not already on the **Active users** page, select **Users** from the left side pane and **Active users** below it.

4. In the Active users list , select **Alex Wilber** to open the right-side pane.

5. From the now visible tabs, select **Licenses and Apps**.

6. Check if the dropdown menu below **Select location** is set to **United States.** Change it to **Canada**. Then select **Save changes** at the end of the window and continue with the next step.

7. Below **Licenses**, verify that **Enterprise Mobility + Security E5** and **Office 365 E5** are both selected with a checkmark.

8. Select the dropdown arrow right beside **Apps** to open the view for the single licenses.

9. Scroll down the list of all apps to **Microsoft Teams** with **Office 365 E5**  listed below it and validate this entry has a checkmark left of it. This indicates that the user has a valid Teams license from the Office 365 E5 subscription assigned.

10. Close the window with the **X**, below the circle with the MA, which stands for the currently signed in user **MOD Administrator**.

11. Repeat the steps 3 to 9 for the users **Joni Sherman**, **Lynne Robbins**, **Allan Deyoung** and **Megan Bowen**, but skip step 6 and do not change their location.

12. After checking the licenses of all users, leave the browser open with the Microsoft 365 admin center.

You have successfully validated, that all users participating in the pilot own Teams licenses and they are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task.

#### **Task 3 - Explore Teams Admin center**  

You need to test access and review the available settings for administering Teams in the Teams admin center. As an administrator for teams, it's important to get to understand the different settings and policies available in the Microsoft Teams Admin Center. You will sign in with Joni Sherman’s account for this task, that you assigned the Teams Service Administrator role in the first task.


1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

	**Note**: You should still be signed in to Microsoft 365 as **MOD Administrator**. You will sign out this user and sign in with Joni Sherman’s account, to perform this task.

2. In the browser window, select the circle with **MA** in the upper right corner, open the side pane and select **Sign out**.

3. Close your browser window and re-open **Microsoft Edge** again and navigate to [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) to open the Teams admin center.

4. When the **Pick an account** window is displayed, select **Use another account**. Sign in as **JoniS@YourTenant.onmicrosoft.com** using the O365 Credentials provided to you.

5. The Microsoft Teams admin center **Dashboard** is displayed. If the icons from the left-side pane are minimized, hover over them to display the names of the different menus.

6. Hover over the first symbol below the house in the left-side pane, which is named **Teams.** That opens another menu with Manage teams and Teams policies.

7. Select **Manage Teams**. In the middle of the screen, the teams of your organization are displayed. Note that **No teams are available in this organization** is displayed because you have not created any teams. You can still select policies without an existing team. Select **Teams policies** in the left-side pane. 

8. The Teams policies dashboard and a single policy named Global (Org-wide default) is displayed. Select the **Global (Org-wide default)** policy and review the configured default global settings. Do not make any changes and select **Cancel**. 

9. Repeat the last steps for the other menus on the left-side pane as you wish and explore the different default policies and settings. Do not make any changes and just explore the UI to understand the structure and options the Teams admin center provides.

10. When you are finished reviewing all settings from the Teams admin center, close the browser window and leave the client open as it is.

You have successfully explored several available menus from the Teams admin center, for managing teams and configuring policies in your tenant. You have finished the first exercise and you can continue with the next one.

### Exercise 2: Explore PowerShell cmdlets for teams

In this exercise you will install the Teams and Skype for Business Online PowerShell modules, required to manage teams, policy packages, telephony and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center also in the PowerShell with the two mentioned modules, you can script for automation and even access several settings not available in the GUI.
 
#### **Task 1 - Install Teams PowerShell module**
Before you can connect to Teams from your tenant and perform any actions, you need to install the Teams PowerShell module. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system and don’t need to download any executables via the browser.

**Note:** The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks when done on servers.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. . On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell (Admin)**.

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

9. Wait till the installation has completed and returned to the command line. Close the elevated PowerShell window and continue to the next task.

You have now successfully installed the latest available Microsoft Teams PowerShell module from the PSGallery repository. Continue with the next task.

#### **Task 2 - Explore Teams PowerShell cmdlets**  

In this task, you will connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell.**

3. To connect to Microsoft Teams in your tenant, enter the following cmdlet in the PowerShell window and press **Enter**:

	```powershell
	Connect-MicrosoftTeams
	```

4. A **Sign in** dialog box will open. Sign in as **JoniS@YourTenant.onmicrosoft.com** using the O365 Credentials provided to you.

5. To confirm the MicrosoftTeams module is loaded, enter the following cmdlet and press **Enter**:

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

8. When you are finished with exploring the Microsoft Teams PowerShell cmdlets, close the PowerShell window and continue to the next task.


#### **Task 3 – Install Skype for Business PowerShell cmdlet**

Since the integration of Skype for Business into Microsoft Teams is not yet completed, it is necessary to know that some configurations must be made in the Skype for Business PowerShell, such as configuring telephony features and policies. Because the Skype for Business Online PowerShell module is not available from an official repository, you need to download the executable and install it manually.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to [**https://www.microsoft.com/en-us/download/details.aspx?id=39366**](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

3. In the Microsoft Download Center, scroll down below **Skype for Business Online, Windows PowerShell Module** and select **Download** in the grey box.

4. Select **Run** in the download bar to download and start the installation of the executable immediately.

5. The installation window may open in the background. Select it from the task bar, select the **I agree the license terms and conditions** checkbox and then select **Install.** 

6. Select **Yes** in the **User Account Control** dialog to confirm the installation process.

7. After the installation is done, select **Close** to finish the setup process and close the browser window.
 

You have successfully installed the Skype for Business Online PowerShell module. Continue with the next task.
 

#### **Task 4 – Explore Skype for Business PowerShell cmdlet**

In this task, you will connect and explore the available cmdlets from the Skype for Business Online PowerShell module for administrating the policy and telephony settings in your tenant.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell**.

	**Note**: Because the execution policy is already set to unrestricted, you don’t need to change it again.

3. To load the Skype for Business Online PowerShell module that was just installed, enter the following cmdlet and press **Enter**:

	```powershell
	Import-Module SkypeOnlineConnector
	```

4. To open a new Session with your tenant, enter in the following cmdlet in the PowerShell window and press **Enter**.

	```powershell
	$Session = New-CsOnlineSession
	```

5. When prompted to enter the user principal name, enter **JoniS@YourTenant.onmicrosoft.com** and press **Enter**.

6. In the **Enter password** dialog box, enter the **password** of **Joni Sherman’s** O365 Credentials provided to you and then select **Sign in**.

7. To load and import the session just established, enter the following cmdlet and press **Enter**:

	```powershell
	Import-PSSession $Session
	```

8. When all cmdlets and functions have been loaded, a list will be displayed. Write down the characters in **Name** column (for example, **tmp_f1kjmla4.h1v**) or copy them to your clipboard. You will need this information in the next step.

9. To display all available cmdlets from the PowerShell module, enter the following cmdlet replacing <Name> with the text from the previous step and press **Enter**: 

	```powershell
	Get-Command -Module <Name>
	```

	For example: **Get-Command -Module tmp_f1kjmla4.h1v**

10. Several cmdlets available to configure your Teams settings and policies are displayed. Most cmdlets have names that imply their function. Use the Get-Help cmdlet to explore the available cmdlets. For example, to get more information about existing messaging policies in your tenant, enter the following cmdlet and press **Enter**.

	```powershell
	Get-Help Get-CsTeamsMessagingPolicy
	```

11. After you have explored all interesting settings, close the remote PowerShell session by entering the following cmdlet and pressing **Enter**.

	```powershell
	Remove-PSSession $Session
	```

12. Close the PowerShell window. 

You have now successfully connected to your Teams tenant with the Skype for Business Online PowerShell module. Most settings can also be configured via the Microsoft Teams Admin center. However, working as an administrator also requires the automation of such processes. This can be done with the help of scripts to facilitate automation. Continue to the next exercise.


### Exercise 3: Create groups and teams

In this exercise you will create some resources required in later tasks. These include an Office 365 group creating from Microsoft 365 admin center and two teams creating from Desktop client and web client. 

#### **Task 1 - Create Office 365 Groups**  

In your role as Joni Sherman, you do not have the necessary permissions to access the Microsoft 365 admin center and to create resources. Therefore you need to sign in as the MOD Administrator to create the Office 365 Group. You will create the Office 365 group named "IT-Department" and then add the pilot members serving as a basis for your future teams and licensing. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.microsoft.com](https://admin.microsoft.com/) to access the **Microsoft 365 admin center**. 

3. When the **Pick an account** window appears, sign in with [admin@YourTenant.onmicrosoft.com](mailto:admin@m365xzzzzzz.onmicrosoft.com) using the O365 Credentials provided to you.

4. In the Microsoft 365 admin center, select **Groups** from the left-side pane and select **Groups** below.

5. Select **Add a group** in the **Groups** window to open the **New Group** pane.

6. Select as group type **Office 365 (recommended)** and select **Next**.

7. Enter the following information to the text fields:

	- Name: **IT-Department**
	- Description: **All staff of the IT-Department** 

8. Select **Next**

9. As group email address type in IT-Department@YourTenant.onmicrosoft.com, set the privacy to **Private – Only members can see group content** and select **Next.**

10. In the Owners field type in the Name of **Joni Sherman** and select her from the **Users** list and select **Next**. Then select **Create group.**

11. When the **New group created** information appears, select **Close**.

12. Wait a moment and select **Refresh** until the group is visible.

13. Select the **IT-Department** group to open the right-side pane.

14. On the **Members** tab, select **View all and manage members**. 

15. In the new window, select **+ Add members** from the top and select the checkbox before the following users: **Alex Wilber, Allan Deyoung, Lynne Robbins** and **Megan Bowen**.

16. Select **Save,** then **Close** two times and close the IT-Department pane with the **X**.

The new Office 365 Group with the names “IT-Department” was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a new team by using the desktop client** 

To test the self-service capabilities of Teams, in this task, Megan Bowen will sign in to the Teams Desktop client, create a new team with the name “Teams Rollout” and add all members participating in the Teams evaluation project.


1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the task bar to start the Teams Desktop client.

3. When prompted to **Enter your work, school or Microsoft account**. Sign in as MeganB@YourTenant.onmicrosoft.com using the O365 Credentials provided to you.

4. The Microsoft Teams Desktop client will start. If a **Bring your team together** window appears, or **Get the Teams mobile app**, or another message, close them with the **X** or **Try it now**.

5. In the left-hand navigation pane, select **Teams** then select **Create team** in the middle of the window.

6. In the **Create your team** window, select **Build a team from scratch**, then select **Public**. Enter the team name **Teams Rollout** and select **Create**.

7. Enter the names of the desired team members: **Alex Wilber**, **Allan Deyoung, Joni Sherman** and **Lynne Robbins**.

8. Select **Add** to add them to the team.

9. After adding the members to the Teams Rollout team, verify that all users have been added correctly and change the status of **Joni Sherman** from **Member** to **Owner** with the dropdown menu.

10. Select **Close.**

You have successfully created a new team with the Teams Desktop client, added the project team members and you have made Joni Sherman a second owner of the team. Close the Teams client and continue with the next task.

#### **Task 3 - Create a new team by using the web client**

In this task, Lynne Robbins will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name “Sales”, she will also add Megan Bowen as a member.


1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge** from the task bar, maximize the window and navigate to [https://teams.microsoft.com](https://teams.microsoft.com/) to access the **Microsoft Teams web client**. 

3. When the Sign in window is displayed, sign in as LynneR@YourTenant.onmicrosoft.com using the O365 credentials provided to you. 

4. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **Yes.**

5. A landing page **Download the Teams desktop app and stay better connected** message is displayed. Select **Use the web app instead** below this message.

6. Another welcome message is displayed. Close all messages with **Try it now** or the **X**.

7. Select **Teams** from the left-side pane if you are not already in the **Teams** overview.

8. Select **Join or create a team** from the lower end of the teams list.

9. Select **Create team** from the middle of the window.

10. In the **Create your team** window, select **Build a team from scratch**, then select **Private**. Insert the team name **Sales** and select **Create**.

11. In the Add members to Sales dialog, enter **Megan Bowen** to add her as a team member.

12. Select **Add** to add her to the team.

13. After adding the members to the Sales team, verify that Megan Bowen has been added correctly.

14. Select **Close.**

15. The newly created team is displayed in the list of your teams.


You have successfully created a new team with the Teams web client. This is the end of lab 1. You can close all browser windows and proceed to the next lab.
