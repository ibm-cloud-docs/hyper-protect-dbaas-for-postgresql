---

copyright:
  years: 2019, 2020
lastupdated: "2020-10-14"

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
{:term: .term}

# Migrating {{site.data.keyword.postgresql}} databases to {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

If you're using {{site.data.keyword.postgresql}} databases and want to migrate to {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, follow the instructions below. It doesn't matter where your {{site.data.keyword.postgresql}} databases are hosted, as long as the platform provides {{site.data.keyword.postgresql}} database services.
{: shortdesc}

## Before you begin
{: #migration_postgre_before_begin}

To use the {{site.data.keyword.postgresql}} commands to complete the migration, you need to download and install {{site.data.keyword.postgresql}} of the version compatible with {{site.data.keyword.postgresql}} 10 that is supported by {{site.data.keyword.ihsdbaas_postgresql_full}}. For more information, see [{{site.data.keyword.postgresql}} website](https://www.postgresql.org/download/){: external}.

## Step 1. Create a dump file for restoring the original databases
{: #step1_create_dump_file}

Use the following `pg_dump` command to create a dump file that contains the databases you want to restore.

```
pg_dump "host=<host_name> port=<port> sslmode=<ssl_mode> sslrootcert=<cert_file> user=<user_name> dbname=<database_name>" -f <dump_file>
```
{: pre}

The following table explains the parameters that are used in the command.

|Parameter|Description|Example|
|---------|-----------|-------|
|*host_name*|The name of the host server that hosts the original databases. You need to connect to the host to get the data.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host.|25050|
|*ssl_mode*|The SSL mode for encryption.|verify-full|
|*cert_file*|The [certificate authority (CA)](#x2016383){: term} file in the `.pem` format that you downloaded from the **Overview** page in the service dashboard. You can specify the file with a relative or absolute path.|./cert.pem|
|*user_name*|The username to access the original databases. The user needs to have CONNECT privilege on the database and SELECT privilege to the tables.|my_user|
|*database_name*|The name of the database that you want to migrate.|my_database|
|*dump_file*|The `.dump` file to store the original data. You can use a relative or absolute path to specify the file.|./pgdump.dump|
{: caption="Table 1. Parameters that are needed to create a dump file"}

For more information about user privileges, see [{{site.data.keyword.postgresql}} documentation](https://www.postgresql.org/docs/10/sql-grant.html){: external} for more information.

## Step 2. Create a new {{site.data.keyword.ihsdbaas_postgresql_full}} service instance
{: #step2_creat_new_service_instance}

Before you restore the data, you need to [create a new {{site.data.keyword.ihsdbaas_postgresql_full}} service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service) as the target database cluster.

When you create the new service instance, you need to set the cluster name, the administrator name, and password. They aren't necessarily to be the same as the ones in your original instance. It doesn't affect the migration. After the migration is completed, the databases are assigned to the new administrator.

## Step 3. Create databases in the new service instance
{: #step3_create_database}

After you create the new service instance, you need to use your database client to create new databases. The databases must have the same name with the original ones. The user needs to have CREATE privilege and doesn't have to be the same as the user that creates the dump file.

## Step 4. Restore the data from the dump file to a new service instance
{: #step4_restore_data}

Use the `psql` command to restore the data from the dump file that is created in [Step 1](#step1_create_dump_file).

```
psql "host=<host-name> port=<port> sslmode=<ssl_mode> sslrootcert=<cert_file> user=<user_name> dbname=<database_name>" -f <dump_file>
```
{: pre}

The following table explains the parameters that are used in the command.

|Parameter|Description|Example|
|---------|-----------|-------|
|*host_name*|The name of the host server that hosts the target cluster. You can find the host address on the **Overview** page in the service dashboard.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host. You can find the port number address on the **Overview** page in the service dashboard.|25003|
|*ssl_mode*|The SSL mode for encryption.|verify-full|
|*cert_file*|The CA file in the `.pem` format that you downloaded from the **Overview** page in the service dashboard. You can specify the file with a relative or absolute path.|./cert.pem|
|*user_name*|The username to access the target database. You can use the same user who creates the target database in [Step 3](#step3_create_database).|new_user|
|*database_name*|The database can be any database that the user has CONNECT privilege on. The `psql` session automatically switches it to the target database that is created in [Step 3](#step3_create_database).|my_database|
|*dump_file*|The `.dump` file that you created in [Step 1](#step1_create_dump_file). You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 2. Parameters that are needed to restore the data from a dump file"}

## What's next
{: #whats_next_migration_postgre}

After the migration, you can connect to the new database cluster to check whether the data is migrated successfully.
