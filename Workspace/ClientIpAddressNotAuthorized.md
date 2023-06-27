# ClientIpAddressNotAuthorized

## What is **ClientIpAddressNotAuthorized** error

The ```ClientIpAddressNotAuthorized``` error in Azure Synapse Analytics Workspace occurs when the IP address of the client attempting to access the workspace is **not** authorized. This can happen if the IP address is **not** included in the firewall settings or virtual network service endpoint configurations. 

### **How to fix it?**

Here are the steps to fix the ```ClientIpAddressNotAuthorized``` error in Azure Synapse Analytics Workspace:

- Check the firewall settings for your Azure Synapse Analytics workspace, and make sure the IP address of the client attempting to access the workspace is included in the firewall's allowed list. You can do this by going to the Azure portal, navigating to your Synapse workspace, and selecting **Firewalls and virtual networks** under the **Security + networking** heading. For more information, see [Configure IP firewall rules using the Azure portal](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-ip-firewall#configure-ip-firewall-rules-using-the-azure-portal).
- If you have configured virtual network service endpoints for your Synapse workspace, ensure that the subnet used by the client is properly configured to allow traffic to the workspace. For more information, see [Virtual network service endpoints for Azure Synapse Analytics](https://learn.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview).
- If the client is **not** in the allowed list of IPs or subnets, **add** it to the list, and **save** the changes.
- You may also need to review and update your virtual network configurations to ensure that traffic from the client is correctly routed to the Synapse workspace. For more information, see [Configure a virtual network for a Synapse workspace](https://learn.microsoft.com/azure/synapse-analytics/security/synapse-workspace-managed-vnet).


### **How to prevent this?**

Here are some steps to prevent the ```ClientIpAddressNotAuthorized``` error from occurring in Azure Synapse Analytics Workspace:

- Maintain an up-to-date list of allowed IP addresses and subnets in the firewall settings of your Azure Synapse Analytics workspace. Regularly review and update the list to ensure that all clients that need access to the workspace are included.
- If you are using virtual network service endpoints, ensure that the subnets used by clients are properly configured to allow traffic to the Synapse workspace. Regularly review and update your virtual network configurations to ensure that they are correctly routing traffic from clients to the workspace.
- Consider implementing a process for adding new client IP addresses or subnets to the allowed list, such as a request and approval process. This can help ensure that new clients are properly authorized before attempting to access the workspace.
- Regularly monitor access logs and alerts to detect and respond to any unauthorized access attempts.


### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>