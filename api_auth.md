---

copyright:
  years: 2019
lastupdated: "2019-08-28"

keywords: access token, "{{site.data.keyword.ihsdbaas_full}} APIs", API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:external: target="_blank" .external}

# Setting up authentication to use {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs
{: #api-auth}

You can use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} RESTful APIs to create and manage the {{site.data.keyword.ihsdbaas_postgresql_full}} services.
{:shortdesc: .shortdesc}

For authentication, you need an API key, an access token, and a user ID to issue API requests.
To do so, follow these instructions:

1. Generate an API key:

   a. In the {{site.data.keyword.cloud}} dashboard, select **Manage > Access (IAM)**.

      The Access (IAM) dashboard is displayed.

   b. In the side navigation pane of the Access (IAM) dashboard, select **{{site.data.keyword.cloud_notm}} API Keys**.

   c. Click **Create an {{site.data.keyword.cloud_notm}} API Key**.

   d. In the **Create API key** dialog box, enter a name and a description for the API key and click **Create**.

   e. Click **Download** to download and save the API key, or click **Copy** to copy the API key to your clipboard.

      This operation returns a JSON file similar to this example:

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      The value that is assigned to `apiKey` is your API key. **Important:** Make a note of this value before you close the window.

2. To ensure secure data transfer, obtain a Certificate Authority (CA) file from the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, and copy it to an appropriate directory such as **/etc/ssl/certs/**.

3. Get an access token and a user ID by using the GET /auth/token operation:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    This operation returns an access token and a user ID similar to this example:

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Save the values of the access token and the user ID for future use.
