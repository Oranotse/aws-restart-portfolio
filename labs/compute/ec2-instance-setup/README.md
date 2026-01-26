# EC2 Instance Setup Lab

## Overview
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.

Amazon EC2's simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon's proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.
## Objective
To provision a basic overview of launching, resizing, managing, and monitoring an Amazon EC2 instance.

## Key Concepts Covered
- Launch a web server with termination protection enabled
- Monitor Your EC2 instance
- Modify the security group that your web server is using to allow HTTP access
- Resize your Amazon EC2 instance to scale
- Test termination protection
- Terminate your EC2 instance Connecting to an EC2 instance

## Implementation Steps
## Task 1: Launching an EC2 Instance

In this task, I launched an Amazon EC2 instance with termination protection enabled to prevent accidental termination. I also used a User Data script to automatically deploy a simple web server during the instance startup process.
I accessed the AWS Management Console, navigated to the EC2 service, and used the EC2 Dashboard to launch a new instance. This step marked the beginning of setting up a scalable compute resource in the AWS cloud.
 
<img width="940" height="179" alt="image" src="https://github.com/user-attachments/assets/d2512b7f-effe-4baa-b5b3-e3b15d284165" />

 
<img width="940" height="474" alt="image" src="https://github.com/user-attachments/assets/a96385f5-1303-48ef-af56-1dc077fb1f08" />

 <img width="940" height="472" alt="image" src="https://github.com/user-attachments/assets/9f868dc1-d9c1-462e-bd51-efbe0e305acb" />


### Naming the EC2 Instance and Selecting an AMI

I named the EC2 instance **Web Server**, which created a key-value pair where the key is `Name` and the value is `Web Server`.
I then selected an Amazon Machine Image (AMI) for the instance. Under the Application and OS Images section, the default **Amazon Linux 2023** AMI was selected, and I kept this setting.

<img width="678" height="471" alt="image" src="https://github.com/user-attachments/assets/26169a7d-fbd2-4696-be86-d04291d49a03" />


### Choosing an Instance Type and Configuring a Key Pair

I selected the **t3.micro** instance type, which has 2 virtual CPUs and 1 GiB of memory.  
For the key pair, I chose **Proceed without a key pair**, as logging in to the instance was not required for this lab.

<img width="940" height="493" alt="image" src="https://github.com/user-attachments/assets/37dd1368-45d3-412c-b9c3-bcae759d3486" />

 
### Configuring Network Settings and Adding Storage

I selected the **Lab VPC** in the Network settings pane.  

I created a security group named **Web Server security group** with the description "Security group for my web server" and removed the SSH inbound rule.  

I kept the default storage configuration using an 8 GiB Amazon EBS root volume.
 
  <img width="940" height="653" alt="image" src="https://github.com/user-attachments/assets/7eb2b6f1-a806-4743-b13e-cc6a35e5e3e7" />

<img width="940" height="310" alt="image" src="https://github.com/user-attachments/assets/4887fbb5-365a-4d94-8194-b5b9c2d72436" />

### Configuring Advanced Details


I expanded the **Advanced details** pane and enabled **termination protection**.  

I also added a **User Data script** to automate setting up a web server on the instance.


 <img width="940" height="271" alt="image" src="https://github.com/user-attachments/assets/4e3bb6a7-107f-4c38-96fe-8fa74210988f" />
<img width="940" height="443" alt="image" src="https://github.com/user-attachments/assets/63ec87bb-98b6-4af6-9cc2-d803aebb111f" />



## Outcome
Successfully launched and accessed an EC2 instance, demonstrating foundational cloud compute knowledge.
