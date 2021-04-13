---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-13"

keywords: service endpoints for Hyper Protect DBaaS, private network for Hyper Protect DBaaS

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


# Securing your connection to {{site.data.keyword.ihsdbaas_postgresql_full}}
{: #service-connection}

To ensure that you have enhanced control and security over your data when you use {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}}, you have the option of using private routes to {{site.data.keyword.cloud_notm}} service endpoints. 
{: shortdesc}

You can choose one of the following options when you create a service instance of {{site.data.keyword.cloud_notm}} {{site.data.keyword.ihsdbaas_postgresql_full}}:
- Public endpoints
- Private endpoints
- Both public and private endpoints

{{site.data.keyword.ihsdbaas_postgresql_full}} doesn't support changing your service endpoint configuration after service creation for now. If you choose both public and private endpoints, you can connect with either of them; public endpoints can't be disabled later.
{: note}

Traffic to [integrated {{site.data.keyword.cloud_notm}} services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-service-integration) (except for {{site.data.keyword.keymanagementserviceshort}} and {{site.data.keyword.hscrypto}}) goes over private routes by default, regardless of your endpoint choice during service creation.

## Public endpoints
{: #public-service-endpoint}

Public endpoints provide a connection to your service instance on the public network. When you create a service instance, a public endpoint is the default option for all service instances. Your environment needs to have internet access to connect to a service instance.

You don't need to do any service endpoint setting on your {{site.data.keyword.cloud_notm}} account.

## Private endpoints
{: #private-service-endpoint}

A service instance with a service endpoint on the private network gets an endpoint that isn't accessible from the public internet. All traffic is routed to hardware dedicated to {{site.data.keyword.ihsdbaas_postgresql_full}} service instances and remains on the {{site.data.keyword.cloud_notm}} private network. All traffic to and from this endpoint is free and unmetered as long as the traffic remains in {{site.data.keyword.cloud_notm}}. When your environment has access to the {{site.data.keyword.cloud_notm}} private network, an internet connection isn't required to connect to your service instance. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data against threats from the public network. 

If you create a service instance with private endpoints, the connection with your databases will go over private routes; the data you enter on the service creation page (Database admin name, etc.) will still go over public routes.

### Before you begin
{: #prereq-service-endpoint}

Before you create a service instance with private endpoints, you need to enable your account for virtual routing and forwarding (VRF) and then for connectivity to service endpoints. For detailed instructions, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

Currently, enabling VRF on your account is a manual step that is handled by a support ticket. When you complete the request by following the instructions in [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint), you can check on the status of the ticket by going to the [**Manage cases** page](https://cloud.ibm.com/unifiedsupport/cases){: external}.

### Provisioning with private service endpoints
{: #provision-with-service-endpoint}

Choose the private (or both public and private) option for service endpoints when you [create a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service).

### Connecting to databases
{: #connect-with-service-endpoint}

You can connect to your databases over the private network. For detailed instructions, see [Connecting to databases](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-gettingstarted#accessing-database-introduction).
