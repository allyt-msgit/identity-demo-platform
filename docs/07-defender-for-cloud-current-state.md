# 07 – Microsoft Defender for Cloud (Current State)

## Purpose

This document captures the **current state of Microsoft Defender for Cloud (DfC)** for the Identity Demo Platform.

The objective at this stage is to ensure:
- Secure‑by‑default protection
- Posture visibility from day one
- Zero friction when the first resources are deployed
- Controlled and predictable cost behaviour

This is a **prepared-but-quiet** configuration.

---

## Subscription Scope

Defender for Cloud is enabled for:
sub-demo-platform-MCAP611031

The subscription is currently:
- Empty of customer workloads
- Used for platform and demo build‑out only

---

## Defender for Cloud – Posture Management (CSPM)

### Foundational CSPM (Free)

- **Status:** Enabled
- **Coverage:** Full (no resources yet)

Provides:
- Secure Score
- Baseline security recommendations
- Visibility of misconfigurations as resources appear

This forms the baseline security posture for the subscription.

---

### Defender CSPM (Paid)

- **Status:** Enabled
- **Coverage:** Partial (no protected resources yet)

Provides:
- Advanced Cloud Security Posture Management
- Attack path analysis
- Agentless discovery
- Enhanced visibility across the environment

Partial coverage is expected at this stage and will increase automatically as resources are deployed.

---

## Cloud Workload Protection (CWPP) Plans

The following Defender plans are configured to ensure workloads are protected **as soon as they are created**, without retrofitting.

### Defender for Servers
- **Status:** Enabled
- **Billing model:** Per VM
- **Current resources:** 0 servers
- **Current cost:** £0

This ensures:
- Immediate protection when VMs are deployed
- No delay in security posture or alerting

---

### Defender Plans Not Yet Enabled

The following plans are intentionally **disabled** until the corresponding workload types exist:

- Defender for App Service
- Defender for Databases
- Defender for Storage
- Defender for Containers
- Defender for AI Services
- Defender for Key Vault
- Defender for Resource Manager
- Defender for APIs

This avoids unnecessary cost and noise and keeps the platform focused.

---

## Alerting & Monitoring

- Defender security alerts are enabled
- No alerts are expected until protected workloads exist
- Alerts are designed to integrate with:
  - Log Analytics
  - Microsoft Sentinel

There is no email or automation noise configured at this stage.

---

## Integration with Microsoft Sentinel

- Microsoft Sentinel is enabled on the Log Analytics workspace:

law-demo-platform
- Defender for Cloud is prepared to feed alerts and signals into Sentinel
- No analytics rules or automation are configured yet

This provides a future‑ready **SIEM + CNAPP** security model.

---

## Cost Management Approach

The current Defender configuration is intentionally cost‑aware:

- Posture management costs are predictable
- Workload protection costs are incurred **only when resources exist**
- Storage and PaaS plans are deferred until explicitly required

This allows the platform to remain secure without unintended spend.

---

## What Is Intentionally Deferred

The following are deferred to later phases:

- Workload‑specific Defender plan tuning
- Auto‑provisioning agents and extensions
- Alert severity tuning
- Integration with specific application workloads

These will be enabled as the platform evolves.

---

## Status

Microsoft Defender for Cloud is **enabled, paid, and ready**.

The configuration is accepted as‑is and considered complete for the current build phase.
