# ADR-003 – Email Is Not a Foundational Identity Dependency

## Status
Accepted

## Context

Traditional enterprise identity architectures strongly couple identity to email:
- Usernames double as mail addresses
- Email is treated as the primary identifier
- Many access decisions implicitly assume mailbox availability

In this demo platform, the Microsoft Entra tenant is:
- Secure Future Initiative (SFI) governed
- Restricted to the default `onmicrosoft.com` domain
- Focused on modern identity and Zero Trust security

This provides an opportunity to **intentionally decouple identity from email**.

---

## Decision

Email is **not treated as a foundational identity dependency** in this environment.

Specifically:
- Exchange Online is optional
- Internal mail may exist for collaboration and signal generation
- External mail flow, branding, and domain-based email scenarios are out of scope
- Identity, access control, and security enforcement must function without reliance on email

---

## Rationale

This decision aligns with modern identity and security principles:

- Identity should not depend on a single workload (email)
