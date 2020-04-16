--- 
lab: 
    title: 'Lab: Manage roles and create teams'
    module: 'Module 01: Microsoft Teams in Microsoft 365'
---

# Lab 01: Manage roles and create teams
# Student lab manual
## Microsoft 365 user interface 

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual. 

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## Lab Scenario

In the labs of this course you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to conduct a pilot project to test the implementation of Microsoft Teams against Contoso Ltd. business requirements. 

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman ([](mailto:)[JoniS@YourTenant.onmicrosoft.com](mailto:JoniS@m365xzzzzzz.onmicrosoft.com)) **Group coordinator / Teams admin**

- Alex Wilber ([AlexW@YourTenant.onmicrosoft.com](mailto:AlexW@m365xzzzzzz.onmicrosoft.com)) **Regular pilot user from Canada**

- Lynne Robbins ([LynneR@YourTenant.onmicrosoft.com](mailto:LynneR@m365xzzzzzz.onmicrosoft.com)) **Regular pilot user**

- Allan Deyoung ([AllanD@YourTenant.onmicrosoft.com](mailto:AllanD@m365xzzzzzz.onmicrosoft.com)) **Teams communication support engineer**

- Megan Bowen ([MeganB@YourTenant.OnMicrosoft.com](mailto:MeganB@m365xzzzzzz.onmicrosoft.com)) **Regular employee**

 

## Objectives

After you complete this lab, you will be able to:

- Assign Teams admin roles to users
- Check license assignment for users
- Understand the Teams admin center and its menus
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


#### 1. Sign in to the lab virtual machines

The labs in this course will use two virtual machines:

- Client 1 VM : a stand-alone Windows 10 client virtual machine.
- Client 2 VM : a stand-alone Windows 10 client virtual machine.

**Note:** Lab virtual machine sign in instructions will be provided to you by your instructor. 

**Important:** A local administrator account has been created on the client VMs. These will be the accounts that you use to log into each VM. All MS700 lab exercises will use the admin account for login.  

Since the MS700 lab scenario involves a cloud-only deployment, you will not be logging into an on-premises domain, since no such domain exists. Following your login, the desktop will indicate that you are logged in as either the local user **CLIENT01\Admin** or **CLIENT02\admin**, depending on which machine you are on.

 
#### 2. Review installed applications

Once you signed in to the VM, observe the start menu, and verify following applications have been installed:

- Microsoft Teams

#### 3. Review Microsoft 365 tenant

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

In the first exercise you will assign required administrative roles to users, check license assignments for the Teams license and explore the Microsoft Teams admin center. To perform the tasks, you need the default tenant global admin and the account of Joni Sherman (JoniS@YourTenant.onmicrosoft.com).


#### Task 1 - Assign a Teams Admin Role to a user  

In this task you will use the default global admin to login to the Microsoft 365 admin center and assign several teams admin roles to different users. This task is crucial for the following tasks and exercises, because you will perform most of the tasks in context of Joni Sherman’s account.


1. Sign in to the M365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com/)) using admin@YourTenant.onmicrosoft.com.

2. Assign the role of the **Teams admin** to **Joni Sherman**.

3. Assign the role of the **Teams communication support engineer** to **Allan Deyoung**.

4. Leave the client open at the Microsoft 365 admin center.

 
You have now successfully assigned the Teams admin role to Joni Sherman and the Teams communications support engineer to Allan Deyoung. Proceed to the next task.
 

#### Task 2 - Assign licenses to several users  

In this task, you will check the license assignment of all users participating in the pilot. You will continue where you left off in the last task, logged in as the MOD Administrator on Client 01, with an open browser window in the Microsoft 365 admin center. At the end of the task you can confirm, that all pilot users are licensed correctly.

1. Navigate to the M365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com/)).

2. Change the **Usage Location** of **Alex Wilber** to **Canada**.

3. Check, that all pilot users have the **Enterprise Mobility + Security E5** and **Office 365 E5** licenses assigned.

4. Close the Microsoft 365 admin center.


You have successfully validated, that all users participating in the pilot own Teams licenses and they are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task.

#### Task 3 - Explore Teams Admin center  

You need to access and review the available settings for administering Teams in the Teams admin center. As an administrator for teams, it's important to get to understand the different settings and policies available in the Microsoft Teams Admin Center. You will login with Joni Sherman’s account for this task, that you assigned the Teams Service Administrator role in the first task.

 

