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


# Installazione del plugin CLI DBaaS
{: #install-dbaas-cli-plugin}

Per accedere a una serie completa di comandi DBaaS quando utilizzi la CLI {{site.data.keyword.cloud}},
devi installare i seguenti componenti
(vedi [Istruzioni](#dbaas_cli_instr)):

- Runtime Python (consigliata la 2.7.15; la versione 3.x **non** è supportata)
- Sistema di gestione del pacchetto Pip Python
- Libreria delle richieste Python
- Plugin CLI DBaaS

## Istruzioni per l'installazione dei componenti CLI DBaaS (per sistema operativo)
{: #dbaas_cli_instr}

- [Su Linux](#dbaas_cli_linux)
- [Su MacOS](#dbaas_cli_macos)
- [Su Windows](#dbaas_cli_windows)

### Su Linux:
{: #dbaas_cli_linux}

1. La maggior parte delle distribuzioni dispongono di Python e Pip preinstallati. Se non è così nel tuo caso, utilizza questi comandi per installarli:

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Per installare la libreria delle richieste Python, utilizza questo comando:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Per installare il plugin CLI DBaaS, utilizza questo comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Per confermare che il plugin CLI DBaaS è stato installato correttamente, utilizza questo comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Il sistema visualizza `dbaas` nell'elenco dei comandi disponibili.

### Su MacOS:
{: #dbaas_cli_macos}

1. Se ancora non disponi di Python, scaricalo e installalo seguendo queste istruzioni:

    a. Vai al sito web Python a questo URL: https://www.python.org/downloads/release/python-2715/

    b. Seleziona il programma di installazione MacOS appropriato, scaricalo ed eseguilo. L'installazione dovrebbe includere Pip.

2. Per installare la libreria delle richieste Python, utilizza questo comando:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Per installare il plugin CLI DBaaS, utilizza questo comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Per confermare che il plugin CLI DBaaS è stato installato correttamente, utilizza questo comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Il sistema visualizza `dbaas` nell'elenco dei comandi disponibili.

### Su Windows:
{: #dbaas_cli_windows}

**Nota:** è supportata solo la versione x86_64 di Windows.

1. Se ancora non disponi di Python, scaricalo e installalo seguendo queste istruzioni:

    a. Vai al sito web Python a questo URL: https://www.python.org/downloads/release/python-2715/

    b. Seleziona il programma di installazione **Windows x86-64 MSI**, scaricalo ed eseguilo.

    c. Nel menu **Customize Python** della procedura guidata **Python Setup**, specifica: **pip Will be installed on local hard disk drive**

2. Dopo aver installato Python, utilizza la tua finestra di dialogo **Modifica variabile di sistema** di Windows
   per accodare i seguenti valori al valore della variabile **Path** esistente:

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Per installare la libreria delle richieste Python, apri la finestra **Prompt dei comandi** ed immetti questo comando:

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. Per installare il plugin CLI DBaaS, utilizza questo comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. Per confermare che il plugin CLI DBaaS è stato installato correttamente, utilizza questo comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   Il sistema visualizza `dbaas` nell'elenco dei comandi disponibili.

Per informazioni dettagliate sui comandi del plugin CLI DBaaS, puoi fare riferimento alla [Guida di riferimento API DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
