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


# Allgemeine Anweisungen für die Verwendung der DBaaS-Manager-APIs
{: #gen_inst_mgr_apis}
<ol>
<li>Geben Sie die Daten der Anforderung im JSON-Format an.
</li>
<li>Senden Sie die API-Anforderung an den DBaaS-Manager.
<p>Zur Verarbeitung einer Anforderung können Sie einen REST-konformen API-Client verwenden, zum Beispiel Curl.
</p>
<p>DBaaS-Manager werden an den folgenden Positionen bereitgestellt:
<table>
  <tr>
    <th> Hostname </th>
    <th> Portnummer </th>
    <th> Region </th>
    <th> Ort </th>
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

Ausführlichere Informationen (Methoden und Parameter) finden Sie in der [Dokumentation zur DBaaS-API](https://{DomainName}/apidocs/hyperp-dbaas){: external}.

## Beispiel
{: #api-example}

Setzen Sie zum Erstellen einer Serviceinstanz einen direkten API-Abruf ab, zum Beispiel:

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

Dabei gilt:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>Das vorher abgerufene Zugriffstoken; Informationen hierzu finden Sie unter [Authentifizierung zur Verwendung mit DBaaAS-Manager-APIs festlegen](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Hinweis:** Wenn das Zugriffstoken abgelaufen ist, geben Sie diese Anweisungen zurück und fordern Sie ein neues Token an.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>Der Hostname eines DBaaS-Managers. Gültige Hostnamen werden in der obigen Tabelle aufgeführt.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>Die Portnummer des DBaaS-Managers. Die gültige Portnummer lautet wie folgt:
<p>20000</p>
</dd>
</dl>

**Hinweis:** Der Datenbankadministrator verfügt nicht über die Berechtigung SUPERUSER.
Die Berechtigungen für den Datenbankadministrator sind auf INHERIT, CREATEROLE, CREATEDB, LOGIN und REPLICATION beschränkt.
