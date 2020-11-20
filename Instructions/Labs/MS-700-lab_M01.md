---
lab:
    title: 'Lab 01: Manage roles and create teams'
    module: 'Module 1: Microsoft Teams in Microsoft 365'
---

# **Lab 01: Manage roles and create teams**

# **Student lab manual**

## **Microsoft 365 user interface**

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual.

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to conduct a pilot project to test the implementation of Microsoft Teams against Contoso Ltd. business requirements.

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman (JoniS@_&lt;YourTenant&gt;_.OnMicrosoft.com) **Group coordinator / Teams admin**

- Alex Wilber (AlexW@_&lt;YourTenant&gt;_.OnMicrosoft.com) **Regular pilot user from Canada**

- Lynne Robbins (LynneR@_&lt;YourTenant&gt;_.OnMicrosoft.com) **Regular pilot user**

- Allan Deyoung (AllanD@_&lt;YourTenant&gt;_.OnMicrosoft.com) **Teams communication support engineer**

- Megan Bowen (MeganB@_&lt;YourTenant&gt;_.OnMicrosoft.com) **Regular employee**

## **Objectives**

After you complete this lab, you will be able to:

- Assign Teams admin roles to users

- Check license assignment for users

- Understand the Teams admin center and its menus

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

- The username of the Global Administrator (MOD Administrator) is (admin&lt;YourTenant&gt;.onmicrosoft.com).

- **&lt;YourTenant&gt;.onmicrosoft.com** - This is the domain associated with the Microsoft 365 tenant that was provided by the lab hosting provider. The first part of this domain name (&lt;YourTenant&gt;) is the unique tenant ID provided by the lab hosting provider. The &lt;YourTenant&gt; portion of the tenant ID, which is the tenant suffix ID, will be unique for each student.

  **IMPORTANT:** This is critical because throughout this lab, you will be asked to enter the **&lt;YourTenant&gt;.onmicrosoft.com** domain name when signing into apps with a given username (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com). When doing so, you must enter the unique tenant suffix ID that is assigned to your tenant ID in place of the **&lt;YourTenant&gt;**.

  For example, if your Tenant Email is **admin@contosolab.onmicrosoft.com**, the unique tenant suffix ID (&lt;YourTenant&gt;) is **contosolab**. When signing in as Joni when entering this domain, you would replace &lt;YourTenant&gt; with contosolab (for example, JoniS@contosolab.onmicrosoft.com).

   **RECOMMENDATION:** You should write down your unique tenant suffix, mentioned as &lt;YourTenant&gt; in this lab and provided by your training provider. After a while, you will have this name or number memorized as you move through the labs in this course.

- **Use the new Microsoft 365 admin center** 

  Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center, make sure the slider in the upper right corner is set to **The new admin center**. If you can read **Try the new admin center**, select the slider and activate it.  
‎‎  
  ‎‎**IMPORTANT:** The instructions that are provided in the lab exercises for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

### **Exercise 1: Prepare team roles and licenses**

In the first exercise, you will assign required administrative roles to users, check license assignments for the Teams license, and then explore the Microsoft Teams admin center. To perform these tasks, you will use default tenant global admin and the Joni Sherman’s account (JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com).

#### **Task 1 - Assign Teams Admin Roles to users**

In this task, you will use the default global admin to login to the Microsoft 365 admin center and assign several teams admin roles to different users. This task is crucial for the following tasks and exercises because you will perform most of the tasks in context of Joni Sherman’s account.

