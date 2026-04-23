# Evaluating DevOps Tools 🛠️

## What This Lab Is About

In this lab, I worked with evaluating different **DevOps tools** that are used in modern software development and operations. According to AWS, the DevOps landscape is continuously changing as new products and technology come to market, so it is important to understand what tools are available and when to use them. The lab focused on researching a specific tool, identifying its use cases, and understanding why it is important in a DevOps pipeline.

## The Tool I Researched: AWS CodeDeploy

I chose to research **AWS CodeDeploy**, which falls under the category of **Build and Test Tools**. 

### What Does This Tool Do?

**AWS CodeDeploy** is an Amazon tool that automatically deploys your applications updates across multiple AWS services. It supports **Amazon EC2** for virtual servers, **AWS Lambda** for serverless code, and **Amazon ECS** for containerized applications, and can even reach your on-premises servers. Without it, teams would manually copy code onto servers one by one, which is slow and error-prone. CodeDeploy handles all of that automatically, keeping your application running smoothly with minimal downtime.

### Why Is This Tool Important?

Before AWS CodeDeploy, deployment of software was done manually, this meant that logging servers one by one, copying files, and hoping that nothing breaks. One mistake could take down the whole system and make businesses lose money. CodeDeploy solves this by making deployments fast, consistent, and automatic, so your teams spends less time worrying about releasing software and more time building it. In a world of constant updates, automated deployment is not optional, it is essential.

### Specific Use Cases

During my research, I identified several real-world use cases for **AWS CodeDeploy**:

1. **Automate Deployments to Remove Manual Operations**: Teams can set up automatic deployments so that whenever new code is ready, it gets pushed to production without anyone having to manually log into servers and copy files.

2. **Deploy to Many Hosts**: If you have hundreds or thousands of servers running your application, CodeDeploy can update all of them at once instead of doing it one by one, which saves time and reduces the chance of errors.

3. **Monitor Health and Roll Back**: CodeDeploy monitors the health of your application during deployment, and if something goes wrong, it can automatically roll back to the previous version so that users do not experience downtime.

## What I Learned

This lab taught me that DevOps is not just about writing code, but also about how that code gets from a developer's computer into production safely and efficiently. **AWS CodeDeploy** is particularly useful when teams need to deploy applications across multiple environments without manual intervention, which reduces the risk of errors and speeds up the release process.

I also learned that automation is a key part of DevOps, because manual deployments are slow, error-prone, and do not scale well as applications grow. Understanding tools like CodeDeploy will help me work more efficiently in real-world DevOps environments. 🎉
