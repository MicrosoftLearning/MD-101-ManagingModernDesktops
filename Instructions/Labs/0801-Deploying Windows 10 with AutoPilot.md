# Practice Lab: Deploying Windows 10 with Autopilot

## Summary

In this lab you will learn how provision a Windows 10 device with Autopilot using User-driven mode.

### Scenario

Contoso IT is planning to roll out a deployment of new Windows 10 devices using Autopilot. The devices have a default installation of Windows 10. Users should be able to connect the device, turn it on, and answer minimal questions during the OOBE, using their Azure AD credentials to sign in. The process should automatically enroll and join the Azure AD domain. You have been asked to configure and test the experience using the SEA-WS4, which you recently installed and configured using Hyper-V.

### Task 1: Create group in Azure AD

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**. 
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, in the address bar, type **https://aad.portal.azure.com**, and then press **Enter**. If prompted, sign in with your **Admin\@yourtenant.onmicrosoft.com** and the default tenant password.
4. In the navigation pane, select **Azure Active Directory**.
5. Under **Manage**, select **Groups**.
6. In the **Groups | All groups** blade, select **New group**.
7. In the **New Group** blade, in the **Group type** list, select **Security**.
8. In the **Group name** box, type **IT Devices**.
9. In the **Group description** box, type **IT Department Devices**.
10. In the **Membership type** list, select **Dynamic Device**.
11. Select **Add dynamic query**.
12. On the **Dynamic membership rules** blade select **Edit** above the **Rule syntax** box.
13. In the Edit rule syntax text box, add the following simple membership rule and select **OK**.

   ```powershell
   (device.devicePhysicalIDs -any (_ -contains "[ZTDId]"))
   ```

14. Select **Save** to close **Dynamic membership rules**, and then select **Create** to create the group.

### Task 2: Generate a device-specific comma-separated value (CSV) file

1. Switch to **SEA-SVR2** and sign in as **Contoso\Administrator** with the password of **Pa55w.rd**.
2. Select **Hyper-V Manager** in the taskbar.
3. Under Virtual Machines, right-click **SEA-WS4** and select **Connect**.
4. On the **SEA-WS4** window, select **Start**. When the computer starts, maximize the window.
5. Sign in to **SEA-WS4** as **Administrator** with the password of **Pa55w.rd**.
6. Right-click **Start**, select **Windows PowerShell (Admin)**, and then select **Yes** at the **User Account Control** prompt.
7. At the Windows PowerShell command-line prompt, type the following cmdlet, and then press **Enter**:

   ```powershell
   Install-Script -Name Get-WindowsAutoPilotInfo
   ```

8. You will receive three prompts. Each time, type **Y**, and then press **Enter**.
9. At the Windows PowerShell command-line prompt, type the following cmdlet, and then press **Enter**:

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

10. When prompted, type **Y**, and then press Enter.
11. At the Windows PowerShell command-line prompt, type the following cmdlet, and then press **Enter**:

    ```powershell
    Get-WindowsAutoPilotInfo.ps1 -OutputFile C:\Computer.csv
    ```

12. At the Windows PowerShell command-line prompt, type the following command, press **Enter**, and then review the file content:

    ```powershell
    type C:\Computer.csv
    ```

13. At the Windows PowerShell command-line prompt, type the following command, press **Enter**. This will copy the file to SEA-SVR2:

    ```powershell
    copy c:\computer.csv \\sea-svr2\labfiles
    ```

14. Close the Windows PowerShell command prompt.

### Task 3: Work with a Windows Autopilot deployment profile

1. Switch to **SEA-CL1**. 
2. In **Microsoft Edge**, open a new tab and navigate to **https://endpoint.microsoft.com**. If prompted, sign in with your **Admin\@yourtenant.onmicrosoft.com**.
3. In the **Microsoft Endpoint Manager admin center**, select **Devices**.
4. In the **Device enrollment** section, select **Enroll devices**. 
5. In the details pane scroll down to **Windows Autopilot Deployment Program**, and then select **Devices**.
6. In the **Windows Autopilot devices** blade on the menu bar, select **Import**, select the **folder icon** and then browse to **\\\\SEA-SVR2\\Labfiles**, select **Computer.csv**, select **Open**, and then select **Import**. 

   _Note: The import process can take up to 15 minutes, but normally takes around 5 minutes._  

   _**Important**: After the process is complete, the device may not show. If this is the case, select the **Sync** button, wait a few minutes, and then select **Refresh**._

