# Resolve errors for request disallowed by policy

This article describes the cause of the `RequestDisallowedByPolicy` error and provides a solution for the error. The request disallowed by policy error can occur when you deploy resources with an Azure Resource Manager template (ARM template) or Bicep file.

## Symptom

During a deployment, you might receive a `RequestDisallowedByPolicy` error that prevents you from creating a resource. Azure CLI, Azure PowerShell, and the Azure portal's activity log show similar information about the error. The key elements are the error code, policy assignment, and policy definition.

```
"statusMessage": "{"error":{"code":"RequestDisallowedByPolicy", "target":"examplenic1207",
  "message":"Resource `examplenic1207` was disallowed by policy. Policy identifiers:

"policyAssignment":{"name":"Network interfaces should not have public IPs",
  "id":"/subscriptions/{guid}/providers/Microsoft.Authorization/policyAssignments/1111aa2222bb3333cc4444dd"}

"policyDefinition":{"name":"Network interfaces should not have public IPs",
  "id":"/subscriptions/{guid}/providers/Microsoft.Authorization/policyDefinitions/83a86a26-fd1f-447c-b59d-e51f44264114"}
```

In the `id` string, the `{guid}` placeholder represents an Azure subscription ID. The name of a `policyAssignment` or `policyDefinition` is the last segment of the `id` string.

### Cause

In this example, the error occurred when an administrator attempted to create a network interface with a public IP address. A policy assignment enables enforcement of a built-in policy definition that prevents public IPs on network interfaces.

You can use the name of a policy assignment or policy definition to get more details about a policy that caused the error. The example commands use placeholders for input. For example, replace `<policy definition name>` including the angle brackets, with the definition name from your error message.

### [Azure CLI](#tab/azure-cli)

To get more information about a policy definition, use [az policy definition show](https://learn.microsoft.com/cli/azure/policy/definition?view=azure-cli-latest#az-policy-definition-show).

```
defname=<policy definition name>
az policy definition show --name $defname
```

To get more information about a policy assignment, use [az policy assignment show](https://learn.microsoft.com/cli/azure/policy/assignment?view=azure-cli-latest#az-policy-assignment-show).

```
rg=<resource group name>
assignmentname=<policy assignment name>
az policy assignment show --name $assignmentname --resource-group $rg
```

### [PowerShell](#tab/azure-powershell)

To get more information about a policy definition, use [Get-AzPolicyDefinition](https://learn.microsoft.com/powershell/module/az.resources/get-azpolicydefinition?view=azps-10.0.0).

The `ConvertTo-Json` cmdlet has a `Depth` parameter that expands the output and the default value is 2. For more information, see [ConvertTo-Json](https://learn.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.3).

```
$subid = (Get-AzContext).Subscription.Id
$defname = "<policy definition name>"
(Get-AzPolicyDefinition -Id "/subscriptions/$subid/providers/Microsoft.Authorization/policyDefinitions") |
  Where-Object -Property Name -EQ -Value $defname |
    ConvertTo-Json -Depth 10
```

To get more information about a policy assignment, use [Get-AzPolicyAssignment](https://learn.microsoft.com/powershell/module/az.resources/get-azpolicyassignment?view=azps-10.0.0).

```
$rg = Get-AzResourceGroup -Name "<resource group name>"
$assignmentname = "<policy assignment name>"
Get-AzPolicyAssignment -Name $assignmentname -Scope $rg.ResourceId | ConvertTo-Json -Depth 5
```

---

### Solution

For security or compliance, your subscription administrators might assign policies that limit how resources are deployed. For example, policies that prevent creating public IP addresses, network security groups, user-defined routes, or route tables.

To resolve `RequestDisallowedByPolicy` errors, review the resource policies and determine how to deploy resources that comply with those policies. The error message displays the names of the policy definition and policy assignment.


### Resources

- [What is Azure Policy?](https://learn.microsoft.com/azure/governance/policy/overview)
- [Tutorial: Create and manage policies to enforce compliance](https://learn.microsoft.com/azure/governance/policy/tutorials/create-and-manage)
- [Azure Policy built-in policy definitions](https://learn.microsoft.com/azure/governance/policy/samples/built-in-policies)



### **Here are some relevant results from the web**
<azureKB>
    <client>Portal</client>
</azureKB>