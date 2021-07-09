---
lab:
    title: 'Lab 05: Manage Teams meetings experiences'
    type: 'Answer Key'
    module: 'Module 5: Manage meetings and virtual events in Microsoft Teams'
---

# **Lab 05: - Manage Teams meetings experiences**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. According to Contoso business requirements, Microsoft Teams will be used as an organization’s solution for conferencing and telephony. Therefore, Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide best user experience during collaboration and communication. 

## **Objectives**

After you complete this lab, you will be able to:

- Manage meeting policies

- Configure meeting settings

- Create live event policies

- Create a live event

- Create configuration profiles for devices

- Configure a new Microsoft Teams Room

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage Live event and meetings experiences**

Contoso organization has deployed Microsoft 365 and is testing pilot projects on collaboration and communication scenarios to meet business requirements. First, Teams admins need to configure meeting policies and schedule initial meetings. Then, business managers want to test the Live meetings option in Microsoft Teams in order to broadcast audio and video to large audiences.

#### Task 1 - Edit the default meeting policy and restrict all recording features for meetings

As part of your pilot project for setting up the events and meetings in your organization, you need to fulfil the requirement for all meetings in teams, including prohibiting meeting recording. You will edit the default meeting policy to ensure that this requirement is met.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Teams admin center** at [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/).

3. On the **Pick an account** page, select the **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. If a **Stay signed in?** dialog box is displayed, select the **Don’t show this again** checkbox and **Yes**.

5. In the **Teams admin center,** on the left navigation pane, select **Meetings,** and then choose **Meeting policies**.

6. Select the **Global (Org-wide default)** policy to change the settings for all users.

7. On the **Meetings policies\Global** page, review the available settings, and under **Audio &amp; Video** section, use the slider to turn **Off** the **Allow cloud recording** setting. Select **Save**.

You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 2 – Test the meeting policy for restricting recording

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

3. Select **Calendar** from the left navigation pane and **Meet Now** from the upper right corner to start a meeting.

4. On the Microsoft Teams page, select **Computer audio** and leave the rest of the settings at the defaults and select **Join now** button.

5. On the Microsoft Team page, hover the mouse over the meeting page, and select the three dots (…) for **More actions**.

6. Note that **Start recording** option is visible but is dimmed, not available to be selected.

 

#### Task 3 - Configure meeting settings and restrict anonymous users from joining meetings

Contoso Ltd. works with several external partners and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Meetings,** and then choose **Meetings settings**.

4. On the **Meetings settings** page, below participants, use the slider to turn **Off** the option **Anonymous users can join a meeting**.

5. Select **Save**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 4 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to management users. Only the organizer of a live event should be able to record his own meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Meetings** and then select **Live event policies**.

4. Select **+ Add** from the top pane, to create a new **Live event policy** with individual settings for assigned users.

5. On **Live event policies\Add** page, enter the following information:

	- Add live events policy: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers**

	- Allow scheduling: **On**

	- Allow transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**

	- Who can record an event: **Organizer can record**

6. Select **Save**.

7. Back on the **Live events policies** page, use the checkbox left of **Management Live Events** and select **Manage users** from the top pane to assign the new policy to users.

8. In the right-side pane, type into the search field **Megan Bowen** and Add right from her name.

9. Select **Apply** to assign the policy to the selected user.

You have successfully created a custom Live event policy and assigned it to a user.

#### Task 5 – Create a new live event 

Contoso Ltd. Wants to broadcast video and meeting content to large online audiences using Teams live events. As a Teams admin, you need to demonstrate the functionality of live meetings to Management.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. Open the Teams Desktop client from the taskbar, where you are still signed in as **Megan Bowen**.

3. On the left navigation pane select **Calendar**.

4. In the top right select the arrow next to **new meeting** and select **live event** in the dropdown menu.

5. Create a new **live event**:

	- Title: Management Showcase

	- Start/End: Select a time close to your current time 

6. Select **Next**.

7. Under **Live event permissions** select **Org-Wide**.

8. Under **How will you produce your live event?** Select **Teams**.

9. Select **Schedule**.

10. On the next page select **Get attendee link** and send it in a chat message to Joni Sherman.

11. On the left navigation pane select **Calendar**.

12. Select the **live event** named **Management Showcase**.

13. In the information window select **Join** to join the meeting.

14. In the meeting preparation window select **Join now**.

15. In the bottom pane of the meeting select **Share** and select your Desktop to share.

16. In the bottom pane of the live event select **My desktop**.

17. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

18. In the **Microsoft Teams client** sign in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

19. On the left navigation pane select **Chat**.

20. Select the link sent to you by Megan Bowen to join the live event.

21. Switch back to **Client 2 VM** and select **Send live** as Megan Bowen.

22. Select **Start** to start the live event.

23. In the **Are you sure you want to start the live event now?** Window select **Continue**.

24. Switch back to **Client 1 VM** and wait for the live event to start.

25. Switch to **Client 2 VM** and select **End**.

26. In the **End live event now?** Window select **End live event**.

You have successfully created a live event and shared content with your attendees.



### **Exercise 2: Deploy Teams device profiles**

As a Teams administrator, you will create configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices.

