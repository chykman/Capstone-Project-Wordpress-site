# Capstone-Project-WordPress-Site

---

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Project Objectives](#project-objectives)  
3. [Project Deliverables](#project-deliverables)  
4. [Project Steps](#project-steps)  
    - [Creating the VPC](#41-creating-the-vpc)  
    - [Creating the Subnets](#42-creating-the-subnets)  
    - [Internet Gateway](#43-internet-gateway)  
    - [Route Table](#44-route-table)  
    - [NAT Gateway](#45-nat-gateway)  
    - [Security Groups](#46-security-groups)  
    - [AWS MySQL RDS](#47-aws-mysql-rds)  
    - [EC2 Instances](#ec2-instances)  
    - [WordPress Installation](#wordpress)  
    - [Elastic File System (EFS)](#efs)  
    - [Load Balancers](#load-balancers)  
    - [Auto Scaling Group](#auto-scaling-group)  
5. [Fully Deployed WordPress Site](#a-fully-deployed-wordpress-site)  
6. [Mounted EFS](#the-mounted-efs)  
7. [Network Traffic](#the-network-traffic)  

---

## 1. Project Overview
The goal of this project is to deploy a **highly available and scalable WordPress website on AWS** using:

- **VPC**: Secure and isolated network.
- **RDS**: Host MySQL database.
- **EFS**: Shared storage for WordPress files.
- **ALB**: Distribute traffic across instances.
- **Auto Scaling**: Scale instances based on traffic.

---

## 2. Project Objectives
- Design and implement a secure VPC with public and private subnets.
- Set up MySQL database using Amazon RDS.
- Configure shared file storage using Amazon EFS.
- Deploy WordPress on EC2 and ensure high availability using ALB and Auto Scaling.
- Test and validate scalability, performance, and security.

---

## 3. Project Deliverables
- **Architecture Diagram**.
- **Step-by-Step Implementation Guide**.
- **Working WordPress Website**.
- **Testing and Validation Report**.

---

# 4. Project Steps

---

## 4.1 Creating the VPC

- Go to the search bar and search for VPC then click Create.

![VPC](https://github.com/user-attachments/assets/b3cd94b1-6d55-4000-959a-9bec7cd3cf62)

![Availability Zones](https://github.com/user-attachments/assets/061f32ae-d784-4122-82f3-c5a8d2437198)

![VPC Created](https://github.com/user-attachments/assets/38407af4-51f0-4412-80b3-17a6919bddb3)

![VPC Confirmed](https://github.com/user-attachments/assets/fa83ab8b-8dfe-4056-9877-e8b75be96a8e)

---

## 4.2 Creating the Subnets

- Navigate to the subnet section and click on Create.

![Subnet Create](https://github.com/user-attachments/assets/ed7382e3-9291-4982-91d2-b0e3ee4b5e2d)

- Create four subnets (two per Availability Zone).

![Subnets Setup](https://github.com/user-attachments/assets/58eb53a5-f060-4978-b993-8b03ee0d39b8)

![Subnets Created](https://github.com/user-attachments/assets/e398118a-142d-4e01-ad94-79dfdb4a5e77)

![Subnets Success](https://github.com/user-attachments/assets/b38e6dc2-e1e9-4c9d-bd59-51b05af484a5)

---

## 4.3 Internet Gateway

- Navigate to the Internet Gateway section.

![Internet Gateway](https://github.com/user-attachments/assets/f92e5c9e-8bd3-4c37-8362-47ed5a5d7fab)

- Create and attach it to the VPC.

![Gateway Creation](https://github.com/user-attachments/assets/62f8fa30-21c2-4556-9b0a-b690945ccb43)

![Attach to VPC](https://github.com/user-attachments/assets/d141571a-111b-43fd-9234-d5ec5193e260)

![Gateway Attached](https://github.com/user-attachments/assets/60ae50ef-eb43-4042-9dfc-b3f35ebe1c6f)

![Gateway Success](https://github.com/user-attachments/assets/13586663-1f4c-493f-b0c7-aaaf5b103a5b)

---

## 4.4 Route Table

- Navigate to Route Tables and create a Route Table.

![Create Route Table](https://github.com/user-attachments/assets/45a15ee2-859a-40ba-9c6d-67621d7aa021)

![Route Table Setup](https://github.com/user-attachments/assets/4e8177ec-9039-4708-a707-8e9e04e076ca)

![Route Table Created](https://github.com/user-attachments/assets/0d743abb-a253-4997-bbfe-9e6785e38966)

![Subnet Associations](https://github.com/user-attachments/assets/06fc4890-6c21-45b2-8e46-286d71aa7a0e)

![Select Subnets](https://github.com/user-attachments/assets/f63a2875-860d-4f50-93f9-2c6170a31987)

![Edit Routes](https://github.com/user-attachments/assets/86875852-a344-4e8b-a6a9-e675fbdf1836)

![Private Subnet](https://github.com/user-attachments/assets/666d21a2-d066-4ffe-a877-2d1db2d501c2)

![Add NAT Gateway Route](https://github.com/user-attachments/assets/8c694650-8623-486e-88ff-c0254ab1accc)

![NAT Gateway Route Added](https://github.com/user-attachments/assets/559b0d32-4b02-48b0-9b3d-5cb62eee2e79)

---

## 4.5 NAT Gateway

- Create Elastic IP addresses for NAT Gateways.

![Elastic IP](https://github.com/user-attachments/assets/b351cedb-071b-4a10-a13a-56af0bee07c9)

![Elastic IP Setup](https://github.com/user-attachments/assets/8d633eaf-5f86-4596-a58f-9d2718e81768)

- Create NAT Gateways using the Elastic IPs.

![Create NAT Gateway](https://github.com/user-attachments/assets/e3c3b5ef-4990-4e24-9d8a-d5d24fd3e7a7)

![NAT Gateway Details](https://github.com/user-attachments/assets/7bae9d0f-c7dd-4c2f-b3b1-2c0e33a2bd39)

![Second NAT Gateway](https://github.com/user-attachments/assets/91fc9c83-5412-4dc1-90fa-c077e058585b)

![NAT Gateway Created](https://github.com/user-attachments/assets/d626d318-429e-4053-9c10-6324acdfdd29)

---

## 4.6 Security Groups

- Create Security Groups for ALB, SSH, Web Server, Database, and EFS.

![Security Group Creation](https://github.com/user-attachments/assets/a481d2cc-d856-4791-b046-56bee7bff2a0)

![ALB Security Group](https://github.com/user-attachments/assets/01c50507-9c97-45df-9d91-207037b404f0)

![Outbound Rules ALB](https://github.com/user-attachments/assets/39529be2-d1c4-4355-ba30-07e5e28c0042)

![SSH Security Group](https://github.com/user-attachments/assets/f8ce2055-a523-450a-9b62-a21b7ffbb6b6)

![Web Server SG](https://github.com/user-attachments/assets/fb1ce1cd-17de-4535-81b6-99fd1e44e4a6)

![Inbound Web Server](https://github.com/user-attachments/assets/b030b595-f4e0-4f36-b7a8-35438e54a947)

![Outbound Web Server](https://github.com/user-attachments/assets/3bc41218-ce3a-4965-a203-8baeb963c65d)

![Database SG](https://github.com/user-attachments/assets/daff1288-b15a-4442-971b-6c47887d4f38)

![EFS Security Group](https://github.com/user-attachments/assets/b8d6c9e7-d163-423f-b7bc-359a4c74c23b)

![All SGs Created](https://github.com/user-attachments/assets/c2d86342-c864-47ea-acfc-4072518bcb15)

---
---

## 4.7 AWS MySQL RDS

- Navigate to RDS from the AWS search bar.

![RDS Dashboard](https://github.com/user-attachments/assets/9f2a602c-861f-4c5a-a75f-0bf42417c1bc)

- Select **Database** from the sidebar.

![Database Sidebar](https://github.com/user-attachments/assets/8ad568a8-5fdf-41c4-a09f-1d12f90d76ff)

- Click **Create Database**.

![Create Database](https://github.com/user-attachments/assets/91b897ec-4e51-46f5-b126-90127abe13c9)

- Select **Standard Create** and **MySQL Engine**.

![Select MySQL](https://github.com/user-attachments/assets/7a1cc348-b932-498f-b9d9-70551d76f3dc)

- Set your **Master Password**.

![Master Password](https://github.com/user-attachments/assets/97549fd4-8e1e-4940-a3da-a51a76b40106)

- Configure **Connectivity Settings**.

![Connectivity Settings](https://github.com/user-attachments/assets/ee2d42de-6063-4b18-b427-93cac9d8eb26)

- Attach existing VPC and Security Group.

![VPC Security Group](https://github.com/user-attachments/assets/020d218b-7236-4d52-ac39-00577f6fbffe)

- Click **Create Database**.

![Database Creation](https://github.com/user-attachments/assets/b8a1f4b2-ca8b-4d11-93ad-8193de5f82f0)

- Database is being created.

![Database Progress](https://github.com/user-attachments/assets/eb47acdf-e9ea-43fe-8053-783449af458d)

- Database successfully created.

![Database Created](https://github.com/user-attachments/assets/c3797c89-72d2-4fdd-bd97-6293401ac4c7)

- DB Subnet Group created only on Private Subnets.

![DB Subnet Group](https://github.com/user-attachments/assets/7080ce4c-ad12-4f6a-8fa6-5cfd09821f77)

---

# EC2 Instances

- Navigate to EC2 and click **Launch Instance**.

![Launch Instance](https://github.com/user-attachments/assets/7a29b584-00e6-40b3-84b2-a14b4f6b7a68)

- Select VPC and **Public Subnet**.

![Public Subnet Settings](https://github.com/user-attachments/assets/5f8ee2fc-5e5c-43f6-a09a-4319fa1cffbb)

- Launch your instance.

![Instance Launched](https://github.com/user-attachments/assets/8e6fb875-a5aa-461c-994f-6702753ec72f)

---

# WordPress

- SSH into the  EC2 instance.

![SSH Connection](https://github.com/user-attachments/assets/5f44969b-176a-4a8d-8e00-7906deb9588a)

- Update system dependencies.

![Update Dependencies](https://github.com/user-attachments/assets/642dc63e-b83b-4a17-b4ad-7d66edf15911)

- Install Apache Web Server.

![Install Apache](https://github.com/user-attachments/assets/d4bee349-c0b7-4293-9346-d0e2cfee0e06)

- Install PHP and PHP-MySQL Connector.

![Install PHP](https://github.com/user-attachments/assets/6b247ddd-eb7f-4765-875f-0ce378bfc602)

- Install MySQL Server.

![Install MySQL Server](https://github.com/user-attachments/assets/a12dec41-9640-42bf-bfbf-10eb73f55ecf)

- Login to MySQL server.

![Login MySQL](https://github.com/user-attachments/assets/cdcc2205-9f2b-4f97-a9d1-496d64f83bb8)

- Change Authentication Plugin.

![Change Authentication Plugin](https://github.com/user-attachments/assets/38fc454e-75da-4491-9946-f60b187371fc)

- Create new WordPress Database and User.

![Create Database](https://github.com/user-attachments/assets/1b77d66e-6057-4e39-9fe8-6336a7604435)

- Grant Privileges.

![Grant Privileges](https://github.com/user-attachments/assets/eefed3dc-b1f0-407c-b9d7-55bda1ef9b20)

- Login as Admin User.

![Login as Admin](https://github.com/user-attachments/assets/ec4629b4-5725-4a8b-bec6-819f096c7295)

- Download WordPress to `/tmp` folder.

![Download WordPress](https://github.com/user-attachments/assets/fec16730-89fe-4ab8-b492-e50b9d17ec9b)

- Download and Extract.

![Extract WordPress](https://github.com/user-attachments/assets/05bdfb0e-f671-4df9-a69b-84e87ac2d3fe)

![WordPress Extracted](https://github.com/user-attachments/assets/9bf51611-f12b-42e3-8f48-c41c1f75e112)

- Move to `/var/www/html`.

![Move WordPress](https://github.com/user-attachments/assets/2a90cecf-8873-4353-8a73-f6c4519fff22)

- Enable and Restart Apache.

![Restart Apache](https://github.com/user-attachments/assets/a4be5cce-ce0c-4c0d-90da-948530283325)

- Access WordPress Website.

![WordPress Site](https://github.com/user-attachments/assets/80e6412e-df57-4d51-a768-1e1a298c7587)

![WordPress Setup](https://github.com/user-attachments/assets/68105236-ba71-4941-bd6e-ab24f7764c8d)

![Install WordPress](https://github.com/user-attachments/assets/b8598484-0b62-46b1-a629-688196709063)

![WordPress Success](https://github.com/user-attachments/assets/667ebfe9-801c-4b1a-9cf6-3c4866ecc2dd)

---

# EFS

- Navigate to **EFS** service.

![EFS Dashboard](https://github.com/user-attachments/assets/e7e262fd-3df4-4cb1-9cd8-42a4f071ffc3)

- Create a Filesystem.

![Create EFS](https://github.com/user-attachments/assets/2ccb50e7-843e-4fbe-89a7-b133bb4f6c1b)

- Provide Name and VPC.

![EFS Name and VPC](https://github.com/user-attachments/assets/34f0c7f5-1510-437e-b95b-bf9a9e051297)

- Attach Security Groups.

![EFS Security Groups](https://github.com/user-attachments/assets/36c4d7e0-ffa8-42d5-ab7c-44547ee4228d)

- Create EFS.

![EFS Created](https://github.com/user-attachments/assets/0f1a8581-271f-4b75-93ee-4b2f806089d5)

- View and Attach EFS.

![EFS Attach](https://github.com/user-attachments/assets/2f7f1850-99b0-4f0f-a12b-aaf8aed281a0)

![EFS View Details](https://github.com/user-attachments/assets/bbc809f9-4e8b-4937-9a80-32cf19381dd5)

![Select Mount Helper](https://github.com/user-attachments/assets/692b07a0-8108-4810-9c06-e89ac98b3aa7)

![Mount EFS](https://github.com/user-attachments/assets/33e59ae2-798c-47fb-a6b8-435c0b7ea8ab)

![SSH Mount EFS](https://github.com/user-attachments/assets/a4a677dd-f1f5-47c7-abc7-242e11318f63)

---

# Load Balancers

- Create **Application Load Balancer**.

![Load Balancer](https://github.com/user-attachments/assets/c1e69a0c-02e3-44f2-a104-70ea2a653c90)

![Select ALB](https://github.com/user-attachments/assets/2ce23373-bc61-4aa9-bf64-208de2ac1b68)

- Internet Facing Settings.

![Internet Facing](https://github.com/user-attachments/assets/36e7fdd9-22d8-4c6f-927a-d7afb57bbd3b)

- Network and Target Group.

![Network Settings](https://github.com/user-attachments/assets/6d53405c-8db5-4e8e-af6c-b2be11f2ba1b)

![Target Group](https://github.com/user-attachments/assets/ade89b86-1b16-4e49-b1db-690bc2618a0e)

- Load Balancer Created.

![Load Balancer Created](https://github.com/user-attachments/assets/842d2f46-9252-47fa-a0ea-46f2cce738f7)

![ALB Success](https://github.com/user-attachments/assets/d7a7e8c3-6b17-49fb-b878-45281abd101e)

---

---

# Auto Scaling Group

- Navigate to the search bar and type **Auto Scaling**, then select it.

![Auto Scaling Search](https://github.com/user-attachments/assets/e5dcf198-d54f-4dfc-b0df-53e4702a428d)

- Click on **Create Auto Scaling Group**.

![Create Auto Scaling Group](https://github.com/user-attachments/assets/96c390f6-ddcd-43f5-8427-97628c4cbc8d)

- Enter the name and select the **already created Launch Template**.

![Select Launch Template](https://github.com/user-attachments/assets/7d95c1ab-328c-4980-a420-ac229986f0f6)

- Configure the **Network Settings**.

![Network Settings for ASG](https://github.com/user-attachments/assets/d02407d7-2fce-4273-8a1f-97d83c09d0c9)

- Attach the **created Load Balancer**.

![Attach Load Balancer](https://github.com/user-attachments/assets/ae206e48-4a83-44cb-b7e3-514d8c986059)

- Leave the other settings as default and click **Create Auto Scaling Group**.

![Create ASG](https://github.com/user-attachments/assets/2f1ec5fd-7587-4c13-96ae-602a03e4a0b4)

- Auto Scaling Group created successfully!

![ASG Created](https://github.com/user-attachments/assets/a87924b2-d30a-41e3-b937-b14dd0cb3342)

---

# A Fully Deployed WordPress Site 🎯

- WordPress site running and accessible via Load Balancer.

![WordPress Site Screenshot 1](https://github.com/user-attachments/assets/81b8298c-a2ad-4e21-9ed2-ac44402256cd)

![WordPress Site Screenshot 2](https://github.com/user-attachments/assets/a007dfdc-4066-4991-905d-11fd24400350)

![WordPress Site Screenshot 3](https://github.com/user-attachments/assets/286a31c3-1543-4e27-8448-18e00e1a315f)

![WordPress Site Screenshot 4](https://github.com/user-attachments/assets/253de3f6-4c8c-4b36-a67d-63586cafdfaa)

![WordPress Site Screenshot 5](https://github.com/user-attachments/assets/73f33378-f83b-4114-815d-631dd3104273)

![WordPress Site Screenshot 6](https://github.com/user-attachments/assets/3d2fdd8a-bd2f-4767-8a82-a7de875aa840)

![WordPress Site Screenshot 7](https://github.com/user-attachments/assets/a6cab4ce-b727-4558-9831-e44d6d76ce74)

---

# The Mounted EFS

- The EFS filesystem has been properly mounted to the EC2 instances.

![Mounted EFS Screenshot 1](https://github.com/user-attachments/assets/7d6aa667-eaae-4f7b-9114-d3374b5b8389)

![Mounted EFS Screenshot 2](https://github.com/user-attachments/assets/84345377-7266-4be8-b005-b1718bf9a039)

---

# The Network Traffic (Load Test)

- Servers behind the Load Balancer are active.

![Servers Behind Load Balancer](https://github.com/user-attachments/assets/a5e0ac0a-5716-41b6-ba4b-35264344acd1)

- Auto Scaling Group instances created dynamically based on load.

![ASG Instances](https://github.com/user-attachments/assets/73d5df87-db9e-4ffe-aa4d-3b2b56fbcab5)

- Traffic load observed on all three servers.

![Traffic Load on Servers](https://github.com/user-attachments/assets/a7dc2c78-5a9b-45d8-8711-f351b1afe23e)

- JMeter used to simulate load traffic.

![JMeter Load Testing](https://github.com/user-attachments/assets/43b65365-7fce-4202-9ca3-fbe0b2e3b42c)

- Successful Response Code from servers during load test.

![Success Response Code](https://github.com/user-attachments/assets/b594200e-e125-4c9d-b7b0-7208db37eba8)

---

# Final Outcome 🎯

✅ WordPress website is highly available.  
✅ Auto Scaling launches additional servers during peak load.  
✅ Load Balancer efficiently distributes traffic.  
✅ Database is hosted securely on RDS.  
✅ Shared file storage through EFS is mounted and working.

---

# Conclusion

This project successfully demonstrates how to deploy a highly available and scalable WordPress website on AWS using best practices. By leveraging services such as VPC, RDS, EFS, Load Balancer, and Auto Scaling Groups, we achieved a secure, resilient, and fault-tolerant architecture ready for production workloads.

---

