---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# Introdução ao {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

O {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} é um serviço do {{site.data.keyword.cloud_notm}} que fornece bancos de dados PostgreSQL on demand. Ele oferece uma plataforma flexível e escalável que permite provisionar e gerenciar
de forma rápida e fácil o seu banco de dados de escolha.
{: shortdesc}

Essa oferta {{site.data.keyword.cloud_notm}} fornece clusters de banco de dados PostgreSQL. Cada cluster de banco de dados inclui uma instância de banco de dados principal e dois escravos da instância de banco de dados que fazem backup do principal.

Com o {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, é possível criar clusters de banco de dados no {{site.data.keyword.cloud_notm}},
gerenciar instâncias de banco de dados, administrar usuários de banco de dados, criar e
monitorar bancos de dados.

## Segurança e privacidade de dados
{: #data-security-and-privacy}

A {{site.data.keyword.IBM_notm}} hospeda seus bancos de dados em um ambiente altamente disponível e seguro:
<ul>
<li>As tecnologias subjacentes evitam que a {{site.data.keyword.IBM_notm}} ou um terceiro possa acessar seus dados.
<p>A tecnologia do {{site.data.keyword.IBM_notm}} Secure Service Container protege o sistema por meio de um
ambiente inviolável. O acesso ao sistema é restrito e é ativado somente
por meio de APIs de RESTful bem definidas.</p></li>
<li>Os dados são criptografados em repouso e em andamento.</li>
<li>O hardware do sistema, a configuração do sistema e a configuração do banco de dados asseguram alta disponibilidade.</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## Criando um cluster de banco de dados
{: #creating-a-database-cluster-introduction}

Para criar um cluster de banco de dados, basta inserir os valores necessários na
tela de configuração de serviço do {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} e clicar em **Criar**.

Depois de ter criado o cluster de banco de dados, o {{site.data.keyword.IBM_notm}} fornece um ou mais nomes de host e números
de porta das instâncias de banco de dados criadas. Agora é possível usar essas informações
e as credenciais do usuário especificadas no catálogo para criar e acessar os seus
bancos de dados.

## Gerenciando o cluster de banco de dados
{: #managing-database-cluster-introduction}

Em um cluster de banco de dados, é possível criar bancos de dados, gerenciar as instâncias de banco de dados e
criar ou excluir usuários.

O {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} contém um DBaaS Manager, que gerencia e
planeja de forma inteligente as suas solicitações com base nos recursos disponíveis.

É possível direcionar as solicitações ao DBaaS Manager por meio de uma dessas interfaces:

- A [Interface com o usuário da web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- As [APIs do DBaaS Manager (para gerenciamento de cluster de banco de dados)](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- As APIs do [{{site.data.keyword.cloud_notm}} (para gerenciamento de instância de serviço)](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- O [plug-in da CLI com a ferramenta de CLI do {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## Acessando o banco de dados
{: #accessing-database-introduction}

Após a criação de um banco de dados PostgreSQL, será possível usar pgAdmin ou sua ferramenta PostgreSQL favorita para gerenciar os bancos de dados.

### Antes de começar
{: #accessing-database-introduction-byb}

Para assegurar a transferência de dados segura, obtenha um arquivo de autoridade de certificação (CA)
por meio do painel e copie-o para o diretório apropriado.

### Conectando-se a um banco de dados
{: #accessing-database-introduction-connect}

O painel do {{site.data.keyword.ihsdbaas_postgresql_full}} fornece as informações necessárias para se conectar a um banco de dados.

#### psql shell
{: #accessing-database-introduction-connect-psqlshell}

É possível utilizar este comando:
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
Em
que:
<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> É o nome do host do cluster de banco de dados </dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> É o nome do usuário para o administrador do Banco de dados conforme especificado na tela de criação de serviço </dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> É o número da porta do cluster de banco de dados </dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> É o caminho do arquivo de CA </dd>  
</dl>

**Nota:** o comando `psql` não verificará o certificado de cluster de banco de dados se as opções `sslmode` e `sslrootcert` não forem fornecidas.

### Outras ferramentas
{: #accessing-database-introduction-connect-other}

Para outras ferramentas, como pgAdmin, o {{site.data.keyword.ihsdbaas_postgresql_full}} suporta *validação de certificado do servidor SSL* para conexão com o host. Se necessário, use o arquivo de CA fornecido.
