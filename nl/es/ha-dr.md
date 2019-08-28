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

# Consideraciones sobre la recuperación tras desastre y alta disponibilidad
{: #ha-dr}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} es un servicio de disponibilidad general que se ofrece en Dallas. Cada región soportada tiene tres centros de datos distintos para redundancia.
{: shortdesc}

{{site.data.keyword.IBM_notm}} aloja las bases de datos en un entorno de alta disponibilidad y seguridad. La tecnología Secure Service Container de {{site.data.keyword.IBM_notm}} protege el sistema a través de un entorno a prueba de manipulaciones. {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} proporciona cifrado de datos en reposo y en curso. Ya que ni el personal de {{site.data.keyword.IBM_notm}} Cloud ni un tercero pueden acceder a sus datos sin su consentimiento, es esencial tener una política de copia de seguridad y restauración de sus bases de datos.

Consulte [Copia de seguridad y restauración de sus bases de datos utilizando IBM Cloud Object Storage](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases) y [Restauración de sus bases de datos por parte del equipo de soporte de IBM](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases) para aprender cómo hacer una copia de seguridad de sus bases de datos y restaurarlas.
