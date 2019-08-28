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


# 資料庫監視
{: #dbaas-webui-database-monitor}

已啟用資料庫監視後，可以使用 Grafana 來檢視資料庫度量值。
{: shortdesc}

## 開始之前
{: #webui-database-monitoring-byb}

1.  務必要能存取達拉斯 (us-south) 的 Cloud Foundry 組織和空間。如需如何取得此類存取權的資訊，請參閱[管理 Cloud Foundry 存取權](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}。

2.  確保資料庫叢集的所有實例都在執行中。

3.  在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 儀表板中，選取「監視」標籤。

## 啟用資料庫監視
{: #webui-enable-database-monitoring}

如果在「監視」標籤中顯示**監視已停用**訊息，請執行下列動作：

1. 按一下**啟用**。
2. 在「啟用監視」視窗中，選取組織和空間，然後按一下**提交**。


## 檢視資料庫度量值
{: #webui-view-database-metrics}

在 Grafana 中有兩種方式可檢視度量值：

- 複製顯示的鏈結，然後開啟新的標籤或視窗，並將鏈結貼到瀏覽器。
- 按一下**在 Grafana 中檢視**。

若要在 Grafana 的新儀表板中顯示度量值，請選取左上角 Grafana 圖示，然後選取**儀表板 > 新建**。可能需要一些時間才能顯示資料庫叢集 ID 和實例 ID，並且您可能必須重新載入儀表板。

如需使用 Grafana 的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 監視](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started)。
