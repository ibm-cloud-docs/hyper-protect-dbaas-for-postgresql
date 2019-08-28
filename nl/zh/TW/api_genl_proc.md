---

copyright:
  years: 2019
lastupdated: "2019-06-21"

keywords: DBaaS Manager APIs, DBaaS Manager, API request

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 使用 DBaaS 管理程式 API 的一般指示
{: #gen_inst_mgr_apis}
<ol>
<li>以 JSON 格式指定要求的資料。
</li>
<li>將 API 要求傳送到 DBaaS 管理程式。
<p>可以使用 RESTful API 用戶端（例如 cURL）來處理要求。
</p>
<p>DBaaS 管理程式在以下位置可用：
<table>
  <tr>
    <th> 主機名稱</th>
    <th> 埠號</th>
    <th> 地區</th>
    <th> 縣/市</th>
  </tr>
  <tr>
    <td> dbaas900.hyperp-dbaas.cloud.ibm.com</td>
    <td> 20000 </td>
    <td> us-south </td>
    <td>  達拉斯      </td>
  </tr>
</table>
</p>	 
</li>
</ol>

如需更詳細的資訊（方法和參數），可以參閱 [DBaaS API 文件](https://{DomainName}/apidocs/hyperp-dbaas){: external}。

## 範例
{: #api-example}

若要建立服務實例，請發出直接 API 呼叫，例如：

```
curl -X POST \
"https://<ip>:<port>/api/v1/services" \
-d '{"catalog": "hyperp-dbaas-postgresql", "name": "Service_Name", "resource_group": "default", "plan": "postgresql-small", "admin_name": "admin", "password": "passWORD4User19"}'
-H "x-auth-token: <access_token>" \
-H "accept: application/json" \
-H "accept-license-agreement: yes"
```
{:codeblock}

其中：
<dl>
<dt> &lt;<em>access_token</em>&gt;</dt>
<dd>是先前取得的存取記號；請參閱[設定鑑別以使用 DBaaS 管理程式 API](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth)。（**附註：**如果存取記號已到期，請回到這些指示並要求新記號。）</dd>
<dt> &lt;<em>ip</em>&gt;</dt>
<dd>是 DBaaS 管理程式的主機名稱。上表中列出了有效的主機名稱。</dd>
<dt> &lt;<em>port</em>&gt;</dt>
<dd>是 DBaaS 管理程式的埠號。這是有效的埠號：<p>20000 </p>
</dd>
</dl>

**附註：**資料庫管理者沒有 SUPERUSER 權限。資料庫管理者的權限受限於 INHERIT、CREATEROLE、CREATEDB、LOGIN 及 REPLICATION。
