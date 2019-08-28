---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Datenbankinstanzen
{: #dbaas-webui-database-instances}

## Vorbereitungen
{: #webui-database-instances-byb}

Wählen Sie im {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Dashboard die Registerkarte 'Instanzen' aus.

## Datenbankinstanz starten
{: #webui-start-database-instance}

1. Wählen Sie die Datenbankinstanz aus.
2. Klicken Sie auf die drei Punkte am rechten Ende der Zeile und wählen Sie anschließend **Starten** aus.

## Datenbankinstanz stoppen
{: #webui-stop-database-instance}

1. Wählen Sie die Datenbankinstanz aus.
2. Klicken Sie auf die drei Punkte am rechten Ende der Zeile und wählen Sie anschließend **Stoppen** aus. Wenn es sich um einen Primärknoten handelt, können Sie auch **Stopp erzwingen** auswählen.

## Datenbankinstanz erneut starten
{: #webui-restart-database-instance}

1. Wählen Sie die Datenbankinstanz aus.
2. Klicken Sie auf die drei Punkte am rechten Ende der Zeile und wählen Sie anschließend **Erneut starten** aus.

## Protokoll herunterladen
{: #webui-download-log}

1. Wählen Sie die Datenbankinstanz aus.
2. Wählen Sie das **Startdatum** und das **Enddatum** aus, um die Protokolle anhand des Datums zu filtern.
3. Wählen Sie die Protokolle aus, die heruntergeladen werden sollen, indem Sie auf das **Kontrollkästchen** vor dem Namen des jeweiligen Protokolls klicken.
4. Klicken Sie auf die Schaltfläche für den **Download**.

## Status der Instanz überprüfen
{: #webui-check-instance-status}

Der farbige Punkt in der Instanzanzeige gibt den Status der Instanz an. Anhand der folgenden Tabelle können Sie den Instanzstatus überprüfen.

|Farbe|Status|Aktion|
|-----|------|------|
|Grün|Die Instanz ist aktiv.|Sie können die Instanz stoppen oder neu starten.|
|Gelb|Die Instanz ist gestoppt.|Sie können die Instanz starten.|
|Rot|Bei der Instanz ist ein Fehler aufgetreten.|In [Unterstützung anfordern](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support) finden Sie weitere Informationen.|
{: caption="Tabelle 1. Statusfarben"}
