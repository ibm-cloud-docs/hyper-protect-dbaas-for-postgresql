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


# 数据库监视
{: #dbaas-webui-database-monitor}

启用数据库监视后，可以使用 Grafana 来查看数据库度量值。
{: shortdesc}

## 开始之前
{: #webui-database-monitoring-byb}

1.  确保您有权访问达拉斯 (us-south) 的 Cloud Foundry 组织和空间。有关如何获取此类访问权的信息，请参阅[管理 Cloud Foundry 访问权](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}。

2.  确保数据库集群的所有实例都在运行。


3.  在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 仪表板中，选择“监视”选项卡。

## 启用数据库监视
{: #webui-enable-database-monitoring}

如果在“监视”选项卡中显示**监视已禁用**消息，请执行以下操作：

1. 单击**启用**。
2. 在“启用监视”窗口中，选择组织和空间，然后单击**提交**。


## 查看数据库度量值
{: #webui-view-database-metrics}

在 Grafana 中有两种方式可查看度量值：

- 复制显示的链接，然后打开新的选项卡或窗口，并将链接粘贴到浏览器。
- 单击**在 Grafana 中查看**。

要在 Grafana 的新仪表板中显示度量值，请选择左上角的 Grafana 图标，然后选择**仪表板 > 新建**。可能需要一些时间才能显示数据库集群标识和实例标识，并且您可能必须重新装入仪表板。

有关使用 Grafana 的更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 监视](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started)。
