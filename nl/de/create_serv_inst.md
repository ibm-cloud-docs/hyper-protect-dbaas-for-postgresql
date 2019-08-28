---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: service instance, ibmcloud resource

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Serviceinstanz erstellen
{: #dbaas_cli_create_service}

Verwenden Sie zum Erstellen einer Serviceinstanz wie im folgenden Beispiel dargestellt den Befehl `ibmcloud resource service-instance-create`. Unter Windows wird empfohlen, ein Bash-Terminal wie Cygwin oder Git Bash zu verwenden, um den Befehl einzugeben.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Für die Parameter gelten hierbei die folgenden Definitionen:

| Parameter        |  Definition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  Der Name der Serviceinstanz (durch einen Namen der eigenen Auswahl ersetzen). |
| *hyperp-dbaas-postgresql* | Der Katalogname von {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | Der Planname. Verfügbare Pläne sind: **postgresql-small**, **postgresql-medium** und **postgresql-large**.  (**Hinweis:** Bei Plannamen muss die Groß-/Kleinschreibung beachtet werden.) |
| *us-south*            | Die Position, an der sich die neue Datenbank befindet. (**Hinweis:** Derzeit wird {{site.data.keyword.ihsdbaas_postgresql_full}} nur von **us-south** unterstützt.) |
| *-p*               | Eine gültige JSON-Zeichenfolge, die die Parameter in der folgenden Tabelle enthalten muss. |

<table>
  <tr>
    <th>Parameter "-p"</th>
    <th>Definition</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>Der Name des Datenbankclusters.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>Der Benutzername des Administrators für die Datenbank, die erstellt werden soll.</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>Das Benutzerkennwort des Administrators der Datenbank, die erstellt werden soll. Erstellen Sie ein sicheres Kennwort mit den folgenden Attributen:
        <ul>
          <li>Eine Länge von mindestens **15 Zeichen**</li>
          <li>Mindestens **ein Großbuchstabe**</li>
          <li>Mindestens **ein Kleinbuchstabe**</li>
          <li>Mindestens **eine Zahl**</li>
          <li>Der Benutzername darf nicht Bestandteil des Kennworts sein.</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>Dasselbe Kennwort.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>Der Wert **agreed** gibt an, dass die Lizenzvereinbarung akzeptiert wird, was für die Nutzung von {{site.data.keyword.ihsdbaas_postgresql_full}} erforderlich ist.</td>
  </tr>
</table>

Nach dem Eingeben des Befehls kann sich die neue Serviceinstanz wie im folgenden Beispiel dargestellt vorübergehend in einem inaktiven Status (**inactive**) befinden.

```
Erstellen der Serviceinstanz MYDBaaSIns03 in Ressourcengruppe 'default' des Kontos 'BSS Metering Test Account' als bluemix_ui_metering_test@mailinator.com...
OK
Serviceinstanz MYDBaaSIns03 wurde erstellt.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753
Standort:         USA (Süden)
Status:           Inaktiv
Typ:              Serviceinstanz
Subtyp:
Erstellt:         2019-06-03T06:17:13Z
Aktualisiert:     2019-06-03T06:17:13Z
Letzte Operation:
                  Status          Erstellung wird ausgeführt
                  Aktualisiert    2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

Dies liegt daran, dass es einige Minuten dauert, bis der Cluster vorbereitet ist. Verwenden Sie zum Aktualisieren des Clusterstatus wie im folgenden Beispiel veranschaulicht den Befehl `ibmcloud resource service-instances`:

```
ibmcloud resource service-instances
Abrufen aller Instanzen aller Services in Ressourcengruppe 'default' und alle Standorte unter Konto 'BSS Metering Test Account' als bluemix_ui_metering_test@mailinator.com...
OK
Name           Standort     Status     Typ
MyDBaaSIns03   USA (Süden)  Aktiv      Serviceinstanz
```
{: codeblock}

Für eine erweiterte Sicherheit wird empfohlen, das **Kennwort des Datenbankadministrators** sofort nach der Bereitstellung der Serviceinstanz zu aktualisieren. Dabei müssen dieselben Regeln beachtet werden, die oben für das Festlegen des neuen Kennworts angegeben wurden.
{: note}
