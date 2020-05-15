--- 
lab: 
    title: 'Lab: Environment preparation for Teams'
    type: 'Answer Key' 
    module: 'Module 03: Prepare the environment for a Microsoft Teams deployment' 
---

# Lab 03: Environment preparation for Teams   
# Student lab answer key
## Use the new Microsoft 365 admin center

Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center and are prompted with a window asking if you want to try the new Microsoft 365 admin center, always select the **Try it now** button.   
‎  
**‎IMPORTANT**: The instructions that are provided in the lab exercises for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

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

| **Location**| **Total number of employees**  | **WAN link capacity / audio/video queue size (Mbps)** | **Office 365 connection**  | **Internet connection** |
|------|-------------|---------|-------------|----------------------------|
| New York HQ | 1000| 1024/300/500 | ExpressRoute | Local Internet 1024 Mbps|
| Los Angeles Office | 250 | 500/100/200  | Remote connection through HQ | Remote Internet through HQ | 
| Houston Office     | 150 | 400/50/100   | Remote connection through HQ | Remote Internet through HQ |                         

Next, you will analyze your current bandwidth usage and test your network quality and connection to Microsoft Teams. You will also need to troubleshoot potential voice quality issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com) to access the **Microsoft Teams admin center**. 

3. When you see the Pick an account window, select **admin@_YourTenant_.onmicrosoft.com** and sign in.

4. In the **Teams admin center,** on the left-hand navigation pane, select the **Planning**, then choose **Network Planner**. 

5. On the **Network planner** page, under **Network plans** tab, select **Add**. 

6. On the **Network plan name** page, in the **Network plan name** box, type **Contoso plan**, and in the **Description** box type **Contoso Teams Network plan**, and then select **Apply**.

7. On the Network planner page, select **Personas** tab, and then select **Add**.

8. On the **Add persona** page, in the **Persona name** box type **New York office**, in the **Description** box type **New York office Teams users**, under the **Permissions** section turn **On** all buttons, and then select **Apply**.

9. Select **Add** again, and on the **Add persona** page, in the **Persona name** box type **Los Angeles office**, in the **Description** box type **Los Angeles office Teams users**, under the **Permissions** section, turn **Off PSTN** button, and turn **On** all other buttons, and then select **Apply**.

10. Click on the **Networks plans** tab, then select **Contoso plan**, and under **Network sites** tab, select **Add a network site**.

11. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **New York HQ site**

	- In the in the description field type **New York HQ site network infrastructure**

	- In the **Network users** field type **1000**.

	- In the **Network settings** section, in the **Subnet** box type **172.16.0.0**, and in the **Network range** box type **16**.

	- In the **Network settings** section, turn **On** the **Express Route** button.

	- In the **Network settings** section, in the **Internet link capacity** box, type **1024**.

	- In the **Network settings** section, in the **PSTN egress** drop-down box, choose **Use VoIP only**, and then select **Save**.

12. On the **Contoso plan** page, under **Network sites** tab, select **Add a network site**.

13. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **Los Angeles site**

	- In the in the description field type **Los Angeles site network infrastructure**

	- In the **Network users** field type **250**.

	- In the **Network settings** section, in the **Subnet** box type **192.168.10.0**, and in the **Network range** box type **24**.

	- In the **Network settings** section, ensure **ExpressRoute** button is **Off**.

	- In the **Network settings** section, turn **On** the **Connected to WAN** button, then in **WAN link capacity** box type **500**, in the **WAN audio queue size** box type **100**, and in **Video queue size** box type **200**. 

	- In the **Network settings** section, in the **PSTN egress** drop-down box, **choose VoIP only**, and then select **Save**.

14. On the **Contoso plan** page, under **Network sites** tab, select **Add a network site**.

15. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **Houston site**

	- In the in the description field type **Houston site network infrastructure**

	- In the **Network users** field type **150**.

	- In the **Network settings** section, in the **Subnet** box type **192.168.20.0**, and in the **Network range** box type **24**.

	- In the **Network settings** section, ensure ExpressRoute button is **Off**.

	- In the **Network settings** section, turn **On** the **Connected to WAN** button, then in **WAN link capacity** box type **400**, in the **WAN audio queue size** box type **50**, and in **Video queue size** box type **100**. 

	- In the **Network settings** section, in the **PSTN egress** drop-down box, **choose VoIP only**, and then select **Save**.

16. On the **Contoso plan** page, select **Report** tab and then select **Start a report**.

17. On the Report page, in the **Report name** field, type **Contoso report** and in the description field, type **Contoso network estimation report**.

