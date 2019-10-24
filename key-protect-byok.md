---

copyright:
  years: 2019
lastupdated: "2019-10-22"

keywords: key protect integration, data encryption, byok

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

# {{site.data.keyword.keymanagementserviceshort}} Integration 
{: #key-protect-byok}

The data that you store in {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} databases are encrypted by default by randomly generated keys. If you need full control over your encryption keys, you can use [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/key-protect?topic=key-protect-about) to create, add, and manage encryption keys and associate the keys with your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance to encrypt your databases.
{: shortdesc}

## Step 1: Creating or adding a root key in {{site.data.keyword.keymanagementserviceshort}}
{: #create-add-key}

To create or add a root key in {{site.data.keyword.keymanagementserviceshort}}, complete the following steps:

 1. [Provision a {{site.data.keyword.keymanagementserviceshort}} service instance](/docs/services/key-protect?topic=key-protect-provision) if you don't have one.

2. Navigate to your instance of {{site.data.keyword.keymanagementserviceshort}} and [create a root key](/docs/services/key-protect?topic=key-protect-create-root-keys) or [import an existing root key](/docs/services/key-protect?topic=key-protect-getting-started-tutorial#import-keys).

## Step 2: Granting service authorization
{: #grant-authorization}

Authorize {{site.data.keyword.keymanagementserviceshort}} for use with {{site.data.keyword.ihsdbaas_postgresql_full}} service instances:

1. Open your {{site.data.keyword.cloud_notm}} dashboard.
2. From the menu bar, click **Manage** > **Access (IAM)**.
3. In the side navigation, click **Authorizations**.
4. Click **Create**.
5. In the **Source service** menu, select **{{site.data.keyword.ihsdbaas_postgresql_full}}**.
6. In the **Source service instance** menu, select **All service instances**.
7. In the **Target service** menu, select **{{site.data.keyword.keymanagementserviceshort}}**.
8. In the **Target service instance** menu, select the service instance to authorize.
9. Enable the **Reader** role.
10. Click **Authorize**.

If you want to remove an authorization, see [Removing an authorization](/docs/iam?topic=iam-serviceauth#remove-auth). 

## Step 3: Creating a {{site.data.keyword.ihsdbaas_postgresql_full}} instance with the {{site.data.keyword.keymanagementserviceshort}} Key
{: use-key-protect}

When you [create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#creating-a-database-cluster-introduction), select your {{site.data.keyword.keymanagementserviceshort}} instance and root key.

The new {{site.data.keyword.ihsdbaas_postgresql_full}} service instance uses your {{site.data.keyword.keymanagementserviceshort}} root key to encrypt your data.

## Step 4 (Optional): Removing keys and deleting your data
{: remove-key}

If you delete the key that is used to encrypt your service, you lose access to the data. You will not be able to recover the data from the instance. You might be able recover your data by restoring a backup into a new service instance.
{: important}

If you want to securely delete your data, you must delete both the service instance and the {{site.data.keyword.keymanagementserviceshort}} key.
