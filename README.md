# Cloud Engineer Junior Assessment

## Project Overview

This project demonstrates the deployment of a simple static website on AWS using Infrastructure as Code (Terraform) and an automated CI/CD pipeline using GitHub Actions.

The objective was to provision cloud infrastructure, deploy an application on a virtual machine with public access, configure IAM permissions, and automate deployments through GitHub Actions.

---

## Technologies Used

- AWS EC2 (Amazon Linux 2023)
- AWS IAM
- AWS Security Groups
- Terraform
- GitHub Actions
- Nginx
- Git & GitHub


## Infrastructure Components

### EC2 Instance

- Amazon Linux 2023
- Public IP enabled
- Hosts the website using Nginx

### Security Group

Inbound Rules:

| Port | Protocol | Purpose |

| 22 | TCP | SSH Access 
| 80 | TCP | HTTP Access 

### IAM Role

An IAM role was attached to the EC2 instance to demonstrate secure AWS resource access without using hardcoded credentials.

---

## Terraform Setup

Terraform is used to provision:

- EC2 Instance
- Security Group
- IAM Role
- IAM Instance Profile

### Initialize Terraform


terraform init

Validate Configuration
terraform validate
Review Changes
terraform plan
Create Infrastructure
terraform apply
Destroy Infrastructure
terraform destroy
Application Deployment

The application consists of a simple static HTML page.

Nginx serves the website from:

/usr/share/nginx/html

The website becomes accessible through the EC2 public IP.

Example:

http://<EC2_PUBLIC_IP>
CI/CD Pipeline

GitHub Actions is used to automate deployment.

Workflow
Developer pushes code to the main branch.
GitHub Actions workflow is triggered.
Files are copied to the EC2 instance using SCP.
SSH is used to deploy files to the Nginx web root.
Nginx serves the updated website.
GitHub Secrets Used
Secret	Purpose
HOST	EC2 Public IP
SSH_KEY	Private SSH Key
Design Decisions
Why Terraform?

Terraform provides Infrastructure as Code (IaC), making infrastructure repeatable, version-controlled, and easy to maintain.

Why GitHub Actions?

GitHub Actions integrates directly with the repository and provides a simple way to automate deployments without additional tooling.

Why EC2?

EC2 provides full control over the operating system and infrastructure, making it suitable for demonstrating cloud engineering fundamentals.

Why Nginx?

Nginx is lightweight, easy to configure, and commonly used as a web server in production environments.

Trade-Offs Considered
Advantages
Simple and easy-to-understand architecture
Fully automated deployment process
Infrastructure managed through code
Low operational cost
Limitations
Single EC2 instance creates a single point of failure
No load balancing
No auto-scaling
No monitoring or alerting configured

Cost Awareness

The solution was designed with cost optimization in mind.

Resources used:

1 EC2 Instance (t2.micro / Free Tier eligible)
1 Security Group
1 IAM Role
GitHub Actions (Free tier)

Estimated cost remains minimal and can fit within AWS Free Tier limits.

Challenges Faced

During implementation, the following issues were encountered and resolved:

SSH authentication issues caused by missing EC2 key pair configuration.
GitHub Actions deployment failures due to incorrect SSH username.
Nginx installation issue caused by using Ubuntu package commands on Amazon Linux 2023.
Security group validation for SSH and HTTP access.




├── terraform/
│   ├── main.tf
│   ├── provider.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── website/
│   └── index.html
│
├── .github/
│   └── workflows/
│       └── deploy.yml
____.gitignore
│
├── architecture.png
│
└── README.md






Author
sasi preetha chandaka
