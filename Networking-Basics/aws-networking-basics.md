# AWS Cloud Infrastructure Project

This project provides a practical introduction to building and managing AWS cloud infrastructure using Terraform, an Infrastructure as Code (IaC) tool. By the end of this project, you will have a solid understanding of various AWS components and how to automate their deployment using Terraform.

## Table of Contents

1. [Introduction to AWS and Cloud Computing](#introduction-to-aws-and-cloud-computing)
   - [AWS Cloud Overview](#aws-cloud-overview)
2. [Virtual Private Cloud (VPC)](#virtual-private-cloud-vpc)
   - [Understanding VPC](#understanding-vpc)
   - [CIDR Range Explained](#cidr-range-explained)
   - [Creating a VPC in AWS](#creating-a-vpc-in-aws)
3. [Subnets in AWS](#subnets-in-aws)
   - [Understanding Subnets](#understanding-subnets)
   - [Creating Subnets in a VPC](#creating-subnets-in-a-vpc)
4. [EC2 Instances](#ec2-instances)
   - [Understanding EC2 Instances](#understanding-ec2-instances)
   - [Launching EC2 Instances](#launching-ec2-instances)
5. [Internet Gateways](#internet-gateways)
   - [Understanding Internet Gateways](#understanding-internet-gateways)
   - [Attaching an Internet Gateway to a VPC](#attaching-an-internet-gateway-to-a-vpc)
6. [Route Tables](#route-tables)
   - [Understanding Route Tables](#understanding-route-tables)
   - [Configuring Route Tables](#configuring-route-tables)
7. [NAT Gateways](#nat-gateways)
   - [Understanding NAT Gateways](#understanding-nat-gateways)
   - [Creating a NAT Gateway](#creating-a-nat-gateway)

---

## Introduction to AWS and Cloud Computing

### AWS Cloud Overview

Amazon Web Services (AWS) is a comprehensive and widely adopted cloud platform that offers over 200 fully featured services from data centers globally. AWS provides various infrastructure services such as computing power, storage options, and networking capabilities, making it easier to build and scale applications. By leveraging AWS, businesses can access a broad range of tools and resources to optimize their operations, enhance security, and innovate rapidly.

![AWS Cloud Diagram](https://example.com/aws-cloud-diagram.png)

## Virtual Private Cloud (VPC)

### Understanding VPC

A Virtual Private Cloud (VPC) is a virtual network dedicated to your AWS account. It enables you to launch AWS resources in a logically isolated virtual network that you define. Think of a VPC as your private data center in the cloud, providing you with complete control over your networking environment, including selection of IP address range, creation of subnets, and configuration of route tables and network gateways.

![VPC Diagram](https://example.com/vpc-diagram.png)

### CIDR Range Explained

CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing Internet Protocol packets. In a VPC, you specify a CIDR block that determines the range of IP addresses available in your VPC. The CIDR block is crucial for defining the network's size and structure. Proper planning of the CIDR block helps avoid IP address conflicts and ensures efficient IP address management.

### Creating a VPC in AWS

To create a VPC in AWS:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "Create VPC."
3. Specify the required details such as Name, CIDR Block, and tenancy.
4. Click "Create" to provision your VPC.

Creating a VPC is the foundational step in setting up your AWS infrastructure. This VPC will house all subsequent resources you deploy, providing a secure and scalable environment for your applications.

## Subnets in AWS

### Understanding Subnets

Subnets are segments of a VPC's IP address range where you can place groups of isolated resources. By dividing your VPC into subnets, you can create public-facing and private resources, enhancing security and organization. Public subnets are typically used for resources that need direct access to the internet, while private subnets are used for internal resources that should not be directly accessible from the internet.

![Subnet Diagram](https://example.com/subnet-diagram.png)

### Creating Subnets in a VPC

To create a subnet:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "Subnets" and then "Create Subnet."
3. Choose the VPC, specify the subnet’s name, and define the CIDR block.
4. Click "Create" to provision your subnet.

Creating subnets allows you to logically partition your VPC and manage resources more efficiently. For instance, you can deploy web servers in public subnets and databases in private subnets.

## EC2 Instances

### Understanding EC2 Instances

Amazon EC2 (Elastic Compute Cloud) provides resizable compute capacity in the cloud. It allows you to launch virtual servers, called instances, to run applications and services. EC2 instances are fundamental to any AWS infrastructure as they provide the necessary compute power for your applications. With a variety of instance types, you can choose the right mix of CPU, memory, storage, and networking capacity to suit your workload.

![EC2 Instance](https://example.com/ec2-instance.png)

### Launching EC2 Instances

To launch an EC2 instance:

1. Go to the EC2 Dashboard in the AWS Management Console.
2. Click "Launch Instance."
3. Choose an Amazon Machine Image (AMI) and instance type.
4. Configure instance details, including network and security settings.
5. Click "Launch" to start your EC2 instance.

Launching EC2 instances is a critical step as these instances will host your applications and services. By properly configuring instance details, you ensure that your applications run efficiently and securely.

## Internet Gateways

### Understanding Internet Gateways

An Internet Gateway (IGW) is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet. The IGW is essential for any VPC that needs to access the internet, whether for outgoing or incoming traffic. It provides a target in your VPC route tables for internet-routable traffic and performs network address translation (NAT) for instances with public IP addresses.

![Internet Gateway](https://example.com/internet-gateway.png)

### Attaching an Internet Gateway to a VPC

To attach an Internet Gateway:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "Internet Gateways" and then "Create Internet Gateway."
3. Specify the name and click "Create."
4. Attach the Internet Gateway to your VPC.

Attaching an Internet Gateway is necessary to enable internet connectivity for resources in your VPC. This setup allows your EC2 instances in public subnets to communicate with the internet.

## Route Tables

### Understanding Route Tables

A route table contains a set of rules, called routes, that are used to determine where network traffic is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for the subnet. Proper configuration of route tables ensures that traffic is efficiently and securely routed within your VPC and to external networks.

![Route Table](https://example.com/route-table.png)

### Configuring Route Tables

To configure a route table:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "Route Tables" and then "Create Route Table."
3. Choose the VPC and specify the route table name.
4. Add routes to direct traffic as needed.
5. Associate the route table with the appropriate subnets.

Configuring route tables is key to controlling traffic flow and ensuring that your network operates smoothly. For example, you can add routes to direct internet-bound traffic to an Internet Gateway or direct traffic between subnets within your VPC.

## NAT Gateways

### Understanding NAT Gateways

A NAT Gateway allows instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating connections with those instances. This is essential for security and enabling internet access for private instances. By using a NAT Gateway, you can ensure that your instances in private subnets can access necessary updates and resources without exposing them to external threats.

![NAT Gateway](https://example.com/nat-gateway.png)

### Creating a NAT Gateway

To create a NAT Gateway:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "NAT Gateways" and then "Create NAT Gateway."
3. Choose the subnet and specify the Elastic IP allocation.
4. Click "Create NAT Gateway."

Creating a NAT Gateway is crucial for providing secure internet access to instances in private subnets. This setup allows these instances to initiate outbound connections to the internet, while protecting them from inbound connections from the internet.

