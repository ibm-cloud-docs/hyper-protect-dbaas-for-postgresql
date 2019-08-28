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


# 建立服務實例
{: #dbaas_cli_create_service}

若要建立服務實例，請使用 `ibmcloud resource service-instance-create` 指令，如下列範例中所示。在 Windows 中，建議使用 Bash 終端機（例如，Cygwin 或 Git Bash）來輸入指令。

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

其中，參數的定義如下：

|參數|定義|
| ---------------- |  -------------------------------------------------------------- |
|*MyDBaaSIns03*|服務實例的名稱（取代為您自己選擇的名稱）。|
|*hyperp-dbaas-postgresql*|{{site.data.keyword.ihsdbaas_postgresql_full}} 的型錄名稱。|
| *postgresql-small*  |方案名稱。可用的方案為：**postgresql-small**、**postgresql-medium** 和 **postgresql-large**。（**附註：**方案名稱會區分大小寫。）|
|*us-south*|新資料庫將位於的位置。（**附註：**目前，僅 **us-south** 支援 {{site.data.keyword.ihsdbaas_postgresql_full}}。）|
|*-p*|有效的 JSON 字串，必須包含下表中的參數。|

<table>
  <tr>
    <th>-p 參數</th>
    <th>定義</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>資料庫叢集的名稱。</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>要建立之資料庫管理者的使用者名稱。</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>要建立之資料庫管理者的使用者密碼。您需要建立具有下列屬性的高保護性密碼：<ul>
          <li>長度為最少 **15 個字元**</li>
          <li>至少**一個大寫**字元</li>
          <li>至少**一個小寫**字元</li>
          <li>至少**一個數字**</li>
          <li>不包含使用者名稱</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>相同密碼。</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>值為 **agreed** 指出接受授權合約，這樣才能使用 {{site.data.keyword.ihsdbaas_postgresql_full}}。</td>
  </tr>
</table>

輸入指令後，新服務實例的狀態可能會暫時顯示為 **inactive**，如下列範例中所示：

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

這是因為準備叢集需要幾分鐘時間。若要取得叢集狀態的更新，請使用 `ibmcloud resource service-instances` 指令，如下列範例中所示：

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

若要更進一步強化安全，建議您在佈建服務實例之後立即更新**資料庫管理者密碼**。您需要遵循先前所提及的相同規則來設定新密碼。
{: note}
