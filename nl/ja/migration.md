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

# {{site.data.keyword.postgresql}} データベースの {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} へのマイグレーション
{: #migration_postgre}

{{site.data.keyword.postgresql}} データベースを使用していて、{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} にマイグレーションする場合には、このトピックで詳細を確認してください。 プラットフォームで {{site.data.keyword.postgresql}} データベース・サービスが提供されている限り、{{site.data.keyword.postgresql}} データベースがホストされている場所は問題にはなりません。
{: shortdesc}

## 始めに
{: #migration_postgre_before_begin}

{{site.data.keyword.postgresql}} コマンドを使用してマイグレーションを実行するには、まずマシンに {{site.data.keyword.postgresql}} をダウンロードしてインストールする必要があります。 詳しくは、[{{site.data.keyword.postgresql}} Web サイト](https://www.postgresql.org/download/){: external}を参照してください。

## 手順 1: 元のデータベースを復元するためのダンプ・ファイルを作成する
{: #step1_create_dump_file}

以下の `pg_dump` コマンドを使用して、復元するデータベースが含まれるダンプ・ファイルを作成します。

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

以下の表に、このコマンドで使用する変数の説明を記載します。

|変数|説明|例|
|---------|-----------|-------|
|*host_name*|元のデータベースをホストするリモート・サーバー。 データを取得するため、このホストに接続する必要があります。 データベースを {{site.data.keyword.ihsdbaas_full}} ベータ・インスタンスでデプロイした場合は、クラスター・インスタンス UI の概要ページでホスト・アドレスを確認できます。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|ホストへの接続を確立するためのポート番号。 データベースを {{site.data.keyword.ihsdbaas_full}} ベータ・インスタンスでデプロイした場合は、クラスター・インスタンス UI の概要ページでポートを確認できます。|25050|
|*user_name*|元のデータベースにアクセスするユーザー名。 データベースに対する CONNECT 特権およびテーブルに対する SELECT 特権を持つユーザーでなければなりません。|my_user|
|*database_name*|マイグレーションするデータベースの名前。|my_database|
|*dump_file*|元のデータが格納される `.dump` ファイル。 ファイルの指定には絶対パスと相対パスのどちらでも使用できます。|./pgdump.dump|
{: caption="表 1. ダンプ・ファイルを作成するときに必要な変数"}

ユーザー特権について詳しくは、[{{site.data.keyword.postgresql}} の資料](https://www.postgresql.org/docs/10/sql-grant.html){: external}を参照してください。

## 手順 2: {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} に新しいサービス・インスタンスを作成する
{: #step2_creat_new_service_instance}

データを復元する前に、ターゲット・データベース・クラスターである新しいサービス・インスタンスを {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} に作成する必要があります。 新しいサービス・インスタンスは以下のいずれかを使用して作成できます。
- [Web ユーザー・インターフェース](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [{{site.data.keyword.cloud_notm}} CLI の CLI プラグイン](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

新しいサービス・インスタンスを作成するときには、クラスター名、管理者名、パスワードを設定する必要があります。 元のインスタンスと同じにする必要はありません。 マイグレーションには影響ありません。 マイグレーションの完了後に、データベースは新しい管理者に割り当てられます。

## 手順 3: 新しいサービス・インスタンスにデータベースを作成する
{: #step3_create_database}

新しいサービス・インスタンスを作成した後、新しいデータベースを作成する必要があります。 データベースには元のデータベースと同じ名前を付ける必要があります。 CREATE 特権を持つユーザーでなければなりません。ダンプ・ファイルを作成したユーザーと同じにする必要はありません。 このタスクを実行するには、以下のいずれかの方法を使用できます。
- [Web ユーザー・インターフェース](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [{{site.data.keyword.cloud_notm}} CLI の CLI プラグイン](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

新規ユーザーを作成するには、以下のいずれかの方法を使用できます: [Web ユーザー・インターフェース](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user)、[DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}、[{{site.data.keyword.cloud_notm}} CLI の CLIプラグイン](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create)、および [{{site.data.keyword.postgresql}} コマンド](https://www.postgresql.org/docs/10/sql-createuser.html){: external}。
{: tip}

## 手順 4: ダンプ・ファイルのデータを新しいサービス・インスタンスに復元する
{: #step4_restore_data}

`psql` コマンドを使用して、[手順 1](#step1_create_dump_file) で作成したダンプ・ファイルのデータを復元します。

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

以下の表に、このコマンドで使用する変数の説明を記載します。

|変数|説明|例|
|---------|-----------|-------|
|*host_name*|ターゲットのクラスターをホストしている DBaaS Manager サーバー。 クラスター・インスタンス UI の概要ページでホスト・アドレスを確認できます。|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|ホストへの接続を確立するためのポート番号。 クラスター・インスタンス UI の概要ページでポート番号アドレスを確認できます。|25003|
|*user_name*|ターゲット・データベースにアクセスするユーザー名。 [手順 3](#step3_create_database) でターゲット・データベースを作成したユーザーと同じユーザーを使用できます。|new_user|
|*database_name*|データベースは、ユーザーが CONNECT 特権を持つ任意のデータベースにすることができます。 `psql` セッションによって、[手順 3](#step3_create_database) で作成したターゲット・データベースに自動的に切り替わります。|my_database|
|*dump_file*|[手順 1](#step1_create_dump_file) で作成した `.dump` ファイル。 ファイルの指定には絶対パスと相対パスのどちらでも使用できます。|./pgdump.dump|
{: caption="表 2. ダンプ・ファイルのデータを復元するときに必要な変数"}

## 次の作業
{: #whats_next_migration_postgre}

マイグレーションしたら、新しいデータベース・クラスターに接続して、データが正常にマイグレーションされたかどうかを確認できます。
