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


# Scelta di un endpoint del servizio con cui accedere
{: #choose-endpoint}

{{site.data.keyword.cloud}} fornisce molti endpoint del servizio in diverse regioni geografiche a cui puoi accedere.
Per trovare un endpoint del servizio vicino alla tua ubicazione geografica, utilizza il comando `ibmcloud regions` come mostrato in questo esempio:

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

Al momento, {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} è supportato solo nella regione **us-south**.
{: note}

Per accedere a un endpoint del servizio {{site.data.keyword.cloud_notm}}, attieniti a questa procedura:

1. Immetti il comando `ibmcloud login`, che indica che stai utilizzando SSO (Single Sign-On) e specifica l'URL dell'endpoint a cui vuoi accedere, come mostrato in questo esempio:

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   Il sistema visualizza un URL per una pagina web che ti fornisce un passcode monouso.

2. Copia l'URL dalla tua console di sistema a incollalo nel tuo browser web.

   Il sistema visualizza la pagina **{{site.data.keyword.cloud_notm}} One time passcode**.

3. Copia il passcode dalla pagina web e incollalo nella tua riga di comando della console di sistema.

   Il passcode non viene visualizzato nella riga di comando. Quando la password viene autenticata, ricevi un messaggio **OK** che indica che hai effettuato l'accesso.

Per ulteriori informazioni sui parametri del comando `ibmcloud login`, puoi vedere la [Guida di riferimento API {{site.data.keyword.cloud_notm}}](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).

Quando utilizzi {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, potresti dover creare gli spazi in più di una regione ed eseguire lo switch tra le regioni utilizzando il comando `ibmcloud target`. Per ulteriori informazioni, vedi
[Aggiunta di organizzazioni e spazi](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)
e [Comandi (ibmcloud) CLI generali](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target).
{: note}
