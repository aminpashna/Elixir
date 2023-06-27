
## Background

Customer was trying to deploy synapse artifacts from managed vnet workspace to shared workspace using Azure DevOps Pipeline. 

## Symptom

While running this ADO pipeline, customer received following error:  Updating property managedVirtualNetwork is not supported.

![image.png](https://supportability.visualstudio.com/1e7c700d-94b1-4840-8da5-a82f1ddd9692/_apis/git/repositories/a169f6d4-cbee-4c92-bccc-80747080ff43/Items?path=/AzureSynapseAnalytics/.attachments/image-b582971d-fcc5-427f-83a4-4e4c973670c0.png&download=false&resolveLfs=true&%24format=octetStream&api-version=5.0-preview.1&sanitize=true&versionDescriptor.version=master)

## Mitigation:
Currently (as of Oct-2022) it is not supported using synapse deployment extension to move resources from a managed VNET workspace to a non-managed VNET workspace and error doesn't represent a clear explanation of what is happening. IR in vnet enabled workspace has an attribute which throws 400 if deployed on workspace without managed vnet.  It only supports skipping MPE no other artifact. Hence, to mitigate this issue, customer should make sure both source and target workspace should have similar VNETs configured/unconfigured.

Also, there is one more workaround suggested by PG to mitigate this issue. Customer can manually try to remove following managed vnet property from TemplateForWorkspace.json:

```
"managedVirtualNetwork": 
    {
        "type": "ManagedVirtualNetworkReference",
        "referenceName": "default"
    }
```

And after removing this code from template, you can deploy synapse artifacts from managed vnet workspace to non-managed vnet workspace as well. But it is not a recommended practice/feasible solution to make manual changes to the template file before running ADO pipeline, because this can lead to unexpected behavior. Customers should consider moving from an MVNET workspace to shared VNET workspace to be an unsupported scenario.



## Related ICM:
https://portal.microsofticm.com/imp/v3/incidents/details/335250444/home


## Public Docs:
- [ARM template deployment failing with error DataFactoryPropertyUpdateNotSupported](https://learn.microsoft.com/en-us/azure/data-factory/ci-cd-github-troubleshoot-guide#arm-template-deployment-failing-with-error-datafactorypropertyupdatenotsupported)
- [Use the Synapse workspace deployment task to deploy Synapse artifacts](https://learn.microsoft.com/en-us/azure/synapse-analytics/cicd/continuous-integration-delivery#troubleshoot-artifacts-deployment)