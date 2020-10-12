---

copyright:
  years: 2019, 2020
lastupdated: "2020-10-13"

keywords: database monitoring, database cluster, database metrics

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

# Monitoring databases
{: #monitor}

Monitoring for {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} is provided through integration with [{{site.data.keyword.mon_full_notm}}](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-getting-started). Your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance forwards selected information so you can monitor its health and resource usage.
{: shortdesc}

{{site.data.keyword.mon_short}} integration is available for {{site.data.keyword.ihsdbaas_postgresql_full}} according to the following table.

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.mon_short}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Dallas (us-south)`
{: caption="Table 1. {{site.data.keyword.mon_short}} regions" caption-side="top"}

To view metrics of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have a {{site.data.keyword.mon_short}} service instance in the same region, except for `Sydney (au-syd)`. For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in `Sydney (au-syd)`, you need to have a {{site.data.keyword.mon_short}} instance in `Dallas (us-south)`.

## Prerequisite
{: #monitoring-prerequisite}

To enable monitoring, all three nodes of the database cluster need to be running. If one or more nodes aren't running, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support). You can retry enabling monitoring for the nodes when they're running again.

## Add monitoring
{: #add-monitoring}

In the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Observability** in the side navigation pane. Complete the following steps to add monitoring.

1. In the **Monitoring** Pane, select the checkbox to agree to sending metrics to {{site.data.keyword.mon_short}} and click **Enable for monitoring**.

2. When you see the message that the service instance is enabled to send platform metrics, click **Add monitoring**.
  
   a. If you don't have a {{site.data.keyword.mon_short}} service instance, you'll be directed to the service creation page to create one. Select the same region as your service instance (if your service instance is in Sydney, select Dallas). For **platform metrics**, leave the **Enable** option selected.
   
   b. If you already have a {{site.data.keyword.mon_short}} service instance in the same region but it isn't enabled to receive platform metrics, you need to select the Sysdig service instance to receive platform metrics in the pop-up dialog box.

3. After you add a {{site.data.keyword.mon_short}} service instance, click **Launch monitoring** to be directed to the {{site.data.keyword.mon_short}} dashboard to view the metrics.

## Available metrics
{: #available-metrics}

The table describes all the available metrics for {{site.data.keyword.ihsdbaas_postgresql_full}}.

| Metric | Description|
|----------|-----------|
| CPU utilization | The vaule of CPU utilization measured in percentage. |
| Memory utilization | The vaule of memory utilization measured in percentage. |
| File system usage information | The vaule of file system usage information measured in percentage. |
{: caption="Table 1. {{site.data.keyword.ihsdbaas_postgresql_full}} metrics" caption-side="top"}
