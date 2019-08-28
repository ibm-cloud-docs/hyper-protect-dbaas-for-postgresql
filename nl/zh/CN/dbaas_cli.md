---

copyright:
  years: 2019
lastupdated: "2019-06-10"

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


# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 插件
{: #dbaas_cli_plugin}

使用 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 插件可创建、删除和显示有关数据库和用户的信息，显示有关集群的详细信息，启动和停止实例以及列出和下载日志文件。
{:shortdesc}


## 先决条件
{: #prerequisites_dbaas_cli_plugin}

- 安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)。{{site.data.keyword.cloud_notm}} CLI 需要 Java SDK 1.7.0。用于通过 {{site.data.keyword.cloud_notm}} CLI 运行命令的前缀是 `ibmcloud`。在终端中，`ibmcloud` CLI 和插件更新可用时，您会收到通知。请确保使 CLI 保持最新，从而可使用所有可用的命令和标志。

- 安装 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 插件。有关参考信息，可以参阅[安装 DBaaS CLI 插件](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)。如果要查看 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 插件的当前版本，请运行 `ibmcloud plugin show dbaas-cli`。


## CLI 插件用法命令
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

此命令显示 DBaaS 命令的列表。

```
ibmcloud help dbaas
```
{: pre}


## 集群命令
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

此命令显示指定集群的详细信息，包括有关每个副本成员的信息。  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。要查找资源名称，请使用 {{site.data.keyword.cloud_notm}} 命令 `ibmcloud resource service-instances`。</dd>
</dl>

## 数据库命令
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

此命令创建数据库和（可选）集合。

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*database_name*</dt>
<dd>要创建的数据库的名称。</dd>
<dt>*collection*</dt>
<dd>（可选）要创建的集合的名称。</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

此命令删除数据库。如果数据库是通过凭证创建的，并且该凭证仍在使用中，请勿删除该数据库。

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*database_name*</dt>
<dd>要删除的数据库的名称。</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

此命令列出给定集群上的所有数据库。

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
</dl>


## 数据库用户命令
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

此命令创建数据库用户。

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*username*</dt>
<dd>要分配给所创建的数据库用户的用户名。</dd>
<dt>*db_name*</dt>
<dd>（可选）此选项指定用户将具有其读和写访问权的数据库。</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

此命令删除数据库用户。如果数据库用户是通过凭证创建的，并且该凭证仍在使用中，请勿删除该数据库用户。

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*username*</dt>
<dd>要删除的数据库用户的用户名。</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

此命令列出所有数据库用户。

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

此命令显示有关数据库用户的详细信息。

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*username*</dt>
<dd>要显示的数据库用户的用户名。</dd>
</dl>


## 实例命令
{: #instance_cmds}

要使用此处列出的任何实例命令，您需要知道 `instance_id`。要获取 `instance_id`，请首先使用以下 `ibmcloud` 命令来列出您帐户下的服务实例资源组名称，然后使用 [`cluster_show`](#cluster_show) 命令来获取 `instance_id`。

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

此命令重新启动正在运行的实例。

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*instance_id*</dt>
<dd>实例的标识。</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

此命令启动已停止的实例。

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*instance_id*</dt>
<dd>实例的标识。</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

此命令停止实例（集群的复制成员）。

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*instance_id*</dt>
<dd>实例的标识。</dd>
</dl>


## 日志命令
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

此命令从实例下载日志文件。

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*instance_id*</dt>
<dd>实例的标识。</dd>
<dt>*filename*</dt>
<dd>要下载的日志文件的名称。要确定需要下载的日志文件的文件名，请使用 [ibmcloud dbaas logs-list](#log_list) 命令。</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

此命令列出实例上的所有日志文件。可以将列出的任何文件名用作 [ibmcloud dbaas log-get](#log_get) 命令的输入。

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**命令选项**

<dl>
<dt>*resource_name*</dt>
<dd>集群资源的名称。</dd>
<dt>*instance_id*</dt>
<dd>实例的标识。</dd>
</dl>
