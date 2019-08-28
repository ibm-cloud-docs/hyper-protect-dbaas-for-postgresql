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


# 服務實例
{: #dbaas_webui_service}

## 建立服務實例
{: #dbaas_webui_create_service}

<ol>
<li>按一下 {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} 型錄項目以開啟服務建立畫面。</li>
<li>輸入所需的值。
  <dl>
    <dt>服務名稱：</dt>
    <dd>資料庫服務的名稱。</dd>

    <dt>選取要在其中部署的地區/位置：</dt>
    <dd>選取資料庫將位於的資料中心。</dd>

    <dt>選取資源群組：</dt>
    <dd>如果沒有可選擇的資源群組，可以在 {{site.data.keyword.cloud_notm}}「儀表板」上建立資源群組。</dd>

    <dt>標籤：</dt>
    <dd>標籤是選用的。如需標籤的相關資訊，請參閱[標籤資源](/docs/resources?topic=resources-tag#tag)。</dd>

    <dt>叢集/抄本集名稱：</dt>
    <dd>服務實例的名稱。</dd>

    <dt>資料庫管理者名稱：</dt>
    <dd>資料庫管理者 (DBA) 的使用者 ID。<p>**附註：**資料庫管理者沒有 SUPERUSER 權限。資料庫管理者的權限受限於 INHERIT、CREATEROLE、CREATEDB、LOGIN 及 REPLICATION。</p></dd>

    <dt>資料庫管理者密碼：</dt>
    <dd>
    <p>DBA 使用者 ID 的密碼。您需要建立具有下列屬性的高保護性密碼：<ul>
        <li>長度為最少 **15 個字元**</li>
        <li>至少**一個大寫字元**</li>
        <li>至少**一個小寫字元**</li>
        <li>至少**一個數字**</li>
        <li>不包含使用者名稱</li>
      </ul>
    </p>
    </dd>

    <dt>確認密碼：</dt>
    <dd>確認 DBA 使用者 ID 的密碼。</dd>

    <dt>授權合約：</dt>
    <dd>閱讀授權合約後，勾選該方框以確認您同意。</dd>

    <dt>定價方案：</dt>
    <dd>對於 PostgreSQL 類型的資料庫，定價方案提供了不同的定價種類。請選擇最符合您需求的種類。</dd>
  </dl>
</li>
<li>按一下**建立**。<p>在出現一個對話框視窗指示您需要時間來部署服務後，將顯示 {{site.data.keyword.cloud_notm}}「資源清單」儀表板。可以在清單的**服務**區段下看到您建立的服務實例。服務的狀態為**已佈建**時，說明實例可供使用。</p>
</li>

<li>選取相應服務以顯示 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 儀表板。</li>
</ol>

若要更進一步強化安全，建議您在佈建服務實例之後立即更新**資料庫管理者密碼**。您需要遵循先前所提及的相同規則來設定新密碼。
{: note}

## 列出所有服務實例
{: #dbaas_webui_list_service}

開啟 {{site.data.keyword.cloud_notm}}「儀表板」以顯示已建立服務實例的清單：

<ol>
	<li>按一下主控台左上角的三槓按鈕。</li>
	<li>選取「儀表板」。</li>
	<li>選取「服務」。</li>
</ol>

## 顯示服務實例的詳細資料
{: #dbaas_webui_show_detail_service}

1. 按一下目標實例名稱以顯示服務儀表板。
2. 在左側導覽列中選取**管理**，然後可以在**概觀**標籤頁面上看到整體資訊。
3. 選取**實例**標籤以顯示詳細資料。


## 刪除服務實例
{: #dbaas_webui_delete_service}

1. 藉由按一下**導覽功能表 > 資源清單**來顯示 {{site.data.keyword.cloud_notm}} 資源清單。
2. 開啟**服務**折疊標記以顯示服務實例。
3. 選取要刪除的服務實例。
4. 按一下右側的三個點。
5. 按一下**刪除**。
