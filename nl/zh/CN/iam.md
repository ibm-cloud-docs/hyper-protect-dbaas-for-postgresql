---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

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

# Identity and Access Management 角色和操作
{: #iam}

帐户中用户对 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服务实例的访问权由 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 进行控制。访问帐户中 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服务的每个有户都必须分配有定义了 IAM 角色的访问策略。策略确定用户可以在您选择的服务或实例的上下文中执行的操作。允许的操作由 {{site.data.keyword.cloud_notm}} 服务进行定制，并定义为允许在服务上执行的操作。然后，操作会映射到 IAM 用户角色。
{: shortdesc}

策略支持在不同级别授予访问权。一些选项包括以下各项：

* 对帐户中所有服务实例的访问权
* 对帐户中单个服务实例的访问权
* 对实例中特定资源的访问权

定义访问策略的作用域后，您可分配一个角色，用于确定用户的访问级别。查看以下各表，其中概述了每个角色在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服务中允许的操作。

下表详细描述了映射到平台管理角色的操作。平台管理角色支持用户在平台级别对服务资源执行任务，例如为用户分配对服务的访问权，创建或删除实例，以及将实例绑定到应用程序。

|平台管理角色|操作描述|示例操作|
|------------------------|----------------------|----------------------------------------------------------------|
|查看者|可以查看服务实例，但无法对其进行修改|<ul><li>列出集群</li><li>查看集群的详细信息</li></ul>|
|编辑者|执行除管理帐户和分配访问策略以外的其他所有平台操作|<ul><li>将服务绑定到集群</li></ul>|
|操作员|执行配置和操作服务实例所需的平台操作，例如查看服务的仪表板|<ul><li>将服务绑定到集群</li></ul>|
|管理员|基于此角色分配用于的资源执行所有平台操作，包括为其他用户分配访问策略|<ul><li>除去集群</li><li>创建集群</li><li>更新用户访问策略</li><li>查看者、编辑者和操作员可以执行的所有操作</li></ul>|
{: caption="表 1. IAM 用户角色和操作"}

有关在 UI 中分配用户角色的信息，请参阅[管理对资源的访问权](/docs/iam?topic=iam-iammanidaccser#iammanidaccser)。
