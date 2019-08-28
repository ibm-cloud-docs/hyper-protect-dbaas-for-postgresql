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


# Création d'une instance de service
{: #dbaas_cli_create_service}

Pour créer une instance de service, utilisez la commande `ibmcloud resource service-instance-create`, comme illustré dans l'exemple ci-après. Sous Windows, il est recommandé d'utiliser un terminal Bash, tel que Cygwin ou Git Bash, pour entrer la commande.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Où les définitions des paramètres sont les suivantes :

| Paramètre        |  Définition                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  Nom de l'instance de service (remplacez cette valeur par un nom de votre choix). |
| *hyperp-dbaas-postgresql* | Nom de catalogue de {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | Nom de plan. Les plans disponibles sont : **postgresql-small**, **postgresql-medium** et **postgresql-large**.  (**Remarque :** les noms de plan sont sensibles à la casse.) |
| *us-south*            | Futur emplacement de votre nouvelle base de données. (**Remarque :** actuellement, seule la région **us-south** prend en charge {{site.data.keyword.ihsdbaas_postgresql_full}}.) |
| *-p*               | Chaîne JSON valide, qui doit contenir les paramètres présentés dans le tableau suivant : |

<table>
  <tr>
    <th>Paramètre -p</th>
    <th>Définition</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>Nom de votre cluster de base de données.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>Nom d'utilisateur de l'administrateur de la base de données à créer.</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>Mot de passe de l'administrateur de la base de données à créer. Vous devez créer un mot de passe fort avec les attributs suivants :
        <ul>
          <li>minimum de **15 caractères**</li>
          <li>au moins **un caractère majuscule**</li>
          <li>au moins **un caractère minuscule**</li>
          <li>au moins **un nombre**</li>
          <li>ne contient pas de nom d'utilisateur</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>Même mot de passe.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>La valeur **agreed** indique que le contrat de licence est accepté, ce qui est obligatoire pour pouvoir utiliser {{site.data.keyword.ihsdbaas_postgresql_full}}.</td>
  </tr>
</table>

Après que vous avez entré la commande, l'instance de service peut prendre temporairement l'état **inactive**, comme illustré dans cet exemple :

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

Cela est dû au fait que la préparation du cluster prend quelques minutes. Pour obtenir une mise à jour de l'état du cluster, utilisez la commande `ibmcloud resource service-instances`, comme illustré dans l'exemple suivant :

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

Pour renforcer la sécurité, il est conseillé de mettre à jour le **mot de passe de l'administrateur de la base de données** immédiatement après la mise à disposition de l'instance de service. Vous devez suivre les mêmes règles que celles mentionnées précédemment pour définir le nouveau mot de passe.
{: note}
