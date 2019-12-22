---

copyright:
  years: 2019
lastupdated: "2019-12-20"

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

# Troubleshooting for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #troubleshoot}

General problems with using {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} might include failing to get Cluster ID. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

## Why can't I get Cluster ID?
{: #troubleshoot-clusterid}
{: troubleshoot}

You might receive the error **Get Cluster ID Failed — Cannot get cluster id from cookie. Make sure that cookie is enabled in your browser!** when you use the Safari browser to open the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance dashboard.
{: tsSymptoms}

Cookies are blocked or cross-site tracking is prevented.
{: tsCauses}

In the **Privacy** preferences of your Safari browser, clear the **Website tracking** and the **Block all cookies** checkboxes, and restart the browser. If you still get the same error, restart your computer and try again.
{: tsResolve}

## Getting help and support
{: #getting-help}
{: troubleshoot}

If you still have problems with using {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, see [Getting help and support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).
