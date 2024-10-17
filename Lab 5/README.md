# Creating NAT Gateways in AWS

## Overview

This lab guides you through the process of creating a NAT Gateway in AWS. You will set up a VPC, create public and private subnets, and configure internet connectivity for instances in both subnets.

## Steps

### 1. Sign into AWS Management Console

### 2. Create a VPC

### 3. Create Public and Private Subnets

- **Public Subnet:**
  - Go to the "Subnets" section.
  - Click "Create subnet," select your VPC, and specify the CIDR block for the public subnet.
  
- **Private Subnet:**
  - Repeat the steps above for the private subnet with a different CIDR block.

### 4. Create an Internet Gateway

- In the VPC dashboard, click on "Internet Gateways."
- Create a new Internet Gateway and attach it to your VPC.

### 5. Create Public Route Table and Configure

- Go to "Route Tables" and create a new route table for the public subnet.
- Edit routes to add a route that Destination : Enter 0.0.0.0/0
- Target : Select Internet Gateway, and once the internet gateways have been created.
- To associate the Public Subnet to the route table, Select PublicRouteTable.
- Click on the Subnet Associations tab.
- Click on Edit subnet associations.
- On the next page, select MyPublicSubnet from the list displayed.
- Click on Save associations.

### 6. Launch an EC2 Instance in Public Subnet

- Navigate to the EC2 dashboard.
- Launch an instance in the public subnet and ensure it has a public IP.

### 7. Launch an EC2 Instance in Private Subnet

- Repeat the process to launch an EC2 instance in the private subnet (without a public IP).

### 8. SSH into Public and Private EC2 Instances and Test Internet Connectivity

- SSH into the public instance using its public IP.
- From the public instance, SSH into the private instance using its private IP.
- Test internet connectivity from both instances (e.g., ping a public IP).

### 9. Create a NAT Gateway

- Go to "NAT Gateways" in the VPC dashboard.
- Create a NAT Gateway in the public subnet and allocate an Elastic IP.

### 10. Update Route Table and Configure NAT Gateway

- Navigate back to your private route table.
- Edit the routes to add a route that directs `0.0.0.0/0` to the NAT Gateway.

### 11. Test Internet Connection from Instance Inside Private Subnet

- SSH into the private instance.
- Test internet connectivity (e.g., using `curl` or `ping`).

## Conclusion

You have successfully created a NAT Gateway in AWS, allowing instances in a private subnet to access the internet.
NAT Gateway allows for high scalability and can handle thousands to tens of thousands of concurrent connections per second. It is designed to handle significant traffic loads and provides automatic scaling based on the demand. 
This means that as your network traffic increases, AWS automatically scales up the NAT Gateway capacity to accommodate the higher workload. This scalability feature ensures that your instances in the private subnet can maintain reliable and efficient internet connectivity, 
even during periods of high demand or traffic spikes.

