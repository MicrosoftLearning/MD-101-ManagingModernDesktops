# Practice Lab: Creating device inventory reports

## Summary

In this lab, you will view device inventory within Intune, Excel, and using Power BI.

## Exercise 1: Reviewing device inventory with Intune 

### Scenario

You've been asked to review the inventory for SEA-WS3. Use Intune to review the devices hardware and app inventory.

### Task 1: Examining device inventory

1. On **SEA-CL1**, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd**.
2. On the taskbar, select **Microsoft Edge**.
3. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
4. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
5. In the Microsoft Endpoint Manager admin center, select **Devices** from the navigation bar.
6. In the Devices navigation pane, select **All devices** and in the details pane, select the **SEA-WS3** entry. Examine the various information displayed about the device.
7. Select **Properties** and note that you can change the **Management name**, **Device category** and **Device ownership**.
8. In the **Management name** field, replace the existing text with **SEA-WS3** and select **Save**.
9. Under **Monitor**, select **Hardware** and examine the hardware from **SEA-WS3**. You need to scroll down to see it all.
10. Under **Monitor**, select **Discovered apps** and examine the app inventory from **SEA-WS3**. You may need to scroll down to see it all.

**Results**: After completing this exercise, you will have successfully reviewed device hardware and app inventory.


## Exercise 2: Exporting Intune data to Excel

### Scenario

Management is requesting a report of all devices. They do not have access to the Intune dashboards, and have requested the information be sent in an Excel file.

### Task 1: Export Intune Data

1. On **SEA-CL1**, in the Microsoft Endpoint Manager admin center, select **Devices** and then select **All devices**.
2. On the **Devices | All devices** blade, in the details pane, select **Export**.
3. At the Export all managed devices message, select **Yes**, and wait for the export to be prepared and a message that indicates that the export is complete.
4. At the bottom of the Microsoft Edge window, next to the zip file, select the ellipse and then select **Show in folder**.
5. In the Downloads folder, right-click the downloaded zip file and select **Extract all**. Browse to the **Downloads** folder and select **Extract**.

### Task 2: Import Intune data into Microsoft Excel

1. On **SEA-CL1**, select **Start** and then select **Excel**.
2. In Excel, select **Browse**, select the **Downloads** folder and in the **All Excel Files** drop-down box, select **All Files**.
3. In the **Open** dialog box, select the file you just extracted. Then select **Open**.
4. In the **Text Import Wizard – Step 1 of 3** dialog box, select **Delimited** and then select **Next**.
5. In the **Text Import Wizard – Step 2 of 3** dialog box, remove the check mark next to **Tab** and select the check box next to **Comma**. Then select **Next**.
6. In the **Text Import Wizard – Step 3 of 3** dialog box, select **Finish**.
7. Review the report content. When finished, close Excel and select **No** when asked about saving the report.
8. Close all open Windows.

**Results**: After completing this exercise, you will have successfully exported Intune data to Excel for review.


## Exercise 3: Reviewing Intune Data using Power BI 

### Scenario

Your organization uses Power BI for reporting. You need to set up Power BI on SEA-CL1 and connect to the Intune Data Warehouse. You need to see a report that shows the primary user of each device. 

*Note: Power BI Desktop was deployed and installed using Configuration Manager in Module 4.* 

### Task 1: Connect Power BI to the Intune Data Warehouse

1. On SEA-CL1, on the desktop, double-click **Power BI Desktop**.
2. After Power BI loads, with the **Home** tab selected in the ribbon, select **Get Data**. 
3. In the **Get Data** dialog box, select **Other** on the left side, and then select **OData Feed** and then select **Connect**.
4. On the taskbar, select **Microsoft Edge**.
5. In Microsoft Edge, type **https://endpoint.microsoft.com** in the address bar, and then press **Enter**. 
6. Sign in as **admin\@yourtenant.onmicrosoft.com** with the tenant Admin password.
7. In the Microsoft Endpoint Manager admin center, select **Reports** and then select **Data warehouse**.
8. In the **OData feed for reporting service** field, copy the Odata URL into the clipboard.
9. Switch back to **Power BI Desktop** and in the OData feed dialog box, paste the **OData URL** into the **URL** box and select **OK**.
10. In the **OData feed** dialog box, select the **Organizational account** tab and then select **Sign in**.
11. On the **Sign in** page, select **admin\@yourtenant.onmicrosoft.com**. 
12. On the **Enter password** page, enter the tenant Admin password, and select **Sign in**.
13. Back on the **OData feed** dialog box, select **Connect**. Wait for the connection and load of data. The **Navigator** window opens.
14. In the **Navigator** window, select all tables. You can select the first table, and then shift-select the last table to select all tables. With all tables selected, select **Load**. It will take a few minutes for the process to complete.

### Task 2: Create a custom report using Power BI and Intune Data Warehouse

1. In the **Visualizations** pane, select the **Treemap** option (the icon appears to have several rectangles of various sizes). The Treemap chart will be added to the report canvas.
2. In the menu bar, select **View**, and then in the ribbon select **Page view** and then select **Actual size**.
3. In the **Fields** pane, find the **devices** table and expand it. 
4. Select the **deviceName** data field and drag it onto the Treemap chart in the report canvas.
5. Drag the **deviceKey** data field from the devices table to the **Visualizations** pane and drop it on under the **Values** section in the box labeled **Add data fields here**.
6. In the Fields pane, scroll down and find the **users** table and expand it. 
7. Drag the **displayName** data field from the users table to the **Visualizations** pane and drop it on under the **Details** section.

   _Note: You should now see device names in each report object, with a user name listed under each device._

8. Select the **Treemap** you added to the report canvas. In the **Visualizations** pane, select the **Table** report option (the icon appears as a spreadsheet) to switch the report canvas to a table view.
9. Select **File**, select **Export**, then select **Export to PDF**. The browser should launch and display the report in a PDF format. 
10. Close all open windows.

**Results**: After completing this exercise, you will have successfully connected Power BI desktop to the Intune Data Warehouse and created a report using Power BI.


**END OF LAB**