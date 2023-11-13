
## Exercise 3: Data Science experience, explore Machine Learning and Business Intelligence scenarios.

### Task 3.1: Build ML models, experiments, and Log ML model in the built-in model registry using MLflow and batch scoring.

#### Databricks

The architecture diagram shown here illustrates the end-to-end MLOps pipeline using the Azure Databricks managed MLflow. 

After multiple iterations with various hyperparameters, the best performing model is registered in the Databricks MLflow model registry. Then it is set up as the model serving in the Azure Databricks Workspace for low-latency requests.
	
   ![Close the browser.](media/task-3.1.1.png)

1. Navigate back to the **Databricks workspace** we started for the previous exercise.

2. In the left navigation pane, select **Workspace** and click **Workspace** again. Click on the **03_ML_Solutions_in_a_Box.ipynb** notebook.

	![Close the browser.](media/task-3.1.2.png)

Now that we've ingested and processed our customer data, we want to understand what makes one customer more likely to churn than another, so we want to see if we can produce a machine learning model that can accurately predict if a particular customer will churn.

Ultimately, we would like to understand our customers' sentiment so we can create targeted campaigns to improve our sales.

3. Navigate to **cmd 10**.

With the data prepared, we can begin exploring the patterns it contains. 

Let's start by examining the customer churn outcome based on factors like the tenure in months and the total amount spent by them. As a result, we can see a high churn rate is seen if the customer tenure is low, and they have a lower spend amount.

   ![Close the browser.](media/task-3.1.4.png)

4. Navigate to **cmd 20**.

5. Navigate to **cmd 21**. 

By registering this model in Model Registry, we can easily reference the model from anywhere within Databricks. 

   ![Close the browser.](media/task-3.1.5.png)

6. Review the **cmd 29** cell.

Let’s look at the comparison of multiple runs in the UI.

You can visualize the different runs using a parallel coordinates plot, which shows the impact of different parameter values on a metric.

The best ML model for Customer Churn is selected and registered with Databricks model registry.

   ![Close the browser.](media/task-3.1.6.png)

7. Navigate to **cmd 38**.

For low-latency use cases, you can use MLflow to deploy the model for online serving. The serving system loads the Production model version from the Model Registry. 

   ![Close the browser.](media/task-3.1.7.png)

8. Navigate to **cmd 40**.

It is then used to predict the probability of Customer Churn using the deployed model and this model endpoint is ready for production.

   ![Close the browser.](media/task-3.1.8.png)

9. Navigate to **cmd 41**. 

Once we have the predicted data, it is stored back in delta tables in the gold layer back in OneLake.

   ![Close the browser.](media/task-3.1.9.png)	

#### Microsoft Fabric

Microsoft Fabric offers Data Science experiences to empower users to complete end-to-end data science workflows for the purpose of data enrichment and business insights. You can complete a wide range of activities across the entire data science process, all the way from data exploration, preparation and cleansing to experimentation, modeling, model scoring and serving predictive insights to BI reports.

1. Navigate back to the **Power BI workspace**.	
	
When building data science workflows, we can leverage data science services alongside Microsoft Fabric to handle different stages of the workflow, such as data ingestion, data processing, model training, and deployment. 
In this lab we have stored data science models as microservices within Microsoft Fabric, taking advantage of its scalability and reliability features.

   ![Close the browser.](media/task-3.1.11.png)	

2. In Power BI service, click on **Workspaces** and then click on **contosoSales**. 

	![Close the browser.](media/task-3.1.10.png)

3. Click on **Filter** and select **Notebook** then click on the **02 Churn Prediction Using MLFlow From Silver To Gold Layer** notebook.

	![Close the browser.](media/task-3.1.12.png)

4. Wait for few seconds to load the page, In the left pane, click on the **Missing Lakehouse** button and select **Remove all Lakehouses**.  

	![Datawarehouse.](media/task-1.3-notebook-11.png)

`Note:` If you do not see Missing lakehouse, you'll see **lakehouse{Name}**, click on that name to get the **Remove all Lakehouses** option.

5. Click on **Continue** in the pop-up window.

	![Datawarehouse.](media/task-1.3-notebook-12.png)

6. In the left pane, click on the **Add** button.

	![Datawarehouse.](media/task-1.3-notebook-13.png)

7. In the pop-up, select the **Existing Lakehouse** radio button and then click on the **Add** button.

	![Datawarehouse.](media/task-1.3-notebook-14.png)

8. Click on the **lakehouseSilver** checkbox and then click on **Add**.

	![Datawarehouse.](media/task-3.1.13.png)

