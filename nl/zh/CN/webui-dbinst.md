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


# 数据库实例
{: #dbaas-webui-database-instances}

## 开始之前
{: #webui-database-instances-byb}

在 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 仪表板中，选择“实例”选项卡。

## 启动数据库实例
{: #webui-start-database-instance}

1. 选择数据库实例。
2. 单击行右端的三个点，然后选择**启动**。

## 停止数据库实例
{: #webui-stop-database-instance}

1. 选择数据库实例。
2. 单击行右端的三个点，然后选择**停止**。如果这是主节点，那么还可以选择**强制停止**。

## 重新启动数据库实例
{: #webui-restart-database-instance}

1. 选择数据库实例。
2. 单击行右端的三个点，然后选择**重新启动**。

## 下载日志
{: #webui-download-log}

1. 选择数据库实例。
2. 选择**开始日期**和**结束日期**以按时间过滤日志。
3. 通过单击日志名称前面的**复选框**，选择要下载的日志。
4. 单击**下载**按钮。

## 检查实例状态
{: #webui-check-instance-status}

实例面板上的彩色圆点指示实例的状态。您可以参阅下表来检查实例状态。

|颜色|状态|操作|
|-----|------|------|
|绿色|实例正在运行。|可以停止或重新启动实例。|
|黄色|实例已停止。|可以启动实例。|
|红色|实例发生故障。|您可以参阅[获取帮助与支持](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support)。|
{: caption="表 1. 状态颜色"}
