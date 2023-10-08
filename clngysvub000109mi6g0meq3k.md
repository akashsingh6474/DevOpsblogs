---
title: "Day 38 Getting Started with AWS Basics☁"
datePublished: Sun Oct 08 2023 04:29:13 GMT+0000 (Coordinated Universal Time)
cuid: clngysvub000109mi6g0meq3k
slug: day-38-getting-started-with-aws-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696709874726/012300ca-e887-4860-8ef7-13867f2f25d8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696709902481/935e7d51-d345-4a6f-ad83-90855e832c9b.png
tags: cloud, aws, devops, iam, 90daysofdevops

---

Hey, DevOps enthusiast. Welcome back to my blog so far we have learned about Linux, Git, Github, Docker, Jenkins and Kubernetes, and we have done some projects those tools. Now it is time to learn about the cloud let's learn most popular cloud provider AWS lets get started.

# **What is AWS?**

![](https://miro.medium.com/v2/resize:fit:223/1*l31gDNikhvDUHMRkidZJOA.png align="center")

> Amazon Web Services is a subsidiary of Amazon providing on-demand cloud computing platforms and APIs to individuals, companies, and governments, on a metered pay-as-you-go basis.

## **Cloud Computing in AWS**

Amazon Web Services (**AWS**) is the world’s most comprehensive and broadly adopted cloud platform, offering over 175 fully featured services from data centers globally. Millions of customers — including the fastest-growing startups, largest enterprises, and leading government agencies — are using AWS to lower costs, become more agile, and innovate faster.

Amazon Web Services (**AWS**) is a secure cloud services platform, offering compute power, database storage, content delivery and other functionality to help businesses scale and grow. Running web and application servers in the cloud to host dynamic websites.

## **Why do we need AWS?**

Amazon Web Service is made up of so many different cloud computing products and services. The highly profitable Amazon division provides servers, storage, networking, remote computing, email, mobile development, and security. AWS is so large and present in the computing world that it’s far outpaced its competitors.

![](https://miro.medium.com/v2/resize:fit:458/1*ai-v5HNlsid43Etic0ZGxA.png align="center")

## **Why AWS is leading cloud platform in market ?**

AWS provides some very important functions, which are stated as below :

1. \*\*Most functionality :  
    \*\**AWS has significantly more services, and more features within those services than any other cloud provider from infrastructure technologies like compute, storage, and databases to emerging technologies such as machine learning and artificial intelligence, data lakes and analytics, and Internet of Things. This makes it faster, easier, and more cost effective to move your existing applications to the cloud and build nearly anything you can imagine. AWS also has the deepest functionality within those services.*
    
2. \*\*Largest Community :  
    \*\**AWS has the largest and most dynamic community with millions of active customers and tens of thousands of partners globally. Customers across virtually every industry and of every size including startups, enterprises and public sector organizations are running every imaginable use case on AWS.*
    
3. \*\*Most Secure :  
    \*\**AWS is architected to be the most flexible and secure cloud computing environment available today. The backend provided by a deep set of cloud security tools with 230 security, compliance & governance services & features. AWS supports 90 security standards & the compliance certifications. There are total 117 AWS services that store customer data offer the ability to encrypt the data.*
    
4. \*\*Fastest pace of innovation :  
    \*\**With AWS, you can leverage the latest technologies to experiment and innovate more quickly. As AWS continually accelerating the pace of innovation to invent entirely new technologies you can use to transform your business. Also in 2014, AWS pioneered the server-less computing space with the launch of AWS Lambda, which lets developers run their code without provisioning or managing servers.*
    
5. \*\*Mostly proven operational expertise :  
    \*\**AWS has unmatched experience, maturity, reliability, security, and performance that you can depend upon for your most important applications. For over 13 years, AWS has been delivering cloud services to millions of customers around the world running a wide variety of use cases. AWS has the most operational experience, at greater scale, of any cloud provider.*
    

# **Global Network of AWS :**

![](https://miro.medium.com/v2/resize:fit:875/1*DUdC3Y2oZYbla4g29DiArg.png align="left")

### **Most secure**

AWS is architected to be the most flexible and secure cloud computing environment available today. Our core infrastructure is built to satisfy the security requirements for the military, global banks, and other high-sensitivity organizations. This is backed by a deep set of cloud security tools, with over 300 security, compliance, and governance services and features, as well as support for 143 security standards and compliance certifications.

# **AWS Global Infrastructure**

![](https://miro.medium.com/v2/resize:fit:875/0*eX3acg8ErThb3ZgL align="left")

# **What are Regions?**

A region is a geographic area that is served by a specific set of AWS infrastructure.

Each region has multiple Availability Zones, which are isolated from each other by distance and independent power and cooling. This helps to ensure that your applications are highly available even if there is a problem with one Availability Zone.

Each region is identified by a two-letter code, such as us-east-1 for the US East (N. Virginia) region.

AWS also offers several Local Zones, which are smaller, more focused deployments of infrastructure that are designed to be closer to end users.

# **What are Availability Zones?**

An Availability Zone is an isolated data center within an AWS region that is designed to provide high availability and fault tolerance for applications and services.

> ***High Availability: High availability refers to the ability of a system or application to remain operational and accessible for an extended period, typically measured in terms of uptime.***
> 
> ***Fault Tolerance: Fault tolerance refers to the ability of a system or application to continue functioning properly, or at a degraded level, even in the presence of faults or failures.***

In other words, an Availability Zone (AZ) is a distinct location within a region that is isolated from other AZs by distance and independent power and cooling. This helps to ensure that your applications are highly available even if there is a problem with one AZ.

> ***As per the latest update, A region should have a minimum of 3 AZs and a maximum of 6 AZs.***

# **Services in AWS for a DevOps Engineer**

As of October 2023, there are over 200 AWS services available. In those 200+ services, a few services that you may use as a DevOps Engineer are:

1. Compute: EC2, ECS, Lambda, Fargate, EKS.
    
2. Storage: S3, RDS, DynamoDB, ElastiCache.
    
3. Networking: VPC, Route53, CloudFront.
    
4. Security: IAM, KMS, Secrets Manager.
    
5. DevOps: CodeBuild, CodePipeline, CodeCommit, CodeDeploy.
    
6. Logging & Monitoring: CloudWatch, OpenSearch, CloudTrail.
    

These are the few services you will have to learn to become a Cloud Admi or a Cloud Engineer.

In the upcoming blogs, I will discuss in depth the above services.

For today, let me discuss the most important service: Security (IAM).

## [IAM:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day38/tasks.md#iam)

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

When you create an AWS account, you begin with one sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the AWS account *root user* and is accessed by signing in with the email address and password that you used to create the account. We strongly recommend that you don't use the root user for your everyday tasks. Safeguard your root user credentials and use them to perform the tasks that only the root user can perform. For the complete list of tasks that require you to sign in as the root user

### [Task1:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day38/tasks.md#task1)

Create an IAM user with the username of your own wish and grant EC2 Access. Launch your Linux instance through the IAM user that you created now and install Jenkins and Docker on your machine via a single Shell Script.

first login on your AWS console and then search IAM in the search bar

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696677120313/cab5b510-740d-4f73-8756-d867f0be4fe4.png align="center")

In the left corner, you can see Access Management. Go to Users.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696677204059/90369f47-c500-45c4-879b-8fac3657e4b8.png align="center")

Click on users and click on Create User

*Step 1: Specify user details*

* Provide the username you want.
    
* Select the checkbox for “Provide user access to the AWS Management Console — *optional*”.
    
* Select “I want to create an IAM user”
    
* Click on Next.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696677386933/e508559a-d295-44f2-abc6-a52d7ccc7238.png align="center")
    

* *Step 2: Set permissions*
    
* Select “Attach policies directly” in the Permission Options.
    
* In the Permission Policies search bar, search for EC2 and select “[**AmazonEC2FullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=ap-south-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonEC2FullAccess)”.
    
* Click on Next.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696684184059/ae51a32c-9555-404c-b11f-fdee17be2dda.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696684403502/14cf239c-8b6c-42bb-8b78-83623a873def.png align="center")

