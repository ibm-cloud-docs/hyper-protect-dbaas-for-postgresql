---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# Eventos do {{site.data.keyword.cloudaccesstrailshort}}
{: #activity-tracker-events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e os aplicativos interagem com o {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para saber como provisionar o serviço do {{site.data.keyword.cloudaccesstrailshort}}, consulte a [documentação do {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started) para obter mais informações. Como o serviço do {{site.data.keyword.ihsdbaas_postgresql_full}} atualmente está disponível no data center de Dallas, selecione **us-south** como a região de captura de logs.

## Lista de eventos
{: #list-activity-tracker-events}

A tabela a seguir lista as ações que geram um evento:

| Ação                 | Descrição                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | Criar um cluster de banco de dados                 |
| `cluster.delete` | Excluir um cluster de banco de dados                 |
| `database.create` | Criar um banco de dados                  |
| `database.delete` | Excluir um banco de dados                  |
| `user.create`     | Criar um usuário do banco de dados                    |
| `user.delete`     | Excluir um usuário do banco de dados                    |
| `instance.start` | Iniciar uma instância de serviço de banco de dados         |
| `instance.stop`  | Parar uma instância de serviço de banco de dados          |
| `instance.restart`  | Reiniciar uma instância de serviço de banco de dados          |
| `log.get`       | Fazer download de um arquivo de log |
{: caption="Tabela 1. Ações que geram eventos do  {{site.data.keyword.cloudaccesstrailfull_notm}}"}

Para o evento de `cluster.create` e `cluster.delete`, o serviço do {{site.data.keyword.cloudaccesstrailfull_notm}} não registra o nome da conta e o endereço IP do usuário que executa a ação. O valor de `initiator.name` e `host.address` no log indica o ID do serviço do Cloud Broker e o endereço IP do Cloud Broker respectivamente.
{: note}

## Onde visualizar os eventos
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no
{{site.data.keyword.cloudaccesstrailshort}} **domínio de contas** disponível na região do
{{site.data.keyword.cloud_notm}} na qual eles são gerados.
