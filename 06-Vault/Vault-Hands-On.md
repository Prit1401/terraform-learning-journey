# Terraform Vault Hands-On

## Objective
Store secrets in HashiCorp Vault and use them securely inside Terraform.

---
## Step 1: Install Vault
Install HashiCorp Vault on an Ubuntu server or EC2 instance.

---
## Step 2: Start Vault Development Server
```bash
vault server -dev
```

---
## Step 3: Export Vault Address
```bash
export VAULT_ADDR='http://127.0.0.1:8200'
```

---
## Step 4: Login to Vault
```bash
vault login <root-token>
```

---
## Step 5: Create a Secret
```bash
vault kv put secret/demo \
username=admin \
password=password123
```

---
## Step 6: Configure Vault Provider
```hcl
provider "vault" {}
```

---
## Step 7: Read Secret from Vault
```hcl
data "vault_kv_secret_v2" "demo" {
  mount = "secret"
  name  = "demo"
}
```

---
## Step 8: Use Secret in Resource
```hcl
tags = {
  password = data.vault_kv_secret_v2.demo.data["password"]
}
```

---
## Initialize Terraform
```bash
terraform init
```

---
## Deploy Infrastructure
```bash
terraform apply
```

--
## Verify
Check that the secret value has been successfully retrieved from Vault and used during resource creation.

---
## Cleanup

```bash
terraform destroy
```

This demonstration shows how Terraform can securely consume secrets from HashiCorp Vault without storing sensitive information in code.

