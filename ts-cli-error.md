---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-23"

keywords: troubleshoot, troubleshooting, cli plugin error

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

# Why am I receiving the error message `Unable to obtain plug-in’s metadata. Error: signal: abort trap`?
{: #troubleshoot-cli-install-error}
{: troubleshoot}
{: support}

You might receive the error **Unable to obtain plug-in’s metadata. Error: signal: abort trap** when you install the DBaaS CLI components on MacOS.
{: tsSymptoms}

Either the installed Python version isn't correct (only Python 3.6.x is supported), or the `python-dev` isn't included in the installed Python package.
{: tsCauses}

Make sure to download and install the correct Python package from https://www.python.org/downloads/mac-osx/.
{: tsResolve}
