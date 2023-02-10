# Section 4: IAM & AWS CLI #

# :pushpin: IAM Section Summary #

* **Users:** mapped to a physical user, has a password for AWS Console
* **Groups:** contains users only
* **Policies:** JSON document that outlines permissions for users and groups
* **Roles:** for EC2 instances or for AWS Services
* **Security:** MFA + Password Policy
* **Access Keys:** access AWS using CLI or SDK
* **Audit:** IAM Credential Reports & IAM Access Advisor

## IAM: Users & Groups ##

* IAM: Identity and Access Management, is a **Global** service
* Root account created by default, shouldn't be shared
* **Users** are people within the organisation, and can be _grouped_
* **Groups** only contain **users**, not other groups
* Users don't have to belong to a group, anyway they can be part of multiple groups

![alt text](https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/groups.png)

## IAM: Permissions ##

* Users and Groups can be json documents called **policies**
* These policies define **permissions** of the user
* In AWS you apply the **least privilege principal:** don't give more permissions than a user needs.
<!-- ![alt text](https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/policies.png) -->
Example: <img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/policies.png"  width="50%" height="15%">

## IAM: Users and Groups - Hands on ##

* Step 1: Go to IAM Dadhboard
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/IAM_Dashboard.png"  width="50%" height="25%">

* Step 2: Create a user (Users -> Add User)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user1.png"  width="50%" height="25%">

* Step 3: Add user into a group
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user2.png"  width="50%" height="25%">

* Step 4: Add Tags (Optional)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user3.png"  width="50%" height="25%">

* Step 5: Create and Download csv
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user4.png"  width="50%" height="25%">

* Group created (Further we can toggle around users and groups to see the information we set)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user5.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user6.png"  width="50%" height="25%">

* Step 6: Login with the user created by clicking on the url (mentioned in image below)
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user7.png"  width="50%" height="25%">

* Step 7: Click and open the link in an incognito tab
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/user8.png"  width="50%" height="25%">

## IAM: Policies inheritance ##
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/iam_policyinh.png"  width="50%" height="25%">

## IAM Policies Structure ##

* Consists of:
    * **Version:** policy language version, always include "2012-10-17"
    * **Id:** an identifier for the policy (optional)
    * **Statement:** one or more indvidual statements (required)

* **Statement** consists of:
    * **Sid:** an identifier for the statement (optional)
    * **Effect:** whether the statement allows or denies access (Allow, Deny)
    * **Principal:** account/user/role to which this policy allows or denies
    * **Action:** list of action this policy allows or denies
    * **Resource:** list of resources to which the actions are applied to
    * **Condition:** conditions for when this policy is in effect (optional)

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/polstruc.png"  width="60%" height="30%">


## IAM Multi Factor Authentication (MFA) ##

* To protect the root user account and IAM users
* MFA = password you know + security device you own
* MFA Devices:
    * Virtual MFA Device: Google Authenticator, Authy
    * Universal 2nd Factor (U2F) Security Key: Yubikey
    * Hardware Key Fob MFA Device: Gemalto
    * Hardware Key Fob MFA Device for AWS GovCloud (US): SurePassID

## How to access AWS? ##

* There are 3 options:
    * AWS Management Console (protected by password + MFA)
    * AWS Command Line Interface (CLI): protected by access keys
    * AWS Software Development Kit (SDK) - for code; protected by access keys

* Access keys are secret just like password (KeyID, Password)

## AWS CLI ##

* A tool that enables you to interact with AWS Services using command line in your command-line shell
* Direct access to the public api of AWS Services
* We can develop scripts to manage resources
* Opensource
* Alternative to AWS CLI

## AWS SDK ##

* AWS SDK is basically a set of libraries that can be used for development
* Enables you to access and manage AWS services programmically
* Embedded within your application
* Supports: SDKs (JS, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++), Mobile SDK (Android, IOS, etc), IoT Device SDK (Embedded C, Arduino, etc)

## AWS CLI Hands on ##

* Step 1: Create access key from the **IAM User account**
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/cli1.png"  width="50%" height="25%">

* Step 2: Configure aws cli on command prompt
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/cli2.png"  width="50%" height="25%">

* Step 3: Try the commands
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/cli3.png"  width="50%" height="25%">

## AWS Cloudshell ##

* Cloudshell is an alternative to terminal
* Terminal in cloud that is free to use
* All files created in the cloudshell environment they will stay
* We can download and upload the files from cloudshell 

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/cloudshell1.png"  width="50%" height="25%">

## IAM Roles for Services ##

* Some AWS services will need to perform actions on your behalf
* To do so, we will assign **permissions** to AWS services with **IAM Roles**
* Common roles:
  * EC2 Instance Roles
  * Lambda Function Roles
  * Roles for cloud formation

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/rolesAWS.png"  width="50%" height="25%">

## IAM Roles Hands on ##

* Step 1: Go to the user account and under IAM click on roles
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/roles1.png"  width="50%" height="25%">

* Step 2: Click on create roles and select a trusted entity type for **AWS Services** and use case as **EC2**
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/roles2.png"  width="50%" height="25%">

* Step 3: Set the permission as **IAM Read only Access** 
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/roles3.png"  width="50%" height="25%">

* Step 4: Set the role name and click on create role and you role is created
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/roles4.png"  width="50%" height="25%">

* The role looks like this
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/roles5.png"  width="50%" height="25%">

## IAM Security Tools ##

* **IAM Security report (account level)**
  * a report that lists all the account users and the status of various credentials
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/credentialrep.png"  width="50%" height="25%">

* **IAM Access Advisor (user level)**
  * Access advisor shows the service permissions granted to a user and when those services were last used
  * You can use this information to revise the policies
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/accessadvisor.png"  width="50%" height="25%">

## IAM Guidelines & Best Practices ##

* Don't use the root account excepts for AWS Account setup
* One physical user = One AWS user
* **Assign users to groups** and permissions to groups
* Create a **strong password policy**
* Use and enforce the **Multi Factor Authentication (MFA)**
* Create and use **Roles** for giving permissions in AWS services
* Use Access Keys for Programmatic access (CLI/SDK)
* Audit permissions of your account with the IAM Credentials Report
* **Never Share IAM Users and Access Keys**

# QUIZ 1 Solutions #

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_1.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_2.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_3.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_4.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_5.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_6.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_7.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_8.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_9.png"  width="50%" height="25%">
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/Q1_10.png"  width="50%" height="25%">