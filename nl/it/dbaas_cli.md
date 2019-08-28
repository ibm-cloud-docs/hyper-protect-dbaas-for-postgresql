---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: instance commands, cluster resource, CLI plugin

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


# Plugin CLI {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #dbaas_cli_plugin}

Utilizza il plugin CLI {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} per creare, eliminare
e visualizzare le informazioni sui database e gli utenti, per mostrare i dettagli sui cluster,
per avviare e arrestare le istanze e per elencare e scaricare i file di log.
{:shortdesc}


## Prerequisiti
{: #prerequisites_dbaas_cli_plugin}

- Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started). La CLI {{site.data.keyword.cloud_notm}} richiede l'SDK Java 1.7.0. Il prefisso per l'esecuzione dei comandi utilizzando la CLI {{site.data.keyword.cloud_notm}} è `ibmcloud`. Nel terminale, ricevi una notifica quando sono disponibili degli aggiornamenti ai plug-in e alla CLI `ibmcloud`. Assicurati di mantenere la tua CLI aggiornata in modo che tu possa utilizzare tutti i comandi e gli indicatori disponibili.

- Installa il plugin CLI {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}. Come riferimento puoi vedere [Installazione del plugin CLI DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin). Se vuoi visualizzare la versione corrente del tuo plugin CLI {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}},
esegui `ibmcloud plugin show dbaas-cli`.


## Comando di utilizzo del plugin CLI
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

Questo comando visualizza un elenco di comandi DBaaS.

```
ibmcloud help dbaas
```
{: pre}


## Comando cluster
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

Questo comando mostra i dettagli del cluster specificato, incluse le informazioni su ogni membro della replica.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster. Per trovare il nome della risorsa, utilizza il comando {{site.data.keyword.cloud_notm}} `ibmcloud resource service-instances`.</dd>
</dl>

## Comandi database
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

Questo comando crea un database e, facoltativamente, una raccolta.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*database_name*</dt>
<dd>Il nome del database da creare.</dd>
<dt>*collection*</dt>
<dd>(Facoltativo) Il nome della raccolta da creare.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

Questo comando elimina un database. Non eliminare un database se è stato creato da delle credenziali e tali credenziali sono ancora in uso.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*database_name*</dt>
<dd>Il nome del database da eliminare.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

Questo comando elenca tutti i database sul cluster selezionato.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
</dl>


## Comandi utente database
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

Questo comando crea un utente del database.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*username*</dt>
<dd>Il nome utente da assegnare all'utente del database che viene creato.</dd>
<dt>*db_name*</dt>
<dd>(Facoltativo) Specifica un database per cui l'utente avrà l'accesso in lettura e scrittura.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

Questo comando elimina un utente del database. Non eliminare un utente del database se è stato creato da delle credenziali e tali credenziali sono ancora in uso.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*username*</dt>
<dd>Il nome dell'utente del database che viene eliminato.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

Questo comando elenca tutti gli utenti del database.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

Questo comando mostra i dettagli su un utente del database.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*username*</dt>
<dd>Il nome dell'utente del database che viene mostrato.</dd>
</dl>


## Comandi istanza
{: #instance_cmds}

Per utilizzare uno dei comandi dell'istanza elencati qui di seguito, devi conoscere l'ID istanza (`instance_id`). Per ottenere un ID istanza (`instance_id`), utilizza prima il seguente comando `ibmcloud` per elencare i nomi dei gruppi di risorse dell'istanza del servizio e poi utilizza il comando [`cluster_show`](#cluster_show) per ottenere l'ID istanza (`instance_id`).

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

Questo comando riavvia un'istanza in esecuzione.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*instance_id*</dt>
<dd>L'ID dell'istanza.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

Questo comando avvia un'istanza arrestata.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*instance_id*</dt>
<dd>L'ID dell'istanza.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

Questo comando arresta un'istanza (un membro di replica del cluster).

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*instance_id*</dt>
<dd>L'ID dell'istanza.</dd>
</dl>


## Comandi di log
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

Questo comando scarica un file di log da un'istanza.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*instance_id*</dt>
<dd>L'ID dell'istanza.</dd>
<dt>*filename*</dt>
<dd>Il nome del file di log da scaricare. Per determinare il nome file del file di log che vuoi scaricare, utilizza il comando [ibmcloud dbaas logs-list](#log_list).</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

Questo comando elenca tutti i file di log su un'istanza. Puoi utilizzare uno qualsiasi dei nomi file elencati come input per il comando [ibmcloud dbaas log-get](#log_get).

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Opzioni del comando**

<dl>
<dt>*resource_name*</dt>
<dd>Il nome della risorsa cluster.</dd>
<dt>*instance_id*</dt>
<dd>L'ID dell'istanza.</dd>
</dl>
