---

copyright:
  years: 2019
lastupdated: "2019-06-12"

keywords: backup, disaster recovery, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:tip: .tip}


# Sauvegarde et restauration de vos bases de données à l'aide de {{site.data.keyword.cos_full_notm}}
{: #backup_postgresql_databases}

Le service {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} déclenche automatiquement une sauvegarde de la totalité de votre base de données toutes les 24 heures. Ces sauvegardes chiffrées sont disponibles pour les 7 derniers jours et elles sont mises à disposition de manière redondante sur le stockage local dans toutes les zones de disponibilité de la région prise en charge.
{: shortdesc}

Si vous souhaitez augmenter vos capacités de reprise après incident et sauvegarder les données en dehors de la région prise en charge, vous pouvez utiliser le [service {{site.data.keyword.cos_full_notm}}](https://cloud.ibm.com/catalog/services/cloud-object-storage){: external} pour stocker vos données dans une autre région en vous référant aux étapes suivantes.

## Avant de commencer
{: #backup_postgresql_before_begin}

Pour utiliser les commandes {{site.data.keyword.postgresql}} afin de finaliser la sauvegarde, vous devez d'abord télécharger et installer {{site.data.keyword.postgresql}} sur votre machine. Pour plus d'informations, voir le [site Web {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Etape 1 : Création d'un fichier de vidage pour sauvegarder les bases de données d'origine
{: #step1_create_dump_file_backup_postgresql}

Utilisez la commande `pg_dump` suivante pour créer un fichier de vidage contenant les bases de données que vous souhaitez sauvegarder.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

Le tableau suivant présente les variables utilisées dans la commande :

|Variables|Description|Exemple|
|---------|-----------|-------|
|*host_name*|Serveur distant qui héberge les bases de données d'origine. Vous devez vous connecter à l'hôte afin d'obtenir les données. L'adresse hôte figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Numéro de port permettant d'établir une connexion à l'hôte. Le numéro de port figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|25050|
|*user_name*|Nom d'utilisateur permettant d'accéder aux bases de données d'origine. L'utilisateur doit disposer du privilège CONNECT sur la base de données et du privilège SELECT sur les tables.|my_user|
|*database_name*|Nom de la base de données que vous souhaitez sauvegarder.|my_database|
|*dump_file*|Fichier `.dump` dans lequel stocker les données d'origine. Vous pouvez utiliser des chemins relatifs ou absolus pour spécifier le fichier.|./pgdump.dump|
{: caption="Tableau 1. Variables nécessaires pour créer un fichier de vidage"}

Pour en savoir plus sur les privilèges utilisateur, voir la [documentation {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Etape 2 : Création d'une instance {{site.data.keyword.cos_full_notm}}
{: #step2_create_object_storage_backup_postgresql}

Vous devez créer l'instance dans une région différente de celle où l'instance de service {{site.data.keyword.ihsdbaas_postgresql_full}} est hébergée. Vous pouvez vous reporter aux étapes suivantes :

1. [Créez une instance Cloud {{site.data.keyword.cos_short}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-provision).
2. [Créez un compartiment](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints#endpoints-region) dans une autre région.
3. [Créez des données d'identification de service](/docs/services/cloud-object-storage?topic=cloud-object-storage-service-credentials) et enregistrez les identifiants `access_key_id` et `secret_access_key` pour une utilisation ultérieure.
4. Installez un client S3.
5. Utilisez le client S3 et les clés d'accès pour vous connecter au noeud final de Cloud {{site.data.keyword.cos_short}} du compartiment que vous avez créé précédemment.
6. Utilisez le client S3 pour [télécharger le fichier de sauvegarde {{site.data.keyword.postgresql}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-upload) que vous avez créé à l'[étape 1](#step1_create_dump_file_backup_postgresql) dans le compartiment.

Pour plus d'informations, vous pouvez vous reporter à la [documentation {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started).

Une fois cette étape terminée, vous avez sauvegardé vos données dans une instance Cloud {{site.data.keyword.cos_short}} dans une autre région. Si vous souhaitez restaurer les données de l'instance Cloud {{site.data.keyword.cos_short}} dans une instance {{site.data.keyword.ihsdbaas_postgresql_full}}, consultez l'étape 3 suivante pour plus de détails.

## Etape 3 : restaurez les données de l'instance Cloud {{site.data.keyword.cos_short}} dans une instance {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step3_restore_data_from_cos_postgresql}

Vous devez d'abord télécharger le fichier de sauvegarde du compartiment Cloud {{site.data.keyword.cos_short}} vers votre machine locale, puis utiliser la commande `psql` pour restaurer les données.

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

Le tableau suivant présente les variables utilisées dans la commande :

|Variables|Description|Exemple|
|---------|-----------|-------|
|*host_name*|Serveur de gestionnaire DBaaS qui héberge le cluster cible. L'adresse hôte figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Numéro de port permettant d'établir une connexion à l'hôte. Le numéro de port figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|25003|
|*user_name*|Nom d'utilisateur permettant d'accéder à la base de données cible.|new_user|
|*database_name*|Il peut s'agir de n'importe quelle base de données sur laquelle l'utilisateur dispose du privilège CONNECT. La session `psql` bascule automatiquement vers la base de données cible dans laquelle vous souhaitez restaurer les données.|my_database|
|*dump_file*|Fichier `.dump` que vous téléchargez à partir de votre compartiment Cloud {{site.data.keyword.cos_short}}. Vous pouvez utiliser des chemins relatifs ou absolus pour spécifier le fichier.|./pgdump.dump|
{: caption="Tableau 2. Variables nécessaires pour restaurer les données à partir d'un fichier de vidage"}

## Etapes suivantes
{: #whats_next_backup_postgresql}

Après l'[étape 3](#step3_restore_data_from_cos_postgresql), vous pouvez vous connecter au cluster de base de données pour vérifier si la restauration des données a abouti.
