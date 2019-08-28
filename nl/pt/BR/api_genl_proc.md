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


# Instruções gerais para usar as APIs do DBaaS Manager
{: #gen_inst_mgr_apis}
<ol>
<li>Especifique os dados de sua solicitação no formato de JSON.
</li>
<li>Envie a solicitação de API para o DBaaS Manager.
<p>É possível usar um cliente da API de RESTful, como cURL, para manipular uma solicitação.
</p>
<p>Os DBaaS Managers estão disponíveis aqui:
<table>
  <tr>
    <th> Nome do host </th>
    <th> Número da porta </th>
    <th> Região </th>
    <th> Cidade </th>
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

Para obter informações mais detalhadas (métodos e parâmetros), é possível ver a [documentação da API do DBaaS](https://{DomainName}/apidocs/hyperp-dbaas){: external}.

## Exemplo
{: #api-example}

Para criar uma instância de serviço, emita uma chamada de API direta, como:

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

Em
que:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>É o token de acesso obtido anteriormente; consulte [Configurando a autenticação para usar as APIs do DBaaS Manager](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth). (**Nota:** se o token de acesso tiver expirado, retorne para essas instruções e solicite um novo token.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>É o nome do host de um DBaaS Manager. Os nomes do host válidos estão listados na tabela acima.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>É o número da porta do DBaaS Manager. Este é o número da porta válido:
<p>20000</p>
</dd>
</dl>

**Nota:** o administrador de banco de dados não tem a autoridade SUPERUSER.
As autoridades do administrador de banco de dados são limitadas a INHERIT, CREATEROLE, CREATEDB, LOGIN e REPLICATION.
