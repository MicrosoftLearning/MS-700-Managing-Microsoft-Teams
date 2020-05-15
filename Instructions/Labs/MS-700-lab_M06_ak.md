--- 
lab: 
    title: 'Lab: Manage communication in Microsoft Teams'
    type: 'Answer Key' 
    module: 'Module 06: Manage communication in Microsoft Teams' 
---

# Lab 06: - Manage communication in Microsoft Teams
# Student lab answer key
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

2. Open Microsoft Edge, maximize the window and navigate to [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com) to access the **Microsoft Teams admin center**. 

3. In the **Pick an account** box, select **JoniS@_YourTenant_.onmicrosoft.com** and sign in with the provided credentials.

4. If a **Stay signed in?** dialog box is displayed, select the **Don’t show this again** checkbox and **Yes**.

5. In the **Teams admin center,** on the left navigation pane, select **Meetings,** and then choose **Meeting policies**.

6. Select the **Global (Org-wide default)** policy to change the settings for all users.

7. On the **Meetings policies\\Global** page, review the available settings, and under **Audio &amp; Video** section, use the slider to turn **Off** the **Allow cloud recording** setting. Select **Save**.

 
You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.


#### Task 2 - Configure meeting settings and restrict anonymous users from joining meetings.

Contoso Ltd. works with several external partners and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, select **Meetings,** and then choose **Meetings settings**.

4. On the **Meetings settings** page, below participants, use the slider to turn **Off** the option **Anonymous users can join a meeting**.

5. Select **Save**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.


#### Task 3 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to management users. Only the organizer of a live event should be able to record his own meetings.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, select **Meetings** and then select **Live event policies**.

4. Select **+ Add** from the top pane, to create a new **Live event policy** with individual settings for assigned users.

5. On **Live event policies\\Add** page, enter the following information:

	- Add live events policy: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers**

	- Allow scheduling: **On**

	- Allow transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**

	- Who can record an event: **Organizer can record**

6. Select **Save**.

7. Back on the **Live events policies** page, use the checkbox left of **Management Live Events** and select **Manage users** from the top pane, to assign the new policy to users.

8. In the right-side pane, type into the search field **Megan Bowen** and Add right from her name.

9. Select **Apply** to assign the policy to the selected user.

You have successfully created a custom Live event policy and assigned it to a user.


### Exercise 2: Manage phone system for Microsoft Teams

Contoso organization is using legacy PBX system. With introduction of Microsoft Teams, Contoso will migrate their legacy telephony system to Microsoft Phone System. Teams admins are responsible for evaluating and testing Microsoft Teams voice functionalities.


#### Task 1 - Add a new emergency address

In this task you will add a new emergency address "One Microsoft Way, Redmond, WA 98052, USA" for users in the United States. It is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane select **Locations** and below select **Emergency addresses**.

4. Select **+ Add** from the top pane to create a new emergency address.

5. On the **Location\\Add location** page, enter the following information:

	- Put in a name for your location: **Contoso Emergency Address**

	- Add a friendly description so you know why it was created: **Emergency Address for Contoso employees.**

	- Country or region: **United States**
	
	- Address: **1 Microsoft Way, Redmond, WA 98052**

6. Select **Save**.

You have successfully created an emergency address that can be used for phone numbers.


#### Task 2 - Create a new calling policy for management users with voicemail activated. 

As part of your pilot project for calling functionalities with Microsoft Teams, you have the requirement that all pilot users receive access to the voicemail functionalities. You create and assign a new calling policy and configure the settings. However, all other users should not receive voicemail functionalities during the testing period. Therefore, you will edit the default policy to ensure that voicemail is disabled for all other users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, select **Voice**, and then **Calling policies** below.

4. Select the **Global (Org-wide default)** policy to edit the default settings.

5. In **Calling policies\\Global**, use the dropdown menu right to **Voicemail is available for routing inbound calls** and select **Disabled**. Then select **Save**.

