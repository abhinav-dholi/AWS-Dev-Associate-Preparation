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

* Step 6: Login with the user created















