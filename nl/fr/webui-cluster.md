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


# Instances de service
{: #dbaas_webui_service}

## Création d'une instance de service
{: #dbaas_webui_create_service}

<ol>
<li>Cliquez sur l'entrée de catalogue {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} pour ouvrir l'écran de création de service.</li>
<li>Entrez les valeurs requises.
  <dl>
    <dt>Nom du service :</dt>
    <dd>Nom pour le service de base de données.</dd>

    <dt>Sélectionnez une région/un emplacement où effectuer le déploiement :</dt>
    <dd>Sélectionnez le centre de données dans lequel la base de données résidera.</dd>

    <dt>Sélectionnez un groupe de ressources :</dt>
    <dd>Si aucun groupe de ressources ne peut être sélectionné, vous pouvez en créer un sur le tableau de bord {{site.data.keyword.cloud_notm}}.</dd>

    <dt>Etiquettes :</dt>
    <dd>Les étiquettes sont facultatives. Pour plus d'informations sur l'étiquetage, voir [Etiquetage de ressources](/docs/resources?topic=resources-tag#tag).</dd>

    <dt>Nom de cluster / jeu de répliques :</dt>
    <dd>Nom pour l'instance de service.</dd>

    <dt>Nom de l'administrateur de base de données :</dt>
    <dd>ID utilisateur de l'administrateur de base de données (DBA).
    <p>**Remarque :** l'administrateur de base de données ne possède pas les droits superutilisateur. Les droits de l'administrateur de base de données se limitent à INHERIT, CREATEROLE, CREATEDB, LOGIN et REPLICATION.</p></dd>

    <dt>Mot de passe de l'administrateur de base de données :</dt>
    <dd>
    <p>Mot de passe pour l'ID utilisateur DBA. Vous devez créer un mot de passe fort avec les attributs suivants :
      <ul>
        <li>minimum de **15 caractères**</li>
        <li>au moins **un caractère majuscule**</li>
        <li>au moins **un caractère minuscule**</li>
        <li>au moins **un nombre**</li>
        <li>ne contient pas de nom d'utilisateur</li>
      </ul>
    </p>
    </dd>

    <dt>Confirmer le mot de passe :</dt>
    <dd>Confirmation du mot de passe pour l'ID utilisateur de l'administrateur de base de données.</dd>

    <dt>Contrat de licence :</dt>
    <dd>Après avoir lu le contrat de licence, cochez la case pour indiquer que vous acceptez les dispositions qu'il contient.</dd>

    <dt>Plans de tarification :</dt>
    <dd>Les plans de tarification offrent différentes catégories de tarification pour les bases de données de type PostgreSQL. Choisissez celui qui répond le mieux à vos besoins.</dd>
  </dl>
</li>
<li>Cliquez sur **Créer**.
<p>Après une boîte de dialogue vous indiquant que le déploiement du service peut être long, le tableau de bord Liste de ressources {{site.data.keyword.cloud_notm}} s'affiche. Vous pouvez voir l'instance de service que vous créez dans la section **Services**. Lorsque le statut du service est **mis à disposition**, l'instance est prête à être utilisée.</p>
</li>

<li>Sélectionnez le service pour afficher le tableau de bord {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.</li>
</ol>

Pour renforcer la sécurité, il est conseillé de mettre à jour le **mot de passe de l'administrateur de la base de données** immédiatement après la mise à disposition de l'instance de service. Vous devez suivre les mêmes règles que celles mentionnées précédemment pour définir le nouveau mot de passe.
{: note}

## Affichage de toutes les instances de service
{: #dbaas_webui_list_service}

Ouvrez le tableau de bord {{site.data.keyword.cloud_notm}} pour afficher la liste des instances de service créées :

<ol>
	<li>Cliquez sur le bouton à trois barres situées dans l'angle supérieur gauche de la console.</li>
	<li>Sélectionnez Tableau de bord.</li>
	<li>Sélectionnez Services.</li>
</ol>

## Affichage des informations détaillées relatives à une instance de service
{: #dbaas_webui_show_detail_service}

1. Cliquez sur le nom de l'instance cible pour afficher le tableau de bord du service.
2. Sélectionnez **Gérer** dans la barre de navigation de gauche pour afficher les informations générales dans la page à onglets **Présentation**.
3. Sélectionnez l'onglet **Instances** pour afficher des informations détaillées.


## Suppression d'une instance de service
{: #dbaas_webui_delete_service}

1. Affichez la liste de ressources {{site.data.keyword.cloud_notm}} en cliquant sur **Menu de navigation > Liste de ressources**.
2. Ouvrez **Service** pour afficher vos instances de service.
3. Sélectionnez l'instance de service que vous voulez supprimer.
4. Cliquez sur les trois points situés à droite.
5. Cliquez sur **Supprimer**.
