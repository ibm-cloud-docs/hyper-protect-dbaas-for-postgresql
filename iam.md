---

copyright:
  years: 2019
lastupdated: "2019-08-28"

keywords: IAM, identity, access management, role

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

# Identity and Access Management roles and actions
{: #iam}

Access to {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instances for users in your account is controlled by {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Every user that accesses the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} service in your account must be assigned an access policy with an IAM role defined. The policy determines what actions a user can perform within the context of the service or instance that you select. The allowable actions are customized and defined by the {{site.data.keyword.cloud_notm}} service as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles.
{: shortdesc}

Policies enable access to be granted at different levels. Some of the options include the following:

* Access across all instances of the service in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance

After you define the scope of the access policy, you assign a role that determines the user's level of access. Review the following tables which outline what actions each role allows within the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} service.

The following table details actions that are mapped to platform management roles. Platform management roles enable users to perform tasks on service resources at the platform level, for example assign user access for the service, create or delete instances, and bind instances to applications.

|Platform management role|Description of actions|Example actions                                                 |
|------------------------|----------------------|----------------------------------------------------------------|
|Viewer                  |Can view service instances, but can't modify them|<ul><li>List clusters</li><li>View details for a cluster</li></ul>|
|Editor                  |Perform all platform actions except for managing the account and assigning access policies|<ul><li>Bind a service to a cluster</li></ul>|
|Operator                |Perform platform actions required to configure and operate service instances, such as viewing a service's dashboard|<ul><li>Bind a service to a cluster</li></ul>|
|Administrator           |Perform all platform actions based on the resource this role is being assigned, including assigning access policies to other users|<ul><li>Remove a cluster</li><li>Create a cluster</li><li>Update user access policies</li><li>All actions a viewer, editor, and operator can perform</li></ul>|
{: caption="Table 1. IAM user roles and actions"}

<!--
The following table details actions that are mapped to service access roles. Service access roles enable users access to {{site.data.keyword.ihsdbaas_postgresql_full}} as well as the ability to call the {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}} API.

| Service access role | Description of actions | Example actions                                                 |
|---------------------|------------------------|-----------------------------------------------------------------|
| Reader              | Description            | <ul><li>Example 1</li><li>Example 2</li></ul>                   |
| Writer              | Description            |<ul><li>Example 1</li><li>Example 2</li></ul>                    |
| Manager             | Description            | <ul><li>Example 1</li><li>Example 2</li><li>Example 3</li></ul> |
{: caption="Table 2. IAM service access roles and actions" caption-side="top"}
-->

For information about assigning user roles in the UI, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser#iammanidaccser).
