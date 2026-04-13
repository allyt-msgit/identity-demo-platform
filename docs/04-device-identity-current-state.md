# 04 – Device Identity & Intune: Current State

## Purpose

This document captures the **current state of device identity and Microsoft Intune** in the identity demo platform.

At this stage, **no end‑user devices have been enrolled**.  
This is an intentional pause point to allow the core identity and access controls to stabilise before introducing device signals.

---

## Current State Summary

### Microsoft Intune

- ✅ Microsoft Intune is available in the tenant
- ✅ Intune is not actively used for device management
- ❌ No devices enrolled
- ❌ No Autopilot profiles
- ❌ No application deployment
- ❌ No device‑based Conditional Access enforcement

Intune exists as a **capability**, not yet as an enforced control.

---

### Device Identity

- ❌ No Entra‑joined user devices
- ❌ No Hybrid‑joined devices
- ❌ No device compliance signals in use
- ❌ Conditional Access does not currently evaluate device state

All access decisions are currently based on:
- User identity
- Risk signals
- Authentication requirements

---

## Design Intent (Why This Is Intentional)

This pause is deliberate and aligns with platform principles:

- Conditional Access baseline is **SFI‑deployed and accepted**
- Device trust is a **second‑order control**, not foundational
- Introducing devices too early creates unnecessary complexity
- The platform is currently focused on:
  - Identity
  - Risk
  - Authentication
  - Access control logic

Device identity will be introduced **when there is a clear enforcement story**, not “just because Intune exists”.

---

## What Is Explicitly Deferred

The following activities are deferred to a later build phase:

- Enrolling Entra‑joined devices
- Creating device compliance policies
- Consuming device state in Conditional Access
- Authentication Strength binding to device trust
- Application access decisions based on device compliance

This deferral is intentional and temporary.

---

## Re‑Entry Criteria (When to Resume Device Work)

Device identity work should resume when **at least one** of the following is true:

- A demo requires device trust as a control (e.g. admin access)
- An application scenario requires device‑based access decisions
- A Zero Trust “identity + device” narrative is required
- Verified ID flows need to be contrasted with managed devices

At that point, a **minimal Intune deployment** will be introduced.

---

## Planned Next Steps (Not Yet Executed)

When device identity work resumes, the planned approach is:

1. Enrol a single Entra‑joined Windows device
2. Create one minimal compliance policy
3. Validate device visibility in sign‑in logs
4. Introduce device trust **in a scoped Conditional Access policy**

These steps will be documented at the time of execution.

---

## Status

Device identity is **deliberately not active**.  
This is a planned, documented, and accepted state.

---

## Related Documents

- `docs/00-intent-and-constraints.md`
- `docs/03-conditional-access-baseline.md`
- `decisions/ADR-002-single-dc-no-resilience.md`
