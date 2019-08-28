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

# 將 {{site.data.keyword.postgresql}} 資料庫移轉到 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

如果使用的是 {{site.data.keyword.postgresql}} 資料庫，並且要將其移轉到 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}，請閱讀本主題以取得詳細資料。不管在何處管理 {{site.data.keyword.postgresql}} 資料庫，只要平台提供 {{site.data.keyword.postgresql}} 資料庫服務即可。
{: shortdesc}

## 開始之前
{: #migration_postgre_before_begin}

若要使用 {{site.data.keyword.postgresql}} 指令來完成移轉，您需要先在機器上下載並安裝 {{site.data.keyword.postgresql}}。如需相關資訊，請參閱 [{{site.data.keyword.postgresql}} 網站](https://www.postgresql.org/download/){: external}。

## 步驟 1：建立用於還原原始資料庫的傾出檔案
{: #step1_create_dump_file}

請使用下列 `pg_dump` 指令來建立傾出檔案，其中包含您要還原的資料庫。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表說明指令中使用的變數。

|變數|說明|範例|
|---------|-----------|-------|
|*host_name*|用於管理原始資料庫的遠端伺服器。您需要連接至主機來取得資料。如果資料庫部署在 {{site.data.keyword.ihsdbaas_full}} 測試版實例中，可以在叢集實例使用者介面的概觀頁面上找到主機位址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用來建立對主機之連線的埠號。如果資料庫部署在 {{site.data.keyword.ihsdbaas_full}} 測試版實例中，可以在叢集實例使用者介面的概觀頁面上找到該埠。|25050|
|*user_name*|用於存取原始資料庫的使用者名稱。使用者需要對資料庫具有 CONNECT 專用權，並對表格具有 SELECT 專用權。|my_user|
|*database_name*|要移轉的資料庫名稱。|my_database|
|*dump_file*|用於儲存原始資料的 `.dump` 檔案。您可以使用相對或絕對路徑來指定檔案。|./pgdump.dump|
{: caption="表 1. 建立傾出檔案所需的變數"}

如果您想要進一步瞭解使用者專用權，可以參閱 [{{site.data.keyword.postgresql}} 文件](https://www.postgresql.org/docs/10/sql-grant.html){: external}來取得相關資訊。

## 步驟 2：在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 中建立新的服務實例
{: #step2_creat_new_service_instance}

在還原資料之前，需要在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 中建立新的服務實例，以作為目標資料庫叢集。可以使用下列其中一種方式來建立新的服務實例：
- [Web 使用者介面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [{{site.data.keyword.cloud_notm}} CLI 的 CLI 外掛程式](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

建立新服務實例時，需要設定叢集名稱、管理者名稱和密碼。這些資訊不必與原始實例中的相同。這不會影響移轉。移轉完成後，會將資料庫指派給新的管理者。

## 步驟 3：在新的服務實例中建立資料庫
{: #step3_create_database}

建立新服務實例後，需要建立新資料庫。這些資料庫必須與原始資料庫同名。該使用者需要具有 CREATE 專用權，但不必是建立傾出檔案的同一個使用者。可以使用下列其中一種方式來執行此作業：
- [Web 使用者介面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [{{site.data.keyword.cloud_notm}} CLI 的 CLI 外掛程式](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

可以使用下列其中一種方式來建立新使用者：[Web 使用者介面](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user)、[DBaaS 管理程式 API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}、[{{site.data.keyword.cloud_notm}} CLI 的 CLI 外掛程式](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create)及 [{{site.data.keyword.postgresql}} 指令](https://www.postgresql.org/docs/10/sql-createuser.html){: external}。
{: tip}

## 步驟 4：將資料從傾出檔案還原到新服務實例
{: #step4_restore_data}

使用 `psql` 指令可從[步驟 1](#step1_create_dump_file) 中建立的傾出檔案還原資料。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表說明指令中使用的變數。

|變數|說明|範例|
|---------|-----------|-------|
|*host_name*|管理目標叢集的 DBaaS 管理程式伺服器。可以在叢集實例使用者介面的概觀頁面上找到主機位址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用來建立對主機之連線的埠號。可以在叢集實例使用者介面的概觀頁面上找到該埠號。|25003|
|*user_name*|用於存取目標資料庫的使用者名稱。可以使用在[步驟 3](#step3_create_database) 中建立目標資料庫的同一使用者。|new_user|
|*database_name*|資料庫可以是該使用者對其具有 CONNECT 專用權的任何資料庫。`psql` 階段作業會自動將其切換到在[步驟 3](#step3_create_database) 中建立的目標資料庫。|my_database|
|*dump_file*|在[步驟 1](#step1_create_dump_file) 中建立的 `.dump` 檔案。您可以使用相對或絕對路徑來指定檔案。|./pgdump.dump|
{: caption="表 2. 從傾出檔案還原資料所需的變數"}

## 下一步為何？
{: #whats_next_migration_postgre}

移轉之後，可以連接至新的資料庫叢集，以檢查資料移轉是否順利。
