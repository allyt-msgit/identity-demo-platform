## Active Directory Domain Configuration

**Domain Controller:** DC01  
**AD Forest / Domain DNS Name:**  
`MngEnvMCAP611031.onmicrosoft.com`

**NetBIOS Name:**  
`MCAP611031`

### Rationale
- This environment is a demo / lab and does not have ownership of a public DNS domain.
- Using the tenant’s initial Microsoft Entra namespace (`*.onmicrosoft.com`) avoids the need for public domain management.
- AD-integrated DNS is hosted locally on the Domain Controller.
- No dependency on Azure DNS or public DNS resolvers.

### Notes
- DNS zone for `MngEnvMCAP611031.onmicrosoft.com` is created automatically during AD DS promotion.
- This domain is private to the VNet and only resolvable from within the environment.
- The NetBIOS name was explicitly set to avoid truncation and ensure clarity.

### Recovery
- **DSRM (Directory Services Restore Mode) password** is stored securely in **Dashlane**.
- Backup is provided via **Azure Backup** (single DC, no high availability).

### Caveats
- The AD namespace is tightly aligned with the Entra initial tenant domain.
- This is acceptable for demo and POC scenarios but would normally be revisited for production designs.
