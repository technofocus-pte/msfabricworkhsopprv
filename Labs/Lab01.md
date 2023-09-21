Lab 1: Lakehouse end-to-end scenario: overview and architecture

This lab walks you through an end-to-end scenario from data acquisition to data consumption. It helps you build a basic understanding of Fabric, including the different experiences and how they integrate, as well as the professional and citizen developer experiences that come with working on this platform. This lab isn't intended to be a reference architecture, an exhaustive list of features and functionality, or a recommendation of specific best practices.

# Exercise 1: Setup Lakehouse end-to-end scenario

Traditionally, organizations have been building modern data warehouses for their transactional and structured data analytics needs. And data lakehouses for big data (semi/Lab01 (1).png)

1.  In the **Microsoft Fabric** window, enter your **Microsoft 365** credentials, and click on the **Submit** button.

    ![](media/Lab01 (2).png)

2.  Then, In the **Microsoft** window enter the password and click on the **Sign in** button\*\*.\*\*

    ![](media/Lab01 (3).png)

3.  In **Stay signed in?** window, click on the **Yes** button.

    ![](media/Lab01 (4).png)

![A screenshot of a computer Description automatically generated](media/Lab01 (5).png)

# Task 2: Start the Microsoft Fabric (Preview) trial

Follow these steps to start your Fabric (Preview) trial.

Open your browser, navigate to the address bar, and type or paste the following URL: /Lab01 (6).png)

1.  On Power BI home page select the Account manager. In the Account manager, select **Start trial**.

![](media/Lab01 (7).png)

1.  If prompted, agree to the terms and then select **Start trial**.

    ![](media/Lab01 (8).png)

2.  Once your trial capacity is ready, you receive a confirmation message. Select **Got it** to begin working in Fabric.

    ![](media/Lab01 (9).png)

3.  Open your Account manager again. Notice that you now have a heading for **Trial status**. Your Account manager keeps track of the number of days remaining in your trial. You also see the countdown in your Fabric menu bar when you work in a product experience.

    ![](media/Lab01 (10).png)

# Task 3: onedrive configured sign up for the microsoft 365 admin center

Open your browser, navigate to the address bar, and type or paste the following URL: /Lab01 (11).png)

1.  In the **Microsoft Azure** window, enter your **Sign-in** credentials, and click on the **Next** button.

    ![A screenshot of a computer Description automatically generated](media/Lab01 (12).png)

2.  Then, In the **Microsoft** window enter the password and click on the **Sign in** button\*\*.\*\*

    ![](media/Lab01 (13).png)

3.  In **Stay signed in?** window, click on the **Yes** button.

    ![](media/Lab01 (14).png)

4.  In Microsoft 365 admin center page on the left-side, select the **App launcher.**

    ![A screenshot of a computer Description automatically generated](media/Lab01 (15).png)

5.  In the Microsoft 365 page from the Apps pane select **OneDrive**

    ![A screenshot of a computer Description automatically generated](media/Lab01 (16).png)

6.  In One Drive page, under **Securely store and share files** select **your One Drive is ready**

    ![A screenshot of a computer Description automatically generated](media/Lab01 (17).png)

    ![](media/Lab01 (18).png)

# Exercise 2: Build and implement an end-to-end lakehouse for your organization

## Task 1: Create a Fabric workspace

In this task, you create a Fabric workspace. The workspace contains all the items needed for this lakehouse tutorial, which includes lakehouse, dataflows, Data Factory pipelines, the notebooks, Power BI datasets, and reports.

Open your browser, navigate to the address bar, and type or paste the following URL: /Lab01 (19).png)

1.  In the Workspaces pane Select **+** **New workspace**.

    ![](media/Lab01 (20).png)

2.  In the **Create a workspace tab**, enter the following details and click on the **Apply** button.

| **Name**                   | **!! Fabric Lakehouse Tutorial-XX !!**\*(\*XX can be a unique number) (here, we entered **Fabric Lakehouse Tutorial-29**) |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **Description**            | !!This workspace contains all the items for the lakehouse tutorial !!                                                     |
| **Advanced**               | Under **License mode**, select **Trial**                                                                                  |
| **Default storage format** | **Small dataset storage format**                                                                                          |
| **Template apps**          | **Check the Develop template apps**                                                                                       |

