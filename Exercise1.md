## Exercise 1: Data Engineering experience, Data ingestion from a spectrum of analytical data sources into OneLake

*Before we start executing the steps, we will trigger the simulator app to start streaming data to eventhub.*

 **Open** the new tab in the browser and copy paste the below URL to verify app service streaming data. 

```BASH
 <inject key= "NameSpaceBrowse" enableCopy="true"/>
```

 **Wait** for the page to load. You will see a page like the one shown below.

![Simulator.](media/task-1.3.png)


### Task 1.1: Create a Microsoft Fabric enabled workspace


1. Open **PowerBI** in a new tab by copy pasting the below link.

 ```BASH
   https://app.powerbi.com/
```

`Note: After you paste the link in the browser, the page will automatically login.`

*Close* the top bar for a better view, if it appear.

   ![Create Power BI Workspace.](media/task-1.1-new1.png)

1. In Power BI service, click on **Workspaces**.

2. Click the **+ New workspace** button.

	![Create Power BI Workspace.](media/task-1.1.2.png)

3. Copy the below name and paste it in the **Name** field of workspace and if the **contosoSales** workspace is not availabe please add any *suffix*.

  ```BASH
  contosoSales
  ```	

   ![Create Power BI Workspace.](media/task-1.1.3.png)


`Note: If you are getting any popups follow up the below steps or else jump to Task 1.2`

*Click on the **Try free** button.*

   ![Create Power BI Workspace.](media/task-1.1-new2.png)

*Click on the **Got it** button to continue.*

   ![Create Power BI Workspace.](media/task-1.1-new3.png)

5. Click on **Workspaces** to verify if the workspace with the given name got created, if not **perform** the above steps once again.

	![Create Power BI Workspace.](media/task-1.1-new4.png)

  ```BASH
  contosoSales
  ```

### Task 1.2: Create/Build a Lakehouse


1. In Power BI service, click **+ New** and then select **Show all**.

`Note: You may see More options instead of Show all.` 

   ![Close the browser.](media/task-1.2.1.png)

2. In the new window, under Data Engineering section, click **Lakehouse (Preview)**.

    ![Close the browser.](media/task-1.2.2.png)

3. **Wait** for the Microsoft Fabric capacity to upgrade and then click on **OK**.

   ![Create Power BI Workspace.](media/task-1.2-new5.png)

4. Enter the name **lakehouseBronze**.

```BASH
lakehouseBronze
```

`Note: If the page get refreshed and lakehouse did not create, follow the steps from 1 to 4.`


5. Click the **Create** button.

    ![Close the browser.](media/task-1.2.3.png)

6. Click on **Workspaces** in the left navigation pane and select **ContosoSales**.

	![Give the name and description for the new workspace.](media/task-1.2.4.png)

`Note: For this lab we need three lakehouses altogether. For creating the other two, follow the step provided below.`

7. Repeat from **steps 1 to 5** to create two more lakehouses with the names **lakehouseSilver** and **lakehouseGold** respectively.

```BASH
lakehouseGold
```

```BASH	
lakehouseSilver
```

### Task 1.3: Data Ingestion
    
### Using Data Pipelines/Data Flow ‘No Code-Low Code experience’

1. Go to **contosoSales** workspace, and click on the **+ New** button and select **More options**.

	![Pipeline.](media/task-1.3.1.png)



`Note: Instead of More options you may see Show all.`

2. Under the Data Factory section, select **Data pipeline (Preview)**.

	![Pipeline.](media/task-1.3.2.png)

3. In the pop-up, paste the pipeline name given below and click on the **Create** button.

	![Pipeline.](media/task-1.3.3.png)

```BASH
Sales data from Azure SQL DB - Low Code Experience
```

4. Click on **Copy data**.

    ![Pipeline.](media/task-1.3.4.png)

5. In the pop-up, scroll down through the resources, click on **Azure SQL Database** and then click on the **Next** button.

    ![Pipeline.](media/task-1.3.5.png)

`Note: You may not see the Azure SQL Database in the same location as shown in the screenshot.`

6. Select the **Create new connection** radio button.

    ![Pipeline.](media/task-1.3.6.png)

`Note: To fill in the details for required fileds, we need to fetch the data from the SQL Database resource deployed in the Azure Portal.`


7. In the **Server** field copy and paste the value given below.
   
```BASH
 <inject key= "MssqlServer" enableCopy="true"/>
 ```

 In the **Database** field paste the below value.

