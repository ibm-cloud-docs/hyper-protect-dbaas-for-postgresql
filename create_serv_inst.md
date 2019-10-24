---

copyright:
  years: 2019
lastupdated: "2019-10-22"

keywords: service instance, ibmcloud resource

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

# Creating a service instance
{: #dbaas_cli_create_service}

To create a {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance, use the `ibmcloud resource service-instance-create` command, as shown in the following example. In Windows, it is recommended that you use a Bash terminal such as Cygwin or Git Bash to enter the command.
{: shortdesc}

```
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Where the parameters have the following definitions:

| Parameter        |  Definition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  The name of the service instance (replace with a name of your own choosing). |
| *hyperp-dbaas-postgresql* | The catalog name of {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | The plan name. Available plans are: **postgresql-small**, **postgresql-medium**, and **postgresql-large**.  (**Note:** Plan names are case-sensitive.) |
| *us-south*            | The location where your new database will be located. |
| *-p*               | A valid JSON string, which must contain the required parameters in the following table. |
{: caption="Table 1.Parameters used in creating a service instance" caption-side="top"}

| Parameter        |  Definition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *name* | The name of your database cluster. |
| *admin_name* | The administrator's user name of the database to be created. |
| *password* | The administrator's user password of the database to be created. The administrator's user password of the database to be created. You need to create a strong password with a minimum of **15 characters**, at least **one uppercase** character, **one lowercase** character, and **one number**. |
| *confirm_password* | The same password. |
| *license_agree* | A value of **agreed** indicates acceptance of the license agreement, which is required to use {{site.data.keyword.ihsdbaas_postgresql_full}}. |
{: caption="Table 2. -p parameters" caption-side="top"}

After you enter the command, the state of the new service instance might temporarily appear as **inactive**, as shown in this example:

```
Creating service instance MYDBaaSIns03 in resource group default of account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Service instance MYDBaaSIns03 was created.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753   
Location:         us-south   
State:            inactive   
Type:             service_instance   
Sub Type:            
Created at:       2019-06-03T06:17:13Z   
Updated at:       2019-06-03T06:17:13Z   
Last Operation:                      
                  Status       create in progress      
                  Updated At   2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

This is because it takes a few minutes to prepare the cluster. To get an update of the cluster status, use the `ibmcloud resource service-instances` command, as shown in this example:

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

To even further strengthen security, it is suggested that you update the **database admin password** immediately after the service instance is provisioned. You need to follow the same rules that are previously mentioned to set the new password.
{: note}

For more DBaaS CLI plug-in commands, see [DBaaS CLI reference](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
