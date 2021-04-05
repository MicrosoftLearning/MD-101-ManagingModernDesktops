# Practice Lab: Configuring Enterprise State Roaming

## Summary

In this lab, you will enable Enterprise State Roaming in Azure AD. 

### Scenario

Enterprise State Roaming in Azure AD provides the ability for user settings and application settings to be synchronized to the cloud. Diego Siciliani works with multiple Windows devices and would like to have all user settings to be the same on each device. You need to enable and test Enterprise State Roaming to address Diego's requirements.


### Task 1: Enable Enterprise State Roaming

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://aad.portal.azure.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. In the Azure Active Directory admin center, in the navigation pane, select **Azure Active Directory**.
6. On the **Contoso** blade, in the navigation pane, select **Devices**.
7. On the **Devices** blade, make a note of devices that are listed in the details pane. In the Devices navigation pane, select **Enterprise State Roaming**.
8. On the **Devices|Enterprise State Roaming** blade, in the details pane, next to **Users may sync settings and app data across devices** section, select **Selected**.
9. Select **Selected No member selected**, select **Add** and type **Diego Sicilian** in the text box.
10. Select **Diego Siciliani** and then select **Select**.
11. Select **OK**, and then select **Save**. Close the **Devices | Enterprise State Roaming** blade.

    _Note: By performing this task, you enabled Enterprise State Roaming for Diego Siciliani._


### Task 2: Verify sync is enabled on SEA-WS2

1. Switch to **SEA-WS2** and sign in as **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password if you are not already signed in. 
2. On the taskbar, select **Start** and then select the **Settings** icon. 
3. Select **Accounts** and then select Access work or school. 
4. In the **Access work or school** page, select **Connected to Contoso's Azure AD** and then select **Info**.
5. On the **Managed by Contoso** page, scroll down and then select **Sync**.
6. Select the Back button to return to the Accounts page.
7. In the **Accounts** navigation pane, select **Sync your settings**.
8. On the **Sync your settings** page, verify that **Sync settings** is set to **On**. 

   _**Important**: If Sync settings is set to off and it is greyed out, restart the device and sign back in. If the settings remain greyed out then you must rejoin to Azure AD. This is due to an issue with ESR being enabled after devices have been enrolled. If this occurs, continue with Task 3, otherwise skip Task 3 and continue with Task 4._


### Task 3: Re-enroll SEA-WS2 (only perform if needed)

1. In Accounts, select **Access work or school**. Select **Connected to Contoso's Azure AD** and
    select **Disconnect**. Select **Yes** and then select **Disconnect** to confirm.
2. In the **Windows Security** dialog enter **Admin** as **Email Address** and **Pa55w.rd** as **Password**. Select **OK**.
3. On the **Restart your PC** dialog box, select **Restart now**. 
4. After SEA-WS2 has restarted, sign in as **Admin**, with the password **Pa55w.rd**.
5. Select **Start**, type **View advanced system settings** and press **Enter**.
6. In the **Advanced** tab under **User Profiles** select **Settings**.
7. In the **User Profiles** window select **Account Unknown** and then select **Delete**. Confirm with **Yes** and then select **OK** twice.
8. Select **Start**, select **Settings**, and then select **Accounts**. 
9. Select **Access work or school** and select **Connect**.
10. In the **Microsoft account** window, select **Join this device to Azure Active Directory**.
11. On the **Sign in** page, type **diegos\@yourtenant.onmicrosoft.com** and then select **Next**.
12. On the **Enter password** page, enter the tenant password and select **Sign in**.
13. On the **Make sure this is your organization** dialog, select **Join**.
14. On the **You're all set!** page, select **Done**.
15. Sign out of SEA-WS2.
16. Sign in to **SEA-WS2** as **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password.
17. At the **Use Windows Hello with your account** page, select **OK**.
18. At the **Enter code** page, enter the code that has been texted to your mobile device and then select **Verify**.
19. At the **Set up a PIN** dialog box, in the **New PIN** and **Confirm PIN** boxes, type **102938** and then select **OK**.
20. On the **All set!** page, select **OK**.

### Task 4: Test Enterprise State Roaming

1. On SEA-WS2, on the taskbar, select **Start** and then select the **Settings** icon. 
2. Select **Accounts** then select **Sync your settings**.
3. On the **Sync your settings** page, verify that **Sync settings** is set to **On**. 
4. Close the Settings window.
5. On SEA-WS2 perform the following customizations:

   - Pin **Feedback Hub**, **Calculator**, and **Calendar** to the Start screen.

   - Pin **Maps** to the taskbar

   - Unlock the **taskbar** and move it to the right side of the screen.

6. On **SEA-WS2**, on the taskbar, select **Microsoft Edge** and in the address bar, type **www.microsoft.com/learn**, and then press **Enter**. 
7. When the page loads, select the star and the end of the address bar (or press CTRL+D). In the **Favorite added** pop-up, select **Done**.
8. Close Microsoft Edge.
9. Sign out of **SEA-WS2**.
10. Switch to **SEA-WS3**. 
11. Sign in to **SEA-WS3** as **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password.
12. At the **Use Windows Hello with your account** page, select **OK**.
13. At the **Enter code** page, enter the code that has been texted to your mobile device and then select **Verify**.
14. At the **Set up a PIN** dialog box, in the **New PIN** and **Confirm PIN** boxes, type **102938** and then select **OK**.
15. On the **All set!** page, select **OK**.
16. On the taskbar, select **Microsoft Edge**. 
17. In **Microsoft Edge**, press CTRL+I to view favorites. Verify if the Microsoft Learn favorites page is already synced from **SEA-WS2**. 

    _Note: It can take several minutes for settings to sync. If the favorites option doesn't show, try rebooting and signing back in as DiegoS\@yourtenant.onmicrosoft.com._

18. Sign out of **SEA-WS3**.

**Results**: After completing this exercise, you will have successfully enable Enterprise State Roaming in Azure AD.

**END OF LAB**