# Portfolio Lab 1 - VPC Design & Deployment

## Objective

Design and deploy a custom Virtual Private Cloud (VPC) using AWS Management Console to demonstrate fundamental cloud networking skills. This lab simulates the base network layer for SaaS application deployments.

## Architecture Summary

- VPC CIDR: 10.10.0.0/16
- Public Subnet: 10.10.1.0/24
- Private Subnet: 10.10.2.0/24
- Internet Gateway: Attached to VPC
- NAT Gateway: Not configured (free-tier cost optimization)
- Public Route Table: Configured with IGW route
- Private Route Table: Default route only (internal)
- Security Group: SSH and HTTP allowed
- EC2 Instance: Amazon Linux 2023 (t2.micro, free-tier eligible)
- Testing: Verified outbound internet access via curl and ping

## Architecture Diagram

VPC (10.10.0.0/16)
|
|-- Public Subnet (10.10.1.0/24)
|     |-- EC2 Instance (t2.micro)
|
|-- Private Subnet (10.10.2.0/24)

Internet Gateway → attached to VPC → Route Table → Public Subnet → EC2 Instance

## Lab Build Steps

1. Created custom VPC with CIDR block 10.10.0.0/16.
2. Created two subnets:
   - Public Subnet: 10.10.1.0/24
   - Private Subnet: 10.10.2.0/24
3. Created Internet Gateway and attached it to the VPC.
4. Configured Route Tables:
   - Public Route Table with route 0.0.0.0/0 → IGW
   - Private Route Table associated with private subnet.
5. Created Security Group allowing:
   - SSH (port 22) from my IP.
   - HTTP (port 80) from anywhere.
6. Launched EC2 instance inside public subnet using Amazon Linux 2023 AMI.
7. Verified internet access using SSH, curl, and ping commands.

## Testing Output

Successfully connected to EC2 instance via SSH and verified internet access:

- curl google.com
- ping 8.8.8.8

## Key Learnings

- VPC isolation using CIDR blocks.
- Subnetting for public and private workloads.
- Route Table configuration for public access.
- Internet Gateway setup for public subnet routing.
- Secure remote access using key pairs and security groups.
- Internet connectivity testing from EC2 instances.

## Proof of Work

- Screenshots of:
  - VPC creation
  - Subnets
  - Route Tables
  - Internet Gateway
  - EC2 Instance
  - SSH Session with curl and ping output
- Architecture Diagram attached in repository.
- Full lab documentation provided here as README.

## Conclusion

This lab demonstrates building a fully functioning AWS Virtual Private Cloud using manual configuration through AWS Management Console. It forms the base for advanced SaaS multi-tier architectures in future labs.
