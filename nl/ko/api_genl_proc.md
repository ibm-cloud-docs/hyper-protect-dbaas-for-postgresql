---

copyright:
  years: 2019
lastupdated: "2019-06-21"

keywords: DBaaS Manager APIs, DBaaS Manager, API request

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# DBaaS Manager API 사용을 위한 일반 지시사항
{: #gen_inst_mgr_apis}
<ol>
<li>JSON 형식으로 요청의 데이터를 지정하십시오.
</li>
<li>API 요청을 DBaaS Manager에 전송하십시오.
<p>RESTful API 클라이언트(예: cURL)를 사용하여 요청을 처리할 수 있습니다.
</p>
<p>DBaaS Manager는 다음에서 사용 가능합니다.
<table>
  <tr>
    <th> 호스트 이름 </th>
    <th> 포트 번호 </th>
    <th> 지역 </th>
    <th> 도시 </th>
  </tr>
  <tr>
    <td> dbaas900.hyperp-dbaas.cloud.ibm.com </td>
    <td> 20000 </td>
    <td> us-south </td>
    <td> Dallas </td>
  </tr>
</table>
</p>	 
</li>
</ol>

자세한 정보(메소드 및 매개변수)는 [DBaaS API 문서](https://{DomainName}/apidocs/hyperp-dbaas){: external}를 참조하십시오.

## 예제
{: #api-example}

서비스 인스턴스를 작성하려면 다음과 같이 직접 API 호출을 실행하십시오.

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

여기서:
<dl>
<dt> &lt;<em>access_token</em>&gt; </dt>
<dd>이전에 가져온 액세스 토큰입니다. [DBaaS Manager API 사용을 위한 인증 설정](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth)을 참조하십시오. (**참고:** 액세스 토큰이 만료된 경우에는 해당 지시사항으로 돌아가서 새 토큰을 요청하십시오.) </dd>
<dt> &lt;<em>ip</em>&gt; </dt>
<dd>DBaaS Manager의 호스트 이름입니다. 유효한 호스트 이름은 위의 표에 나열되어 있습니다.
</dd>
<dt> &lt;<em>port</em>&gt; </dt>
<dd>DBaaS Manager의 포트 번호입니다. 유효한 포트 번호는 다음과 같습니다.
<p>20000</p>
</dd>
</dl>

**참고:** 데이터베이스 관리자는 SUPERUSER 권한이 없습니다.
데이터베이스 관리자의 권한은 INHERIT, CREATEROLE, CREATEDB, LOGIN 및 REPLICATION으로 제한됩니다.
