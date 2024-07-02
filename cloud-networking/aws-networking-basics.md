# Cloud Networking with AWS

This project explain the foundational concepts and practical steps for establishing cloud networking in AWS. You'll gain insights into CIDR ranges, VPCs, EC2 instances, Internet Gateways, Route Tables, and more.

## Table of Contents

1. [CIDR Range Explained](#cidr-range-explained)
2. [VPC Terminology](#vpc-terminology)
3. [Creating a VPC](#creating-a-vpc)
4. [Launching an EC2 Instance](#launching-an-ec2-instance)
5. [Internet Gateway](#internet-gateway)
6. [Route Table](#route-table)
7. [Connecting to the Internet](#connecting-to-the-internet)
8. [Launching a Private EC2 Instance](#launching-a-private-ec2-instance)
9. [NAT Gateway](#nat-gateway)
10. [Network ACL (NACL)](#network-acl-nacl)

## CIDR Range Explained

CIDR (Classless Inter-Domain Routing) notation efficiently groups IP addresses, similar to how zip codes organize neighborhoods.

### How It Looks

A CIDR address comprises two parts:
1. **Network Address (like a zip code)**: e.g., `192.168.1.0`
2. **Netmask (a slash followed by a number)**: e.g., `/24`

The netmask indicates the size of the address group. A larger number after the slash represents a smaller group.

### Examples

- **`192.168.1.0/24`**:
  - Represents 256 IP addresses
  - Example usage: Home networks
  - Analogous to a small neighborhood

- **`10.0.0.0/8`**:
  - Represents over 16 million IP addresses
  - Example usage: Large enterprise networks
  - Analogous to a large city

- **`2001:db8::/32`**:
  - Represents an IPv6 address group
  - Example usage: Modern, extensive networks
  - Analogous to a futuristic city

CIDR notation is crucial for organizing and managing the vast number of IP addresses on the internet. It simplifies traffic routing and enhances address allocation efficiency.

---

## VPC Terminology

A Virtual Private Cloud (VPC) is a secure and isolated network environment within the AWS cloud, providing your own private segment of AWS infrastructure to launch and manage resources like servers, databases, and load balancers.

![VPC Diagram](path/to/vpc_diagram.png) 

### Key Terms

- **VPC**: A virtual network dedicated to your AWS account.
- **Subnet**: A range of IP addresses in your VPC.
- **Internet Gateway**: A redundant, highly available VPC component allowing communication between instances in your VPC and the internet.
- **Route Table**: A set of rules (routes) that direct network traffic.
- **NACL (Network ACL)**: An optional layer of security for your VPC, acting as a firewall for controlling traffic in and out of subnets.

---

## Explanation of EC2

Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable compute capacity in the cloud, allowing you to run virtual servers, known as instances, on AWS infrastructure.

![EC2 Diagram](path/to/ec2_diagram.png)

### Key Features

- **Virtual Servers**: EC2 instances run applications, host websites, process data, and more.
- **Scalability**: Easily scale up or down based on computing needs.
- **Flexibility**: Choose from various instance types and configurations to match specific requirements.
- **Pay-As-You-Go**: Only pay for the compute power used, making it cost-effective.
- **Global Availability**: Launch instances in multiple regions worldwide for improved performance and redundancy.

In essence, EC2 provides the computing power needed in the cloud without the hassle of managing physical hardware.

---

## Creating a VPC

Creating a VPC is the first step in setting up your AWS network infrastructure. This provides a dedicated, isolated network for your AWS resources.

1. Go to the VPC Dashboard.
2. Click on **Create VPC**.
3. Fill in the details: 
    - **Name tag**: my-vpc
    - **IPv4 CIDR block**: 10.0.0.0/16

By setting the IPv4 CIDR block to `10.0.0.0/16`, you allocate a range of IP addresses for your VPC, allowing for a maximum of 65,536 IP addresses. This is suitable for larger networks that might require extensive IP address allocation.

![Create VPC Screenshot](path/to/create_vpc_screenshot.png)

### Detailed Description

- **Name Tag**: Assigning a name tag helps in easily identifying the VPC within the AWS console.
- **IPv4 CIDR Block**: This block defines the range of IP addresses available within your VPC. Choosing `/16` gives you ample addresses for a sizeable network.

---

## Launching an EC2 Instance

An EC2 instance is essentially a virtual server. Launching one within your VPC enables you to utilize AWS's scalable compute power.

1. Navigate to the EC2 Dashboard.
2. Click on **Launch Instance**.
3. Select an Amazon Machine Image (AMI).
4. Choose an instance type (e.g., t2.micro).
5. Configure instance details: 
    - Select the VPC created earlier.
    - Select a subnet.
6. Add storage and tags.
7. Configure security group settings.
8. Review and launch the instance.

![EC2 Instance Summary Screenshot](path/to/ec2_instance_summary.png)

### Detailed Description

- **AMI Selection**: Amazon Machine Images are pre-configured templates for your instances. Choose one based on your application needs.
- **Instance Type**: Select an instance type that matches your workload. t2.micro is a good starting point for testing and development.
- **Configuration**: Ensure the instance is associated with the VPC and subnet you created.
- **Security Group**: Define firewall rules to control traffic to your instance.

---

## Internet Gateway

An Internet Gateway (IGW) is a virtual component that acts as a bridge between your private network resources and the public internet. It allows your instances in a public subnet to communicate with the internet and vice versa.

![Internet Gateway Screenshot](path/to/internet_gateway.png)

Think of it like a doorman for your cloud network:

- **Incoming**: Lets incoming traffic from the internet reach your public resources.
- **Outgoing**: Allows your resources to send traffic out to the internet.
- **Security**: Does not allow unsolicited inbound traffic, adding a layer of security to your network.

1. Navigate to the VPC Dashboard.
2. Click on **Internet Gateways** in the sidebar.
3. Click on **Create Internet Gateway**.
4. Attach the Internet Gateway to your VPC.

![Create Internet Gateway Screenshot](path/to/create_internet_gateway.png)

### Detailed Description

- **Creation**: The process involves naming the Internet Gateway and linking it to your VPC.
- **Functionality**: It enables instances in public subnets to communicate with the internet while maintaining a secure boundary for the VPC.

---

## Route Table

Route Tables contain a set of rules (routes) that determine where network traffic from your VPC is directed.

1. Navigate to the Route Tables section in the VPC Dashboard.
2. Click on **Create Route Table**.
3. Associate the Route Table with your VPC.
4. Add routes to direct traffic to the Internet Gateway.

![Route Table Screenshot](path/to/route_table.png)

### Detailed Description

- **Routes**: Routes define the paths that traffic will follow. Adding a route to the IGW ensures internet traffic is correctly routed.
- **Association**: Link the Route Table with your subnets to apply the routing rules.

---

## Connecting to the Internet

To connect your instances to the internet, you need to update the route tables associated with your VPC.

1. Go to the **Route Tables** section.
2. Select the Route Table associated with your subnet.
3. Click on **Routes** -> **Edit Routes**.
4. Add a route with:
    - **Destination**: 0.0.0.0/0
    - **Target**: Your Internet Gateway

![Connecting to the Internet Screenshot](path/to/edit_routes.png)

### Detailed Description

- **Route Addition**: The route `0.0.0.0/0` directs all traffic to the IGW, allowing outbound internet access.
- **Verification**: Ensure that the route is correctly configured to avoid connectivity issues.

---

## NAT Gateway

A NAT Gateway (Network Address Translation Gateway) enables instances in a private subnet to connect to the internet or other AWS services while preventing the internet from initiating connections with those instances.

1. Navigate to the VPC Dashboard.
2. Click on **NAT Gateways**.
3. Create a NAT Gateway and associate it with a public subnet.

![NAT Gateway Screenshot](path/to/nat_gateway.png)

### Detailed Description

- **Creation**: Assign the NAT Gateway to a public subnet and an Elastic IP address.
- **Functionality**: It allows instances in private subnets to access external resources without exposing them to inbound internet traffic.

---

## Network ACL (NACL)

A Network ACL (NACL) is an optional layer of security for your VPC that acts as a stateless firewall, controlling inbound and outbound traffic at the subnet level. NACLs are typically used to provide an additional layer of security to your VPC, though they are often left unchanged once initially configured.

### Detailed Description

- **Inbound and Outbound Rules**: Define rules for both incoming and outgoing traffic.
- **Stateless

 Nature**: Unlike security groups, NACLs do not maintain session state, meaning rules must be defined for both directions.

