---

copyright:
  years: 2020, 2021
lastupdated: "2021-05-19"

keywords: service integration

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


# Setting up Terraform for Hyper Protect DBaaS
{: #terraform-setup}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multi-tier cloud environments following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API, you can automate the provisioning, update, and deletion of your {{site.data.keyword.ihsdbaas_postgresql_full}} service instances by using HashiCorp Configuration Language (HCL).
{: shortdesc}





1. [Install the Terraform CLI and the {{site.data.keyword.cloud_notm}} Provider plug-in](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
2. [Create or retrieve an {{site.data.keyword.cloud_notm}} API key](/docs/account?topic=account-userapikey#create_user_key). The API key is used to authenticate with the {{site.data.keyword.cloud_notm}} platform and to determine your permissions for {{site.data.keyword.cloud_notm}} services.
3. Create a variables file that is named `terraform.tfvars` and specify the {{site.data.keyword.cloud_notm}} API key that you retrieved. Variables that are defined in the `terraform.tfvars` file are automatically loaded by Terraform when the {{site.data.keyword.cloud_notm}} Provider plug-in is initialized and you can reference them in every Terraform configuration file that you use. 

   Because the `terraform.tfvars` file contains confidential information, do not push this file to a version control system. This file is meant to be on your local system only. 
   {: important}
   
   ```
   ibmcloud_api_key = "<ibmcloud_api_key>"
   ```
   {: codeblock}
   
4. Create a provider configuration file that is named `provider.tf`. Use this file to configure the {{site.data.keyword.cloud_notm}} Provider plug-in with the {{site.data.keyword.cloud_notm}} API key from your `terraform.tfvars` file. The plug-in uses this key to access {{site.data.keyword.cloud_notm}} and to provision your {{site.data.keyword.ihsdbaas_postgresql_full}} service instance. To access a variable value from the `terraform.tfvars` file, you must first declare the variable in the `provider.tf` file and then reference the variable by using the `var.<variable_name>` syntax . 

   ```
   variable "ibmcloud_api_key" {}
 
   provider "ibm" {
       ibmcloud_api_key   = var.ibmcloud_api_key
      }
   ```
   {: codeblock}

## Working with {{site.data.keyword.ihsdbaas_postgresql_full}} resources in Terraform

The following is an example of creating a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in Terraform.

1. Create a Terraform configuration file that is named `main.tf`. In this file, you declare the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance that you want to provision. The following example creates a {{site.data.keyword.ihsdbaas_postgresql_full}} service instance that is named `0001-postgresql` in the `us-south` region. For detailed parameter reference, see the tables in the [documentation](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-create-service#cli-create-service). For more information about `ibm_resource_instance`, see the [`ibm_resource_instance` documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/resource_instance){: external}. 
   
   ```
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_resource_instance" "myhpdbcluster" {
     name = "0001-postgresql"
     service = "hyperp-dbaas-postgresql"
     plan = "postgresql-free"
     location = "us-south"
     resource_group_id = data.ibm_resource_group.group.id

     timeouts {
       create = "15m"
       update = "15m"
       delete = "15m"
     }
     parameters = {
       "name": "cluster01",
       "admin_name": "admin",
       "password": "Hyperprotectdbaas0001"
       "confirm_password": "Hyperprotectdbaas0001",
      "db_version": "10"
    }
   }
   ```
   {: codeblock}
   
2. Initialize the Terraform CLI. 
   ```
   terraform init
   ```
   {: pre}
   
3. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in your account.
   ```
   terraform plan
   ```
   {: pre}
   
4. Create the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance in {{site.data.keyword.cloud_notm}}.
   ```
   terraform apply
   ```
   {: pre}
   
5. From the [{{site.data.keyword.cloud_notm}} resource dashboard](https://cloud.ibm.com/resources){: external}, find the {{site.data.keyword.ihsdbaas_postgresql_full}} service instance that you created.
