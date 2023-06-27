# Azure Synapse Analytics Workspace / Connectivity / Azure Synapse Studio

## Resolve Azure Synapse Studio connectivity issues

Connectivity issues in Azure Synapse Studio can be caused by incorrect firewall settings for public and private networks, not having the correct role-based access control (RBAC) role assignment, or other issues.

Use the following guidance to troubleshoot connectivity issues with Synapse Studio. Scan and select one or more of the following sections for guidance to help resolve your issues.

### Table: Symptom, cause, and solution

Use the following table to help determine symptoms, causes, and olutions for connectivity issues.

| Symptom | Cause | Solution |
|-|-|-|
|Error code 9054 Cannot connect to linked services|Deployments of a workspace in GIT without the Managed VNet|Add the Managed Virtual Network configuration on the template used for workspace deployment|
|Cannot connect to SQL database|Error Code: 40892. Error Message: Cannot connect to database when it is paused.|Try pausing and resuming the pool.|
|Error in Power BI when refreshing the data via Synapse: The SQL pool is warming up|The activation happens automatically on the first activity, such as the first connection attempt. The activation process might take a bit longer than a single connection attempt interval, so the error message is displayed.|Retry the connection attempt.|
|Failed to detect schema, review and update the file format settings to allow file schema detection|You must have access to the workspace with at least the Storage Blob **Data Contributor** access role to the ADLS Gen2 Account to query the files from storage account.|[Use external tables with Synapse SQL](https://learn.microsoft.com/azure/synapse-analytics/sql/develop-tables-external-tables?tabs=hadoop)
|Error 400 while loading synapse workspace|misconfiguration|<ul><li>[Connect to workspace resources in Azure Synapse Analytics Studio from a restricted network](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network)</li><li>[Azure Private Endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns)</li></ul>|
|ADLS Gen2 operation failed for: Storage operation get failed with operation returned an invalid status code 'Forbidden'|When a workspace is created, a default linked service to storage account is also created. It uses the workspace Managed Service Identity as the authentication method and this linked service can't be edited. You are getting this error because the workspace identity is lacking the Storage Blob Data Contributor role on the associated storage account|[Access control in Synapse Workspace](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-set-up-access-control#step-4-grant-the-workspace-msi-access-to-the-default-storage-container)|
|An instance-specific error occurred while establishing a connection to SQL Server. Connection was denied because Deny Public Network Access is set to Yes|Using data exfiltration protection (DEP) enabled workspace|<ul><li>[Understanding Azure Synapse Private Endpoints](https://techcommunity.microsoft.com/t5/azure-architecture-blog/understanding-azure-synapse-private-endpoints/ba-p/2281463)</li><li>[Connect to a Synapse workspace using private links](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links)</li><li>[Data exfiltration protection for Azure Synapse Analytics workspaces](https://learn.microsoft.com/azure/synapse-analytics/security/workspace-data-exfiltration-protection)</li><li>[Managed private endpoints](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints)</li></ul>|
|Error Message: COPY statement input file schema discovery failed Cannot bulk load|Misconfiguration|[Use external tables with Synapse SQL](https://learn.microsoft.com/azure/synapse-analytics/sql/develop-tables-external-tables?tabs=hadoop)|
|Table lock while pulling the data from SAP ECC|By design|This is due to transaction isolation to reduce inconsistency in the data|
|Can't install integration Rruntime. Received the following error message: Per-machine installation is stopped because there is existing per user gateway installation|This error is expected. It indicates that a self-hosted integration runtime (SHIR) has already been installed on the target virtual machine. Only one SHIR per VM is permitted. To install additional SHIR, you'll need to set up a separate VM to host each integration runtime (IR) instance|You can install only one instance of a self-hosted integration runtime on any single machine. If you have two data factories or Synapse workspaces that need to access on-premises data sources, either use the self-hosted IR sharing feature to share the self-hosted IR or install the self-hosted IR on two on-premises computers, one for each data factory or Synapse workspace. Only Azure Data Factory supports the self-hosted IR sharing feature. [Create a self-hosted integration runtime](https://learn.microsoft.com/azure/data-factory/create-self-hosted-integration-runtime?tabs=synapse-analytics)|
|Error code 2108, Error calling the endpoint ''. Response status code: ''. More details: Exception message: "Request didn't reach the server from the client." This could happen because of an underlying issue such as network connectivity, a DNS failure, a server certificate validation or a timeout|Misconfigured with a Managed Virtual Network and with Data Exfiltration Protection enabled|If you want to create a workspace that is in a shared VNet, or in a Managed VNet without DEP, you'll need to create a new workspace. See the private endpoint overview and related documentation: <ul><li>[What is a private endpoint?](https://learn.microsoft.com/azure/private-link/private-endpoint-overview)</li><li>[Understanding Azure Synapse Private Endpoints](https://techcommunity.microsoft.com/t5/azure-architecture-blog/understanding-azure-synapse-private-endpoints/ba-p/2281463)</li></ul>A Private Link Service may also be a possible solution:<ul><li>[What is Azure Private Link?](https://learn.microsoft.com/azure/private-link/private-link-overview)</li><li>[What is Azure Private Link service?](https://learn.microsoft.com/azure/private-link/private-link-service-overview)</li></ul>Many configurations will require DNS configuration within your network so that requests will be correctly routed to the Private Endpoints inside the VNET:<ul><li>[Azure Private Endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns)</li><ul>|
|ADLS Gen 1 data access via service principal is not working|Linked service in the GIT repo can't be published to Synapse live mode|The linked service in the GIT repo cannot be published to Synapse live mode|
|Network issue when connecting to Sftp server 'ServerName', SocketErrorCode:'TimedOut'|SFTP connection issue|[SFTP Connection Issue](https://learn.microsoft.com/answers/questions/101104/sftp-connection-issue.html)|
|Synapse built-in pool in not available|System clock is out of sync, problem occurs during CSRF token validation.|Sync System clock|

**Additional troubleshooting guidance**

- Learn how to [troubleshoot Azure Synapse Studio](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio#troubleshooting-steps).

- [Diagnose connectivity issues using this PowerShell script](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio-powershell).

- Confirm that Synapse Studio can access all the required endpoints:
  - Make sure that the firewall on your network and local computer allows outgoing communication on TCP ports 80, 443, and 1443 for Synapse Studio.
  - Make sure that outgoing communication is allowed on UDP port 53 for Synapse Studio.
  - To connect using tools such as SSMS and Power BI, you must allow outgoing communication on TCP port 1433.
  - If you're using the default Redirect connection policy setting, you may need to allow outgoing communication on additional ports.

- Test access with different browsers, and disable any pop-up blockers and plugins.

- Investigate issues related to security and permissions:
  - [Workspaces, data, and pipelines](https://docs.microsoft.com/azure/synapse-analytics/sql/access-control)
  - [Managed identities](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-identity)
  - [Database access](https://docs.microsoft.com/azure/azure-sql/database/logins-create-manage?toc=%2Fazure%2Fsynapse-analytics%2Ftoc.json&bc=%2Fazure%2Fsynapse-analytics%2Fbreadcrumb%2Ftoc.json)


### Failed to load one or more resources due to forbidden issue, error code 403

This could be an intermittent issue while opening your Synapse workspace in Synapse Studio.

Make sure you have the following required permissions to access your workspace:
 - From Azure portal, under **Synapse Workspace** > **Access control (IAM)** > **View my access**, the user needs to have Owner/Contributor permission.
 - From Azure portal, under **Synapse Workspace** > **Networking**, the user needs to make sure that the correct client IP address is present in the [firewall rules](https://docs.microsoft.com/azure/azure-sql/database/firewall-configure?view=azuresql#create-and-manage-ip-firewall-rules).

You can also try the following two options:

* Try to manually sign in to your [workspace](https://web.azuresynapse.net). For more information, see [Get started creating a workspace](https://docs.microsoft.com/azure/synapse-analytics/get-started-create-workspace#open-synapse-studio).

* Also try the following actions:
 - Clear **Cookies and Cached Data** in your browser.
 - Use Private Mode.
 - Try using a different browser.

### Set up Synapse on a private network

You may not be able to connect to Azure Synapse if you disable the public network in firewall.
- Enable Public IP and add specific IPs that need to access Azure Synapse. Azure Firewall will not allow any other Public IP Address besides the one already added.

If you want to disable public IP, you can implement one of the following options.
* If only a few users are planning to connect to Azure Synapse from their own machine, use a [Point-To-Site](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) VPN connection to connect to Azure Synapse.
* If many users want to connect to Azure services from their own workstation, use [ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-introduction).

### FAQ: Azure Synapse Studio connectivity

**How do I connect to Azure Synapse Studio from behind an on-premises network firewall?**

You can do this by setting up a secure connection using a virtual private network (VPN). Additionally, you can use a secure gateway to allow access to the [Azure Synapse Studio](https://docs.microsoft.com/azure/synapse-analytics/quickstart-synapse-studio#launch-synapse-studio) from within the on-premises network. This gateway will provide secure access from the on-prem network to the Azure Synapse Studio. You can also use [Azure private endpoint DNS configuration](https://learn.microsoft.com/azure/private-link/private-endpoint-dns) to connect to Azure Synapse Studio from behind an on-premises network firewall. [Private endpoints](https://techcommunity.microsoft.com/t5/azure-architecture-blog/understanding-azure-synapse-private-endpoints/ba-p/2281463) enable you to access Azure resources securely from within your on-prem network. By configuring a private endpoint DNS configuration, you can securely connect to the Azure Synapse Studio from within your on-premises network *without having to set up a VPN or a secure gateway*.

**I am unable to pull data from linked Azure Data Explorer data sources**

Go to [Azure portal](https://ms.portal.azure.com/#home), and then navigate to the resource > **Access Control (IAM)** > **View my access** > and then make sure that users have proper permission. Also verify that Azure Data Explorer has access to Synapse resource under the same Access Control (IAM) on the Azure Data Explorer end (Contributor role). 

**I am unable to connect to default blob storage**

To resolve this issue, use the following troubleshooting steps: First, make sure that you're using the correct connection credentials. If you're using the correct credentials, then check to see if the storage account is active and that the firewall and virtual networks are set up correctly. Also need to check the access control list to make sure that you have the appropriate permissions to access the storage account.

**How do I change the compatibility level of the DW?**

To change the compatibility level of the DW, use one of the two following options:
- [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](https://learn.microsoft.com/sql/t-sql/statements/alter-database-scoped-configuration-transact-sql?view=sql-server-ver15)
- [ALTER DATABASE (Transact-SQL) compatibility level](https://learn.microsoft.com/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-ver15)

**Technical info about data processed by a Synapse Studio privatelink**

A [Synapse Studio private link](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-private-link-hubs) is a secure, private data link that allows users to securely transfer data between systems. It provides a secure, private connection between two systems, allowing data to be transferred without any risk of interception. It also provides a secure, private connection between two systems, allowing data to be transferred without any risk of interception. The privatelink provides a secure, private connection between two systems, allowing data to be transferred without any risk of interception.

**How do I connect Synapse workspace Data Flow (Data) connectivity to SQL Server?**

See the following example of connecting Synapse workspace Data Flow to SQL Server:
1. Create a Synapse workspace Data Flow. 
2. In the Data Flow, add the SQL Server Connector. 
3. Configure the connector with the appropriate connection information, such as the server name, database name, user name, and password. 
4. Select the type of data.
5. Select the source and destination tables or views. 
6. Configure the data flow with the necessary transformations. 
7. Test the data flow and run it to move data from the source to the destination.
8. Monitor the data flow to make sure that it's running properly and that the data is being transferred correctly.
9. After the data is transferred, verify that the data is correct and complete. 
10. Finally, deploy the data flow to make it available for use.

### Resources

- [Connect to Synapse from your own network](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#connect-to-synapse-from-your-own-network)
- [Synapse Workspace Pools and On Demand Inaccessible](https://techcommunity.microsoft.com/t5/azure-synapse-analytics/synapse-workspace-pools-and-on-demand-inaccessible/ba-p/1403485)
- [Azure RBAC permissions for Azure Private Link](https://docs.microsoft.com/azure/private-link/rbac-permissions?msclkid=d6948d48c6dc11ec857440eb53627605)
- Create a [self-hosted integration runtime (SHIR)](https://docs.microsoft.com/azure/purview/manage-integration-runtimes) while [data exfiltration protection (DEP)](https://docs.microsoft.com/azure/synapse-analytics/security/workspace-data-exfiltration-protection) is enabled in your workspace to prevent access issues.
- [Connect to workspace resources from a restricted network](https://learn.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network)

### Relevant results from the web

<azureKB>
    <client>Portal</client>
</azureKB>