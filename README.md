# Deploy a Static Website on AWS

## Project Overview
This Cloud Project involves hosting a static HTML web app on AWS. The architecture utilizes various AWS services and resources, providing high availability, fault tolerance, and security measures.

## Architecture
The project architecture includes:
- **VPC with Public and Private Subnets in 2 Availability Zones:** Provides network isolation for resources and enhances fault tolerance and high availability.
- **Internet Gateway:** Enables communication between instances in the VPC and the Internet.
- **Security Groups:** Implemented as a firewall to control inbound and outbound traffic.
- **2 Availability Zones:** Used for increased availability and fault tolerance.
- **Resources in Public Subnets:** Nat Gateway, Bastion Host, and Application Load Balancer.
- **EC2 Instance Connect Endpoint:** Used for secure connecting to resources in public and private subnets.
- **Private Subnets for Web and Database Servers:** Enhances security by isolating these servers.
- **Nat Gateway:** Allows instances in private subnets to access the Internet.
- **EC2 Instances for Hosting the Website:** Instances deployed in private subnets for enhanced security.
- **Application Load Balancer (ALB):** Distributes web traffic across an Auto Scaling Group of EC2 instances.
- **Auto Scaling Group:** Ensures high availability, scalability, fault tolerance, and elasticity.
- **Route 53:** Used for domain registration and creating a record set for the website.
- **GitHub:** Webfiles are stored on GitHub for version control and easy deployment.
- **EC2 Instance to Create AMI:** Once the website is installed, the EC2 instance is used to create an Amazon Machine Image (AMI) for future instances.

## Deployment Script
Below is the bash script used to deploy the web app on an EC2 instance:

```bash
#!/bin/bash
sudo su
yum update -y
yum install -y httpd
cd /var/www/html
wget https://github.com/azeezsalu/jupiter/archive/refs/heads/main.zip
unzip main.zip
cp -r jupiter-main/* /var/www/html/
rm -rf jupiter-main main.zip
systemctl enable httpd 
systemctl start httpd
```

## Deployment Steps
1. **VPC Setup**: Configure the VPC with public and private subnets-
2. **Security and Gateway Configuration**: Setup the Internet Gateway and Security Groups-
3. **Launch EC2 Instances**: Deploy EC2 instances within the VPC subnets-
4. **Configure Load Balancer and Auto Scaling**: Setup the Application Load Balancer and Auto Scaling Group.
5. **Domain Setup**: Register and configure the domain name with Route 53.
6. **Deploy Web App**: Use the provided script to install and start the web application on EC2 instances.
7. **AMI Creation**: After successful deployment, create an AMI from the EC2 instance.

## Repository Structure
- `Deployment Script`: Contains the script for setting up the web application on the EC2 instance
- `Architectural Diagram`: Visual representation of the AWS architecture used

## Additional Resources
- AWS Documentation: [EC2 User Guide](https://docs.aws.amazon.com/ec2/index.html)
- GitHub Repository for Webfiles: [leonomar8/static-web-site](https://github.com/leonomar8/Deploy-a-Static-Website-on-AWS)
