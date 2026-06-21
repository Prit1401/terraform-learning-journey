# Terraform Workspaces

## Introduction
Terraform Workspaces allow you to manage multiple environments (Dev, Stage, Prod) using the same Terraform code.
Each workspace has its own separate state file, preventing conflicts between environments.

---
## Why Do We Need Workspaces?
Without workspaces, Terraform uses a single state file. Running the same code for different environments may overwrite or modify existing infrastructure.

Problems:
* State conflicts
* Infrastructure overwrites
* Duplicate code in multiple folders

Workspaces solve this problem by creating separate state files for each environment.

---
## How Workspaces Work
```text
terraform.tfstate.d/
├── dev/
├── stage/
└── prod/
```

Each workspace maintains its own infrastructure state.

---
## Workspace Commands
### Create a Workspace
```bash
terraform workspace new dev
```

### List Workspaces
```bash
terraform workspace list
```

### Switch Workspace
```bash
terraform workspace select prod
```

### Show Current Workspace
```bash
terraform workspace show
```

### Delete Workspace
```bash
terraform workspace delete dev
```
---
## Using terraform.workspace
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

Terraform automatically selects the correct value based on the current workspace.

---
## Benefits of Workspaces
* Environment isolation
* Code reusability
* Easy environment management
* Separate state files
* Less code duplication

---
## Best Practices
* Use one codebase for all environments.
* Always verify the current workspace before apply or destroy.
* Use remote backends for team environments.
* Protect production workspace.

---
## Common Mistakes
* Running destroy in the wrong workspace.
* Forgetting to switch workspace.
* Hardcoding environment values.

---
## Summary
Terraform Workspaces allow you to manage multiple environments using the same code while keeping their state files completely isolated.

