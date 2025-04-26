# 🌐 AWS VPC with EC2 in Private Subnets and NAT Gateway

This project demonstrates how to create a secure, production-ready Virtual Private Cloud (VPC) on AWS using **public and private subnets**, **EC2 instances**, and a **NAT Gateway**, with **Linux Ubuntu** as the base operating system for provisioning and access.

---

## 📌 Overview

You will design a custom AWS VPC with proper **routing**, **network isolation**, and **access controls**. This includes:

- Public and private subnets across multiple Availability Zones
- EC2 instances with IAM roles and controlled security groups
- NAT Gateway to allow outbound access from private instances
- Secure SSH access using Linux-native tools
- Network ACLs and routing tables to enforce traffic flow

---


---

## ✅ Features

- ✅ Multi-tier VPC: Public + Private Subnets
- ✅ NAT Gateway for secure internet access from private EC2
- ✅ Security Groups and Network ACLs for layered protection
- ✅ IAM roles and access control
- ✅ SSH access with private key from Ubuntu Linux

---

## 🖥️ Prerequisites

- ✅ AWS Account
- ✅ AWS CLI configured (`aws configure`)
- ✅ Ubuntu Linux environment (tested on 20.04+)
- ✅ SSH client (`ssh`), SCP for file transfer
- ✅ Basic knowledge of VPC, EC2, and IAM

---

## ⚙️ Implementation Steps

### 1. VPC Design

- Create a custom VPC (e.g., `10.0.0.0/16`)
- Create **public** and **private** subnets in different AZs
- Set up **route tables** and associate them:
  - Public subnet ➝ route to Internet Gateway
  - Private subnet ➝ route to NAT Gateway

### 2. Configure Network Security

- Create **Network ACLs** for inbound/outbound subnet traffic
- Set up **Security Groups**:
  - Allow SSH (port 22) on public instances only
  - Allow necessary ports for applications (e.g., HTTP, HTTPS)

### 3. Launch EC2 Instances

- Launch a public EC2 instance (Ubuntu) in public subnet
- Launch private EC2 instances in private subnets
- Attach appropriate **IAM roles** for permissions (e.g., SSM, S3 access)

### 4. Configure Internet Access

- Attach an **Internet Gateway** to the VPC
- Create a **NAT Gateway** in the public subnet
- Configure private route table to route `0.0.0.0/0` through the NAT Gateway

### 5. SSH Access & IAM Control (Linux Specific)

- Use .pem or .pub when launching EC2:
 - Upload public key via AWS Console or import into EC2
-Connect to EC2 from Ubuntu terminal:
- Connect to private EC2 (via bastion):

---
## 🎯 Project Outcomes

After completing this project, you will:

- Understand how to isolate public and private workloads in AWS
- Use a NAT Gateway to enable secure internet access for private instances
- Apply IAM roles and key-based SSH access control from a Linux (Ubuntu) environment
- Secure your cloud infrastructure using AWS networking and security best practices

---

## 📜 License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for more information.

