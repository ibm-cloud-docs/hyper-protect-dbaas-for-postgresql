---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-22"

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

# FAQs about usage
{: #faqs-usage}

You can use the following FAQs to help you with {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}. To find all FAQs for {{site.data.keyword.cloud_notm}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## How can I prevent data loss from hardware failure?
{: #protect-from-failure}
{: faq}
{: support}

{{site.data.keyword.ihsdbaas_postgresql_full}} provides [automatic in-region data redundancy and failover](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery#in-region-redundancy-failover) and [automatic database backups in all availability zones](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery#automatic-daily-backups). It also supports [manual cross-region backups](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery#cross-region-backups) to prepare for the disaster scenario where the entire region fails.

## Do I need to enable the replication to secondary nodes manually?
{: #replication-by-default}
{: faq}
{: support}

No. By default, your {{site.data.keyword.ihsdbaas_full}} service instance consists of three nodes, one primary and two secondary nodes in three different availability zones in the {{site.data.keyword.cloud_notm}} region. The data in your primary node is automatically replicated to secondary nodes (replicas) with low latency.

## Can {{site.data.keyword.ihsdbaas_full}} back up my data automatically?
{: #automatic-backup}
{: faq}
{: support}

Yes. {{site.data.keyword.ihsdbaas_full}} does [automatic database backups](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery#automatic-daily-backups) in all availability zones in the region of your service instance every day. You can restore your data from backups in the last seven days.

## Where can I find usage and billing information?
{: #metering-and-billing}
{: faq}
{: support}

Go to **Manage > Billing and usage** in the {{site.data.keyword.cloud_notm}} console. For more information, see [How you're charged](/docs/billing-usage?topic=billing-usage-charges).