18. Under the **Calculation** section, review the default distribution of different personas in each site, and then select **Generate report**.

19. Under the **Reports** section, review the impact of Microsoft Teams on the Contoso network infrastructure by analyzing the report results on bandwidth needed for audio, video, screen sharing, Office 365 traffic, and PSTN.

20. On the report page, select the **Switch to chart view** at upper-right hand corner to display report results in different views. 

21. Click the circle with the admin's initials (**MA**) at the upper right and then select **Sign out**. Close the browser window.

Once you generate the report, you’ll see the recommendation of your bandwidth requirements. The allowed bandwidth shows how much of your overall traffic is reserved for real-time communications. 30% is the recommended threshold. By changing this value and selecting **Run report**, you can see the different impact on the bandwidth for your network. Any areas that need more bandwidth will be highlighted in red. Work with your instructor to modify the parameters in the Network Planner and verify different results based on the input data.

In this lab, you have used Network Planner to estimate the Microsoft Teams impact on the bandwidth in your network infrastructure.


#### Task 2 - Use network testing companion

You are in the planning phase of a Microsoft Teams deployment. Before deploying Microsoft Teams in your organization, you want to test your network quality and connection to Microsoft Teams. After completing the test, you will interpret the results and gain insights into potential network issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the User Account Control dialog with Yes.

4. In the PowerShell window, type **Install-Module -Name NetworkTestingCompanion** and press **Enter**.

5. Type in **y** and hit **return** for the Question with the **Untrusted repository**.

6. In the PowerShell cli run the **Invoke-ToolCreateShortcuts** cmdlet to get a desktop shortcut. 

7. Open **Network Testing Companion** from the desktop shortcut and select the **Install** button, to install the Network Assessment Tool.

8. On the **User Account Control** window, select **Yes**.

9. Wait until window **Skype for Business and Microsoft Teams Network Testing Companion** initializes with green **Start** button appears in the **Network Connectivity and Quality Test** section on the right side of the window.

10. In the **Skype for Business and Microsoft Teams Network Testing Companion** window, review the information in the sections under **Windows operating system**, **Internet connection**, and **Network Assessment tool**, and verify that no errors appear.

11. In the **Skype for Business and Microsoft Teams Network Testing Companion** window, select the green **Start** button in the **Network Connectivity and Quality Test** section.

12. On the **Windows Security Alert** window, select **Allow access** and in the green **Start** button in the **Network Connectivity and Quality Test** section select **Start** again and wait until it completes.

13. After the test is **finished**, select the **View Results** tab and review the results of the testing.

14. In the **View Results** tab, select **Report file** icon under **Network Connectivity** and **Network Quality** and review the testing steps and reports. 

15. Discuss the results with the instructor.
 
In this task, you have used Skype for Business and Microsoft Teams Network Testing Companion to test the connectivity and connection quality of your network infrastructure for Microsoft Teams.



### Exercise 2: Deploy Teams device profiles 

As a Teams administrator, you will create configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices.

Your organization could purchase Microsoft Teams Rooms that provide complete meeting experience with HD video, audio, and content sharing in conference rooms. You will need to prepare the deployment prerequisites by define Microsoft Teams Rooms service account in Office 365.


#### Task 1 - Create configuration profiles 

During the planning phase of Teams Phones devices in your organization, you want to evaluate settings that can be applied to Teams devices by using configuration profiles in Teams admin center. You will create configuration profile for Teams device and analyze settings that will include in the configuration profile. Once devices are deployed into your organization, you will be ready to apply configuration profiles to those devices. 

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com) to access the **Microsoft Teams admin center**. 

3. When you see the **Pick an account** window, select **JoniS@_YourTenant_.onmicrosoft.com** and sign in with the credentials provided to you.

4. In **Teams admin center**, on the left navigation pane, select **Devices**, and then choose **Phones**.

5. On the **Phones** page, select **Configuration profiles** tab, and then select **Add**.

6. Enter the following information for the new configuration profile:

	- **Configuration profile Name**: New York Teams Desk Phones

	- **Description:** Configuration profile for Teams Desk Phones in New York HQ

7. Under **General** section, configure following settings:

	- **Device lock:** On.

	- **Timeout** 30 seconds

	- **PIN:** 123456

	- **Language:** English (United States).

	- **Timezone**: (UTC-5:00) Eastern Time (US and Canada)

	- **Date format:** MM/DD/YYYY

	- **Time format:** 12 Hours (AM/PM)

