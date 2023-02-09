# Section 4: IAM & AWS CLI #

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
    * Sid: an identifier for the statement (optional)
    * Effect: whether the statement allows or denies access (Allow, Deny)
    * Principal: account/user/role to which this policy allows or denies
    * Action: list of action this policy allows or denies
    * Resource: list of resources to which the actions are applied to
    * Condition: conditions for when this policy is in effect (optional)

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

to be continued tomorrow.....




























