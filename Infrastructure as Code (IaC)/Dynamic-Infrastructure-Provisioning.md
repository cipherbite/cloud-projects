# Project: Infrastructure with Terraform

This project demonstrates the use of Terraform for Infrastructure as Code (IaC). We cover Terraform's installation, configuration, and application to create a simple AWS infrastructure, including a VPC, Subnet, Internet Gateway, and an EC2 instance.

## Table of Contents
- [What is Infrastructure as Code (IaC)?](#what-is-infrastructure-as-code-iac)
- [Benefits of Terraform](#benefits-of-terraform)
- [Installing Terraform](#installing-terraform)
- [Connecting to AWS with Terraform](#connecting-to-aws-with-terraform)
- [Terraform Project Structure](#terraform-project-structure)
  - [`main.tf`](#maintf)
  - [`variables.tf`](#variablestf)
  - [`terraform.tfvars`](#terraformtfvars)
  - [`output.tf`](#outputtf)
- [Steps to Apply Terraform Configuration](#steps-to-apply-terraform-configuration)
- [Destroying Infrastructure](#destroying-infrastructure)
- [Conclusion](#conclusion)

## What is Infrastructure as Code (IaC)?

Infrastructure as Code (IaC) is the practice of managing and provisioning computing infrastructure through machine-readable configuration files rather than physical hardware configuration or interactive configuration tools. IaC enables version control, automation, and the ability to replicate environments easily.

## Benefits of Terraform

Terraform is an open-source IaC tool that allows you to define and provision infrastructure using a high-level configuration language. Its benefits include:

- **Declarative Configuration**: Define infrastructure in a straightforward and readable manner.
- **Execution Plans**: Preview changes before applying them.
- **Resource Graph**: Understand dependencies and manage complex configurations.
- **Change Automation**: Apply and update infrastructure efficiently and consistently.

## Installing Terraform

To install Terraform, follow the [official installation guide](https://learn.hashicorp.com/tutorials/terraform/install-cli).

## Connecting to AWS with Terraform

To begin using Terraform with AWS, configure your AWS credentials:

```bash
aws configure
```

Then, initialize Terraform:

```bash
terraform init
```

## Terraform Project Structure

### `main.tf`

The `main.tf` file contains the primary configuration for your infrastructure, including provider configuration and resource definitions. 

#### Example Configuration

```hcl
provider "aws" {
  region = var.aws_region
}

resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type
}
```

#### Explanation

- **Provider Block**: Configures the AWS provider with the specified region.
- **Resource Block**: Defines an EC2 instance with specified AMI and instance type.

To apply these changes, run:

```bash
terraform apply
```

### `variables.tf`

The `variables.tf` file defines input variables for your Terraform configuration. 

#### Example Configuration

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

#### Explanation

- **Variable Definitions**: Variables allow you to reuse and customize your Terraform configuration.
- **Example Variables**: Define AWS region, AMI ID, and instance type.

You can override variables when applying the configuration:

```bash
terraform apply -var "instance_name=MyNewEC2Instance"
```

### `terraform.tfvars`

The `terraform.tfvars` file provides default values for the variables defined in `variables.tf`.

#### Example Configuration

```hcl
aws_region    = "us-west-2"
ami_id        = "ami-0c55b159cbfafe1f0"
instance_type = "t2.micro"
```

#### Explanation

- **Purpose**: Provides default values for variables, simplifying the configuration process.
- **Example**: Sets default values for AWS region, EC2 AMI, and instance type.

### `output.tf`

The `output.tf` file defines outputs for your Terraform configuration, allowing you to extract information about your resources after they are created.

#### Example Configuration

```hcl
output "instance_id" {
  value = aws_instance.example.id
}

output "instance_public_ip" {
  value = aws_instance.example.public_ip
}
```

#### Explanation

- **Outputs**: Provide information about the resources created, such as the EC2 instance ID and public IP address.

You can view the outputs by running:

```bash
terraform output
```

## Steps to Apply Terraform Configuration

1. **Configure AWS Credentials**: Use `aws configure` to set up your AWS credentials.
2. **Initialize Terraform**: Run `terraform init` to initialize the configuration.
3. **Apply the Configuration**: Use `terraform apply` to create the infrastructure.

## Destroying Infrastructure

To clean up and destroy the infrastructure you created, run:

```bash
terraform destroy
```

This command will remove all resources defined in your configuration.

## Conclusion

This project demonstrates the basics of using Terraform for Infrastructure as Code, showcasing the creation of a VPC, Subnet, Internet Gateway, and an EC2 instance in AWS. Terraform's declarative configuration and automation capabilities simplify the process of managing and provisioning cloud infrastructure.
