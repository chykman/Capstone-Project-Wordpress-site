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


  ## 4.6. AWS Mysql RDS 

  - Navigate to the Search bar and type RDS
    ![image](https://github.com/user-attachments/assets/9f2a602c-861f-4c5a-a75f-0bf42417c1bc)
    - Select database module by the sidebar
      ![image](https://github.com/user-attachments/assets/8ad568a8-5fdf-41c4-a09f-1d12f90d76ff)
      - Click on Create database
        ![image](https://github.com/user-attachments/assets/91b897ec-4e51-46f5-b126-90127abe13c9)

        - Select Standard create and select mysql Engine option
          ![image](https://github.com/user-attachments/assets/7a1cc348-b932-498f-b9d9-70551d76f3dc)

          -

         







 
    


-


      ## 5. AWS RDS
    ### 5.1. Creating the database

    - Navigate to the search bar and enter RDS and click on it
      ![image](https://github.com/user-attachments/assets/c9046a42-06b2-4347-bffc-664000eb2379)

      - Go to DB Instances
        ![image](https://github.com/user-attachments/assets/eafd902e-0ea9-44a7-8b64-5a183e180141)

        - Click on Create DB
       ![image](https://github.com/user-attachments/assets/860b7cdf-e335-4374-a1e8-44bb71edecf4)

    - Select the Standard create for the databse and mysql for the db engine type
      ![image](https://github.com/user-attachments/assets/2402dc16-67ff-4fe7-957c-bd958d999b24)

      - For the engine version we will use the 8.0.35 and the free tier template
        ![image](https://github.com/user-attachments/assets/496bdc93-7eda-4c7f-b1ab-9a95508e034c)

        - next





























    


