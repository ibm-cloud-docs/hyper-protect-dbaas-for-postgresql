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


# 有关使用 DBaaS 管理器 API 的常规指示信息
{: #gen_inst_mgr_apis}
<ol>
<li>以 JSON 格式指定请求的数据。
</li>
<li>将 API 请求发送到 DBaaS 管理器。
<p>可以使用 RESTful API 客户机（例如，cURL）来处理请求。
</p>
<p>DBaaS 管理器在以下位置可用：
<table>
  <tr>
    <th> 主机名</th>
    <th> 端口号</th>
    <th> 区域</th>
    <th> 城市</th>
  </tr>
  <tr>
    <td> dbaas900.hyperp-dbaas.cloud.ibm.com</td>
    <td> 20000 </td>
    <td> us-south </td>
    <td> 达拉斯</td>
  </tr>
</table>
</p>	 
</li>
</ol>

有关更详细的信息（方法和参数），可以参阅 [DBaaS API 文档](https://{DomainName}/apidocs/hyperp-dbaas){: external}。

## 示例
{: #api-example}

要创建服务实例，请发出直接 API 调用，例如：

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
<dd>是先前获取的访问令牌；请参阅[设置认证以使用 DBaaS 管理器 API](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-api-auth)。（**注：**如果访问令牌已到期，请返回到这些指示信息并请求新令牌。）</dd>
<dt> &lt;<em>ip</em>&gt;</dt>
<dd>是 DBaaS 管理器的主机名。上表中列出了有效的主机名。</dd>
<dt> &lt;<em>port</em>&gt;</dt>
<dd>是 DBaaS 管理器的端口号。这是有效的端口号：<p>20000</p>
</dd>
</dl>

**注：**数据库管理员没有 SUPERUSER 权限。数据库管理员的权限限制为 INHERIT、CREATEROLE、CREATEDB、LOGIN 和 REPLICATION。
