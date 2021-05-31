---

copyright:
  years: 2019, 2021
lastupdated: "2021-05-31"

keywords: access token, "{{site.data.keyword.ihsdbaas_full}} APIs", API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Setting up the APIs
{: #api-setup}

You can use the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} RESTful APIs to create and monitor {{site.data.keyword.ihsdbaas_postgresql_full}} service instances.
{: shortdesc}

## Setting up authentication
{: #api-auth}

For authentication, you need an API key, an [access token](#x2113001){: term}, and a user ID to issue API requests. Complete the following steps:

1. Generate an API key:

   a. In the {{site.data.keyword.cloud_notm}} console, go to **Manage > Access (IAM)**.

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
      {: screen}

      The value that is assigned to `apiKey` is your API key. 

      Make a note of this value before you close the window.
      {: important}

2. For Linux, to ensure secure data transfer, download the [certificate authority (CA)](#x2016383){: term} file from the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, and copy it to an appropriate directory such as **/etc/ssl/certs/**.

   For Windows and MacOS, the CA file is in the operating system. If not, download it from the {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, and add `--cacert <cert_file>` to the command in the following step.

3. Get an access token and a user ID by using the `GET /auth/token` operation:

    ```sh
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
    {: screen}

4. Save the values of the access token and the user ID for future use.

## General instructions for using the APIs
{: #gen_inst_mgr_apis}

1. Specify the data of your request in JSON format.
2. Send the API request to the DBaaS Manager. You can use a RESTful API client, such as cURL, to handle a request.

DBaaS Managers are available in the following regions for service instances with public endpoints:

| Hostname | Port Number | Region | City |
|-----------|-------------|--------|------|
| dbaas900.hyperp-dbaas.cloud.ibm.com | 20000 | `us-south` | Dallas |
| dbaas906.hyperp-dbaas.cloud.ibm.com | 20000 | `us-east` | Washington DC |
| dbaas902.hyperp-dbaas.cloud.ibm.com | 20000 | `eu-de` | Frankfurt |
| dbaas904.hyperp-dbaas.cloud.ibm.com | 20000 | `au-syd` | Sydney |
{: caption="Table 1. DBaaS Managers" caption-side="top"}

DBaaS Managers are available in the following regions for service instances with private endpoints:

| Hostname | Port Number | Region | City |
|-----------|-------------|--------|------|
| dbaas900.private.hyperp-dbaas.cloud.ibm.com | 20000 | `us-south` | Dallas |
| dbaas906.private.hyperp-dbaas.cloud.ibm.com | 20000 | `us-east` | Washington DC |
| dbaas902.private.hyperp-dbaas.cloud.ibm.com | 20000 | `eu-de` | Frankfurt |
| dbaas904.private.hyperp-dbaas.cloud.ibm.com | 20000 | `au-syd` | Sydney |
{: caption="Table 2. DBaaS Managers (private)" caption-side="top"}

For more information about methods and parameters, see [{{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v3){: external}.
