---
title: "Day 49 - INTERVIEW QUESTIONS ON AWS"
datePublished: Sat Oct 28 2023 12:30:09 GMT+0000 (Coordinated Universal Time)
cuid: cloa0sewg000309mre4od68lj
slug: day-49-interview-questions-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698446428413/0f2c1852-1fc6-465d-99b6-bd17d986d88a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698446475072/730889ef-ac06-442e-9206-0fe7cdfe1b5e.png
tags: interview, aws, devops, 90daysofdevops, awscloud

---

* ### **Name 5 AWS services you have used and what are the use cases?**
    

1. **EC2 (Elastic Compute Cloud)**: EC2 is a scalable cloud computing service that allows you to launch virtual servers (instances) to run your applications. You can choose the instance type and operating system, making it suitable for a wide range of use cases, from hosting web applications to running data processing workloads.
    
2. **IAM (Identity and Access Management)**: IAM is AWS's identity management service. It allows you to control who can access your AWS resources and what actions they can perform. IAM is essential for ensuring the security of your AWS environment by managing user accounts, roles, and permissions.
    
3. **S3 (Simple Storage Service)**: S3 is a scalable object storage service that is commonly used for storing and retrieving data. It's great for storing static assets like images, videos, and backups, and it can be integrated with other AWS services to host static websites or store data for applications.
    
4. **CloudWatch**: CloudWatch is AWS's monitoring and observability service. It allows you to collect and track metrics, collect and monitor log files, and set alarms. It's crucial for gaining insights into the operational health and performance of your AWS resources, and for responding to operational events and issues in real-time.
    

* ### **What are the tools used to send logs to the cloud environment?**
    

1. **Amazon CloudWatch Logs**: CloudWatch Logs is a built-in service in AWS that allows you to collect, monitor, and store log data from various AWS resources and applications. You can configure your AWS resources to send their logs directly to CloudWatch Logs.
    
2. **Amazon Kinesis Data Streams**: Kinesis Data Streams is a service for real-time data streaming and ingestion. It's often used to stream and process large volumes of log data in real time.
    
3. **AWS Lambda**: You can create AWS Lambda functions to ingest, process, and forward logs from various sources to your preferred log management service. Lambda functions can be triggered by events and can be used to customize log handling.
    
4. **Amazon S3**: You can store logs in Amazon S3 buckets. Many organizations use S3 to archive logs for compliance and long-term storage. You can configure your applications or services to write log data directly to S3 buckets.
    

* ### **What are IAM Roles? How do you create /manage them?**
    

IAM (Identity and Access Management) roles in AWS are a way to grant permissions to entities that you trust. These entities can be AWS services, applications, or users within your AWS account or external AWS accounts. Roles are a secure way to delegate permissions to access AWS resources without the need for long-term security credentials, like access keys or passwords. IAM roles are commonly used for services and applications that need to interact with AWS resources on your behalf.

