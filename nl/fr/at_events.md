---

copyright:
  years: 2019
lastupdated: "2019-06-19"

keywords: Activity tracker events

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

# Evénements {{site.data.keyword.cloudaccesstrailshort}}
{: #activity-tracker-events}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour savoir comment les utilisateurs et les applications interagissent avec {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités initiées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour avoir des informations sur la mise à disposition du service {{site.data.keyword.cloudaccesstrailshort}}, consultez la [documentation {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started). Le service {{site.data.keyword.ihsdbaas_postgresql_full}} étant actuellement disponible dans le centre de données de Dallas, veillez à sélectionner la région **us-south** pour capturer les journaux.

## Liste des événements
{: #list-activity-tracker-events}

Le tableau suivant répertorie les actions qui génèrent un événement :

| Action                 | Description                               |
| ---------------------- | ----------------------------------------- |
| `cluster.create` | Création d'un cluster de base de données                 |
| `cluster.delete` | Suppression d'un cluster de base de données                 |
| `database.create` | Création d'une base de données                  |
| `database.delete` | Suppression d'une base de données                  |
| `user.create`     | Création d'un utilisateur de base de données                    |
| `user.delete`     | Suppression d'un utilisateur de base de données                    |
| `instance.start` | Démarrage d'une instance de service de base de données         |
| `instance.stop`  | Arrêt d'une instance de service de base de données          |
| `instance.restart`  | ReDémarrage d'une instance de service de base de données          |
| `log.get`       | Téléchargement d'un fichier journal |
{: caption="Tableau 1. Actions qui génèrent des événements {{site.data.keyword.cloudaccesstrailfull_notm}}"}

Pour l'événement `cluster.create` et `cluster.delete`, le service {{site.data.keyword.cloudaccesstrailfull_notm}} n'enregistre pas le nom du compte et l'adresse IP de l'utilisateur qui effectue l'action. La valeur d'`initiator.name` et `host.address` dans le journal indique l'ID de service de Cloud Broker et l'adresse IP de Cloud Broker, respectivement.
{: note}

## Où consulter les événements
{: #view-activity-tracker-events}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}}, lui-même disponible dans la région {{site.data.keyword.cloud_notm}} où les événements sont générés.
