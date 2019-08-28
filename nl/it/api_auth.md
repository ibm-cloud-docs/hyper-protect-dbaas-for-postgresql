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


# Configurazione dell'autenticazione per utilizzare le API DBaaS Manager
{: #api-auth}

Per l'autenticazione, hai bisogno di una chiave API, un token di accesso e un ID utente per emettere le richieste API.
A tale scopo, segui queste istruzioni:

1. Genera una chiave API:

   a. Nel dashboard {{site.data.keyword.cloud}}, seleziona **Manage > Access (IAM)**.

      Viene visualizzato il dashboard Access (IAM).

   b. Nel pannello di navigazione laterale del dashboard Access (IAM), seleziona **{{site.data.keyword.cloud_notm}} API Keys**

   c. Fai clic su **Create an {{site.data.keyword.cloud_notm}} API Key**.

      Viene visualizzata la finestra di dialogo Create API Key.

   d. Nella finestra di dialogo Create API key, immetti un nome e una descrizione per la chiave API e fai clic su **Create**.

   e. Fai clic su **Download** per scaricare e salvare la chiave API oppure fai clic su **Copy** per copiare la chiave API nei tuoi appunti.

      Questa operazione restituisce un file JSON simile a questo esempio:

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      Il valore che viene assegnato a `apiKey` è la tua chiave API. **Importante:** prendi nota di questo valore prima di chiudere questa finestra.

2. Per garantire un trasferimento dei dati sicuro, ottieni un file dell'autorità di certificazione (o CA, certificate authority) dal dashboard {{site.data.keyword.ihsdbaas_postgresql_full}} e copialo in una directory appropriata come ad esempio **/etc/ssl/certs/**.

3. Ottieni un token di accesso e un ID utente utilizzando l'operazione GET /auth/token:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    Questa operazione restituisce un token di accesso e un ID utente simili a questo esempio:

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Salva i valori del token di accesso e dell'ID utente per un utilizzo futuro.
