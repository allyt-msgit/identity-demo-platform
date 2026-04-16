#GitHub → Microsoft Entra authentication (OIDC App Registration)
##Purpose
This app registration enables secure, secretless authentication from GitHub Actions into Microsoft Entra using OpenID Connect (OIDC).
It is used to allow GitHub workflows to run Microsoft Graph / Azure commands without client secrets or certificates.
This pattern is required for:

Automating Entra configuration (branding, lifecycle workflows, etc.)
Running Graph PowerShell or Azure CLI from GitHub Actions
Aligning with Microsoft Zero Trust and workload identity best practice


##App Registration Overview

App name: github-demo-build
Tenant: <this Entra tenant>
Authentication type: Federated credentials (OIDC)
Trust model: GitHub Actions → Microsoft Entra
Secrets: ❌ None (no client secrets or certs)


##Federated Credential Configuration
The app registration uses a Federated credential with the following settings:
Federated credential scenario

Scenario: GitHub Actions deploying Azure resources

This configures Entra to trust GitHub as an external identity provider for this application.

GitHub account linkage

























SettingValueOrganisationallys-msgezRepositorydemo-brandingEntity typeBranchBranch namemain
This ensures that only workflows running on the main branch of the specified repository are trusted.

Subject identifier (auto-generated)
The subject identifier is automatically constructed by Entra based on the GitHub inputs:
Plain Textrepo:allys-msgez/demo-branding:ref:refs/heads/main``Show more lines
This value is validated against the OIDC token issued by GitHub Actions at runtime.

Credential details





















FieldValueNamegithub-basicDescriptionused for github access for deploymentAudienceapi://AzureADTokenExchange
The audience value is required for Entra workload identity federation and must not be changed.

Why OIDC is used (instead of secrets)

No client secrets stored in GitHub
No certificate rotation
Tokens are short-lived and issued per workflow run
Access is tightly scoped to:

One repository
One branch


Fully auditable in Entra sign-in logs

This is the recommended Microsoft pattern for GitHub → Azure / Entra integration.

How this is used in practice
In GitHub Actions, workflows will:

Request an OIDC token from GitHub
Exchange it with Microsoft Entra using this app registration
Obtain an access token for:

Microsoft Graph
Azure Resource Manager (if required)



This enables running commands such as:

Microsoft Graph PowerShell
Azure CLI
Bicep / ARM deployments
Entra configuration scripts

All without storing secrets.

Dependencies / prerequisites

App registration exists in Entra
Federated credential configured as above
App registration granted appropriate API permissions (e.g. Microsoft Graph)
GitHub workflow uses OIDC (permissions: id-token: write)


Notes

Any change to repository name, organisation, or branch will break authentication until the federated credential is updated.
Multiple federated credentials can be created if different repos or branches need access.
This app registration is intended for automation, not interactive use.
