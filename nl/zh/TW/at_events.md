---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #activity-tracker-events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服務可追蹤使用者及應用程式與 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 互動的方式。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始並且會變更 {{site.data.keyword.cloud_notm}} 中服務狀態的活動。如需如何佈建 {{site.data.keyword.cloudaccesstrailshort}} 服務的相關資訊，請參閱 [{{site.data.keyword.cloudaccesstrailshort}} 文件](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)。由於 {{site.data.keyword.ihsdbaas_postgresql_full}} 服務目前提供於達拉斯資料中心，請務必選取 **us-south** 作為要擷取日誌的地區。

## 事件清單
{: #list-activity-tracker-events}

下表列出產生事件的動作：

|動作|說明|
| ---------------------- | ----------------------------------------- |
|`cluster.create`|建立資料庫叢集|
|`cluster.delete`|刪除資料庫叢集|
|`database.create`|建立資料庫|
|`database.delete`|刪除資料庫|
|`user.create`|建立資料庫使用者|
|`user.delete`|刪除資料庫使用者|
|`instance.start`|啟動資料庫服務實例|
|`instance.stop`|停止資料庫服務實例|
|`instance.restart`|重新啟動資料庫服務實例|
|`log.get`|下載日誌檔|
{: caption="表 1. 產生 {{site.data.keyword.cloudaccesstrailfull_notm}} 事件的動作"}

對於 `cluster.create` 和 `cluster.delete` 事件，{{site.data.keyword.cloudaccesstrailfull_notm}} 服務不會記錄執行動作之使用者的帳戶名稱和 IP 位址。日誌中 `initiator.name` 和 `host.address` 的值，分別指出 Cloud Broker 的服務 ID 和 Cloud Broker 的 IP 位址。
{: note}

## 事件的檢視位置
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 事件可在 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**取得，而該網域位於產生事件的 {{site.data.keyword.cloud_notm}} 地區。
