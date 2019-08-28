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


# 選擇要登入的服務端點
{: #choose-endpoint}

{{site.data.keyword.cloud}} 在您可以登入的各種地理地區中提供了許多服務端點。若要尋找在您所在地理位置附近的服務端點，請使用 `ibmcloud regions` 指令，如下列範例中所示：

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

目前，僅 **us-south** 地區支援 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}。
{: note}

若要登入 {{site.data.keyword.cloud_notm}} 服務端點，請執行以下步驟：

1. 輸入 `ibmcloud login` 指令，指出您將使用單一登入 (SSO)，並指定要登入的端點 URL，如下列範例中所示：

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   系統會顯示提供一次性密碼的網頁 URL。

2. 從系統主控台複製該 URL，並將其貼到 Web 瀏覽器中。

   系統會顯示 **{{site.data.keyword.cloud_notm}} 一次性密碼**頁面。

3. 從該網頁複製密碼，並將其貼到系統主控台指令行中。

   密碼不會顯示在指令行中。鑑別密碼後，您將收到 **OK** 訊息，指出您已登入。

如需 `ibmcloud login` 指令參數的相關資訊，可以參閱 [{{site.data.keyword.cloud_notm}} CLI 參考資料](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login)。

使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 時，可能需要在多個地區中建立空間，並使用 `ibmcloud target` 指令在地區之間進行切換。如需相關資訊，請參閱[新增組織和空間](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)和[一般 CLI (ibmcloud) 指令](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target)。
{: note}
