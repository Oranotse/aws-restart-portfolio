# Introduction to AWS Identity and Access Management (IAM) 🔐

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked with **AWS Identity and Access Management (IAM)** to explore how users, user groups, and policies control access to AWS resources. The goal was to create a custom password policy, add users to groups with specific permissions, and test how those permissions work in practice. According to AWS, IAM helps manage who can access your AWS resources and what actions they can perform, which is essential for maintaining security in cloud environments.

## Creating a Custom Password Policy

I started by creating a custom password policy for the AWS account. In the **IAM Console**, I navigated to **Account settings** and clicked **Change password policy**. I configured the policy to require a minimum password length of 10 characters, enabled requirements for uppercase letters, lowercase letters, numbers, and symbols, and set password expiration to 90 days with password reuse prevention for 5 passwords. These changes apply to all users in the AWS account and make passwords much more difficult to crack.

## Exploring User Groups and Policies

I explored three pre-created user groups: **EC2-Admin**, **EC2-Support**, and **S3-Support**. The **EC2-Support** group had a managed policy called **AmazonEC2ReadOnlyAccess** attached, which allows users to view EC2 resources but not modify them. The **S3-Support** group had the **AmazonS3ReadOnlyAccess** policy, which grants permission to view S3 buckets and their contents. The **EC2-Admin** group had a customer inline policy that granted permission to view EC2 information and also start and stop instances. I learned that policies define what actions are allowed or denied through three main components: **Effect** (Allow or Deny), **Action** (the specific API calls), and **Resource** (which AWS resources the policy applies to).

## Adding Users to User Groups

I added users to the appropriate groups based on their job functions. I added **user-1** to the **S3-Support** group, **user-2** to the **EC2-Support** group, and **user-3** to the **EC2-Admin** group by navigating to **User groups**, selecting each group, clicking the **Users** tab, and choosing **Add users**.

## Testing User Permissions

To test the permissions, I copied the **Sign-in URL for IAM users** from the IAM Dashboard and opened a private browser window. I signed in as **user-1** and confirmed they could view S3 buckets but received an error when trying to view EC2 instances. I then signed in as **user-2** and confirmed they could view EC2 instances but could not stop them, and they also could not access S3 buckets. Finally, I signed in as **user-3** and successfully stopped an EC2 instance because they had admin permissions.

## What I Learned

This lab taught me how IAM controls access to AWS resources through users, user groups, and policies. I learned that user groups make it easier to manage permissions by allowing you to apply policies to multiple users at once instead of configuring each user individually. Managed policies are pre-built and can be attached to multiple groups, while inline policies are custom and assigned to only one user or group for specific situations. Testing the permissions by signing in as different users showed me how policies actually work in practice and how read-only access differs from administrative access. Working with IAM gave me hands-on experience with one of the most important security services in AWS.
