## Active Directory – Initial OU and User Objects

### Domain
`MngEnvMCAP611031.onmicrosoft.com`  
(NetBIOS: `MCAP611031`)

---

## Organisational Unit (OU)

### OU: `OnpremUsers`

**Location:**  
MngEnvMCAP611031.onmicrosoft.com
└── OnpremUsers

**Purpose:**
- Contains initial on-premises user accounts
- Separates users from default `Users` container
- Designed as a target OU for future:
  - Group Policy
  - Entra ID / sync experimentation
  - Role-based access modelling

---

## User Accounts

### 1. Brendon Van Eyssen

| Attribute | Value |
|--------|------|
| Name | Brendon Van Eyssen |
| Display Name | Brendon Van Eyssen |
| User Logon Name (UPN) | `bvaneyssen@MngEnvMCAP611031.onmicrosoft.com` |
| Job Title | SOC Manager |
| Department | SOC |
| Office | London |
| OU | `OnpremUsers` |

---

### 2. Cooper Turnbull

| Attribute | Value |
|--------|------|
| Name | Cooper Turnbull |
| Display Name | Cooper Turnbull |
| User Logon Name (UPN) | `cturnbull@MngEnvMCAP611031.onmicrosoft.com` |
| Job Title | SOC Analyst |
| Department | SOC |
| Office | London |
| OU | `OnpremUsers` |

---

## Reporting Structure

The following **explicit reporting relationship** is defined:

- **Cooper Turnbull reports to Brendon Van Eyssen**

> This relationship has been captured for organisational modelling and future identity governance scenarios.

---

## Notes

- These users were created manually as part of the initial Active Directory build.
- No Group Policy Objects (GPOs) are currently linked to the `OnpremUsers` OU.
- This structure is intended as a **baseline** and will evolve as:
  - Identity governance scenarios are explored
  - Entra ID integration is introduced