![](media/Lab01 (21).png)

![](media/Lab01 (22).png)

![](media/Lab01 (23).png)

1.  Wait for the deployment to complete. It takes 2-3 minutes to complete

![](media/Lab01 (24).png)

## Task 2: Create a lakehouse

1.  In the **Power BI Fabric Lakehouse Tutorial-XX** page, click on the **Power BI** icon located at the bottom left and select **Data Engineering** under the Synapse.

    ![](media/Lab01 (25).png)

2.  In the **Synapse** **Data Engineering** **Home** page, select **Lakehouse(Preview)** to create a lakehouse.

![](media/Lab01 (26).png)

1.  In the **New lakehouse** dialog box, enter!! **wwilakehouse** !!in the **Name** field, click on the **Create** button and open the new lakehouse.

    ![](media/Lab01 (27).png)

    ![](media/Lab01 (28).png)

2.  You will see a notification stating **Successfully created SQL endpoint**.

    ![](media/Lab01 (29).png)

## Task 3: Ingest sample data

1.  In the **wwilakehouse** home page, under the **Explorer pane**, Select **New Dataflow Gen2 under Get data in your lakehouse.**

    ![](media/Lab01 (30).png)

    On the new dataflow pane, select **Import from a Text/Lab01 (31).png**)

2.  On the **Connect to data source** pane, select the **Upload file** radio button. Click on **Browse button** and browse your VM to **C:\\LabFiles** and then select **dimension_customer.csv** file. Select **Open.**

    ![](media/Lab01 (32).png)

    ![](media/Lab01 (33).png)

3.  In the Connect to data source pane select **Next.**

    ![](media/Lab01( 34).png)

4.  From the **Preview file data** page, preview the data and select **Create** to proceed and return back to the dataflow canvas.

    ![](media/Lab01 (35).png)

5.  In the **Query settings** pane, enter **dimension_customer** for the **Name** field. From the menu items, select **Add data destination** and select **Lakehouse**.

    ![](media/Lab01(36).png)

    **Note:**

-   *If needed, from the Connect to data destination screen, sign into your account. Select Next.*
-   Navigate to the **wwilakehouse** in your workspace.
-   If the **dimension_customer** table doesn't exist, select the **New table** setting and enter the table name **dimension_customer**. If the table already exists, select the **Existing table** setting and choose **dimension_customer** from the list of tables in the object explorer. Select **Next**.

**Note:** *Fabric adds a space and number at the end of the table name by default. Table names must be lower case and must not contain spaces. Please rename it appropriately and remove any spaces from the table name.*

1.  From the dataflow canvas, you can easily transform the data based on your business requirements. For simplicity, we aren't making any changes in this task. To proceed, select **Publish** at the bottom right of the screen.

    ![](media/Lab01(37).png)

2.  A spinning circle next to the dataflow's name indicates publishing is in progress in the item view. ![](media/Lab01(38).png)
3.  In the **Fabric Lakehouse Tutorial-XX** tab, when publishing is complete, select the Dataflow1 **...** and select **Properties**.

    ![](media/Lab01(39).png)

4.  In the Dataflow 1 tab ,rename the dataflow to !! **Load Lakehouse Table** !! and select **Save**.

    ![](media/Lab01(40).png)

5.  Select the **Refresh now** option next to data flow name to refresh the dataflow. It runs the dataflow and moves data from the source file to lakehouse table. While it's in progress, you see a spinning circle under **Refreshed** column in the item view.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(41).png)

6.  Refreshing data will take around 10-12 min.

![](media/Lab01(42).png)

1.  Once the dataflow is refreshed, select **wwilakehouse** in the left navigation panel to view the **dimension_customer** delta table. Select the table to preview its data.

![](media/Lab01(43).png)

![](media/Lab01(44).png)

1.  You can also use the SQL endpoint of the lakehouse to query the data with SQL statements. Select **SQL endpoint** from the **Lakehouse** drop-down menu at the top right of the screen.

