# ADR-001 – No Custom DNS Domain

## Status
Accepted

## Context

The Microsoft Entra tenant used for this demo platform is **provisioned and governed under Microsoft’s Secure Future Initiative (SFI)**.

As part of this provisioning model:
- The tenant does **not support onboarding a custom DNS domain**
- The default `*.onmicrosoft.com` domain is the only available namespace

This constraint is imposed at the platform level and cannot be overridden via admin roles or configuration.

---

## Decision

We will **not use a custom DNS domain** in this environment.

All identities will use the default tenant domain:

``
MngEnvMCAP611031.onmicrosoft.com

Email, branding, and UPN alignment are explicitly **out of scope** for this platform.

---

## Rationale

This decision is intentional and aligned with modern identity guidance:

- Secure Future Initiative prioritises **tenant isolation and abuse prevention**
- Identity architecture does **not require email or DNS ownership**
- Verified Identity, Conditional Access, device trust, and Zero Trust controls do not depend on custom domains
- Removing domain dependency reinforces a **cloud-first, cryptographic trust model**

This constraint also supports realistic customer conversations, as many non-production and demo tenants are similarly restricted.

---

## Consequences

### Positive
- Simplifies tenant governance
- Reduces attack surface
- Aligns with SFI “secure by default” principles
- Strengthens narratives around:
  - Passwordless
  - Verified ID
  - Identity beyond email

### Negative
- No branded UPNs
- No realistic Exchange or mail-flow demos
- Reduced visual realism in customer-facing screenshots

These trade-offs are accepted and documented.

---

## Notes for demos

When explaining this decision to customers:

> “This environment deliberately avoids custom domains to demonstrate that modern identity security should not depend on email addresses or DNS ownership.”

This framing has proven effective in Zero Trust and identity modernisation discussions.
