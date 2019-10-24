---

copyright:
  years: 2019
lastupdated: "2019-10-23"

keywords: database user, Users tab, user name

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

# Managing database users
{: #dbaas-webui-database-users}

In the {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} dashboard, select the **Users** tab to manage database users.
{: shortdesc}

## Creating a database user
{: #webui-create-database-user}

For information about the role attributes and privileges of {{site.data.keyword.postgresql}} database users, see [Role attributes](https://www.postgresql.org/docs/12/role-attributes.html){: external} and [Privileges](https://www.postgresql.org/docs/12/ddl-priv.html){: external}.

1. Click **Create**.
2. Enter the required values:
 - **User name** - The name of the user.
 - **Password** - The password for the user.
 - **Confirm password** - Confirm the password for the user.
 - **Databases** - (Optional) Databases that the user has privileges on. You can also specify databases after you create the user.
3. Click **Create**.

## Deleting a database user
{: #webui-delete-database-user}

1. Select the database user.
2. Click **Delete**.
