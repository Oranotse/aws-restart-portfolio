# 🧠 SimuLearn: Databases in Practice (Amazon RDS)

## 📌 Overview
This SimuLearn activity focused on using **Amazon RDS** to reduce database administration overhead while improving availability and performance. The goal was to move away from manual database management and use AWS managed services to handle routine operational tasks.

This activity forms part of my **AWS Cloud Practitioner learning journey** and helped me understand how managed databases work in real-world cloud scenarios.


## 🎯 Solution Request
The task was to migrate a customer database to **Amazon RDS** in order to:
- Automate routine database administration tasks
- Improve database availability
- Increase performance for read-heavy workloads


## 🏗️ Solution Design (Learn Section)
In this SimuLearn, I worked with the following concepts:

- I used **Amazon RDS** to host a customer application database.
- Amazon RDS handled infrastructure provisioning, backups, snapshots, and maintenance automatically.
- High availability was achieved using **Multi-AZ deployment**, where data is synchronously replicated to a standby instance in a different Availability Zone.
- In the event of a failure, Amazon RDS automatically fails over to the standby instance without manual intervention.
- The database DNS name remains the same during failover, allowing applications to reconnect automatically.
- **Read replicas** were used to support read-heavy workloads by distributing read traffic across multiple database copies.

## 🛠️ DIY Task
### Goal
Create a **read replica** of an existing Amazon RDS database.
<img width="1919" height="915" alt="Screenshot 2026-02-09 114230" src="https://github.com/user-attachments/assets/d6bcf2ab-61eb-4f76-b783-8f75bd09e5e5" />

### Configuration
- **Primary Database:** my-database  
- **Read Replica Name:** my-database-read-replica  
- **Instance Type:** db.t3.xlarge  

This task demonstrated how read replicas can be used to improve performance and scalability for applications with high read demand.

---

## ✅ Validation Results
The DIY task was successfully validated by the SimuLearn test servers.

<img width="1918" height="973" alt="Screenshot 2026-02-09 113916" src="https://github.com/user-attachments/assets/760b44ed-de38-4d81-b062-8957cbc012d8" />


## 📜 Certificate of Completion
This section contains proof of completion for the SimuLearn activity.

<img width="941" height="728" alt="image" src="https://github.com/user-attachments/assets/fcab9668-e3d4-4d93-841e-c69066df06f4" />


## 📝 Reflection
This SimuLearn helped me better understand how **Amazon RDS**, **Multi-AZ deployments**, and **read replicas** work together to improve reliability and performance. It also reinforced the value of using managed AWS services to reduce operational complexity while maintaining high availability.
