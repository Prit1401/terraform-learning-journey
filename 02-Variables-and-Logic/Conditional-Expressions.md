# Terraform Conditional Expressions
## What are Conditional Expressions?
Conditional expressions allow Terraform configurations to make decisions based on conditions.
They work similarly to if-else statements in programming languages.

---
## Syntax

```hcl
condition ? true_value : false_value
```

---
## Example

```hcl
instance_type = var.environment == "prod" ? "t3.medium" : "t2.micro"
```
Meaning:
- If environment is prod → use t3.medium
- Otherwise → use t2.micro

---
## Why are Conditional Expressions Needed?

- Reduces duplicate code.
- Supports environment-specific configurations.
- Improves flexibility.

---
## Real World Example

Development Environment:
```text
t2.micro
```
Production Environment:
```text
t3.medium
```
Using conditional expressions helps manage both scenarios using the same codebase.

---
## Interview Perspective

### Q. What is the syntax of a Terraform conditional expression?
```hcl
condition ? true_value : false_value
```
---
## Key Takeaways
- Conditional expressions provide decision-making capability.
- Useful when working with multiple environments.
