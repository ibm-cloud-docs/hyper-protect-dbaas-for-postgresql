---

copyright:
  years: 2019
lastupdated: "2019-09-23"

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

# {{site.data.keyword.cloudaccesstrailshort}} events
{: #activity-tracker-events}

Use the {{site.data.keyword.at_full}} service to track how users and applications interact with {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailshort}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [getting started tutorial for {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Viewing events
{: #view-activity-tracker-events}

{{site.data.keyword.cloudaccesstrailshort}} integration is available for {{site.data.keyword.ihsdbaas_postgresql_full}} deployments according to the following table.

Deployment Region | {{site.data.keyword.cloudaccesstrailshort}} Region
----------|-----------
`Dallas (us-south)` | `Dallas (us-south)`
`Frankfurt (eu-de)` | `Frankfurt (eu-de)`
`Sydney (au-syd)` | `Dallas (us-south)`
{: caption="Table 1. {{site.data.keyword.cloudaccesstrailshort}}" caption-side="top"}

To view events of your {{site.data.keyword.ihsdbaas_postgresql_full}} instance, you need to have an {{site.data.keyword.cloudaccesstrailshort}} instance in the same region, with the exception of `Sydney (au-syd)`. For {{site.data.keyword.ihsdbaas_postgresql_full}} instances in Sydney, you need to have an {{site.data.keyword.cloudaccesstrailshort}} instance in Dallas.

{{site.data.keyword.cloudaccesstrailshort}} can have only one instance per location. To view events, you must access the web UI of the corresponding {{site.data.keyword.cloudaccesstrailshort}} instance. For detailed instructions, see [Launching the web UI through the {{site.data.keyword.cloud_notm}} UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## List of events
{: #list-activity-tracker-events}

The following table lists the actions that generate an event:

| Action                 | Description                               |
| ---------------------- | ----------------------------------------- |
| `hyperp-dbaas-postgresql.cluster.create` | Create a database cluster                 |
| `hyperp-dbaas-postgresql.cluster.delete` | Delete a database cluster                 |
| `hyperp-dbaas-postgresql.database.create` | Create a database                  |
| `hyperp-dbaas-postgresql.database.delete` | Delete a database                  |
| `hyperp-dbaas-postgresql.user.create`     | Create a database user                    |
| `hyperp-dbaas-postgresql.user.delete`     | Delete a database user                    |
| `hyperp-dbaas-postgresql.instance.start` | Start a database service instance         |
| `hyperp-dbaas-postgresql.instance.stop`  | Stop a database service instance          |
| `hyperp-dbaas-postgresql.instance.restart`  | Restart a database service instance          |
| `hyperp-dbaas-postgresql.log.get`       | Download a log file |
{: caption="Table 1. Actions that generate {{site.data.keyword.cloudaccesstrailshort}} events"}

For the event of `hyperp-dbaas-postgresql.cluster.create` and `hyperp-dbaas-postgresql.cluster.delete`, the {{site.data.keyword.cloudaccesstrailshort}} service does not record the account name and IP address of the user who performs the action. The value of `initiator.name` and `host.address` in the log indicates the service ID of Cloud Broker and the IP address of Cloud Broker respectively.
{: note}
