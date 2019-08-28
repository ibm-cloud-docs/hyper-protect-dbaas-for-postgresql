---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: migrate, beta, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 将 {{site.data.keyword.postgresql}} 数据库迁移到 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

如果使用的是 {{site.data.keyword.postgresql}} 数据库，并且要将其迁移到 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}，请阅读本主题以获取详细信息。不管在何处托管 {{site.data.keyword.postgresql}} 数据库，只要平台提供 {{site.data.keyword.postgresql}} 数据库服务即可。
{: shortdesc}

## 开始之前
{: #migration_postgre_before_begin}

要使用 {{site.data.keyword.postgresql}} 命令来完成迁移，需要首先在计算机上下载并安装 {{site.data.keyword.postgresql}}。有关更多信息，请参阅 [{{site.data.keyword.postgresql}} Web 站点](https://www.postgresql.org/download/){: external}。

## 步骤 1：创建用于复原原始数据库的转储文件
{: #step1_create_dump_file}

使用以下 `pg_dump` 命令来创建包含要复原的数据库的转储文件。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表说明了命令中使用的变量。

|变量|描述|示例|
|---------|-----------|-------|
|*host_name*|用于托管原始数据库的远程服务器。您需要连接到主机来获取数据。如果数据库部署在 {{site.data.keyword.ihsdbaas_full}} Beta 实例中，那么可以在集群实例 UI 的概述页面上找到主机地址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用于与主机建立连接的端口号。如果数据库部署在 {{site.data.keyword.ihsdbaas_full}} Beta 实例中，那么可以在集群实例 UI 的概述页面上找到该端口。|25050|
|*user_name*|用于访问原始数据库的用户名。用户需要对数据库具有 CONNECT 特权，并对表具有 SELECT 特权。|my_user|
|*database_name*|要迁移的数据库的名称。|my_database|
|*dump_file*|用于存储原始数据的 `.dump` 文件。可以使用相对路径或绝对路径来指定该文件。|./pgdump.dump|
{: caption="表 1. 创建转储文件所需的变量"}

如果要了解有关用户特权的更多信息，可以参阅 [{{site.data.keyword.postgresql}} 文档](https://www.postgresql.org/docs/10/sql-grant.html){: external}来获取更多信息。


## 步骤 2：在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 中创建新的服务实例
{: #step2_creat_new_service_instance}

在复原数据之前，需要在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 中创建新的服务实例，以作为目标数据库集群。可以使用下列其中一种方式来创建新的服务实例：
- [Web 用户界面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [DBaaS 管理器 API](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [{{site.data.keyword.cloud_notm}} CLI 的 CLI 插件](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

创建新服务实例时，需要设置集群名称、管理员名称和密码。这些信息不必与原始实例中的相同。这不会影响迁移。迁移完成后，会将数据库分配给新的管理员。

## 步骤 3：在新的服务实例中创建数据库
{: #step3_create_database}

创建新服务实例后，需要创建新数据库。这些数据库必须与原始数据库同名。该用户需要具有 CREATE 特权，但不必是创建转储文件的同一个用户。可以使用下列其中一种方式来执行此任务：
- [Web 用户界面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [DBaaS 管理器 API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [{{site.data.keyword.cloud_notm}} CLI 的 CLI 插件](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

可以使用下列方式来创建新用户：[Web 用户界面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user)、[DBaaS 管理器 API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}、[{{site.data.keyword.cloud_notm}} CLI 的 CLI 插件](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create)以及 [{{site.data.keyword.postgresql}} 命令](https://www.postgresql.org/docs/10/sql-createuser.html){: external}。
{: tip}

## 步骤 4：将数据从转储文件复原到新服务实例
{: #step4_restore_data}

使用 `psql` 命令可从[步骤 1](#step1_create_dump_file) 中创建的转储文件复原数据。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表说明了命令中使用的变量。

|变量|描述|示例|
|---------|-----------|-------|
|*host_name*|托管目标集群的 DBaaS 管理器服务器。可以在集群实例 UI 的概述页面上找到主机地址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用于与主机建立连接的端口号。可以在集群实例 UI 的概述页面上找到该端口号。|25003|
|*user_name*|用于访问目标数据库的用户名。可以使用在[步骤 3](#step3_create_database) 中创建目标数据库的同一用户。|new_user|
|*database_name*|数据库可以是该用户对其具有 CONNECT 特权的任何数据库。`psql` 会话会自动将其切换到在[步骤 3](#step3_create_database) 中创建的目标数据库。|my_database|
|*dump_file*|在[步骤 1](#step1_create_dump_file) 中创建的 `.dump` 文件。可以使用相对路径或绝对路径来指定该文件。|./pgdump.dump|
{: caption="表 2. 从转储文件复原数据所需的变量"}

## 后续步骤
{: #whats_next_migration_postgre}

迁移之后，可以连接到新的数据库集群，以检查数据迁移是否成功。
