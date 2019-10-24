---

copyright:
  years: 2019
lastupdated: "2019-10-18"

keywords: backup, disaster recovery, restore

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
{:external: target="_blank" .external}

# Backing up and restoring your databases using {{site.data.keyword.cos_full_notm}}
{: #backup_postgresql_databases}

The {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service automatically triggers a backup of your complete database once every 24 hours. These encrypted backups are available for the last seven days and redundantly available on local storage in all the availability zones of the supported regions.
{: shortdesc}

If you want to increase your disaster recovery capabilities by making cross-region backups, you can use [{{site.data.keyword.cos_full_notm}} service](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} to store your data in a different region by referring to the following steps.

## Before you begin
{: #backup_postgresql_before_begin}

To use the {{site.data.keyword.postgresql}} commands to complete the backup, you need to download and install {{site.data.keyword.postgresql}} of the version compatible with {{site.data.keyword.postgresql}} 10 that is supported by {{site.data.keyword.ihsdbaas_postgresql_full}}. For more information, see [{{site.data.keyword.postgresql}} website](https://www.postgresql.org/download/){: external}.

## Step 1: Create a dump file for backing up the original databases
{: #step1_create_dump_file_backup_postgresql}

Use the following `pg_dump` command to create a dump file that contains the databases you want to back up.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

The following table illustrates the variables used in the command.

|Variables|Description|Example|
|---------|-----------|-------|
|*host_name*|The remote server that hosts the original databases. You need to connect to the host to get the data. You can find the host address on the overview page of the cluster instance UI.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host. You can find the port on the overview page of the cluster instance UI.|25050|
|*user_name*|The username to access the original databases. The user needs to have CONNECT privilege on the database and SELECT privilege to the tables.|my_user|
|*database_name*|The name of the database that you want to back up.|my_database|
|*dump_file*|The `.dump` file to store the original data. You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 1. The variables that are needed to create a dump file"}

If you want to know more about user privileges, you can refer to [{{site.data.keyword.postgresql}} documentation](https://www.postgresql.org/docs/10/sql-grant.html){: external} for more information.

## Step 2: Create a new {{site.data.keyword.cos_full_notm}} instance
{: #step2_create_object_storage_backup_postgresql}

You need to create the instance in a region that is different from where the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance is currently hosted. You can refer to the following steps:

1. [Create a new Cloud {{site.data.keyword.cos_short}} instance](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Create a bucket](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) in a different region.
3. [Create a service credential](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) and save the `access_key_id` and `secret_access_key` for later use.
4. Install a S3 client.
5. Use the S3 client and the access keys to connect to the Cloud {{site.data.keyword.cos_short}} endpoint of the bucket that you create earlier. For detailed instructions on configuring the `.s3cfg` file, see [Use IBM Cloud Object Storage to serve static website content](https://www.ibm.com/cloud/blog/static-websites-cloud-object-storage-cos){: external}.
6. Use the S3 client to [upload the {{site.data.keyword.postgresql}} backup file](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) that you create in [Step 1](#step1_create_dump_file_backup_postgresql) to the bucket.

You can refer to [{{site.data.keyword.cos_full_notm}} documentation](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started) for more information.

After completing this step, you successfully back up your data in a Cloud {{site.data.keyword.cos_short}} instance in a different region. If you want to restore the data from the Cloud {{site.data.keyword.cos_short}} instance to a {{site.data.keyword.ihsdbaas_postgresql_full}} instance, read the following Step 3 for details.

## Step 3: Restore the data from the Cloud {{site.data.keyword.cos_short}} instance to a {{site.data.keyword.ihsdbaas_postgresql_full}} instance
{: #step3_restore_data_from_cos_postgresql}

You need to download the backup file from the Cloud {{site.data.keyword.cos_short}} bucket to your local machine first, then use the `psql` command to restore the data.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

The following table illustrates the variables used in the command.

|Variables|Description|Example|
|---------|-----------|-------|
|*host_name*|The DBaaS manager server that hosts the target cluster. You can find the host address on the overview page of the cluster instance UI.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host. You can find the port number address on the overview page of the cluster instance UI.|25003|
|*user_name*|The username to access the target database.|new_user|
|*database_name*|The database can be any database that the user has CONNECT privilege on. The `psql` session automatically switches it to the target database that you want to restore the data into.|my_database|
|*dump_file*|The `.dump` file that you download from your Cloud {{site.data.keyword.cos_short}} bucket. You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 2. The variables that are needed to restore the data from a dump file"}

When you run the `psql` command to restore the data, you might get a series of permission-related errors because you do not have SUPERUSER authority. Ignore the errors because they do not affect the restoring result.
{: note}

## What's next
{: #whats_next_backup_postgresql}

After [Step 3](#step3_restore_data_from_cos_postgresql), you can connect to the database cluster to check if the data is restored successfully.
