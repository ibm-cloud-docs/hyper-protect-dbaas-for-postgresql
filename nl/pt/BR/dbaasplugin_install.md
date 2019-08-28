---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: DBaaS CLI, Python runtime

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Instalando o plug-in da CLI do DBaaS
{: #install-dbaas-cli-plugin}

Para acessar um conjunto completo de comandos do DBaaS ao usar a CLI do {{site.data.keyword.cloud}},
deve-se instalar os componentes a seguir
(consulte [Instruções](#dbaas_cli_instr)):

- Tempo de execução Python (2.7.15 é recomendado; 3.x **não** é suportado)
- Sistema de gerenciamento de pacote do Python Pip
- Biblioteca de Solicitações do Python
- Plug-in da CLI do DBaaS

## Instruções para instalar os componentes da CLI do DBaaS (por sistema operacional)
{: #dbaas_cli_instr}

- [No Linux](#dbaas_cli_linux)
- [No MacOS](#dbaas_cli_macos)
- [No Windows](#dbaas_cli_windows)

### No Linux:
{: #dbaas_cli_linux}

1. A maioria das distribuições do Linux tem o Python e o Pip pré-instalados. Se as suas não têm, use esses comandos para instalá-los:

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Para instalar a biblioteca de Solicitações do Python, use este comando:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Para instalar o plug-in da CLI do DBaaS, use este comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Para confirmar se o plug-in da CLI do DBaaS foi instalado corretamente, use este comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   O sistema exibe `dbaas` na lista de comandos disponíveis.

### No MacOS:
{: #dbaas_cli_macos}

1. Se você ainda não tiver o Python, faça download e instale-o seguindo estas instruções:

    a. Acesse o website do Python nesta URL: https://www.python.org/downloads/release/python-2715/

    b. Selecione o instalador do MacOS apropriado, faça download dele e execute-o. A instalação deve incluir o Pip.

2. Para instalar a biblioteca de Solicitações do Python, use este comando:

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. Para instalar o plug-in da CLI do DBaaS, use este comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. Para confirmar se o plug-in da CLI do DBaaS foi instalado corretamente, use este comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   O sistema exibe `dbaas` na lista de comandos disponíveis.

### Em Windows:
{: #dbaas_cli_windows}

**Nota:** apenas a versão x86_64 do Windows é suportada.

1. Se você ainda não tiver o Python, faça download e instale-o seguindo estas instruções:

    a. Acesse o website do Python nesta URL: https://www.python.org/downloads/release/python-2715/

    b. Selecione o instalador do **Windows x86-64 MSI**, faça download dele e execute-o.

    c. No menu **Customizar Python** do assistente de **Configuração do Python**, especifique: **o pip será instalado na unidade de disco rígido local**

2. Após instalar o Python, use o seu diálogo do Windows **Editar variável do sistema** para
   anexar os valores a seguir no valor da variável **Path** existente:

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. Para instalar a biblioteca de Solicitações do Python, abra a janela **Prompt de comandos** e insira este comando:

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. Para instalar o plug-in da CLI do DBaaS, use este comando:

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. Para confirmar se o plug-in da CLI do DBaaS foi instalado corretamente, use este comando:

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   O sistema exibe `dbaas` na lista de comandos disponíveis.

Para obter informações detalhadas sobre os comandos de plug-in da CLI do DBaaS, é possível consultar a [Referência da CLI do DBaaS](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin).
