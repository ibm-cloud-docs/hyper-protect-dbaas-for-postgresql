---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Monitoraggio del database
{: #dbaas-webui-database-monitor}

Dopo aver abilitato il monitoraggio del database, puoi visualizzare le metriche del database utilizzando Grafana.
{: shortdesc}

## Prima di cominciare
{: #webui-database-monitoring-byb}

1.  Assicurati di avere accesso a un'organizzazione e a uno spazio Cloud Foundry in Dallas (us-south).
    Per informazioni su come ottenere tale accesso, vedi [Gestione dell'accesso a Cloud Foundry](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}.

2.  Assicurati che tutte le istanze del cluster di database siano in esecuzione.

3.  Nel dashboard {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, seleziona la scheda Monitoring.

## Abilitazione del monitoraggio del database
{: #webui-enable-database-monitoring}

Nel caso venga visualizzato il messaggio **Monitoring is disabled** nella scheda Monitoring:

1. Fai clic su **Enable**.
2. Nella finestra Enable Monitoring, seleziona la tua organizzazione e il tuo spazio e fai clic su **Submit**.


## Visualizzazione delle metriche del database
{: #webui-view-database-metrics}

Esistono due modi per visualizzare le metriche in Grafana:

- Copia il link visualizzato ed apri una nuova scheda o finestra e incollalo nel browser.
- Fai clic su **View in Grafana**.

Per visualizzare le metriche in un nuovo dashboard in Grafana, seleziona l'icona Grafana in alto a sinistra e seleziona **Dashboards > New**.
Potrebbe essere necessario un po' di tempo prima che i tuoi ID del cluster di database e ID istanza vengano visualizzati e potresti dover ricaricare il dashboard.

Per ulteriori informazioni sull'utilizzo di Grafana, vedi [Monitoraggio di {{site.data.keyword.cloud_notm}}](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started).
