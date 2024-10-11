## Lab 2 Blocking web traffic with WAF in AWS

**WAF (web application firewall)**
1) AWS WAF is a web application firewall that helps you protect your web applications against common web exploits that might affect availability and compromise security.

2) AWS WAF gives you control over how traffic reaches your applications by enabling you to create security rules that block common attack patterns like SQL injection and cross-site scripting.

3) It only allows the request to reach the server based on the rules or patterns you define.

4) Users create their own rules and specify the conditions that AWS WAF searches for in incoming web requests.

5) The cost of WAF is only for what you use. 

6) The pricing is based on how many rules you deploy and how many web requests your application receives.

7) For example, you can deploy AWS WAF on Amazon CloudFront with an Application Load Balancer in front of your web servers or servers running on EC2.

## Features of WAF
**Web traffic filtering using custom rules** 
You can create your own rules, depending on your requirements, whether to block or allow incoming and outgoing requests. You can also customize the string that appears in your web request.

**Blocking malicious requests**
You can also configure rules in AWS WAF to identify and block web request threats like SQL injections and cross-site scripting.

**Tune your rules and monitor traffic**                                
AWS WAF also allows us to review our rules and customize them to prevent new attacks from reaching the server.

# Steps:
1) Sign in to the AWS Management Consol.
2) Create a Security Group for the Load Balancer:

  * Navigate to the EC2 dashboard.
  * Under Network & Security, select Security Groups.
  * Click on __Create Security Group and configure:__
      Name: LB-Security-Group
      Description: Security group for Load Balancer
      Inbound rules: Allow HTTP (port 80) and HTTPS (port 443) traffic.
  
   __* Steps to Create the Web Servers:__
  * Launch two EC2 instances that will serve as your web servers.
  * Assign them the previously created Security Group.
  * Install a web server application (e.g., Apache, Nginx) on each instance.

  __* Create a Load Balancer:__
    Name: MyAppLoadBalancer
    Scheme: Internet-facing
    Listeners: Add HTTP and/or HTTPS as needed.
    Target Group: Select the web servers you created.

3) Testing the Load Balancer.
   Once the Load Balancer is set up, __test__ its endpoint by accessing it in a web browser to ensure it is routing traffic to the web servers correctly.
  
4) Create an IP Set:
 * Navigate to the WAF & Shield service in the AWS Management Console.
 * Under IP sets, click on Create IP set.
 * Define an IP set for blocking specific IP addresses (e.g., BlockedIPs).

5) Create a Web ACL:
 * In the AWS WAF dashboard, click on Web ACLs and then Create Web ACL.
 * Set up rules to block traffic from the IP set created earlier.
 * Associate the Web ACL with the Load Balancer.

6) Testing the Working of the WAF:
 * Attempt to access the application from one of the blocked IPs to verify that access is denied.
 * Access the application from an unblocked IP to ensure normal operation.

7) Unblocking the IP:
 * If needed, go back to the IP set and remove the IP address you want to unblock.
 * Update the Web ACL if necessary to reflect these changes.

Results
Successfully implemented AWS WAF to block specific web traffic based on IP addresses.
Verified functionality through testing access from both blocked and unblocked IPs.

__Web Application Firewall (WAF):__ A Web Application Firewall is a security service that sits between a web application and its users, inspecting and filtering incoming web traffic.
In the context of AWS, the AWS WAF service provides this functionality. It helps protect web applications by examining HTTP/HTTPS requests and applying a set of predefined rules or custom rule configurations to block, allow,
or filter traffic based on specified criteria.
