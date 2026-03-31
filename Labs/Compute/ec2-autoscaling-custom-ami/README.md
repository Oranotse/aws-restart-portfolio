# EC2 Auto Scaling Lab — Creating a Custom AMI

## Overview

In this lab, the AWS Command Line Interface (AWS CLI) was used from a 
pre-provisioned Command Host EC2 instance to launch a new web server 
instance and create a custom AMI from it. This AMI will later serve as 
the launch template source for an Auto Scaling group.

## Objective

Demonstrate how to create a custom AMI using the AWS CLI

## Key Concepts Covered

- Connect to an EC2 instance using EC2 Instance Connect
- Configure the AWS CLI with region and output settings
- Launch a new EC2 instance using a UserData bootstrap script
- Verify a web server deployment via public DNS
- Create a custom AMI from a running EC2 instance

---

## Implementation Steps

### Task 1.1 — Connect to the Command Host Instance

Navigated to **EC2 > Instances** in the AWS Management Console. The 
**Command Host** instance was already in a **Running** state with all 
status checks passed in the `us-west-2a` Availability Zone.

<img width="1919" height="959" alt="Screenshot 2026-03-31 204254" src="https://github.com/user-attachments/assets/b2ebc221-e762-49f0-9de7-6d6611e7bc09" />
<img width="1913" height="954" alt="Screenshot 2026-03-31 204309" src="https://github.com/user-attachments/assets/f353fffd-697d-41a5-ba06-b1a634957e6f" />



Selected the **Command Host** instance and chose **Connect**. On the 
**EC2 Instance Connect** tab, the default username `ec2-user` was 
confirmed and **Connect** was selected to open a browser-based 
terminal session.





