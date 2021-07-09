---
lab:
    title: 'Lab 03: Plan and configure network settings for Microsoft Teams '
    type: 'Answer Key'
    module: 'Module 3: Prepare the environment for a Microsoft Teams deployment'
---

# **Lab 03: Plan and configure network settings for Microsoft Teams**

# **Student lab answer key**

## **Use the new Microsoft 365 admin center**

Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center and are prompted with a window asking if you want to try the new Microsoft 365 admin center, always select the **Try it now** button.  
‎‎  
‎**‎IMPORTANT**: The instructions that are provided in the lab exercises for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. However, there are concerns about current network infrastructure to meet the requirements for Microsoft Teams services. Therefore, you need to analyze the current network infrastructure and perform bandwidth calculations. Based on your estimation, you can provide recommendations to the networking team. Furthermore, your organization is planning to purchase and deploy multiple Teams devices. You will need to evaluate different devices profiles and configure profile settings for the devices. At the end, you will need to evaluate the process of creating Microsoft Teams room, where multiple Teams rooms will be purchased in your organization.

## **Objectives**

After you complete this lab, you will be able to:

- Calculate the network bandwidth capacity for a Teams deployment

- Work with the Network Testing Companion on a client



## **Lab Setup**

- **Estimated Time:** 60 minutes.

## **Instructions**

### **Exercise 1: Calculate networking capabilities**

Microsoft Teams provides users with chat, audio, video and content sharing experience in different network conditions. It includes variable codecs, where media can be negotiated in limited bandwidth environments. However, as a Teams admin, you will need to carefully plan your network bandwidth, because there are other Office 365 services and third-party apps that also need reliable network connection. Therefore, it is very important that Teams admins have tools that could help to estimate the bandwidth consumption according to specific business requirements and existing network infrastructure and provide best experience to business users.

#### Task 1 - Calculate network bandwidth capacity

In this exercise, you will calculate the network requirements for Microsoft teams, depending on your expected Teams usage business requirements. You must ensure enough bandwidth based on your organization network connectivity that is described in the following table:

| **Location**| **Total number of employees**| **WAN link capacity / audio/video queue size (Mbps)**| **Office 365 connection**| **Internet connection** |
| - | - | - | - | - |
| New York HQ| 1000| 1000/300/500| ExpressRoute| Local Internet 1000 Mbps |
| Los Angeles Office| 250| 500/100/200| Remote connection through HQ| Remote Internet through HQ |
| Houston Office| 150| 400/50/100| Remote connection through HQ| Remote Internet through HQ |


