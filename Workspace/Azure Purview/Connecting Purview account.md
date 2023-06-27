# Azure Synapse Analytics Workspace / Azure Purview (Preview) / Connecting Purview account

## What is Azure Purview

Microsoft Purview provides a unified data governance solution to help manage and govern your on-premises, multicloud, and software as a service (SaaS) data. Easily create a holistic, up-to-date map of your data landscape with automated data discovery, sensitive data classification, and end-to-end data lineage. Enable data consumers to access valuable, trustworthy data management.


## Create an account in the Microsoft Purview governance portal

This quickstart describes the steps to Create a Microsoft Purview (formerly Azure Purview) account through the Azure portal. Then we'll get started on the process of classifying, securing, and discovering your data in the Microsoft Purview Data Map!

The Microsoft Purview governance portal surfaces tools like the Microsoft Purview Data Map and Microsoft Purview Data Catalog that help you manage and govern your data landscape. By connecting to data across your on-premises, multicloud, and software-as-a-service (SaaS) sources, the Microsoft Purview Data Map creates an up-to-date map of your data estate. It identifies and classifies sensitive data, and provides end-to-end linage. Data consumers are able to discover data across your organization, and data administrators are able to audit, secure, and ensure right use of your data.

For more information about the governance capabilities of Microsoft Purview, formerly Azure Purview, [see our overview page](https://learn.microsoft.com/azure/purview/overview). For more information about deploying Microsoft Purview governance services across your organization, [see our deployment best practices](https://learn.microsoft.com/azure/purview/deployment-best-practices).


> Important\
> If you have any [Azure Policies](https://learn.microsoft.com/azure/governance/policy/overview) preventing creation of **Storage accounts** or **Event Hub namespaces**, or preventing **updates to Storage accounts** first follow the [Microsoft Purview exception tag](https://learn.microsoft.com/azure/purview/create-microsoft-purview-portal-faq) guide to create an exception for Microsoft Purview accounts. Otherwise you will not be able to deploy Microsoft Purview.


- Sign in to the [Azure portal](https://ms.portal.azure.com/#home) with your Azure account.
- Search for **Microsoft Purview** in the Azure portal.
![image_1](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/purview-accounts-page.png)
- Select **Create** to create a new Microsoft Purview account.
![image_2](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/select-create.png)
Or instead, you can go to the marketplace, search for **Microsoft Purview**, and select **Create**.
![image_3](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/search-marketplace.png)
- On the new Create Microsoft Purview account page under the **Basics** tab, select the Azure subscription where you want to create your account.
- Select an existing **resource group** or create a new one to hold your account.
  - To learn more about resource groups, see our article on [using resource groups to manage your Azure resources](https://learn.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal#what-is-a-resource-group).
- Enter a **Microsoft Purview account name**. Spaces and symbols aren't allowed. The name of the Microsoft Purview account must be globally unique. If you see the following error, change the name of Microsoft Purview account and try creating again.
![image_4](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/name-error.png)
- Choose a **location**. The list shows only locations that support the Microsoft Purview governance portal. The location you choose will be the region where your Microsoft Purview account and meta data will be stored. Sources can be housed in other regions.
    >Note\
    > The Microsoft Purview, formerly Azure Purview, does not support moving accounts across regions, so be sure to deploy to the correction region. You can find out more information about this in [move operation support for resources](https://learn.microsoft.com/azure/azure-resource-manager/management/move-support-resources).
- You can choose a name for your managed resource group. Microsoft Purview will create a managed storage account in this group that it will use during its processes.
- On the **Networking** tab you can choose to connect to all networks, or to use private endpoints. For more information and configuration options, see [Configure firewall settings for your Microsoft Purview account](https://learn.microsoft.com/azure/purview/catalog-firewall) and [private endpoints for Microsoft Purview articles](https://learn.microsoft.com/azure/purview/catalog-private-link).
- On **Configuration** tab you can choose to configure Event Hubs namespaces to programmatically monitor your Microsoft Purview account using Event Hubs and Atlas Kafka.
   - [Steps to configure Event Hubs namespaces](https://learn.microsoft.com/azure/purview/configure-event-hubs-for-kafka)
   - [Send and receive Atlas Kafka topics messages](https://learn.microsoft.com/azure/purview/manage-kafka-dotnet)
![image_5](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/configure-kafka-event-hubs.png)
    > Note\
    >[These options can be configured after you have created your account](https://learn.microsoft.com/azure/purview/configure-event-hubs-for-kafka) in Kafka configuration under settings on your Microsoft Purview account page in the Azure Portal.
    ![image_6](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/select-kafka-configuration.png)
- Select *8Review & Create**, and then select **Create**. It takes a few minutes to complete the creation. The newly created account will appear in the list on your **Microsoft Purview accounts** page.
![image_7](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/create-resource.png)

### Open the Microsoft Purview governance portal

After your account is created, you'll use the Microsoft Purview governance portal to access and manage it. There are two ways to open the Microsoft Purview governance portal:
- Open your Microsoft Purview account in the Azure portal. Select the "Open Microsoft Purview governance portal" tile on the overview page.
![image_8](https://learn.microsoft.com/en-us/azure/purview/media/create-catalog-portal/open-purview-studio.png)
- Alternatively, you can browse to https://web.purview.azure.com, select your Microsoft Purview account name, and sign in to your workspace.

### **Relevant Videos**

<video>
   <src>https://www.youtube.com/watch?v=Kteh9cXkHIE</src>
   <title>How to get started with Azure Purview | Azure Tips and Tricks</title>
</video>


### Resources

- [What's available in the Microsoft Purview governance portal?
](https://learn.microsoft.com/azure/purview/overview?WT.mc_id=docs-azuredevtipsvideo-azureappsdev)
- [Use the Microsoft Purview governance portal
](https://learn.microsoft.com/azure/purview/use-microsoft-purview-governance-portal?WT.mc_id=docs-azuredevtipsvideo-azureappsdev)
- [Custom classifications in Microsoft Purview
](https://learn.microsoft.com/azure/purview/create-a-custom-classification-and-classification-rule?WT.mc_id=docs-azuredevtipsvideo-azureappsdev)
- [Check the required steps to connect your Azure Purview account to Synapse Studio](https://docs.microsoft.com/azure/synapse-analytics/catalog-and-governance/quickstart-connect-azure-purview)
- [Check how you can discover and explore data in Synapse using Azure Purview](https://docs.microsoft.com/azure/synapse-analytics/catalog-and-governance/how-to-discover-connect-analyze-azure-purview)
- [Check how you can configure your Azure Purview account to scan data under Synapse Dedicated SQL pools](https://docs.microsoft.com/azure/purview/register-scan-azure-synapse-analytics)
- [Connect to your Microsoft Purview and scan data sources privately and securely
](https://learn.microsoft.com/azure/purview/catalog-private-link-end-to-end)


### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>