---

copyright:
  years: 2020
lastupdated: "2020-10-14"

keywords: ltree module, postgresql extension

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

# Using ltree module
{: #use-ltree-module}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} supports the ltree module. This module implements a data type `ltree` for representing labels of data stored in a hierarchical tree-like structure. You can search for data through label trees in databases.
{: shortdesc}

The following example hierarchy shows the ltree data type in a database table.

```
                      Top
                  /    |     \
           Science  Hobbies Collections
               /        |             \
        Astronomy Amateurs_Astronomy Pictures
          /    \                        |
Astrophysics  Cosmology              Astronomy
                                    /   |   \
                             Galaxies Stars Astronauts
```

For more information about data types, operators, functions, and indexes of the ltree module, see the [ltree topic](https://www.postgresql.org/docs/10/ltree.html){: external} in PostgreSQL documentation.

## Enabling ltree
{: #enable-ltree}
Use the `CREATE EXTENSION ltree;` command to enable the ltree extension. For more information about installing PostgreSQL extensions, see [Installing extensions](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-extensions#install-extensions).

## Creating a table with path ltree
{: #ltree-create-table}

The following example creates a table named `test` in a database with path ltree.

```
CREATE TABLE test (path ltree);
```
{: codeblock}

You can then populate data in the `test` table. For example, run the following commands to add the same data as in the example hierarchy above.

```
INSERT INTO test VALUES ('Top');
INSERT INTO test VALUES ('Top.Science');
INSERT INTO test VALUES ('Top.Science.Astronomy');
INSERT INTO test VALUES ('Top.Science.Astronomy.Astrophysics');
INSERT INTO test VALUES ('Top.Science.Astronomy.Cosmology');
INSERT INTO test VALUES ('Top.Hobbies');
INSERT INTO test VALUES ('Top.Hobbies.Amateurs_Astronomy');
INSERT INTO test VALUES ('Top.Collections');
INSERT INTO test VALUES ('Top.Collections.Pictures');
INSERT INTO test VALUES ('Top.Collections.Pictures.Astronomy');
INSERT INTO test VALUES ('Top.Collections.Pictures.Astronomy.Stars');
INSERT INTO test VALUES ('Top.Collections.Pictures.Astronomy.Galaxies');
INSERT INTO test VALUES ('Top.Collections.Pictures.Astronomy.Astronauts');
```
{: codeblock}

## Searching for data in the path ltree table
{: #ltree-search-table}

The ltree module supports different operators, functions, and indexes to simplify the data matching and operations in a database table.

For example, run the following command to match path whose left argument equals or is a descendant of 'Top.Science'.

```
SELECT path FROM test WHERE path <@ 'Top.Science';
```
{: codeblock}

You can get the search results that are similar to the following example:

```
                path
------------------------------------
 Top.Science
 Top.Science.Astronomy
 Top.Science.Astronomy.Astrophysics
 Top.Science.Astronomy.Cosmology
(4 rows)
```
