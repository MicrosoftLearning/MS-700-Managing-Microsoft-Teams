---
lab:
    title: 'Lab 06: Manage communication in Microsoft Teams'
    type: 'Answer Key'
    module: 'Module 6: Manage communication in Microsoft Teams'
---

# **Lab 06: - Manage communication in Microsoft Teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. According to Contoso business requirements, Microsoft Teams will be used as an organization’s solution for conferencing and telephony. Therefore, Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide best user experience during collaboration and communication. Furthermore, Teams admins will need to replace Contoso legacy PBX solution and configure voice features that will provide users with Teams calling capabilities.

## **Objectives**

After you complete this lab, you will be able to:

- Manage meeting policies

- Configure meeting settings

- Create live event policies

- Create a live event

- Configure emergency addresses

- Create calling policies

- Configure resource accounts and calling queues

- Create resource accounts and auto attendants

- Test configured meeting policies

- Test configured meeting settings

- Set up a Calling Plan

- Order and Assign phone numbers

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

### **Exercise 2: Manage phone system for Microsoft Teams**

Contoso organization is using legacy PBX system. With introduction of Microsoft Teams, Contoso will migrate their legacy telephony system to Microsoft Phone System. Teams admins are responsible for evaluating and testing Microsoft Teams voice functionalities.

#### Task 1 - Add a new emergency address

In this task you will add a new emergency address "One Microsoft Way, Redmond, WA 98052, USA" for users in the United States. It is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane select **Locations** and below select **Emergency addresses**.

4. Select **+ Add** from the top pane to create a new emergency address.

5. On the **Location\Add location** page, enter the following information:

	- Put in a name for your location: **Contoso Emergency Address**

	- Add a friendly description so you know why it was created: **Emergency Address for Contoso employees.**

	- Country or region: **United States**

	- Address: **1 Microsoft Way, Redmond, WA 98052** 

      (You can enable **Edit the address manually**, and enter the address manually)

6. Acknowledge the emergency calling disclaimer.

7. Select **Save**.

You have successfully created an emergency address that can be used for phone numbers.

#### Task 2 - Create a calling policy

As part of your pilot project for calling functionalities with Microsoft Teams, you have the requirement that all pilot users receive access to the voicemail functionalities. You create and assign a new calling policy and configure the settings. However, all other users should not receive voicemail functionalities during the testing period. Therefore, you will edit the default policy to ensure that voicemail is disabled for all other users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then **Calling policies** below.

4. Select the **Global (Org-wide default)** policy to edit the default settings.

5. In **Calling policies\Global**, use the dropdown menu right to **Voicemail is available for routing inbound calls** and select **Disabled**. Then select **Save**.

6. Back on the **Calling policies** page, select **+ Add** on the top pane, to create a new policy.

7. Enter the following information:

	- Add new calling policy: **Voicemail enabled pilot users**

	- Description: **Calling policy that allows voicemail for selected pilot users**.

	- Voicemail is available for routing inbound calls: **Enabled**

8. Select **Save** to create the new policy.

9. Back on the **Calling policies** page, use the checkbox left to the **Voicemail enabled pilot users** policy and then select **Manage users** from the top pane.

10. In the right-side pane, type into the search field **Megan, Alex, Joni, Lynne** and select **Add** right from their names.

11. Select **Apply** to assign the policy to the selected users.

In this task, you have disabled voicemail for all users in the organizations, and then you have created a calling policy that will enable voicemail for several users.

#### Task 3 - Create a call queue

Contoso Ltd. has deployed Microsoft Teams voice functionalities throughout the organization. To deploy some automation for incoming support calls, the calling queue functionalities need to be tested before being rolled out. The following settings shall be configured for customers calling in:

1. A greeting message.

2. Music while people are waiting on hold.

3. Redirecting calls to call agents in mail-enabled distribution lists and security groups.

As Teams admin, you are responsible for creating the call queue and configuring different parameters, such as maximum queue size, timeout, and call handling options.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Org-wide settings**, and then choose **Resource accounts,** to create a resource account.

4. On the **Resource accounts** page, select **+ Add** from the top pane.

5. On the right pane, enter the following information:

	- Display name: **Contoso Call Queue Resource Account**

	- Username: **pilot_callqueue1**

	- Resource Account Type: **Call queue**

6. Select **Save**.

