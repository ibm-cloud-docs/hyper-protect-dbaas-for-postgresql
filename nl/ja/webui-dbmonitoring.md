---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# データベース・モニタリング
{: #dbaas-webui-database-monitor}

データベース・モニタリングを有効にすると、Grafana を使用してデータベース・メトリックを表示できます。
{: shortdesc}

## 始めに
{: #webui-database-monitoring-byb}

1.  Cloud Foundry 組織およびダラス (us-south) のスペースに対するアクセス権があることを確認します。
    このようなアクセス権の取得方法については、[Cloud Foundry アクセス権限の管理](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}を参照してください。

2.  データベース・クラスターのすべてのインスタンスが稼働していることを確認します。

3.  {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} ダッシュボードで、「モニタリング」タブを選択します。

## データベース・モニタリングを有効にする
{: #webui-enable-database-monitoring}

「モニタリング」タブに**「モニタリングが無効です (Monitoring is disabled)」**というメッセージが表示される場合:

1. **「有効化 (Enable)」**をクリックします。
2. 「モニタリングの有効化 (Enable Monitoring)」ウィンドウで、組織とスペースを選択し、**「送信」**をクリックします。


## データベース・メトリックの表示
{: #webui-view-database-metrics}

Grafana でメトリックを表示するには、以下の 2 つの方法があります。

- 表示されたリンクをコピーし、新しいタブまたはウィンドウを開き、ブラウザーにリンクを貼り付けます。
- **「Grafana で表示 (View in Grafana)」**をクリックします。

Grafana の新しいダッシュボードにメトリックを表示するには、左上の Grafana アイコンを選択し、**「ダッシュボード」>「新規 (New)」**と選択します。
データベース・クラスター ID とインスタンス ID が表示されるまで時間がかかることがあります。また、ダッシュボードを再ロードする必要がある場合もあります。

Grafana の使用の詳細については、[{{site.data.keyword.cloud_notm}}モニタリング](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started)を参照してください。
