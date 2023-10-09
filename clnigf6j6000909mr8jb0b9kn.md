---
title: "Day 39 AWS and IAM Basics☁"
seoDescription: "Today's learning journey is significant. In this blog, we explored AWS and its worldwide infrastructure. We also covered fundamental IAM"
datePublished: Mon Oct 09 2023 05:30:13 GMT+0000 (Coordinated Universal Time)
cuid: clnigf6j6000909mr8jb0b9kn
slug: day-39-aws-and-iam-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696792525669/5ad1d539-02b0-40fd-8e39-5c65c5658609.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696792573048/a4bd9bca-4fe7-4fd2-9f80-40af7ddd80a1.png
tags: cloud, aws, devops, iam, 90daysofdevops

---

## User Data in AWS

User data in AWS is a feature that allows you to pass custom data to an Amazon EC2 instance when it starts. This data can be used to initialize the instance, configure software, or install files.

User data is passed to the instance as a base64-encoded string. The instance then decodes the string and executes the commands that are specified in the data.

User data can be specified in the following ways:

* When you launch an instance using the AWS Management Console, you can specify user data in the **User data** field.
    
* When you launch an instance using the AWS CLI, you can specify user data using the `--user-data` option.
    
* When you create an AMI, you can specify user data in the **User data** field.
    

User data can be used for a variety of purposes, such as:

* To initialize the instance, such as by creating a user account or mounting a filesystem.
    
* To configure software, such as by installing packages or setting up configuration files.
    
* To install files, such as scripts or data files.
    

Here is an example of user data:

```plaintext
#!/bin/bash

# Update the system packages.
sudo apt-get update && sudo apt-get upgrade

# Install the Apache web server.
sudo apt-get install apache2

# Create a new website.
echo "Hello, world!" > /var/www/html/index.html

# Start the Apache web server.
sudo systemctl start apache2
```

This user data will update the system packages, install the Apache web server, create a new website, and start the Apache web server.

User data is a powerful feature that can be used to automate the setup and configuration of EC2 instances. It is a good way to ensure that your instances are configured consistently and that they have the software and data that they need.

# What is IAM?

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

When you create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account. We strongly recommend that you don't use the root user for your everyday tasks. Safeguard your root user credentials and use them to perform the tasks that only the root user can perform. For the complete list of tasks that require you to sign in as the root user

## **IAM features**

IAM gives you the following features:

**Shared access to your AWS account**

You can grant other people permission to administer and use resources in your AWS account without having to share your password or access key.

**Granular permissions**

You can grant different permissions to different people for different resources. For example, you might allow some users complete access to Amazon Elastic Compute Cloud (Amazon EC2), Amazon Simple Storage Service (Amazon S3), Amazon DynamoDB, Amazon Redshift, and other AWS services. For other users, you can allow read-only access to just some S3 buckets, or permission to administer just some EC2 instances, or to access your billing information but nothing else.

**Secure access to AWS resources for applications that run on Amazon EC2**

You can use IAM features to securely provide credentials for applications that run on EC2 instances. These credentials provide permissions for your application to access other AWS resources. Examples include S3 buckets and DynamoDB tables.

**Multi-factor authentication (MFA)**

You can add two-factor authentication to your account and to individual users for extra security. With MFA you or your users must provide not only a password or access key to work with your account but also a code from a specially configured device. If you already use a FIDO security key with other services, and it has an AWS-supported configuration, you can use WebAuthn for MFA security. For more information

## **Accessing IAM**

You can work with AWS Identity and Access Management in any of the following ways.

**AWS Management Console**

The console is a browser-based interface to manage IAM and AWS resources. For more information about accessing IAM through the console

**AWS Command Line Tools**

You can use the AWS command line tools to issue commands at your system's command line to perform IAM and AWS tasks. Using the command line can be faster and more convenient than the console

# **Difference between IAM Users and IAM Roles**

## **IAM Users:**

\- Purpose: IAM Users are designed to represent individual people or entities.  
\- Usage: They are typically used for interactive access to AWS resources.  
\- Authentication: IAM Users use long-term credentials, such as username/password or access keys, for authentication.  
\- Permission: Permissions are assigned directly to the user.  
\- Trust Relationship: There is no concept of a trust relationship for IAM Users.  
\- Credential Rotation: IAM Users may have long-term credentials that need to be manually rotated periodically.  
\- Auditing and Compliance: IAM Users have separate audit trails and activity tracking.