8. Under **Device settings** configure following settings:

	- **Display screen saver:** On, Timeout 1 minute.

	- **Display high contrast:** On

	- **Office hours:** 08:00-17:00

	- **Power Saving:** On.

9. Under **Network settings**, configure following settings:

	- **DHCP enabled:** On

	- **Logging enabled:** Off

	- **Device’s default admin password:** Pass@word1

10. Once you complete with the configuration profile settings, select **Save**.

11. Click the circle with Joni's picture at the upper right and then select **Sign out**. Close the Edge browser window.

In this task, you have successfully created a configuration profiles that can be applied to Microsoft Teams devices.
 

#### Task 2 - Create a Microsoft Team Room 

Your organization has ordered devices for Microsoft Teams room. In the meantime, you need to ensure that all prerequisites for the equipment installation are being completed. One of the prerequisites for Microsoft Teams Room deployment is adding a device account and assigning Office 365 license for that account.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On Client 1 VM, right-click the Start button, and choose **Windows PowerShell**.

3. In order to connect to Exchnage Online PowerShell, perform the following steps:

4. In **Windows PowerShell** window, run the following cmdlet: 

	```powershell
	$UserCredential = Get-Credential
	```

5. In the **Windows PowerShell Credential Request** dialog box, enter the **admin@_YourTenant_.onmicrosoft.com**, including and the password provided to you and then select **Ok**.

6. Run the following cmdlet to establish a connection to Exchange Online PowerShell:

	```powershell
	$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
	```
7. Import the established session with the following cmdlet:

	```powershell
	Import-PSSession $Session -DisableNameChecking
	```

8. Create a new room mailbox named **NY-TeamsRoom1** by running the following cmdlet (remember to replace your tenant name):

	```powershell
	New-Mailbox -Name "NY-TeamsRoom1" -Alias NY-TeamsRoom1 -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID NY-TeamsRoom1@_YourTenant_.onmicrosoft.com -RoomMailboxPassword (ConvertTo-SecureString -String 'pass@word1' -AsPlainText -Force)
	```

9. Configure the Calendar Processing features for the Teams Room. Read the following description and run the cmdlet at the end:

	- **AutomateProcessing**: AutoAccept (Meeting organizers receive the room reservation decision directly without human intervention: free = accept; busy = decline.)

	- **AddOrganizerToSubject**: $false (The meeting organizer is not added to the subject of the meeting request.)

	- **DeleteComments**: $false (Keep any text in the message body of incoming meeting requests.)

	- **DeleteSubject**: $false (Keep the subject of incoming meeting requests.)

	- **RemovePrivateProperty**: $false (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

	- **AddAdditionalResponse**: $true (The text specified by the AdditionalResponse parameter is added to meeting requests.)

	- **AdditionalResponse**: "This is a Teams Meeting room" (The additional text to add to the meeting request.)
	
	```powershell
	Set-CalendarProcessing -Identity "NY-TeamsRoom1" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Teams Meeting room"
	```

10. Disconnect from Exchage Online and end the established session with the following cmdlet:

	```powershell
	Remove-PSSession $Session
	```

11. Connect to **Azure AD PowerShell** to configure Teams Room account settings by running the following cmdlet:

	```powershell
	Connect-AzureAD
	```

12. On the sign in window, enter **admin@_YourTenant_.onmicrosoft.com** and sign in with the password provided.

13. Disable the password expiration for the Teams Room account **NY-TeamsRoom1@_YourTenant_.onmicrosoft.com** by running the following cmdlet:

	```powershell
	Set-AzureADUser -ObjectId NY-TeamsRoom1@_YourTenant_.onmicrosoft.com -PasswordPolicies DisablePasswordExpiration
	```

14. Close the PowerShell window and open the Edge browser from the task bar.

15. Navigate to the **Microsoft 365 admin center** page by entering the following URL in the address bar: **https://admin.microsoft.com**.

16. When you see the Pick an account window, select **admin@_YourTenant_.onmicrosoft.com** and sign in.

17. In **Microsoft 365 admin center** from the left navigation pane, select **Users**, and then choose **Active Users**.

18. Select the **NY-TeamsRoom1@_YourTenant_.onmicrosoft.com** account, and then select **Manage product licenses** tab.

19. On **NY-TeamsRoom1@contoso.onmicrosoft.com** page, under the **Licenses and Apps** tab, select Office 365 E5 and then select **Save changes,** which is final step in preparing an account for your Microsoft Teams Room service in Office 365

You have successfully created, configured and licensed a Microsoft Team Room service account, which is a prerequisite for deploying Microsoft Teams Room systems.
