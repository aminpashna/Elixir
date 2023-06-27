# PatchWorkspaceError

## What is Customer Managed Keys

You can use your own encryption key to protect the data in your storage account. When you specify a customer-managed key, that key is used to protect and control access to the key that encrypts your data. Customer-managed keys offer greater flexibility to manage access controls.

You must use one of the following Azure key stores to store your customer-managed keys:

- [Azure Key Vault](https://learn.microsoft.com/azure/key-vault/general/overview)
- [Azure Key Vault Managed Hardware Security Module (HSM)](https://learn.microsoft.com/azure/key-vault/managed-hsm/overview)

You can either create your own keys and store them in the key vault or managed HSM, or you can use the Azure Key Vault APIs to generate keys. The storage account and the key vault or managed HSM can be in different Azure Active Directory (Azure AD) tenants, regions, and subscriptions.

>Note\
Azure Key Vault and Azure Key Vault Managed HSM support the same APIs and management interfaces for configuration of customer-managed keys. Any action that is supported for Azure Key Vault is also supported for Azure Key Vault Managed HSM.

:::Section Updating CMK caused Workspace in failed state:::

The issue started after attempting to update the customer-managed key (CMK), which resulted in a 403 error, causing the workspace to enter a failed state. Here are some steps you can take to mitigate the issue:

- If the workspace is stuck in a **Failed** state, you can try to delete and recreate the workspace. Please note that this will delete all data and configurations associated with the workspace, so make sure to backup any important data before attempting this step.
- You can also try to redeploy the workspace using an [ARM template](https://learn.microsoft.com/azure/azure-resource-manager/templates/overview) or the [Azure portal](https://ms.portal.azure.com/#home) to see if that resolves the issue.



:::Section Resources:::

- [Customer-managed keys for Azure Storage encryption](https://learn.microsoft.com/azure/storage/common/customer-managed-keys-overview)

### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>