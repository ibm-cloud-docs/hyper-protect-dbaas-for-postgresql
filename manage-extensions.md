---

copyright:
  years: 2020, 2021
lastupdated: "2021-05-31"

keywords: postgresql extensions

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
{:terraform: .ph data-hd-interface='terraform'}
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


# Managing PostgreSQL extensions
{: #manage-extensions}

In PostgreSQL, extensions are modules that supply extra functions, operators, or types. Many extensions are available in {{site.data.keyword.ihsdbaas_postgresql_full}}. In order to use them, [connect with `psql`](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#accessing-database-introduction-connect-psqlshell) first.

## Listing installed extensions
{: #list-extensions}

Get a list of all the extensions installed on the database by using the `\dx` command.

For example, the output for `\dx` when run on the {{site.data.keyword.ihsdbaas_postgresql_full}} default database shows the only installed extensions.

```
admin=> \dx;
```
```
                     List of installed extensions
  Name   | Version |   Schema   |         Description
---------+---------+------------+-------------------------------------------------------------
 pljava  | 1.5.2   | sqlj       | PL/Java procedural language (https://tada.github.io/pljava/)
 plpgsql | 1.0     | pg_catalog | PL/pgSQL procedural language
(2 rows)
```
{: screen}

## Installing extensions
{: #install-extensions}

To install an extension on to the database, use [`CREATE EXTENSION`](https://www.postgresql.org/docs/10/sql-createextension.html){: external}. For example, to install `isn` on the database, use the following command.

```
admin=> CREATE EXTENSION isn;
CREATE EXTENSION
```

If you run the `\dx` command after you install an extension, it appears in the table.
```
admin=> \dx;
```
```
                                 List of installed extensions
  Name   | Version |   Schema   |                         Description                          
---------+---------+------------+--------------------------------------------------------------
 isn     | 1.1     | public     | data types for international product numbering standards
 pljava  | 1.5.2   | sqlj       | PL/Java procedural language (https://tada.github.io/pljava/)
 plpgsql | 1.0     | pg_catalog | PL/pgSQL procedural language
(3 rows)
```
{: screen}

## Removing extensions
{: #remove-extensions}

To remove extensions from the database, use the [`DROP EXTENSION`](https://www.postgresql.org/docs/10/sql-dropextension.html){: external} command. For example, to remove `isn`, use `DROP EXTENSION isn;`.

## Available extensions
{: #available-extensions}

Currently, not all default extensions in `available_table` are supported. For a list of available extensions on your service instance, use the `show extwlist.extensions;` command in `psql`.
```
admin=> show extwlist.extensions;
```
```
                                                                                   extwlist.extensions
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 autoinc,bloom,btree_gin,btree_gist,chkpass,citext,cube,earthdistance,fuzzystrmatch,hstore,insert_username,intagg,intarray,isn,lo,ltree,moddatetime,pg_trgm,pgcrypto,pgrowlocks,refint,seg,sslinfo,tablefunc,tcn,timetravel,tsm_system_rows,tsm_system_time,uuid-ossp,xml2
 
```
{: screen}

See [Additional Supplied Modules](https://www.postgresql.org/docs/10/contrib.html){: external} for how to use the extensions.

The function of some extensions is limited compared to the x86 version because the privilege setting in {{site.data.keyword.ihsdbaas_postgresql_full}} is different.
{: note}
