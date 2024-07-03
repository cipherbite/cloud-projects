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

## Virtual Private Cloud (VPC)

### Understanding VPC

A Virtual Private Cloud (VPC) is a virtual network dedicated to your AWS account. It enables you to launch AWS resources in a logically isolated virtual network that you define. Think of a VPC as your private data center in the cloud, providing you with complete control over your networking environment, including the selection of IP address ranges, creation of subnets, and configuration of route tables and network gateways.

![VPC Diagram](https://example.com/vpc-diagram.png)

### CIDR and VPCs Explained

**IP Addresses:** Think of IP addresses as street addresses for devices on a network.

**CIDR (Classless Inter-Domain Routing):** A method to organize IP addresses using flexible-sized subnets.

**CIDR Block:**
- **IPv4 Example:** `192.168.0.0/24`
- **IPv6 Example:** `2001:db8::/32`
The `/24` and `/32` indicate the number of bits used for the network part of the address.

**Network Size:**
The CIDR block defines the IP address range in your VPC:
- **Smaller prefix (e.g., /16):** Larger network
- **Larger prefix (e.g., /24):** Smaller network

**Subnet Creation:**
Divide the CIDR block into smaller subnets for different purposes:
- **Web Servers:** `192.168.1.0/24`
- **Databases:** `192.168.2.0/24`
- **Internal Use:** `192.168.10.0/24`

### Importance of Planning

- **Avoiding Conflicts:** Proper planning ensures that IP addresses within subnets don't overlap, preventing communication issues.
- **Efficient Allocation:** Sizes subnets appropriately for the number of devices they support, avoiding wasted IP addresses.
- **Scalability:** Good planning leaves room for future growth and expansion of your network.

### Key Points

- **Flexible Network Sizes:** CIDR allows defining flexible network sizes.
- **VPC Structure:** The CIDR block sets the size and structure of your VPC.
- **Subnets:** These are smaller CIDR blocks within the VPC.
- **Planning:** Essential for a well-organized and scalable network.

In summary, CIDR provides efficient and flexible IP address management within VPCs. Careful planning ensures a scalable and conflict-free network.

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

Launching an EC2 (Elastic Compute Cloud) instance is essential for running applications and services on AWS. Here is a detailed guide to help you through the process:

1. **Access the EC2 Dashboard:**
   - Navigate to the AWS Management Console.
   - In the Services menu, select "EC2" to open the EC2 Dashboard.

2. **Initiate the Launch:**
   - Click the "Launch Instance" button on the EC2 Dashboard.

3. **Select an Amazon Machine Image (AMI):**
   - Choose an AMI that best fits your requirements. An AMI is a template that contains the software configuration (OS, application server, and applications).
   - Amazon provides various AMIs, including predefined configurations, the AWS Marketplace, and custom AMIs.

4. **Choose an Instance Type:**
   - Select an instance type based on the necessary compute, memory, storage, and network capacity. Instance types are categorized into families, designed for different use cases.

5. **Configure Instance Details:**
   - Set up network configurations, including the VPC and subnet.
   - Adjust settings for auto-assignment of public IPs, IAM roles, and shutdown behavior.
   - Configure advanced settings such as purchasing options (on-demand or spot instances), user data scripts for initialization, and monitoring.

6. **Add Storage:**
   - Specify the storage volumes for your instance. You can add multiple EBS (Elastic Block Store) volumes and configure their size, type, and IOPS.

7. **Configure Security Group:**
   - Set up security groups to control inbound and outbound traffic to your instance. Security groups act as virtual firewalls.

8. **Review and Launch:**
   - Review your configurations to ensure everything is set correctly.
   - Click "Launch," then select or create a key pair for SSH access to your instance.
   - Confirm the key pair selection and click "Launch Instances."

Launching EC2 instances correctly is crucial as they will host your applications. Proper configuration ensures your applications run efficiently and securely.

## Internet Gateways

### Understanding Internet Gateways

An Internet Gateway (IGW) is a crucial component in your Virtual Private Cloud (VPC) that allows communication between instances in your VPC and the internet. It is horizontally scaled, redundant, and highly available. The IGW facilitates both inbound and outbound internet traffic and performs Network Address Translation (NAT) for instances with public IP addresses.

![Internet Gateway](https://example.com/internet-gateway.png)

### Steps to Attach an Internet Gateway to a VPC

1. **Access the VPC Dashboard:**
   - Open the AWS Management Console.
   - Select "VPC" from the Services menu to go to the VPC Dashboard.

2. **Create an Internet Gateway:**
   - Click on "Internet Gateways" in the VPC Dashboard.
   - Select "Create Internet Gateway" and provide a name for the IGW.
   - Click "Create" to finalize the creation of the IGW.

3. **Attach the Internet Gateway:**
   - Select the newly created IGW.
   - Click on the "Actions" button and choose "Attach to VPC."
   - Select your VPC from the list and click "Attach Internet Gateway."

Attaching an Internet Gateway to your VPC is essential for enabling internet connectivity. This setup is necessary for instances in public subnets to communicate with the internet.

## Route

 Tables

### Understanding Route Tables

A route table in AWS contains rules (routes) that determine the direction of network traffic. Each subnet in your VPC must be associated with a route table, which controls the routing for that subnet. Configuring route tables properly ensures that network traffic is directed efficiently and securely within your VPC and to external networks.

![Route Table](https://example.com/route-table.png)

### Steps to Configure a Route Table

1. **Access the VPC Dashboard:**
   - Go to the AWS Management Console.
   - Select "VPC" from the Services menu to open the VPC Dashboard.

2. **Create a Route Table:**
   - Click on "Route Tables" and then "Create Route Table."
   - Provide a name and select the VPC for the route table.
   - Click "Create" to finalize the creation.

3. **Add Routes:**
   - Select the newly created route table.
   - In the "Routes" tab, click "Edit routes" to add new routes.
   - Specify the destination CIDR block and target (e.g., Internet Gateway, NAT Gateway, VPC peering connection).
   - Click "Save routes" to apply the changes.

4. **Associate Route Table with Subnets:**
   - In the "Subnet Associations" tab, click "Edit subnet associations."
   - Select the subnets you want to associate with this route table.
   - Click "Save associations" to finalize the association.

Properly configuring route tables ensures that traffic is routed correctly within your VPC and to external networks, optimizing both efficiency and security.

## NAT Gateways

### Understanding NAT Gateways

A NAT (Network Address Translation) Gateway is a service in AWS that allows instances within a private subnet to access the internet or other AWS services while preventing the internet from initiating connections with those instances. This setup is vital for maintaining security while enabling internet access for private instances. The NAT Gateway ensures that your instances can obtain updates and necessary resources without being exposed to potential external threats.

#### Key Points:
- **Private Subnet**: A subnet that is not directly accessible from the internet.
- **Outbound Internet Access**: Instances can initiate connections to the internet.
- **Inbound Protection**: Instances are protected from unsolicited inbound connections.

![NAT Gateway](https://example.com/nat-gateway.png)

### Creating a NAT Gateway

To set up a NAT Gateway, follow these steps:

1. **Access the VPC Dashboard:**
   - Log in to the AWS Management Console.
   - Navigate to "VPC" under the Services menu to open the VPC Dashboard.

2. **Create a NAT Gateway:**
   - In the VPC Dashboard, click on "NAT Gateways" from the sidebar.
   - Click the "Create NAT Gateway" button.

3. **Select the Subnet and Allocate Elastic IP:**
   - **Choose Subnet**: Select the subnet in which the NAT Gateway will reside. This subnet should be a public subnet (one that has a route to an Internet Gateway).
   - **Elastic IP Allocation**: Choose or allocate an Elastic IP address. An Elastic IP is a static IPv4 address designed for dynamic cloud computing.

4. **Finalize Creation:**
   - Click the "Create NAT Gateway" button to create your NAT Gateway.

### Importance of a NAT Gateway

Creating a NAT Gateway is crucial for several reasons:

- **Secure Internet Access**: Instances in private subnets can connect to the internet securely, which is essential for downloading updates or connecting to external services without exposing them to the internet.
- **Controlled Network Traffic**: By routing traffic through the NAT Gateway, you can control and monitor outbound traffic from private subnets.
- **Improved Security**: Prevents unsolicited inbound connections, enhancing the overall security of your VPC.

#### Example Scenario:

Imagine you have a web application with a database server and an application server. The database server is in a private subnet to protect it from direct internet access, while the application server is in a public subnet to allow user access. The application server might need to fetch updates or send logs to an external monitoring service. By setting up a NAT Gateway, you can ensure the application server can access the internet securely without exposing the database server.

### Visualizing the Setup

Here’s a simplified diagram to illustrate the setup:

```
|------------|        |-------------------|        |------------|
| Private    |------->|  NAT Gateway      |------->|   Internet |
| Subnet     |        |  (Public Subnet)  |        |            |
|------------|        |-------------------|        |------------|
```

In this diagram, instances in the private subnet can route their traffic through the NAT Gateway located in the public subnet, enabling secure internet access.
