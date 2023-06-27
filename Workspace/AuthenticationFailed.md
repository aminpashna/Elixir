# AuthenticationFailed

## Azure Synapse Analytics security: Authentication

Frequent headlines of data breaches, malware infections, and malicious code injection are among an extensive list of security concerns for companies looking to cloud modernization. The enterprise customer requires a cloud provider or service solution that can address their concerns as they can't afford to get it wrong.

Some common security questions include:

- How can I control who can see what data?
- What are the options for verifying a user's identity?
- How is my data protected?
- What network security technology can I use to protect the integrity, confidentiality, and access of my networks and data?
- What are the tools that detect and notify me of threats?

Authentication is the process of proving the user is who they claim to be. Authentication activities can be logged with [Azure SQL Auditing](https://learn.microsoft.com/azure/azure-sql/database/auditing-overview?view=azuresql), and an IT administrator can configure reports and alerts whenever a login from a suspicious location is attempted.

:::Section Token authentication failed - response status code does not indicate success: 401 (unauthorized):::

The error message suggests that the token authentication failed with a 401 unauthorized status code. Here are some steps you can try to troubleshoot and resolve this issue:

- Ensure that the service principal has the necessary permissions on the Azure Synapse workspace. The **Synapse Contributor** role should be sufficient, but you can also try to assign the **Synapse Administrator** role to the service principal to see if that resolves the issue.
- Verify that the service principal's credentials are still valid and have not expired. You can do this by going to the Azure portal, navigating to the **Azure Active Directory** service, and then selecting **App registrations** from the left-hand menu. From there, find the service principal used to run the pipelines, and verify that the credentials are still valid.
- Check if there have been any changes to the authentication policies or configurations for the Azure Synapse workspace or the Azure subscription that may be causing the issue.
- Make sure that the Azure PowerShell module is up to date and that you are using the latest version of the ```Invoke-AzSynapsePipeline``` cmdlet.

:::Section Managed identity for Azure Synapse:::

This article helps you understand managed identity (formerly known as Managed Service Identity/MSI) and how it works in Azure Synapse.

>[!Note]\
We recommend that you use the Azure Az PowerShell module to interact with Azure. See [Install Azure PowerShell](https://learn.microsoft.com/powershell/azure/install-azure-powershell?view=azps-10.0.0) to get started. To learn how to migrate to the Az PowerShell module, see [Migrate Azure PowerShell from AzureRM to Az](https://learn.microsoft.com/powershell/azure/migrate-from-azurerm-to-az?view=azps-10.0.0).

Managed identities eliminate the need to manage credentials. Managed identities provide an identity for the service instance when connecting to resources that support Azure Active Directory (Azure AD) authentication. For example, the service can use a managed identity to access resources like [Azure Key Vault](https://learn.microsoft.com/azure/key-vault/general/overview), where data admins can securely store credentials or access storage accounts. The service uses the managed identity to obtain Azure AD tokens.

There are two types of supported managed identities: 

- **System-assigned:** You can enable a managed identity directly on a service instance. When you allow a system-assigned managed identity during the creation of the service, an identity is created in Azure AD tied to that service instance's lifecycle. By design, only that Azure resource can use this identity to request tokens from Azure AD. So when the resource is deleted, Azure automatically deletes the identity for you. Azure Synapse Analytics requires that a system-assigned managed identity must be created along with the Synapse workspace.
- **User-assigned:** You may also create a managed identity as a standalone Azure resource. You can [create a user-assigned managed identity](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/how-manage-user-assigned-managed-identities?pivots=identity-mi-methods-azp) and assign it to one or more instances of a Synapse workspace. In user-assigned managed identities, the identity is managed separately from the resources that use it.

Managed identity provides the below benefits:

- [Store credential in Azure Key Vault](https://learn.microsoft.com/en-us/azure/data-factory/store-credentials-in-key-vault), in which case-managed identity is used for Azure Key Vault authentication.
- Access data stores or computes using managed identity authentication, including Azure Blob storage, Azure Data Explorer, Azure Data Lake Storage Gen1, Azure Data Lake Storage Gen2, Azure SQL Database, Azure SQL Managed Instance, Azure Synapse Analytics, REST, Databricks activity, Web activity, and more. Check the connector and activity articles for details.
- Managed identity is also used to encrypt/decrypt data and metadata using the customer-managed key stored in Azure Key Vault, providing double encryption. 

### **Authentication failed for 'Microsoft.ManagedIdentity' error**

This error message suggests that the authentication process for the Managed Identity has failed. Here are some steps you can take to troubleshoot and resolve this issue:

- Verify that the Managed Identity is correctly configured and has the necessary permissions to access the resource it is trying to authenticate with. You can do this by going to the Azure portal, navigating to the resource that the Managed Identity is associated with, and then selecting **Identity** under the **Settings** section. From there, you can verify that the Managed Identity is enabled and has the necessary permissions.
- Ensure that the resource the Managed Identity is trying to authenticate with supports Managed Identity authentication. Not all Azure services support Managed Identity authentication, so it's important to verify that the service you're trying to access supports this authentication method.
- Check if there have been any changes to the authentication policies or configurations for the resource or the Azure subscription that may be causing the issue.
- Make sure that the system-assigned or user-assigned Managed Identity is correctly configured and that the application or service attempting to use the Managed Identity is properly authorized.

:::Section Resources:::

- [Azure Synapse Analytics security white paper: Authentication](https://learn.microsoft.com/azure/synapse-analytics/guidance/security-white-paper-authentication)
- [Auditing for Azure SQL Database and Azure Synapse Analytics](https://learn.microsoft.com/azure/azure-sql/database/auditing-overview?view=azuresql)
- [Azure Synapse: ManagedIdentityCredential authentication failed](https://learn.microsoft.com/answers/questions/867543/azure-synapse-managedidentitycredential-authentica)
- [Managed identity for Azure Synapse](https://learn.microsoft.com/azure/synapse-analytics/synapse-service-identity)

### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>