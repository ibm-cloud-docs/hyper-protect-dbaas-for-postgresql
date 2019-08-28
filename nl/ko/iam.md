---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

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

# Identity and Access Management 역할 및 조치
{: #iam}

계정의 사용자를 위한 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 서비스 인스턴스 액세스는 {{site.data.keyword.cloud_notm}} Identity and Access Management(IAM)로 제어됩니다. 계정의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 서비스에 액세스하는 모든 사용자를 IAM 역할이 정의된 액세스 정책에 지정해야 합니다. 정책은 선택된 서비스 또는 인스턴스의 컨텍스트 내에서 사용자가 수행할 수 있는 조치를 판별합니다. 허용 가능한 조치는 서비스에서 수행할 수 있는 오퍼레이션으로서 {{site.data.keyword.cloud_notm}} 서비스를 통해 사용자 정의하고 정의합니다. 그런 다음 조치를 IAM 사용자 역할에 맵핑합니다.
{: shortdesc}

정책을 통해 다양한 레벨에서 액세스 권한을 부여할 수 있습니다. 옵션 중 일부에는 다음이 포함됩니다.

* 계정의 서비스의 모든 인스턴스에 대한 액세스
* 계정의 개별 서비스 인스턴스에 대한 액세스
* 인스턴스 내 특정 리소스에 대한 액세스

액세스 정책의 범위를 정의한 후 사용자 액세스 레벨을 판별하는 역할을 지정합니다. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 서비스 내에서 각 역할이 허용하는 조치를 설명한 다음 표를 검토하십시오.

다음 표에는 플랫폼 관리 역할에 맵핑되는 조치가 자세히 설명되어 있습니다. 플랫폼 관리 역할을 사용하면 사용자가 플랫폼 레벨에서 서비스 리소스에 대한 태스크를 수행할 수 있습니다(예: 서비스에 대한 사용자 액세스 지정, 인스턴스 작성 또는 삭제 및 애플리케이션에 인스턴스 바인드).

|플랫폼 관리 역할        |조치 설명             |조치 예                                                         |
|------------------------|----------------------|----------------------------------------------------------------|
|뷰어                    |서비스 인스턴스를 볼 수 있지만 수정할 수 없음|<ul><li>클러스터 나열</li><li>클러스터의 세부사항 보기</li></ul>|
|편집자                  |계정 관리 및 액세스 정책 지정을 제외한 모든 플랫폼 조치를 수행할 수 있음|<ul><li>클러스터에 서비스 바인드</li></ul>|
|운영자                  |서비스 대시보드 보기와 같이 서비스 인스턴스를 구성하고 운영하는 데 필요한 플랫폼 조치를 수행할 수 있음|<ul><li>클러스터에 서비스 바인드</li></ul>|
|관리자                  |다른 사용자에게 액세스 정책 지정을 포함해, 이 역할이 지정되는 리소스를 기반으로 한 모든 플랫폼 조치를 수행할 수 있음|<ul><li>클러스터 제거</li><li>클러스터 작성</li><li>사용자 액세스 정책 업데이트</li><li>뷰어, 편집자 및 운영자가 수행할 수 있는 모든 조치</li></ul>|
{: caption="표 1. IAM 사용자 역할 및 조치"}

UI에서 사용자 역할 지정에 대한 정보는 [리소스에 대한 액세스 관리](/docs/iam?topic=iam-iammanidaccser#iammanidaccser)를 참조하십시오.
