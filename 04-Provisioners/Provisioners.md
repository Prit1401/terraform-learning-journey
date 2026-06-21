# Terraform Provisioners

## Introduction
Terraform Provisioners are used to execute scripts or commands on a local machine or remote server during resource creation or 
destruction.Provisioners act as a bridge between infrastructure provisioning and application deployment.

## Why Do We Need Provisioners?
In real-world scenarios, creating a server is only the first step. After the server is created, we often need to:
* Install software packages
* Copy configuration files
* Deploy applications
* Start services
* Run initialization scripts

Provisioners help automate these tasks.

## Types of Provisioners
### 1. File Provisioner
Copies files or directories from the local machine to a remote server.

#### Use Cases
* Copy application code
* Copy configuration files
* Upload scripts

#### Example
```hcl
provisioner "file" {
  source      = "app.py"
  destination = "/tmp/app.py"
}
```

---
### 2. Remote-Exec Provisioner
Executes commands on the remote server.

#### Use Cases
* Install packages
* Configure applications
* Start services

#### Example
```hcl
provisioner "remote-exec" {
  inline = [
    "sudo apt update",
    "sudo apt install python3 -y",
    "python3 /tmp/app.py"
  ]
}
```

---
### 3. Local-Exec Provisioner
Executes commands on the machine running Terraform.

#### Use Cases
* Store logs
* Send notifications
* Print messages
* Trigger external scripts

#### Example

```hcl
provisioner "local-exec" {
  command = "echo EC2 Created Successfully"
}
```

---
## Connection Block

Terraform uses a connection block to connect to remote servers.
```hcl
connection {
  type        = "ssh"
  user        = "ubuntu"
  private_key = file("key.pem")
  host        = self.public_ip
}
```

---
## Provisioner Lifecycle
1. Create Infrastructure
2. Establish Connection
3. Copy Files
4. Execute Commands
5. Deploy Application

---
## Best Practices
* Use provisioners only when necessary.
* Prefer cloud-init or configuration management tools for complex setups.
* Keep scripts idempotent.
* Store SSH keys securely.
* Avoid hardcoding sensitive information.

---

## Common Issues
* SSH connection timeout
* Incorrect private key permissions
* Wrong username
* Application process not starting in the background
* Security group blocking port 22

---
## Summary
Terraform Provisioners automate post-deployment tasks and help bridge the gap between infrastructure provisioning and application deployment.
