---

copyright:
  years: 2019
lastupdated: "2019-06-18"

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

# 常规高可用性和灾难恢复注意事项
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 是在达拉斯提供的 GA 服务。每个支持的区域有三个不同的数据中心以实现冗余。
{: shortdesc}

{{site.data.keyword.IBM_notm}} 在高可用性的安全环境中托管数据库。{{site.data.keyword.IBM_notm}} Secure Service Container 技术通过防篡改环境来保护系统。{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 提供数据静态加密和动态加密。由于 {{site.data.keyword.IBM_notm}} Cloud 员工和第三方未经您同意都无法访问您的数据，因此数据库的备份和复原策略至关重要。

请参阅[使用 IBM Cloud Object Storage 备份和复原数据库](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)以及[通过 IBM 支持复原数据库](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases)，以了解如何备份和复原数据库。
