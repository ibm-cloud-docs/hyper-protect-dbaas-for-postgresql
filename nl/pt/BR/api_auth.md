---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: access token, DBaaS Manager APIs, API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Configurando a autenticação para usar as APIs do DBaaS Manager
{: #api-auth}

Para autenticação, é necessária uma chave de API, um token de acesso e um ID do usuário para emitir solicitações de API.
Para fazer isso, siga estas instruções:

1. Gere uma chave de API:

   a. No painel do {{site.data.keyword.cloud}}, selecione **Gerenciar > Acesso (IAM)**.

      O painel de Acesso (IAM) é exibido.

   b. No painel de navegação lateral do painel de Acesso (IAM), selecione Chaves de API do **{{site.data.keyword.cloud_notm}}**.

   c. Clique em **Criar uma chave de API do {{site.data.keyword.cloud_notm}}**.

      O diálogo Criar Chave de API é exibido.

   d. No diálogo Criar Chave de API, insira um nome e uma descrição para a chave de API e clique em **Criar**.

   e. Clique em **Download** para fazer download e salve a chave de API ou clique em **Copiar** para copiar a chave de API para a sua área de transferência.

      Esta operação retorna um arquivo de JSON semelhante a este exemplo:

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      O valor que é designado a `apiKey` é sua chave de API. **Importante:** anote esse valor antes de fechar a janela.

2. Para garantir a transferência de dados segura, obtenha um arquivo de autoridade de certificação (CA) por meio do painel do {{site.data.keyword.ihsdbaas_postgresql_full}} e copie-o para um diretório apropriado, como **/etc/ssl/ce rts/**.

3. Obtenha um token de acesso e um ID do usuário usando a operação GET /auth/token:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    Esta operação retorna um token de acesso e um ID do usuário semelhante a este exemplo:

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Salve os valores do token de acesso e o ID do usuário para uso futuro.
