---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Monitoramento do banco de dados
{: #dbaas-webui-database-monitor}

Depois de ter ativado o monitoramento do banco de dados, será possível visualizar as métricas do banco de dados usando o Grafana.
{: shortdesc}

## Antes de começar
{: #webui-database-monitoring-byb}

1.  Certifique-se de ter acesso a uma organização do Cloud Foundry e a um espaço em Dallas (us-south).
    Para obter informações sobre como obter esse acesso, consulte [Gerenciando o acesso do Cloud Foundry](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}.

2.  Certifique-se de que todas as instâncias do cluster do banco de dados estejam em execução.

3.  No painel do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, selecione a guia Monitoramento.

## Ativando o monitoramento do banco de dados
{: #webui-enable-database-monitoring}

No caso de a mensagem **O monitoramento está desativado** ser exibida na guia Monitoramento:

1. Clique em **Ativar**.
2. Na janela Ativar Monitoramento, selecione a sua organização e o seu espaço e, em seguida, clique em **Enviar**.


## Visualizando métricas do banco de dados
{: #webui-view-database-metrics}

Há duas maneiras de visualizar as métricas no Grafana:

- Copie o link exibido e, em seguida, abra uma nova guia ou janela e cole o link no navegador.
- Clique em **Visualizar no Grafana**.

Para exibir as métricas em um novo painel no Grafana, selecione o ícone superior esquerdo do Grafana, em seguida, selecione **Painéis > Novo**.
Pode demorar um pouco até que o seu ID do cluster de banco de dados e os IDs da instância sejam exibidos e você pode ter que recarregar o painel.

Para obter mais informações sobre como usar o Grafana, consulte [Monitoramento do {{site.data.keyword.cloud_notm}}](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started).
