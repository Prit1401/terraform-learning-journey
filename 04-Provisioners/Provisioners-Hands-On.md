# Hands-On: Deploy Python Application Using Provisioners

## Objective
Create an EC2 instance and automatically deploy a Python application.

## Steps

### Step 1
Create networking resources:
* VPC
* Public Subnet
* Route Table
* Internet Gateway
* Security Group

### Step 2
Create EC2 Instance.

### Step 3
Copy application file.
```hcl
provisioner "file" {
  source = "app.py"
  destination = "/tmp/app.py"
}
```

### Step 4
Execute commands remotely.
```hcl
provisioner "remote-exec" {
  inline = [
    "sudo apt update",
    "sudo apt install python3-pip -y",
    "python3 /tmp/app.py"
  ]
}
```

### Step 5
Run Terraform.
```bash
terraform init
terraform plan
terraform apply
```

### Verification
```bash
ssh -i key.pem ubuntu@<public-ip>
ps -ef | grep python
curl http://<public-ip>:5000
```

### Cleanup
```bash
terraform destroy
```