![](media/Lab01(45).png)

1.  In the wwilakehouse page, under Explorer select the **dimension_customer** table to preview its data and select **New SQL query** to write your SQL statements.

![](media/Lab01(46).png)

1.  The following sample query aggregates the row count based on the **BuyingGroup column** of the **dimension_customer** table. SQL query files are saved automatically for future reference, and you can rename or delete these files based on your need. paste the code, select the **Run** icon at the top of the script file.

SQLCopy

SELECT BuyingGroup, Count(\*) AS Total

FROM dimension_customer

GROUP BY BuyingGroup

![](media/Lab01(47).png)

![](media/Lab01(48).png)

## Task 4: Build a report

1.  In wwilakehouse, on the left-side pane select **Fabric Lakehouse** **Tutorial** -XX

    ![](media/Lab01(\#).png)

2.  In the **Fabric Lakehouse Tutorial-XX** view, select the **wwilakehouse** default dataset. This dataset is automatically created and has the same name as the lakehouse.

    ![](media/Lab01(\#).png)

3.  From the dataset pane, you can view all the tables. You have options to create reports either from scratch, paginated report, or let Power BI automatically create a report based on your data. For this task, select **Auto-create** under **+Create a report**

![](media/Lab01(\#).png)

![](media/Lab01(\#).png)

![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

1.  Since the table is a dimension and there are no measures in it, Power BI creates a measure for the row count and aggregates it across different columns, and creates different charts as shown in the following image.
2.  Save this report for the future by selecting **Save** from the top ribbon.

    ![](media/Lab01(\#).png)

3.  In the **Save your replort** dialog box, enter a name for your report as !! **dimension_customer-report** !!and select **Save.**

![](media/Lab01(\#).png)

1.  You will see a notification stating **Report saved**.

![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

# Exercise 3: Ingest data into the lakehouse

In this exercise, you ingest additional dimensional and fact tables from the Wide World Importers (WWI) into the lakehouse.

## Task 1: Ingest data

In this task, you use the **Copy data activity** of the Data Factory pipeline to ingest sample data from an Azure storage account to the **Files** section of the lakehouse you created earlier.

1.  Select **Workspaces** in the left navigation pane, and then select your new workspace from the **Workspaces** menu. The items view of your workspace appears.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

2.  In the **Fabric Lakehouse Tutorial-XX** workspace tab, drop down the **+New** button and select **Data pipeline (Preview)**.

    ![](media/Lab01(\#).png)

3.  In the New pipeline dialog box, specify the name as !! **IngestDataFromSourceToLakehouse !!** and select **Create.** A new data factory pipeline is created and opened

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

4.  On newly created data factory pipeline i.e **IngestDataFromSourceToLakehouse**, select **Add pipeline activity** to add an activity to the pipeline and select **Copy data**. This action adds copy data activity to the pipeline canvas.

    ![](media/Lab01(\#).png)

5.  Select the newly added copy data activity from the canvas. Activity properties appear in a pane below the canvas (you may need to expand the pane upwards by dragging the top edge). Under the **General** tab in the properties pane, specify the name for the copy data activity **Data Copy to Lakehouse**.

    ![](media/Lab01(\#).png)

6.  Under **Source** tab of the selected copy data activity, select **External** as **Data store type** and then select **+ New** to create a new connection to data source.

    ![](media/Lab01(\#).png)

7.  For this task, all the sample data is available in a public container of Azure blob storage. You connect to this container to copy data from it. On the **New connection** wizard, select **Azure Blob Storage** and then select **Continue**.

![](media/Lab01(\#).png)

1.  On the next screen of the **New connection** wizard, enter the following details and select **Create** to create the connection to the data source.

| **Property**        | **Value**                                                    |
|---------------------|--------------------------------------------------------------|
| Account name or URI | https://azuresynapsestorage.blob.core.windows.net/sampledata |
| Connection          | Create new connection                                        |
| Connection name     | wwisampledata                                                |
| Authentication kind | Anonymous                                                    |

![](media/Lab01(\#).png)

1.  Once the new connection is created, return to the **Source** tab of the copy data activity, and the newly created connection is selected by default. Specify the following properties before moving to the destination settings.

| **Property**    | **Value**                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------|
| Data store type | External                                                                                                   |
| Connection      | wwisampledata                                                                                              |
| File path type  | File path                                                                                                  |
| File path       | Container name (first text box): sampledata Directory name (second text box): WideWorldImportersDW/parquet |
| Recursively     | Checked                                                                                                    |
| File Format     | Binary                                                                                                     |

![](media/Lab01(\#).png)

1.  Under the **Destination** tab of the selected copy data activity, specify the following properties:

| **Property**              | **Value**                                     |
|---------------------------|-----------------------------------------------|
| Data store type           | Workspace                                     |
| Workspace data store type | Lakehouse                                     |
| Lakehouse                 | wwilakehouse                                  |
| Root Folder               | Files                                         |
| File path                 | Directory name (first text box): wwi-raw-data |
| File Format               | Binary                                        |

![](media/Lab01(\#).png)

1.  You have finished configuring the copy data activity. Select the **Save** button on the top ribbon (under **Home**) to save your changes.

![](media/Lab01(\#).png)

1.  You will see a notification stating **Saving completed.**

![](media/Lab01(\#).png)

1.  In the I**ngestDataFromSourceToLakehouse** page select **Run** to execute your pipeline and its activity.

    ![](media/Lab01(\#).png)

2.  This action triggers data copy from the underlying data source to the specified lakehouse and might take up to a minute to complete. You can monitor the execution of the pipeline and its activity under the **Output** tab, which appears when you click anywhere on the canvas. Optionally, you can ![](media/Lab01(\#).png)

![](media/Lab01(\#).png)

1.  Under the Output tab, select the **glasses icon** of **IngestDataFromSourceToLakehouse** to look at the details of the data transfer.

![](media/Lab01(\#).png)

![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

1.  Once the data is copied, go to the items view **Fabric Lakehouse** **Tutorial-XX** and select your new lakehouse (**wwilakehouse**) to launch the **Lakehouse explorer**.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

2.  Validate that in the **Lakehouse explorer** view, a new folder **wwi-raw-data** has been created and data for all the tables have been copied there.

![](media/Lab01(\#).png)

# Exercise 4: Prepare and transform data in the lakehouse

## Task 1: Prepare data

From the previous exercise steps, we have raw data ingested from the source to the **Files** section of the lakehouse. Now you can transform that data and prepare it for creating delta tables.

1.  From the experience switcher located at the bottom left of the screen, select **Data engineering**.

    ![](media/Lab01(\#).png)

2.  In the Synapse Data Engineering Home page, Select **Import notebook** from the **New** section at the top of the landing page.

    ![](media/Lab01(\#).png)

3.  Select **Upload** from the **Import status** pane that opens on the right side of the screen.

    ![](media/Lab01(\#).png)

4.  Navigate and select **01-Create Delta Tables, 02-Data Transformation-Business Aggregation** notebook from **C:\\LabFiles** and click on the **Open** button.

    ![](media/Lab01(\#).png)

5.  You will see a notification stating **Imported successfully.**

    ![](media/Lab01(\#).png)

6.  After the import is successful, to see the newly imported notebooks select **Fabric Lakehouse Tutorial-XX** under the Recommended.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

7.  In **Fabric Lakehouse Tutorial-XX** pane, Select **wwilakehouse** lakehouse to open it.

    ![](media/Lab01(\#).png)

8.  Once the wwilakehouse lakehouse is opened, dropdown the **Open notebook** and select **Existing notebook** from the top navigation menu.

    ![](media/Lab01(\#).png)

9.  From the list of **Open existing notebook**, select the **01 - Create Delta Tables** notebook and select **Open**.

    ![](media/Lab01(\#).png)

10. In the open notebook in **Lakehouse explorer**, you see the notebook is already linked to your opened lakehouse.

![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

**Note**

Fabric provides the [**V-order**](https://learn.microsoft.com/en-us/fabric/data-engineering/delta-optimization-and-v-order) capability to write optimized delta lake files. V-order often improves compression by three to four times and up to 10 times performance acceleration over the Delta Lake files that aren't optimized. Spark in Fabric dynamically optimizes partitions while generating files with a default 128 MB size. The target file size may be changed per workload requirements using configurations. With the [**optimize write**](https://learn.microsoft.com/en-us/fabric/data-engineering/delta-optimization-and-v-order#what-is-optimized-write) capability, the Apache Spark engine that reduces the number of files written and aims to increase individual file size of the written data.

1.  Before you write data as delta lake tables in the **Tables** section of the lakehouse, you use two Fabric features (**V-order** and **Optimize Write**) for optimized data writing and for improved reading performance. To enable these features in your session, set these configurations in the first cell of your notebook.
2.  To start the notebook and execute the cell, select the **Run** icon that appears to the left of the cell upon hover.

![](media/Lab01(\#).png)

When running a cell, you didn't have to specify the underlying Spark pool or cluster details because Fabric provides them through Live Pool. Every Fabric workspace comes with a default Spark pool, called Live Pool. This means when you create notebooks, you don't have to worry about specifying any Spark configurations or cluster details. When you execute the first notebook command, the live pool is up and running in a few seconds. And the Spark session is established and it starts executing the code. Subsequent code execution is almost instantaneous in this notebook while the Spark session is active.

![](media/Lab01(\#).png)

1.  Next, you read raw data from the **Files** section of the lakehouse, and add more columns for different date parts as part of the transformation. you use partitionBy Spark API to partition the data before writing it as delta table based on the newly created data part columns (Year and Quarter).
2.  To execute the second cell, select **Run** icon that appears to the left of the cell upon hover.

    PythonCopy

    from pyspark.sql.functions import col, year, month, quarter

    table_name = 'fact_sale'

df = spark.read.format("parquet").load('Files/Lab01(\#).png)

![](media/Lab01(\#).png)

1.  After the fact tables load, you can move on to loading data for the rest of the dimensions. The following cell creates a function to read raw data from the **Files** section of the lakehouse for each of the table names passed as a parameter. Next, it creates a list of dimension tables. Finally, it loops through the list of tables and creates a delta table for each table name that's read from the input parameter.
2.  Select the cell and select **Run** icon that appears to the left of the cell upon hover.

    PythonCopy

    from pyspark.sql.types import \*

    def loadFullDataFromSource(table_name):

df = spark.read.format("parquet").load('Files/Lab01(\#).png)

![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

1.  To validate the created tables, right click and select refresh on the **wwilakehouse** lakehouse. The tables appear.

    ![](media/Lab01(\#).png)

2.  In the **Reload site?** dialog box, click on the **Reload** button

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

3.  Go the items view of the workspace again select **Fabric Lakehouse Tutorial-XX** and select the **wwilakehouse** lakehouse to open it.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

4.  Now, open the second notebook. In the lakehouse view, dropdown the **Open notebook** and select **Existing notebook** from the top navigation menu.

    ![](media/Lab01(\#).png)

5.  From the list of Open existing notebook, select the **02 - Data Transformation - Business** **Aggregation** notebook and click on the **Open**.

    ![](media/Lab01(\#).png)

6.  In the open notebook in **Lakehouse explorer**, you see the notebook is already linked to your opened lakehouse.
7.  To start the notebook and select the 1st cell and select the **Run** icon that appears to the left of the cell upon hover.

![](media/Lab01(\#).png)

An organization might have data engineers working with Scala/Lab01(\#).png)

1.  In this cell, you join these tables using the dataframes created earlier, do group by to generate aggregation, rename a few of the columns, and finally write it as a delta table in the **Tables** section of the lakehouse.

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

    sale_by_date_city.write.mode("overwrite").format("delta").option("overwriteSchema", "true").save("Tables/Lab01(\#).png)

2.  **Approach \#2 (sale_by_date_employee)** - Use Spark SQL to join and aggregate data for generating business aggregates. With the following code, you create a temporary Spark view by joining three tables, do group by to generate aggregation, and rename a few of the columns. Finally, you read from the temporary Spark view and finally write it as a delta table in the **Tables** section of the lakehouse to persist with the data.

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

![](media/Lab01(\#).png)

1.  In this cell, you read from the temporary Spark view created in the previous cell and finally write it as a delta table in the **Tables** section of the lakehouse.

    PythonCopy

    sale_by_date_employee = spark.sql("SELECT \* FROM sale_by_date_employee")

sale_by_date_employee.write.mode("overwrite").format("delta").option("overwriteSchema", "true").save("Tables/Lab01(\#).png)

1.  To validate the created tables, right click and select refresh on the **wwilakehouse** lakehouse. The aggregate tables appear.

![](media/Lab01(\#).png)

![](media/Lab01(\#).png)

Both the approaches produce a similar outcome. You can choose based on your background and preference, to minimize the need for you to learn a new technology or compromise on the performance.

Also you may notice that you're writing data as delta lake files. The automatic table discovery and registration feature of Fabric picks up and registers them in the metastore. You don't need to explicitly call CREATE TABLE statements to create tables to use with SQL.

# Exercise 5: Building reports in Microsoft Fabric

In this section of the tutorial, you create a Power BI data model and create a report from scratch.

**Important**

Microsoft Fabric is in [**preview**](https://learn.microsoft.com/en-us/fabric/get-started/preview).

## Prerequisites

-   [Prepare and transform the data using notebooks and Spark runtime](https://learn.microsoft.com/en-us/fabric/data-engineering/tutorial-lakehouse-data-preparation)

## Task 1: Build a report

Power BI is natively integrated in the whole Fabric experience. This native integration brings a unique mode, called DirectLake, of accessing the data from the lakehouse to provide the most performant query and reporting experience. DirectLake mode is a groundbreaking new engine capability to analyze very large datasets in Power BI. The technology is based on the idea of loading parquet-formatted files directly from a data lake without having to query a data warehouse or lakehouse endpoint, and without having to import or duplicate data into a Power BI dataset. DirectLake is a fast path to load the data from the data lake straight into the Power BI engine, ready for analysis.

In traditional DirectQuery mode, the Power BI engine directly queries the data from the source to execute each query, and the query performance depends on data retrieval speed. DirectQuery eliminates the need to copy data, ensuring that any changes in the source are immediately reflected in the query results during the import. On the other hand, performance is better because the data is readily available in the memory without querying data from the source for each query execution. However, the Power BI engine must first copy the data into memory during data refresh. Only changes to the underlying data source are picked up during the next data refresh(in scheduled as well as on-demand refresh).

DirectLake mode now eliminates this import requirement by loading the data files directly into memory. Because there's no explicit import process, it's possible to pick up any changes at the source as they occur, thus combining the advantages of DirectQuery and import mode while avoiding their disadvantages. DirectLake mode is therefore the ideal choice for analyzing very large datasets and datasets with frequent updates at the source.

1.  From your **wwilakehouse** lakehouse, select **SQL endpoint** from the **Lakehouse** drop-down menu at the top right of the screen.

    ![](media/Lab01(\#).png)

    ![](media/Lab01(\#).png)

2.  From the SQL endpoint pane, you should be able to see all the tables you created. If you don't see them yet, select the **Refresh** icon at the top. Next, select the **Model** tab at the bottom to open the default Power BI dataset.

![](media/Lab01(\#).png)

1.  For this data model, you need to define the relationship between different tables so that you can create reports and visualizations based on data coming across different tables. From the **fact_sale** table, drag the **CityKey** field and drop it on the **CityKey** field in the **dimension_city** table to create a relationship. The **Create Relationship** dialog box appears.

    ![](media/Lab01(\#).png)

2.  In the **Create Relationship** dialog box:
    1.  **Table 1** is populated with **fact_sale** and the column of **CityKey**.
    2.  **Table 2** is populated with **dimension_city** and the column of **CityKey**.
    3.  Cardinality: **Many to one (\*:1)**
    4.  Cross filter direction: **Single**
    5.  Leave the box next to **Make this relationship active** selected.
    6.  Select the box next to **Assume referential integrity.**
    7.  Select **Confirm.**

        ![](media/Lab01(\#).png)

        ![A screenshot of a computer Description automatically generated](media/Lab01(\#).png)

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
