# Section 6: EC2 Instance Storage Section #

## What is EBS Volume? ##
* An EBS (Elastic Block Store) **volume** is a **network** drive you can attach to your instances while they run
* It allows your instances to persist data, even after their termination
* **They can only be mounted to one instance at a time** (at the CCP level)
* They are bound to a **specific availability zone**
* **Analogy**: Think of them as a "network USB stick"
* Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month

## EBS Volume ##

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

To be continued......




  


