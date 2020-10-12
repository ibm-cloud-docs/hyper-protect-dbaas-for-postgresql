---

copyright:
  years: 2020
lastupdated: "2020-10-13"

keywords: customize configuration, change configuration, configuration parameters

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:term: .term}
{:external: target="_blank" .external}

# Changing the PostgreSQL configuration
{: #changing-configuration}

In {{site.data.keyword.ihsdbaas_postgresql_full}}, with the Manager role, you can change some of the PosgreSQL configuration settings of your service instance to tune your PostgreSQL databases to your use case.
{: shortdesc}

The database admins or users with the [Manager role](#changing-configuration-prerequisite) can update the available configuration parameters with the [CLI](#changing-configuration-cli) or the [API](#changing-configuration-api). The configuration is defined in a schema. To make a change, you send a JSON object with the settings and their new values to the CLI or the API. For example, to change the `deadlock_timeout` setting to 150, you need to provide `{"configuration":{"deadlock_timeout":150}}` to either the CLI or the API.

If a request to change configuration settings fails, the {{site.data.keyword.ihsdbaas_postgresql_full}} SRE team will be notified automatically. You can also use the [task commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#task-cmds) or the [API request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-tasks){: external} to view the request status.

Some configuration changes require a restart to the primary and secondary nodes. The secondary nodes will be restarted first, then the primary node. You can find the `requires_restart` information in [Available configuration settings](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration#available-config-settings).
{: note}

## Prerequisite
{: #changing-configuration-prerequisite}

You need to have the **Manager** role to change configuration settings, as defined in the [IAM service access roles table](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#service-access-roles). To assign access, see [Managing IAM access for users or services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#manage-access).

## Using the CLI
{: #changing-configuration-cli}

You can check the current configuration of your service instance with the following command.
```
ibmcloud dbaas configuration-show <resource_name>
```
{: codeblock}

To change your configuration through the CLI, use the following command.
```
ibmcloud dbaas configuration-update <resource_name> [@JSON_FILE | JSON_STRING]
```
{: codeblock}

The command reads the changes that you would like to make from the JSON file or string. For more information about formatting `JSON_FILE` or `JSON_STRING`, see the [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db-config-update).

You can run the following commands to check the request status of configuration changes.
```
ibmcloud dbaas tasks-list <resource_name>
ibmcloud dbaas task-show <resource_name> <task_id>
```
{: codeblock}

## Using the API
{: #changing-configuration-api}

There are two deployment-configuration endpoints, one for viewing the configuration schema and one for changing the configuration:

1. To view the configuration schema, use the [API request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-configuration){: external}.
2. To change the configuration, specify the settings as a JSON object in the [request to update configuration](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#update-configuration){: external}. You can use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-tasks){: external} to check the task status.

## Available configuration settings
{: #available-config-settings}
<!--
### Memory Settings
{: #available-config-settings-memory}
-->

[`shared_buffers`](https://www.postgresql.org/docs/10/runtime-config-resource.html#GUC-SHARED-BUFFERS){: external}
  - Default - `128` (MB)
  - Restarts database? - **Yes**
  - Note - Shared memory buffers that the server use. The recommended memory allocation for `shared_buffers` is 1/4 of the service intance's RAM. Setting `shared_buffers` any higher can result in memory issues that cause the database to crash. Setting `shared_buffers` equal, close to equal, or higher than the amount of allocated memory prevents the database from starting. <!--The maximum amount of total space for `shared_buffers` is 8 GB or 1048576 buffers based on recommendations from the PostgreSQL community. Your service instance can make use of additional RAM for caching and performance, even without allocating it to `shared_buffers`. You do not have to configure the database to use all of the allocated RAM in order for your deployment to use it.-->

<!--
### General Settings
{: #available-config-settings-general}

[`synchronous_commit`](https://www.postgresql.org/docs/current/wal-async-commit.html)
  - Default - `local`
  - Restarts database? - No
  - Options - `local` or `off`
  - Notes - Setting `synchronous_commit` to `off` increases transaction commit rate at the expense of a loss of committed transactions in the event of an unclean shutdown.
-->
[`max_locks_per_transaction`](https://www.postgresql.org/docs/10/runtime-config-locks.html){: external}
  - Default - `64`
  - Restarts database? - **Yes**
  - Note - The setting controls the average number of object locks allocated for each transaction. It's recommended to leave this setting at the default. Increase it only if you have queries that touch many different tables in a single transaction.

<!--
### WAL Settings
{: #available-config-settings-wal}
-->
[`deadlock_timeout`](https://www.postgresql.org/docs/10/runtime-config-locks.html){: external}
  - Default - `1000`
  - Restarts database? - **No**
  - Options - Minimum value of 100
  - Note - The number of milliseconds to wait before checking for deadlock and the duration where lock waits are logged. Logs available through the logging integration. Setting this number too low negatively impacts performance.
