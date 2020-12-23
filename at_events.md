---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-23"

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Auditing events for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #activity-tracker-events}

Use the {{site.data.keyword.cloud}} {{site.data.keyword.at_short}} service to track how users and applications interact with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.cloudaccesstrailshort}}](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).

## Viewing events
{: #view-activity-tracker-events}
{: help}
{: support}

To view events of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have an {{site.data.keyword.cloudaccesstrailshort}} instance in the same region, except for `Sydney (au-syd)`, as the following table shows:

{{site.data.keyword.ihsdbaas_postgresql_full}} Region | {{site.data.keyword.cloudaccesstrailshort}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Dallas (us-south)`
{: caption="Table 1. {{site.data.keyword.cloudaccesstrailshort}} regions" caption-side="top"}

1. [Provision an {{site.data.keyword.cloudaccesstrailshort}} instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision) if you don't have one. {{site.data.keyword.cloudaccesstrailshort}} can have only one instance per location.

2. To view events, access the web UI of the corresponding {{site.data.keyword.cloudaccesstrailshort}} instance. For detailed instructions, see [Launching the web UI through the {{site.data.keyword.cloud_notm}} UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch#launch_cloud_ui). You can apply search and filtering criteria to define the events that are displayed through a [custom view](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-views).

## List of events
{: #list-activity-tracker-events}

The following table lists the actions that generate an event:

| Action                 | Description                               |
| ---------------------- | ----------------------------------------- |
| `hyperp-dbaas-postgresql.cluster.create` | Create a database cluster |
| `hyperp-dbaas-postgresql.cluster.delete` | Delete a database cluster 
| `hyperp-dbaas-postgresql.log.get`       | Download a log file |
| `hyperp-dbaas-postgresql.logging.enable` | Enable logging for the cluster |
| `hyperp-dbaas-postgresql.monitoring.enable` | Enable monitoring for the cluster |
| `hyperp-dbaas-postgresql.cluster.resource.scale` | Scale cluster resources | 
| `hyperp-dbaas-postgresql.configuration.update` | Update PosgreSQL configuration settings |
| `hyperp-dbaas-postgresql.database.restore` | Restore databases by SRE as delegated by service instance owner |
{: caption="Table 1. Actions that generate {{site.data.keyword.cloudaccesstrailshort}} events"}

For the events of `hyperp-dbaas-postgresql.cluster.create` and `hyperp-dbaas-postgresql.cluster.delete`, the {{site.data.keyword.cloudaccesstrailshort}} service doesn't record the account name and IP address of the user who performs the action. The values of `initiator.name` and `host.address` in the log indicate the service ID of Cloud Broker and the IP address of Cloud Broker. For the event of `hyperp-dbaas-postgresql.database.restore`, the value of `initiator.name` is `dbaas.sre@de.ibm.com`.
{: note}
