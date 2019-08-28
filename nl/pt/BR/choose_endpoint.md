---

copyright:
  years: 2019
lastupdated: "2019-06-20"

keywords: service endpoint, ibmcloud regions

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Escolhendo um terminal em serviço para efetuar login no
{: #choose-endpoint}

O {{site.data.keyword.cloud}} fornece muitos terminais em serviço em várias regiões geográficas nas quais é possível efetuar login.
Para localizar um terminal em serviço próximo à sua localização geográfica, use o comando `ibmcloud regions`, conforme mostrado neste exemplo:

<pre><code class="hljs">~$ ibmcloud regions
Listing regions...

Name       Display name
au-syd     Sydney
jp-tok     Tokyo
eu-de      Frankfurt
eu-gb      London
us-south   Dallas
us-east    Washington DC

</code></pre>

Atualmente, o {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} é suportado somente na região **us-south**.
{: note}

Para efetuar login em um terminal em serviço do {{site.data.keyword.cloud_notm}}, siga estas etapas:

1. Insira o comando `ibmcloud login`, indicando que você está usando Conexão única (SSO) e especificando a URL do terminal no qual você deseja efetuar login, conforme mostrado neste exemplo:

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   O sistema exibe uma URL para uma página da web que fornece a você uma senha descartável.

2. Copie a URL de seu console do sistema e cole-a em seu navegador da web.

   O sistema exibe a página **{{site.data.keyword.cloud_notm}} One time passcode**.

3. Copie a senha da página da web e cole-a em sua linha de comandos do console do sistema.

   A senha não é exibida na linha de comandos. Quando a senha for autenticada, você receberá uma mensagem **OK** indicando que o login foi efetuado.

Para obter mais informações sobre os parâmetros do comando `ibmcloud login`, é possível consultar a [Referência da CLI do {{site.data.keyword.cloud_notm}}] (/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login).

Ao usar o {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, pode ser necessário criar espaços em mais de uma região e alternar entre as regiões por meio do comando `ibmcloud target`. Para obter mais informações, consulte [Incluindo organizações e espaços](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)
e [Comandos gerais da CLI (ibmcloud)](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target).
{: note}
