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


# Istruzioni generali per l'utilizzo delle API DBaaS Manager
{: #gen_inst_mgr_apis}
<ol>
<li>Specifica i dati della tua richiesta nel formato JSON.
</li>
<li>Invia la richiesta API a DBaaS Manager.
<p>Puoi utilizzare un client API RESTful, come ad esempio cURL, per gestire una richiesta.
</p>
<p>I DBaaS Manager sono disponibili qui:
<table>
  <tr>
    <th> Nome host </th>
    <th> Numero di porta </th>
    <th> Regione </th>
    <th> Città </th>
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

Per informazioni più dettagliate (metodi e parametri), puoi vedere la [documentazione API DBaaS](https://{DomainName}/apidocs/hyperp-dbaas){: external}.

## Esempio
{: #api-example}

Per creare un'istanza del servizio, emetti una chiamata API diretta, ad esempio:

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

Dove:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>È il token di accesso precedentemente ottenuto; vedi [Configurazione dell'autenticazione per utilizzare le API DBaaS Manager](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Nota:** se il token di accesso è scaduto, torna a tali istruzioni e richiedi un nuovo token.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>È il nome host di un DBaaS Manager. I nomi host validi sono elencati nella precedente tabella.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>È il numero di porta del DBaaS Manager. Questo è il numero di porta valido:
<p>20000</p>
</dd>
</dl>

**Nota:** l'amministratore del database non deve avere l'autorità SUPERUSER.
Le autorità dell'amministratore del database sono limitate a INHERIT, CREATEROLE, CREATEDB, LOGIN e REPLICATION.
