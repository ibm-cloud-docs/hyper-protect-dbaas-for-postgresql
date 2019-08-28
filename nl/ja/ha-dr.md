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

# 一般的な高可用性と災害復旧の考慮事項
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} はダラスで提供されている GA サービスです。 各サポート対象地域には、冗長性を確保するために 3 つの異なるデータ・センターがあります。
{: shortdesc}

{{site.data.keyword.IBM_notm}} は、可用性が高くセキュアな環境でデータベースをホストします。 {{site.data.keyword.IBM_notm}} Secure Service Container テクノロジーにより、改ざん防止環境でシステムを保護しています。 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} は、保存中も転送中もデータの暗号化が可能です。 {{site.data.keyword.IBM_notm}} Cloud の担当者も第三者もお客様の同意なしにお客様のデータにアクセスできないため、データベースのバックアップと復元のポリシーが不可欠です。

データベースをバックアップおよび復元する方法については、[IBM Cloud Object Storage を使用したデータベースのバックアップと復元](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)および[IBM サポートによるデータベースの復元](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases)を参照してください。
