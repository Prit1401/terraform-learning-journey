# Terraform Scenarios and Interview Questions

## Scenario 1: Migrating Existing Infrastructure to Terraform
### Problem
A company already has infrastructure running in AWS, Azure, or GCP that was created manually or using another tool.
Terraform cannot automatically manage these resources because they are not present in the Terraform State file.

### Solution: Import Existing Resources
Terraform provides the `terraform import` command to bring existing resources under Terraform management.

---
## Step 1: Create Resource Configuration
Example:
```hcl
resource "aws_instance" "example" {
}
```

---
## Step 2: Import the Resource
```bash
terraform import aws_instance.example i-0123456789abcdef0
```

where:
* `aws_instance.example` → Terraform resource address
* `i-0123456789abcdef0` → Existing EC2 Instance ID

---

## Step 3: Verify State
```bash
terraform state list
```

```bash
terraform state show aws_instance.example
```

---
## Generate Configuration Automatically
```bash
terraform plan -generate-config-out=generated.tf
```

This command generates Terraform configuration for imported resources.

---
## Benefits
* Migrate existing infrastructure to Terraform.
* Avoid recreating production resources.
* Bring manually created resources under Infrastructure as Code.

---
## Interview Question
**Q:** How do you manage existing infrastructure using Terraform?
**Answer:**
I use the `terraform import` command to import existing resources into the Terraform State file and then generate or update the 
Terraform configuration to manage them through Infrastructure as Code.

---
# Scenario 2: Drift Detection

## What is Drift?
Drift occurs when someone manually changes cloud resources outside of Terraform.

Example:
* Terraform creates an EC2 instance as `t2.micro`.
* An engineer manually changes it to `t2.large` from AWS Console.
* Terraform State and actual infrastructure no longer match.

This mismatch is called **Infrastructure Drift**.

---
## Detecting Drift
### Option 1: Terraform Refresh
```bash
terraform refresh
```

This command updates the Terraform State file with the latest infrastructure changes.
> Note: In newer Terraform versions, `terraform plan` automatically performs a refresh before generating the execution plan.

---
### Option 2: Terraform Plan
```bash
terraform plan
```

Terraform compares:
* Configuration files
* State file
* Actual infrastructure

and reports any differences.

---
### Option 3: Automated Drift Detection
Organizations often automate drift detection by:
* Scheduled CI/CD jobs
* Cron Jobs
* AWS Lambda Functions
* Cloud Audit Logs
* CloudWatch Events

If a manual change is detected, an alert is sent to the team.

---
## Best Practices
* Avoid manual changes in production.
* Use IAM permissions to restrict console access.
* Run periodic `terraform plan`.
* Store State files remotely.
* Enable monitoring and alerting.

---
## Interview Question
**Q:** What is Terraform Drift?
**Answer:**
Terraform Drift occurs when infrastructure managed by Terraform is modified manually outside of Terraform, causing a mismatch 
between the Terraform State file and the actual infrastructure.

---
## Interview Question
**Q:** How do you detect Terraform Drift?

**Answer:**
* `terraform plan`
* `terraform refresh`
* Automated monitoring and audit logs
* Scheduled validation jobs in CI/CD pipelines

---
# Key Takeaways

✅ Import existing resources using `terraform import`.
✅ Generate configuration using:

```bash
terraform plan -generate-config-out=generated.tf
```

✅ Detect infrastructure drift using:
```bash
terraform plan
terraform refresh
```

✅ Implement monitoring and automation to prevent unauthorized changes.
