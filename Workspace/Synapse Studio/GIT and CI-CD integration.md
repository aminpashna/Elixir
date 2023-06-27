# Azure Synapse Analytics Workspace / Synapse Studio / GIT and CI-CD integration

## Integrate GIT and CI/CD

Continuous integration (CI) is the process of automating the build and testing of code every time a team member commits a change to version control. Continuous delivery (CD) is the process of building, testing, configuring, and deploying from multiple testing or staging environments to a production environment.

In an Azure Synapse Analytics workspace, CI/CD moves all entities from one environment (development, test, production) to another environment. Promoting your workspace to another workspace is a two-part process. First, use an Azure Resource Manager template (ARM template) to create or update workspace resources (pools and workspace). Then, migrate artifacts like SQL scripts and notebooks, Spark job definitions, pipelines, datasets, and other artifacts by using Synapse Workspace Deployment tools in Azure DevOps or on GitHub.

[This](https://docs.microsoft.com/azure/synapse-analytics/cicd/continuous-integration-delivery) article outlines how to use an Azure DevOps release pipeline and GitHub Actions to automate the deployment of an Azure Synapse workspace to multiple environments.

### Automating the Publishing of Workspace Artifacts in Synapse CICD

Azure Synapse Studio is the primary tool to use to interact with the many components that exist in Azure Synapse Analytics, allowing you to perform a wide range of activities against your data and build a fully integrated analytics solution. Integrating Synapse Studio with a Source Control System such as [Azure DevOps Git](https://azure.microsoft.com/products/devops/?nav=min) or Github has been shown as one of Studio’s preferred features to leverage collaborative work and [source control.](https://docs.microsoft.com/azure/synapse-analytics/cicd/source-control)

Working collaboratively and tracking code changes in an integrated analytics platform that combines data warehousing, big data analytics, data integration, and visualization, can be quite challenging. Multidisciplinary teams, working in different projects/features, working in complex applicational lifecycles requiring agility and and…automation!

Follow the [link](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/automating-the-publishing-of-workspace-artifacts-in-synapse-cicd/ba-p/3603042) for more information.


### Recommended Steps

- [How to](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/how-to-use-ci-cd-integration-to-automate-the-deploy-of-a-synapse/ba-p/2248060) use CI/CD integration to automate the deploy of a Synapse Workspace to multiple environments
- Consider the [Best practices for CI/CD](https://docs.microsoft.com/azure/data-factory/continuous-integration-deployment#best-practices-for-cicd).
- Be aware of the [unsupported features list](https://docs.microsoft.com/azure/data-factory/continuous-integration-deployment#unsupported-features).
- By design, CI/CD publishing does not allow for cherry picking and/or selective publishing subset of changes. To publish individual changes into production environment, consider Hot fix or QFE.
- [Troubleshooting Git integration](https://docs.microsoft.com/azure/data-factory/source-control#troubleshooting-git-integration)
- [CI/CD in Azure Synapse Analytics](https://techcommunity.microsoft.com/t5/data-architecture-blog/ci-cd-in-azure-synapse-analytics-part-1/ba-p/1964172)


### Resources

- [Continuous integration and delivery](https://docs.microsoft.com/azure/data-factory/continuous-integration-deployment)



### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>