--- 
lab: 
    title: 'Lab: Manage teams'
    module: 'Module 04: Deploy and manage teams' 
---

# Lab 04: Manage teams 
# Student lab manual
## Lab Scenario  

In the labs of this course, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership and recovering deleted teams. In the second half of this lab, you will configure the guest access for your tenant and review access for both, internal and external users.

## Objectives

After you complete this lab, you will be able to:

- Create a Team from a Microsoft 365 Group
- Create a Team by using PowerShell
- Create a Team with dynamic membership
- Delete and recover Teams
- Configure guest access in Azure and Teams
- Review Access to a resource

## Lab Setup  

- **Estimated Time:** 90 minutes.

## Instructions



### Exercise 1: Manage team resources


#### Task 1 - Create a Team from the Microsoft 365 Group 

As part of your pilot project for Contoso, you need to modify the **"IT-Department"** Microsoft 365 Group, created in an earlier task of this lab, and add Teams features to it.

1. Sign in to the Teams Desktop client using **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com**.

2. Create a new team with the following settings:

	- Name: **IT-Department**

	- Type: **Create from... An existing Microsoft 365 group or team**

	- Owners: **Joni Sherman**

	- Members: **Lynne Robbins**, **Megan Bowen**, **Allan Deyoung** and **Alex Wilber**

3. Close the Teams Desktop client.

You have successfully created a new team with the Teams Desktop client, by using an existing Microsoft 365 Group. Leave the Teams client open and continue with the next task.



#### Task 2 - Create a new team by using PowerShell

In this task you will create via the Teams PowerShell a new team **"CA-Office"**. You will create the public channels **"Support"** and **"Recruiting"**. Additionally, you will create the private channel **"Administration"** via Teams PowerShell. 
 
1. Open an elevated PowerShell (Admin) window.

2. Check the Teams PowerShell module for the ability to create private channels:

	```powershell
	If ((Get-Command New-TeamChannel -ParameterName 'MembershipType' -ErrorAction Ignore) -eq $Null) {"Close PowerShell and install the Teams private preview module."} else {"Continue with the current module."}
	```

    If the output of the command is "**_Continue with the current module_**", skip steps 3-6 and continue with step 7. If the output of the command is "**_Close PowerShell and install the Teams private preview module._**", close the PowerShell window and continue with step 3.

3.  If you need to install the Teams private preview module, first open an elevated PowerShell (Admin) window and uninstall the current PowerShell module by running the following cmdlet:

	```powershell
	Uninstall-Module MicrosoftTeams
	```
		
     >**Note:** If the Uninstall-Module command fails, close the PowerShell window, open a new elevated PowerShell (Admin) window, and then repeat this step.

4. Add the official testing repository:

	```powershell
	Register-PSRepository -Name PSGalleryInt -SourceLocation https://www.poshtestgallery.com/ -InstallationPolicy Trusted 
	```

5. Install the Teams PowerShell private preview module from the testing repository:

	```powershell
	Install-Module MicrosoftTeams -Repository PSGalleryInt -AllowClobber -Force
	```

6. Verify that the Teams PowerShell module supports creating private channels:

	```powershell
	If ((Get-Command New-TeamChannel -ParameterName 'MembershipType' -ErrorAction Ignore) -eq $Null) {"Close PowerShell and install the Teams private preview module."} else {"Continue with the current module."}
	```

7. Connect to Teams in your tenant:

	```powershell
	Connect-MicrosoftTeams
	```

8. Create a new team with the following settings, using the ```New-Team``` cmdlet:

	- Displayname: **CA-Office**
	- MailNickName: **CA-Office**
	- Visibility: **Public**

9. Use the GroupId and add **Alex Wilbur** and **Allan Deyoung** as members to the team, using the ```Add-TeamUser``` cmdlet.

10. Use the GroupId and and create the regular channels **“Support”** and **“Recruiting”**, using the ```New-TeamChannel``` cmdlet.

11. Use the GroupId and and create the private channel **“Administration”**, using the ```New-TeamChannel``` cmdlet.

12. Close the PowerShell window. 

You have successfully created a team named **CA-Office** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.


#### Task 3 - Delete and recover teams 

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Sign in to the Teams Desktop client using JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com.