1. Sign in to the Teams admin center (https://admin.teams.microsoft.com) using JoniS@YourTenant.onmicrosoft.com.

2. Navigate to the teams management page.

3. Navigate through the policies and settings menus.

4. Close the Teams admin center.


You have successfully explored several available menus from the Teams admin center, for managing teams and configuring policies in your tenant. You have finished the first exercise and you can continue to the next one.
 

### Exercise 2: Explore PowerShell cmdlets for teams

In this exercise you will install the Teams and Skype for Business Online PowerShell modules, required to manage teams, policy packages, telephony and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center also in the PowerShell with the two mentioned modules, you can script for automation and even access several settings not available in the GUI.


#### Task 1 - Install Teams PowerShell module

Before you can connect to Teams from your tenant and perform any actions, you need to install the Teams PowerShell module. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system and don’t need to download any executables via the browser.

 
1. Open an elevated PowerShell (Admin) window.

2. Change the current execution policy with cmdlet: ```Set-ExecutionPolicy Unrestricted```

3. Install the mainstream Teams PowerShell module: ```Install-Module -Name MicrosoftTeams```

4. Close the elevated PowerShell (Admin) window.

 
You have now successfully installed the latest available Microsoft Teams PowerShell module from the PSGallery repository. Continue with the next task.


#### Task 2 - Explore Teams PowerShell cmdlets  

In this task, you will connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant.


1. Open a regular PowerShell window.

2. Connect to Teams in your tenant using cmdlet: ```Connect-MicrosoftTeams```

3. Check the installed modules using cmdlet: ```Get-Module```

4. Investigate the available cmdlets: ```Get-Command -Module MicrosoftTeams```

5. Use the help cmdlet for more information about the available cmdlets: ```Get-Help <cmdlet>```

6. Close the PowerShell window.

 

When you are finished with exploring the Microsoft Teams PowerShell cmdlets, close the PowerShell window and continue to the next task.

 

#### Task 3 – Install Skype for Business PowerShell cmdlet

Since the integration of Skype for Business into Microsoft Teams is not yet completed, it is necessary to know that some configurations must be made in the Skype for Business PowerShell, such as configuring telephony features and policies. Because the Skype for Business Online PowerShell module is not available from an official repository, you need to download the executable and install it manually.
 
1. Download the Skype for Business PowerShell module from the following link: [https://www.microsoft.com/en-us/download/details.aspx?id=39366](https://www.microsoft.com/en-us/download/details.aspx?id=39366).

2. Install the Skype for Business PowerShell module from the executable.
 

#### Task 4 – Explore Skype for Business PowerShell cmdlet

In this task, you will connect and explore the available cmdlets from the Skype for Business Online PowerShell module for administrating the policy and telephony settings in your tenant.

1. Open a regular PowerShell window.

2. Import the Skype for Business Online PowerShell module: ```Import-Module SkypeOnlineConnector```

3. Connect a new session to your tenant: ```$Session = New-CsOnlineSession```

4. Import the newly created session: ```Import-PSSession $Session```

5. Check the available modules: ```Get-Module```

6. Investigate the available cmdlets: ```Get-Command -Module <name>```

7. Use the help cmdlet for more information about the available cmdlets: ```Get-Help <cmdlet>```

8. Exit the remote PowerShell session: ```Remove-PSSession $Session```

9. Close the PowerShell window.

You have now successfully connected to your Teams tenant with the Skype for Business Online PowerShell module. Most settings can also be configured via the Microsoft Teams Admin center. However, working as an administrator also requires the automation of such processes. This can be done with the help of scripts to facilitate automation. Continue to the next exercise.

### Exercise 3: Create groups and teams

In this exercise you will create some resources required in later tasks. These include an Office 365 group creating from Microsoft 365 admin center and two teams creating from Desktop client and web client. 

#### Task 1 - Create Office 365 Groups  

In your role as Joni Sherman, you do not have the necessary permissions to access the Microsoft 365 admin center and to create resources. Therefore you need to sign in as the MOD Administrator to create the Office 365 Group. You will create the Office 365 group named "IT-Department" and then add the pilot members serving as a basis for your future teams and licensing. 

1. Sign in to the M365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com/)) using admin@YourTenant.onmicrosoft.com.

2. Create a new Office 365 group with the following settings:

	- Name: **IT-Department**

	- Description: **All staff of the IT-Department** 

	- Group email address: IT-Department@YourTenant.onmicrosoft.com

	- Privacy: **Private – Only members can see group content**

	- Owners: **Joni Sherman**

	- Members: **Alex Wilber, Allan Deyoung, Lynne Robbins** and **Megan Bowen**

3. Close the Microsoft 365 admin center.

The new Office 365 Group with the names “IT-Department” was successfully created. Close the browser window and continue to the next task.

#### Task 2 - Create a new team by using the desktop client 

To test the self-service capabilities of Teams, in this task, Megan Bowen will sign in to the Teams Desktop client, create a new team with the name “Teams Rollout” and add all members participating in the Teams evaluation project.

1. Connect to a client and sign in to the Teams Desktop client using MeganB@YourTenant.onmicrosoft.com.

2. Create a new team with the following settings:

	- Name: **Teams Rollout**

	- Type: **Build a team from scratch**

	- Privacy: **Public**

	- Owners: **Joni Sherman** and **Megan Bowen**

	- Members: **Alex Wilber**, **Allan Deyoung** and **Lynne Robbins**

3. Close the Teams Desktop client.
 
You have successfully created a new team with the Teams Desktop client, added the project team members and you have made Joni Sherman a second owner of the team. Close the Teams client and continue with the next task.

#### Task 3 - Create a new team by using the web client

In this task, Lynne Robbins will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name “Sales”, she will also add Megan Bowen as a member.

 

1. Sign in to the Teams web client ([https://teams.microsoft.com](https://teams.microsoft.com/)) using LynneR@YourTenant.onmicrosoft.com.

2. Create a new team with the following settings:

	- Name: **Sales**
	- Type: **Build a team from scratch**
	- Privacy: **Private**
	- Owners: **Lynne Robbins**
	- Members: **Megan Bowen**

3. Close the Teams web client.

 

You have successfully created a new team with the Teams web client. This is the end of lab 1. You can close all browser windows and proceed to the next lab.

 

END OF LAB
