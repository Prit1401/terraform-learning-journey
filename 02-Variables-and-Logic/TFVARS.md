# Terraform TFVARS
## What is a TFVARS File?

A TFVARS file is used to provide values to Terraform input variables.
Instead of hardcoding values inside Terraform code, TFVARS allows us to separate configuration from variable values.

---
## Why are TFVARS Needed?

Without TFVARS:
- Values are hardcoded.
- The same code cannot be reused easily across environments.
- Maintenance becomes difficult.

With TFVARS:
- The same code can be reused.
- Environment-specific values can be managed separately.
- Improves maintainability.

---

## terraform.tfvars
Terraform automatically loads values from a file named:
terraform.tfvars

Example:
instance_type = "t2.micro"
environment   = "dev"

---

## Custom TFVARS Files
Examples:
dev.tfvars
prod.tfvars
qa.tfvars

Terraform does NOT load these automatically.
They must be specified explicitly.

Example:
terraform apply -var-file="dev.tfvars"

---
## Benefits of TFVARS

- Better code reusability
- Environment-specific configurations
- Reduces hardcoding
- Easier maintenance

---
## Interview Perspective
### Q. What is the purpose of TFVARS?
TFVARS files are used to supply values to input variables without modifying the Terraform code.

---
## Key Takeaways
- TFVARS store variable values.
- terraform.tfvars loads automatically.
- Custom TFVARS files require explicit reference.
