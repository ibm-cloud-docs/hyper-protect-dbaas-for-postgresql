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


# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 外掛程式
{: #dbaas_cli_plugin}

使用 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 外掛程式可建立、刪除和顯示有關資料庫和使用者的資訊、顯示有關叢集的詳細資料、啟動和停止實例，以及列出和下載日誌檔。
{:shortdesc}


## 必要條件
{: #prerequisites_dbaas_cli_plugin}

- 安裝 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)。{{site.data.keyword.cloud_notm}} CLI 需要 Java SDK 1.7.0。使用 {{site.data.keyword.cloud_notm}} CLI 來執行指令的字首是 `ibmcloud`。在終端機中，有 `ibmcloud` CLI 和外掛程式更新可用時，您會收到通知。請務必使 CLI 保持最新，以便您可以使用所有可用的指令和旗標。

- 安裝 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 外掛程式。如需參考資料，可以參閱[安裝 DBaaS CLI 外掛程式](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)。如果要檢視 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} CLI 外掛程式的現行版本，請執行 `ibmcloud plugin show dbaas-cli`。


## CLI 外掛程式使用指令
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

這個指令會顯示 DBaaS 指令的清單。

```
ibmcloud help dbaas
```
{: pre}


## 叢集指令
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

這個指令會顯示指定叢集的詳細資料，包括每個抄本成員的相關資訊。  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。若要尋找資源名稱，請使用 {{site.data.keyword.cloud_notm}} 指令 `ibmcloud resource service-instances`。</dd>
</dl>

## 資料庫指令
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

這個指令會建立資料庫，及選用性建立集合。

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*database_name*</dt>
<dd>要建立的資料庫名稱。</dd>
<dt>*collection*</dt>
<dd>（選用）要建立的集合名稱。</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

這個指令會刪除資料庫。如果資料庫是由認證建立，並且該認證仍在使用中，請勿刪除該資料庫。

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*database_name*</dt>
<dd>要刪除的資料庫名稱。</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

這個指令會列出給定叢集上的所有資料庫。

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
</dl>


## 資料庫使用者指令
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

這個指令會建立資料庫使用者。

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*username*</dt>
<dd>要指派給所建立的資料庫使用者的使用者名稱。</dd>
<dt>*db_name*</dt>
<dd>（選用）此參數指定使用者將具有其讀寫權的資料庫。</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

這個指令會刪除資料庫使用者。如果資料庫使用者是由認證建立，並且該認證仍在使用中，請勿刪除該資料庫使用者。

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*username*</dt>
<dd>要刪除之資料庫使用者的使用者名稱。</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

這個指令會列出所有資料庫使用者。

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

這個指令會顯示資料庫使用者的相關詳細資料。

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*username*</dt>
<dd>要顯示之資料庫使用者的使用者名稱。</dd>
</dl>


## 實例指令
{: #instance_cmds}

若要使用這裡列出的任何實例指令，您需要知道 `instance_id`。若要取得 `instance_id`，請先使用下列 `ibmcloud` 指令來列出您帳戶下的服務實例資源群組名稱，然後使用 [`cluster_show`](#cluster_show) 指令來取得 `instance_id`。

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

這個指令會重新啟動執行中的實例。

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*instance_id*</dt>
<dd>實例的 ID。</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

這個指令會啟動已停止的實例。

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*instance_id*</dt>
<dd>實例的 ID。</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

這個指令會指令停止實例（叢集的抄寫成員）。

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*instance_id*</dt>
<dd>實例的 ID。</dd>
</dl>


## 日誌指令
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

這個指令會從實例下載日誌檔。

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*instance_id*</dt>
<dd>實例的 ID。</dd>
<dt>*filename*</dt>
<dd>要下載的日誌檔名稱。若要確定您要下載的日誌檔名稱，請使用 [ibmcloud dbaas logs-list](#log_list) 指令。</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

這個指令會列出實例上的所有日誌檔。可以將列出的任何檔名用作 [ibmcloud dbaas log-get](#log_get) 指令的輸入。

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**指令選項**

<dl>
<dt>*resource_name*</dt>
<dd>叢集資源的名稱。</dd>
<dt>*instance_id*</dt>
<dd>實例的 ID。</dd>
</dl>
