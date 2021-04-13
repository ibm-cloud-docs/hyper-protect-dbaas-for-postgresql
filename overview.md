---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-13"

keywords: Hyper Protect DBaaS, cloud database, data security

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# About {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #overview}

Moving confidential and mission critical data to the cloud presents data confidentiality, security, and reliability concerns. {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} offers highly secure database environments that have technology-enforced protection and high availability.
{: shortdesc}

## Why {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}?
{: #why_hpdb}

Built on {{site.data.keyword.IBM_notm}} LinuxONE technology, {{site.data.keyword.ihsdbaas_postgresql_full}} helps you to alleviate data security and compliance concerns with built-in encryption and tamper protection for data at rest and in flight. You can deploy your workloads with sensitive data and build compliant applications without having to be a security expert.

{{site.data.keyword.ihsdbaas_postgresql_full}} provides a reliable environment that allows you to become more agile in application development. You can quickly get started and move your mission-critical data to the highly available and managed database clusters, saving time and costs on operations. You can also flexibly adjust the amount of resources to meet your requirements.

## How does {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} work?
{: #how_hpdb_works}

The following architectural diagram shows the architecture of {{site.data.keyword.ihsdbaas_postgresql_full}} in an {{site.data.keyword.cloud_notm}} region. 

![{{site.data.keyword.ihsdbaas_postgresql_full}} architecture](images/architecture.svg "{{site.data.keyword.ihsdbaas_postgresql_full}} architecture"){: caption="Figure 1. {{site.data.keyword.ihsdbaas_postgresql_full}} architecture" caption-side="bottom"}

## Features
{: #features}

### Data security and confidentiality
{: #data_security}

Leveraging {{site.data.keyword.IBM_notm}} LinuxONE pervasive encryption and {{site.data.keyword.IBM_notm}} [Secure Service Container](https://www.ibm.com/us-en/marketplace/secure-service-container){: external} technology, {{site.data.keyword.ihsdbaas_postgresql_full}} provides workload isolation, restricted administrator access and tamper protection for data at rest and in flight. You can maintain complete control over your data; not even the cloud administrator has access to it at any point. For more information about security, see [Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security).

### Highly available
{: #highly_available}

When you create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance, you create a cluster that consists of one primary node and two secondary nodes (replicas that back up the primary). Each of them is installed in a unique Availability Zone with automatic daily backups in the local storage. For more information, see [High availability and disaster recovery](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery). {{site.data.keyword.ihsdbaas_postgresql_full}} also supports [manual vertical scaling of resources](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling).

### Managed service
{: #managed}

{{site.data.keyword.ihsdbaas_postgresql_full}} offers non-disruptive version upgrades, monitoring of the system by IBM SREs, and around-the-clock support from {{site.data.keyword.cloud_notm}}. You can focus on building applications rather than managing availability, hardware setup, software patching, etc.

### Developer friendly
{: #developer_friendly}

{{site.data.keyword.ihsdbaas_postgresql_full}} provides standardized APIs to provision and monitor databases. It‘s easy for you to [get started](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted) without the need for specialized database skills.

## What's next
{: #whats_next}

- Follow the [getting started tutorial](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted) to try out the service for free.
- For the compliance standards that {{site.data.keyword.ihsdbaas_postgresql_full}} follow, see [Compliance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-compliance).
- Stay up to date with the latest features with [Release notes](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-what-new).
