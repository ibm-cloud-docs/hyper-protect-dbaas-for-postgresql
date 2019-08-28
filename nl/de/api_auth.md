---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: access token, DBaaS Manager APIs, API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Authentifizierung zur Verwendung mit DBaaS-Manager-APIs festlegen
{: #api-auth}

Für die Authentifizierung benötigen Sie einen API-Schlüssel, ein Zugriffstoken und eine Benutzer-ID, um API-Anforderungen abzusetzen.
Führen Sie hierfür die folgenden Anweisungen aus:

1. Generieren Sie einen API-Schlüssel:

   a. Wählen Sie im {{site.data.keyword.cloud}}-Dashboard **Verwalten > Zugriff (IAM)** aus.

      Das Dashboard 'Zugriff (IAM)' wird angezeigt.

   b. Wählen Sie im seitlichen Navigationsfenster des Dashboards 'Zugriff (IAM)' **{{site.data.keyword.cloud_notm}}-API-Schlüssel** aus.

   c. Klicken Sie auf **{{site.data.keyword.cloud_notm}}-API-Schlüssel erstellen**.

      Das Dialogfenster 'API-Schlüssel erstellen' wird angezeigt.

   d. Geben Sie im Dialog 'API-Schlüssel erstellen' einen Namen und eine Beschreibung für den API-Schlüssel ein und klicken Sie auf **Erstellen**.

   e. Klicken Sie auf **Download**, um den API-Schlüssel herunterzuladen und zu speichern, oder klicken Sie auf **Kopieren**, um den API-Schlüssel in die Zwischenablage zu kopieren.

      Als Ergebnis dieser Operation wird eine JSON-Datei zurückgegeben, die der im folgenden Beispiel ähnelt:

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      Der Wert, der `apiKey` zugewiesen ist, ist Ihr API-Schlüssel. **Wichtig:** Notieren  Sie diesen Wert, bevor Sie das Fenster schließen.

2. Beschaffen Sie zum Sicherstellten einer sicheren Datenübertragung eine Datei einer Zertifizierungsstelle (Certificate Authority, CA) über das {{site.data.keyword.ihsdbaas_postgresql_full}}-Dashboard und kopieren Sie sie in ein passendes Verzeichnis, zum Beispiel **/etc/ssl/certs/**.

3. Rufen Sie unter Verwendung der GET-Operation für den Pfad '/auth/token' ein Zugriffstoken und eine Benutzer-ID ab:

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    Als Ergebnis dieser Operation werden ein Zugriffstoken und eine Benutzer-ID zurückgegeben, die dem im folgenden Beispiel ähneln:

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. Speichern Sie die Werte des Zugriffstokens und der Benutzer-ID für eine zukünftige Verwendung.
