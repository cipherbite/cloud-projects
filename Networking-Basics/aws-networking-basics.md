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
4. [EC2 Instances](#ec2-instances)
   - [Understanding EC2 Instances](#understanding-ec2-instances)
5. [Internet Gateways](#internet-gateways)
   - [Understanding Internet Gateways](#understanding-internet-gateways)
6. [Route Tables](#route-tables)
   - [Understanding Route Tables](#understanding-route-tables)
7. [Launching EC2 Instances](#launching-ec2-instances)
8. [NAT Gateways](#nat-gateways)
   - [Understanding NAT Gateways](#understanding-nat-gateways)

---

## Introduction to AWS and Cloud Computing

### AWS Cloud Overview

Amazon Web Services (AWS) is a comprehensive and widely adopted cloud platform that offers over 200 fully featured services from data centers globally. AWS provides a variety of infrastructure services such as computing power, storage options, and networking capabilities, making it easier to build and scale applications.

![AWS Cloud Diagram](https://example.com/aws-cloud-diagram.png)

## Virtual Private Cloud (VPC)

### Understanding VPC

A Virtual Private Cloud (VPC) is a virtual network dedicated to your AWS account. It enables you to launch AWS resources in a logically isolated virtual network that you define. VPCs are akin to having a private network in the cloud, providing secure and robust networking options.

![VPC Diagram](https://example.com/vpc-diagram.png)

### CIDR Range Explained

CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing Internet Protocol packets. In a VPC, you specify a CIDR block that determines the range of IP addresses available in your VPC.

### Creating a VPC in AWS

To create a VPC in AWS:

1. Go to the VPC Dashboard in the AWS Management Console.
2. Click on "Create VPC."
3. Specify the required details such as Name, CIDR Block, and tenancy.
4. Click "Create" to provision your VPC.

## Subnets in AWS

### Understanding Subnets

Subnets are segments of a VPC's IP address range where you can place groups of isolated resources. Subnets allow you to partition your VPC into smaller networks and enhance security and organization.

![Subnet Diagram](https://example.com/subnet-diagram.png)

## EC2 Instances

### Understanding EC2 Instances

Amazon EC2 (Elastic Compute Cloud) provides resizable compute capacity in the cloud. It allows you to launch virtual servers, called instances, to run applications and services.

![EC2 Instance](https://example.com/ec2-instance.png)

## Internet Gateways

### Understanding Internet Gateways

An Internet Gateway (IGW) is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet.

![Internet Gateway](https://example.com/internet-gateway.png)

## Route Tables

### Understanding Route Tables

A route table contains a set of rules, called routes, that are used to determine where network traffic is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for the subnet.

![Route Table](https://example.com/route-table.png)

## Launching EC2 Instances

To launch an EC2 instance:

1. Go to the EC2 Dashboard in the AWS Management Console.
2. Click "Launch Instance."
3. Choose an Amazon Machine Image (AMI) and instance type.
4. Configure instance details, including network and security settings.
5. Click "Launch" to start your EC2 instance.

## NAT Gateways

### Understanding NAT Gateways

A NAT Gateway allows instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating connections with those instances. This is essential for security and enabling internet access for private instances.

![NAT Gateway](https://example.com/nat-gateway.png)

---
