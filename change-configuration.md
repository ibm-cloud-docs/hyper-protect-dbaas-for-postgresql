---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-13"

keywords: customize configuration, change configuration, configuration parameters

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


# Changing the PostgreSQL configuration
{: #changing-configuration}

In {{site.data.keyword.ihsdbaas_postgresql_full}}, with the Manager role, you can change some of the PosgreSQL configuration settings of your service instance to tune your PostgreSQL databases to your use case.
{: shortdesc}

The database admins or users with the [Manager role](#changing-configuration-prerequisite) can update the available configuration parameters with the [CLI](#changing-configuration-cli) or [API](#changing-configuration-api). The configuration is defined in a schema. To make a change, you send a JSON object with the settings and their new values to the CLI or the API.

If a request to change configuration settings fails, the {{site.data.keyword.ihsdbaas_postgresql_full}} SRE team will be notified automatically. You can also use the [task commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#task-cmds) or the [API request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-tasks){: external} to view the request status.

Some configuration changes require a restart to the primary and secondary nodes. The secondary nodes are restarted first, then the primary node. You can find the `requires_restart` information in [Available configuration settings](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration#available-config-settings).
{: note}

## Prerequisite
{: #changing-configuration-prerequisite}

You need to have the **Manager** role to change configuration settings, as defined in the [IAM service access roles table](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#service-access-roles). To assign access, see [Managing IAM access for users or services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#manage-access).

Updating `max_connections` and `max_locks_per_transaction` with one command/API request is only feasible when you make the values both larger or smaller. If you need to make one larger and the other smaller, you need to run two commands/API requests, updating one setting at a time.
{: important}

## Using the CLI
{: #changing-configuration-cli}

You can check the current configuration of your service instance with the following command.
```
ibmcloud dbaas configuration-show <resource_name>
```
{: codeblock}

To change your configuration through the CLI, use the following command.
```
ibmcloud dbaas configuration-update <resource_name> [@JSON_FILE | JSON_STRING]
```
{: codeblock}

The command reads the changes that you would like to make from the JSON file or string. For more information about formatting `JSON_FILE` or `JSON_STRING`, see the [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db-config-update).

You can run the following commands to check the request status of configuration changes.
```
ibmcloud dbaas tasks-list <resource_name>
ibmcloud dbaas task-show <resource_name> <task_id>
```
{: codeblock}

## Using the API
{: #changing-configuration-api}

Two API requests are available, one for viewing the current configuration and one for changing the configuration:

1. To view the configuration schema, use the [API request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-configuration){: external}.
2. To change the configuration, specify the settings as a JSON object in the [request to update configuration](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#update-configuration){: external}. You can use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-tasks){: external} to check the task status.

## Available configuration settings
{: #available-config-settings}


[`shared_buffers`](https://www.postgresql.org/docs/10/runtime-config-resource.html#GUC-SHARED-BUFFERS){: external}
  - Default - `128` (MB)
  - Restarts database? - **Yes**
  - Note - Shared memory buffers that the server use. The memory allocation for `shared_buffers` can't excceed 40% of the service instance's RAM. Setting `shared_buffers` any higher can result in memory issues that cause the database to crash. Setting `shared_buffers` equal, close to equal, or higher than the amount of allocated memory prevents the database from starting. 


[`max_locks_per_transaction`](https://www.postgresql.org/docs/10/runtime-config-locks.html){: external}
  - Default - `64`
  - Restarts database? - **Yes**
  - Note - The setting controls the average number of object locks allocated for each transaction. It's recommended to leave this setting at the default. Increase it only if you have queries that touch many different tables in a single transaction.


[`deadlock_timeout`](https://www.postgresql.org/docs/10/runtime-config-locks.html){: external}
  - Default - `1000`
  - Restarts database? - **No**
  - Options - Minimum value of 100
  - Note - The number of milliseconds to wait before checking for deadlock and the duration where lock waits are logged. Logs available through the logging integration. Setting this number too low negatively impacts performance.

[`max_connections`](https://www.postgresql.org/docs/10/runtime-config-connection.html#GUC-MAX-CONNECTIONS){: external}
  - Default - `115`
  - Restarts database? - **Yes**
  - Note: The maximum number of concurrent connections to the database server allowed. The value of `max_connections` depends on the resource of your cluster. If you set it too high, your cluster might become unhealthy.