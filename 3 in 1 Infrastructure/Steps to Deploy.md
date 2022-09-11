# **Objective** 
**Deploy Web Application on the Amazon EC2 Windows instances with Elastic Load Balancer in front of web application servers & database. Use two Availability Zones for provision of two web application servers in separate private subnets and configure them for high availability.**

*Region: Can Be ANY Region (I Chose North Virginia)*

## Highlevel Overview

This deployment should include VPC with 2 Public & 3 Private subnets (Web server and RDS should be on Private subnet), Internet | NAT Gateway along with 1 CIDR block.

**Services Used:** ELB, EC2, VPC, RDS, AutoScaling, SNS & Route53

### Steps:

1. Create 1 EC2 Instance (Free Tier Windows Server AMI) in public subnet, Install and Configure Internet Information Services (IIS), Install SQL workbench/client & create Launch Configuration. Create AMI and Delete this machine.

2. All Web Server will be provisioned by using AutoScaling Group on Private Subnet with Minimum, Maximum & desired capacity of 2 VMs.

3. Create an Internet facing Elastic load balancer along with ELB Security Group and add both EC2 Instances in the Target Group so that an internet user should be able to open http web server page (Port 80).

4. Create a separate Security Group (SG) for ELB and ASG to allow web traffic from ELB only.

5. Web servers should be accessible via Bastion host only.

6. Create MySQL RDS which should be accessible via web servers using a client. 

7. connect RDS with MYSQL client under Autoscaling VMs

8. You should receive notifications via Email/SMS from AutoScaling Group.

9. Configure Route 53 with Load Balancer Endpoint so that your Website should be accessible via *A desired Domain*

*Note: Steps will 100% seem confusing but take a look at the following diagram for better understanding of the deployment*

[AWS 3in1 Deployment Diagram.pdf](https://github.com/mhmmd-03/AWS-Deployments/files/9543429/AWS.3in1.Final.project.V1.0.pdf)

