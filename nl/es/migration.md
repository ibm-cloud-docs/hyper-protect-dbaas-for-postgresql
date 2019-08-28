---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: migrate, beta, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Migración de bases de datos {{site.data.keyword.postgresql}} a {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

Si está utilizando bases de datos {{site.data.keyword.postgresql}} y desea migrar a {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, lea este tema para obtener información detallada. No importa dónde estén alojadas las bases de datos {{site.data.keyword.postgresql}}, siempre que la plataforma proporcione servicios de base de datos {{site.data.keyword.postgresql}}.
{: shortdesc}

## Antes de empezar
{: #migration_postgre_before_begin}

Para utilizar los mandatos de {{site.data.keyword.postgresql}} para completar la migración, primero debe descargar e instalar {{site.data.keyword.postgresql}} en la máquina. Para obtener más información, consulte el [sitio web de {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Paso 1: Crear un archivo de volcado para restaurar las bases de datos originales
{: #step1_create_dump_file}

Utilice el siguiente mandato `pg_dump` para crear un archivo de volcado que contenga las bases de datos que desea restaurar.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

En la tabla siguiente se muestran las variables utilizadas en el mandato.

|Variables|Descripción|Ejemplo|
|---------|-----------|-------|
|*host_name*|El servidor remoto que aloja las bases de datos originales. Debe conectarse al host para obtener los datos. Si las bases de datos se despliegan en una instancia de {{site.data.keyword.ihsdbaas_full}} Beta, puede encontrar la dirección de host en la página de visión general de la interfaz de usuario de la instancia de clúster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|El número de puerto para establecer una conexión con el host. Si las bases de datos se despliegan en una instancia de {{site.data.keyword.ihsdbaas_full}} Beta, puede encontrar el puerto en la página de visión general de la interfaz de usuario de instancia de clúster.|25050|
|*user_name*|El nombre de usuario para acceder a las bases de datos originales. El usuario tiene que tener el privilegio CONNECT en la base de datos y el privilegio SELECT para las tablas.|my_user|
|*database_name*|El nombre de la base de datos que desea migrar.|my_database|
|*dump_file*|El archivo `.dump` para almacenar los datos originales. Puede utilizar vías de acceso absolutas o relativas para especificar el archivo.|./pgdump.dump|
{: caption="Tabla 1. Las variables necesarias para crear un archivo de volcado"}

Para obtener más información sobre los privilegios de usuario, consulte el [sitio web de {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Paso 2: Crear una instancia de servicio nueva en {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Antes de restaurar los datos, tiene que crear una nueva instancia de servicio en {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} como clúster de base de datos de destino. Puede utilizar una de las formas siguientes para crear una instancia de servicio nueva:
- [La interfaz de usuario de web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [Las API del gestor de DBaaS](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [El plugin de CLI con la CLI de {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

Cuando crea la nueva instancia de servicio, debe establecer el nombre de clúster, el nombre de administrador y la contraseña. No tienen que ser necesariamente las mismas que en la instancia original. No afecta a la migración. Una vez completada la migración, las bases de datos se asignan al nuevo administrador.

## Paso 3: Crear bases de datos en la nueva instancia de servicio
{: #step3_create_database}

Tras crear la nueva instancia de servicio, debe crear bases de datos nuevas. Las bases de datos deben tener el mismo nombre que las originales. El usuario debe tener el privilegio CREATE y no tiene que ser el mismo que el usuario que crea el archivo de volcado. Puede utilizar una de las formas siguientes para realizar la tarea:
- [La interfaz de usuario de web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [Las API del gestor de DBaaS](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [El plugin de CLI con la CLI de {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

Puede seguir los métodos siguientes para crear nuevos usuarios: [la interfaz de usuario web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [las API de DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [el plugin de CLI con la CLI de {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create) y el [mandato {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Paso 4: Restaurar los datos del archivo de volcado en una nueva instancia de servicio
{: #step4_restore_data}

Utilice el mandato `psql` para restaurar los datos del archivo de volcado que se ha creado en el [Paso 1](#step1_create_dump_file).

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

En la tabla siguiente se muestran las variables utilizadas en el mandato.

|Variables|Descripción|Ejemplo|
|---------|-----------|-------|
|*host_name*|El servidor del gestor de DBaaS que aloja el clúster de destino. Puede encontrar la dirección de host en la página de visión general de la interfaz de usuario de la instancia de clúster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|El número de puerto para establecer una conexión con el host. Puede encontrar el número de puerto en la página de visión general de la interfaz de usuario de la instancia de clúster.|25003|
|*user_name*|El nombre de usuario para acceder a la base de datos de destino. Puede utilizar el mismo usuario que crea la base de datos de destino en el [Paso 3](#step3_create_database).|new_user|
|*database_name*|La base de datos puede ser cualquier base de datos en la que el usuario tenga el privilegio CONNECT. La sesión `psql` cambia automáticamente a la base de datos de destino que se ha creado en el [Paso 3](#step3_create_database).|my_database|
|*dump_file*|El archivo `.dump` que se ha creado en el [Paso 1](#step1_create_dump_file). Puede utilizar vías de acceso absolutas o relativas para especificar el archivo.|./pgdump.dump|
{: caption="Tabla 2. Las variables necesarias para restaurar los datos de un archivo de volcado"}

## Qué hacer a continuación
{: #whats_next_migration_postgre}

Después de la migración, puede conectarse al nuevo clúster de base de datos para comprobar si los datos se han migrado satisfactoriamente.
