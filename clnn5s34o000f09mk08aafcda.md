---
title: "Day 43: S3 Programmatic access with AWS-CLI 💻 📁"
datePublished: Thu Oct 12 2023 12:31:10 GMT+0000 (Coordinated Universal Time)
cuid: clnn5s34o000f09mk08aafcda
slug: day-43-s3-programmatic-access-with-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697109617014/eb5cbab5-69b2-48d3-b0e0-13c0cee880bb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697109657981/752c0c89-34c7-4a0e-b902-6fb81dd4b727.png
tags: cloud, aws, aws-cli, 90daysofdevops, s3-bucket

---

# S3

![s3](https://user-images.githubusercontent.com/115981550/218308379-a2e841cf-6b77-4d02-bfbe-20d1bae09b20.png align="center")

Amazon Simple Storage Service (Amazon S3) is a highly scalable and durable object storage service provided by Amazon Web Services (AWS). It is designed to store and retrieve any amount of data from anywhere on the web, making it a fundamental building block for a wide range of cloud applications and services.

Here are some key features and characteristics of Amazon S3:

1. **Object Storage**: S3 is an object storage service, which means it stores data as objects rather than as files in a hierarchical file system. Each object consists of data, a unique key (or identifier), and metadata.
    
2. **Durability and Availability**: Amazon S3 is known for its high durability and availability. Data stored in S3 is distributed across multiple data centers within an AWS region, providing redundancy and resilience. AWS guarantees a high level of durability, typically 99.999999999% (11 nines).
    
3. **Scalability**: S3 scales automatically to accommodate growing amounts of data. You can store virtually unlimited data in S3, and it is suitable for both small-scale applications and large enterprises.
    
4. **Security**: S3 provides various security features, including access control through AWS Identity and Access Management (IAM), bucket policies, and access control lists (ACLs). You can encrypt data at rest using server-side encryption (SSE) or manage encryption keys yourself with customer-managed keys.
    
5. **Data Lifecycle Management**: You can define data lifecycle policies to automatically transition objects to different storage classes or delete them after a specified period. This helps optimize storage costs.
    
6. **Versioning**: S3 supports versioning, allowing you to preserve, retrieve, and restore every version of every object stored in a bucket. This is useful for data protection and compliance.
    
7. **Data Transfer Acceleration**: Amazon S3 Transfer Acceleration allows you to upload and download objects to/from S3 faster by using Amazon CloudFront's globally distributed edge locations.
    
8. **Static Website Hosting**: You can use S3 to host static websites, making it an affordable and scalable solution for serving web content.
    
9. **Data Analytics**: S3 integrates with various AWS analytics and big data services, such as Amazon Athena, Amazon Redshift Spectrum, and AWS Glue, to enable powerful data processing and analysis.
    
10. **Content Distribution**: S3 can be used in conjunction with Amazon CloudFront (AWS's Content Delivery Network) to distribute content globally, reducing latency for end users.
    
11. **Data Import/Export**: AWS offers services like AWS Snowball and AWS DataSync for efficient and secure data transfer to and from S3, especially for large-scale data migrations.
    

# **Concepts in S3**

[**Buckets**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BasicsBucket): S3 organizes data into containers called buckets. Each bucket has a globally unique name and serves as a logical container for objects.

[**Objects**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BasicsObjects): Objects are the fundamental entities stored in S3. They consist of the data you want to store and associated metadata.

[**Keys**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BasicsKeys): Keys are unique identifiers for objects within a bucket. They represent the object’s path and can include prefixes and subdirectories to organize objects within a bucket.

[**S3 Versioning**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#Versions): S3 supports versioning, which enables you to store multiple versions of an object. This feature helps in tracking changes and recovering from accidental deletions or modifications.

[**Version ID**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BasicsVersionID): In Amazon S3, when versioning is enabled for a bucket, each object can have multiple versions. Each version of an object is assigned a unique identifier called a Version ID. The Version ID is a string that uniquely identifies a specific version of an object within a bucket.

[**Bucket policy**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BucketPolicies): A bucket policy in Amazon S3 is a set of rules that define the permissions and access controls for a specific S3 bucket. It allows you to manage access to your S3 bucket at a more granular level than the permissions granted by IAM (Identity and Access Management) policies.

[**S3 Access Points**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#BasicsAccessPoints): S3 Access Points in Amazon S3 provide a way to easily manage access to your S3 buckets. Access points act as unique hostnames and entry points for applications to interact with specific buckets or prefixes within a bucket. Here are some key points about S3 Access Points:

[**Access control lists (ACLs)**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#S3_ACLs): ACLs (Access Control Lists) in Amazon S3 are a legacy method of managing access control for objects within S3 buckets. While bucket policies and IAM policies are the recommended methods for access control in S3, ACLs can still be used for fine-grained control in specific scenarios.

[**Regions**](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html#Regions): S3 is available in different geographic regions worldwide. When you create a bucket, you select the region where it will be stored. Each region operates independently and provides data durability and low latency within its region.

> ***You can access Amazon S3 and its features only in the AWS Regions that are enabled for your account.***

# **How Amazon S3 works?**

1. You create a bucket. A bucket is like a folder that holds your data.
    
2. You upload your data to the bucket. You can upload files of any size, and you can even upload folders and subfolders.
    
3. You can access your data from anywhere. You can use the Amazon S3 website, the AWS Command-Line Interface (CLI), or any other application that supports Amazon S3.
    

## [Task-01](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day43/tasks.md#task-01):

* Launch an EC2 instance using the AWS Management Console and connect to it using Secure Shell (SSH).
    
* Create an S3 bucket and upload a file to it using the AWS Management Console.
    
* Access the file from the EC2 instance using the AWS Command Line Interface (AWS CLI).
    

*Launch an EC2 instance using the AWS Management Console and connect to it using Secure Shell (SSH).*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696969184366/2d33c7e0-a8a1-432a-843b-c98d8e5f9bee.png align="center")

Connect to it using SSH:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696969260498/69fb0edd-aac1-4bcb-83b7-0ab4d3fb1938.png align="center")

*Create an S3 bucket and upload a file to it using the AWS Management Console.*

Search S3 in the AWS Management Console.

> ***Click on Create Bucket.***
> 
> ***Bucket name: day43task***
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697104604172/c9ded12a-dffb-4eca-881f-3ec0d823b9d0.png align="center")

Upload some data in the bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697104676533/8bc4da61-373b-4155-8f16-cc0c4827a36d.png align="center")

To check the S3 buckets present:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697104933778/64943f90-b891-4d2d-8f45-c2918a30177b.png align="center")

1. Now, SSH to the Ubuntu machine and access the data from CLI -
    
2. Run the command `aws s3 ls` to list all buckets and `aws s3 ls s3://bucket-name` to access data inside a bucket.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697107245408/28513dd7-46fb-4013-8e2f-c531112ddd7c.png align="center")

