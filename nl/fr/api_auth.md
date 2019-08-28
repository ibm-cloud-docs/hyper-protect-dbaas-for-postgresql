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


# Configuration de l'authentification pour utiliser des API DBaaS Manager
{: #api-auth}

Pour l'authentification, vous avez besoin d'une clé d'API, d'un jeton d'accès et d'un ID utilisateur afin d'émettre des demandes d'API.
Pour ce faire, procédez comme suit :

1. Générez une clé d'API :

   a. Dans le tableau de bord d'{{site.data.keyword.cloud}}, sélectionnez **Gérer > Accès (IAM)**.

      Le tableau de bord Accès (IAM) s'ouvre.

   b. Dans le panneau de navigation latéral du tableau de bord Accès (IAM), sélectionnez **Clés d'API {{site.data.keyword.cloud_notm}}**.

   c. Cliquez sur **Créer une clé d'API {{site.data.keyword.cloud_notm}}**.

      La boîte de dialogue Créer une clé d'API s'affiche.

   d. Dans la boîte de dialogue Créer une clé d'API, entrez un nom et une description pour la clé d'API et cliquez sur **Créer**.

   e. Cliquez sur **Télécharger** pour télécharger et sauvegarder la clé d'API ou cliquez sur **Copier** pour copier la clé d'API dans votre tableau de bord.

      Cette opération renvoie un fichier JSON dont le contenu est semblable à celui illustré ci-dessous :

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      La valeur qui est affectée à `apiKey` correspond à votre clé d'API. **Important :** notez cette valeur avant de fermer la fenêtre.

2. Pour garantir le transfert sécurisé des données, procurez-vous un fichier d'autorité de certification à partir du tableau de bord {{site.data.keyword.ihsdbaas_postgresql_full}} et copiez-le dans un répertoire approprié, tel que **/etc/ssl/certs/**.

3. Récupérez un jeton d'accès et un ID utilisateur en exécutant l'opération GET /auth/token :

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    Cette opération renvoie un jeton d'accès et un ID utilisateur semblables à ceux présentés ci-dessous :

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Sauvegardez les valeurs du jeton d'accès et de l'ID utilisateur afin de les utiliser ultérieurement.
