---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: instance commands, cluster resource, dbaas cli plugin reference

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


# {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in
{: #dbaas_cli_plugin}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in to get information about your cluster, databases, users, and nodes, and to list and download log files.
{: shortdesc}

## Prerequisites
{: #prerequisites_dbaas_cli_plugin}

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started). {{site.data.keyword.cloud_notm}} CLI requires Java SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you're notified when updates to the `ibmcloud` CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

2. Install the [DBaaS CLI plug-in](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin#dbaas_cli_instr). If you want to view the current version of your DBaaS CLI plug-in, run `ibmcloud plugin show dbaas-cli`.

## CLI plug-in usage command
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

This command displays a list of DBaaS commands.

```
ibmcloud help dbaas
```
{: pre}

## Cluster commands
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

This command shows the details of the specified cluster, including information about each node. 

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster. To find the resource name, use the {{site.data.keyword.cloud_notm}} command `ibmcloud resource service-instances`.

### `ibmcloud dbaas resource-scale`
{: #resource-scale}

This command scales the cluster resources (disk, RAM, or vCPU). For the valid value range, see the [value table](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling#before-scaling).

```
ibmcloud dbaas resource-scale <resource_name> [--cpu <value>] [--memory <value>] [--storage <value>] [--force]
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

- *--cpu <value>*

  Total number of dedicated CPU cores.
    
- *--memory <value>*

  Total memory allocation in GiB. For example, `--memory 4`.

- *--storage <value>*

  Total storage allocation in GiB. For example, `--storage 10`.
    
- *--force* (optional)

  Force scaling without the `y/N` confirmation.

## Database command
{: #db_cmds}

### `ibmcloud dbaas databases-list`
{: #db_list}

This command lists all the databases on the cluster.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

## Database configuration commands
{: #db-config-cmds}

### `ibmcloud dbaas configuration-show`
{: #db-config-show}

This command shows database configuration details.

```
ibmcloud dbaas configuration-show <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

### `ibmcloud dbaas configuration-update`
{: #db-config-update}

This command sends changes from the JSON file or JSON string to update the database configuration.

```
ibmcloud dbaas configuration-update <resource_name> [@JSON_FILE | JSON_STRING]
```
{: pre}

**Command options**

The [configuration parameters](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration#available-config-settings) are all integers. Don't specify the unit in the JSON file or string.
{: note}

- *resource_name*

  The name of the cluster.

- *@JSON_FILE*

  The JSON file that contains the database configuration. For example:
  ```
  ibmcloud dbaas configuration-update MyDBaaSIns03 @./conf.json
  ```
  {: codeblock}

  Content in the JSON file:
  ```
  {
	  "configuration":{
	  	"max_locks_per_transaction":150,
          "deadlock_timeout":1500,
	  	"shared_buffers":256,
          "max_connections":115

  	}
  }
  ```
  {: codeblock}

  If you want to update only one of the settings, you can just specify the one setting that you want to update in the file. For example:
  ```
  {
      "configuration":{
          "max_locks_per_transaction":150
      }
  }
  ```
  {: codeblock}

- *JSON_STRING*

  The parameter changes to send to the JSON file. For example, `'{"configuration":{"max_locks_per_transaction":150}}'` (for Windows, use `"{\"configuration\": {\"max_locks_per_transaction\": 150}}"`).

## Database user commands
{: #user_cmds}

### `ibmcloud dbaas users-list`
{: #user_list}

This command lists all the database users.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

### `ibmcloud dbaas user-show`
{: #user_show}

This command shows details about a database user.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

- *username*

  The user name of the database user.

## Node command
{: #node_cmds}

To view the information about each node, use the [`cluster_show`](#cluster_show) command.

## Log commands
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

This command downloads a log file from a node.

```
ibmcloud dbaas log-get <resource_name> <node_id> <filename>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

- *node_id*

  The ID of the node.

- *filename*

  The name of the log file to download. To determine the file name of the log file you want to download, use the [ibmcloud dbaas logs-list](#log_list) command.

### `ibmcloud dbaas logs-list`
{: #log_list}

This command lists all the log files on a node. You can use any of the listed file names as input to the [ibmcloud dbaas log-get](#log_get) command.

```
ibmcloud dbaas logs-list <resource_name> <node_id>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

- *node_id*

  The ID of the node.

## Task commands
{: #task-cmds}

### `ibmcloud dbaas tasks-list`
{: #tasks-list}

This command lists all the tasks that are running or recently run on a cluster.

```
ibmcloud dbaas tasks-list <resource_name>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

### `ibmcloud dbaas task-show`
{: #task-show}

This command shows details about a task.

```
ibmcloud dbaas task-show <resource_name> <task_id>
```
{: pre}

**Command options**

- *resource_name*

  The name of the cluster.

- *task_id*

  The ID of the task.
