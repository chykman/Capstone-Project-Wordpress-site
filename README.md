# Capstone-Project-Wordpress-site


## Table of Contents
1. [Project Overview](#project-overview)  
2. [Project Objectives](#project-objectives)  
3. [Project Deliverables](#project-deliverables)  
4. [Creating the Database](#creating-the-database)  
5. [Setting Up EC2 for RDS](#setting-up-ec2-for-rds)  
6. [Troubleshooting](#troubleshooting)  

---

## 1 Project Overview  
The goal of this project is to deploy a **highly available and scalable WordPress website on AWS**. The website will use the following AWS services:  

- **VPC**: To create a secure and isolated network environment.  
- **RDS**: To host the MySQL database for WordPress.  
- **EFS**: To provide shared storage for WordPress files.  
- **ALB (Application Load Balancer)**: To distribute traffic across multiple WordPress instances.  
- **Auto Scaling**: To automatically scale the number of WordPress instances based on traffic.  

---

## 2. Project Objectives  
- **Design and implement** a secure **VPC** with public and private subnets.  
- **Set up** a **MySQL database** using Amazon RDS.  
- **Configure shared file storage** using Amazon **EFS** for WordPress files.  
- **Deploy WordPress** on **EC2 instances** and ensure **high availability** using **ALB and Auto Scaling**.  
- **Test and validate** the setup to ensure **scalability, performance, and security**.  

---

## 3. Project Deliverables  
✔ **Architecture Diagram**: A visual representation of the AWS infrastructure.  
✔ **Step-by-Step Implementation Guide**: Detailed documentation of the setup process.  
✔ **Working WordPress Website**: A fully functional WordPress site hosted on AWS.  
✔ **Testing and Validation Report**: Results of performance, scalability, and security tests.  

# 4. Project Steps
-
## 4.1  Creating the VPC 
- Go to the search bar and search for VPC then enter and click on create.

- The CIDR range and the name of the VPC is specified in the picture below
  ![image](https://github.com/user-attachments/assets/b3cd94b1-6d55-4000-959a-9bec7cd3cf62)

  - You enter the number of Availaibility zones you require 
 
    ![image](https://github.com/user-attachments/assets/061f32ae-d784-4122-82f3-c5a8d2437198)

    - VPC is created
      ![image](https://github.com/user-attachments/assets/38407af4-51f0-4412-80b3-17a6919bddb3)

      ![image](https://github.com/user-attachments/assets/fa83ab8b-8dfe-4056-9877-e8b75be96a8e)



## 4.2  Creating the Subnets 

    - Navigate to the subnet section and click on create

![image](https://github.com/user-attachments/assets/ed7382e3-9291-4982-91d2-b0e3ee4b5e2d)

- Create your four subnets two for each Availability zone
![image](https://github.com/user-attachments/assets/58eb53a5-f060-4978-b993-8b03ee0d39b8)

- When done click on create
  ![image](https://github.com/user-attachments/assets/e398118a-142d-4e01-ad94-79dfdb4a5e77)

  - It has been created
    ![image](https://github.com/user-attachments/assets/b38e6dc2-e1e9-4c9d-bd59-51b05af484a5)


## 4.3 INTERNET GATEWAY 

- Go to the Internet Gateway section
  ![image](https://github.com/user-attachments/assets/f92e5c9e-8bd3-4c37-8362-47ed5a5d7fab)

  - Enter the name of your gateway and click on Create
    ![image](https://github.com/user-attachments/assets/62f8fa30-21c2-4556-9b0a-b690945ccb43)

    - Once it is created , got to actions module and click attach to vpc
      ![image](https://github.com/user-attachments/assets/d141571a-111b-43fd-9234-d5ec5193e260)

      - Select your vpc and click on attach vpc
        ![image](https://github.com/user-attachments/assets/60ae50ef-eb43-4042-9dfc-b3f35ebe1c6f)

        - It is successfully attached to ur vpc
          ![image](https://github.com/user-attachments/assets/13586663-1f4c-493f-b0c7-aaaf5b103a5b)

          

## 4.4.  ROUTE TABLE
    - Navigate to the Route tables and click on create route table
   ![image](https://github.com/user-attachments/assets/45a15ee2-859a-40ba-9c6d-67621d7aa021)
   
  - Enter the required information and click on create 
![image](https://github.com/user-attachments/assets/4e8177ec-9039-4708-a707-8e9e04e076ca)

- Route table has been created
  ![image](https://github.com/user-attachments/assets/0d743abb-a253-4997-bbfe-9e6785e38966)

- Go to Actions module and click on Edit subnet associations
  ![image](https://github.com/user-attachments/assets/06fc4890-6c21-45b2-8e46-286d71aa7a0e)

  - Select your two public associations and click on Save associations
    ![image](https://github.com/user-attachments/assets/f63a2875-860d-4f50-93f9-2c6170a31987)

    - Navigate to edit routes and add internet gateway route and save changes
          -  
![image](https://github.com/user-attachments/assets/86875852-a344-4e8b-a6a9-e675fbdf1836)

- For the public route go to your private subnet select the first one go to the route table section
  ![image](https://github.com/user-attachments/assets/666d21a2-d066-4ffe-a877-2d1db2d501c2)

  - Click on  route
   ![image](https://github.com/user-attachments/assets/8c694650-8623-486e-88ff-c0254ab1accc)

- Add natgateway route and save changes
  ![image](https://github.com/user-attachments/assets/559b0d32-4b02-48b0-9b3d-5cb62eee2e79)

  - This change will also apply to the second private subnet


## 4.5. NAT Gateway

- Navigate to the Elastic ip module and Create your Elastic ip for your Nat gateway
  ![image](https://github.com/user-attachments/assets/b351cedb-071b-4a10-a13a-56af0bee07c9)
  - ![image](https://github.com/user-attachments/assets/8d633eaf-5f86-4596-a58f-9d2718e81768)


- Navigate to the Nat Gateway module and click and Create Nat gateway
  ![image](https://github.com/user-attachments/assets/e3c3b5ef-4990-4e24-9d8a-d5d24fd3e7a7)

- Enter the details and create your Nat gateway
  ![image](https://github.com/user-attachments/assets/7bae9d0f-c7dd-4c2f-b3b1-2c0e33a2bd39)

  - Create another one for the second private subnet
    ![image](https://github.com/user-attachments/assets/91fc9c83-5412-4dc1-90fa-c077e058585b)
    - ![image](https://github.com/user-attachments/assets/d626d318-429e-4053-9c10-6324acdfdd29)


---
## 4.6. SECURITY GROUPS

 - Navigate to the EC2 and click on security group ad create security group
![image](https://github.com/user-attachments/assets/a481d2cc-d856-4791-b046-56bee7bff2a0)

- Craete A Secuurity group for each resource
- ALB Security group
- The Load balancer security group, inound allows http and https protocols
 ![image](https://github.com/user-attachments/assets/01c50507-9c97-45df-9d91-207037b404f0)

- And for the Outbound rule
- ![image](https://github.com/user-attachments/assets/39529be2-d1c4-4355-ba30-07e5e28c0042)

- SSH Security group
  - For the inbound it only allows my ip too ssh
    ![image](https://github.com/user-attachments/assets/f8ce2055-a523-450a-9b62-a21b7ffbb6b6)

    - Web server security group
    - 
      ![image](https://github.com/user-attachments/assets/fb1ce1cd-17de-4535-81b6-99fd1e44e4a6)

      - It allows ALB security group on the HTTP and HTTPS protocol and SSH security group on the SSH protocol on the inbound rule
      ![image](https://github.com/user-attachments/assets/b030b595-f4e0-4f36-b7a8-35438e54a947)

- For the outbound rule
  ![image](https://github.com/user-attachments/assets/3bc41218-ce3a-4965-a203-8baeb963c65d)

- Database Security group
- Inbound rules and outbound rules
  ![image](https://github.com/user-attachments/assets/daff1288-b15a-4442-971b-6c47887d4f38)

  - EFS Security group
   - Inbound Rules
    ![image](https://github.com/user-attachments/assets/b8d6c9e7-d163-423f-b7bc-359a4c74c23b)

- All groups have been created
  ![image](https://github.com/user-attachments/assets/c2d86342-c864-47ea-acfc-4072518bcb15)
 


---


  ## 4.7. AWS Mysql RDS 

  - Navigate to the Search bar and type RDS
    ![image](https://github.com/user-attachments/assets/9f2a602c-861f-4c5a-a75f-0bf42417c1bc)
    - Select database module by the sidebar
      ![image](https://github.com/user-attachments/assets/8ad568a8-5fdf-41c4-a09f-1d12f90d76ff)
      - Click on Create database
        ![image](https://github.com/user-attachments/assets/91b897ec-4e51-46f5-b126-90127abe13c9)

        - Select Standard create and select mysql Engine option
          ![image](https://github.com/user-attachments/assets/7a1cc348-b932-498f-b9d9-70551d76f3dc)
  - Set your master password
    ![image](https://github.com/user-attachments/assets/97549fd4-8e1e-4940-a3da-a51a76b40106)

    - Set your Connectivity settings
      ![image](https://github.com/user-attachments/assets/ee2d42de-6063-4b18-b427-93cac9d8eb26)


      - Select your existing VPC security group
        ![image](https://github.com/user-attachments/assets/020d218b-7236-4d52-ac39-00577f6fbffe)

 - Click on Create database
   ![image](https://github.com/user-attachments/assets/b8a1f4b2-ca8b-4d11-93ad-8193de5f82f0)

   - Our Database is being created
     ![image](https://github.com/user-attachments/assets/eb47acdf-e9ea-43fe-8053-783449af458d)

    - DB has been successfully created
     ![image](https://github.com/user-attachments/assets/c3797c89-72d2-4fdd-bd97-6293401ac4c7)

- Ensure the db subnet group is created on only private subnet
    ![image](https://github.com/user-attachments/assets/7080ce4c-ad12-4f6a-8fa6-5cfd09821f77)


## EC2 INSTANCES 

- Navigate to your  ec2 and click on Launch instance
  ![image](https://github.com/user-attachments/assets/7a29b584-00e6-40b3-84b2-a14b4f6b7a68)

  - Ensure you select your created vpc and private subnet in your network settings
    ![image](https://github.com/user-attachments/assets/5f8ee2fc-5e5c-43f6-a09a-4319fa1cffbb)

    - Launch your instance
      ![image](https://github.com/user-attachments/assets/8e6fb875-a5aa-461c-994f-6702753ec72f)

      - You won't be able to reach the instance due to it being on a private subnet
        ![image](https://github.com/user-attachments/assets/a98b954d-cf6d-49a5-b825-ae3532040837)

        - We will need to create a bastion host, go to the ec2 module and launch instance
          ![image](https://github.com/user-attachments/assets/bdc8013d-487b-465f-9801-1f699ed34c28)

          - Maintain the same configuration but modify the subnet to the private one
            ![image](https://github.com/user-attachments/assets/66cbf5dd-53d0-4cc7-b38d-df6a424cc14b)

          



































    