Next, you will analyze your current bandwidth usage and test your network quality and connection to Microsoft Teams. You will also need to troubleshoot potential voice quality issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Sign in to the **Teams admin center** ([**https://admin.microsoft.com**](https://admin.microsoft.com/)) using **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

3. In the **Teams admin center,** on the left-hand navigation pane, expand **Planning**, and select **Network Planner**.

4. On the **Network planner** page, under **Network plans** tab, select **Add**.

5. On the **Network plan name** page, in the **Network plan name** box, type **Contoso plan**, and in the **Description** box type **Contoso Teams Network plan**, and then select **Apply**.

6. On the **Network planner** page, select **Personas** tab, and then select **Add**.

7. On the **Add persona** page, in the **Persona name** box type **New York office**, in the **Description** box type **New York office Teams users**, under the **Permissions** section, turn **On** all buttons, and then select **Apply**.

8. Select **Add** again, and on the **Add persona** page, in the **Persona name** box type **Los Angeles office**, in the **Description** box type **Los Angeles office Teams users**, under the **Permissions** section, turn **Off PSTN** button, and turn **On** all other buttons, and then select **Apply**.

9. Select the **Networks plans** tab, then select **Contoso plan**, and under **Network sites** tab, select **Add a network site**.

10. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **New York HQ site**.

	- In the in the description field type **New York HQ site network infrastructure**.

	- In the **Network users** field type **1000**.

	- In the **Network settings** section, in the **Subnet** box type **172.16.0.0**, and in the **Network range** box type **16**.

	- In the **Network settings** section, turn **On** the **Express Route** button.

	- In the **Network settings** section, in the **Internet link capacity** box, type **1000**.

	- In the **Network settings** section, in the **PSTN egress** drop-down box, choose **Use VoIP only**, and then select **Save**.

11. On the **Contoso plan** page, under **Network sites** tab, select **Add a network site**.

12. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **Los Angeles site**.

	- In the in the description field type **Los Angeles site network infrastructure**.

	- In the **Network users** field type **250**.

	- In the **Network settings** section, in the **Subnet** box type **192.168.10.0**, and in the **Network range** box type **24**.

	- In the **Network settings** section, ensure **ExpressRoute** button is **Off**.

	- In the **Network settings** section, turn **On** the **Connected to WAN** button, then in **WAN link capacity** box type **500**, in the **WAN audio queue size** box type **100**, and in **Video queue size** box type **200**.

	- In the **Network settings** section, in the **PSTN egress** drop-down box, **choose VoIP only**, and then select **Save**.

13. On the **Contoso plan** page, under **Network sites** tab, select **Add a network site**.

14. On the **Network site** page, enter the following information:

	- In the **Network site name** field, type **Houston site**.

	- In the in the description field type **Houston site network infrastructure**.

	- In the **Network users** field type **150**.

	- In the **Network settings** section, in the **Subnet** box type **192.168.20.0**, and in the **Network range** box type **24**.

	- In the **Network settings** section, ensure ExpressRoute button is **Off**.

	- In the **Network settings** section, turn **On** the **Connected to WAN** button, then in **WAN link capacity** box type **400**, in the **WAN audio queue size** box type **50**, and in **Video queue size** box type **100**.

	- In the **Network settings** section, in the **PSTN egress** drop-down box, **choose VoIP only**, and then select **Save**.

15. On the **Contoso plan** page, select **Report** tab and then select **Start a report**.

16. On the Report page, in the **Report name** field, type **Contoso report,** and in the description field, type **Contoso network estimation report**.

17. Under the **Calculation** section, review the default distribution of different personas in each site, and then select **Generate report**.

18. Under the **Reports** section, review the impact of Microsoft Teams on the Contoso network infrastructure by analyzing the report results on bandwidth needed for audio, video, screen sharing, Office 365 traffic, and PSTN.

19. On the report page, select the **Switch to chart view** at upper-right hand corner to display report results in different views.

Once you generate the report, you’ll see the recommendation of your bandwidth requirements. The allowed bandwidth shows how much of your overall traffic is reserved for real-time communications. Thirty percent is the recommended threshold. By changing this value and selecting **Run report**, you can see the different impact on the bandwidth for your network. Any areas that need more bandwidth will be highlighted in red. Work with your instructor to modify the parameters in the Network Planner and verify different results based on the input data.

In this lab, you have used Network Planner to estimate the Microsoft Teams impact on the bandwidth in your network infrastructure.

#### Task 2 - Use network testing companion

You are in the planning phase of a Microsoft Teams deployment. Before deploying Microsoft Teams in your organization, you want to test your network quality and connection to Microsoft Teams. After completing the test, you will interpret the results and gain insights into potential network issues.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right click the **Start** button and then select **Windows PowerShell (Admin)**.

3. Confirm the **User Account Control** window with **Yes**.

4. In the PowerShell window, enter the following cmdlet to install the Network Testing Companion:

   ```powershell
   Install-Module -Name NetworkTestingCompanion
   ```
5. Type in **y** and hit **return** for the Question with the **Untrusted repository**.

6. Enter the following cmdlet to create desktop shortcuts:

   ```powershell
   Invoke-ToolCreateShortcuts
   ```
7. Close the PowerShell window.

8. Open **Network Testing Companion** from the desktop shortcut and select the **Install** button, to install the Network Assessment Tool.

9. On the **User Account Control** window, select **Yes**.

10. Wait until window **Skype for Business and Microsoft Teams Network Testing Companion** initializes with green **Start** button appears in the **Network Connectivity and Quality Test** section on the right side of the window.

11. Review the information under **Windows operating system** and **Internet connection** sections and verify that no errors appear.

12. Select the green **Install** circle below **Network connectivity and quality test**.

13. A **User Account Control** window will appear in the taskbar. Maximize it and select **Yes.**

14. When the installation was successful, the symbol below **Network assessment tool** will change to a green checkmark in a circle too.

15. Select the green **Start** button in the **Network Connectivity and Quality Test** section to start the tests.
 
16. On the **Windows Security Alert** window, select **Allow access**. 

    >**Note:** If you receive a timeout message during the connectivity test, you can select the **Settings** tab in the tool. Adjust the **Connectivity test timeout (seconds)** option to a larger value and then start the test again.

17. When the tests have finished, the symbols below **Connectivity** and **Quality** will turn to green checkmarks in green circles.

18. After the test is **finished**, select the **View Results** tab and review the detailed results of the tests.

19. In the **View Results** tab, select **Report** file icon under **Network Connectivity** and **Network Quality** and review the testing steps and reports.

20. Discuss the results with the instructor.

21. Close all notepad windows and the **Skype for Business and Microsoft Teams Network Testing Companion.**

In this task, you have used Skype for Business and Microsoft Teams Network Testing Companion to test the connectivity and connection quality of your network infrastructure for Microsoft Teams.


END OF LAB
