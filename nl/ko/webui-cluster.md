---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# 서비스 인스턴스
{: #dbaas_webui_service}

## 서비스 인스턴스 작성
{: #dbaas_webui_create_service}

<ol>
<li>{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 카탈로그 항목을 클릭하여 서비스 작성 화면을 여십시오.</li>
<li>필수 값을 입력하십시오.
  <dl>
    <dt>서비스 이름:</dt>
    <dd>데이터베이스 서비스의 이름입니다.</dd>

    <dt>배치할 지역/위치 선택:</dt>
    <dd>데이터베이스가 위치할 데이터 센터를 선택하십시오.</dd>

    <dt>리소스 그룹 선택:</dt>
    <dd>리소스 그룹을 선택할 수 없는 경우 {{site.data.keyword.cloud_notm}} 대시보드에서 하나를 작성할 수 있습니다.</dd>

    <dt>태그:</dt>
    <dd>태그는 선택사항입니다. 태그 지정에 대한 자세한 정보는 [리소스에 태그 지정](/docs/resources?topic=resources-tag#tag)을 참조하십시오.</dd>

    <dt>클러스터/복제본 세트 이름:</dt>
    <dd>서비스 인스턴스의 이름입니다.</dd>

    <dt>데이터베이스 관리자 이름:</dt>
    <dd>데이터베이스 관리자(DBA)의 사용자 ID입니다.
    <p>**참고:** 데이터베이스 관리자는 SUPERUSER 권한이 없습니다. 데이터베이스 관리자의 권한은 INHERIT, CREATEROLE, CREATEDB, LOGIN 및 REPLICATION으로 제한됩니다.</p></dd>

    <dt>데이터베이스 관리자 비밀번호:</dt>
    <dd>
    <p>DBA 사용자 ID의 비밀번호입니다. 다음 속성을 갖는 강력한 비밀번호를 작성해야 합니다.
      <ul>
        <li>최소 **15자**</li>
        <li>최소 **대문자 1개**</li>
        <li>최소 **소문자 1개**</li>
        <li>최소 **숫자 1개**</li>
        <li>사용자 이름을 포함하면 안됨</li>
      </ul>
    </p>
    </dd>

    <dt>비밀번호 확인:</dt>
    <dd>DBA 사용자 ID의 비밀번호를 확인하십시오.</dd>

    <dt>라이센스 계약:</dt>
    <dd>라이센스 계약을 읽은 후에 계약에 동의함을 확인하는 상자를 선택하십시오.</dd>

    <dt>가격 플랜:</dt>
    <dd>가격 플랜은 PostgreSQL 유형의 데이터베이스에 대한 다양한 가격 카테고리를 제공합니다. 요구사항에 최적인 플랜을 선택하십시오.</dd>
  </dl>
</li>
<li>**작성**을 클릭하십시오.
<p>서비스를 배치하는 데 시간이 걸린다는 대화 상자 창이 표시된 후 {{site.data.keyword.cloud_notm}} 리소스 목록 대시보드가 표시됩니다. **서비스** 섹션에 작성한 서비스 인스턴스가 목록에 표시됩니다. 서비스 상태가 **프로비저닝됨**이라면 인스턴스를 사용할 준비가 된 것입니다.</p>
</li>

<li>{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 대시보드를 표시할 서비스를 선택하십시오.</li>
</ol>

보안을 더 강화하려면 서비스 인스턴스가 프로비저닝된 후 **데이터베이스 관리자 비밀번호**를 즉시 업데이트하는 것이 좋습니다. 새 비밀번호를 설정하기 위해 이전에 언급된 동일한 규칙을 따라야 합니다.
{: note}

## 모든 서비스 인스턴스 나열
{: #dbaas_webui_list_service}

{{site.data.keyword.cloud_notm}} 대시보드를 열어서 작성된 서비스 인스턴스의 목록을 표시하십시오.

<ol>
	<li>콘솔의 왼쪽 상단에서 3개의 막대로 된 단추를 클릭하십시오.</li>
	<li>대시보드를 선택하십시오.</li>
	<li>서비스를 선택하십시오.</li>
</ol>

## 서비스 인스턴스에 대한 자세한 정보 표시
{: #dbaas_webui_show_detail_service}

1. 대상 인스턴스 이름을 클릭하여 서비스 대시보드를 표시하십시오.
2. 왼쪽 탐색줄에서 **관리**를 선택하면 **개요** 탭 페이지에 전반적인 정보가 표시됩니다.
3. **인스턴스** 탭을 선택하여 자세한 정보를 표시하십시오.


## 서비스 인스턴스 삭제
{: #dbaas_webui_delete_service}

1. **탐색 메뉴 > 리소스 목록**을 클릭하여 {{site.data.keyword.cloud_notm}} 리소스 목록을 표시하십시오.
2. **서비스** 트위스터를 열어서 서비스 인스턴스를 표시하십시오.
3. 삭제할 서비스 인스턴스를 선택하십시오.
4. 오른쪽에 있는 세 개의 점을 클릭하십시오.
5. **삭제**를 클릭하십시오.
