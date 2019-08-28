---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: database cluster, service instance, pricing plans, License Agreement

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# サービス・インスタンス
{: #dbaas_webui_service}

## サービス・インスタンスの作成
{: #dbaas_webui_create_service}

<ol>
<li>{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} カタログ・エントリーをクリックして、サービス作成画面を開きます。</li>
<li>必要な値を入力します。
  <dl>
    <dt>サービス名:</dt>
    <dd>データベース・サービスの名前。</dd>

    <dt>デプロイする地域/ロケーションの選択:</dt>
    <dd>データベースを配置するデータ・センターを選択します。</dd>

    <dt>リソース・グループの選択:</dt>
    <dd>選択できるリソース・グループがない場合は、{{site.data.keyword.cloud_notm}} ダッシュボードで作成できます。</dd>

    <dt>タグ:</dt>
    <dd>タグはオプションです。 タグ付けについて詳しくは、[リソースのタグ付け](/docs/resources?topic=resources-tag#tag)を参照してください。</dd>

    <dt>クラスター/レプリカセットの名前:</dt>
    <dd>サービス・インスタンスの名前。</dd>

    <dt>データベース管理者の名前 (Database Admin Name):</dt>
    <dd>データベース管理者 (DBA) のユーザー ID。
    <p>**注:** データベース管理者には SUPERUSER 権限はありません。 データベース管理者の権限は INHERIT、CREATEROLE、CREATEDB、LOGIN、および REPLICATION に制限されています。</p></dd>

    <dt>データベース管理者のパスワード (Database Admin Password):</dt>
    <dd>
    <p>DBA ユーザー ID のパスワード。 以下のような性質の強力なパスワードを作成する必要があります。
      <ul>
        <li>長さは最小でも **15 文字**</li>
        <li>少なくとも **1 つの大文字**</li>
        <li>少なくとも **1 つの小文字**</li>
        <li>少なくとも **1 つの数値**</li>
        <li>ユーザー名を含まない</li>
      </ul>
    </p>
    </dd>

    <dt>パスワードの確認 (Confirm Password):</dt>
    <dd>DBA ユーザー ID のパスワードを確認します。</dd>

    <dt>ご使用条件 (License Agreement):</dt>
    <dd>使用条件を読み、チェック・ボックスを選択して同意します。</dd>

    <dt>価格プラン:</dt>
    <dd>データベース・タイプ PostgreSQL のさまざまな価格カテゴリーが示されます。 要件に最も適したものを選択してください。</dd>
  </dl>
</li>
<li>**「作成」**をクリックします。
<p>サービスのデプロイには時間がかかることを伝えるダイアログ・ウィンドウが表示された後、{{site.data.keyword.cloud_notm}} リソース・リスト・ダッシュボードが表示されます。 **「サービス」**セクションの下に作成したサービス・インスタンスがリストに表示されます。 サービスの状況が**「プロビジョン済み」**である場合、インスタンスは使用可能です。</p>
</li>

<li>サービスを選択して、{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} ダッシュボードを表示します。</li>
</ol>

より一層セキュリティーを強化するには、サービス・インスタンスのプロビジョン後すぐに**データベース管理者のパスワード**を更新することをお勧めします。 新しいパスワードを設定するには、先ほど説明したのと同じルールに従う必要があります。
{: note}

## すべてのサービス・インスタンスのリスト表示
{: #dbaas_webui_list_service}

{{site.data.keyword.cloud_notm}} ダッシュボードを開き、作成済みのサービス・インスタンスのリストを表示します。

<ol>
	<li>コンソールの左上にある 3 本バーのボタンをクリックします。</li>
	<li>ダッシュボードを選択します。</li>
	<li>サービスを選択します。</li>
</ol>

## サービス・インスタンスの詳細情報の表示
{: #dbaas_webui_show_detail_service}

1. ターゲット・インスタンス名をクリックしてサービス・ダッシュボードを表示します。
2. 左側のナビゲーション・バーの**「管理」**を選択すると、**「概要」**タブ・ページに全体的な情報が表示されます。
3. **「インスタンス」**タブを選択し、詳細情報を表示します。


## サービス・インスタンスの削除
{: #dbaas_webui_delete_service}

1. {{site.data.keyword.cloud_notm}} リソース・リストを表示します。そのためには、**「ナビゲーション・メニュー」>「リソース・リスト」**とクリックします。
2. **「サービス」**ツイスターを開いてサービス・インスタンスを表示します。
3. 削除するサービス・インスタンスを選択します。
4. 右側にある 3 つのドットをクリックします。
5. **「削除」**をクリックします。
