---
lab:
  title: 'Lab 04: - Manage Teams meetings and calling experiences'
  description: In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd., and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide the best user experience during collaboration and communication.
  duration: 180 minutes
  level: 100-200
  islab: true
  primarytopics:
    - Microsoft Teams
---

# **Lab 04: - Manage Teams meetings and calling experiences**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd., and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide the best user experience during collaboration and communication.

Your organization is also planning to purchase and deploy multiple Team devices. You will need to evaluate different devices profiles and configure profile settings for the devices and the process of creating Microsoft Teams room, where multiple Teams’ rooms will be purchased in your organization. 

Furthermore, you will replace Contoso legacy PBX solution and configure voice features that will provide users with Teams calling capabilities.

## **Objectives**

After you complete this lab, you will be able to:

- Manage meeting policies

- Configure meeting settings

- Create live event policies

- Create a webinar

- Create configuration profiles for devices

- Configure a new Microsoft Teams Room

- Set up a Calling Plan

- Order and Assign phone numbers

- Configure emergency addresses

- Create calling policies

- Configure resource accounts and calling queues

- Create resource accounts and auto attendants

- Access and navigate through call analytics ad CQD dashoards

## **Lab Setup**

- **Estimated Time:** 180 minutes.

## **Instructions**

### **Exercise 1: Manage Live event and meetings experiences**

Contoso organization has deployed Microsoft 365 and is testing pilot projects on collaboration and communication scenarios to meet business requirements. The Teams admin will configure meeting policies and schedule an initial webinar for testing purposes.

#### Task 1 - Edit the default meeting policy and restrict all recording features for meetings

As part of your pilot project for setting up the events and meetings in your organization, you need to fulfill the requirement for all meetings in Teams, including prohibiting meeting recording. You will edit the default meeting policy to ensure that this requirement is met.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left-hand navigation pane of the Teams admin center, select **Meetings** > **Meeting policies**.

3. On the **Manage policies** tab, select **Global (Org-wide default)**.

4. Turn **Off** the **Meeting recording** setting under the **Recording & transcription** section.

5. Select **Save** and **Confirm**.

You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 2 – Test the meeting policy for restricting recording

