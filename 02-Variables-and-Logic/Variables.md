
# Terraform Variables

## What are Variables?
Variables allow us to parameterize Terraform configurations by avoiding hardcoded values.
Instead of modifying the code repeatedly for different environments, variables help make configurations reusable and flexible.
---

## Why are Variables Needed?
Without variables:
- Code duplication increases.
- Different environments require manual changes.
- Maintenance becomes difficult.

With variables:
- Reusability improves.
- Environment-specific values can be supplied externally.
- Infrastructure becomes more flexible.
---

# Input Variables
Input variables accept values from users.
## Declaration
variable "instance_type" {
  type    = string
  default = "t2.micro"
}

## Usage
instance_type = var.instance_type
---

# Variable Components
## Name
Unique identifier of the variable.

## Type
Defines the expected data type.

Examples:
- string
- number
- bool
- list
- map

## Default
Provides a fallback value.
---

# Benefits of Variables
- Reusability
- Flexibility
- Better maintainability
- Reduced hardcoding
---

# Key Takeaways
- Variables make Terraform code dynamic.
- Input variables accept values from users.
- Variables reduce duplication.
