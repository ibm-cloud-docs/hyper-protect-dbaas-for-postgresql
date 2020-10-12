---

copyright:
  years: 2019, 2020
lastupdated: "2020-10-13"

keywords: frequently asked questions, database

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
{:faq: data-hd-content-type='faq'}
{:external: target="_blank" .external}
{:support: data-reuse='support'}

# General FAQs
{: #faqs-general}

You can use the following FAQs to help you with {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}. To find all FAQs for {{site.data.keyword.cloud_notm}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## What's {{site.data.keyword.postgresql}}?
{: #what-is-postgresql}
{: faq}

{{site.data.keyword.postgresql}} is an open source object-relational database management system. For more information, see [What is {{site.data.keyword.postgresql}}](https://www.postgresql.org/about/){: external}.

## What database types does {{site.data.keyword.ihsdbaas_full}} support?
{: #supported-databases}
{: faq}

{{site.data.keyword.postgresql}} and {{site.data.keyword.mongodb}} EE (see [{{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#postgresql_supported_version) and [{{site.data.keyword.ihsdbaas_mongodb_full}}](/docs/hyper-protect-dbaas-for-mongodb?topic=hyper-protect-dbaas-for-mongodb-gettingstarted#mongodb_supported_version)).

<!--## What are the next DB types supported (after {{site.data.keyword.postgresql}} and {{site.data.keyword.postgresql}})?

## Which DB version is included and when/how can I move to the latest?
How long can I stay on the current DB version until I have to move to the latest?-->

## What's Secure Service Container?
{: #whats-secure-service-container}
{: faq}

{{site.data.keyword.ihsdbaas_full}} is built with [{{site.data.keyword.IBM_notm}} Secure Service Container (SSC)](https://www.ibm.com/us-en/marketplace/secure-service-container){: external} technology. SSC provides the base infrastructure for an integration of operating system, middleware and software components, which are packaged to work autonomously and provide core services and infrastructure with a focus on consumability and security. It protects data and applications from internal or external threats, including misuse of privileged infrastructure admin credentials.  

## What's pervasive encryption?
{: #what-is-pervasive-encryption}
{: faq}

{{site.data.keyword.ihsdbaas_full}} is built on the {{site.data.keyword.IBM_notm}} LinuxONE platform, which provides pervasive encryption of data at rest and in transit. Pervasive encryption is an infrastructure for an end-to-end data protection. In particular, it includes data volume encryption with protected and secure keys. For more information, see [Pervasive encryption](https://www.ibm.com/support/knowledgecenter/linuxonibm/liaaf/lnz_r_crypt.html){: external}.

## How is {{site.data.keyword.ihsdbaas_full}} different from other cloud databases, including {{site.data.keyword.cloud_notm}} databases?
{: #hyper-protect-dbaas-difference}
{: faq}
{: support}

Built on {{site.data.keyword.IBM_notm}} LinuxONE technology, {{site.data.keyword.ihsdbaas_full}} offers the highest level of protection for customer data in the industry. For more information about security, see [Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-data-security). It also provides 2X performance compared to x86 based cloud databases. 

## Can I own and manage my data encryption keys?
{: #keep-or-bring-your-own-key}
{: faq}
{: support}

Yes, you can own and manage your data encryption keys by enabling the [integration with {{site.data.keyword.keymanagementserviceshort}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) or [with {{site.data.keyword.hscrypto}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok) when you create a {{site.data.keyword.ihsdbaas_full}} service instance.

## Where can I find detailed pricing information?
{: #pricing-info}
{: faq}

You can find the pricing information on the [service creation page](https://cloud.ibm.com/catalog/services/hyper-protect-dbaas-for-postgresql){: external}.
