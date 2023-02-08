# Section 3: Getting Started with AWS #

## AWS Cloud Use Cases ##

* AWS enables to build sophisticated, scalable applications
* Applicable to a diverse set of industries
* Use cases include
    * Enterprise IT, Backup & Storage, Big Data Analytics
    * Web hosting, Mobile & Social Apps 
    * Gaming

## AWS Global Infrastructure ##

* AWS Regions - All around the world
* AWS Avaialability Zones
* AWS Data Centers
* AWS Edge Locations / Points of Presence

## AWS Regions ##

* A region is a *cluster of data centers*
* Most AWS Services are region scoped

![alt text](https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/regions.png)

### How to choose an AWS Region? ###

* **Compliance** with data governance and legal requirements: data never leaves without your explicit permission. For ex: If the govt want the data to be local to your country then you'll launch your application in the region where you want your data to stay.

* **Proximity** to customers: If users in India then deploy app in India to reduce latency

* **Available Services** within a region: every service is not available in every region

* **Pricing**: It varies region to region

## AWS Availablility Zones ##

* Each region has minimum 3 or maximum 6 availability zones
* Each availability zone (AZ) is one or more discrete data centers with redundant power, networking and connectivity
* They're separated from each other so that they're isolated from the disasters
* All of them are connected through high bandwidth, ultra low latency networking hence creating a **REGION**

![alt text](https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/AZ.png)

### AWS Global Services Examples ###

* IAM (Identity and Access Management)
* Route 53 (DNS Service)
* CloudFront (Content Delivery Network)
* WAF (Web Application Firewall)

### AWS Region Based Service Examples (most services are region-based) ###

* Amazon EC2 (Infrastructure as a Service)
* Elastic Beanstalk (Platform as a Service)
* Lambda (Function as a Service)
* Rekognition (Software as a Service)

## Demonstation ##

* Important links:
    * https://ap-south-1.console.aws.amazon.com/console/home?region=ap-south-1
    * https://aws.amazon.com/about-aws/global-infrastructure/
    * https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/?p=ngi&loc=4&refid=14a4002d-4936-4343-8211-b5a150ca592b

