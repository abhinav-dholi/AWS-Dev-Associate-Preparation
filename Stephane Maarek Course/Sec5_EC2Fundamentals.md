# Section 5: EC2 Fundamentals #

## AWS Budget Setup - Hands on ##

* Step 1: Change IAM Bill Access setting to make it visible to the users with admin access in root user
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/bill1.png"  width="50%" height="25%">

* Step 2: Go to budgets tab in billing dashboard and create budget
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/create_budget.png"  width="50%" height="25%">

* Step 3: Create a zero spend budget 
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/budget_created.png"  width="50%" height="25%">

* Step 4: Create a monthly bill budget
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/budget_created_2.png"  width="50%" height="25%">


# EC2 Basics #

## Amazon EC2 ##

* EC2 is one of the most popular of AWS's offering
* EC2 = Elastic Compute Cloud = Infrastructure as a Service
* It mainly composed of:
  * Renting virtual machines (EC2)
  * Storing data on virtual drives (EBS)
  * Distributing load accross machines (ELB)
  * Scaling the services in an auto scaling group (ASG)
* Knowing EC2 is fundamental to understand how the cloud works

## EC2 Sizing & Configuring Options ##

* Operating system **(OS)**: Linux, Windows and Mac OS
* How much compute power and cores (CPU)
* How much random-access memory (RAM)
* How much storage space:
  * Network attached (EBS & EFS)
  * Hardware (EC2 Instance store)
* Network card: speed of the card, Public IP address
* Firewall rules: Security group
* Bootstrap Script (Configure at first launch): EC2 User data

## EC2 User Data ##

* It is possible to bootstrap our instances using **EC2 User data** script
* **bootstrapping** means launching commands when a machine starts
* That script is **only run once** at the instance first start
* EC2 user data is used to automate boot tasks such as:
  * Installing updates
  * installing software
  * Downloading common files from the internet 
  * Anything you can think of
* EC2 User Data Script runs on a root user

## EC2 instance types: example ##

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/instancetype.png"  width="80%" height="40%">

* For this course we will be using t2.micro

# EC2 Hands on: Launching an EC2 Instance running Linux #

* We'll be launching our first virtual server using AWS Console
* We'll get a first high level approach to the various parameters
* We'll see that our web server is launched using EC2 user data
* We'll learn how to start/stop/terminate an instance

## Hand on ##

* Step 1: Go into the EC2 console->instances->launch instances
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_1.png"  width="80%" height="40%">

* Step 2: Add in the Name of the instance and choose the base instance as Amazon Linux, set the instance type
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_2.png"  width="80%" height="40%">

* Step 3: Create a new key pair
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_3.png"  width="80%" height="40%">

* Step 4: Set up network settings
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_4.png"  width="80%" height="40%">

* Step 5: Set up storage settings
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_5.png"  width="80%" height="40%">

* Step 6: Go to the advance settings and add the code to the User data - optional (This runs only the first time we launch the instance)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_6.png"  width="80%" height="40%">

* Step 7: Launch the instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_7.png"  width="80%" height="40%">

* Step 8: View instances
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_8.png"  width="80%" height="40%">

* Step 9: Open the public ipv4 address
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_9.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_10.png"  width="80%" height="40%">

Note: After everytime you restart an instance, the public ip will change

## EC2 Instance Types - Overview ##

* You can use different types of EC2 instances that are optimised for different use cases (https://aws.amazon.com/ec2/instance-types/)
* AWS has the following naming convention: For ex: m5.2xlarge
  * m: instance class
  * 5: generation
  * 2xlarge: size within the instance class 

# EC2 Instance Types #

## General Purpose ##

* Great for diversity of workloads such as web servers or code repositories 
* Balance between:
  * Compute
  * Memory
  * Storage
* In the course we are using the **t2.micro** which is a general purpose ec2 instance 
  
## Compute Optimized ##

* Great for compute-intensive tasks that require high performance processors:
  * Batch processing 
  * Media Transcoding 
  * High performance web servers
  * High performance conputing (HPC)
  * Scientific modelling & machine learning
  * Dedicated gaming servers

## Memory Optimised ##

* Fast performance for workloads that process large data sets in memory
* Use cases:
  * High performance, relational/non-relational databases
  * Distributed web scale cache stores
  * In-memory databases optimised for BI(Business Intelligence)
  * Applications performing real-time processing of bug unstructured data

## Storage Optimized Instances ##

* Great for storage-intensive tasks that require high, sequential read and write access to data sets on local storage
* Use cases:
  * High frequency online transaction (OLTP) systems
  * Relational and NoSQL databases 
  * Cache for in-memory databases (for example: Redis)
  * Data warehousing applications
  * Distributed file systems

## EC2 Instance Types Examples ##

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ec2_11.png"  width="80%" height="40%">

# Introduction to Security Groups #

* Security groups are fundamental of network security in AWS
* They control how traffic is allowed into or out of our EC2 instances
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/secgrp_1.png"  width="80%" height="40%">

* Security groups only contain **allow** rules
* Security groups rule can reference by IP or by security group

## Security Groups in Detail ##

* Security groups are acting as a "Firewall" on EC2 instances
* They regulate:
  * Access to ports 
  * Authorise IP ranges - IPV4 & IPV6
  * Control of inbound network (from other side to instance)
  * Control of outbound network (from the instance to other)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/secgrp_2.png"  width="80%" height="40%">

## Security Groups - Important points ##

* Can be attached to multiple instances 
* Locked down to a region/VPC combination
* Does live "outside" the EC2 - if traffic is blocked the EC2 instance won't see it
* It's good to maintain one separate security group for SSH access
* If your application is not accessible (time out), then its a security group issue
* If your application gives a "connection refused" error, then it's an application error or it's not launched
* All inbound traffic is blocked by default
* All outbound traffic is authorised by default

## Referencing other security groups ##
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/secgrp_3.png"  width="80%" height="40%">

## Important ports to know ##

* 22 = SSH (Secure Shell) - log into Linux instance
* 21 = FTP (File Transfer Protocol) - upload files to a file share
* 22 = SFTP (Secure File Transfer Protocol) - upload files using SSH
* 80 = HTTP - access unsecured websites
* 443 = HTTPS - access secured websites
* 3389 = RDP (Remote Desktop Protocol) - log into a Windows instance

## Security Groups Hands on ##

* Step 1: Go to the EC2 dashboard and click on Networks and Security -> Security Groups
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/secgrp_4.png"  width="80%" height="40%">

* Step 2: Check edit inbound rules where we can change the port access for our EC2 instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/secgrp_5.png"  width="80%" height="40%">

## SSH Hands on ##

* Step 1: open power shell at the location you have your .pem file
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ssh_1.png"  width="80%" height="40%">

* Step 2: write the command to connect to the instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ssh_2.png"  width="80%" height="40%">



















  