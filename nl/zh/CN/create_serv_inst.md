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


# 创建服务实例
{: #dbaas_cli_create_service}

要创建服务实例，请使用 `ibmcloud resource service-instance-create` 命令，如以下示例中所示。在 Windows 中，建议使用 Bash 终端（例如，Cygwin 或 Git Bash）来输入命令。

```javascript
ibmcloud resource service-instance-create MyDBaaSIns03 hyperp-dbaas-postgresql postgresql-small us-south -p '{"name":"DBaaSTestCLICluster03", "admin_name":"admin","password":"passWORD4User19", "confirm_password":"passWORD4User19", "license_agree":["agreed"]}'
```
{: codeblock}

其中，参数的定义如下：

|参数|定义|
| ---------------- |  -------------------------------------------------------------- |
|*MyDBaaSIns03*|服务实例的名称（替换为您自己选择的名称）。|
|*hyperp-dbaas-postgresql*|{{site.data.keyword.ihsdbaas_postgresql_full}} 的目录名称。|
|*postgresql-small*|套餐名称。可用的套餐为：**postgresql-small**、**postgresql-medium** 和 **postgresql-large**。（**注：**套餐名称是区分大小写的。）|
|*us-south*|新数据库将位于的位置。（**注：**目前，仅 **us-south** 支持 {{site.data.keyword.ihsdbaas_postgresql_full}}。）|
|*-p*|有效的 JSON 字符串，必须包含下表中的参数。|

<table>
  <tr>
    <th>-p 参数</th>
    <th>定义</th>
  </tr>
  <tr>
    <td>*name*</td>
    <td>数据库集群的名称。</td>
  </tr>
  <tr>
    <td>*admin_name*</td>
    <td>要创建的数据库的管理员用户名。</td>
  </tr>
  <tr>
    <td>*password*</td>
    <td>
      <p>要创建的数据库的管理员用户密码。您需要创建具有以下特性的强密码：<ul>
          <li>长度至少为 **15 个字符**</li>
          <li>至少包含 **1 个大写字符**</li>
          <li>至少包含 **1 个小写字符**</li>
          <li>至少包含 **1 个数字**</li>
          <li>不包含用户名</li>
        </ul>
      </p>
    </td>
  </tr>
  <tr>
    <td>*confirm_password*</td>
    <td>相同密码。</td>
  </tr>
  <tr>
    <td>*license_agree*</td>
    <td>值为 **agreed** 指示接受许可协议，这样才能使用 {{site.data.keyword.ihsdbaas_postgresql_full}}。</td>
  </tr>
</table>

输入命令后，新服务实例的状态可能会暂时显示为 **inactive**，如以下示例中所示：

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

这是因为准备集群需要几分钟时间。要获取集群状态的更新，请使用 `ibmcloud resource service-instances` 命令，如以下示例中所示：

```
ibmcloud resource service-instances
Retrieving all instances of all services in resource group default and all locations under account BSS Metering Test Account as bluemix_ui_metering_test@mailinator.com...
OK
Name           Location   State      Type
MyDBaaSIns03   us-south   active     service_instance
```
{: codeblock}

为了进一步加强安全性，建议您在供应服务实例后立即更新**数据库管理员密码**。您需要遵循先前提到的相同规则来设置新密码。
{: note}
