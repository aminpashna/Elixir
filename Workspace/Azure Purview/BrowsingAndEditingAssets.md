# Azure Synapse Analytics Workspace / Azure Purview (Preview) / Browsing and editing assets

## Browse and edit assets

Searching a data catalog is a great tool for data discovery if a data consumer knows what they're looking for, but often users don't know exactly how their data estate is structured. The Microsoft Purview Data Catalog offers a browse experience that enables users to explore what data is available to them either by collection or through traversing the hierarchy of each data source in the catalog.

To access the browse experience, select "Browse assets" from the data catalog home page.
![image_1](https://learn.microsoft.com/azure/purview/media/how-to-browse-catalog/studio-home-page.png)

### **Browse by collection**

Browse by collection allows you to explore the different collections you're a data reader or curator for.

> Note\
> You will only see collections you have access to. For more information, see [Create and manage Collections](https://learn.microsoft.com/en-us/azure/purview/how-to-create-and-manage-collections).

![image_2](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/browse-by-collection.png)

Once a collection is selected, you'll get a list of assets in that collection with the facets and filters available in search. As a collection can have thousands of assets, browse uses the Microsoft Purview search relevance engine to boost the most important assets to the top.
![image_3](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/browse-collection-results.png)

For certain annotations, you can select the ellipses to choose between an AND condition or an OR condition.
![image_4](https://learn.microsoft.com/en-us/azure/purview/media/how-to-search-catalog/search-and-or-choice.png)

If the selected collection doesn’t contain the data you're looking for, you can easily navigate to related collections, or go back and view the entire collections tree.
![image_5](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/browse-collection-navigation.png)

Once you find the asset you're looking for, you can select it to view more details such as schema, lineage, and a detailed classification list. To learn more about the asset details page, see [Manage catalog assets](https://learn.microsoft.com/azure/purview/catalog-asset-details).
![image_6](https://learn.microsoft.com/en-us/azure/purview/media/how-to-search-catalog/search-view-asset.png)


### **Browse by source type**

Browse by source type allows data consumers to explore the hierarchies of data sources using an explorer view. Select a source type to see the list of scanned sources.

For example, you can easily find a dataset called DateDimension under a folder called Dimensions in Azure Data lake Storage Gen 2. You can use the 'Browse by source type' experience to navigate to the ADLS Gen 2 storage account, then browse to the service > container > folder(s) to reach the specific Dimensions folder and then see the DateDimension table.

A native browsing experience with hierarchical namespace is provided for each corresponding data source.

> Note\
> After a successful scoped scan, there may be delay before newly scanned assets appear in the browse experience.

1- On the Browse by source types page, tiles are categorized by data sources. To further explore assets in each data source, select the corresponding tile.
![image_7](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/browse-asset-types.png)

> Tip\
> Certain tiles are groupings of a collection of data sources. For example, the Azure Storage Account tile contains all Azure Blob Storage and Azure Data Lake Storage Gen2 accounts. The Azure SQL Server tile will display the Azure SQL Server assets that contain Azure SQL Database and Azure Dedicated SQL Pool instances ingested into the catalog.

2- On the next page, top-level assets under your chosen data type are listed. Pick one of the assets to further explore its contents. For example, after selecting "Azure SQL Database", you'll see a list of databases with assets in the data catalog.
![image_8](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/asset-type-specific-browse.png)

3- The explorer view will open. Start browsing by selecting the asset on the left panel. Child assets will be listed on the right panel of the page.
![image_9](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/explorer-view.png)

4- To view the details of an asset, select the name or the ellipses button on the far right.
![image_10](https://learn.microsoft.com/en-us/azure/purview/media/how-to-browse-catalog/view-asset-detail-click-ellipses-inline.png)



### Resources

- [Check the required steps to connect your Azure Purview account to Synapse Studio](https://docs.microsoft.com/azure/synapse-analytics/catalog-and-governance/quickstart-connect-azure-purview)
- [Check how you can discover and explore data in Synapse using Azure Purview](https://docs.microsoft.com/azure/synapse-analytics/catalog-and-governance/how-to-discover-connect-analyze-azure-purview)
- [Check how you can configure your Azure Purview account to scan data under Synapse Dedicated SQL pools](https://docs.microsoft.com/azure/purview/register-scan-azure-synapse-analytics)
- [Manage data assets in the Microsoft Purview Data Catalog](https://learn.microsoft.com/training/modules/manage-data-assets-in-microsoft-purview-data-catalog/)
- [Asset details page in the Microsoft Purview Data Catalog](https://learn.microsoft.com/azure/purview/catalog-asset-details)

### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>