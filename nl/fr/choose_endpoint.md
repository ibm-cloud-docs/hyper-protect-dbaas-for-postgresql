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


# Choix d'un noeud final de service auquel se connecter
{: #choose-endpoint}

{{site.data.keyword.cloud}} fournit un grand nombre de noeuds finaux de service dans différentes régions géographiques auxquelles vous pouvez vous connecter.
Pour trouver un noeud final de service proche de votre emplacement géographique, utilisez la commande `ibmcloud regions` comme illustré dans l'exemple suivant :

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

Actuellement, {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} est seulement pris en charge dans la région **us-south**.
{: note}

Pour vous connecter à un noeud final de service {{site.data.keyword.cloud_notm}}, procédez comme suit :

1. Entrez la commande `ibmcloud login` en indiquant que vous utilisez la connexion unique et en spécifiant l'URL du noeud final auquel vous souhaitez vous connecter, comme illustré dans l'exemple ci-dessous :

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   Le système affiche une adresse URL correspondant à une page Web qui fournit un code d'accès à usage unique.

2. Copiez l'URL à partir de votre console système et collez-la dans votre navigateur Web.

   Le système affiche la page **Code d'accès à usage unique {{site.data.keyword.cloud_notm}}**.

3. Copiez le code d'accès à partir de la page Web et collez-le sur la ligne de commande de votre console système.

   Le code d'accès n'apparaît pas sur la ligne de commande. Lorsque le mot de passe est authentifié, le message **OK** s'affiche pour indiquer que vous êtes connecté.

Pour plus d'informations sur les paramètres de commande `ibmcloud login`, vous pouvez consulter [référence CLI {{site.data.keyword.cloud_notm}}](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).

Lorsque vous utilisez {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, vous pouvez être amené à créer des espaces dans plusieurs régions et à passer des unes aux autres à l'aide de la commande `ibmcloud target`. Pour plus d'informations, voir
[Ajout d'organisations et d'espaces](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)
et [Commandes générales de l'interface CLI (ibmcloud)](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target).
{: note}
