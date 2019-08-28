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


# Fazendo backup e restaurando seus bancos de dados usando o {{site.data.keyword.cos_full_notm}}
{: #backup_postgresql_databases}

O serviço {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} aciona automaticamente um backup completo do seu banco de dados a cada 24 horas. Esses backups criptografados estão disponíveis para os últimos 7 dias e estão disponíveis redundantemente no armazenamento local em todas as Zonas de disponibilidade da região suportada.
{: shortdesc}

Se você deseja aumentar seus recursos de recuperação de desastre e fazer backup dos dados fora da região suportada, é possível usar o [serviço {{site.data.keyword.cos_full_notm}}](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} para armazenar seus dados em uma região diferente consultando as etapas a seguir.

## Antes de começar
{: #backup_postgresql_before_begin}

Para usar os comandos do {{site.data.keyword.postgresql}} para concluir o backup, primeiro é necessário fazer download do {{site.data.keyword.postgresql}} e instalá-lo em sua máquina. Para obter mais informações, consulte o [website do {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Etapa 1: criar um arquivo dump para fazer backup dos bancos de dados originais
{: #step1_create_dump_file_backup_postgresql}

Use o comando `pg_dump` a seguir para criar um arquivo dump que contenha os bancos de dados cujo backup você deseja fazer.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

A tabela a seguir ilustra as variáveis usadas no comando.

|Variáveis|Descrição|Exemplo|
|---------|-----------|-------|
|*host_name*|O servidor remoto que hospeda os bancos de dados originais. É necessário se conectar ao host para obter os dados. É possível localizar o endereço do host na página de visão geral da IU da instância do cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|O número da porta para estabelecer uma conexão com o host. É possível localizar a porta na página de visão geral da IU da instância de cluster.|25050|
|*user_name*|O nome de usuário para acessar os bancos de dados originais. O usuário precisa ter privilégio CONNECT no banco de dados e privilégio SELECT para as tabelas.|my_user|
|*database_name*|O nome do banco de dados cujo backup você deseja fazer.|my_database|
|*dump_file*|O arquivo `.dump` para armazenar os dados originais. É possível usar caminhos relativos ou absolutos para especificar o arquivo.|./pgdump.dump|
{: caption="Tabela 1. As variáveis que são necessárias para criar um arquivo de dump"}

Se deseja saber mais sobre os privilégios do usuário, é possível consultar a [documentação do {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external} para obter mais informações.

## Etapa 2: criar uma nova instância do {{site.data.keyword.cos_full_notm}}
{: #step2_create_object_storage_backup_postgresql}

É necessário criar a instância em uma região diferente daquela na qual a instância de serviço do {{site.data.keyword.ihsdbaas_postgresql_full}} está hospedada atualmente. É possível consultar as etapas a seguir:

1. [criar uma nova instância do Cloud {{site.data.keyword.cos_short}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Criar um depósito](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) em uma região diferente.
3. [Criar uma credencial de serviço](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) e salvar `access_key_id` e `secret_access_key` para uso posterior.
4. Instalar um cliente S3.
5. Use o cliente S3 e as chaves de acesso para se conectar ao terminal do Cloud {{site.data.keyword.cos_short}} do depósito que você criou anteriormente.
6. Use o cliente S3 para [fazer upload do arquivo de backup {{site.data.keyword.postgresql}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) que você criar na [Etapa 1](#step1_create_dump_file_backup_postgresql) para o depósito.

É possível consultar a [documentação do {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started) para obter mais informações.

Após concluir essa etapa, você faz backup dos seus dados com sucesso em uma instância do Cloud {{site.data.keyword.cos_short}} em uma região diferente. Se desejar restaurar os dados da instância do Cloud {{site.data.keyword.cos_short}} para uma instância do {{site.data.keyword.ihsdbaas_postgresql_full}}, leia a Etapa 3 a seguir para obter detalhes.

## Etapa 3: Restaurar os dados da instância do Cloud {{site.data.keyword.cos_short}} para uma instância do {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step3_restore_data_from_cos_postgresql}

Primeiro, é necessário fazer download do arquivo de backup do depósito do Cloud {{site.data.keyword.cos_short}} para sua máquina local e, em seguida, usar o comando `psql` para restaurar os dados.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

A tabela a seguir ilustra as variáveis usadas no comando.

|Variáveis|Descrição|Exemplo|
|---------|-----------|-------|
|*host_name*|O servidor do gerenciador DBaaS que hospeda o cluster de destino. É possível localizar o endereço do host na página de visão geral da IU da instância do cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|O número da porta para estabelecer uma conexão com o host. É possível localizar o endereço do número da porta na página de visão geral da IU da instância do cluster.|25003|
|*user_name*|O nome de usuário para acessar o banco de dados de destino.|new_user|
|*database_name*|O banco de dados pode ser qualquer banco de dados ao qual o usuário tenha privilégio CONNECT. A sessão `psql` alterna automaticamente para o banco de dados de destino para o qual os dados serão restaurados.|my_database|
|*dump_file*|O arquivo `.dump` que você faz download por meio do seu depósito do Cloud {{site.data.keyword.cos_short}}. É possível usar caminhos relativos ou absolutos para especificar o arquivo.|./pgdump.dump|
{: caption="Tabela 2. As variáveis que são necessárias para restaurar os dados de um arquivo de dump"}

## O que Vem Depois
{: #whats_next_backup_postgresql}

Após a [Etapa 3](#step3_restore_data_from_cos_postgresql), é possível se conectar ao cluster do banco de dados para verificar se os dados foram restaurados com sucesso.
