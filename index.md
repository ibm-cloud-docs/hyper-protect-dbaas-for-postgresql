---

copyright:
  years: 2019
lastupdated: "2019-08-28"

keywords: database cluster, Data security, database instance

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

# Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} is an {{site.data.keyword.cloud_notm}} service that provides {{site.data.keyword.postgresql}} databases on demand. It offers a flexible and scalable platform that allows you to quickly and easily provision and manage your database of choice.
{: shortdesc}

This {{site.data.keyword.cloud_notm}} offering provides {{site.data.keyword.postgresql}} database clusters. Each database cluster comprises one primary database instance and two database instance replicas that back up the primary one (for the convenience of reference, the three instances can all be called replicas).

With {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can create database clusters in the {{site.data.keyword.cloud_notm}}, manage database instances, administer database users, create, and monitor databases.

## Supported version
{: #postgresql_supported_version}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} currently supports {{site.data.keyword.postgresql}} 3.6. It provides a secure, up-to-date version of the {{site.data.keyword.postgresql}} Enterprise database. We upgrade database maintenance versions `major.minor.maintenance` when appropriate.

For more information about versions, see [{{site.data.keyword.postgresql}} support policy](https://www.postgresql.com/support-policy){: external}.

## Prerequisite
{: #prerequisite}

Before you start, make sure you are using the [required browser software](/docs/overview?topic=overview-prereqs-platform) for {{site.data.keyword.cloud_notm}}.

For Safari, ensure that the **Prevent cross-site tracking** and **Block all cookies** options under **Safari > Preferences > Privacy** are not selected.

If you encounter problems using one of the required browsers, disable your browser plug-ins.

## Data security and privacy
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} hosts your databases in a highly available and secure environment:
<ul>
<li>The underlying technologies prevent {{site.data.keyword.IBM_notm}} or a third party from being able to
access your data.
<p>The {{site.data.keyword.IBM_notm}} Secure Service Container technology protects the system via a tamper-proof environment. Access to the system is restricted and is only enabled through well-defined RESTful APIs.</p></li>
<li>Data is encrypted at rest and in flight.</li>
<li>The system hardware, the system configuration, and the database setup ensure high availability.</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## Creating a database cluster
{: #creating-a-database-cluster-introduction}

To create a database cluster, you simply enter the required values in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} service configuration screen and click **Create**.

After you have created the database cluster, {{site.data.keyword.IBM_notm}} provides you one or more hostnames and port numbers of the created database instances. You can now use this information and the user credentials you specified in the catalog to create and access your databases.

<!--For new database clusters that are created after August 31, 2019, the PL/Java extension is enabled automatically. For more information about using the PL/Java extension, see [Using PL/Java extension](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use_pljava_extension).-->

## Managing the database cluster
{: #managing-database-cluster-introduction}

In a database cluster, you can create databases, manage the database instances, and create or delete users.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} contains a DBaaS Manager, which manages and intelligently schedules your requests based on the available resources.

You can address requests to the DBaaS Manager through one of these interfaces:

- The [Web User Interface](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- The [{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} RESTful APIs (for service instance management)](/apidocs/hyperp-dbaas){: external}
- The [CLI plug-in with the {{site.data.keyword.cloud_notm}} CLI tool](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)

## Accessing the database
{: #accessing-database-introduction}

After creating a {{site.data.keyword.postgresql}} database, you can use pgAdmin or your favorite {{site.data.keyword.postgresql}} tool to manage the databases.

### Before you begin
{: #accessing-database-introduction-byb}

To ensure secure data transfer, obtain a certificate authority (CA) file from the dashboard, and copy it to the appropriate directory.

### Connecting to a database
{: #accessing-database-introduction-connect}

The {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard provides the necessary information to connect to a database.

#### psql shell
{: #accessing-database-introduction-connect-psqlshell}

You can use this command:
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
Where:
<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> Is the hostname of the database cluster </dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> Is the user name for the Database admin as specified in the service creating screen </dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> Is the port number of the database cluster </dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> Is the path of the CA file </dd>  
</dl>

**Note:** The `psql` command will not verify the database cluster certificate if the options `sslmode` and `sslrootcert` are not provided.

### Other tools
{: #accessing-database-introduction-connect-other}

For other tools, such as pgAdmin, {{site.data.keyword.ihsdbaas_postgresql_full}} supports *SSL server certificate validation* to connect to the host. If needed, use the provided CA file.
