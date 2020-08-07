--- 
lab: 
    title: 'Lab: Environment preparation for Teams'
    module: 'Module 03: Prepare the environment for a Microsoft Teams deployment' 
---

# Lab 03: Environment preparation for Teams   
# Student lab manual

Microsoft 365 user interface 

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual. 

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## Lab Scenario  

In the labs of this course you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. However, there are concerns about current network infrastructure to meet the requirements for Microsoft Teams services. Therefore, you need to analyze the current network infrastructure and perform bandwidth calculations. Based on your estimation, you can provide recommendations to the networking team. Furthermore, your organization is planning to purchase and deploy multiple Teams devices. You will need to evaluate different devices profiles and configure profile settings for the devices. At the end, you will need to evaluate the process of creating Microsoft Teams room, where multiple Teams rooms will be purchased in your organization.

## Objectives

After you complete this lab, you will be able to:

- Calculate the network bandwidth capacity for a Teams deployment
- Work with the Network Testing Companion on a client
- Create configuration profiles for devices
- Configure a new Microsoft Teams Room

## Lab Setup  

- **Estimated Time:** 60 minutes.

## Instructions



### Exercise 1: Calculate networking capabilities 

Microsoft Teams provides users with chat, audio, video and content sharing experience in different network conditions. It includes variable codecs, where media can be negotiated in limited bandwidth environments. However, as a Teams admin, you will need to carefully plan your network bandwidth, because there are other Office 365 services and third-party apps that also need reliable network connection. Therefore, it is very important that Teams admins have tools that could help to estimate the bandwidth consumption according to specific business requirements and existing network infrastructure, and provide best experience to business users.


#### Task 1 - Calculate network bandwidth capacity

In this exercise, you will calculate the network requirements for Microsoft teams, depending on your expected Teams usage business requirements. You must ensure enough bandwidth based on your organization network connectivity that is described in the following table:
 
| **Location**       | **Total number of employees**    | **WAN link capacity / audio/video queue size (Mbps)** | **Office 365 connection**  | **Internet connection** |
|--------------------|-------------------------------|--------------|-------------------------------------------------------|----------------------------|
| New York HQ | 1000| 1000/300/500 | ExpressRoute | Local Internet 1000 Mbps|
| Los Angeles Office | 250 | 500/100/200  | Remote connection through HQ | Remote Internet through HQ | 
| Houston Office     | 150 | 400/50/100   | Remote connection through HQ                          | Remote Internet through HQ |     

