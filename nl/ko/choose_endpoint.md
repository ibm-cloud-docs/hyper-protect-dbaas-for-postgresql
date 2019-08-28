---

copyright:
  years: 2019
lastupdated: "2019-06-20"

keywords: service endpoint, ibmcloud regions

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# 로그인할 서비스 엔드포인트 선택
{: #choose-endpoint}

{{site.data.keyword.cloud}}는 로그인이 가능한 다양한 지리적 지역에서 많은 서비스 엔드포인트를 제공합니다.
사용자의 지리적 위치 근처의 서비스 엔드포인트를 찾으려면 다음 예제에 표시된 대로 `ibmcloud regions` 명령을 사용하십시오.

<pre><code class="hljs">~$ ibmcloud regions
Listing regions...

Name       Display name
au-syd     Sydney
jp-tok     Tokyo
eu-de      Frankfurt
eu-gb      London
us-south   Dallas
us-east    Washington DC

</code></pre>

현재 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}은 **us-south** 지역에서만 지원됩니다.
{: note}

{{site.data.keyword.cloud_notm}} 서비스 엔드포인트에 로그인하려면 다음 단계를 따르십시오.

1. 다음 예제에 표시된 대로 SSO(Single Sign-On)를 사용 중임을 표시하고 로그인할 엔드포인트의 URL을 지정하여 `ibmcloud login` 명령을 입력하십시오.

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   시스템에서 일회성 패스코드를 제공하는 웹 페이지의 URL을 표시합니다.

2. 시스템 콘솔에서 URL을 복사하여 이를 웹 브라우저에 붙여넣으십시오.

   시스템에서 **{{site.data.keyword.cloud_notm}} 일회성 패스코드** 페이지를 표시합니다.

3. 웹 페이지에서 패스코드를 복사하여 이를 시스템 콘솔 명령행에 붙여넣으십시오.

   패스코드는 명령행에 표시되지 않습니다. 비밀번호가 인증되면 로그인되었음을 표시하는 **OK** 메시지를 받습니다.

`ibmcloud login` 명령 매개변수에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} CLI 참조](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)를 참조하십시오.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}을 사용 중인 경우 둘 이상의 지역에 영역을 작성하고 `ibmcloud target` 명령을 사용하여 지역 간에 전환해야 할 수 있습니다. 자세한 정보는
[조직 및 영역 추가](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)
및 [일반 CLI(ibmcloud) 명령](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target)을 참조하십시오.
{: note}
