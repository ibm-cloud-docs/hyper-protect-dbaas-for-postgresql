---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: node, DBaaS dashboard

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


# Viewing information about nodes
{: #nodes}

You can view your node status and download logs through the UI, CLI, and API. 
{: shortdesc}

## Checking node status
{: #check-node-status}

If a node is failed, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support). If your service instance is protected by an external key and the key is deleted or not connected, the nodes are stopped.

### Checking node status in the UI
{: #webui-check-node-status}
{: ui}

1. On the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select **Nodes** in the side navigation pane to view information about your nodes and download logs.

2. Select the primary node or a secondary node to check its ID and status.

### Checking node status from the CLI
{: #cli-check-node-status}
{: cli}

Use the [command](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#cluster_show) to show the details of the specified cluster, including information about each node. 

### Checking node status with the API
{: #api-check-node-status}
{: api}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-database-cluster-details) to show the details of the specified cluster, including information about each node. 

## Getting logs
{: #get-logs}

The **Log files** list is refreshed at intervals with updated time stamps. Two types of logs are available:

|Type of Logs|Maximum Retention Time|
|-----------|-----------|
|postgresql.log|30 days|
|audit.log |90 days|
{: caption="Table 1. Type of logs"}

Logs are deleted when they exceed the maximum retention time.

### Getting logs in the UI
{: #webui-download-logs}
{: ui}

To download logs in the UI:
1. Select a node.
2. Select the **Start date** and **End date** to filter the logs by time.
3. Select the logs that you want to download and click the download button.

### Getting logs from the CLI
{: cli-download-logs}
{: cli}

Use the [log commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#log-commands) to list and download logs.

### Getting logs with the API
{: api-download-logs}
{: api}

1. [List log files of a node.](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-database-log-files){: external}
2. [Get the content of the specified log.](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-log-details){: external}
