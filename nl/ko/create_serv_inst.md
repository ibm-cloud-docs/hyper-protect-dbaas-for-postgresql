---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: service instance, ibmcloud resource

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# 서비스 인스턴스 작성
{: #dbaas_cli_create_service}

서비스 인스턴스를 작성하려면 다음 예제에 표시된 대로 `ibmcloud resource service-instance-create` 명령을 사용하십시오. Windows에서는 Bash 터미널(예: Cygwin 또는 Git Bash)을 사용하여 명령을 입력하는 것이 좋습니다.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

여기서 매개변수의 정의는 다음과 같습니다.

| 매개변수        |정의                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   | 서비스 인스턴스의 이름(직접 선택한 이름으로 대체)입니다. |
| *hyperp-dbaas-postgresql* | {{site.data.keyword.ihsdbaas_postgresql_full}}의 카탈로그 이름입니다. |
| *postgresql-small*  | 플랜 이름입니다. 사용 가능한 플랜은 **postgresql-small**, **postgresql-medium** 및 **postgresql-large**입니다. (**참고:** 플랜 이름은 대소문자를 구분합니다.) |
| *us-south*            | 새 데이터베이스가 있을 위치입니다. (**참고:** 현재는 **us-south**에서만 {{site.data.keyword.ihsdbaas_postgresql_full}}을 지원합니다.) |
| *-p*               |다음 표의 매개변수를 포함해야 하는 유효한 JSON 문자열입니다. |

<table>
  <tr>
    <th> -p 매개변수</th>
    <th>정의</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td> 데이터베이스 클러스터의 이름입니다.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td> 작성할 데이터베이스에 대한 관리자의 사용자 이름입니다.</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p> 작성할 데이터베이스에 대한 관리자의 사용자 비밀번호입니다. 다음 속성을 갖는 강력한 비밀번호를 작성해야 합니다.
        <ul>
          <li>최소 **15자**</li>
          <li>최소 **대문자 1개**</li>
          <li>최소 **소문자 1개**</li>
          <li>최소 **숫자 1개**</li>
          <li>사용자 이름을 포함하면 안됨</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td> 동일한 비밀번호입니다.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td> **agreed** 값은 {{site.data.keyword.ihsdbaas_postgresql_full}}의 사용에 필요한 라이센스 계약의 동의를 표시합니다.</td>
  </tr>
</table>

명령을 입력한 후에 다음 예제에 표시된 대로 새 서비스 인스턴스의 상태가 잠시 **inactive**로 나타날 수 있습니다.

```
Creating service instance MYDBaaSIns03 in resource group default of account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Service instance MYDBaaSIns03 was created.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753   
Location:         us-south   
State:            inactive   
Type:             service_instance   
Sub Type:            
Created at:       2019-06-03T06:17:13Z   
Updated at:       2019-06-03T06:17:13Z   
Last Operation:                      
                  Status       create in progress      
                  Updated At   2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

이는 클러스터 준비에 수 분이 소요되기 때문에 발생하는 현상입니다. 클러스터 상태를 업데이트하려면 다음 예제에 표시된 대로 `ibmcloud resource service-instances` 명령을 사용하십시오.

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

보안을 더 강화하려면 서비스 인스턴스가 프로비저닝된 후 **데이터베이스 관리자 비밀번호**를 즉시 업데이트하는 것이 좋습니다. 새 비밀번호를 설정하기 위해 이전에 언급된 동일한 규칙을 따라야 합니다.
{: note}
