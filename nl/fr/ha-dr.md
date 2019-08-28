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

# Considérations relatives à la disponibilité générale et la reprise après incident
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} est un service de disponibilité générale proposé à Dallas. Chaque région prise en charge comporte 3 centres de données différents pour la redondance.
{: shortdesc}

{{site.data.keyword.IBM_notm}} héberge vos bases de données dans un environnement hautement disponible et sécurisé. La technologie {{site.data.keyword.IBM_notm}} Secure Service Container protège le système via un environnement infalsifiable. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} fournit un chiffrement de données au repos et en cours d'exploitation. Etant donné que ni le personnel {{site.data.keyword.IBM_notm}} Cloud ni un tiers ne peut accéder à vos données sans votre consentement, une règle de sauvegarde et de restauration de vos bases de données est essentielle.

Voir [Sauvegarde et restauration de vos bases de données à l'aide d'IBM Cloud Object Storage](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)
et [Restauration de vos bases de données par le support IBM](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases) pour apprendre à sauvegarder et restaurer vos bases de données.
