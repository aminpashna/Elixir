# Azure Synapse Analytics Workspace / Synapse Studio / Synapse Studio User Interface or publishing issues

## Set up access control for your Azure Synapse workspace
**_Note:_** The approach taken in this guide is to create several security groups and then assign roles to these groups. After the groups are set up, you only need to manage membership within the security groups to control access to the workspace.

To [secure an Azure Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-set-up-access-control#access-control-mechanisms), you'll follow a pattern of configuring the following items:

- **Security Groups,** to group users with similar access requirements.
- **Azure roles,** to control who can create and manage SQL pools, Apache Spark pools and Integration runtimes, and access ADLS Gen2 storage.
- **Synapse roles,** to control access to published code artifacts, use of Apache Spark compute resources, and Integration runtimes.
- **SQL permissions,** to control administrative and data plane access to SQL pools.
- **Git permissions,** to control who can access code artifacts in source control if you configure Git-support for the workspace.

### Failed to load one or more resources due to forbidden issue, error code 403

This could be an intermittent issue while opening synapse workspace.

Make sure you have required permissions to access workspace:
 - From Azure Portal under Synapse Workspace, Access control (IAM), View my access, user needs to have Owner/Contributor permission  
 - From Azure Portal under Synapse Workspace, Networking, user needs to add correct IP address under firewall rules

**Option1:** Try to manually sign into your [workspace](https://web.azuresynapse.net). (Read [more](https://docs.microsoft.com/azure/synapse-analytics/get-started-create-workspace#open-synapse-studio))

**Option2:**
 - Clear "Cookies and Cached data" of your browser.
 - Use Private Mode.
 - Try different browser.


### Troubleshooting

| Symptom | Cause | Resolution |
|-|-|-|
|Unable to return all rows in synapse studio by querying serverless SQL|



### Common errors
Follow the linked errors to resolve the issues related to them.
- [Cannot access the synapse workspace with an error code 403](https://docs.microsoft.com/azure/synapse-analytics/security/connectivity-settings)
- [Not able to access Synapse workspace web portal](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-synapse-rbac-roles)
- [Synapse studio connection issue](https://docs.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#:~:text=You%20can%20also%20add%20IP,Select%20Save%20when%20done.)
- Issues related to [loading Workspace via Private Endpoint](https://techcommunity.microsoft.com/t5/azure-architecture-blog/understanding-azure-synapse-private-endpoints/ba-p/2281463)
- [Troubleshoot Synapse Studio](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio)

:::Section Resources:::
- Troubleshoot [serverless SQL pool service connectivity issue](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio#serverless-sql-pool-service-connectivity-issue)
- Troubleshoot [notebook websocket connection issue](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio#notebook-websocket-connection-issue)
- Troubleshoot [connectivity between Azure Synapse Analytics Synapse Studio and storage](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio-and-storage-connectivity)
- How to [set up access control for your Azure Synapse workspace](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-set-up-access-control)
- How to [create a custom event trigger to run a pipeline in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-create-custom-event-trigger#set-up-a-custom-topic-in-event-grid)
- How to [Connect to workspace resources from a restricted network](https://docs.microsoft.com/azure/synapse-analytics/security/how-to-connect-to-workspace-from-restricted-network)


:::Section Here are some relevant results from the web:::
<azureKB>
    <client>Portal</client>
</azureKB>