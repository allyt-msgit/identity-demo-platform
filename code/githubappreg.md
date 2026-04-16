# GitHub → Microsoft Entra Authentication (OIDC App Registration)

## Purpose

This document describes the Microsoft Entra **App Registration** used to enable
**secure, secretless authentication** from **GitHub Actions** into Microsoft Entra
using **OpenID Connect (OIDC)**.

This integration allows GitHub workflows to run Microsoft Graph, Entra, or Azure
automation without storing client secrets or certificates.

This pattern is required for:

- Automating tenant branding deployment
- Running Microsoft Graph PowerShell from GitHub Actions
- Rebuilding Entra Lifecycle Workflows as code
- Aligning with Zero Trust workload identity best practice

---

## High-level Design

- **Auth model:** Workload identity federation (OIDC)
- **Identity provider:** GitHub Actions
- **Trust anchor:** Microsoft Entra App Registration
- **Secrets:** ❌ None
- **Token lifetime:** Short-lived, per workflow run
- **Scope:** Repository- and branch-specific

---

## App Registration Overview

| Property | Value |
|------|------|
| **Application name** | `github-demo-build` |
| **Tenant** | This Entra tenant |
| **Authentication type** | Federated credentials (OIDC) |
| **Credential storage** | None (no secrets or certificates) |
| **Intended use** | GitHub Actions automation |

This application is **non-interactive** and must not be used for manual sign-in.

---

## Federated Credential Configuration

### Federated credential scenario

- **Scenario:** `GitHub Actions deploying Azure resources`

This configures Microsoft Entra to trust GitHub as an external OpenID Connect
identity provider for this application.

---

### GitHub account linkage

The federated credential is strictly scoped to a single repository and branch:

| Field | Value |
|----|-----|
| **Organisation** | `allyt-msgit` |
| **Repository** | `demo-branding` |
| **Entity type** | `Branch` |
| **Branch name** | `main` |
| **Subject identifier repo:allyt-msgit/demo-branding:ref:refs/heads/main
Only workflows executing from **this repository and branch** are trusted.

---

### Subject identifier (auto-generated)

Microsoft Entra automatically generates and validates the subject identifier
based on the GitHub OpenID token:

```text
repo:allys-msgez/demo-branding:ref:refs/heads/main

Cred name - github-oidc






