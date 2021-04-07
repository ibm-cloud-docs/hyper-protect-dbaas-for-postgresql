---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-07"

keywords: Hyper Protect DBaaS, scaling, resource scaling, RAM, disk, vCPU

subcollection: hyper-protect-dbaas-for-postgresql

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:term: .term}
{:external: target="_blank" .external}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}

# Scaling RAM, disk, and vCPU
{: #resources-scaling}

You can manually adjust the amount of resources available to your {{site.data.keyword.cloud}} {{site.data.keyword.ihsdbaas_postgresql_full}} service instance to suit your workload and the size of your data. 
{: shortdesc}

## Resource breakdown
{: #resources-breakdown}

Billing is based on the total amount of resources that are allocated to your service instance. The resource allocation value that you select is for each node, and the total resource allocation is three times the value you select because one {{site.data.keyword.ihsdbaas_postgresql_full}} service instance has three nodes in a cluster for high availability. For example, if you select 4 GB for RAM allocation, your total RAM allocation is 12 GB. 

While GB is shown in the UI, GiB is used in the backend.
{: note}

### Disk
{: #resources-disk}

Disk allocation is for database storage only. Additional storage for backup and logs is allocated internally based on database storage. The additional storage is also included in the storage cost.

Your disk allocation has to be enough to store all of your data. Disk allocation also affects the performance of the disk, with larger disks having higher performance.

You can't scale down disk allocation.
{: note}

### RAM
{: #resources-ram}

If you find that your service instance is suffering from performance issues due to a lack of memory, you can scale the amount of RAM allocated to it. 

### vCPU
{: #resources-vcpu}

A vCPU is a virtual processor core that is a share of a physical CPU.

A service instance with one vCPU takes longer to provision and might have performance issues. You can choose one vCPU as a starting point to evaluate the service, and add more vCPUs later if needed.
{: note}

## Scaling considerations
{: #scaling-considerations}

The following information provides what you need to know about the scaling process.

### Before
{: #before-scaling}

- It’s recommended that you [monitor](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-monitor) your database usage to find the optimal resource allocation values.

- You need to have the **Manager** role to scale resources, as defined in the [IAM service access roles table](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#service-access-roles). To assign access, see [Managing IAM access for users or services](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-iam#manage-access).

- You can't scale your resources in the following circumstances:
  - A request to back up the databases or to change the database configuration is running.
  - A scaling request is running.
  - Previous scaling failure isn't resolved.
  - One or more resource allocation values aren't in the range.
  - One or more nodes aren't running.
  - Not enough capacity to assign resources.
  - Your service instance is using the fixed pricing plan. See [Converting to the flexible pricing plan](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling#pricing-plan-switch).

-  The acceptable resource allocation values are as follows:

|Resource|Unit|Value Range|
|--------|----|-----------|
|RAM|GB per node|{2, 3, 4, 5, 8, 12, 16, 24, 32, 64, 96, 128} |
|Disk|GB per node|{5, 10, 16, 24, 32, 64, 128, 160, 256, 320, 512, 640, 1280} |
|vCPU|vCPU per node|{1, 2, 3, 4, 5, 6, 8, 9, 12, 16} |
{: caption="Table 1. Acceptable resource allocation values"}

### During
{: #during-scaling}

- The scaling is non-disruptive. Your resources are scaled sequentially on three nodes (from secondary to primary) to ensure that your databases are online during the scaling, which usually takes a few minutes.
- Scaling operations are logged in [{{site.data.keyword.cloudaccesstrailshort}}](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-activity-tracker-events#list-activity-tracker-events).

### After
{: #after-scaling}

- In the following cases, the scaling is considered failed. The scaling stops and an administrator is notified to solve the problem. Your databases are still available.

  - The scaling of any node fails.
  - The scaling of the first or the second node is finished, but the node isn't running after scaling.

- The new billing takes effect when all three nodes are scaled. If the last node isn't running after scaling, an administrator will be notified to solve the problem. The new billing still takes effect in this case.

## Scaling instructions
{: #scaling-instructions}

You can scale your resources through the UI, CLI, and API.

### Scaling in the UI
{: #webui-scaling}
{: ui}

1. On the service dashboard, select **Resources** in the side navigation pane. 
2. Select new allocation values for RAM, Disk, or vCPU.
3. Click **Apply changes**. If your request is accepted, you can see the scaling status of each node. 

### Scaling from the CLI 
{: #cli-scaling}
{: cli}

Use the `ibmcloud dbaas resource-scale` command to scale your resources. Use the `ibmcloud dbaas task-show` command to check the status of the scaling task. For more information about how to use the commands, see [ibmcloud dbaas resource-scale](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#resource-scale) and the [task commands](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-dbaas_cli_plugin#task-cmds).

### Scaling with the API
{: #api-scaling}
{: api}

For the API requests to scale your resources and check the scaling status, see [Scale resources](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#scale-resources) and [List tasks](/apidocs/hyperp-dbaas/hyperp-dbaas-v3#list-tasks).

##  Converting to the flexible pricing plan
{: #pricing-plan-switch}

If you created your service instance with the fixed pricing plan (`Small`, `Medium`, or `Large`), you can convert your plan to the flexible pricing plan in the UI or from the CLI. The resources of your service instance stay the same after conversion. Free service instances can't be converted or scaled.

You don't need to restart your service instance or the applications bound to it after you convert your pricing plan.

Your cluster won't expire if you don't convert the pricing plan. However, if you need to scale your resources, you need to convert before scaling. Your fixed pricing plan service instance has a monthly charge and therefore, we recommend converting the cluster close to the end of the monthly time-frame to prevent double charges. After you convert to the flexible plan, reload the dashboard to see the **Resources** page.
{: tip}

### Using the UI
{: #switch-plan-ui}

Go to the **Plan** page on the service dashboard. Choose **PostgreSQL Flexible** and save.

### Using the CLI
{: #switch-plan-cli}

Use the `ibmcloud resource service-instance-update <resource_name> --service-plan-id <service_plan_id>` command to update to the flexible pricing plan. `c8550ed3-894b-462d-98ee-68e80e3955d4` is the ID of the flexible pricing plan of {{site.data.keyword.ihsdbaas_postgresql_full}}. For example:
```
ibmcloud resource service-instance-update MyDBaaSIns03 --service-plan-id c8550ed3-894b-462d-98ee-68e80e3955d4
```
{: codeblock}

You can use the `ibmcloud resource service-instance <resource_name>` command to verify that `Service Plan Name` is updated to `postgresql-flexible`.

After you convert your plan, you can [scale your resources](/docs/hyper-protect-dbaas-for-postgresql?topic=hyper-protect-dbaas-for-postgresql-resources-scaling).
