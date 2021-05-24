---
lab:
    title: 'Lab 05: Modify collaboration settings for Teams'
    module: 'Module 5: Manage collaboration in Microsoft Teams'
---

# **Lab 05: Modify collaboration settings for Teams**

# **Student lab manual**

## **Lab Scenario**

In managing collaboration in Microsoft Teams, you will manage chat and collaboration experiences such as team settings or private channel creation policies. Finally, you will manage settings for Teams apps such as app setup policies, Apps, bots & connectors in Microsoft Teams or publish a custom app in Microsoft Teams.

## **Objectives**

After you complete this lab, you will be able to:

- Create a messaging policy

- Manage private channels

- Disable third party storage providers

- Create a Power Apps app

- Manage Policy packages

- Upload a tenant wide custom line of business app

- Edit and test default org-wide app policy

- Edit and test default app permission policy

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Configure channel and message policies**

In this exercise you will configure policies to manage the creation of new private channels and the available tools for users in chat.

#### Task 1 - Create messaging policy for giphy, memes and stickers

In the past, some users of Contoso have used a lot of stickers, gif animations, and similar pictures in their conversations, even with externals using other chat solutions. The new corporate guideline shall prohibit the use of graphic elements in corporate communication via Teams, because users shall not use them in conversations with external customers and clients. As a Teams service administrator, you must create a new message policy that prohibits its use and apply it to several users of your pilot project.

**Note:** After creating a messaging policy, it can take up to 24 hours for the settings to be applied to the users.

