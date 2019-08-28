---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Instâncias de serviço
{: #dbaas_webui_service}

## Criando uma instância de serviço
{: #dbaas_webui_create_service}

<ol>
<li>Clique na entrada no catálogo {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} para abrir a tela de criação de serviço.</li>
<li>Insira os valores necessários.
  <dl>
    <dt>Nome do serviço:</dt>
    <dd>Um nome para o serviço de banco de dados.</dd>

    <dt>Escolher uma região/local no qual implementar:</dt>
    <dd>Selecione o data center no qual o banco de dados será localizado.</dd>

    <dt>Selecionar um grupo de recursos:</dt>
    <dd>Se nenhum grupo de recursos for selecionável, será possível criar um no painel do {{site.data.keyword.cloud_notm}}.</dd>

    <dt>Tags:</dt>
    <dd>As identificações são opcionais. Consulte [Recursos de identificação](/docs/resources?topic=resources-tag#tag) para obter mais informações sobre identificação.</dd>

    <dt>Nome do Cluster / Replicaset:</dt>
    <dd>Um nome para a instância de serviço.</dd>

    <dt>Nome Admin do Banco de Dados:</dt>
    <dd>Um ID do usuário para o administrador de banco de dados (DBA).
    <p>**Nota:** o administrador de banco de dados não tem a autoridade SUPERUSER. As autoridades do administrador de banco de dados são limitadas a INHERIT, CREATEROLE, CREATEDB, LOGIN e REPLICATION.</p></dd>

    <dt>Senha Admin do Banco de Dados:</dt>
    <dd>
    <p>Uma senha para o ID de usuário do DBA. É necessário criar uma senha forte com os atributos a seguir:
      <ul>
        <li>mínimo de **15 caracteres** de comprimento</li>
        <li>pelo menos **um caractere maiúsculo**;</li>
        <li>pelo menos **um caractere minúsculo**;</li>
        <li>pelo menos **um número**;</li>
        <li>não conter nome de usuário.</li>
      </ul>
    </p>
    </dd>

    <dt>Confirmar senha:</dt>
    <dd>Confirme a senha para o ID de usuário do DBA.</dd>

    <dt>Contrato de Licença:</dt>
    <dd>Após ler o contrato de licença, marque a caixa para confirmar o seu contrato.</dd>

    <dt>Planos de precificação:</dt>
    <dd>Os planos de precificação oferecem categorias de precificação diferentes para bancos de dados do tipo PostgreSQL. Escolha aquele que melhor atender às suas necessidades.</dd>
  </dl>
</li>
<li>Clique em
**Criar**.
<p>Após uma janela de diálogo informar que leva tempo para implementar o serviço, o painel Lista de recursos do {{site.data.keyword.cloud_notm}} será exibido. É possível ver a instância de serviço que você criar na seção **Serviços** na lista. Quando o status do serviço for **Provisionado**, a instância estará pronta para uso.</p>
</li>

<li>Selecione o serviço para exibir o painel do {{site.data.keyword.cloud_notm}}{{site.data.keyword.ihsdbaas_postgresql_full}}.</li>
</ol>

Para fortalecer ainda mais a segurança, sugere-se que você atualize a **senha do administrador do banco de dados** imediatamente após a instância de serviço ser provisionada. É necessário seguir as mesmas regras que foram mencionadas anteriormente para configurar a nova senha.
{: note}

## Listando todas as instâncias de serviço
{: #dbaas_webui_list_service}

Abra o painel do {{site.data.keyword.cloud_notm}} para exibir uma lista de instâncias de serviço criadas:

<ol>
	<li>clique no botão de três barras na parte superior do console.</li>
	<li>Selecione Painel.</li>
	<li>Selecione Serviços.</li>
</ol>

## Mostrando informações detalhadas de uma instância de serviço
{: #dbaas_webui_show_detail_service}

1. Clique no nome da instância de destino para exibir o painel de serviço.
2. Selecione **Gerenciar** na barra de navegação esquerda e será possível ver as informações gerais na página da guia **Visão geral**.
3. Selecione a guia **Instâncias** para exibir as informações detalhadas.


## Excluindo uma instância de serviço
{: #dbaas_webui_delete_service}

1. Exiba a lista de recursos do {{site.data.keyword.cloud_notm}} clicando em **Menu de navegação > Lista de recursos**.
2. Abra o twister **Serviço** para exibir as suas instâncias de serviço.
3. Selecione a instância de serviço que você deseja excluir.
4. Clique nos três pontos à direita.
5. Clique em  ** Excluir **.
