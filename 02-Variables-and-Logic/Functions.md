# Terraform Functions
## What are Functions?
Functions are built-in operations provided by Terraform to manipulate data and simplify configurations.

---

## Why are Functions Needed?
Functions help avoid manual data transformations and make Terraform code more efficient.

---
# Common Functions
## length()
Returns the number of elements.

Example:
```hcl
length(["dev", "qa", "prod"])
```

Output:
```text
3
```

---
## upper()
Converts text to uppercase.
Example:
```hcl
upper("terraform")
```

Output:
```text
TERRAFORM
```

---
## lower()
Converts text to lowercase.

Example:
```hcl
lower("TERRAFORM")
```

Output:
```text
terraform
```

---
## lookup()
Retrieves a value from a map.

Example:
```hcl
lookup(
  {
    dev  = "t2.micro"
    prod = "t3.medium"
  },
  "prod"
)
```

Output:
```text
t3.medium
```

---
## Benefits of Functions
- Simplifies configurations.
- Reduces manual effort.
- Improves readability.

---
## Interview Perspective
### Q. Why are Terraform functions used?
Terraform functions are used to manipulate data and simplify infrastructure configurations.

---
## Key Takeaways
- Functions are built into Terraform.
- They help transform and manage data efficiently.
