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


# Instructions générales relatives à l'utilisation des API DBaaS Manager
{: #gen_inst_mgr_apis}
<ol>
<li>Spécifiez les données de votre demande au format JSON.
</li>
<li>Envoyez la demande API à DBaaS Manager.
<p>Vous pouvez utiliser un client API RESTful, par exemple, cURL, pour gérer une demande.
</p>
<p>Les gestionnaires DBaaS Manager sont disponibles ici :
<table>
  <tr>
    <th> Nom d'hôte </th>
    <th> Numéro de port </th>
    <th> Région </th>
    <th> Ville </th>
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

Pour des informations plus détaillées (méthodes et paramètres), vous pouvez consulter la [documentation des API DBaaS](https://{DomainName}/apidocs/hyperp-dbaas){: external}.

## Exemple
{: #api-example}

Pour créer une instance de service, émettez un appel API direct, par exemple :

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

Où :
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>Est le jeton d'accès précédemment obtenu. Voir [Configuration de l'authentification pour utiliser des API DBaaS Manager](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Remarque :** si le jeton d'accès a expiré, revenez à ces instructions et demandez un nouveau jeton.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>Est le nom d'hôte d'un gestionnaire DBaaS Manager. Les noms d'hôte valides sont répertoriés dans le tableau ci-dessus.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>Est le numéro de port du gestionnaire DBaaS Manager. Le numéro de port valide est le suivant :
<p>20000</p>
</dd>
</dl>

**Remarque :** l'administrateur de base de données ne possède pas les droits superutilisateur.
Les droits de l'administrateur de base de données se limitent à INHERIT, CREATEROLE, CREATEDB, LOGIN et REPLICATION.
