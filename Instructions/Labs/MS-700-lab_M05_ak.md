--- 
lab: 
    title: 'Lab: Modify collaboration settings for Teams'
    type: 'Answer Key' 
    module: 'Module 05- Manage collaboration in Microsoft Teams' 
---

# Lab 05: Modify collaboration settings for Teams
# Student lab answer key
## Lab Scenario

In managing collaboration in Microsoft Teams, you will manage chat and collaboration experiences such as team settings or private channel creation policies. Finally, you will manage settings for Teams apps such as app setup policies, Apps, bots & connectors in Microsoft Teams or publish a custom app in Microsoft Teams. 

## Objectives

After you complete this lab, you will be able to:

- Create a messaging policy
- Manage private channels
- Disable third party storage providers
- Upload a tenant wide custom line of business app
- Edit and test default org-wide app policy
- Edit and test default app permission policy

## Lab Setup  

- **Estimated Time:** 90 minutes.

## Instructions
### Exercise 1: Configure channel and message policies

In this exercise you will configure policies to manage the creation of new private channels and the available tools for users in chat.

#### Task 1 - Create messaging policy for giphy, memes and stickers

In the past, some users of Contoso have used a lot of stickers, gif animations and similar pictures in their conversations, even with externals using other chat solutions. The new corporate guideline shall prohibit the use of graphic elements in corporate communication via Teams, because users shall not use them in conversations external customers and clients. As a Teams service administrator, you must create a new message policy that prohibits its use and apply it to several users of your pilot project.

**Note:** Please note that after creating a messaging policy it can take up to 24 hours for the settings to be applied to the users.

1. Connect to the Client 1 VM with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) to access the **Microsoft** **Teams** **admin center**. 

3. On the **Pick an account** page, select JoniS@YourTenant.onmicrosoft.com and sign in. 

4. In the left-hand navigation pane, select the **Messaging policies**, then click on the **+ Add** at the right side of the page, to create a new messaging policy.

5. In the **New messaging policy** dialog enter the following information to the fields and set the following configuration:

	- **Name**: Regular users without fun stuff
	- **Description**: Policy to disable giphys, sticker and memes in conversations
	- **Use Giphys in conversations**: off
	- **Use Memes in conversations**: off
	- **Use Stickers in conversations**: off

6. Leave the rest of the settings as default. Select **Save**. 

7. In the Messaging policies overview, select the checkmark left to **Regular users without fun stuff**. Then select **Manage users** in the top navigation pane.

8. Type in **Lynne Robbins** and select **Add**>**Apply**.

9. Stay in the Teams admin center and continue with the next task.

In this task, you have successfully configured a new messaging policy and assigned it to Lynne Robbins. It will now take some time for the policy to take effect. Continue with the next task.

#### Task 2 - Manage private channels in a team

As your part as system administrator of Contoso, you will create a private channel "confidential" in the sales team that only allows some people to be able to access the information.

1. Connect to the Client 1 VM with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) to access the **Microsoft** **Teams** **admin center**. 

3. On the Pick an account page, select JoniS@YourTenant.onmicrosoft.com and sign in. 

4. In the left-hand navigation pane, select **Teams** to open the menu and **Manage teams** below.

5. Select the **Sales** team in the **Manage teams** overview window.

6. Select the **Channels** tab in the middle of the page. Select **+ Add channel** in the navigation pane below to get into the **Add channel** window.

7. In the **Add channel** window enter the following information:

	- **Name:** Confidential sales
	- **Description:** Confidential private sales channel
	- **Type:** Private

8. Enter to the field **Channel owner** the user **Lynne Robbins** and select her as owner.

9. Select **Apply** in the **Add channel** window.

10. Connect to the **Client 2 VM** with the credentials that have been provided to you.

11. Open the Edge browser with the icon from the taskbar.

