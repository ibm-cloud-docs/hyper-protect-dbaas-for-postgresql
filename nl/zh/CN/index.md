---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 入门
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 是一个 {{site.data.keyword.cloud_notm}} 服务，用于根据需要提供 PostgreSQL 数据库。DBaaS 提供了灵活、可缩放的平台，支持快速、轻松地供应和管理所选的数据库。
{: shortdesc}

此 {{site.data.keyword.cloud_notm}} 产品提供 PostgreSQL 数据库集群。每个数据库集群都包含一个主数据库实例和两个从属数据库实例（用于备份主数据库实例）。

通过 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}，可以在 {{site.data.keyword.cloud_notm}} 中创建数据库集群，管理数据库实例，管理数据库用户，以及创建和监视数据库。

## 数据安全和隐私
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} 在高可用性的安全环境中托管数据库：
<ul>
<li>底层技术可阻止 {{site.data.keyword.IBM_notm}} 或第三方访问您的数据。<p>{{site.data.keyword.IBM_notm}} Secure Service Container 技术通过防篡改环境来保护系统。对系统的访问受到限制，并且仅通过明确定义的 RESTful API 启用。</p></li>
<li>数据采用静态加密和动态加密。</li>
<li>系统硬件、系统配置和数据库设置可确保高可用性。</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## 创建数据库集群
{: #creating-a-database-cluster-introduction}

要创建数据库集群，只需在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服务配置屏幕中输入必需值，然后单击**创建**。

创建数据库集群后，{{site.data.keyword.IBM_notm}} 会提供已创建数据库实例的一个或多个主机名和端口号。现在，可以使用这些信息以及目录中指定的用户凭证来创建和访问数据库。

## 管理数据库集群
{: #managing-database-cluster-introduction}

在数据库集群中，可以创建数据库，管理数据库实例以及创建或删除用户。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 包含 DBaaS 管理器，用于根据可用资源来管理和智能安排请求。

可以通过下列其中一个界面来处理对 DBaaS 管理器的请求：

- [Web 用户界面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- [DBaaS 管理器 API（用于数据库集群管理）](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- [{{site.data.keyword.cloud_notm}} API（用于服务实例管理）](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- [{{site.data.keyword.cloud_notm}} CLI 工具的 CLI 插件](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## 访问数据库
{: #accessing-database-introduction}

创建 PostgreSQL 数据库后，可以使用 pgAdmin 或您喜欢的 PostgreSQL 工具来管理数据库。

### 开始之前
{: #accessing-database-introduction-byb}

要确保安全数据传输，请从仪表板获取认证中心 (CA) 文件，然后将其复制到相应的目录。

### 连接到数据库
{: #accessing-database-introduction-connect}

{{site.data.keyword.ihsdbaas_postgresql_full}} 仪表板提供连接到数据库所需的信息。

#### psql shell
{: #accessing-database-introduction-connect-psqlshell}

可以使用以下命令：
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
其中：<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> 是数据库集群的主机名</dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> 是服务创建屏幕中指定的数据库管理员的用户名</dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> 是数据库集群的端口号</dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> 是 CA 文件的路径</dd>  
</dl>

**注：**如果未提供 `sslmode` 和 `sslrootcert` 选项，那么 `psql` 命令不会验证数据库集群证书。

### 其他工具
{: #accessing-database-introduction-connect-other}

对于其他工具（例如，pgAdmin），{{site.data.keyword.ihsdbaas_postgresql_full}} 支持 *SSL 服务器证书验证*以连接到主机。如果需要，请使用提供的 CA 文件。
