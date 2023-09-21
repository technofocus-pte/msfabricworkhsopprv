Lab 1: Lakehouse end-to-end scenario: overview and architecture

This lab walks you through an end-to-end scenario from data acquisition to data consumption. It helps you build a basic understanding of Fabric, including the different experiences and how they integrate, as well as the professional and citizen developer experiences that come with working on this platform. This lab isn't intended to be a reference architecture, an exhaustive list of features and functionality, or a recommendation of specific best practices.

# Exercise 1: Setup Lakehouse end-to-end scenario

Traditionally, organizations have been building modern data warehouses for their transactional and structured data analytics needs. And data lakehouses for big data (semi/unstructured) data analytics needs. These two systems ran in parallel, creating silos, data duplicity, and increased total cost of ownership.

Fabric with its unification of data store and standardization on Delta Lake format allows you to eliminate silos, remove data duplicity, and drastically reduce total cost of ownership.

With the flexibility offered by Fabric, you can implement either lakehouse or data warehouse architectures or combine them together to get the best of both with simple implementation. In this tutorial, you're going to take an example of a retail organization and build its lakehouse from start to finish. It uses the [medallion architecture](https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion) where the bronze layer has the raw data, the silver layer has the validated and deduplicated data, and the gold layer has highly refined data. You can take the same approach to implement a lakehouse for any organization from any industry.

This lab explains how a developer at the fictional Wide World Importers company from the retail domain completes the following steps:

# Task 1: Sign in to Power BI account and sign up for the free [Microsoft Fabric trial](https://learn.microsoft.com/en-us/fabric/get-started/fabric-trial)

