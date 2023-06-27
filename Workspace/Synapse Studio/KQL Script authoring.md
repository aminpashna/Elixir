# Azure Synapse Analytics Workspace / Synapse Studio / KQL Script authoring

## Kusto Query Language (KQL) overview

Kusto Query Language is a powerful tool to explore your data and discover patterns, identify anomalies and outliers, create statistical modeling, and more. The query uses schema entities that are organized in a hierarchy similar to SQLs: databases, tables, and columns.

### What is a Kusto query?

There are three kinds of user [query statements](https://learn.microsoft.com/azure/data-explorer/kusto/query/statements?pivots=azuredataexplorer):

- A [tabular expression statement](https://learn.microsoft.com/azure/data-explorer/kusto/query/tabularexpressionstatements)
- A [let statement](https://learn.microsoft.com/azure/data-explorer/kusto/query/letstatement)
- A [set statement](https://learn.microsoft.com/azure/data-explorer/kusto/query/setstatement?pivots=azuredataexplorer)

All query statements are separated by a ```;``` (semicolon), and only affect the query at hand.

>Note\
>For information about application query statements, see [Application query statements](https://learn.microsoft.com/azure/data-explorer/kusto/query/statements?pivots=azuredataexplorer#application-query-statements).

The most common kind of query statement is a tabular expression statement, which means both its input and output consist of tables or tabular datasets. Tabular statements contain zero or more operators, each of which starts with a tabular input and returns a tabular output. Operators are sequenced by a ```|``` (pipe). Data flows, or is piped, from one operator to the next. The data is filtered or manipulated at each step and then fed into the following step.

It's like a funnel, where you start out with an entire data table. Each time the data passes through another operator, it's filtered, rearranged, or summarized. Because the piping of information from one operator to another is sequential, the query operator order is important, and can affect both results and performance. At the end of the funnel, you're left with a refined output.

Let's look at an example query:

```
StormEvents 
| where StartTime between (datetime(2007-11-01) .. datetime(2007-12-01))
| where State == "FLORIDA"  
| count 
```

[This](https://learn.microsoft.com/azure/data-explorer/kql-quick-reference) article shows you a list of functions and their descriptions to help get you started using Kusto Query Language.

### Query best practices

[Here](https://learn.microsoft.com/azure/data-explorer/kusto/query/best-practices) are several best practices to follow to make your query run faster.

### [**Azure Data Explorer documentation**](https://learn.microsoft.com/azure/data-explorer/)

Azure Data Explorer is a fast, fully managed data analytics service for real-time analysis on large volumes of data streaming from applications, websites, IoT devices, and more. You can use Azure Data Explorer to collect, store, and analyze diverse data to improve products, enhance customer experiences, monitor devices, and boost operations.



### Troubleshoot Data Explorer KQL script publishing issues

If you have a query failure, be sure to select the Data Explorer query failure topic in problem list. If you have publishing issues in Synapse Studio, our [troubleshooting guide](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio) will help you.

### Resources

* [Synapse Studio troubleshooting](https://docs.microsoft.com/azure/synapse-analytics/troubleshoot/troubleshoot-synapse-studio).

### Here are some relevant results from the web
<azureKB>
    <client>Portal</client>
</azureKB>