---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-07"

keywords: node, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:external: target="_blank" .external}
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}

# Viewing information about nodes
{: #nodes}

You can view your node status and download logs through the UI, CLI, and API. 
{: shortdesc}

## Checking node status
{: #check-node-status}

If a node is failed, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support). If your service instance is protected by an external key and the key is deleted or not connected, the nodes are stopped.

### Checking node status in the UI
{: #webui-check-node-status}
{: ui}

1. On the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Nodes** in the side navigation pane to view information about your nodes and download logs.

2. Select the primary node or a secondary node to check its ID and status.

### Checking node status from the CLI
{: #cli-check-node-status}
{: cli}

Use the [command](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#cluster_show) to show the details of the specified cluster, including information about each node. 

### Checking node status with the API
{: #api-check-node-status}
{: api}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-database-cluster-details) to show the details of the specified cluster, including information about each node. 

## Getting logs
{: #get-logs}

The **Log files** list is refreshed at intervals with updated time stamps. Two types of logs are available:

|Type of Logs|Maximum Retention Time|
|-----------|-----------|
|postgresql.log|30 days|
|audit.log |90 days|
{: caption="Table 1. Type of logs"}

Logs are deleted when they exceed the maximum retention time.

### Getting logs in the UI
{: #webui-download-logs}
{: ui}

To download logs in the UI:
1. Select a node.
2. Select the **Start date** and **End date** to filter the logs by time.
3. Select the logs that you want to download and click the download button.

### Getting logs from the CLI
{: cli-download-logs}
{: cli}

Use the [log commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#log-commands) to list and download logs.

### Getting logs with the API
{: api-download-logs}
{: api}

1. [List log files of a node.](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-database-log-files){: external}
2. [Get the content of the specified log.](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-log-details){: external}
