---

copyright:
  years: 2019
lastupdated: "2019-12-18"

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

# Viewing information about nodes
{: #dbaas-webui-nodes}

In the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Nodes** in the side navigation pane to view the information about your nodes and download logs.
{: shortdesc}

## Checking node status
{: #webui-check-node-status}

Select the primary node or a secondary node to check its ID, status, and replication lag. If your service instance is protected by an external key, you can also see the key status. If your key is deleted or not connected, the nodes are stopped.

The information on the page is read-only. To manage the nodes, use your database client. If a node is failed, see [Getting help and support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|

## Downloading logs
{: #webui-download-log}

The **Log Files** list is refreshed at intervals with updated time stamps. Two types of logs are available:

|Type of Logs|Maximum Retention Time|
|-----------|-----------|
|postgresql.log|30 days|
|audit.log |90 days|
{: caption="Table 1. Type of logs"}

Logs will be deleted when they exceed the maximum retention time.

To download logs:

1. Select a node
2. Select the **Start date** and **End date** to filter the logs by time.
3. Select the logs that you want to download and click **Download**.
