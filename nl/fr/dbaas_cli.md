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


# Plug-in CLI {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #dbaas_cli_plugin}

Utilisez le plug-in CLI {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} pour créer, supprimer et afficher des informations relatives aux bases de données et aux utilisateurs, pour afficher des informations détaillées sur les clusters, pour démarrer et arrêter des instances et pour répertorier et télécharger des fichiers journaux.
{:shortdesc}


## Conditions préalables
{: #prerequisites_dbaas_cli_plugin}

- Installez l'interface de ligne de commande [{{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started). L'interface CLI {{site.data.keyword.cloud_notm}} nécessite Java SDK 1.7.0. Le préfixe pour l'exécution de commandes via l'interface CLI {{site.data.keyword.cloud_notm}} est `ibmcloud`. Dans le terminal, vous êtes averti des mises à jour disponibles pour l'interface de ligne de commande `ibmcloud` et les plug-ins. Veillez à maintenir votre interface de ligne de commande à jour pour pouvoir utiliser l'ensemble des commandes et des indicateurs.

- Installez le plug-in d'interface de ligne de commande {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}. Vous pouvez vous reporter à [Installation du plug-in CLI DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin). Si vous souhaitez afficher la version en cours de votre plug-in CLI {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, exécutez la commande `ibmcloud plugin show dbaas-cli`.


## Commandes d'utilisation du plug-in de l'interface CLI
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

Cette commande affiche une liste de commandes DBaaS.

```
ibmcloud help dbaas
```
{: pre}


## Commande de cluster
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

Cette commande affiche les détails relatifs au cluster spécifié, y compris les informations sur chaque membre de réplique.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster. Pour trouver le nom de la ressource, utilisez la commande {{site.data.keyword.cloud_notm}} `ibmcloud resource service-instances`.</dd>
</dl>

## Commandes de base de données
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

Cette commande crée une base de données et, éventuellement, une collection.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>*database_name*</dt>
<dd>Nom de la base de données à créer.</dd>
<dt>*collection*</dt>
<dd>(Facultatif) Nom de la collection à créer.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

Cette commande supprime une base de données. Ne supprimez pas une base de données si elle a été créée par donnée d'identification et si cette donnée d'identification est toujours utilisée.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>*database_name*</dt>
<dd>Nom de la base de données à supprimer.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

Cette commande répertorie toutes les bases de données sur le cluster donné.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
</dl>


## Commandes d'utilisateur de base de données
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

Cette commande crée un utilisateur de base de données.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>*username*</dt>
<dd>Nom d'utilisateur qui doit être affecté à l'utilisateur de base de données en cours de création.</dd>
<dt>*db_name*</dt>
<dd>(Facultatif) Spécifie une base de données pour laquelle l'utilisateur dispose de droits d'accès en écriture et en lecture.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

Cette commande supprime un utilisateur de base de données. Ne supprimez pas un utilisateur de base de données s'il a été créé par donnée d'identification et si cette donnée d'identification est toujours utilisée.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>*username*</dt>
<dd>Nom d'utilisateur de l'utilisateur de base de données en cours de suppression.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

Cette commande répertorie tous les utilisateurs de base de données.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

Cette commande affiche les détails relatifs à un utilisateur de base de données.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>*username*</dt>
<dd>Nom d'utilisateur de l'utilisateur de base de données affiché.</dd>
</dl>


## Commandes d'instance
{: #instance_cmds}

Pour utiliser n'importe laquelle des commandes d'instance répertoriées ici, vous devez connaître l'ID d'instance (`instance_id`). Pour obtenir un ID d'instance (`instance_id`), utilisez d'abord la commande `ibmcloud` suivante pour répertorier les noms des groupes de ressources d'instance de service sous votre compte, puis utilisez la commande [`cluster_show`](#cluster_show) pour obtenir l'ID d'instance (`instance_id`).

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

Cette commande redémarre une instance en cours d'exécution.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>* instance_id *</dt>
<dd>ID de l'instance.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

Cette commande démarre une instance arrêtée.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>* instance_id *</dt>
<dd>ID de l'instance.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

Cette commande arrête une instance (un membre de réplication du cluster).

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>* instance_id *</dt>
<dd>ID de l'instance.</dd>
</dl>


## Commandes de journal
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

Cette commande télécharge un fichier journal d'une instance.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>* instance_id *</dt>
<dd>ID de l'instance.</dd>
<dt>*filename*</dt>
<dd>Nom du fichier journal à télécharger. Pour déterminer le nom de fichier du fichier journal que vous souhaitez télécharger, utilisez la commande [ibmcloud dbaas logs-list](#log_list).</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

Cette commande répertorie tous les fichiers journaux sur une instance. Vous pouvez saisir dans la commande [ibmcloud dbaas log-get](#log_get) n'importe lequel des noms de fichier répertoriés.

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Options de commande**

<dl>
<dt>*resource_name*</dt>
<dd>Nom de la ressource de cluster.</dd>
<dt>* instance_id *</dt>
<dd>ID de l'instance.</dd>
</dl>
