# Azure Synapse Analytics Workspace / Connectivity / Private Link Hubs

## Manage Private Link Hubs

You can securely connect to Azure Synapse Studio from your Azure virtual network using private links. Azure Synapse Analytics private link hubs are Azure resources which act as connectors between your secured network and the Synapse Studio web experience.

There are two steps to connect to Synapse Studio using private links.
- **First**, you must create a private link hubs resource.
- **Second**, you must create a private endpoint from your Azure virtual network to this private link hub.

You can then use private endpoints to securely communicate with Synapse Studio. You must integrate the private endpoints with your DNS solution, either your on-premises solution or Azure Private DNS.

 > Note:\
 Private link hubs are intended for securely loading the static content Synapse Studio over private links. You must create separate, private endpoints to the resources you wish to connect to within the workspace, such as provisioned/dedicated SQL pools, or Spark pools.


### Troubleshooting

Following(s) may help you to resolve the issue.

| Symptom | Cause | Resolution |
| - | - | - |
| Creating the SQL endpoint for Dev environment |  | To have different Managed Private Points for Development and Production it’s recommended to create another Synapse Workspace, and then you will be able to set up different access level in each environment. |




### Resources

- [Synapse workspace Managed virtual network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet)
- [Synapse workspace Managed private endpoints](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints)
- [Connect to Azure Synapse Studio using Azure Private Link Hubs](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-private-link-hubs#azure-private-link-hubs)
 


### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>