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


# Plug-in da CLI do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #dbaas_cli_plugin}

Use o plug-in da CLI do {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} para criar, excluir
e exibir informações sobre bancos de dados e usuários, para mostrar detalhes sobre clusters,
para iniciar e parar instâncias e para listar e fazer download de arquivos de log.
{:shortdesc}


## Pré-requisito
{: #prerequisites_dbaas_cli_plugin}

- Instale a [CLI do {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started). A CLI do {{site.data.keyword.cloud_notm}} requer o Java SDK 1.7.0. O prefixo para executar comandos usando a CLI do {{site.data.keyword.cloud_notm}} é `ibmcloud`. No terminal, você é notificado quando atualizações para a CLI `ibmcloud` e plug-ins estão disponíveis. Certifique-se de manter sua CLI atualizada para que seja possível usar todos os comandos e sinalizações disponíveis.

- Instale o plug-in da CLI do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}. É possível consultar [Instalando o plug-in da CLI do DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-dbaas-cli-plugin) como referência. Se você desejar visualizar a versão atual de seu plug-in da CLI do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, execute `ibmcloud plugin show dbaas-cli`.


## Comando de uso de plug-in da CLI
{: #plugin_use}

### `ibmcloud dbaas help`
{: #display_list}

Esse comando exibe uma lista de comandos do DBaaS.

```
ibmcloud help dbaas
```
{: pre}


## Comando de cluster
{: #cluster_cmds}

### `ibmcloud dbaas cluster-show`
{: #cluster_show}

Esse comando mostra os detalhes do cluster especificado, incluindo informações sobre cada membro de réplica.  

```
ibmcloud dbaas cluster-show <resource_name>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster. Para localizar o nome do recurso, use o comando {{site.data.keyword.cloud_notm}} `ibmcloud resource service-instances`.</dd>
</dl>

## Comandos do banco de dados
{: #db_cmds}

### `ibmcloud dbaas database-create`
{: #db_create}

Esse comando cria um banco de dados e, opcionalmente, uma coleção.

```
ibmcloud dbaas database-create <resource_name> <database_name> [<collection>]
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>*database_name*</dt>
<dd>O nome do banco de dados a ser criado.</dd>
<dt>*coleção*</dt>
<dd>(Opcional) O nome da coleção a ser criada.</dd>
</dl>


### `ibmcloud dbaas database-delete`
{: #db_delete}

Esse comando exclui um banco de dados. Não exclua um banco de dados se esse banco de dados for criado por credencial e se essa credencial ainda estiver em uso.

```
ibmcloud dbaas database-delete <resource_name> <database_name>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>*database_name*</dt>
<dd>O nome do banco de dados a ser excluído.</dd>
</dl>


### `ibmcloud dbaas databases-list`
{: #db_list}

Esse comando lista todos os bancos de dados no cluster especificado.

```
ibmcloud dbaas databases-list <resource_name>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
</dl>


## Comandos de Usuário do banco de dados
{: #user_cmds}

### `ibmcloud dbaas user-create`
{: #user_create}

Esse comando cria um usuário do banco de dados.

```
ibmcloud dbaas user-create <resource_name> <username> <password> [<db_name> [<db_name> [...]]]
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>*username*</dt>
<dd>O nome de usuário a ser designado ao usuário do banco de dados que está sendo criado.</dd>
<dt>*db_name*</dt>
<dd>(Opcional) Isso especifica um banco de dados para o qual o usuário terá acesso de leitura e gravação.</dd>
</dl>


### `ibmcloud dbaas user-delete`
{: #user_delete}

Esse comando exclui um usuário do banco de dados. Não exclua um usuário do banco de dados se esse usuário do banco de dados for criado por credencial e se essa credencial ainda estiver em uso.

```
ibmcloud dbaas user-delete <resource_name> <username>
```
**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>*username*</dt>
<dd>O nome de usuário do usuário do banco de dados que está sendo excluído.</dd>
</dl>

### `ibmcloud dbaas users-list`
{: #user_list}

Esse comando lista todos os usuários do banco de dados.

```
ibmcloud dbaas users-list <resource_name>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
</dl>


### `ibmcloud dbaas user-show`
{: #user_show}

Esse comando mostra detalhes sobre um usuário do banco de dados.

```
ibmcloud dbaas user-show <resource_name> <username>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>*username*</dt>
<dd>O nome de usuário do usuário do banco de dados que está sendo mostrado.</dd>
</dl>


## Comandos da instância
{: #instance_cmds}

Para usar qualquer um dos comandos de instância listados aqui, você precisa saber o `instance_id`. Para obter um `instance_id`, primeiro use o comando `ibmcloud` a seguir para listar os nomes dos grupos de recursos de instância de serviço sob sua conta, em seguida, use o comando [`cluster_show`](#cluster_show) para obter o `instance_id`.

```
ibmcloud resource service-instances
```
{: pre}


### `ibmcloud dbaas instance-restart`
{: #instance_restart}

Esse comando reinicia uma instância em execução.

```
ibmcloud dbaas instance-restart <resource_name> <instance_id>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>* instance_id *</dt>
<dd>O ID da instância.</dd>
</dl>


### `ibmcloud dbaas instance-start`
{: #instance_start}

Esse comando inicia uma instância interrompida.

```
ibmcloud dbaas instance-start <resource_name> <instance_id>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>* instance_id *</dt>
<dd>O ID da instância.</dd>
</dl>


### `ibmcloud dbaas instance-stop`
{: #instance_stop}

Esse comando para uma instância (um membro de replicação do cluster).

```
ibmcloud dbaas instance-stop <resource_name> <instance_id>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>* instance_id *</dt>
<dd>O ID da instância.</dd>
</dl>


## Comandos de log
{: log_cmds}

### `ibmcloud dbaas log-get`
{: #log_get}

Esse comando faz download de um arquivo de log de uma instância.

```
ibmcloud dbaas log-get <resource_name> <instance_id> <filename>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>* instance_id *</dt>
<dd>O ID da instância.</dd>
<dt>*filename*</dt>
<dd>O nome do arquivo de log a ser transferido por download. Para determinar o nome do arquivo do arquivo de log que desejar fazer download, use o comando [ibmcloud dbaas logs-list](#log_list).</dd>
</dl>

### `ibmcloud dbaas logs-list`
{: #log_list}

Esse comando lista todos os arquivos de log em uma instância. É possível usar qualquer um dos nomes de arquivos listados como entrada para o comando [ibmcloud dbaas log-get](#log_get).

```
ibmcloud dbaas logs-list <resource_name> <instance_id>
```
{: pre}

**Opções de comandos**

<dl>
<dt>*resource_name*</dt>
<dd>O nome do recurso de cluster.</dd>
<dt>* instance_id *</dt>
<dd>O ID da instância.</dd>
</dl>
