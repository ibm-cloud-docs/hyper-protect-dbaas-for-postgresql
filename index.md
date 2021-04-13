---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: hyper protect dbaas, hyper protect dbaas for postgresql, postgresql, cloud database, data security, secure database, encrypted database

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


# Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}} provides tamper-proof, enterprise cloud database environments with high availability for workloads with sensitive data. It offers a flexible and scalable platform that allows you to easily provision and manage your database of choice ({{site.data.keyword.postgresql}} and [{{site.data.keyword.mongodb}}](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-gettingstarted)), without data security concerns.
{: shortdesc}

For more information about the industry-leading data security level of {{site.data.keyword.ihsdbaas_postgresql_full}}, see [Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security).

{{site.data.keyword.ihsdbaas_postgresql_full}} provides {{site.data.keyword.postgresql}} database clusters in the {{site.data.keyword.cloud_notm}}. Each {{site.data.keyword.ihsdbaas_full}} database cluster has one primary node and two secondary nodes (replicas that back up the primary). For more information about high data availability, see [High availability and disaster recovery](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery).

With {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you can create database clusters, scale your resources, view information about your nodes, databases, and users, monitor databases, and view service logs.

Watch the following video to find out how to get started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}}:

![Getting started with {{site.data.keyword.ihsdbaas_full}}](https://www.kaltura.com/p/1773841/sp/177384100/embedIframeJs/uiconf_id/27941801/partner_id/1773841?iframeembed=true&entry_id=0_2wa8vkxt){: video output="iframe" data-script="#video-transcript-gettingstarted" id="mediacenterplayer" frameborder="0" width="560" height="315" allowfullscreen webkitallowfullscreen mozAllowFullScreen}

## Video transcript
{: #video-transcript-gettingstarted}
{: notoc}

Hi, welcome to this getting started video for IBM Cloud™ Hyper Protect DBaaS, an offering that allows you to easily provision and manage highly secure, high volume databases for your sensitive data without sacrificing performance.

Every Hyper Protect DBaaS service instance contains a highly available three-node cluster with multi-zone region support. Built on LinuxONE technology, Hyper Protect DBaaS encrypts both data at rest and data in flight. It offers complete data confidentiality; not even the cloud admin has access to your data. It also supports many industry certifications, GDPR for example, and client regulatory compliance activities. And as you will see in the rest of this video, you can easily provision and monitor secure MongoDB or PostgreSQL databases without specialized database skills.

In the following demo, you will learn how to create a Hyper protect DBaaS service instance, connect to your databases, and navigate the service dashboard.

Before you start, you need to have an IBM Cloud account and log in. Go to the IBM Cloud service Catalog and find Hyper Protect DBaaS. You can choose between MongoDB and PostgreSQL. In this video, we’ll use MongoDB as an example.

On the service provisioning page, select a region and a pricing plan. With the flexible plan, you can select your initial resource allocation values.

You can also try out the service with the free plan. The service name is auto-generated. Select a resource group to organize your resources, which can't be changed after you create the instance. Tags are optional. Name the cluster and the admin. Enter and confirm your password. You can choose to use your own KMS instance with a root key for more secure encryption. You also have the option of using private service endpoints to enhance control and security over your data.

You can find the service instance you just created on the Resource list page. It takes a few minutes for the provisioning to complete. Select your service instance to open the service dashboard.

Click Getting started to read the getting started documentation. If you need more information and detailed instructions, select View docs in Actions to go to the full documentation.

To connect to the databases, you can run the mongo shell command or use MongoDB Compass. In this video, we'll use MongoDB Compass. In the service dashboard, download the certificate authority file, and copy the cluster URL.

Open MongoDB Compass. Paste your connection string. Click Fill in connection fields individually. In the Authentication dropdown list, choose Username / Password, enter your admin name and password. In the More options tab, for SSL, select Server Validation. Upload the certificate authority file you just downloaded, and click Connect. Now you have connected to your databases.

Let’s go back to the service dashboard.

If you are using the flexible pricing plan, you can see the Resources label. On the resources page, you can manually adjust the amount of resources to suit your workload and the size of your data. If you are using the old fixed pricing plan (aka. Small, Medium, or Large), go to the Plan page first to convert you fixed pricing plan to the flexible plan and reload the dashboard to see the Resources page and scale your resources. Free service instances can't be converted or scaled.

On the Manage page, you can see the overall information of your service instance.

Select Databases and Users to view the information about your databases and users.

Select Nodes to view the information of your primary and secondary nodes, and download audit and mongod logs.

Select Observability to go to monitoring and logging. To use monitoring or logging, first you need to agree to sending your metrics or logs to the monitoring or logging service. The steps to add monitoring and logging are similar. Here we’ll use logging as an example. Click Add logging. If you don't have a Log Analysis service instance, you'll be directed to the service creation page to create one. Select the same region as your service instance. After you add the Log Analysis service instance, click Launch logging to be directed to the Log Analysis dashboard to view the logs.

Similarly, you can add the IBM Cloud Monitoring service to monitor your CPU, memory and disk usage.

Now you have a general idea about the service. Go to the [Hyper Protect DBaaS homepage](https://www.ibm.com/cloud/hyper-protect-dbaas){: external} to learn more and get started for free.

## Supported version
{: #postgresql_supported_version}

{{site.data.keyword.ihsdbaas_postgresql_full}} currently supports {{site.data.keyword.postgresql}} 10. It provides a secure, up-to-date version of the {{site.data.keyword.postgresql}} Enterprise database. We upgrade database maintenance versions `major.minor.maintenance` when appropriate.

For more information about versions, see [{{site.data.keyword.postgresql}} support policy](https://www.postgresql.org/support/versioning/){: external}.

## Prerequisites
{: #prerequisite}

1. To use the UI, make sure you're using the [required browser software](/docs/overview?topic=overview-prereqs-platform) for {{site.data.keyword.cloud_notm}}.

  For Safari, ensure that the **Prevent cross-site tracking** and **Block all cookies** options under **Safari > Preferences > Privacy** are not selected.

  If you encounter problems when you use one of the required browsers, disable your browser plug-ins.

2. You can create a 30-day free plan service instance with three types of accounts: [Pay-As-You-Go, Subscription](/docs/account?topic=account-accounts), or [trial accounts](/docs/account?topic=account-accountfaqs#freetrial) (trial accounts are available for faculty and students at accredited academic institutions).

  To check your account type, go to the [Account settings](https://cloud.ibm.com/account/settings){: external} page.

  If you have a Lite account, you need to [upgrade your account to a Pay-As-You-Go or Subscription account](/docs/account?topic=account-upgrading-account), or [convert it to a trial account](/docs/account?topic=account-accountfaqs#convertacct).

## Step 1. Create a service instance
{: #creating-a-database-cluster-introduction}
{: help} 
{: support}

When you create a service instance, you create a cloud database cluster (replica set) with one primary and two secondary nodes as replicas, as shown in the following diagram. 

![A {{site.data.keyword.ihsdbaas_full}} service instance](images/cluster-node-db.svg "A {{site.data.keyword.ihsdbaas_full}} service instance with high availability"){: caption="Figure 1. A {{site.data.keyword.ihsdbaas_full}} service instance with high availability" caption-side="bottom"}

You can create a service instance through the UI, CLI, and API. For more information and detailed instructions, see [Creating a service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service).

Free plans are designed for evaluation purposes and are not suitable for production usage. Free-plan service instances will be automatically deleted 30 days after creation.
{: note}

## Step 2. Connect to databases
{: #accessing-database-introduction}

After you create a {{site.data.keyword.postgresql}} database, you can use psql or your favorite {{site.data.keyword.postgresql}} tool to connect to your databases. {{site.data.keyword.ihsdbaas_postgresql_full}} allows only [SSL](#x2038004){: term}-secured client connections. If you create a service instance with both private and public endpoints, you can connect in either way by choosing from the two commands on the service dashboard.

### Before you begin
{: #accessing-database-introduction-byb}

The tool that you use needs to be compatible with {{site.data.keyword.postgresql}} 10 that is supported by {{site.data.keyword.ihsdbaas_postgresql_full}}.

To enable verification of the server certificate during database connection, download the [certificate authority (CA)](#x2016383){: term} file from the **Overview** page on the service dashboard, and copy it to the appropriate directory.

The CA file you download from the dashboard contains root and intermediate certificates, which are both required for certificate validation.
{: note}

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
2. Download the certificate authority (CA) file from the **Overview** page on the {{site.data.keyword.ihsdbaas_postgresql_full}} service dashboard.
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

You can send the requests to the DBaaS Manager through the UI, CLI, and API. For detailed instructions, see [Managing your service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service).

To create or delete your databases and database users, use your database client.

To enable PostrgeSQL extensions, see [Managing PostgreSQL extensions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-extensions). For database clusters that are created after 23 September, 2019, the PL/Java extension is enabled automatically. For more information about using the PL/Java extension, see [Using PL/Java extension](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use_pljava_extension).

## Step 4 (Optional). Migrate from {{site.data.keyword.postgresql}} databases
{: #migrating-from-postgresql}

To migrate from {{site.data.keyword.postgresql}} databases to {{site.data.keyword.ihsdbaas_postgresql_full}}, follow the [migration instructions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-migration_postgre).
