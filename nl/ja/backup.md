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


# {{site.data.keyword.cos_full_notm}} を使用したデータベースのバックアップとリストア
{: #backup_postgresql_databases}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} サービスは、24 時間ごとに 1 回、データベース全体のバックアップを自動的にトリガーします。 これらの暗号化されたバックアップの直近 7 日分が、サポート対象地域のすべてのアベイラビリティー・ゾーンのローカル・ストレージ上に冗長的に保持されます。
{: shortdesc}

災害復旧能力を向上させるためにサポート対象外の地域にデータをバックアップするには、以下の手順を参照することで、[{{site.data.keyword.cos_full_notm}} サービス](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external}を使用して別の地域にデータを保管できます。

## 始めに
{: #backup_postgresql_before_begin}

{{site.data.keyword.postgresql}} コマンドを使用してバックアップを実行するには、まずマシンに {{site.data.keyword.postgresql}} をダウンロードしてインストールする必要があります。 詳しくは、[{{site.data.keyword.postgresql}} Web サイト](https://www.postgresql.org/download/){: external}を参照してください。

## 手順 1: 元のデータベースをバックアップするためのダンプ・ファイルを作成する
{: #step1_create_dump_file_backup_postgresql}

以下の `pg_dump` コマンドを使用して、バックアップするデータベースが含まれるダンプ・ファイルを作成します。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

以下の表に、このコマンドで使用する変数の説明を記載します。

|変数|説明|例|
|---------|-----------|-------|
|*host_name*|元のデータベースをホストするリモート・サーバー。 データを取得するため、このホストに接続する必要があります。 クラスター・インスタンス UI の概要ページでホスト・アドレスを確認できます。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|ホストへの接続を確立するためのポート番号。 クラスター・インスタンス UI の概要ページでポートを確認できます。|25050|
|*user_name*|元のデータベースにアクセスするユーザー名。 データベースに対する CONNECT 特権およびテーブルに対する SELECT 特権を持つユーザーでなければなりません。|my_user|
|*database_name*|バックアップするデータベースの名前。|my_database|
|*dump_file*|元のデータが格納される `.dump` ファイル。 ファイルの指定には絶対パスと相対パスのどちらでも使用できます。|./pgdump.dump|
{: caption="表 1. ダンプ・ファイルを作成するときに必要な変数"}

ユーザー特権について詳しくは、[{{site.data.keyword.postgresql}} の資料](https://www.postgresql.org/docs/10/sql-grant.html){: external}を参照してください。

## 手順 2: 新規 {{site.data.keyword.cos_full_notm}} インスタンスを作成する
{: #step2_create_object_storage_backup_postgresql}

インスタンスは、現在 {{site.data.keyword.ihsdbaas_postgresql_full}} サービス・インスタンスがホストされている地域とは別の地域に作成する必要があります。 以下の手順を参照してください。

1. [新規 Cloud {{site.data.keyword.cos_short}} インスタンスを作成します](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision)。
2. 他の地域に[バケットを作成](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region)します。
3. [サービス資格情報を作成](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials)し、後で使用するために `access_key_id` と `secret_access_key` を保存します。
4. S3 クライアントをインストールします。
5. S3 クライアントとアクセス・キーを使用して、前の手順で作成したバケットの Cloud {{site.data.keyword.cos_short}} エンドポイントに接続します。
6. S3 クライアントを使用して、バケットに[手順 1](#step1_create_dump_file_backup_postgresql) で作成した [{{site.data.keyword.postgresql}} バックアップ・ファイルをアップロード](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload)します。

詳しくは、[{{site.data.keyword.cos_full_notm}} の資料](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started) を参照してください。

この手順を完了すると、別の地域の Cloud {{site.data.keyword.cos_short}} インスタンスにデータが正常にバックアップされます。 Cloud {{site.data.keyword.cos_short}} インスタンスから {{site.data.keyword.ihsdbaas_postgresql_full}} インスタンスにデータを復元する場合、詳しくは以下の手順 3 を参照してください。

## 手順 3: Cloud {{site.data.keyword.cos_short}} インスタンスから {{site.data.keyword.ihsdbaas_postgresql_full}} インスタンスにデータを復元する
{: #step3_restore_data_from_cos_postgresql}

まずバックアップ・ファイルを Cloud {{site.data.keyword.cos_short}} バケットからローカル・マシンにダウンロードしてから、`psql` コマンドを使用してデータを復元する必要があります。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

以下の表に、このコマンドで使用する変数の説明を記載します。

|変数|説明|例|
|---------|-----------|-------|
|*host_name*|ターゲットのクラスターをホストしている DBaaS Manager サーバー。 クラスター・インスタンス UI の概要ページでホスト・アドレスを確認できます。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|ホストへの接続を確立するためのポート番号。 クラスター・インスタンス UI の概要ページでポート番号アドレスを確認できます。|25003|
|*user_name*|ターゲット・データベースにアクセスするユーザー名。|new_user|
|*database_name*|データベースは、ユーザーが CONNECT 特権を持つ任意のデータベースにすることができます。 `psql` セッションによって、データの復元先のターゲット・データベースに自動的に切り替わります。|my_database|
|*dump_file*|Cloud {{site.data.keyword.cos_short}} バケットからダウンロードした `.dump` ファイル。 ファイルの指定には絶対パスと相対パスのどちらでも使用できます。|./pgdump.dump|
{: caption="表 2. ダンプ・ファイルのデータを復元するときに必要な変数"}

## 次の作業
{: #whats_next_backup_postgresql}

[手順 3](#step3_restore_data_from_cos_postgresql) の後、データベース・クラスターに接続してデータが正常に復元されたかどうか確認できます。
