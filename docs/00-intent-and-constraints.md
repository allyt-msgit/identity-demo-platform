# 00 – Intent and Constraints

## Purpose of this Platform

This repository documents a **Secure Future Initiative (SFI) aligned identity demo platform**.

The platform exists to:
- Demonstrate modern identity and Zero Trust principles
- Support customer discussions around identity modernisation
- Compare legacy, hybrid, and cloud‑native identity approaches
- Showcase passwordless authentication and Microsoft Entra Verified ID
- Provide a realistic, explainable demo environment

This is **not** a production reference architecture.

---

## Design Intent

This environment is designed around the following principles:

- **Identity is the control plane**
- **Security is enforced in the cloud**
- **Access decisions do not depend on email or DNS**
- **Legacy infrastructure exists only to show why it should be reduced**
- **Operational reality is prioritised over idealised designs**

The platform intentionally reflects constraints commonly found in customer environments.

---

## Core Constraints (Intentional)

The following constraints are **deliberate and non‑negotiable**.

### Secure Future Initiative (SFI) Tenant

- The Microsoft Entra tenant is provisioned and governed under SFI
- Tenant‑level capabilities are restricted by design
- Security‑first defaults are enforced

---

### No Custom DNS Domain

- The tenant does **not support custom DNS domains**
- All identities use:
  MngEnvMCAP611031.onmicrosoft.com
- Branding and domain‑based identity patterns are out of scope

This constraint is documented in **ADR‑001**.

---

### Email Is Not Foundational

- Email is treated as a workload, not an identity dependency
- Exchange Online is optional
- Identity, access control, and security enforcement must function without email

This constraint is documented in **ADR‑003**.

---

### Cloud‑First Identity Model

- Microsoft Entra ID is the primary identity authority
- Authentication and access enforcement occur in the cloud
- On‑prem identity is not treated as authoritative

---

### On‑Prem Is Legacy and Fragile by Design

- On‑premises Active Directory exists for comparison only
- A **single Domain Controller** is used
- There is **no high availability**
- Recovery relies on **backup, not resilience**

This constraint is documented in **ADR‑002**.

---

## What This Platform Is Good For

This environment is well suited to demonstrate:

- Conditional Access and Zero Trust
- Device‑based access control
- Phishing‑resistant authentication
- Privileged Identity Management (PIM)
- Identity Protection and risk‑based access
- Microsoft Entra Verified ID
- Hybrid dependency risk and blast radius
- Modernisation narratives

---

## What This Platform Is Not Intended For

This platform is **not suitable** for:

- Exchange or mail‑flow demonstrations
- Branding‑led identity scenarios
- High‑availability on‑prem designs
- Production readiness validation
- Cost‑optimised infrastructure designs

These scenarios are intentionally excluded.

---

## Positioning Statement

Use the following framing when explaining this platform:

> “This environment is intentionally constrained to show how modern identity and Zero Trust security can operate independently of domains, email, and legacy infrastructure.”

---

## Reference Documents

- `decisions/ADR-001-no-custom-domain.md`
- `decisions/ADR-002-single-dc-no-resilience.md`
- `decisions/ADR-003-email-not-foundational.md`
- `runbooks/onprem-single-dc.md`
