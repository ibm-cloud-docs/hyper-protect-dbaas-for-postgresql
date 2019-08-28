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


# ログインするサービス・エンドポイントの選択
{: #choose-endpoint}

{{site.data.keyword.cloud}} には、ログイン可能な多数のサービス・エンドポイントがさまざまな地理的領域に用意されています。
地理的に近い場所にあるサービス・エンドポイントを見つけるには、以下の例に示す `ibmcloud regions` コマンドを使用します。

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

現在、{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} は **us-south** 地域でのみサポートされています。
{: note}

{{site.data.keyword.cloud_notm}} サービス・エンドポイントにログインするには、以下の手順に従います。

1. 以下の例に示すように、シングル・サインオン (SSO) を使用することを指示し、ログインするエンドポイントの URL を指定して `ibmcloud login` コマンドを入力します。

   ```
   ibmcloud login --sso -a https://cloud.ibm.com
   ```
   {:codeblock}

   ワンタイム・パスコードを取得できる Web ページの URL がシステムから表示されます。

2. システム・コンソールの URL をコピーして Web ブラウザーに貼り付けます。

   **「{{site.data.keyword.cloud_notm}} ワンタイム・パスコード ({{site.data.keyword.cloud_notm}} One time passcode)** ページがシステムから表示されます。

3. Web ページのパスコードをコピーしてシステム・コンソールのコマンド・ラインに貼り付けます。

   パスコードはコマンド・ラインに表示されません。 パスワードが認証されると、ログインしたことを示す**「OK」**のメッセージが表示されます。

`ibmcloud login` コマンド・パラメーターについて詳しくは、[{{site.data.keyword.cloud_notm}} CLI リファレンス](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) を参照してください。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} を使用する場合は、複数の地域にスペースを作成し、`ibmcloud target` コマンドを使用して地域を切り替える必要がある場合があります。 詳しくは、[組織およびスペースの追加](/docs/account?topic=account-orgsspacesusers#orgsspacesusers)
および [一般 CLI (ibmcloud) コマンド](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#bluemix_target) を参照してください。
{: note}
