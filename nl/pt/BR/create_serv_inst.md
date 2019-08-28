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


# Criando uma instância de serviço
{: #dbaas_cli_create_service}

Para criar uma instância de serviço, use o comando `ibmcloud resource service-instance-create`, conforme mostrado no exemplo a seguir. No Windows, é recomendado usar um terminal Bash, como Cygwin ou Git Bash, para inserir o comando.

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

Em que os parâmetros têm as definições a seguir:

| Parâmetro        |  Definição                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  O nome da instância de serviço (substitua por um nome de sua própria escolha). |
| *hyperp-dbaas-postgresql* | O nome do catálogo do {{site.data.keyword.ihsdbaas_postgresql_full}}. |
| *postgresql-small*  | O nome do plano. Os planos disponíveis são:**postgresql-small**, **postgresql-medium** e **postgresql-large**.  (**Nota:** os nomes de plano fazem distinção entre maiúsculas e minúsculas.) |
| *us-south*            | O local no qual o seu novo banco de dados será localizado. (**Nota:** atualmente apenas **us-south** suporta o {{site.data.keyword.ihsdbaas_postgresql_full}}.) |
| *-p*               | Uma sequência de JSON válida, que deve conter os parâmetros na tabela a seguir. |

<table>
  <tr>
    <th>parâmetro -p</th>
    <th>Definição</th>
  </tr>
  <tr>
    <td>*nome*</td>
    <td>O nome de seu cluster de banco de dados.</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>O nome do usuário do administrador do banco de dados a ser criado.</td>
  </tr>
  <tr>
    <td>*senha*</td>
    <td>
      <p>A senha do usuário do administrador do banco de dados a ser criada. É necessário criar uma senha forte com os atributos a seguir:
        <ul>
          <li>mínimo de **15 caracteres** de comprimento</li>
          <li>pelo menos **um caractere maiúsculo**;</li>
          <li>pelo menos **um caractere minúsculo**;</li>
          <li>pelo menos **um número**;</li>
          <li>não conter nome de usuário.</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>A mesma senha.</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>Um valor de **agreed** indica a aceitação do contrato de licença, que é necessário para usar o {{site.data.keyword.ihsdbaas_postgresql_full}}.</td>
  </tr>
</table>

Após você inserir o comando, o estado da nova instância de serviço pode aparecer temporariamente como **inativo**, conforme mostrado neste exemplo:

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

Isso ocorre porque leva alguns minutos para preparar o cluster. Para obter uma atualização do status do cluster, use o comando `ibmcloud resource service-instances`, conforme mostrado neste exemplo:

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

Para fortalecer ainda mais a segurança, sugere-se que você atualize a **senha do administrador do banco de dados** imediatamente após a instância de serviço ser provisionada. É necessário seguir as mesmas regras que foram mencionadas anteriormente para configurar a nova senha.
{: note}