12. In your browser, select the address bar and go to the **Teams Web Client** page by entering the following URL: [**https://teams.microsoft.com**](https://teams.microsoft.com/)

13. In the **Pick an account** window, select LynneR@YourTenant.onmicrosoft.com and sign in..

14. On the Microsoft Teams landing page click **Use the web app instead**

15. On the team overview in the Teams web client, you should see the new private channel **Confidential sales**, marked with a small padlock.

In this task you learned how to create a private channel in the Microsoft Teams Admin center and how to configure and check the access.

### Exercise 2: Manage app settings for team
#### Task 1 - Disable third party storage providers

In the past, users stored data at various location, including third-party storage providers. Recently, the company deployed OneDrive for Business for all users and would like to guide the users to use OneDrive for Business as the primary data storage location. As the system admin, you are asked to deactivate all third-party storage providers in Microsoft Teams to align with the direction. 

**Note:** Please note that after disabling the third-party storage provider, it can take up to 24 hours for the settings to be applied to the teams.



1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) to access the **Microsoft** **Teams** **admin center**. 

3. When you see the **Pick an account** window, select JoniS@YourTenant.onmicrosoft.com and sign in.

4. On the left-side navigation pane, select the **Org-wide settings** to open the menu, then select **Teams settings** below**.** 

5. In the Teams settings overview go to the **Files** section. Configure the following file sharing and cloud file storage options.

	- **Citrix files** off
	- **DropBox** off
	- **Box** off
	- **Google Drive** off

6. After this scroll down and select **Save**. 

In this task you have learned how to enable or disable third-party storage providers for your whole tenant.

#### Task 2 - Edit default org-wide app policy

In the pilot project, the company decided that Microsoft Planner is the default app for all (existing) teams. To do this, edit the default org-wide app policy

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) to access the **Microsoft** **Teams** **admin center**. 

3. When you see the **Pick an account** window, select JoniS@YourTenant.onmicrosoft.com and sign in.

4. In the left-hand navigation pane, select the **Teams apps** to open the menu, then select **Setup policies.** 

5. In the **App setup policies** window select **Global (Org-wide default)** name to open the org-wide app policy.

6. In the **Pinned apps** section select **+ Add apps** to open the **Add pinned apps** menu at the right side. 

7. Select **Global** and type in the name **Planner**, mouseover the presented name and select **Add**. After this select **Add** to return previous window.

8. Make sure that **Planner** is now listed in the **Pinned apps** section and select **Save**.

9. In the **App setup policies** window select **Global (Org-wide default)** make sure there is a selected checkmark in the front of the name.

10. Then select **Manage users** in the top navigation pane to open the **Mange users** dialog. Enter the name of **Lynne Robbins** and mouseover the presented name and select **Add**. Then select **Apply.**

11. Connect to the **Client 2 VM** with the credentials that have been provided to you.

