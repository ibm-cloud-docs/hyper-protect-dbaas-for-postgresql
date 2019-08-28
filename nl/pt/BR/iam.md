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

# Funções e ações do Identity and Access Management
{: #iam}

O acesso às instâncias de serviço do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} para usuários em sua conta é controlado pelo {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Cada usuário que acessa o serviço {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} em sua conta deve ser designado a uma política de acesso com uma função do IAM definida. A política determina quais ações um usuário pode executar dentro do contexto do serviço ou instância que você selecionar. As ações permitidas são customizadas e definidas pelo serviço {{site.data.keyword.cloud_notm}} como operações que têm permissão para serem executadas no serviço. As ações são então mapeadas para as funções de usuário do IAM.
{: shortdesc}

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem o seguinte:

* Acesso em todas as instâncias do serviço em sua conta
* Acesso a uma instância de serviço individual em sua conta
* Acesso a um recurso específico dentro de uma instância

Após definir o escopo da política de acesso, você designa uma função que determina o nível de acesso do usuário. Revise as tabelas a seguir que descrevem quais ações cada função permite dentro do serviço do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.

A tabela a seguir detalha as ações que são mapeadas para funções de gerenciamento de plataforma. As funções de gerenciamento da plataforma permitem que os usuários executem tarefas nos recursos de serviço no nível de plataforma, por exemplo, designar acesso de usuário para o serviço, criar ou excluir instâncias e ligar instâncias a aplicativos.

|Função de gerenciamento da plataforma|Descrição das ações|Exemplo de ações                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Visualizador                  |Pode visualizar instâncias de serviço, mas não pode modificá-las|<ul><li>Listar clusters</li><li>Visualizar detalhes para um cluster</li></ul>|
|Aplicativos                  |Executar todas as ações da plataforma, exceto para gerenciar a conta e designar políticas de acesso|<ul><li>Ligar um serviço a um cluster</li></ul>|
|Operador                |Executar ações de plataforma necessárias para configurar e operar instâncias de serviço, como visualizar o painel de um serviço|<ul><li>Ligar um serviço a um cluster</li></ul>|
|Administrador           |Executar todas as ações da plataforma com base no recurso para o qual essa função está sendo designada, incluindo a designação de políticas de acesso a outros usuários|<ul><li>Remover um cluster</li><li>Criar um cluster</li><li>Atualizar políticas de acesso de usuário</li><li>Todas as ações que um visualizador, um editor e um operador podem executar</li></ul>|
{: caption="Tabela 1. Funções e ações do usuário do IAM"}

Para obter informações sobre como designar funções de usuário na IU, consulte [Gerenciando acesso aos recursos](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
