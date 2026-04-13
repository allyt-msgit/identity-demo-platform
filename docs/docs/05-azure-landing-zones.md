# 05 – Azure Landing Zones (Current State)

## Purpose

This document captures the **current Azure Landing Zone state** for the identity demo platform.

The landing zone provides a CAF‑aligned foundation while remaining intentionally simple and cost‑constrained.

---

## Current State Summary

- ✅ Management group hierarchy established
- ✅ Single subscription in use
- ✅ No workloads deployed
- ✅ No platform separation yet
- ✅ No networking or policy guardrails applied

This represents an intentional **starting point**, not a final-state architecture.

---

## Management Group Structure
Tenant Root Group
└── Landing Zones
└── Corp

The **Corp** management group represents the initial workload landing zone.

---

## Subscription Model

A single subscription is used due to cost constraints:


sub-demo-platform-MCAP611031

Placement:

Landing Zones / Corp

This subscription currently contains no resources.

---

## Design Rationale

The single-subscription model is intentional:

- Subscriptions act primarily as billing boundaries
- Cost is constrained to a single funding source
- CAF allows future subscription splits without re‑architecture
- Identity, security, and Zero Trust controls do not depend on multiple subscriptions

This approach reflects the reality of many early-stage or demo environments.

---

## What Is Intentionally Not Implemented Yet

- Platform subscriptions (Identity / Management / Connectivity)
- Hub‑and‑spoke networking
- Azure Policy guardrails
- Centralised logging resources
- Workload-specific landing zones

These will be introduced only when justified by requirements.

---

## Next Planned Evolution

As the platform matures, this landing zone can evolve to include:

- Additional subscriptions under Platform management groups
- Dedicated logging and management subscriptions
- Networking and connectivity patterns
- Workload-specific landing zones

This evolution does not require rework of existing identity or access controls.

---

## Status

Azure Landing Zones are **established and accepted** in their current form.
