# Lab 3 Implementing AWS WAF with ALB to block SQL Injection, Geo Location and Query string Attacks

## Overview
This lab demonstrates how to implement AWS WAF (Web Application Firewall) with an Application Load Balancer (ALB) to enhance the security of web applications by blocking SQL injection attempts, geo-location restrictions, and unwanted query strings.

## Steps

### 1. Sign in to AWS Management Console

### 2. Launch First EC2 Instance
- Navigate to the **EC2** dashboard.
- Click on **Launch Instance**.
- Choose an Amazon Machine Image (AMI), select an instance type, and configure settings.
- Ensure to assign a security group that allows HTTP (port 80) access.

### 3. Launch Second EC2 Instance
- Repeat the previous step to launch a second EC2 instance, which will also serve as a target for the Load Balancer.

### 4. Create a Target Group
- In the EC2 dashboard, navigate to **Target Groups**.
- Click on **Create target group**.
- Choose **Instances** as the target type.
- Add the two EC2 instances launched previously and configure health checks.

### 5. Create an Application Load Balancer
- Navigate to the **Load Balancers** section in the EC2 dashboard.
- Click on **Create Load Balancer** and select **Application Load Balancer**.
- Configure the following:
  - **Name**: MyAppLoadBalancer
  - **Scheme**: Internet-facing
  - **Listeners**: Add HTTP (port 80).
  - **Availability Zones**: Select the appropriate zones.
  - **Target Group**: Associate with the target group created earlier.

### 6. Test Load Balancer DNS
- Once the Load Balancer is active, copy its DNS name.
- Open a web browser and access the Load Balancer's DNS to ensure it routes traffic to the EC2 instances correctly.

### 7. Create AWS WAF Web ACL
- Navigate to the **WAF & Shield** service.
- Click on **Web ACLs** and then **Create Web ACL**.
- Add rules to:
  - **Block SQL Injection**:
    - Use the SQL Injection Match Condition.
  - **Block Requests from Specific Geo Locations**:
    - Specify countries or regions to block.
  - **Block Requests Based on Query Strings**:
    - Create conditions to match specific query strings you want to block.

### 8. Associate the Web ACL with the Load Balancer
- In the Web ACL settings, choose to associate it with your Application Load Balancer.

### 9. Test Load Balancer DNS Again
- After associating the Web ACL, repeat the test from Step 6 to ensure that the Load Balancer is still functioning correctly.
- Access the Load Balancer's DNS in a web browser and confirm it is routing traffic as expected, while the WAF rules are in effect.

