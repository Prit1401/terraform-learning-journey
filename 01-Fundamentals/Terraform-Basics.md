# Terraform Fundamentals

## What is Terraform?

Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp. It allows engineers to provision, manage, and update infrastructure using code instead of manually creating resources through cloud provider consoles.

---

## Why Terraform Was Created?

Before Terraform, infrastructure was created manually through cloud consoles. This approach had several challenges:

- Time-consuming process
- Human errors
- Lack of consistency across environments
- Difficult to track infrastructure changes
- Limited reusability

Terraform was introduced to automate infrastructure provisioning and make infrastructure management repeatable, version-controlled, and scalable.

---
## What is Infrastructure as Code (IaC)?

Infrastructure as Code (IaC) is the practice of managing and provisioning infrastructure through code rather than manual processes.

Instead of manually creating resources such as servers, storage, and networking components, engineers define them using configuration files.

### Benefits of IaC

- Automation
- Consistency
- Reusability
- Version Control
- Faster Provisioning
- Reduced Human Errors

---
# Terraform Core Lifecycle Commands

Terraform follows a lifecycle approach to manage infrastructure.

---
## terraform init

### Purpose

Initializes the Terraform working directory.

### What it does

- Reads Terraform configuration files
- Downloads required provider plugins
- Initializes the backend configuration
- Creates the `.terraform` directory

### Creates Infrastructure?
❌ No

---
## terraform plan
### Purpos
Generates an execution plan before making any changes.

### What it does
- Compares the current state with the desired state
- Shows resources to be added, modified, or destroyed

### Creates Infrastructure?
❌ No
---

## terraform apply
### Purpose
Applies the planned changes.

### What it does
- Creates infrastructure
- Updates existing resources if needed
- Records changes in the state file

### Creates Infrastructure?
✅ Yes

---
## terraform destroy
### Purpose
Deletes all infrastructure managed by the current Terraform configuration.

### What it does
- Removes provisioned resources
- Updates the Terraform state accordingly

### Deletes Infrastructure?
✅ Yes

---
# Provider Block
## What is a Provider?
A provider is a plugin that enables Terraform to interact with APIs of cloud platforms and other services.

Examples include:
- AWS
- Azure
- Google Cloud Platform (GCP)

### Example
provider "aws" {
  region = "ap-south-1"
}

---
## Why is a Provider Needed?
Terraform itself does not know how to communicate with cloud platforms.
Providers act as translators between Terraform and the target platform APIs.

---
# Resource Block
## What is a Resource?
A resource block defines the infrastructure component that Terraform should create or manage.

Examples:
- EC2 Instances
- S3 Buckets
- VPCs
- Security Groups

### Example
resource "aws_instance" "web" {
  ami           = "ami-xxxxxxxx"
  instance_type = "t2.micro"
}

---
# Important Terraform Files
## main.tf
The primary configuration file where Terraform resources and providers are typically defined.

Purpose:
- Defines the desired infrastructure state.

---
## terraform.tfstate
A state file automatically created by Terraform.

Purpose:
- Tracks infrastructure managed by Terraform.
- Maps configuration to real-world resources.
- Helps Terraform determine changes during future executions.

Note:
Do not edit the state file manually.
---

# Key Takeaways
- Terraform is an Infrastructure as Code tool.
- IaC enables infrastructure management through code.
- Providers allow Terraform to communicate with cloud platforms.
- Resources define what infrastructure should be created.
- `terraform init` prepares the environment.
- `terraform plan` previews changes.
- `terraform apply` creates or updates infrastructure.
- `terraform destroy` removes infrastructure.
- `terraform.tfstate` keeps track of managed resources.
