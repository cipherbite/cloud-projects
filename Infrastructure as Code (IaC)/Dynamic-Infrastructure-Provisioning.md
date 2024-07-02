# Project: Infrastructure with Terraform

This project demonstrates the use of Terraform for Infrastructure as Code (IaC). We cover Terraform's installation, configuration, and application to create a simple AWS infrastructure, including a VPC, Subnet, Internet Gateway, and an EC2 instance.

## Table of Contents
- [What is Infrastructure as Code (IaC)?](#what-is-infrastructure-as-code-iac)
- [Benefits of Terraform](#benefits-of-terraform)
- [Installing Terraform](#installing-terraform)
- [Terraform Project Structure](#terraform-project-structure)
  - [`main.tf`](#maintf)
  - [`variables.tf`](#variablestf)
  - [`terraform.tfvars`](#terraformtfvars)
  - [`output.tf`](#outputtf)
- [Steps to Apply Terraform Configuration](#steps-to-apply-terraform-configuration)
- [Final Steps](#final-steps)
- [Conclusion](#conclusion)

## What is Infrastructure as Code (IaC)?

Infrastructure as Code (IaC) is the practice of managing and provisioning computing infrastructure through machine-readable configuration files rather than physical hardware configuration or interactive configuration tools. IaC enables version control, automation, and the ability to replicate environments easily.

## Benefits of Terraform

Terraform is an open-source IaC tool that allows you to define and provision infrastructure using a high-level configuration language. Its benefits include:

- **Declarative Configuration**: Define infrastructure in a declarative manner.
- **Execution Plans**: Preview changes before applying them.
- **Resource Graph**: Understand dependencies and manage complex configurations.
- **Change Automation**: Apply and update infrastructure efficiently and consistently.

## Installing Terraform

To install Terraform, follow the [official installation guide](https://learn.hashicorp.com/tutorials/terraform/install-cli).

### Step-by-Step Instructions

1. **Download Terraform** from the official website.
2. **Unzip the package** and move it to a directory included in your system's PATH.
3. **Verify the installation** by running `terraform -v` in your terminal.

## Terraform Project Structure

Create a new directory for your Terraform project and navigate into it.

### `main.tf`

The `main.tf` file contains the primary configuration for your infrastructure. It includes provider configuration and resource definitions.

![main.tf screenshot](link)

#### Explanation

- **Provider Block**: Configures the AWS provider with the specified region.
- **VPC**: Defines a Virtual Private Cloud.
- **Subnet**: Creates a subnet within the VPC.
- **Internet Gateway**: Attaches an Internet Gateway to the VPC.
- **Route Table**: Creates a route to the Internet using the Internet Gateway.
- **Security Group**: Defines a security group to allow HTTP traffic.
- **EC2 Instance**: Launches an EC2 instance within the subnet.

### `variables.tf`

The `variables.tf` file defines input variables for your Terraform configuration. Variables allow you to parameterize your configuration.

![variables.tf screenshot](link)

#### Explanation

- **Variable Definitions**: Variables allow you to reuse and customize your Terraform configuration.
- **Example Variables**:
  - `vpc_cidr`: CIDR block for the VPC.
  - `vpc_name`: Name of the VPC.
  - `subnet_cidr`: CIDR block for the subnet.
  - `subnet_name`: Name of the subnet.
  - `igw_name`: Name of the Internet Gateway.
  - `ec2_ami`: AMI ID for the EC2 instance.
  - `instance_type`: Type of EC2 instance.

### `terraform.tfvars`

The `terraform.tfvars` file provides default values for the variables defined in `variables.tf`. This file is useful for separating variable values from the configuration.

![terraform.tfvars screenshot](link)

#### Explanation

- **Purpose**: Provides default values for variables, simplifying the configuration process.
- **Example**: Sets default values for AWS region, EC2 AMI, instance type, and instance name.

### `output.tf`

The `output.tf` file defines outputs for your Terraform configuration. Outputs allow you to extract information about your resources after they are created.

![output.tf screenshot](link)

#### Explanation

- **Outputs**: Define outputs to extract and display resource information.
- **Example Outputs**: EC2 instance ID and public IP address.

## Steps to Apply Terraform Configuration

1. **Initialize Terraform**: Run `terraform init` to initialize your Terraform configuration.
2. **Validate Configuration**: Run `terraform validate` to check for any syntax errors.
3. **Plan Changes**: Run `terraform plan` to preview the changes Terraform will make.
4. **Apply Configuration**: Run `terraform apply` to create the infrastructure. You can provide variable values using `-var` options or by using a `terraform.tfvars` file.

### Example Command

```sh
terraform apply -var "instance_name=MyNewEC2Instance"
```

![main.tf explanation screenshot](link)

- **Provider Block**: Specifies the provider (AWS) and region.
- **VPC**: Defines a VPC with a specified CIDR block.
- **Subnet**: Creates a subnet within the VPC.
- **Internet Gateway**: Attaches an Internet Gateway to the VPC.
- **Route Table**: Creates a route to the Internet using the Internet Gateway.

![variables.tf explanation screenshot](link)

- **Variable Definitions**:
  - `vpc_cidr`: CIDR block for the VPC.
  - `vpc_name`: Name of the VPC.
  - `subnet_cidr`: CIDR block for the subnet.
  - `subnet_name`: Name of the subnet.
  - `igw_name`: Name of the Internet Gateway.
  - `ec2_ami`: AMI ID for the EC2 instance.
  - `instance_type`: Type of EC2 instance.

![main.tf security group and EC2 instance explanation screenshot](link)

- **Security Group**: Defines a security group to allow HTTP traffic.
- **EC2 Instance**: Launches an EC2 instance within the subnet.

![subnets screenshot](link)
![route tables screenshot](link)
![instance in internet screenshot](link)

## Final Steps

1. **Initialize Terraform**: Run `terraform init` to initialize your configuration.
2. **Apply Configuration**: Run `terraform apply` to create your AWS infrastructure.
3. **Check Outputs**: Run `terraform output` to view the resource IDs and IP addresses.

## Conclusion

This project demonstrates how to use Terraform for Infrastructure as Code, showcasing the creation of a VPC, Subnet, Internet Gateway, and an EC2 instance in AWS. Terraform's declarative configuration and automation capabilities simplify the process of managing and provisioning cloud infrastructure.

## Destroying Infrastructure

To clean up and destroy the infrastructure you created, run `terraform destroy`. This command will remove all resources defined in your configuration.

![terraform destroy screenshot](link)

---

By following this guide, you will gain hands-on experience with Terraform, enhancing your skills and preparing you for a career in cloud infrastructure management. This project is an excellent demonstration of your ability to manage infrastructure as code, a critical skill for cloud professionals.