Step 3 review create

Review the details and click on “Create User”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696684478284/198530a5-a45e-4869-ab7f-08cb3616cd66.png align="center")

*Step 4: Retrieve the password*

You can view and download the user’s password below or email the user’s instructions for signing in to the AWS Management Console. This is the only time you can view and download this password.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696684592423/4eb34a5d-78c3-4854-aeb8-f460717d1d68.png align="center")

Click on the Return user list then you will see your user

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696684641848/4fe7284d-cc7c-4cd9-8ce7-a3a952cd4155.png align="center")

Let’s log in to AWS as an IAM user. Open in any other browser.

![](https://miro.medium.com/v2/resize:fit:875/0*cw6HDdw7q-mPW--k align="left")

Account ID will be the 12-digit number we had in the console sign-in URL.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696685239536/0a5775b5-3e29-4440-8445-d416ebde960d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696685292312/8599477b-d343-4ba0-b812-dd44b8c743e6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696685340663/9d5ad481-4897-4494-9470-dec498fe53fd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696685551840/bda2391f-5ec8-4abf-8043-62bd2011bb4f.png align="center")

Once you are in the AWS console, launch an EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696685991949/6ec725c5-da87-4993-993b-3cce5d19b470.png align="center")

Connect to the instance.

> Let’s install docker and Jenkins in this instance using a shell script.
> 
> Create a file named **install-file.sh**

