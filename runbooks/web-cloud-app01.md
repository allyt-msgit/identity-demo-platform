# web-cloud-app01 – Cloud HTTPS Demo Application (Static Web App)

## Overview

`web-cloud-app01` is a **cloud‑hosted HTTPS application** used in the Entra Identity
Governance demo platform to represent a **modern SaaS-style application**.

The application is intentionally lightweight and low cost, providing a simple
web endpoint that can be protected by Microsoft Entra and used for:

- Access Package demonstrations
- Conditional Access testing
- Cloud joiner scenarios
- Comparison with on‑premises application access patterns

---

## Resource Details

| Property | Value |
|--------|------|
| **Name** | web-cloud-app01 |
| **Resource type** | Microsoft.Web/staticSites |
| **Resource Group** | rg-onprem |
| **Region** | West Europe |
| **SKU** | Free |
| **Provisioning model** | Azure Static Web App |
| **Lifecycle state** | Active |

---

## Tags

The following tags are applied for governance, ownership, and cost tracking.

| Tag | Value |
|---|---|
| CostCentre | Demo |
| Environment | Demo |
| Lifecycle | Active |
| Owner | alturnbu |
| Platform | Identity-Demo |
| Purpose | Web Server |
| Workload | Cloud |

---

## Application Characteristics

| Setting | Value |
|------|------|
| **Hosting model** | Fully managed (PaaS) |
| **Compute** | Serverless |
| **HTTPS** | Enabled by default |
| **Inbound access** | Public (identity protected) |
| **Outbound dependencies** | None |

No infrastructure management is required to operate the application.

---

## Networking

Azure Static Web Apps are exposed via a Microsoft‑managed global edge network.

| Setting | Value |
|----|----|
| **Default hostname** | `https://jolly-field-0ee2f4f03.7.azurestaticapps.net` |
| **Inbound IP (edge)** | 132.220.38.112 |
| **Custom domains** | None configured |
| **Private endpoints** | Not configured |

All inbound HTTPS traffic is terminated at the Azure Static Web Apps front door and
routed internally to the application.

---

## Deployment Model

| Setting | Value |
|------|------|
| **Deployment authorisation** | Deployment token |
| **Source repository** | None |
| **CI/CD integration** | Not configured |
| **Content upload** | Manual / ad-hoc |

The application content is currently provisioned manually for demo purposes.
No GitHub repository or automated pipeline is in use.

---

## Authentication & Identity (Current State)

| Capability | Status |
|---|---|
| Microsoft Entra authentication | Not yet enforced |
| Built-in auth provider | Planned |
| Enterprise Application | Created once auth is enabled |

Authentication has intentionally **not yet been finalised**. This allows the
application to exist as a neutral test endpoint while identity governance scenarios
are built incrementally.

---

## Intended Use

This application is intended **only** for:

- Demo and PoC scenarios
- Identity governance walkthroughs
- Access control testing

It is **not intended** for:
- Production use
- Performance testing
- Hosting sensitive data

---

## Notes & Design Decisions

- The Free SKU was selected to minimise cost.
- No GitHub integration is used to reduce setup complexity.
- Content is deliberately minimal to keep focus on identity and access flows.
- Authentication and governance controls will be layered on later and
  documented as the demo platform evolves.

``
