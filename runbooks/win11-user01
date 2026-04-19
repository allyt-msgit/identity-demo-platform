# WIN11-USER01 – End User Workstation (Demo Platform)

## Overview

`WIN11-USER01` is the primary **end‑user workstation** used for demonstrating
Microsoft Entra Identity Governance scenarios from a **user perspective**.

The virtual machine is designed to simulate a modern, enterprise-managed endpoint and is
used to demonstrate:

- End‑user joiner scenarios (hybrid and cloud-native)
- Access Package requests and approvals
- Conditional Access and Terms of Use prompts
- Global Secure Access (GSA) enforcement
- Intune device management and compliance

---

## Resource Details

| Property | Value |
|--------|------|
| **Name** | WIN11-USER01 |
| **Resource type** | Microsoft.Compute/virtualMachines |
| **Resource Group** | rg-onprem |
| **Region** | North Europe |
| **Provisioning state** | Succeeded |
| **Time created** | 19 April 2026 |
| **Managed identity** | System-assigned |

---

## Tags

The following tags are applied to support governance, cost management, and lifecycle control.

| Tag | Value |
|---|---|
| Environment | Demo |
| CostCentre | Demo |
| Action | Do Not Delete |
| Platform | Identity-Demo |
| Purpose | End User workstation |
| Region | North Europe |
| Lifecycle | Active |

---

## Compute Configuration

| Setting | Value |
|------|------|
| **VM size** | Standard_D4s_v4 |
| **Architecture** | x64 |
| **Hibernation** | Disabled |

This sizing provides a responsive Windows 11 experience suitable for live demos,
screen‑sharing, and portal-heavy workflows without unnecessary cost.

---

## Operating System

| Setting | Value |
|------|------|
| **OS** | Windows 11 Enterprise |
| **Version** | 25H2 |
| **Image SKU** | win11-25h2-ent |
| **Patch mode** | Automatic by OS |
| **Assessment mode** | Image default |
| **Hotpatching** | Disabled |
| **VM agent** | Enabled |

The workstation is intentionally deployed with an enterprise image to ensure
compatibility with Intune, Conditional Access, and modern endpoint security controls.

---

## Storage

### OS Disk

| Setting | Value |
|------|------|
| **Disk type** | Premium SSD (LRS) |
| **Disk size** | 127 GB |
| **Caching** | Read/Write |
| **Delete on VM delete** | Yes |
| **Controller type** | SCSI |

No additional data disks are configured.

---

## Security Configuration

| Setting | Value |
|------|------|
| **Security type** | Trusted Launch |
| **Secure Boot** | Enabled |
| **vTPM** | Enabled |

This configuration aligns the workstation with modern endpoint security baselines
and supports Zero Trust and device trust demos.

---

## Identity & Access

| Setting | Value |
|------|------|
| **Local admin account** | Present (bootstrap only) |
| **Entra join** | Microsoft Entra joined |
| **Azure VM Entra login** | Not enabled |
| **Managed Identity** | System-assigned |

The local administrator account is used **only** for initial bootstrap and recovery.
All demo activity is performed using Microsoft Entra user accounts.

---

## Networking

The workstation is deployed into the same on‑premises demo network as other
identity infrastructure to keep connectivity simple and predictable.

### Network Configuration

| Setting | Value |
|----|----|
| **Virtual network** | vnet-onprem |
| **Subnet** | onprem |
| **NIC count** | 1 |
| **NIC delete on VM delete** | Enabled |
| **NSG model** | Subnet-level NSG |
| **Per-NIC NSG** | Not used |

## Networking

The WIN11-USER01 workstation is deployed into the shared on‑premises demo virtual
network and uses the same network model as other demo infrastructure components.
This ensures consistent connectivity and simplifies identity and access demonstrations.

### IP Addressing

| Type | Value | Notes |
|----|----|----|
| **Private IPv4** | `10.10.1.5` | Assigned within the on‑prem subnet |
| **Private IPv6** | Not assigned | IPv6 not in use |
| **Public IPv4 (NAT Gateway)** | `20.13.162.109` | Shared outbound connectivity via NAT gateway |
| **Public IPv4 (NIC)** | `20.223.128.168` | Direct public IP on workstation network interface |
| **Public IPv6** | Not assigned | IPv6 not in use |

Two public IPv4 addresses are associated with this virtual machine:
- One via the **NAT Gateway** (`nat-onprem`) for outbound traffic
- One directly attached to the **network interface** (`win11-user01822`) for
  controlled inbound management access

---

### Virtual Network Configuration

| Setting | Value |
|----|----|
| **Virtual network** | `vnet-onprem` |
| **Subnet** | `onprem (10.10.1.0/24)` |
| **DNS** | Azure-provided (DNS name not configured) |

The workstation shares this virtual network with identity and application
workloads to enable realistic end‑to‑end demo scenarios without additional routing complexity.

---

### Network Security

- Network security is enforced using a **subnet‑level Network Security Group (NSG)**
- No per‑NIC NSG is applied
- **Inbound RDP (TCP 3389)** access is provided using **Just‑In‑Time (JIT)** VM access
- No permanently exposed inbound management ports are configured

This design supports:
- Secure, time‑bound administrative access
- Reduced attack surface
- Alignment with Zero Trust demo narratives

---

### Notes

- Public connectivity is retained to support demo and management workflows.
- The flat network design is intentional and optimised for demos rather than
  production network segmentation or isolation.
### Connectivity & Access

- Inbound management access is provided via **Just‑In‑Time (JIT)** VM access
- No permanently open inbound management ports are configured
- Outbound internet access is enabled to support:
  - Entra ID sign-in
  - Intune enrolment
  - Microsoft 365 and Entra portals
  - Global Secure Access client flows

---

## Diagnostics & Monitoring

| Setting | Value |
|------|------|
| **Boot diagnostics** | Enabled |

---

## Intended Use

WIN11-USER01 is intended **only** for:

- End‑user experience demonstrations
- Identity Governance scenario testing
- Access control and device trust demos

It is **not designed** for:
- Persistent user workloads
- Production endpoint security benchmarking
- Multi-user access

---

## Notes

- The workstation acts as a functional stand‑in for Windows 365 or physical
  Entra‑joined devices in customer environments.
- Intune policies are intentionally lightweight to avoid obscuring demo flows.
- The VM is intentionally excluded from high availability or resilience features,
  as it represents a single-user demo endpoint.
