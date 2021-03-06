---

copyright:
  years: 2020, 2021
lastupdated: "2021-05-17"

keywords: data encryption, data security, Hyper Protect DBaaS, postgresql, BYOK, KYOK

subcollection: hyper-protect-dbaas-for-postgresql

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Securing your data in {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #data-security}

{{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} is a public multi-tenant cloud database service. It implements security protections at all levels, including workload isolation, data encryption (Keep Your Own Key), and identity and administration access control, to ensure that your data is protected in a multi-tenancy environment. Learn more in the following documentation about how your data is protected and how you can securely delete your data.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #data-storage}

{{site.data.keyword.ihsdbaas_postgresql_full}} uses the following methods to protect your data.

- Built on [{{site.data.keyword.IBM_notm}} Secure Service Container technology](https://www.ibm.com/us-en/marketplace/secure-service-container){: external}, {{site.data.keyword.ihsdbaas_postgresql_full}} provides workload isolation, restricted administrator access and tamper protection for data at rest and in flight. Not even the cloud administrator has access to your data at any point.
- All {{site.data.keyword.ihsdbaas_postgresql_full}} connections use TLS/SSL encryption for data in transit. The current supported version of this encryption is TLS 1.2.
- Access to the {{site.data.keyword.cloud_notm}} account, {{site.data.keyword.ihsdbaas_postgresql_full}} management web user interface, CLI, and API is secured via [{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM)](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam).
- Access to the database is secured and managed through the standard access controls provided by the database. All database access controls are unavailable in the service interfaces. IAM users are not able to authenticate to the database itself. This separation provides a higher isolation for your environment. 
- All {{site.data.keyword.ihsdbaas_postgresql_full}} storage is provided on storage encrypted with LUKS using AES-256. The default keys are managed within the locked down environment within [Secure Service Containers](https://www.ibm.com/us-en/marketplace/secure-service-container){: external}. Bring Your Own Key (BYOK) for encryption is also available through [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok), and Keep Your Own Key (KYOK) through [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok).

## Protecting your sensitive data in {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #data-encryption}

The data that you store in {{site.data.keyword.ihsdbaas_postgresql_full}} databases is encrypted by default by randomly generated keys. If you need full control over your encryption keys, you can enable [integration with {{site.data.keyword.keymanagementserviceshort}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) or [{{site.data.keyword.hscrypto}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok) when you create a service instance.

### About customer-managed keys
{: #about-encryption-keys}

{{site.data.keyword.ihsdbaas_postgresql_full}} uses envelope encryption to implement customer-managed keys. Envelope encryption describes encrypting one encryption key with another encryption key. The key used to encrypt the actual data is known as a data encryption key (DEK). The DEK itself is never stored but is wrapped by a second key that is known as the key encryption key (KEK) to create a wrapped DEK. To decrypt data, the wrapped DEK is unwrapped to get the DEK. This process is possible only by accessing the KEK, which in this case is your [root key](#x6946961){: term} that is stored in {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.hscrypto}}.
![Creating a wrapped DEK](images/Wrapped_DEK.svg "Creating a wrapped DEK"){: caption="Figure 1. Creating a wrapped DEK" caption-side="bottom"}

{{site.data.keyword.keymanagementserviceshort}} keys are secured by FIPS 140-2 Level 3 certified cloud-based [hardware security modules (HSMs)](#x6704988){: term}. {{site.data.keyword.hscrypto}} keys are secured by FIPS 140-2 Level 4-certified cloud-based HSMs, the highest security level for cloud-based HSMs.

### Enabling customer-managed keys for {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #bring-keep-your-own-key}

For detailed instructions on enabling customer-managed keys, see [{{site.data.keyword.keymanagementservicelong_notm}} integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok) or [{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} integration](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok), depending on which service you choose to use.

## Deleting your data in {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #data-delete}

### Deleting service instances
{: #service-delete}

You can delete your service instance through the [UI](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-manage-service#webui-manage-service), [CLI](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete), and [API](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#delete-a-service-instance){: external}.

When the service instance is deleted in these ways, it's **disabled** (pending reclamation) rather than deleted completely. You can't find deleted service instances in your service instance list. All your data in {{site.data.keyword.ihsdbaas_full}} components is cleaned up after the retention period of seven days. The data in the [services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-service-integration) that you integrate with {{site.data.keyword.ihsdbaas_postgresql_full}} isn't deleted. See their respective documentation to delete the data if necessary.

In some cases, two nodes in your service instance are disabled at first, which is considered successful disabling. The pending node will be disabled automatically later. This tolerance situation (with one pending node to be disabled) doesn't affect the permanent deletion of service instances (described in the following paragraph) or the [restoration of service instances](#service-restore).
{: note}

You can permanently delete the service instance by using the [`ibmcloud resource reclamation-delete` command](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_delete). You can't restore the service instance afterward.

### Restoring service instances
{: #service-restore}

You can restore a deleted service instance with no data loss within the retention period of **seven days**. After seven days, the service instance is permanently deleted.

Use the [{{site.data.keyword.cloud_notm}} resource reclamation CLI commands](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamations) to list service instances in the retention period and restore a service instance.

The service instance in the retention period is not billed to your account. The billing starts again when the service instance is restored. 

In some cases, two nodes in your service instance are restored at first, which is considered successful restoration. The pending node will be restored automatically later.
{: note}

### Deleting and restoring databases
{: #database-delete-restore}

To delete databases, use your database client. For options to back up your databases, see [Backing up and restoring your databases by using IBM Cloud Object Storage](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-backup_postgresql_databases) and [Restoring your databases by {{site.data.keyword.IBM_notm}} Support](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-restore_postgresql_databases).

### Deleting keys
{: #key-delete}

If you enabled KYOK or BYOK, when you delete the key that is used to encrypt your service, you lose access to the data. For more information, see [Removing {{site.data.keyword.hscrypto}} keys](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-hpcs-byok#hpcs-remove-key) or [Removing {{site.data.keyword.keymanagementserviceshort}} keys](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-key-protect-byok#kp-remove-key).
