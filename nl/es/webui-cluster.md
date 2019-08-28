---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Instancias de servicio
{: #dbaas_webui_service}

## Creación de una instancia de servicio
{: #dbaas_webui_create_service}

<ol>
<li>Pulse la entrada del catálogo de {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} para abrir la pantalla de creación del servicio.</li>
<li>Especifique los valores necesarios.
  <dl>
    <dt>Nombre del servicio:</dt>
    <dd>Un nombre para el servicio de base de datos.</dd>

    <dt>Seleccione una región/ubicación de despliegue:</dt>
    <dd>Seleccione el centro de datos en el que se ubicará la base de datos.</dd>

    <dt>Seleccione un grupo de recursos:</dt>
    <dd>Si no se puede seleccionar ningún grupo de recursos, puede crear uno en el panel de control de {{site.data.keyword.cloud_notm}}.</dd>

    <dt>Etiquetas:</dt>
    <dd>Las etiquetas son opcionales. Consulte [Etiquetado de recursos](/docs/resources?topic=resources-tag#tag) para obtener más información sobre el etiquetado.</dd>

    <dt>Nombre de clúster/Replicaset:</dt>
    <dd>Un nombre para la instancia de servicio.</dd>

    <dt>Nombre del administrador de la base de datos:</dt>
    <dd>Un ID de usuario para el administrador de base de datos (DBA).
    <p>**Nota:** El administrador de base de datos no tiene autoridad de SUPERUSER. Las autoridades del administrador de base de datos están limitadas a INHERIT, CREATEROLE, CREATEDB, LOGIN y REPLICATION.</p></dd>

    <dt>Contraseña del administrador de la base de datos:</dt>
    <dd>
    <p>Una contraseña para el ID de usuario de DBA. Tiene que crear una contraseña fuerte con los siguientes atributos:
      <ul>
        <li>mínimo de **15 caracteres** de longitud</li>
        <li>al menos **un carácter en mayúscula**</li>
        <li>al menos **un carácter en minúscula**</li>
        <li>al menos **un número**</li>
        <li>no debe contener el nombre de usuario</li>
      </ul>
    </p>
    </dd>

    <dt>Confirmar contraseña:</dt>
    <dd>Confirme la contraseña para el ID de usuario de DBA.</dd>

    <dt>Acuerdo de licencia:</dt>
    <dd>Después de leer el acuerdo de licencia, marque el recuadro para confirmar su acuerdo.</dd>

    <dt>Planes de precios:</dt>
    <dd>Los planes de precios ofrecen distintas categorías de precios para bases de datos de tipo PostgreSQL. Elija el que mejor se adapte a sus necesidades.</dd>
  </dl>
</li>
<li>Pulse **Crear**.
<p>Después de una ventana de diálogo que le indica que se tarda un rato en desplegar el servicio, se muestra el panel de control de la lista de recursos de {{site.data.keyword.cloud_notm}}. Puede ver la instancia de servicio que ha creado en la sección **Servicios** de la lista. Cuando el estado del servicio sea **Suministrado**, la instancia estará lista para ser utilizada.</p>
</li>

<li>Seleccione el servicio para visualizar el panel de control de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.</li>
</ol>

Para reforzar aún más la seguridad, se recomienda actualizar la **contraseña de administración de la base de datos** inmediatamente después de que se suministre la instancia de servicio. Debe seguir las mismas reglas mencionadas anteriormente para establecer la nueva contraseña.
{: note}

## Listado de todas las instancias de servicio
{: #dbaas_webui_list_service}

Abra el panel de control de {{site.data.keyword.cloud_notm}} para visualizar una lista de las instancias de servicio creadas:

<ol>
	<li>Pulse el botón con las tres barras de la parte superior izquierda de la consola.</li>
	<li>Seleccione Panel de control.</li>
	<li>Seleccione Servicios.</li>
</ol>

## Mostrar información detallada de una instancia de servicio
{: #dbaas_webui_show_detail_service}

1. Pulse el nombre de la instancia de destino para ver el panel de control del servicio.
2. Seleccione **Gestionar** en la barra de navegación de la izquierda y verá la información general en la página del separador **Visión general**.
3. Seleccione el separador **Instancias** para ver la información detallada.


## Supresión de una instancia de servicio
{: #dbaas_webui_delete_service}

1. Visualice la lista de recursos de {{site.data.keyword.cloud_notm}} pulsando **Menú de navegación > Lista de recursos**.
2. Abra el mosaico **Servicio** para visualizar las instancias de servicio.
3. Seleccione la instancia de servicio que desea suprimir.
4. Pulse los tres puntos de la derecha.
5. Pulse **Suprimir**.
