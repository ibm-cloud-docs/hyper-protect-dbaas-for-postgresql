---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} の概要
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} は、オンデマンドで PostgreSQL データベースを提供する {{site.data.keyword.cloud_notm}} サービスです。 柔軟かつスケーラブルなプラットフォームで、最適なデータベースを迅速かつ簡単にプロビジョンして管理することができます。
{: shortdesc}

この {{site.data.keyword.cloud_notm}} オファリングでは、PostgreSQL データベース・クラスターが提供されます。 各データベース・クラスターは、1 つのマスター・データベース・インスタンスと、マスター・データベースをバックアップする 2 つのデータベース・インスタンス・スレーブから構成されます。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} では、{{site.data.keyword.cloud_notm}} 内にデータベース・クラスターを作成し、
データベース・インスタンスの管理、データベース・ユーザーの管理、データベースの作成とモニターを行えます。

## データ・セキュリティーおよびプライバシー
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} は可用性が高くセキュアな環境でデータベースをホストします。
<ul>
<li>基礎のテクノロジーにより、{{site.data.keyword.IBM_notm}} や第三者によるデータ・アクセスを防止しています。
<p>{{site.data.keyword.IBM_notm}} Secure Service Container テクノロジーにより、改ざん防止環境でシステムを保護しています。 システムへのアクセスは制限されており、明確に定義された RESTful API を使用しないとアクセスできません。</p></li>
<li>データは保存中も転送中も暗号化されます。</li>
<li>システムのハードウェア、システム構成、およびデータベースのセットアップにより、高可用性を実現しています。</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## データベース・クラスターの作成
{: #creating-a-database-cluster-introduction}

データベース・クラスターを作成する方法は、{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} サービス構成画面に必要な値を入力して**「作成」**をクリックするだけです。

データベース・クラスターを作成すると、作成された 1 つ以上のデータベース・インスタンスのホスト名とポート番号が {{site.data.keyword.IBM_notm}} から通知されます。 その情報とカタログに指定したユーザー資格情報を使用すれば、
データベースを作成してアクセスできます。

## データベース・クラスターの管理
{: #managing-database-cluster-introduction}

データベース・クラスターでは、データベースの作成、データベース・インスタンスの管理、およびユーザーの作成/削除を行えます。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} に含まれている DBaaS Manager は、使用可能なリソースに基づいて要求を処理し、インテリジェントにスケジューリングすることができます。

要求を DBaaS Manager に送信するには、以下のいずれかのインターフェースを使用します。

- [Web ユーザー・インターフェース](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- [DBaaS Manager API (データベース・クラスターの管理)](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- [{{site.data.keyword.cloud_notm}} API (サービス・インスタンスの管理)](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- [{{site.data.keyword.cloud_notm}} CLI ツールの CLI プラグイン](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## データベースへのアクセス
{: #accessing-database-introduction}

PostgreSQL データベースの作成後、pgAdmin またはお気に入りの PostgreSQL ツールを使用してデータベースを管理できます。

### 始めに
{: #accessing-database-introduction-byb}

セキュアなデータ転送を確保するために、ダッシュボードから認証局 (CA) ファイルを取得して適切なディレクトリーにコピーします。

### データベースへの接続
{: #accessing-database-introduction-connect}

データベースに接続するために必要な情報は、{{site.data.keyword.ihsdbaas_postgresql_full}} ダッシュボードに表示されます。

#### psql シェル
{: #accessing-database-introduction-connect-psqlshell}

次のコマンドを使用できます。
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
各パラメーターの説明は以下のとおりです。
<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> データベース・クラスターのホスト名 </dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> サービス作成画面で指定されたデータベース管理者のユーザー名 </dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> データベース・クラスターのポート番号 </dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> CA ファイルのパス </dd>  
</dl>

**注:** オプション `sslmode` および `sslrootcert` が指定されていない場合、`psql` コマンドでデータベース・クラスター証明書は検証されません。

### その他のツール
{: #accessing-database-introduction-connect-other}

その他のツール (pgAdmin など) については、{{site.data.keyword.ihsdbaas_postgresql_full}} は、ホストに接続するために *SSL サーバー証明書の検証*をサポートしています。 必要に応じて、提供されている CA ファイルを使用してください。
