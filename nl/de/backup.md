---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: backup, disaster recovery, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:tip: .tip}


# Datenbanken mithilfe von {{site.data.keyword.cos_full_notm}} sichern und wiederherstellen
{: #backup_postgresql_databases}

Vom {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Service wird in Abständen von 24 Stunden automatisch eine Sicherung der vollständigen Datenbank ausgelöst. Diese verschlüsselten Sicherungen sind für die letzten sieben Tage verfügbar und werden im lokalen Speicher in allen Verfügbarkeitszonen der unterstützten Region redundant zur Verfügung gestellt.
{: shortdesc}

Wenn Sie die Disaster-Recovery-Funktionen erweitern und die Daten außerhalb der unterstützten Region sichern möchten, können Sie den [{{site.data.keyword.cos_full_notm}}-Service](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} verwenden, um Daten in einer anderen Region zu speichern, indem Sie die nachfolgend beschriebenen Schritte ausführen.

## Vorbereitungen
{: #backup_postgresql_before_begin}

Um die {{site.data.keyword.postgresql}}-Befehle zum Durchführen der Sicherung zu verwenden, müssen Sie zuerst {{site.data.keyword.postgresql}} auf Ihr System herunterladen und installieren. Weitere Informationen hierzu finden Sie auf der [{{site.data.keyword.postgresql}}-Website](https://www.postgresql.org/download/){: external}.

## Schritt 1: Erstellen einer Speicherauszugsdatei zum Sichern der ursprünglichen Datenbanken
{: #step1_create_dump_file_backup_postgresql}

Verwenden Sie den folgenden `pg_dump`-Befehl, um eine Speicherauszugsdatei zu erstellen, die die Datenbanken enthält, die gesichert werden sollen.

```
pg_dump -h <hostname> -p <port> -U <benuzername> -d <datenbankname> -f <speicherauszugsdatei>
```
{: pre}

In der folgenden Tabelle werden die Variablen aufgeführt, die im Befehl verwendet werden.

|Variablen|Beschreibung|Beispiel|
|---------|-----------|-------|
|*hostname*|Der ferne Server, auf dem sich die ursprünglichen Datenbanken befinden. Sie müssen eine Verbindung zum Host herstellen, um die Daten abzurufen. Die Hostadresse finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Die Portnummer zum Herstellen einer Verbindung zum Host. Den Port finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|25050|
|*benutzername*|Der Benutzername für den Zugriff auf die ursprünglichen Datenbanken. Der Benutzer muss über die Berechtigung CONNECT für die Datenbank und die Berechtigung SELECT für die Tabellen verfügen.|mein_benutzer|
|*datenbankname*|Der Name der Datenbank, die gesichert werden soll.|meine_datenbank|
|*speicherauszugsdatei*|Die `.dump`-Datei, in der die ursprünglichen Daten gespeichert werden. Sie können relative oder absolute Pfade verwenden, um die Datei anzugeben.|./pgdump.dump|
{: caption="Tabelle 1. Zum Erstellen einer Speicherauszugsdatei erforderliche Variablen"}

Weitere Informationen zu Benutzerberechtigungen finden Sie in der [Dokumentation zu {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Schritt 2: Erstellen einer neuen {{site.data.keyword.cos_full_notm}}-Instanz
{: #step2_create_object_storage_backup_postgresql}

Sie müssen die Instanz in einer Region erstellen, bei der es sich nicht um die Region handelt, in der die {{site.data.keyword.ihsdbaas_postgresql_full}}-Serviceinstanz aktuell bereitgestellt wird. Sie können die folgenden Schritte ausführen:

1. [Erstellen Sie eine neue {{site.data.keyword.cos_short}}-Instanz in der Cloud](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Erstellen Sie ein Bucket](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) in einer anderen Region.
3. [Erstellen Sie einen Serviceberechtigungsnachweis](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) und speichern Sie die Werte für `access_key_id` und `secret_access_key` zur späteren Verwendung.
4. Installieren Sie einen S3-Client.
5. Verwenden Sie den S3-Client und die Zugriffsschlüssel, um eine Verbindung zum {{site.data.keyword.cos_short}}-Endpunkt in der Cloud für das Bucket herzustellen, das Sie zuvor erstellt haben.
6. Verwenden Sie den S3-Client, um die [{{site.data.keyword.postgresql}}-Sicherungsdatei](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload), die Sie in [Schritt 1](#step1_create_dump_file_backup_postgresql) erstellt haben, in das Bucket hochzuladen.

In der [Dokumentation zu {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started) finden Sie weitere Informationen.

Durch die Ausführung dieses Schritts sichern Sie die Daten erfolgreich in einer {{site.data.keyword.cos_short}}-Instanz in der Cloud in einer anderen Region. Wenn Sie die Daten aus der {{site.data.keyword.cos_short}}-Instanz in der Cloud in einer {{site.data.keyword.ihsdbaas_postgresql_full}}-Instanz wiederherstellen möchten, lesen Sie die Details im nachfolgend beschriebenen Schritt 3.

## Schritt 3: Daten aus der {{site.data.keyword.cos_short}}-Instanz in der Cloud in einer {{site.data.keyword.ihsdbaas_postgresql_full}}-Instanz wiederherstellen
{: #step3_restore_data_from_cos_postgresql}

Sie müssen zuerst die Sicherungsdatei aus dem {{site.data.keyword.cos_short}}-Bucket in der Cloud auf Ihre lokale Maschine herunterladen. Anschließend verwenden Sie den Befehl `psql`, um die Daten wiederherzustellen.

```
psql -h <hostname> -p <port> -U <benutzername> -d <datenbankname> -f <speicherauszugsdatei>
```
{: pre}

In der folgenden Tabelle werden die Variablen aufgeführt, die im Befehl verwendet werden.

|Variablen|Beschreibung|Beispiel|
|---------|-----------|-------|
|*hostname*|Der Server des DBaaS-Managers, auf dem sich der Zielcluster befindet. Die Hostadresse finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Die Portnummer zum Herstellen einer Verbindung zum Host. Die Portnummer finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|25003|
|*benutzername*|Der Benutzername für den Zugriff auf die Zieldatenbank.|neuer_benutzer|
|*datenbankname*|Bei der Datenbank kann es sich um eine beliebige Datenbank handeln, für die der Benutzer über die Berechtigung CONNECT verfügt. Die `psql`-Sitzung ändert sie automatisch in die Zieldatenbank, in der die Daten wiederhergestellt werden sollen.|meine_datenbank|
|*speicherauszugsdatei*|Die `.dump`-Datei, die Sie aus dem {{site.data.keyword.cos_short}}-Bucket in der Cloud heruntergeladen haben. Sie können relative oder absolute Pfade verwenden, um die Datei anzugeben.|./pgdump.dump|
{: caption="Tabelle 2. Zum Wiederherstellen der Daten einer Speicherauszugsdatei erforderliche Variablen"}

## Weitere Schritte
{: #whats_next_backup_postgresql}

Nach dem Abschluss von [Schritt 3](#step3_restore_data_from_cos_postgresql) können Sie eine Verbindung zum Datenbankcluster herstellen, um zu überprüfen, ob die Daten erfolgreich wiederhergestellt wurden.
