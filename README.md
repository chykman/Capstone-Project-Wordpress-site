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


## 4.3  Creating the Routes 
    - Navigate to the Route tables and click on create route table
   ![image](https://github.com/user-attachments/assets/45a15ee2-859a-40ba-9c6d-67621d7aa021)
   
  - Enter the required information and click on create , do same fot the public route table 
![image](https://github.com/user-attachments/assets/18c52949-edef-4fe0-88ab-1cb2b8dc2e61)

- After creating go to the subnet association section and edit association
  ![image](https://github.com/user-attachments/assets/a5c0c128-95c9-4966-875d-22057f9e7a10)

  ![image](https://github.com/user-attachments/assets/b5c3a4be-238a-4f7d-b94b-3902f57eeb8d)

  - Select the private subnets for the private routes and public sunets for public routes and then save
    
    ![image](https://github.com/user-attachments/assets/abc0c496-93cb-4354-a536-096b92d7c71c)

    ![image](https://github.com/user-attachments/assets/90972e6d-ccac-43de-a6d0-ada8bfbdf12c)


  ## 4.4.  INTERNET GATEWAY AND NAT GATEWAY

  - Navigate to the insternet gateway and click on Create Internet gateway
    ![image](https://github.com/user-attachments/assets/ff8d3ceb-9bc2-4bd4-9bd6-199f12644e9e)

    - Create your Internet gateway
      ![image](https://github.com/user-attachments/assets/9a994865-89a6-4f23-b351-74fbb6b3f70f)
      
  - We will now attach it to our Wordpress VPC , Click on Attach VPC
    ![image](https://github.com/user-attachments/assets/24b7f760-5f2a-4fd9-bb0d-d1dfed14cdd8)
 
 - Select your vpc and click on attach
    ![image](https://github.com/user-attachments/assets/226d076a-40fc-481a-b832-336cc459ce79)

   - Our Internet gateway is now attached to our wordpress VPC
     ![image](https://github.com/user-attachments/assets/5c78a4a0-674e-4710-9d1b-3076f14dfa1c)
     
 - Now that it is attached we go to our route table section and configure so as to access internet
   ![image](https://github.com/user-attachments/assets/36c4ed30-1756-40d7-9b8e-9ccdc47117d5)



 
    


      - Navigate to the Nat gateway and click on create Nat gateway on your private subnet
      ![image](https://github.com/user-attachments/assets/c2e20c52-dbfc-457e-9aaa-530d6c354ae9)

![image](https://github.com/user-attachments/assets/a01062a3-20d0-4adf-af96-f48546ea8528)

- Then navigate to the route section and click on edit route
  ![image](https://github.com/user-attachments/assets/4c069fad-a7d2-4b00-a5ff-95810ee5a7f2)

  - On the location , allow traffic on all CIDR ranges and select the Nat gateway you created as Target
    ![image](https://github.com/user-attachments/assets/b1f82283-0f17-45b7-a762-c7e5680bfa29)

    - Ensure your subnet associations are set to the private subnets
      ![image](https://github.com/user-attachments/assets/569abd60-27da-40be-8129-3e084bae87c7)























    


