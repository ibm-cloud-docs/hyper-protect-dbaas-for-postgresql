---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-23"

keywords: instance commands, cluster resource, CLI plugin

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in
{: #dbaas_cli_plugin}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in to get information about your cluster, databases, users, and nodes, and to list and download log files.
{: shortdesc}

## Prerequisites
{: #prerequisites_dbaas_cli_plugin}

- Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started). {{site.data.keyword.cloud_notm}} CLI requires Java SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you're notified when updates to the `ibmcloud` CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

- Install the [DBaaS CLI plug-in](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin#dbaas_cli_instr). If you want to view the current version of your DBaaS CLI plug-in, run `ibmcloud plugin show dbaas-cli`.

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

  Total memory allocation in GB. For example, `--memory 4`.

- *--storage <value>*

  Total storage allocation in GB. For example, `--storage 10`.
    
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