6. Back on the **Calling policies** page, select **+ Add** on the top pane, to create a new policy.

7. Enter the following information:

	- Add new calling policy: **Voicemail enabled pilot users**

	- Description: **Calling policy that allows voicemail for selected pilot users**.

	- Voicemail is available for routing inbound calls: **Enabled**

8. Select **Save** to create the new policy.

9. Back on the **Calling policies** page, use the checkbox left to the **Voicemail enabled pilot users** policy and then select **Manage users** from the top pane.

10. In the right-side pane, type into the search field **Megan, Alex, Joni, Lynne** and **Add** right from their names.

11. Select **Apply** to assign the policy to the selected users.

In this task, you have disabled voicemail for all users in the organizations, and then you have created a calling policy that will enable voicemail for several users.
 

#### Task 3 - Create a new calling queue for Contoso customers

Contoso Ltd. has deployed Microsoft Teams voice functionalities throughout the organization. To deploy some automation for incoming support calls, the calling queue functionalities need to be tested before rolled out. The following settings shall be configured for customers calling in:

- A greeting message.
- Music while people are waiting on hold.
- Redirecting calls to call agents in mail-enabled distribution lists and security groups.

As Teams admin, you are responsible to create the call queue and configure different parameters, such as such as queue maximum size, timeout, and call handling options.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, select **Org-wide settings**, and then choose **Resource accounts,** to create a resource account.

4. On the **Resource accounts** page, select **+ Add** from the top pane.

5. On the right pane, enter the following information:

	- Display name: **Contoso Call Queue Resource Account**

	- Username: **pilot_callqueue1**

	- Resource Account Type: **Call queue**

6. Select **Save**.

7. On the left navigation pane, select **Voice** and **Call queues**, to create a call queue. 

8. Select **+ Add** from the top pane.

9. Enter the following information:

	- Call queue name: **Contoso Call Queue**

	- You haven't added any resource accounts yet: Select **Add accounts**. On the right-side pane, search for **Contoso**, select **Add** from **Contoso Call Queue**, and then select **Add**.

	- Greeting: select **Play an audio file**, and then select **Upload file**

	- In **Open** window, navigate to **C:\\Windows\\Media**, select **Alarm03.wav** and select **Open**.

	- Music on hold: **Play default music**

	- Call answering: Select **Add groups** and on the right-side pane, search for **Sales**, select **Add** for **Sales** and select **Add** at the bottom of the **Add call agents** pane.

	- Routing method: **Round robin**

	- Agents can opt out of taking calls: **On**

	- Agent alert time: **30 seconds**

	- Maximum calls in the queue: **50**

	- When the maximum number of calls is reached: **Disconnect**

	- Call time out handling: **5 minutes**

	- When call times out: **Disconnect**

10. Select **Save** to create the new call queue.

Creating the new call queue may take some time, but you have successfully created a new custom call queue based on a resource account in your tenant.

**Note:** Because this call queue shall have a custom greeting, you need to upload some wav file for demonstration purposes. In real-world scenario, you would record and prepare a greeting audio file and upload the audio file as shown in this task.

 
#### Task 4 - Create an auto attendant with transcribed greeting message and out of office hours

In your role as Teams admin, you were assigned a task to create an auto attendant with transcribed welcome message that will respond to customers outside of office hours. As some of your employees work in different time zones, the auto attendant informs a caller that the subscriber is currently on vacation and to call another person in the organization. Furthermore, the auto attendant informs callers about business hours.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be signed in as **JoniS@_YourTenant_.onmicrosoft.com** and you are in the **Teams admin center**.

3. On the left navigation pane, select **Org-wide settings**, and then choose **Resource accounts,** to create resource account first.

4. On the **Resource accounts** page, select **+ Add** from the top pane.

5. On the right pane, enter the following information:

	- Display name: **Contoso Auto Attendant**

	- Username: **pilot_autoattendant1**

	- Resource Account Type: **Auto attendant**

