---

copyright:
  years: 2020
lastupdated: "2020-11-24"

keywords: Hyper Protect DBaaS, postgresql database, responsibilities

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:pre: .pre}	
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:term: .term}
{:external: target="_blank" .external}

# Understanding your responsibilities when using {{site.data.keyword.ihsdbaas_full}}
{: #responsibilities-hpdbass}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_full}}. For a high-level view of the service types in {{site.data.keyword.cloud_notm}} and the breakdown of responsibilities between the Customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.ihsdbaas_full}}. For the overall terms of use, see [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

## Incident and operations management
{: #incident-and-ops-responsibilities}

Incident and operations management includes tasks such as backup and recovery, monitoring, and high availability.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
|Backups and restore| {{site.data.keyword.ihsdbaas_full}} is responsible for making automatic daily backups, monitoring the state of customer backups, and restoring backup upon customer requests.| The Customer is responsible for submitting the [restoration request](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases), timeliness, and validity of restored data. |
|Monitoring| {{site.data.keyword.ihsdbaas_full}} is responsible for integrating monitoring and health services. | The Customer is responsible for setting up their service instances of [Monitoring](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-monitor), [Activity Tracker](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-activity-tracker-events), or [Logging services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-sendlogs). |
|[High availability](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-high-availability-disaster-recovery)| {{site.data.keyword.ihsdbaas_full}} is responsible for deploying databases across availability zones in a [Multi-Zone region (MZR)](#x9774820){: term} and storing backups in local storage across availability zones. {{site.data.keyword.ihsdbaas_full}} provides replication, fail-over features, and infrastructure maintenance and updates. | The Customer is responsible for designing application logic to retry connections caused by temporary connection failures (during regular database maintenance and updates).|
|Database performance | {{site.data.keyword.ihsdbaas_full}} is responsible for hosting and maintaining database infrastructure. | The Customer is responsible for the data model and performance, including tuning the data model, queries, [configuration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-changing-configuration), and [scaling resources](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling) for application needs. |
{: caption="Table 1. Responsibilities for incident and operations" caption-side="top"}

## Change management
{: #change-management-responsibilities}

Change management includes tasks such as upgrades.<!--deployment, configuration, upgrades, patching, configuration changes, and deletion-->

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
|Major version upgrades| {{site.data.keyword.ihsdbaas_full}} is responsible for providing availability and tooling for database major version upgrades. | The Customer is responsible for migrating to a supported version before end-of-support for old version. |
{: caption="Table 2. Responsibilities for change management" caption-side="top"}

## Security and regulation compliance
{: #security-responsibilities}

Security and regulation compliance includes tasks such as security controls implementation<!--and compliance certification-->.

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
|Encryption| {{site.data.keyword.ihsdbaas_full}} is responsible for the encryption of data on disk, in motion, and in backups. | The Customer is responsible for choosing and managing appropriate additional security features. If the Customer uses [Key Protect (Bring Your Own Key)](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) or [{{site.data.keyword.hscrypto}} (Keep Your Own Key)](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok), the Customer is responsible for managing the service authorization and keys. |
|Security| {{site.data.keyword.ihsdbaas_full}} is responsible for ensuring the security of data on disk and data in motion within our infrastructure. | The Customer is responsible for managing {{site.data.keyword.cloud_notm}} passwords and database passwords, and keeping passwords secure. |
{: caption="Table 3. Responsibilities for security and regulation compliance" caption-side="top"}

## Disaster recovery
{: #disaster-recovery-responsibilities}

Disaster recovery includes tasks such as provisioning disaster recovery environments.
<!--Disaster recovery includes tasks such as providing dependencies on disaster recovery sites, provision disaster recovery environments, data and configuration backup, replicating data and configuration to the disaster recovery environment, and failover on disaster events.-->

| Task | {{site.data.keyword.IBM_notm}} Responsibilities | Your Responsibilities |
|----------|-----------------------|--------|
|Backups|{{site.data.keyword.ihsdbaas_full}} is responsible for automatic backups and storing them in local storage across availability zones in an MZR. | If required, the Customer can define their own cross-region backup policy to create [cross-region data redundancy](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases). |
{: caption="Table 4. Responsibilities for disaster recovery" caption-side="top"}
