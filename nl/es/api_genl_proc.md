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


# Instrucciones generales para utilizar las API del gestor de DBaaS
{: #gen_inst_mgr_apis}
<ol>
<li>Especifique los datos de su solicitud en formato JSON.
</li>
<li>Envíe la solicitud de API al gestor de DBaaS.
<p>Puede utilizar un cliente de API RESTful, por ejemplo cURL, para manejar una solicitud.
</p>
<p>Los gestores de DBaaS están disponibles aquí:
<table>
  <tr>
    <th> Nombre de host </th>
    <th> Número de puerto </th>
    <th> Región </th>
    <th> Ciudad </th>
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

Para obtener más información sobre métodos y parámetros, consulte la [documentación de la API de DBaaS](https://{DomainName}/apidocs/hyperp-dbaas){: external}.

## Ejemplo
{: #api-example}

Para crear una instancia de servicio, emita una llamada de API directa, como por ejemplo:

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

Donde:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>Es la señal de acceso obtenida previamente; consulte [Configuración de la autenticación para utilizar las API del gestor de DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Nota:** si la señal de acceso ha caducado, vuelva a estas instrucciones y solicite una nueva señal.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>Es el nombre de host de un gestor de DBaaS. Los nombres de host válidos se enumeran en la lista de la tabla anterior.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>Es el número de puerto del gestor de DBaaS. Este es el número de puerto válido:
<p>20000</p>
</dd>
</dl>

**Nota:** El administrador de base de datos no tiene autoridad de SUPERUSER.
Las autoridades del administrador de base de datos están limitadas a INHERIT, CREATEROLE, CREATEDB, LOGIN y REPLICATION.