```BASH 	
SalesDb
```

![Datawarehouse.](media/task-1.3.15.png)

8. Scroll down and select **Basic** for Authentication kind, enter **labsqladmin** as the Username, **Smoothie@2023** as the Password and finally click on the **Next** button.


```BASH
labsqladmin
```

```BASH
Smoothie@2023
```

   ![Datawarehouse.](media/task-1.3.16.png)

`Note: Close any pop-up as such which you see throughout the lab.`
   
   ![Datawarehouse.](media/task-1.3.16.1.png)

`Note: Wait for the connection to be created.`

9. Select the **Existing tables** radio button, click on the **checkbox** for the first table below the Select all option, and then click on the **Next** button.

	![Datawarehouse.](media/task-1.3.17.png)

10. Scroll down and click on **Lakehouse** and then click on the **Next** button.

	![Datawarehouse.](media/task-1.3.18.png)

11. Click on the **Existing Lakehouse** radio button, click on the **dropdown**, select **lakehouseBronze** and then click on the **Next** button.

	![Datawarehouse.](media/task-1.3.19.png)

12. Select the **Load to new table** radio button, click on the checkbox beside **Source** and then click on **Next**.

	![Datawarehouse.](media/task-1.3.20.png)

13. Click on **Save + Run**.

	![Datawarehouse.](media/task-1.3.21.png)

14. Click on the **three dots** at top right of the screen, select **Notifications**.

	![Datawarehouse.](media/task-1.3.21.1.png)

15. Verify the **Running status** of the pipeline.

	![Datawarehouse.](media/task-1.3.22.png)

`Note: Please wait for the pipeline to execute.`

16. Once the status shows **Run Succeeded**, your data has been transfered from Azure SQL Database to Lakehouse.

	![Datawarehouse.](media/task-1.3.23.png)

17. Similarly you can get data into the Lakehouses using pipelines from various other sources like Snowflake, Dataverse, etc.


 *Due to time constraints, we will be moving forward to the next steps.*


### Using the ‘New Shortcut’ option from external data sources

1. In **Power BI**, click **Workspaces** and select the **contosoSales** workspace.

    ![Lakehouse.](media/task-1.3-ext-shortcut.png)

2. In the **contosoSales** workspace, click on the **lakehouseBronze** lakehouse.

    ![Lakehouse.](media/task-1.3-ext-shortcut2.png)

`Note: There will be 3 options for lakehouseBronze, namely Lakehouse, Dataset (default) and SQL endpoint. Make sure to select the Lakehouse option.`

3. Click on the **three dots** on the right side of Files.

4. Click on **New shortcut**.

	![Lakehouse.](media/task-1.3-ext-shortcut3.png)

5. In the pop-up window, under **External sources**, select the **Azure Data Lake Storage Gen2** source.

	![Lakehouse.](media/task-1.3-ext-shortcut4.png)

`Note: Wait for the screen to load.`

6. In the screen below, we need to enter the connection details for the ADLS Gen2 shortcut. For this, we need to get the details from the Storage Account resource.

	![Lakehouse.](media/task-1.3-ext-shortcut11.png)

7. Copy the below **Data Lake Storage** endpoint and paste it in the URL field of **New Shortcut** page under **Connection Settings**. 

   	<inject key= "StorageEndpoint" enableCopy="true"/>


8. To get the Key of the storage Account, navigate to the **Azure Portal**, search for **fabric-dpoc** in the search tab and select the resource group name with **fabric-dpoc**.

    ![Pipeline.](media/task-1.3.11.png)

9. Search for **storage account** and click on the storage account resource.

	![Lakehouse.](media/task-1.3-ext-shortcut5.png)

10. If you are not able to left panel, In the resource window click on the **Hamburger icon**.

	![Lakehouse.](media/task-1.3-ext-shortcut5.1.png)

11. Scroll down to **Security + networking** section.

12. Click on **Access keys**.

	![Lakehouse.](media/task-1.3-ext-shortcut5.2.png)

13. Scroll down and click on the **Show** button under key1.

	![Lakehouse.](media/task-1.3-ext-shortcut6.png)

14. Click on the **Copy to clipboard** button. Save this information in a notepad for further use.

	![Lakehouse.](media/task-1.3-ext-shortcut7.png)


15. Navigate back to the **Power BI** workspace (i.e. the Power BI tab in which we were working earlier).

16. In the **Authentiation kind** dropdown, select **Account Key**.

17. Paste the key copied in **step number 14** in the **Account Key** field.

