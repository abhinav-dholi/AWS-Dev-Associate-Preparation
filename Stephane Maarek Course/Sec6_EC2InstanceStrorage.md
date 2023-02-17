# Section 6: EC2 Instance Storage Section #

## What is EBS Volume? ##
* An EBS (Elastic Block Store) **volume** is a **network** drive you can attach to your instances while they run
* It allows your instances to persist data, even after their termination
* **They can only be mounted to one instance at a time** (at the CCP level)
* They are bound to a **specific availability zone**
* **Analogy**: Think of them as a "network USB stick"
* Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month

# EBS Volume #

* It's a network drive (i.e. not a physical drive)
  * It uses the network to communicate the instance, which means there might be a bit of **latency**
  * It can be detached from an EC2 instance and attached to another one quickly

* It is locked to an Avaialibility Zone (AZ)
  * An EBS Volume in us-east-l a cannot be attached to us-east-l b
  * To move a volume across, you need to first snapshot it

* Have a provisioned capacity (size in GBs, and IOPS)
  * You get billed for all the provisioned capacity
  * You can increase the capacity of the drive over time

## EBS Volume - Example ##

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_1.png"  width="80%" height="40%">

## EBS - Delete on termination attribute ##
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_2.png"  width="80%" height="40%">

* Controls the EBS behaviour when an EC2 instance terminates
  * By default, the root EBS volume is deleted (attribute enabled)
  * By default, any other attached EBS volume is not deleted (attribute disabled)

* This can be controlled by AWS Console / AWS CLI
* **Use Case: preserve root volume when instance is terminated**

## EBS Hands on ##

* Step 1: Go to EC2 dashboard and click on Volumes
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_3.png"  width="80%" height="40%">

* Step 2: Create a new volume
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_4.png"  width="80%" height="40%">

* Step 3: Click on the created volume in the volume dashboard and attach it to an instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_5.png"  width="80%" height="40%">

* Step 4: Check on the instance page, we have 2 volume attached to it
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_6.png"  width="80%" height="40%">

* Step 5: The first volume has delete on termination attribute so if I terminate the instance the first volume is going to get deletd and the second one will stay available
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_7.png"  width="80%" height="40%">


## EBS Snapshots ##

* Make a backup (snapshot) of your EBS volume at a point in time
* Not necessary to detach volume to do a snapshot, but recommended
* Can copy snapshots across AZ or Region
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_8.png"  width="80%" height="40%">

## EBS Snapshot Features ##

* **EBS Snapshot Archive**
  * Move a Snapshot to an "archive tier" that is 75% cheaper
  * Takes within 24 to 74hrs for restoring the archive

* **Recycling Bin**
  * Setup rules to retain deleted snapshots so you can recover them after an accidental deletion
  * Specify retention (from 1 day to 1 year)

* **Fast Snapshot Restore (FSR)**
  * Force full initialization of snnapshot to have no latency on the first use ($$$)


## EBS Snapshots - Hands on ##

* Step 1: Go to the volumes dashboard and click on create a snapshot
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_9.png"  width="80%" height="40%">

* Step 2: Give description and create a snapshot
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_10.png"  width="80%" height="40%">

* Step 3: We can copy snapshot into different regions and also create a volume from it in different region
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebs_11.png"  width="80%" height="40%">

Also try working with the recycling bin

## AMI Overview ##

* AMI = Amazon Machine Image
* AMI are **customization** of an EC2 instance
  * You add your own software, configuration, operating system, monitoring...
  * Faster boot/configurtion time because all your software is pre-packed
* AMI are built in **specific region** (and can be copied across regions)
* You can launch EC2 instances from:
  * **A public AMI:** AWS provided
  * **Your own AMI:** you can make and maintain yourself
  * **An AWS Marketplace AMI:** an AMI someone else made (and potentially sells)

## AMI Process (from an EC2 instance) ##

* Start an EC2 instance and customize it
* Stop the instance (for data integrity)
* Build an AMI - this will also create EBS snapshots
* Launch instances from other AMIs

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_1.png"  width="80%" height="40%">

