# Practice Lab: Managing Windows 10 security and feature updates

## Summary

In this lab you will configure Windows 10 security and feature update settings using Intune.

### Scenario

You have been asked to configure Update Rings in Intune to manage Windows update settings. Devices should be configured to be in the Semi-Annual channel and Feature updates deferred 45 days after release. You would like to test the settings using SEA-WS3. 

#### Task 1: Verify current update settings for a single device

1. On **SEA-WS3**, sign in as as **Aaron Nicholls** with the PIN **102938**. 
2. Select **Start**, and then select the **Settings** icon.
3. In **Settings**, select **Update & Security**.
4. Select **Delivery Optimization**.
5. On the **Delivery Optimization** page, verify that the **Allow downloads from other PCs** option is enabled.
6. Select **PCs on my local network, and PCs on the Internet**.
7. In the navigation pane, select **Windows Insider Program**. Notice that you must change the level of diagnostic data before you can get Insider Preview builds. 
8. Select the **Go to Diagnostics & Feedback settings to turn on optional diagnostic data** link. 
9. On the Diagnostics and feedback page, set **Diagnostic data** setting to **Optional diagnostic data**. 
10. In the Settings navigation on the left, select **Home**. Select **Update & Security** and then select **Windows Insider Program**. 
11. Note that the **Get Started** option is now available.
12. In the navigation pane, select **Home** and then select **Update & Security**.

#### Task 2: Review applied settings

1. On the **Windows Update** page, select **View update history**.
2. Review the updates listed, if any, and then select **Uninstall updates**. 
3. Review the updates listed in **Installed Updates**. Close Installed Updates.
4. On the **View update history** page, select **Back**. Close the **Settings** app.

#### Task 3: Configure update settings by using Intune

1. Switch to **SEA-CL1** and sign in as **Contoso\Administrator** with the password of **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**. 
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**.
4. In the navigation pane, select **Devices** and then select **Windows 10 update rings**.
5. On the **Devices | Windows 10 update rings** blade select **Create profile**.
6. In the **Basics** blade, enter the following information, and then select **Next**:

   -   Name: **Contoso Updates - standard**

   -   Description: **Standard Windows updates configuration** 

7. In the **Update ring settings** blade, enter the following information, and then select **Next**:

   -   Servicing channel: **Semi-Annual Channel**

   -   Feature update deferral period \(days\): **45**

   -   Option to pause Windows updates: **Disable**

8. On the **Assignments** blade, select **Add groups**. 
9. On the **Select groups to include** blade, in the **Search** box, select **Contoso Developer devices** and then select **Select**.
10. Select **Next** and on the **Review + create** blade select **Create**.
11. From the navigation bar select **Configuration profiles**.
12. On the **Devices | Configuration profiles** blade, in the details pane, select **Create profile**.
13. In the **Create a profile** blade, select the following options, and then select **Create**:

    -   Platform: **Windows 10 and later**

    -   Profile: **Templates** then select **Delivery Optimization**

14. In the **Basics** blade, enter the following information, and then select **Next**:

    -   Name: **Contoso Developer - Delivery optimization**

    -   Description: **Delivery optimization for Developer**

15. In the **Configuration settings** blade, enter the following information, and then select **Next**:

    -   Download Mode: **HTTP only, no peering \(0\)**

16. On the **Assignments** blade, select **Add groups**. 
17. On the **Select groups to include** blade, select **Contoso Developer devices** and then select **Select**.
18. Select **Next** twice, and on the **Review + create** blade select **Create**.

#### Task 4: Verify that the device’s update settings are managed centrally

1. Switch to **SEA-WS3**.
2. Select **Start**, and then select the **Settings** icon.
3. In the **Settings** app, select the **Accounts** tile and then select **Access work or school**.
4. In the **Access work or school** section, select the **Connected to Contoso's Azure AD** link and then select **Info**.
5. In the **Managed by Contoso** dialog box, select **Sync**. Wait for the synchronization to complete. 
6. Select the left arrow in the upper left corner twice. Select **Update & Security**.
7. Notice the red banner **Some settings are managed by your organization**. 
8. Select **Advanced options**. Notice that you are not able to pause updates.
9. Select **Delivery Optimization**. Notice that **Allow downloads from other PCs** is not available.
10. In the navigation pane, select **Windows Insider Program**.
11. On the **Windows Insider Program** tab, notice the **Some settings are hidden or managed by your organization** banner.
12. Notice that the **Get started** button is unavailable. Close the **Settings** app.
13. Close all open apps and windows.

_Note: These labs are configured to prevent Windows Updates from being applied to avoid delays and unintentional impact during the labs._

**END OF LAB**