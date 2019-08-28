---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: access token, DBaaS Manager APIs, API key

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# DBaaS Manager API 사용을 위한 인증 설정
{: #api-auth}

인증을 위해서는 API 요청을 실행하기 위한 사용자 ID 및 API 키, 액세스 토큰이 필요합니다.
이를 수행하려면 다음 지시사항을 따르십시오.

1. API 키 생성:

   a. {{site.data.keyword.cloud}} 대시보드에서 **관리 > 액세스(IAM)**를 선택하십시오.

      액세스(IAM) 대시보드가 표시됩니다.

   b. 액세스(IAM) 대시보드의 사이드 탐색 패널에서 **{{site.data.keyword.cloud_notm}} API 키**를 선택하십시오.

   c. **{{site.data.keyword.cloud_notm}} API 키 작성**을 클릭하십시오.

      API 키 작성 대화 상자가 표시됩니다.

   d. API 키 작성 대화 상자에서 API 키의 이름과 설명을 입력하고 **작성**을 클릭하십시오.

   e. **다운로드**를 클릭하여 API 키를 다운로드 및 저장하거나 **복사**를 클릭하여 API 키를 클립보드에 복사하십시오.

      이 오퍼레이션은 다음 예제와 유사한 JSON 파일을 리턴합니다.

      ```
      {
       "name": "dbaasmgr",
       "description": "DBaaS Manager",
       "createdAt": "201...",
       "apiKey": "**Pt...Y**"
      }
       ```
      {: codeblock}

      `apiKey`에 지정된 값은 사용자의 API 키입니다. **중요:** 창을 닫기 전에 이 값을 기록해 두십시오.

2. 데이터 전송의 보안을 유지하려면 {{site.data.keyword.ihsdbaas_postgresql_full}} 대시보드에서 인증 기관(CA) 파일을 가져와서 이를 적절한 디렉토리(예: **/etc/ssl/certs/**)에 복사하십시오.

3. GET /auth/token 오퍼레이션을 사용하여 액세스 토큰과 사용자 ID를 가져오십시오.

    ```curl
    curl -X GET -H "accept: application/json" -H "api_key: icGVY1*** ***UdfcIg4kzE" https://dbaas900.hyperp-dbaas.cloud.ibm.com:20000/api/v1/auth/token
    ```
    {: pre}

    이 오퍼레이션은 다음 예제와 유사한 액세스 토큰과 사용자 ID를 리턴합니다.

    ```
    {
     "access_token":"eyJraWQiOiIyMDE3MT*** ***3V4pMYrOvMniLA",
     "user_id":"e9433*** ***b188"
    }
    ```
    {: codeblock}

4. 향후 사용을 위해 액세스 토큰과 사용자 ID의 값을 저장하십시오.
