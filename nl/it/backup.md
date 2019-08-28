---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: backup, disaster recovery, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:tip: .tip}


# Backup e ripristino dei tuoi database tramite {{site.data.keyword.cos_full_notm}}
{: #backup_postgresql_databases}

Il servizio {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} attiva automaticamente un backup del tuo intero database ogni 24 ore. Questi backup crittografati sono disponibili per gli ultimi 7 giorni e in modo ridondante sull'archiviazione locale in tutte le zone di disponibilità della regione supportata.
{: shortdesc}

Se vuoi aumentare le tue funzionalità di ripristino di emergenza e backup dei dati al di fuori della regione supportata, puoi utilizzare il servizio [{{site.data.keyword.cos_full_notm}}](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} per archiviare i tuoi dati in una regione diversa facendo riferimento alla seguente procedura.

## Prima di cominciare
{: #backup_postgresql_before_begin}

Per utilizzare i comandi {{site.data.keyword.postgresql}} in modo da completare il backup, devi prima scaricare e installare {{site.data.keyword.postgresql}} sulla tua macchina. Per ulteriori informazioni, vedi il [sito web {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Passo 1: crea un file di dump per eseguire il backup dei database originali
{: #step1_create_dump_file_backup_postgresql}

Utilizza il seguente comando `pg_dump` per creare un file di dump che contiene i database di cui vuoi eseguire il backup.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

La seguente tabella illustra le variabili utilizzate nel comando.

|Variabili|Descrizione|Esempio|
|---------|-----------|-------|
|*host_name*|Il server remoto che ospita i database originali. Devi connetterti all'host per ottenere i dati. Puoi trovare l'indirizzo host sulla pagina della panoramica dell'IU dell'istanza del cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Il numero di porta per stabilire una connessione all'host. Puoi trovare la porta sulla pagina della panoramica dell'IU dell'istanza del cluster.|25050|
|*user_name*|Il nome utente per accedere ai database originali. L'utente deve disporre del privilegio CONNECT sul database e SELECT sulle tabelle.|my_user|
|*database_name*|Il nome del database di cui vuoi eseguire il backup.|my_database|
|*dump_file*|Il file `.dump` per archiviare i dati originali. Puoi utilizzare dei percorsi relativi o assoluti per specificare il file.|./pgdump.dump|
{: caption="Tabella 1. Le variabili necessarie per creare un file di dump"}

Se vuoi saperne di più sui privilegi utente, puoi fare riferimento alla [documentazione {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external} per ulteriori informazioni.

## Passo 2: crea una nuova istanza di {{site.data.keyword.cos_full_notm}}
{: #step2_create_object_storage_backup_postgresql}

Devi creare l'istanza in una regione diversa rispetto a quella in cui al momento è ospitata l'istanza del servizio {{site.data.keyword.ihsdbaas_postgresql_full}}. Puoi fare riferimento alla seguente procedura:

1. [Crea una nuova istanza {{site.data.keyword.cos_short}} cloud](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Crea un bucket](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) in una regione diversa.
3. [Crea le credenziali del servizio](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) e salva `access_key_id` e `secret_access_key` per un utilizzo successivo.
4. Installa un client S3.
5. Utilizza il client S3 e le chiavi di accesso per la connessione all'endpoint {{site.data.keyword.cos_short}} cloud del bucket che hai creato in precedenza.
6. Utilizza il client S3 per [caricare il file di backup di {{site.data.keyword.postgresql}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) che hai creato nel [Passo 1](#step1_create_dump_file_backup_postgresql) nel bucket.

Per ulteriori informazioni, puoi fare riferimento alla [documentazione {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started).

Dopo aver completato questo passo, avrai correttamente eseguito il backup dei tuoi dati in un'istanza {{site.data.keyword.cos_short}} cloud in una regione diversa. Se vuoi ripristinare i dati dall'istanza {{site.data.keyword.cos_short}} cloud in un'istanza {{site.data.keyword.ihsdbaas_postgresql_full}}, leggi il seguente passo 3 per i dettagli.

## Passo 3: ripristina i dati dall'istanza {{site.data.keyword.cos_short}} cloud a un'istanza {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step3_restore_data_from_cos_postgresql}

Devi prima caricare il file di backup dal bucket {{site.data.keyword.cos_short}} cloud nella tua macchina locale e poi utilizzare il comando `psql` per ripristinare i dati.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

La seguente tabella illustra le variabili utilizzate nel comando.

|Variabili|Descrizione|Esempio|
|---------|-----------|-------|
|*host_name*|Il server del DBaaS manager che ospita il cluster di destinazione. Puoi trovare l'indirizzo host sulla pagina della panoramica dell'IU dell'istanza del cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Il numero di porta per stabilire una connessione all'host. Puoi trovare l'indirizzo del numero di porta sulla pagina della panoramica dell'IU dell'istanza del cluster.|25003|
|*user_name*|Il nome utente per accedere al database di destinazione.|new_user|
|*database_name*|Il database può essere un qualsiasi database di cui l'utente ha il privilegio CONNECT. La sessione `psql` passa automaticamente al database di destinazione in cui vuoi ripristinare i dati.|my_database|
|*dump_file*|Il file `.dump` che hai scaricato dal tuo bucket {{site.data.keyword.cos_short}} cloud. Puoi utilizzare dei percorsi relativi o assoluti per specificare il file.|./pgdump.dump|
{: caption="Tabella 2. Le variabili necessarie per ripristinare i dati da un file di dump"}

## Operazioni successive
{: #whats_next_backup_postgresql}

Dopo aver completato il [Passo 3](#step3_restore_data_from_cos_postgresql), puoi eseguire la connessione al cluster di database per controllare se i dati sono stati ripristinati correttamente.