Your organization could purchase Microsoft Teams Rooms that provide complete meeting experience with HD video, audio, and content sharing in conference rooms. You will need to prepare the deployment prerequisites by define Microsoft Teams Rooms service account in Office 365.

#### Task 1 - Create configuration profiles

During the planning phase of Teams Phones devices in your organization, you want to evaluate settings that can be applied to Teams devices by using configuration profiles in Teams admin center. You will create configuration profile for Teams device and analyze settings that will include in the configuration profile. Once devices are deployed into your organization, you will be ready to apply configuration profiles to those devices.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Teams admin center** at [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/).

3. On the **Pick an account** page, select the **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. In **Teams admin center**, on the left navigation pane, select **Devices**, and then choose **IP Phones**.

5. On the **IP Phones** page, select **Configuration profiles** tab, and then select **Add**.

6. Enter the following information for the new configuration profile:

	- Configuration profile Name: **New York Teams Desk Phones**

	- Description: **Configuration profile for Teams Desk Phones in New York HQ**

7. Under **General** section, configure following settings:

	- Device lock: **On**

	- Timeout: **30 seconds**

	- PIN: **123456**

	- Language: English **(United States)**

	- Timezone: **(UTC-5:00) Eastern Time (US and Canada)**

	- Date format: **MM/DD/YYYY**

	- Time format: **12 Hours (AM/PM)**

8. Under **Device settings** configure following settings:

	- Display screen saver: **On, Timeout 1 minute**

	- Display high contrast: **On**

	- Office hours: **08:00-17:00**

	- Power Saving: **On**

9. Under **Network settings**, configure following settings:

	- DHCP enabled: **On**

	- Logging enabled: **Off**

	- Device’s default admin password: **Pass@word1**

10. Once you complete with the configuration profile settings, select **Save**.

In this task, you have successfully created a configuration profiles that can be applied to Microsoft Teams devices.

#### Task 2 - Create a Microsoft Teams Room

Your organization has ordered devices for Microsoft Teams room. In the meantime, you need to ensure that all prerequisites for the equipment installation are being completed. One of the prerequisites for Microsoft Teams Room deployment is adding a device account and assigning Office 365 license for that account. Because you need to use the Exchange Online PowerShell to complete this task, you will first install the new Exchange PowerShell module.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the **User Account Control** window with **Yes**.

4. Enter the following cmdlet to install the Exchange PowerShell v2:

   ```powershell
   Install-Module ExchangeOnlineManagement
   ```
5. Confirm the Untrusted repository message with **y** for yes.

6. Close the elevated PowerShell window.

7. Right-click the Start button and select **Windows PowerShell.**

8. Enter the following cmdlet to connect to Exchnage Online PowerShell:

   ```powershell
   Connect-ExchangeOnline
   ```
9. When you see the **Sign in** window, enter admin@&lt;YourTenant&gt;.onmicrosoft.com and sign in with the credentials provided to you.

10. Create a new room mailbox named **NY-TeamsRoom1** by running the following cmdlet (remember to replace your tenant name):

    ```powershell
    New-Mailbox -Name "NY-TeamsRoom1" -Alias NY-TeamsRoom1 -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID NY-TeamsRoom1@<YourTenant>.onmicrosoft.com -RoomMailboxPassword (ConvertTo-SecureString -String 'pass@word1' -AsPlainText -Force)
    ```
11. Configure the Calendar Processing features for the Teams Room. Read the following description and run the cmdlet at the end:

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
12. Disconnect from Exchage Online and end the established session with the following cmdlet:

    ```powershell
    Disconnect-ExchangeOnline
    ```
13. Confirm the command with **y** for yes.

14. Connect to **Azure AD PowerShell** to configure Teams Room account settings by running the following cmdlets:

    ```powershell
    Connect-AzureAD
    ```
    When you see the Sign in window, type admin@&lt;YourTenant&gt;.onmicrosoft.com and sign in with the credentials provided to you.

15. Disable the password expiration for the Teams Room account **NY-TeamsRoom1** by running the following cmdlet:

    ```powershell
    Get-AzureADUser | Where {$_.DisplayName -eq "NY-TeamsRoom1"} | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```
16. Close the PowerShell window.

17. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 admin center** at [**https://admin.microsoft.com/**](https://admin.microsoft.com/).

18. On the **Pick an account** page, select the **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

19. In the **Microsoft 365 admin center** from the left navigation pane, under **Billing** select **Purchase services**.

20. In the **Search** box on the right, type **Meeting Room** and then hit Enter.

21. In the results page, locate the **Collaboration and communication** section, and under **Microsoft Teams Rooms Standard** tile, select **Details** and then select **Start free trial**.

22. In the **Check out** page, select **Try now**, and in the **order receipt** page, select **Continue**.

23. In the **Microsoft 365 admin center** from the left navigation pane, select **Users**, and then choose **Active Users**.

24. Select the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com account, and then select the **Licenses and Apps** tab.

25. In the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com page, under the **Licenses and Apps** tab, select **Microsoft Teams Rooms Standard** and then select **Save changes**.

26. Close all open windows.

You have successfully created, configured, and licensed a Microsoft Teams Room service account, which is a prerequisite for deploying a Microsoft Teams Room system.
