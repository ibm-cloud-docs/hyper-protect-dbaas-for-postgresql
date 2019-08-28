---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: backup, disaster recovery, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:tip: .tip}


# 使用 {{site.data.keyword.cos_full_notm}} 备份和复原数据库
{: #backup_postgresql_databases}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服务每 24 小时自动触发一次完整数据库备份。其中可用的是最近 7 天的加密备份，这些备份以冗余方式在受支持区域中所有可用性专区的本地存储器上提供。
{: shortdesc}

如果要提高灾难恢复能力，并备份受支持区域外部的数据，那么可以使用 [{{site.data.keyword.cos_full_notm}} 服务](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external}通过参考以下步骤将数据存储在其他区域。

## 开始之前
{: #backup_postgresql_before_begin}

要使用 {{site.data.keyword.postgresql}} 命令来完成备份，需要首先在计算机上下载并安装 {{site.data.keyword.postgresql}}。有关更多信息，请参阅 [{{site.data.keyword.postgresql}} Web 站点](https://www.postgresql.org/download/){: external}。

## 步骤 1：创建用于备份原始数据库的转储文件
{: #step1_create_dump_file_backup_postgresql}

使用以下 `pg_dump` 命令来创建包含要备份的数据库的转储文件。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表说明了命令中使用的变量。

|变量|描述|示例|
|---------|-----------|-------|
|*host_name*|用于托管原始数据库的远程服务器。您需要连接到主机来获取数据。可以在集群实例 UI 的概述页面上找到主机地址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用于与主机建立连接的端口号。可以在集群实例 UI 的概述页面上找到该端口。|25050|
|*user_name*|用于访问原始数据库的用户名。用户需要对数据库具有 CONNECT 特权，并对表具有 SELECT 特权。|my_user|
|*database_name*|要备份的数据库的名称。|my_database|
|*dump_file*|用于存储原始数据的 `.dump` 文件。可以使用相对路径或绝对路径来指定该文件。|./pgdump.dump|
{: caption="表 1. 创建转储文件所需的变量"}

如果要了解有关用户特权的更多信息，可以参阅 [{{site.data.keyword.postgresql}} 文档](https://www.postgresql.org/docs/10/sql-grant.html){: external}来获取更多信息。


## 步骤 2：创建新的 {{site.data.keyword.cos_full_notm}} 实例
{: #step2_create_object_storage_backup_postgresql}

您创建该实例所在的区域需要与当前托管 {{site.data.keyword.ihsdbaas_postgresql_full}} 服务实例的位置不同。可以参阅以下步骤：

1. [创建新的 Cloud {{site.data.keyword.cos_short}} 实例](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision)。
2. 在其他区域中[创建存储区](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region)。
3. [创建服务凭证](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials)，并保存 `access_key_id` 和 `secret_access_key` 以供稍后使用。
4. 安装 S3 客户机。
5. 使用 S3 客户机和访问密钥来连接到先前创建的存储区的 Cloud {{site.data.keyword.cos_short}} 端点。
6. 使用 S3 客户机[上传 {{site.data.keyword.postgresql}} 备份文件](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload)（即在[步骤 1](#step1_create_dump_file_backup_postgresql) 中创建的备份文件）至存储区。

有关更多信息，请参阅 [{{site.data.keyword.cos_full_notm}} 文档](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started)。

完成此步骤后，您已成功在不同区域的 Cloud {{site.data.keyword.cos_short}} 实例中备份数据。如果要将数据从 Cloud {{site.data.keyword.cos_short}} 实例复原到 {{site.data.keyword.ihsdbaas_postgresql_full}} 实例，请阅读下面的步骤 3 以获取详细信息。

## 步骤 3：将数据从 Cloud {{site.data.keyword.cos_short}} 实例复原到 {{site.data.keyword.ihsdbaas_postgresql_full}} 实例
{: #step3_restore_data_from_cos_postgresql}

您需要先将 Cloud {{site.data.keyword.cos_short}} 存储区中的备份文件下载到本地计算机，然后使用 `psql` 命令来复原数据。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表说明了命令中使用的变量。

|变量|描述|示例|
|---------|-----------|-------|
|*host_name*|托管目标集群的 DBaaS 管理器服务器。可以在集群实例 UI 的概述页面上找到主机地址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用于与主机建立连接的端口号。可以在集群实例 UI 的概述页面上找到该端口号。|25003|
|*user_name*|用于访问目标数据库的用户名。|new_user|
|*database_name*|数据库可以是该用户对其具有 CONNECT 特权的任何数据库。`psql` 会话会自动将其切换到要将数据复原到其中的目标数据库。|my_database|
|*dump_file*|从 Cloud {{site.data.keyword.cos_short}} 存储区下载的 `.dump` 文件。可以使用相对路径或绝对路径来指定该文件。|./pgdump.dump|
{: caption="表 2. 从转储文件复原数据所需的变量"}

## 后续步骤
{: #whats_next_backup_postgresql}

执行[步骤 3](#step3_restore_data_from_cos_postgresql) 之后，可以连接到数据库集群，以检查数据复原是否成功。
