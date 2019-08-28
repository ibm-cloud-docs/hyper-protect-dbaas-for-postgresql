---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Serviceinstanzen
{: #dbaas_webui_service}

## Serviceinstanz erstellen
{: #dbaas_webui_create_service}

<ol>
<li>Klicken Sie auf den {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Katalogeintrag, um die Ansicht für die Serviceerstellung zu öffnen.</li>
<li>Geben Sie die folgenden Werte ein.
  <dl>
    <dt>Servicename:</dt>
    <dd>Ein Name für den Datenbankservice.</dd>

    <dt>Wählen Sie eine Region bzw. einen Standort für die Bereitstellung aus:</dt>
    <dd>Wählen Sie das Rechenzentrum aus, in dem sich die Datenbank befinden soll.</dd>

    <dt>Wählen Sie eine Ressourcengruppe aus:</dt>
    <dd>Wenn keine Ressourcengruppe ausgewählt werden kann ist, können Sie eine Ressourcengruppe im {{site.data.keyword.cloud_notm}}-Dashboard erstellen.</dd>

    <dt>Tags:</dt>
    <dd>Tags sind optional. Weitere Informationen zum Tagging finden Sie unter [Ressourcen mit Tags versehen](/docs/resources?topic=resources-tag#tag).</dd>

    <dt>Cluster-/Replikatgruppenname:</dt>
    <dd>Ein Name für die Serviceinstanz.</dd>

    <dt>Datenbankadministrationsname:</dt>
    <dd>Eine Benutzer-ID für den Datenbankadministrator (DBA).
    <p>**Hinweis:** Der Datenbankadministrator verfügt nicht über die Berechtigung SUPERUSER. Die Berechtigungen für den Datenbankadministrator sind auf INHERIT, CREATEROLE, CREATEDB, LOGIN und REPLICATION beschränkt.</p></dd>

    <dt>Datenbankadministratorkennwort:</dt>
    <dd>
    <p>Das Kennwort zur Benutzer-ID des Datenbankadministrators. Erstellen Sie ein sicheres Kennwort mit den folgenden Attributen:
      <ul>
        <li>Eine Länge von mindestens **15 Zeichen**</li>
        <li>Mindestens **einen Großbuchstaben**</li>
        <li>Mindestens **einen Kleinbuchstaben**</li>
        <li>Mindestens **eine Zahl**</li>
        <li>Der Benutzername darf nicht Bestandteil des Kennworts sein.</li>
      </ul>
    </p>
    </dd>

    <dt>Kennwort bestätigen:</dt>
    <dd>Bestätigen Sie das Kennwort für die Benutzer-ID des Datenbankadministrators.</dd>

    <dt>Lizenzvereinbarung:</dt>
    <dd>Wählen Sie nach dem Lesen der Lizenzvereinbarung das Kästchen zum Bestätigen der Vereinbarung aus.</dd>

    <dt>Preistarife:</dt>
    <dd>In den Preistarifen werden verschiedene Preiskategorien für Datenbanken des Typs 'PostgreSQL' angeboten. Wählen Sie den aus, der ihren Bedürfnissen am besten entspricht.</dd>
  </dl>
</li>
<li>Klicken Sie auf **Erstellen**.
<p>Nachdem ein Dialogfeld mit der Nachricht, dass die Bereitstellung des Service einige Zeit in Anspruch nimmt, eingeblendet wurde, wird das {{site.data.keyword.cloud_notm}}-Dashboard mit der Ressourcenliste angezeigt. Die von Ihnen erstellte Serviceinstanz wird im Abschnitt **Services** in der Liste aufgeführt. Wenn der Status des Service **Bereitgestellt** lautet, ist die Instanz zur Verwendung bereit.</p>
</li>

<li>Wählen Sie den Service zum Anzeigen des {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}-Dashboards aus.</li>
</ol>

Für eine erweiterte Sicherheit wird empfohlen, das **Kennwort des Datenbankadministrators** sofort nach der Bereitstellung der Serviceinstanz zu aktualisieren. Dabei müssen dieselben Regeln beachtet werden, die oben für das Festlegen des neuen Kennworts angegeben wurden.
{: note}

## Alle Serviceinstanzen auflisten
{: #dbaas_webui_list_service}

Öffnen Sie das {{site.data.keyword.cloud_notm}}-Dashboard, um eine Liste der erstellten Serviceinstanzen anzuzeigen:

<ol>
	<li>Klicken Sie auf die Schaltfläche mit den drei Balken in der linken oberen Ecke der Konsole.</li>
	<li>Wählen Sie das Dashboard aus.</li>
	<li>Wählen Sie die Services aus.</li>
</ol>

## Detaillierte Informationen einer Serviceinstanz anzeigen
{: #dbaas_webui_show_detail_service}

1. Klicken Sie auf den Zielinstanznamen, um das Service-Dashboard aufzurufen.
2. Wählen Sie **Verwalten** in der linken Navigationsleiste aus. Die allgemeinen Informationen werden auf der Registerkartenseite **Übersicht** angezeigt.
3. Wählen Sie die Registerkarte **Instanzen** aus, um detaillierte Informationen anzuzeigen.


## Serviceinstanz löschen
{: #dbaas_webui_delete_service}

1. Rufen Sie die {{site.data.keyword.cloud_notm}}-Ressourcenliste durch Klicken auf **Navigationsmenüs > Ressourcenliste** auf.
2. Öffnen Sie den Twister **Service**, um die Serviceinstanzen anzuzeigen.
3. Wählen Sie die Serviceinstanz aus, die Sie löschen möchten.
4. Klicken Sie auf die drei Punkte auf der rechten Seite.
5. Klicken Sie auf **Löschen**.
