---
lab:
    title: 'Lab 02: Configure security and compliance for teams and content'
    module: 'Module 2: Implement Microsoft Teams Governance, Security and Compliance'
---

# **Lab 02: Configure Security and Compliance for teams and content**

# **Student lab manual**

## **Lab Scenario**

In the labs of this course you will assume the role of the System Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. Before starting the deployment, IT department is gathering business requirements about Teams governance as well as data security and compliance, including how the data shared in Teams is regulated according to the organization’s compliance requirements. After you complete the planning process, you will configure Microsoft 365 Groups governance, protect Teams from threats, and configure Teams to meet your organization compliance requirements.

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

Your organization has started the planning process for Microsoft 365 services adoption. You are assigned as a Teams admin role to plan Teams governance. Since Teams relies on Microsoft 365 groups, you need to plan governance procedures for Microsoft 365 groups, including creating, configuring and assigning sensitivity labels, creating Microsoft 365 groups expiration policies, configuring Microsoft 365 Group creation policy permissions, and configuring with testing Microsoft 365 Groups naming policies.

#### Task 1 – Activate sensitivity labels for Teams 

You need to evaluate governance for Microsoft 365 Groups before deploying them in your organizations. In this task, you will activate the sensitivity labels for Teams in Azure AD, for being able to assign labels in a following task.

1. Open a **Windows PowerShell** window.

2. Install the Azure AD Preview module:

   Install-Module AzureADPreview

3. Connect to Azure AD in your tenant as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com):

   Connect-AzureAD

4. Load the Azure AD unified group template:
   ```powershell
   $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
   ```
5. Check if a Azure AD setting is already existing and load it, if yes. If not, create a blank Azure AD setting object. Run the following cmdlet to populate the "$Setting" variable:
   ```powershell
   if (!($Setting=Get-AzureADDirectorySetting|Where {$_.TemplateId -eq $Template.Id})) {$Setting = $Template.CreateDirectorySetting()}
   ```
6. Enable the Microsoft Identity Protection (MIP) support:
   ```powershell
   $Setting["EnableMIPLabels"] = "True"
   ```
7. To verify the new configuration, run the following cmdlet:
   ```powershell
   $Setting.Values
   ```
8. As soon as the "Setting" variable attributes contain the desired values, write back the settings object to your directory. Use the following cmdlet, to create a new "Group.Unified" Azure AD configuration with the custom settings:

   ```powershell
   New-AzureADDirectorySetting -DirectorySetting $Setting
   ```
   **Note:** Since this is a new tenant, there’s no directory settings object in the tenant yet. You need to use ```New-AzureADDirectorySetting``` to create a directory settings object at the first time.

   If there’s an existing directory settings object, you will need to run the following cmdlet to update the directory setting in Azure Active Directory:
   
   ```powershell
   Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
   ```
9. Close the PowerShell window.

You have successfully changed your tenants Azure AD settings and activated sensitivity labels for Microsoft 365 Groups and Microsoft Teams.
   
#### Task 2 - Create sensitivity labels for Teams

After activating sensitivity labels for groups, you will now create three sensitivity labels. In this task, you will create three sensitivity labels "General," "Internal," and "Confidential." For each of them, you will create appropriate user and admin descriptions.

