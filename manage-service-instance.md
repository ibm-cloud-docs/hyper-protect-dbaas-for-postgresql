---

copyright:
  years: 2020, 2021
lastupdated: "2021-05-12"

keywords: database cluster, create service instance, DBaaS dashboard

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


# Managing your service instance
{: #manage-service}

You can manage your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance through the UI, CLI, and API.
{: shortdesc}

To scale your resources, see [Scaling RAM, disk, and vCPU](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling). To change your database configuration, see [Changing the PostgreSQL configuration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration).

## Viewing information about your service instance
{: #show-detail-service}

You can view information about your service instances, databases, users, and nodes. To enable logging and monitoring, see [Logging for {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-sendlogs) and [Monitoring metrics for {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-monitor).

### Viewing information in the UI
{: #webui-show-service}
{: ui}

1. In the {{site.data.keyword.cloud_notm}} console, click **View all** on the **Resource summary** pane, or click **Resource List** in the upper left corner, to display all your resources.
2. Select the service instance on the **Resource list** to display the service dashboard. On the **Overview** page, you can see the overall information and connection information of the service instance.
3. Select **Databases**, **Users**, and **Nodes** in the side navigation pane to view more information.

### Viewing information from the CLI
{: #cli-show-service}
{: cli}

- [List your service instances.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instances)
- [Show the details of your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance)
- To view information about your databases, users, and nodes, use the DBaaS CLI plug-in commands in [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).

### Viewing information with the API
{: #api-show-service}
{: api}

Use the [{{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-service-instances){: external} to list your service instances, get detailed information about your service instance, and so on.

## Managing your service instance
{: #manage-service-how}

With the required access, you can rename, delete, add tags to, and export the access report (a list of users and services that have access to your resource) of your service instance.

For more information about deleting (and restoring) your service instance, see [Deleting your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#data-delete).
{: important}

To assign access to other users or services to use your service instance, see [Managing access for {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam). To manage {{site.data.keyword.postgresql}} roles and privileges for your database users, see [Managing users, roles, and privileges](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-user-management).

### Managing your service instance in the UI
{: #webui-manage-service}
{: ui}

1. Go to the **Resource list** page in the {{site.data.keyword.cloud_notm}} console.
2. Expand **Services**. Find the target service instance and click the overflow icon.
3. Select the action that you want to complete.

### Managing your service instance from the CLI
{: #cli-manage-service}
{: cli}

- [Rename your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update)
- [Delete your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete)
- [Add tags to your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_tag_attach)
- Downloading in the [UI](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service#webui-manage-service) is only way to get your access report. 

### Managing your service instance with the API
{: #api-manage-service}
{: api}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#delete-a-service-instance){: external} to delete your service instance. For the other tasks, see the UI or CLI instructions.
