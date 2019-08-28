---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: service instance, ibmcloud resource

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Creación de una instancia de servicio
{: #dbaas_cli_create_service}

Para crear una instancia de servicio, utilice el mandato `ibmcloud resource service-instance-create`, como se muestra en el siguiente ejemplo. En Windows, se recomienda utilizar un terminal Bash, como Cygwin o Git Bash, para especificar el mandato.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Donde los parámetros tienen las siguientes definiciones:

| Parámetro        |  Definición                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  El nombre de la instancia de servicio (sustituir por un nombre de su propia elección). |
| *hyperp-dbaas-postgresql* | El nombre del catálogo de {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | El nombre del plan. Los planes disponibles son: **postgresql-small**, **postgresql-medium** y **postgresql-large**.  (**Nota:** los nombres de los planes distinguen entre mayúsculas y minúsculas.) |
| *us-south*            | La ubicación en la que se colocara la nueva base de datos. (**Nota:** actualmente solo **us-south** soporta {{site.data.keyword.ihsdbaas_postgresql_full}}.) |
| *-p*               | Una serie JSON válida, que debe contener los parámetros de la tabla siguiente. |

<table>
  <tr>
    <th>parámetro -p</th>
    <th>Definición</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>El nombre del clúster de la base de datos.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>El nombre de usuario del administrador de la base de datos que se va a crear.</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>La contraseña de usuario del administrador de la base de datos que se va a crear. Tiene que crear una contraseña fuerte con los siguientes atributos:
        <ul>
          <li>mínimo de **15 caracteres** de longitud</li>
          <li>al menos **un carácter en mayúscula**</li>
          <li>al menos **un carácter en minúscula**</li>
          <li>al menos **un número**</li>
          <li>no debe contener el nombre de usuario</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>La misma contraseña.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>Un valor de **agreed** indica aceptación del acuerdo de licencia, que es necesario para utilizar {{site.data.keyword.ihsdbaas_postgresql_full}}.</td>
  </tr>
</table>

Después de especificar el mandato, el estado de la nueva instancia de servicio puede aparecer temporalmente como **inactivo**, como se muestra en este ejemplo:

```
Creating service instance MYDBaaSIns03 in resource group default of account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Service instance MYDBaaSIns03 was created.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753
Location:         us-south
State:            inactive
Type:             service_instance
Sub Type:
Created at:       2019-06-03T06:17:13Z
Updated at:       2019-06-03T06:17:13Z
Last Operation:
                  Status       create in progress
                  Updated At   2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

Esto se debe a que el clúster tarda unos minutos en prepararse. Para obtener una actualización del estado del clúster, utilice el mandato `ibmcloud resource service-instances`, como se muestra en este ejemplo:

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

Para reforzar aún más la seguridad, se recomienda actualizar la **contraseña de administración de la base de datos** inmediatamente después de que se suministre la instancia de servicio. Debe seguir las mismas reglas mencionadas anteriormente para establecer la nueva contraseña.
{: note}
