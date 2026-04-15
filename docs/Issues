## Connectivity Issue – RDP access to Azure VM blocked on corporate network

**Date:** 2026-04-15  
**Component:** Azure VM (DC01) – RDP access  
**Status:** Resolved

### Issue
Unable to establish an RDP connection to the Azure VM (`DC01`) despite:
- VM running and healthy
- Public IP correctly configured and associated
- NSGs and Defender Just-In-Time (JIT) access configured correctly
- No errors reported in Azure networking diagnostics

RDP attempts consistently failed with:
- Error `0x204`
- Client reason `516`
- No Windows logon screen presented

### Root Cause
Outbound RDP (TCP 3389) is **blocked on the corporate Microsoft network**.

The block occurs **before traffic reaches Azure**, meaning:
- Azure-side logs and diagnostics appear healthy
- No inbound connection is ever received by the VM
- Serial Console remains the only available access path

### Resolution
Switched to an alternative, non-corporate network (e.g. home / mobile hotspot).

Once connected via a different network:
- RDP connection succeeded immediately
- VM logon screen was presented
- No changes were required in Azure (networking, NSGs, JIT, NAT Gateway)

### Validation
- Successful RDP connection from non-corporate network
- Confirmed issue reproducible only when connected to corporate network

### Notes
- This is a **client-side / network egress restriction**, not an Azure configuration issue
- NAT Gateway configuration was **not** related (NAT handles outbound traffic from the VM only)
- Just-In-Time access was functioning as expected

