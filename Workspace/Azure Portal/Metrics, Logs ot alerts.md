# Azure Synapse Analytics Workspace / Azure Portal / Metrics, Logs or alerts

## Learn about monitoring, metrics, and alerts in Azure Synapse Analytics

Azure Monitor helps you maximize the availability and performance of your applications and services. It delivers a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. This information helps you understand how your applications are performing and proactively identify issues that affect them and the resources they depend on.

A few examples of what you can do with Azure Monitor include:

- Detect and diagnose issues across applications and dependencies with [Application Insights](https://learn.microsoft.com/azure/azure-monitor/app/app-insights-overview?tabs=net).
- Correlate infrastructure issues with [VM insights](https://learn.microsoft.com/azure/azure-monitor/vm/vminsights-overview) and [Container insights](https://learn.microsoft.com/azure/azure-monitor/containers/container-insights-overview).
- Drill into your monitoring data with [Log Analytics](https://learn.microsoft.com/azure/azure-monitor/logs/log-query-overview) for troubleshooting and deep diagnostics.
- Support operations at scale with [automated actions](https://learn.microsoft.com/azure/azure-monitor/alerts/alerts-processing-rules?tabs=portal).
- Create visualizations with Azure [dashboards](https://learn.microsoft.com/azure/azure-monitor/visualize/tutorial-logs-dashboards) and [workbooks](https://learn.microsoft.com/azure/azure-monitor/visualize/workbooks-overview).
- Collect data from [monitored resources](https://learn.microsoft.com/azure/azure-monitor/monitor-reference) by using [Azure Monitor Metrics](https://learn.microsoft.com/azure/azure-monitor/essentials/data-platform-metrics).
- Investigate change data for routine monitoring or for triaging incidents by using [Change Analysis](https://learn.microsoft.com/azure/azure-monitor/change/change-analysis).

> **Note**\
This service supports [Azure Lighthouse](https://learn.microsoft.com/azure/lighthouse/overview), which lets service providers sign in to their own tenant to manage subscriptions and resource groups that customers have delegated.

### Overview
The following diagram gives a high-level view of Azure Monitor.

- The stores for the [data platform](https://learn.microsoft.com/azure/azure-monitor/data-platform) are at the center of the diagram. Azure Monitor stores these fundamental types of data: metrics, logs, traces, and changes.
- The [sources of monitoring data](https://learn.microsoft.com/azure/azure-monitor/data-sources) that populate these data stores are on the left.
- The different functions that Azure Monitor performs with this collected data are on the right. This includes such actions as analysis, alerting.
- At the bottom is a layer of integration pieces. These are actually integrated throughout other parts of the diagram, but that is too complex to show visually.

![monitor](https://learn.microsoft.com/azure/azure-monitor/media/overview/azure-monitor-overview-2022_10_15-add-prometheus-opt.svg#lightbox)



Use the following guidance to learn best practices for monitoring your workload.

### Guidance and best practices

Learn how to [use the Azure portal to monitor your workload](https://docs.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-monitor-workload-portal), which includes setting up Azure Monitor logs to investigate query execution and workload trends using log analytics for [Synapse SQL](https://azure.microsoft.com/blog/workload-insights-with-sql-data-warehouse-delivered-through-azure-monitor-diagnostic-logs-pass/).

### Resources

- [Manageability and monitoring with Synapse Dedicated SQL pool](https://docs.microsoft.com/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-manageability-monitoring?toc=/azure/synapse-analytics/toc.json&bc=/azure/synapse-analytics/breadcrumb/toc.json)
- [Monitor your Apache Spark applications](https://docs.microsoft.com/azure/synapse-analytics/monitoring/how-to-monitor-spark-applications#accessing-the-list-of-spark-applications)
- [Monitor your workspace pipeline runs](https://docs.microsoft.com/azure/synapse-analytics/monitoring/how-to-monitor-pipeline-runs)
- Information about SQL requests/queries in an Azure Synapse dedicated SQL pool. [SynapseSqlPoolExecRequests](https://docs.microsoft.com/azure/azure-monitor/reference/tables/synapsesqlpoolexecrequests)


### Relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>