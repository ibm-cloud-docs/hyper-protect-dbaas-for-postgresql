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


# Suppression d'une instance de service
{: #dbaas_cli_delete_service}

Pour passer en revue les services que vous avez créés, utilisez la commande suivante :

<pre><code class="hljs">~$ ibmcloud resource service-instances
</code></pre>

Si vous souhaitez en supprimer un, utilisez la commande `ibmcloud resource service-instance-delete`, comme illustré dans l'exemple suivant :

<pre><code class="hljs">~$ ibmcloud resource service-instance-delete MyDBaaSIns03
</code></pre>

Confirmez la suppression en saisissant **y**.
