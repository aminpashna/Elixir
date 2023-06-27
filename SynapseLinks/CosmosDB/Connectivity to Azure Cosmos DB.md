# Azure Synapse Analytics Synapse Link / Cosmos DB / Connectivity to Azure Cosmos DB

## Resolve Azure Cosmos DB connectivity issues

Most users are able to resolve their Azure Synapse Link for Azure Cosmos DB issues using the steps below.  

### **Configure Azure Private Link for Azure Cosmos DB analytical store**

[Enable a private endpoint for the analytical store](https://learn.microsoft.com/azure/cosmos-db/analytical-store-private-endpoints#enable-a-private-endpoint-for-the-analytical-store)







### **Recommended Steps**  

#### **Supported APIs**  

Today, Azure Synapse Link for Azure Cosmos DB is supported for SQL API and Azure Cosmos DB API for MongoDB. It is not supported for Gremlin API and Table API. Support for Cassandra API is in private preview: for more information, contact the Azure Synapse Link team at cosmosdbsynapselink@microsoft.com.  

#### **Workspace with Managed Virtual Network**   

Azure Synapse Link for Azure Cosmos DB is not supported in workspace with Managed Vnet.   

We recommend creating a workspace without Managed Vnet to access Azure Synapse Link.  

#### **Cannot access Cosmos DB analytical store with Synapse SQL dedicated pool**  

Only Synapse SQL serverless pool and Synapse Spark pool are currently supported. Synapse SQL dedicated pool is not supported.  

### **Recommended Documents**  

* [Azure Synapse Link limits](https://docs.microsoft.com/azure/synapse-analytics/synapse-link/concept-synapse-link-cosmos-db-support)
 



### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>