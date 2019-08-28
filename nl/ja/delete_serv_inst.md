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


# サービス・インスタンスの削除
{: #dbaas_cli_delete_service}

作成したサービスを確認するには、以下のコマンドを使用します。

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

それらのいずれかを削除する場合は、以下の例に示すように `ibmcloud resource service-instance-delete` コマンドを使用します。

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

**y** と入力して、削除を確認します。
