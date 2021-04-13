---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: migrate, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


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
|*cert_file*|The [certificate authority (CA)](#x2016383){: term} file in the `.pem` format that you downloaded from the **Overview** page on the service dashboard. You can specify the file with a relative or absolute path.|./cert.pem|
|*user_name*|The username to access the original databases. The user needs to have CONNECT privilege on the database and SELECT privilege to the tables.|my_user|
|*database_name*|The name of the database that you want to migrate.|my_database|
|*dump_file*|The `.dump` file to store the original data. You can use a relative or absolute path to specify the file.|./pgdump.dump|
{: caption="Table 1. Parameters that are needed to create a dump file"}

For more information about user privileges, see [{{site.data.keyword.postgresql}} documentation](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

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
|*host_name*|The name of the host server that hosts the target cluster. You can find the host address on the **Overview** page on the service dashboard.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|The port number to establish a connection to the host. You can find the port number address on the **Overview** page on the service dashboard.|25003|
|*ssl_mode*|The SSL mode for encryption.|verify-full|
|*cert_file*|The CA file in the `.pem` format that you downloaded from the **Overview** page on the service dashboard. You can specify the file with a relative or absolute path.|./cert.pem|
|*user_name*|The username to access the target database. You can use the same user who creates the target database in [Step 3](#step3_create_database).|new_user|
|*database_name*|The database can be any database that the user has CONNECT privilege on. The `psql` session automatically switches it to the target database that is created in [Step 3](#step3_create_database).|my_database|
|*dump_file*|The `.dump` file that you created in [Step 1](#step1_create_dump_file). You can use relative or absolute paths to specify the file.|./pgdump.dump|
{: caption="Table 2. Parameters that are needed to restore the data from a dump file"}

## What's next
{: #whats_next_migration_postgre}

After the migration, you can connect to the new database cluster to check whether the data is migrated successfully.
