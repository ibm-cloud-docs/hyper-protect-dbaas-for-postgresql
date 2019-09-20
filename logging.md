---

copyright:
  years: 2019
lastupdated: "2019-09-23"

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
{: #prerequisite}

You need to create and configure a {{site.data.keyword.loganalysisshort_notm}} instance to receive platform service logs. For more information about configuring a {{site.data.keyword.loganalysisshort_notm}} instance, see [Configuring {{site.data.keyword.cloud_notm}} service logs](/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-config_svc_logs){: external}.

For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in Dallas or Frankfurt, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in the same region as your {{site.data.keyword.ihsdbaas_postgresql_full}} instance. For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in Sydney, you need to have a {{site.data.keyword.loganalysisshort_notm}} instance in Dallas.
{: note}

##Steps
{: #steps}

1. In the service instance dashboard of {{site.data.keyword.ihsdbaas_postgresql_full}}, select the **Logging** tab and click the **Enable** button.
2. Click **View in logdna** to be directed to the {{site.data.keyword.loganalysisshort_notm}} instance list.

In Step 2, if you see an error message about failing to enable logging for certain instance(s) under the logging link, it means one or more of your database instances are not running (see the [ **HELP**](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support) section to troubleshoot). You can retry enabling logging for the instance(s) when they are running again.

Now you can view logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance in the {{site.data.keyword.loganalysisshort_notm}} instance that is configured to receive platform service logs. For detailed instructions on viewing logs, see [Viewing logs](/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-view_logs)
