# Azure Synapse Analytics Workspace / Create, Delete or Move and Deployments / Create or delete Workspace

## Create or delete a Synapse Analytics workspace

>**Note**: Review the [list of known issues](https://learn.microsoft.com/azure/synapse-analytics/known-issues) currently active or recently resolved in Azure Synapse Analytics.

Use the following guidance to learn how to create, delete, and recover a Synapse Analytics workspace, and more.

### Before you begin

Make sure Microsoft.Synapse and Microsoft.Sql resource providers are registered in your subscription. See [Azure resource providers and types](https://docs.microsoft.com/azure/azure-resource-manager/management/resource-providers-and-types). 

When deploying resources, frequently retrieve information about the resource providers and types. For example, to store keys and secrets, engage the Microsoft.KeyVault resource provider who has the vault resource type to create the key vault.

### **Troubleshooting**

| Symptom | Cause | Resolution |
|-|-|-|
|'status': 'Failed','error': 'code': '**ValidationFailed**','message': 'Workspace request validation failed, check error details for more information', 'details':  'code': '**SqlServerRegionDoesNotAllowProvisioning**', 'message': 'Location '{Location}' is not accepting creation of new Windows Azure SQL Database servers for the subscription '{subId}' at this time.'|It means SQL Server is not registered as an allowed resource provider on your Azure Subscription.|[Register resource provider](https://learn.microsoft.com/azure/azure-resource-manager/management/resource-providers-and-types#register-resource-provider-1)|
|ReachedPerSubscriptionWorkspaceLimit, **message:** Reached the maximum number of Synapse workspaces allowed for this subscription.|[Azure Synapse limits for workspaces](https://learn.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-synapse-limits-for-workspaces)|[Request quota increases and get support for Azure Synapse Analytics](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-get-started-create-support-ticket)|
|DeploymentFailed, **message:**At least one resource deployment operation failed. Please list deployment operations for details.|Request quota increases|[Request quota increases and get support for Azure Synapse Analytics](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-get-started-create-support-ticket)|
|ValidationFailed, **message:** Workspace request validation failed, check error details for more information, **Details:** Cannot create logical server in subscription *** because the quota limit has been reached.|Request quota increases|[Request quota increases and get support for Azure Synapse Analytics](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-get-started-create-support-ticket)|


### Create a workspace

Use the following information to create an Azure Synapse workspace by using the Azure portal. 

See [Quickstart: Create a Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/quickstart-create-workspace).

### Lock resources

Administrators can lock a subscription, resource group, or resource to prevent other users in an organization from accidentally deleting or modifying resources. The lock overrides any permissions a user has. See [Lock resources to prevent unexpected changes](https://docs.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json).

### Delete and recover an Azure Log Analytics workspace

If you plan to delete a Log Analytics workspace, we recommend the soft-delete operation. By using this operation, the workspace, its data, and connected agents can be recovered within 14 days. The deletion can be accidental or intentional. After the soft-delete period, the workspace and its data are not recoverable and are queued for purge within 30 days.

The Contributor role can perform the operation. Permissions are for a workspace subscription and resource group. Workspace recovery is re-creating the Log Analytics workspace with deleted workspace details:

- Subscription ID
- Resource group name
- Workspace name
- Region

**Note**: To override soft-delete and permanently delete your workspace, see [Permanent workspace delete](https://docs.microsoft.com/azure/azure-monitor/logs/delete-workspace#permanent-workspace-delete).

Learn more: [Delete and recover Azure Log Analytics workspace](https://docs.microsoft.com/azure/azure-monitor/logs/delete-workspace) 

### Move workspaces

After Microsoft Sentinel is deployed on a workspace, moving the workspace to another resource group or subscription isn't supported.

- If you moved the workspace, disable active rules under Analytics. 
- After five minutes, reenable them. 
  - This is not supported and entails risk.
- It can take Azure Resource Manager a few hours to complete. 
  - Solutions may be unresponsive during the operation.

### Common errors and solutions

**Error code 405**

The delete command is not supported for the Security Alert Policy API. See [Sql Pool Security Alert Policies](https://docs.microsoft.com/rest/api/synapse/sql-pool-security-alert-policies?source=docs).

**Workspace quota limit**

* [Workspace quota limit - Unable to create Synapse workspace due to subscription limit](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/workspace-quota-limit-unable-to-create-synapse-workspace-due-to/ba-p/2104173)
* [Azure Synapse Analytics limits](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-synapse-analytics-limits) 

### Resources

- [Quickstart: Create a Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/quickstart-create-workspace)
- [Lock resources to prevent unexpected changes](https://docs.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json)
- [Move resources to a new resource group or subscription](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription)
- [Move a Log Analytics workspace to another region by using the Azure portal](https://docs.microsoft.com/azure/azure-monitor/logs/move-workspace-region)

### Relevant results from the web

<azureKB>
    <client>Portal</client>
</azureKB>