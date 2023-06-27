# PublicNetworkAccessDenied

## Learn about configuring connectivity and resolving a "PublicNetworkAccessDenied" error

This article will explain connectivity settings in Azure Synapse Analytics, how to configure them where applicable, and how to resolve a "PublicNetworkAccessDenied" error. Scan and select one or more of the following sections for guidance.

:::Section Public network access overview :::

You can use the public network access feature to allow incoming public network connectivity to your Azure Synapse workspace. 

- When public network access is **disabled**, you can connect to your workspace only using [private endpoints](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints). 
- When public network access is **enabled**, you can connect to your workspace also from public networks. You can manage this feature both during and after your workspace creation. 

> [!IMPORTANT]\
> This feature is only available to Azure Synapse workspaces associated with [Azure Synapse Analytics Managed Virtual Network](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/synapse-workspace-managed-vnet). However, you can still open your Synapse workspaces to the public network regardless of its association with managed VNet. 

Selecting the **Disable** option will not apply any firewall rules that you may configure. Additionally, your firewall rules will appear greyed out in the Network setting in Synapse portal. Your firewall configurations will be reapplied when you enable public network access again. 

> [!TIP]\
> When you revert to enable, allow some time before editing the firewall rules.


:::Section Configure public network access when you create your workspace:::

- Select the **Networking** tab when you create your workspace in [Azure portal](https://ms.portal.azure.com/#home).
- Under Managed virtual network, select **Enable** to associate your workspace with managed virtual network and permit public network access. 
![EnablePublicNetworkAccess](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/media/connectivity-settings/create-synapse-workspace-managed-virtual-network-1.png)

- Under **Public network access**, select **Disable** to deny public access to your workspace. Select **Enable** if you want to allow public access to your workspace.
![DisablePublicNetworkAccess](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/media/connectivity-settings/create-synapse-workspace-public-network-access-2.png)
- Complete the rest of the workspace creation flow.

### Configure public network access after you create your workspace

- Select your Synapse workspace in [Azure portal](https://ms.portal.azure.com/#home).
- Select **Networking** from the left navigation.
- Select **Disabled** to deny public access to your workspace. Select **Enabled** if you want to allow public access to your workspace.
![ConfigAfter](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/media/connectivity-settings/synapse-workspace-networking-public-network-access-3.png)

- When disabled, the **Firewall rules** gray out to indicate that firewall rules are not in effect. Firewall rule configurations will be retained. 
![FirewallRules](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/media/connectivity-settings/synapse-workspace-networking-firewall-rules-4.png)
 
- Select **Save** to save the change. A notification will confirm that the network setting was successfully saved.

### Connection policy
The connection policy for Synapse SQL in Azure Synapse Analytics is set to *Default*. You cannot change this in Azure Synapse Analytics. You can learn more about how that affects connections to Synapse SQL in Azure Synapse Analytics [here](https://learn.microsoft.com/azure/azure-sql/database/connectivity-architecture?view=azuresql#connection-policy). 

### Minimal TLS version
The serverless SQL endpoint and development endpoint only accept TLS 1.2 and above.

Starting in December 2021, a requirement for TLS 1.2 has been implemented for workspace-managed dedicated SQL pools in new Synapse workspaces. Login attempts from connections using a TLS version lower than 1.2 will fail. Customers can raise or lower the minimal TLS version using the API, for both new Synapse workspaces or existing workspaces, so users who need to use a lower client version in the workspaces can connect. Customers can also raise the minimum TLS version to meet their security needs. Learn more by reading [minimal TLS REST API](https://learn.microsoft.com/rest/api/synapse/sqlserver/workspace-managed-sql-server-dedicated-sql-minimal-tls-settings/update?tabs=HTTP).


:::Section **PublicNetworkAccessDenied error when trying to open Synapse Studio after enabling Private end points**:::

This error message usually indicates that you are trying to access Azure Synapse Analytics from a network that is not allowed by the private endpoint configuration. To resolve this issue, you can try the following steps:
- Verify that the virtual network associated with the private endpoint is correctly configured to allow traffic to Azure Synapse Analytics.
- Check the network security group rules associated with the subnet that the private endpoint is in. Make sure that traffic is allowed from your IP address to the Azure Synapse Analytics service.
- If you are using a firewall or VPN, make sure that traffic is allowed to the Azure Synapse Analytics service.


:::Section **PublicNetworkAccessDenied** The public network interface on this Workspace is not accessible.:::

This error message indicates that the public network interface for the Azure Synapse workspace is not accessible. This is likely caused by the fact that the workspace has been configured with Managed Virtual Network, which restricts access to the workspace to only private endpoints within the virtual network. Here are some steps you can take to resolve this issue:

- If you want to access the workspace using the public endpoint, you can enable the public network access by going to the Azure portal, navigating to the Synapse workspace, and then selecting **Firewall and virtual networks** under the **Security + networking** section. From there, you can enable the **Allow all connections** option under the **Public endpoint access** section.
- If you want to access the workspace using the private endpoint, make sure that your network is properly configured to route traffic to the private endpoint. This can be done by creating a DNS record that maps the workspace URL to the private IP address of the private endpoint.
- Verify that the virtual network associated with the private endpoint is correctly configured to allow traffic to Azure Synapse Analytics.
- Check the network security group rules associated with the subnet that the private endpoint is in. Make sure that traffic is allowed from your IP address to the Azure Synapse Analytics service.

:::Section Resources:::

- [Azure Synapse Analytics connectivity settings](https://learn.microsoft.com/azure/synapse-analytics/security/connectivity-settings)
- [Disabling Public Network Access in Synapse](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/disabling-public-network-access-in-synapse/ba-p/3692197)
- [Azure Synapse - Disable public network access](https://learn.microsoft.com/answers/questions/664868/azure-synapse-disable-public-network-access)
- [Azure Synapse Analytics IP firewall rules](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/synapse-workspace-ip-firewall)

### Relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>