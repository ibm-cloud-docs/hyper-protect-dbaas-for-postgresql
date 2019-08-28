---

copyright:
  years: 2019
lastupdated: "2019-06-20"

keywords: service endpoint, ibmcloud regions

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Elección de un punto final de servicio para iniciar sesión
{: #choose-endpoint}

{{site.data.keyword.cloud}} proporciona muchos puntos finales de servicio en varias regiones geográficas en los que puede iniciar sesión.
Para encontrar un punto final de servicio cerca de su ubicación geográfica, utilice el mandato `ibmcloud regions`, como se muestra en este ejemplo:

<pre><code class="hljs">~$ ibmcloud regions
Listing regions...

Name       Display name
au-syd     Sydney
jp-tok     Tokyo
eu-de      Frankfurt
eu-gb      London
us-south   Dallas
us-east    Washington DC

</code></pre>

Actualmente, {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} solo recibe soporte en la región **us-south**.
{: note}

Para iniciar sesión en un punto final de servicio de {{site.data.keyword.cloud_notm}}, siga estos pasos:

1. Especifique el mandato `ibmcloud login`, indicando que está utilizando el inicio de sesión único (SSO) y especificando el URL del punto final en el que desea iniciar sesión, como se muestra en este ejemplo:

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   El sistema muestra un URL para una página web que le proporciona un código de acceso de un solo uso.

2. Copie el URL de la consola del sistema y péguelo en el navegador web.

   El sistema muestra la página **Código de acceso de un solo uso de {{site.data.keyword.cloud_notm}}**.

3. Copie el código de acceso de la página web y péguelo en la línea de mandatos de la consola del sistema.

   El código de acceso no se visualiza en la línea de mandatos. Cuando la contraseña se autentica, recibe un mensaje **Correcto** que indica que ha iniciado sesión.

Para obtener más información sobre los parámetros del mandato `ibmcloud login` command parameters, revise la [Consulta de CLI de {{site.data.keyword.cloud_notm}}](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).

Si utiliza {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, es posible que tenga que crear espacios en más de una región y cambiar entre regiones mediante el mandato `ibmcloud target` command. Para obtener más información, consulte [Adición de organizaciones y espacios](/docs/account?topic=account-orgsspacesusers#orgsspacesusers) y [Mandatos de CLI generales (ibmcloud)](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target).
{: note}
