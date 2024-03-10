---
title: "Project- 3 Hosting a static website using an AWS S3 bucket"
datePublished: Sun Mar 10 2024 12:03:48 GMT+0000 (Coordinated Universal Time)
cuid: cltlguocx00010ajy6o6yf7rj
slug: project-3-hosting-a-static-website-using-an-aws-s3-bucket
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710072129156/a8a7de8b-99f4-4f8c-8b43-4acadf128710.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1710072213743/e640c5cc-8f26-4b01-a20a-f2bd92e6e8e2.png
tags: cloud, aws, devops, static-website, 90daysofdevops, happy-learning

---

### Tools Used:  
1\. AWS S3 bucket.  
2\. AWS Route53

### Implementation:  
1\. Created an S3 bucket with public access.  
2\. Upload the code to the bucket.  
3\. Host it by enabling, “Static Website Hosting”.  
4\. Give access to the objects that are in the S3 bucket, by editing “Bucket Policy”.  
5\. It will generate a link to access the static website.  
6\. Using Route53, we can connect it to a specific domain name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710070136484/0a434521-6135-4d5c-b45f-7774c3667d71.png align="center")

Changes Bucket policy

```plaintext
{
  "Version": "2012-10-17",
    "Statement": [
        
        {
            "Sid": "publicReadForGetBucketObjects",
            "Effect":"Allow",
            "Principal": "*",
            "Action" :"s3:GetObject",
            "Resource":"arn:aws:s3:::akash6474/*"
        }
    ]
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710071584397/8d6fe5d9-bb99-4683-90dc-5680548b1dba.png align="center")

enable static web hosting

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710071657968/342ea84a-e9ed-4f39-93c2-bb8d1aa3fdee.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710071782746/c1dfcbba-cc86-4678-b9d1-4b6ef5981c36.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710071907689/faa306a6-0457-4af9-a0e0-32d18ad8ebbb.png align="center")

* Thank you for enjoying my DevOps blog! Your positive response fuels my passion to dive deeper into technology and innovation.
    
* Stay tuned for more captivating DevOps articles, where we'll explore this dynamic field together. Follow me on **Hashnode** and connect on **LinkedIn** ([https://www.linkedin.com/in/akash-singh-70o/](https://www.linkedin.com/in/akash-singh-70o/)) for the latest updates and discussions.