<properties
    pageTitle="Azure Synapse Analytics Workspace / Create Delete or Move and Deployments / Deployments using ARM templates  REST API  PowerShell or Azure CLI"
    description="Azure Synapse Analytics Workspace / Create Delete or Move and Deployments / Deployments using ARM templates  REST API  PowerShell or Azure CLI"
    ms.author="dialmoth"
    articleId="591dd46d-8945-476a-92a7-faaa6029507a"
    selfHelpType="apollo"
    supportTopicIds="35c5ce3b-c705-b5e6-0a7c-b7f9be7bb7af,d504a4d6-77a0-d6e2-a0e3-6c617bfe93c8"
    productPesIds="17583,17578"
    cloudEnvironments="public,fairfax,mooncake,usnat,ussec"
    resourceRequired="false"
    ownershipId="AzureData_SynapseAnalytics" />

# Azure Synapse Analytics Workspace / Create, Delete or Move and Deployments / Deployments using ARM templates, REST API, PowerShell or Azure CLI

## Learn about deployments by using Azure Resource Manager templates (ARM template), REST API, PowerShell, and Azure CLI

>**Note**: Review the [list of known issues](https://learn.microsoft.com/azure/synapse-analytics/known-issues) currently active or recently resolved in Azure Synapse Analytics.

Infrastructure as code (IaC) can be used to provision dedicated SQL pools. Deployment can be completed by using different tools, like ARM templates, REST API, PowerShell, and Azure CLI.

Use the following guidance to learn how to deploy to dedicated SQL pools using these tools. Scan and select one or more of the following sections to learn more about that topic.

### Before you begin: verify you're using the latest version of the tools

>**Note:** Before you start, it's always recommended *to verify and use the latest version* of the tool. 
Here are resources for the latest version of the tools:
- Latest Azure CLI [Install Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli)
- Latest PowerShell [Install PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-az-ps)
- REST API reference for [dedicated SQL pool (formerly SQL DW)](https://learn.microsoft.com/rest/api/sql/)
- REST API reference for [Synapse workspace REST API reference](https://learn.microsoft.com/rest/api/synapse/)

>**Note:** There are differences between the tools which can be used based on the dedicated SQL pool that you're using—dedicated SQL pools (formerly SQL DW) or  dedicated SQL pool in an Azure Synapse Analytics workspace. 

In each section of guidance below, we've identified the links you can use based on the version.


:::Section Symptoms Table:::

| Symptom | Cause | Resolution |
|-|-|-|
|During a deployment, you might receive a ```RequestDisallowedByPolicy``` error that prevents you from creating a resource. Azure CLI, Azure PowerShell, and the Azure portal's activity log show similar information about the error. The key elements are the error code, policy assignment, and policy definition.|RequestDisallowedByPolicy|[Resolve errors for request disallowed by policy](https://learn.microsoft.com/azure/azure-resource-manager/troubleshooting/error-policy-requestdisallowedbypolicy?tabs=azure-cli)|
|the size limit has been exceeded. The maximum size of 20 MB for synapse template has been reached|There is a file size limitation in git provider, for example, in Azure DevOps the maximum file size is 20Mb.|[Workspace arm file is more than 20MB](https://learn.microsoft.com/azure/synapse-analytics/cicd/continuous-integration-delivery#1--publish-failed-workspace-arm-file-is-more-than-20mb)|
|Workspace is in non-terminal state Failed and cannot be updated|Resource already exists||
|Managed private endpoint stuck in failed state 'error':'code':'UnknownError','message':'\\'CorrelationId\\':\\'\\',\\'StatusCode\\':409,\\'Message\\':|Remove the lock from Resource Group and try again|[Lock your resources to protect your infrastructure](https://learn.microsoft.com/azure/azure-resource-manager/management/lock-resources?tabs=json)|
|Failing to publish SQL script with getting `HttpWrapOperationAsyncFailed` error|There is a special character in the sql script||
|SqlServerRegionDoesNotAllowProvisioning|Quota Issue|[Azure Synapse limits for workspaces](https://learn.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-synapse-limits-for-workspaces)



:::Section PowerShell:::

PowerShell commands can be used to manage many administrative tasks related to the dedicated SQL pools. 
- For a dedicated SQL pool (formerly SQL DW):
  - [PowerShell commands to automate common tasks in your](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-reference-powershell-cmdlets)
- For a dedicated SQL pool in an Azure Synapse Analytics workspace:
  - [PowerShell cmdlets for Azure Synapse Analytics](https://learn.microsoft.com/powershell/module/az.synapse/?context=%2Fazure%2Fsynapse-analytics%2Fcontext%2Fcontext&view=azps-9.1.0)

>**Note**: The cmdlet for SQL pool contains `AzSynapseSql`.

:::Section REST APIs:::

REST APIs can be used to manage compute for SQL pools in Azure Synapse Analytics.
- For a dedicated SQL pool (formerly SQL DW):
  - [REST APIs for dedicated SQL pool (formerly SQL DW)](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-manage-compute-rest-api)
- For a dedicated SQL pool in an Azure Synapse Analytics workspace:
  - [Azure Synapse Analytics REST API](https://learn.microsoft.com/rest/api/synapse/)

:::Section ARM template:::

>**Note**: For dedicated SQL pool (formerly SQL DW), the Azure Resource Manager resource type is `Microsoft.Sql/servers/databases`. For a dedicated SQL pool in an Azure Synapse Analytics workspace, the Azure Resource Manager resource type is `Microsoft.Synapse/workspaces/sqlPools`.

- For a dedicated SQL pool (formerly SQL DW):
  - [Create an Azure Synapse Analytics dedicated SQL pool (formerly SQL DW)](https://learn.microsoft.com/azure/synapse-analytics/sql-data-warehouse/quickstart-arm-template?tabs=CLI)
- For a dedicated SQL pool in an Azure Synapse Analytics workspace:
  - [Create Synapse workspace by using Azure Resource Manager for proof of concept (POC)](https://learn.microsoft.com/azure/templates/microsoft.synapse/workspaces/sqlpools?pivots=deployment-language-arm-template#quickstart-templates)

:::Section Resources:::

**Create a workspace with different tools**

- [Create an Azure Synapse workspace using an ARM template](https://docs.microsoft.com/azure/synapse-analytics/quickstart-deployment-template-workspaces)
- [Create an Azure synapse workspace with Azure CLI](https://docs.microsoft.com/azure/synapse-analytics/quickstart-create-workspace-cli)
- [Create an Azure synapse workspace with Azure PowerShell](https://docs.microsoft.com/azure/synapse-analytics/quickstart-create-workspace-powershell)

**Additional resources**

- [Azure Synapse Analytics REST API](https://docs.microsoft.com/rest/api/synapse/)
- [Azure CLI - az synapse](https://docs.microsoft.com/cli/azure/service-page/azure%20synapse%20analytics?view=azure-cli-latest)
- [Azure PowerShell - Az.Synapse](https://docs.microsoft.com/powershell/module/az.synapse/)
- [Azure Synapse Analytics .NET SDK](https://docs.microsoft.com/dotnet/api/microsoft.azure.management.synapse)
- [Azure Synapse Analytics GO SDK](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/services/preview/synapse)
- [Synapse Samples](https://github.com/Azure-Samples/Synapse)

### Relevant results from the web

<azureKB>
  <client>portal</client>
</azureKB>