# Understanding and Configuring Layered Security in an AWS VPC

## Overview

This guide outlines the steps to create a secure AWS VPC environment with layered security using VPC features such as Security Groups and Network ACLs.

## Steps

### 1. Sign in to AWS Management Console

### 2. Create a New VPC

- Navigate to the VPC dashboard.
- Click on "Create VPC" and specify the necessary details (e.g., CIDR block).

### 3. Create and Attach an Internet Gateway

- In the VPC dashboard, click on "Internet Gateways."
- Create a new Internet Gateway.
- Attach the Internet Gateway to your VPC.

### 4. Create Two Subnets

- Go to the "Subnets" section.
- Click "Create subnet" and specify the following:
  - **Subnet 1:** Choose your VPC and define a CIDR block (e.g., for public access).
  - **Subnet 2:** Choose your VPC and define a different CIDR block (e.g., for private access).

### 5. Create Route Tables, Configure Routes, and Associate Them with Subnets

- Navigate to "Route Tables."
- Create a new route table for the public subnet:
  - add routes to the Route Tables.
  - Select public_route.
  - Go to the Routes tab. Click on Edit routes. On the next page, click on Add route.
  - Specify the following values:
  - Destination: Enter 0.0.0.0/0
  - Target: Select Internet Gateway from the dropdown menu to select Created Internet Gateway.
  - Click on Save changes button.
- Associate this route table with the public subnet.
- (Optionally) Create a separate route table for the private subnet with no public routes.

### 6. Create a Security Group

- In the EC2 dashboard, navigate to "Security Groups."
- Create a new security group and define inbound and outbound rules based on your security requirements (e.g., allowing SSH and All ICMP - IPv4).

### 7. Create and Configure Network ACL

- Go to "Network ACLs" in the VPC dashboard.
- Create a new Network ACL and specify rules for inbound and outbound traffic. Ensure the rules align with your security needs (e.g., allow certain IP ranges).
  - Go to Inbound rules tab. Click on Edit inbound rules and then click on the Add new rule. 
  -  Add the following rules:
  - For SSH, click on Add new rule,
    * Rule number : Enter 100
    * Type: Choose SSH (22) 
    * Source: Enter 0.0.0.0/0
    * Allow / Deny: Select Allow
  - For ALL ICMP- IPv4, click on Add new rule,
    * Rule number : Enter 200
    * Type: Choose ALL ICMP - IPv4
    * Source: Enter 0.0.0.0/0
    * Allow / Deny: Select Allow
- Click on Save changes button.
- NACLs are stateless. You need to add the rules in __Outbound rules__ too. 
- Select whizlabs_NACL and go to Onbound rules tab. Click on Edit onbound rules and then click on the Add Rule button.
- For ALL ICMP- IPv4, click on Add new rule,
  - Rule# : Enter 100
  - Type: Choose ALL ICMP - IPv4
  - Destination: Enter 0.0.0.0/0
  - Allow / Deny: Select Allow
- For Custom TCP Rule, click on Add new rule,
  - Rule# : Enter 200
  - Type: Choose Custom TCP Rule
  - Port Range: Enter 1024 - 65535
  - Destination: Enter 0.0.0.0/0
  - Allow / Deny: Select Allow
Click on Save changes button.

### 8. Launch 2 EC2 Instances

- Navigate to the EC2 dashboard.
- Launch one instance in the public subnet and another in the private subnet.
- Ensure they are associated with the appropriate security groups.

### 9. Test the EC2 Instances

- SSH into the public instance using its public IP.
- From the public instance, try to connect to the private instance using its private IP.
- Verify that security group and NACL rules are correctly implemented by testing connectivity (ping <your Private EC2 IPv4 address>).

## Conclusion

You have successfully configured layered security within an AWS VPC, utilizing Security Groups and Network ACLs to manage access and enhance security.
Security groups are applied at the instance level and provide stateful control over traffic, while NACLs are applied at the subnet level and provide stateless control over traffic. 
