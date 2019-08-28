---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Instancias de base de datos
{: #dbaas-webui-database-instances}

## Antes de empezar
{: #webui-database-instances-byb}

En el panel de control de {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, seleccione el separador Instancias.

## Inicio de una instancia de base de datos
{: #webui-start-database-instance}

1. Seleccione la instancia de base de datos.
2. Pulse los tres puntos situados en el extremo derecho de la línea y, a continuación, seleccione **Iniciar**.

## Detención de una instancia de base de datos
{: #webui-stop-database-instance}

1. Seleccione la instancia de base de datos.
2. Pulse los tres puntos situados en el extremo derecho de la línea y, a continuación, seleccione **Detener**. Si es un nodo primario, también puede seleccionar **Forzar detención**.

## Reinicio de una instancia de base de datos
{: #webui-restart-database-instance}

1. Seleccione la instancia de base de datos.
2. Pulse los tres puntos situados en el extremo derecho de la línea y, a continuación, seleccione **Reiniciar**.

## Descarga del registro
{: #webui-download-log}

1. Seleccione la instancia de base de datos.
2. Seleccione la **Fecha de inicio** y la **Fecha de finalización** para filtrar los registros por tiempo.
3. Seleccione los registros que desea descargar pulsando **el recuadro de selección** que hay antes del nombre del registro.
4. Pulse el botón **Descargar**.

## Comprobación del estado de la instancia
{: #webui-check-instance-status}

El punto coloreado del panel de la instancia indica el estado de la instancia. Puede consultar la tabla siguiente para comprobar el estado de la instancia.

|Color|Estado|Acción|
|-----|------|------|
|Verde|La instancia se está ejecutando.|Puede detener o reiniciar la instancia.|
|Amarillo|La instancia se ha detenido.|Puede iniciar la instancia.|
|Rojo|La instancia ha fallado.|Puede consultar el apartado sobre [Obtención de ayuda y de soporte](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Tabla 1. El color de estado"}
