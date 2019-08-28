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


# 資料庫實例
{: #dbaas-webui-database-instances}

## 開始之前
{: #webui-database-instances-byb}

在 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 儀表板中，選取「實例」標籤。

## 啟動資料庫實例
{: #webui-start-database-instance}

1. 選取資料庫實例。
2. 按一下該行右端的三個點，然後選取**啟動**。

## 停止資料庫實例
{: #webui-stop-database-instance}

1. 選取資料庫實例。
2. 按一下該行右端的三個點，然後選取**停止**。如果這是主要節點，您也可以選取**強制停止**。

## 重新啟動資料庫實例
{: #webui-restart-database-instance}

1. 選取資料庫實例。
2. 按一下該行右端的三個點，然後選取**重新啟動**。

## 下載日誌
{: #webui-download-log}

1. 選取資料庫實例。
2. 選取**開始日期**和**結束日期**以按時間過濾日誌。
3. 藉由按一下日誌名稱前面的**勾選框**，選取要下載的日誌。
4. 按一下**下載**按鈕。

## 檢查實例狀態
{: #webui-check-instance-status}

實例畫面上的彩色圓點指出實例的狀態。您可以參閱下表格來檢查實例狀態。

|顏色|狀態|動作|
|-----|------|------|
|綠色|實例執行中。|可以停止或重新啟動實例。|
|黃色|實例已停止。|可以啟動實例。|
|紅色|實例發生故障。|您可以參閱[取得協助與支援](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support)。|
{: caption="表 1. 狀態顏色"}
