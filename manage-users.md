---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-13"

keywords: users, roles, DBaaS admin user, privileges

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Managing users, roles, and privileges
{: #user-management}

PostgreSQL uses the concept of roles to manage database permissions. When a single user or a group of users is granted a role, the user or group are granted with the corresponding set of privileges. You can list roles in your {{site.data.keyword.ihsdbaas_postgresql_full}} instance by using the `psql` command `\du`.
{: shortdesc}

```
admin=> \du
                                                 List of roles
    Role name    |                        Attributes                          |        Member of    
-----------------+------------------------------------------------------------+-------------------------
 admin           | Create role, Create DB                                     | {ibm-cloud-admin}
 ibm-cloud-admin | Create role, Create DB, Cannot login                       | {pg_monitor,pg_signal_backend}
 postgres        | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
 replicator      | Replication                                                | {}                            
```

As a managed cloud database service, {{site.data.keyword.ihsdbaas_postgresql_full}} doesn't grant you the {{site.data.keyword.postgresql}} super user role `postgres` when you create a service instance. Instead, it assigns you to the `ibm-cloud-admin` role that has some super user privileges.

## The `ibm-cloud-admin` role
{: #role-ibm-cloud-admin}

### How do I get the `ibm-cloud-admin` role?
{: #get-ibm-cloud-admin-role}

When you create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in {{site.data.keyword.cloud_notm}}, you are the `admin` user and are automatically given the `ibm-cloud-admin` role to access and manage your databases.

If your {{site.data.keyword.ihsdbaas_postgresql_full}} service instances were created before [14 October, 2020](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-what-new#october-2020), you need to use a user who has the `Create role` privilege to grant the `ibm-cloud-admin` role to the database admin or any user who needs it.

### What can I do with the `ibm-cloud-admin` role?
{: #ibm-cloud-admin-role-privileges}

#### `CREATE CAST`
{: #ibm-cloud-admin-role-create-cast}

To [`CREATE CAST`](https://www.postgresql.org/docs/10/sql-createcast.html){: external} with the `ibm-cloud-admin` role, you need to create your databases with the default PostgreSQL `template1`. A cast specifies how to perform a conversion between two data types.

If you create your databases with `template0`, you still get the `ibm-cloud-admin` role as described in the previous section, but you don't get the `CREATE CAST` funtion. For more information about template databases, see [Template Databases](https://www.postgresql.org/docs/10/manage-ag-templatedbs.html){: external} in PostgreSQL documentation.
{: note}

#### `pg_monitor` and `pg_signal_backend`
{: #ibm-cloud-admin-role-other-privileges}

Users and roles with the `ibm-cloud-admin` role (whether directly or indirectly inherited) have the [`pg_monitor`](https://www.postgresql.org/docs/10/default-roles.html){: external} and [`pg_signal_backend`](https://www.postgresql.org/docs/10/default-roles.html){: external} roles. The `pg_monitor` role provides a set of permissions for monitoring the database server. The `pg_signal_backend` role provides the ability to send signals to cancel queries and connections initiated by other users except database superusers.

Member roles that have the `INHERIT` attribute not only have the privileges of roles of which they are members, but also (indirectly) have privileges that are inherited by those roles. For more information about inheriting roles, see [Role Membership](https://www.postgresql.org/docs/10/role-membership.html){:external}.
{: tip}

Users/roles with the `ibm-cloud-admin` role can grant these two roles to other users/roles in your service instance. For example:

- To set up a specific monitoring user `deb`, run the following command using users/roles with the `pg_monitor` role (for example, a member of `ibm-cloud-admin`).
  ```
  GRANT pg_monitor TO deb;
  ```
  {: codeblock}

- To expose the ability to cancel queries to a user `stan`, run the following command using users/roles with the `pg_signal_backend` role (for example, a member of `ibm-cloud-admin`).
  ```
  GRANT pg_signal_backend TO stan;
  ```
  {: codeblock}

  This privilege allows the user or users to end any connections to the database, so assign it with care.
  {: note}
