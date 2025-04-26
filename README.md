# 🚀 Secure AWS VPC Architecture with Load Balancer, NAT Gateway, Auto Scaling Group, and Bastion Host

This project demonstrates how to create a secure, production-ready Virtual Private Cloud (VPC) on AWS using **public and private subnets**, **EC2 instances**, and a **NAT Gateway**, with **Linux Ubuntu** as the base operating system for provisioning and access.

The project covers setting up a Virtual Private Cloud (VPC) with both public and private subnets across two availability zones, deploying applications using Auto Scaling groups, and configuring a load balancer to distribute traffic efficiently. It also highlights key concepts like Elastic IPs and Bastion Hosts to ensure secure access and stable communication between resources.It uses concepts learned from the AWS Zero to Hero series, providing a hands-on approach to creating scalable, secure, and high-availability infrastructure in AWS.

## Key Concepts Used

- **VPC Setup:** A VPC is created with both public and private subnets. Public subnets contain the Load Balancer and NAT Gateway, while private subnets host the EC2 instances.
- **Auto Scaling:** Auto Scaling ensures that EC2 instances scale automatically based on traffic.
- **Load Balancer:** The Application Load Balancer (ALB) is configured to distribute incoming HTTP traffic to multiple EC2 instances, providing high availability.
- **Bastion Host:** A Bastion host is used for secure SSH access to private EC2 instances.
- **Elastic IPs:** Static IP addresses are used to ensure consistent external IP for the NAT Gateway.

## 🏗️ Architecture Overview

- **Virtual Private Cloud (VPC)** with **public** and **private subnets** across **two Availability Zones**.
- **Application Load Balancer** deployed in the **public subnet** to handle incoming internet traffic.
- **NAT Gateway** in the **public subnet** to enable private subnet instances to access the internet securely.
- **Auto Scaling Group (ASG)** to automatically scale EC2 instances based on demand.
- **Bastion Host** deployed in the public subnet to allow secure SSH access to instances in the private subnet.
- **EC2 instances** (applications) deployed in private subnets, accessible only via the Load Balancer or Bastion Host.


## Setup Instructions

### 1. **Create VPC and Subnets**
   - Set up a VPC with public and private subnets in two availability zones.
   - Assign appropriate route tables to public and private subnets.

### 2. **Create Auto Scaling Group (ASG)**
   - Create an Auto Scaling group using an EC2 launch template that includes the AMI, instance type, and security settings.
   - Specify the desired number of EC2 instances (e.g., 2 instances) and configure scaling options based on traffic demand.

### 3. **Bastion Host Setup**
   - Create a Bastion host in the public subnet for SSH access to private EC2 instances.
   - SSH into the Bastion host and securely copy your private key to the Bastion host.
   - Use the Bastion host to SSH into the private EC2 instances for management and installation tasks.

### 4. **Install Application on EC2 Instances**
   - On one EC2 instance in the private subnet, install a simple Python application:
     ```bash
     python3 -m http.server 8000
     ```
   - Set up a basic HTML page to serve through HTTP on Port 8000.

### 5. **Load Balancer Configuration**
   - Create an Application Load Balancer (ALB) in the public subnet to handle incoming HTTP traffic.
   - Define a target group that includes the private EC2 instances and configure health checks.
   - The ALB will distribute traffic to the healthy instances, ensuring high availability.

### 6. **Security Group Configuration**
   - Ensure the security group for the ALB allows inbound HTTP traffic on Port 80.
   - Configure the security groups for EC2 instances and ALB appropriately.

### 7. **Testing and Scaling**
   - Test the setup by accessing the load balancer’s IP address. Initially, traffic will be routed to the healthy EC2 instance.
   - To demonstrate scaling, install the application on both EC2 instances in the Auto Scaling group. Once both instances are healthy, the load balancer will alternate traffic between them.

## Explanation of Key Concepts

### Load Balancer
   - The Application Load Balancer (ALB) distributes incoming traffic across multiple EC2 instances.
   - The load balancer can handle path-based and host-based routing, ensuring that requests are efficiently routed based on availability.
   - For example, with two EC2 instances, the load balancer will divide 100 requests into 50 per instance. If one server is more powerful, the load balancer can send more traffic to it (e.g., 60 requests to one, 40 to the other).

### Bastion Host
   - The Bastion host in the public subnet provides secure SSH access to EC2 instances in private subnets.
   - Since private instances don’t have public IPs, the Bastion host allows secure access through SSH for management and auditing.

### Elastic IP
   - Elastic IPs are static IP addresses that remain the same even if an EC2 instance is stopped and started.
   - Elastic IPs are useful for services like NAT Gateways, which need a stable IP address to mask private EC2 instance IPs when accessing the internet.

### Auto Scaling Group
   - The Auto Scaling Group ensures that the right number of EC2 instances are running based on traffic demands.
   - It automatically adds or removes instances as needed, improving scalability and availability.

## 🛠️ Technologies Used

- AWS VPC
- EC2
- Elastic Load Balancer (ALB)
- Auto Scaling Group (ASG)
- NAT Gateway
- Bastion Host
- Internet Gateway
- Route Tables
- IAM Roles and Policies
- Linux (Ubuntu)

---
## 🎯 Project Outcomes

After completing this project, i :

- Understand how to isolate public and private workloads in AWS
- Use a NAT Gateway to enable secure internet access for private instances
- Apply IAM roles and key-based SSH access control from a Linux (Ubuntu) environment
- Secure your cloud infrastructure using AWS networking and security best practices

---

## Conclusion

This project demonstrates how to set up a scalable, secure, and highly available architecture in AWS using essential services like VPCs, Auto Scaling, Load Balancers, and Bastion Hosts. By following the steps in this project, you will gain hands-on experience in building production-grade AWS infrastructures that scale with traffic.

---

## 📚 References

- [AWS Best Practices for VPC Architecture](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Introduction.html)
- [AWS Auto Scaling Group Documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
- [AWS NAT Gateway Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)
- [Elastic Load Balancing Overview](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)
- [AWS Bastion Host Setup](https://docs.aws.amazon.com/quickstart/latest/linux-bastion/overview.html)

---

## 📜 License

This project is licensed under the **MIT License**.  
See the [LICENSE](LICENSE) file for more information.

## 🙋‍♂️ Author & Contributions

Built with ❤️ on **Linux Ubuntu**.

Contributions, suggestions, and improvements are always welcome! Feel free to open an issue or submit a pull request.

---
