---

copyright:
  years: 2019, 2020
lastupdated: "2020-10-14"

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
{:term: .term}
{:external: target="_blank" .external}

# Setting up the APIs
{: #api-setup}

You can use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} RESTful APIs to create and monitor {{site.data.keyword.ihsdbaas_postgresql_full}} service instances.
{: shortdesc}

## Setting up authentication
{: #api-auth}

For authentication, you need an API key, an [access token](#x2113001){: term}, and a user ID to issue API requests. Complete the following steps:

1. Generate an API key:

   a. In the {{site.data.keyword.cloud_notm}} dashboard, select **Manage > Access (IAM)**.

   b. In the side navigation pane of the **Access (IAM)** dashboard, select **API Keys**.

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

      The value that is assigned to `apiKey` is your API key. 

      Make a note of this value before you close the window.
      {: important}

2. For Linux, to ensure secure data transfer, download the [certificate authority (CA)](#x2016383){: term} file from the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, and copy it to an appropriate directory such as **/etc/ssl/certs/**.

   For Windows and MacOS, the CA file is in the operating system. If not, download it from the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, and add `--cacert <cert_file>` to the command in the following step.

3. Get an access token and a user ID by using the `GET /auth/token` operation:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v3/auth/token
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

## General instructions for using the APIs
{: #gen_inst_mgr_apis}

1. Specify the data of your request in JSON format.
2. Send the API request to the DBaaS Manager. You can use a RESTful API client, such as cURL, to handle a request.

DBaaS Managers are available in the following regions:

| Hostname | Port Number | Region | City |
|-----------|-------------|--------|------|
| dbaas900.hyperp-dbaas.cloud.ibm.com | 20000 | us-south | Dallas |
| dbaas902.hyperp-dbaas.cloud.ibm.com | 20000 | eu-de | Frankfurt |
| dbaas904.hyperp-dbaas.cloud.ibm.com | 20000 | au-syd | Sydney |
{: caption="Table 1. DBaaS Managers" caption-side="top"}

For more information about methods and parameters, see [{{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v3){: external}.
