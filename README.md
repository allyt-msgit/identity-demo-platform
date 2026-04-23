# Identity Demo Platform (SFI-aligned)

## Purpose

This repository documents a **Secure Future Initiative (SFI) aligned identity, device, and access-control demo platform** built using Microsoft Entra ID, Azure, and selected on‑premises components.

It is designed for:
- Identity and Zero Trust architecture discussions
- Security and access control demos
- Hybrid vs cloud‑native comparison
- Verified ID and passwordless narratives

This is **not** a production reference architecture.

---

## Key Constraints (Intentional)

This environment is intentionally constrained to reflect modern security guidance and real-world limitations:

- ✅ Provisioned Microsoft Entra tenant (SFI governed)
- ✅ Cloud‑first identity model

These constraints are deliberate and form part of the demo narrative.

---

## Identity Model
- **Primary domain hub.proseware.uk** 
- **Primary control plane:** Microsoft Entra ID
- **Admin model:** Least privilege + Just-In-Time (PIM)
- **Authentication:** Phishing-resistant MFA, passwordless-first
- **Legacy dependencies:** Demonstrated, not relied upon

### Key Accounts (pre-provisioned via SFI)

- **Emergency access**
  ms-breakglass@MngEnvMCAP611031.onmicrosoft.com
  - **Platform admin**

admin@MngEnvMCAP611031.onmicrosoft.com

- **Primary working identity (PIM-elevated)**

alturnbu@MngEnvMCAP611031.onmicrosoft.com
alturnbu@hub.proseware.uk
---
## Servers config
- **DC01 - Domain controller 10.10.1.4
- **APP-WEB-01 - Web server on prem + file share server - 10.10.1.6
- ** WIN11-USER01 - vm IN AZURE FOR cooper

## AD domain
- **MngEnvMCAP611031.onmicrosoft.com
- **Netbios name MCAP611031
## Repository Structure

```text
docs/        → Conceptual architecture and design guidance
runbooks/    → Step-by-step build and operation guides
decisions/   → Architectural Decision Records (ADRs)
diagrams/    → Architecture diagrams and visuals