Let us sync the contents of the local folder with our bucket.

```plaintext
touch file{1..10}.txt
ls 
#aws s3 sync <local-folder> s3://bucket-name
aws s3 sync . s3://s3awsbucket.01
```

This sync can be verified in the console:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697107516185/d2b992db-f375-4f4e-96f7-7a834b4c1390.png align="center")

To list the objects in an S3 bucket:

```plaintext
aws s3 ls s3://day43task
aws s3 ls s3://bucket-name
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697107664179/70e41c5e-b090-49f6-9813-2a3ce9851fc9.png align="center")

To delete an object from an S3 bucket:

```plaintext
aws s3 rm s3://bucket-name/file.txt
aws s3 ls s3://day43task
```

To create a new bucket:

```plaintext
aws s3 mb s3://bucket-name
aws s3 ls
```

To delete a bucket from S3:

```plaintext
aws s3 rb s3://bucket-name
```

# **Task 2:**

**Create a snapshot of the EC2 instance and use it to launch a new EC2 instance. Download a file from the S3 bucket using the AWS CLI. Verify that the contents of the file are the same on both EC2 instances.**

Steps -

1. Go to EC2 &gt; Snapshot &gt; Create Snapshot
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697107880356/648166b5-9315-4399-96d7-683a6859e543.png align="center")

Once the snapshot is created, create an image (AMI) from the snapshot.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697108221410/d8a22ea8-4eb6-4f1d-9d4b-5e23f34268c9.png align="center")

1. Access the AMI and create a new EC2 instance from AMI.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697108334527/f09097f8-ce57-408f-962b-7701bf5825e5.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697108382688/3ba76f56-deaf-4fac-92ed-7abb9b4308e4.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697108601485/9ccac2a0-c110-4319-9cc0-42e6aa149df7.png align="center")
    
    1. Connect to both old and new EC2 machines and validate if we can see the same data in S3 buckets.
        
    2. Run the command `aws s3 cp s3://day43-task-bucket/test_file.txt .` to download a file from the bucket to the local machine.
        
    
3. *Select the Instance &gt; Actions &gt; Click on Launch Instance from AMI*
    

And that’s how we can access and modify S3 and its contents through CLI.

In this blog, I have discussed S3 programmatic access with AWS CLI. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day43 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)