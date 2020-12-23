---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-23"

keywords: PL/Java extension

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

# Using PL/Java extension
{: #use_pljava_extension}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} supports PL/Java [1.5.2](https://github.com/tada/pljava/releases){: external} (besides plpgsql 1.0). [PL/Java](https://tada.github.io/pljava/){: external} is a free open source extension for {{site.data.keyword.postgresql}} that allows stored procedures, triggers, and functions to be written in the Java language and executed in the backend.
{: shortdesc}

The PL/Java extension is enabled by default when you create a database. To use the extension, complete the following instructions.

## Prerequisites
{: #pljava_extension_prereq}

1. You need IBM Java SDK 8.0.5.37 or above to build your PL/Java code, as PL/Java uses IBM JRE 8.0.5.37.
2. Create your customized schema and add the schema to `search_path`. Your PL/Java code package will be installed in the schema. For more information about schema and search path, see [Schemas](https://www.postgresql.org/docs/10/ddl-schemas.html){: external}.

## Steps
{: #pljava_steps}

The following example shows [how to load and use the `hello` function](https://tada.github.io/pljava/use/hello.html){: external}.

1. Use the `CREATE SCHEMA` statement to create a schema for installing your PL/Java code.
  ```
  create schema <schema_name>;
  ```
  {: codeblock}
  This example names the schema `javatest`.
  ```
  create schema javatest;
  ```
  {: codeblock}

  Returns:
  ```
  CREATE SCHEMA
  ```

2. Add the `javatest` schema to `search_path` and make it the first schema in the search path with the following command. Your PL/Java code will be installed in this first schema.
  ```
  set search_path to javatest,public;
  ```
  {: codeblock}
  Returns:
  ```
  SET
  ```

3. To install the `hello` function, put the package in an external `https` server and then download it with the following command:
    ```
    select sqlj.install_jar(<https://hostname:port/path/proj-0.0.1-SNAPSHOT.jar>,'hellojar','true');
    ```
    {: codeblock}

    Returns:
    ```
    install_jar
    ------------
    (1 row)
    ```

4. List functions with the `\df` command.
  Returns:
  ```
                          List of functions
  Schema    | Name  | Result data type  |   Argument data types    |  Type  
  ----------+-------+-------------------+--------------------------+--------
  javatest  | hello | character varying | towhom character varying | normal
  (1 row)
  ```

5. To use the `hello` function in a new session without setting the search path again, save your search path with the following command:
  ```
  ALTER DATABASE <dbname> SET search_path TO javatest,public;
  ```
  {: codeblock}

  Returns:
  ```
  ALTER DATABASE
  ```

6. Define a classpath for the `javatest` schema to make sure that the Java virtual machine gets the path of `.class` files.
  ```
  select sqlj.set_classpath('javatest', 'hellojar');
  ```
  {: codeblock}

  Returns:
  ```
    set_classpath
  ---------------

  (1 row)
  ```

7. Run the `hello` function:
  ```
  select hello('world');
  ```
  {: codeblock}

  Returns:
  ```
      hello
  ---------------
    Hello, world!
  (1 row)
  ```

Now you have successfully loaded and executed the `hello` function by using PL/Java.
