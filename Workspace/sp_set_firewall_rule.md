# sp_set_firewall_rule (Azure SQL Database)

## Learn about sp_set_firewall_rule in Azure SQL Database

This stored procedure creates or updates the server-level firewall settings for your SQL Database server and is only available in the primary database to the server-level principal sign-in or assigned Azure Active Directory (Azure AD) principal. Review the following guidance to learn more.
  
  
### Syntax  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
### Arguments  

The following table demonstrates the supported arguments and options in Azure SQL Database.
  
|Name|Datatype|Description|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR(128)**|The name used to describe and distinguish the server-level firewall setting. The value passed in must match this parameter's data type (NVARCHAR).|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR(50)**|The lowest IP address in the range of the server-level firewall setting. IP addresses equal to or greater than this can attempt to connect to the SQL Database server. The lowest possible IP address is `0.0.0.0`.|
|[@end_ip_address =] 'end_ip_address'|**VARCHAR(50)**|The highest IP address in the range of the server-level firewall setting. IP addresses equal to or less than this can attempt to connect to the SQL Database server. The highest possible IP address is `255.255.255.255`.<br /><br /> **Note**: Azure connection attempts are allowed when both this field and the *start_ip_address* field equals `0.0.0.0`.|  
  
### Remarks  

The names of server-level firewall settings must be unique. If the name of the setting provided for the stored procedure already exists in the firewall settings table, the starting and ending IP addresses will be updated. Otherwise, a new server-level firewall setting will be created.  
  
When you add a server-level firewall setting where the beginning and ending IP addresses are equal to `0.0.0.0`, you enable access to your SQL Database server from Azure. Provide a value to the *name* parameter that will help you remember what the server-level firewall setting is for.  
  
In SQL Database server, sign-in data required to authenticate a connection and server-level firewall rules are temporarily cached in each database. This cache is periodically refreshed. To force a refresh of the authentication cache and make sure that a database has the latest version of the logins table, run [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](https://learn.microsoft.com/sql/t-sql/database-console-commands/dbcc-flushauthcache-transact-sql?view=azuresqldb-current&viewFallbackFrom=azure-sqldw-latest).  
 
This is an extended stored procedure, so the data type of the value passed in for each parameter must match the parameter definition.
  
### Permissions  

Only the server-level principal sign-in created by the provisioning process or an Azure AD principal assigned as admin can create or modify server-level firewall rules. The user must be connected to the primary database to run `sp_set_firewall_rule`.  
  
### Examples  

The following code creates a server-level firewall setting called `Allow Azure` that enables access from Azure. Run the following in the virtual primary database.  
  
```  
-- Enable Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 The following code creates a server-level firewall setting called `Example setting 1` for only the IP address `0.0.0.2`. Then, the `sp_set_firewall_rule` stored procedure is called again to update the end IP address to `0.0.0.4`, in that firewall setting. This creates a range, which allows IP addresses `0.0.0.2`, `0.0.0.3`, and `0.0.0.4` to access the server.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
### Resources 
- [Azure SQL Database Firewall](https://learn.microsoft.com/en-us/azure/azure-sql/database/firewall-configure?view=azuresql)   
- [How to: Configure Firewall Settings (Azure SQL Database)](https://learn.microsoft.com/en-us/azure/azure-sql/database/firewall-configure?view=azuresql)   
- [sys.firewall_rules &#40;Azure SQL Database&#41;](https://learn.microsoft.com/en-us/sql/relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database?view=azuresqldb-current&viewFallbackFrom=azure-sqldw-latest)