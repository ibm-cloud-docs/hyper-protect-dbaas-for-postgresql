---

copyright:
  years: 2019
lastupdated: "2019-06-18"

keywords: high availability disaster recovery

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 일반 고가용성 및 재해 복구 고려사항
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}은 댈러스에서 제공되는 GA 서비스입니다. 지원되는 각 지역에는 중복성을 위해 세 가지 서로 다른 데이터 센터가 있습니다.
{: shortdesc}

{{site.data.keyword.IBM_notm}}은 고가용성의 보안 환경에서 데이터베이스를 호스팅합니다. {{site.data.keyword.IBM_notm}} Secure Service Container 기술은 변조 방지 환경을 통해 시스템을 보호합니다. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}은 저장 및 이동 시 데이터 암호화를 제공합니다. {{site.data.keyword.IBM_notm}} Cloud 직원이나 서드파티 모두 사용자의 동의 없이 사용자의 데이터에 액세스할 수 없으므로 사용자 데이터베이스의 백업 및 복원 정책이 필수적입니다.

데이터베이스를 백업하고 복원하는 방법에 대해 알아보려면
[IBM Cloud Object Storage를 사용하여 데이터베이스 백업 및 복원](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)
및 [IBM 지원 센터에서 데이터베이스 복원](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases)을 참조하십시오.