1. Sign in to the **Microsoft 365 compliance center** [**https://compliance.microsoft.com**](https://compliance.microsoft.com/) using the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Turn on now the ability to process content in Office online files that have encrypted sensitivity labels applied.

3. Create a new sensitivity label with the following settings:

    - **Name**: General

	- **Description for users**: General information without protection

	- **Description for admins**: General information without encryption, marking or sharing restriction settings activated

	- **Privacy:** None. Team and group members can set the privacy settings themselves

	- **External users access**: Select Let Microsoft 365 group owners add people outside the organization to the group

	- **Unmanaged devices:** Allow full access from desktop apps, mobile apps, and the web

4. Create the second new sensitivity label with the following settings:

	- **Name**: Internal

	- **Description for users**: Internal information with sharing protection

	- **Description for admins**: Internal information with moderate encryption, marking and sharing restriction settings activated

	- **Assign permissions now or let users decide**: Assign permissions now

	- **User access to content expires**: Never

	- **Allow offline access**: Always

	- **Assign permissions**: Add all users and groups in your organization

	- **Watermark text**: Internal use only

	- **Privacy:** None. Team and group members can set the privacy settings themselves

	- **External users access**: Leave the box unchecked

	- **Unmanaged devices:** Allow limited, web-only access

5. Create the third new sensitivity label with the following settings:

	- **Name**: Confidential

	- **Description for users**: Confidential information with all protection

	- **Description for admins**: Confidential information with all restrictive encryption, marking, and sharing settings activated

	- **Assign permissions now or let users decide**: Assign permissions now

	- **User access to content expires**: Never

	- **Allow offline access**: Never

	- **Assign permissions**: Add all users and groups in your organization

	- **Choose permissions**: Reviewer

	- **Watermark text**: Confidential

	- **Privacy:** Private. Only team owners and members can access the group or team, and only owners can add members

	- **External users access**: Leave the box unchecked

	- **Unmanaged devices:** Allow limited, web-only access

6. Publish the sensitivity labels with the following settings:

	- **Name**: All company sensitivity labels

	- **Description**: Default sensitivity labels for all users in the company

	- Publish to all users and groups

	- **Default to documents and email**: General

	- **Default to groups and sites**: General

7. Close the **Microsoft 365 compliance center**

In this task, you have created and published three new sensitivity labels available for all users, which can be assigned to new and existing Teams.

#### Task 3 - Assign sensitivity labels to Teams

Once the sensitivity labels are created and published, users can now assign them to teams. Furthermore, users can modify assigned labels if needed. In this task, you will assign the "Internal" label to the "Teams Rollout" team.

Note: It can take several minutes till the newly created sensitivity labels are available to users.

1. Connect to a client and sign in to the Teams Desktop client using **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

2. Assign the **Internal** sensitivity label to the **Teams Rollout** team.

3. Close the Teams Desktop client.

You have successfully applied a sensitivity labels to an existing team. The configured settings of the Internal label are now applied to the Teams Rollout team. Continue with the next task.

#### Task 4 - Create and assign an expiration policy

Based on the organization requirement, unneeded groups should be deleted automatically after 90 days. To evaluate the expiration feature for teams, you will configure a group expiration policy that will expire the **Teams Rollout** group after 90 days.

1. Sign in to the **Azure Portal** [**https://portal.azure.com**](https://portal.azure.com/) using the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Go to **Azure Active Directory** and **Groups**.

3. On the **Groups** page, configure **Expiration** so that **Group lifetime (in days)** is **90**.

4. In the **Email contact for groups with no owners** field, type the email address (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

5. Apply the expiration policy you just created to **Teams Rollout** group only.

You have successfully created a new expiration policy and configured the **Teams Rollout** team to expire after 90 days. If the team won’t have a owner after 90 days, Joni Sherman is notified about the expiration if the team.

#### Task 5 - Configure a group creation policy

You are an administrator for your Teams organization. You need to limit which users can create Microsoft 365 groups. You will create a security group named **GroupCreators** which only the members of the group can create Microsoft 365 groups.

1. Open a **Windows PowerShell** window.

2. Connect to the Azure AD in your tenant as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com):
   ```powershell
   Connect-AzureAD
   ```
3. Create a new security group "GroupCreators" by running the following cmdlet:
   ```powershell
   New-AzureADGroup -DisplayName "GroupCreators" -SecurityEnabled:$true -MailEnabled:$false -MailNickName "GroupCreators"
   ```
4. Run following cmdlet to add **Lynne Robbins** to the new security group:

   ```powershell
   Get-AzureADGroup -SearchString "GroupCreators" | Add-AzureADGroupMember -RefObjectId (Get-AzureADUser -SearchString "Lynne Robbins").ObjectId
   ```
5. Fetch the current group settings for the Azure AD organization

   ```powershell
   $Setting = Get-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ).id
   ```
6. Run following cmdlet to modify the group creation setting for your tenant with the "EnableGroupCreation" attribute:

   ```powershell
   $Setting["EnableGroupCreation"] = "False"
   ```
7. Run following cmdlet to add the just created security group "GroupCreators" as permitted group to create groups, by their ObjectID:
   ```powershell
   $Setting["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString "GroupCreators").objectid
   ```
8. Then save the changes and apply the settings:
   ```powershell
   Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
   ```
9. To test the newly configured settings, connect to the **Client 2 VM** with the credentials that have been provided to you.

10. In Microsoft Edge browser, sign in to **Microsoft Teams web client** (**https://teams.microsoft.com/**) as user MeganB@&lt;YourTenant&gt;.OnMicrosoft.com.

11. Select **Join or create a team** and you won’t see the option to **Create team**.

12. Close all open windows.

**Note:** When you are still able to create a new team, wait several minutes for the new configuration to take effect on your users.

In this task, you have successfully created a security group and configured Azure AD settings to restrict the creation of new groups to members of this security group only. At the end of the task, you have successfully tested the new group creation restrictions.

#### Task 6 - Configure a new naming policy

As part of your Teams planning project, you will configure the naming policy where each new Microsoft 365 Group or Team needs to comply with the organization’s regulations on naming objects. Each group name should start with letters **Group** and end with the **Country** attribute. Furthermore, there is an internal regulation that forbids using following specific keywords in Teams names: CEO, Payroll and HR.

1. Sign in to the **Azure Portal** ([**https://admin.microsoft.com**](https://admin.microsoft.com/)) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Go to **Azure Active Directory** and **Groups**.

3. On the **Groups** page, configure the **Naming policy**.

4. Download a blocked words sample file. Save the file, and then open the file in **Notepad**.

5. Type **CEO, Payroll,** HR, replacing the empty quotes in the Notepad window and save the file in place. Afterwards, close the Notepad file.

6. Back to the **Groups | Naming policy** page, upload the **BlockedWords.csv** file you just created.

7. On the **Groups | Naming policy** page, configure group name prefix to be the string: **Group_**, and the group name suffix to be the **CountryOrRegion** attribute.

8. On the **Groups | Naming policy** page, under **Current policy** section, preview the group name format listed as **Group_&lt;Group name&gt;&lt;CountryOrRegion&gt;**. GroupNaming Policy.

9. Select **Save** to apply the new naming policy.

In this task, you have configured a naming policy that will block specific words to be used in an Microsoft 365 Group name, as well as you have configured a new naming policy for Microsoft 365 Group and Teams names.

#### Task 7 - Test the new naming policy

You need to test the newly created naming policy to see its effects in your pilot environment. In the following task, you will try to create a new team and see the configured naming policy template completing the configured name for your new team.

**Note:** It can take up to 24 hours till the blocked words setting will take effect. Therefore, you will only test the configured naming policy, which takes effect immediately.

1. Sign in to the Teams web client ([**https://teams.microsoft.com**](https://teams.microsoft.com/)) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new team with the name **Afterwork** with no members.

3. Review the name of the newly created team.

You have successfully tested the configured naming policy for managing the prefix and suffixes of user created teams. Continue with the next task.

#### Task 8 – Reset Azure AD settings

You can revert any changes in Azure AD unified groups settings to the defaults again. You can do this by loading a blank template and replacing the current configuration with the template. To clean up your test environment after testing, you will now do this and reset all changes you did for Microsoft 365 Groups and Teams.

1. Open a regular **Windows PowerShell** window.

2. Connect to the Azure AD in your tenant as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com):

   ```powershell
   Connect-AzureAD
   ```
3. To load the unifed group template, use the following cmdlet:

   ```powershell
   $Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
   ```
4. Create a blank Azure AD tenant settings object:

   ```powershell
   $Setting = $Template.CreateDirectorySetting()
   ```
5. Check the Azure AD tenant settings configured in the template:
   ```powershell
   $Setting.Values
   ```
6. Check the current configured Azure AD tenant settings and note the differences, to the values in the "$Setting" variable, that contains the default template settings:

   ```powershell
   (Get-AzureADDirectorySetting).Values
   ```
7. Because you will still need the sensitivity labels at a later point of this lab, activate only them in your settings variable again:

   ```powershell
   $Setting["EnableMIPLabels"] = "True"
   ```
8. Apply the configured settings, to revert all other changes:

   ```powershell
   Set-AzureADDirectorySetting -Id $Setting.Id -DirectorySetting $Setting
   ```
9. Check your configured Azure AD tenant settings again, which are all on default again:

   ```powershell
   (Get-AzureADDirectorySetting).Values
   ```
10. Close the PowerShell window.

You have successfully reset all Azure AD tenant settings for Microsoft 365 Groups and Teams in your test tenant.
 
### **Exercise 2: Implement security for Microsoft Teams**

In this exercise, you will increase the security level in your organization by configuring Safe Attachments to ensure that no malicious content is sent through documents shared in Teams by blocking attachments that contain malware.

#### Task 1 - Configure Safe Attachments for Microsoft Teams

Users in your organization are using Microsoft Teams for communication and collaboration. Business managers are concerned that documents that are shared within Microsoft Teams may contain malware. You will need to ensure that no malicious content is sent through documents shared in Teams by configuring Safe Attachments that blocks documents that contain malware.

1. Sign in to the **Microsoft 365 security center** ([https://security.microsoft.com](https://security.microsoft.com/) ) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the **Microsoft 365 security center**, navigate to **Policies& rules** and open **Safe Attachments**.

3. On the **Safe Attachments** page, select **Global settings** then set **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** to **On**.

4. Select **Save** and close the Edge browser window.

In this task, you have activated Safe Attachments scanning for SharePoint, OneDrive, and Microsoft Teams that blocks block documents that contain malware.

### **Exercise 3: Implement compliance for Microsoft Teams**

Before deploying Microsoft Teams in your organization, you need to evaluate Microsoft Teams compliance features to meet organizations requirements. First, you will configure retention settings on data in Microsoft Teams. Next you will configure DLP policy that will search for GDPR related and credit card data and test a DLP policy in the end.

#### Task 1 - Create a new retention policy to retain content

Teams retention settings are very important for managing the lifecycle of company data, and therefore, the capabilities of retention policies need to be evaluated in the Teams pilot. In this task, you will create a new retention policy that retains the Teams channel messages of the "Sales" Team for 7 years after last modification.

1. Sign in to the **Microsoft 365 compliance center** ([https://compliance.microsoft.com](https://compliance.microsoft.com/) ) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **policies**, **Data** and **Retention**.

3. On the **Retention** page, create a new retention policy with the following configuration:

	- **Name**: Sales retention policy

	- **Description**: Retention policy for Sales department that will retain channel messages for 7 years

	- **Locations to apply to policy:** Teams channel messages > **Sales** team only

	- **Retain items for a specified period:** 7 years from the date the item was last modified

	- **At the end of the retention period**: Do nothing

4. Leave the browser open for the next task.

In this this task, you have successfully created a new retention policy named **Sales retention policy** that retains the channel messages and chat of the **Sales** Team for **7 years after the last modification**.

#### Task 2 - Create a new retention policy to delete content

After configuring a retain policy to protect data from deletion, you also need to evaluate the capabilities of retention policies to delete content automatically. For demonstration purpose, you will set the deletion threshold to a single day and apply the retention policy to the "Teams Rollout" team, to remove all channel messages older than a day automatically.

1. Sign in to the **Microsoft 365 compliance center** ([https://compliance.microsoft.com](https://compliance.microsoft.com/) ) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **policies**, **Data** and **Retention**.

3. On the **Retention** page, create a new retention policy with the following configuration:

	- **Name**: Teams Rollout deletion policy.

	- **Description**: Retention policy for the Teams Rollout team to delete messages older than a day.

	- Delete content that’s older than **1 day** from the date **when it was created.**

	- **Locations to apply to policy:** Teams channel messages > Teams Rollout team only.

4. Close all browser windows.

You have successfully created a second retention policy for testing the deletion capabilities to clean up the "Teams Rollout" team from all conversation messages older than a day.

#### Task 3 – Test the retention policy for deleting content (optional)

In this task you will test the retention policy for deleting content from the Teams Rollout team after a day. Before you can see the retention policy taking any effect, you must create some conversation content in the team.

**Note:** Because you need to wait for 24 hours till the retention policy deletes anything, this task is marked as optional. After creating content in the Teams Rollout team, you need to return to this task after waiting 24 hours to see the retention policies effect.

1. Connect to a client and sign in to the Teams Desktop client using **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a **New conversation** in the **General** channel of **Teams Rollout.**

3. Write down **Hello world!** and any other messages you like.

4. Come back after 24 hours to see, the content has been deleted automatically.

You have added a conversation message to a team, which is deleted by the deletion retention policy after 24 hours.

#### Task 4 - Create a DLP policy for GDPR (PII) content from a template

According to your organization compliance requirements, you need to implement basic protection of PII data for European users. You will create a new DLP Policy named **GDPR DLP Policy** from the template "General Data Protection Regulation (GDPR)." The DLP policy you create will detect if GDPR sensitive content is shared with people outside of your organization. If the policy detects at least one occurrence of the GDPR sensitive information, it will send email to Joni Sherman and block people from sharing the content and restricting access to shared content. Furthermore, it will display a tip to users who tried to share the sensitive content and it will allow them to override the policy with business justification. Since you are evaluating the DLP policies, you will create the DLP policy in a test mode with policy tips enabled.

1. Sign in to the **Microsoft 365 compliance center** ([https://compliance.microsoft.com](https://compliance.microsoft.com/) ) using **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. Navigate to **Data loss prevention**.

3. Create a new DLP policy with the following configuration:

	- **Template:** General Data Protection Regulation (GDPR)

	- **Name:** GDPR DLP Policy

	- **Description:** Data loss prevention policy for GDPR regulations in Teams

	- **Locations to apply to policy:**  Teams chat and channel messages

	- **Instances of the same sensitive info type**: 1

	- **Send incident reports in email**: MOD Administrator and Joni Sherman

	- Select **Block people from sharing and restrict access to shared locations**

	- Select **Only people outside your organization. People inside your organization will continue to have access**

	- Select **Override the rule automatically if they report it as false** positive

	- **Test or turn on the policy:** Turn it on right away

4. Stay on the **Data loss prevention page** in the **Microsoft 365 compliance center**.

After completing this task, you have created a DLP Policy from the template "General Data Protection Regulation (GDPR)" that detects if GDPR sensitive content is shared with people outside of your organization. The policy is extra sensitive for the configured threshold of 1 rule match and Joni Sherman will be notified if a matching occurs.

#### Task 5 - Create a DLP policy from scratch

After creating a DLP Policy for protecting GDPR relevant data, you will create another policy from scratch. Instead of using a template, you will configure rules directly with custom rules and actions.

1. Sign in to the **Microsoft 365 compliance center** ([https://compliance.microsoft.com](https://compliance.microsoft.com/) ) using **MOD Administrator** (admin@_&lt;YourTenant&gt;_.onmicrosoft.com).

2. Navigate to **Data loss prevention**.

3. Create a new DLP policy with the following configuration:

	- **Template**: Custom 

	- **Name:** Credit card data DLP Policy

	- **Description**: Data loss prevention policy for credit card data in Teams

	- **Locations to apply to policy:**  Teams chat and channel messages

	- **Custom rule name**: Credit card numbers found

	- **Custom rule description**: Basic rule for protecting credit card numbers form being shared in Teams

	- **Conditions**: Content contains at least 1 instance of Sensitive information type "Credit Card Number" with default accuracy

	- **Action**: Restrict access or encrypt content in Microsoft 365 locations

	- **User notification**: Customize the policy tip text: "Credit card numbers are not allowed to be shared!"

	- **Incident reports**: Send an alert to admins when a rule match occurs and include Joni Sherman

	- **Test or turn on the policy** Turn it on right away

4. Close the **Data loss prevention page** and the **Microsoft 365 compliance center**.

You have successfully created a new custom DLP policy for protecting credit card numbers from being shared via Teams conversations.

#### Task 6 – Test the DLP Policies

To make sure your configured DLP policies are working as expected, you need to perform some testing with your pilot users.

**Note:** It can take up to 24 hours till new DLP policies take effect. If the steps do not work, continue with the lab, and perform task 6 at a later point of working through this lab.

1. Connect to a client and sign in to the Teams Desktop client using **Megan Bowen** (MeganB@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a **New conversation** in the **General** channel of **Teams Rollout.**

3. Enter the following lines to the textbox and send the message:

	- MasterCard: 5105105105105100

	- Visa: 4111111111111111

	- Visa: 4012888888881881

4. Review the error message.

5. Sign in to the **Microsoft 365 compliance center** ([https://compliance.microsoft.com](https://compliance.microsoft.com/) ) using **MOD Administrator** (admin@_&lt;YourTenant&gt;_.onmicrosoft.com).

6. Navigate to **Reports**.

7. Review the DLP policy violations.

You have successfully tested your DLP policy to block sharing of credit card information via Teams chat and channel conversations.

END OF LAB