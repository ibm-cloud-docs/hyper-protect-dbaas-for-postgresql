---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: instance commands, cluster resource, CLI plugin

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}


# Plug-in für {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Befehlszeilenschnittstelle
{: #dbaas_cli_plugin}

Mit dem Plug-in für die {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Befehlszeilenschnittstelle können Sie Informationen zu Datenbanken und Benutzern erstellen, löschen und anzeigen, Details zu Clustern anzeigen, Instanzen starten und stoppen sowie Protokolldateien auflisten und herunterladen.
{:shortdesc}


## Voraussetzungen
{: #prerequisites_dbaas_cli_plugin}

- Installieren Sie die [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-getting-started). Für die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle ist Java SDK 1.7.0 erforderlich. Das Präfix zum Ausführen von Befehlen über die {{site.data.keyword.cloud_notm}}-CLI lautet `ibmcloud`. Sie werden im Terminal benachrichtigt, wenn Aktualisierungen für die `ibmcloud`-Befehlszeilenschnittstelle (CLI) und die zugehörigen Plug-ins verfügbar sind. Halten Sie Ihre CLI stets aktuell, sodass Sie alle verfügbaren Befehle und Flags verwenden können.

- Installieren Sie das {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Befehlszeilenschnittstellen-Plug-in. [DBaaS-Befehlszeilenschnittstellen-Plug-in installieren](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin) enthält Referenzinformationen hierzu. Wenn Sie die aktuelle Version des Plug-ins für die {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Befehlszeilenschnittstelle anzeigen möchten, führen Sie `ibmcloud plugin show dbaas-cli` aus.


## Befehl für die Verwendung des CLI-Plug-ins
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

Mit diesem Befehl wird eine Liste der DBaaS-Befehle angezeigt.

```
ibmcloud help dbaas
```
{: pre}


## Clusterbefehl
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

Bei Verwendung dieses Befehls werden die Details des angegebenen Clusters einschließlich der Informationen zu jedem Replikatmitglied angezeigt.  

```
ibmcloud dbaas cluster-show <ressourcenname>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*Ressourcenname*</dt>
<dd>Der Name der Clusterressource. Verwenden Sie zum Ermitteln des Ressourcennamens den {{site.data.keyword.cloud_notm}}-Befehl `ibmcloud resource service-instances`.</dd>
</dl>

## Datenbankbefehle
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

Bei Verwendung dieses Befehls wird eine Datenbank und optional eine Sammlung erstellt.

```
ibmcloud dbaas database-create <ressourcenname> <datenbankname> [<datensammlung>]
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*datenbankname*</dt>
<dd>Der Name der zu erstellenden Datenbank.</dd>
<dt>*datensammlung*</dt>
<dd>(Optional) Der Name der zu erstellenden Datensammlung.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

Bei Verwendung dieses Befehls wird eine Datenbank gelöscht. Löschen Sie eine Datenbank nicht, wenn diese Datenbank anhand eines Berechtigungsnachweises erstellt wird und dieser Berechtigungsnachweis noch im Gebrauch ist.

```
ibmcloud dbaas database-delete <ressourcenname> <datenbankname>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*datenbankname*</dt>
<dd>Der Name der Datenbank, die gelöscht werden soll.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

Bei Verwendung dieses Befehls werden alle Datenbanken im angegebenen Cluster aufgelistet.

```
ibmcloud dbaas databases-list <ressourcenname>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
</dl>


## Datenbankbenutzerbefehle
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

Bei Verwendung dieses Befehls wird ein Datenbankbenutzer erstellt.

```
ibmcloud dbaas user-create <ressourcenname> <benutzername> <kennwort> [<datenbankname> [<datenbankname> [...]]]
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*benutzername*</dt>
<dd>Der Benutzername, der dem Datenbankbenutzer zugeordnet werden soll, der erstellt wird.</dd>
<dt>*Datenbankname*</dt>
<dd>(Optional) Gibt eine Datenbank an, für die der Benutzer über Lese- und Schreibzugriff verfügt.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

Bei Verwendung dieses Befehls wird ein Datenbankbenutzer gelöscht. Löschen Sie einen Datenbankbenutzer nicht, wenn dieser Datenbankbenutzer anhand eines Berechtigungsnachweises erstellt wird und dieser Berechtigungsnachweis noch im Gebrauch ist.

```
ibmcloud dbaas user-delete <ressourcenname> <benutzername>
```
**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*benutzername*</dt>
<dd>Der Benutzername des Datenbankbenutzers, der gelöscht wird.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

Bei Verwendung dieses Befehls werden alle Datenbankbenutzer aufgelistet.

```
ibmcloud dbaas users-list <ressourcenname>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

Bei Verwendung dieses Befehls werden die Details zu einem Datenbankbenutzer angezeigt.

```
ibmcloud dbaas user-show <ressourcenname> <benutzername>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*benutzername*</dt>
<dd>Der Benutzername des Datenbankbenutzers, der angezeigt wird.</dd>
</dl>


## Instanzbefehle
{: #instance_cmds}

Wenn Sie einen der hier aufgeführten Instanzbefehle verwenden möchten, müssen Sie die Instanz-ID (`instance_id`) kennen. Zum Abrufen des Werts für `instance_id` verwenden Sie zuerst den `ibmcloud`-Befehl zum Auflisten der Namen der Ressourcengruppen für die Serviceinstanzen unter Ihrem Konto und anschließend den Befehl [`cluster_show`](#cluster_show), um den Wert für `instance_id` abzurufen.

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

Bei Verwendung dieses Befehls wird eine aktive Instanz erneut gestartet.

```
ibmcloud dbaas instance-restart <ressourcenname> <instanz-id>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*instanz-id*</dt>
<dd>Die ID der Instanz.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

Bei Verwendung dieses Befehls wird eine gestoppte Instanz gestartet.

```
ibmcloud dbaas instance-start <ressourcenname> <instanz-id>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*instanz-id*</dt>
<dd>Die ID der Instanz.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

Bei Verwendung dieses Befehls wird eine Instanz gestoppt (ein Replikationsmitglied des Clusters).

```
ibmcloud dbaas instance-stop <ressourcenname> <instanz-id>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*instanz-id*</dt>
<dd>Die ID der Instanz.</dd>
</dl>


## Protokollbefehle
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

Bei Verwendung dieses Befehls wird eine Datei von einer Instanz heruntergeladen.

```
ibmcloud dbaas log-get <ressourcenname> <instanz-id> <dateiname>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*instanz-id*</dt>
<dd>Die ID der Instanz.</dd>
<dt>*dateiname*</dt>
<dd>Der Name der Protokolldatei, die heruntergeladen werden soll. Um den Dateinamen der Protokolldatei zu ermitteln, die Sie herunterladen möchten, verwenden Sie den Befehl [ibmcloud dbaas logs-list](#log_list).</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

Bei Verwendung dieses Befehls werden alle Protokolldateien auf einer Instanz aufgelistet. Sie können alle aufgelisteten Dateinamen als Eingabe für den Befehl [ibmcloud dbaas log-get](#log_get) verwenden.

```
ibmcloud dbaas logs-list <ressourcenname> <instanz-id>
```
{: pre}

**Befehlsoptionen**

<dl>
<dt>*ressourcenname*</dt>
<dd>Der Name der Clusterressource.</dd>
<dt>*instanz-id*</dt>
<dd>Die ID der Instanz.</dd>
</dl>
