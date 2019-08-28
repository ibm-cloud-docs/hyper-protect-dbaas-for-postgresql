---

copyright:
  years: 2019
lastupdated: "2019-06-05"

keywords: ibmcloud resource, service instance, CLI tool

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# 서비스 인스턴스 삭제
{: #dbaas_cli_delete_service}

작성한 서비스를 검토하려면 다음 명령을 사용하십시오.

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

서비스 인스턴스 중 하나를 삭제하려면 다음 예제에 표시된 대로 `ibmcloud resource service-instance-delete` 명령을 사용하십시오.

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

**y**를 입력하여 삭제를 확인하십시오.
