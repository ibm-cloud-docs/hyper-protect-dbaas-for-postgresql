---

copyright:
  years: 2020
lastupdated: "2020-12-22"

keywords: postgresql extensions

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

# Managing PostgreSQL extensions
{: #manage-extensions}

In PostgreSQL, extensions are modules that supply extra functions, operators, or types. Many extensions are available in {{site.data.keyword.ihsdbaas_postgresql_full}}. In order to use them, [connect with `psql`](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#accessing-database-introduction-connect-psqlshell) first.

## Listing installed extensions
{: #list-extensions}

Get a list of all the extensions installed on the database by using the `\dx` command.

For example, the output for `\dx` when run on the {{site.data.keyword.ihsdbaas_postgresql_full}} default database shows the only installed extensions.

```
admin=> \dx;
                 List of installed extensions
  Name   | Version |   Schema   |         Description
---------+---------+------------+------------------------------
 pljava  | 1.5.2   | sqlj       | PL/Java procedural language (https://tada.github.io/pljava/)
 plpgsql | 1.0     | pg_catalog | PL/pgSQL procedural language
(2 rows)
```

## Installing extensions
{: #install-extensions}

To install an extension on to the database, use [`CREATE EXTENSION`](https://www.postgresql.org/docs/10/sql-createextension.html){: external}. For example, to install `isn` on the database, use the following command.

```
admin=> CREATE EXTENSION isn;
CREATE EXTENSION
```

If you run the `\dx` command after you install an extension, it appears in the table.
```
ibmclouddb=> \dx
                                     List of installed extensions
        Name        | Version |   Schema   |                        Description
--------------------+---------+------------+-----------------------------------------------------------
 isn     | 1.1     | public     | data types for international product numbering standards
 pljava  | 1.5.2   | sqlj       | PL/Java procedural language (https://tada.github.io/pljava/)
 plpgsql | 1.0     | pg_catalog | PL/pgSQL procedural language
(3 rows)
```

## Removing extensions
{: #remove-extensions}

To remove extensions from the database, use the [`DROP EXTENSION`](https://www.postgresql.org/docs/10/sql-dropextension.html){: external} command. For example, to remove `isn`, use `DROP EXTENSION isn;`.

## Available extensions
{: #available-extensions}

Currently, not all default extensions in `available_table` are supported. For a list of available extensions on your service instance, use the `show extwlist.extensions;` command in `psql`.
```
admin=> show extwlist.extensions;
                                                                                                                            extwlist.extensions                                                                                                                            
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 autoinc,bloom,btree_gin,btree_gist,chkpass,citext,cube,earthdistance,fuzzystrmatch,hstore,insert_username,intagg,intarray,isn,lo,ltree,moddatetime,pg_trgm,pgcrypto,pgrowlocks,refint,seg,sslinfo,tablefunc,tcn,timetravel,tsm_system_rows,tsm_system_time,uuid-ossp,xml2
 ```

See [Additional Supplied Modules](https://www.postgresql.org/docs/10/contrib.html){: external} for how to use the extensions.

The function of some extensions is limited compared to the x86 version because the privilege setting in {{site.data.keyword.ihsdbaas_postgresql_full}} is different.
{: note}
