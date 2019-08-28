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


# 安裝 DBaaS CLI 外掛程式
{: #install-dbaas-cli-plugin}

若要在使用 {{site.data.keyword.cloud}} CLI 時存取完整的 DBaaS 指令集，必須安裝以下元件（請參閱[指示](#dbaas_cli_instr)）：

- Python 運行環境（建議使用 2.7.15；**不**支援 3.x）
- Python Pip 套件管理系統
- Python Requests 程式庫
- DBaaS CLI 外掛程式

## 關於安裝 DBaaS CLI 元件的指示（依作業系統）
{: #dbaas_cli_instr}

- [在 Linux 上](#dbaas_cli_linux)
- [在 MacOS 上](#dbaas_cli_macos)
- [在 Windows 上](#dbaas_cli_windows)

### 在 Linux 上：
{: #dbaas_cli_linux}

1. 大多數 Linux 發行套件都會預先安裝 Python 和 Pip。如果您的發行套件未預先安裝，請使用以下指令進行安裝：

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. 若要安裝 Python Requests 程式庫，請使用這個指令：

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. 若要安裝 DBaaS CLI 外掛程式，請使用這個指令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. 若要確認 DBaaS CLI 外掛程式已正確地安裝，請使用這個指令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系統會在可用的指令清單中顯示 `dbaas`。

### 在 MacOS 上：
{: #dbaas_cli_macos}

1. 如果您還沒有 Python，請遵循下列指示來下載並安裝它：

    a. 前往 Python 網站，URL 為 https://www.python.org/downloads/release/python-2715/

    b. 選取適當的 MacOS 安裝程式，然後下載並執行。安裝應該會包含 Pip。

2. 若要安裝 Python Requests 程式庫，請使用這個指令：

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. 若要安裝 DBaaS CLI 外掛程式，請使用這個指令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. 若要確認 DBaaS CLI 外掛程式已正確地安裝，請使用這個指令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系統會在可用的指令清單中顯示 `dbaas`。

### 在 Windows 上：
{: #dbaas_cli_windows}

**附註：**僅支援 x86_64 版本的 Windows。

1. 如果您還沒有 Python，請遵循下列指示來下載並安裝它：

    a. 前往 Python 網站，URL 為 https://www.python.org/downloads/release/python-2715/

    b. 選取 **Windows x86-64 MSI** 安裝程式，然後下載並執行。

    c. 在 **Python 安裝**精靈的**自訂 Python** 功能表上，指定：**pip 將安裝在本端硬碟上**

2. 安裝 Python 後，使用 Windows **編輯系統變數**對話框將下列值附加到現有 **Path** 變數值：

   ```javascript
   C:\Python27;C:\Python27\Scripts
   ```
   {: codeblock}

3. 若要安裝 Python Requests 程式庫，請開啟**命令提示字元**視窗，然後輸入這個指令：

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. 若要安裝 DBaaS CLI 外掛程式，請使用這個指令：

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. 若要確認 DBaaS CLI 外掛程式已正確地安裝，請使用這個指令：

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   系統會在可用的指令清單中顯示 `dbaas`。

如需 DBaaS CLI 外掛程式指令的詳細資料，可以參閱 [DBaaS CLI 參考資料](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin)。