1. Sign in to the **Microsoft 365 admin center** ([**https://admin.microsoft.com**](https://admin.microsoft.com/)) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Assign the role of the **Teams service admin** to **Joni Sherman**.

3. Assign the role of the **Teams communication support engineer** to **Allan Deyoung**.

4. Leave the client open at the **Microsoft 365 admin center**.

You have now successfully assigned the Teams admin role to Joni Sherman and the Teams communications support engineer to Allan Deyoung. Proceed to the next task.

#### **Task 2 - Check license assignment of your users**

In this task, you will check the license assignment of all users participating in the pilot. You will continue where you left off in the last task, signed in as the MOD Administrator on Client 1 VM, with an open browser window in the Microsoft 365 admin center. At the end of the task, you will confirm that all pilot users are licensed correctly and change Alex’s location to Canada as preparation for a later task.

1. Navigate to the **Microsoft 365 admin center** ([**https://admin.microsoft.com**](https://admin.microsoft.com/)) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Change the **Usage Location** of **Alex Wilber** to **Canada**.

3. Check, that all pilot users have the **Enterprise Mobility + Security E5** and **Office 365 E5** licenses assigned.

4. Close the **Microsoft 365 admin center**.

You have successfully validated, that all users participating in the pilot own Teams licenses and they are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task.

#### **Task 3 - Explore Teams Admin center**

You need to access and review the available settings for administering Teams in the Teams admin center. As an administrator for teams, it’s important to get to understand the different settings and policies available in the Microsoft Teams Admin Center. You will login with Joni Sherman’s account for this task, that you assigned the Teams Service Administrator role in the first task.

1. Sign in to the **Teams admin center** [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to the Teams admin page.

3. Navigate through the policies and settings menus.

4. Leave the **Teams admin center** opened.

You have successfully explored several available menus from the Teams admin center in managing teams and configuring policies in your tenant. You have finished the first exercise and you can continue to the next one.

### **Exercise 2: Explore PowerShell cmdlets for Teams**

In this exercise you will install the Teams and Skype for Business Online PowerShell modules, required to manage teams, policy packages, telephony, and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center also in the PowerShell with the two mentioned modules. You can script for automation and even access several settings not available in the GUI.

#### **Task 1 - Install Teams PowerShell module**

Before you can connect to Teams from your tenant and perform any actions, you need to install the Teams PowerShell module. You can install the Teams PowerShell module from the available repositories preconfigured in your Windows 10 operating system. You don’t need to download any executables via the browser.

1. Open an elevated **Windows PowerShell (Admin)** window.

2. Change the current execution policy with cmdlet:

   ```powershell
   Set-ExecutionPolicy Unrestricted
   ```
3. Install the mainstream Teams PowerShell module:
   ```powershell
   Install-Module -Name MicrosoftTeams
   ```
4. Close the elevated PowerShell window.

You have now successfully installed the latest available Microsoft Teams PowerShell module from the PSGallery repository. Continue with the next task.
   
#### **Task 2 - Explore Teams PowerShell cmdlets**

In this task, you will connect with the Teams PowerShell module to your tenant and explore the available cmdlets and functions to manage your tenant.

1. Open a regular **Windows PowerShell** window.

2. Connect to Teams in your tenant using cmdlet:

   ```powershell
   Connect-MicrosoftTeams
   ```
3. Check the installed modules using cmdlet:

   ```powershell
   Get-Module
   ```
4. Investigate the available cmdlets:

   ```powershell
   Get-Command -Module MicrosoftTeams
   ```
5. Use the help cmdlet for more information about the available cmdlets:

   ```powershell
   Get-Help <cmdlet>
   ```
6. Close the PowerShell window.

When you are finished with exploring the Microsoft Teams PowerShell cmdlets, close the PowerShell window and continue to the next task.
   
#### **Task 3 - Import former Skype for Business Online cmdlets**

Because the Skype for Business Online cmdlets have been integrated into the Teams PowerShell, a separate module is no longer required, but the cmdlets still need to be loaded into the Teams PowerShell session. In this task you will connect to your voice and policy endpoint in your tenant.

1. Open a regular **Windows PowerShell** window.

2. Establish a session to the SfBPowerShell:

   ```powershell
   $Session = New-CsOnlineSession
   ```
3. Import the new session:

   ```powershell
   Import-PSSession $Session
   ```
4. Review the modules from the CsOnlineSession module:

   ```powershell
   Get-Command -Module (Get-Module -Name tmp*)
   ```
5. Close the PowerShell window.

You have successfully established a connection to the CsOnline endpoint in your tenant, to manage voice and policy settings that formerly required the independent Skype for Business Online module.

### **Exercise 3: Create groups and teams**

In this exercise, you will create some resources required in later tasks. These include creating a Microsoft 365 Group from the Microsoft 365 admin center and creating a team in the Desktop client and then the web client.

#### **Task 1 - Create a Microsoft 365 Group**

In real world scenarios, the Microsoft 365 Groups would already exist and your task as Teams service admin would only be to enable their Teams functionality, but for this lab you need to create them manually.

You will create the new Microsoft 365 Group named "IT-Department" and then add the pilot members serving as a basis for your future teams and licensing.

1. Sign in to the **Microsoft 365 admin center** ([**https://admin.microsoft.com**](https://admin.microsoft.com/)) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create and configure a new Microsoft 365 group with the following settings:

	- Name: **IT-Department**

	- Description: **All staff of the IT-Department**

	- Owners: **Joni Sherman**

	- Group email address: **IT-Department**@&lt;YourTenant&gt;.onmicrosoft.com

	- Privacy: **Private – Only members can see group content**

	- Create a team for this group: **Clear the checkbox**

	- Members: **Alex Wilber, Allan Deyoung, Lynne Robbins** and **Megan Bowen**

3. Close the **Microsoft 365 admin center**.

The new Microsoft 365 Group with the name "IT-Department" was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a new team by using the desktop client**

To test the self-service capabilities of Teams, in this task, Megan Bowen will sign in to the Teams Desktop client, create a new team with the name "Teams Rollout" and add all members participating in the Teams evaluation project.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Connect to a client and sign in to the Teams Desktop client using **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

3. Create a new team with the following settings:

	- Type: **Build a team from scratch**

	- Privacy: **Public**

	- Name: **Teams Rollout**

	- Owners: **Joni Sherman** and **Megan Bowen**

	- Members: **Alex Wilber**, **Allan Deyoung** and **Lynne Robbins**

4. Close the Teams Desktop client.

You have successfully created a new team with the Teams Desktop client, added the project team members and you have made Joni Sherman a second owner of the team. Close the Teams client and continue with the next task.

#### **Task 3 - Create a new team by using the web client**

In this task, Lynne Robbins will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name "Sales". She will also add Megan Bowen as a member.

1. Sign in to the Teams web client ([**https://teams.microsoft.com**](https://teams.microsoft.com/)) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new team with the following settings:

	- Type: **Build a team from scratch**

	- Privacy: **Private**

	- Name: **Sales**

	- Owners: **Lynne Robbins**

	- Members: **Megan Bowen**

3. Close the Teams web client.

You have successfully created a new team with the Teams web client. This is the end of lab 1. You can close all browser windows and proceed to the next lab.

END OF LAB
