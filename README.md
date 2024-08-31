# Three-Tier Architecture Deployment with Terraform
##Overview

This repository contains Terraform configurations for deploying a three-tier architecture on Amazon Web Services (AWS). The architecture consists of:

Web Tier: Hosted in public subnets, including a Bastion Host for secure SSH access and a NAT Gateway for internet access.
Application Tier: Located in private subnets, with an internet-facing Elastic Load Balancer (ELB) and an Auto Scaling Group (ASG) for both frontend and backend applications.
Database Tier: Also in private subnets, hosting a MySQL database with an AWS RDS instance.
The architecture ensures scalability, security, and high availability by segregating different application layers and enabling seamless communication between them.


##Architecture Components
Amazon Virtual Private Cloud (VPC)
Elastic Load Balancer (ELB)
Auto Scaling Group (ASG)
Amazon RDS (Relational Database Service)


##Web Tier
-Bastion Host: Provides a secure access point for SSH.
-NAT Gateway: Enables internet access for instances in private subnets while protecting their IP addresses.


##Application Tier
-Internet-Facing Load Balancer: Distributes incoming internet traffic to the ASG in private subnets.
-ASG: Manages the scaling of frontend and backend applications.

##Scripts:
-Frontend: Installs Apache web server.
-Backend: Installs Node.js.
-Database Tier
-Private Subnets: Host a MySQL database accessed via Node.js.

##Deployment Guide
##-Prerequisites
-AWS Account: Ensure you have valid AWS credentials (Access Key ID and Secret Access Key).
-Terraform: Install Terraform from official website.
-Basic AWS Knowledge: Familiarity with EC2, VPC, ELB, ASG, and RDS.
-Terraform Basics: Understanding of Terraform configuration files (.tf).



##Steps to Deploy
###Clone the Repository


git clone https://github.com/MShalbi/3tier.git
cd your-repo-directory


###Configure AWS Credentials

aws configure
Enter your Access Key ID and Secret Access Key.
Optionally, set the default region.


Configure S3 Bucket for State File Storage

##Create an S3 bucket in the AWS Management Console to store the Terraform state file.
-Update Terraform Variables
-Edit terraform.tfvars in your project directory.
-Set the values for dbuser, dbpassword, and db_name.

##Initialize Terraform
terraform fmt
terraform init

##Review and Validate
terraform plan

##Deploy the Infrastructure
terraform apply

Confirm the deployment by typing yes when prompted.
Access the Application
Use the DNS name of the ELB (provided in Terraform output) to access your application in a web browser.
##Destroy the Infrastructure (Optional)
terraform destroy
##Confirm the destruction by typing yes.
##Verify Infrastructure

Check the AWS console for VPC, subnets, internet gateway, route tables, EC2 instances, load balancers, and RDS database.
Verify the load balancer endpoint displays the Apache web server message, and that the frontend autoscaling group IP address updates upon refresh.


##Conclusion
You have successfully deployed a scalable and highly available three-tier architecture on AWS using Terraform. For production environments, adhere to AWS best practices and security guidelines.