1. Sign in to the **Teams admin center** [**https://admin.teams.microsoft.com**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new **New messaging policy** with the following settings:

	- **Name:** Regular users without fun stuff

	- **Description:** Policy to disable giphys, stickers, and memes in conversations

	- **Use Giphys in conversations:** off

	- **Use Memes in conversations:** off

	- **Use Stickers in conversations:** off

3. Assign the new messaging policy to **Lynne Robbins**.

4. Leave the Teams admin center open.

In this task, you have successfully configured a new messaging policy and assigned it to Lynne Robbins. It will now take some time for the policy to take effect. Continue with the next task.

#### Task 2 - Manage private channels in a team

As Teams administrator of Contoso, you will create a private channel "confidential" in the sales team that only allows some people to be able to access the information.

1. Sign in to the Teams admin center [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new channel for the **Sales** team, using the following settings:

	- **Name:** Confidential sales

	- **Description:** Confidential private sales channel

	- **Type:** Private

	- **Owner:** Lynne Robbins

3. Sign in to the Teams web client [**https://teams.microsoft.com/**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

4. Check the existence of the new channel.

5. Close the Teams web client.

In this task you learned how to create a private channel in the Microsoft Teams Admin center and how to configure and check the access.

### **Exercise 2: Manage app settings**

#### Task 1 - Disable third party storage providers

In the past, users stored data at various locations, including third-party storage providers. Recently, the company deployed OneDrive for all users and would like to guide the users to use SharePoint and OneDrive as the primary data storage locations with Box as an alternative for all file collaborations. As the Teams admin, you are asked to deactivate all third-party storage providers except Box in Microsoft Teams to align with the direction.

**Note:** After disabling the third-party storage provider, it can take up to 24 hours for the settings to be applied to the teams.

1. Sign in to the Teams admin center [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Change the **Teams settings** to the following values:

	- **Citrix files:** Off

	- **DropBox:** Off

	- **Box:** On

	- **Google Drive:** Off

	- **Egnyte:** Off

3. Leave the Teams admin center open.

In this task you have learned how to enable or disable third-party storage providers for your whole tenant.

#### Task 2 - Edit default org-wide app policy

In the pilot project, the company decided that Microsoft Planner is the default app for all (existing) teams. To do this, edit the default org-wide app policy

1. Sign in to the Teams admin center [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Edit the **App setup policies** with the name **Global (Org-wide default)** to the following settings:

	- **Pinned apps:** Planner

3. Make sure **Lynne Robbins** has the **App setup policies** with the name **Global (Org-wide default)** configured.

4. Sign in to the Teams web client [**https://teams.microsoft.com/**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

5. Check, that **Planner** is present as new pinned app.

6. Close the Teams web client.

#### Task 3 - Edit default app permission policy

In this task you will edit the default app permission policy and block the Google Analytics app for all tenants

1. Sign in to the Teams admin center [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Create a new **App permission policies** with the following settings:

	- Name: **Block Google Analytics**

	- **Block specific apps and allow all others**

	- Block third party apps: **Google Analytics** and **Google Analytics Insights**

3. Assign the **App permission policy** to **Lynne Robbins**.

4. Close the Teams admin center.

In this task you have learned how to block the Google Analytics app for your tenant.

#### Task 4 – Manage policy packages

To avoid administrative overhead with managing large numbers of policies individually for groups of different users, you need to evaluate using policy packages to group policies into logical units. In this task you need to review the default policy packages and change a default policy package for first line workers.

1. Sign in to the Teams admin center [**https://admin.teams.microsoft.com/**](https://admin.teams.microsoft.com/) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Select **Policy packages** and review the existing policy packages.

3. **Edit** the **Messaging policy** of the **Frontline_Worker** package with the following setting:

	- **Send urgent messages using priority notifications**: On

4. **Edit** the **Calling policy** of the **Frontline_Worker** package with the following settings:

	- **Prevent toll bypass and send calls through the PSTN**: On

	- **Busy on busy is available when in a call**: On

5. Add **Allan Deyoung** to the policy package.

6. Select **Users** and review the policies for **Allan Dyoung**. You should see **Frontline worker** package and the **Frontline_Worker** policies.

You have successfully modified included policies from an existing policy package and assigned the package to a single user. This will help you assign the same set of policies to a group of users working in the same role or requiring the same access.

#### Task 5 - Add a custom line of business app

In this task, you will add a custom line of business app required for your company Contoso Ltd. for all users of your tenant. You find sample LOB app at: **https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp**.

1. Download the custom app from the following links: [**Notification Bot**](https://github.com/OfficeDev/msteams-sample-line-of-business-apps-csharp/blob/master/Cross%20Vertical/NotificationBot/Manifest/Notification%20App.zip).

2. Sign in to the Teams web client [**https://teams.microsoft.com**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

3. Upload the custom app in **Apps**.

4. Interrogate with the new app to receive a weather forecast.

5. Close the Teams web client.

You have successfully added a custom app to your tenant with the account of Joni Sherman, who is a Teams admin in your tenant. Afterwards, you have successfully tested the app availability with a regular user.

#### Task 6 - Add a custom app from Microsoft Power Apps

In this task, you will need to evaluate the integration of Power Apps into Teams by creating a new app from a template and integrate it into the IT-Department team. You will choose the Out of Office template and provide a fast option for IT-Department members to activate the Out of Office function for their mailbox.

1. Sign in to the **Power Apps** dashboard ([**https://make.powerapps.com/**](https://make.powerapps.com/)**)** using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Open the app editor and create a new **Power App** called MyOofApp from the **Out of Office** template.

3. Test the app and explore the options the app provides under **create new**.

4. Share the app with **Everyone in Contoso**.

5. Sign in to the Teams web client [**https://teams.microsoft.com**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

6. Using the **Microsoft Teams Desktop Client** pin your new **Power App** to the **General** channel of the **IT-Department** team.

In this task, you have successfully created a Power App and integrated it into a Teams channel. All members of the IT-Department team can now use the app in the tab to plan and create an Out of Office (Oof) message for their mailboxes.

### **Exercise 3: Test configured policy settings**

In this exercise, you will test the configured policy settings on a client with the affected user Lynne Robbins and compare the settings to the available client settings of Joni Sherman.

#### Task 1 – Test the messaging policy and private channel access

In this task, you will test the **messaging policies** configured in exercise 1 and compare the difference between affected user (Lynne Robbins) vs regular user(Joni Sherman).

1. Sign in to the Teams web client [**https://teams.microsoft.com**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Open a chat with **Joni Sherman** and check, if the **messaging policy** works as expected.

3. Write a message to the **Confidential Sales** channel conversation window.

#### Task 2 – Test the app permission policy and storage providers

In this task, you will test the **app permission policies** configured in exercise 2 and compare the difference between affected user (Lynne Robbins) vs regular user (Joni Sherman).

1. Sign in to the Teams web client [**https://teams.microsoft.com**](https://teams.microsoft.com/) using **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Try to add an additional **Google Analytics** connector to the **IT-Department** team. If this does not work, the **app permission policy** works as desired.

3. Try to add non-SharePoint storage providers to the **IT-Department** team. If you only see Box as an alternative, the configured **Teams settings** works as expected.

4. Close the Teams web client.

END OF LAB
