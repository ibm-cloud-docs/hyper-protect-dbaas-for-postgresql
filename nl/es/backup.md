---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: backup, disaster recovery, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:tip: .tip}


# Copia de seguridad y restauración de sus bases de datos utilizando {{site.data.keyword.cos_full_notm}}
{: #backup_postgresql_databases}

El servicio {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} desencadena automáticamente una copia de seguridad de su base de datos completa una vez cada 24 horas. Estas copias de seguridad cifradas están disponibles durante los últimos 7 días y disponibles de forma redundante en el almacenamiento local en todas las Zonas de disponibilidad de la región soportada.
{: shortdesc}

Si desea ampliar sus funciones de recuperación tras desastre y realizar una copia de seguridad de los datos fuera de la región soportada, puede utilizar el [servicio {{site.data.keyword.cos_full_notm}}](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} para almacenar los datos en otra región siguiendo los pasos siguientes.

## Antes de empezar
{: #backup_postgresql_before_begin}

Para utilizar los mandatos de {{site.data.keyword.postgresql}} para completar la copia de seguridad, primero debe descargar e instalar {{site.data.keyword.postgresql}} en la máquina. Para obtener más información, consulte el [sitio web de {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Paso 1: Crear un archivo de volcado para hacer copia de seguridad de las bases de datos originales
{: #step1_create_dump_file_backup_postgresql}

Utilice el siguiente mandato `pg_dump` para crear un archivo de volcado que contenga las bases de datos de las que desea hacer copia de seguridad.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

En la tabla siguiente se muestran las variables utilizadas en el mandato.

|Variables|Descripción|Ejemplo|
|---------|-----------|-------|
|*host_name*|El servidor remoto que aloja las bases de datos originales. Debe conectarse al host para obtener los datos. Puede encontrar la dirección de host en la página de visión general de la interfaz de usuario de la instancia de clúster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|El número de puerto para establecer una conexión con el host. Puede encontrar el puerto en la página de visión general de la interfaz de usuario de la instancia de clúster.|25050|
|*user_name*|El nombre de usuario para acceder a las bases de datos originales. El usuario tiene que tener el privilegio CONNECT en la base de datos y el privilegio SELECT para las tablas.|my_user|
|*database_name*|El nombre de la base de datos de la que desea hacer copia de seguridad.|my_database|
|*dump_file*|El archivo `.dump` para almacenar los datos originales. Puede utilizar vías de acceso absolutas o relativas para especificar el archivo.|./pgdump.dump|
{: caption="Tabla 1. Las variables necesarias para crear un archivo de volcado"}

Para obtener más información sobre los privilegios de usuario, consulte el [sitio web de {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Paso 2: Crear una nueva instancia de {{site.data.keyword.cos_full_notm}}
{: #step2_create_object_storage_backup_postgresql}

Tiene que crear la instancia en una región distinta de aquella en la que está alojada actualmente la instancia de servicio de {{site.data.keyword.ihsdbaas_postgresql_full}}. Puede seguir los siguientes pasos:

1. [Cree una nueva instancia de {{site.data.keyword.cos_short}} en la nube](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Cree un grupo](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) en otra región.
3. [Cree una credencial de servicio](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) y guarde `access_key_id` y `secret_access_key` para utilizarlos más adelante.
4. Instale un cliente S3.
5. Utilice el cliente S3 y las claves de acceso para conectar con el punto final de {{site.data.keyword.cos_short}} de la nube del grupo que ha creado antes.
6. Utilice el cliente S3 para [cargar el archivo de copia de seguridad de {{site.data.keyword.postgresql}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) que ha creado en el [Paso 1](#step1_create_dump_file_backup_postgresql) en el grupo.

Consulte la [documentación de {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started) para obtener más información.

Después de completar este paso, habrá hecho una copia de seguridad correctamente de sus datos en una instancia de {{site.data.keyword.cos_short}} en la nube en otra región. Si desea restaurar los datos de la instancia de {{site.data.keyword.cos_short}} en la nube en una instancia de {{site.data.keyword.ihsdbaas_postgresql_full}}, lea el siguiente Paso 3 para ver detalles.

## Paso 3: Restaurar los datos de la instancia de {{site.data.keyword.cos_short}} en la nube en una instancia de {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step3_restore_data_from_cos_postgresql}

Primero tiene que descargar el archivo de copia de seguridad del grupo de {{site.data.keyword.cos_short}} en la nube en su máquina local y luego utilizar el mandato `psql` para restaurar los datos.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

En la tabla siguiente se muestran las variables utilizadas en el mandato.

|Variables|Descripción|Ejemplo|
|---------|-----------|-------|
|*host_name*|El servidor del gestor de DBaaS que aloja el clúster de destino. Puede encontrar la dirección de host en la página de visión general de la interfaz de usuario de la instancia de clúster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|El número de puerto para establecer una conexión con el host. Puede encontrar el número de puerto en la página de visión general de la interfaz de usuario de la instancia de clúster.|25003|
|*user_name*|El nombre de usuario para acceder a la base de datos de destino.|new_user|
|*database_name*|La base de datos puede ser cualquier base de datos en la que el usuario tenga el privilegio CONNECT. La sesión `psql` cambia automáticamente a la base de datos de destino en la que desea restaurar los datos.|my_database|
|*dump_file*|El archivo `.dump` que ha descargado del grupo de {{site.data.keyword.cos_short}} en la nube. Puede utilizar vías de acceso absolutas o relativas para especificar el archivo.|./pgdump.dump|
{: caption="Tabla 2. Las variables necesarias para restaurar los datos de un archivo de volcado"}

## Qué hacer a continuación
{: #whats_next_backup_postgresql}

Después del [Paso 3](#step3_restore_data_from_cos_postgresql), puede conectar con el clúster de la base de datos para comprobar si los datos se han restaurado correctamente.
