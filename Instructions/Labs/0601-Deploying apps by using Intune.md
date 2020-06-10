# Practice Lab - Deploying apps by using Intune

## Summary

In this lab, you will practice creating and deploying  a Line of Business app using Intune and the Company Portal.

### Scenario

A. Datum Corporation’s has decided to manage all developers in the company using Azure Active Directory (Azure AD) and Intune. Many of the developers use Remote Desktop Protocol (RDP) on a daily basis to connect to various servers when developing apps for A. Datum. They want a solution where they can choose the servers from a list and easily connect to them instead of entering server names each time they need to connect. You have found Remote Desktop Connection Manager from Microsoft that should fit their needs. As part of evaluating Intune, you will make this app available from the Company Portal. 

#### Task 1: Verify installed apps on device before deployment 

1.  Switch to **LON-CL4**, and sign in with
    **DiegoS\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  Select **Start** and then select the **Settings** app.

3.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, select **Programs and Features** on the right under Related Settings.

4.  In the **Program and Features** window, verify that **Remote Desktop
    Connection Manager 2.7** is not listed.

5.  Close all Windows.

#### Task 2: Add LON-CL4 to the A.Datum Developer Devices Group

1. Sign in to **LON-CL3** as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

2.  In Microsoft Edge, navigate to https://portal.azure.com and select
    **Azure Active Directory**.

3.  On the **Azure Active Directory** blade, in the navigation pane, select
    **Groups**.

4. Select **A. Datum developer devices** and then select **Members**. Select **+Add Members**. 
    In the Add Members panel, select **MARKETING-###** and then select **Select**. 

#### Task 3: Create a line-of-business (LOB) app type based on the scenario 

1.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Client apps**.

2.  In the **Client apps** blade, select **Apps**. In the details pane, select **+
    Add**.

3.  In the **Add app** blade, select the **Select an app type** under **App
    type** and select **Line-of-business app**.

4.  Select **App package file Select file**, and in **App package file** blade,
    select the folder icon next to **Select a file**.

5.  In the Open dialog box, browse to **C:\\Software** and select **rdcman.msi**.
    Then select **Open** and **OK**.

6.  Back on the Add app blade, select **App information Configure**. Configure
    the following options:

-   Name: **Remote Desktop Connection Manager**

-   Description: **App for developers in A. Datum**

-   Publisher: **Microsoft**

-   Category: **Computer Management**

7.  Scroll down to the bottom and select **Logo Select image** and in Logo blade,
    select the folder icon next to **Select a file**.

8.  In the **Open** dialog box, browse to **C:\\Software** and select
    **rdcman-icon.jpg**. Then select **Open** and **OK**.

9.  Select **Next** and then select **Add** to create the app in Intune. Notice the
    app is not yet available. 

10. On the **Client apps – Apps** blade, select **Audit logs**.  As the RDC app
    is being created, you will see log entries created.  When there are 4 entries,
    the app should be available.  This can take up to a couple minutes.

11.  On the **Client apps – Apps** blade, in the details pane, select **Remote
    Desktop Connection Manager**.

12.  On the **Remote Desktop Connection Manager** blade, select **Assignments**
    and on the **Remote Desktop Connection Manager - Assignments** blade, select
    **Add group**.

13.  On the **Add group** blade, select **Select assignment type** under
    **Assignment type** and select **Available for enrolled devices**.

14.  Select **No groups selected Included Groups** and on the **Assign** blade,
    select **Make this app available to all users with enrolled devices** to **Yes**
    amd select **Ok** twice. 

15. Back on the **Remote Desktop Connection Manager - Assignments** blade, select
    **Save**. In the details pane verify that **All users** is listed
    under **Available for enrolled devices**.

#### Task 4: Install the Company Portal on a Windows 10 device

1.  On **LON-CL3**, On the taskbar, select **Microsoft Edge**, and navigate to
    <https://businessstore.microsoft.com>.

