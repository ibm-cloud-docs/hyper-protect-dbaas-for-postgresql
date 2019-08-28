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


# Istanze del database
{: #dbaas-webui-database-instances}

## Prima di cominciare
{: #webui-database-instances-byb}

Nel dashboard {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, seleziona la scheda Instances.

## Avvio di un'istanza del database
{: #webui-start-database-instance}

1. Seleziona l'istanza del database.
2. Fai clic sui tre punti alla destra della riga e seleziona **Start**.

## Arresto di un'istanza del database
{: #webui-stop-database-instance}

1. Seleziona l'istanza del database.
2. Fai clic sui tre punti alla destra della riga e seleziona **Stop**. Se si tratta di un nodo primario, puoi anche selezionare **Force stop**.

## Riavvio di un'istanza del database
{: #webui-restart-database-instance}

1. Seleziona l'istanza del database.
2. Fai clic sui tre punti alla destra della riga e seleziona **Restart**.

## Scaricamento del log
{: #webui-download-log}

1. Seleziona l'istanza del database.
2. Seleziona la data di inizio (**Start date**) e la data di fine (**End date**) per filtrare i log in base al tempo.
3. Seleziona i log che vuoi scaricare facendo clic sulla **casella di spunta** prima del nome del log.
4. Fai clic sul pulsante **Download**.

## Controllo dello stato dell'istanza
{: #webui-check-instance-status}

Il punto colorato sul pannello dell'istanza indica lo stato dell'istanza. Puoi fare riferimento alla seguente tabella per controllare lo stato dell'istanza.

|Colore|Stato|Azione|
|-----|------|------|
|Verde|L'istanza è in esecuzione.|Puoi arrestare o riavviare l'istanza.|
|Giallo|L'istanza è arrestata.|Puoi avviare l'istanza.|
|Rosso|L'istanza ha riscontrato un problema.|Puoi fare riferimento a [Come ottenere aiuto e supporto](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Tabella 1. Il colore dello stato"}
