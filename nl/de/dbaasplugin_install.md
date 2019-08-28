---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: DBaaS CLI, Python runtime

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Plug-in für DBaaS-Befehlszeilenschnittstelle installieren
{: #install-dbaas-cli-plugin}

Wenn Sie mit der {{site.data.keyword.cloud}}-Befehlszeilenschnittstelle auf alle DBaaS-Befehle zugreifen möchten, müssen Sie die folgenden Komponenten installieren (Informationen hierzu finden Sie unter [Anweisungen](#dbaas_cli_instr)):

- Python-Laufzeitumgebung (2.7.15 wird empfohlen; 3.x wird **nicht** unterstützt)
- Python Pip-Paketmanagementsystem
- Python Requests-Bibliothek
- DBaaS-CLI-Plug-in

## Anweisungen zum Installieren der DBaaS-CLI-Komponenten (nach Betriebssystem)
{: #dbaas_cli_instr}

- [Unter Linux](#dbaas_cli_linux)
- [Unter Mac OS](#dbaas_cli_macos)
- [Unter Windows](#dbaas_cli_windows)

### Unter Linux:
{: #dbaas_cli_linux}

1. Unter den meisten Linux-Distributionen sind Python und Pip vorinstalliert. Falls dies unter Ihrem Linux-System nicht der Fall ist, führen Sie die folgenden Befehle zur Installation aus:

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Führen Sie den folgenden Befehl aus, um die Python Requests-Bibliothek zu installieren:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Führen Sie den folgenden Befehl aus, um das DBaaS-CLI-Plug-in zu installieren:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Führen Sie den folgenden Befehl aus, um sicherzustellen, dass das DBaaS-CLI-Plug-in ordnungsgemäß installiert wurde:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Vom System wird in der Liste der verfügbaren Befehle `dbaas` angezeigt.

### Unter Mac OS:
{: #dbaas_cli_macos}

1. Wenn Sie noch nicht über Python verfügen, laden Sie die Software anhand der folgenden Anweisungen herunter und installieren Sie sie:

    a. Rufen Sie die Python-Website unter https://www.python.org/downloads/release/python-2715/ auf.

    b. Wählen Sie das entsprechende Mac OS-Installationsprogramm aus, laden Sie es herunter, und führen Sie es aus. Die Installation sollte Pip umfassen.

2. Führen Sie den folgenden Befehl aus, um die Python Requests-Bibliothek zu installieren:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Führen Sie den folgenden Befehl aus, um das DBaaS-CLI-Plug-in zu installieren:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Führen Sie den folgenden Befehl aus, um sicherzustellen, dass das DBaaS-CLI-Plug-in ordnungsgemäß installiert wurde:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Vom System wird in der Liste der verfügbaren Befehle `dbaas` angezeigt.

### Unter Windows:
{: #dbaas_cli_windows}

**Hinweis:** Es wird nur die x86_64-Version von Windows unterstützt.

1. Wenn Sie noch nicht über Python verfügen, laden Sie die Software anhand der folgenden Anweisungen herunter und installieren Sie sie:

    a. Rufen Sie die Python-Website unter https://www.python.org/downloads/release/python-2715/ auf.

    b. Wählen Sie das Installationsprogramm **Windows x86-64 MSI** aus, laden Sie es herunter, und führen Sie es aus.

    c. Geben Sie im Menü zum Anpassen von Python (**Customize Python**) des Assistenten für die Konfiguration von Python (**Python Setup**) an, dass PIP auf einem lokalen Festplattenlaufwerk installiert wird (**pip Will be installed on local hard disk drive**).

2. Verwenden Sie unter Windows nach der Installation von Python das Dialogfenster **Systemvariable bearbeiten**, um die folgenden Werte an den vorhandenen Variablenwert **Pfad** anzuhängen.

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Öffnen Sie zum Installieren der Python Requests-Bibliothek das Fenster **Eingabeaufforderung** und geben Sie den folgenden Befehl ein:

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. Führen Sie den folgenden Befehl aus, um das DBaaS-CLI-Plug-in zu installieren:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. Führen Sie den folgenden Befehl aus, um sicherzustellen, dass das DBaaS-CLI-Plug-in ordnungsgemäß installiert wurde:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Vom System wird in der Liste der verfügbaren Befehle `dbaas` angezeigt.

Detaillierte Informationen zu Befehlen des DBaaS-Befehlszeilenschnittstellen-Plug-ins finden Sie in den [Referenzinformationen zur DBaaS-Befehlszeilenschnittstelle](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
