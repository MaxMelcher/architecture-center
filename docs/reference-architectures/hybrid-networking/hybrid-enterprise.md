---
title: Large-Scale Hybrid Enterprise Networking
description: This reference architecture deploys a hub-spoke network topology in Azure for large enterprises in multiple regions.
Autor: Gbuch
keywords: hybrid, expressroute, hub-spoke 
ms.date: 30/01/2020
ms.topic: reference-architecture
ms.service: architecture-center
---

# Hub-spoke network topology in Azure

This reference architecture is an extension to the [hub-spoke topology](hub-spoke.md) architecture, with scale-out options for large enterprises.

<!-- @todo Update the intro so its easier to understand our terms -->
The *hub* is a virtual network (VNet) in Azure that acts as a central point of connectivity to your on-premises network. The *spokes* are VNets that peer with the hub, and can be used to isolate workloads. Traffic flows between the on-premises datacenter and the hub through an ExpressRoute or VPN gateway connection. [**Deploy this solution**](#deploy-the-solution).

<!-- @todo Add Picture -->
![alt text](./media/folder_name/architecture-diagram.png)

<!-- @todo Add Visio -->
_Download a [Visio file](https://arch-center.azureedge.net/cdn/architecture.vsdx) that contains this architecture diagram._

The benefits of this topology include:

<!-- @todo adjust bullets with full benefits -->
- **Cost savings** by centralizing services that can be shared by multiple workloads, such as network virtual appliances (NVAs) and DNS servers, in a single location.
- **Overcome subscriptions limits** by peering VNets from different subscriptions to the central hub.
- **Separation of concerns** between central IT (SecOps, InfraOps) and workloads (DevOps).
- **Availability** by having multiple regions

Typical uses for this architecture include:
<!-- @todo update the typical uses -->
- Workloads deployed in different environments, such as development, testing, and production, that require shared services such as DNS, IDS, NTP, or AD DS. Shared services are placed in the hub VNet, while each environment is deployed to a spoke to maintain isolation.
- Workloads that do not require connectivity to each other, but require access to shared services.
- Enterprises that require central control over security aspects, such as a firewall in the hub as a DMZ, and segregated management for the workloads in each spoke.

## Architecture

The architecture consists of the following components:

- **On-premises network**. A private local-area network running within an organization.
- **ExpressRoute circuit**. A layer 2 or layer 3 circuit supplied by the connectivity provider that joins the on-premises network with Azure through the edge routers. The circuit uses the hardware infrastructure managed by the connectivity provider.
- **Azure virtual networks (VNets)**. Each VNet resides in a single Azure region, and can host multiple application tiers. Application tiers can be segmented using subnets in each VNet.
- **Azure virtual network peering**. <!-- @todo describe peering -->


## Recommendations

The following recommendations apply for most scenarios. Follow these recommendations unless you have a specific requirement that overrides them.

## Scalability considerations
### ExpressRoute circuit
### Virtual Network peering 

<!--  -->

## Availability considerations

### ExpressRoute geo redundancy
<!-- @todo Example ExpressRoute within geopolitical boundary -->

## Manageability considerations

### Hub & Spoke creation 
<!-- @todo guidance how to automate the hub & spoke -->

## Security considerations

### Internet break-out
<!-- @todo Internet break-out -->

### Internet break-in
<!-- @todo Internet break-in -->

## Deploy the solution
<!-- @todo Deployment with terraform -->