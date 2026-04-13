# 06 – Logging, Sentinel & Tagging (Current State)

## Purpose

This document captures the **current state of logging, security visibility, and tagging** for the Identity Demo Platform.

It records:
- Log Analytics deployment
- Microsoft Sentinel enablement
- Default region choice
- The standard tagging scheme used for all resources

This is a **state checkpoint**, not a final or tuned design.

---

## Azure Region Strategy

### Default Region

All Azure resources for this platform are deployed in:

``
North Europe

### Rationale

- Broadest Azure service availability in the EU
- Very low risk of regional capability gaps
- Competitive pricing compared to other EU regions
- Commonly used by customer estates

This choice balances cost sensitivity with platform capability.

---

## Log Analytics

### Current State

- Log Analytics workspace exists
- Name:

law-demo-platform
- Resource group:

rg-logging
- Region:

North Europe

### Scope

The Log Analytics workspace acts as the **central telemetry store** for:

- Azure Activity Logs
- Security and identity signals (future)
- Sentinel analytics and incidents (future)

No additional solutions or agents are configured at this stage.

---

## Microsoft Sentinel

### Current State

- Microsoft Sentinel is **enabled**
- Sentinel is bound to:

law-demo-platform
- No analytics rules enabled
- No data connectors configured beyond base logging
- No incidents expected or active

### Intent

Sentinel exists as:
- The security control plane
- A landing point for future signals
- A demo‑ready SOC foundation

Tuning and signal onboarding are intentionally deferred.

---

## Standard Tagging Scheme (Authoritative)

All Azure resources in the platform **must use this tagging scheme**.

This scheme applies to:
- Current resources
- Future resources
- Core platform and demo workloads

---

### Mandatory Tags (All Resources)

| Tag | Example Value | Purpose |
|---|---|---|
| `Platform` | `Identity-Demo` | Groups all resources belonging to the demo platform |
| `Workload` | `Core` | Distinguishes platform vs demo workloads |
| `Purpose` | `Logging` | Explains why the resource exists |
| `Owner` | `alturnbu` | Accountability and ownership |
| `CostCentre` | `Demo` | Cost reporting and filtering |
| `Region` | `NorthEurope` | Explicit region visibility |
| `Lifecycle` | `Active` | Resource lifecycle tracking |

---

### Optional (Recommended) Tags

| Tag | Example Value | Usage |
|---|---|---|
| `Environment` | `Demo` | Supports future duplication or comparison |
| `Source` | `Manual` | Indicates creation method |

---

### Example: Log Analytics Workspace

Applied tags for:


law-demo-platform

Platform     = Identity-Demo
Workload     = Core
Purpose      = Logging
Owner        = alturnbu
CostCentre   = Demo
Region       = NorthEurope
Lifecycle    = Active
Environment  = Demo
Source       = Manual

---

## Tagging Principles

- Tags are applied **at creation time**
- Consistency is more important than completeness
- Tag enforcement via Policy is intentionally deferred
- Tags support:
  - Cost visibility
  - Resource relationship clarity
  - Cleanup and lifecycle management

---

## What Is Intentionally Deferred

- Sentinel analytics rule tuning
- Defender or Entra connectors
- Device or application logs
- Tag enforcement via Azure Policy

These will be introduced only when the platform use‑cases require them.

---

## Status

Logging, Sentinel, and tagging are **implemented and accepted** in their current form.

This layer of the platform is complete for now.
