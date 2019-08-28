---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# Einführung in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} ist ein {{site.data.keyword.cloud_notm}}-Service, von dem auf Anforderung PostgreSQL-Datenbanken bereitgestellt werden. Er bietet eine flexible und skalierbare Plattform, die es Ihnen ermöglicht, schnell und einfach eine Datenbank Ihrer Wahl bereitzustellen und zu verwalten.
{: shortdesc}

Von diesem {{site.data.keyword.cloud_notm}}-Angebot werden PostgreSQL-Datenbankcluster bereitgestellt. Jeder Datenbankcluster besteht aus einer Masterdatenbankinstanz und zwei Slavedatenbankinstanzen für die Sicherung der Masterdatenbankinstanz.

Mit {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} können Sie Datenbankcluster in {{site.data.keyword.cloud_notm}} erstellen, Datenbankinstanzen verwalten, Datenbankbenutzer verwalten sowie Datenbanken erstellen und überwachen.

## Datensicherheit und Datenschutz
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} stellt Datenbanken in einer hoch verfügbaren und sicheren Umgebung per Hosting bereit:
<ul>
<li>Von den zugrunde liegenden Technologien wird verhindert, dass von {{site.data.keyword.IBM_notm}} oder einem Drittanbieter auf Ihre Daten zugegriffen werden kann.
<p>Mithilfe der {{site.data.keyword.IBM_notm}} Secure Service Container-Technologie wird das System durch eine manipulationssichere Umgebung geschützt. Der Zugriff auf das System ist eingeschränkt und wird nur über klar strukturierte und REST-konforme APIs aktiviert.</p></li>
<li>Die Daten sind im Ruhezustand und während der Übertragung verschlüsselt.</li>
<li>Von der Systemhardware, der Systemkonfiguration und der Datenbankkonfiguration wird eine hohe Verfügbarkeit sichergestellt.</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## Datenbankcluster erstellen
{: #creating-a-database-cluster-introduction}

Zum Erstellen eines Datenbankclusters geben Sie einfach die erforderlichen Werte in die Ansicht der {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Servicekonfiguration ein und klicken auf **Erstellen**.

Wenn Sie den Datenbankcluster erstellt haben, werden von {{site.data.keyword.IBM_notm}} mindestens ein Hostname und eine Portnummer der erstellten Datenbankinstanzen bereitgestellt. Diese Informationen und die im Katalog angegebenen Benutzerberechtigungsnachweise können Sie jetzt verwenden, um Datenbanken zu erstellen und auf sie zuzugreifen.

## Datenbankcluster verwalten
{: #managing-database-cluster-introduction}

In einem Datenbankcluster können Sie Datenbanken erstellen, die Datenbankinstanzen verwalten und Benutzer erstellen oder löschen.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} enthält einen DBaaS-Manager, vom dem Anforderungen basierend auf den verfügbaren Ressourcen verwaltet und auf intelligente Weise geplant werden.

Sie können Anforderungen an den DBaaS-Manager über eine der folgenden Schnittstellen senden:

- Die [Webbenutzerschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- Die [DBaaS-Manager-APIs (für das Datenbankclustermanagement)](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- Die [{{site.data.keyword.cloud_notm}}-APIs (für das Serviceinstanzmanagement)](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- Das [Befehlszeilenschnittstellen-Plug-in mit dem {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstellentool](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## Auf Datenbank zugreifen
{: #accessing-database-introduction}

Nach dem Erstellen einer PostgreSQL-Datenbank können Sie die Datenbank mithilfe von 'pgAdmin' oder Ihrem bevorzugten PostgreSQL-Tool verwalten.

### Vorbereitungen
{: #accessing-database-introduction-byb}

Beschaffen Sie zum Sicherstellten einer sicheren Datenübertragung eine Datei einer Zertifizierungsstelle (Certificate Authority, CA) über das Dashboard und kopieren Sie sie in ein passendes Verzeichnis.

### Verbindung zu einer Datenbank herstellen
{: #accessing-database-introduction-connect}

Im {{site.data.keyword.ihsdbaas_postgresql_full}}-Dashboard  werden die erforderlichen Informationen zum Herstellen einer Verbindung zu einer Datenbank bereitgestellt.

#### psql-Shell
{: #accessing-database-introduction-connect-psqlshell}

Sie können den folgenden Befehl verwenden:
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
Hierbei gilt Folgendes:
<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> Der Hostname des Datenbankclusters. </dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> Der Benutzername für den Datenbankadministrator, der in der Serviceerstellungsanzeige angegeben wurde. </dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> Die Portnummer des Datenbankclusters. </dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> Der Pfad der Datei der Zertifizierungsstelle. </dd>  
</dl>

**Hinweis:** Vom Befehl `psql` wird nicht das Zertifikat des Datenbankclusters überprüft, wenn die Optionen `sslmode` und `sslrootcert` nicht angegeben sind.

### Weitere Tools
{: #accessing-database-introduction-connect-other}

Für weitere Tools, wie zum Beispiel 'pgAdmin', wird von {{site.data.keyword.ihsdbaas_postgresql_full}} für die Verbindung zum Host die Überprüfung des SSL-Serverzertifikats (*SSL-Serverzertifikatsvalidierung*) unterstützt. Verwenden Sie bei Bedarf die bereitgestellte Datei der Zertifizierungsstelle.
