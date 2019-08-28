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


# 选择要登录到的服务端点
{: #choose-endpoint}

{{site.data.keyword.cloud}} 在您可以登录到的各种地理区域中提供了许多服务端点。要查找在您所在地理位置附近的服务端点，请使用 `ibmcloud regions` 命令，如以下示例中所示：

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

目前，仅 **us-south** 区域支持 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}。
{: note}

要登录到 {{site.data.keyword.cloud_notm}} 服务端点，请执行以下步骤：

1. 输入 `ibmcloud login` 命令，指示您将使用单点登录 (SSO)，并指定要登录到的端点的 URL，如以下示例中所示：

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   系统会显示提供一次性密码的 Web 页面的 URL。

2. 从系统控制台复制该 URL，并将其粘贴到 Web 浏览器中。

   系统会显示 **{{site.data.keyword.cloud_notm}} 一次性密码**页面。

3. 从该 Web 页面复制密码，并将其粘贴到系统控制台命令行中。

   密码不会显示在命令行中。认证密码后，您将收到 **OK** 消息，指示您已登录。

有关 `ibmcloud login` 命令参数的更多信息，可以参阅 [{{site.data.keyword.cloud_notm}} CLI 参考](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)。
使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 时，可能需要在多个区域中创建空间，并使用 `ibmcloud target` 命令在区域之间进行切换。有关更多信息，请参阅[添加组织和空间](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)和[常规 CLI (ibmcloud) 命令](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target)。
{: note}