```plaintext
#!/bin/bash
sudo apt update
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
sudo apt-get update
sudo apt-get install docker.io -y
sudo systemctl start docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696686594290/4cdbc435-5a6a-4d44-beb7-c017d31c8034.png align="center")

now run the script

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696686724514/32f2497c-666a-4763-8032-f1ca74c25ae9.png align="center")

NOw open the port because Jenkins runs on 8080 port.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696686908763/3babe9e0-92e8-4048-83fd-dee52d2a5753.png align="center")

Verify if Jenkins and Docker were installed successfully.

```plaintext
systemctl status jenkins
systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696687111222/42b3f2eb-0419-4f26-83ad-185e9dc0adc8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696687153060/38d8748b-3279-42ff-9984-e75efe7adeea.png align="center")

The status of both Docker and Jenkins is Active(Running), which means the installation was successful.

Now go to your browser, open PublicIP:8080 and you must be able to see the Unlock Jenkins page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696687277990/bf4848ee-99e0-4e1d-b54e-a34d35c43880.png align="center")

### **Task:02**

In this task you need to prepare a devops team of avengers. Create 3 IAM users of avengers and assign them in devops groups with IAM policy.

Log in to the AWS console as a root user. Go to IAM.

Go to Access Management &gt; User Groups &gt; Create Group &gt; User Group Name “Avengers”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696707116827/3bc4ee0c-1b4e-4dca-be3e-58c6baae4aae.png align="center")

Go to Access Management &gt; Users &gt; Create 3 users named Hulk, thor, and Doctorstr..

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696707770253/5571843f-ae0c-47de-bc2d-6e37311f3448.png align="center")

Go to User Groups &gt; Open the Group Avengers &gt; In the Users section &gt; Click on Add Users &gt;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696708033705/deba0c3e-1f14-45a0-8a39-fc6a2d9b26a6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696708079183/8049222b-f3c3-476f-9e2d-d52121cb2c82.png align="center")

Today's learning journey is significant. In this blog, we explored AWS and its worldwide infrastructure. We also covered fundamental IAM (Identity and Access Management) concepts and created users with attached policies. If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day38 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/akashsinghtech9@gmail.com**