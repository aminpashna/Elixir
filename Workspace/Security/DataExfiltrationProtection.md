# Azure Synapse Analytics Workspace / Security / Data Exfiltration Protection

## Data Exfiltration Protection

Azure Synapse Analytics workspaces support enabling data exfiltration protection for workspaces. With exfiltration protection, you can guard against malicious insiders accessing your Azure resources and exfiltrating sensitive data to locations outside of your organization’s scope. At the time of workspace creation, you can choose to configure the workspace with a [managed virtual network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet) and additional protection against data exfiltration. When a workspace is created with a managed virtual network, Data integration and Spark resources are deployed in the managed virtual network. The workspace’s dedicated SQL pools and serverless SQL pools have multi-tenant capabilities and as such, need to exist outside the managed virtual network. For workspaces with data exfiltration protection, resources within the managed virtual network always communicate over [managed private endpoints](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints) and the Synapse SQL resources can only connect to authorized Azure resources (targets of approved managed private endpoint connections from the workspace).

:::Section Sample workspace with data exfiltration protection enabled:::

Let us use an example to illustrate data exfiltration protection for Synapse workspaces. Contoso has Azure resources in Tenant A and Tenant B and there is a need for these resources to connect securely. A Synapse workspace has been created in Tenant A with Tenant B added as an approved Azure AD tenant. The diagram shows private endpoint connections to Azure Storage accounts in Tenant A and Tenant B that have been approved by the Storage account owners. The diagram also shows blocked private endpoint creation. The creation of this private endpoint was blocked as it targeted an Azure Storage account in the Fabrikam Azure AD tenant, which is not an approved Azure AD tenant for Contoso’s workspace.

![sample](https://docs.microsoft.com/azure/synapse-analytics/security/media/workspace-data-exfiltration-protection/workspace-data-exfiltration-protection-diagram.png)

>**Important**
Resources in tenants other than the workspace's tenant must not have blocking firewall rules in place for the SQL pools to connect to them. Resources within the workspace’s managed virtual network, such as Spark clusters, can connect over managed private links to firewall-protected resources.

:::Section Prevent Data Exfiltration in Azure SQL Managed Instance:::

Data exfiltration is a technique that is also sometimes described as data theft or data extrusion, that describes the unauthorized extraction of data from the original source. This unauthorized extraction can be executed either manually or automatically by the malicious attacker.

As part of your Network Infrastructure, you might have tightened your security to make sure you have all the bells and whistles to lock down your Azure SQL Managed Instance to be accessed only by your application and not exposed to the Internet or any other traffic. However, this doesn’t stop a malicious admin from taking a backup or creating a linked server to another resource outside your enterprise subscription for extracting the data. This action would be data exfiltration. In a typical on-premises infrastructure, you can lock down network access completely to make sure that the data never leaves your network. However, in a cloud setup, there is a possibility that someone with elevated privileges can export data or perform some other malicious activity targeting their own resources outside your organization, compromising your enterprise data. Hence, it is very important to understand the different data exfiltration scenarios and make sure that you are taking the right steps to monitor for and prevent such activities.

[Here](https://techcommunity.microsoft.com/t5/azure-sql-blog/prevent-data-exfiltration-in-azure-sql-managed-instance/ba-p/3590381) are of the different exfiltration scenarios and the associated preventive actions and controls.


:::Section Resources:::

- [Data exfiltration protection for Azure Synapse Analytics workspaces](https://docs.microsoft.com/azure/synapse-analytics/security/workspace-data-exfiltration-protection)

- [Security baseline](https://docs.microsoft.com/azure/synapse-analytics/security-baseline)

:::Section Here are some relevant results from the web:::

<azureKB>
    <client>Portal</client>
</azureKB>