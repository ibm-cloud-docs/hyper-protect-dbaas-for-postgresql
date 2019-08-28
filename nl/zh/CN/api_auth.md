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


# 设置认证以使用 DBaaS 管理器 API
{: #api-auth}

要进行认证，您需要 API 密钥、访问令牌和用户标识来发出 API 请求。为此，请遵循以下指示信息：

1. 生成 API 密钥：

   a. 在 {{site.data.keyword.cloud}}“仪表板”中，选择**管理 > 访问权 (IAM)**。

      这将显示“访问权 (IAM)”仪表板。

   b. 在“访问权 (IAM)”仪表板的侧边导航面板中，选择 **{{site.data.keyword.cloud_notm}} API 密钥**。

   c. 单击**创建 {{site.data.keyword.cloud_notm}} API 密钥**。

      这将显示“创建 API 密钥”对话框。

   d. 在“创建 API 密钥”对话框中，输入 API 密钥的名称和描述，然后单击**创建**。

   e. 单击**下载**以下载并保存 API 密钥，或者单击**复制**以将 API 密钥复制到剪贴板。

      此操作会返回类似于以下示例的 JSON 文件：

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      分配给 `apiKey` 的值是 API 密钥。**重要信息：**关闭窗口之前，请记下此值。

2. 要确保安全数据传输，请从 {{site.data.keyword.ihsdbaas_postgresql_full}} 仪表板获取认证中心 (CA) 文件，然后将其复制到相应的目录，例如 **/etc/ssl/certs/**。

3. 使用 GET /auth/token 操作获取访问令牌和用户标识：

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    此操作会返回类似于以下示例的访问令牌和用户标识：

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. 保存访问令牌和用户标识的值，以供未来使用。
