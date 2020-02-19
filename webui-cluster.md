---

copyright:
  years: 2019
lastupdated: "2019-12-20"

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
{:external: target="_blank" .external}

# Creating and managing service instances
{: #dbaas_webui_service}

You can create and manage your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance through the web user interface.
{: shortdesc}

## Creating a service instance
{: #dbaas_webui_create_service}

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.
2. Click **Catalog** on the top menu bar to view the list of services that are available on the {{site.data.keyword.cloud_notm}}.
3. Type `Hyper Protect DBaaS` into the search field. Click the **{{site.data.keyword.ihsdbaas_postgresql_full}}** tile.
4. Choose a pricing plan. Free plans are designed for evaluation purposes and are not suitable for production usage. If you create free-plan instances, note that they will be automatically deleted 30 days after creation. Free plans follow [{{site.data.keyword.cloud_notm}} Service Level Agreements (SLAs)](https://www-03.ibm.com/software/sla/sladb.nsf/pdf/6605-18/$file/i126-6605-18_08-2019_en_US.pdf){: external}.
5. Enter the required values on the provisioning page and click **Create**. **Tags** is optional and can be added after you create the service instance. To create a service instance with your own encryption key, see [{{site.data.keyword.keymanagementserviceshort}} Integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) and [{{site.data.keyword.hscrypto}} Integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok).

  The database administrator does not have SUPERUSER authority. The authorities of the database administrator are limited to INHERIT, CREATEROLE, CREATEDB, LOGIN, and REPLICATION.
  {: note}

6. Refresh the **Resource List** page after several minutes. When the status of the service instance is **Provisioned**, the instance is ready to use.

  To even further strengthen security, it is suggested that you update the **database admin password** immediately after the service instance is provisioned. You need to follow the same rules that are previously mentioned to set the new password.
  {: note}

7. To connect to your databases, see [Connecting to databases](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#accessing-database-introduction).

## Viewing detailed information of a service instance
{: #dbaas_webui_show_detail_service}

1. In the {{site.data.keyword.cloud_notm}} dashboard, click **View resources** on the **Resource summary** pane, or click **Resource List** in the upper left corner, to display all your resources.
2. Select the service instance on the **Resource list** to display the service dashboard.
3. On the **Overview** page, you can see the overall information and connection information of the service instance.
4. Select **Databases**, **Users**, or **Nodes** in the side navigation pane to view the more information. Select **Logging** or **Monitoring** to enable and view logs and metrics of the databases.

## Managing a service instance
{: #dbaas_webui_manage_service}

With the required access, you can re-name, delete, add tags to, and export the access report of a service instance.

1. In the {{site.data.keyword.cloud_notm}} dashboard, go to the **Resource list** page.
2. Expand **Services**. Find the target service instance and click the overflow icon.
3. Select the action that you want to complete.

To assign access to other users or services to use your service instance, see [Identity and Access Management roles and actions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam).
