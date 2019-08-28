---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: migrate, beta, restore

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Migration de bases de données {{site.data.keyword.postgresql}} vers {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #migration_postgre}

Si vous utilisez des bases de données {{site.data.keyword.postgresql}} et souhaitez les faire migrer vers {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, lisez cette rubrique. Peu importe où vos bases de données {{site.data.keyword.postgresql}} sont hébergées à partir du moment où la plateforme fournit des services de base de données {{site.data.keyword.postgresql}}.
{: shortdesc}

## Avant de commencer
{: #migration_postgre_before_begin}

Pour utiliser les commandes {{site.data.keyword.postgresql}} afin de finaliser la migration, vous devez d'abord télécharger et installer {{site.data.keyword.postgresql}} sur votre machine. Pour plus d'informations, voir le [site Web {{site.data.keyword.postgresql}}](https://www.postgresql.org/download/){: external}.

## Etape 1 : Création d'un fichier de vidage pour restaurer les bases de données d'origine
{: #step1_create_dump_file}

Utilisez la commande `pg_dump` suivante pour créer un fichier de vidage contenant les bases de données que vous souhaitez restaurer.

```
pg_dump -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

Le tableau suivant présente les variables utilisées dans la commande :

|Variables|Description|Exemple|
|---------|-----------|-------|
|*host_name*|Serveur distant qui héberge les bases de données d'origine. Vous devez vous connecter à l'hôte afin d'obtenir les données. Si vos bases de données sont déployées dans une instance bêta de {{site.data.keyword.ihsdbaas_full}}, l'adresse hôte figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Numéro de port permettant d'établir une connexion à l'hôte. Si vos bases de données sont déployées dans une instance bêta de {{site.data.keyword.ihsdbaas_full}}, le port figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|25050|
|*user_name*|Nom d'utilisateur permettant d'accéder aux bases de données d'origine. L'utilisateur doit disposer du privilège CONNECT sur la base de données et du privilège SELECT sur les tables.|my_user|
|*database_name*|Nom de la base de données que vous souhaitez faire migrer.|my_database|
|*dump_file*|Fichier `.dump` dans lequel stocker les données d'origine. Vous pouvez utiliser des chemins relatifs ou absolus pour spécifier le fichier.|./pgdump.dump|
{: caption="Tableau 1. Variables nécessaires pour créer un fichier de vidage"}

Pour en savoir plus sur les privilèges utilisateur, voir la [documentation {{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-grant.html){: external}.

## Etape 2 : Création d'une nouvelle instance de service dans {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #step2_creat_new_service_instance}

Avant de restaurer les données, vous devez créer une nouvelle instance de service dans {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} comme cluster de base de données cible. Vous pouvez utiliser l'une des méthodes suivantes pour créer une nouvelle instance de service :
- L'[interface utilisateur Web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_webui_service#dbaas_webui_create_service)
- Les [API DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-an-ibm-cloud-service-instance-of-hyperprote){: external}
- Le [plug-in CLI avec l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_create_service)

Lorsque vous créez la nouvelle instance de service, vous devez définir le nom du cluster, ainsi que le nom et le mot de passe de l'administrateur. Ils ne doivent pas nécessairement être identiques à ceux de votre instance d'origine. Cela n'affecte pas la migration. Une fois la migration terminée, les bases de données sont affectées au nouvel administrateur.

## Etape 3 : Création de bases de données dans la nouvelle instance de service
{: #step3_create_database}

Après avoir créé la nouvelle instance de service, vous devez créer de nouvelles bases de données. Celles-ci doivent avoir le même nom que les bases de données d'origine. L'utilisateur doit disposer du privilège CREATE et ne doit pas nécessairement être le même que celui qui a créé le fichier de vidage. Vous pouvez utiliser l'une des méthodes suivantes pour exécuter la tâche :
- L'[interface utilisateur Web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-databases#webui-create-database)
- Les [API DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-a-database-in-database-cluster){: external}
- Le [plug-in CLI avec l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#db_create)

Vous pouvez utiliser les méthodes suivantes pour créer des utilisateurs : [l'interface utilisateur Web](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas-webui-database-users#webui-create-database-user), [les API DBaaS Manager](https://{DomainName}/apidocs/hyperp-dbaas#create-a-user-in-a-database-cluster){: external}, [le plug-in CLI avec l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#user_create) et la commande [{{site.data.keyword.postgresql}}](https://www.postgresql.org/docs/10/sql-createuser.html){: external}.
{: tip}

## Etape 4 : Restauration des données depuis le fichier de vidage dans un nouvelle instance de service
{: #step4_restore_data}

Utilisez la commande `psql` pour restaurer les données du fichier de vidage qui est créé à l'[étape 1](#step1_create_dump_file).

```
psql -h <host_name> -p <port> -U <user_name> -d <database_name> -f <dump_file>
```
{: pre}

Le tableau suivant présente les variables utilisées dans la commande :

|Variables|Description|Exemple|
|---------|-----------|-------|
|*host_name*|Serveur de gestionnaire DBaaS qui héberge le cluster cible. L'adresse hôte figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|4e.52.37a9.ip4.static.sl-reverse.com|
|*port*|Numéro de port permettant d'établir une connexion à l'hôte. Le numéro de port figure sur la page de présentation de l'interface utilisateur d'instance de cluster.|25003|
|*user_name*|Nom d'utilisateur permettant d'accéder à la base de données cible. Vous pouvez utiliser le même utilisateur que celui qui crée la base de données cible à l'[étape](#step3_create_database).|new_user|
|*database_name*|Il peut s'agir de n'importe quelle base de données sur laquelle l'utilisateur dispose du privilège CONNECT. La session `psql` passe automatiquement à la base de données cible qui est créée à l'[étape 3](#step3_create_database).|my_database|
|*dump_file*|Fichier `.dump` que vous avez créé à l'[étape 1](#step1_create_dump_file). Vous pouvez utiliser des chemins relatifs ou absolus pour spécifier le fichier.|./pgdump.dump|
{: caption="Tableau 2. Variables nécessaires pour restaurer les données à partir d'un fichier de vidage"}

## Etapes suivantes
{: #whats_next_migration_postgre}

Après la migration, vous pouvez vous connecter au nouveau cluster de base de données pour vérifier si la migration des données a abouti.