1. **Sign in to the AWS Management Console**: Go to the AWS IAM console ([https://console.aws.amazon.com/iam/](https://console.aws.amazon.com/iam/)).
    
2. **Navigate to Roles**: In the left navigation pane, select "Roles."
    
3. **Create a New Role**:
    
    * Click the "Create role" button.
        
    * Select the trusted entity type (e.g., AWS service, another AWS account, or SSO identity provider).
        
    * Choose the use case that best describes the role's purpose. For example, if you're creating a role for an EC2 instance, you can choose "EC2" as the use case.
        
4. **Set Permissions**:
    
    * Attach policies to the role. Policies define what the role is allowed to do. You can choose from existing policies or create custom policies.
        
5. **Name and Review**:
    
    * Give the role a name and, optionally, add tags to help with organization.
        
    * Review the role's configuration and click "Create role."
        
    * **Update Trust Relationships**: You can edit the trust relationship to allow or restrict who or what can assume the role.
        
    * **Update Permissions**: You can attach or detach policies to grant or remove permissions for the role. It's essential to review and update policies as needed to ensure the role has the necessary permissions.
        
    * **Delete a Role**: If a role is no longer needed, you can delete it. Be cautious when deleting roles, as this can impact the services and applications relying on it.
        

* ### **How to upgrade or downgrade a system with zero downtime?**
    

Upgrading or downgrading a system with zero downtime is a common requirement in high-availability environments to ensure uninterrupted service for users. Achieving this goal involves careful planning and the use of various strategies and technologies.

1. **Load Balancers**:
    
    * Implement a load balancer in front of your application servers. AWS Elastic Load Balancer or similar services can distribute traffic across multiple instances, providing redundancy and scalability.
        
2. **Redundant Infrastructure**:
    
    * Set up redundant infrastructure, including application servers, databases, and other critical components. This ensures that one set of servers can be upgraded while the other set continues to handle incoming requests.
        

* ### **What is infrastructure as code and how do you use it?**
    
* Infrastructure as Code (IaC) is a method of managing and provisioning infrastructure using code, enabling automation and consistency. To use it:
    
    1. Choose an IaC tool.
        
    2. Write code or configuration files to define infrastructure.
        
    3. Version control the code.
        
    4. Automate deployment and testing.
        
    5. Integrate it into your CI/CD pipeline.
        
    6. Use IaC for scalability, security, and documentation.
        
    7. Gain benefits like repeatability and agility.
        
* ### **What is a load balancer? Give scenarios of each kind of balancer based on your experience.**
    
* **Load balancers** distribute network traffic to ensure application availability and scalability. Common types include:
    
    1. **ALB** for HTTP/HTTPS and microservices.
        
    2. **NLB** for low-latency TCP/UDP.
        
    3. **CLB** for basic load balancing.
        
    4. **GSLB** for global redundancy.
        
    5. **Hardware** for specific needs.
        
    6. **DNS** for geographic routing.
        
    7. **Reverse proxy** for web security.
        
    8. **Software** for cost-effective load balancing.
        
* ### **What is CloudFormation and why is it used?**
    
    **AWS CloudFormation** is a service that enables the automated provisioning and management of AWS resources using infrastructure as code (IaC). It is used to automate deployments, ensure resource consistency, manage scaling, handle dependencies, and streamline change management in AWS environments. It's a key tool for infrastructure automation and management in AWS.
    
* ### **Difference between AWS CloudFormation and AWS Elastic Beanstalk?**
    
* **AWS CloudFormation**:
    
    * It's a service for defining and provisioning AWS infrastructure as code.
        
    * You create templates in JSON or YAML to specify AWS resources and their configurations.
        
    * Useful for full infrastructure control, including EC2 instances, databases, networking, and more.
        
    * Supports complex architectures and can create or modify resources.
        
    * Typically used for infrastructure orchestration and configuration management.
        
    
    **AWS Elastic Beanstalk**:
    
    * It's a Platform as a Service (PaaS) for deploying and managing web applications.
        
    * Developers provide their application code, and Elastic Beanstalk handles infrastructure provisioning.
        
    * Ideal for simplified application deployment and scalability.
        
    * Supports multiple programming languages and frameworks.
        
    * Best for quick and straightforward application hosting without deep infrastructure management.
        
* ### **What are the kinds of security attacks that can occur on the cloud? And how can we minimize them?**
    
* Common cloud security attacks and how to minimize them:
    
    1. **Unauthorized Access**: Use strong access controls and MFA.
        
    2. **Data Breaches**: Encrypt data, secure networks, and monitor.
        
    3. **DDoS Attacks**: Employ DDoS protection and load balancing.
        
    4. **Malware/Virus**: Keep software updated and use antivirus.
        
    5. **Phishing**: Educate users and filter emails.
        
    6. **Insider Threats**: Audit, follow the least privilege, and exit processes.
        
    7. **MITM Attacks**: Use encryption and validate SSL.
        
    8. **Data Loss**: Back up data and use DLP tools.
        
    9. **API Attacks**: Secure APIs and monitor traffic.
        
    10. **Shared Tech Vulnerabilities**: Keep software updated and configured securely.
        
    11. **Zero-Day Exploits**: Stay informed, use intrusion detection, and have an incident response plan.
        
* ### **Can we recover the EC2 instance when we have lost the key?**
    
* **Recover the Original Key Pair**: If you have a backup of the private key or can retrieve the lost key, you can regain access by replacing the key pair.
    
* **Create a New EC2 Instance**: If you can't recover the original key pair, you can create an AMI of the instance and launch a new one with a new key pair.
    
* **Access via Instance Metadata** (Linux Instances): In some cases, for Linux instances with IAM roles, you may access the instance using instance metadata and the public key.
    

It's crucial to emphasize the importance of proactive key management and maintaining backups to prevent such access issues.

Use the following command to retrieve the public key from the instance metadata and use it to log in:

```plaintext
bashCopy codecurl http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key
```

* ### **What is a gateway?**
    
* In an interview:
    
    A **gateway** is a crucial networking device or software application that acts as an intermediary connecting one network to another. It serves various functions, including protocol translation, network connectivity, security, load balancing, application layer services, and more. Gateways play a pivotal role in enabling communication between different networks and ensuring data flows smoothly between them.
    
* ### **What is the difference between the Amazon Rds, Dynamodb, and Redshift?**
    
* In an interview:
    
    * **Amazon RDS (Relational Database Service)** is a managed relational database service ideal for structured, transactional data and commonly used in web applications and content management systems.
        
    * **Amazon DynamoDB** is a fully managed NoSQL database designed for high-throughput, real-time applications with flexible schemas, such as gaming and IoT.
        
    * **Amazon Redshift** is a managed data warehousing service optimized for analytics and complex queries, often used for business intelligence and decision support systems.
        
* ### **Do you prefer to host a website on S3? What's the reason if your answer is either yes or no?**
    
* **Yes, Host on S3**:
    
    * **Cost-Effective**: Hosting a website on S3 is cost-effective, especially for static websites with low traffic. You pay only for the storage and data transfer you use.
        
    * **Scalability**: S3 can handle high traffic volumes and is automatically scalable. It's suitable for small to medium websites.
        
    * **Simple Setup**: Setting up a static website on S3 is straightforward, and AWS provides tools to simplify the process.
        
    * **Security**: S3 allows fine-grained control over access permissions, and you can integrate it with other AWS services for added security.
        
    
    **No, Don't Host on S3**:
    
    * **Dynamic Content**: If your website relies on dynamic content generated by a server, S3 alone is not suitable. You'd need a web server or serverless architecture to handle dynamic requests.
        
    * **Database**: If your website requires a database for user authentication, e-commerce functionality, or content management, S3 is not the best choice. You'd need a more comprehensive hosting solution.
        
    * **Complexity**: For complex websites with many features, interactivity, and databases, using S3 alone may become complex to manage, and other hosting solutions might be more appropriate.
        

In this blog, we’ve provided a comprehensive list of AWS interview questions and answers, covering key topics like cloud computing, AWS services, security, networking, and DevOps tools. These questions serve as a valuable resource for interview preparation.

If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day43 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)