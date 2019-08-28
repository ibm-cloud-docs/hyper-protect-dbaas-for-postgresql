---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

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

# Identity and Access Management-Rollen und -Aktionen
{: #iam}

Der Zugriff auf {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Serviceinstanzen für Benutzer in Ihrem Konto wird mithilfe von {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) gesteuert. Jedem Benutzer, der auf den {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Service in Ihrem Konto zugreift, muss eine Zugriffsrichtlinie mit einer definierten IAM-Rolle zugewiesen werden. Die Richtlinie bestimmt, welche Aktionen ein Benutzer im Kontext des von Ihnen ausgewählten Service bzw. der von Ihnen ausgewählten Instanz ausführen kann. Die zulässigen Aktionen werden vom {{site.data.keyword.cloud_notm}}-Service angepasst und als Operationen definiert, die für den Service ausgeführt werden dürfen. Die Aktionen werden dann IAM-Benutzerrollen zugeordnet.
{: shortdesc}

Richtlinien machen es möglich, dass Zugriff auf verschiedenen Ebenen erteilt werden kann. Zu den Optionen gehört z. B. Folgendes:

* Zugriff auf alle Instanzen des Service in Ihrem Konto
* Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto
* Zugriff auf eine bestimmte Ressource in einer Instanz

Nach der Definition des Gültigkeitsbereichs der Zugriffsrichtlinie weisen Sie eine Rolle zu, die die Zugriffsebene des Benutzers bestimmt. In den folgenden Tabellen wird beschrieben, welche Aktionen die einzelnen Rollen innerhalb des {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Service zulassen.

In der folgenden Tabelle sind Aktionen beschrieben, die Plattformmanagementrollen zugeordnet sind. Plattformmanagementrollen ermöglichen es Benutzern, Aufgaben für Serviceressourcen auf Plattformebene durchzuführen. Hierzu gehören beispielsweise das Zuweisen von Benutzerzugriffsberechtigungen für den Service, das Erstellen oder Löschen von Instanzen und das Binden von Instanzen an Anwendungen.

|Plattformmanagementrolle|Beschreibung der Aktionen|Besipielaktionen                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Anzeigeberechtigter                  |Serviceinstanzen anzeigen, nicht jedoch ändern|<ul><li>Cluster auflisten</li><li>Details für einen Cluster anzeigen</li></ul>|
|Bearbeiter                  |Alle Plattformaktionen ausführen mit Ausnahme der Kontoverwaltung und der Zuweisung von Zugriffsrichtlinien|<ul><li>Service an einen Cluster binden</li></ul>|
|Operator                |Plattformaktionen ausführen, die für die Konfiguration und den Betrieb von Serviceinstanzen erforderlich sind, z. B. Anzeigen eines Service-Dashboards|<ul><li>Service an einen Cluster binden</li></ul>|
|Administrator           |Alle Plattformaktionen basierend auf der Ressource ausführen, der diese Rolle zugewiesen ist, einschließlich dem Zuweisen von Zugriffsrichtlinien zu anderen Benutzern|<ul><li>Cluster entfernen</li><li>Cluster erstellen</li><li>Benutzerzugriffsrichtlinien aktualisieren</li><li>Alle Aktionen, die ein Anzeigeberechtigter, Bearbeiter und Operator ausführen kann</li></ul>|
{: caption="Tabelle 1. IAM-Benutzerrollen und Aktionen"}

Informationen zum Zuweisen von Benutzerrollen in der Benutzerschnittstelle finden Sie in [Zugriff auf Ressourcen verwalten](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
