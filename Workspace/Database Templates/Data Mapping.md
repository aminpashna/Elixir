# Azure Synapse Analytics Workspace / Database Templates (Preview) / Data mapping

## Resolve issues using data mapper to generate dataflows for lake databases

Use the following guidance to resolve issues when using data mapper to generate  data flows for lake databases, as well as to learn more about Azure Synapse database templates and lake databases in general.



### What is the Map data tool?

The Map Data tool is a guided process to help users create ETL mappings and mapping data flows from their source data to Synapse lake database tables without writing code. This process starts with the user choosing the destination tables in Synapse lake databases and then mapping their source data into these tables.

For more information on Synapse lake databases, see [Overview of Azure Synapse database templates - Azure Synapse Analytics | Microsoft Docs](https://learn.microsoft.com/azure/synapse-analytics/database-designer/overview-database-templates)

Map Data provides for a guided experience where the user can generate a mapping data flow without having to start with a blank canvas. Then you can quickly generate a scalable mapping data flow runnable in Synapse pipelines.



### Create data mapping

Configure your data mapping with the source type you selected.
![newdatamapping1](https://learn.microsoft.com/azure/synapse-analytics/database-designer/media/overview-map-data/map-data-file-selection.png)

> Note\
 You can choose a folder or a single file. If you choose a folder you will be able to map multiple files to your lake database tables. If you choose a folder you are also prompted after selecting continue to include only specific files, if desired.

Name your data mapping and select the Synapse lake database destination.
![newdatamapping2](https://learn.microsoft.com/azure/synapse-analytics/database-designer/media/overview-map-data/destination-map-data.png)


### **Resources**

- [What are Azure Synapse database templates?](https://docs.microsoft.com/azure/synapse-analytics/database-designer/overview-database-templates)
- [Lake database templates](https://docs.microsoft.com/azure/synapse-analytics/database-designer/concepts-database-templates)
- [Lake database](https://docs.microsoft.com/azure/synapse-analytics/database-designer/concepts-lake-database)
- [Map Data in Azure Synapse Analytics](https://learn.microsoft.com/azure/synapse-analytics/database-designer/overview-map-data)


**How-to guides**

- [Quickstart: Create a new Lake database leveraging database templates](https://docs.microsoft.com/azure/synapse-analytics/database-designer/quick-start-create-lake-database)
- [How-to: Create an empty lake database](https://docs.microsoft.com/azure/synapse-analytics/database-designer/create-empty-lake-database)
- [How-to: Create a lake database from database templates](https://docs.microsoft.com/azure/synapse-analytics/database-designer/create-lake-database-from-lake-database-templates)
- [How-to: Modify a lake database](https://docs.microsoft.com/azure/synapse-analytics/database-designer/modify-lake-database)



### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>

