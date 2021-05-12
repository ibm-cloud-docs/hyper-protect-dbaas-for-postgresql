---

copyright:
  years: 2019, 2021
lastupdated: "2021-05-12"

keywords: release note, new, added, changed, deleted

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


# Release notes
{: #what-new}

Stay up to date with the new features that are available for {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

## TBD May 2021
{: #may-2021}

### Changed: PL/Java version
{: #pljava-version}

{{site.data.keyword.ihsdbaas_postgresql_full}} supports [PL/Java 1.6.2](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-use_pljava_extension) (previously 1.5.2). Note that for security reasons, **only ports 80 and 443 are allowed** to connect from PL/Java.

### Changed: Automatic handling in tolerance situations
{: #changed-tolerance}

In the tolerance situation during [creating](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service), [disabling](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#service-delete), and [restoring](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#service-restore) service instances, operations on the pending node will be completed automatically later (previously by SRE).

## 7 April 2021
{: #apr-2021}

### Added: Tolerance in creating/disabling/restoring service instances
{: #added-tolerance}

The processes of [creating](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service), [disabling](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#service-delete), and [restoring](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#service-restore) service instances are fault-tolerant in the case that one Availability Zone is unavailable. The operation is considered successful when it's completed on two of the three nodes. Operation on the other node will be completed later by SRE.

### Added: Downstream service calls over IBM Cloud Private Network
{: #added-downstream-service-private-network}

Traffic to [integrated {{site.data.keyword.cloud_notm}} services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-service-integration) (except for {{site.data.keyword.keymanagementserviceshort}} and {{site.data.keyword.hscrypto}}) goes over IBM Cloud Private Network by default, regardless of your endpoint choice during service creation.

### Changed: Dashboard
{: #changed-dashboard}

The **Manage** page on the service dashboard is renamed to **Overview**. Dashboard improvements are also implemented.

### Added: UI/CLI/API switcher in documentation
{: #added-interface-switcher}

An interface switcher is implemented in documentation about tasks that can be completed in multiple interfaces. You can select between the **UI**, **CLI**, and **API** tabs on the top of the topic, depending on which interface you want to use.

### Added: What's the difference between using template0 and template1?
{: #added-template-difference}

Added difference between using `template0` and `template1` in [FAQs about usage](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-faqs-usage#database-template-difference).

## 25 February 2021
{: #feb-2021}

### Added: {{site.data.keyword.ihsdbaas_postgresql_full}} expands into Washington DC region
{: #added-washington-dc-region}

You can [create](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service) {{site.data.keyword.ihsdbaas_postgresql_full}} service instances in the Washington DC region. 

## 23 December 2020
{: #dec-23-2020}

### Added: Database version parameter
{: #added-db-version}

The database version parameter `db_version` is added in the service creation command. Currently, it's optional and only version `10` is supported. For example, if you omit the parameter in the command, you create a service instance running {{site.data.keyword.postgresql}} 10 by default. 

## 15 December 2020
{: #dec-2020}

### Added: Resource reclamation
{: #added-resource-reclamation}

When you delete a service instance, it's disabled (pending reclamation) rather than deleted completely. You can restore a deleted service instance with no data loss within the retention period of seven days. You can also choose to permanently delete it. See [Deleting service instances](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#service-delete).

## 25 November 2020
{: #nov-2020}

### Changed: Pricing plan
{: #changed-pricing-plan}

With the flexible pricing plan, you can select the initial allocation values of RAM, disk, and vCPU. See [Resource breakdown](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling#resources-breakdown).

### Added: Vertical scaling
{: #added-vertical-scaling}

You can manually adjust the amount of resources available to your service instance to suit your workload and the size of your data. You can [scale your resources](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling) by using the UI, CLI, and API.

### Added: {{site.data.keyword.mon_short}}
{: #added-monitoring}

You can monitor the disk, memory, and vCPU usage of your service instance through [integration with {{site.data.keyword.mon_full_notm}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-monitor).

### Added: Changing `max_connections`
{: #added-setting-max-connections}

One more configuration setting that you can change. See [Changing the PostgreSQL configuration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration).

## 14 October 2020
{: #october-2020}

### Added: Securing your connection
{: #added-secure-connection}

You can create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance with [private endpoints](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-service-connection) so that your database data will go over private routes.

### Added: PostgreSQL extension support
{: #added-extension-framework}

You can use the `CREATE EXTENSION` command to [install PostgreSQL extensions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-extensions) from the list of extensions supported by {{site.data.keyword.ihsdbaas_postgresql_full}}.

### Added: `ibm-cloud-admin` role
{: #added-ibm-cloud-admin}

When you create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance, you are automatically given the [`ibm-cloud-admin` role](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-user-management). You have more privileges and can grant privileges to other users or roles.

### Added: Changing the PostgreSQL configuration
{: #added-change-postgresql-configuration}

Users with the Manager role can change some of the [PostgreSQL configuration settings](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration) as needed.

### Added: Managing access to multiple service instances
{: #added-manage-multiple-instances}

You can leverage [{{site.data.keyword.cloud_notm}} enterprises](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#manage-multiple-instances) to manage resources in multiple accounts and user access.

### Changed: Task documentation structure
{: #changed-task-doc-reorg}

For a task that can be completed in multiple interfaces (UI, CLI, and API), the instructions for different interfaces are incorporated in the same topic for the task.

## 23 June 2020
{: #June-2020}

### Changed: `instance_id` is changed to `node_id`
{: #changed-cli-v2}

`instance_id` is changed to `node_id` in commands.

## 19 February 2020
{: #Feb-2020}

### Added: ltree module support
{: #added-ltree}

You can use the ltree module for newly provisioned {{site.data.keyword.ihsdbaas_postgresql_full}} services.

### Added: Related links topic under REFERENCE section
{: #added-related-links}

[Related links](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-related-links) topic lists more resources to help you learn about securing data and resources with {{site.data.keyword.cloud_notm}} Hyper Protect DBaaS.

## 20 December 2019
{: #Dec-2019}

### Added: Role-based authorization with {{site.data.keyword.cloud_notm}} Identity and Access Management
{: #added-iam-integration}

You can assign access to other users or services to use your service instance with {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

### Added: Creating a service instance with your own encryption key
{: #added-byok}

You can create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance with your own encryption key by using {{site.data.keyword.keymanagementservicelong_notm}} or {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}.

### Changed: Dashboard
{: #changed-dashboard}

The major changes to the dashboard are navigation and renaming of terms. The new service dashboard uses side navigation. The terms **instance** and **replica** are replaced by **node**.

### Changed: Manage databases and database users with only database clients
{: #changed-manage}

To enhance security, use your database client to manage databases and database users. The **Databases**, **Users**, and **Nodes** pages on the dashboard are read-only.

### Changed: Python components for using CLI
{: #changed-cli-python}

Python 3 (instead of Python 2) components are required to access a complete set of DBaaS commands when you use the {{site.data.keyword.cloud_notm}} CLI.

## 23 September 2019
{: #Sep23-2019}

### Added: PL/Java extension support
{: #pljava}

You can use the PL/Java extension for newly provisioned {{site.data.keyword.ihsdbaas_postgresql_full}} services.

### Added: Sending logs to {{site.data.keyword.la_full_notm}}
{: #added-logging}
New as of: 2019-09-23

You can view logs of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance in a configured {{site.data.keyword.loganalysisshort_notm}} instance.

### Added: {{site.data.keyword.ihsdbaas_postgresql_full}} expands into Sydney region
{: #added-sydney-region}

You can create {{site.data.keyword.ihsdbaas_postgresql_full}} service instances in the Sydney region. To receive logs and events of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance in Sydney, use {{site.data.keyword.cloud_notm}} {{site.data.keyword.loganalysisshort_notm}} and {{site.data.keyword.at_short}} instances in Dallas for now.

### Changed: Frankfurt support for {{site.data.keyword.cloudaccesstrailshort}}
{: #changed-at-frankfurt}

You can use your {{site.data.keyword.cloudaccesstrailshort}} instance in Frankfurt to view events of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance in Frankfurt.

## 13 September 2019
{: #Sep13-2019}

### Added: Free plans are available
{: #added-free-plans}

You can try out free plans for {{site.data.keyword.ihsdbaas_postgresql_full}}. They're designed for evaluation purposes and are not suitable for production usage. Free-plan service instances will be automatically deleted 30 days after creation.

## 28 August 2019
{: #Aug-2019}

### Added: {{site.data.keyword.ihsdbaas_postgresql_full}} expands into Frankfurt region
{: #added-frankfurt-region}

You can create {{site.data.keyword.ihsdbaas_postgresql_full}} service instances in the Frankfurt region.

## 21 June 2019
{: #June-2019}

### {{site.data.keyword.ihsdbaas_postgresql_full}} is generally available
{: #ga-201906}

{{site.data.keyword.ihsdbaas_full}} is an {{site.data.keyword.cloud_notm}} service that provides tamper-proof, enterprise cloud database environments with high availability for workloads with sensitive data. It offers a flexible platform where you can quickly and easily provision and manage your database of choice.

{{site.data.keyword.IBM_notm}} hosts your databases in a highly available and secure environment.

For more information, see [Getting started with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted).
