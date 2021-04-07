---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-07"

keywords: database, DBaaS dashboard, template1

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
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}

# Viewing information about databases
{: #databases}

In an {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} cluster, a node hosts databases.
{: shortdesc}

You can view information about your databases through the UI, CLI, and API. To create and manage databases, use your database client. For information about database templates, see [What's the difference between using template0 and template1?](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-faqs-usage#database-template-difference).

## Viewing information about databases in the UI
{: webui-databases}
{: ui}

On the service dashboard, select **Databases** in the side navigation pane to view the name and size of your databases. 

## Viewing information about databases from the CLI
{: cli-databases}
{: cli}

Use the [command](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_list) to list all your databases in the service instance. 

## Viewing information about databases with the API
{: api-databases}
{: api}

Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-databases){: external} to list all your databases in the service instance. 
