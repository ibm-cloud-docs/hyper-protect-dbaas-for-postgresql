---

copyright:
  years: 2019
lastupdated: "2019-10-23"

keywords: IAM, identity, access management, role

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Identity and Access Management roles and actions
{: #iam}

Access to {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instances is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Every user or service that accesses the {{site.data.keyword.ihsdbaas_postgresql_full}} service in your account must be assigned an access policy with an IAM role defined. The policy determines what actions a user or service can perform within the context of the service instance that you select. The allowable actions are customized and defined by {{site.data.keyword.ihsdbaas_postgresql_full}} as operations that are allowed to be performed on the service. The actions are then mapped to IAM roles.
{: shortdesc}

Two types of IAM roles can be assigned: platform management roles and service access roles. The following documentation focuses on service access roles defined by {{site.data.keyword.ihsdbaas_postgresql_full}}. For information about platform management roles, see [Platform management roles](/docs/iam?topic=iam-userroles#platformroles). For more information about IAM access, see [IAM sccess](/docs/iam?topic=iam-userroles).

## IAM service access roles
{: #service-access-roles}

The following tables outline what actions each service access role allows for the {{site.data.keyword.ihsdbaas_postgresql_full}} service.

| Service access role | Action description |
| --- |--- |
| Reader | Show cluster<br>List DB user<br>Show DB user<br>List DB<br>List DB logs |
| Writer | Show cluster<br>List DB user<br>Show DB user<br>List DB<br>List DB logs<br>Enable DBA logging<br>Enable DBA Monitoring<br>Create DB user<br>Delete DB user<br>Create DB<br>Delete DB<br> |
| Manager | Show cluster<br>List DB user<br>Show DB user<br>List DB<br>List DB logs<br>Enable DBA logging<br>Enable DBA Monitoring<br>Create DB user<br>Delete DB user<br>Create DB<br>Delete DB<br>Stop instance<br>Start instance<br>Restart instance<br>Get DB log |
{: caption="Table 1. IAM service access roles and actions}}"}

| Action description | Action |
| --- | --- |
| Show cluster | hyperp-dbaas-postgresql.clusters.read |
| Enable DBA logging | hyperp-dbaas-postgresql.logging.enable |
| Enable DBA Monitoring| hyperp-dbaas-postgresql.monitoring.enable |
| Create DB user | hyperp-dbaas-postgresql.users.create |
| Delete DB user | hyperp-dbaas-postgresql.users.delete |
| List DB user | hyperp-dbaas-postgresql.users.list |
| Show DB user | hyperp-dbaas-postgresql.users.read |
| Create DB | hyperp-dbaas-postgresql.databases.create |
| Delete DB | hyperp-dbaas-postgresql.databases.delete |
| List DB | hyperp-dbaas-postgresql.databases.list |
| Stop instance | hyperp-dbaas-postgresql.instances.stop |
| Start instance | hyperp-dbaas-postgresql.instances.start |
| Restart instance | hyperp-dbaas-postgresql.instances.restart |
| List DB logs | hyperp-dbaas-postgresql.logs.list |
| Get DB log | hyperp-dbaas-postgresql.logs.read |
{: caption="Table 1. IAM service access actions" caption-side="top"}

## Difference between IAM service access and database user privileges
{: #compare-IAM-dbuser-access}

IAM service access applies to {{site.data.keyword.ihsdbaas_postgresql_full}} service instances. It manages the authorization of the service APIs. Database user privileges (as you see on the **Users** tab in the service dashbaord) apply to databases within your database cluster.

## Managing access
{: #manage-access}

For detailed instructions on managing access to users or services, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser) or [Managing service ID access policies](/docs/iam?topic=iam-serviceidpolicy). To organize a set of users and service IDs into a single entity that makes it easy for you to assign access, see [Setting up access groups](/docs/iam?topic=iam-groups#create_ag).
