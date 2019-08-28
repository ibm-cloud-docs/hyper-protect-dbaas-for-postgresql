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


# 安装 DBaaS CLI 插件
{: #install-dbaas-cli-plugin}

要在使用 {{site.data.keyword.cloud}} CLI 时访问完整的 DBaaS 命令集，必须安装以下组件（请参阅[指示信息](#dbaas_cli_instr)）：

- Python 运行时（建议使用 2.7.15；**不**支持 3.x）
- Python Pip 程序包管理系统
- Python 请求库
- DBaaS CLI 插件

## 关于安装 DBaaS CLI 组件的指示信息（按操作系统）
{: #dbaas_cli_instr}

- [在 Linux 上](#dbaas_cli_linux)
- [在 MacOS 上](#dbaas_cli_macos)
- [在 Windows 上](#dbaas_cli_windows)

### 在 Linux 上：
{: #dbaas_cli_linux}

1. 大多数 Linux 分发版都会预安装 Python 和 Pip。如果您的分发版未预安装，请使用以下命令进行安装：

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. 要安装 Python 请求库，请使用以下命令：

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. 要安装 DBaaS CLI 插件，请使用以下命令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. 要确认是否 DBaaS CLI 插件已正确安装，请使用以下命令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系统会在可用命令列表中显示 `dbaas`。

### 在 MacOS 上：
{: #dbaas_cli_macos}

1. 如果您还没有 Python，请遵循以下指示信息下载并安装 Python：

    a. 转至以下 URL 处的 Python Web 站点：https://www.python.org/downloads/release/python-2715/

    b. 选择相应的 MacOS 安装程序，然后下载并运行。安装应该会包含 Pip。

2. 要安装 Python 请求库，请使用以下命令：

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. 要安装 DBaaS CLI 插件，请使用以下命令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. 要确认是否 DBaaS CLI 插件已正确安装，请使用以下命令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系统会在可用命令列表中显示 `dbaas`。

### 在 Windows 上：
{: #dbaas_cli_windows}

**注：**仅支持 x86_64 版本的 Windows。

1. 如果您还没有 Python，请遵循以下指示信息下载并安装 Python：

    a. 转至以下 URL 处的 Python Web 站点：https://www.python.org/downloads/release/python-2715/

    b. 选择 **Windows x86-64 MSI** 安装程序，然后下载并运行。

    c. 在 **Python 安装**向导的**定制 Python** 菜单上，指定：**pip 将安装在本地硬盘驱动器上**

2. 安装 Python 后，使用 Windows **编辑系统变量**对话框将以下值附加到现有 **Path** 变量值：

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. 要安装 Python 请求库，请打开**命令提示符**窗口，然后输入以下命令：

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. 要安装 DBaaS CLI 插件，请使用以下命令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. 要确认是否 DBaaS CLI 插件已正确安装，请使用以下命令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系统会在可用命令列表中显示 `dbaas`。

有关 DBaaS CLI 插件命令的详细信息，可以参阅 [DBaaS CLI 参考](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin)。
