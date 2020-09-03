--- 
lab: 
    title: 'Lab: Configure Security and Compliance for teams and content'
    type: 'Answer Key' 
    module: 'Module 02: Implement Microsoft Teams Governance, Security and Compliance' 
---

# Lab 02: Configure Security and Compliance for teams and content
# Student lab answer key
## Lab Scenario  

In the labs of this course you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. Before starting the deployment, IT department is gathering business requirements about Teams governance as well as data security and compliance, including how the data shared in Teams be regulated according to the organization's compliance requirements. After you complete the planning process, you will configure Microsoft 365 Groups governance, protect Teams from threats, and configure Teams to meet your organization compliance requirements.

## Objectives

After you complete this lab, you will be able to:

- Configure expiration policies
- Restrict creation of new teams to members of a security group
- Create naming policies
- Reset all Azure AD settings to defaults
- Activating ATP protection for SharePoint, OneDrive and Teams
- Configure retention policies
- Create a DLP policy to protect GDPR content

## Lab Setup  
- **Estimated Time:** 90 minutes.

## Instructions



### Exercise 1: Implement Governance and Lifecycle Management for Microsoft Teams

Your organization has started the planning process for Microsoft 365 services adoption. You are assigned as a Teams admin role to plan Teams governance. Since Teams relies on Microsoft 365 groups, you need to plan governance procedures for Microsoft 365 groups, including creating Microsoft 365 groups expiration policies, configuring Microsoft 365 Group creation policy permissions, and configuring Microsoft 365 Groups naming policies.

#### Task 1 - Create and assign expiration policy    
Based on the organization requirement, unneeded groups should be deleted automatically after 90 days. To evaluate the group expiration policy experience, you will configure an expiration policy, that will delete the **Teams Rollout** group after a 90 days.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [**https://portal.azure.com**](https://portal.azure.com/). 

3. Sign in with the global admin credential (**admin@_&lt;YourTenant&gt;_.onmicrosoft.com**).

4. If the **Welcome to Microsoft Azure** dialog box appears, select **Maybe later**. If an Azure Advisor recommendations window is displayed, close it with the **X**.

5. In the **Microsoft Azure portal**, below the **Azure services** section, select **Azure Active Directory** (You might need to select **More services** to see the option).

6. In the **Azure Active Directory**, on the left navigation pane, select **Groups**.

7. On the **Groups - All groups** page, on the left navigation pane, select **Expiration**.

8. In the **Groups - Expiration** page, use the **Group lifetime (in days)** drop-down box, and choose **Custom**.

9. In the box right from **Custom,** type **90**.

10. In the **Email contact for groups with no owners** field, type **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com**.

11. In the Field **Enable expiration for the Office 365 groups**, select the **Selected** button, and then select  **+ Add** button to open a right-side pane.

12. In the **Select groups** pane, type **Teams Rollout** into the textbox and selec the group.

13. Use the **Select** button on the lower end of the right-side pane to apply the policy to the **Selected group**.

14. Back on the **Groups - Expiration** page, select **Save**.

15. Close the Edge Browser window.

You have successfully created a new expiration policy and configured the **Teams Rollout** team to expire after 90 days. If the team won’t have a owner after 90 days, Joni Sherman is notified about the expiration if the team.


#### Task 2 - Configure group creation policy    

You are an administrator for your Teams organization. You need to limit which users are able to create Microsoft 365 groups. You will create a security group named **GroupCreators** which only the members of the group are allowed to create Microsoft 365 groups.


1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the User Account Control window with **Yes**. 

4. In the PowerShell window, enter the following to install the Azure AD Preview module:

   ```powershell
   Install-Module AzureADPreview
   ```

5. When you are prompted to install from the Untrusted repository, also confirm by entering **Y** and pressing Enter.

6. Connect to the Azure AD in your tenant with the following cmdlet:

   ```powershell
   Connect-AzureAD
   ```

7. A Sign in dialog box will open. Sign in as **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** using the O365 Credentials provided to you.

8. Create a new security group “GroupCreators” with the following cmdlet:

	```powershell
	New-AzureADGroup -DisplayName “GroupCreators” -SecurityEnabled:$true -MailEnabled:$false -MailNickName “GroupCreators”
	```

9. Run following cmdlet to add **Lynne Robbins** to the new security group:

	```powershell
	Get-AzureADGroup -SearchString "GroupCreators" | Add-AzureADGroupMember -RefObjectId (Get-AzureADUser -SearchString “Lynne Robbins”).ObjectId
	```

10. Run following cmdlet to fetch the unified group template again and load it into the “$template” variable:

	```powershell
	$Template = Get-AzureADDirectorySettingTemplate | Where {$_.DisplayName -eq "Group.Unified"}
	```

11. Run following cmdlet to check if a Azure AD setting is already existing and load it, if existing. If not, create a blank Azure AD setting object and populate the “$Setting” variable:

	```powershell
	if (!($Setting=Get-AzureADDirectorySetting|Where {$_.TemplateId -eq $Template.Id})) {$Setting = $Template.CreateDirectorySetting}
	```

12. Run following cmdlet to modify the group creation setting for your tenant with the “EnableGroupCreation” attribute:

	```powershell
	$Setting["EnableGroupCreation"] = “False”
	```

13. Run following cmdlet to add the just created security group “GroupCreators” as permitted group to create groups, by their ObjectID:

	```powershell
	$Setting["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString “GroupCreators”).objectid
	```

14. Write back the changed settings object to your Azure AD tenant, by using the following cmdlet:

	```powershell
	Set-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where {$_.DisplayName -eq "Group.Unified"}).id -DirectorySetting $Setting
	```

15. To test the newly configured settings, connect to the **Client 2 VM** with the credentials that have been provided to you.

16. Open a Edge browser window and navigate to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/).

