# Practice Lab: Managing Identities in Azure AD

## Summary

In this lab, you will use the Azure Active Directory admin center to create and modify users, groups, and license assignments.

## Exercise 1: Creating users in Azure AD

### Scenario

You need to create user accounts in Azure AD for new employees that will start next week. New users are listed in the following table:

| Name           | User Name                            | Password |
| -------------- | ------------------------------------ | -------- |
| Edmund Reeve   | ereeve\@yourtenant.onmicrosoft.com   | Pa55w.rd |
| Miranda Snider | msnider\@yourtenant.onmicrosoft.com  | Pa55w.rd |
| Cody Godinez   | cgodinez\@yourtenant.onmicrosoft.com | Pa55w.rd |

_Note: For location use either your local region or United States._ 

You've also been told that several more employees will be hired over the next couple of months.  You've decided that scripting would be a far more efficient method of adding a large number of new users. You've decided to create a PowerShell script and test it out when you create Cody Godinez's account. 

### Task 1: Create users by using the Azure Active Directory admin center

1.  On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2.  On the taskbar, select **Microsoft Edge**.
3.  In the address bar, enter **http://portal.office.com**.
4.  At the Sign-in prompt, enter **admin\@yourtenant.onmicrosoft.com** and then select **Next**.
5.  At the Enter password page, enter the password for the Admin account and then select **Sign in**. Note: Check with your instructor on the password to use for signing in with the Admin account.
6.  At the Save password prompt, select **Save**.
7.  At the Stay signed in prompt, select **No**. The Office 365 portal opens.
8.  At the top corner, select the **App launcher** and then select **Admin**. The Microsoft 365 admin center opens.
9.  Select the **Navigation menu** and then select **Show all**.
10.  In the Navigation pane, under **Admin centers** select **Azure Active Directory**. The Azure Active Directory admin center opens.
11.  In the Azure Active Directory admin center, in the navigation pane, select **Users**.
12.  On the **Users | All users** page, select **New user**.
13.  On the **New User** page, ensure that **Create user** is selected, enter the following:

     -  User Name: **ereeve\@yourtenant.onmicrosoft.com**
     -  Name: **Edmund Reeve**

14.  Select **Let me create the password.**
15.  Next to **Initial password**, enter **Pa55w.rd**.
16.  Under Settings, next to Usage location, select **United States**, and then select **Create**. If necessary, close the **Save password** prompt.
17.  On the **Users | All users** page, select **New user**.
18.  On the **New User** page, ensure that **Create user** is selected, enter the following:

    -  User Name: **msnider\@yourtenant.onmicrosoft.com**
    -  Name: **Miranda Snider**
19.  Select **Let me create the password.**
20.  Next to **Initial password**, enter **Pa55w.rd**.
21.  Under Settings, next to Usage location, select **United States**, and then select **Create**. If necessary, close the **Save password** prompt.

### Task 2: Create users by using PowerShell

1.  On SEA-CL1, on the taskbar, right-click **Start**, and then select **Windows PowerShell**.

2.  In the **Windows PowerShell** window, type the following command, and then press **Enter**. If prompted, enter **Y** at the NuGet and repository messages:

```
Install-Module MSOnline

```

3.  In the **Windows PowerShell** window, type the following command, and then press **Enter**:

```
Connect-MsolService

```

4.  In the **Sign in to your account** dialog box, sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant password, and then select **Sign in**.

5.  In the **Windows PowerShell** window, type the following code to create a new user, and then press **Enter**. Be sure to replace "yourtenant" with your assigned tenant name:

```
New-MsolUser –UserPrincipalName cgodinez@yourtenant.onmicrosoft.com
-DisplayName “Cody Godinez” -FirstName “Cody” -LastName “Godinez” -Password
‘Pa55w.rd’ -ForceChangePassword $false -UsageLocation “US”

```

6.  In the **Windows PowerShell** window, type the following command, and then press **Enter**:

```
Get-MsolUser

```

7.  Verify that a list of users is displayed from your tenant.

**Results**: After completing this exercise, you will have successfully created new user accounts in Azure AD.

