# Terraform Project: Infrastructure as Code (IaC)

This repository demonstrates the use of Terraform to provision and manage infrastructure in AWS. We'll cover the basics of IaC, Terraform benefits, installation, and create a simple infrastructure setup.

## What is Infrastructure as Code (IaC)?

Infrastructure as Code is the practice of managing and provisioning infrastructure through code, rather than manual processes. This enables:

* **Version control:** Track changes and revert to previous states.
* **Automation:** Deploy infrastructure consistently and repeatably.
* **Collaboration:** Work effectively on infrastructure projects.

## Benefits of Terraform

Terraform, by HashiCorp, is a leading IaC tool known for:

* **Open Source:** Wide community support and extensive documentation.
* **Declarative Syntax:** Define the desired state, and Terraform figures out how to get there.
* **State Management:** Tracks the actual state of your infrastructure.
* **Multi-Cloud:** Supports a wide range of cloud providers and services.

## Installing Terraform

1. **Download:** Get the appropriate package for your operating system from the official website: [https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)
2. **Install:** Follow the installation instructions for your OS.
3. **Verify:** Run `terraform -v` to check the installed version.

## Project Structure

* `main.tf`: Core Terraform configuration file.
* `variables.tf`: Defines variables for customization.
* `terraform.tfvars`: Stores variable values.
* `output.tf`: Declares values to display after deployment.
* `screenshots/`: Directory for storing screenshots.

## Let's Get Started!

1. Follow the instructions in the configuration files to set up your AWS provider.
2. Explore the Terraform commands like `init`, `apply`, `plan`, and `destroy`.
3. Customize the variables in `terraform.tfvars` to match your environment.
4. Refer to the AWS CLI documentation for interacting with your infrastructure: [https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
5. The Terraform Registry contains detailed documentation for all available resources: [https://registry.terraform.io/providers/hashicorp/aws/latest/docs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
