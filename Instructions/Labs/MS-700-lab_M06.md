--- 
lab: 
    title: 'Lab: Manage communication in Microsoft Teams '
    type: 'Answer Key' 
    module: 'Module 06: Manage communication in Microsoft Teams' 
---

# Lab 06: - Manage communication in Microsoft Teams
# Student lab manual
## Microsoft 365 user interface 

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual. 

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## Lab Scenario  
In the labs of this course you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. According to Contoso business requirements, Microsoft Teams will be used as an organization's solution for conferencing and telephony. Therefore, Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide best user experience during collaboration and communication. Furthermore, Teams admins will need to replace Contoso legacy PBX solution and configure voice features that will provide users with Teams calling capabilities. 

## Objectives

After you complete this lab, you will be able to:

- Manage meeting policies
- Configure meeting settings
- Create live event policies
- Configure emergency addresses
- Create calling policies
- Configure resource accounts and calling queues
- Create resource accounts and auto attendants
- Test configured meeting policies
- Test configured meeting settings

## Lab Setup  

- **Estimated Time:** 90 minutes.
 
## Instructions



### Exercise 1: Manage Live event and meetings experiences

Contoso organization has deployed Microsoft 365 and is testing pilot projects on collaboration and communication scenarios to meet business requirements. First, Teams admin needs to configure meeting policies and schedule initial meetings. Furthermore, business managers want to test the Live meetings option in Microsoft Teams in order to broadcast audio and video to large audiences.


#### Task 1 - Edit the default meeting policy and restrict all recording features for meetings.

