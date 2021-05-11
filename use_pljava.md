---

copyright:
  years: 2019, 2021
lastupdated: "2021-05-11"

keywords: PL/Java extension

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


# Using PL/Java extension
{: #use_pljava_extension}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} supports PL/Java [1.6.2](https://github.com/tada/pljava/releases){: external} (besides plpgsql 1.0). [PL/Java](https://tada.github.io/pljava/){: external} is a free open source extension for {{site.data.keyword.postgresql}} that allows stored procedures, triggers, and functions to be written in the Java language and executed in the backend.
{: shortdesc}

The PL/Java extension is enabled by default when you create a database with `template1`. To use the extension, complete the following instructions.

## Prerequisites
{: #pljava_extension_prereq}

1. You need [AdoptOpenJDK 11](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/){:external} or above to build your PL/Java code, as PL/Java in {{site.data.keyword.ihsdbaas_postgresql_full}} uses AdoptOpenJDK 11.
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

3. To install the `hello` function, put the package in an external `https` server and then download it with the following command.

  For security reasons, only ports 80 and 443 are allowed to connect from PL/Java.
  {: important}

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

5. To use the `hello` function in a new session without setting the search path again, save your search path with the following command.
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
