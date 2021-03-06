---
title: Reduce service costs using Azure Advisor | Microsoft Docs
description: Use Azure Advisor to optimize the cost of your Azure deployments.
services: advisor
documentationcenter: NA
author: saket-ms
ms.service: advisor
ms.topic: article
ms.date: 01/29/2019
ms.author: sagupt
---

# Reduce service costs using Azure Advisor

Advisor helps you optimize and reduce your overall Azure spend by identifying idle and underutilized resources. You can get cost recommendations from the **Cost** tab on the Advisor dashboard.

## Optimize virtual machine spend by resizing or shutting down underutilized instances 

Although certain application scenarios can result in low utilization by design, you can often save money by managing the size and number of your virtual machines. Advisor advanced evaluation models considers a virtual machines for shut-down when P95th of the max of max value of CPU utilization is less than 3% and network utilization is less than 2% over a 7 day period. Virtual machines are considered for right size when it is possible to fit the current load in a smaller SKU (within the same SKU family) or a smaller number # of instance such that the current load doesn’t go over 80% utilization when non-user facing workloads and not above 40% when user-facing workload. Here, the type of workload is determined by analyzing the CPU utilization characteristics of the workload.

The recommended actions are shut-down or resize, specific to resource being recommended for. Advisor shows you the estimated cost savings for either recommended actions - resize or shut-down. Also, for resize recommended action, Advisor provides current and target SKU information. 

If you want to be more aggressive at identifying underutilized virtual machines, you can adjust the CPU utilization rule on a per subscription basis.

## Reduce costs by eliminating unprovisioned ExpressRoute circuits

Advisor identifies ExpressRoute circuits that have been in the provider status of *Not Provisioned* for more than one month, and recommends deleting the circuit if you aren't planning to provision the circuit with your connectivity provider.

## Reduce costs by deleting or reconfiguring idle virtual network gateways

Advisor identifies virtual network gateways that have been idle for over 90 days. Since these gateways are billed hourly, you should consider reconfiguring or deleting them if you don't intend to use them anymore. 

## Buy reserved virtual machine instances to save money over pay-as-you-go costs

Advisor will review your virtual machine usage over the last 30 days and determine if you could save money by purchasing an Azure reservation. Advisor will show you the regions and sizes where you potentially have the most savings and will show you the estimated savings from purchasing reservations. With Azure reservations, you can pre-purchase the base costs for your virtual machines. Discounts will automatically apply to new or existing VMs that have the same size and region as your reservations. [Learn more about Azure Reserved VM Instances.](https://azure.microsoft.com/pricing/reserved-vm-instances/)

Advisor will also notify you of reserved instances that you have that will expire in the next 30 days. It will recommend that you purchase new reserved instances to avoid paying pay-as-you-go pricing.

## Delete unassociated public IP addresses to save money

Advisor identifies public IP addresses that are not currently associated to Azure resources such as Load Balancers or VMs. These public IP addresses come with a nominal charge. If you do not plan to use them, deleting them can result in cost savings.

## Delete Azure Data Factory pipelines that are failing

Azure Advisor will detect Azure Data Factory pipelines that repeatedly fail and recommend that you resolve the issues or delete the failing pipelines if they are no longer needed. You will be billed for these pipelines even if though they are not serving you while they are failing. 

## Use Standard Snapshots for Managed Disks
To save 60% of cost, we recommend storing your snapshots in Standard Storage, regardless of the storage type of the parent disk. This is the default option for Managed Disks snapshots. Azure Advisor will identify snapshots that are stored Premium Storage and recommend migrating your snapshot from Premium to Standard Storage. [Learn more about Managed Disk pricing](https://aka.ms/aa_manageddisksnapshot_learnmore)

## How to access Cost recommendations in Azure Advisor

1. Sign in to the [Azure portal](https://portal.azure.com), and then open [Advisor](https://aka.ms/azureadvisordashboard).

2.	On the Advisor dashboard, click the **Cost** tab.

## Next steps

To learn more about Advisor recommendations, see:
* [Introduction to Advisor](advisor-overview.md)
* [Get Started](advisor-get-started.md)
* [Advisor Performance recommendations](advisor-performance-recommendations.md)
* [Advisor High Availability recommendations](advisor-high-availability-recommendations.md)
* [Advisor Security recommendations](advisor-security-recommendations.md)
* [Advisor Operational Excellence recommendations](advisor-operational-excellence-recommendations.md)
