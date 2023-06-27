# Azure Synapse Analytics Workspace / Synapse Studio / SQL Script authoring

## Troubleshoot Synapse Studio SQL scripts

Synapse Studio provides a SQL script web interface for you to author SQL queries.

### **Begin authoring in SQL script**

There are several ways to start the authoring experience in SQL script. You can create a new SQL script through one of the following methods.

 - From the Develop menu, select the "+" icon and choose **SQL script**.
 - From the Actions menu, choose **New SQL script**.
 - Choose **Import** from the **Actions** menu under Develop SQL scripts. Select an existing SQL script from your local storage.
![image_1](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-3-actions.png)

### **Create your SQL script**

- Choose a name for your SQL script by selecting the **Property** button and replacing the default name assigned to the SQL script.
![image_2](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-rename.png)

- Choose the specific dedicated SQL pool or serverless SQL pool from the **Connect to** drop-down menu. Or if necessary, choose the database from **Use database**.
![image_3](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-choose-pool.png)

 - Start authoring your SQL script using the intellisense feature.

### **Run your SQL script**

Select the **Run** button to execute your SQL script. The results are displayed by default in a table.
![image_3](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-results-table.png)

### **Export your results**

You can export the results to your local storage in different formats (including CSV, Excel, JSON, XML) by selecting "Export results" and choosing the extension.

You can also visualize the SQL script results in a chart by selecting the **Chart** button. Select the "Chart type" and **Category column**. You can export the chart into a picture by selecting **Save as image**.
![image_4](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-results-chart.png)


### **Explore data from a Parquet file**

You can explore Parquet files in a storage account using SQL script to preview the file contents.
![image_5](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-script-sqlod-parquet.png)



### **SQL Tables, external tables, views**

By selecting the **Actions** menu under data, you can select several actions such as:
- New SQL script
- Select TOP 1000 rows
- CREATE
- DROP and CREATE

Explore the available gesture by right-clicking the nodes of SQL databases.
![image_6](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-script-database.png)


### **Create folders and move SQL scripts into a folder**

From the Actions menu under Develop SQL scripts Choose "New folder" from the "Actions" menu under Develop SQL scripts. And type in the name of the new folder in the pop-up window.
![image_7](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-create-folder.png)

To move a SQL script into a folder, you can select the sql script and choose "Move To" from the Actions menu. Then find the destination folder in the new window and move the sql script into selected folder.You can also quickly drag the sql script and drop it into a folder.
![image_8](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/media/author-sql-script/new-sql-script-move-folder.png)



### **Recommended Steps**

- If you need to run queries that return large datasets, it's not recommended to use Synapse Studio. Instead, use other tools like SQL Server Management Studio or Azure Data Studio.

- [Synapse Studio troubleshooting](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio).

- [Troubleshoot Synapse Studio connectivity with PowerShell](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio-powershell).

- [Troubleshoot connectivity between Azure Synapse Analytics Synapse Studio and storage](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio-and-storage-connectivity).

- Submit feedback or new ideas for [Synapse workspace SQL Scripts](https://feedback.azure.com/forums/307516-azure-synapse-analytics/category/387862-workspace-sql-scripts).

### **Resources**

- [Author and Run SQL Scripts](https://docs.microsoft.com/azure/synapse-analytics/sql/author-sql-script) using Synapse Studio
- [Analyze and explore data with T-SQL in Azure Synapse Analytics](https://techcommunity.microsoft.com/t5/azure-synapse-analytics/analyze-and-explore-data-with-t-sql-in-azure-synapse-analytics/ba-p/1986861)



### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>