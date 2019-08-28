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


# 使用 {{site.data.keyword.cos_full_notm}} 備份和還原資料庫
{: #backup_postgresql_databases}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服務每 24 小時會自動觸發一次完整資料庫的備份。其中可用的是最近 7 天的加密備份，這些備份以冗餘方式在受支援地區中所有可用性區域的本端儲存空間提供。
{: shortdesc}

如果要提高災難回復功能，並將資料備份到受支援地區外，可以使用 [{{site.data.keyword.cos_full_notm}} 服務](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external}，參考下列步驟將資料儲存在其他地區。

## 開始之前
{: #backup_postgresql_before_begin}

若要使用 {{site.data.keyword.postgresql}} 指令來完成備份，您需要先在機器上下載並安裝 {{site.data.keyword.postgresql}}。如需相關資訊，請參閱 [{{site.data.keyword.postgresql}} 網站](https://www.postgresql.org/download/){: external}。

## 步驟 1：建立用於備份原始資料庫的傾出檔案
{: #step1_create_dump_file_backup_postgresql}

請使用下列 `pg_dump` 指令來建立傾出檔案，其中包含您要備份的資料庫。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表說明指令中使用的變數。

|變數|說明|範例|
|---------|-----------|-------|
|*host_name*|用於管理原始資料庫的遠端伺服器。您需要連接至主機來取得資料。可以在叢集實例使用者介面的概觀頁面上找到主機位址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用來建立對主機之連線的埠號。可以在叢集實例使用者介面的概觀頁面上找到該埠。|25050|
|*user_name*|用於存取原始資料庫的使用者名稱。使用者需要對資料庫具有 CONNECT 專用權，並對表格具有 SELECT 專用權。|my_user|
|*database_name*|要備份的資料庫的名稱。|my_database|
|*dump_file*|用於儲存原始資料的 `.dump` 檔案。您可以使用相對或絕對路徑來指定檔案。|./pgdump.dump|
{: caption="表 1. 建立傾出檔案所需的變數"}

如果您想要進一步瞭解使用者專用權，可以參閱 [{{site.data.keyword.postgresql}} 文件](https://www.postgresql.org/docs/10/sql-grant.html){: external}來取得相關資訊。

## 步驟 2：建立新的 {{site.data.keyword.cos_full_notm}} 實例
{: #step2_create_object_storage_backup_postgresql}

您建立該實例所在的地區需要與現行管理 {{site.data.keyword.ihsdbaas_postgresql_full}} 服務實例的位置不同。可以參閱下列步驟：

1. [建立新的 Cloud {{site.data.keyword.cos_short}} 實例](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision)。
2. 在其他地區中[建立儲存區](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region)。
3. [建立服務認證](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials)，並儲存 `access_key_id` 和 `secret_access_key` 以供稍後使用。
4. 安裝 S3 用戶端。
5. 使用 S3 用戶端和存取金鑰來連接至先前建立之儲存區的 Cloud {{site.data.keyword.cos_short}} 端點。
6. 使用 S3 用戶端[上傳 {{site.data.keyword.postgresql}} 備份檔](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload)（即在[步驟 1](#step1_create_dump_file_backup_postgresql) 中建立的備份檔）至儲存區。

如需相關資訊，請參閱 [{{site.data.keyword.cos_full_notm}} 文件](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started)。

完成此步驟後，您已順利在不同地區的 Cloud {{site.data.keyword.cos_short}} 實例中備份資料。如果要將資料從 Cloud {{site.data.keyword.cos_short}} 實例還原到 {{site.data.keyword.ihsdbaas_postgresql_full}} 實例，請閱讀下面的步驟 3 以取得詳細資料。

## 步驟 3：將資料從 Cloud {{site.data.keyword.cos_short}} 實例還原到 {{site.data.keyword.ihsdbaas_postgresql_full}} 實例
{: #step3_restore_data_from_cos_postgresql}

您需要先將 Cloud {{site.data.keyword.cos_short}} 儲存區中的備份檔下載到本端機器，然後使用 `psql` 指令來還原資料。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

下表說明指令中使用的變數。

|變數|說明|範例|
|---------|-----------|-------|
|*host_name*|管理目標叢集的 DBaaS 管理程式伺服器。可以在叢集實例使用者介面的概觀頁面上找到主機位址。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|用來建立對主機之連線的埠號。可以在叢集實例使用者介面的概觀頁面上找到該埠號。|25003|
|*user_name*|用於存取目標資料庫的使用者名稱。|new_user|
|*database_name*|資料庫可以是該使用者對其具有 CONNECT 專用權的任何資料庫。`psql` 階段作業會自動將其切換到要將資料還原到其中的目標資料庫。|my_database|
|*dump_file*|從 Cloud {{site.data.keyword.cos_short}} 儲存區下載的 `.dump` 檔案。您可以使用相對或絕對路徑來指定檔案。|./pgdump.dump|
{: caption="表 2. 從傾出檔案還原資料所需的變數"}

## 下一步為何？
{: #whats_next_backup_postgresql}

執行[步驟 3](#step3_restore_data_from_cos_postgresql) 之後，可以連接至資料庫叢集，以檢查資料還原是否順利。
