---

copyright:
  years: 2019, 2021
lastupdated: "2021-05-18"

keywords: Activity tracker events

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


# Auditing events for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #activity-tracker-events}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.at_short}} service to track how users and applications interact with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.cloudaccesstrailshort}}](/docs/activity-tracker?topic=activity-tracker-getting-started).

## Viewing events
{: #view-activity-tracker-events}
{: help}
{: support}

To view events of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have an {{site.data.keyword.cloudaccesstrailshort}} instance in the same region, as the following table shows:

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.cloudaccesstrailshort}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Washington DC (us-east)` | `Washington DC (us-east)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Sydney (au-syd)`
{: caption="Table 1. {{site.data.keyword.cloudaccesstrailshort}} regions" caption-side="top"}

1. [Provision an {{site.data.keyword.cloudaccesstrailshort}} instance](/docs/activity-tracker?topic=activity-tracker-provision) if you don't have one. {{site.data.keyword.cloudaccesstrailshort}} can have only one instance per location.

2. To view events, access the web UI of the corresponding {{site.data.keyword.cloudaccesstrailshort}} instance. For detailed instructions, see [Launching the web UI through the {{site.data.keyword.cloud_notm}} UI](/docs/activity-tracker?topic=activity-tracker-launch#launch_cloud_ui). You can apply search and filtering criteria to define the events that are displayed through a [custom view](/docs/activity-tracker?topic=activity-tracker-views).

## List of events
{: #list-activity-tracker-events}

The following table lists the actions that generate an event:

| Action                 | Description                               |
| ---------------------- | ----------------------------------------- |
| `hyperp-dbaas-postgresql.cluster.create` | Create a database cluster |
| `hyperp-dbaas-postgresql.cluster.delete` | Delete a database cluster 
| `hyperp-dbaas-postgresql.log.get`       | Download a log file |
| `hyperp-dbaas-postgresql.logging.enable` | Enable logging for the cluster |
| `hyperp-dbaas-postgresql.monitoring.enable` | Enable monitoring for the cluster |
| `hyperp-dbaas-postgresql.cluster.resource.scale` | Scale cluster resources | 
| `hyperp-dbaas-postgresql.configuration.update` | Update PosgreSQL configuration settings |
| `hyperp-dbaas-postgresql.database.restore` | Restore databases by SRE as delegated by service instance owner |
{: caption="Table 1. Actions that generate {{site.data.keyword.cloudaccesstrailshort}} events"}

For the events of `hyperp-dbaas-postgresql.cluster.create` and `hyperp-dbaas-postgresql.cluster.delete`, the {{site.data.keyword.cloudaccesstrailshort}} service doesn't record the account name and IP address of the user who performs the action. The values of `initiator.name` and `host.address` in the log indicate the service ID of Cloud Broker and the IP address of Cloud Broker. For the event of `hyperp-dbaas-postgresql.database.restore`, the value of `initiator.name` is `dbaas.sre@de.ibm.com`.
{: note}