## AMI - Hands on ##

* Step 1: Launch an instance select existing security group and add user data like done previously without the last line
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_2.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_3.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_4.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_5.png"  width="80%" height="40%">

* Step 2: Go to the test page of the instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_6.png"  width="80%" height="40%">

* Step 3: Right click on the instance and create and image
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_7.png"  width="80%" height="40%">

* Step 4: Give name and click on create an image
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_8.png"  width="80%" height="40%">

* Step 5: Go to AMI dashboard notice if the AMI has been created or not
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_9.png"  width="80%" height="40%">

* Step 6: Go to the instance page and launch instance from AMI
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_10.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_11.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_12.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_13.png"  width="80%" height="40%">

* Step 7: Click on the instance link
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_14.png"  width="80%" height="40%">

* Step 8: We have the instance from the AMI running and we can view it from by going to the ip address
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ami_15.png"  width="80%" height="40%">


## EC2 Instance Store ##

* EBS volumes are **network drives** with good but "limited" performance
* If you need a high-performance hardware disk, use EC2 Instance Store
* Bettor I/O Performance 
* EC2 Instance Store lose their storage if they're stopped (ephemeral)
* Good for buffer / cache / scratch data / temporary content
* Risk of data loss if hardware fails
* Backups and Replication is your responsibility

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ins_store_1.png"  width="80%" height="40%">

## EBS Volume Types ##

* EBS Volumes come in 6 types
  * gp2 / gp3 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
  * io1 / io2  (SSD): Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads
  * st 1 (HDD): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
  * sc 1 (HDD): Lowest cost HDD volume designed for less frequently accessed workloads

* EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops Per Sec)
* When in doubt consult AWS documentation - it's good!
* Only gp2 / gp3 and io1 / io2 can be used as boot volumes

# EBS Volume Types Use Cases #

## General Purpose SSD ##

* Cost effective storage, low-latency
* System-boot volumes, Virtual Desktops, Development and test environments
* 1 Gib - 16 Tib
* gp3:
  * Baseline of 3000 IOPS and throughput of 125 MiB/s
  * Can increase IOPS up to 16000 and throughput up to 1000 MiB/s independently
* gp2:
  * Small gp2 volumes can burst IOPS to 3000
  * Size of the volume and IOPS are linked, max IOPS is 16000
  * 3 IOPS per GB, means at 5334 GB we are at the max IOPS

## Provisioned IOPS (PIOPS) SSD ##

* Critical business applications with sustained IOPS performance 
* Or applications that need more than 16000 IOPS 
* Great for **databases workloads** (sensitive to storage performance and consistency)
* io1/io2 (4 GiB - 16 TiB):
  * Max PIOPS: 64000 for Nitro EC2 instances & 32000 for other
  * Can increase PIOPS independently from storage size
  * io2 have more durability and more IOPS per GiB (at the same price as io1)
* io2 Block Express (4 GiB - 64 TiB):
  * Sub-millisecond latency
  * Max PIOPS: 256000 with an IOPS:GiB ratio of 1000:1
* Supports EBS Multi-attach

## Hard Disk Drives (HDD) ##

* Cannot be a boot volume 
* 125 GiB to 16 TiB
* Throughput Optimized HDD (st1)
  * Big Data, Data Warehouses, log processing 
  * **Max Throughput:** 500 MiB/s - max IOPS 500
* Cold HDD (sc1):
  * For data that is infrequently accessed 
  * Scenarios where lowest cost is important 
  * **Max Throughput:** 250 MiB/s - max IOPS 250

## EBS Volume Types Summary ##

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ins_store_2.png"  width="80%" height="40%">

# EBS Multi-Attach - io1/io2 family #

* Attach the same EBS volume to multiple EC2 instances in the same AZ
* Each instance has full read & write permissions to the high-performance volume
* **Use Cases:**
  * Achieve **higher application availablity** in clustered Linux applications (ex: Teradata)
  * Applications must manage concurrent write operations
