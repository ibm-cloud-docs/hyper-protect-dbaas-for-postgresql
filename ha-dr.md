---

copyright:
  years: 2019
lastupdated: "2019-08-28"

keywords: high availability disaster recovery

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# General high availability and disaster recovery considerations
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} is a GA service that is offered in Dallas and Frankfurt. Each supported region has three different data centers for redundancy.
{: shortdesc}

{{site.data.keyword.IBM_notm}} hosts your databases in a highly available and secure environment. The {{site.data.keyword.IBM_notm}} Secure Service Container technology protects the system via a tamper-proof environment. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} provides data encryption at rest and in flight. Because neither {{site.data.keyword.IBM_notm}} Cloud personnel nor a third party is able to access your data without your consent, a backup and restore policy for your databases is essential.

See [Backing up and restoring your databases using IBM Cloud Object Storage](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)
and [Restoring your databases by IBM Support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases)
to learn how to back up and restore your databases.
