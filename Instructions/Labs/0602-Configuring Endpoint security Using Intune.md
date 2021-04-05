# Practice Lab: Configuring Endpoint security using Intune

## Summary

In this lab, you will create a policy to configure Microsoft Defender for managed devices in Intune.

### Scenario

You've been asked to ensure that the Contoso Developers Group have Microsoft Defender correctly configured. It's been requested that:
* Tamper protection be prevented
* Hide the Account protection, App and browser control, Device security, Device performance and health, and Family options areas in the Windows Security app
* Contact name and phone number must be added. 
* Real-time protection, Remediation, and scan settings are also to be configured.

Settings will be verified by testing on an enrolled device, SEA-WS2 and a non-enrolled device, SEA-CL1.

### Task 1: Configure Windows Security Experience in Intune

1. Sign in to **SEA-CL1** as **Contoso\\Administrator** with the password **Pa55w.rd**. 
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the  address bar, and then press **Enter**. 
4. Sign in as as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.
5. From the navigation pane select **Endpoint security**, then select **Antivirus**.
6. On the **Endpoint security |Antivirus** pane, select **Create Policy**.
7. In the **Create a profile** pane, select **Windows 10 and later** for Platform. In the Profile  list, select **Windows Security experience**. Then select **Create**.
8. On the Basics tab, in the **Name** field, enter **Windows Security Settings**. Select **Next**.
9. On the **Configuration settings** tab, expand the **Windows Security** section. 
10. Under Windows security, configure the following settings:

    - Enable tamper protection to prevent Microsoft Defender from being disabled: Enable

    - Hide the Account protection area in the Windows Security app: Yes

    - Hide App and browser control are in the Windows Security app: Yes

    - Hide the Device security area in the Windows Security app: Yes

    - Hide the Device performance and health area in the Windows Security app: Yes

    - Hide the Family options area in the Windows Security app: Yes

11. Next to **Organization's support contact information** select **Display in app and in notifications**.
12. In the **Contact name** field, enter **Contoso IT**.
13. For **Phone number**, enter **555-1234** and then select **Next**.
14. On the **Scope tags** page, select **Next**.
15. On the **Assignments** tab, select **Add groups**. Choose the **Contoso Developers Devices** group and then choose **Select**.
16. Select **Next** and then on the **Review + Create** tab, review the information and select **Create**.

### Task 2: Configure Microsoft Defender Antivirus policy in Intune

1. On the **Endpoint security |Antivirus** pane, select **Create Policy**.
2. In the **Create a profile** pane, select **Windows 10 and later** for Platform. In the Profile  list, select **Microsoft Defender Antivirus**. Then select **Create**.
3. On the Basics tab, in the **Name** field, enter **Microsoft Defender Antivirus Settings**. Select **Next**.
4. On the **Configuration settings** tab, expand the **Real-time protection** section. 
5. Under **Real-time protection**, configure the following settings:

   - Turn on real-time protection: Yes

   - Monitor for incoming and outgoing files: Only monitor incoming files

   - Scan all downloaded files and attachments: Yes

6. On the **Configuration settings** tab, expand the **Remediation** section. 
7. Under **Remediation**, configure the following settings:

   - Number of days to keep quarantined malware: 60

   - Submit samples consent: Always prompt

8. On the **Configuration settings** tab, expand the **Scan** section. 
9. Under **Scan**, configure the following settings:

   - Run daily quick scan at: 12 PM

   - Check for signature updates before running scan: Yes

10. On the **Configuration settings** tab, select **Next**.
11. On the **Scope tags** page, select **Next**.
12. On the **Assignments** tab, select **Add groups**. Choose the **Contoso Developers Devices** group and then choose **Select**.
13. Select **Next** and then on the **Review + Create** tab, review the information and select **Create**.


### Task 3: Sync the managed devices

1. In the Microsoft Endpoint Manager admin center, select **Devices** and then select **All devices**.
2. On the **Devices | All devices** pane, select **SEA-WS2** and then on the **SEA-WS2** blade, select **Sync** on the toolbar, and then select **Yes**. Wait for 3-4 minutes for the sync to complete.
3. Close Microsoft Edge.

### Task 4: Verify the configuration

1. On **SEA-CL1**, in the notification area, right-click the **Windows Security** icon and select **View security dashboard** to open Windows Security. Notice that all security options are displayed. This is because SEA-CL1 is not enrolled to Intune.
2. Close **Windows Security**.
3. Switch to **SEA-WS2**, and sign in as **Diego Siciliani** with the PIN **102938**.
4. In the notification area, right-click the **Windows Security** icon and select **View security dashboard** to open Windows Security. Notice that all of the restricted areas as configured in the Intune policy are not displayed. SEA-WS2 is enrolled in Intune and has been applied the security settings.
5. Close **Windows Security** and sign out of **SEA-WS2**.

**Results**: After completing this exercise, you will have successfully created and applied a policy to configure Microsoft Defender for managed devices in Intune.

**END OF LAB**