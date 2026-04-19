## Terms of Use – Configuration Details

### Overview

A Microsoft Entra **Terms of Use (ToU)** has been created to govern access to the demo tenant.
At this stage, the ToU exists but is **not yet enforced** via Conditional Access. Enforcement
will be added later during scenario testing.

---

### Terms of Use Configuration

| Setting | Value |
|------|------|
| **Name** | All Proseware users TOU |
| **Require users to expand the terms of use** | On |
| **Require users to consent on every device** | Off |
| **Expire consents** | Off |
| **Expire starting on** | – |
| **Frequency** | – |
| **Duration before re-acceptance required (days)** | 90 |
| **Users accepted** | 0 |
| **Users declined** | 0 |

---

### Reference Document

The Terms of Use document uploaded to Microsoft Entra was based on an existing
Acceptable Usage Policy stored in OneDrive.

**Reference location:**
- OneDrive → **MTC Demos** folder

This document is used as a suitable baseline for:
- Demo environments
- Non-production tenants
- Identity Governance and audit scenarios

---

### Current Enforcement State

- ✅ Terms of Use document created
- ✅ Document uploaded successfully
- ❌ Not yet attached to any Conditional Access policy
- ❌ No user prompts enforced at this stage

This is an intentional design choice to avoid impacting users during platform build
and initial scenario validation.

---

### Planned Next Step

The Terms of Use will be attached to one or more **Conditional Access policies**
during scenario testing, once lifecycle and access flows are validated.
