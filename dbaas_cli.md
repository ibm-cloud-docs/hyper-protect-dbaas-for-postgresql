---

copyright:
  years: 2019
lastupdated: "2019-08-28"

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


# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in
{: #dbaas_cli_plugin}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in to create, delete,
and display information about databases and users, to show details about clusters,
to start and stop instances, and to list and download log files.
{:shortdesc}


## Prerequisites
{: #prerequisites_dbaas_cli_plugin}

- Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started). {{site.data.keyword.cloud_notm}} CLI requires Java SDK 1.7.0. The prefix for running commands by using the {{site.data.keyword.cloud_notm}} CLI is `ibmcloud`. In the terminal, you are notified when updates to the `ibmcloud` CLI and plug-ins are available. Be sure to keep your CLI up-to-date so that you can use all the available commands and flags.

- Install the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI plug-in. You can see [Installing the DBaaS CLI plug-in](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin) for reference. If you want to view the current version of your {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
CLI plug-in, run `ibmcloud plugin show dbaas-cli`.


## CLI plug-in usage command
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

This command displays a list of DBaaS commands.

```
ibmcloud help dbaas
```
{: pre}


## Cluster command
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

This command shows the details of the specified cluster, including information about each replica member.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource. To find the resource name, use the {{site.data.keyword.cloud_notm}} command `ibmcloud resource service-instances`.</dd>
</dl>

## Database commands
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

This command creates a database and, optionally, a collection.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*database_name*</dt>
<dd>The name of the database to create.</dd>
<dt>*collection*</dt>
<dd>(Optional) The name of the collection to create.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

This command deletes a database. Do not delete a database if that database is created by credential and if that credential is still in use.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*database_name*</dt>
<dd>The name of the database to delete.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

This command lists all the databases on the given cluster.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
</dl>


## Database User commands
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

This command creates a database user.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*username*</dt>
<dd>The user name to be assigned to the database user being created.</dd>
<dt>*db_name*</dt>
<dd>(Optional) This specifies a database for which the user will have read and write access.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

This command deletes a database user. Do not delete a database user if that database user is created by credential and if that credential is still in use.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*username*</dt>
<dd>The user name of the database user being deleted.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

This command lists all the database users.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

This command shows details about a database user.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*username*</dt>
<dd>The user name of the database user being shown.</dd>
</dl>


## Instance commands
{: #instance_cmds}

To use any of the instance commands listed here, you need to know the `instance_id`. To obtain an `instance_id`, first use the following `ibmcloud` command to list the service instance resource group names under your account, then use [`cluster_show`](#cluster_show) command to get the `instance_id`.

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

This command restarts a running instance.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*instance_id*</dt>
<dd>The ID of the instance.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

This command starts a stopped instance.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*instance_id*</dt>
<dd>The ID of the instance.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

This command stops an instance (a replication member of the cluster).

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*instance_id*</dt>
<dd>The ID of the instance.</dd>
</dl>


## Log commands
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

This command downloads a log file from an instance.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*instance_id*</dt>
<dd>The ID of the instance.</dd>
<dt>*filename*</dt>
<dd>The name of the log file to download. To determine the file name of the log file you want to download, use the [ibmcloud dbaas logs-list](#log_list) command.</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

This command lists all the log files on an instance. You can use any of the listed file names as input to the [ibmcloud dbaas log-get](#log_get) command.

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Command options**

<dl>
<dt>*resource_name*</dt>
<dd>The name of the cluster resource.</dd>
<dt>*instance_id*</dt>
<dd>The ID of the instance.</dd>
</dl>
