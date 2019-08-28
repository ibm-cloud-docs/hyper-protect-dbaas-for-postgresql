---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: service instance, ibmcloud resource

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# サービス・インスタンスの作成
{: #dbaas_cli_create_service}

サービス・インスタンスを作成するには、以下の例に示すように `ibmcloud resource service-instance-create` コマンドを使用します。 Windows の場合は、Cygwin や Git Bash などの Bash 端末を使用してコマンドを入力することをお勧めします。

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

各パラメーターの定義は以下のとおりです。

| パラメーター        |  定義                                                    |
| ---------------- |  -------------------------------------------------------------- |
| *MyDBaaSIns03*   |  サービス・インスタンスの名前 (任意の名前に置き換えてください)。 |
| *hyperp-dbaas-postgresql* | {{site.data.keyword.ihsdbaas_postgresql_full}} のカタログ名。 |
| *postgresql-small*  | プランの名前。 使用可能なプランは、**postgresql-small**、**postgresql-medium**、および **postgresql-large** です。  (**注:** プランの名前には大/小文字の区別があります)。 |
| *us-south*            | 新しいデータベースを作成するロケーション (**注:** 現在は **us-south** だけが {{site.data.keyword.ihsdbaas_postgresql_full}} をサポートしています)。 |
| *-p*               | 有効な JSON ストリング。以下の表のパラメーターを指定する必要があります。 |

<table>
  <tr>
    <th>-p パラメーター</th>
    <th>定義</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>データベース・クラスターの名前。</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>作成するデータベースの管理者のユーザー名。</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>作成するデータベースの管理者のユーザー・パスワード。 以下のような性質の強力なパスワードを作成する必要があります。
        <ul>
          <li>長さは最小でも **15 文字**</li>
          <li>少なくとも **1 つの大文字**</li>
          <li>少なくとも **1 つの小文字**</li>
          <li>少なくとも **1 つの数値**</li>
          <li>ユーザー名を含まない</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>同じパスワード。</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>値 **agreed** が使用条件を承諾したことを示します。{{site.data.keyword.ihsdbaas_postgresql_full}} を使用するためにはこれが必須です。</td>
  </tr>
</table>

以下の例に示すように、コマンドを入力した後、新しいサービス・インスタンスの状態は一時的に **inactive** になります。

```
Creating service instance MYDBaaSIns03 in resource group default of account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Service instance MYDBaaSIns03 was created.

Name:             MYDBaaSIns03
ID:               crn:v1:bluemix:public:hyperp-dbaas-postgresql:us-south:a/0e79133675a31dbfd10504847a9e174f:279be69f-20f2-4ade-baf9-5c470c400753::
GUID:             279be69f-20f2-4ade-baf9-5c470c400753   
Location:         us-south   
State:            inactive   
Type:             service_instance   
Sub Type:            
Created at:       2019-06-03T06:17:13Z   
Updated at:       2019-06-03T06:17:13Z   
Last Operation:                      
                  Status       create in progress      
                  Updated At   2019-06-03 06:17:13.917566444 +0000 UTC
```
{: codeblock}

これは、クラスターの準備に数分間かかるためです。 更新されたクラスター・ステータスを表示するには、以下の例に示すように `ibmcloud resource service-instances` コマンドを使用します。

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

より一層セキュリティーを強化するには、サービス・インスタンスのプロビジョン後すぐに**データベース管理者のパスワード**を更新することをお勧めします。 新しいパスワードを設定するには、先ほど説明したのと同じルールに従う必要があります。
{: note}
