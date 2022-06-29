---
lab:
    title: 'Lab 05: Manage Teams meetings experiences'
    type: 'Answer Key'
    module: 'Module 5: Manage meetings and virtual events in Microsoft Teams'
---

# **Lab 05: - Manage Teams meetings experiences**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd., and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide the best user experience during collaboration and communication. 

Furthermore, your organization is planning to purchase and deploy multiple Team devices. You will need to evaluate different devices profiles and configure profile settings for the devices. In the end, you will need to evaluate the process of creating Microsoft Teams room, where multiple Teams’ rooms will be purchased in your organization.

## **Objectives**

After you complete this lab, you will be able to:

- Manage meeting policies

- Configure meeting settings

- Create live event policies

- Create a webinar

- Create configuration profiles for devices

- Configure a new Microsoft Teams Room

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage Live event and meetings experiences**

Contoso organization has deployed Microsoft 365 and is testing pilot projects on collaboration and communication scenarios to meet business requirements. The Teams admin will configure meeting policies and schedule an initial webinar for testing purposes. 

#### Task 1 - Edit the default meeting policy and restrict all recording features for meetings

As part of your pilot project for setting up the events and meetings in your organization, you need to fulfill the requirement for all meetings in Teams, including prohibiting meeting recording. You will edit the default meeting policy to ensure that this requirement is met.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Meetings** > **Meeting policies**.

3. Select the **Global (Org-wide default)** policy.

4. On the **Meetings policies\Global** page, turn **Off** the **Cloud recording** setting under the **Recording &amp; transcription** section. 

5. Select **Save**.

You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 2 – Test the meeting policy for restricting recording

In this task, you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM**  and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Select **Calendar** from the left navigation pane.

3. Select **Meet Now** > **Start meeting** from the upper right corner.

4. Select **Join now** to start the meeting.

5. Close **Invite people to join your window** by selecting **X** on the upper right corner.

6. In the meeting window, select … for **More actions**.

7. Notice that you can't select **Start recording**.

8. End the meeting.
 

#### Task 3 - Configure meeting settings and restrict anonymous users from joining meetings

Contoso Ltd. works with several external partners, and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account, and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Meetings** > **Meetings settings**.

3. On the **Meetings settings** page, turn **Off** the option **Anonymous users can join a meeting** in the participants section.

4. Select **Save**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 4 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to manage users. Only the organizer of a live event should be able to record his meetings.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left navigation of the Teams admin center, select **Meetings** > **Live events policies**.

3. Select **+ Add** from the top menu.

4. On the **Live events policies\Add** page, enter the following information:

	- Add live events policy: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers**

	- Live events scheduling: **On**

	- Transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**

	- Who can record an event: **Organizer can record**

5. Select **Save**.

6. Back on the **Live events policies** page, select **Management Live Events** policy and select **Assign users** from the top menu.

7. In the **Manage users** pane, search and add **Lynne Robbins**.

8. Select **Apply** to assign the policy to the selected user.

You have successfully created a custom Live event policy and assigned it to a user.

#### Task 5 – Create a webinar 

The IT department wants to host a company-wide meeting to answer employees' questions regarding the new reporting system. As a Teams admin, you will create a webinar allowing employees to submit their questions before the meeting. 

1. Connect to the **Client 1 VM** and browse to **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. In the Teams Calendar, select the dropdown menu **New meeting** and select **Webinar**. Scheduling page will open **Teams.Microsoft.com/Scheduling**.

4. Create a new **webinar**:

	- **Title**: IT Office Hours
	- **Start/End**: Select a time close to your current time 
	- **Presenters**: Patti Fernandez, Allan Deyoung

5. Select **View registration form**, it opens a new webpage with the url **Teams.microsoft.com/registration**. Enter the following information: 

	1. **Title**: IT Office Hours
	2. Select **+ Add field** > **Custom question** > **Input**.
	3. Enter the following to the textbox below **Custom question**:

		*What is your question about the new reporting system?*
	
	4. **Start/End**: Select a time close to your current time
	 
	5. Select **Save** and select **Copy registration link**. Preview the invitation by clicking the **View in browser** and closing the page.
	6. Go back to the **Teams.Microsoft.com/scheduling** window and click **Send** button to activate the Webinar registration.
	7. Click **Teams** on the left navigation pane, Select **General** under the **IT-Support**. Click the **New Conversation** and paste the copied registration link in the new conversation text box and click send.
	8. Sign out and close all browser windows.
		
