# 3D E-Commerce Platform Architecture on AWS 🛍️

## Overview

This was a project I did as part of my AWS re/Start training. The task was to design a cloud architecture for a 3D e-commerce platform where users can interact with 3D product models before purchasing. The platform had to support millions of global users and meet five key requirements which were high availability, scalability, performance, security, and cost optimization.

## Architecture Diagram

<img width="812" height="1141" alt="Architecture Diagram drawio" src="https://github.com/user-attachments/assets/8b429990-85ef-4663-a153-6ca4f95d321a" />



## AWS Services Used and Why ☁️

- **Route 53** - Used for DNS and health checks, it directs users to healthy endpoints and automatically reroutes traffic when something fails
- **Amazon CloudFront** - A CDN that caches 3D assets and static content at edge locations closer to users, which makes the platform load faster no matter where the user is
- **Elastic Load Balancer** - Distributes incoming traffic evenly across EC2 instances in both Availability Zones so no single server gets overwhelmed
- **EC2 with Auto Scaling** - The actual servers running the application, grouped under an Auto Scaling group so they scale up or down based on how much traffic is coming in
- **Amazon RDS (Multi-AZ)** - Stores all the structured data like products, orders, and accounts, with a standby database in a second Availability Zone that takes over automatically if the primary one fails
- **Amazon S3** - Stores all the 3D model files, images, and static content, and acts as the origin that CloudFront pulls from. As a managed AWS service it sits outside the VPC and is accessed over the internet
- **Amazon CloudWatch** - Monitors everything inside the architecture including EC2, RDS, and the ALB, and triggers alarms that tell the Auto Scaling group when to add or remove instances. It is a managed service that operates outside the VPC
- **AWS Trusted Advisor** - Gives recommendations on how to improve cost, security, and performance across the whole environment. Like CloudWatch and S3 it is a managed AWS service that operates outside the VPC
- **VPC with Public and Private Subnets** - The load balancer sits in the public subnet facing the internet, while EC2 and RDS are in private subnets so they are never directly exposed


## How It Meets the Requirements ✅

- **High Availability** - Running EC2 across two Availability Zones, having a Multi-AZ RDS setup, and using Route 53 health checks means the platform stays up even if one zone goes down
- **Scalability** - Auto Scaling handles sudden traffic spikes without any manual work, and CloudFront with S3 scale on their own
- **Performance** - CloudFront brings 3D assets closer to users globally, and the load balancer makes sure requests are spread evenly so no server slows down
- **Security** - EC2 and RDS are in private subnets so they cannot be reached directly from the internet, security groups control what traffic is allowed, and Trusted Advisor flags anything that looks risky
- **Cost Optimization** - Auto Scaling means you are not paying for servers you do not need, CloudFront reduces how much work EC2 has to do, and Trusted Advisor helps spot where money is being wasted

## Trade-offs and Challenges

Multi-AZ RDS costs more than a single instance setup but it was worth it for the availability guarantee. Setting up public and private subnets also added some complexity to the design but it was important to show that security was taken seriously and not just an afterthought.
```
