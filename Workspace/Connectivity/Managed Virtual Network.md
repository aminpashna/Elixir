# Azure Synapse Analytics Workspace / Connectivity / Managed Virtual Network

## Learn about managed virtual networks in Azure Synapse Analytics

A managed virtual network eases network configuration while creating services such as Azure Data Factory, Azure Synapse Analytics, and Microsoft Purview. It builds on private links and private endpoints. Private endpoints enable many Azure services to have a network interface in a customer's virtual network, and each Azure resource gets a private IP address from that virtual network address space. This provides secure access to specific Azure resources over an ExpressRoute/site-to-site VPN and within Azure.

Scan the following headings and select one or more to learn more about that topic.


:::Section Troubleshooting:::

Following(s) may help you to resolve the issue.

| Symptom | Cause | Resolution |
|-|-|-|
|Error message: "To connect to this server, use the Private Endpoint from inside your virtual network"|By Design||



:::Section What is the difference between Private Enpoint and Managed Private Endpoint:::

A **Private Endpoint** is a network interface that uses a private IP address from your virtual network. This network interface connects you privately and securely to a service that's powered by Azure Private Link. By enabling a private endpoint, you're bringing the service into your virtual network.

**Managed Private Endpoints** are private endpoints created in the Data Factory managed virtual network that establishes a private link to Azure resources. Data Factory manages these private endpoints on your behalf.

> **Note:** The resource provider **_Microsoft.Network_** must be registered to your subscription.


:::Section Azure Synapse-managed virtual network overview:::

Following are additional aspects of an Azure Synapse-managed virtual network:

- **Azure Synapse-managed private endpoints.** This manages the private endpoints from an Azure Synapse workspace to various other Azure resources—for example, to Azure Data Lake Storage Gen2, Azure Cosmos DB, or Azure SQL Database. Traffic between an Azure Synapse workspace and Azure resources traverses the Microsoft backbone network over a private link.

- **Managed virtual networks aren't visible to users.** Also, they're managed by an Azure Synapse workspace.

- **Azure Synapse private link hubs.** Azure Synapse provides a studio that's a web UI and can be accessed to create various artifacts, such as notebooks, pipelines, and SQL scripts. Private endpoint connections are added to private link hubs, so the Azure Synapse Studio can be accessed over a private IP address.

- **Private DNS.** An Azure private DNS can manage the DNS name resolution for Azure resources that have private endpoint connections. This is a key aspect for enabling hybrid connections from on-premises.


:::Section How to access on-premises SQL Server from Data Factory Managed VNet using Private Endpoint:::

**Prerequisites**
- Azure subscription
- Virtual Network
- Virtual network to on-premises network
- Data Factory with Managed VNet enabled

**Step 1**: Create subnets for resources\
**Step 2**: Create a standard load balancer\
**Step 3**: Create load balancer resources\
**Step 4**: Create a private link service\
**Step 5**: Create backend servers\
**Step 6**: Creating Forwarding Rule to Endpoint\
**Step 7**: Create a Private Endpoint to Private Link Service\
**Step 8**: Create a linked service and test the connection

Learn more about [How to access on-premises SQL Server from Data Factory Managed VNet using Private Endpoint](https://learn.microsoft.com/azure/data-factory/tutorial-managed-virtual-network-on-premise-sql-server)

:::Section How to create a private endpoint to your Azure Synapse workspace:::

To learn how to create a private endpoint to your Azure Synapse workspace, see [Connect to your Azure Synapse workspace using private links](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links) and [private links and private endpoints](https://docs.microsoft.com/azure/private-link/).

- **Step 1**: Register your network resource provider.
- **Step 2**: Open your Azure Synapse workspace in the Azure portal.<br>

  Under **Security**, select **Private endpoint connection**.

![Example of Synapse workspace page and private endpoint connections option is highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-1.png)

   On the next screen, select **+ Private endpoint**.

![Example of Private endpoint connections pane with Private endpoint highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-1a.png)

- **Step 3**: Select your subscription and region details.<br>

![Required fields are highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-2.png)

- **Step 4**: Select your Azure Synapse workspace details.

![Required fields are highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-3.png)
![Required fields are highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-4.png)
![Example of approved private endpoint connection](https://docs.microsoft.com/azure/synapse-analytics/security/media/how-to-connect-to-workspace-with-private-links/private-endpoint-5.png)

:::Section Relevant Videos:::

### Network isolation with Managed VNets

<video>
   <src>https://www.youtube.com/watch?v=4PJOuhFosLY</src>
   <title>Network Isolation with Managed VNets</title>
</video>

Summary of the video:
- Why network isolation?
- What is Managed VNet?
- How to create a Managed VNet?
- Deep dive into Managed VNet

### Inbound network security

<video>
   <src>https://www.youtube.com/watch?v=4u8Xscmy5HE</src>
   <title>Inbound Network Security</title>
</video>

Summary of the video:
- Inbound Connections - Connections coming into the Synapse Workspace
- Endpoint - Point of incoming connection

### Outbound network security

<video>
   <src>https://www.youtube.com/watch?v=vwScocYyeyk</src>
   <title>Outbound Network Security</title>
</video>

Summary of the video:
- Outbound Connections - Connections going out of Synapse Workspace to access other resources and services
- Possible outbound connections 

:::Section Resources:::

- [Troubleshooting connectivity issues](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-troubleshoot-connectivity)
- [Configure virtual network service endpoints](https://docs.microsoft.com/azure/sql-database/sql-database-vnet-service-endpoint-rule-overview?toc=/azure/sql-data-warehouse/toc.json)
- [Configure a VNet-to-VNet connection using the Azure portal](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-vnet-vnet-resource-manager-portal)
- [Configure a VNet-to-VNet connection using Azure CLI](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-vnet-vnet-cli?WT.mc_id=pid:13491:sid:32630460/)
- [Configure a VNet-to-VNet connection using PowerShell](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-vnet-vnet-rm-ps?WT.mc_id=pid:13491:sid:32630460/)
- [Azure Synapse Analytics&ndash;managed virtual network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet)
- [Managed virtual networks and DNS for Azure Synapse Analytics to enable a seamless data estate](https://techcommunity.microsoft.com/t5/azure-architecture-blog/managed-virtual-networks-and-dns-for-synapse-analytics-to-enable/ba-p/3268509)
- [Connect to your Azure Synapse workspace using private links](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links)
- [Connect to workspace resources from a restricted network](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network?source=recommendations)


   
:::Section Relevant results from the web:::

<azureKB>
    <client>Portal</client>
</azureKB>