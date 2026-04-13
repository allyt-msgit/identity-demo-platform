# 03 – Conditional Access Baseline (SFI)

## Purpose

This document describes the **Secure Future Initiative (SFI) deployed Conditional Access baseline** for this identity demo platform.

The baseline is:
- Security‑first
- Signal‑driven
- Intentionally minimal
- Accepted as‑is

No additional Conditional Access policies are added at this stage.

---

## Design Principles

The Conditional Access configuration in this tenant follows these principles:

- Protect **all identities by default**
- React dynamically to **risk signals**
- Reduce attack surface through **preventative controls**
- Avoid premature optimisation or over‑customisation
- Establish a clean foundation for later device‑based access

Conditional Access is treated as the **identity enforcement layer**, not a feature playground.

---

## SFI‑Deployed Baseline Policies

The following policies are deployed automatically as part of SFI tenant provisioning.

### 1. Tenant‑Wide Multifactor Authentication

**Policy**
> Multifactor authentication for Microsoft partners and vendors

**Intent**
- Enforce MFA for all users across all cloud applications
- Establish MFA as the default authentication requirement

**Key Characteristics**
- Scope: All users (with emergency access exclusions)
- Apps: All cloud apps
- Control: Require multifactor authentication

---

### 2. Risk‑Based Reauthentication (Sign‑in Risk)

**Policy**
> Reauthentication on sign‑in risk for Microsoft partners and vendors

**Intent**
- Respond to potentially compromised sign‑ins
- Force reauthentication when Microsoft Entra detects elevated sign‑in risk

**Key Characteristics**
- Scope: All users
- Apps: All cloud apps
- Condition: Sign‑in risk (medium/high)
- Control: Require MFA
- Session: Reauthenticate every time

---

### 3. User Compromise Remediation (User Risk)

**Policy**
> Secure password change on high user risk for Microsoft partners and vendors

**Intent**
- Remediate suspected account compromise
- Force credential reset when user risk is high

**Key Characteristics**
- Scope: All users
- Apps: All cloud apps
- Condition: High user risk
- Control: Require password change

---

### 4. Security Information Registration Protection

**Policy**
> Security info registration for Microsoft partners and vendors

**Intent**
- Protect MFA and security info registration flows
- Prevent attackers from registering authentication methods

**Key Characteristics**
- Scope: All users
- Target: User action – Register security information
- Condition: Network / location based
- Control: Block access unless conditions are met

---

## Baseline Assessment

This Conditional Access baseline provides:

- ✅ Mandatory MFA for all users
- ✅ Automated response to sign‑in risk
- ✅ Automated remediation of compromised accounts
- ✅ Protection of identity recovery and MFA registration surfaces

This constitutes a **strong, complete Zero Trust identity baseline** for this platform.

---

## Explicit Acceptance Decision

The SFI‑deployed Conditional Access baseline is **accepted as sufficient** for the demo platform.

No additional policies are added at this stage.

This decision is intentional and prevents:
- Over‑engineering
- Policy sprawl
- Conflicting access logic
- Future rework during device onboarding

---

## What Is Intentionally Deferred

The following are deferred to later build phases:

- Device‑based Conditional Access (compliant / joined devices)
- Authentication Strength enforcement
- Application‑specific Conditional Access policies
- Session hardening beyond risk scenarios

These controls will be introduced **after device identity is established**.

---

## Operational Notes

- All policies are Microsoft‑owned and SFI‑managed
- Customisation of these policies is deliberately avoided
- Emergency access accounts remain excluded
- Conditional Access is considered **closed** until the device phase

---

## Related Documents

- `docs/00-intent-and-constraints.md`
- `decisions/ADR-001-no-custom-domain.md`
- `decisions/ADR-002-single-dc-no-resilience.md`
- `decisions/ADR-003-email-not-foundational.md`
