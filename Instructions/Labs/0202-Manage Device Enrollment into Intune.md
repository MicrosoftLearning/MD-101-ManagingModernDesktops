# Practice Lab: Manage Device Enrollment into Intune

## Summary

In this lab, you will prepare for device management using Microsoft Intune by reviewing and assigning licenses, configuring Windows automatic enrollment, and configuring enrollment restrictions. 

### Scenario

You need to prepare for device management using Microsoft Intune. First of all, you need to ensure that users are assigned appropriate licenses for device management. As a verification test, you will assign Aaron Nicholls the required licenses. You also need to ensure that any Windows 10 device that is joined or registered to Azure AD will automatically be enrolled into Intune. Finally you have been asked to ensure that members of the Sales group are restricted from enrolling personal Android and iOS devices into Intune.

### Task 1: Review and assign licenses for device management

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd**. 
2. On the taskbar select **Microsoft Edge**, in the address bar type **https://aad.portal.azure.com**, and then press **Enter**.
3. Sign in as user Admin@yourtenant.onmicrosoft.com, and use the tenant Admin password. If the **Stay signed in?** prompt appears, select **No**. The Azure Active Directory admin center opens.
4. In the Azure Active Directory admin center, in the navigation pane, select **Azure Active Directory**.
5. On the **Contoso** page, under **Manage**, select **Licenses**.
6. On the **Licenses** page, under **Manage**, select **All products**. Take note of the licenses that are available in the tenant. 
7. Select **Enterprise Mobility + Security E5**. Notice all the users that have been assigned this license. You can assign and remove licenses from this location.
8. Under **General**, select **Service plan detail**. Take note of the services included in the Enterprise Mobility + Security E5 license. Microsoft Intune is one of the supported services for this license.
9. In the Azure Active Directory admin center navigation pane, select **Users**.
10. Select **Aaron Nicholls**.
11. In the Aaron Nicholls pane, select **Edit**.
12. Under Settings, in the **Usage location** field, select **United States** and then select **Save**.

    _Note: Before you can assign a license to a user, the user must have a usage location set._

13. In the Aaron Nicholls navigation pane, select **Licenses**.
14. In the Aaron Nicholls|Licenses pane, select **Assignments**.
15. In the **Update license assignments** page, select both **Enterprise Mobility + Security E5** and **Office 365 E5**, and then select **Save**.
16. In the Azure Active Directory admin center navigation pane, select **Dashboard**.

### Task 2: Enable Windows Automatic Enrollment into Microsoft Intune

1. In **SEA-CL1**, open a new tab in **Microsoft Edge**, and then in the address bar type **https://endpoint.microsoft.com**, and then press **Enter**. The Microsoft Endpoint Manager admin center opens.
2. In the Microsoft Endpoint Manager admin center, select **Devices**.
3. On the Devices pane, select **Enroll devices**.
4. In the Enroll devices pane, select **Windows enrollment**.
5. In the General section, select **Automatic Enrollment**.
6. On the **MDM user scope** row, select **All** and then select **Save**.

   _**Note**: By performing this step, you enabled automatic enrollment into Intune for any Windows device that performs an Azure AD join._

### Task 3: Configure Enrollment Restrictions

1. In the Microsoft Endpoint Manager admin center, select **Devices**.
2. On the **Devices** pane, select **Enrollment restrictions**. Notice that you can specify Device type restrictions and Device limit restrictions.
3. In the details pane, select **Create restriction** and then select **Device type restriction**.
4. On the Create restriction page, in the Name box enter **Android and iOS Personal Device Restriction**. Select **Next**.
5. On the Platform settings page, under **Personally owned**, select **Block** for the following device types:

   - **Android Enterprise (work profile)**

   - **Android device administrator**
   
   - **iOS/iPadOS**

6. On the Platform settings page, select **Next**.
7. On the Scope tags page, select **Next**.
8. On the Assignments page, select **Select groups to include**.
9. Select **Sales** and then click **Select** and then click **Next**.
10. On the Review + create page, select **Create**.
11. In the Microsoft Endpoint Manager admin center, in the navigation pane, select **Home**.

**Results**: After completing this exercise, you will have successfully reviewed and assigned licenses, configured Windows automatic enrollment, and enabled and assigned enrollment restrictions.


**END OF LAB**