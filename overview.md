---

copyright:
  years: 2019, 2021
lastupdated: "2021-02-06"

keywords: Hyper Protect DBaaS, cloud database, data security

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:external: target="_blank" .external}

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
