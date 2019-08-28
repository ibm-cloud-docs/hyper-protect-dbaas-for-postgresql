---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: IAM, identity, access management, role

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Identity and Access Management 角色及動作
{: #iam}

對於您帳戶中的使用者，{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服務實例的存取權是受到 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 控制。在您帳戶中，存取 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服務的每位使用者都必須獲得指派存取原則，並定義 IAM 角色。原則會決定使用者可以在您選取的服務或實例環境定義內執行什麼動作。可允許的動作是由 {{site.data.keyword.cloud_notm}} 服務自訂，並定義為能夠對服務執行的作業。然後動作會對映到 IAM 使用者角色。
{: shortdesc}

原則能啟用在不同層次授與的存取權。部分選項包括下列各項：

* 帳戶中跨所有服務實例的存取權
* 帳戶中個別服務實例的存取權
* 實例內特定資源的存取權

定義存取原則的範圍之後，您會指派決定使用者存取權層次的角色。請檢閱下表，它概述了每個角色在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} 服務內容許的動作。

下表詳細說明對映至平台管理角色的動作。平台管理角色讓使用者能在平台層次對服務資源執行作業，例如指派使用者對服務的存取權、建立或刪除實例，以及將實例連結至應用程式。

|平台管理角色|動作的說明|動作範例|
|------------------------|----------------------|----------------------------------------------------------------|
|檢視者|可以檢視服務實例，但無法修改它們|<ul><li>列出叢集</li><li>檢視叢集的詳細資料</li></ul>|
|編輯者|執行所有平台動作，但管理帳戶及指派存取原則除外|<ul><li>將服務連結至叢集</li></ul>|
|操作員|執行配置及操作服務實例所需的平台動作，例如檢視服務的儀表板|<ul><li>將服務連結至叢集</li></ul>|
|管理者|根據指派這個角色的資源執行所有平台動作，包括指派存取原則給其他使用者|<ul><li>移除叢集</li><li>建立叢集</li><li>更新使用者存取原則</li><li>檢視者、編輯者及操作員可以執行的所有動作</li></ul>|
{: caption="表 1. IAM 使用者角色及動作"}

如需在使用者介面中指派使用者角色的相關資訊，請參閱[管理對資源的存取權](/docs/iam?topic=iam-iammanidaccser#iammanidaccser)。
