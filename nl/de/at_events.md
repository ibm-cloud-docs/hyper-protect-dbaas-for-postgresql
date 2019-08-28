---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse
{: #activity-tracker-events}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um zu verfolgen, wie Benutzer und Anwendungen mit dem {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} interagieren.
{: shortdesc}

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service erfasst vom Benutzer eingeleitete Aktivitäten, mit denen der Status eines Service in {{site.data.keyword.cloud_notm}} geändert wird. Weitere Informationen zur Bereitstellung des {{site.data.keyword.cloudaccesstrailshort}}-Service finden Sie in der [Dokumentation zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started). Da der {{site.data.keyword.ihsdbaas_postgresql_full}}-Service derzeit im Rechenzentrum Dallas zur Verfügung gestellt wird, müssen Sie **us-south** als Region für die Erfassung von Protokollen auswählen. 

## Liste der Ereignisse
{: #list-activity-tracker-events}

In der folgenden Tabelle werden die Aktionen aufgeführt, die das Generieren von Ereignissen auslösen:

| Aktion                 | Beschreibung                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | Erstellen eines Datenbankclusters                 |
| `cluster.delete` | Löschen eines Datenbankclusters                 |
| `database.create` | Erstellen einer Datenbank                  |
| `database.delete` | Löschen einer Datenbank                  |
| `user.create`     | Erstellen eines Datenbankbenutzers                    |
| `user.delete`     | Löschen eines Datenbankbenutzers                    |
| `instance.start` | Starten einer Datenbankserviceinstanz         |
| `instance.stop`  | Stoppen einer Datenbankserviceinstanz          |
| `instance.restart`  | Neustart einer Datenbankserviceinstanz          |
| `log.get`       | Download einer Protokolldatei |
{: caption="Tabelle 1. Aktionen, die {{site.data.keyword.cloudaccesstrailfull_notm}}-Ereignisse generieren"}

Für die Ereignisse `cluster.create` und `cluster.delete` zeichnet der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service den Kontonamen und die IP-Adresse des Benutzers, der die Aktion ausführt, nicht auf. Die Werte für `initiator.name` und `host.address` im Protokoll geben die Service-ID und die IP-Adresse von Cloud Broker an.
{: note}

## Wo die Ereignisse angezeigt werden
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse stehen in der {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** zur Verfügung, die in der {{site.data.keyword.cloud_notm}}-Region verfügbar ist, in der die Ereignisse generiert werden.
