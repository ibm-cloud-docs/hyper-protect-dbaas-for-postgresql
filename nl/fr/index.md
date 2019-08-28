---

copyright:
  years: 2019
lastupdated: "2019-06-11"

keywords: database cluster, Data security, database instance

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}

# Initiation à {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #gettingstarted}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} est un service {{site.data.keyword.cloud_notm}} qui fournit des bases de données PostgreSQL à la demande. Il offre une plateforme souple et évolutive qui vous permet de mettre à disposition et gérer la base de données de votre choix avec rapidité et en toute facilité.
{: shortdesc}

Cette offre {{site.data.keyword.cloud_notm}} fournit des clusters de base de données PostgreSQL. Chaque cluster de base de données comprend une instance de base de données maître et deux esclaves de base de données destinés à la sauvegarde de cette dernière.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} vous permet de créer des clusters de base de données dans {{site.data.keyword.cloud_notm}}, de gérer des instances de base de données, d'administrer des utilisateurs de base de données et de créer et surveiller des bases de données.

## Sécurité et confidentialité des données
{: #data-security-and-privacy}

{{site.data.keyword.IBM_notm}} héberge vos bases de données dans un environnement sécurisé hautement disponible et sécurisé :
<ul>
<li>Les technologies sous-jacentes empêchent {{site.data.keyword.IBM_notm}} ou un tiers d'accéder à vos données.
<p>La technologie {{site.data.keyword.IBM_notm}} Secure Service Container protège le système via un environnement infalsifiable. L'accès au système est restreint et est activé uniquement via des API RESTful bien définies.</p></li>
<li>Les données sont chiffrées au repos et à la volée.</li>
<li>Le matériel du système, la configuration du système et la configuration de la base de données garantissent une haute disponibilité.</li>
</ul>

<!--
For more information, watch:

- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - English version](https://www.youtube.com/watch?v=__IBP727IL8){: external}
- [Data security and privacy using {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_full}} - Chinese version](https://v.youku.com/v_show/id_XMzc3ODQzMzYwMA==.html){: external}
-->

## Création d'un cluster de base de données
{: #creating-a-database-cluster-introduction}

Pour créer un cluster de base de données, il vous suffit de saisir les valeurs requises sur l'écran de configuration de service d'{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} et de cliquer sur **Créer**.

Une fois que vous avez créé le cluster de base de données, {{site.data.keyword.IBM_notm}} vous fournit un ou plusieurs noms d'hôte et numéros de port pour les instances de base de données créées. Vous pouvez désormais utiliser ces informations ainsi que les données d'identification d'utilisateur que vous avez spécifiées dans le catalogue pour créer vos bases de données et y accéder.

## Gestion du cluster de base de données
{: #managing-database-cluster-introduction}

Dans un cluster de base de données, vous pouvez créer des bases de données, gérer les instances de base de données et créer ou supprimer des utilisateurs.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} contient un gestionnaire DBaaS Manager, qui gère et planifie intelligemment vos demandes en fonction des ressources disponibles.

Vous pouvez envoyer des demandes au gestionnaire DBaaS Manager via l'une des interfaces suivantes :

- L'[interface utilisateur Web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service)
- Les [API DBaaS Manager (pour la gestion de cluster de base de données)](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gen_inst_mgr_apis)
- Les [API {{site.data.keyword.cloud_notm}} (pour la gestion d'instance de service)](https://{DomainName}/apidocs/hyperp-dbaas){: external}
- Le [plug-in CLI avec l'outil CLI {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-install-ibm-cli)


## Accès à la base de données
{: #accessing-database-introduction}

Après avoir créé une base de données PostgreSQL, vous pouvez utiliser pgadmin ou votre outil PostgreSQL de prédilection pour gérer les bases de données.

### Avant de commencer
{: #accessing-database-introduction-byb}

Pour garantir le transfert sécurisé des données, procurez-vous un fichier d'autorité de certification à partir du tableau de bord et copiez-le dans le répertoire approprié.

### Connexion à une base de données
{: #accessing-database-introduction-connect}

Le tableau de bord {{site.data.keyword.ihsdbaas_postgresql_full}} fournit les informations nécessaires pour la connexion à une base de données.

#### Shell psql
{: #accessing-database-introduction-connect-psqlshell}

Vous pouvez utiliser la commande suivante :
<pre><code class="hljs">psql "host=&lt;<em>Hostname</em>&gt; user=&lt;<em>Username</em>&gt; port=&lt;<em>PortNumber</em>&gt; sslmode=verify-full sslrootcert=&lt;<em>CAFilePath</em>&gt;"</code></pre>
Où :
<dl>
  <dt> &lt;<em>Hostname</em>&gt; </dt>
    <dd> Nom d'hôte du cluster de base de données. </dd>
  <dt> &lt;<em>Username</em>&gt; </dt>
    <dd> Nom d’utilisateur de l’administrateur de base de données spécifié dans l’écran de création de service. </dd>
  <dt> &lt;<em>PortNumber</em>&gt; </dt>
    <dd> Numéro de port du cluster de base de données. </dd>
  <dt> &lt;<em>CAFilePath</em>&gt; </dt>
    <dd> Chemin d'accès au fichier d'autorité de certification. </dd>  
</dl>

**Remarque :** la commande `psql` ne vérifie pas le certificat du cluster de base de données si les options `sslmode` et `sslrootcert` ne sont pas fournies.

### Autres outils
{: #accessing-database-introduction-connect-other}

Pour les autres outils, tels que pgAdmin, {{site.data.keyword.ihsdbaas_postgresql_full}} prend en charge la *validation de certificat serveur SSL* pour établir une connexion à l'hôte. Si besoin, utilisez le fichier d'autorité de certification fourni.
