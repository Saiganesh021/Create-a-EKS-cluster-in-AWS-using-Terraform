# Create an EKS Cluster in AWS Using Terraform

This repository demonstrates how to **provision an Amazon EKS (Elastic Kubernetes Service) cluster using Terraform** following Infrastructure as Code (IaC) best practices. The setup includes VPC networking, EKS control plane, and managed worker node groups.
##  Overview

* **Terraform** is used to provision AWS infrastructure
* **Amazon EKS** provides a managed Kubernetes control plane
* **Managed Node Groups** run container workloads
* **AWS VPC** is created for secure networking

This project is suitable for **learning, assignments, interviews, and real-world DevOps practice**.

---
##  Architecture

`
![Uploading image.png…]()
<img width="491" height="410" alt="image" src="https://github.com/user-attachments/assets/909d5e6f-e75d-4d2c-b545-585ad870a0e3" />

##  Prerequisites

Before you begin, ensure you have the following:
* AWS Account
* AWS CLI configured (`aws configure`)
* Terraform (>= 1.3)
* kubectl
* IAM user with EKS, EC2, VPC permissions

Verify installations:

aws --version
terraform --version
kubectl version --client
## Repository Structure

<img width="491" height="410" alt="image" src="https://github.com/user-attachments/assets/2e02346b-28e1-43c5-bfb7-b000bf6ab749" />

##  Configure Terraform

### 1. Provider Configuration

Ensure AWS provider is defined:

provider "aws" {
  region = var.aws_region
}

### 2. Variables

Update `terraform.tfvars`:

```hcl
aws_region = "us-east-1"
cluster_name = "my-eks-cluster"
node_instance_type = "t3.medium"
desired_capacity = 2
```

---

##  Create the EKS Cluster

### 1. Initialize Terraform


terraform init
```

### 2. Validate Configuration


terraform validate
```

### 3. Plan Infrastructure


terraform plan
```

### 4. Apply Configuration

terraform apply
```

Type `yes` when prompted.

---

##  Configure kubectl Access

After cluster creation, update kubeconfig:


aws eks update-kubeconfig \
  --region us-east-1 \
  --name my-eks-cluster
```

Verify cluster access:


kubectl get nodes
```

---

##  Verify EKS Resources


kubectl get pods -A
kubectl get svc
```

---

##  Destroy Infrastructure

To delete all AWS resources created by Terraform:


terraform destroy
```

 **Warning:** This will permanently delete the EKS cluster and related AWS resources.

---

##  Key Features

* Fully automated EKS provisioning
* Reusable Terraform modules
* Secure VPC networking
* Scalable managed node groups
* Production-ready baseline

---

## References

* [https://docs.aws.amazon.com/eks/](https://docs.aws.amazon.com/eks/)
* [https://developer.hashicorp.com/terraform](https://developer.hashicorp.com/terraform)
* [https://registry.terraform.io/providers/hashicorp/aws](https://registry.terraform.io/providers/hashicorp/aws)

---
## Author

Maintained by **Saiganesh Paluri**
⭐ If this repository helps you, consider giving it a star!
