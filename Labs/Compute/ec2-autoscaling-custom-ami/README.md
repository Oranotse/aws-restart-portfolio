# EC2 Auto Scaling Lab: Creating a Custom AMI

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

## Implementation Steps

### Task 1.1 Connect to the Command Host Instance

Navigated to **EC2 > Instances** in the AWS Management Console. The 
**Command Host** instance was already in a **Running** state with all 
status checks passed in the `us-west-2a` Availability Zone.

Selected the **Command Host** instance and chose **Connect**. On the 
**EC2 Instance Connect** tab, the default username `ec2-user` was 
confirmed and **Connect** was selected to open a browser-based 
terminal session.


<img width="1919" height="959" alt="Screenshot 2026-03-31 204254" src="https://github.com/user-attachments/assets/b2ebc221-e762-49f0-9de7-6d6611e7bc09" />
<img width="1913" height="954" alt="Screenshot 2026-03-31 204309" src="https://github.com/user-attachments/assets/f353fffd-697d-41a5-ba06-b1a634957e6f" />




### Task 1.2 — Configure the AWS CLI

I confirmed the instance region by running this command:

"curl http://169.254.169.254/latest/dynamic/instance-identity/document | grep region"

This returned **`us-west-2`**. I then ran `aws configure`, pressed Enter
for the Access Key ID and Secret Access Key since the instance uses an
IAM role, set the region to `us-west-2`, and the output format to `json`.

I then navigated to the working directory:
"cd /home/ec2-user/"
<img width="1918" height="760" alt="Screenshot 2026-03-31 212750" src="https://github.com/user-attachments/assets/f6fd3fdc-4bde-4ff6-99fd-636bbf4cc62c" />

### Task 1.3 — Launch a New EC2 Instance

I inspected the `UserData.txt` script by running:
more UserData.txt


The script updates installed software and installs **Apache**, **PHP**,
and a **stress tool** to simulate high CPU load. The final lines erase
shell history and SSH keys to ensure no sensitive data is left on the
instance before the AMI is captured.

<img width="1919" height="765" alt="Screenshot 2026-03-31 212759" src="https://github.com/user-attachments/assets/150ad13b-ae11-4120-a355-8c296ced9f70" />

I copied the **KEYNAME**, **AMIID**, **HTTPACCESS**, and **SUBNETID**
values from the lab credentials panel and ran the `aws ec2 run-instances`
command to launch a new `t3.micro` instance.

The command returned Instance ID: `i-0585d2d22e62d748a`.

I then ran the `aws ec2 run-instances` command to launch a new `t3.micro` instance
tagged as **WebServer**, which returned the Instance ID `i-0585d2d22e62d748a`.
I then ran `aws ec2 wait instance-running` to wait until the instance was fully running.

Once the instance was ready, I ran `aws ec2 describe-instances` to retrieve
its public DNS name: `ec2-44-243-239-25.us-west-2.compute.amazonaws.com`.

<img width="1913" height="241" alt="Screenshot 2026-03-31 220315" src="https://github.com/user-attachments/assets/563123b9-67d3-47fb-a53e-bcde11e3ae23" />












