---

copyright:
  years: 2019
lastupdated: "2019-12-18"

keywords: high availability disaster recovery

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}

# High availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} provides several ways to protect your data and help keep your applications operational.
{: shortdesc}

## Types of protection
{: #types-of-protection}

High Availability (HA) means providing the best possible continuous data availability after hardware failure to avoid impact on operations. Disaster Recovery (DR) means the ability to make all the data available on an alternative system as quickly as possible after a severe or extensive hardware failure.

{{site.data.keyword.ihsdbaas_postgresql_full}} provides [automatic in-region data redundancy and failover](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-ha-dr#in-region-redundancy-failover) by default. The service is offered in Multi-Zone regions (Dallas, Frankfurt, and Sydney), each with three availability zones for redundancy.

To prepare for the disaster scenario where the entire region fails (broken network, for example) and the service in that region becomes unavailable, you need to define your own cross-region backup policy to restore your data in another available region. {{site.data.keyword.ihsdbaas_postgresql_full}} supports [manual cross-region backups](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-ha-dr#cross-region-backups).

{{site.data.keyword.ihsdbaas_postgresql_full}} does [automatic database backups in all availability zones](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-ha-dr#automatic-daily-backups) every day. You can restore your data from backups in the last seven days.

## Automatic in-region data redundancy and failover
{: #in-region-redundancy-failover}

You can create {{site.data.keyword.ihsdbaas_postgresql_full}} service instances in one of the supported {{site.data.keyword.cloud_notm}} regions, which represent the geographic area where your service requests are handled and processed. By default, your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance consists of three nodes, one primary and two secondary nodes in three different availability zones in the {{site.data.keyword.cloud_notm}} region.

The data in your primary node are automatically replicated to secondary nodes (replicas) with low latency. You don't need to do anything to enable the replication. When your primary node fails, a secondary node in the cluster will be elected as the primary to prevent your applications from being affected. In this way, you have automatic high availability within one region for your data.

## Manual cross-region backups
{: #cross-region-backups}

To protect your data across more than one region against the disaster scenario where the entire region fails, you need to define your own cross-region backup policy. To create cross-region data redundancy, you need to have regular backups of your complete databases from your service instance in a region, and when the region is unavailable, you can provision a new service instance in another available region to restore your database manually. For detailed instructions on backing up and restoring your data in a different region, see [Backing up and restoring your databases using IBM Cloud Object Storage](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases).

Time of restoration varies, depending on the size of your data and network condition. For your reference, it takes about 45 minutes to restore data of 10G from Poughkeepsie to a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance deployed in Dallas. Therefore, to minimize the impact of region-wide failures, you need to plan ahead, for example, by having a service instance in a second region as a cold standby.

## Automatic database backups in all availability zones
{: #automatic-daily-backups}

[Automatic in-region data redundancy and failover](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-ha-dr#in-region-redundancy-failover) provide high availability within one region. [Manual cross-region backups](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-ha-dr#cross-region-backups) provide a disaster recovery capability that helps you protect against failures across an entire region. Both of the HA/DR capabilities help you to maintain access to the current copy of your data.

You can also choose to restore your data from automatic historical backups. {{site.data.keyword.ihsdbaas_postgresql_full}} automatically triggers a backup of your complete database once every 24 hours. These encrypted backups are available for the last seven days and redundantly available on local storage in all availability zones of the supported regions. If you want to restore one of the backups, see [Restoring your databases by IBM Support](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases).
