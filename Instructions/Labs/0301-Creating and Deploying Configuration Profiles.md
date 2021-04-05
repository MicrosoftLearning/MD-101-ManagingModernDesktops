# Practice Lab: Creating and Deploying Configuration Profiles

## Summary

In this lab, you will use Microsoft Intune to create and apply a Configuration profile for a Windows 10 device.

## Exercise 1: Create and apply a Configuration profile

### Scenario

You need to use Azure Active Directory (Azure AD) and Intune to manage members of the Developers department at Contoso . You have been asked to evaluate the solutions that would enable the users to work effectively and securely on Windows 10 devices. Diego Siciliani has volunteered to help you test and evaluate the solution and provide feedback. He has also given you some initial requirements that must be included and applied to the developer's Windows 10 devices:

-   The Gaming section in Settings should not be visible.
-   The Privacy section in Settings should be restricted as much as possible.
-   The C:\DevProjects folder must be excluded from Windows Defender.
-   The process devbuild.exe must be excluded from Windows Defender.
-   Most used apps and Recently added apps should not be displayed on the Start menu.


### Task 1: Verify device settings before enrollment

1. Sign in to **SEA-WS2** as **Admin** with the password of **Pa55w.rd**.
2. On **SEA-WS2**, on the taskbar, select **Start** and then select **Settings**.
3. In **Settings**, verify that you can see the **Gaming** tile.
4. Select **Privacy** and verify that you can see several customization options.
5. Select the left arrow in the upper left corner to go back to the main Windows Settings page.
6. Select the **Personalization** tile and then in the navigation pane, select **Start**. Verify that **Show recently added apps** and **Show most used apps** are both set to **On**.
7. Select the left arrow in the upper left corner to go back to the main Windows Settings page.
8. In the **Settings** app, select **Update and Security**.
9. On the **Update & Security** page, select **Windows Security** and then **Open Windows Security**.
10. On the **Windows Security** page, select the **Open Navigation** button and then select **Virus & threat protection**.
11. On the **Virus & threat protection** page, under **Virus & threat protection settings**, select **Manage settings** . Scroll down to **Exclusions** and select **Add or remove exclusions**.
12. On the **Exclusions** page, verify that no exclusions have been configured.
13. Close the **Windows Security** window.
14. On the Settings page, select the left arrow in the upper left corner to go back to the main Windows Settings page.

### Task 2: Join SEA-WS2 to Azure AD and Enroll in Intune 

1. On **SEA-WS2**, with the **Settings** app still open, navigate to the **Accounts** page. 
2. Select **Access work or school**. In the **Access work or school** section, select **Connect**.
3. In the **Microsoft account** window, on the **Set up a work or school account** page, select **Join this device to Azure Active Directory**.
4. On the **Sign in** page, type **DiegoS\@yourtenant.onmicrosoft.com** and select **Next**.
5. On the **Enter password** page, enter the default Tenant password and then select **Sign in**.
6. On the **Make sure this is your organization** dialog box, select **Join**.
7. On the **You’re all set!** page, select **Done**.
8. In the **Access work or school** section, verify that Connected to Contoso's Azure AD is displayed.
9. Close the Settings window.

### Task 3: Sign in to SEA-WS2 with an Azure AD account

1. Sign out of **SEA-WS2**.
2. Select **Other user**, and in the **Email address** field type **DiegoS\@yourtenant.onmicrosoft.com**.
3. In the Password field, enter the default tenant password and then press **Enter**.
4. At the **Use Windows Hello with your account** page, select **OK**.
5. On the **More information required** page, select **Next**.
6. On the **Keep your account secure** page, select **I want to set up a different method**.
7. In the **Choose a different method** dialog box, select **Phone** and then select **Confirm**.
8. On the **Phone** page, in the **Enter phone number** field, enter your mobile phone number which is able to receive text messages. Select **Next**.
9. When you receive the verification code, enter the code on the Phone page and then select **Next**.
10. On the verification page, select **Next** and then select **Done**.
11. On the **Set up a PIN** page, in the **New PIN** and **Confirm PIN** boxes, type **102938** and then select **OK**.
12. On the **All set!** page, select **OK**.

### Task 4: Create device profile based on scenario

1. Switch to **SEA-CL1**.
2. On **SEA-CL1**, on the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. In the Microsoft Endpoint Manager admin center, select **Devices** from the navigation bar.
6. On the **Devices | Overview** page, select **Configuration Profiles**.
7. On the **Devices | Configuration profiles** blade, in the details pane, select **Create profile**.
8. In the **Create a profile** blade, select the following options, and then select **Create**:

   -   Platform: **Windows 10 and later**

   -   Profile: **Device restrictions**

9. In the **Basics** blade, enter the following information, and then select **Next**:

   -   Name: **Contoso Developer - standard**

   -   Description: **Basic restrictions and configuration for Contoso Developers.**

10. On the **Configurations settings** blade, expand **Control Panel and Settings**. 
11. Select **Block** next to the **Gaming** and **Privacy** options.
12. On the **Device restrictions** blade, expand **Start**. Scroll down and select **Block** next to **Most used apps**, **Recently added apps** and **Recently opened items in Jump Lists**.
13. On the **Device restrictions** blade, scroll down and expand **Microsoft Defender Antivirus**. 
14. Under **Microsoft Defender Antivirus,** scroll down and expand **Microsoft Defender Antivirus Exclusions**.
15. Under **Microsoft Defender Antivirus Exclusions** in the **Files and folders** box, type the following:  
    **C:\\DevProjects**.
16. In the **Processes** box, type the following:  
    **DevBuild.exe**. 
17. Then select **Next** three times until you reach the **Review + create** blade. Select **Create**.

### Task 5: Create the Contoso Developer device group

