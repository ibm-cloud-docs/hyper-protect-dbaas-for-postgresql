---

copyright:
  years: 2020
lastupdated: "2020-10-14"

keywords: database cluster, create service instance, DBaaS dashboard

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

# Managing your service instance
{: #manage-service}

You can manage your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance through the UI, the CLI, and the API.
{: shortdesc}

To change your database configuration, see [Changing the PostgreSQL configuration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration).

## Viewing information about your service instance
{: #show-detail-service}

You can view information about your service instances, databases, users, and nodes. To enable logging and monitoring, see [Sending logs to {{site.data.keyword.la_full_notm}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-sendlogs) and [Monitoring databases](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-monitor).

### Viewing information in the UI
{: #webui-show-service}

1. In the {{site.data.keyword.cloud_notm}} dashboard, click **View resources** on the **Resource summary** pane, or click **Resource List** in the upper left corner, to display all your resources.
2. Select the service instance on the **Resource list** to display the service dashboard. On the **Overview** page, you can see the overall information and connection information of the service instance.
3. Select **Databases**, **Users**, and **Nodes** in the side navigation pane to view more information.

### Viewing information from the CLI
{: #cli-show-service}

- [List your service instances.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instances)
- [Show the details of your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance)
- To view information about your databases, users, and nodes, use the DBaaS CLI plug-in commands in [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).

### Viewing information with the API
{: #api-show-service}

Use the [{{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-service-instances){: external} to list your service instances, get detailed information about your service instance, etc.

## Managing your service instance
{: #manage-service-how}

With the required access, you can rename, delete, add tags to, and export the access report (a list of users and services that have access to your resource) of your service instance.

Deleting the service instance fully erases all data. {{site.data.keyword.ihsdbaas_postgresql_full}} doesn't support restoring the data for now. For more information about deleting data, see [Deleting your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security#data-delete).
{: important}

To assign access to other users or services to use your service instance, see [Managing access for {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam). To manage {{site.data.keyword.postgresql}} roles and privileges for your database users, see [Managing users, roles, and privileges](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-user-management).

### Managing your service instance in the UI
{: #webui-manage-service}

1. In the {{site.data.keyword.cloud_notm}} dashboard, go to the **Resource list** page.
2. Expand **Services**. Find the target service instance and click the overflow icon.
3. Select the action that you want to complete.

### Managing your service instance from the CLI
{: #cli-manage-service}

- [Rename your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update)
- [Delete your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete)
- [Add tags to your service instance.](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_tag_attach)
- Downloading in the [UI](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service#webui-manage-service) is only way to get your access report. 

### Managing your service instance with the API
{: #api-manage-service}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#delete-a-service-instance){: external} to delete your service instance.
