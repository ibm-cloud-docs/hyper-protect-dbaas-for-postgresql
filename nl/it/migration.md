---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: migrate, beta, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Migrazione dei database {{site.data.keyword.postgresql}} a {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

Se stai utilizzando i database {{site.data.keyword.postgresql}} e vuoi eseguire la migrazione a {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, leggi questo argomento per i dettagli. Non importa dove sono ubicati i tuoi database {{site.data.keyword.postgresql}}, finché la piattaforma fornisce dei servizi database {{site.data.keyword.postgresql}}.
{: shortdesc}

## Prima di cominciare
{: #migration_postgre_before_begin}

Per utilizzare i comandi {{site.data.keyword.postgresql}} in modo da completare la migrazione, devi prima scaricare e installare {{site.data.keyword.postgresql}} sulla tua macchina. Per ulteriori informazioni, vedi il [sito web {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Passo 1: crea un file di dump per ripristinare i database originali
{: #step1_create_dump_file}

Utilizza il seguente comando `pg_dump` per creare un file di dump che contiene i database che vuoi ripristinare.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

La seguente tabella illustra le variabili utilizzate nel comando.

|Variabili|Descrizione|Esempio|
|---------|-----------|-------|
|*host_name*|Il server remoto che ospita i database originali. Devi connetterti all'host per ottenere i dati. Se i tuoi database vengono distribuiti in un'istanza {{site.data.keyword.ihsdbaas_full}} Beta, puoi trovare l'indirizzo host nella pagina della panoramica dell'IU dell'istanza del cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Il numero di porta per stabilire una connessione all'host. Se i tuoi database vengono distribuiti in un'istanza {{site.data.keyword.ihsdbaas_full}} Beta, puoi trovare la porta nella pagina della panoramica dell'IU dell'istanza del cluster.|25050|
|*user_name*|Il nome utente per accedere ai database originali. L'utente deve disporre del privilegio CONNECT sul database e SELECT sulle tabelle.|my_user|
|*database_name*|Il nome del database che vuoi migrare.|my_database|
|*dump_file*|Il file `.dump` per archiviare i dati originali. Puoi utilizzare dei percorsi relativi o assoluti per specificare il file.|./pgdump.dump|
{: caption="Tabella 1. Le variabili necessarie per creare un file di dump"}

Se vuoi saperne di più sui privilegi utente, puoi fare riferimento alla [documentazione {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external} per ulteriori informazioni.

## Passo 2: crea una nuova istanza del servizio in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Prima di ripristinare i dati, devi creare una nuova istanza del servizio in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} come il cluster di database di destinazione. Puoi utilizzare uno dei seguenti modi per creare una nuova istanza del servizio:
- [L'interfaccia utente web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [Le API DBaaS Manger](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [Il plugin CLI con la CLI {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

Quando crei la nuova istanza del servizio, devi impostare il nome del cluster, il nome e la password dell'amministratore. Non devono necessariamente essere gli stessi di quelli nella tua istanza originale. Non influisce sulla migrazione. Dopo aver completato la migrazione, i database vengono assegnati al nuovo amministratore.

## Passo 3: crea dei database nella nuova istanza del servizio
{: #step3_create_database}

Dopo avere creato la nuova istanza del servizio, devi creare dei nuovi database. I database devono avere lo stesso nome di quelli originali. L'utente deve disporre del privilegio CREATE e non essere lo stesso utente che ha creato il file di dump. Puoi utilizzare uno dei seguenti modi per eseguire l'attività:
- [L'interfaccia utente web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [Le API DBaaS Manger](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [Il plugin CLI con la CLI {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

Puoi utilizzare i seguenti modi per creare dei nuovi utenti: [L'interfaccia utente web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [Le API DBaaS Manger](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [Il plugin CLI con la CLI {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create) e [il comando {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Passo 4: ripristina i dati dal file di dump a una nuova istanza del servizio.
{: #step4_restore_data}

Utilizza il comando `psql` per ripristinare i dati dal file di dump creato nel [Passo 1](#step1_create_dump_file).

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

La seguente tabella illustra le variabili utilizzate nel comando.

|Variabili|Descrizione|Esempio|
|---------|-----------|-------|
|*host_name*|Il server del DBaaS manager che ospita il cluster di destinazione. Puoi trovare l'indirizzo host sulla pagina della panoramica dell'IU dell'istanza del cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Il numero di porta per stabilire una connessione all'host. Puoi trovare l'indirizzo del numero di porta sulla pagina della panoramica dell'IU dell'istanza del cluster.|25003|
|*user_name*|Il nome utente per accedere al database di destinazione. Puoi utilizzare lo stesso utente che ha creato il database di destinazione nel [Passo 3](#step3_create_database).|new_user|
|*database_name*|Il database può essere un qualsiasi database di cui l'utente ha il privilegio CONNECT. La sessione `psql` passa automaticamente al database di destinazione creato nel [Passo 3](#step3_create_database).|my_database|
|*dump_file*|Il file `.dump` che hai creato nel [Passo 1](#step1_create_dump_file). Puoi utilizzare dei percorsi relativi o assoluti per specificare il file.|./pgdump.dump|
{: caption="Tabella 2. Le variabili necessarie per ripristinare i dati da un file di dump"}

## Operazioni successive
{: #whats_next_migration_postgre}

Dopo la migrazione, puoi eseguire la connessione al nuovo cluster di database per controllare se i dati sono stati migrati correttamente.
