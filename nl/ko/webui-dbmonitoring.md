---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# 데이터베이스 모니터링
{: #dbaas-webui-database-monitor}

데이터베이스 모니터링 사용을 설정한 이후 Grafana를 사용하여 데이터베이스 메트릭을 볼 수 있습니다.
{: shortdesc}

## 시작하기 전에
{: #webui-database-monitoring-byb}

1.  Dallas(us-south)의 Cloud Foundry 조직 및 영역에 대한 액세스 권한이 있는지 확인하십시오.
    이와 같은 액세스 권한을 얻는 방법에 대한 정보는 [Cloud Foundry 액세스 관리](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}를 참조하십시오.

2.  데이터베이스 클러스터의 모든 인스턴스가 실행 중인지 확인하십시오.

3.  {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 대시보드에서 모니터링 탭을 선택하십시오.

## 데이터베이스 모니터링 사용
{: #webui-enable-database-monitoring}

**모니터링 사용 안함** 메시지가 모니터링 탭에 표시될 경우 다음을 수행하십시오.

1. **사용**을 클릭하십시오.
2. "모니터링 사용" 창에서 조직 및 영역을 선택하고 **제출**을 클릭하십시오.


## 데이터베이스 메트릭 보기
{: #webui-view-database-metrics}

Grafana에서 메트릭을 보는 두 가지 방법이 있습니다.

- 표시된 링크를 복사한 후 새 탭이나 창을 열고 해당 링크를 브라우저에 붙여넣으십시오.
- **Grafana에서 보기**를 클릭하십시오.

Grafana의 새 대시보드에 메트릭을 표시하려면 상단 왼쪽 Grafana 아이콘을 선택한 다음 **대시보드 > 새로 작성**을 선택하십시오.
데이터베이스 클러스터 ID 및 인스턴스 ID가 표시되려면 다소 시간이 걸릴 수 있으며 대시보드를 다시 로드해야 할 수 있습니다.

Grafana 사용에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} 모니터링](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started)을 참조하십시오.
