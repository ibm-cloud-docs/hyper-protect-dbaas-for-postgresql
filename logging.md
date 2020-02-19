---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-07"

keywords: logs, logging, Log Analysis, LogDNA

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

# Sending logs to {{site.data.keyword.la_full_notm}}
{: #sendlogs}

When you use {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can forward your database logs and database audit logs to your designated {{site.data.keyword.la_full_notm}} instance.
{: shortdesc}

## Prerequisite
{: #logging-prerequisite}

You need to create and configure a {{site.data.keyword.loganalysisshort_notm}} instance to receive platform service logs. For more information about configuring a {{site.data.keyword.loganalysisshort_notm}} instance, see [Configuring {{site.data.keyword.cloud_notm}} service logs](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-config_svc_logs){: external}.

{{site.data.keyword.loganalysisshort_notm}} integration is available for {{site.data.keyword.ihsdbaas_postgresql_full}} deployments according to the following table.

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.loganalysisshort_notm}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Dallas (us-south)`
{: caption="Table 1. {{site.data.keyword.loganalysisshort_notm}} regions" caption-side="top"}

To receive logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in the same region, except for `Sydney (au-syd)`. For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in `Sydney (au-syd)`, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in `Dallas (us-south)`.

## Steps
{: #view-log-steps}

1. In the service instance dashboard of {{site.data.keyword.ihsdbaas_postgresql_full}}, select **Logging** in the side navigation pane and click **Enable**.
2. Click **View logs in LogDNA** to be directed to the {{site.data.keyword.loganalysisshort_notm}} instance list.

In Step 2, if you see an error message about failing to enable logging for certain nodes under the logging link, it means one or more of your nodes are not running (see the [ **HELP**](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support) section to troubleshoot). You can retry enabling logging for the nodes when they are running again.

Now you can view logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in the {{site.data.keyword.loganalysisshort_notm}} instance that is configured to receive platform service logs. For detailed instructions on viewing logs, see [Viewing logs](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-view_logs).
