---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Instâncias do banco de dados
{: #dbaas-webui-database-instances}

## Antes de começar
{: #webui-database-instances-byb}

No painel do {{site.data.keyword.cloud}}{{site.data.keyword.ihsdbaas_postgresql_full}}, selecione a guia Instâncias.

## Iniciando uma instância de banco de dados
{: #webui-start-database-instance}

1. Selecione a instância de banco de dados.
2. Clique nos três pontos na extremidade direita da linha e, em seguida, selecione **Iniciar**.

## Parando uma instância de banco de dados
{: #webui-stop-database-instance}

1. Selecione a instância de banco de dados.
2. Clique nos três pontos na extremidade direita da linha e, em seguida, selecione **Parar**. Se for um Nó primário, também será possível selecionar **Forçar parada**.

## Reiniciando uma instância de banco de dados
{: #webui-restart-database-instance}

1. Selecione a instância de banco de dados.
2. Clique nos três pontos na extremidade direita da linha e, em seguida, selecione **Reiniciar**.

## Fazendo download do log
{: #webui-download-log}

1. Selecione a instância de banco de dados.
2. Selecione a **Data de início** e a **Data de encerramento** para filtrar os logs por horário.
3. Selecione os logs que deseja fazer download clicando na **caixa de seleção** antes do nome do log.
4. Clique no botão **Fazer download**.

## Verificando o status da instância
{: #webui-check-instance-status}

O ponto colorido no painel da instância indica o status da instância. É possível consultar a tabela a seguir para verificar o status da instância.

|Color|Status|Ação|
|-----|------|------|
|Green|A instância está em execução.|É possível parar ou reiniciar a instância.|
|~90 Graus Sentido Horário|A instância está interrompida.|É possível iniciar a instância.|
|Vermelho|A instância está com falha.|É possível consultar [Obtendo ajuda e suporte](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Tabela 1. A cor do status"}
