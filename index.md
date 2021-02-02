---

copyright:
  years: 2019, 2021
lastupdated: "2021-02-02"

keywords: hyper protect dbaas, hyper protect dbaas for postgresql, postgresql, cloud database, data security, secure database, encrypted database

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
{:video: .video}
{:external: target="_blank" .external}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}} provides tamper-proof, enterprise cloud database environments with high availability for workloads with sensitive data. It offers a flexible and scalable platform that allows you to easily provision and manage your database of choice ({{site.data.keyword.postgresql}} and [{{site.data.keyword.mongodb}}](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-gettingstarted)), without data security concerns.
{: shortdesc}

For more information about the industry-leading data security level of {{site.data.keyword.ihsdbaas_postgresql_full}}, see [Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security).

{{site.data.keyword.ihsdbaas_postgresql_full}} provides {{site.data.keyword.postgresql}} database clusters in the {{site.data.keyword.cloud_notm}}. Each {{site.data.keyword.ihsdbaas_full}} database cluster has one primary node and two secondary nodes (replicas that back up the primary). For more information about high data availability, see [High availability and disaster recovery](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery).

With {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can create database clusters, scale your resources, view information about your nodes, databases, and users, monitor databases, and view service logs.

Watch the following video to find out how to get started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}}:

![Getting started with {{site.data.keyword.ihsdbaas_full}}](https://www.kaltura.com/p/1773841/sp/177384100/embedIframeJs/uiconf_id/27941801/partner_id/1773841?iframeembed=true&entry_id=0_2wa8vkxt){: video output="iframe" data-script="none" id="mediacenterplayer" frameborder="0" width="560" height="315" allowfullscreen webkitallowfullscreen mozAllowFullScreen}

## Supported version
{: #postgresql_supported_version}

{{site.data.keyword.ihsdbaas_postgresql_full}} currently supports {{site.data.keyword.postgresql}} 10. It provides a secure, up-to-date version of the {{site.data.keyword.postgresql}} Enterprise database. We upgrade database maintenance versions `major.minor.maintenance` when appropriate.

For more information about versions, see [{{site.data.keyword.postgresql}} support policy](https://www.postgresql.org/support/versioning/){: external}.

## Prerequisites
{: #prerequisite}

1. To use the UI, make sure you're using the [required browser software](/docs/overview?topic=overview-prereqs-platform) for {{site.data.keyword.cloud_notm}}.

  For Safari, ensure that the **Prevent cross-site tracking** and **Block all cookies** options under **Safari > Preferences > Privacy** are not selected.

  If you encounter problems when you use one of the required browsers, disable your browser plug-ins.

2. You can create a 30-day free plan service instance (or a paid service instance) with three types of accounts: [Pay-As-You-Go, Subscription](/docs/account?topic=account-accounts), or [trial accounts](/docs/account?topic=account-accountfaqs#freetrial) (trial accounts are available for faculty and students at accredited academic institutions).

  To check your account type, go to the [Account settings](https://cloud.ibm.com/account/settings){: external} page.

  If you have a Lite account, you need to [upgrade your account to a Pay-As-You-Go or Subscription account](/docs/account?topic=account-upgrading-account), or [convert it to a trial account](/docs/account?topic=account-accountfaqs#convertacct).

## Step 1. Create a service instance
{: #creating-a-database-cluster-introduction}
{: help} 
{: support}

When you create a service instance, you create a cloud database cluster (replica set) with one primary and two secondary nodes as replicas, as shown in the following diagram. 

![A {{site.data.keyword.ihsdbaas_full}} service instance](images/cluster-node-db.svg "A {{site.data.keyword.ihsdbaas_full}} service instance with high availability"){: caption="Figure 1. A {{site.data.keyword.ihsdbaas_full}} service instance with high availability" caption-side="bottom"}

You can create a service instance through the UI, the CLI, and the API. For more information and detailed instructions, see [Creating a service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service).

Free plans are designed for evaluation purposes and are not suitable for production usage. Free-plan service instances will be automatically deleted 30 days after creation.
{: note}

## Step 2. Connect to databases
{: #accessing-database-introduction}

After you create a {{site.data.keyword.postgresql}} database, you can use psql or your favorite {{site.data.keyword.postgresql}} tool to connect to your databases. {{site.data.keyword.ihsdbaas_postgresql_full}} allows only [SSL](#x2038004){: term}-secured client connections. If you create a service instance with both private and public endpoints, you can connect in either way by choosing from the two commands on the service dashboard.

### Before you begin
{: #accessing-database-introduction-byb}

The tool that you use needs to be compatible with {{site.data.keyword.postgresql}} 10 that is supported by {{site.data.keyword.ihsdbaas_postgresql_full}}.

To enable verification of the server certificate during database connection, download the [certificate authority (CA)](#x2016383){: term} file from the **Manage** page on the service dashboard, and copy it to the appropriate directory.

#### Using psql shell
{: #accessing-database-introduction-connect-psqlshell}

To use the [psql shell](https://www.postgresql.org/download/){: external} to connect to your databases, run the following command. You can copy the command from the service dashboard.

```
psql "host=<host_name> user=<user_name> port=<port> sslmode=verify-full sslrootcert=<CAFilePath>"
```
{: codeblock}

**Command options**

- *host_name*

  The hostname of the database cluster.

- *user_name*

  The user name for the database admin as specified on the service creation page.

- *port*

  The port number of the database cluster.

- *sslmode*

   {{site.data.keyword.ihsdbaas_postgresql_full}} supports the following values for the `sslmode` parameter of the psql command: `allow`, `prefer`, `require`, `verify-ca`, and `verify-full`. It is recommended to specify the parameter as `verify-full`.

- *CAFilePath*

  The path of the `cert.pem` file that you downloaded from the service dashboard.

It is recommended to always enable full verification of the server certificate when you use psql. To do so, specify the parameter `sslmode = verify-full` and provide the `sslrootcert` parameter. {{site.data.keyword.ihsdbaas_postgresql_full}} doesn't support non-secure client connections and the connection will fail if you specify the `sslmode` parameter as `disable`.
{: note}

#### Using pgAdmin or other tools
{: #accessing-database-introduction-connect-other}

For other tools, such as pgAdmin, {{site.data.keyword.ihsdbaas_postgresql_full}} supports *SSL server certificate validation* to connect to the host.

For example, to use pgAdmin to connect to your databases, complete the following steps:
1. Download and install [pgAdmin](https://www.pgadmin.org/download/){: external}.
2. Download the certificate authority (CA) file from the **Manage** page on the {{site.data.keyword.ihsdbaas_postgresql_full}} service dashboard.
3. Open pgAdmin.
4. On the pgAdmin dashboard, select **Add New Server** from the **Quick links** section. In the **Create - Server** dialog, provide the required values.
  - On the **General** page, fill in **Name** and leave the **Connect now?** option checked.
  - On the **Connection** page, fill out the basic connection information.
  - On the **SSL** page, for **SSL mode**, select any option but not **Disable**. **Verify-Full** is recommended. For **Root certificate**, select the CA file downloaded in step 2.
5. Click **Save**.

## Step 3. Manage the database cluster
{: #managing-database-cluster-introduction}
{: help} 
{: support}

Each {{site.data.keyword.ihsdbaas_postgresql_full}} cluster contains a DBaaS Manager, which manages and intelligently schedules your requests based on the available resources.

In a database cluster, you can:
- Scale your resources
- Change database configuration
- View information about databases, users and nodes
- View service logs
- Monitor databases
- ...

You can send the requests to the DBaaS Manager through the UI, the CLI, and the API. For detailed instructions, see [Managing your service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service).

To create or delete your databases and database users, use your database client.

To enable PostrgeSQL extensions, see [Managing PostgreSQL extensions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-extensions). For database clusters that are created after 23 September, 2019, the PL/Java extension is enabled automatically. For more information about using the PL/Java extension, see [Using PL/Java extension](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use_pljava_extension).

## Step 4 (Optional). Migrate from {{site.data.keyword.postgresql}} databases
{: #migrating-from-postgresql}

To migrate from {{site.data.keyword.postgresql}} databases to {{site.data.keyword.ihsdbaas_postgresql_full}}, follow the [migration instructions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-migration_postgre).
