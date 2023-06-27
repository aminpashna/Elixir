# Azure Synapse Analytics Workspace / Connectivity / Firewall rules

## Learn to manage firewall rules in an Azure Synapse Analytics workspace

IP firewall rules grant or deny access to your Synapse workspace based on the originating IP address of each request. You can configure IP firewall rules for your workspace. IP firewall rules configured at the workspace level apply to all public endpoints of the workspace (dedicated SQL pools, serverless SQL pool, and development).

Use the following guidance to learn more about managing firewall rules in an Azure Synapse Analytics workspace. Scan the following headings and select one or more to learn more about that topic and to resolve any issues you may be experiencing.

**Diagnose Azure Synapse Studio connectivity issues** with the [`Test-AzureSynapse` PowerShell script](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio-powershell).


:::Section Create and manage IP firewall rules:::

**Important**: This feature is available only in Azure Synapse workspaces not associated with a managed virtual network.

There are two ways to add IP firewall rules to an Azure Synapse workspace. 

1. To add an IP firewall to your workspace during the workspace creation, select **Networking** and check **Allow connections from all IP addresses**.

![Create Synapse workspace page with Networking selected and Allow connections from all IP addresses checked](https://docs.microsoft.com/azure/synapse-analytics/security/media/synpase-workspace-ip-firewall/azure-synapse-workspace-networking-connections-all-ip-addresses.png#lightbox)

2. You can also add IP firewall rules to a Synapse workspace after the workspace is created. Select **Firewalls** under **Security** from the Azure portal. To add a new IP firewall rule, give it a name, start IP, and end IP. Select **Save** when done.

> **Note**: The public network access feature is only available to Azure Synapse workspaces associated with an Azure Synapse Analytics&ndash;managed virtual network. However, you can still open your Azure Synapse workspaces to the public network, regardless of its association with a managed virtual network. For more information, see [Public network access](https://docs.microsoft.com/azure/synapse-analytics/security/connectivity-settings#public-network-access).

![Networking pane with select elements highlighted](https://docs.microsoft.com/azure/synapse-analytics/security/media/synpase-workspace-ip-firewall/azure-synapse-workspace-networking-firewalls-add-client-ip.png#lightbox)


:::Section Troubleshoot SQL Server Error 10054:::

Review the following documents if you're encountering "Error 10054" while using SQL Server Management Studio to connect to an Azure workspace, or if you're encountering "Client unable to establish connection" using an ODBC driver.

- [Azure TLS Certificate Changes | Microsoft Docs](https://docs.microsoft.com/azure/security/fundamentals/tls-certificate-changes)
- Review the minimum allowed TLS version set: [Connectivity settings for Azure SQL Database and Azure Synapse Analytics - Azure SQL Database and Azure Synapse Analytics | Microsoft Docs](https://docs.microsoft.com/azure/azure-sql/database/connectivity-settings?view=azuresql&tabs=azure-portal)
- Make sure the machine has the correct certificates installed to allow the TLS handshake to succeed.


:::Section Self-hosted integration runtime:::

The integration runtime is the compute infrastructure that Azure Data Factory and Synapse pipelines use to provide data-integration capabilities across different network environments. For details about integration runtime, see [Integration runtime overview](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime).

A self-hosted integration runtime can run copy activities between a cloud data store and a data store in a private network. It also can dispatch transform activities against compute resources in an on-premises network or an Azure virtual network. The installation of a self-hosted integration runtime needs an on-premises machine or a virtual machine inside a private network.

A self-hosted integration runtime is capable of:
- Running copy activity between a cloud data store and a data store in a private network.
- Dispatching the following transform activities against compute resources in on-premises or Azure Virtual Network: HDInsight Hive activity (Bring Your Own Cluster [BYOC]), HDInsight Pig activity (BYOC), HDInsight MapReduce activity (BYOC), HDInsight Spark activity (BYOC), HDInsight Streaming activity (BYOC), ML Studio (classic) Batch Execution activity, ML Studio (classic) Update Resource activities, Stored Procedure activity, Data Lake Analytics U-SQL activity, Custom activity (runs on Azure Batch), Lookup activity, and Get Metadata activity.

**Self-hosted integration runtime network environment**

If you want to perform data integration securely in a private network environment that doesn't have a direct line of sight from the public cloud environment, you can install a self-hosted integration runtime in your on-premises environment behind a firewall, or inside a virtual private network. The self-hosted integration runtime only makes outbound HTTP-based connections to the internet.

:::Section Resources:::

- [IP firewall rules](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall)
- [Create and manage IP firewall rules](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#create-and-manage-ip-firewall-rules)
- [Connecting to Synapse from your own network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#connecting-to-synapse-from-your-own-network)
- [Managed workspace virtual network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet)
- [Managed private endpoint](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints)
- [Connect to your Azure Synapse workspace using private links](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links#step-1-open-your-azure-synapse-workspace-in-azure-portal)
- [Create and configure a self-hosted integration runtime](https://docs.microsoft.com/azure/data-factory/create-self-hosted-integration-runtime?tabs=data-factory)


:::Section Relevant results from the web:::

<azureKB>
    <client>Portal</client>
</azureKB>