This notebook describes steps and scripts/code to create, evaluate and deploy a customer churn prediction model.

`Note: Due to time constraints, we will not run this notebook.`

*Load Data using Drag & Drop.*

Microsoft Fabric allows an easy drag and drop feature to load the data from the delta tables.
We can simply drag the tables from lakehouseSilver and drop it to the notebook cell.

*Chart view to explore data.*

Microsoft Fabric provides an interactive visualization interface for exploring and analyzing data. 

It offers a variety of chart types and customization options to create insightful visualizations that help with understanding patterns, trends, and relationships within the data.

*Data Wrangler to preprocess data in lakehouses.*

Data Wrangler is a code tool that prepares data and generates Python code. This experience makes it easy to accelerate data cleansing and build repeatability and automation through generated code.


## Exercise 4: Data Warehouse experience, explore SQL Analytics with Data Warehouse.

### Task 4.1: Create a Data Warehouse

1. In the bottom-left corner of the Power BI tab, click on **Power BI**.

`Note: You may see Data Science instead.` 

2. Select **Data Warehouse**.

	![Datawarehouse.](media/task-4.1.warehouse-1.png)

3. Click on **Warehouse (Preview)**.

	![Datawarehouse.](media/task-4.1.warehouse-2.png)

4. In the 'New Warehouse' pop-up, paste the name **salesDW**.

```BASH
salesDW
```

5. Click **Create**.

	![Datawarehouse.](media/task-4.1.warehouse-3.png)

### Task 4.2: Load data in the warehouse

1. Click **Get data**.

2. Select **New data pipeline**.

	![Datawarehouse.](media/task-4.1.warehouse-4.png)

`Note: It will take some time for the page to load.`

3. In the pop-up, paste the name **02 Sales data from Azure SQL DB to Data Warehouse - Low Code Experience**.

```BASH
02 Sales data from Azure SQL DB to Data Warehouse - Low Code Experience
```

4. Click **Create**.

	![Datawarehouse.](media/task-4.1.warehouse-5.png)

5. **Wait** for a new pop-up.

6. Scroll down in the pop-up.

7. Select **Azure SQL Database**.

8. Click **Next** button.

	![Datawarehouse.](media/task-4.1.warehouse-6.png)

9. Since you have already created a connection earlier, select from the drop down below as seen in the picture.

	![Datawarehouse.](PowerBI/Task4.1.png)

10. Click on **test connection** and **Next**.

	![Datawarehouse.](PowerBI/Task4.2.png)


11. In **Connect to data source**, select **Existing tables**, select **Select all** and then click on the **Next** button.

	![Datawarehouse.](media/task-4.1.warehouse-12.png)

17. In **Choose data destination** select the **Data Warehouse** and click the **Next** button.

	![Datawarehouse.](media/task-4.1.warehouse-13.png)

18. In **Connect to data destination**, select **Load to new table** and click on the **Source** checkbox. Then click the **Next** button.

	![Datawarehouse.](media/task-4.1.warehouse-14.png)

19. In the **Settings** section, keep it **default** and click the **Next** button.

	![Datawarehouse.](media/task-4.1.warehouse-15.png)

20. In the **Review + save** section, scroll down to the end and then click the **Save + Run** button.

	![Datawarehouse.](media/task-4.1.warehouse-16.png)	

`Note: When you click on Save + Run the pipeline is automatically triggered.`

21. If the below screen is prompted click on the **OK** button.

	![Datawarehouse.](media/task-4.1.warehouse-16.1.png)	

22. **Check** the notification or pipeline output screen for the progress of copy database.

	![Datawarehouse.](media/task-4.1.warehouse-17.png)

23. In the progress section of the pipeline, check the **status** of the running pipeline in the output section below.

	![Datawarehouse.](media/task-4.1.warehouse-18.png)

`Note: Wait for the resultant data to load.`

24. **Wait** for the status of the pipeline to display **Succeeded** and go back to the **Data Warehouse** from the workspace.

	![Datawarehouse.](media/task-4.1.warehouse-19.png)


### Task 4.3: Create virtual Data Warehouses

Introducing virtual warehouses, where we not only analyze data from the department, but also query any data from another warehouse or a lakehouse SQL end point - across the organization from any department.

1. Click on the **+ Warehouse** button.

	![Datawarehouse.](media/task_4.3.2.png)

2. In the pop-up window, select the **lakehouseSilver SQL Endpoint checkbox** and click on the **Confirm** button.

	![Datawarehouse.](media/task_4.3.3.png)

`Note: It will take a few seconds for the new warehouse to appear.`
`
