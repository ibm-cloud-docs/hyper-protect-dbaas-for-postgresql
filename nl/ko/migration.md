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

# {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}로 {{site.data.keyword.postgresql}} 데이터베이스 마이그레이션
{: #migration_postgre}

{{site.data.keyword.postgresql}} 데이터베이스를 사용 중이며 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}로 마이그레이션하려면 이 주제의 세부사항을 참조하십시오. 플랫폼에서 {{site.data.keyword.postgresql}} 데이터베이스 서비스를 제공하는 한 {{site.data.keyword.postgresql}} 데이터베이스의 호스팅 위치는 중요하지 않습니다.
{: shortdesc}

## 시작하기 전에
{: #migration_postgre_before_begin}

{{site.data.keyword.postgresql}} 명령을 사용하여 마이그레이션을 완료하려면 우선 시스템에 {{site.data.keyword.postgresql}}을 다운로드하여 설치해야 합니다. 자세한 정보는 [{{site.data.keyword.postgresql}} 웹 사이트](https://www.postgresql.org/download/){: external}를 참조하십시오.

## 1단계: 원래 데이터베이스의 복원을 위한 덤프 파일 작성
{: #step1_create_dump_file}

다음의 `pg_dump` 명령을 사용하여 복원할 데이터베이스가 포함된 덤프 파일을 작성하십시오.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

다음의 표는 명령에서 사용되는 변수를 보여줍니다.

|변수|설명|예제|
|---------|-----------|-------|
|*host_name*|원래 데이터베이스를 호스팅하는 원격 서버입니다. 데이터를 가져오려면 호스트에 연결해야 합니다. 데이터베이스가 {{site.data.keyword.ihsdbaas_full}} Beta 인스턴스에 배치된 경우에는 클러스터 인스턴스 UI의 개요 페이지에서 호스트 주소를 찾을 수 있습니다.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|호스트에 대한 연결을 설정하기 위한 포트 번호입니다. 데이터베이스가 {{site.data.keyword.ihsdbaas_full}} Beta 인스턴스에 배치된 경우에는 클러스터 인스턴스 UI의 개요 페이지에서 포트를 찾을 수 있습니다.|25050|
|*user_name*|원래 데이터베이스에 액세스하기 위한 사용자 이름입니다. 사용자는 데이터베이스에 대한 CONNECT 권한과 테이블에 대한 SELECT 권한을 보유해야 합니다.|my_user|
|*database_name*|마이그레이션할 데이터베이스의 이름입니다.|my_database|
|*dump_file*|원래 데이터를 저장할 `.dump` 파일입니다. 상대 또는 절대 경로를 사용하여 파일을 지정할 수 있습니다.|./pgdump.dump|
{: caption="표 1. 덤프 파일 작성에 필요한 변수"}

사용자 권한에 대해 자세히 알려면 [{{site.data.keyword.postgresql}} 문서](https://www.postgresql.org/docs/10/sql-grant.html){: external}에서 자세한 정보를 참조하십시오.

## 2단계: {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}에서 새 서비스 인스턴스 작성
{: #step2_creat_new_service_instance}

데이터를 복원하려면 우선 대상 데이터베이스 클러스터로서 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}에서 새 서비스 인스턴스를 작성해야 합니다. 다음 방법 중 하나를 사용하여 새 서비스 인스턴스를 작성할 수 있습니다.
- [웹 사용자 인터페이스](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [{{site.data.keyword.cloud_notm}} CLI의 CLI 플러그인](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

새 서비스 인스턴스를 작성하는 경우에는 클러스터 이름, 관리자 이름 및 비밀번호를 설정해야 합니다. 이는 원래 인스턴스에서와 반드시 동일할 필요가 없습니다. 이는 마이그레이션에 영향을 주지 않습니다. 마이그레이션이 완료되면 데이터베이스가 새 관리자에게 지정됩니다.

## 3단계: 새 서비스 인스턴스에서 데이터베이스 작성
{: #step3_create_database}

새 서비스 인스턴스가 작성되면 새 데이터베이스를 작성해야 합니다. 데이터베이스 이름은 원래 데이터베이스의 이름과 동일해야 합니다. 사용자는 CREATE 권한을 보유해야 하며, 이는 덤프 파일을 작성한 사용자와 동일할 필요가 없습니다. 다음 방법 중 하나를 사용하여 태스크를 수행할 수 있습니다.
- [웹 사용자 인터페이스](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [{{site.data.keyword.cloud_notm}} CLI의 CLI 플러그인](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

다음 방법을 사용하여 사용자를 새로 작성할 수 있습니다. [웹 사용자 인터페이스](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [DBaaS Manger API](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [CLI {{site.data.keyword.cloud_notm}} CLI의 CLI 플러그인](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create), [{{site.data.keyword.postgresql}} 명령](https://www.postgresql.org/docs/10/sql-createuser.html){: external}
{: tip}

## 4단계: 새 서비스 인스턴스로 덤프 파일의 데이터 복원
{: #step4_restore_data}

`psql` 명령을 사용하여 [1단계](#step1_create_dump_file)에서 작성된 덤프 파일의 데이터를 복원할 수 있습니다.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

다음의 표는 명령에서 사용되는 변수를 보여줍니다.

|변수|설명|예제|
|---------|-----------|-------|
|*host_name*|대상 클러스터를 호스팅하는 DBaaS 관리자 서버입니다. 클러스터 인스턴스 UI의 개요 페이지에서 호스트 주소를 찾을 수 있습니다.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|호스트에 대한 연결을 설정하기 위한 포트 번호입니다. 클러스터 인스턴스 UI의 개요 페이지에서 포트 번호 주소를 찾을 수 있습니다.|25003|
|*user_name*|대상 데이터베이스에 액세스하기 위한 사용자 이름입니다. [3단계](#step3_create_database)에서 대상 데이터베이스를 작성한 동일한 사용자를 사용할 수 있습니다.|new_user|
|*database_name*|데이터베이스는 사용자가 CONNECT 권한을 보유한 임의의 데이터베이스일 수 있습니다. `psql` 세션이 [3단계](#step3_create_database)에서 작성된 대상 데이터베이스로 자동 전환합니다.|my_database|
|*dump_file*|[1단계](#step1_create_dump_file)에서 작성한 `.dump` 파일입니다. 상대 또는 절대 경로를 사용하여 파일을 지정할 수 있습니다.|./pgdump.dump|
{: caption="표 2. 덤프 파일에서 데이터 복원에 필요한 변수"}

## 다음에 수행할 작업
{: #whats_next_migration_postgre}

마이그레이션 이후 새 데이터베이스 클러스터에 연결하여 데이터 마이그레이션의 성공 여부를 확인할 수 있습니다.