18. Click on **Next**.

	![Lakehouse.](media/task-1.3-ext-shortcut9.png)

19. Under **Shortcut Name**, copy and paste below name **data**.

```BASH
data
```

20. Under **Sub Path**, type **/adlsfabricshortcut**.

```BASH
/adlsfabricshortcut
```

21. Click on the **Create** button.

	![Lakehouse.](media/task-1.3-ext-shortcut10.png)


#*We will now create another shortcut for Litware Inc. data.*


22. Click on the **three dots** to the right of **Files**.

23. Click on **New shortcut**.

	![Lakehouse.](media/task-1.3-ext-shortcut3.png)

24. In the pop-up window, under **External sources**, select the **Azure Data Lake Storage Gen2** source.

	![Lakehouse.](media/task-1.3-ext-shortcut4.png)

`Note: Wait for the screen to load.`

25. Copy the below **Data Lake Storage** endpoint and paste it in the URL field of **New Shortcut** page under **Connection Settings**.

```BASH
<inject key= "StorageEndpoint" enableCopy="true"/>
```

`Note: The details entered earlier will be auto fetched. So click on next, if not follow steps 07 and 17 below.`

26. Click on **Next**.

	![Lakehouse.](media/task-1.3-ext-shortcut9.png)

27. Under **Shortcut Name**, copy paste the below value **sales-transaction-litware**.

```BASH
sales-transaction-litware
```

28. Under **Sub Path**, copy paste the below value **/bronzeshortcutdata**.

```BASH
/bronzeshortcutdata
```

29. Click on the **Create** button.

	![Lakehouse.](media/task-1.3-ext-shortcut13.png)


### Using Spark Notebook ‘Code-first experience’

1. While you are in the **Power BI workspace**, click on **Power BI** in the bottom left corner and select **Data Science**.

	![Datawarehouse.](media/task-1.3-notebook-5.png)

2. Click on **Import notebook**.

	![Datawarehouse.](media/task-1.3-notebook-6.png)
	
3. In the **Import Status**, click on the **Upload** button.

	![Datawarehouse.](media/task-1.3-notebook-7.png)
	
4. Browse to the notebooks from your JumpVM through the path **C:\LabFiles\IgniteDreamLab2023\artifacts\fabricnotebooks**, select all of the notebooks and click on the **Open** button.

	![Datawarehouse.](media/task-1.3-notebook-8.png)

5. Click on the **notification** icon to check the upload status. 

	![Datawarehouse.](media/task-1.3-notebook-17.png)

6. Once the upload is complete, the notification will display **Imported succussfully**. Click on **Go to Workspace**.

	![Datawarehouse.](media/task-1.3-notebook-9.png)

7. In the workspace, click on the **01 Marketing Data to Lakehouse (Bronze) - Code-First Experience** notebook.

	![Datawarehouse.](media/task-1.3-notebook-10.png)

8. In the left pane, click on the **Missing Lakehouse** button and select **Remove all Lakehouses**.

	![Datawarehouse.](media/task-1.3-notebook-11.png)

`Note:` If you do not see Missing lakehouse, you may see **lakehouse{Name}**, click on it to get the Remove all Lakehouses option.

9. Click on **Continue** in the pop-up window.

	![Datawarehouse.](media/task-1.3-notebook-12.png)

10. In the left navigation pane, click on the **Add** button.

	![Datawarehouse.](media/task-1.3-notebook-13.png)

11. In the pop-up, select the **Existing Lakehouse** radio button and then click on the **Add** button.

	![Datawarehouse.](media/task-1.3-notebook-14.png)

12. Click on the **lakehouseBronze** checkbox and then click on **Add**.

	![Datawarehouse.](media/task-1.3-notebook-15.png)


 `Note: This notebook is used to get the data to the Bronze Lakehouse.`


13. Close the **Information box** for a better view of the notebook content, if it appears.

	![Datawarehouse.](media/task-1.3-notebook-15.1.png)

14. Go to the cell with name **Shortcut Folder Path**, replace from Hash to Hash **#WORKSPACE_NAME#** with the Fabric Workspace name you are working on and also verify the lakehouse name which should be the Bronze Lakehouse you created.

```BASH
contosoSales
```

   ![Close the browser.](media/task-1.3-notebook-18.png)

*This notebook is used to get the data to the Bronze Lakehouse.*

15. Click on **Run all**.

	![Close the browser.](media/task-1.3-notebook-16.png)

