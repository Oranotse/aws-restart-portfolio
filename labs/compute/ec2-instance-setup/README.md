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

### Launching the EC2 Instance

After configuring all instance settings, I launched the EC2 instance.  

I monitored the instance as it moved from **Pending** to **Running**, and confirmed that the **Status Checks** passed. I also reviewed the **Details**, **Security**, and **Networking** tabs to verify the instance configuration and confirm it was accessible.


<img width="1917" height="510" alt="image" src="https://github.com/user-attachments/assets/579159db-319a-4a8a-90bc-7c3974d203f7" />
<img width="1919" height="530" alt="image" src="https://github.com/user-attachments/assets/233ac07a-9412-44ea-ac51-ef18d1d75590" />
<img width="1918" height="866" alt="image" src="https://github.com/user-attachments/assets/c8c9c166-3e7f-4264-bcde-0b19aa25076c" />

## Task 2: Monitor Your EC2 Instance

Monitoring is an important part of maintaining the reliability, availability, and performance of EC2 instances and AWS solutions.  

I selected my EC2 instance and navigated to the **Status Checks** tab at the bottom of the screen. Here, I confirmed that both the **System reachability** and **Instance reachability** checks had passed, indicating that the instance was running without hardware or software issues.  

Next, I went to the **Monitoring** tab, which displays Amazon CloudWatch metrics for the instance. Since the instance was recently launched, only a few metrics were available. I explored the graphs to see an expanded view of the instance's performance. By default, basic five-minute monitoring is enabled, but detailed one-minute monitoring can also be enabled for more granular insights.  

I then used the **Actions > Monitor and troubleshoot > Get Instance Screenshot** option to view what the instance console would look like if a screen were attached. This allowed me to visually verify the status of the instance without needing SSH or RDP access. After reviewing the screenshot, I selected **Cancel** to close the view.  

Through these steps, I explored several ways to monitor my EC2 instance, including status checks, CloudWatch metrics, and instance screenshots, ensuring I could track its performance and troubleshoot if necessary.

<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/58f8b2b8-a34e-4c3c-b3ca-7f3d8e1c31ec" />
<img width="1919" height="863" alt="image" src="https://github.com/user-attachments/assets/1714989d-ea9c-4480-99ed-49f5117704f1" />
<img width="1912" height="721" alt="image" src="https://github.com/user-attachments/assets/696764f7-615e-4958-a625-02f4e32f6f3a" />
<img width="842" height="883" alt="image" src="https://github.com/user-attachments/assets/6fea46bd-8614-438e-8943-31aa93273f34" />




## Task 3: Update Your Security Group and Access the Web Server

I updated the **Web Server security group** to allow inbound HTTP traffic.  

In the **Inbound rules** tab, I added a rule with the following settings:

- **Type:** HTTP  
- **Source:** Anywhere-IPv4  

I clicked **Save rules** to apply the changes.  

After returning to my web browser and refreshing the page, I was able to see the message:

**Hello From Your Web Server!**

This confirmed that I successfully permitted HTTP traffic into my EC2 instance and accessed the web server.

<img width="1641" height="401" alt="image" src="https://github.com/user-attachments/assets/a8a8e60f-8f2b-4d3f-aaac-9cbcd4ec9832" />
<img width="1390" height="171" alt="image" src="https://github.com/user-attachments/assets/119a78e7-92c8-4b22-a62f-1f4ecd11b7ae" />
<img width="289" height="814" alt="image" src="https://github.com/user-attachments/assets/8f2ea6a5-a37e-4a79-9f22-e643129db7c3" />
<img width="1919" height="870" alt="image" src="https://github.com/user-attachments/assets/3e6ea489-a370-459b-82e5-edf3545dbd00" />
<img width="1891" height="555" alt="image" src="https://github.com/user-attachments/assets/2fdfda32-343c-4a6f-8e36-28c1147a955e" />
<img width="1614" height="450" alt="image" src="https://github.com/user-attachments/assets/efb86df6-df23-43ad-89fc-579016f5ca68" />
<img width="1917" height="259" alt="image" src="https://github.com/user-attachments/assets/d768b1db-ac6c-4cf7-aca5-6fd2f4e1a0a5" />



## Outcome
Successfully launched and accessed an EC2 instance, demonstrating foundational cloud compute knowledge.
