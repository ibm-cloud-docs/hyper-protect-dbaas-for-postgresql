---

copyright:
  years: 2019
lastupdated: "2019-10-17"

keywords: database instance, DBaaS dashboard

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

# Managing database instances
{: #dbaas-webui-database-instances}

## Before you begin
{: #webui-database-instances-byb}

In the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select the **Instances** tab.

## Starting a database instance
{: #webui-start-database-instance}

1. Select a stopped database instance.
2. Click the three dots in the upper-right corner of the instance information pane, then select **Start**.

## Stopping a database instance
{: #webui-stop-database-instance}

1. Select a running database instance.
2. Click the three dots in the upper-right corner of the instance information pane, then select **Stop**. If it is a Primary node, you can also select **Force stop**.

## Restarting a database instance
{: #webui-restart-database-instance}

1. Select a running database instance.
2. Click the three dots in the upper-right corner of the instance information pane, then select **Restart**.

## Downloading logs
{: #webui-download-log}

The **Log Files** list is refreshed at intervals with updated timestamps. Two types of logs are available:

|Type of logs|Maximum retention time|
|-----------|-----------|
|postgresql.log|30 days|
|audit.log |90 days|
{: caption="Table 1. Type of logs"}

Logs will be deleted when they exceed the maximum retention time.

To download logs:

1. Select a database instance.

1. Select the database instance.
2. Select the **Start date** and **End date** to filter the logs by time.
3. Select the logs that you want to download and click the **Download** button.

## Checking instance status
{: #webui-check-instance-status}

The colored dot on the instance pane indicates the status of the database instance. You can refer to the following table to check the instance status.

|Color|Status|Action|
|-----|------|------|
|Green|The instance is running.|You can stop or restart the instance.|
|Yellow|The instance is stopped.|You can start the instance.|
|Red|The instance is failed.|You can refer to [Getting help and support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Table 1. The status color"}
