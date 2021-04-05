# Practice Lab: Monitor device and user activity in Intune

## Summary

In this lab, you will monitor user Sign-in activity, Audit logs, and device activity.

### Scenario

You need to review Diego Siciliani's sign-in activity and general information provided by the Audit logs. You also need to verify the hardware on SEA-WS2 and confirm the configuration profile assigned to this device is successfully applied. 

### Task 1: Monitor user activity

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. On the **Microsoft Endpoint Manager admin center** page, select **Users**.
6. In the Users navigation pane, in the Activity section, select **Sign-ins**. 
7. In the Details pane, user sign-ins are listed. Select on the first entry where the **User** column displays **Diego Siciliani**.
8. In the **Details** pane, Diego Siciliani´s sign-in details are displayed. 
9. Select each of the main pages, including **Basic info**, **Location**, **Device info**, **Authentication Details**, and **Conditional Access**. Scroll to examine information on each page. 
10. In the Users navigation pane, in the Activity section, select **Audit logs**. 
11. In the details pane, audit information is displayed about administrative changes to users. Examine the information by selecting the various entries.

### Task 2: Monitor device activity

1. In the Microsoft Endpoint Manager admin center, from the navigation pane, select **Devices**.
2. In the Devices navigation pane, select **Overview**.
3. In the details pane, take note of the device information for enrolled devices. Select the ellipse icon (if shown) to view all of the overview tabs. Available tabs include **Enrollment status**, **Enrollment alerts**, **Compliance status**, **Configuration status**, and **Software update status**. Select each tab to view information.
4. Select **All devices**, and in the details pane, select **SEA-WS2**. Information about the device such as name, Primary user, and operating system is displayed.
5. In the SEA-WS2 navigation pane, select **Hardware** and examine the hardware inventory.
6. In the SEA-WS2 navigation pane, select **Discovered apps** and examine the app inventory.
7. In the SEA-WS2 navigation pane, select **Device configuration** and in the details pane, take note of the Device configuration profiles assigned to the device. The **State** column should display **Succeeded**, which means that the profiles were applied successfully to the device.
8. In the details pane, select **Contoso Developer – standard**. On the **Contoso Developer – standard** blade, take note of each setting you configured in the profile. The **State** should display **Succeeded** next to all of them.
9. In the Microsoft Endpoint Manager admin center, from the navigation pane, select **Home**.

**Results**: After completing this exercise, you will have successfully monitored user Sign-in activity, Audit logs, and device activity.

**END OF LAB**