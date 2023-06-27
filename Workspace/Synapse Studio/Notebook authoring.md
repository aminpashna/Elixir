# Azure Synapse Analytics Workspace / Synapse Studio / Notebook authoring

## Synapse Studio Notebooks

A [Synapse Studio notebook](https://learn.microsoft.com/azure/synapse-analytics/spark/apache-spark-notebook-concept) is a web interface for you to create files that contain live code, visualizations, and narrative text. Notebooks are a good place to validate ideas and use quick experiments to get insights from your data.


| Symptom | Cause | Resolution |
|-|-|-|
|Error 401, Operation failed. Server failed to authenticate the request. Refer to the information in the www-authenticate header|ADLSGen2 access issue for the user|To enable other users to use the storage account after you create your workspace, you will have to perform below tasks:<ul><li>Assign other users to the Contributor role on workspace</li><li>Assign other users to a Workspace, SQL, or Spark admin role using Synapse Studio</li><li>Assign yourself and other users to the Storage Blob Data Contributor role on the storage account</li></ul>|
|Not able to run a query on a connected SQL server from synapse notebook|By design|It's not possible to perform stored procedure functions when you connect SQL database to Synapse using Linked Service. Use JDBC for connection to perform desired operations|
|Cannot open database '' requested by the login. The login failed|The database goes into inaccessible state when it cannot reach the key vault, or they encryption key for TDE is not found on the key vault.This is by design, and as a consequence, it is not possible to connect to the database. The reason is that without being able to access the key, the data cannot be decrypted, and hence SQL cannot open the database. When the AKV key is moved or transferred between subscriptions (during the period of transition), SQL is unable to access the key. Hence the database enters the inaccessible state. If key is reinstated within 48 hours, then the database should self-heal. Otherwise, user action is required to bring database back online|No action needed|





### Recommended Steps

- Review [Apache Spark Notebooks](https://docs.microsoft.com/azure/synapse-analytics/sql/author-sql-script).

- You can reference data across languages [using temp tables](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#use-temp-tables-to-reference-data-across-languages).

- Notebooks are integrated with the Monaco editor to bring IDE-style [IntelliSense](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#ide-style-intellisense) to the cell editor.

- You can visualize data in a notebook with [```Display()```](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#display) and [```DisplayHTML()```](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#displayhtml)

### Resources

- [Create a notebook](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#create-a-notebook)
- [Run notebooks](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#run-notebooks)
- [Save notebooks](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#save-notebooks)
- [Magic commands](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#magic-commands)
- [Shortcut keys](https://docs.microsoft.com/azure/synapse-analytics/spark/apache-spark-development-using-notebooks#shortcut-keys)



### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>