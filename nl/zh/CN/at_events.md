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

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务可跟踪用户和应用程序如何与 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 进行交互。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录由用户发起的可更改 {{site.data.keyword.cloud_notm}} 中服务状态的活动。有关如何供应 {{site.data.keyword.cloudaccesstrailshort}} 服务的更多信息，请参阅 [{{site.data.keyword.cloudaccesstrailshort}} 文档](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)。目前在达拉斯数据中心已提供 {{site.data.keyword.ihsdbaas_postgresql_full}} 服务，请确保选择**美国南部**作为捕获日志的区域。

## 事件列表
{: #list-activity-tracker-events}

下表列出了生成事件的操作：

|操作|描述|
| ---------------------- | ----------------------------------------- |
|`cluster.create`|创建数据库集群|
|`cluster.delete`|删除数据库集群|
|`database.create`|创建数据库|
|`database.delete`|删除数据库|
|`user.create`|创建数据库用户|
|`user.delete`|删除数据库用户|
|`instance.start`|启动数据库服务实例|
|`instance.stop`|停止数据库服务实例|
|`instance.restart`|重新启动数据库服务实例|
|`log.get`|下载日志文件|
{: caption="表 1. 生成 {{site.data.keyword.cloudaccesstrailfull_notm}} 事件的操作"}

对于 `cluster.create` 和 `cluster.delete` 事件，{{site.data.keyword.cloudaccesstrailfull_notm}} 服务不会记录执行操作的用户的帐户名称和 IP 地址。日志中 `initiator.name` 和 `host.address` 的值分别指示 Cloud Broker 的服务标识和 Cloud Broker 的 IP 地址。
{: note}

## 查看事件的位置
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 事件在 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**中提供，该域在生成这些事件的 {{site.data.keyword.cloud_notm}} 区域中提供。
