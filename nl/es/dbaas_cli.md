---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: instance commands, cluster resource, CLI plugin

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


# Plugin de la CLI de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #dbaas_cli_plugin}

Utilice el plugin de la CLI de {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} para crear, suprimir y visualizar información sobre bases de datos y usuarios, para mostrar detalles sobre clústeres, para iniciar y detener instancias y para listar y descargar archivos de registro.
{:shortdesc}


## Prerrequisitos
{: #prerequisites_dbaas_cli_plugin}

- Instale la [CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started). La CLI de {{site.data.keyword.cloud_notm}} requiere Java SDK 1.7.0. El prefijo para ejecutar mandatos mediante la CLI de {{site.data.keyword.cloud_notm}} es `ibmcloud`. En el terminal, se le notifica cuando están disponibles las actualizaciones de la CLI y los plugins de `ibmcloud`. Asegúrese de mantener actualizada la CLI para poder utilizar todos los mandatos y distintivos disponibles.

- Instale el plugin de la CLI de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}. Puede consultar el apartado sobre [Instalación del plugin de la CLI de DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin). Si desea ver la versión actual del plugin de la CLI de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, ejecute `ibmcloud plugin show dbaas-cli`.


## Mandato de uso de plugin de CLI
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

Este mandato muestra una lista de mandatos DBaaS.

```
ibmcloud help dbaas
```
{: pre}


## Mandato de clúster
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

Este mandato muestra los detalles del clúster especificado, incluida la información sobre cada miembro de la réplica.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster. Para encontrar el nombre del recurso, utilice el mandato de {{site.data.keyword.cloud_notm}} `ibmcloud resource service-instances`.</dd>
</dl>

## Mandatos de base de datos
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

Este mandato crea una base de datos y, opcionalmente, una recopilación.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*database_name*</dt>
<dd>El nombre de la base de datos que se va a crear.</dd>
<dt>*collection*</dt>
<dd>(Opcional) El nombre de la recopilación que se va a crear.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

Este mandato suprime una base de datos. No suprima una base de datos si dicha base de datos se ha creado mediante credencial y si dicha credencial aún está en uso.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*database_name*</dt>
<dd>El nombre de la base de datos que se va a suprimir.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

Este mandato lista todas las bases de datos en el clúster determinado.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
</dl>


## Mandatos de usuario de base de datos
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

Este mandato crea un usuario de base de datos.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*username*</dt>
<dd>El nombre de usuario que se va a asignar al usuario de base de datos que se está creando.</dd>
<dt>*db_name*</dt>
<dd>(Opcional) Especifica una base de datos a la cual el usuario tendrá acceso de lectura y escritura.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

Este mandato suprime un usuario de base de datos. No suprima un usuario de base de datos si dicho usuario de base de datos se ha creado mediante credencial y si dicha credencial aún está en uso.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*username*</dt>
<dd>El nombre de usuario del usuario de base de datos que se está suprimiendo.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

Este mandato lista todos los usuarios de base de datos.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

Este mandato muestra detalles sobre un usuario de base de datos.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*username*</dt>
<dd>El nombre de usuario del usuario de base de datos mostrado.</dd>
</dl>


## Mandatos de instancia
{: #instance_cmds}

Para utilizar cualquiera de los mandatos de instancia que se muestran aquí, debe conocer el `instance_id`. Para obtener un `instance_id`, primero utilice el siguiente mandato `ibmcloud` para obtener una lista de nombres de grupos de recursos de instancia de servicio de su cuenta y luego utilice el mandato [`cluster_show`](#cluster_show) para obtener el `instance_id`.

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

Este mandato reinicia una instancia en ejecución.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*instance_id*</dt>
<dd>El ID de la instancia.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

Este mandato inicia una instancia detenida.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*instance_id*</dt>
<dd>El ID de la instancia.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

Este mandato detiene una instancia (un miembro de réplica del clúster).

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*instance_id*</dt>
<dd>El ID de la instancia.</dd>
</dl>


## Mandatos de registro
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

Este mandato descarga un archivo de registro de una instancia.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*instance_id*</dt>
<dd>El ID de la instancia.</dd>
<dt>*filename*</dt>
<dd>El nombre del archivo de registro que se va a descargar. Para determinar el nombre del archivo de registro que desea descargar, utilice el mandato [ibmcloud dbaas logs-list](#log_list).</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

Este mandato lista todos los archivos de registro de una instancia. Puede utilizar cualquiera de los nombres de archivo listados como entrada para el mandato [ibmcloud dbaas log-get](#log_get).

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Opciones del mandato**

<dl>
<dt>*resource_name*</dt>
<dd>El nombre del recurso del clúster.</dd>
<dt>*instance_id*</dt>
<dd>El ID de la instancia.</dd>
</dl>
