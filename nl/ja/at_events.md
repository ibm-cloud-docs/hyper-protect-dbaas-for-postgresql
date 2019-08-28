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

# {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #activity-tracker-events}

{{site.data.keyword.cloudaccesstrailfull}} サービスを使用して、{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} に対するユーザーとアプリケーションの操作を追跡できます。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.cloud_notm}} 内のサービスの状態を変更するアクティビティーをユーザーが開始した場合にそのアクティビティーを記録します。 {{site.data.keyword.cloudaccesstrailshort}} サービスのプロビジョンの方法について、詳しくは [{{site.data.keyword.cloudaccesstrailshort}} 資料](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started) を参照してください。現在 {{site.data.keyword.ihsdbaas_postgresql_full}} サービスはダラスのデータ・センターで利用可能ですので、ログの取得には **us-south** 地域を選択してください。

## イベントのリスト
{: #list-activity-tracker-events}

以下の表に、イベントが生成される操作をリストします。

| 操作                 | 説明                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | データベース・クラスターを作成する                 |
| `cluster.delete` | データベース・クラスターを削除する                 |
| `database.create` | データベースを作成する                  |
| `database.delete` | データベースを削除する                  |
| `user.create`     | データベース・ユーザーを作成する                    |
| `user.delete`     | データベース・ユーザーを削除する                    |
| `instance.start` | データベース・サービス・インスタンスを開始する         |
| `instance.stop`  | データベース・サービス・インスタンスを停止する          |
| `instance.restart`  | データベース・サービス・インスタンスを再始動する          |
| `log.get`       | ログ・ファイルをダウンロードする |
{: caption="表 1. {{site.data.keyword.cloudaccesstrailfull_notm}} イベントが生成される操作"}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、`cluster.create` および `cluster.delete` のイベントの場合は、アクションを実行するユーザーのアカウント名と IP アドレスを記録しません。 ログ内の `initiator.name` および `host.address` の値は、それぞれ Cloud Broker のサービス ID および IP アドレスを示します。
{: note}

## イベントの表示場所
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成された {{site.data.keyword.cloud_notm}} 地域内の {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**にあります。
