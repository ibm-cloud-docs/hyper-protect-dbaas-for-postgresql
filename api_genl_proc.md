---

copyright:
  years: 2019
lastupdated: "2019-8-28"

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
<ol>
<li>Specify the data of your request in JSON format.
</li>
<li>Send the API request to the DBaaS Manager.
<p>You can use a RESTful API client, such as cURL, to handle a request.
</p>
<p>DBaaS Managers are available here:
<table>
  <tr>
    <th> Host name </th>
    <th> Port number </th>
    <th> Region </th>
    <th> City </th>
  </tr>
  <tr>
    <td> dbaas900.hyperp-dbaas.cloud.ibm.com </td>
    <td> 20000 </td>
    <td> us-south </td>
    <td> Dallas </td>
  </tr>
</table>
</p>	 
</li>
</ol>

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

Where:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>Is the previously obtained access token; see [Setting up authentication to use {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Note:** If the access token has expired, return to those instructions and request a new token.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>Is the host name of a DBaaS Manager. Valid host names are listed in the table above.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>Is the port number of the DBaaS Manager. This is the valid port number:
<p>20000</p>
</dd>
</dl>

**Note:** The database administrator does not have SUPERUSER authority. The authorities of the database administrator are limited to INHERIT, CREATEROLE, CREATEDB, LOGIN, and REPLICATION.
