---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

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

# Roles de usuario y acciones de Identity and Access Management
{: #iam}

El acceso a las instancias de servicio de {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} para los usuarios de su cuenta está controlado por {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Todos los usuarios que acceden al servicio {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} en su cuenta deben tener asignada una política de acceso con un rol de usuario de IAM definido. La política determina qué acciones puede llevar a cabo el usuario en el contexto del servicio o de la instancia que seleccione. Las acciones permitidas se personalizan y definen mediante el servicio de {{site.data.keyword.cloud_notm}} como operaciones que se permiten que se realicen en el servicio. Las acciones se correlacionan entonces con los roles de usuario de IAM.
{: shortdesc}

Las políticas permiten otorgar acceso en distintos niveles. Algunas de las opciones son las siguientes:

* Acceso a todas las instancias del servicio de su cuenta
* Acceso a una instancia de servicio individual en su cuenta
* Acceso a un recurso específico dentro de una instancia

Después de definir el ámbito de la política de acceso, debe asignar un rol que determina el nivel de acceso del usuario. Revise las tablas siguientes que describen las acciones que cada rol permite dentro del servicio {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.

En la tabla siguiente se detallan las acciones que se correlacionan con los roles de gestión de plataforma. Los roles de gestión de plataforma permiten a los usuarios realizar tareas en los recursos de servicio a nivel de plataforma, por ejemplo, asignar acceso de usuario para el servicio, crear o suprimir instancias y enlazar instancias a las aplicaciones.

|Rol de gestión de plataforma|Descripción de acciones|Acciones de ejemplo                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Visor                  |Puede ver las instancias de servicio, pero no las puede modificar|<ul><li>Listar clústeres</li><li>Ver los detalles de un clúster</li></ul>|
|Editor                  |Realizar todas las acciones de plataforma excepto la gestión de la cuenta y la asignación de políticas de acceso|<ul><li>Enlazar un servicio a un clúster</li></ul>|
|Operador                |Realizar acciones de plataforma necesarias para configurar y operar instancias de servicio, como la visualización de un panel de control de servicio|<ul><li>Enlazar un servicio a un clúster</li></ul>|
|Administrador           |Realizar todas las acciones de plataforma basadas en el recurso al que se está asignando este rol, incluida la asignación de políticas de acceso a otros usuarios|<ul><li>Eliminar un clúster</li><li>Crear un clúster</li><li>Actualizar políticas de acceso de usuarios</li><li>Todas las acciones que puede realizar un visor, un editor, y un operador</li></ul>|
{: caption="Tabla 1. Roles de usuario y acciones de IAM"}

Para obtener información sobre la asignación de roles de usuario en la interfaz de usuario, consulte [Gestión del acceso a los recursos](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
