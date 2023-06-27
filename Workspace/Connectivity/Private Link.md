# Azure Synapse Analytics Workspace / Connectivity / Private Link

## Learn to manage Azure Private Link

Azure Private Link allows you to connect to various platform-as-a-service (PaaS) services in Azure by using a private endpoint. A private endpoint is a private IP address within a specific virtual network and subnet.

For a list of PaaS services that support Private Link functionality, see the [Private Link documentation](https://docs.microsoft.com/azure/private-link/). 

You can [set up a private link](https://docs.microsoft.com/azure/sql-database/sql-database-private-endpoint-overview?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json#how-to-set-up-private-link-for-azure-sql-database) for your SQL pool. Connections to private endpoints only support proxy as the connection policy.

For more information about managing Private Link, scan the following headings and select one or more to learn more about that topic.


:::Section Troubleshooting:::

Review the following troubleshooting guidance to help resolve your issue.

| Symptom | Cause | Resolution |
|-|-|-|
|Failed to load one or more resources due to forbidden issue, error code 403.|Public network access is disabled. |[Azure Synapse Analytics connectivity settings](https://learn.microsoft.com/azure/synapse-analytics/security/connectivity-settings)|
| Failed provisioning of managed private endpoint to Cosmos DB. | Not registered in Microsoft.Network in resource provider. | [Register resource provider](https://docs.microsoft.com/azure/azure-resource-manager/management/resource-providers-and-types#register-resource-provider). |
| Synapse Private Link Hub doesn't work on-premises. | Make sure that the firewall on your network and local computer allows outgoing communication on TCP ports 80, 443, and 1443. These ports are used by Synapse Studio. | [Configure IP firewall rules](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall).|
PrivateLink named: '' within Azure Synapse workspace: '' failed to provision and doesn't function causing issues with specific access patterns to the storage (referenced in another support request ID). |The MPE is in a failed state and is not able to delete.| <ul><li>Check if there is a lock on any [resource group](https://learn.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json#configure-locks).</li><li>Check if there is a lock on the [storage account level](https://learn.microsoft.com/azure/storage/common/lock-account-resource?tabs=portal).</li><li>Delete/re-create failed managed private endpoint.</li></ul>
403 error when using private endpoint for Azure Synapse.|User credential doesn’t have synapse role-based access control (RBAC) permission.|<ul><li>[Synapse RBAC Roles](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-synapse-rbac-roles).</li><li>[Query fails because file can't be opened](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql/resources-self-help-sql-on-demand?tabs=x80070002#query-fails-because-file-cant-be-opened).</li></ul>
ClientIpAddressNotAuthorized.|Allowlisting IP address on the Synapse resource.|[Create and manage IP firewall rules](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#create-and-manage-ip-firewall-rules).
Failed to load one or more resources due to *unknown* error.|The workspace doesn't have an associated managed virtual network. A managed virtual network can only be assigned during workspace creation.|[Create an Azure Synapse workspace with a managed workspace virtual network](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet).
Unable to query Synapse from CosmosDB in the same virtual network.|Private endpoint(s)/managed private endpoint(s) misconfiguration.|[Connect to your Azure Synapse workspace using private links](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links).
Issues with web access over site-to-site VPN.|Private connection is not properly configured.|[Connect to workspace resources from a restricted network](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network).|
|Connection issue to reach dedicated SQL pool: an instance-specific error occurred while establishing a connection to SQL Server. Connection was denied since *Deny Public Network Access* is set to *Yes*.|Private endpoint to SQL dedicated pool not created. Two private endpoints are created against dev.|Create a new private endpoint to the SQL dedicated pool.|
|"Azure Data Lake Storage Gen2 operation failed for: An error occurred while sending the request. Account: 'AccountName'. An error occurred while sending the request. The remote name could not be resolved: 'AccountName.dfs.core.windows.net' Activity ID: 'id'."|DNS can't resolve the storage account private endpoint IP address.|Drop and re-create the storage account managed private endpoint.|


:::Section Private endpoints:::

Private endpoints allow you to access Azure PaaS services, like Azure Storage, Azure SQL Database, and Azure Synapse, over a private network connection. Private endpoints provide private connectivity from your on-premises or virtual network to Azure PaaS services over a Microsoft-managed network.

The traffic between your virtual network and the service travels the Microsoft backbone network. Exposing your service to the public internet is no longer necessary.

In the image below, we can see how the connection using a private endpoint works. Synapse clients, by default, will try to go to the public gateway IPs, see [Azure Synapse Analytics connectivity architecture](https://learn.microsoft.com/azure/azure-sql/database/connectivity-architecture?view=azuresql). By using private endpoints, you can close the public path so users can only connect from the private endpoint.

![Diagram of connectivity architecture](https://learn.microsoft.com/azure/azure-sql/database/media/private-endpoint/pe-connect-overview.png?view=azuresql)

When working with Synapse, there's not just one endpoint (SQL)—there are multiple endpoints (SQL, serverless, development, web, data lake).

The public network access feature is only available to Azure Synapse workspaces associated with Azure Synapse Analytics Managed Virtual Network, so you won't see the option to close the public endpoint in the portal. So if you have an environment without a managed virtual network, and you want to close the public endpoint, don't open it to any public IPs.

For more information, see:
- [Azure Synapse Analytics IP firewall rules](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall)
- [Synapse Connectivity Series Part #2 - Inbound Synapse Private Endpoints](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/synapse-connectivity-series-part-2-inbound-synapse-private/ba-p/3705160)


:::Section Connect to workspace resources from a restricted network:::

Suppose you're an IT administrator who is managing your organization's restricted network, and you want to enable the network connection between Azure Synapse Analytics Studio and a workstation within this restricted network.

**Prerequisites**

- Azure subscription
- Azure Synapse Analytics workspace
- A restricted network

**Step 1**: Add network outbound security rules to the restricted network.<br>
**Step 2**: Create private link hubs.<br>
**Step 3**: Create a private endpoint for your Synapse Studio.<br>
**Step 4**: Create private endpoints for your workspace resource.<br>
**Step 5**: Create private endpoints for workspace linked storage.

Learn more about [Connecting to workspace resources from a restricted network](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network).


:::Section Application and service principal objects in Azure Active Directory:::

To learn about application registration, application objects, and service principals in Azure Active Directory (Azure AD), see [Application and service principal objects in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals). The article describes what they are, how they're used, and how they relate to each other. A multitenant example scenario is also presented to illustrate the relationship between an application's application object and corresponding service principal objects.


:::Section Enable Azure Synapse Link for Azure Cosmos DB accounts:::

1. Sign in to the [Azure portal](https://ms.portal.azure.com/#home).
2. [Create a new Azure account](https://learn.microsoft.com/azure/cosmos-db/nosql/quickstart-dotnet?tabs=azure-portal%2Cwindows%2Cpasswordless%2Csign-in-azure-cli#create-account), or select an existing Azure Cosmos DB account.
3. Navigate to your Azure Cosmos DB account and open the Azure Synapse Link under **Integrations** in the left navigation menu.
4. Select **Enable**. This process can take one to five minutes to complete.

![Screenshot of Azure Synapse Link pane in the portal](https://learn.microsoft.com/azure/cosmos-db/media/configure-synapse-link/enable-synapse-link.png)

5. Your account is now enabled to use Synapse Link. Next, see how to create analytical store–enabled containers to automatically start replicating your operational data from the transactional store to the analytical store.

>**Note**: Turning on Synapse Link does not turn on the analytical store automatically. Once you enable Synapse Link on the Cosmos DB account, enable analytical store on containers to start using Synapse Link.

>**Note**: You can also enable Synapse Link for your account using the Power BI and the Synapse Link pane in the **Integrations** section of the left navigation menu.

Enable Synapse Link in your Azure Cosmos DB API for NoSQL or MongoDB account using [Azure CLI](https://learn.microsoft.com/azure/cosmos-db/configure-synapse-link#command-line-tools) or [PowerShell](https://learn.microsoft.com/azure/cosmos-db/configure-synapse-link#powershell).

:::Section Establish a connection between Azure Synapse Analytics and Azure SQL Managed Instance using a private endpoint:::

Possible solutions:

- Use the Azure integration runtime with the Private Link service.
  - [How to access a SQL Managed Instance from an Azure Data Factory–managed virtual network using a private endpoint](https://docs.microsoft.com/azure/data-factory/tutorial-managed-virtual-network-sql-managed-instance).
  - [Copy and transform data in Azure SQL Managed Instance using Azure Data Factory or Synapse Analytics](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-managed-instance?tabs=data-factory).

- Using self-hosted integration runtime
  - Create a new subnet in the same virtual network where the SQL Server Managed Instance is deployed.
  - Create a virtual machine and add it to the created subnet. (This is for installing a self-hosted integration runtime.)
  - Open the Azure Synapse Studio from which the linked service needs to be created. Create a new self-hosted integration runtime.
  - Get the link to download the self-hosted integration runtime and download the newest self-hosted integration runtime to the virtual machine that was created earlier.
  - Install the self-hosted integration runtime on the virtual machine and register it with Synapse Studio by using the key that was generated while adding the new self-hosted integration runtime in Synapse Studio.
  - Sign in to the virtual machine again and open the self-hosted integration runtime configuration manager. In the diagnostics, enter the details of the SQL Server Managed Instance and check connectivity.
  - Create a new linked service to SQL Server Managed Instance by using the newly created self-hosted integration runtime.
  - In **Account selection method**, select **Enter manually** and enter the fully qualified domain name of the managed instance.
  - Enter the database name, username, and password (SQL authentication), and test the connection.


:::Section Cross-tenant data ingestion with Private Link:::

While general guidance suggests operating under the same tenant, there are instances where it’s not possible. See [this blog](https://cloudblogs.microsoft.com/industry-blog/en-gb/technetuk/2022/01/14/cross-tenant-data-ingestion-without-whitelisting-ip-addresses-with-azure-synapse-pipelines-azure-data-factory/) for guidance in situations where organizations can't operate under one tenant due to specific constraints or requirements.


:::Section Frequently asked questions (FAQ):::

**Why do I need to allowlist my VNet on my data lake where my Synapse Private Link endpoint resides?**

- When you use managed private endpoints, traffic between your Azure Synapse workspace and other Azure resources traverses entirely over the Microsoft backbone network.
- Managed private endpoints protect against data exfiltration. A managed private endpoint uses private IP address from your managed virtual network to effectively bring the Azure service that your Azure Synapse workspace is communicating into your virtual network. Managed private endpoints are mapped to a specific resource in Azure and not the entire service. Customers can limit connectivity to a specific resource approved by their organization. *Protect against data exfiltration* means that the managed private endpoint is only in charge of the outbound traffic (from workspace to outside, for example, storage account, etc.). So, you'll need a managed private endpoint to connect to the storage account for sending requests from the Synapse workspace to the storage account. When the storage account receives the requests and sends back responses, your Synapse workspace is within a virtual network that controls all the inbound traffic. That's why you need to set this virtual network as an allowlist on the storage account side. The purpose of the managed private endpoint is to make sure your outbound traffic can be sent to the storage account successfully. Meanwhile, you must set up the allowlist for the virtual network on the storage side so that the response can be received.

**How do I set up Synapse for PowerBI?**

- Power BI requires a public endpoint to be enabled to connect to a Synapse workspace. See:
  - [Quickstart: Linking a Power BI workspace to a Synapse workspace](https://learn.microsoft.com/azure/synapse-analytics/quickstart-power-bi)
  - [Use virtual network data gateway and data sources in Power BI](https://learn.microsoft.com/data-integration/vnet/use-data-gateways-sources-power-bi?source=recommendations)

**When trying to create the private endpoint, we can't see all the options under target sub-resources.**

- When creating a private endpoint, you may not be able to see all the options under target sub-resources due to access control settings. If you need to access certain target sub-resources, you may need to adjust the access control settings to allow access.

**ERROR: "The public network interface on this Workspace is not accessible. To connect to this Workspace, use the Private Endpoint from inside your virtual network or enable public network access for this workspace."**

- This behavior is by design. After you've denied public network access to your Synapse workspace, you need to create a few corresponding private endpoints so you can connect to your workspace through private connections.

- To resolve the issue:
  - Create a private endpoint for your dedicated SQL pool.
  - Create a private endpoint for your serverless SQL pool.
  - Create a private endpoint for your development endpoint.
  - Create a Synapse Private Link hub.
  - Create a private endpoint for the Private Link hub.
  - Create entries for those private endpoints and private IP mapping in your Windows hosts file.
  - Create a point-to-site VPN to establish private connectivity from your client machine to Azure virtual network and private endpoints in it.
  - Generate a self-signed certificate.
  - Create peering between the VNet contains private endpoints and VPN Gateway.
  - Install the VPN client in your client machine.

:::Section Resources:::

- [How to link a Power BI workspace to a Synapse workspace](https://learn.microsoft.com/en-us/azure/synapse-analytics/quickstart-power-bi)
- [How to set up access control for your Azure Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-set-up-access-control)
- [Test connectivity to SQL Database from an Azure virtual machine in same virtual network](https://docs.microsoft.com/azure/sql-database/sql-database-private-endpoint-overview?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json#test-connectivity-to-sql-database-from-an-azure-vm-in-same-virtual-network-vnet)
- [On-premises connectivity over private peering](https://docs.microsoft.com/azure/sql-database/sql-database-private-endpoint-overview?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json#on-premises-connectivity-over-private-peering)
- [Connecting from an Azure Synapse Analytics&ndash;dedicated SQL pool to Azure Storage using PolyBase](https://docs.microsoft.com/azure/sql-database/sql-database-private-endpoint-overview?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json#connecting-from-an-azure-sql-data-warehouse-to-azure-storage-using-polybase)


### Relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>