
# DC01 – Domain Controller (Demo Platform)

## Overview

`DC01` is the on‑premises Active Directory Domain Controller used in the
Microsoft Entra Identity Governance demo platform.

The virtual machine provides:
- AD DS and DNS services
- Authoritative identity source for hybrid joiner scenarios
- Integration with Microsoft Entra Cloud Sync
- A baseline for lifecycle workflow demonstrations

---

## Resource Details

| Property | Value |
|--------|------|
| **Name** | DC01 |
| **Resource type** | Microsoft.Compute/virtualMachines |
| **Resource Group** | rg-onprem |
| **Region** | North Europe |
| **Provisioning state** | Succeeded |
| **Time created** | 15 April 2026 |

---

## Tags

The following tags are applied to the VM to support cost management,
ownership, and operational clarity.

| Tag | Value |
|---|---|
| Platform | Identity-Demo |
| Workload | Hybrid |
| Purpose | Domain Controller |
| Owner | alturnbu |
| CostCentre | Demo |
| Region | North Europe |
| Environment | Demo |

---

## Compute Configuration

| Setting | Value |
|------|------|
| **VM size** | Standard_B2s_v2 |
| **Architecture** | x64 |
| **Hibernation** | Disabled |

This sizing reflects a cost‑efficient configuration suitable for
demo and lab workloads rather than production-scale AD.

---

## Operating System

| Setting | Value |
|------|------|
| **OS** | Windows Server 2022 Datacenter |
| **Image SKU** | 2022-datacenter-g2 |
| **Patch mode** | Automatic by platform |
| **Reboot setting** | If required |
| **Hotpatching** | Disabled |
| **VM agent** | Enabled |

---

## Storage

### OS Disk

| Setting | Value |
|------|------|
| **Disk type** | Standard SSD (LRS) |
| **Disk size** | 127 GB |
| **Caching** | Read/Write |
| **Delete on VM delete** | Yes |
| **Controller type** | SCSI |

No additional data disks are currently configured.

---

## Security Configuration

| Setting | Value |
|------|------|
| **Security type** | Trusted Launch |
| **Secure Boot** | Enabled |
| **vTPM** | Enabled |

This aligns the VM with modern security baselines and supports Zero Trust
demo narratives where required.

---

## Networking

| Setting | Value |
|------|------|
| **NIC count** | 1 |
| **NIC delete on VM delete** | Enabled |
| **VNet** | on‑prem demo VNet |
| **NSG** | Subnet‑level NSG |

Connectivity is intentionally simple and flat to support demo scenarios
and reduce operational overhead.
## Networking

The DC01 virtual machine is deployed into the on‑premises demo virtual network and uses
a combination of subnet‑level security controls and Just‑In‑Time (JIT) access for management.

### IP Addressing

| Type | Value | Notes |
|----|----|----|
| **Private IPv4** | `10.10.1.4` | Static assignment within the on‑prem subnet |
| **Private IPv6** | Not assigned | IPv6 not in use |
| **Public IPv4 (NAT Gateway)** | `20.13.162.109` | Shared outbound connectivity via NAT gateway |
| **Public IPv4 (NIC)** | `4.208.91.73` | Direct public IP on network interface |
| **Public IPv6** | Not assigned | IPv6 not in use |

Two public IPv4 addresses are associated with this VM:
- One via the **NAT Gateway** (for outbound connectivity)
- One directly on the **network interface** (used for controlled inbound access)

---

### Virtual Network Configuration

| Setting | Value |
|----|----|
| **Virtual network** | `vnet-onprem` |
| **Subnet** | `onprem (10.10.1.0/24)` |
| **DNS** | Azure-provided (DNS name not configured) |

The virtual machine shares this VNet and subnet with other demo infrastructure components,
including identity and application workloads.

---

### Network Security

- The subnet is protected by a **subnet‑level Network Security Group (NSG)**  
  (`vnet-onprem-onprem-nsg-northeurope`)
- No per‑NIC NSG is used
- **Inbound RDP (TCP 3389)** access is controlled via **Just‑In‑Time (JIT)** VM access
- No permanently open inbound management ports are configured

This design aligns with demo security best practice:
- Minimal exposed surface area
- Time‑bound administrative access
- Centralised network policy at subnet level

---

### Notes

- Public connectivity is retained for demo and management convenience.
- The network layout is intentionally simple and flat to support
  rapid demo scenarios rather than production isolation or segmentation.
---

## Diagnostics & Monitoring

| Setting | Value |
|------|------|
| **Boot diagnostics** | Enabled |

---

## VM Extensions

### VM Access Agent
Used for local administrator access management.

- **Publisher:** Microsoft.Compute  
- **Type:** VMAccessAgent  
- **Version:** 2.0  
- **Provisioning state:** Succeeded  

### Microsoft Defender for Endpoint (Server)

- **Publisher:** Microsoft.Azure.AzureDefenderForServers  
- **Type:** MDE.Windows  
- **Version:** 1.0  
- **Auto update:** Enabled  
- **vNext:** Enabled  
- **Provisioning state:** Succeeded  

This confirms the VM is onboarded to Defender for Servers for
security visibility during demos.

---

## Intended Use

DC01 is intended **only** for:
- Demo and POC workloads
- Hybrid identity scenarios
- Identity lifecycle demonstrations

It is **not designed** for:
- Production resilience
- High availability
- Performance benchmarking

---

## Notes

- Local administrator access exists purely for bootstrap and recovery.
- All identity and access demonstrations are performed via Entra identities.
- Configuration reflects a deliberate balance between realism and cost control.
