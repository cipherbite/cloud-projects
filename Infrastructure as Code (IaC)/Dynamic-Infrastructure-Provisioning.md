# Terraforming AWS: A Hands-On Project


This project provides a practical introduction to Infrastructure as Code (IaC) using Terraform. It guides you through setting up basic AWS resources, giving you a solid foundation for building more complex cloud infrastructures.

## Table of Contents
- [Why Infrastructure as Code (IaC)?](#why-infrastructure-as-code-iac)
- [Benefits of Terraform](#benefits-of-terraform)
- [Project Overview](#project-overview)
- [Setting Up Your Environment](#setting-up-your-environment)
- [Terraform Configuration](#terraform-configuration)
    - [`main.tf`](#maintf)
    - [`variables.tf`](#variablestf)
    - [`terraform.tfvars`](#terraformtfvars)
    - [`output.tf`](#outputtf)
- [Applying and Managing Changes](#applying-and-managing-changes)
- [Destroying Infrastructure](#destroying-infrastructure)
- [Conclusion](#conclusion)

## Why Infrastructure as Code (IaC)?

IaC allows you to define and manage infrastructure using code. Key benefits include:

- **Consistency:** Ensure repeatable, reliable deployments.
- **Version Control:** Track changes, collaborate, and roll back if needed.
- **Efficiency:** Automate infrastructure management, reducing manual errors and saving time.

## Benefits of Terraform

Terraform, a leading IaC tool, offers these advantages:

- **Declarative Language:** Describe the desired state of your infrastructure clearly and concisely.
- **State Management:** Track resource changes and maintain accurate infrastructure status.
- **Multi-Cloud Support:** Provision resources across multiple cloud providers.
- **Open Source:** Benefit from a vast community and extensive documentation.

## Project Overview

This project creates the following AWS resources:

- **Virtual Private Cloud (VPC)**
- **Subnet**
- **Internet Gateway (IGW)**
- **Route Table**
- **EC2 Instance**

![Diagram of AWS resources Placeholder](#)

## Setting Up Your Environment

1. **Install Terraform:** Follow the official [installation guide](https://learn.hashicorp.com/tutorials/terraform/install-cli).
2. **Configure AWS Credentials:** Use the `aws configure` command to set up your AWS access key ID and secret access key.

![Screenshot of AWS configuration Placeholder](#)

## Terraform Configuration

### `main.tf`

The core configuration file defining resources and their relationships.

```hcl
provider "aws" {
  region = var.aws_region
}

resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type
}
```

![Screenshot of main.tf Placeholder](#)

#### Explanation

- **Provider Block**: Configures the AWS provider with the specified region.
- **Resource Block**: Defines an EC2 instance with specified AMI and instance type.

### `variables.tf`

Declares variables for customizable aspects of your infrastructure.

```hcl
variable "aws_region" {
  description = "The AWS region to deploy resources"
  type        = string
  default     = "us-west-2"
}

variable "ami_id" {
  description = "The AMI ID for the EC2 instance"
  type        = string
}

variable "instance_type" {
  description = "The instance type for the EC2 instance"
  type        = string
  default     = "t2.micro"
}
```

![Screenshot of variables.tf Placeholder](#)

#### Explanation

- **Variable Definitions**: Variables allow you to reuse and customize your Terraform configuration.
- **Example Variables**: Define AWS region, AMI ID, and instance type.

### `terraform.tfvars`

Stores variable values. For sensitive information, use environment variables or a secret management tool.

```hcl
aws_region    = "us-west-2"
ami_id        = "ami-0c55b159cbfafe1f0"
instance_type = "t2.micro"
```

![Screenshot of terraform.tfvars Placeholder](#)

#### Explanation

- **Purpose**: Provides default values for variables, simplifying the configuration process.
- **Example**: Sets default values for AWS region, EC2 AMI, and instance type.

### `output.tf`

Defines values to display after Terraform creates resources.

```hcl
output "instance_id" {
  value = aws_instance.example.id
}

output "instance_public_ip" {
  value = aws_instance.example.public_ip
}
```

![Screenshot of output.tf Placeholder](#)

#### Explanation

- **Outputs**: Provide information about the resources created, such as the EC2 instance ID and public IP address.

## Applying and Managing Changes

1. **Initialize:**
   ```bash
   terraform init
   ```
2. **Apply:**
   ```bash
   terraform apply
   ```

## Destroying Infrastructure

To clean up and destroy the infrastructure you created, run:

```bash
terraform destroy
```

![Terraform Destroy Screenshot Placeholder](#)

This command will remove all resources defined in your configuration.

## Conclusion

This project demonstrates the basics of using Terraform for Infrastructure as Code, showcasing the creation of a VPC, Subnet, Internet Gateway, and an EC2 instance in AWS. Terraform's declarative configuration and automation capabilities simplify the process of managing and provisioning cloud infrastructure.

---

This revised file incorporates detailed explanations and placeholder images to enhance understanding and maintain a professional yet accessible format.
