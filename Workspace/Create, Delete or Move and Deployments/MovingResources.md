# Azure Synapse Analytics Workspace / Create, Delete or Move and Deployments / Moving resources

## Learn about moving Azure Synapse Analytics workspace resources



>**Note**: After creating your Azure Synapse workspace, you will not be able to move the workspace to another Azure Active Directory tenant. If you do so through subscription migration or other actions, you may lose access to the artifacts within the workspace.


:::Section Move Azure resources across resource groups, subscriptions, or regions:::

Azure resources can be moved to a new resource group or subscription, or across regions.
- You can move Azure resources to either another Azure subscription or another resource group under the same subscription. You can use the Azure portal, Azure PowerShell, Azure CLI, or the REST API to move resources. To learn more, see [Move resources to a new resource group or subscription](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resources-overview)
- In [this](https://docs.microsoft.com/azure/resource-mover/move-region-within-resource-group?toc=%2Fazure%2Fazure-resource-manager%2Fmanagement%2Ftoc.json) article, learn how to move resources in a specific resource group to a different Azure region. In the resource group, you select the resources you want to move. Then, you move them using [Azure Resource Mover](https://docs.microsoft.com/azure/resource-mover/overview).


:::Section Unable to move Synapse resources to different Subscription:::

Moving operation is not supported in Azure synapse workspace.

**Dedicated SQL Pool:**
- Move operation is possible with Dedicated SQL Pool inside the same tenant with different subscription.
  - [Github](https://github.com/MicrosoftDocs/azure-docs/blob/main/articles/synapse-analytics/sql-data-warehouse/backup-and-restore.md) blog.
  - [Move across regions\Subscriptions.](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/how-to-move-your-azure-data-warehouse-to-a-new-region-and-or/ba-p/682907)
- [How to Move](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription?toc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Ftoc.json&bc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fbreadcrumb%2Ftoc.json#use-the-portal) from one subscription to another in same tenant.

**Workspace SQL pool:**
- Move operation is [not supported](https://docs.microsoft.com/azure/azure-resource-manager/management/move-support-resources#microsoftsynapse) inside the workspace for SQL pools.


:::Section Resources:::
- Move operation [support](https://docs.microsoft.com/azure/azure-resource-manager/management/move-support-resources#microsoftsynapse) for resources


- List [Azure deny assignments](https://docs.microsoft.com/azure/role-based-access-control/deny-assignments-powershell) using Azure PowerShell.

- [Understand Azure deny assignments](https://docs.microsoft.com/azure/role-based-access-control/deny-assignments), similar to a role assignment, a deny assignment attaches a set of deny actions to a user, group, or service principal at a particular scope for the purpose of denying access. Deny assignments block users from performing specific Azure resource actions even if a role assignment grants them access.

:::Section Relevant results from the web:::
<azureKB>
    <client>Portal</client>
</azureKB>