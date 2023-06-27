# Azure Synapse Analytics Workspace / Security / Access control or permissions

## Learn how to manage Azure Synapse workspace access control and permissions

Azure Synapse provides a comprehensive and fine-grained [access control](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-access-control-overview) system, that integrates:

- **Azure roles** for resource management and access to data in storage,
- **Synapse roles** for managing live access to code and execution,
- **SQL roles** for data plane access to data in SQL pools, and
- **Git permissions** for source code control, including continuous integration and deployment support.

Azure Synapse roles provide sets of permissions that can be applied at different scopes. This granularity makes it easy to grant appropriate access to administrators, developers, security personnel, and operators to compute resources and data.

**What is the purpose of private endpoints created in synapse service?**
 - Private endpoints are used for ***connecting to the workspace privately.*** They are created in the Azure portal on the Synapse workspace resource under the Private Endpoints tab as shown in your screenshot.\

 **How can we use them?**
  - Private endpoints can be created for *any* workspace. **Private endpoint creation has no bearing on Managed VNET/DEP. They are unrelated.**

**What is this setting Public network access - Enable or Disable?**
 - When public network access is enabled, you can connect to your workspace also from public networks. If you disable public network access, you can connect to your workspace only using private endpoint and yes it is more secure. You also need to whitelist IP Addresses for connecting to Synapse(firewall rules)\
[Azure Synapse connectivity settings - Azure Synapse Analytics | Microsoft Learn](https://learn.microsoft.com/azure/synapse-analytics/security/connectivity-settings)\
[Configure IP firewall rules - Azure Synapse Analytics | Microsoft Learn](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall)

**Private Endpoint vs Private Link Hub**
  - Synapse Private Link Hubs are used to connect to the ***WEB*** endpoint for Synapse Studio, web.azuresynapse.net. The Web endpoint is used to load the studio itself.

:::Section Failed to load one or more resources due to forbidden issue, error code 403:::

This could be an intermittent issue while opening synapse workspace.

Make sure you have required permissions to access workspace:
 - From Azure Portal under Synapse Workspace, Access control (IAM), View my access, user needs to have Owner/Contributor permission  
 - From Azure Portal under Synapse Workspace, Networking, user needs to add correct IP address under firewall rules

**Option1:** Try to manually sign into your [workspace](https://web.azuresynapse.net). (Read [more](https://docs.microsoft.com/azure/synapse-analytics/get-started-create-workspace#open-synapse-studio))

**Option2:**
 - Clear "Cookies and Cached data" of your browser.
 - Use Private Mode.
 - Try different browser.


:::Section Recommendations and best practices:::

A [system-assigned managed identity](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-identity) is created for your Azure Synapse workspace when you create the workspace. You can [retrieve your workspace's managed identity](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-identity#retrieve-managed-identity-in-azure-portal) from Azure Portal.

When a table (a table in a Spark database or external table created in Serverless SQL) is queried by Spark or Serverless SQL pool engines that the query submitter has the right to use, the query submitter's security principal is being passed through to the underlying files. Permissions are checked at the file system level. Learn how to [assign ```Storage Blob Data Reader``` or ```Storage Blob Data Contributor``` RBAC permissions on Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal?toc=/azure/synapse-analytics/toc.json&bc=/azure/synapse-analytics/breadcrumb/toc.json#assign-a-built-in-rbac-role).

:::Section Spark and SQL Pool Security Model on Metadata:::

- The Spark databases and tables, along with their synchronized representations in the SQL engines will be secured at the underlying storage level.

- The security principal who creates a database is considered the owner of that database, and has all the rights to the database and its objects.

- The security principal who creates a managed table is considered the owner of that table and has all the rights to the table as well as the underlying folders and files. In addition, the owner of the database will automatically become co-owner of the table.

- If you create a Spark or SQL external table with authentication pass-through, the data is only secured at the folder and file levels. If someone queries this type of external table, the security identity of the query submitter is passed down to the file system, which will check for access rights.

:::Section Resources:::

- [Secure your Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-set-up-access-control#overview)

- [Azure Synapse workspace managed identity](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-identity)

- [Create and manage IP firewall rules](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#create-and-manage-ip-firewall-rules)

- [Managed workspace VNet](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet)

- [Managed private endpoint](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-private-endpoints)

- [Azure Active Directory Authentication](https://docs.microsoft.com/azure/synapse-analytics/sql/active-directory-authentication)

- [AAD pass-through in Azure Synapse Analytics](https://docs.microsoft.com/azure/synapse-analytics/sql/active-directory-authentication#aad-pass-through-in-azure-synapse-analytics)



:::Section Here are some relevant results from the web:::
<azureKB>
    <client>Portal</client>
</azureKB>