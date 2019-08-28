---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# 服务实例
{: #dbaas_webui_service}

## 创建服务实例
{: #dbaas_webui_create_service}

<ol>
<li>单击 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 目录条目以打开服务创建屏幕。</li>
<li>输入所需的值。
  <dl>
    <dt>服务名称：</dt>
    <dd>数据库服务的名称。</dd>

    <dt>选择要在其中部署的区域/位置：</dt>
    <dd>选择数据库将位于的数据中心。</dd>

    <dt>选择资源组：</dt>
    <dd>如果没有可选择的资源组，那么可以在 {{site.data.keyword.cloud_notm}}“仪表板”上创建资源组。</dd>

    <dt>标记：</dt>
    <dd>标记是可选的。有关标记的更多信息，请参阅[标记资源](/docs/resources?topic=resources-tag#tag)。</dd>

    <dt>集群/副本集名称：</dt>
    <dd>服务实例的名称。</dd>

    <dt>数据库管理员名称：</dt>
    <dd>数据库管理员 (DBA) 的用户标识。<p>**注：**数据库管理员没有 SUPERUSER 权限。数据库管理员的权限限制为 INHERIT、CREATEROLE、CREATEDB、LOGIN 和 REPLICATION。</p></dd>

    <dt>数据库管理员密码：</dt>
    <dd>
    <p>DBA 用户标识的密码。您需要创建具有以下特性的强密码：<ul>
        <li>长度至少为 **15 个字符**</li>
        <li>至少包含 **1 个大写字符**</li>
        <li>至少包含 **1 个小写字符**</li>
        <li>至少包含 **1 个数字**</li>
        <li>不包含用户名</li>
      </ul>
    </p>
    </dd>

    <dt>确认密码：</dt>
    <dd>确认 DBA 用户标识的密码。</dd>

    <dt>许可协议：</dt>
    <dd>阅读许可协议后，选中该框以确认您同意。</dd>

    <dt>价格套餐：</dt>
    <dd>对于 PostgreSQL 类型的数据库，价格套餐提供了不同的定价类别。请选择最符合您需求的类别。</dd>
  </dl>
</li>
<li>单击**创建**。<p>在出现一个对话框窗口指示您需要时间来部署服务后，将显示 {{site.data.keyword.cloud_notm}}“资源列表”仪表板。可以在列表的**服务**部分下看到您创建的服务实例。服务的状态为**已供应**时，说明实例可供使用。</p>
</li>

<li>选择相应服务以显示 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 仪表板。</li>
</ol>

为了进一步加强安全性，建议您在供应服务实例后立即更新**数据库管理员密码**。您需要遵循先前提到的相同规则来设置新密码。
{: note}

## 列出所有服务实例
{: #dbaas_webui_list_service}

打开 {{site.data.keyword.cloud_notm}}“仪表板”以显示已创建服务实例的列表：

<ol>
	<li>单击控制台左上角的三杠按钮。</li>
	<li>选择“仪表板”。</li>
	<li>选择“服务”。</li>
</ol>

## 显示服务实例的详细信息
{: #dbaas_webui_show_detail_service}

1. 单击目标实例名称以显示服务仪表板。
2. 在左侧导航栏中选择**管理**，然后可以在**概述**选项卡页面上看到总体信息。
3. 选择**实例**选项卡以显示详细信息。


## 删除服务实例
{: #dbaas_webui_delete_service}

1. 通过单击**导航菜单 > 资源列表**来显示 {{site.data.keyword.cloud_notm}} 资源列表。
2. 打开**服务**折叠标记以显示服务实例。
3. 选择要删除的服务实例。
4. 单击右侧的三个点。
5. 单击**删除**。
