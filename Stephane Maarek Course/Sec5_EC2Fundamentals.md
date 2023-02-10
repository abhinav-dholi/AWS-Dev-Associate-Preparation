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

## EC2 Hands on: Launching an EC2 Instance running Linux ##

to be continued from tomorrow...







  