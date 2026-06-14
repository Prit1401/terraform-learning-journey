# Terraform Module Sources
## What are Module Sources?
Module sources define where Terraform should retrieve the module code from.
When using a module, Terraform needs to know the location of the module implementation.

---
## Types of Module Sources
### 1. Local Modules
Modules stored within the same repository.

Example:

```hcl
module "ec2_instance" {
  source = "./modules/ec2"
}
```

### Use Cases
- Learning purposes
- Small projects
- Internal repository structures

---
### 2. Terraform Registry Modules
Modules published in the official Terraform Registry.

Example:

```hcl
module "vpc" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "5.0.0"
}
```

### Benefits

- Quick implementation
- Community-supported
- Well-documented

### Limitations

- Limited customization
- Dependency on external maintainers

---
### 3. GitHub Modules
Modules stored in Git repositories.
Example:

```hcl
module "ec2" {
  source = "git::https://github.com/organization/terraform-modules.git//ec2"
}
```
### Benefits

- Version controlled
- Easy collaboration
- Internal standardization

---
### 4. Private Modules
Modules hosted in private repositories.
These are commonly used in organizations to enforce security and compliance standards.

### Benefits

- Improved security
- Better governance
- Organization-specific implementations

---
## Industry Perspective
Most organizations prefer using private modules hosted in internal Git repositories.
Reasons include:

- Security requirements
- Standardization
- Better control over updates
- Compliance adherence

---
## Interview Perspective
### What are the different types of Terraform module sources?
Terraform modules can be sourced from:

- Local directories
- Terraform Registry
- Git repositories
- Private repositories

---
### Which module source is commonly used in enterprises?
Private Git repositories are commonly used because they provide better control, security, and standardization.

---
## Key Takeaways
- Module sources specify where Terraform retrieves module code.
- Local modules are useful for learning.
- Terraform Registry provides reusable public modules.
- Enterprises typically rely on private modules.
