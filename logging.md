---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-07"

keywords: logs, logging, Log Analysis

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

# Logging for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #sendlogs}

When you use {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can forward your database logs and database audit logs to your chosen {{site.data.keyword.la_full_notm}} instance.
{: shortdesc}

{{site.data.keyword.loganalysisshort_notm}} integration is available for {{site.data.keyword.ihsdbaas_postgresql_full}} according to the following table.

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.loganalysisshort_notm}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Washington DC (us-east)` | `Washington DC (us-east)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Dallas (us-south)`
{: caption="Table 1. {{site.data.keyword.loganalysisshort_notm}} regions" caption-side="top"}

To receive logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in the same region, except for `Sydney (au-syd)`. For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in `Sydney (au-syd)`, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in `Dallas (us-south)`.

## Prerequisite
{: #logging-prerequisite}

To enable logging, all three nodes of the database cluster need to be running. If one or more nodes aren't running, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support). You can retry enabling logging for the nodes when they're running again.

## Add logging
{: #add-logging}

On the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Observability** in the side navigation pane. Complete the following steps to add logging.

1. In the **Logging** pane, select the checkbox to agree to sending logs to {{site.data.keyword.loganalysisshort_notm}} and click **Enable for logging**.

2. When you see the message that the service instance is enabled to send platform metrics, click **Add logging**.

   a. If you don't have a {{site.data.keyword.loganalysisshort_notm}} service instance, you'll be directed to the service creation page to create one. Select the same region as your service instance (if your service instance is in Sydney, select Dallas).
   
   b. If you already have a {{site.data.keyword.loganalysisshort_notm}} service instance in the same region but it isn't enabled to receive platform logs, you need to select the {{site.data.keyword.loganalysisshort_notm}} service instance to receive platform logs in the pop-up dialog box.

3. After you add a {{site.data.keyword.loganalysisshort_notm}} service instance, click **Launch logging** to be directed to the {{site.data.keyword.loganalysisshort_notm}} dashboard to view the logs.
  
Now you can view logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in the {{site.data.keyword.loganalysisshort_notm}} instance that is configured to receive platform logs. For detailed instructions on viewing logs, see [Viewing logs](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-view_logs).
