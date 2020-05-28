---

copyright:
  years: 2019, 2020
lastupdated: "2020-05-28"

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
{:external: target="_blank" .external}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}} provides tamper-proof, enterprise cloud database environments with high availability for workloads with sensitive data. It offers a flexible platform that allows you to easily provision and manage your database of choice, without data security concerns.
{: shortdesc}

For more information about the industry-leading data security level of {{site.data.keyword.ihsdbaas_postgresql_full}}, see [Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security).

{{site.data.keyword.ihsdbaas_postgresql_full}} provides {{site.data.keyword.postgresql}} database clusters in the {{site.data.keyword.cloud_notm}}. Each {{site.data.keyword.ihsdbaas_full}} database cluster has one primary node and two secondary nodes (replicas that back up the primary). For more information about high data availability, see [High availability and disaster recovery](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery).

With {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can create database clusters, view information about your nodes, databases, and users, monitor databases, and view service logs.

Watch the following video to find how to get started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}:

<iframe width="737" height="415" src="https://www.youtube.com/embed/YzQdszTI4Zg" title="Getting started with Hyper Protect DBaaS" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Supported version
{: #postgresql_supported_version}

{{site.data.keyword.ihsdbaas_postgresql_full}} currently supports {{site.data.keyword.postgresql}} 10. It provides a secure, up-to-date version of the {{site.data.keyword.postgresql}} Enterprise database. We upgrade database maintenance versions `major.minor.maintenance` when appropriate.

For more information about versions, see [{{site.data.keyword.postgresql}} support policy](https://www.postgresql.org/support/versioning/){: external}.

## Prerequisite
{: #prerequisite}

Before you start, make sure you're using the [required browser software](/docs/overview?topic=overview-prereqs-platform) for {{site.data.keyword.cloud_notm}}.

For Safari, ensure that the **Prevent cross-site tracking** and **Block all cookies** options under **Safari > Preferences > Privacy** are not selected.

If you encounter problems when you use one of the required browsers, disable your browser plug-ins.

## Step 1. Create a service instance
{: #creating-a-database-cluster-introduction}
{: help} 
{: support}

When you create a service instance, you create a cloud database cluster (replica set) with one primary and two secondary nodes as replicas, as shown in the following diagram. 

![A {{site.data.keyword.ihsdbaas_full}} service instance](images/cluster-node-db.svg "A {{site.data.keyword.ihsdbaas_full}} service instance with high availability"){: caption="Figure 1. A {{site.data.keyword.ihsdbaas_full}} service instance with high availability" caption-side="bottom"}

If you haven't created a service instance yet, you can create one through [the web user interface](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service), [the CLI](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service), or [the {{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v1){: external}.

Free plans are available. They are designed for evaluation purposes and are not suitable for production usage. If you create free-plan instances, note that they will be automatically deleted 30 days after creation.

You can select a root key that you create in {{site.data.keyword.hscrypto}} or {{site.data.keyword.keymanagementserviceshort}} only when you create the DBaaS instance. Otherwise, a randomly generated key will be used by default.
{: note}

For database clusters that are created after 23 September, 2019, the PL/Java extension is enabled automatically. For more information about using the PL/Java extension, see [Using PL/Java extension](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use_pljava_extension).

For database clusters that are created after 19 February, 2020, the ltree module is enabled automatically. For more information about using the ltree module, see [Using ltree module](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use-ltree-module).

## Step 2. Manage the database cluster
{: #managing-database-cluster-introduction}
{: help} 
{: support}

Each {{site.data.keyword.ihsdbaas_postgresql_full}} cluster contains a DBaaS Manager, which manages and intelligently schedules your requests based on the available resources.

In a database cluster, you can:
- View information about databases
- View information about users
- View information about nodes
- View service logs
- Monitor databases

You can send the requests to the DBaaS Manager through one of the following interfaces:

- [The web user interface](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- [The CLI plug-in with the {{site.data.keyword.cloud_notm}} CLI tool](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)
- [The {{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v1){: external}

To manage your databases and database users, use your database client.

## Step 3. Connect to databases
{: #accessing-database-introduction}

After you create a {{site.data.keyword.postgresql}} database, you can use psql or your favorite {{site.data.keyword.postgresql}} tool to connect to your databases. {{site.data.keyword.ihsdbaas_postgresql_full}} allows only [SSL](#x2038004){: term}-secured client connections.

### Before you begin
{: #accessing-database-introduction-byb}

The tool that you use needs to be compatible with {{site.data.keyword.postgresql}} 10 that is supported by {{site.data.keyword.ihsdbaas_postgresql_full}}.

To enable verification of the server certificate during database connection, download a [certificate authority (CA)](#x2016383){: term} file from the **Overview** page in the service dashboard, and copy it to the appropriate directory.

#### Using psql shell
{: #accessing-database-introduction-connect-psqlshell}

To use the [psql shell](https://www.postgresql.org/download/){: external} to connect to your databases, run the following command. You can copy the commmand from the service dashboard.

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

  The path of the `cert.pem` file you downloaded from the service dashboard.

It is recommended to always enable full verification of the server certificate when you use psql. To do so, specify the parameter `sslmode = verify-full` and provide the `sslrootcert` parameter. {{site.data.keyword.ihsdbaas_postgresql_full}} doesn't support non-secure client connections and the connection will fail if you specify the `sslmode` parameter as `disable`.
{: note}

#### Using other tools
{: #accessing-database-introduction-connect-other}

For other tools, such as pgAdmin, {{site.data.keyword.ihsdbaas_postgresql_full}} supports *SSL server certificate validation* to connect to the host. If needed, use the CA file from the service dashboard.

## Step 4 (Conditional). Migrate from {{site.data.keyword.postgresql}} databases
{: #migrating-from-postgresql}

To migrate from {{site.data.keyword.postgresql}} databases to {{site.data.keyword.ihsdbaas_postgresql_full}}, follow the [migration instructions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-migration_postgre).
