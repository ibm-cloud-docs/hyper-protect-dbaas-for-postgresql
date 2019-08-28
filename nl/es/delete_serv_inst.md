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


# Supresión de una instancia de servicio
{: #dbaas_cli_delete_service}

Para revisar los servicios que ha creado, utilice este mandato:

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

Si desea suprimir uno de ellos, utilice el mandato `ibmcloud resource service-instance-delete`, como se muestra en este ejemplo:

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

Confirme la supresión escribiendo **y**.
