# Terraform Outputs

## What are Outputs?
Outputs allow Terraform to display important information after infrastructure has been provisioned.

Examples:
- Public IP Address
- Instance ID
- DNS Name
  
---
## Why are Outputs Needed?
- Easy access to resource details.
- Sharing information between modules.
- Visibility after deployment.

---
## Example
output "public_ip" {
  value = aws_instance.web.public_ip
}

---
# Key Takeaways
- Outputs expose useful information.
- Displayed after terraform apply.
