---

copyright:
  years: 2019
lastupdated: "2019-06-10"

keywords: database instance, DBaaS dashboard

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}


# Instances de base de données
{: #dbaas-webui-database-instances}

## Avant de commencer
{: #webui-database-instances-byb}

Dans le tableau de bord {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, sélectionnez l'onglet Instances.

## Démarrage d'une instance de base de données
{: #webui-start-database-instance}

1. Sélectionnez l'instance de base de données.
2. Cliquez sur les trois points situés à la fin de la ligne, puis sélectionnez **Démarrer**.

## Arrêt d'une instance de base de données
{: #webui-stop-database-instance}

1. Sélectionnez l'instance de base de données.
2. Cliquez sur les trois points situés à la fin de la ligne, puis sélectionnez **Arrêter**. S'il s'agit d'un noeud principal, vous pouvez également sélectionner **Forcer l'arrêt**.

## Redémarrage d'une instance de base de données
{: #webui-restart-database-instance}

1. Sélectionnez l'instance de base de données.
2. Cliquez sur les trois points situés à la fin de la ligne, puis sélectionnez **Redémarrer**.

## Téléchargement du journal
{: #webui-download-log}

1. Sélectionnez l'instance de base de données.
2. Sélectionnez la **date de début** et la **date de fin** pour filtrer les journaux par heure.
3. Sélectionnez les journaux que vous souhaitez télécharger en cliquant sur la **case à cocher** en regard du nom du journal.
4. Cliquez sur le bouton **Télécharger**.

## Vérification du statut de l'instance
{: #webui-check-instance-status}

Le point coloré sur le panneau d'instance indique le statut de l'instance. Vous pouvez vous reporter au tableau suivant pour vérifier le statut de l'instance.

|Couleur|Statut|Action|
|-----|------|------|
|Vert|L'instance est en cours d'exécution.|Vous pouvez arrêter ou redémarrer l'instance.|
|Jaune|L'instance est arrêtée.|Vous pouvez démarrer l'instance.|
|Rouge|L'instance est en échec.|Vous pouvez vous reporter à [Aide et assistance](/docs/services/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-getting-help-and-support).|
{: caption="Tableau 1. Couleur de statut"}