2.  Sign in to the store as **Admin\@yourtenant.onmicrosoft.com** with your tenant password.

3.  In the **Search field** on the right, type **Company Portal** and press
    **Enter**. Accept the consent dialog if prompted.

4.  Select **Company Portal** in the results list and select **Get the App**.

5.  Accept any agreements you are prompted with. On the Thanks for your order
    dialog, select **Close**.

6.  On the right side, under Unlimited licenses available, select **Assign to
    Users**.

7.  On the **Assign to people** dialog, type
    **DiegoS\@yourtenant.onmicrosoft.com**. Select **Assign** and then **Close**.

8.  Switch to **LON-CL4** and sign in as **DiegoS\@yourtenant.onmicrosoft.com.**

9.  On the taskbar, select **Microsoft Edge** and navigate to
    <https://businessstore.microsoft.com>.

10. Select **Sign In**. Login as **DiegoS\@yourtenant.onmicrosoft.com** if it does
    not by default.

11. In the search box, type **Company Portal** and press **Enter**.

12. Select **Company Portal** in the results list and select **Install**.

13. In the Windows Store app, select **Install**. This process should take about
    a minute.

14. **Close** the Microsoft Store Window.

#### Task 5: Install an app through the Company Portal

1.  On **LON-CL4**, on the taskbar, select **Start** and in the apps list under
    **C**, select **Company Portal**. You will be signed in to the Company Portal
    automatically using Single-Sign-On, because the device is Azure AD joined.

2.  In the **Company Portal** under **Apps**, select **Remote Desktop Connection**. On the **Remote Desktop Connection Manager** page, select
    **Install**.

3.  Wait for the app installation files to download and for the installation to
    complete. When it says **Installed**, the Remote Desktop Connection Manager
    is installed.

#### Task 6: Verify on device that app is installed

1.  On **LON-CL4**, on the taskbar, select **Start** and then select the
    **Settings** app.

2.  In the **Settings** app, select the **Apps** tile and on the **Apps &
    features** page, scroll down and verify that **Remote Desktop Connection
    Manager** is listed.

3.  Close the **Settings** app and select the **Start** button.

4.  In the app list, scroll down to **R** and select **Remote Desktop Connection
    Manager** and verify that the app opens.

5.  Close all open windows.

#### Task 7: Verify app installation in Intune

1.  Switch to **LON-CL3**.

2.  In the Azure portal, select **Intune** in the navigation pane, and then on
    the **Microsoft Intune** blade, select **Client apps**.

3.  On the **Client apps** blade, select **App install status** under
    **Monitor**. In the details pane, select **Remote Desktop Connection
    Manager**.

    _Note: If you see no data, select the **Load more** link._

4.  In the details pane, under **Device status** and under **User status**,
    **1** is displayed under Installed. This indicates that the app is installed
    on one device and for one user.

    _Note: The graph may take time before it's updated.  If it still displays
    **0**, continue on. 

5.  Select **Device install status** to the left of the blue circle. In the
    details pane, you can see the devices that the app is installed on, and also
    the name of the user. The **DEVICE NAME** column should list **MARKETING-###** and
    the **USER NAME** column should list DiegoS in the **STATUS** column should
    say **Installed**. This mean that the app is installed on LON-CL4 VM by the
    user DiegoS.

6.  In the Azure portal, select **Microsoft Intune** in the breadcrumb navigation, and then on
    the **Microsoft Intune** blade, select **Devices**.

7.  On the **Devices** blade, select **All devices** and then in the details
    pane, select **MARKETING-###**.

8.  On the **MARKETING-###** blade, select **Managed Apps** under
    **Monitor**.

9.  On the **MARKETING-### - Managed Apps** blade, in the details pane,
    select **Remote Desktop Connection Manager**.

10. On the **Remote Desktop Connection Manager - Installation details** blade,
    you can see the entire lifecycle of the application, that is - when it was
    created, assigned, installation time and status and the last time the device
    checked in (synced with Intune).

**END OF LAB**