2. Delete the **IT-Department** team.

3. Sign in to the **Azure Portal** (https://portal.azure.com/) using JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com.

4. Navigate to **Azure Active Directory** and **Deleted groups**.

5. Restore the **IT-Department** team.

6. Check the Teams Desktop client for the recovered group.

You have successfully deleted and restored a via the Teams Desktop client and Azure Admin Portal. 


#### Task 4 - Create team with dynamic membership

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Sign in to the **Azure Portal** (https://portal.azure.com/) using admin@_&lt;YourTenant&gt;_.onmicrosoft.com.

2. Navigate to **Azure Active Directory** and **Groups**.

3. Switch **CA-Office** to a group with Dynamic membership, using the following expression:

	- **Property** accountEnabled
	- **Operator** Equals
	- **Value** true

4. Add a second expression:

	- **Property** usageLocation
	- **Operator** Equals
	- **Value** CA

5. Check the **Membership processing status** for members with the correct usage location.

6. Close the Azure Portal.

You have successfully converted a Microsoft 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation “Canada" is added automatically to the team. 



### Exercise 2: Manage sharing and access

In this exercise, you will test the guest access features in Office 365. To do so, you will configure guest access in Azure AD, add a new external guest user and revoke the guest access by using access reviews.


#### Task 1 - Configure guest access in Teams

In this task, you will configure the guest user access for Microsoft Teams in your tenant. 

1. Sign in to the Teams admin center (https://admin.teams.microsoft.com/) using admin@_&lt;YourTenant&gt;_.onmicrosoft.com.
2. Change the **Org-wide settings** and allow **Allow guest access in Teams**.
3. Close the Teams admin center.

You have now successfully activated guest user access in Teams for your tenant.


#### Task 2 - Configure guest access in the Azure AD (optional)

In this task, you will configure the guest user access in the Microsoft Azure Portal. You will change the default settings for inviting/creating guest users and then add your personal Outlook.com account as a guest user to your tenant.

**Note**: You need to have a personal outlook.com account for this and the following tasks. If you don’t have an account like this, open your web browser, go to https://outlook.com and create a new account.

1. Sign in to the **Azure Portal** (https://portal.azure.com) using admin@_&lt;YourTenant&gt;_.onmicrosoft.com.

2. Navigate to **Azure Active Directory** and **Users**.

3. Change the **External collaboration settings** and activate **Guests can invite**.

4. Create a new guest user with the following settings:

	- **Name:** *your full name*
	- **Email address:** *your Outlook.com email address*
	- **First name:** *your First name*
	- **Last name:** *your last name*
	- **Personal Message:** Hello Guest, here is the link to access to our Contoso test organization. Best regards, Contoso admin.
	- **Groups**: IT-Department

5. Sign in to the **Outlook Web Portal** (https://outlook.live.com/owa/) using your personal account.

6. Grant consent and explore the guest access. 

You have successfully changed the external collaboration settings, so guests can also invite new guests. Then you have added a personal outlook.com account as a guest to your tenant and as a member to the team “IT-Department”.


#### Task 3 - Review access to a resource with access reviews

As a part of your system administrator role, you need to review access to resources in your tenant on a regular basis. You can do that by using access reviews in Microsoft Teams. 

1. Sign in to the Azure Portal (https://portal.azure.com) using admin@_&lt;YourTenant&gt;_.onmicrosoft.com.

2. Navigate to **Azure Active Directory** and **Groups**.

3. Onboard to **Access reviews** and create a new access review with the following settings:

	- **Review name:** Guest access review
	- **Description:** Reviewing guest access
	- **StartDate:** your current date 
	- **Frequency:** One time
	- **EndDate:** your current date + 7 days into the future
	- **Scope:** Guest users only
	- **Group:** IT-Department
	- **Reviewers:** Group owners 

4. Navigate to **Outlook on the web** (https://outlook.office365.com) using JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com.

5. Review the access reviews mail and deny access for the guest user in the **IT-Department** team.

6. Close the Outlook on the web window.

You have successfully created a new access review and blocked a guest user in your tenant. This is the end of lab 4. You can close all browser windows and proceed to the next lab.


END OF LAB
