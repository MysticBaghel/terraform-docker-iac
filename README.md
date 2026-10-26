# Terraform Docker Infrastructure as Code (IaC)

## Overview

This project demonstrates Infrastructure as Code (IaC) using Terraform to provision and manage a local Docker container running Nginx.

## Objective

- Configure Terraform to work with Docker.
- Provision a Docker image and container using Terraform.
- Inspect infrastructure using Terraform state.
- Understand the infrastructure lifecycle, from planning and deployment to cleanup.

## Tech Stack

- **OS:** Zorin OS
- **IaC:** Terraform
- **Containerization:** Docker
- **Web Server:** Nginx Alpine
- **Version Control:** Git and GitHub

## Project Structure

```text
terraform-docker-iac/
├── main.tf
├── README.md
├── .gitignore
├── terraform.lock.hcl
└── evidence/
    ├── docker-ps.txt
    ├── nginx-response.html
    └── state-list.txt
```

## Infrastructure Details

The Terraform configuration in `main.tf` defines two resources:

1. **Docker image:** Uses `nginx:alpine`.
2. **Docker container:** Creates a container named `terraform-nginx`.

### Port Mapping

| Host port | Container port |
|---|---|
| 8081 | 80 |

The Nginx server can be accessed locally at:

`http://localhost:8081`

Port 8081 is used because port 8080 was already occupied on the host.

## Implementation

### 1. Initialize Terraform

```bash
terraform init
```

Initializes the working directory and installs the required Docker provider.

### 2. Validate the configuration

```bash
terraform validate
```

Checks the Terraform configuration for errors.

### 3. Preview changes

```bash
terraform plan
```

Displays the resources Terraform intends to create or modify before applying changes.

### 4. Provision infrastructure

```bash
terraform apply
```

Creates the configured Docker image and container after confirmation.

### 5. Verify the container

```bash
docker ps
```

Test the Nginx web server:

```bash
curl http://localhost:8081
```

### 6. Inspect Terraform state

List managed resources:

```bash
terraform state list
```

Inspect the container:

```bash
terraform state show docker_container.nginx
```

Terraform state records information about the resources it manages.

### 7. Destroy infrastructure

```bash
terraform destroy
```

Removes the resources managed by this Terraform configuration after confirmation.

## Evidence

The `evidence/` directory contains execution outputs demonstrating container status, the Nginx HTTP response, and Terraform state.

Additional screenshots and logs can be included to document initialization, planning, deployment, and cleanup.

## Key Learnings

- Understanding Infrastructure as Code.
- Using Terraform providers and resources.
- Understanding `terraform plan` versus `terraform apply`.
- Provisioning Docker containers declaratively.
- Inspecting Terraform state.
- Troubleshooting host-port conflicts.
- Managing the infrastructure lifecycle.

## Conclusion

This project demonstrates a basic Infrastructure as Code workflow using Terraform and Docker on Linux, including configuration, planning, provisioning, verification, and resource management.
