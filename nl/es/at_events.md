---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# Sucesos de {{site.data.keyword.cloudaccesstrailshort}}
{: #activity-tracker-events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento sobre cómo interactúan los usuarios y las aplicaciones con {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra actividades iniciadas por los usuarios que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener información sobre cómo suministrar el servicio {{site.data.keyword.cloudaccesstrailshort}}, consulte la [documentación de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started). Ya que el servicio {{site.data.keyword.ihsdbaas_postgresql_full}} actualmente está disponible en el centro de datos de Dallas, asegúrese de seleccionar **us-south** como la región para capturar registros.

## Lista de sucesos
{: #list-activity-tracker-events}

La tabla siguiente lista las acciones que generan un suceso:

| Acción                 | Descripción                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | Crear un clúster de base de datos                 |
| `cluster.delete` | Suprimir un clúster de base de datos                 |
| `database.create` | Crear una base de datos                  |
| `database.delete` | Suprimir una base de datos                  |
| `user.create`     | Crear un usuario de base de datos                    |
| `user.delete`     | Suprimir un usuario de base de datos                    |
| `instance.start` | Iniciar una instancia de servicio de base de datos         |
| `instance.stop`  | Detener una instancia de servicio de base de datos          |
| `instance.restart`  | Reiniciar una instancia de servicio de base de datos          |
| `log.get`       | Descargar un archivo de registro |
{: caption="Tabla 1. Acciones que generan sucesos de {{site.data.keyword.cloudaccesstrailfull_notm}}"}

En el caso de `cluster.create` y `cluster.delete`, el servicio {{site.data.keyword.cloudaccesstrailfull_notm}} no registra el nombre de la cuenta ni la dirección IP del usuario que lleva a cabo la acción. El valor de `initiator.name` y de `host.address` del registro indican el ID de servicio de Cloud Broker y la dirección IP de Cloud Broker respectivamente.
{: note}

## Dónde ver los sucesos
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de la cuenta** de {{site.data.keyword.cloudaccesstrailshort}} disponible en la región de {{site.data.keyword.cloud_notm}} donde se han generado los sucesos.
