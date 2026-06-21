# Terraform and HashiCorp Vault

## Introduction
HashiCorp Vault is a tool used to securely store and manage sensitive information such as:
* Passwords
* API Tokens
* Database Credentials
* Certificates
* SSH Keys

Terraform can retrieve these secrets during infrastructure deployment without exposing them in the code.

---
## Why Use Vault?
Storing secrets directly in Terraform code or Git repositories is not secure.
Vault provides:
* Secure secret storage
* Encryption at rest
* Access control and authentication
* Secret rotation and auditing

---
## How Vault Works
```text
Terraform → Vault → Secret → Infrastructure
```
Terraform authenticates with Vault, retrieves the required secret, and uses it during deployment.

---
## Authentication Methods

Terraform can authenticate using:
* AppRole
* Token
* AWS IAM
* Kubernetes Authentication

In this demo, AppRole authentication is used.

---
## AppRole Authentication
AppRole generates:
* Role ID
* Secret ID

These credentials allow Terraform to securely access secrets stored in Vault.

---
## Storing a Secret

Example:
```text
username = admin
password = my-secret-password
```

Vault automatically encrypts the data.

---
## Reading Secrets in Terraform
```hcl
data "vault_kv_secret_v2" "demo" {
  mount = "secret"
  name  = "demo"
}
```

---
## Accessing the Secret
```hcl
data.vault_kv_secret_v2.demo.data["password"]
```

---
## Example Use Cases
* Database passwords
* API keys
* SSH credentials
* Kubernetes secrets
* Third-party tokens

---
## Benefits of Vault
* Centralized secret management
* Secure authentication
* Encryption and auditing
* Eliminates hardcoded credentials
* Better compliance and security

---
## Best Practices
* Never hardcode secrets in Terraform files.
* Use least-privilege policies.
* Rotate secrets regularly.
* Store sensitive information only in Vault.
* Restrict access using policies and roles.

---
## Summary
HashiCorp Vault enables Terraform to securely retrieve sensitive information during infrastructure deployments without exposing secrets in code or repositories.

