# Terraform Workspaces Hands-On

## Objective
Create and manage Dev, Stage, and Production environments using Terraform Workspaces.

---
## Create Workspaces
```bash
terraform workspace new dev
terraform workspace new stage
terraform workspace new prod
```

---
## List Workspaces
```bash
terraform workspace list
```

---
## Switch Workspace
```bash
terraform workspace select dev
terraform workspace select stage
terraform workspace select prod
```

---
## Verify Current Workspace
```bash
terraform workspace show
```

---
## Apply Infrastructure

```bash
terraform apply
```

---
## Destroy Infrastructure

```bash
terraform destroy
```

⚠️ Always verify the current workspace before running `terraform destroy`.

---
## Example
```hcl
instance_type = lookup(
{
  dev   = "t2.micro"
  stage = "t2.medium"
  prod  = "t2.xlarge"
},
terraform.workspace
)
```
This automatically creates different server sizes for different environments.