* **Up to 16 EC2 instances at a time**
* Must use a file system that's cluster-aware (not XFS, EX4, etc....)

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/multiatt_1.png"  width="80%" height="40%">

# Amazon EFS - Elastic File System #

* Managed NFS (network file system) that can be mounted on many EC2
* EFS works with EC2 instances in a multi-AZ
* Highly available, scalable, expensive (3x gp2), pay per use
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_1.png"  width="80%" height="40%">

* Use cases: content management, web serving, data sharing, Workpress
* Uses NFSv4.1 protocol
* Uses security group to control access to EFS 
* **Compatible with Linux based AMI (Not Windows)**
* Encryption at rest using KMS
* POSIX file system (~ Linux) that is standard API
* File system scales automatically, pay-per-use, no capacity planning

## EFS - Performance and Storage Classes ##

* EFS Scale 
  * 1000s of concurrent NFS clients, 10 GB+/s throughput
  * Grow to Pentabyte-scale network file system, automatically
* Performance Mode (set an EFS creation time)
  * General purpose (default): latency-sensitive use case (web server, CMS, etc)
  * Max I/O: High latency, throughput, highly parallel (big data, media processing)
* Throughput Mode:
  * Bursting: 1TB = 50 MiB/s + burst of up to 100 MiB/s
  * Provsisioned: set your throughput regardless of storage size, ex: 1 GiB/s for 1 TB storage 
  * Elastic: automatically scales throughput up or down based on your workloads
    * Up to 3 GiB/s for reads and 1 GiB/s for writes
    * used for unpredictable workloads 

## EFS - Storage Classes ##

* Storage Tiers (lifecycle management feature - move file after N days)
  * Standard: for frequently accessed files
  * Infrequent access (EFS-IA): cost to retrieve files, lower price to store. Enable EFS-IA with a Lifecycle Policy
* Availaility and Durability
  * Standard: Multi-AZ, great for prod
  * One Zone: One AZ, great for dev, backup enabled by default, compatible with IA (EFS One Zone - IA)
* Over 90% in cost savings

## Amazon EFS - Hands on ##

* Step 1: Go to EFS management console and create file system and go to customize (keep everything as default)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_2.png"  width="80%" height="40%">

* Step 2: First create a security group from the EC2 Console
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_3.png"  width="80%" height="40%">

* Step 3: In network access settings add the security group we created then go next
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_4.png"  width="80%" height="40%">

* Step 4: Skip file system policy and review and create
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_5.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_6.png"  width="80%" height="40%">

* Step 5: create a new instance and mount this to an EC2 Instance
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_7.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_8.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_9.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_10.png"  width="80%" height="40%">

* Step 6: Create a second instance with different AZ and mount to EFS we created
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_11.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_12.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_13.png"  width="80%" height="40%">

* Step 7: Connect both EC2 instance using instance connect
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_14.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/efs_15.png"  width="80%" height="40%">

## EFS vs EBS - Elastic Block Storage ##

* EBS Volumes:
  * one instance (except multi-attach io1/io2)
  * are locked at the Availability Zone (AZ) level
  * gp2: IO increases if the disk size increases 
  * io1: can increase IO independantly
* To migrate an EBS volume across AZ 
  * Take a snapshot 
  * Restore the snapshot to another AZ
  * EBS backups use IO and you shouldn't run them while your application is handling a lot of traffic
* Root EBS Volumes of instances get terminated by default if the EC2 instance gets terminated. (you can disable it)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebsvsefs_1.png" width="80%" height="40%">

## EBS vs EFS - Elastic File System ##

* Mounting 100s of instances accross AZ
* EFS shares website files (WordPress)
* Only for Linux Instances (POSIX)
* EFS has a higher price point than EFS
* Can leverage EFS-IA for cost savings 
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ebsvsefs_2.png" width="80%" height="40%">


# Quiz 3 Solutions #

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_1.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_2.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_3.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_4.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_5.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_6.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_7.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_8.png"  width="80%" height="40%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q3_9.png"  width="80%" height="40%">








  
