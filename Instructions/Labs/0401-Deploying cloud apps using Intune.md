# Practice Lab: Deploying cloud apps using Intune

## Summary

In this lab, you will create and deploy cloud-based apps using Intune and the Company Portal Website.

## Exercise 1: Add a Microsoft Store App to Intune

### Scenario

You use Microsoft Intune to manage desktops and apps for Contoso Corporation. The Research department often connects to various servers to perform tasks and has asked for the Windows 10 Microsoft Remote Desktop app to be available for Research members to install as needed. The Microsoft Remote Desktop is available from the Microsoft Store, but you decide to add the app to Intune so that users can access it from the Company Portal website. A Research member named Aaron Nicholls has agreed to test the installation process after you have published the app to the portal.

### Task 1: Add Microsoft Remote Desktop to Intune

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. On the **Microsoft Endpoint Manager admin center** page, select **Apps**.
6. On the **Apps** page, in the navigation pane, select **All apps**.
7. In the details pane, select **Add**.
8. On the **Select app type** page, click the drop-down menu and then select **Microsoft Store app**.
9. Read the information about Microsoft store app and then click **Select**. The Add App page opens.
10. On the App information page, enter the following information and then select **Next**:

    - Name: **Microsoft Remote Desktop**

    - Description: **Microsoft Remote Desktop for Research Department**

    - Publisher: **Microsoft**

    - Appstore URL: **https://www.microsoft.com/p/microsoft-remote-desktop/9wzdncrfj3ps**

    - Category: **Business**

    - Show this as a featured app in the Company Portal: **Yes**

11. Select **Next** and then select **Create**.
12. The Microsoft Remote Desktop page opens. Take note of the Properties, Device install status, and User install status nodes.

### Task 2: Assign a Group to the App 

1. In the Microsoft Remote Desktop page, select **Properties**.
2. In the details pane, scroll down to the **Assignments** section and then select **Edit**.
3. On the **Assignments** page, select **Add group**.
4. On the **Select groups** page, select the **Research** group and then click **Select**.
5. Select **Review + save** and then select **Save**.
    
### Task 3: Install an app from the Company Portal Website

1. Switch to **SEA-WS3**.
2. Select **Other user**, and sign in as **Aaron\@yourtenant.onmicrosoft.com** with the password **Pa55w.rd**. 
3. On the taskbar, select **Microsoft Edge**.
4. In the address bar browse to **https://portal.manage.microsoft.com**.
5. Sign in as **Aaron\@yourtenant.onmicrosoft.com** with the password **Pa55w.rd**.
6. On the Contoso web portal, select **Devices**.
7. On the Devices page, select **Tap here to tell us which device you're using or add a new device**.
8. On the **Which device are you using** dialog box select the option next to **SEA-WS3**, and then select **Select**. Notice that the message now changes to Apps will be installed onto: SEA-WS3.
9. At the top-left corner, select the navigation button and then select **Apps**. Take note of the Microsoft Remote Desktop app listed on the Apps page.
10. Select **Microsoft Remote Desktop**.
11. On the Microsoft Remote Desktop page, select **View in Store**.
12. On the **This site is trying to open Microsoft Store**, select **Open**.
13. On the **Microsoft Remote Desktop** page, select **Get**.
14. At the Use across your devices message, select **No, thanks**. The app starts to download and installs on SEA-WS3.
15. After the app is installed close all open windows.
16. Select Start and verify that **Remote Desktop** is displayed on the Start menu.

**Results**: After completing this exercise, you will have successfully added and installed a Microsoft Store App from Intune.

## Exercise 2: Configure and deploy Microsoft 365 Apps from Intune

### Scenario

All the developers at Contoso require Microsoft 365 Apps. You've been asked to deploy the 64-bit versions of Microsoft Excel, Outlook, PowerPoint and Word to their Windows 10 devices. You also need to ensure they are configured for the Current Channel for updates.

### Task 1: Verify installed apps on SEA-WS2