17. On the Pick an account window, select **MeganB@_&lt;YourTenant&gt;_.OnMicrosoft.com** and sign in with her credentials.

18. Select **Join or create a team** from the lower end of the teams overview and you won’t see the option to **Create team**.

19. Click the circle with Megan's picture at the upper right and then select **Sign out**. Close all open windows.

In this task, you have succerssfully created a security group and configured Azure AD settings to restrict the creation of new groups to members of this security group only. At the end of the task, you have successfully tested the new group creation restrictions.


#### Task 3 - Configure a new naming policy  
As part of your Teams planning project, you will configure the naming policy where each new Microsoft 365 Group or Team needs to comply with the organization’s regulations on naming objects. Each group name should start with letters **Group** and end with the **Country** attribute. Furthermore, there is an internal regulation that forbids using following specific keywords in Teams names: CEO, Payroll and HR. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Azure Portal**: [**https://portal.azure.com**](https://portal.azure.com).

3. When you see the **Pick an account** window, select **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in.

4. In the **Microsoft Azure portal**, under **Azure services** section, select **Azure Active Directory**.

5. In the **Azure Active Directory**, on the left navigation pane, select **Groups**.

6. On the **Groups - All groups** page, on the left navigation pane, select **Naming policy**.

7. Select **Download** in the main window to download a blocked words sample file. **Save** the file and select **Open folder**.

8. Right-click the file and select **Edit** to open **Notepad**.

9. Type **CEO,Payroll,HR** replacing the empty quotes in the Notepad window and save the file in place. Afterwards, close the Notepad file.

10. Back to the **Groups - Naming policy** page, under **Blocked words** section, at **Step 3. Upload your .csv file**, select the **folder** icon, then browse for **BlockedWords.csv** file, which is located in your **Downloads** folder, and select **Open**. 

11. On the **Group - Naming policy** page, select **Save**. After this step **BlockedWords.csv** file that contains blocked words be uploaded to the naming policy.

12. On the **Groups - Naming policy** page, select the **Group naming policy** tab.

13. Under the **Group naming policy** section, select the checkbox next to **Add prefix** and from the drop-down menu, choose string, and in the empty box to the right, type **Group**.

14. Under the **Group naming policy** section, select the checkbox next to **Add suffix** and from the drop-down list, choose **Attribute**, and from the drop-down list choose **CountryOrRegion**.

15. On the **Groups - Naming policy** page, under **Current policy** section, preview the group name format listed as **Group&lt;Group name&gt;&lt;CountryOrRegion&gt;**.
![GroupNaming Policy](media/M02-GroupNamingPolicy.png)

16. Since you are only testing the naming policy for evaluation, select **Discard** and confirm with **Yes**.

In this task, you have configured a naming policy that will block specific words to be used in an Microsoft 365 Group name, as well as you have evaluated the options for prefix and suffix of the Microsoft 365 Group name.


#### Task 4 – Remove the changed Azure AD settings again  
You can revert the Azure AD settings changes to defaults with following steps.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell**.

3. Connect to the Azure AD in your tenant with the following cmdlet:

   ```powershell
   Connect-AzureAD
   ```

4. A Sign in dialog box will open. Sign in as **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** using the O365 Credentials provided to you.

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

8. Check the current configured Azure AD tenant settings and note the differences, to the values in the “$Setting” variable, that contains the default template settings:

	```powershell
	(Get-AzureADDirectorySetting).Values
	```

9. Apply the default settings, to revert all changes:

	```powershell
	Set-AzureADDirectorySetting -Id (Get-AzureADDirectorySetting | where {$_.DisplayName -eq "Group.Unified"}).id -DirectorySetting $Setting
	```

10. Check your configured Azure AD tenant settings again, which are all on default again:

	```powershell
	(Get-AzureADDirectorySetting).Values 
	```

11. Close the PowerShell window.

You have successfully reset all Azure AD tenant settings in your test tenant. 



### Exercise 2: Implementing security for Microsoft Teams
In this exercise, you will increase the security level in your organization by configuring an ATP policy to ensure that no malicious content is sent through documents shared in Teams by blocking attachments that contain malware. 


#### Task 1 - Configure ATP for Microsoft Teams 
Users in your organization are using Microsoft Teams for communication and collaboration. Business managers are concerned that documents that are shared within Microsoft Teams may contain malware. You will need to ensure that no malicious content is sent through documents shared in Teams by configuring ATP policy that blocks documents that contain malware. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Microsoft 365 Security center**: [**https://security.microsoft.com**](https://security.microsoft.com). 

3. When you see the **Pick an account** window, select **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in.

4. In the **Microsoft 365 Security center**, in the left navigation pane, select **Policies**.

5. On the **Policies** page, scroll to the **Threat protection** section and select **ATP safe attachments (Office 365)**.

6. On the **Safe attachments** page, select **Global settings** on the ribbon. 

7. In the wizard, set **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** to **On**.

8. Select the **Save** button.

9. Close the Edge browser window.

In this task, you have activated ATP safe attachments scanning for SharePoint, OneDrive, and Microsoft Teams that blocks block documents that contain malware.



### Exercise 3: Implementing Compliance for Microsoft Teams
Before deploying Microsoft Teams in your organization, you need to evaluate Microsoft Teams compliance features to meet organizations requirements. First, you will configure retention settings on data in Microsoft Teams. Next you will configure DLP policy that will search for all GDPR related data.


#### Task 1 - Create a new retention policy for a single team  
Before deploying Microsoft Teams in your organization, you will need to evaluate Microsoft Teams retention settings. You will create a new retention policy that retains the content of the "Sales" Team for 7 years after last modification. 
 
1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Office 365 Security &amp; Compliance center**: [**https://protection.office.com**](https://protection.office.com)

3. When you see the **Pick an account** window, select **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in.

4. In **Office 365 Security &amp; Compliance center**, on the left navigation pane, select **information governance**, and then choose **Retention**.

5. On the **Retention** page, select **Create**, and then on the **Name your policy** page, in the **Name** box, type: **Sales retention policy**. In the **Description** box, type: **Retention policy for Sales department that will retain data for 7 years.**, and then select **Next**.

6. On the **Decide if you want to retain content, delete it, or both** page, ensure that following settings are configured and then select **Next**:

   - **Yes, I want to retain it**
      - **For this long…**
	  - **7**
	  - **years**

   - **Retain the content based on**
      - **when it was last modified**

   - **Do you want us to delete it after this time?**
      - **No** 

7. On the **Choose locations** page, scroll down and select **Teams channel messages**, then click **Choose teams**. 

8. On the **Edit locations** page, select **Choose teams**, and then select the Team **Sales**, select **Choose** and at the end, select **Done**.

9. On the **Choose locations page,** select **Next** and on **Review your settings** page, select **Create this policy**.

10. Leave the browser open for the next task.

In this this task, you have successfully created a new retention policy named **Sales retention policy** that retains the channel messages of the **Sales** Team for **7 years after the last modification**. 


#### Task 2 - Create a DLP policy for GDPR (PII) content from a template  
According to your organization compliance requirements, you need to implement basic protection of PII data for European users. You will create a new DLP Policy named **GDPR DLP Policy** from the template "General Data Protection Regulation (GDPR)". The DLP policy you create will detect if GDPR sensitive content is shared with people outside of your organization. If the policy detects at least one occurrence of the GDPR sensitive information, it will send email to the Global Admin and block people from sharing the content and restricting access to shared content. Furthermore, it will display a tip to users who tried to share the sensitive content and it will allow them to override the policy with business justification. Since you are evaluating the DLP policies, you will create the DLP policy in a test mode with policy tips enabled.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Microsoft 365 Compliance center**: [**https://compliance.microsoft.com**](https://compliance.microsoft.com).

3. You are still signed in as **admin@_&lt;YourTenant&gt;_.onmicrosoft.com**. When you see the **Pick an account** window, select **admin@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in.

4. In **Microsoft 365 compliance center**, on the left navigation pane, select **Show all** and then select **Data loss prevention**.

5. On the Data loss prevention page, select **+ Create policy**.

6. On the **New DLP policy** page, select the searchbox and type: **GDPR**, select **General Data Protection Regulation (GDPR)**, and then select **Next**.

7. On the **Name your policy** page, type the following values, and then select **Next**:

   - Name: **GDPR DLP Policy**
   
   - Description: **Data loss prevention policy for GDPR regulations in Teams.**

8. On the **Choose locations** page, select **Let me choose specific locations**, and then select **Next**.

9. On the **Choose locations** page, change the "switches" to the following settings, and then select **Next**:

   - Exchange email: **Off**

   - SharePoint sites: **Off**

   - OneDrive accounts: **Off**

   - Teams chat and channel messages: **On** 

10. On the **Customize the type of content you want to protect** page, ensure that the default options are selected, and then select **Next**:

   - The radio button is selected for: **Find content that contains:**
   
      - A checkbox is selected for: **Detect when this content is shared:**
   
      - The drop-down menu shows: **with people outside my organization**

11. On the **What do you want to do if we detect sensitive info?** page, ensure that the following settings are configured, and then select **Next**:

	- A checkbox is selected for: **Send incident reports in email**

	- A checkbox is selected for: **Detect when content that's being shared contains**
	
	   - In the **At least __ instances of the same sensitive info type.** box, type: **1**
	
	- A checkbox is selected for: **Show policy tips to users and send them an email notification.**

	- Select the checkbox for: **Restrict access or encrypt the content**
	
	   - The radio button is selected for: **Block people from sharing and restrict access to shared content**

12. On the **Customize access and override permissions** page, ensure that following settings are configured, and then select **Next**:

	- The radio button is selected for: **Only people outside your organization**

	- The "switch" is **On** for: **Let people who see the tip override the policy**

	- Select the check box for: **Require a business justification to override**
	
	- A checkbox is selected for: **Override the rule automatically if they report it as a false positive**

13. On the **Do you want to turn on the policy or test things out first?** page, ensure that following settings are configured, and then select **Next**:

	- The radio button is selected for: **I'd like to test it out first**
	
	   - Select check box for: **Show policy tips while in test mode**

14. On the Review your settings page, select **Create**.

15. Close all windows.

After completing this task, you have created a DLP Policy from the template "General Data Protection Regulation (GDPR)" that detects if GDPR sensitive content is shared with people outside of your organization.
