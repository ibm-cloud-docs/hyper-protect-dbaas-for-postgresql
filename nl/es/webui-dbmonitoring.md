---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Supervisión de bases de datos
{: #dbaas-webui-database-monitor}

Una vez habilitada la supervisión de bases de datos, podrá visualizar las métricas de base de datos mediante Grafana.
{: shortdesc}

## Antes de empezar
{: #webui-database-monitoring-byb}

1.  Asegúrese de tener acceso a una organización de Cloud Foundry y a un espacio en Dallas (us-south).
    Para obtener información sobre cómo obtener dicho acceso, consulte [Gestión del acceso de Cloud Foundry](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}.

2.  Asegúrese de que todas las instancias del clúster de la base de datos se estén ejecutando.

3.  En el panel de control de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, seleccione el separador Supervisión.

## Habilitación de la supervisión de bases de datos
{: #webui-enable-database-monitoring}

En caso de que aparezca el mensaje **La supervisión está inhabilitada** en el separador Supervisión:

1. Pulse **Habilitar**.
2. En la ventana Habilitar supervisión, seleccione la organización y el espacio y, a continuación, pulse **Enviar**.


## Visualización de métricas de base de datos
{: #webui-view-database-metrics}

Existen dos maneras de ver las métricas en Grafana:

- Copie el enlace visualizado, abra un nuevo separador o ventana y pegue el enlace en el navegador.
- Pulse **Ver en Grafana**.

Para visualizar las métricas en un nuevo panel de control en Grafana, seleccione el icono de Grafana de la esquina superior izquierda y, a continuación, **Paneles de control > Nuevo**.
Puede tardar un poco hasta que se muestren todos los ID de instancia y de clúster de base de datos, y es posible que tenga que volver a cargar el panel de control.

Para obtener más información sobre el uso de Grafana, consulte [Supervisión de {{site.data.keyword.cloud_notm}}](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started).