## Exercise 2: Validating licenses and creating and managing groups

### Scenario

You need to review current license allocation for the tenant and modify the Company branding for the sign-in page. 

You also need to add the three new users to a Security group and assign licenses as indicated in the table below.   

| Name           | Member of:        | License to assign                                |
| -------------- | ----------------- | ------------------------------------------------ |
| Edmund Reeve   | Contoso_Marketing | Office 365 E5, Enterprise Mobility + Security E5 |
| Miranda Snider | Contoso_Marketing | None                                             |
| Cody Godinez   | Contoso_Sales     | None                                             |

### Task 1: Review licenses and modify company branding

1.  On SEA-CL1, switch to Microsoft Edge.
2.  In the Azure Active Directory admin center, in the Navigation pane, select **Azure Active Directory**.
3.  On the **Contoso|Overview** page, under **Manage**, select **Licenses**.
4.  On the **Licenses|Overview** page, under **Manage**, select **All products**. Take note of the current licenses available and assigned for Enterprise Mobility + Security E5 and Office 365 E5.
5.  In the Azure Active Directory admin center, in the Navigation pane, select **Azure Active Directory**.
6.  On the **Contoso|Overview** page, under **Manage**, select **Company branding** and then select **Configure**.
7.  On the Configure company branding page, configure the following settings and then select **Save**:
    - Sign-in page text: **Contoso Corp. Sign-in Page**
    - Show option to remain signed in: **Yes**
8.  In the Azure Active Directory admin center, in the Navigation pane, select **Users**.
9.  In the user list, select **Edmund Reeve**.
10.  In the Edmund Reeve|Profile page, under Manage, select **Licenses**.
11.  Select **Assignments**.
12.  In the Update license assignments page, select the check box next to **Enterprise Mobility + Security E5** and **Office 365 E5**.
13.  Select **Save**.

### Task 2: Create groups by using the Azure Active Directory admin center

1.  On **SEA-CL1**, in the Azure Active Directory admin center, in the navigation pane, select **Azure Active Directory**.
2.  On the **Contoso|Overview** page, under **Manage**, select **Groups**.
3.  Select **New group**.
4.  On the **New Group** page, enter the following:

    -  Group type: Security
    -  Group name: Contoso_Marketing
    -  Membership type: Assigned
5.  Under Members, select **No members selected**.
6.  In the Add members page add **Edmund Reeve** and **Miranda Snider** and then click **Select**.
7.  Select **Create**.

### Task 3: Create groups by using PowerShell

1.  In the **Windows PowerShell** window, type the following code to create a new group, and then press **Enter**:


```
New-MsolGroup -DisplayName “Contoso_Sales” -Description “Contoso Sales team users”

```

2.  In the **Windows PowerShell** window, type the following command, and then press **Enter**:

```
Get-MsolGroup

```

3.  Verify that you get the list of groups in your tenant, including the Contoso_Sales group you just created.

4.  In the **Windows PowerShell** window, type the following code to define a variable as the Contoso_Sales group, and then press
    **Enter**:

```
$group = Get-MsolGroup | Where-Object {$_.DisplayName -eq "Contoso_Sales"}

```

5.  In the **Windows PowerShell** window, type the following code to define another variable as the user, and then press
    **Enter**:

```
$user = Get-MsolUser | Where-Object {$_.DisplayName -eq “Cody Godinez”}

```

6.  In the **Windows PowerShell** window, type the following code to add Cody to Contoso_Sales using set variables, and then press **Enter**:

```
Add-MsolGroupMember -GroupObjectId $group.ObjectId -GroupMemberType "User"
-GroupMemberObjectId $user.ObjectId

```

7.  In the **Windows PowerShell** window, type the following code, and then press **Enter**:

```
Get-MsolGroupMember -GroupObjectId $group.ObjectId

```

8.  Verify that you get **Cody Godinez** as a result. Minimize the **Windows PowerShell** window.
9.  Close Windows PowerShell and Microsoft Edge.

**Results**: After completing this exercise, you should have successfully validated licenses, and created and managed groups.

**END OF LAB**
