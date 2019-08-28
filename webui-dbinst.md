---

copyright:
  years: 2019
lastupdated: "2019-08-28"

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
2. Click the three dots at the right end of the line, then select **Start**.

## Stopping a database instance
{: #webui-stop-database-instance}

1. Select a running database instance.
2. Click the three dots at the right end of the line, then select **Stop**. If it is a Primary node, you can also select **Force stop**.

## Restarting a database instance
{: #webui-restart-database-instance}

1. Select a running database instance.
2. Click the three dots at the right end of the line, then select **Restart**.

## Downloading the log
{: #webui-download-log}

1. Select the database instance.
2. Select the **Start date** and **End date** to filter the logs by time.
3. Select the logs that you want to download by selecting the check box before the name of the log.
4. Click the **Download** button.

## Checking instance status
{: #webui-check-instance-status}

The colored dot on the instance pane indicates the status of the database instance. You can refer to the following table to check the instance status.

|Color|Status|Action|
|-----|------|------|
|Green|The instance is running.|You can stop or restart the instance.|
|Yellow|The instance is stopped.|You can start the instance.|
|Red|The instance is failed.|You can refer to [Getting help and support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Table 1. The status color"}