1. On **SEA-WS2**, sign in as **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password. 
2. On the taskbar, select **Start** and then select the **Settings** app.
3. In the **Settings** app, select the **Apps** tile and on the **Apps & features** page, select **Programs and Features** under **Related Settings**.
4. In the **Program and Features** window, verify that **Microsoft 365 Apps for enterprise - en-us** is not listed.
5. Close all open windows.

### Task 2: Add Microsoft 365 apps to Intune

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. On the **Microsoft Endpoint Manager admin center** page, select **Apps**.
6. In the **Apps | Overview** blade, select **All Apps**. In the details pane, select **Add**.
7. In the **Select app type** blade, select **Windows 10** under **Microsoft 365 Apps**, and then select **Select**.
8. On the **Microsoft 365 Apps** blade, configure the following options and select **Next**:

   -   Suite Name: **Microsoft 365 Apps (Contoso developers)**

   -   Suite Description: **Microsoft 365 Apps for developers at Contoso**

9. On the **Configure app suite** blade, expand the **Select Office apps** dropdown, select the following Office 365 apps and select **Next**:

   -   **Excel**

   -   **Outlook**

   -   **PowerPoint**

   -   **Word**

10. On the **Configure app suite** tab, configure the following options and select **Next**:

    -   Architecture: **64-bit**

    -   Update channel: **Current Channel**

    -   Accept the Microsoft Software License Terms on behalf of users: **Yes**

11. On the **Assignments** tab, in the **Required** section, select **Add group.** 
12. On the **Select groups** blade, select **Contoso Developer devices**, and then choose **Select**.
13. Select **Next**. On the **Review + Create** tab, select **Create**.
14. On the **Microsoft 365 Apps (Contoso developers)** page, select **Properties**. 
15. In the details pane verify that **Contoso Developer devices** is listed under **Required** in the Assignments section.

### Task 3: Force policy synchronization from the Intune console

1. In the **Microsoft Endpoint Manager admin center**, select **Devices** and then select **All devices**.
2. In the details pane, select **SEA-WS2**. 
3. On the **SEA-WS2** blade, select **Sync** and when prompted select **Yes**. Intune will contact the device and tell it to synchronize all policies. This may take up to 5 minutes.

### Task 4: Verify Microsoft 365 apps are installed

1. Switch to **SEA-WS2** and wait approximately 10-15 minutes for the Office 365 Suite to install on the device.
2. On **SEA-WS2**, on the taskbar, select **Start** and then select the **Settings** app.
3. In the **Settings** app, select the **Apps** tile and on the **Apps & features** page, scroll down and verify that **Microsoft 365 Apps for enterprise - en-us** is listed.
4. Close the **Settings** app and select the **Start** button.
5. In the app list, scroll down to **W** and select **Word** and verify that the app opens.
6. Close all open windows.

### Task 5: Monitor app installation status in Intune

1. Switch to **SEA-CL1**.
2. In the **Microsoft Endpoint Manager admin center**, select **Apps**.
3. On the **Apps | Overview** blade, select **Monitor** and then select **App install status**. In the details pane, select **Microsoft 365 Apps \(Contoso developers\)**.
4. In the details pane, under **Device status** and under **User status**, verify that **1** is displayed under Installed. 

   _Note: This indicates that the app is installed on one device and for one user. Note that it may take some time for the information to display._

5. Select **Device install status**. In the details pane, you can see the devices that the app is installed on, and also the name of the user. The **Device Name** column should list **SEA-WS2** and the **Status** column should say **Installed**. This means that the app is installed on SEA-WS2.
6. In the **Microsoft Endpoint Manager admin center**, select **Devices**.
7. On the **Devices | Overview** blade, select **All devices** and then in the details pane, select **SEA-WS2**.
8. On the **SEA-WS2** blade, select **Managed Apps**.
9. On the **SEA-WS2 | Managed Apps** blade, in the details pane, select **Microsoft 365 Apps (Contoso developers)**.
10. On the **Microsoft 365 Apps (Contoso developers) - Installation details** blade, you can see the entire lifecycle of the application, that is - when it was created, assigned, installation time and status and the last time the device checked in (synced with Intune).
11. Close all open windows.

**Results**: After completing this exercise, you will have successfully configured and deployed Microsoft 365 Apps from Intune.

**END OF LAB**