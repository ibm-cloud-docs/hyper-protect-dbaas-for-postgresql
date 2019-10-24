---

copyright:
  years: 2019
lastupdated: "2019-10-10"

keywords: DBaaS Manager, API request, "{{site.data.keyword.ihsdbaas_full}} APIs"

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

# General instructions for using the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs
{: #gen_inst_mgr_apis}

General procedures for using the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs are as follows:
{: shortdesc}

1. Specify the data of your request in JSON format.
2. Send the API request to the DBaaS Manager. You can use a RESTful API client, such as cURL, to handle a request.

DBaaS Managers are available in the following regions:

| Host name | Port number | Region | City |
|-----------|-------------|--------|------|
| dbaas900.hyperp-dbaas.cloud.ibm.com | 20000 | us-south | Dallas |
| dbaas902.hyperp-dbaas.cloud.ibm.com | 20000 | eu-de | Frankfurt |
| dbaas904.hyperp-dbaas.cloud.ibm.com | 20000 | au-syd | Sydney |
{: caption="Table 1. DBaaS Managers" caption-side="top"}

For more detailed information (methods and parameters), see the [{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}} API documentation](/apidocs/hyperp-dbaas){: external}.

## Example
{: #api-example}

To create a service instance, issue a direct API call, such as:

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "content-type: application/json" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

**Command options**

- *access_token*

  The access_token that you obtained when you [set up authentication to use {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth).

  If the access token has expired, return to those instructions and request a new token.
  {: note}

- *ip*

  The host name of a DBaaS Manager. Valid host names are listed in Table 1.

- *port*

  The port number of the DBaaS Manager. The valid port number is 20000.

The database administrator does not have SUPERUSER authority. The authorities of the database administrator are limited to INHERIT, CREATEROLE, CREATEDB, LOGIN, and REPLICATION.
{: note}
