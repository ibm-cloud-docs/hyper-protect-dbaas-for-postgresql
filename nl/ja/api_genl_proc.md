---

copyright:
  years: 2019
lastupdated: "2019-06-21"

keywords: DBaaS Manager APIs, DBaaS Manager, API request

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# DBaaS Manager API の一般的な使用手順
{: #gen_inst_mgr_apis}
<ol>
<li>要求データを JSON 形式で指定します。
</li>
<li>API 要求を DBaaS Manager に送信します。
<p>cURL などの RESTful API クライアントを使用して要求を操作できます。
</p>
<p>DBaaS Manager は以下で提供されています。
<table>
  <tr>
    <th> ホスト名 </th>
    <th> ポート番号 </th>
    <th> 地域 </th>
    <th> 都市 </th>
  </tr>
  <tr>
    <td> dbaas900.hyperp-dbaas.cloud.ibm.com </td>
    <td> 20000 </td>
    <td> us-south </td>
    <td> ダラス </td>
  </tr>
</table>
</p>	 
</li>
</ol>

詳細情報 (メソッドおよびパラメーター) については、[DBaaS API の資料](https://{DomainName}/apidocs/hyperp-dbaas){: external}を参照してください。

## 例
{: #api-example}

サービス・インスタンスを作成するために、以下のように直接の API 呼び出しを実行します。

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

各パラメーターの説明は以下のとおりです。
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>事前に取得したアクセス・トークン。[DBaaS Manager API を使用するための認証のセットアップ](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth)を参照してください (**注:** アクセス・トークンの期限が切れている場合は、この手順に戻って新しいトークンを要求してください)。 </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>DBaaS Manager のホスト名。 上記の表に有効なホスト名をリストしています。
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>DBaaS Manager のポート番号。 有効なポート番号を以下に示します。
<p>20000</p>
</dd>
</dl>

**注:** データベース管理者には SUPERUSER 権限はありません。
データベース管理者の権限は INHERIT、CREATEROLE、CREATEDB、LOGIN、および REPLICATION に制限されています。