1. In the Microsoft Endpoint Manager admin center, in the navigation pane, select **Groups**.
2. On the **Groups | All groups** blade, select **New group**.
3. On the **New Group** blade, enter the following information:

   -   Group type: **Security**

   -   Group name: **Contoso Developer devices**

   -   Group description: **All Windows 10 devices in Contoso Developer department**

   -   Membership type: **Assigned**

4. Under **Members**, select **No members selected**. 
5. On the **Add members** blade, in the **Search** box type **Sea**. Select **SEA-WS2** and then choose **Select**.
6. On the **New Group** blade, select **Create**. 
7. On the **Groups | All groups** blade, verify that the **Contoso developer devices** group is displayed.

### Task 6: Create a dynamic Azure AD device group

1. On the **Groups | All Groups** blade, on the details pane, select **New group**.

2. On the **Group** blade, provide the following values:

   -   Group type: **Security**

   -   Group name: **Windows Devices**

   -   Membership type: **Dynamic Device**

3. Under the **Dynamic Device Members** section, select **Add dynamic query**. 

4. On the **Dynamic membership rules** blade, in the **Rule syntax** section, select **Edit**. 
    
5. In the **Edit rule syntax** text box, add the following simple membership rule and select **OK**.

   ```powershell
   device.deviceOSType -contains "Windows"
   ```
6. On the **Dynamic membership rules** blade, select **Save**.
7. On the **New Group** page, select **Create**.

### Task 7: Assign a Configuration profile to Windows 10 devices

1. In the Microsoft Endpoint Manager admin center, select **Home** in the breadcrumb navigation menu and then select **Devices**. 
2. On the **Devices | Overview** blade, select **Configuration profiles**.
3. On the **Devices | Configuration profiles** blade, in the details pane, select the **Contoso Developer – standard** profile.
4. On the **Contoso Developer – standard** blade, select **Properties**. Scroll down to the **Assignments** section, and select **Edit**.
5. In the **Assignments** section, select **Select groups to include**.
6. On the **Select groups to include** blade, in the **Search** box, select **Contoso Developer devices** and then select **Select**.
7. Back on the **Device restrictions** blade, select **Review + save**, then select **Save**.
8. In the Microsoft Endpoint Manager admin center, select **Devices** in the breadcrumb navigation menu.

### Task 8: Verify that Configuration profile is applied

1. Switch to **SEA-WS2**.
2. On **SEA-WS2**, on the taskbar, select **Start** and then select **Settings**.
3. In **Settings**, select the **Accounts** tile and then select **Access work or school**.
4. In the **Access work or school** section, select the **Connected to Contoso's Azure AD** link and then select **Info**.
5. In the **Managed by Contoso** page, select **Info**. Scroll down and then under Device sync status, select **Sync**. Wait for the synchronization to complete. 

   _Note: The sync progress should only take a few seconds, however it may take up to 15 minutes before the profile is applied to Windows 10 device. Signing out or rebooting can accelerate this process._

6. Close the **Settings** app, and open it again. Verify that the **Gaming** tile has been removed.
7. Select **Privacy** and notice that most of the privacy settings are now hidden. Select the left arrow in the upper left corner.
8. Select the **Personalization** tile and then select **Start**. Verify that **Show recently added apps** and **Show most used apps** are set to **Off**. Select the left arrow in the upper left corner.
9. In the **Settings** app, select **Update and Security**.
10. On the **Update & Security** page, select **Windows Security** and then **Open Windows Security**.
11. On the **Windows Security** page, select **Virus & threat protection**.
12. On the **Virus & threat protection** page, select **Manage settings** under **Virus & threat protection settings**. Scroll down to **Exclusions** and select **Add or remove exclusions**.
13. On the **Exclusion** page, verify that **C:\\DevProjects** and **DevBuild.exe** are displayed.
14. Close the **Windows Security** page and then close the **Settings** app.

**Results**: After completing this exercise, you will have successfully created and assigned a Configuration profile for Windows 10 devices.

## Exercise 2: Modify an assigned Configuration profile policy  

### Scenario

There was an exception to Contoso's policy that specifies that members of the Developer department should not have the Privacy options blocked in Settings on their devices. This change should be implemented and tested.

### Task 1: Change settings in assigned profile

1. On **SEA-CL1**, in the Microsoft Endpoint Manager admin center, select **Devices | Configuration profiles** in the breadcrumb navigation pane. 
2. On the **Devices | Configuration profiles** blade, in the details pane select **Contoso Developer -  standard**.
3. On the **Contoso Developer - standard** blade, select **Properties**. 
4. On the **Contoso Developer - standard|Properties** blade, on the **Configuration settings** line, select **Edit**.
5. On the **Configuration settings** page, expand **Control Panel and Settings**. 
6. Next to **Privacy**, select **Not configured**. 
7. Select **Review + save**, and then select **Save**.

### Task 2: Force device synchronization from Microsoft Endpoint Manager admin center

1. On **SEA-CL1**, in the Microsoft Endpoint Manager admin center, select **Devices** in the navigation pane and then select **All devices**.
    
2. In the details pane, select **SEA-WS2**. 
    
3. On the **SEA-WS2** blade, select **Sync** and when prompted select **Yes**. 

   _Note: Intune will contact the device and tell it to synchronize all policies. This may take up to 5 minutes._

### Task 3: Verify profile changes on SEA-WS2

1. Switch to **SEA-WS2**.
2. On **SEA-WS2** and on the taskbar, select **Start** and then select the **Settings** app.
3. In the **Settings** app, select **Privacy** and verify that all of the customization options are back.
4. Close all open windows.

**Results**: After completing this exercise, you will have successfully modified an assigned Configuration profile and verified the changes.

**END OF LAB**