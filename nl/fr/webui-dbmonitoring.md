---

copyright:
  years: 2019
lastupdated: "2019-06-13"

keywords: database monitoring, database cluster, database metrics

subcollection: hyper-protect-dbaas-for-postgresql

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Surveillance de base de données
{: #dbaas-webui-database-monitor}

Après avoir activé la surveillance de base de données, vous pouvez afficher les métriques de base de données à l'aide de Grafana.
{: shortdesc}

## Avant de commencer
{: #webui-database-monitoring-byb}

1.  Vérifiez que vous avez accès à une organisation et un espace Cloud Foundry à Dallas (us-south).
    Pour savoir comment obtenir ce type d'accès, voir [Gestion de l'accès Cloud Foundry](https://cloud.ibm.com/docs/iam?topic=iam-mngcf#mngcf){: external}.

2.  Assurez-vous que toutes les instances du cluster de base de données sont en cours d'exécution.

3.  Dans le tableau de bord {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}, sélectionnez l'onglet Surveillance.

## Activation de la surveillance de base de données
{: #webui-enable-database-monitoring}

Si le message **La surveillance est désactivée** s'affiche dans l'onglet Surveillance :

1. Cliquez sur **Activer**.
2. Dans la fenêtre Activer la surveillance, sélectionnez votre organisation et votre espace, puis cliquez sur **Soumettre**.


## Affichage des métriques de base de données
{: #webui-view-database-metrics}

Deux méthodes permettent d'afficher les métriques dans Grafana :

- Copiez le lien affiché, puis ouvrez un nouvel onglet ou une nouvelle fenêtre et collez le lien vers le navigateur.
- Cliquez sur **Afficher dans Grafana**.

Pour afficher les métriques dans un nouveau tableau de bord dans Grafana, sélectionnez l'icône Grafana située dans l'angle supérieur gauche, puis sélectionnez **Tableaux de bord > Nouveau**.
L'affichage de votre ID de cluster de base de données et de vos ID d'instance peut prendre un certain temps et vous devrez peut-être recharger le tableau de bord.

Pour plus d'informations sur l'utilisation de Grafana, voir [Surveillance de {{site.data.keyword.cloud_notm}}](/docs/services/cloud-monitoring?topic=cloud-monitoring-getting-started).