6. Select **Save**.

7. On the left navigation pane, select **Voice** and **Auto attendants** below.

8. Select **+ Add** from the top pane, to create a new auto attendant.

9. Enter the following information:

	- Add a name for your auto attendant: **Contoso Auto attendant**

	- Operator: **Voice app**

	- Search by resource account: **Contoso Call Queue Resource Account**

	- Time zone: **(UTC-08:00) Pacific Time (US \& Canada)**

	- Language: **English (United States)**

	- Enable voice inputs: **Off**

10. Select **Next**.

11. On the **Call flow** page, configure the following:

	- First play a greeting message: **Type in the greeting message**

	- Type in : **Welcome. The person you called is currently on vacation, your call will be redirected to an operator.**

	- Then route the call: **Redirect call**

	- Redirect to: **Voice app**

	- Search by resource account: **Contoso Call Queue Resource Account**

12. Select **Next**.

13. On the **Set business hours** page, configure the following:

	- Select **Clear all hours**

	- Configure working hours **Monday** to **Friday** from **08:00 AM** to **04:00 PM**

	- Leave **Saturday** and **Sunday** blank.

	- First play a greeting message: **Type in a greeting message**

	- Type in: **Thank you for your call, our business hours are Monday to Friday, 08:00 AM to 04:00 PM.**

	- Then route the call: **Disconnect**

14. Select **Next**.

15. On the **Holiday call settings** page, select **Next**.

16. On the **Find people** page, select **Next**.

17. On the **Resource accounts** page, select **Add accounts**. In the right-side pane, type **Contoso auto attendant**, and then select **Add** twice.

18. Select **Submit** to finish the creation of the auto attendant.

You have successfully created a resource account for the auto attendant and afterwards an auto attendant configuration.



### Exercise 3: Test the configured meeting settings

In this exercise you will test the configuration from exercise 1, which required some time till the policies came into effect for the users.


#### Task 1 – Test the meeting policy for restricting recording

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. On the taskbar at the bottom of the page, select the **Edge Browser** icon. Maximize your browser window when it opens.

3. Open the **Microsoft Teams Desktop client**, where you are already signed in as **MeganB@_YourTenant_.onmicrosoft.com**.

4. Select **Calendar** from the left navigation pane and **Meet Now** from the upper right corner to start a meeting.

5. On the Microsoft Teams page, leave the default settings and select **Join now** button.

6. On the Microsoft Team page, hover the mouse over the meeting page, and select the three dots (…) for **More actions**.

7. Note that **Start recording** option is visible but is dimmed, not available to be selected.


#### Task 2 - Test meeting settings for restricting anonymous users

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and anonymous users are restricted from joining a meeting.

1. Connect to the **Client 2 VM** and sign in with the Credentials that have been provided to you.

2. Open the **Microsoft Teams Desktop client**, where you are already signed in as **MeganB@_YourTenant_.onmicrosoft.com**.

3. On the Microsoft Teams page, on the left navigation pane, select **Calendar**, and on the upper right side select **+ New meeting**.

4. On the **New meeting** page, in the **Title** field, type **Contoso Web App Project**, and in the invite people, type **Joni Sherman** and your outlook.com address, previously used in Lab 04, that is not from _YourTenant_.onmicrosoft.com.

5. On the **New meeting** page, choose the current date and time and then select **Send**.

6. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

7. Open an window in your browser and go to the **Microsoft Teams** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

8. On the **Pick an account** page, select **JoniS@_YourTenant_.onmicrosoft.com** and sign in.

9. On the left navigation pane, select **Calendar,** select the meeting and then select **Join**. Note that you can join the meeting as user **Joni Sherman**.

10. Open a **New InPrivate window** in your browser and sign in to your ***outlook.com email***. Read the meeting invite email and select the **Join Microsoft Teams Meeting** link.

11. A message will appear that **Only people with access to this org can join its meetings**.

12. Sign out and close all windows.