12. Open the Edge browser, select the address bar and go to the **Teams Web Client** page by entering the following URL: [**https://teams.microsoft.com**](https://teams.microsoft.com/)

13. On the **Pick an account** window, select LynneR@YourTenant.onmicrosoft.com and sign in.

14. On the Microsoft Teams landing page click **Use the web app instead**

15. In the left-hand navigation pane, the **Planner** app should be displayed by default below the Files **menu**.
 

#### Task 3 - Edit default app permission policy

In this task you will edit the default app permission policy and block the Google Analytics app for all tenants

1. Connect to the Client 1 VM with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the window and navigate to [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com) to access the **Microsoft** **Teams** **admin center**. 

3. On the **Pick an account** window, select JoniS@YourTenant.onmicrosoft.com and sign in.

4. In the left-hand navigation pane, select the **Teams apps** to open the menu, then select **Permission policies.** 

5. In the **App permission policies** window select **+ Add** to create a new policy.

6. After this the policy creation dialog appears, type in the policy name **Block Google Analytics** and expand the menu in the **Third-party app** section, and select **Block specific apps and allow all others**.

7. Select **Block apps** below the Notification **Add apps that you want to block** to open the right-side menu.

8. In the Add third party apps dialog, type in Google Analytics, mouseover the presented name and select **Add**. After this select **Block** to return to the **App permission policies** window. Select **Save.**

9. In the App permission policies overview, select the checkmark left to **Block Google Analytics**. Then select **Manage users** in the top navigation pane.

10. Type in **Lynne Robbins** and select **Add** by mouseover the presented name, then click **Apply**.

11. Close all browser windows.

In this task you have learned how to block the Google Analytics app for your tenant.

 

#### Task 4 - Add a custom line of business app

In this task, you will add a custom line of business app required for your company Contoso Ltd. for all users of your tenant. You find sample LOB app at: https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Select the **Edge Browser** icon from the taskbar. In your browser go to the following link and download the custom line of business app as zip package: 

	- Go to the following link:
[Notification Bot](https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp/blob/master/Cross%20Vertical/NotificationBot/Manifest/Notification%20App.zip).
	- Select **download** and **Save**, to download the file to the **Downloads** folder.

3. Navigate to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

4. When you see the **Pick an account** window, select **JoniS@YourTenant.onmicrosoft.com** and enter the provided credentials.

5. On the teams landing page, select **Use the web app instead**.

6. Select **Apps** from the side pane.

7. Scroll down the list of **Apps**, select **Upload a custom app** and **Upload for Contoso**.

8. A file select window appears. Navigate to **Downloads** and select **Notification App.zip**.

9. Go back to **Apps** from the side pane.

10. Scroll down and select **Built for Contoso**.

11. Note the **NotificationBot** app.

12. Select **Joni Shermans** picture in the upper right corner and select **Sign out**.

13. Close the browser and open a new Edge browser window.

14. Navigate to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

15. On the Pick an account page, select LynneR@YourTenant.onmicrosoft.com and sign in with the credentials provided.

16. On the teams landing page, select **Use the web app instead**.

17. Go back to **Apps** from the side pane.

18. Scroll down and select **Built for Contoso**.

19. Select **NotificationBot** and review the details.

20. Select **Add**, to test the custom app.

21. On the **Welcome to Notification** **Bot** conversation, select the dropdown menu and select **Weather**.

22. The weather forecast for your location is being displayed.

23. Close all browser windows.

You have successfully added a custom app to your tenant with the account of Joni Sherman, who is a Teams admin in your tenant. Afterwards, you have successfully tested the app availability with a regular user.

### Exercise 3: Test configured policy settings

In this exercise, you will test the configured policy settings on a client with the affected user Lynne Robbins and compare the settings to the available client settings of Joni Sherman.

#### Task 1 – Test the messaging policy and private channel access

In this task, you will test the **messaging policies** configured in exercise 1 and compare the difference between affected user (Lynne Robbins) vs regular user(Joni Sherman).

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Edge Browser** icon from the taskbar. In your browser go to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

3. On the **Pick an account** window, select LynneR@YourTenant.onmicrosoft.com and sign in.

4. On the Microsoft Teams landing page click **Use the web app instead**

5. Skip a potential welcome dialog by clicking on **x** in the right corner.

6. In the left-hand navigation pane, select **Chat**, then select the **Contacts tab** in the middle of the page. 

7. If there is no contact for **Joni Sherman**, then select **…** and select **Add a contact to this group**. Type in the name **Joni Sherman** and select her by mouseover the presented name. After this select **Add** to return to the **Contacts tab**.

8. **In the Contacts tab,** select **Joni Sherman. If the giphy, memes and stickers icons are missing below the conversation-bar, the messaging policy** takes effect.

9. In the left-hand navigation pane, select **Teams.**

10. If you can see and select the **Confidential sales** channel of the **Sales** team and if you are able to write a comment, and confirm that you have access to the private channel.

#### Task 2 – Test the app permission policy and storage providers

In this task, you will test the **app permission policies** configured in exercise 2 and compare the difference between affected user (Lynne Robbins) vs regular user (Joni Sherman).

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Edge Browser** icon from the taskbar. In your browser go to the **Microsoft Teams web client** page by entering the following URL in the address bar: [**https://teams.microsoft.com/**](https://teams.microsoft.com/)

3. On the **Pick an account** window, select LynneR@YourTenant.onmicrosoft.com and sign in.

4. On the Microsoft Teams landing page click **Use the web app instead**

5. Skip a potential welcome dialog by clicking on **x** in the right corner.

6. In the left-hand navigation select **Teams** and select the **IT-Department** channel **General**. Mouseover the presented name and select **…** and select **Connectors**.

7. In the **Connectors for "General"** window, enter **Google Analytics** into the search field. 

8. **If you can't find Google Analytics as a search result and can't add the app to the channel, the app permission policy will work as desired.**

9. In the left-hand navigation pane, select **Teams**, then select the **IT-Department** team. Select the **files** Tab on the middle of the Teams web client. Then select **+ Add cloud storage** in the navigation pane below. 

10. If only SharePoint is shown as selection, the deactivation of the 3rd party cloud storage provider worked as expected.
