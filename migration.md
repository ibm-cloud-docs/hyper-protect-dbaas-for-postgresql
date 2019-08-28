---

copyright:
  years: 2019
lastupdated: "2019-08-28"

keywords: migrate, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Migrating {{site.data.keyword.postgresql}} databases to {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

If you are using {{site.data.keyword.postgresql}} databases and want to migrate to {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, read this topic for details. It does not matter where your {{site.data.keyword.postgresql}} databases are hosted, as long as the platform provides {{site.data.keyword.postgresql}} database services.
{: shortdesc}

## Before you begin
{: #migration_postgre_before_begin}

To use the {{site.data.keyword.postgresql}} commands to complete the migration, you need to download and install {{site.data.keyword.postgresql}} on your machine first. For more information, see [{{site.data.keyword.postgresql}} website](https://www.postgresql.org/download/){: external}.

## Step1: Create a dump file for restoring the original databases
{: #step1_create_dump_file}

Use the following `pg_dump` command to create a dump file that contains the databases you want to restore.

```
pg_dump "host=<host-name> port=<port> sslmode=<ssl_mode> sslrootcert=<cert_file> user=<user_name> dbname=<database_name>" -f <dump_file>
```
{: pre}

The following table illustrates the variables used in the command.

|Variables|Description|Example|
|---------|-----------|-------|
|*host_name*|The remote server that hosts the original databases. You need to connect to the host to get the data.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host.|25050|
|*ssl_mode*|The SSL mode for encryption.|verify-full|
|*cert_file*|The certificate authority (CA) file in the `.pem` format that contains SSL CA certificates. You can specify the file using relative or absolute paths.|./cert.pem|
|*user_name*|The username to access the original databases. The user needs to have CONNECT privilege on the database and SELECT privilege to the tables.|my_user|
|*database_name*|The name of the database that you want to migrate.|my_database|
|*dump_file*|The `.dump` file to store the original data. You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 1. The variables that are needed to create a dump file"}

If you want to know more about user privileges, you can refer to [{{site.data.keyword.postgresql}} documentation](https://www.postgresql.org/docs/10/sql-grant.html){: external} for more information.

## Step2: Create a new service instance in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Before you restore the data, you need to create a new service instance in {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} as the target database cluster. You can use one of the following ways to create a new service instance:
- [The web user interface](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [The DBaaS Manger APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [The CLI plug-in with the {{site.data.keyword.cloud_notm}} CLI](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

When you create the new service instance, you need to set the cluster name, the administrator name and password. They are not necessarily to be the same as the ones in your original instance. It does not affect the migration. After the migration is completed, the databases are assigned to the new administrator.

## Step3: Create databases in the new service instance
{: #step3_create_database}

After you create the new service instance, you need to create new databases. The databases must have the same name with the original ones. The user needs to have CREATE privilege and does not have to be the same with the user that creates the dump file. You can use one of the following ways to perform the task:
- [The web user interface](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [The DBaaS Manger APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [The CLI plug-in with the {{site.data.keyword.cloud_notm}} CLI](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

You can use the following ways to create new users: [The web user interface](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [The DBaaS Manger APIs](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [The CLI plug-in with the {{site.data.keyword.cloud_notm}} CLI](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create), and [{{site.data.keyword.postgresql}} command](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Step4: Restore the data from the dump file to a new service instance
{: #step4_restore_data}

Use the `psql` command to restore the data from the dump file that is created in [Step1](#step1_create_dump_file).

```
psql "host=<host-name> port=<port> sslmode=<ssl_mode> sslrootcert=<cert_file> user=<user_name> dbname=<database_name>" -f <dump_file>
```
{: pre}

The following table illustrates the variables used in the command.

|Variables|Description|Example|
|---------|-----------|-------|
|*host_name*|The DBaaS manager server that hosts the target cluster. You can find the host address on the overview page of the cluster instance UI.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host. You can find the port number address on the overview page of the cluster instance UI.|25003|
|*ssl_mode*|The SSL mode for encryption.|verify-full|
|*cert_file*|The CA file in the `.pem` format that contains SSL CA certificates. You can specify the file using relative or absolute paths.|./cert.pem|
|*user_name*|The username to access the target database. You can use the same user who creates the target database in [Step3](#step3_create_database).|new_user|
|*database_name*|The database can be any database that the user has CONNECT privilege on. The `psql` session automatically switches it to the target database that is created in [Step3](#step3_create_database).|my_database|
|*dump_file*|The `.dump` file that you create in [Step1](#step1_create_dump_file). You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 2. The variables that are needed to restore the data from a dump file"}

## What's next
{: #whats_next_migration_postgre}

After the migration, you can connect to the new database cluster to check whether the data is migrated successfully.
