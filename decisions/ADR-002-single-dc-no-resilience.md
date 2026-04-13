# ADR-002 – Single Domain Controller, No On‑Prem Resilience

## Status
Accepted

## Context

This demo platform includes an on‑premises Active Directory environment to support **hybrid identity and legacy comparison scenarios**.

However, the environment is:
- Cost‑constrained
- Non‑production
- Intended for architecture and security demonstrations

As such, full on‑prem resilience (multiple Domain Controllers, failover, clustering) is not feasible.

---

## Decision

We will operate with:
- **One on‑premises Domain Controller (DC01)**
- **No on‑prem high availability**
- **No secondary Domain Controller**
- **Backup‑based recovery only**

On‑prem Active Directory is treated as:
- A **legacy dependency**
- Not a highly available, business‑critical system
- Not the primary identity authority

---

## Rationale

This decision is intentional and supports modern identity discussions:

- Many real‑world customers operate single‑DC environments due to cost
- Hybrid identity increases blast radius when on‑prem infrastructure fails
- Cloud identity controls (Conditional Access, device trust, Verified ID) should not depend on on‑prem availability
- Backup‑based recovery is a realistic strategy for non‑production and constrained estates

This design enables clear comparison between:
- Fragile, legacy identity dependencies
- Resilient, cloud‑native identity enforcement

---

## Consequences

### Positive
- Simplified infrastructure
- Lower cost and operational overhead
- Clear demonstration of single‑instance risk
- Strong support for cloud‑first and Zero Trust narratives
- Clear justification for moving away from hybrid dependency

### Negative
- No automatic failover for AD
- On‑prem outage affects hybrid‑synced users
- Recovery time depends on backup restore

These trade‑offs are accepted and documented.

---

## Operational Notes

- DC01 **must be backed up regularly**
- Restore procedures are documented in:
- runbooks/onprem-single-dc.md
- Cloud‑only users and Verified ID scenarios remain fully functional during on‑prem outages

---

## Notes for demos

When discussing this decision with customers:

> “This environment deliberately uses a single Domain Controller to show the real operational and security risks of hybrid dependency — and why cloud‑native identity reduces that risk.”

This framing consistently resonates in modernisation discussions.
