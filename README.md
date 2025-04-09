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

      

            - We will ssh into the  instancerunning the command below
              "ssh -i wpkey.pem ubuntu@13.216.22.19

         ![image](https://github.com/user-attachments/assets/5f44969b-176a-4a8d-8e00-7906deb9588a)


       ## Wordpress

              - Now to install Wordpress on our private ec2 instance, ssh to the private instance
    ![image](https://github.com/user-attachments/assets/866f3929-08dd-4256-8807-96918389691e)
                - Update all dependies
                  ![image](https://github.com/user-attachments/assets/642dc63e-b83b-4a17-b4ad-7d66edf15911)

                  - Install apache web server
    ![image](https://github.com/user-attachments/assets/d4bee349-c0b7-4293-9346-d0e2cfee0e06)


            - Install php runtime and php mysql connector
    ![image](https://github.com/user-attachments/assets/6b247ddd-eb7f-4765-875f-0ce378bfc602)

              - Install MySQL server
     ![image](https://github.com/user-attachments/assets/a12dec41-9640-42bf-bfbf-10eb73f55ecf)

                - Login to MySQL server
     ![image](https://github.com/user-attachments/assets/cdcc2205-9f2b-4f97-a9d1-496d64f83bb8)

                - Change authentication plugin to mysql_native_password
    ![image](https://github.com/user-attachments/assets/38fc454e-75da-4491-9946-f60b187371fc)

                  - Create a new database admin user for wordpress
     ![image](https://github.com/user-attachments/assets/1b77d66e-6057-4e39-9fe8-6336a7604435)

                    - CREATE DATABASE Word press db and grant all privileges to user admin user
     ![image](https://github.com/user-attachments/assets/eefed3dc-b1f0-407c-b9d7-55bda1ef9b20)

                      - We can now login with our Admin user
     ![image](https://github.com/user-attachments/assets/ec4629b4-5725-4a8b-bec6-819f096c7295)

  - wE will now download wordpress, Navigate to your temp folder on the private instance
    ![image](https://github.com/user-attachments/assets/fec16730-89fe-4ab8-b492-e50b9d17ec9b)

    - Download wordpress on it
      ![image](https://github.com/user-attachments/assets/05bdfb0e-f671-4df9-a69b-84e87ac2d3fe)

- ![image](https://github.com/user-attachments/assets/9bf51611-f12b-42e3-8f48-c41c1f75e112)

      - Extract it
     ![image](https://github.com/user-attachments/assets/81dceeb1-98c5-4d8a-9886-e8bc72488316)

- Move the extracted folder to var/html/www folder
  ![image](https://github.com/user-attachments/assets/2a90cecf-8873-4353-8a73-f6c4519fff22)

  - Enable your apache server then restart
    ![image](https://github.com/user-attachments/assets/a4be5cce-ce0c-4c0d-90da-948530283325)

    - Open the Wordpress site on your browser
      ![image](https://github.com/user-attachments/assets/80e6412e-df57-4d51-a768-1e1a298c7587)

      - ![image](https://github.com/user-attachments/assets/68105236-ba71-4941-bd6e-ab24f7764c8d)
      - ![image](https://github.com/user-attachments/assets/b8598484-0b62-46b1-a629-688196709063)
      - ![image](https://github.com/user-attachments/assets/667ebfe9-801c-4b1a-9cf6-3c4866ecc2dd)





## EFS 

- Navigate to the search bar and enter EFS
  ![image](https://github.com/user-attachments/assets/e7e262fd-3df4-4cb1-9cd8-42a4f071ffc3)

  - Click on Create filesystem
    ![image](https://github.com/user-attachments/assets/2ccb50e7-843e-4fbe-89a7-b133bb4f6c1b)

    - Provide name 
     ![image](https://github.com/user-attachments/assets/34f0c7f5-1510-437e-b95b-bf9a9e051297)

      - Select the vpc and security groups
        ![image](https://github.com/user-attachments/assets/36c4d7e0-ffa8-42d5-ab7c-44547ee4228d)

        - Leave rest as default and clcik on create
          ![image](https://github.com/user-attachments/assets/0f1a8581-271f-4b75-93ee-4b2f806089d5)

          - Filesystem has been created
            ![image](https://github.com/user-attachments/assets/2f7f1850-99b0-4f0f-a12b-aaf8aed281a0)
        -  Click on View details module
        - ![image](https://github.com/user-attachments/assets/bbc809f9-4e8b-4937-9a80-32cf19381dd5)
        - Click on Attach
          ![image](https://github.com/user-attachments/assets/692b07a0-8108-4810-9c06-e89ac98b3aa7)
       
          - Select the mount helper command
            ![image](https://github.com/user-attachments/assets/33e59ae2-798c-47fb-a6b8-435c0b7ea8ab)
          - SSh to your instance and run the command
            ![image](https://github.com/user-attachments/assets/a4a677dd-f1f5-47c7-abc7-242e11318f63)


              


            ## Load balancers

            - Navigate to the Load Balancers module and click on Create aLoad balancer
            ![image](https://github.com/user-attachments/assets/c1e69a0c-02e3-44f2-a104-70ea2a653c90)
 - Click on Application Load balancer
   ![image](https://github.com/user-attachments/assets/2ce23373-bc61-4aa9-bf64-208de2ac1b68)

   - Ensure it is internet facing
     ![image](https://github.com/user-attachments/assets/36e7fdd9-22d8-4c6f-927a-d7afb57bbd3b)

- Select your vpc
  ![image](https://github.com/user-attachments/assets/6d53405c-8db5-4e8e-af6c-b2be11f2ba1b)

  - Select created Target group
    ![image](https://github.com/user-attachments/assets/ade89b86-1b16-4e49-b1db-690bc2618a0e)

    - Create Load balancer
      ![image](https://github.com/user-attachments/assets/842d2f46-9252-47fa-a0ea-46f2cce738f7)

      - Load balancer has been created successfully
        ![image](https://github.com/user-attachments/assets/d7a7e8c3-6b17-49fb-b878-45281abd101e)


        ## Auto Scaling Group

        - Navigate to your search bar and enter Auto scaling and click on it
          ![image](https://github.com/user-attachments/assets/e5dcf198-d54f-4dfc-b0df-53e4702a428d)
       - Click on Create
         ![image](https://github.com/user-attachments/assets/96c390f6-ddcd-43f5-8427-97628c4cbc8d)
         - Enter the name and select your already created launch template
           ![image](https://github.com/user-attachments/assets/7d95c1ab-328c-4980-a420-ac229986f0f6)
           - Select your network settings
             ![image](https://github.com/user-attachments/assets/d02407d7-2fce-4273-8a1f-97d83c09d0c9)

             - Select the created Load Balancer
               ![image](https://github.com/user-attachments/assets/ae206e48-4a83-44cb-b7e3-514d8c986059)

               - Leave other settings as default and Create the Auto scaling group
                 ![image](https://github.com/user-attachments/assets/2f1ec5fd-7587-4c13-96ae-602a03e4a0b4)

                 - Auto scaling Group has been created
                   ![image](https://github.com/user-attachments/assets/a87924b2-d30a-41e3-b937-b14dd0cb3342)




   ## A FULLY DEPLOYED WORDPRESS SITE
   ![image](https://github.com/user-attachments/assets/81b8298c-a2ad-4e21-9ed2-ac44402256cd)
 




    









    









                  

 




                


          



































    


