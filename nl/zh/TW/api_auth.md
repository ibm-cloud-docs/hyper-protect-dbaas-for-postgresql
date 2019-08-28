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


# 設定鑑別以使用 DBaaS 管理程式 API
{: #api-auth}

要進行鑑別，您需要 API 金鑰、存取記號和使用者 ID 來發出 API 要求。若要這麼做，請遵循以下指示：

1. 產生 API 金鑰：

   a. 在 {{site.data.keyword.cloud}} 儀表板中，選取**管理 > 存取權 (IAM)**。

      這將顯示「存取權 (IAM)」儀表板。

   b. 在「存取權 (IAM)」儀表板的側邊導覽畫面中，選取 **{{site.data.keyword.cloud_notm}} API 金鑰**。

   c. 按一下**建立 {{site.data.keyword.cloud_notm}} API 金鑰**。

      這將顯示「建立 API 金鑰」對話框。

   d. 在「建立 API 金鑰」對話框中，輸入 API 金鑰的名稱和說明，然後按一下**建立**。

   e. 按一下**下載**以下載並儲存 API 金鑰，或者按一下**複製**以將 API 金鑰複製到剪貼簿。

      此作業會傳回類似下列範例的 JSON 檔案：

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      指派給 `apiKey` 的值是 API 金鑰。**重要事項：**關閉視窗之前，請記下此值。

2. 若要確保安全資料傳送，請從 {{site.data.keyword.ihsdbaas_postgresql_full}} 儀表板取得憑證管理中心 (CA) 檔案，然後將其複製到相應的目錄，例如 **/etc/ssl/certs/**。

3. 使用 GET /auth/token 作業取得存取記號和使用者 ID：

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    此作業會傳回類似下列範例的存取記號和使用者 ID：

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. 儲存存取記號和使用者 ID 的值，以供未來使用。
