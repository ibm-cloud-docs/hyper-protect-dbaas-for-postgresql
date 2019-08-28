---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: access token, DBaaS Manager APIs, API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# DBaaS Manager API を使用するための認証のセットアップ
{: #api-auth}

認証を受けるために、API 要求を発行するときには API キー、アクセス・トークン、およびユーザー ID が必要になります。
そのため、以下の手順に従ってください。

1. API キーを生成します。

   a. {{site.data.keyword.cloud}} ダッシュボードで、**「管理」>「アクセス (IAM)」**を選択します。

      「アクセス (IAM)」ダッシュボードが表示されます。

   b. 「アクセス (IAM)」ダッシュボードの端のナビゲーション・パネルで、**「{{site.data.keyword.cloud_notm}} API キー」**を選択します。

   c. **「{{site.data.keyword.cloud_notm}} API キーの作成」**をクリックします。

      「API キーの作成」ダイアログが表示されます。

   d. 「API キーの作成」ダイアログで、API キーの名前と説明を入力して**「作成」**をクリックします。

   e. **「ダウンロード」**をクリックして API キーをダウンロードして保存するか、**「コピー」**をクリックして API キーをクリップボードにコピーします。

      この操作により、以下の例のような JSON ファイルが返されます。

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      `apiKey` に割り当てられた値が、使用する API キーです。 **重要:** ウィンドウを閉じる前に、この値をメモしてください。

2. セキュアなデータ転送を確保するために、{{site.data.keyword.ihsdbaas_postgresql_full}} ダッシュボードで認証局 (CA) ファイルを取得して適切なディレクトリー (**/etc/ssl/certs/** など) にコピーします。

3. GET /auth/token 操作を使用して、アクセス・トークンおよびユーザー ID を取得します。

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    この操作により、以下の例のようなアクセス・トークンおよびユーザー ID が返されます。

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. アクセス・トークンとユーザー ID の値を将来の使用に備えて保存します。
