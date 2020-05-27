---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-03"

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
{: #dbaas-webui-database-monitor}

Unfortunately, monitoring is not available temporarily because {{site.data.keyword.cloud}} Monitoring with Grafana is withdrawn from service. [Monitoring with Sysdig](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-getting-started) will be available soon.
{: shortdesc}

<!--After you enable database monitoring, you can view the database metrics in the Grafana dashboard.
{: shortdesc}

## Prerequisites
{: #webui-database-monitoring-byb}

1.  Be sure to have access to a Cloud Foundry organization and space in the same region as your service instance.
    For information about how to obtain such access, see [Adding orgs and spaces](https://cloud.ibm.com/docs/account?topic=account-orgsspacesusers){: external}.

2.  Make sure that all nodes of the database cluster are running.

## Enabling database monitoring
{: #webui-enable-database-monitoring}

In the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Monitoring** in the side navigation pane. Complete the following steps to enable monitoring if you haven't:

1. Click **Enable**.
2. In the **Enable Monitoring** window, select your organization and space, then click **Submit**.

In Step 2, if you see an error message about failing to enable monitoring for certain nodes, it means one or more of your nodes are not running (see the [**HELP**](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-getting-help-and-support) section to troubleshoot). You can retry enabling monitoring for the nodes when they are running again.

## Viewing database metrics
{: #webui-view-database-metrics}

Click **View monitoring information in Grafana** on the **Monitoring** page.

To display the metrics in a new dashboard in Grafana, select the upper left Grafana icon, then select **Dashboards > New**. For more information, see [Configuring a metric query in Grafana](/docs/cloud-monitoring/retrieve-metrics?topic=cloud-monitoring-define_query).

It might take a while until your database cluster ID and node IDs are displayed, and you might have to reload the dashboard.

## Available metrics
{: #available-metrics}

The table describes all the available metrics for {{site.data.keyword.ihsdbaas_postgresql_full}}.

| Metric | Description|
|----------|-----------|
| `memory-percent-used` | How much percent of memory that your service instance is using. |
{: caption="Table 1. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} metrics" caption-side="top"}-->
