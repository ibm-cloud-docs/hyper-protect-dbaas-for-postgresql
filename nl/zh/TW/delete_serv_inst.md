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


# 刪除服務實例
{: #dbaas_cli_delete_service}

若要檢閱已建立的服務，請使用下列指令：

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

如果要刪除其中一個服務，請使用 `ibmcloud resource service-instance-delete` 指令，如下列範例中所示：

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

藉由輸入 **y** 來確認刪除。
