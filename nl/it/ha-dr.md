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

# Considerazioni generali sull'alta disponibilità e il ripristino d'emergenza
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} è un servizio GA offerto in Dallas. Ogni ubicazione ha tre diversi data center per la ridondanza.
{: shortdesc}

{{site.data.keyword.IBM_notm}} ospita i tuoi database in un ambiente altamente disponibile e sicuro. La tecnologia {{site.data.keyword.IBM_notm}} SSC (Secure Service Container) protegge il sistema tramite
un ambiente a prova di manomissione. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} fornisce la crittografia dei dati sia quando sono inattivi che quando sono in transito. Poiché né il personale di {{site.data.keyword.IBM_notm}} Cloud né un servizio di terze parti può accedere ai tuoi dati senza il tuo consenso, è essenziale una politica di backup e ripristino per i tuoi database.

Vedi [](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases)Backup e ripristino dei tuoi database utilizzando IBM Cloud Object Storage
e [Ripristino dei tuoi database da parte del supporto IBM](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases)
per ulteriori informazioni su come eseguire il backup e il ripristino dei tuoi database.
