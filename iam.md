---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-23"

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
{:term: .term}
{:important: .important}

# Managing access for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #iam}

As the owner of your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance, you can assign access to other users or services to use your service instance.
{: shortdesc}

Access to {{site.data.keyword.ihsdbaas_postgresql_full}} service instances is controlled by {{site.data.keyword.cloud_notm}} [Identity and Access Management (IAM)](#x7547040){: term}. Every user or service that accesses the {{site.data.keyword.ihsdbaas_postgresql_full}} service in your account must be assigned an [access policy](#x2853407){: term} with an IAM role defined. The policy determines what actions a user or service can perform within the context of the service instance that you select. The allowable actions are customized and defined by {{site.data.keyword.ihsdbaas_postgresql_full}} as operations that are allowed to be performed on the service. The actions are then mapped to IAM roles.

Two types of IAM roles can be assigned: platform management roles and service access roles. The following documentation focuses on service access roles that are defined by {{site.data.keyword.ihsdbaas_postgresql_full}}. For more information about platform management roles, see [Platform management roles](/docs/account?topic=account-userroles#platformroles). For more information about IAM access, see [IAM access](/docs/account?topic=account-userroles).

## IAM service access roles
{: #service-access-roles}

The following tables outline what actions each service access role allows for the {{site.data.keyword.ihsdbaas_postgresql_full}} service.

| Action | Reader | Writer | Manager |
|-----|-----|-----|----|
| Get DB cluster details | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| List DB users | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Get DB user details | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| List DBs | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| List DB log files | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Download a DB log file | | | ![Check mark icon](../icons/checkmark-icon.svg) |
| Enable DB logging | | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Enable DB Monitoring | | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Scale cluster resources | | | ![Check mark icon](../icons/checkmark-icon.svg) |
| Show DB configuration | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Update DB configuration | | | ![Check mark icon](../icons/checkmark-icon.svg) |
| List cluster tasks | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
| Get cluster task details | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) | ![Check mark icon](../icons/checkmark-icon.svg) |
{: caption="Table 1. IAM service access roles and actions" caption-side="top"}

| Action Description | Action |
| --- | --- |
| Get DB cluster details | hyperp-dbaas-postgresql.clusters.read |
| List DB users | hyperp-dbaas-postgresql.users.list |
| Get DB user details | hyperp-dbaas-postgresql.users.read |
| List DBs | hyperp-dbaas-postgresql.databases.list |
| List DB log files | hyperp-dbaas-postgresql.logs.list |
| Download a DB log file | hyperp-dbaas-postgresql.logs.read |
| Enable DB logging | hyperp-dbaas-postgresql.logging.enable |
| Enable DB Monitoring| hyperp-dbaas-postgresql.monitoring.enable |
| Show DB configuration | hyperp-dbaas-postgresql.clusters.configuration.read |
| Update DB configuration | hyperp-dbaas-postgresql.clusters.configuration.update |
| Scale cluster resources | hyperp-dbaas-postgresql.clusters.resource.scale |
| List cluster tasks | hyperp-dbaas-postgresql.clusters.tasks.list |
| Get cluster task details | hyperp-dbaas-postgresql.clusters.tasks.read |
{: caption="Table 2. IAM service access actions" caption-side="top"}

## Difference between IAM service access and database user privileges
{: #compare-IAM-dbuser-access}

IAM service access applies to {{site.data.keyword.ihsdbaas_postgresql_full}} service instances. It manages the authorization of the service APIs. Database user privileges (as you see on the **Users** page in the service dashboard) apply to databases within your database cluster.

## Managing IAM access for users or services
{: #manage-access}

For detailed instructions on managing access for users or services, see [Managing access to resources](/docs/account?topic=account-assign-access-resources). To organize a set of users and service IDs into a single entity that makes it easy for you to assign access, see [Setting up access groups](/docs/account?topic=account-groups).

Expect a maximum 10-minute interval before the IAM authorization change is refreshed.

## Managing access to multiple instances
{: #manage-multiple-instances}

If you have multiple {{site.data.keyword.ihsdbaas_postgresql_full}} instances in different accounts, you might need to leverage {{site.data.keyword.cloud_notm}} enterprises to manage accounts and user access.

1. **Create the enterprise hierarchy**

  {{site.data.keyword.cloud_notm}} enterprises enable you to centrally manage multiple accounts and resources. You can create an enterprise hierarchy as needed by nesting account groups or accounts within the enterprise account. The access management to the enterprise and its child accounts is isolated to provide greater security. To learn how to create an enterprise and add accounts to an enterprise, see [Setting up an enterprise](/docs/account?topic=account-enterprise-tutorial) and [Best practices for setting up an enterprise](/docs/account?topic=account-enterprise-best-practices).

2. **Organize account resources in resource groups**

  {{site.data.keyword.ihsdbaas_postgresql_full}} instances are associated with child accounts of the enterprise. Within each account, you can organize service instances in resource groups so that you can assign different access policies to each resource group to enable independent access control. For how to create resource groups and organize resources, see [Best practices for organizing resources](/docs/account?topic=account-account_setup).

3. **Assign access to manage the enterprise and resources**

  Based on the {{site.data.keyword.ihsdbaas_postgresql_full}} IAM platform roles and [service access roles](#service-access-roles) listed above, you can assign users respective access to each tier of the enterprise hierarchy. For more information about assigning access to resources, see [Managing IAM access for users or services](#manage-access). For more information about assigning access to your enterprise account, see [User management for enterprises](/docs/account?topic=account-enterprise-access).

4. **Use {{site.data.keyword.cloud_notm}} API keys**

  You can create [{{site.data.keyword.cloud_notm}} API keys](/docs/account?topic=account-manapikey) for users or services to track and control API usage. The user API key is associated with the user identity and inherits all access that the user is assigned. The service API key is granted the access that is associated with a specific service ID. API keys can also be used to [generate IAM tokens](/docs/account?topic=account-iamtoken_from_apikey) for API calls authentication. For how to manage API keys, see [Managing user API keys](/docs/account?topic=account-userapikey) and [Managing service ID API keys](/docs/account?topic=account-serviceidapikeys).

The following example shows how to use the enterprise to manage multiple instances and user access. Assume that your organization has two {{site.data.keyword.ihsdbaas_postgresql_full}} instances for development and production, and two separate teams that manage and operate the instances. You can create the following enterprise hierarchy to better manage accounts, instances, and user access:

![An example of the enterprise hierarchy and user access management](/images/enterprise_hierarchy_example.svg "An example of the enterprise hierarchy and user access management"){: caption="Figure 1. An example of the enterprise hierarchy and user access management" caption-side="bottom"}

- Use separate accounts and distinct resource groups to manage instances for development purpose and production purpose.
- Assign users the minimum access to the corresponding resources. For example, assign the enterprise managers the administrator role for accounts and billing management; assign the developer team members the editor and manager roles for performing operations towards the development instance; assign other members the viewer and reader role only for viewing instance resources.