Next, you will analyze your current bandwidth usage and test your network quality and connection to Microsoft Teams. You will also need to troubleshoot potential voice quality issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. In Microsoft Edge, sign in to **Microsoft Teams admin center** (https://admin.teams.microsoft.com) as user **admin@_&lt;YourTenant&gt;_.onmicrosoft.com**.

3. In the **Teams admin center,** under **Planning** section, open **Network Planner**. 

4. In **Network planner**, create a new network plan named **Contoso plan**, with the description **Contoso Teams Network plan**.

5. In **Network planner**, add a **persona** with name **New York office**, and add a description **New York office Teams users**. Under **Permissions** section, turn **On** all buttons.

6. In **Network planner**, add a **persona** with name  **Los Angeles office**, and add a description **Los Angeles office Teams users**. Under **Permissions** section, turn **Off PSTN** button, and turn **On** all other buttons.

7. In **Contoso plan**, add a **Network site** with following configuration:

	- Network site name:  **New York HQ site**

	- Description: **New York HQ site network infrastructure**

	- Network users: **1000**

	- In the **Network settings** section, add following configuration:

		- Subnet: **172.16.0.0**, Network range: **16**

		- Express Route: **On**

		-  Internet link capacity: **1000**

		-  PSTN egress: **Use VoIP only**

8. In **Contoso plan**, add a **Network site** with following configuration:

	- Network site name: **Los Angeles site**

	- Description: **Los Angeles site network infrastructure**

	- Network users field type: **250**

	- In the **Network settings** section, add following configuration:

		- Subnet: **192.168.10.0**, Network range: **24**

		- ExpressRoute: **Off**

		- Connected to WAN: **On**

		-  WAN link capacity: **500**

		- WAN audio queue size: **100**

		-  Video queue size: **200**

	   - Internet link capacity **500**

		- PSTN egress: **Use VoIP only**

9. In **Contoso plan**, add a **Network site** with following configuration:

	- Network site name: **Houston site**

	- Description: **Houston site network infrastructure**

	- Network users: **150**

    - In the **Network settings** section, add following configuration:

	   - Subnet: **192.168.20.0**, Network range: **24**

	   - ExpressRoute: **Off**

	   -  Connected to WAN: **On**

	   - WAN link capacity: **400**

	   - WAN audio queue size: **50**

	   - Video queue size: **100**

	   - Internet link capacity **400**

	   - PSTN egress: **Use VoIP only**

10. Start a report for the **Contoso plan** with a name **Contoso report** and a description **Contoso network estimation report**.

11. Under the **Calculation** section, review the default distribution of different personas in each site, and then select **Generate report**.

12. Under the **Reports** section, review the impact of Microsoft Teams on the Contoso network infrastructure by analyzing the report results on bandwidth needed for audio, video, screen sharing, Office 365 traffic, and PSTN.

13. On the report page, use the **Switch to chart view** to display report results in different views. 

Once you generate the report, you’ll see the recommendation of your bandwidth requirements. The allowed bandwidth shows how much of your overall traffic is reserved for real-time communications. 30% is the recommended threshold. By changing this value and selecting **Run report**, you can see the different impact on the bandwidth for your network. Any areas that need more bandwidth will be highlighted in red. Work with your instructor to modify the parameters in the Network Planner and verify different results based on the input data.

In this lab, you have used Network Planner to estimate the Microsoft Teams impact on the bandwidth in your network infrastructure.


#### Task 2 - Use network testing companion

You are in the planning phase of a Microsoft Teams deployment. Before deploying Microsoft Teams in your organization, you want to test your network quality and connection to Microsoft Teams. After completing the test, you will interpret the results and gain insights into potential network issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Start **Windows PowerShell (Admin)** and confirm the User Account Control dialog.

3. In the PowerShell window, run the following cmdlet, and accept the question for **Untrusted repository**: 

   ```powershell
   Install-Module -Name NetworkTestingCompanion
   ```  

4. In the PowerShell wihdow, run the following cmdlet to get a desktop shortcut:

   ```powershell
   Invoke-ToolCreateShortcuts
   ``` 

5. Open **Network Testing Companion** and then install the Network Assessment Tool, accepting the **User Account Control** dialog.

6. Wait until window **Skype for Business and Microsoft Teams Network Testing Companion** initializes with green **Start** button appears in the **Network Connectivity and Quality Test** section on the right side of the window.

7. In the **Skype for Business and Microsoft Teams Network Testing Companion** window, review the information in the sections under **Windows operating system**, **Internet connection**, and **Network Assessment tool**, and verify that no errors appear.

8. In the **Skype for Business and Microsoft Teams Network Testing Companion** window, start the **Network Connectivity and Quality Test** and allow access on the **Windows Security Alert** window, and wait until test completes.

9. After the test is finished, review the results of the testing with detailed testing steps and reports. 

10. Discuss the results with the instructor.

In this task, you have used Skype for Business and Microsoft Teams Network Testing Companion to test the connectivity and connection quality of your network infrastructure for Microsoft Teams.


 
### Exercise 2: Deploy Teams device profiles 

As a Teams administrator, you will create configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices.

Your organization could purchase Microsoft Teams Rooms that provide complete meeting experience with HD video, audio, and content sharing in conference rooms. You will need to prepare the deployment prerequisites by define Microsoft Teams Rooms service account in Office 365.


#### Task 1 - Create configuration profiles 

During the planning phase of Teams Phones devices in your organization, you want to evaluate settings that can be applied to Teams devices by using configuration profiles in Teams admin center. You will create configuration profile for Teams device and analyze settings that will include in the configuration profile. Once devices are deployed into your organization, you will be ready to apply configuration profiles to those devices. 

 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Sign in to **Microsoft Teams admin center** (https://admin.teams.microsoft.com) as user **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in with the credentials provided to you.

3. In **Teams admin center**, in the **Devices** section, on the **Phones** page, create a **Configuration profile** with following configuration:

	- Configuration profile Name: **New York Teams Desk Phones**

	- Description: **Configuration profile for Teams Desk Phones in New York HQ**

4. Under **General** section, configure following settings:

	- Device lock: **On**

	- Timeout: **30 seconds**

	- PIN: **123456**

	- Language: **English (United States)**

	- Timezone: **(UTC-5:00) Eastern Time (US and Canada)**

	- Date format: **MM/DD/YYYY**

	- Time format: **12 Hours (AM/PM)**

5. Under **Device settings** configure following settings:

	- Display screen saver: **On, Timeout 1 minute**

	- Display high contrast: **On**

	- Office hours: **08:00-17:00**

	- Power Saving: **On**

6. Under **Network settings**, configure following settings:

	- DHCP enabled: **On**

	- Logging enabled: **Off**

	- Device’s default admin password: **Pass@word1**

In this task, you have successfully created a configuration profiles that can be applied to Microsoft Teams devices.
 

#### Task 2 - Create a Microsoft Teams Room 

Your organization has ordered devices for Microsoft Teams room. In the meantime, you need to ensure that all prerequisites for the equipment installation are being completed. One of the prerequisites for Microsoft Teams Room deployment is adding a device account and assigning Office 365 license for that account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.
2. On Client 1 VM, run **Windows PowerShell**.
3. In order to connect to Exchnage Online PowerShell, perform the following steps:
	- Run the following cmdlet:

		 ```powershell
	    $UserCredential = Get-Credential
	    ```

	- In the **Windows PowerShell Credential Request** dialog box, enter the **admin@_&lt;YourTenant&gt;_.onmicrosoft.com**, including and the password provided to you.

	- Run the following cmdlet to establish a connection to Exchange Online PowerShell:

		 ```powershell
		 $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
		 ```

	- Import the established session with the following cmdlet:

		 ```powershell
		 Import-PSSession $Session -DisableNameChecking
		 ```

4. Create a new room mailbox named **NY-TeamsRoom1** by running the following cmdlet (remember to replace your tenant name):

	```powershell
	New-Mailbox -Name "NY-TeamsRoom1" -Alias NY-TeamsRoom1 -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID NY-TeamsRoom1@<YourTenant>.onmicrosoft.com -RoomMailboxPassword (ConvertTo-SecureString -String 'pass@word1' -AsPlainText -Force)
	```

5. Configure the Calendar Processing features for the Teams Room. Read the following description and run the cmdlet at the end:

	- AutomateProcessing: **AutoAccept** (Meeting organizers receive the room reservation decision directly without human intervention: free = accept; busy = decline.)

	- AddOrganizerToSubject: **$false** (The meeting organizer is not added to the subject of the meeting request.)

	- DeleteComments: **$false** (Keep any text in the message body of incoming meeting requests.)

	- DeleteSubject: **$false** (Keep the subject of incoming meeting requests.)

	- RemovePrivateProperty: **$false** (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

	- AddAdditionalResponse: **$true** (The text specified by the AdditionalResponse parameter is added to meeting requests.)

	- AdditionalResponse: **"This is a Teams Meeting room"** (The additional text to add to the meeting request.)

	```powershell
	Set-CalendarProcessing -Identity "NY-TeamsRoom1" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Teams Meeting room"
	```
 
6. Disconnect from Exchage Online and end the established session with the following cmdlet:

	```powershell
	Remove-PSSession $Session
	```
	
7. Connect to **Azure AD PowerShell,** to configure Teams Room account settings by running the following cmdlet:

	```powershell
	Connect-AzureAD -Credential $UserCredential
	```

8. Disable the password expiration for the Teams Room account **NY-TeamsRoom1@_&lt;YourTenant&gt;_.onmicrosoft.com** by running the following cmdlet:

	```powershell
	Set-AzureADUser -ObjectId NY-TeamsRoom1@<YourTenant>.onmicrosoft.com -PasswordPolicies DisablePasswordExpiration
	```

9. Close the PowerShell window and open the Edge browser, navigate to the **Microsoft 365 admin center** page at:**https://admin.microsoft.com** and sign in as **admin@_&lt;YourTenant&gt;_.onmicrosoft.com**.

10. In the **Microsoft 365 admin center** from **Purchase services** (under **Billing**), obtain a **Meeting Room** trial license.

11. In the **Microsoft 365 admin center** from **Users** section, choose **Active Users**.

12. Add **Meeting Room** product license to the **NY-TeamsRoom1@_&lt;YourTenant&gt;_.onmicrosoft.com** account.

You have successfully created, configured, and licensed a Microsoft Teams Room service account, which is a prerequisite for deploying a Microsoft Teams Room system.
