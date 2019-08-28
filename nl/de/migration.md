---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: migrate, beta, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# {{site.data.keyword.postgresql}}-Datenbanken auf {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} migrieren
{: #migration_postgre}

Lesen Sie diesen Abschnitt, wenn Sie {{site.data.keyword.postgresql}}-Datenbanken verwenden und Details zur Migration auf {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} erfahren möchten. Wenn auf der Plattform {{site.data.keyword.postgresql}}-Datenbankservices bereitgestellt werden, ist der Standort, an dem die {{site.data.keyword.postgresql}}-Datenbanken gehostet werden, ohne Bedeutung.
{: shortdesc}

## Vorbereitungen
{: #migration_postgre_before_begin}

Wenn Sie {{site.data.keyword.postgresql}}-Befehle zum Durchführen der Migration verwenden möchten, müssen Sie zuerst {{site.data.keyword.postgresql}} auf die Maschine herunterladen und installieren. Weitere Informationen hierzu finden Sie auf der [{{site.data.keyword.postgresql}}-Website](https://www.postgresql.org/download/){: external}.

## Schritt 1: Erstellen einer Speicherauszugsdatei zum Wiederherstellen der ursprünglichen Datenbanken
{: #step1_create_dump_file}

Verwenden Sie den folgenden Befehl `pg_dump`, um eine Speicherauszugsdatei zu erstellen, die die Datenbanken enthält, die wiederhergestellt werden sollen.

```
pg_dump -h <hostname> -p <port> -U <benuzername> -d <datenbankname> -f <speicherauszugsdatei>
```
{: pre}

In der folgenden Tabelle werden die Variablen aufgeführt, die im Befehl verwendet werden.

|Variablen|Beschreibung|Beispiel|
|---------|-----------|-------|
|*hostname*|Der ferne Server, auf dem sich die ursprünglichen Datenbanken befinden. Sie müssen eine Verbindung zum Host herstellen, um die Daten abzurufen. Wenn die Datenbanken in einer {{site.data.keyword.ihsdbaas_full}}-Beta-Instanz bereitgestellt werden, finden Sie die Hostadresse auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Die Portnummer zum Herstellen einer Verbindung zum Host. Wenn die Datenbanken in einer {{site.data.keyword.ihsdbaas_full}}-Beta-Instanz bereitgestellt werden, finden Sie den Port auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|25050|
|*benutzername*|Der Benutzername für den Zugriff auf die ursprünglichen Datenbanken. Der Benutzer muss über die Berechtigung CONNECT für die Datenbank und die Berechtigung SELECT für die Tabellen verfügen.|mein_benutzer|
|*datenbankname*|Der Name der Datenbank, die Sie migrieren möchten.|meine_datenbank|
|*speicherauszugsdatei*|Die `.dump`-Datei, in der die ursprünglichen Daten gespeichert werden. Sie können relative oder absolute Pfade verwenden, um die Datei anzugeben.|./pgdump.dump|
{: caption="Tabelle 1. Zum Erstellen einer Speicherauszugsdatei erforderliche Variablen"}

Weitere Informationen zu Benutzerberechtigungen finden Sie in der [Dokumentation zu {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Schritt 2: Erstellen einer neuen Serviceinstanz in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Vor dem Wiederherstellen der Daten müssen Sie eine neue Serviceinstanz in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} als Zieldatenbankcluster erstellen. Für die Erstellung der neuen Serviceinstanz können Sie eine der folgenden Optionen auswählen:
- [Die Webbenutzerschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [Die DBaaS-Manager-APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [Das CLI-Plug-in mit der {{site.data.keyword.cloud_notm}}-CLI](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

Wenn Sie die neue Serviceinstanz erstellen, müssen Sie den Clusternamen, den Administratornamen und das Kennwort festlegen. Sie müssen nicht unbedingt mit den Angaben in der ursprünglichen Instanz identisch sein. Dies hat keine Auswirkungen auf die Migration. Wenn die Migration abgeschlossen ist, werden die Datenbanken dem neuen Administrator zugeordnet.

## Schritt 3: Erstellen der Datenbanken in der neuen Serviceinstanz
{: #step3_create_database}

Nach der Erstellung der neuen Serviceinstanz müssen Sie neue Datenbanken erstellen. Die Datenbanken müssen denselben Namen wie die ursprünglichen Datenbanken aufweisen. Der Benutzer muss über die Berechtigung CREATE verfügen und muss nicht mit dem Benutzer identisch sein, der die Speicherauszugsdatei erstellt hat. Zur Ausführung dieser Task können Sie eine der folgenden Optionen verwenden:
- [Die Webbenutzerschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [Die DBaaS-Manager-APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [Das CLI-Plug-in mit der {{site.data.keyword.cloud_notm}}-CLI](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

Für die Erstellung neuer Benutzer stehen die folgenden Möglichkeiten zur Verfügung: die [Webbenutzerschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), die [DBaaS-Manager-APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, das [Befehlszeilenschnittstellen-Plug-in mit der {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create) und der [{{site.data.keyword.postgresql}}-Befehl](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Schritt 4: Wiederherstellen der Daten aus der Speicherauszugsdatei in eine neue Serviceinstanz
{: #step4_restore_data}

Verwenden Sie den Befehl `psql`, um die Daten aus der Speicherauszugsdatei wiederherzustellen, die in [Schritt 1](#step1_create_dump_file) erstellt wurde.

```
psql -h <hostname> -p <port> -U <benutzername> -d <datenbankname> -f <speicherauszugsdatei>
```
{: pre}

In der folgenden Tabelle werden die Variablen aufgeführt, die im Befehl verwendet werden.

|Variablen|Beschreibung|Beispiel|
|---------|-----------|-------|
|*hostname*|Der Server des DBaaS-Managers, auf dem sich der Zielcluster befindet. Die Hostadresse finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Die Portnummer zum Herstellen einer Verbindung zum Host. Die Portnummer finden Sie auf der Übersichtsseite der Benutzerschnittstelle der Clusterinstanz.|25003|
|*benutzername*|Der Benutzername für den Zugriff auf die Zieldatenbank. Sie können denselben Benutzer verwendet, der die Zieldatenbank in [Schritt 3](#step3_create_database) erstellt.|neuer_benutzer|
|*datenbankname*|Bei der Datenbank kann es sich um eine beliebige Datenbank handeln, für die der Benutzer über die Berechtigung CONNECT verfügt. Von der `psql`-Sitzung wird automatisch zu der Zieldatenbank gewechselt, die in [Schritt 3](#step3_create_database) erstellt wurde.|meine_datenbank|
|*speicherauszugsdatei*|Die `.dump`-Datei, die Sie in [Schritt 1](#step1_create_dump_file) erstellen. Sie können relative oder absolute Pfade verwenden, um die Datei anzugeben.|./pgdump.dump|
{: caption="Tabelle 2. Zum Wiederherstellen der Daten einer Speicherauszugsdatei erforderliche Variablen"}

## Weitere Schritte
{: #whats_next_migration_postgre}

Nach der Migration können Sie eine Verbindung zum neuen Datenbankcluster herstellen, um zu überprüfen, ob die Daten erfolgreich migriert wurden.
