---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-23"

keywords: database, DBaaS dashboard

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

# Viewing information about databases
{: #databases}

In an {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} cluster, a node hosts databases.
{: shortdesc}

You can view information about your databases through the UI, the CLI, and the API. To manage the databases, use your database client.

## Viewing information about databases in the UI
{: webui-databases}

In the service dashboard, select **Databases** in the side navigation pane to view the name and size of your databases. 

## Viewing information about databases from the CLI
{: cli-databases}

Use the [command](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_list) to list all your databases in the service instance. 

## Viewing information about databases with the API
{: api-databases}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-databases){: external} to list all your databases in the service instance. 
