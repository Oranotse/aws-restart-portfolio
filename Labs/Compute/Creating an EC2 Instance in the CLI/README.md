# Creating an EC2 Instance in the CLI 💻

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I used the **AWS CLI** on a **Command Host** EC2 instance to launch a new web server instance and create a custom **AMI** based on it. According to AWS, an AMI is a template used to launch instances with the same configuration, which is the foundation of **Auto Scaling**.

## Connecting to the Command Host

I opened the **EC2 Management Console**, selected the **Command Host** instance, and clicked **Connect** using the **EC2 Instance Connect** tab. Once inside the terminal, I ran `aws configure` to set the correct region and output format, and navigated to `/home/ec2-user/` where the lab scripts were stored.

## Inspecting the UserData Script

I used the more UserData.txt command to view the startup script for the EC2 instance. This script runs automatically when the instance starts. It installs a PHP web application during the first boot. At the end, it clears shell history and removes authorized_keys files to make sure no sensitive information is left behind or saved in the image.

## Launching the Web Server Instance

I ran `aws ec2 run-instances` with the required parameters — key name, AMI ID, security group, and subnet — to launch a new **t3.micro** instance tagged as **WebServer**. The command returned an **InstanceId**, which I used in the next steps. I then ran `aws ec2 wait instance-running` to pause until the instance was fully ready before continuing.

## Verifying the Web Server

I used `aws ec2 describe-instances` with the `--query` flag to retrieve the **public DNS name** of the new instance. I pasted it into a browser and confirmed the PHP web application was running successfully. I waited about 5 minutes after launch since the UserData script takes time to finish in the background.

## Creating a Custom AMI

With the web server confirmed, I ran `aws ec2 create-image --name WebServerAMI --instance-id NEW-INSTANCE-ID` to capture the instance as a reusable image. AWS briefly restarts the instance before taking the snapshot to ensure the file system is consistent.

## What I Learned

This lab showed me how to build and capture a configured EC2 instance entirely through the CLI without touching the console. I learned how **UserData scripts** automate software installation at launch, how `aws ec2 wait` handles timing without guesswork, and why cleaning up credentials before creating an AMI is a security best practice. Most importantly, I now understand that a custom AMI is what makes **Auto Scaling** possible, it gives AWS a ready-made template to spin up new instances automatically.
