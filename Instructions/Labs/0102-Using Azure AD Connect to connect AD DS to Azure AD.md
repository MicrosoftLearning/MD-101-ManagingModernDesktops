# Practice Lab: Using Azure AD Connect to connect AD DS to Azure AD

## Summary

In this lab, you will configure synchronization between Active Directory Domain Services and Azure Active Directory.

### Scenario

Contoso Corporation is currently managing users in both AD DS and Azure AD as separate processes. This is time consuming and has led to inconsistent information. You have been tasked with addressing this issue by connecting the two directories by using the Azure AD Connect synchronization tool.

#### Task 1: Configure directory synchronization with Azure AD Connect

1. On **SEA-SVR1**, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2. On the taskbar, select **Internet Explorer**.
3. In the address bar, enter **http://www.microsoft.com/en-us/download/details.aspx?id=47594**.

    _**Important**: If you experience any problems with launching the download, add the https://download.microsoft.com website to your Trusted sites._

4. On the Microsoft Azure Active Directory Connect page, select **Download** and then select **Save**. Azure AD Connect downloads.
5. Select **Open folder** and then in the Downloads window, double-click **AzureADConnect.msi**.
6. In the **Microsoft Azure Active Directory Connect** wizard, on the **Welcome to Azure AD Connect** page, select the **I agree to the license terms and privacy notice** check box, and then select **Continue**.
7. On the **Express Settings** page, select **Customize**.
8. On the **Install required components** page, select **Install**.
9. On the **User sign-in** page, ensure that **Password Hash Synchronization** is selected, and then select **Next**.
10. On the **Connect to Azure AD** page, in the **USERNAME** and **PASSWORD** boxes, enter **admin\@yourtenant.onmicrosoft.com**, and your provided password, and then select **Next**.
11. On the **Connect your directories** page, ensure that **Contoso.com** is listed under **FOREST**, and then select **Add Directory**.
12. In the **AD forest account** window, select the **Create New AD Account** option, and in the **ENTERPRISE ADMIN USERNAME** field, type **Contoso\\Administrator**, and then type **Pa55w.rd** in the **PASSWORD** field. Select **OK**, and then select **Next**.
13. On the **Azure AD sign-in configuration** page, ensure that in the **USER PRINCIPAL NAME** drop-down list, the **userPrincipalName** value is selected. Select **Continue without matching all UPN suffixes to verified domains** and then select **Next**.
14. On the **Domain and OU filtering** page, select **Sync selected domains and OUs**.
15. Expand **Contoso.com**, clear the checkbox next to **Contoso.com** and ensure that the only following check boxes are selected: **IT**, **Managers**, **Marketing**, **Research**, and **Sales**. Select **Next**.
16. On the **Uniquely identifying your users** page, select **Next**.
17. On the **Filter users and devices** page, select **Next**.
18. On the **Optional features** page, review available options, but do not make any changes. Ensure that **Password hash synchronization** is selected, and then select **Next**.
19. On the **Ready to configure** page, ensure that **Start the synchronization process when configuration completes** is selected, and then select **Install**.
20. When configuration is complete, select **Exit**.

    _Note: At this time, synchronization of objects from your local Active Directory Domain Services (AD DS) and Azure AD begins. You should wait approximately 3-4 minutes for this process to complete._

21. Close all open windows.

#### Task 2: Verify synchronization in Azure AD

1. Switch to **SEA-CL1**.
2. On the taskbar, select **Microsoft Edge**.
3. In the address bar, enter **http://portal.office.com**.
4. At the Sign-in prompt, enter **admin\@yourtenant.onmicrosoft.com** and then select **Next**.
5. At the Enter password page, enter the password for the Admin account and then select **Sign in**. Note: Check with your instructor on the password to use for signing in with the Admin account.
6. At the Save password prompt, select **Save**.
7. At the Stay signed in prompt, select **No**. The Office 365 portal opens.
8. At the top corner, select the **App launcher** and then select **Admin**. The Microsoft 365 admin center opens.
9. Select the **Navigation menu** and then select **Show all**.
10. In the Navigation pane, under **Admin centers** select **Azure Active Directory**. The Azure Active Directory admin center opens.
11. In the Azure Active Directory admin center, in the navigation pane, select **Users**.
12. Verify that you see users from your local AD DS. Ensure that these users have the value **Yes** in the **Directory synced** column. 
13. In the Navigation pane, select **Azure Active Directory** and then select **Groups**. Verify that you see groups from your local AD DS.
14. Select the **Managers** group.
15. On the **Managers** group page, select **Members** and then ensure that you see users. Also, verify that you cannot add members or remove this group, as it is sourced from the local Active Directory. 
16. Close Microsoft Edge.

**Results**: After completing this exercise, you should have successfully configured Azure AD Connect to synchronize between Active Directory Domain Services and Azure Active Directory.

**END OF LAB**