As part of your pilot project for setting up the events and meetings in your organization, you need to fulfil the requirement for all meetings in teams, including prohibiting meeting recording. You will edit the default meeting policy to ensure that this requirement is met.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. In Microsoft Edge, sign in to **Microsoft Teams admin center** (https://admin.teams.microsoft.com) as user **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com**.

3. In the **Teams admin center,** under **Meetings** section, choose **Meeting policies**.

4. Edit the **Global (Org-wide default)** policy review the available settings, and turn **Off** the **Allow cloud recording** setting.

You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time till the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.


#### Task 2 - Configure meeting settings and restrict anonymous users from joining meetings.

Contoso Ltd. works with several external partners and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, under **Meetings** section, choose **Meetings settings**.

4. On the **Meetings settings** page, below participants, turn **Off** the option **Anonymous users can join a meeting**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time till the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.


#### Task 3 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to management users. Only the organizer of a live event should be able to record his own meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, under **Meetings** section, choose **Live event policies**.

4. Create a new **Live event policy** with the following configuration:

	- Add live events policy: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers.**

	- Allow scheduling: **On**

	- Allow transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**
	
	- Who can record an event: **Organizer can record**

5. Assign the new policy to a user **Megan Bowen**.

You have successfully created a custom Live event policy and assigned it to a user.



### Exercise 2: Manage phone system for Microsoft Teams

Contoso organization is using legacy PBX system. With introduction of Microsoft Teams, Contoso will migrate their legacy telephony system to Microsoft Phone System. Teams admins are responsible for evaluating and testing Microsoft Teams voice functionalities.


#### Task 1 - Add a new emergency address

In this task you will add a new emergency address "One Microsoft Way, Redmond, WA 98052, USA" for users in the United States. It is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane under **Locations** section, choose **Emergency addresses**.

4. Create a new emergency address with the following configuration:

	- Put in a name for your location: **Contoso Emergency Address**

	- Add a friendly description so you know why it was created: **Emergency Address for Contoso employees.**

	- Country or region: **United States**

	- Address: **1 Microsoft Way, Redmond, WA 98052**

You have successfully created an emergency address that can be used for phone numbers.


#### Task 2 - Create a new calling policy for management users with voicemail activated. 

As part of your pilot project for calling functionalities with Microsoft Teams, you have the requirement that all pilot users receive access to the voicemail functionalities. You create and assign a new calling policy and configure the settings. However, all other users should not receive voicemail functionalities during the testing period. Therefore, you will edit the default policy to ensure that voicemail is disabled for all other users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, under **Voice** section, choose **Calling policies**.

4. Edit the **Global (Org-wide default)** policy to disable **Voicemail is available for routing inbound calls** option.

5. Create a new policy with the following configuration:

	- Add new calling policy: **Voicemail enabled pilot users**

	- Description: **Calling policy that allows voicemail for selected pilot users.**

	- Voicemail is available for routing inbound calls: **Enabled**

6. Assign the new calling policy **Voicemail enabled pilot users** to users **Megan, Alex, Joni,** and **Lynne**.
 
In this task, you have disabled voicemail for all users in the organizations, and then you have created a calling policy that will enable voicemail for several users.

 
#### Task 3 - Create a new calling queue for Contoso customers

Contoso Ltd. has deployed Microsoft Teams voice functionalities throughout the organization. To deploy some automation for incoming support calls, the calling queue functionalities need to be tested before rolled out. The following settings shall be configured for customers calling in:

- A greeting message.
- Music while people are waiting on hold.
- Redirecting calls to call agents in mail-enabled distribution lists and security groups.

As Teams admin, you are responsible to create the call queue and configure different parameters, such as such as queue maximum size, timeout, and call handling options.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, under **Org-wide settings** section, choose **Resource accounts**, and create a resource account with the following configuration:

	- Display name: **Contoso Call Queue Resource Account**

	- Username: **pilot_callqueue1**

	- Resource Account Type: **Call queue**

4. On the left navigation pane, under **Voice** section, choose **Call queues**, and create a call queue with the following configuration:

	- Call queue name: **Contoso Call Queue**

	- Add accounts: **Contoso Call Queue**

	- Greeting: **Play an audio file C:\\Windows\\Media\\Alarm03.wav**

	- Music on hold: **Play default music**

	- Call answering: **Add groups: Sales**

	- Routing method: **Round robin**

	- Agents can opt out of taking calls: **On**

	- Agent alert time: **30 seconds**

	- Maximum calls in the queue: **50**

	- When the maximum number of calls is reached: **Disconnect**

	- Call time out handling **5 minutes**

	- When call times out: **Disconnect**

 Creating the new call queue may take some time, but you have successfully created a new custom call queue based on a resource account in your tenant.

**Note:** Because this call queue shall have a custom greeting, you need to upload some wav file for demonstration purposes. In real-world scenario, you would record and prepare a greeting audio file and upload the audio file as shown in this task.


#### Task 4 - Create an auto attendant with transcribed greeting message and out of office hours

In your role as Teams admin, you were assigned a task to create an auto attendant with transcribed welcome message that will respond to customers outside of office hours. As some of your employees work in different time zones, the auto attendant informs a caller that the subscriber is currently on vacation and to call another person in the organization. Furthermore, the auto attendant informs callers about business hours.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, under **Org-wide settings**, choose **Resource accounts,** and create resource account with the following configuration:

	- Display name: **Contoso Auto Attendant**

	- Username: **pilot_autoattendant1**

	- Resource Account Type: **Auto attendant** 

4. On the left navigation pane, under **Voice** section, choose **Auto attendants**.

5. Create a new auto attendant with the following configuration:

	- Add a name for your auto attendant: **Contoso Auto attendant**

	- Operator: **Voice app**

	- Search by resource account: **Contoso Call Queue Resource Account**

	- Time zone: **(UTC-08:00) Pacific Time (US \& Canada)**

	- Language: **English (United States)**

	- Enable voice inputs **Off**

6. On the **Call flow** page, configure the following:

	- First play a greeting message: **Type in the greeting message**

	- Type in: **Welcome. The person you called is currently on vacation, your call will be redirected to an operator.**

	- Then route the call: **Redirect call**

	- Redirect to: **Voice app**

	- Search by resource account: **Contoso Call Queue Resource Account**

7. On the **Set business hours** page, configure the following:

	- Select **Clear all hours**

	- Configure working hours **Monday** to **Friday** from **08:00 AM** to **04:00 PM**

	- Leave **Saturday** and **Sunday** blank.

	- First play a greeting message: **Type in a greeting message**

	- Type in: **Thank you for your call, our business hours are Monday to Friday, 08:00 AM to 04:00 PM.**

	- Then route the call **Disconnect**

8. On the **Holiday call settings** page, accept the default settings.

9. On the **Find people** page, accept the default settings.

10. On the **Resource accounts** page, add the **Contoso Auto attendant**, resource account.

You have successfully created a resource account for the auto attendant and afterwards an auto attendant configuration.



### Exercise 3: Test the configured meeting settings

In this exercise you will test the configuration from exercise 1, which required some time till the policies came into effect for the users.


#### Task 1 – Test the meeting policy for restricting recording

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. On the taskbar at the bottom of the page, select the **Edge Browser** icon. Maximize your browser window when it opens.

3. Open the **Microsoft Teams Desktop client**, where you are already signed in as **MeganB@_&lt;YourTenant&gt;_.onmicrosoft.com**.

4. Select **Calendar** from the left navigation pane and **Meet Now** from the upper right corner to start a meeting.

5. On the Microsoft Teams page, leave the default settings and select **Join now** button.

6. On the Microsoft Team page, hover the mouse over the meeting page, and select the three dots (**…**) **(More actions)**.

7. Note that **Start recording** option is visible but is dimmed, not available to be selected.


#### Task 2 - Test meeting settings for restricting anonymous users

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and anonymous users are restricted from joining a meeting.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. On the taskbar at the bottom of the page, select the **Edge Browser** icon. Maximize your browser window when it opens.

3. Open the **Microsoft Teams Desktop client**, where you are already signed in as **MeganB@_&lt;YourTenant&gt;_.onmicrosoft.com**.

4. On the Microsoft Teams page, on the left navigation pane, select **Calendar**, and on the upper right side select **New meeting**.

5. Create a new meeting with title **Contoso Web App Project**, and invite **Joni Sherman** and the Outlook.com address, previously used in Lab 04, that is not from _&lt;YourTenant&gt;_.onmicrosoft.com.

6. On the **New meeting** page, choose the current date and time.

7. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

8. Open an window in your browser and go to the **Microsoft Teams** page: (https://teams.microsoft.com/)

9. On the **Pick an account** page, select **JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com** and sign in.

10. On the left navigation pane, select **Calendar**, select the meeting and then select **Join**. Note that you can join the meeting as user **Joni Sherman**.

11. Open a window in your browser and sign in to your email hosting provider, for example Outlook.com. Read the meeting invite email and select the **Join Microsoft Teams Meeting** link.

12. A message will appear that **Only people with access to this org can join its meetings**.
