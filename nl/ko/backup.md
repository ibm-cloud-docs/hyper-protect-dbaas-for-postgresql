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


# {{site.data.keyword.cos_full_notm}}를 사용하여 데이터베이스 백업 및 복원
{: #backup_postgresql_databases}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 서비스는 24시간마다 한 번씩 전체 데이터베이스의 백업을 자동으로 트리거합니다. 이러한 암호화된 백업은 최근 7일에 대해 사용 가능하며, 지원되는 지역의 모든 가용성 구역에 있는 로컬 스토리지에서 중복 사용할 수 있습니다.
{: shortdesc}

재해 복구 기능을 늘리고 지원되는 지역 외부에 데이터를 백업하려는 경우 다음 단계에 따라 [{{site.data.keyword.cos_full_notm}} 서비스](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external}를 사용하여 데이터를 다른 지역에 저장할 수 있습니다.

## 시작하기 전에
{: #backup_postgresql_before_begin}

{{site.data.keyword.postgresql}} 명령을 사용하여 백업을 완료하려면 먼저 시스템에 {{site.data.keyword.postgresql}}을 다운로드하여 설치해야 합니다. 자세한 정보는 [{{site.data.keyword.postgresql}} 웹 사이트](https://www.postgresql.org/download/){: external}를 참조하십시오.

## 1단계: 원본 데이터베이스 백업용 덤프 파일 작성
{: #step1_create_dump_file_backup_postgresql}

다음 `pg_dump` 명령을 사용하여 백업할 데이터베이스가 포함된 덤프 파일을 작성하십시오.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

다음의 표는 명령에서 사용되는 변수를 보여줍니다.

|변수|설명|예제|
|---------|-----------|-------|
|*host_name*|원래 데이터베이스를 호스팅하는 원격 서버입니다. 데이터를 가져오려면 호스트에 연결해야 합니다. 클러스터 인스턴스 UI의 개요 페이지에서 호스트 주소를 찾을 수 있습니다.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|호스트에 대한 연결을 설정하기 위한 포트 번호입니다. 클러스터 인스턴스 UI의 개요 페이지에서 포트를 찾을 수 있습니다.|25050|
|*user_name*|원래 데이터베이스에 액세스하기 위한 사용자 이름입니다. 사용자는 데이터베이스에 대한 CONNECT 권한과 테이블에 대한 SELECT 권한을 보유해야 합니다.|my_user|
|*database_name*|백업할 데이터베이스의 이름입니다.|my_database|
|*dump_file*|원래 데이터를 저장할 `.dump` 파일입니다. 상대 또는 절대 경로를 사용하여 파일을 지정할 수 있습니다.|./pgdump.dump|
{: caption="표 1. 덤프 파일 작성에 필요한 변수"}

사용자 권한에 대해 자세히 알려면 [{{site.data.keyword.postgresql}} 문서](https://www.postgresql.org/docs/10/sql-grant.html){: external}에서 자세한 정보를 참조하십시오.

## 2단계: {{site.data.keyword.cos_full_notm}} 인스턴스 새로 작성
{: #step2_create_object_storage_backup_postgresql}

{{site.data.keyword.ihsdbaas_postgresql_full}} 서비스 인스턴스가 현재 호스팅되는 지역과 다른 지역에 인스턴스를 작성해야 합니다. 다음 단계를 참조하십시오.

1. [Cloud {{site.data.keyword.cos_short}} 인스턴스를 새로 작성](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision)하십시오.
2. 다른 지역에 [버킷을 작성](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region)하십시오.
3. [서비스 인증 정보를 작성](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials)한 후 나중에 사용할 수 있도록 `access_key_id` 및 `secret_access_key`를 저장하십시오.
4. S3 클라이언트를 설치하십시오.
5. S3 클라이언트와 액세스 키를 사용하여 앞에서 작성한 버킷의 Cloud {{site.data.keyword.cos_short}} 엔드포인트에 연결하십시오.
6. S3 클라이언트를 사용하여 [[1단계](#step1_create_dump_file_backup_postgresql)(/docs/services/cloud-object-storage?topic=cloud-object-storage-upload)]에서 작성한 {{site.data.keyword.postgresql}} 백업 파일을 버킷에 업로드하십시오.

자세한 내용은 [{{site.data.keyword.cos_full_notm}} 문서](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started)를 참조하십시오.

이 단계를 완료하면 Cloud {{site.data.keyword.cos_short}} 인스턴스의 데이터가 다른 지역에 성공적으로 백업됩니다. Cloud {{site.data.keyword.cos_short}} 인스턴스의 데이터를 {{site.data.keyword.ihsdbaas_postgresql_full}} 인스턴스로 복원하려면 다음 3단계에서 세부사항을 참조하십시오.

## 3단계: Cloud {{site.data.keyword.cos_short}} 인스턴스에서 {{site.data.keyword.ihsdbaas_postgresql_full}} 인스턴스로 데이터 복원
{: #step3_restore_data_from_cos_postgresql}

Cloud {{site.data.keyword.cos_short}} 버킷의 백업 파일을 로컬 시스템으로 먼저 다운로드한 후 `psql` 명령을 사용하여 데이터를 복원해야 합니다.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

다음의 표는 명령에서 사용되는 변수를 보여줍니다.

|변수|설명|예제|
|---------|-----------|-------|
|*host_name*|대상 클러스터를 호스팅하는 DBaaS 관리자 서버입니다. 클러스터 인스턴스 UI의 개요 페이지에서 호스트 주소를 찾을 수 있습니다.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|호스트에 대한 연결을 설정하기 위한 포트 번호입니다. 클러스터 인스턴스 UI의 개요 페이지에서 포트 번호 주소를 찾을 수 있습니다.|25003|
|*user_name*|대상 데이터베이스에 액세스하기 위한 사용자 이름입니다.|new_user|
|*database_name*|데이터베이스는 사용자가 CONNECT 권한을 보유한 임의의 데이터베이스일 수 있습니다. `psql` 세션이 데이터를 복원할 대상 데이터베이스로 자동 전환합니다.|my_database|
|*dump_file*|Cloud {{site.data.keyword.cos_short}} 버킷에서 다운로드하는 `.dump` 파일입니다. 상대 또는 절대 경로를 사용하여 파일을 지정할 수 있습니다.|./pgdump.dump|
{: caption="표 2. 덤프 파일에서 데이터 복원에 필요한 변수"}

## 다음에 수행할 작업
{: #whats_next_backup_postgresql}

[3단계](#step3_restore_data_from_cos_postgresql)를 수행한 후에는 데이터베이스 클러스터에 연결하여 데이터가 성공적으로 복원되었는지 확인할 수 있습니다.
