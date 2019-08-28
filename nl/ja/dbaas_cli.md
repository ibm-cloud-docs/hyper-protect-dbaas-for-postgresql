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


# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI プラグイン
{: #dbaas_cli_plugin}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI プラグインを使用して、
データベースおよびユーザーの作成、削除、情報表示、クラスターに関する詳細の表示、
インスタンスの開始と停止、およびログ・ファイルのリスト表示とダウンロードを行えます。
{:shortdesc}


## 前提条件
{: #prerequisites_dbaas_cli_plugin}

- [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started) をインストールします。 {{site.data.keyword.cloud_notm}} CLI には、Java SDK 1.7.0 が必要です。 {{site.data.keyword.cloud_notm}} CLI を使用してコマンドを実行するための接頭部は、`ibmcloud` です。 `ibmcloud` CLI およびプラグインの更新が使用可能になると、端末に通知が表示されます。 使用可能なすべてのコマンドおよびフラグを使用できるように、CLI を最新の状態に保つようにしてください。

- {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI プラグインをインストールします。 [DBaaS
CLI プラグインのインストール](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)を参考にしてください。 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI プラグインの現行バージョンを表示するには、
`ibmcloud plugin show dbaas-cli` を実行します。


## CLI プラグイン使用方法コマンド
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

このコマンドは DBaaS コマンドのリストを表示します。

```
ibmcloud help dbaas
```
{: pre}


## クラスター・コマンド
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

このコマンドは、各レプリカ・メンバーに関する情報など、指定されたクラスターの詳細を表示します。  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。 リソース名を確認するには、{{site.data.keyword.cloud_notm}} コマンドの `ibmcloud resource service-instances` を使用します。</dd>
</dl>

## データベース・コマンド
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

このコマンドは、データベース、およびオプションでコレクションを作成します。

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*database_name*</dt>
<dd>作成するデータベースの名前。</dd>
<dt>*collection*</dt>
<dd>(オプション) 作成するコレクションの名前。</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

このコマンドはデータベースを削除します。 データベースの作成に使用した資格情報をまだ使用している場合は、そのデータベースを削除しないでください。

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*database_name*</dt>
<dd>削除するデータベースの名前。</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

このコマンドは、指定されたクラスター上のすべてのデータベースのリストを表示します。

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
</dl>


## データベース・ユーザー・コマンド
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

このコマンドはデータベース・ユーザーを作成します。

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*username*</dt>
<dd>作成するデータベース・ユーザーに割り当てるユーザー名。</dd>
<dt>*db_name*</dt>
<dd>(オプション) これはユーザーが読み取り権限と書き込み権限を持つデータベースを指定します。</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

このコマンドはデータベース・ユーザーを削除します。 データベース・ユーザーの作成に使用した資格情報をまだ使用している場合は、そのデータベース・ユーザーを削除しないでください。

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*username*</dt>
<dd>削除するデータベース・ユーザーのユーザー名。</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

このコマンドはすべてのデータベース・ユーザーのリストを表示します。

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

このコマンドはデータベース・ユーザーの詳細を表示します。

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*username*</dt>
<dd>表示するデータベース・ユーザーのユーザー名。</dd>
</dl>


## インスタンス・コマンド
{: #instance_cmds}

ここに記載するインスタンス・コマンドを使用するには、`instance_id` がわかっていなければなりません。 `instance_id` を確認するには、まず以下の `ibmcloud` コマンドを使用して、アカウントにあるサービス・インスタンスのリソース・グループ名をリスト表示してから、[`cluster_show`](#cluster_show) コマンドを使用して `instance_id` を取得します。

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

このコマンドは実行中のインスタンスを再始動します。

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*instance_id*</dt>
<dd>インスタンスの ID。</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

このコマンドは停止しているインスタンスを開始します。

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*instance_id*</dt>
<dd>インスタンスの ID。</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

このコマンドはインスタンス (クラスターのレプリケーション・メンバー) を停止します。

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*instance_id*</dt>
<dd>インスタンスの ID。</dd>
</dl>


## ログ・コマンド
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

このコマンドは、インスタンスからログ・ファイルをダウンロードします。

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*instance_id*</dt>
<dd>インスタンスの ID。</dd>
<dt>*filename*</dt>
<dd>ダウンロードするログ・ファイルの名前。 ダウンロードするログ・ファイルのファイル名を確認するには、[ibmcloud dbaas logs-list](#log_list) コマンドを使用します。</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

このコマンドはインスタンス上のすべてのログ・ファイルのリストを表示します。 リストされたファイル名を [ibmcloud dbaas log-get](#log_get) コマンドへの入力として使用できます。

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**コマンド・オプション**

<dl>
<dt>*resource_name*</dt>
<dd>クラスター・リソースの名前。</dd>
<dt>*instance_id*</dt>
<dd>インスタンスの ID。</dd>
</dl>