## **IAM Roles:**

\- Purpose: IAM Roles are used to grant permissions to AWS services or non-human entities.  
\- Usage: They are commonly used to provide access for applications running on AWS services.  
\- Authentication: IAM Roles provide temporary credentials for entities assuming the role.  
\- Permission: Permissions are attached to the role and are assumed by entities.  
\- Trust Relationship: IAM Roles define trust relationships that specify which entities are allowed to assume the role.  
\- Credential Rotation: IAM Roles provide temporary credentials that are automatically rotated by AWS.  
\- Auditing and Compliance: Actions performed by entities assuming a role are logged under the role’s activity.

In the previous blog, we performed a task on IAM too. Let’s get started with the tasks and learn further.

### [Task1:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day39/tasks.md#task1)

* Launch the EC2 instance with already installed Jenkins on it. Once the server shows up in the console, hit the IP address in the browser and your Jenkins page should be visible.
    

In the AWS Management console &gt; Search EC2 &gt; Click on Launch an Instance.

Given the below details for the creation of instance:

> ***Name of the instance: install-Jenkins***
> 
> ***Application and OS Images (Amazon Machine Image): Ubuntu***
> 
> ***Instance Type: t2.micro***
> 
> ***Key Pair: Select the key pair you have generated or create a new key pair.***
> 
> ***Network settings: Check the boxes for “Allow HTTPS traffic from the Internet” and “Allow HTTP traffic from the Internet”***
> 
> ***Now expand the Advanced Details tab.***

Scroll down to User Data — optional box.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696790235741/b6595f83-f47d-4cd9-9b12-a99d2282ec90.png align="center")

In the box, enter the script that we need to be executed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696790329024/229bad93-6276-49b0-af43-ab6abd2436b2.png align="center")

```plaintext
#!/bin/bash
sudo apt-get update -y
sudo apt install openjdk-11-jre -y
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

And click on Launch Instance. Make sure you open port 8080 to the instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696790538063/f09bb14d-c103-488c-823c-297edef7bd58.png align="center")

Now copy the Public IP of the instance and the port you just opened.

In the browser open the Jenkins UI using the following format:

```plaintext
port no. 8080
```

We will get the Jenkins page if the script we passed as User Data was executed successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696790654045/279aa54c-1485-4c4c-9ae2-d9355d58410c.png align="center")

### [Task2:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day39/tasks.md#task2)

* Create three Roles named: DevOps-User, Test-User and Admin.'
    

Go into your instance and click on the search button and search IAM &gt; Click on that

you will IAM dashboard looks like this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696791616124/2ff65bfa-238d-4b49-be68-d1a4e2030414.png align="center")

\-&gt; Click on roles and create roles

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696791815356/e6426c3c-f9ab-4a12-97ce-0b5df5689179.png align="center")

Add permissions policies give the permissions about the service for ex. ec2

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696791897400/1b8501f0-01bc-4823-99ce-1adbe5f79e9c.png align="center")

Now give the role name what you want to assign and review the name and permissions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696792054521/1cbb03ce-4fe2-4558-8290-167681a84387.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696792162451/93beedf3-651b-4eac-ac10-1a2ccb83cb9d.png align="center")

Click on Create Role.

Similarly, create the roles Test-User and Admin.

Yay! We created IAM roles.

**While creating IAM roles, we need to select the trusted entity. Here is a brief description of the trusted entity:**

* **AWS service: Allows an AWS service to assume the role.**
    
* **Another AWS account: Allows another AWS account to assume the role.**
    
* **Web identity: Allows web-based identity providers (such as Amazon Cognito, Google, or Facebook) to assume the role.**
    
* **SAML 2.0 federation: Allows an external identity provider that supports SAML 2.0 to assume the role.**
    
* **IAM user: Allows an IAM user within your AWS account to assume the role.**
    

It’s a new day in learning. In this blog, I have discussed how to automate EC2 instance creation using User Data and more about IAM. If you have any questions or would like to share your experiences, please leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

Today's learning journey is significant. In this blog, we explored AWS and its worldwide infrastructure. We also covered fundamental IAM (Identity and Access Management) concepts and created roles with attached policies. If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day39 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/akashsinghtech9@gmail.com**