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


# Eliminazione di un'istanza del servizio
{: #dbaas_cli_delete_service}

Per controllare quali servizi hai creato, utilizza questo comando:

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

Se vuoi eliminarne uno, utilizza il comando `ibmcloud resource service-instance-delete`, come mostrato in questo esempio:

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

Conferma l'eliminazione immettendo **y**.
