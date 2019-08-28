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


# Serviceendpunkt für Anmeldung auswählen
{: #choose-endpoint}

Von {{site.data.keyword.cloud}} werden viele Serviceendpunkte in verschiedenen geografischen Regionen bereitgestellt, an denen Sie sich anmelden können.
Wenn Sie einen Serviceendpunkt in der Nähe Ihres Standorts suchen, verwenden Sie wie im folgenden Beispiel dargestellt den Befehl `ibmcloud regions`:

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

Derzeit wird {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} nur in der Region **us-south** unterstützt.
{: note}

Führen Sie die folgenden Schritte aus, um sich an einem {{site.data.keyword.cloud_notm}}-Serviceendpunkt anzumelden:

1. Geben Sie den Befehl `ibmcloud login` ein, der angibt, dass Sie Single Sign-On (SSO) verwenden und die URL des Endpunkts angeben, an dem Sie sich anmelden möchten; dies wird im folgenden Beispiel veranschaulicht.

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   Vom System wird eine URL für eine Webseite angezeigt, von der Ihnen ein einmaliger Kenncode bereitgestellt wird.

2. Kopieren Sie die URL aus der Systemkonsole und fügen Sie sie in den Web-Browser ein.

   Vom System wird die Seite für den einmaligen Kenncode (**{{site.data.keyword.cloud_notm}} One time passcode**) anzeigt.

3. Kopieren Sie den Kenncode von der Webseite und fügen Sie ihn in die Befehlszeile der Systemkonsole ein.

   Der Kenncode wird in der Befehlszeile nicht angezeigt. Wenn das Kennwort authentifiziert wird, empfangen Sie die Nachricht **OK* *, die angibt, dass Sie angemeldet sind.

Weitere Informationen zu den Parametern des Befehls `ibmcloud login` finden Sie den [Referenzinformationen zur {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).

Bei der Verwendung von {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} müssen Sie möglicherweise Bereiche in mehreren Regionen erstellen und mithilfe des Befehls `ibmcloud target` zwischen den Regionen wechseln. Weitere Informationen finden Sie unter [Organisationen und Bereiche hinzufügen] (/docs/account?topic=account-orgsspacesusers#orgsspacesusers) und [Allgemeine CLI-Befehle (ibmcloud)] (/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target).
{: note}
