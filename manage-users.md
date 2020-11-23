---

copyright:
  years: 2020
lastupdated: "2020-11-24"

keywords: users, roles, DBaaS admin user, privileges

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

# Managing users, roles, and privileges
{: #user-management}

PostgreSQL uses a system of roles to manage database permissions. When a single user or a group of users is granted a role, the user or group are granted with the corresponding set of privileges. You can list roles in your {{site.data.keyword.ihsdbaas_postgresql_full}} instance by using the `psql` command `\du`.
{: shortdesc}

```
admin=> \du

Role name | Attributes | Member of
-------------+-----------------------------+----------------------
admin | Create role, Create DB | {ibm-cloud-admin}
ibm-cloud-admin | Create role, Create DB, Cannot login | {pg_monitor, pg_signal_backend}
postgres | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
replicator | Replication | {}
```

When you create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in {{site.data.keyword.cloud_notm}}, you are automatically given the `ibm-cloud-admin` role to access and manage PostgreSQL databases.

If your databases are created with the default PostgreSQL `template1` after [October 14, 2020](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-what-new#october-2020), the database owner is automatically granted the `ibm-cloud-admin` role to [`CREATE CAST`](https://www.postgresql.org/docs/10/sql-createcast.html){: external}. With `CREATE CAST`, customized data type can be created to build required data models. If your databases are created with other PostgreSQL templates, the superuser `postgres` is the only role who can `CREATE CAST`. For more information about template databases, see [Template Databases](https://www.postgresql.org/docs/10/manage-ag-templatedbs.html){: external} in PostgreSQL documentation.
{: note}

## The `ibm-cloud-admin` role
{: #role-ibm-cloud-admin}

### How do I get the `ibm-cloud-admin` role?
{: #get-ibm-cloud-admin-role}

When you create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in {{site.data.keyword.cloud_notm}}, you are the `admin` user and are automatically given the `ibm-cloud-admin` role to access and manage PostgreSQL.

If your {{site.data.keyword.ihsdbaas_postgresql_full}} service instances were created before [October 14, 2020](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-what-new#october-2020), you need to use a user who has the `Create role` privilege and grant the `ibm-cloud-admin` role to the database admin or any user who needs it.

### What can I do with the `ibm-cloud-admin` role?
{: #ibm-cloud-admin-role-privileges}

When a user in `ibm-cloud-admin` creates a resource in a database, like a table, all users in `ibm-cloud-admin` own that object. Resources that are created by users in `ibm-cloud-admin` are not accessible by other users, unless they are granted required permissions.

The biggest difference between the `ibm-cloud-admin` role user and other users you add to your service instance is the [`pg_monitor`](https://www.postgresql.org/docs/10/default-roles.html){: external} and [`pg_signal_backend`](https://www.postgresql.org/docs/10/default-roles.html){: external} roles. The `pg_monitor` role provides a set of permissions for monitoring the database server. The `pg_signal_backend` role provides the ability to send signals to cancel queries and connections initiated by other users except database superusers.

A user with the `ibm-cloud-admin` role can grant these two roles to other users or roles in your service instance. For example:

- If you want to set up a specific monitoring user, `deb`, run the following command:
  ```
  GRANT pg_monitor TO deb;
  ```
  {: codeblock}

  You can also grant `pg_monitor` to all the users with the `admin` role with the following command:
  ```
  GRANT pg_monitor TO "admin";
  ```
  {: codeblock}

- If you want to expose the ability to cancel queries to other database users, you can grant the `pg_signal_backend` role to them. For example, run the following command to enable user `stan` to cancel backends:
  ```
  GRANT pg_signal_backend TO stan;
  ```
  {: codeblock}

  You can also grant `pg_signal_backend` to all the users with the `admin` role with the following command:
  ```
  GRANT pg_signal_backend TO "admin";
  ```
  {: codeblock}

  This privilege allows the user or users to end any connections to the database, so assign it with care.
  {: note}

<!--
## Users created through the CLI and the APIs
{: #user-created-via-CLI-API}

Users that you create through the {{site.data.keyword.ihsdbaas_postgresql_full}} CLI and the APIs will be members of `ibm-cloud-admin`. They are able to create users and create databases, but cannot log in.

When a user creates a resource in a database, like a table, all users that are in the same group have access to that resource. Resources created by any of the users in `ibm-cloud-admin` are accessible to other users in `ibm-cloud-admin`.
-->
