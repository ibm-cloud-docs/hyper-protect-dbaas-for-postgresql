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


# Configuración de la autenticación para utilizar las API del gestor de DBaaS
{: #api-auth}

Para la autenticación, necesita una clave de API, una señal de acceso y un ID de usuario para emitir las solicitudes de API.
Para ello, siga estas instrucciones:

1. Genere una clave de API:

   a. En el panel de control de {{site.data.keyword.cloud}}, seleccione **Gestionar > Acceso (IAM)**.

      Se muestra el panel de control Acceso (IAM).

   b. En el panel de navegación lateral del panel de control Acceso (IAM), seleccione **Claves de API de {{site.data.keyword.cloud_notm}}**.

   c. Pulse **Crear una clave de API de {{site.data.keyword.cloud_notm}}**.

      Se abre el diálogo Crear clave de API.

   d. En el diálogo Crear clave de API, especifique un nombre y una descripción para la clave de API y pulse **Crear**.

   e. Pulse **Descargar** para descargar y guardar la clave de API, o pulse **Copiar** para copiar la clave de API en el portapapeles.

      Esta operación devuelve un archivo JSON similar al de este ejemplo:

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      El valor que se asigna a `apiKey` es la clave de API. **Importante:** anote este valor antes de cerrar la ventana.

2. Para garantizar la transferencia segura de datos, obtenga un archivo de la Entidad emisora de certificados (CA) desde el panel de control de {{site.data.keyword.ihsdbaas_postgresql_full}} y cópielo en un directorio adecuado, como **/etc/ssl/certs/**.

3. Obtenga una señal de acceso y un ID de usuario utilizando la operación GET /auth/token:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    Esta operación devuelve una señal de acceso y un ID de usuario similar a este ejemplo:

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Guarde los valores de la señal de acceso y el ID de usuario para su uso futuro.
