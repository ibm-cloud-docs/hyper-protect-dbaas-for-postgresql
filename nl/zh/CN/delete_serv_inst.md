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


# 删除服务实例
{: #dbaas_cli_delete_service}

要查看已创建的服务，请使用以下命令：

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

如果要删除其中一个服务，请使用 `ibmcloud resource service-instance-delete` 命令，如以下示例中所示：

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

通过输入 **y** 来确认删除。
