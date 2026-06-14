# Terraform Modules Hands-On
## Objective
Learn how to create and consume reusable Terraform modules.

---
## Module Structure
A standard Terraform module structure looks like this:

```text
modules/
└── ec2_instance/
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```

---
## Step 1: Create a Module
Inside the module directory, define the required resources.

Example:
```hcl
resource "aws_instance" "example" {
  ami           = var.ami_value
  instance_type = var.instance_type_value
  subnet_id     = var.subnet_id_value
}
```

---
## Step 2: Define Input Variables
Create a `variables.tf` file.

Example:

```hcl
variable "ami_value" {
  type = string
}

variable "instance_type_value" {
  type = string
}

variable "subnet_id_value" {
  type = string
}
```

---
## Step 3: Define Outputs
Create an `outputs.tf` file.

Example:
```hcl
output "public_ip" {
  value = aws_instance.example.public_ip
}
```

---
## Step 4: Call the Module
From the root project, use the `module` block.

Example:
```hcl
module "ec2_instance" {
  source              = "./modules/ec2_instance"
  ami_value           = "ami-xxxxxxxx"
  instance_type_value = "t2.micro"
  subnet_id_value     = "subnet-xxxxxxxx"
}
```

---
## Step 5: Initialize Terraform
Run:

```bash
terraform init
```

Purpose:
- Downloads providers
- Downloads module dependencies
- Initializes the working directory

---
## Step 6: Preview Changes

Run:
```bash
terraform plan
```

Purpose:
- Displays the proposed infrastructure changes.

---
## Step 7: Apply Changes
Run:

```bash
terraform apply
```

Purpose:
- Creates the infrastructure defined in the module.

---
## Step 8: Verify Outputs
Review the output values displayed after successful execution.

Examples:
- Public IP Address
- Instance ID
- DNS Name

---
## Step 9: Destroy Resources
Run:
```bash
terraform destroy
```

Purpose:
- Deletes all resources managed by Terraform.

---
## Important Notes
- Run `terraform init` whenever a new module is added.
- Modules improve reusability and maintainability.
- Use variables instead of hardcoded values.
- Store sensitive values outside Terraform code.

---
## Interview Perspective
### What are the steps involved in creating and using a Terraform module?

1. Create module resources.
2. Define input variables.
3. Define outputs.
4. Call the module.
5. Initialize Terraform.
6. Plan the changes.
7. Apply the configuration.

---
## Key Takeaways
- Modules allow infrastructure reuse.
- Inputs make modules flexible.
- Outputs expose useful information.
- Hands-on practice is essential for understanding modules.
