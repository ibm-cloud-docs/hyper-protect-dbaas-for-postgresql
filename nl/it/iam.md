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

# Ruoli e azioni di Identity and Access Management
{: #iam}

L'accesso alle istanze del servizio {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} per gli utenti nel tuo account è controllato da {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Ad ogni utente che accede al servizio {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} nel tuo account deve essere assegnata una politica di accesso con un ruolo IAM definito. La politica determina quali azioni possono essere eseguite da un utente all'interno del contesto del servizio o dell'istanza che selezioni. Le azioni consentite sono personalizzate e definite dal servizio {{site.data.keyword.cloud_notm}} come delle operazioni che è permesso eseguire sul servizio. Le azioni vengono poi associate ai ruoli utente IAM.
{: shortdesc}

Le politiche abilitano la concessione dell'accesso a diversi livelli. Alcune delle opzioni includono le seguenti:

* Accesso a tutte le istanze del servizio nel tuo account
* Accesso a una sola istanza del servizio nel tuo account
* Accesso a una risorsa specifica all'interno di un'istanza

Dopo aver definito l'ambito della politica di accesso, assegna un ruolo che determina il livello di accesso dell'utente. Controlla le seguenti tabelle che descrivono quali azioni sono consentite da ogni ruolo all'interno del servizio {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.

La seguente tabella illustra le azioni associate ai ruoli di gestione della piattaforma. I ruoli di gestione della piattaforma abilitano gli utenti ad eseguire delle attività sulle risorse del servizio al livello della piattaforma, ad esempio assegnare l'accesso utente per il servizio, creare o eliminare le istanze e associare le istanze alle applicazioni.

|Ruolo di gestione della piattaforma|Descrizione delle azioni|Azioni di esempio                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Visualizzatore                  |Può visualizzare le istanze del servizio ma non può modificarle|<ul><li>Elencare i cluster</li><li>Visualizzare i dettagli per un cluster</li></ul>|
|Editor                  |Esegue tutte le azioni della piattaforma ad eccezione della gestione dell'account e dell'assegnazione delle politiche di accesso|<ul><li>Associare un servizio a un cluster</li></ul>|
|Operatore                |Esegue le azioni della piattaforma necessarie a configurare ed utilizzare le istanze del servizio, ad esempio la visualizzazione del dashboard di un servizio|<ul><li>Associare un servizio a un cluster</li></ul>|
|Amministratore           |Esegue tutte le azioni della piattaforma basate sulla risorsa a cui è assegnato questo ruolo, inclusa l'assegnazione delle politiche di accesso ad altri utenti|<ul><li>Rimuovere un cluster</li><li>Creare un cluster</li><li>Aggiornare le politiche di accesso utente</li><li>Tutte le azioni che possono essere eseguite da un visualizzatore, editor o operatore</li></ul>|
{: caption="Tabella 1. Ruoli e azioni utente di IAM"}

Per informazioni sull'assegnazione dei ruoli utente nell'IU, vedi [Gestione dell'accesso alle risorse](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
