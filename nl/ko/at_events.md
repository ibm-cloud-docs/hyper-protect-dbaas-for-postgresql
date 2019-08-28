---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# {{site.data.keyword.cloudaccesstrailshort}} 이벤트
{: #activity-tracker-events}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자와 애플리케이션이 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}과 상호작용하는 방법을 추적할 수 있습니다.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.cloud_notm}}에서 서비스의 상태를 변경하는 사용자 시작 활동을 기록합니다. {{site.data.keyword.cloudaccesstrailshort}} 서비스를 프로비저닝하는 방법에 대한 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}} 문서](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started)를 참조하십시오. {{site.data.keyword.ihsdbaas_postgresql_full}} 서비스는 현재 댈러스 데이터 센터에서 제공되므로, 로그를 캡처하려면 지역으로 **us-south**를 선택해야 합니다.

## 이벤트 목록
{: #list-activity-tracker-events}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

| 조치                 |설명                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | 데이터베이스 클러스터 작성                 |
| `cluster.delete` | 데이터베이스 클러스터 삭제                 |
| `database.create` | 데이터베이스 작성                  |
| `database.delete` |  데이터베이스 삭제                  |
| `user.create`     | 데이터베이스 사용자 작성                    |
| `user.delete`     | 데이터베이스 사용자 삭제                    |
| `instance.start` | 데이터베이스 서비스 인스턴스 시작         |
| `instance.stop`  | 데이터베이스 서비스 인스턴스 중지          |
| `instance.restart`  | 데이터베이스 서비스 인스턴스 다시 시작          |
| `log.get`       | 로그 파일 다운로드 |
{: caption="표 1. {{site.data.keyword.cloudaccesstrailfull_notm}} 이벤트를 생성하는 조치"}

`cluster.create` 및 `cluster.delete` 이벤트의 경우 {{site.data.keyword.cloudaccesstrailfull_notm}} 서비스에서 조치를 수행한 사용자의 계정 이름과 IP 주소를 기록하지 않습니다. 로그의 `initiator.name` 및 `host.address` 값은 각각 클라우드 브로커의 서비스 ID와 클라우드 브로커의 IP 주소를 나타냅니다.
{: note}

## 이벤트를 보는 위치
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 이벤트가 생성된 {{site.data.keyword.cloud_notm}} 지역에서 사용 가능한 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**에서 사용될 수 있습니다.
