---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# 開始使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 是一個 {{site.data.keyword.cloud_notm}} 服務，用於隨需應變提供 PostgreSQL 資料庫。DBaaS 提供了靈活、可調整的平台，讓您能快速、輕鬆地佈建和管理所選的資料庫。
{: shortdesc}

此 {{site.data.keyword.cloud_notm}} 供應項目提供 PostgreSQL 資料庫叢集。每個資料庫叢集都包含一個主要資料庫實例和兩個從屬資料庫實例（用於備份主要資料庫實例）。

使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}，您可以在 {{site.data.keyword.cloud_notm}} 中建立資料庫叢集、管理資料庫實例、管理資料庫使用者，以及建立和監視資料庫。

## 資料安全與隱私
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} 在高可用性的安全環境中，管理您的資料庫：
<ul>
<li>基礎技術可防止 {{site.data.keyword.IBM_notm}} 或協力廠商存取您的資料。<p>{{site.data.keyword.IBM_notm}} Secure Service Container 技術透過防篡改環境來保護系統。對系統的存取權受到限制，並且只能透過明確定義的 RESTful API 啟用。</p></li>
<li>不論資料是在靜止還是使用中，都會予以加密。</li>
<li>系統硬體、系統配置及資料庫設定都確保高可用性。</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## 建立資料庫叢集
{: #creating-a-database-cluster-introduction}

若要建立資料庫叢集，只需在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服務配置畫面中輸入必要值，然後按一下**建立**。

建立資料庫叢集後，{{site.data.keyword.IBM_notm}} 會提供已建立資料庫實例的一個以上主機名稱和埠號。現在，可以使用這些資訊以及型錄中指定的使用者認證來建立和存取資料庫。

## 管理資料庫叢集
{: #managing-database-cluster-introduction}

在資料庫叢集裡，可以建立資料庫、管理資料庫實例以及建立或刪除使用者。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 包含 DBaaS 管理程式，用於根據可用資源來管理和聰明地排定要求。

可以透過下列其中一個介面來處理對 DBaaS 管理程式的要求：

- [Web 使用者介面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- [DBaaS 管理程式 API（用於資料庫叢集管理）](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- [{{site.data.keyword.cloud_notm}} API（用於服務實例管理）](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- [{{site.data.keyword.cloud_notm}} CLI 工具的 CLI 外掛程式](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## 存取資料庫
{: #accessing-database-introduction}

建立 PostgreSQL 資料庫後，可以使用 pgAdmin 或您喜歡的 PostgreSQL 工具來管理資料庫。

### 開始之前
{: #accessing-database-introduction-byb}

若要確保安全資料傳送，請從儀表板取得憑證管理中心 (CA) 檔案，然後將其複製到相應的目錄。

### 連接至資料庫
{: #accessing-database-introduction-connect}

{{site.data.keyword.ihsdbaas_postgresql_full}} 儀表板提供連接至資料庫所需的資訊。

#### psql Shell
{: #accessing-database-introduction-connect-psqlshell}

您可以使用這個指令：
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
其中：<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> 是資料庫叢集的主機名稱</dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> 是資料庫管理者的使用者名稱，如服務建立畫面中所指定</dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> 是資料庫叢集的埠號</dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> 是 CA 檔案的路徑</dd>  
</dl>

**附註：**如果未提供 `sslmode` 和 `sslrootcert` 選項，`psql` 指令不會驗證資料庫叢集憑證。

### 其他工具
{: #accessing-database-introduction-connect-other}

對於其他工具（例如 pgAdmin），{{site.data.keyword.ihsdbaas_postgresql_full}} 支援使用 *SSL 伺服器憑證驗證* 以連接至主機。如果需要，請使用提供的 CA 檔案。
