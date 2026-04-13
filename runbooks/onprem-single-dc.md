# Runbook – Single On‑Prem Domain Controller (Backup‑Only)

## Context

This runbook describes how to build and operate a **single on‑premises Active Directory Domain Controller** as part of a **Secure Future Initiative (SFI) aligned identity demo platform**.

This design is **intentionally non‑resilient**:
- No high availability
- No second DC
- Recovery is achieved through backup and rebuild

This reflects real-world, cost‑constrained customer environments and supports modernisation discussions.

---

## Scope & Constraints

- Microsoft Entra tenant is SFI‑provisioned
- No custom DNS domain (onmicrosoft.com only)
- On‑prem AD is included for hybrid comparison only
- Cloud identity remains the primary control plane

---

## Server Overview

| Server | Purpose |
|------|--------|
| DC01 | Active Directory Domain Services + DNS |
| MGMT01 | Entra Connect + management |

---

## Naming & Identity

**AD Forest**
corp.internal
NetBIOS: CORP

**Servers**

DC01.corp.internal
MGMT01.corp.internal

**Service Account**

svc-adconnect

---

## Phase A – Build the Domain Controller

### A1. Provision DC01

- OS: Windows Server 2022
- Static IP
- No public IP
- Defender for Servers enabled
- Azure Monitor / Log Analytics agent installed

DC01 is treated as **rebuildable**, not permanent.

---

### A2. Install Active Directory

On DC01:

1. Install roles:
   - Active Directory Domain Services
   - DNS
2. Promote server as new forest:

corp.internal
3. Configure DNS:
- Forwarders to Azure
- Secure dynamic updates only
4. Configure time sync with Azure

---

### A3. Basic OU Structure

```text
CORP
├─ Users
├─ Groups
├─ Servers
└─ Service Accounts

Minimal GPO usage only.

Phase B – Backup Strategy (Primary Recovery Method)
B1. Backup Requirements
The following must be backed up:

DC01:

System state
OS disk


MGMT01:

Full VM


Entra Connect configuration


B2. Backup Implementation
Recommended approach:

Azure Backup for VMs
Daily backups
Short retention (7–14 days)

Recovery approach:

Restore DC01 from backup
Validate AD and DNS health
Resume Entra Connect sync


Phase C – Entra Connect (Hybrid Identity)
C1. Install Entra Connect
On MGMT01:

Sign in using:
admin@MngEnvMCAP611031.onmicrosoft.com



Configuration:

Password Hash Sync: Enabled
Pass‑through Authentication: Disabled
Federation: Disabled
Cloud‑first configuration


C2. UPN Strategy

On‑prem users:
user@corp.internal


Cloud users:
user@MngEnvMCAP611031.onmicrosoft.com



Mismatch is intentional and supports legacy vs modern comparison.

C3. Sync Scope

Sync only test users
Exclude:

Tenant admins
Break‑glass accounts
Service accounts (initially)




Phase D – Demonstration Scenarios
This architecture supports the following narratives:

Impact of single‑instance AD failure
Dependency on backups vs resilience
Hybrid identity complexity
Cloud‑only identity survivability
Transition to passwordless and Verified ID


What This Runbook Deliberately Avoids

Second Domain Controller
On‑prem high availability
Matching on‑prem and cloud UPNs
Email‑led identity dependencies

These omissions are intentional.
