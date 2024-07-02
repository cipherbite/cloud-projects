# Terraforming AWS Infrastructure: A Practical Project

This project showcases the power of Terraform to automate the provisioning of AWS infrastructure. It provides a hands-on example of building a secure, scalable foundation in the cloud using Infrastructure as Code (IaC) principles.

## Table of Contents
- [Why Infrastructure as Code (IaC)?](#why-infrastructure-as-code-iac)
- [The Terraform Advantage](#the-terraform-advantage)
- [Project Overview](#project-overview)
- [Code Structure](#code-structure)
- [How to Use This Project](#how-to-use-this-project)
- [Security Considerations](#security-considerations)

## Why Infrastructure as Code (IaC)?

IaC is a modern approach to managing infrastructure that leverages code to define and provision resources. This offers several benefits:

- **Consistency:** Ensures your infrastructure is built the same way every time.
- **Reproducibility:** Easily replicate environments across different stages (dev, test, prod).
- **Version Control:** Track changes, collaborate, and roll back if necessary.
- **Automation:** Reduce manual errors and speed up deployments.

## The Terraform Advantage

Terraform is a leading IaC tool known for its:

- **Declarative Syntax:** Describe the desired end state, and Terraform determines how to get there.
- **State Management:**  Keeps track of your real-world infrastructure for accurate updates.
- **Multi-Cloud Support:** Works with AWS, Azure, GCP, and many other providers.
- **Open Source & Extensible:**  Large community and wide range of plugins/modules.

## Project Overview

This project builds the following AWS resources:

- **Virtual Private Cloud (VPC):**  An isolated network segment within AWS.
- **Subnet:** A subdivision of the VPC, allowing for logical grouping of resources.
- **Internet Gateway (IGW):** Provides connectivity between the VPC and the internet.
- **Route Table:** Controls how traffic is routed within the VPC.
- **Security Group:** Acts as a virtual firewall, controlling inbound/outbound traffic.
- **EC2 Instance:** A virtual server for running applications or services.

## Code Structure

- `main.tf`: The main configuration file defining resources and their dependencies.
- `variables.tf`: Declares variables for flexible configuration.
- `terraform.tfvars`: Stores variable values (sensitive values should NOT be here).
- `output.tf`: Defines values to display after Terraform creates your infrastructure.

## How to Use This Project

1. **Prerequisites:**
   - Install Terraform: [https://learn.hashicorp.com/tutorials/terraform/install-cli](https://learn.hashicorp.com/tutorials/terraform/install-cli)
   - Configure AWS Credentials: Use `aws configure` to set your AWS Access Key ID and Secret Access Key.
2. **Clone the Repository:**
   ```bash
   git clone <repository-url>
