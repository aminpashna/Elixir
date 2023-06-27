# Workspace is in Failed state

## What is Azure Synapse Analytics?

**Azure Synapse** is an enterprise analytics service that accelerates time to insight across data warehouses and big data systems. Azure Synapse brings together the best of **SQL** technologies used in enterprise data warehousing, **Spark** technologies used for big data, **Data Explorer** for log and time series analytics, **Pipelines** for data integration and ETL/ELT, and deep integration with other Azure services such as **Power BI**, **CosmosDB**, and **AzureML**.

![image_workspace](https://learn.microsoft.com/azure/synapse-analytics/media/overview-what-is/synapse-architecture.png)


### **Azure Synapse Analytics terminology**

A Synapse workspace is a securable collaboration boundary for doing cloud-based enterprise analytics in Azure. A workspace is deployed in a specific region and has an associated ADLS Gen2 account and file system (for storing temporary data). A workspace is under a resource group.

A workspace allows you to perform analytics with SQL and Apache spark. Resources available for SQL and Spark analytics are organized into SQL and Spark pools.

### **Troubleshoot Workspace in Failed state**

| Symptom | Cause | Resolution |
|-|-|-|
|During a deployment, you might receive a ```RequestDisallowedByPolicy``` error that prevents you from creating a resource. Azure CLI, Azure PowerShell, and the Azure portal's activity log show similar information about the error. The key elements are the error code, policy assignment, and policy definition.|RequestDisallowedByPolicy|The request disallowed by policy error can occur when you deploy resources with an [Azure Resource Manager template (ARM template) or Bicep file](https://learn.microsoft.com/azure/azure-resource-manager/troubleshooting/error-policy-requestdisallowedbypolicy?tabs=azure-cli)|
|Workspace is in Failed state|ClientIpAddressNotAuthorized|The error occurs when the IP address of the client attempting to access the workspace is not authorized. This can happen if the IP address is not included in the [firewall](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#configure-ip-firewall-rules-using-the-azure-portal) settings or [virtual network service endpoint configurations](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet)|
|Workspace is in Failed state|PublicNetworkAccessDenied|[Azure Synapse Analytics connectivity settings](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/connectivity-settings)|




### **Resources**

- [Azure Synapse Analytics terminology](https://learn.microsoft.com/azure/synapse-analytics/overview-terminology)
- [What is Azure Synapse Analytics?](https://learn.microsoft.com/azure/synapse-analytics/overview-what-is)


### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>