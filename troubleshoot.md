---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-23"

keywords: troubleshoot, troubleshooting, can't get cluster id

subcollection: hyper-protect-dbaas-for-postgresql

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #troubleshoot}

General problems with using {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} might include failing to get Cluster ID. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

## Unable to get Cluster ID
{: #troubleshoot-clusterid}
{: troubleshoot}
{: support}

You might receive the error **Get Cluster ID Failed — Cannot get cluster id from cookie. Make sure that cookie is enabled in your browser!** when you use the Safari browser to open the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance dashboard.
{: tsSymptoms}

Cookies are blocked or cross-site tracking is prevented.
{: tsCauses}

In the **Privacy** preferences of your Safari browser, clear the **Website tracking** and the **Block all cookies** checkboxes, and restart the browser. If you still get the same error, restart your computer and try again.
{: tsResolve}

## Got error message `Unable to obtain plug-in’s metadata. Error: signal: abort trap` when you install the DBaaS CLI components
{: #troubleshoot-cli-install-error}
{: troubleshoot}
{: support}

You might receive the error **Unable to obtain plug-in’s metadata. Error: signal: abort trap** when you install the DBaaS CLI components on MacOS.
{: tsSymptoms}

Either the installed Python version isn't correct (only Python 3.6.x is supported), or the `python-dev` isn't included in the installed python package.
{: tsCauses}

Make sure to download and install the correct Python package from https://www.python.org/downloads/mac-osx/.
{: tsResolve}

## Getting help and support
{: #getting-help}
{: troubleshoot}

If you still have problems with using {{site.data.keyword.ihsdbaas_postgresql_full}}, see [Getting help and support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).
