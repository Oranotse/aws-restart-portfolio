# Highly Available Web Applications 🌐

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked on making a web application highly available by using an Application Load Balancer (ALB), an Auto Scaling group, and multiple Availability Zones. According to AWS, Amazon EC2 Auto Scaling) helps you maintain application availability and lets you automatically add or remove EC2 instances according to conditions you define. The starting point of this lab was reviewing the existing **TravelAgencyWebServers** Auto Scaling group, which was only running one EC2 instance in a single Availability Zone and had no load balancer attached to it yet.

## Setting Up the Target Group and Load Balancer

Before creating the load balancer, I first created a **Target Group** called `TravelAgencyWebServer-TG`. A target group is what the load balancer uses to route requests to the right EC2 instances. I configured it to use the `TravelAgencyVpc` and set it to target instances. After that, I created an **Application Load Balancer** called `TravelAgencyServers-ALB`, set it to be internet-facing, and spread it across three Availability Zones (`us-east-1a`, `us-east-1b`, and `us-east-1c`) using their public subnets. I then configured the listener to forward traffic to the target group I just created. Once the load balancer was ready, I went back to the Auto Scaling group and attached it to the `TravelAgencyWebServer-TG` target group under the Integrations tab.

## Configuring Security Groups

This was an important part of the lab because security groups control what traffic is allowed in and out of your resources. I created a new security group called **TravelAgencyLoadBalancer** and configured it to allow inbound HTTP traffic from `0.0.0.0/0`, meaning anyone on the internet can reach the load balancer. For the outbound rule, I restricted it to only send traffic to the **TravelAgencyWebServer** security group, so traffic could only flow to the actual web server instances. I then edited the **TravelAgencyWebServer** security group to only accept inbound traffic from the **TravelAgencyLoadBalancer** security group, removing the previous `0.0.0.0/0` rule. This setup means users can only reach the EC2 instances through the load balancer, which is a much more secure architecture. Finally, I assigned the **TravelAgencyLoadBalancer** security group to the ALB and confirmed the application was accessible using the ALB's DNS name in the browser with **http://**.

## Configuring Health Checks and Testing Auto Healing

I updated the target group's health check path to `/health` instead of the default root path, and tightened the settings so that instances would be marked unhealthy after just 10 seconds (2 checks at 5 second intervals) instead of the default 150 seconds. According to AWS, health checks allow the load balancer to monitor the health of registered targets and route traffic only to healthy ones. To test auto healing, I terminated the existing EC2 instance manually. Because this dropped the Auto Scaling group below its minimum capacity, it automatically launched a new instance in `PublicSubnet1`. I confirmed this by checking the new instance's subnet ID and refreshing the `/health` page, where I could see the instance ID had changed to the new one.

## Adding a Second Availability Zone and Scaling Out

To make the application truly highly available, I added `PublicSubnet2` to the Auto Scaling group so it now spanned two Availability Zones. I then increased the desired capacity from 1 to 2, which caused the Auto Scaling group to automatically launch a second EC2 instance and place it in `PublicSubnet2`. I verified this by checking the new instance's subnet ID under the Networking tab. Refreshing the `/health` page multiple times confirmed that the load balancer was distributing traffic across both instances, as the instance ID in the response kept changing. This showed that the application was now running across multiple Availability Zones with a load balancer sitting in front, making it resilient to failures in any single zone. 🎉
