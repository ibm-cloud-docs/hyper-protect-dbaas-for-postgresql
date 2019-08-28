---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# データベース・インスタンス
{: #dbaas-webui-database-instances}

## 始めに
{: #webui-database-instances-byb}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} ダッシュボードで、「インスタンス」タブを選択します。

## データベース・インスタンスの開始
{: #webui-start-database-instance}

1. データベース・インスタンスを選択します。
2. 行の右端にある 3 つのドットをクリックし、**「開始」**を選択します。

## データベース・インスタンスの停止
{: #webui-stop-database-instance}

1. データベース・インスタンスを選択します。
2. 行の右端にある 3 つのドットをクリックし、**「停止」**を選択します。 1 次ノードの場合は、**「強制停止 (Force stop)」**を選択することもできます。

## データベース・インスタンスの再始動
{: #webui-restart-database-instance}

1. データベース・インスタンスを選択します。
2. 行の右端にある 3 つのドットをクリックし、**「再始動」**を選択します。

## ログのダウンロード
{: #webui-download-log}

1. データベース・インスタンスを選択します。
2. **「開始日」**と**「終了日」**を選択し、時間でログをフィルター操作します。
3. ログの名前の前にある**チェック・ボックス**をクリックして、ダウンロードするログを選択します。
4. **「ダウンロード」**ボタンをクリックします。

## インスタンス状況の確認
{: #webui-check-instance-status}

インスタンス・パネル上の色付きのドットは、インスタンスの状況を示しています。 以下の表を参照して、インスタンスの状況を確認できます。

|色|状況|操作|
|-----|------|------|
|緑|インスタンスは実行中です。|インスタンスを停止または再開することができます。|
|黄|インスタンスは停止しています。|インスタンスを開始できます。|
|赤|インスタンスが失敗しました。|[ヘルプとサポートの利用](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support)を参照してください。|
{: caption="表 1. 状況の色"}
