# Practice Lab: Configure and Deploy Windows Information Protection Policies by using Intune

## Summary

In this lab, you will configure and apply a Windows Information Protection policy to provide application protection for non-managed Windows 10 devices.

### Task 1: Configure the MAM service

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd**. 
2. On the taskbar select **Microsoft Edge**, in the address bar type  **https://endpoint.microsoft.com**, and then press **Enter**.
3. Sign in as user **Admin\@yourtenant.onmicrosoft.com**, and use the tenant Admin password. If the **Stay signed in?** prompt appears, select **No**. 
4. In the navigation pane, select **Devices**.
5. In the **Devices** navigation pane, select **Enroll devices**.
6. On the **Enroll devices** page, select **Automatic Enrollment**.
7. On the **Configure** page, next to **MAM user scope**, select **All**, and then select **Save**.

### Task 2: Configure an App protection policy for Windows Information Protection

1. In the Microsoft Endpoint Manager admin center, in the navigation pane, select **Apps**.
2. Select **App protection policies**, select **Create policy** and select **Windows 10**.
3. In the **Name** text box, type **Windows 10 WIP policy**.
4. In the **Enrollment state** list, select **Without enrollment** and select **Next**.
5. On the **Targeted apps** tab, under **Protected apps**, select **Add**.
6. Select **Notepad** and **MsEdge - WIPMode-Allow-Enterprise AppLocker Policy File.xml**. Select **OK** and select **Next**.
7. On the **Required settings** tab, next to the **Windows Information Protection mode** option, select **Block** and then select **Next**. Note: Do not change the Corporate identity setting.
8. On the **Advanced settings** tab, in the **Network perimeter** section, select **Add**.
9. On the **Add network boundary** pane, configure the following and then select **OK**:

   - Boundary type: **Cloud resources**

   - Name: **SharePoint online**

   - Value: **yourtenant.sharepoint.com**

10. On the **Advanced settings** tab, next to **Show the enterprise data protection icon**, select **On** and then select **Next**.
11. On the **Assignments** tab, select **Next** and then select **Create**.

### Task 3: Deploy the policy

1. On the **Apps|App protection policies** page, in the details pane, select **Windows 10 WIP policy**.
2. On the **Windows 10 WIP policy** page, select **Properties**.
3. Scroll down and click **Edit** next to **Assignments**.
4. Select **+ Select groups to include**, select **Contoso_Marketing**, and then click **Select**.
5. Select **Review + save** and then select **Save**.
6. Close Microsoft Edge.

### Task 4: Create a test file

1. Sign in to **SEA-WS1** as **Admin** with the password of **Pa55w.rd**. Note that SEA-WS1 is not managed by Intune.
2. Right-click on the desktop and select **New**, and then select **Text Document**.
3. Rename the file to **Sample Document.txt**.
4. Open **Sample Document.txt**.
5. In the Notepad window, enter **This is a sample corporate file**.
6. Save and close the file.
7. On the taskbar select Microsoft Edge and then navigate to **https://yourtenant.sharepoint.com**.
8. Sign in as **ereeve\@yourtenant.onmicrosoft.com** with the password of **Pa55w.rd**.
9. If **Update your password** displays enter the following and then select **Sign in**:

   - Current password: **Pa55w.rd**

   - New password: **Pa55w.rd1234**

   - Confirm password: **Pa55w.rd1234**

10. If the Microsoft Edge Update password prompt displays, select **No thanks**.
11. On the top, click **Documents**.
12. From the desktop, drag and drop the **Sample Document.txt** file into the Documents library to upload the file.
13. Once uploaded, delete the **Sample Document.txt** file from the Desktop.
14. Close all open windows.

### Task 5: Add a corporate account to Windows 10

1. On SEA-WS1, on the **Start** menu, select **Settings**.
2. Select **Accounts** and then select **Access work or school**.
3. Under **Access work or school**, select **Connect**.
4. In the **Set up a work or school account** pane, enter **ereeve\@yourtenant.onmicrosoft.com** and then select **Next**.
5. Enter the password **Pa55w.rd1234**, and then select **Sign in**.
6. On the **More information required** page, select **Next**.
7. On the **Keep your account secure** page, enter your mobile phone number that is able to receive text messages and then select **Next**.
8. When you receive a text message, enter the provided code in the **Enter code** field and then select **Next**.
9. On the SMS verified message page, select **Next** and then select **Done**.
10. On the **Use Windows Hello with your account** page, select **OK**.
11. In the Windows Security prompt, in the **New PIN** and **Confirm PIN** fields, enter **102938**, and then select **OK**.
12. On the **Almost done** page, select **Next**.
13. On the **Windows Security** page, enter **Pa55w.rd** and then select **OK**.
14. On the Access work or school page, select **Work or school account** and then select **Info**. Scroll down and notice that the Connection info specifies that a wip.mam management server is being used.
15. Select the **Sync** button and then close the **Settings** window.

### Task 6: Verify the WIP policy

1. On the taskbar, select **Microsoft Edge**.
2. In **Microsoft Edge**, navigate to **https://yourtenant.sharepoint.com**.
3. If necessary, sign in as **ereeve\@yourtenant.onmicrosoft.com** with the password of **Pa55w.rd1234**.
4. Take note of the briefcase icon at the right side of the address bar. Select the icon and verify that this website is managed by the tenant.
5. On the top, select **Documents**.
6. Select **Sample Document.txt** and select **Download**.
7. At the bottom of the Edge browser, select **Save as**.
8. In the **Save As** dialog box, select the **Documents** folder.
9. Next to the File name, notice the drop down arrow that shows a briefcase. Select the **Work** briefcase icon and then select **Save**.
10. On the taskbar, open **File Explorer** and browse to the **Documents** folder.

   _Note: The briefcase icon in the file icon and the File ownership column indicates that the file is protected._

11. Open the **Sample Document.txt** file using **Notepad**. The file should open because Notepad is a managed app indicated in the policy. 
12. Close **Notepad**.
13. Attempt to open the **Sample Document.txt** file using **WordPad**. The file will not open and a dialog box will display to indicate that access to the file is denied. WordPad is not a managed app and is not be able to open protected files.
14. Open the **Sample Document.txt** file using Notepad. 
15. Open **WordPad** and attempt to copy and paste text from Notepad into WordPad. Notice that you are prevented from pasting content into WordPad.
16. Close all open windows and sign out of SEA-WS1.

**Results**: After completing this exercise, you will have successfully configured a Windows Information Protection policy to provide data protection.

**END OF LAB**