7. Select **X** to close the **Windows Autopilot devices** blade. 
8. On the Windows enrollment blade, in the details pane, select **Deployment Profiles**.
9. On the **Windows AutoPilot deployment profiles** blade, select **Create profile** and then select **Windows PC**.
10. In the **Basics** tab, in the **Name** text box, type **Contoso profile1**.
11. For **Convert all targeted devices to Autopilot** select **No**, and then select **Next**.
12. On the **Out-of-box experience (OOBE)** tab, ensure that the **Deployment mode** is set to **User-Driven**.
13. Ensure that **Join to Azure AD as** is set to **Azure AD Joined**.
14. Ensure that the following options are set:

    -   Microsoft Software License Terms: **Hide**

    -   Privacy Settings: **Hide**

    -   Hide change account options: **Hide**

    -   User account type: **Administrator**.

    -   Allow White Glove OOBE: **No**.

    -   Apply device name template: **No**.

15. Select **Next**.
16. On the **Assignments** tab, select **Add groups**.
17. Select the **IT Devices** group and select **Select**. Select **Next**.
18. On the **Review + create** blade, review the information and then select **Create**.

### Task 4: Reset the PC

1. Switch to **SEA-SVR2**. The SEA-WS4 computer should be still maximized.
2. On **SEA-WS4**, select **Start**, type **reset** and select **Reset this PC**.
3. Under **Reset this PC**, select **Get started**.
4. Select **Remove everything**, and then select **Local reinstall**.
5. Select **Next** and then select **Reset**.

   _Note: Normally this task is not required for new deployment of physical devices. The device’s autopilot info is either provided by the manufacturer or can be obtained from the device prior to the OOBE. For the purposes of this lab, we must initiate a reset to simulate a new device OOBE._

   _Note: This process can take 30-45 minutes and will reboot several times during the process._

### Task 5: Verify Autopilot deployment

1. At the **Welcome to Contoso** screen, enter **Aaron\@yourtenant.onmicrosoft.com** and select **Next**.
2. At the Password page, enter **Pa55w.rd1234** and select **Next**.
3. At the **Use Windows Hello with your account**, select **OK**.
4. On the **More information required** page, select **Next**.
5. On the **Keep your account secure** page, enter your phone number of a mobile device that can receive text messages, and then select **Next**.
6. In the **Enter code** page, enter the verification code and then select **Next**.
7. On the SMS verified message, select **Next** and then select **Done**.
8. On the **Setup up a PIN** dialog box, in the **New PIN** and **Confirm PIN** fields, enter **102938**, and then select **OK**.
9. On the **All set!** page, select **OK**.
10. Select **Start** and select **Settings**. 
11. Select **Accounts**, and then select **Access work or school**. Verify the device is connected to Contoso's Azure AD.
12. Select **Connected to Contoso's Azure AD** and select **Info**.
13. On the **Managed by Contoso** page, scroll down and then select **Sync**.
14. On **SEA-WS4**, close the **Settings** window.
15. Shut down **SEA-WS4** and close the SEA-WS4 window.
16. On SEA-SVR2, close Hyper-V Manager.
17. Switch to **SEA-CL1**.
18. In the Azure Active Directory admin center, select **Azure Active Directory** and then **Devices**. Note that the new device displays with an icon that indicates an Autopilot device. Also note that the Join Type is Azure AD joined with Aaron Nicholls as the owner.
19. On **SEA-CL1**, close Microsoft Edge.

**Results**: After completing this exercise, you will have provisioned a Windows 10 device with Autopilot using User-driven mode.

**END OF LAB**