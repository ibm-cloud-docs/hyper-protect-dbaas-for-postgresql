---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# 데이터베이스 인스턴스
{: #dbaas-webui-database-instances}

## 시작하기 전에
{: #webui-database-instances-byb}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 대시보드에서 인스턴스 탭을 선택하십시오.

## 데이터베이스 인스턴스 시작
{: #webui-start-database-instance}

1. 데이터베이스 인스턴스를 선택하십시오.
2. 라인의 오른쪽 끝에 있는 세 개의 점을 클릭한 후 **시작**을 선택하십시오.

## 데이터베이스 인스턴스 중지
{: #webui-stop-database-instance}

1. 데이터베이스 인스턴스를 선택하십시오.
2. 라인의 오른쪽 끝에 있는 세 개의 점을 클릭한 후 **중지**를 선택하십시오. 기본 노드일 경우에는 **강제 중지**를 선택할 수도 있습니다.

## 데이터베이스 인스턴스 다시 시작
{: #webui-restart-database-instance}

1. 데이터베이스 인스턴스를 선택하십시오.
2. 라인의 오른쪽 끝에 있는 세 개의 점을 클릭한 후 **다시 시작**을 선택하십시오.

## 로그 다운로드
{: #webui-download-log}

1. 데이터베이스 인스턴스를 선택하십시오.
2. **시작 날짜** 및 **종료 날짜**를 선택하여 시간으로 로그를 필터링하십시오.
3. 로그 이름 앞에 있는 **선택란**을 클릭하여 다운로드할 로그를 선택하십시오.
4. **다운로드** 단추를 클릭하십시오.

## 인스턴스 상태 확인
{: #webui-check-instance-status}

인스턴스 패널에서 색이 있는 점은 인스턴스의 상태를 나타냅니다. 인스턴스 상태를 확인하려면 다음 표를 참조하십시오.

|색상|상태| 조치|
|-----|------|------|
|초록색|인스턴스가 실행 중입니다.|인스턴스를 중지하거나 다시 시작할 수 있습니다.|
|노란색|인스턴스가 중지되었습니다.|인스턴스를 시작할 수 있습니다.|
|빨간색|인스턴스가 실패했습니다.|[도움 및 지원 받기](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support)를 참조하십시오.|
{: caption="표 1. 상태 색상"}
