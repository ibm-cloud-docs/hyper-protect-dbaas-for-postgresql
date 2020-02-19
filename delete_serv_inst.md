---

copyright:
  years: 2019
lastupdated: "2019-12-20"

keywords: ibmcloud resource, service instance, CLI tool

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting a service instance
{: #dbaas_cli_delete_service}

To review the service instances you created, use the following command:
{: shortdesc}

```
~$ ibmcloud resource service-instances
```
{: pre}

If you want to delete one of them, use the `ibmcloud resource service-instance-delete` command, as shown in this example:

```
~$ ibmcloud resource service-instance-delete MyDBaaSIns03
```
{: pre}

Confirm the deletion by typing **y**.

For more DBaaS CLI plug-in commands, see [DBaaS CLI reference](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
