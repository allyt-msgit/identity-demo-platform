## Microsoft Entra Cloud Sync – Provisioning Agent Configuration

### Agent Installation Location
- **Server:** DC01
- **Role:** Domain Controller
- **OS:** Windows Server (domain-joined)

> Installation of the Microsoft Entra provisioning agent on a Domain Controller is supported and used intentionally in this environment.

---

### Active Directory Configuration

- **Active Directory Domain:**
 MngEnvMCAP611031.onmicrosoft.com

- **Agent Service Account:**

MngEnvMCAP611031.onmicrosoft.com\provAgentgMSA

- **Account Type:**
- Group Managed Service Account (gMSA)
- Automatically created and managed by the Cloud Sync installer

> No manually created service accounts are used for Cloud Sync.

---

### Microsoft Entra ID Configuration

- **Signed-in Entra administrator during configuration:**

alturnbu@MngEnvMCAP611031.onmicrosoft.com

- **Role used for configuration:**
- Hybrid Identity Administrator (or higher)

---

### Design Notes

- The Cloud Sync agent is registered directly with Microsoft Entra ID.
- Synchronisation configuration and logic are managed **in the cloud**, not on the server.
- DC01 performs only the lightweight agent role; no local sync engine or SQL database is installed.
- This aligns with Microsoft’s strategic direction for new hybrid identity deployments.

---

### Status at Time of Capture

- Agent configuration confirmed prior to activation
- Active Directory and Entra ID contexts validated
- No user or group sync scopes applied at this stage
