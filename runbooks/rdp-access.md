# Secure RDP Access to Demo Virtual Machines

## Purpose

This document describes **how Remote Desktop (RDP) access works** for demo virtual
machines in the Entra Identity Governance demo platform, and the **approved method**
for connecting securely.

RDP access is intentionally restricted to:
- Reduce attack surface
- Align with Zero Trust principles
- Prevent access from Microsoft corporate networks

---

## Important Behaviour to Understand

### ❌ RDP does NOT work from Microsoft Corporate Networks

You **cannot** RDP to these demo VMs when connected to:
- Microsoft corporate LAN
- Microsoft VPN
- Microsoft managed wired or wireless networks

This is expected and by design.

Outbound RDP (TCP 3389) is blocked on Microsoft networks and **cannot be bypassed**.

---

## ✅ Approved Network for RDP

To connect successfully, you must use:

- **Wi‑Fi:** `MSFTONENET`
- Or a personal hotspot / non‑Microsoft network

This ensures outbound RDP traffic is permitted.

---

## Security Model Overview

RDP access is secured using:

- **Just‑In‑Time (JIT) VM Access**
- **Subnet‑level Network Security Groups**
- **Time‑bound inbound access only**
- **No permanently open RDP ports**

| Control | Status |
|---|---|
| Permanent RDP (3389) | ❌ Disabled |
| JIT access | ✅ Enabled |
| NSG open inbound | ❌ No |
| Source IP restriction | ✅ Yes |

---

## Step‑by‑Step: How to Connect via RDP

### 1. Connect to the Approved Network

Ensure your device is connected to:
- ✅ **MSFTONENET Wi‑Fi**
- ❌ Not Microsoft VPN
- ❌ Not Microsoft wired network

---

### 2. Open the VM in Azure Portal

1. Go to **Azure Portal**
2. Navigate to:
3. Virtual Machines → <vm name=""> → Connect</vm>
3. Select **Connect** (RDP)

---

### 3. Verify Connection Prerequisites

On the **Connect** page, confirm the following show green ✅:

| Check | Expected State |
|---|---|
| Just‑in‑Time (JIT) access | ✅ Granted |
| VM port | 3389 |
| Source IP | Your current public IP |
| NSG check | ✅ Accessible |

If JIT is not enabled:
- Select **Configure JIT + Request access**
- Request access for **TCP 3389**
- Duration: 1–3 hours (demo‑friendly)

---

### 4. Download and Use the RDP File

1. Select **Download RDP file**
2. Open the file locally
3. When prompted for credentials:

| Field | Value |
|---|---|
| Username | Local admin account (e.g. `localadmin`) |
| Password | Stored securely in **Dashlane** |

> ⚠️ Credentials are **never stored in Azure** and must not be shared or hard‑coded.

---

### 5. Successful Connection

Once connected:
- You are logged in using the **local bootstrap account**
- The session is valid **only while JIT is active**
- When the JIT window expires, RDP access automatically closes

---

## Credential Management

- Local administrator credentials are:
- Used **only** for initial access and recovery
- Stored securely in **Dashlane**
- All demo scenarios are performed using:
- **Microsoft Entra user sign‑in**
- **Entra‑joined workstation sessions**

---

## Troubleshooting

### RDP fails immediately
- Check you are **not** on a Microsoft corporate network
- Switch to:
- MSFTONENET
- Personal hotspot

### JIT access denied
- Confirm:
- Defender for Cloud is enabled
- You requested access for TCP 3389
- The request duration has not expired

### Credentials not accepted
- Validate username spelling
- Retrieve the password from Dashlane
- Confirm you are not attempting Entra VM login (not enabled)

---

## Security Rationale

This access model is intentional and provides:

- Zero Trust–aligned access control
- No standing inbound exposure
- Strong auditability for demos
- A realistic enterprise security posture

---

## Summary

✅ RDP access is **supported**, but strictly controlled  
✅ Microsoft corporate networks are **blocked by design**  
✅ JIT + MSFTONENET is the **approved access path**  
✅ Credentials are handled securely via Dashlane  

This model ensures the demo environment remains secure while still being usable for live demonstrations.
