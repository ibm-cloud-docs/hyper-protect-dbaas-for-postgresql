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

# Eventi {{site.data.keyword.cloudaccesstrailshort}}
{: #activity-tracker-events}

Utilizza il servizio {{site.data.keyword.cloudaccesstrailfull}} per tenere traccia di come gli utenti e le applicazioni interagiscono con {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per la modalità di provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}, consulta la [documentazione di {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started) per ulteriori informazioni. Poiché il servizio {{site.data.keyword.ihsdbaas_postgresql_full}}  è attualmente disponibile nel data center di Dallas, assicurati di selezionare **us-south** come regione per l'acquisizione dei log.

## Elenco di eventi
{: #list-activity-tracker-events}

La seguente tabella elenca le azioni che generano un evento:

| Azione                 | Descrizione                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | Creare un cluster di database                 |
| `cluster.delete` | Elimina un cluster di database                 |
| `database.create` | Crea un database                  |
| `database.delete` | Elimina un database                  |
| `user.create`     | Crea un utente del database                    |
| `user.delete`     | Elimina un utente del database                    |
| `instance.start` | Avvia un'istanza del servizio database         |
| `instance.stop`  | Arresta un'istanza del servizio database          |
| `instance.restart`  | Riavvia un'istanza del servizio database          |
| `log.get`       | Scarica un file di log |
{: caption="Tabella 1. Azioni che generano gli eventi {{site.data.keyword.cloudaccesstrailfull_notm}}"}

Per l'evento `cluster.create` e `cluster.delete`, il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} non registra il nome dell'account e l'indirizzo IP dell'utente che esegue l'azione. Il valore di `initiator.name` e `host.address` nel log indica rispettivamente l'ID servizio e l'indirizzo IP del broker cloud.
{: note}

## Dove visualizzare gli eventi
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nel **dominio dell'account** {{site.data.keyword.cloudaccesstrailshort}}disponibile nella regione {{site.data.keyword.cloud_notm}} in cui vengono generati gli eventi.