1.  Open your browser, navigate to the address bar, and type or paste the following URL: [https://app.fabric.microsoft.com/](https://app.fabric.microsoft.com/,) then press the **Enter** button.

    ![](media/0966c8761dc69ad1b5ca1b981c9f55b0.png)

2.  In the **Microsoft Fabric** window, enter your **Microsoft 365**  credentials, and click on the **Submit** button.

    ![](media/781a00f5fb7308776b02c72f52195665.png)

3.  Then, In the **Microsoft** window enter the password and click on the **Sign in** button**.**

    ![](media/7121d57fc11d291a63e93359ea450e47.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

    ![](media/cf20e9498ab9d9221639afe642827f7e.png)

![A screenshot of a computer Description automatically generated](media/082c114d436e992e6bb91ca6dc1fbffb.png)

# Task 2: Start the Microsoft Fabric (Preview) trial

Follow these steps to start your Fabric (Preview) trial.

1.  Open your browser, navigate to the address bar, and type or paste the following URL: <https://app.fabric.microsoft.com/home> then press the **Enter** button.

![A screenshot of a computer Description automatically generated](media/082c114d436e992e6bb91ca6dc1fbffb.png)

1.  On Power BI home page select the Account manager. In the Account manager, select **Start trial**.

![](media/0af35e5b8be0e08979228de8896e57d5.png)

1.  If prompted, agree to the terms and then select **Start trial**.

    ![](media/7cb38798dea36b7ecec5395579d8f481.png)

2.  Once your trial capacity is ready, you receive a confirmation message. Select **Got it** to begin working in Fabric.

    ![](media/e39be53702fe5e9d3654be3be0ddcf8d.png)

3.  Open your Account manager again. Notice that you now have a heading for **Trial status**. Your Account manager keeps track of the number of days remaining in your trial. You also see the countdown in your Fabric menu bar when you work in a product experience.

    ![](media/b5c85f5a85fc985e17982061d21aee64.png)

# Task 3: onedrive configured sign up for the microsoft 365 admin center

1.  Open your browser, navigate to the address bar, and type or paste the following URL: [https://admin.microsoft.com/AdminPortal/Home\#/homepage](https://admin.microsoft.com/AdminPortal/Home#/homepage) then press the **Enter** button.

    ![A screenshot of a computer Description automatically generated](media/e1005e4c85ebc598050a05c36a9e3248.png)

2.  In the **Microsoft Azure** window, enter your **Sign-in** credentials, and click on the **Next** button.

    ![A screenshot of a computer Description automatically generated](media/8ac2f088e1a7498129aa10c731db887e.png)

3.  Then, In the **Microsoft**  window enter the password and click on the **Sign in** button**.**

    ![](media/7121d57fc11d291a63e93359ea450e47.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

    ![](media/cf20e9498ab9d9221639afe642827f7e.png)

5.  In Microsoft 365 admin center page on the left-side, select the **App launcher.**

    ![A screenshot of a computer Description automatically generated](media/fd186cb57c2b5f41dc561438fe4f8e1b.png)

6.  In the Microsoft 365 page from the Apps pane select **OneDrive**

    ![A screenshot of a computer Description automatically generated](media/8134dca8eb8e0bb04740307ae24358e4.png)

7.  In One Drive page, under **Securely store and share files** select **your One Drive is ready**

    ![A screenshot of a computer Description automatically generated](media/dd27b901487ee02c9c8a62f37062fbf4.png)

    ![](media/79e56af7e642ecbffcb2e629d27a2554.png)

# Exercise 2: Build and implement an end-to-end lakehouse for your organization

## **Task 1: Create a Fabric workspace**

In this task, you create a Fabric workspace. The workspace contains all the items needed for this lakehouse tutorial, which includes lakehouse, dataflows, Data Factory pipelines, the notebooks, Power BI datasets, and reports.

1.  Open your browser, navigate to the address bar, and type or paste the following URL: <https://app.fabric.microsoft.com/home> then press the **Enter** button
2.  In the **Power BI** **Home** page, on the left-side pane navigate and click on **Workspaces**.

    ![](media/1b3fad5262e07f1b1d5f3670ad2d5cf2.png)

3.  In the Workspaces pane Select **+** **New workspace**.

    ![](media/5968b6d45a359500b120904448cbba91.png)

4.  In the **Create a workspace tab**, enter the following details and click on the **Apply** button.

| **Name**                   | **!! Fabric Lakehouse Tutorial-XX !!***(*XX can be a unique number) (here, we entered **Fabric Lakehouse Tutorial-29**) |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------|
| **Description**            | !!This workspace contains all the items for the lakehouse tutorial !!                                                   |
| **Advanced**               | Under **License mode**, select **Trial**                                                                                |
| **Default storage format** | **Small dataset storage format**                                                                                        |
| **Template apps**          | **Check the Develop template apps**                                                                                     |

![](media/899d704c0aeaf3775c76c2a5d15dd3e8.png)

![](media/7ab2383e456d29ba59b3e2e0dbdd8655.png)

![](media/90e15204369dd4c23ec5f34038fcc900.png)

1.  Wait for the deployment to complete. It takes 2-3 minutes to complete

![](media/e5778bce7109e42745362ffd62c1f1db.png)

## **Task 2: Create a lakehouse**

1.  In the **Power BI Fabric Lakehouse Tutorial-XX** page, click on the **Power BI** icon located at the bottom left and select **Data Engineering** under the Synapse.

    ![](media/e048208404b3b302d253aa0d3e242f18.png)

2.  In the **Synapse** **Data Engineering** **Home** page, select **Lakehouse(Preview)** to create a lakehouse.

![](media/a026813e5ee15178676826e14449acfe.png)

1.  In the **New lakehouse** dialog box, enter!! **wwilakehouse** !!in the **Name** field, click on the **Create** button and open the new lakehouse.

    ![](media/baa312877dbd47ad48715e268d3d0d1f.png)

    ![](media/ce49074b6cca1fc7484fb5e314e07a8d.png)

2.  You will see a notification stating **Successfully created SQL endpoint**.

    ![](media/f65dadd599fe72000f3242710cda7783.png)

## **Task 3: Ingest sample data**

1.  In the **wwilakehouse** home page, under the **Explorer pane**, Select **New Dataflow Gen2 under Get data in your lakehouse.**

    ![](media/96c8b6a0774e18f03f7c31073fe2b153.png)

2.  On the new dataflow pane, select **Import from a Text/CSV file**.

    ![](media/69efc5a0e0172760a583bd2f5b17da4d.png)

3.  On the **Connect to data source** pane, select the **Upload file** radio button. Click on **Browse button** and browse your VM to **C:\\LabFiles** and then select **dimension_customer.csv** file. Select **Open.**

    ![](media/f344598525eba675e699cab341a306c3.png)

    ![](media/dcff3273abf94fc4cbcfa5cde956b39b.png)

4.  In the Connect to data source pane select **Next.**

    ![](media/8b8c11c1b7627b5f998091c12976a8d9.png)

5.  From the **Preview file data** page, preview the data and select **Create** to proceed and return back to the dataflow canvas.

    ![](media/c5d99a379bb53cada1d12ded2a26fb5d.png)

6.  In the **Query settings** pane, enter **dimension_customer** for the **Name** field. From the menu items, select **Add data destination** and select **Lakehouse**.

    ![](media/d735f764163270fc7a37b32562e933b0.png)

    **Note:**

-   *If needed, from the Connect to data destination screen, sign into your account. Select Next.*
-   Navigate to the **wwilakehouse** in your workspace.
-   If the **dimension_customer** table doesn't exist, select the **New table** setting and enter the table name **dimension_customer**. If the table already exists, select the **Existing table** setting and choose **dimension_customer** from the list of tables in the object explorer. Select **Next**.

**Note:** *Fabric adds a space and number at the end of the table name by default. Table names must be lower case and must not contain spaces. Please rename it appropriately and remove any spaces from the table name.*

1.  From the dataflow canvas, you can easily transform the data based on your business requirements. For simplicity, we aren't making any changes in this task. To proceed, select **Publish** at the bottom right of the screen.

    ![](media/9de06a04fda5c7022fcbe8ee962cb759.png)

1.  A spinning circle next to the dataflow's name indicates publishing is in progress in the item view. ![](media/786639dde024c1daadef9375ccc7cc40.png)
2.  In the **Fabric Lakehouse Tutorial-XX** tab, when publishing is complete, select the Dataflow1 **...** and select **Properties**.

    ![](media/5fb5a8ca5e900132798bb465b53062ce.png)

3.  In the Dataflow 1 tab ,rename the dataflow to !! **Load Lakehouse Table** !! and select **Save**.

    ![](media/ed3eb1b8a73c1342aa06dfd07de7661a.png)

4.  Select the **Refresh now** option next to data flow name to refresh the dataflow. It runs the dataflow and moves data from the source file to lakehouse table. While it's in progress, you see a spinning circle under **Refreshed** column in the item view.

    ![](media/b42608129892a2c5ca48979ed9b29b57.png)

    ![](media/42e7a8098611d1bf0dc673cfafc85ea7.png)

5.  Refreshing data will take around 10-12 min.

![](media/0a4e8f08012dcf58429c8b579bdc4590.png)

1.  Once the dataflow is refreshed, select **wwilakehouse** in the left navigation panel to view the **dimension_customer** delta table. Select the table to preview its data.

![](media/ac4edd33fb07f6d9c88e67f3d0c165e6.png)

![](media/679135de20955e043ec29fb865c166c2.png)

1.  You can also use the SQL endpoint of the lakehouse to query the data with SQL statements. Select **SQL endpoint** from the **Lakehouse** drop-down menu at the top right of the screen.

![](media/4e56c5fd67c4538aeeca97256c91e4c1.png)

1.  In the wwilakehouse page, under Explorer select the **dimension_customer** table to preview its data and select **New SQL query** to write your SQL statements.

![](media/f56d6bee6fe0883c5943f2d49c636813.png)

1.  The following sample query aggregates the row count based on the **BuyingGroup column** of the **dimension_customer** table. SQL query files are saved automatically for future reference, and you can rename or delete these files based on your need. paste the code, select the **Run** icon at the top of the script file.

SQLCopy

SELECT BuyingGroup, Count(\*) AS Total

FROM dimension_customer

GROUP BY BuyingGroup

![](media/09c0084612f445156d990210127d30d0.png)

![](media/667f2ee6fec68a703e8340e9dbb14c7b.png)

## **Task 4: Build a report**

1.  In wwilakehouse, on the left-side pane select **Fabric Lakehouse** **Tutorial** -XX

    ![](media/3db1dd84fce132371928b6103197da63.png)

2.  In the **Fabric Lakehouse Tutorial-XX** view, select the **wwilakehouse** default dataset. This dataset is automatically created and has the same name as the lakehouse.

    ![](media/3b02ac2f1f08875b55d2ad0c1582dc03.png)

3.  From the dataset pane, you can view all the tables. You have options to create reports either from scratch, paginated report, or let Power BI automatically create a report based on your data. For this task, select **Auto-create** under **+Create a report**

![](media/9a91b32d8c1d7bf56a63909a584c4b22.png)

![](media/6aa8bddf017d0b74cf5190b3da2a9549.png)

![A screenshot of a computer Description automatically generated](media/cea36d57aed2f0fca0fea7f4bf9e2dc6.png)

1.  Since the table is a dimension and there are no measures in it, Power BI creates a measure for the row count and aggregates it across different columns, and creates different charts as shown in the following image.
2.  Save this report for the future by selecting **Save** from the top ribbon.

    ![](media/ada0f47d90e50b9955b01308f41c0271.png)

3.  In the **Save your replort** dialog box, enter a name for your report as !! **dimension_customer-report** !!and select **Save.**

![](media/3d1c57be7105890e4b5e793774d473d5.png)

1.  You will see a notification stating **Report saved**.

![A screenshot of a computer Description automatically generated](media/349c23a4b8660901f3c6efd8386f180f.png)

# Exercise 3: Ingest data into the lakehouse

In this exercise, you ingest additional dimensional and fact tables from the Wide World Importers (WWI) into the lakehouse.

## **Task 1: Ingest data**

In this task, you use the **Copy data activity** of the Data Factory pipeline to ingest sample data from an Azure storage account to the **Files** section of the lakehouse you created earlier.

1.  Select **Workspaces** in the left navigation pane, and then select your new workspace from the **Workspaces** menu. The items view of your workspace appears.

    ![](media/3c95d8f551d1e8d28e40ef611ccbfc8a.png)

    ![](media/44d8f2f912d51bb6a2cd81097117b0c2.png)

2.  In the **Fabric Lakehouse Tutorial-XX** workspace tab, drop down the **+New** button and select **Data pipeline (Preview)**.

    ![](media/4a434f992dfab6ae127e47556608f832.png)

3.  In the New pipeline dialog box, specify the name as !! **IngestDataFromSourceToLakehouse !!** and select **Create.** A new data factory pipeline is created and opened

    ![](media/db35382c72e1603afd65325946106cae.png)

    ![](media/4db5b211e132b1ae9aa24c11b6d805ac.png)

4.  On newly created data factory pipeline i.e **IngestDataFromSourceToLakehouse**, select **Add pipeline activity** to add an activity to the pipeline and select **Copy data**. This action adds copy data activity to the pipeline canvas.

    ![](media/1e5f76f4d0bd1c71f7867f67848a6277.png)

5.  Select the newly added copy data activity from the canvas. Activity properties appear in a pane below the canvas (you may need to expand the pane upwards by dragging the top edge). Under the **General** tab in the properties pane, specify the name for the copy data activity **Data Copy to Lakehouse**.

    ![](media/7e9f7ee65e50eba190ff4257ea5de9a4.png)

6.  Under **Source** tab of the selected copy data activity, select **External** as **Data store type** and then select **+ New** to create a new connection to data source.

    ![](media/f31d666ebbf2f40e0d261b2cdaaddeb6.png)

7.  For this task, all the sample data is available in a public container of Azure blob storage. You connect to this container to copy data from it. On the **New connection** wizard, select **Azure Blob Storage** and then select **Continue**.

![](media/3555bda91220430e2470ab9bfe9bc179.png)

1.  On the next screen of the **New connection** wizard, enter the following details and select **Create** to create the connection to the data source.

| **Property**        | **Value**                                                    |
|---------------------|--------------------------------------------------------------|
| Account name or URI | https://azuresynapsestorage.blob.core.windows.net/sampledata |
| Connection          | Create new connection                                        |
| Connection name     | wwisampledata                                                |
| Authentication kind | Anonymous                                                    |

![](media/2a955beb22d7782f65327b3eb4b76fe9.png)

1.  Once the new connection is created, return to the **Source** tab of the copy data activity, and the newly created connection is selected by default. Specify the following properties before moving to the destination settings.

| **Property**    | **Value**                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------|
| Data store type | External                                                                                                   |
| Connection      | wwisampledata                                                                                              |
| File path type  | File path                                                                                                  |
| File path       | Container name (first text box): sampledata Directory name (second text box): WideWorldImportersDW/parquet |
| Recursively     | Checked                                                                                                    |
| File Format     | Binary                                                                                                     |

![](media/05af72eb784214f727a8a5dd9132edfc.png)

1.  Under the **Destination** tab of the selected copy data activity, specify the following properties:

| **Property**              | **Value**                                     |
|---------------------------|-----------------------------------------------|
| Data store type           | Workspace                                     |
| Workspace data store type | Lakehouse                                     |
| Lakehouse                 | wwilakehouse                                  |
| Root Folder               | Files                                         |
| File path                 | Directory name (first text box): wwi-raw-data |
| File Format               | Binary                                        |

![](media/ebde676dd2d8f5f406afd313abd8886b.png)

1.  You have finished configuring the copy data activity. Select the **Save** button on the top ribbon (under **Home**) to save your changes.

![](media/dc8ca7a062b243ed1315e5331cbe7500.png)

1.  You will see a notification stating **Saving completed.**

![](media/d1da9ae284ba124b50cbdd3693343cca.png)

1.  In the I**ngestDataFromSourceToLakehouse** page select **Run** to execute your pipeline and its activity.

    ![](media/a44008d3cf45674ab6f1c98f2b4aca75.png)

2.  This action triggers data copy from the underlying data source to the specified lakehouse and might take up to a minute to complete. You can monitor the execution of the pipeline and its activity under the **Output** tab, which appears when you click anywhere on the canvas. Optionally, you can ![](media/cfd330997978d68d2a6a7327b5f973cc.png)

![](media/a63a523b28cb5b95121d595de2692409.png)

1.  Under the Output tab, select the **glasses icon** of **IngestDataFromSourceToLakehouse**  to look at the details of the data transfer.

![](media/c82130fa367039282176975150ecf357.png)

![A screenshot of a computer Description automatically generated](media/7e331bae3419bcd6dfac3f881bacae71.png)

1.  Once the data is copied, go to the items view **Fabric Lakehouse** **Tutorial-XX** and select your new lakehouse (**wwilakehouse**) to launch the **Lakehouse explorer**.

    ![](media/385fb1cc706feff13507203f024bccb4.png)

    ![](media/6de8d331db73268c293896b7698f18d9.png)

2.  Validate that in the **Lakehouse explorer** view, a new folder **wwi-raw-data** has been created and data for all the tables have been copied there.

![](media/344a35e31e262bd88efde8b3fed0e6a6.png)

# Exercise 4: Prepare and transform data in the lakehouse

## **Task 1: Prepare data**

From the previous exercise steps, we have raw data ingested from the source to the **Files** section of the lakehouse. Now you can transform that data and prepare it for creating delta tables.

1.  From the experience switcher located at the bottom left of the screen, select **Data engineering**.

    ![](media/f9db3a2d9fb91d41422b3cb2cfcb1a55.png)

2.  In the Synapse Data Engineering Home page, Select **Import notebook** from the **New** section at the top of the landing page.

    ![](media/5e7fbde5f2b3084d602caa688a595f1a.png)

3.  Select **Upload** from the **Import status** pane that opens on the right side of the screen.

    ![](media/648f5e812b5982b01fa39de6f19ef066.png)

4.  Navigate and select **01-Create Delta Tables, 02-Data Transformation-Business Aggregation** notebook from **C:\\LabFiles** and click on the **Open** button.

    ![](media/2fa8bd0e1bc94048dc3f23fb3b7934c8.png)

5.  You will see a notification stating **Imported successfully.**

    ![](media/a47563840a03a54c525b5f90d3c27589.png)

6.  After the import is successful, to see the newly imported notebooks select **Fabric Lakehouse Tutorial-XX** under the Recommended.

    ![](media/9623f65edf7c1bc96e0260f58ea67454.png)

    ![](media/0db8d6e907b147177dcf4698230dfc3a.png)

7.  In **Fabric Lakehouse Tutorial-XX** pane, Select **wwilakehouse** lakehouse to open it.

    ![](media/3c351753db504228bde18b9aeb408d90.png)

8.  Once the wwilakehouse lakehouse is opened, dropdown the **Open notebook** and select **Existing notebook** from the top navigation menu.

    ![](media/d4f1f04a93b7446cdcb2d5bd9dac7a17.png)

9.  From the list of **Open existing notebook**, select the **01 - Create Delta Tables** notebook and select **Open**.

    ![](media/afd4fbe1afb3551949be7abb15658f65.png)

10. In the open notebook in **Lakehouse explorer**, you see the notebook is already linked to your opened lakehouse.

![A screenshot of a computer Description automatically generated](media/bc31ca71f049f1c0573029dbe11a6129.png)

**Note**

Fabric provides the [**V-order**](https://learn.microsoft.com/en-us/fabric/data-engineering/delta-optimization-and-v-order) capability to write optimized delta lake files. V-order often improves compression by three to four times and up to 10 times performance acceleration over the Delta Lake files that aren't optimized. Spark in Fabric dynamically optimizes partitions while generating files with a default 128 MB size. The target file size may be changed per workload requirements using configurations. With the [**optimize write**](https://learn.microsoft.com/en-us/fabric/data-engineering/delta-optimization-and-v-order#what-is-optimized-write) capability, the Apache Spark engine that reduces the number of files written and aims to increase individual file size of the written data.

1.  Before you write data as delta lake tables in the **Tables** section of the lakehouse, you use two Fabric features (**V-order** and **Optimize Write**) for optimized data writing and for improved reading performance. To enable these features in your session, set these configurations in the first cell of your notebook.
2.  To start the notebook and execute the cell, select the **Run** icon that appears to the left of the cell upon hover.

![](media/6413852cb5ec4e230b09fa74e7ee27c2.png)

When running a cell, you didn't have to specify the underlying Spark pool or cluster details because Fabric provides them through Live Pool. Every Fabric workspace comes with a default Spark pool, called Live Pool. This means when you create notebooks, you don't have to worry about specifying any Spark configurations or cluster details. When you execute the first notebook command, the live pool is up and running in a few seconds. And the Spark session is established and it starts executing the code. Subsequent code execution is almost instantaneous in this notebook while the Spark session is active.

![](media/6f1e5efc59432aff86402d0b585bf98a.png)

1.  Next, you read raw data from the **Files** section of the lakehouse, and add more columns for different date parts as part of the transformation. you use partitionBy Spark API to partition the data before writing it as delta table based on the newly created data part columns (Year and Quarter).
2.  To execute the second cell, select **Run** icon that appears to the left of the cell upon hover.

    PythonCopy

    from pyspark.sql.functions import col, year, month, quarter

    table_name = 'fact_sale'

    df = spark.read.format("parquet").load('Files/wwi-raw-data/full/fact_sale_1y_full')

    df = df.withColumn('Year', year(col("InvoiceDateKey")))

    df = df.withColumn('Quarter', quarter(col("InvoiceDateKey")))

    df = df.withColumn('Month', month(col("InvoiceDateKey")))

    df.write.mode("overwrite").format("delta").partitionBy("Year","Quarter").save("Tables/" + table_name)

![A screenshot of a computer Description automatically generated](media/cc8b48934c7dadeb5c5b0acede48e345.png)

![](media/55f420e47a4e044cc2cd75c1815cb1fd.png)

1.  After the fact tables load, you can move on to loading data for the rest of the dimensions. The following cell creates a function to read raw data from the **Files** section of the lakehouse for each of the table names passed as a parameter. Next, it creates a list of dimension tables. Finally, it loops through the list of tables and creates a delta table for each table name that's read from the input parameter.
2.  Select the cell and select **Run** icon that appears to the left of the cell upon hover.

    PythonCopy

    from pyspark.sql.types import \*

    def loadFullDataFromSource(table_name):

    df = spark.read.format("parquet").load('Files/wwi-raw-data/full/' + table_name)

    df.write.mode("overwrite").format("delta").save("Tables/" + table_name)

    full_tables = [

    'dimension_city',

    'dimension_date',

    'dimension_employee',

    'dimension_stock_item'

    ]

    for table in full_tables:

    loadFullDataFromSource(table)

![](media/30451723e31da5c73353ea152b163232.png)

![A screenshot of a computer Description automatically generated](media/46f4313a0bde5a3ff8b2283fa363fb69.png)

1.  To validate the created tables, right click and select refresh on the **wwilakehouse** lakehouse. The tables appear.

    ![](media/05df1d47c57e1df91e68f6837ecd717a.png)

2.  In the **Reload site?** dialog box, click on the **Reload** button

    ![](media/128d21119709c48be3b6c4ffa6205f8f.png)

    ![](media/42cfa21503de0a0ef9a5f7a71331a283.png)

3.  Go the items view of the workspace again select **Fabric Lakehouse Tutorial-XX** and select the **wwilakehouse** lakehouse to open it.

    ![](media/7d7bad57b1d9259380098b31ab3bec68.png)

    ![](media/3c351753db504228bde18b9aeb408d90.png)

4.  Now, open the second notebook. In the lakehouse view, dropdown the **Open notebook** and select **Existing notebook** from the top navigation menu.

    ![](media/5d1fe0815ef47ba520fafb46c8162940.png)

5.  From the list of Open existing notebook, select the **02 - Data Transformation - Business** **Aggregation** notebook and click on the **Open**.

    ![](media/c4736fe38b9553bd2499f8a1f3f49ce3.png)

6.  In the open notebook in **Lakehouse explorer**, you see the notebook is already linked to your opened lakehouse.
7.  To start the notebook and select the 1st cell and select the **Run** icon that appears to the left of the cell upon hover.

![](media/4aee350a9a6a88b955a57cf80df309a1.png)

1.  An organization might have data engineers working with Scala/Python and other data engineers working with SQL (Spark SQL or T-SQL), all working on the same copy of the data. Fabric makes it possible for these different groups, with varied experience and preference, to work and collaborate. The two different approaches transform and generate business aggregates. You can pick the one suitable for you or mix and match these approaches based on your preference without compromising on the performance:
-   **Approach \#1** - Use PySpark to join and aggregates data for generating business aggregates. This approach is preferable to someone with a programming (Python or PySpark) background.
-   **Approach \#2** - Use Spark SQL to join and aggregates data for generating business aggregates. This approach is preferable to someone with SQL background, transitioning to Spark.
1.  **Approach \#1 (sale_by_date_city)** - Use PySpark to join and aggregate data for generating business aggregates. With the following code, you create three different Spark dataframes, each referencing an existing delta table. Then you join these tables using the dataframes, do group by to generate aggregation, rename a few of the columns, and finally write it as a delta table in the **Tables** section of the lakehouse to persist with the data.

    In this cell, you create three different Spark dataframes, each referencing an existing delta table.

    PythonCopy

    df_fact_sale = spark.read.table("wwilakehouse.fact_sale")

    df_dimension_date = spark.read.table("wwilakehouse.dimension_date")

    df_dimension_city = spark.read.table("wwilakehouse.dimension_city")

    ![](media/5a60a11ff1bb5bae7a789ddb6239a057.png)

2.  In this cell, you join these tables using the dataframes created earlier, do group by to generate aggregation, rename a few of the columns, and finally write it as a delta table in the **Tables** section of the lakehouse.

    PythonCopy

    sale_by_date_city = df_fact_sale.alias("sale") \\

    .join(df_dimension_date.alias("date"), df_fact_sale.InvoiceDateKey == df_dimension_date.Date, "inner") \\

    .join(df_dimension_city.alias("city"), df_fact_sale.CityKey == df_dimension_city.CityKey, "inner") \\

    .select("date.Date", "date.CalendarMonthLabel", "date.Day", "date.ShortMonth", "date.CalendarYear", "city.City", "city.StateProvince", "city.SalesTerritory", "sale.TotalExcludingTax", "sale.TaxAmount", "sale.TotalIncludingTax", "sale.Profit")\\

    .groupBy("date.Date", "date.CalendarMonthLabel", "date.Day", "date.ShortMonth", "date.CalendarYear", "city.City", "city.StateProvince", "city.SalesTerritory")\\

    .sum("sale.TotalExcludingTax", "sale.TaxAmount", "sale.TotalIncludingTax", "sale.Profit")\\

    .withColumnRenamed("sum(TotalExcludingTax)", "SumOfTotalExcludingTax")\\

    .withColumnRenamed("sum(TaxAmount)", "SumOfTaxAmount")\\

    .withColumnRenamed("sum(TotalIncludingTax)", "SumOfTotalIncludingTax")\\

    .withColumnRenamed("sum(Profit)", "SumOfProfit")\\

    .orderBy("date.Date", "city.StateProvince", "city.City")

    sale_by_date_city.write.mode("overwrite").format("delta").option("overwriteSchema", "true").save("Tables/aggregate_sale_by_date_city")

    ![](media/63622f2b27511a0553a41ad9e0e42392.png)

3.  **Approach \#2 (sale_by_date_employee)** - Use Spark SQL to join and aggregate data for generating business aggregates. With the following code, you create a temporary Spark view by joining three tables, do group by to generate aggregation, and rename a few of the columns. Finally, you read from the temporary Spark view and finally write it as a delta table in the **Tables** section of the lakehouse to persist with the data.

    In this cell, you create a temporary Spark view by joining three tables, do group by to generate aggregation, and rename a few of the columns.

    PythonCopy

    %%sql

    CREATE OR REPLACE TEMPORARY VIEW sale_by_date_employee

    AS

    SELECT

    DD.Date, DD.CalendarMonthLabel

    , DD.Day, DD.ShortMonth Month, CalendarYear Year

    ,DE.PreferredName, DE.Employee

    ,SUM(FS.TotalExcludingTax) SumOfTotalExcludingTax

    ,SUM(FS.TaxAmount) SumOfTaxAmount

    ,SUM(FS.TotalIncludingTax) SumOfTotalIncludingTax

    ,SUM(Profit) SumOfProfit

    FROM wwilakehouse.fact_sale FS

    INNER JOIN wwilakehouse.dimension_date DD ON FS.InvoiceDateKey = DD.Date

    INNER JOIN wwilakehouse.dimension_Employee DE ON FS.SalespersonKey = DE.EmployeeKey

    GROUP BY DD.Date, DD.CalendarMonthLabel, DD.Day, DD.ShortMonth, DD.CalendarYear, DE.PreferredName, DE.Employee

    ORDER BY DD.Date ASC, DE.PreferredName ASC, DE.Employee ASC

![](media/beb26a6332862173d601a9db48cf2019.png)

1.  In this cell, you read from the temporary Spark view created in the previous cell and finally write it as a delta table in the **Tables** section of the lakehouse.

    PythonCopy

    sale_by_date_employee = spark.sql("SELECT \* FROM sale_by_date_employee")

    sale_by_date_employee.write.mode("overwrite").format("delta").option("overwriteSchema", "true").save("Tables/aggregate_sale_by_date_employee")

![](media/a005e4b2f9c0ac5b3dd1e3c57b412146.png)

1.  To validate the created tables, right click and select refresh on the **wwilakehouse** lakehouse. The aggregate tables appear.

![](media/063471332dfaf578eacc281d0e4881d2.png)

![](media/c13b538b4d5e5998cc7505f6ddb3d9c4.png)

Both the approaches produce a similar outcome. You can choose based on your background and preference, to minimize the need for you to learn a new technology or compromise on the performance.

Also you may notice that you're writing data as delta lake files. The automatic table discovery and registration feature of Fabric picks up and registers them in the metastore. You don't need to explicitly call CREATE TABLE statements to create tables to use with SQL.

# Exercise 5: Building reports in Microsoft Fabric

In this section of the tutorial, you create a Power BI data model and create a report from scratch.

**Important**

Microsoft Fabric is in [**preview**](https://learn.microsoft.com/en-us/fabric/get-started/preview).

## Prerequisites

-   [Prepare and transform the data using notebooks and Spark runtime](https://learn.microsoft.com/en-us/fabric/data-engineering/tutorial-lakehouse-data-preparation)

## **Task 1: Build a report**

Power BI is natively integrated in the whole Fabric experience. This native integration brings a unique mode, called DirectLake, of accessing the data from the lakehouse to provide the most performant query and reporting experience. DirectLake mode is a groundbreaking new engine capability to analyze very large datasets in Power BI. The technology is based on the idea of loading parquet-formatted files directly from a data lake without having to query a data warehouse or lakehouse endpoint, and without having to import or duplicate data into a Power BI dataset. DirectLake is a fast path to load the data from the data lake straight into the Power BI engine, ready for analysis.

In traditional DirectQuery mode, the Power BI engine directly queries the data from the source to execute each query, and the query performance depends on data retrieval speed. DirectQuery eliminates the need to copy data, ensuring that any changes in the source are immediately reflected in the query results during the import. On the other hand, performance is better because the data is readily available in the memory without querying data from the source for each query execution. However, the Power BI engine must first copy the data into memory during data refresh. Only changes to the underlying data source are picked up during the next data refresh(in scheduled as well as on-demand refresh).

DirectLake mode now eliminates this import requirement by loading the data files directly into memory. Because there's no explicit import process, it's possible to pick up any changes at the source as they occur, thus combining the advantages of DirectQuery and import mode while avoiding their disadvantages. DirectLake mode is therefore the ideal choice for analyzing very large datasets and datasets with frequent updates at the source.

1.  From your **wwilakehouse** lakehouse, select **SQL endpoint** from the **Lakehouse** drop-down menu at the top right of the screen.

    ![](media/71a46d396fe94228bdba632c3761642e.png)

    ![](media/5c9f2e4917702851b0553b5a80f201ab.png)

2.  From the SQL endpoint pane, you should be able to see all the tables you created. If you don't see them yet, select the **Refresh** icon at the top. Next, select the **Model** tab at the bottom to open the default Power BI dataset.

![](media/0495b5423e7746064a52407bb9d50aab.png)

1.  For this data model, you need to define the relationship between different tables so that you can create reports and visualizations based on data coming across different tables. From the **fact_sale** table, drag the **CityKey** field and drop it on the **CityKey** field in the **dimension_city** table to create a relationship. The **Create Relationship** dialog box appears.

    ![](media/825171b88beec9fd93c658c828d50501.png)

2.  In the **Create Relationship** dialog box:
    -   **Table 1** is populated with **fact_sale** and the column of **CityKey**.
    -   **Table 2** is populated with **dimension_city** and the column of **CityKey**.
    -   Cardinality: **Many to one (\*:1)**
    -   Cross filter direction: **Single**
    -   Leave the box next to **Make this relationship active** selected.
    -   Select the box next to **Assume referential integrity.**
    -   Select **Confirm.**

        ![](media/5afa7eb456103712c74a1326836e9db9.png)

        ![A screenshot of a computer Description automatically generated](media/bd46e47584b588fd760229cac8d752aa.png)

**Note:** *When defining relationships for this report, make sure you have a many to one relationship from the fact_sale table (Table 1) to the dimension_\* tables (Table 2) and not vice versa.*

1.  Next, add these relationships with the same **Create Relationship** settings as shown above but with the following tables and columns:
    1.  StockItemKey(fact_sale) - StockItemKey(dimension_stock_item)
    2.  Salespersonkey(fact_sale) - EmployeeKey(dimension_employee)
    3.  CustomerKey(fact_sale) - CustomerKey(dimension_customer)
    4.  InvoiceDateKey(fact_sale) - Date(dimension_date)

        After you add these relationships, your data model is ready for reporting as shown in the following image:

2.  Select **New report** to start creating reports/dashboards in Power BI. On the Power BI report canvas, you can create reports to meet your business requirements by dragging required columns from the **Data** pane to the canvas and using one or more of available visualizations.
3.  Add a title:
    1.  In the Ribbon, select **Text box**.
    2.  Type in **WW Importers Profit Reporting**.
    3.  Highlight the text and increase size to 20 and place in the upper left of the report page.
4.  Add a Card:
    1.  On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection creates a column chart and adds the field to the Y-axis.
    2.  With the bar chart selected, select the **Card** visual in the visualization pane. This selection converts the visual to a card.
    3.  Place the card under the title.
5.  Add a Bar chart:
    1.  On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection creates a column chart and adds the field to the Y-axis.
    2.  On the **Data** pane, expand **dimension_city** and check the box for **SalesTerritory**. This selection adds the field to the Y-axis.
    3.  With the bar chart selected, select the **Clustered bar chart** visual in the visualization pane. This selection converts the column chart into a bar chart.
    4.  Resize the Bar chart to fill in the area under the title and Card.
6.  Click anywhere on the blank canvas (or press the Esc key) so the bar chart is no longer selected.
7.  Build a stacked area chart visual:
    1.  On the **Visualizations** pane, select the **Stacked area chart** visual.
    2.  Reposition and resize the stacked area chart to the right of the card and bar chart visuals created in the previous steps.
    3.  On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. Expand dimension_date and check the box next to **FiscalMonthNumber**. This selection creates a filled line chart showing profit by fiscal month.
    4.  On the **Data** pane, expand **dimension_stock_item** and drag **BuyingPackage** into the Legend field well. This selection adds a line for each of the Buying Packages.
8.  Click anywhere on the blank canvas (or press the Esc key) so the stacked area chart is no longer selected.
9.  Build a column chart:
    1.  On the **Visualizations** pane, select the **Stacked column chart** visual.
    2.  On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection adds the field to the Y-axis.
    3.  On the **Data** pane, expand **dimension_employee** and check the box next to **Employee**. This selection adds the field to the X-axis.
10. Click anywhere on the blank canvas (or press the Esc key) so the chart is no longer selected.
11. From the ribbon, select **File** \> **Save**.
12. Enter the name of your report as **Profit Reporting**.
13. Select **Save**.
