## TSG ID (to be included in SR Internal title if used)

## Keywords (optional)

[[_TOC_]]

## Background
Customer would like to know which URLs needs to be added to their firewall's allowed list for access through PrivateLink to web.azuresynapse.net

## Explanation

### What is Azure Private Link?
Azure Private Link enables you to access Azure PaaS Services (for example, Azure Storage and SQL Database) and Azure hosted customer-owned/partner services over a [private endpoint](https://learn.microsoft.com/azure/private-link/private-endpoint-overview) in your virtual network.

Traffic between your virtual network and the service travels the Microsoft backbone network. Exposing your service to the public internet is no longer necessary. You can create your own private link service in your virtual network and deliver it to your customers. Setup and consumption using Azure Private Link is consistent across Azure PaaS, customer-owned, and shared partner services.

> Azure Private Link is now generally available. Both Private Endpoint and Private Link service (service behind standard load balancer) are generally available. Different Azure PaaS will onboard to Azure Private Link at different schedules. See [Private Link availability](https://learn.microsoft.com/azure/private-link/availability) for an accurate status of Azure PaaS on Private Link. For known limitations, see [Private Endpoint](https://learn.microsoft.com/azure/private-link/private-endpoint-overview#limitations) and [Private Link Service](https://learn.microsoft.com/azure/private-link/private-link-service-overview#limitations).

![image_1](https://learn.microsoft.com/en-us/azure/private-link/media/private-link-overview/private-link-center.png)

### [Deploy and configure Azure Firewall using the Azure portal](https://learn.microsoft.com/azure/firewall/tutorial-firewall-deploy-portal)

## Mitigation

This is a basic list of required endpoint for synapse studio:\
https://management.azure.com\
https://login.microsoftonline.com\
https://dev.azure.com\
https://graph.microsoft.com\
https://{storageaccountName}.[blob|table|dfs].core.windows.net\
https://{workspaceName}.[dev|sql].azuresynapse.net\
https://aadcdn.msauth.net\
https://dc.services.visualstudio.com\
https://{workspaceName}-ondemand.sql.azuresynapse.net


## Related ICM/TSG/Work Item
https://portal.microsofticm.com/imp/v3/incidents/details/361193108/home


<div id='csswikifeedback-start'></div>
<br/>

**How good have you found this content?**

<div>
<span>
<a href='https://csswikifeedback.azurewebsites.net/feedback/smile?wiki=AzureSynapseAnalytics&pageId=286289&pageTitle=TSG Template&product=Synapse' target='_blank'>
<img alt='Smile' src='https://sqldbwikifeedback.blob.core.windows.net/assets/smile.png'>
</a>
</span>

<span>
<a href='https://csswikifeedback.azurewebsites.net/feedback/frown?wiki=AzureSynapseAnalytics&pageId=286289&pageTitle=TSG Template&product=Synapse' target='_blank'>
<img alt='Sad' src='https://sqldbwikifeedback.blob.core.windows.net/assets/sad.png'>
</a>
</span>
</div>
<div id='csswikifeedback-end'></div>