In this task, you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM** and browse to **Microsoft Teams web client** (https://teams.microsoft.com) as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Select **Calendar** from the left navigation pane.

3. In the upper-right corner, select **Meet now**, and then in the **Start a meeting now** dialog, select **Start meeting**.

4. Select **Join now** to start the meeting.

5. If prompted, select **X** to close the **Invite people to join you** window.

6. In the meeting window, select **More**.

7. Select **Record and transcribe**, and then confirm that **Start recording** is unavailable.

8. Select **Leave** to end the meeting.

#### Task 3 - Configure meeting settings and restrict anonymous users from joining meetings

Contoso Ltd. works with several external partners, and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account, and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation pane of the Teams admin center, select **Meetings** > **Meeting settings**.

3. On the **Meetings settings** page, turn **Off** the option **Anonymous users can join a meeting** in the participants section.

4. Select **Save** and **Confirm**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 4 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to manage users. Only the organizer of a live event should be able to record his meetings.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation pane of the Teams admin center, select **Meetings** > **Live events policies**.

3. Select **+Add** under **Manage Policies** tab.

4. On the **Live events policies\Add** page, enter the following information:

	- Name: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers**

	- Live events scheduling: **On**

	- Transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**

	- Record an event: **Organizer can record**

5. Select **Save**.

6. Back on the **Live events policies** page, select the **Management Live Events** policy, and then select **Manage Users** > **Assign users** from the top menu.

7. In the **Manage users** pane, search and add **Lynne Robbins**.

8. Select **Apply**, and then select **Confirm** to assign the policy to the selected user.

You have successfully created a custom Live event policy and assigned it to a user.

#### Task 5 – Create a webinar

The IT department wants to host a company-wide meeting to answer employees’ questions regarding the new reporting system. As a Teams admin, you will create a webinar allowing employees to submit their questions before the meeting.

1. Connect to the **Client 1 VM** and browse to **Microsoft Teams web client** (https://teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the **Calendar**, select the **New** dropdown, and then under **Organization templates**, select **Webinar**.

3. On the **Details** page, enter the following information and then select **Save and send invites**:

	- **Title**: IT Office Hours
	- **Start date/End date**: Select a time close to your current time 
	- **Description**: Company-wide meeting to answer questions regarding the new reporting system.
	- **Presenters from your org**: Search for and add **Patti Fernandez** and **Allan Deyoung**
	- **Co-organizers**: Search for and add **Diego Siciliani**
	- **Event access**: Your organization

	> [!NOTE]
    > When you save the event, Teams sends invites to presenters and co-organizers automatically.

4. In the top navigation bar, select **Meeting options** and review the available settings. If prompted, select **Save** first.

5. In the left navigation pane, under **Registration**, select **Configuration**. Enter the following information and then select **Save**:

    - **Event capacity**: 1000
    - In the **Form** section, select **+ Add field** > **Custom question** > **Text input** and enter the following in the **Custom question** textbox:

        `What is your question about the new reporting system?`
		 

6. In the upper-right corner, select **View draft** to preview the registration site. The registration page preview opens in a new tab. If prompted, select **Sign in with your school or work account** and select the **Joni Sherman** account. Review the site and then close the tab.

7. Publish the Registration site and share the link:

	1. On the **IT Office Hours | Microsoft Teams** tab, select **Publish site** and then select **Publish** to activate the Webinar registration site.

	2. Copy the **Share link**, and then close the **All set and ready to share** dialog.

	3. In the left navigation pane, select **Chat**. Under **Teams and channels**, expand **IT-Department** and select the **General** channel.
	
	4. Select **Post in channel**, paste the copied registration link in the text box, and then select **Post**.

	5. Sign out and close all browser windows.
		
8. Test the meeting registration. 

	1. Stay in the **Client 1 VM** and browse to **Microsoft Teams web client** (https://teams.microsoft.com/) as **MOD Administrator**.

	2. In the **General** channel of the **IT-Department** team, select the registration link posted earlier.

	3. On the registration page select **Register**.
	
	4. Verify that the MOD Administrator's name and email are populated, select the **I have read and agree to the Microsoft Event Terms and Conditions** check box, and then select **Register**.

	5. Open a new browser tab and browse to **Outlook** (https://outlook.office.com/mail/) as **MOD Administrator**. Verify that an email with the subject **You're registered for IT Office Hours** appears in the inbox.
	
	5. Sign out and close all browser windows.


You have successfully created a webinar with a custom registration form.

### **Exercise 2: Deploy Teams device profiles**

As a Teams administrator, you will create configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable, and then assign a profile to a device or groups of devices.

Your organization could purchase Microsoft Teams Rooms that provide a complete meeting experience with HD video, audio, and content sharing in conference rooms. You will need to prepare the deployment prerequisites by defining Microsoft Teams Rooms service account in Office 365.

#### Task 1 - Create configuration profiles

During the planning phase of Teams Phones devices in your organization, you want to evaluate settings that can be applied to Teams devices by using configuration profiles in Teams admin center. You will create a configuration profile for Teams device and analyze settings that will include in the configuration profile. Once devices are deployed into your organization, you will be ready to apply configuration profiles to those devices.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com) as the Teams device administrator - **Patti Fernandez** (PattiF@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the **Teams admin center**, on the left navigation pane, under **Teams devices**, select **Phones**.

3. On the **Phones** page, select **Configuration profiles** tab, and then select **+ Add**.

4. Enter the following information for the new configuration profile:

	- Configuration profile Name: **New York Teams Desk Phones**

	- Description: **Configuration profile for Teams Desk Phones in New York HQ**

5. Under the **General** section, configure the following settings:

	- Set device lock: **On**

	- Timeout: **30 seconds**

	- Device lock PIN: **123456**

	- Language: English **(United States)**

	- Timezone: **(UTC-5:00) Eastern Time (US & Canada)**

	- Date format: **MM/DD/YYYY**

	- Time format: **12 Hours (AM/PM)**

6. Under **Device settings**, configure the following settings:

	- Display screen saver: **On (Recommended)**

	- Display screen saver Timeout: **1 minute**

	- Display high contrast: **On**

	- Office hours: **Set Office Hours**, start time **08:00**, end time **17:00**

	- Power Saving: **On**

7. Under **Network settings**, configure the following settings:

	- DHCP enabled: **On**

	- Logging enabled: **Off**

	- Device's admin password: **Set Device admin password**, enter `Pass@word1`

8. Select **Review changes**.

9. Review the configured settings and select **Save changes**.

10. Sign out and close all browser windows.

You have sucessfully created a configuration profile that can be applied to Microsoft Teams devices.

#### Task 2 - Configure a resource account for Teams Room

Your organization has ordered devices for Microsoft Teams room. In the meantime, you need to ensure that all prerequisites for the equipment installation are being completed. One of the prerequisites for Microsoft Teams Room deployment is adding a device account and assigning Office 365 license for that account.

> [!NOTE]
> You can also use Exchange Online PowerShell to complete this task. You need to install the Exchange Online PowerShell module first.

1. Connect to the **Client 1 VM** and browse to **Microsoft 365 admin center** (https://admin.microsoft.com/) as **MOD Administrator**.

2. Create a Microsoft 365 resource account for Teams Rooms.
	1. In the left navigation pane of the Microsoft 365 admin center, select **Show all** > **Resources** > **Rooms & equipment**. If **Resources** is not visible, in the top search bar, search for `Rooms & equipment` and select the result.

	2. On the **Rooms & equipment** page, select **+ Add resource**.

	3. In the **Add resource** pane, select and enter the following information: 

		* Resource type: **Room**
		* Name: **NY-TeamsRoom1** 
		* Email: enter **NY-TeamsRoom1** and verify your tenant domain is selected in the **Domains** dropdown

	4. Select **Save**.
	
	5. Select **Edit booking options**, verify the following options are selected, and then select **Save changes**:

        * **Allow repeating meetings**
        * **Automatically decline meetings outside of the limits**
        * **Auto-accept meeting requests**

3. Assign the license to the Teams Rooms account.

	1. In the left navigation pane of the **Microsoft 365 admin center**, select **Users** > **Active users**.

	2. Select the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com account, and then select the **Licenses and Apps** tab.

	3. In the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com page, under the **Licenses and Apps** tab, select **Microsoft Teams Rooms Pro** and then select **Save changes**.

4. Sign out and close all open windows.

You have successfully created, configured, and licensed a Microsoft Teams Room service account, which is a prerequisite for deploying a Microsoft Teams Room system.
 

### **Exercise 3: Set up a Calling Plan (Optional)**

In this exercise, you will set up one of your users with a Calling Plan Trial. You will need to start the trial, order a phone number from Microsoft as your provider and enable your user to use this phone number when making outgoing calls.

> [!NOTE]
> Calling Plan availability varies by country and region. Check the link below to verify availability for your location. These instructions are based on the United States.

[https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans](https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)

#### Task 1 - Add a new emergency address

In this task, you will add a new emergency address “One Microsoft Way, Redmond, WA 98052, USA” for users in the United States. It is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. On the left navigation pane, select **Locations** > **Emergency addresses**.

3. Select **+ Add** from the top pane to create a new emergency address.

4. On the **Emergency addresses\New emergency address** page, enter the following information:

	- Enter a name for your emergency address: **Contoso Emergency Address**

	- Country or region: **United States**

	- Address: **1 Microsoft Way, Redmond, WA 98052**

	> [!NOTE]
    > If the address is not recognized, enable **Input address manually** and enter the address fields individually:
    > - **Street number**: `1`
    > - **Street name**: `Microsoft Way`
    > - **City**: `Redmond`
    > - **State**: Washington
    > - **Zip code**: `98052`
    > - **Latitude**: `47.6394`
    > - **Longitude**: `-122.1282`
    > - **Organization name**: `Contoso`

5. Acknowledge the emergency calling disclaimer. If an information page opens, select **Print** or **Cancel** to dismiss it.

6. Select **Save**.

7. Sign out and close the browser.

You have successfully created an emergency address that can be used for phone numbers.

#### Task 2 – Assign a Calling Plan license to a user

In this task, you will assign the calling plan license to a user to allow them to make domestic calls via the public switched telephone network.

1. Connect to the **Client 1 VM** and browse to **Microsoft 365 admin center** (https://admin.microsoft.com/) as **MOD Administrator** (Admin@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation pane of the **Microsoft 365 admin center**, select **Users** > **Active users**.

3. On the **Active users** page, search for and select **Lynne Robbins**.

4. Select **Licenses and apps**.

5. Under **Licenses**, select the **Microsoft Teams Domestic Calling Plan** checkbox.

6. Select **Save Changes** to assign the license, sign out, and close all browser windows.

You have assigned the Calling Plan license to a user. With this license assigned your users can use the Calling Plan features and receive a phone number.

#### Task 3 – Order a phone number for your user (Instructional steps only - do not complete)

In this task, you will learn how to order a phone number for a user with an assigned Calling Plan license. Please note, that you can no longer order a phone number without a business justification so the set of steps below are meant to educate. Please do not follow these steps within your lab environments. These steps are designed to educate the user on how to execute the task.

1. Connect to the **Client 1 VM** and browse to **Teams admin center** (https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation pane, select **Voice** > **Phone numbers**.

3. On the **Numbers** tab, select **+ Add**.

4. In the **Order Name** field, enter `Phone number order`.

5. In the **Description** field, enter `Number for Lynne Robbins during the Calling Plan trial`.

6. In the **Country or region** dropdown, select **United States**.

7. In the **Verification required** section, select **Provide now**.
   > [!NOTE]
   > Phone number acquisition is blocked until baseline KYC information is provided and all verification steps are completed. In a lab environment, you cannot complete this verification. The remaining steps describe the process after KYC verification is approved.

8. For **Number Type** select **User (Subscriber)**.

9. For the **Operator**, select **Microsoft**.

10. For **Quantity** type **1**.

11. In the **Search for new numbers** section, you can use one of the following approaches to find new numbers:

	- Search by city name

		- Select **Search by city name**.

		- Search **Redmond** and select **Contoso Emergency Address**

		- Select Area code available.

		- Select **Next**.

	- Search by area code

		- Select **Search by area code**.

		- Enter an area code in United States.

		- Select **Next**.

	> [!NOTE]
    > If the following message appears, try a different area code or create another location by selecting **Add a location** next to **Search by city name**. On the **New emergency address** pane, enter a name for the emergency address. In the **Country or region** dropdown, select **United States**. In the **Address** field, enable **Input address manually**, enter the new address, and then select **Save**. The **Get phone numbers** page displays again so you can continue the city search with the new emergency address.
    >
	> **Message**: *We can’t find any phone numbers for the address you selected.*

12. Once you reserved a phone number successfully, you can proceed by selecting **Place order**, then **Finish**.

    > [!NOTE]
    > It may take some time for the phone numbers to appear. You can check the status on the **Order history** tab.

You just ordered a phone number for a User in Microsoft Teams. This is the same process you use to order numbers for all other Microsoft Teams services such as Call Queues.

#### Task 4 – Assign a phone number to your user (Instructional steps only - do not complete)

In this task, you will learn how to assign an existing phone number to a user. Please note, that you can no longer order a phone number without a business justification so the set of steps below are meant to educate. Please do not follow these steps within your lab environments. These steps are designed to educate the user on how to execute the task.

1. Connect to the **Client 1 VM** and browse to the **Teams admin center** (https://admin.teams.microsoft.com) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. On the left navigation pane, select **Voice** > **Phone numbers**.

4. Select the phone number you want to assign, and then select **Edit**.

5. In the **Assigned to** field, search for **Lynne Robbins** and select **Assign**.

6. In the **Emergency Location** field, select **Search by the location description**.

7. Search for `Contoso` to find the emergency location you created earlier.

8. Select **Apply** to assign the phone number to the user.

### **Exercise 4: Manage Teams Phone** 

Contoso organization is using the legacy PBX system. With the introduction of Microsoft Teams, Contoso will migrate their legacy telephony system to Microsoft Teams Phone. Teams admins are responsible for evaluating and testing Microsoft Teams voice functionalities.

#### Task 1 - Create a calling policy

As part of your pilot project for calling functionalities with Microsoft Teams, you have the requirement that all pilot users receive access to the voicemail functionalities. You create and assign a new calling policy and configure the settings. However, all other users should not receive voicemail functionalities during the testing period. Therefore, you will edit the default policy to ensure that voicemail is disabled for all other users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice** > **Calling policies**.

4. On the **Calling policies** page, select **Global (Org-wide default)**.

5. On the **Edit policy details** page, set **Voicemail for inbound calls** to **Off**, and then select **Save** and **Confirm**.

6. On the **Calling policies** page, on the **Manage policies** tab, select **+ Add** to create a new policy.

7. On the **Add policy details** page, enter and select the following information:

    - Name: **Voicemail enabled pilot users**

    - Description: **Calling policy that allows voicemail for selected pilot users**

    - Voicemail for inbound calls: **On**

8. Select **Save** to create the new policy.

9. On the **Calling policies** page, select the checkbox next to **Voicemail enabled pilot users**, and then select **Manage users** > **Assign users**.

10. In the **Manage users** pane, search for `Megan` and select **Add**. Repeat for **Alex**, **Joni**, and **Lynne**.

11. Select **Apply** to assign the policy to the selected users, then select **Confirm**.

You have disabled voicemail for all users in the organization and created a calling policy that enables voicemail for the pilot users.

#### Task 2 - Create a call queue

Contoso Ltd. has deployed Microsoft Teams voice functionalities throughout the organization. To automate incoming support calls, the call queue functionality needs to be tested before rollout. Configure the following settings for incoming callers:

- A greeting message.

- Music while people are waiting on hold.

- Redirecting calls to call agents in mail-enabled distribution lists and security groups.

As Teams admin, you are responsible for creating the call queue and configuring different parameters, such as maximum queue size, timeout, and call handling options.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice** > **Resource accounts**.

4. On the **Resource accounts** page, select **+ Add**.

5. On the **Add resource account** pane, enter and select the following information:

	- Display name: **Contoso Call Queue Resource Account**

	- Username: enter **pilot_callqueue1** and verify your tenant domain is selected in the **Domains** dropdown

	- Resource account Type: **Call queue**

6. Select **Save**.

   > [!NOTE]
   > If the error *You don't have the required permissions to create/manage resource accounts* appears, open the **Microsoft 365 admin center** (https://admin.microsoft.com) as **MOD Administrator**. Select **Users** > **Active users**, and then select **Joni Sherman**. Select **Manage roles**, assign the **User Administrator** role, and then select **Save changes**. Sign out of the Teams admin center and sign back in as **Joni Sherman** before retrying.

7. Download the file **Alarm03.wav** from the following link and save to the Downloads folder.

   [https://github.com/MicrosoftLearning/MS-700-Managing-Microsoft-Teams/blob/master/Instructions/Labs/media/Alarm03.wav](https://github.com/MicrosoftLearning/MS-700-Managing-Microsoft-Teams/blob/master/Instructions/Labs/media/Alarm03.wav)

8. In the **Teams admin center**, on the left navigation pane, select **Voice** > **Call queues**.

9. Select **+ Add**. In the **Set up Call Queue** dialog, select **Classic setup**.

10. On the **Add a call queue** page, enter the following information:

	- Add a name for  your call queue: **Contoso Call Queue Resource Account**

	- Under **Resource accounts**, select **Add**. In the **Add accounts** pane, search for `Contoso`, select **Add** next to **Contoso Call Queue Resource Account**, select **Add** to confirm, and then select **Save**
	
	- Language: **English (United States)**

	- Select **Next**

	- Greeting: select **Play an audio file**, and then select **Upload file**

	- In the **Open** window, navigate to the Downloads folder, select **Alarm03.wav**, and then select **Open**

	- Music on hold: **Play default music**

	- Select **Next**

	- Call answering: Select **Choose users and groups**, then select **Add groups**. In the **Add call agents** pane, search for `Sales`, select **Add** next to **Sales**, and then select **Add** at the bottom of the pane.

	- Select **Next**

	- Routing method: **Round robin**

	- Presence-based routing: **Off**

	- Call agents can opt out of taking calls: **On**

	- Call agent alert time: **30 seconds**
	
	- Select **Next**

	- Enable callback: **Off**

	- Select **Next**

	- Under the **Exception handling** page, expand **Call overflow** and set **Maximum calls in the queue** to **50**.

	- When the maximum number of calls is reached: **Disconnect**

	- Expand **Call timeout** and set **Maximum wait time**: **5 minutes**

	- When call times out: **Disconnect**

11. Select **Submit** to create the new call queue.

Creating the new call queue may take some time, but you have successfully created a new custom call queue based on a resource account in your tenant.

   > [!NOTE]
   > Because this call queue shall have a custom greeting, you need to upload some wav files for demonstration purposes. In a real-world scenario, you would record and prepare a greeting audio file and upload the audio file as shown in this task.

#### Task 3 - Create an auto attendant

As Teams admin, you were tasked to create an auto attendant with a transcribed welcome message that will respond to customers outside of office hours. As some of your employees work in different time zones, the auto-attendant informs a caller that the subscriber is currently on vacation and to call another person in the organization. Furthermore, the auto-attendant informs callers about business hours.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice** > **Resource accounts**.

4. On the **Resource accounts** page, select **+ Add**.

5. On the **Add resource account** pane, enter and select the following information:

	- Display name: **Contoso Auto Attendant**

	- Username: **pilot_autoattendant1** and verify your tenant domain is selected in the **Domains** dropdown

	- Resource account Type: **Auto attendant**

6. Select **Save**.

7. On the left navigation pane, select **Voice** > **Auto attendants**.

8. Select **+ Add**. In the **Set up Auto attendant** dialog, select **Classic setup**.

9. Enter and select the following information:

	- Add a name for your auto attendant: **Contoso Auto attendant**

	- Operator: **Voice app**

	- Search by auto attendant or call : **Contoso Call Queue Resource Account**

	- Time zone: **(UTC-08:00) Pacific Time (US &amp; Canada)**

	- Language: **English (United States)**

	- Enable voice inputs: **Off**

10. Select **Next**.

11. On the **Call flow** page, configure the following:

    - Under **Greeting options**, select **Add a greeting message**

    - In the text box, enter `Welcome. The person you called is currently on vacation, your call will be redirected to an operator.`

    - Under **Call routing options**, select **Redirect call**

    - Redirect to: **Voice app**

    - Search by auto attendant or call queue: **Contoso Call Queue Resource Account**

12. Select **Next**.

13. On the **After-hours call flow** page, configure the following:

    - Under **Set business hours**, set **Monday** to **Friday** from **08:00 AM** to **04:00 PM**

    - Leave **Saturday** and **Sunday** unchecked

    - Under **Greeting options**, select **Add a greeting message**

    - In the text box, enter `Thank you for your call, our business hours are Monday to Friday, 08:00 AM to 04:00 PM.`

    - Under **Call routing options**, select **Disconnect**

14. Select **Next**.

15. On the **Holiday call flow** page, select **Next**.

16. On the **Dial scope** page, select **Next**.

17. On the **Resource accounts** page, select **Add**. In the **Add accounts** pane, search for `Contoso Auto Attendant`, select **Add** next to **Contoso Auto Attendant**, and then select **Save**.

18. Select **Submit** to finish the creation of the auto attendant.

19. Close all browser windows.

You have successfully created a resource account for the auto attendant and then created an auto attendant configuration.

### **Exercise 5: Explore reports for call quality in Microsoft Teams**

When users experience calling problems, an organization's Teams administrator must quickly diagnose and fix the problems. The Teams client, the network, and any number of configuration issues in the Microsoft Teams admin center can disrupt an organization's users from effectively sending and receiving calls and participating in Teams meetings.

In this exercise, you'll explore the monitoring and troubleshooting tools available in Teams admin center, including call analytics, and the call quality dashboard to investigate voice issues.

> [!NOTE]
> Because no calls have been made in this environment, reports will be blank and incomplete.

#### Task 1 – Explore call analytics for users, calls, and meetings

1. Connect to the **Client 1 VM** and browse to **Teams admin center** ([https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)) as **Joni Sherman** ([JoniS@&lt;YourTenant&gt;.onmicrosoft.com](mailto:JoniS@&lt;YourTenant&gt;.onmicrosoft.com)).

2. In the left navigation pane, select **Users** > **Manage users**, and then select a user.

3. On the user's page, select the **Meetings & calls** tab.

4. The **Meetings & calls** tab displays all calls and meetings for the selected user.

By selecting a session in the list, you can view other information about a given session, including detailed media and networking statistics for call and meeting activities.

#### Task 2 – Explore Call Quality Dashboard (CQD)

CQD is designed to help Microsoft Teams administrators and network engineers monitor call and meeting quality at an organization-wide level. The near real-time data enables Teams admins to quickly resolve issues by drilling down to find where issues originated, and who was affected.

In this task you navigate to Call Quality Dashboard

1. Connect to the **Client 1 VM** and browse to **Teams admin center** ([https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/)) as **Joni Sherman** ([JoniS@&lt;YourTenant&gt;.onmicrosoft.com](mailto:JoniS@&lt;YourTenant&gt;.onmicrosoft.com)).

2. In the left navigation pane, select **Analytics & reports** > **Call Quality Dashboard**.

3. A new browser tab opens with the **Call Quality Dashboard** portal ([https://cqd.teams.microsoft.com/](https://cqd.teams.microsoft.com/)). If prompted, sign in with the **Joni Sherman** account.

   > [!NOTE]
   > If an error occurs when the tab opens, enter `https://cqd.teams.microsoft.com/` directly in the browser address bar.

4. The **Call Quality Dashboard** displays summary reports with daily and monthly call quality trends. Call quality is classified as good, poor, or unclassified.

5. In the **Product Filter** dropdown, select **Microsoft Teams**.

6. Review the data under the **Overall Call Quality**, **Server-Client**, **Client-Client**, and **Voice Quality SLA** tabs.

You have successfully accessed and navigated call analytics and the Call Quality Dashboard.

END OF LAB

 