6. Test the meeting registration. 

	1. Stay in the **Client 1 VM** and browse to **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **MOD Administrator**.

	2. Go to the **General** channel of the **IT Support** team and select the registration link that you posted.

	3. Fill out the registration form using <Your outlook account> and select **Register now**.

	4. Go to **Outlook Web Portal** (https://outlook.live.com/owa/), and check the email with subject **You're registered for IT Office Hours**
	
	5. Sign out and close all browser windows.

You have successfully created a webinar with a custom registration form.

### **Exercise 2: Deploy Teams device profiles**

As a Teams administrator, you will create configuration profiles to manage settings and features for Teams devices in your organization. You can create or upload configuration profiles to include settings and features you want to enable or disable and then assign a profile to a device or groups of devices.

Your organization could purchase Microsoft Teams Rooms that provide a complete meeting experience with HD video, audio, and content sharing in conference rooms. You will need to prepare the deployment prerequisites by defining Microsoft Teams Rooms service account in Office 365.

#### Task 1 - Create configuration profiles

During the planning phase of Teams Phones devices in your organization, you want to evaluate settings that can be applied to Teams devices by using configuration profiles in Teams admin center. You will create a configuration profile for Teams device and analyze settings that will include in the configuration profile. Once devices are deployed into your organization, you will be ready to apply configuration profiles to those devices.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as the Teams device administrator - **Patti Fernandez**  (PattiF@&lt;YourTenant&gt;.onmicrosoft.com).

2. In **Teams admin center**, on the left navigation pane, select **Phones** under **Teams devices**.

3. On the **Phones** page, select **Configuration profiles** tab, and then select **+ Add**.

4. Enter the following information for the new configuration profile:

	- Configuration profile Name: **New York Teams Desk Phones**

	- Description: **Configuration profile for Teams Desk Phones in New York HQ**

5. Under **General** section, configure following settings:

	- Device lock: **On**

	- Timeout: **30 seconds**

	- PIN: **123456**

	- Language: English **(United States)**

	- Timezone: **(UTC-5:00) Eastern Time (US and Canada)**

	- Date format: **MM/DD/YYYY**

	- Time format: **12 Hours (AM/PM)**

6. Under **Device settings** configure following settings:

	- Display screen saver: **On, Timeout 1 minute**

	- Display high contrast: **On**

	- Office hours: **08:00-17:00**

	- Power Saving: **On**

7. Under **Network settings**, configure following settings:

	- DHCP enabled: **On**

	- Logging enabled: **Off**

	- Device’s default admin password: **Pass@word1**

8. Once you complete with the configuration profile settings, select **Save**.

9. Sign out and close all browser windows.

In this task, you have successfully created a configuration profile that can be applied to Microsoft Teams devices.

#### Task 2 - Create a Microsoft Teams Room

Your organization has ordered devices for Microsoft Teams room. In the meantime, you need to ensure that all prerequisites for the equipment installation are being completed. One of the prerequisites for Microsoft Teams Room deployment is adding a device account and assigning Office 365 license for that account. 

**Note:** You may choose to use the Exchange Online PowerShell to complete this task, however, you will need to first install the new Exchange PowerShell module.


1. Connect to the **Client 1 VM** and browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.

2. Create a Microsoft 365 resource account for Teams Rooms.
	1. In left navigation of the Microsoft 365 admin center, select **Show all** > **Resources** > **Rooms & equipment**. If you don't find **Resources**, search for **Rooms & equipment** from the top search bar and select.

	2. On the Rooms & equipment screen, select the **+ Add resource** option to add a new resource account. 

	3. On the **Add resource** page, follow the wizard with the following information. 

		* Resource type: **Room**.
		* Name: **NY-TeamsRoom1** 
		* Email: Enter **NY-TeamsRoom1** inside the Email text box and verify your tenant id in the domains

	4. Select **Save**.
	5. Select **Edit booking options**, keep the default settings with the following checked.

		* Allow repeating meetings
		* Automatically decline meetings outside of the limits
		* auto-accept meeting requests
	
3. Get Microsoft Teams Rooms Standard trial licenses

	1. In the **Microsoft 365 admin center** from the left navigation pane, under **Billing** select **Purchase services**.

	2. In the **Search** box on the right, type **Meeting Room** and then hit Enter.

	3. In the results page, locate the **Collaboration and communication** section, and under **Microsoft Teams Rooms Standard** tile, select **Details** and then select **Start free trial**.

	4. In the **Check out** page, select **Try now**, and in the **order receipt** page, select **Continue**.

4. Assign the license to the Teams Rooms account.

	1. In the **Microsoft 365 admin center** from the left navigation pane, select **Users**, and then choose **Active Users**.

	2. Select the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com account, and then select the **Licenses and Apps** tab.

	3. In the NY-TeamsRoom1@&lt;YourTenant&gt;.onmicrosoft.com page, under the **Licenses and Apps** tab, select **Microsoft Teams Rooms Standard** and then select **Save changes**.

5. Sign out and close all open windows.

You have successfully created, configured, and licensed a Microsoft Teams Room service account, which is a prerequisite for deploying a Microsoft Teams Room system.

END OF LAB
