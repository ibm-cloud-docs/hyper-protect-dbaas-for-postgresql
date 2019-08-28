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


# DBaaS CLI プラグインのインストール
{: #install-dbaas-cli-plugin}

{{site.data.keyword.cloud}} CLI ですべての DBaaS コマンドを利用するためには、
以下のコンポーネントをインストールする必要があります ([手順](#dbaas_cli_instr)を参照してください)。

- Python ランタイム (2.7.15 をお勧めします。3.x はサポート**されていません**)
- Python Pip パッケージ管理システム
- Python Requests ライブラリー
- DBaaS CLI プラグイン

## DBaaS CLI コンポーネントのインストール手順 (オペレーティング・システム別)
{: #dbaas_cli_instr}

- [Linux の場合](#dbaas_cli_linux)
- [MacOS の場合](#dbaas_cli_macos)
- [Windows の場合](#dbaas_cli_windows)

### Linux の場合:
{: #dbaas_cli_linux}

1. ほとんどの Linux ディストリビューションには、Python および Pip がプリインストールされています。 プリインストールされていない場合は、以下のコマンドを使用してインストールしてください。

   ```javascript
   sudo apt-get install python python2.7 python-dev
   sudo apt-get install python-pip
   ```
   {: codeblock}

2. Python Requests ライブラリーをインストールするには、以下のコマンドを使用します。

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. DBaaS CLI プラグインをインストールするには、以下のコマンドを使用します。

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. DBaaS CLI プラグインが正常にインストールされたことを確認するには、以下のコマンドを使用します。

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   システムで使用可能なコマンドのリストに、`dbaas` が表示されます。

### MacOS の場合:
{: #dbaas_cli_macos}

1. まだ Python がない場合は、以下の手順に従い、ダウンロードしてインストールします。

    a. Python の Web サイト (URL: https://www.python.org/downloads/release/python-2715/) にアクセスします。

    b. 適切な MacOS インストーラーを選択し、ダウンロードして実行します。 このインストールには Pip も含まれているはずです。

2. Python Requests ライブラリーをインストールするには、以下のコマンドを使用します。

   ```javascript
   sudo pip install requests
   ```
   {: codeblock}

3. DBaaS CLI プラグインをインストールするには、以下のコマンドを使用します。

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

4. DBaaS CLI プラグインが正常にインストールされたことを確認するには、以下のコマンドを使用します。

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   システムで使用可能なコマンドのリストに、`dbaas` が表示されます。

### Windows の場合:
{: #dbaas_cli_windows}

**注:** x86_64 バージョンの Windows のみがサポートされています。

1. まだ Python がない場合は、以下の手順に従い、ダウンロードしてインストールします。

    a. Python の Web サイト (URL: https://www.python.org/downloads/release/python-2715/) にアクセスします。

    b. **Windows x86-64 MSI** インストーラーを選択し、ダウンロードして実行します。

    c. **「Python のセットアップ (Python Setup)」**ウィザードの**「Python のカスタマイズ (Customize Python)」**メニューで、**「pip をローカル・ハード・ディスクにインストールする (pip Will be installed on local hard disk drive)」**を指定します。

2. Python をインストールしたら、Windows の**「システム変数の編集」**ダイアログを使用して、
以下の値を既存の **Path** 変数値に追加します。

   ```javascript
   C:&#xa5;Python27;C:&#xa5;Python27&#xa5;Scripts
   ```
   {: codeblock}

3. Python Requests ライブラリーをインストールするには、**コマンド・プロンプト**・ウィンドウを開いて以下のコマンドを入力します。

   ```javascript
   pip install requests
   ```
   {: codeblock}

4. DBaaS CLI プラグインをインストールするには、以下のコマンドを使用します。

   ```javascript
   ibmcloud plugin install dbaas-cli
   ```
   {: codeblock}

5. DBaaS CLI プラグインが正常にインストールされたことを確認するには、以下のコマンドを使用します。

   ```javascript
   ibmcloud
   ```
   {: codeblock}

   システムで使用可能なコマンドのリストに、`dbaas` が表示されます。

DBaaS CLI プラグイン・コマンドについて詳しくは、[DBaaS CLI リファレンス](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin)を参照してください。