7. Download the file **Alarm03.wav** from the following link and save to **C:\Windows\Media.**

   [https://github.com/MicrosoftLearning/MS-700-Managing-Microsoft-Teams/blob/master/Instructions/Labs/media/Alarm03.wav](https://github.com/MicrosoftLearning/MS-700-Managing-Microsoft-Teams/blob/master/Instructions/Labs/media/Alarm03.wav)

8. On the left navigation pane, select **Voice** and **Call queues**, to create a call queue.

9. Select **+ Add** from the top pane.

10. Enter the following information:

	- Call queue name: **Contoso Call Queue**

	- You haven’t added any resource accounts yet: Select **Add accounts**. On the right-side pane, search for **Contoso**, select **Add** from **Contoso Call Queue**, and then select **Add**.

	- Greeting: select **Play an audio file**, and then select **Upload file**.

	- In **Open** window, navigate to **C:\Windows\Media**, select **Alarm03.wav** and select **Open**.

	- Music on hold: **Play default music**

	- Call answering: Select **Choose users and groups** then select **Add groups** and on the right-side pane, search for **Sales**, select **Add** for **Sales** and then select **Add** at the bottom of the **Add call agents** pane.

	- Routing method: **Round robin**

	- Presence-based routing: **Off**

	- Call agents can opt out of taking calls: **On**

	- Call agent alert time: **30 seconds**

	- Maximum calls in the queue: **50**

	- When the maximum number of calls is reached: **Disconnect**

	- Call time out handling: **5 minutes**

	- When call times out: **Disconnect**

11. Select **Save** to create the new call queue.

Creating the new call queue may take some time, but you have successfully created a new custom call queue based on a resource account in your tenant.

**Note:** Because this call queue shall have a custom greeting, you need to upload some wav file for demonstration purposes. In real-world scenario, you would record and prepare a greeting audio file and upload the audio file as shown in this task.

#### Task 4 - Create an auto attendant

As Teams admin, you were tasked to create an auto attendant with a transcribed welcome message that will respond to customers outside of office hours. As some of your employees work in different time zones, the auto attendant informs a caller that the subscriber is currently on vacation and to call another person in the organization. Furthermore, the auto attendant informs callers about business hours.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Org-wide settings**, and then choose **Resource accounts,** to create the resource account first.

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

	- Time zone: **(UTC-08:00) Pacific Time (US &amp; Canada)**

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

19. Close all browser windows.

You have successfully created a resource account for the auto attendant and then created an auto attendant configuration.

### **Exercise 3: Set up a Calling Plan (Optional)**

In this exercise you will set up one of your users with a Calling Plan Trial. You will need to start the trial, order a phone number from Microsoft as your provider and enable your user to use this phone number when making outgoing calls.

 

**Note:** The availability of Calling Plans varies based on different countries and regions. Please go to the link below to check the availability of your location. The following instruction is based on the location of the United States.

[https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans](https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans) 

 

#### Task 1 – Activate a trial Calling Plan 

In this task you will activate the Calling Plan Add-on Trial for your tenant so you can assign the calling plan to your users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. Open **Microsoft Edge**, maximize the window and navigate to the **Microsoft 365 admin center** at [**https://admin.microsoft.com/**](https://admin.microsoft.com/).

3. On the **Pick an account** page, select the **MOD Administrator**(Admin@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

4. Open the Navigation Menu in the upper left corner and select  **Billing &gt; purchase services**.

5. Select **Add-ons**.

6. Scroll down until you see **Microsoft 365 Domestic Calling Plan for US and Canada Trial** (you may have to select **See more add-ons products**) and select **Details**.

7. Select **Start free trial**.

8. Select **Try now** to get 25 Calling Plans for a month.

9. Select **Continue** to continue past the order receipt.

You now have 25 Calling Plan licenses to assign to your users to test Domestic Calling Plan capabilities.

#### Task 2 – Assign a Calling Plan license to a user

In this task you will assign the calling plan license to a user to allow them to make domestic calls via the public switched telephone network.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Microsoft 365 admin center** and signed in as **MOD Administrator** (Admin@&lt;YourTenant&gt;.onmicrosoft.com).

3. Open the Navigation Menu in the upper left corner and select **Users**.

4. Select **Active users**.

5. Search for **Megan Bowen** and open the additional settings by selecting her name.

6. Select **Licenses and Apps**.

7. Under **Licenses** select **Microsoft 365 Domestic Calling Plan** by setting the checkmark in front of it.

8. Select **Save Changes** to assign the license.

You have assigned the Calling Plan license to a user. With this license assigned your users can use the Calling Plan features and receive a phone number.

#### Task 3 – Order a phone number for your user

In this task you will order a phone number to a user with an assigned Calling Plan license.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. In the **Microsoft Teams client** sign in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

3. Navigate to the **Teams admin center** at [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/).

4. On the left navigation pane, select **Voice**, and then **Phone numbers** below.

5. Select **Add** in the right pane.

6. Type **Phone number order** as the **Order Name**.

7. Fill out the description as **Number for Megan Bowen during the Calling Plan trial**.

8. In the dropdown menu of **Country or region**, select **United States**.

9. For **Number Type** select **User (Subscriber)**.

10. For **Location,** search **Redmond** and select **Contoso Emergency Address**.

11. For **Quantity**  select 1.

12. Select **Next**, **Place order**, then **Finish**.

**Note:** It might take some time for the phone numbers to show up. You can check your order from the **Order history** tab.

You just ordered a phone number for a User in Microsoft Teams. This is the same process you use to order numbers for all other Microsoft Teams services such as Call queues.

#### Task 4 – Assign a phone number to your user

In this Task you will assign an existing phone number to a user.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then **Phone numbers** below.

4. Select the phone number you want to assign and select **edit** to open the options.

5. Under **Assigned to** search for **Megan Bowen** and select **assign**.

6. Under **Emergency Location** select **Search by the location description**.

7. Search for the emergency location you created earlier.

8. Select **Apply** to assign the phone number to the user.

END OF LAB

 
