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

# Migrando bancos de dados do {{site.data.keyword.postgresql}} para o {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

Se você estiver usando bancos de dados do {{site.data.keyword.postgresql}} e desejar migrar para o {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, leia este tópico para obter detalhes. Não importa em que local os seus bancos de dados do {{site.data.keyword.postgresql}} estão hospedados, desde que a plataforma forneça serviços de banco de dados do {{site.data.keyword.postgresql}}.
{: shortdesc}

## Antes de começar
{: #migration_postgre_before_begin}

Para usar os comandos do {{site.data.keyword.postgresql}} para concluir a migração, é necessário fazer download e instalar o {{site.data.keyword.postgresql}} em sua máquina primeiro. Para obter mais informações, consulte o [website do {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Etapa 1: Crie um arquivo de dump para restaurar os bancos de dados originais
{: #step1_create_dump_file}

Use o comando `pg_dump` a seguir para criar um arquivo dump que contenha os bancos de dados que você deseja restaurar.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

A tabela a seguir ilustra as variáveis usadas no comando.

|Variáveis|Descrição|Exemplo|
|---------|-----------|-------|
|*host_name*|O servidor remoto que hospeda os bancos de dados originais. É necessário se conectar ao host para obter os dados. Se seus bancos de dados estiverem implementados em uma instância do {{site.data.keyword.ihsdbaas_full}} Beta, será possível localizar o endereço do host na página de visão geral da IU da instância do cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|O número da porta para estabelecer uma conexão com o host. Se seus bancos de dados estiverem implementados em uma instância do {{site.data.keyword.ihsdbaas_full}} Beta, será possível localizar a porta na página de visão geral da IU da instância do cluster.|25050|
|*user_name*|O nome de usuário para acessar os bancos de dados originais. O usuário precisa ter privilégio CONNECT no banco de dados e privilégio SELECT para as tabelas.|my_user|
|*database_name*|O nome do banco de dados que você deseja migrar.|my_database|
|*dump_file*|O arquivo `.dump` para armazenar os dados originais. É possível usar caminhos relativos ou absolutos para especificar o arquivo.|./pgdump.dump|
{: caption="Tabela 1. As variáveis que são necessárias para criar um arquivo de dump"}

Se deseja saber mais sobre os privilégios do usuário, é possível consultar a [documentação do {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external} para obter mais informações.

## Etapa 2: Criar uma nova instância de serviço no {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Antes de restaurar os dados, é necessário criar uma nova instância de serviço no {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} como o cluster de banco de dados de destino. É possível usar uma das maneiras a seguir para criar uma nova instância de serviço:
- [A interface com o usuário da web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- [As APIs do DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- [O plug-in da CLI com a CLI do {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

Quando você criar a nova instância de serviço, será necessário configurar o nome do cluster, o nome do administrador e a senha. Eles não devem ser necessariamente os mesmos que os de sua instância original. Isso não afeta a migração. Depois que a migração for concluída, os bancos de dados serão designados ao novo administrador.

## Etapa 3: Criar bancos de dados na nova instância de serviço
{: #step3_create_database}

Depois de criar a nova instância de serviço, é necessário criar novos bancos de dados. Os bancos de dados devem ter o mesmo nome dos originais. O usuário precisa ter o privilégio CREATE e não deve ser o mesmo do usuário que cria o arquivo dump. É possível executar a tarefa usando:
- [A interface com o usuário da web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- [As APIs do DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- [O plug-in da CLI com a CLI do {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

É possível usar as formas a seguir para criar novos usuários:[A interface com o usuário da web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [As APIs do DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [O plug-in da CLI com a CLI do {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create) e o [comando {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Etapa 4: Restaurar os dados do arquivo dump para uma nova instância de serviço
{: #step4_restore_data}

Use o comando `psql` para restaurar os dados do arquivo dump criados na [Etapa 1](#step1_create_dump_file).

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

A tabela a seguir ilustra as variáveis usadas no comando.

|Variáveis|Descrição|Exemplo|
|---------|-----------|-------|
|*host_name*|O servidor do gerenciador DBaaS que hospeda o cluster de destino. É possível localizar o endereço do host na página de visão geral da IU da instância do cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|O número da porta para estabelecer uma conexão com o host. É possível localizar o endereço do número da porta na página de visão geral da IU da instância do cluster.|25003|
|*user_name*|O nome de usuário para acessar o banco de dados de destino. É possível usar o mesmo usuário que cria o banco de dados de destino na [Etapa 3](#step3_create_database).|new_user|
|*database_name*|O banco de dados pode ser qualquer banco de dados ao qual o usuário tenha privilégio CONNECT. A sessão `psql` alterna automaticamente para o banco de dados de destino criado na [Etapa 3](#step3_create_database).|my_database|
|*dump_file*|O arquivo `.dump` que você cria na [Etapa 1](#step1_create_dump_file). É possível usar caminhos relativos ou absolutos para especificar o arquivo.|./pgdump.dump|
{: caption="Tabela 2. As variáveis que são necessárias para restaurar os dados de um arquivo de dump"}

## O que Vem Depois
{: #whats_next_migration_postgre}

Após a migração, será possível conectar-se ao novo cluster de banco de dados para verificar se os dados foram migrados com êxito.
