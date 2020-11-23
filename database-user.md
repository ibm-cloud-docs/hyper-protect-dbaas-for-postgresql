---

copyright:
  years: 2019, 2020
lastupdated: "2020-11-24"

keywords: database user, Users page, user name

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

# Viewing information about database users
{: #database-users}

You can view information about your database users and manage their roles and privileges through the UI, the CLI, and the API. To create or delete the database users, use your database client.
{: shortdesc}

To manage user roles and privileges, see [Managing users, roles, and privileges](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-user-management).

For more information about the role attributes and privileges of {{site.data.keyword.postgresql}} database users, see [Role attributes](https://www.postgresql.org/docs/12/role-attributes.html){: external} and [Privileges](https://www.postgresql.org/docs/12/ddl-priv.html){: external}.

## Viewing information about database users in the UI
{: webui-database-users}

In the service dashboard, select **Users** in the side navigation pane to view the information about your database users.

## Viewing information about database users from the CLI
{: cli-database-users}

Use the [commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_cmds) to list all your database users in the service instance and get detailed information about the database users.

## Viewing information about database users with the API
{: api-database-users}

- Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-database-users){: external} to list all your database users in the service instance. 
- Use the [request](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#get-database-user-details){: external} to get detailed information about the database users.
