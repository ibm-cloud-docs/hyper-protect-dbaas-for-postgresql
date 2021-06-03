---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Monitoring metrics for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #monitor}

Monitoring for {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} is provided through integration with [{{site.data.keyword.mon_full_notm}}](/docs/monitoring?topic=monitoring-getting-started). Your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance forwards selected information so you can monitor its health and resource usage.
{: shortdesc}

{{site.data.keyword.mon_short}} integration is available for {{site.data.keyword.ihsdbaas_postgresql_full}} according to the following table.

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.mon_short}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Washington DC (us-east)` | `Washington DC (us-east)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Sydney (au-syd)`
{: caption="Table 1. {{site.data.keyword.mon_short}} regions" caption-side="top"}

To view metrics of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have a {{site.data.keyword.mon_short}} service instance in the same region.

## Prerequisite
{: #monitoring-prerequisite}

To enable monitoring, all three nodes of the database cluster need to be running. If one or more nodes aren't running, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support). You can retry enabling monitoring for the nodes when they're running again.

## Add monitoring
{: #add-monitoring}

On the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Observability** in the side navigation pane. Complete the following steps to add monitoring.

1. In the **Monitoring** Pane, select the checkbox to agree to sending metrics to {{site.data.keyword.mon_short}} and click **Enable for monitoring**.

2. When you see the message that the service instance is enabled to send platform metrics, click **Add monitoring**.
  
   a. If you don't have a {{site.data.keyword.mon_short}} service instance, you'll be directed to the service creation page to create one. Select the same region as your service instance. For **platform metrics**, leave the **Enable** option selected.
   
   b. If you already have a {{site.data.keyword.mon_short}} service instance in the same region but it isn't enabled to receive platform metrics, you need to select the {{site.data.keyword.mon_short}} service instance to receive platform metrics in the pop-up dialog box.

3. After you add a {{site.data.keyword.mon_short}} service instance, click **Launch monitoring** to be directed to the {{site.data.keyword.mon_short}} dashboard to view the metrics. For more information about using the {{site.data.keyword.mon_short}} dashboard and configuring alerts, see the [Getting started tutorial](/docs/monitoring?topic=monitoring-getting-started-monitor#getting-started-monitor_step5).

## Available metrics
{: #available-metrics}

The table describes all the available metrics for {{site.data.keyword.ihsdbaas_postgresql_full}}.

| Metric | Description|
|----------|-----------|
| CPU Idle Percentage | CPU idle states measured in percentage |
| Memory Usage | Memory usage measured in percentage |
| Database Disk Usage | Disk usage measured in percentage |
{: caption="Table 1. {{site.data.keyword.ihsdbaas_postgresql_full}} metrics" caption-side="top"}

If you need to view all metrics of your databases, use any other monitoring tools that you prefer to connect to your databases. For more information, see [Monitoring](https://wiki.postgresql.org/wiki/Monitoring){: external}.
{: note}
