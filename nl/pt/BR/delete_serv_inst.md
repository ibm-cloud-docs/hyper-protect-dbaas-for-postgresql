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


# Excluindo uma instância de serviço
{: #dbaas_cli_delete_service}

Para revisar quais serviços você criou, use este comando:

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

Se você desejar excluir um deles, use o comando `ibmcloud resource service-instance-delete`, conforme mostrado neste exemplo:

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

Confirme a exclusão digitando **y**.
