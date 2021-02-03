---

copyright:
  years: 2019, 2021
lastupdated: "2021-02-02"

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

# Creating a service instance
{: #create-service}

You can create your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance through the UI, the CLI, and the API.
{: shortdesc}

## Before you begin
{: #create-service-prerequisite}

Make sure you are familiarized with the following information. **Especially if you want to use your own encryption key or use private endpoints**, you need to follow the instructions in the corresponding topics (see the last two points) **before** you create a service instance.
{: note}

- You can create a 30-day free plan service instance with three types of accounts: [Pay-As-You-Go, Subscription](/docs/account?topic=account-accounts), or [trial accounts](/docs/account?topic=account-accountfaqs#freetrial) (trial accounts are available for faculty and students at accredited academic institutions). To check your account type, go to the [Account settings](https://cloud.ibm.com/account/settings){: external} page. If you have a Lite account, you need to [upgrade your account to a Pay-As-You-Go or Subscription account](/docs/account?topic=account-upgrading-account), or [convert it to a trial account](/docs/account?topic=account-accountfaqs#convertacct).

- Free plans are designed for evaluation purposes and are not suitable for production usage. Free-plan service instances will be automatically deleted 30 days after creation. Free plans follow [{{site.data.keyword.cloud_notm}} Service Level Agreements (SLAs)](https://www-03.ibm.com/software/sla/sladb.nsf/pdf/6605-18/$file/i126-6605-18_08-2019_en_US.pdf){: external}.

- For the flexible plan, billing is based on the total amount of resources that are allocated to your service instance. For more information about resources and pricing, see [Resource breakdown](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling#resources-breakdown).

- If you want to create a service instance with your own encryption key, follow the instructions in [{{site.data.keyword.keymanagementserviceshort}} integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) or [{{site.data.keyword.hscrypto}} integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok). You can select your own key only when you create the service instance. Otherwise, a randomly generated key is used by default.

- If you want to create a service instance with private endpoints or both private and public endpoints, follow the instructions in [Securing your connection to {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-service-connection#prereq-service-endpoint).

The database administrator doesn't have SUPERUSER authority. The authorities of the database administrator are limited to INHERIT, CREATEROLE, CREATEDB, LOGIN, and REPLICATION.
{: note}

## Creating a service instance in the UI
{: #webui-create-service}

1. [Log in to your {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/login){: external}.
2. Click **Catalog** on the top menu bar to view the list of services that are available on the {{site.data.keyword.cloud_notm}}.
3. Type `{{site.data.keyword.ihsdbaas_full}}` into the search field. Click the **{{site.data.keyword.ihsdbaas_postgresql_full}}** tile.
4. Choose the free plan or the flexible plan. Enter the required values on the provisioning page. If you choose the flexible plan, select the initial allocation values of RAM, disk, and vCPU. To estimate your costs, click **Add to estimate** or **Estimate costs** and input your allocation values. **Tags** are optional and can be added after you create the service instance. Don't use special characters such as & and # in your password.
5. Click **Create**.
6. Refresh the **Resource List** page after several minutes. When the status of the service instance is **Active**, the instance is ready to use.

## Creating a service instance from the CLI
{: #cli-create-service}

1. [Set up the CLI.](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin)

2. To create a {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance, use the `ibmcloud resource service-instance-create` command, as shown in the following example. In Windows, it is recommended that you use a Bash terminal such as Cygwin or Git Bash to enter the command.

```
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-flexible us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "cpu":2, "memory":"2GiB", "storage":"5GiB", "license_agree":["agreed"], "kms_instance":"crn:v1:bluemix:public:kms:us-south:a/5b9cd17284125db65be173928b05bd50:e0e6a08c-f751-45ce-835f-9db8d01ff54a::", "kms_key":"66f22ec7-1ca9-4ad4-bdae-4ad949470a7c", "db_version":"10"}' --service-endpoints public-and-private
```
{: codeblock}

Where the parameters have the following definitions:

| Parameter        |  Definition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  The name of the service instance (replace with a name of your own choosing). |
| *hyperp-dbaas-postgresql* | The catalog name of {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-flexible*  | The plan name. For a 30-day free trial, use `postgresql-free` and omit the values of cpu, memory, and storage in the `-p` JSON string.<!-- (**Note:** Plan names are case-sensitive.)--> |
| *us-south*            | The location where your new database will be located. |
| *-p*               | A valid JSON string, which must contain the required parameters in the following table. |
| *--service-endpoints* | Enter `private`, `public`, or `public-and-private` for the *--service-endpoints* option. If you omit this option, you will create a service instance with public endpoints.|
{: caption="Table 1. Parameters that are used in creating a service instance" caption-side="top"}

| Parameter        |  Definition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *name* | The name of your database cluster. |
| *admin_name* | The administrator's user name of the database to be created. |
| *password* | The administrator's user password of the database to be created. You need to create a strong password with a minimum of **15 characters**, at least **one uppercase** character, **one lowercase** character, and **one number**. Don't use special characters such as & and #. |
| *confirm_password* | The same password. |
| *license_agree* | A value of `agreed` indicates acceptance of the license agreement, which is required to use {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *cpu* | Total number of dedicated CPU cores. For the valid value range of *cpu*, *memory*, and *storage*, see the [value table](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling#before-scaling). |
| *memory* | Total memory allocation in GiB. |
| *storage* | Total disk allocation in GiB. |
| *kms_instance* | (Optional) Valid CRN of the selected KMS (key management service) instance. |
| *kms_key* | (Optional, paired with *kms_instance*) UUID of the selected root key. |
| *db_version*| (Optional) Supports {{site.data.keyword.postgresql}} 10 only. |
{: caption="Table 2. -p parameters" caption-side="top"}

The *kms_instance* and *kms_key* parameters are required if you want to create a service instance with your own encryption key. {{site.data.keyword.ihsdbaas_postgresql_full}} doesn't verify the *kms_instance* and *kms_key* parameters from the CLI. Make sure you copy and paste the correct values in the same format as the example.
{: important}

After you enter the command, the state of the new service instance might temporarily appear as **inactive** because it takes a few minutes to prepare the cluster. To get an update of the cluster status, use the `ibmcloud resource service-instance` command.

```
ibmcloud resource service-instance MyDBaaSIns03
```
{: codeblock}

For more {{site.data.keyword.cloud_notm}} CLI commands, see the [REFERENCE section of the {{site.data.keyword.cloud_notm}} CLI documentation](/docs/cli?topic=cli-ibmcloud_cli).

## Creating a service instance with the API
{: #api-create-service}

1. [Set up authentication to use the APIs.](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-setup#api-auth)

2. For the detailed API request, see [{{site.data.keyword.ihsdbaas_full}} RESTful APIs](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#create-service){: external}.

## What's next
{: #create-connect}

To even further strengthen security, it is suggested that you update the **database admin password** immediately after the service instance is created. You need to follow the same rules to set the new password.
{: note}

1. To connect to your databases, see [Connecting to databases](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#accessing-database-introduction).
2. To manage your service instance, see [Managing your service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service).
