# Practice Lab: Configuring Disk Encryption Using Intune

## Summary

In this lab, you will configure BitLocker disk encryption using Intune.

### Scenario

It's been determined that all the information on SEA-WS2 should be encrypted. You've been asked to configure full disk encryption on SEA-WS2 and require additional authentication at startup.

### Task 1: Configure device configuration policy in Intune

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**. 
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the  address bar, and then press **Enter**. 
4. Sign in as as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.
5. In the Microsoft Endpoint Manager admin center, select **Devices** from the navigation bar.
6. On the **Devices | Overview** page, select **Configuration Profiles**.
7. On the **Devices | Configuration profiles** blade, in the details pane, select **Create profile**.
8. In the **Create a profile** page, select the following options, and then select **Create**:

   -   Platform: **Windows 10 and later**

   -   Profile: **Endpoint protection**
9. On the **Basics** page, enter the following information, and then select **Next**:

   -   Name: **Contoso BitLocker**

   -   Description: **Enable BitLocker for all devices**

10. On the **Configurations settings** page, expand **Windows Encryption** and then configure the following options:

    - Encrypt devices: **Require**

    - Additional authentication at startup: **Require**

11. On the **Configurations settings** page, select **Next**.
12. On the **Assignments** tab, choose **Select groups to include**. Select **Contoso Developer Devices**, choose **Select**, and then select **Next** twice.
13. On the **Review + create** page, select **Create**.
14. Close all open windows on **SEA-CL1**.

### Task 2: Verify and enable BitLocker settings

1. On **SEA-WS2**, sign in as **Diego Siciliani** with the PIN **102938**.
2. On the taskbar, select **Start** and then select the **Settings** app.
3. In the **Settings** app, select the **Accounts** tile and then select **Access work or school**.
4. In the **Access work or school** section, select the **Connected to Contoso's Azure AD** link and then select **Info**. Select **Sync**.
5. Select the **Encryption needed** notification.

   _Note: It may take some time until the notification shows up._

6. On the **Are you ready to start encryption?** dialog select the first checkbox and select **Yes**.
7. On the **Choose how to unlock your drive at startup?** page, select **Enter a password**
8. Enter **Pa55w.rd** in the **Enter your password** and **Reenter your password** boxes, and then select **Next**.
9. On the **How do you want to back up your recovery key?** page, select **Save to your Azure AD account**. Then select **Next**.
10. On the **Choose how much of your drive to encrypt** page, select **Encrypt used disk space only** and select **Next**.
11. On the **Choose which encryption mode to use** page, ensure that **New encryption mode (best for fixed drives on this device)** is selected, and then select **Next**.
12. On the **Are you ready to encrypt this drive** page, select **Continue**. Wait for the encryption to complete.
13. At the **Encryption of C: is complete** message, select **Close**, and then restart **SEA-WS2**.
14. When **SEA-WS2** restarts, type **Pa55w.rd** and press **Enter** to unlock the drive.

### Task 3: Verify BitLocker protection

1. Sign in to **SEA-WS2** as **Diego Siciliani** with the PIN **102938**.
2. On the taskbar, select **File Explorer** and then select **This PC**.
3. In the navigation pane, right-click **Local Disk (C:)** and then select **Manage BitLocker**.
4. In the **BitLocker Drive Encryption** window, ensure that you see **C: BitLocker on** status. This means that drive is encrypted. 
5. Close all open windows and sign out of **SEA-WS2**.

**Results**: After completing this exercise, you will have successfully configured BitLocker using Intune.

**END OF LAB**