---
lab:
    title: 'Lab 06: Manage calling in Microsoft Teams'
    type: 'Answer Key'
    module: 'Module 6: Manage calling in Microsoft Teams'
---

# **Lab 06: - Manage calling in Microsoft Teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. According to Contoso business requirements, Microsoft Teams will be used as an organization’s solution for conferencing and telephony. Teams admins will need to replace Contoso legacy PBX solution and configure voice features that will provide users with Teams calling capabilities.

## **Objectives**

After you complete this lab, you will be able to:


- Set up a Calling Plan

- Order and Assign phone numbers

- Configure emergency addresses

- Create calling policies

- Configure resource accounts and calling queues

- Create resource accounts and auto attendants


## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**


### **Exercise 1: Set up a Calling Plan (Optional)**

In this exercise you will set up one of your users with a Calling Plan Trial. You will need to start the trial, order a phone number from Microsoft as your provider and enable your user to use this phone number when making outgoing calls.

 

**Note:** The availability of Calling Plans varies based on different countries and regions. Please go to the link below to check the availability of your location. The following instruction is based on the location of the United States.

[https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans](https://docs.microsoft.com/en-us/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans) 

 
#### Task 1 - Add a new emergency address

In this task you will add a new emergency address "One Microsoft Way, Redmond, WA 98052, USA" for users in the United States. It is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

1. Connect to the **Client 1 VM** and browse to the **Teams admin center** as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. On the left navigation pane select **Locations** and below select **Emergency addresses**.

3. Select **+ Add** from the top pane to create a new emergency address.

4. On the **Location\Add location** page, enter the following information:

	- Put in a name for your location: **Contoso Emergency Address**

	- Country or region: **United States**

	- Address: **1 Microsoft Way, Redmond, WA 98052** 

      (You can enable **Edit the address manually**, and enter the address manually)

5. Acknowledge the emergency calling disclaimer.

6. Select **Save**.

You have successfully created an emergency address that can be used for phone numbers.

#### Task 2 – Activate a trial Calling Plan 

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

#### Task 3 – Assign a Calling Plan license to a user

In this task you will assign the calling plan license to a user to allow them to make domestic calls via the public switched telephone network.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Microsoft 365 admin center** and signed in as **MOD Administrator** (Admin@&lt;YourTenant&gt;.onmicrosoft.com).

3. Open the Navigation Menu in the upper left corner and select **Users**.

4. Select **Active users**.

5. Search for **Lynne Robbins** and open the additional settings by selecting her name.

6. Select **Licenses and Apps**.

7. Under **Licenses** select **Microsoft 365 Domestic Calling Plan** by setting the checkmark in front of it.

8. Select **Save Changes** to assign the license.

You have assigned the Calling Plan license to a user. With this license assigned your users can use the Calling Plan features and receive a phone number.

#### Task 4 – Order a phone number for your user

In this task you will order a phone number to a user with an assigned Calling Plan license.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. In the **Microsoft Teams client** sign in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and sign in with the provided credentials.

3. Navigate to the **Teams admin center** at [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/).

4. On the left navigation pane, select **Voice**, and then **Phone numbers** below.

5. Select **Add** in the right pane.

6. Type **Phone number order** as the **Order Name**.

7. Fill out the description as **Number for Lynne Robbins during the Calling Plan trial**.

8. In the dropdown menu of **Country or region**, select **United States**.

9. For **Number Type** select **User (Subscriber)**.

10. For the Operator, pick Microsoft 

11. For **Quantity**  select 1.

12. In the **Search for new numbers** section, you can use one of the following approaches to find new numbers:

	* Search by city name
		
		1. Select **Search by city name**. 
		2. Search **Redmond** and select **Contoso Emergency Address**, which is the location you just created. 
		3. Select **Next**.

	* Search by area code

		1. Select **Search by area code**. 
		2. Enter an area code in United States.
		3. Select **Next**.

	**Note**: If you received the following message, please try other area codes or creating another location by selecting **Add a location** and repeat task 1. 

	*We can't find any phone numbers for the address you selected.*

13. Once you reserved a phone number successfully, you can proceed by selecting **Place order**, then **Finish**.

**Note:** It might take some time for the phone numbers to show up. You can check your order from the **Order history** tab. 

You just ordered a phone number for a User in Microsoft Teams. This is the same process you use to order numbers for all other Microsoft Teams services such as Call queues.

#### Task 5 – Assign a phone number to your user

In this Task you will assign an existing phone number to a user.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then **Phone numbers** below.

4. Select the phone number you want to assign and select **edit** to open the options.

5. Under **Assigned to** search for **Lynne Robbins** and select **assign**.

6. Under **Emergency Location** select **Search by the location description**.

7. Search for the emergency location you created earlier.

8. Select **Apply** to assign the phone number to the user.



 

### **Exercise 2: Manage phone system for Microsoft Teams**

Contoso organization is using legacy PBX system. With introduction of Microsoft Teams, Contoso will migrate their legacy telephony system to Microsoft Phone System. Teams admins are responsible for evaluating and testing Microsoft Teams voice functionalities.


#### Task 1 - Create a calling policy

As part of your pilot project for calling functionalities with Microsoft Teams, you have the requirement that all pilot users receive access to the voicemail functionalities. You create and assign a new calling policy and configure the settings. However, all other users should not receive voicemail functionalities during the testing period. Therefore, you will edit the default policy to ensure that voicemail is disabled for all other users.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then **Calling policies** below.

4. Select the **Global (Org-wide default)** policy to edit the default settings.

5. In **Calling policies\Global**, use the dropdown menu right to **Voicemail is available for routing inbound calls** and select **Not Enabled**. Then select **Save**.

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

#### Task 2 - Create a call queue

Contoso Ltd. has deployed Microsoft Teams voice functionalities throughout the organization. To deploy some automation for incoming support calls, the calling queue functionalities need to be tested before being rolled out. The following settings shall be configured for customers calling in:

1. A greeting message.

2. Music while people are waiting on hold.

3. Redirecting calls to call agents in mail-enabled distribution lists and security groups.

As Teams admin, you are responsible for creating the call queue and configuring different parameters, such as maximum queue size, timeout, and call handling options.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then choose **Resource accounts,** to create a resource account.

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

#### Task 3 - Create an auto attendant

As Teams admin, you were tasked to create an auto attendant with a transcribed welcome message that will respond to customers outside of office hours. As some of your employees work in different time zones, the auto attendant informs a caller that the subscriber is currently on vacation and to call another person in the organization. Furthermore, the auto attendant informs callers about business hours.

1. Connect to the **Client 1 VM** and sign in with the Credentials that have been provided to you.

2. You should still be in the **Teams admin center** and signed in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. On the left navigation pane, select **Voice**, and then choose **Resource accounts,** to create the resource account first.

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

	- First play a greeting message: Select **Add a greeting message**

	- Type in: **Welcome. The person you called is currently on vacation, your call will be redirected to an operator.**

	- Then route the call: **Redirect call**

	- Redirect to: **Voice app**

	- Search by resource account: **Contoso Call Queue Resource Account**

12. Select **Next**.

13. On the **Set business hours** page, configure the following:

	- Select **Clear all hours**

	- Configure working hours **Monday** to **Friday** from **08:00 AM** to **04:00 PM**

	- Leave **Saturday** and **Sunday** blank.

	- First play a greeting message: **Add a greeting message**

	- Type in: **Thank you for your call, our business hours are Monday to Friday, 08:00 AM to 04:00 PM.**

	- Then route the call: **Disconnect**

14. Select **Next**.

15. On the **Holiday call settings** page, select **Next**.

16. On the **Find people** page, select **Next**.

17. On the **Resource accounts** page, select **Add accounts**. In the right-side pane, type **Contoso auto attendant**, and then select **Add** twice.

18. Select **Submit** to finish the creation of the auto attendant.

19. Close all browser windows.

You have successfully created a resource account for the auto attendant and then created an auto attendant configuration.

END OF LAB
