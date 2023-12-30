---
title: "Day 64 - Terraform with AWS"
datePublished: Sat Dec 30 2023 16:09:45 GMT+0000 (Coordinated Universal Time)
cuid: clqs9dh8n000308l445ape8ee
slug: day-64-terraform-with-aws
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1703952490158/7ac56392-4af7-47e9-850a-e5a575f715b5.png
tags: cloud, aws, devops, terraform, infrastructure-as-code, iac, 90daysofdevops

---

Welcome to our blog on leveraging the combined strength of Terraform and AWS! Dive into the world of Infrastructure as Code (IaC) as we explore how Terraform simplifies the provisioning and management of AWS resources. Discover step-by-step guides, and best practices empowering you to build and manage scalable infrastructure in the AWS cloud.

### **Prerequisites:\*\***

### **First step: AWS CLI installed**

The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

```plaintext
sudo apt-get update

sudo apt install awscli -y

aws --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703947867870/763073ea-db03-45a5-bd1c-c35355f4ff68.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703947890006/1f1f0a26-8a18-4151-b321-0931dba1d631.png align="center")

# **Second Step -2: AWS IAM User**

IAM (Identity Access Management) AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

To connect your AWS account and Terraform, you need the access keys and secret access keys exported to your machine which we already got from AWS IAM User.

For getting the access key and secret access key of IAM.

First of all you need to create to IAM USER and give to permissions. After created user Go to the creational and get access key &gt; select AWSCLI and click on the check out . then you will get the access key and secret access key and download that.\\

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703948630936/52678e32-8163-435d-9ef4-c59106c0b011.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703948872381/05d24d3a-6e6d-44d8-ab4d-a5ba6c1261b4.png align="center")

```plaintext
export AWS_ACCESS_KEY_ID=<access key>
export AWS_SECRET_ACCESS_KEY=<secret access key>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703948390150/2ce85ef7-0846-4ca9-acef-372e6c17f3aa.png align="center")

# **Third Step -3: Install AWS Providers**

```plaintext
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.0"
    }
  }
}
```

Add the region where you want your instances to be

```plaintext
provider "aws" {
  region = "us-east-1"
}
```

## Task-01

* Provision an AWS EC2 instance using Terraform
    

Create a terraform file named [`main.tf`](http://main.tf/) provision an AWS EC2 instance using terraform aws provider.

```plaintext
  terraform {
    required_providers {
      aws = {
        source  = "hashicorp/aws"
        version = "~> 4.0"
      }
    }
  }
```

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703949177578/c56a7a7c-cd94-4570-8af7-eb3ee4a0cb8c.png align="center")
    
    Create a [`providers.tf`](http://providers.tf/) and put the selected AWS Region that you want to create an EC2 instance.
    
* ```plaintext
      provider "aws" {
      region = "us-east-1"
      }
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703949341153/92e2b133-2545-45f8-803e-684be2602692.png align="center")
    
    * In the [`aws.tf`](http://aws.tf/) provide all the details like AMI ID, instance type and instance name and the number of EC2 count that has to be created.
        
    

```plaintext
resource "aws_instance" "aws_ec2_test" {
        count = 4
        ami = "ami-0fc5d935ebf8bc3bc"
        instance_type = "t2.micro"
        tags = {
     Name = "TerraformTestServerInstance"
  }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703949567993/16c6ccbb-690b-4fa5-b203-6f6cb7630fd8.png align="center")

* Now the first step is to initialize the working directory with the necessary plugins and modules by executing `terraform init`
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703949932858/84a2fe2d-4e4b-49db-8024-d20ef3b720df.png align="center")
    
* Once you initialize all the plugins required for AWS, now execute the `terraform plan` which will create an execution plan by analyzing the changes required to achieve the desired state of your infrastructure.
    

![](https://miro.medium.com/v2/resize:fit:875/0*ewiz72OFWrZzFsmE align="left")

* Finally, use the command `terraform apply` it will apply the changes to create or update resources as needed
    
* ![](https://miro.medium.com/v2/resize:fit:875/0*QYVA72TbqryHGtRg align="left")
    
    * You can check, a new EC2 instance is created using Terraform as we provided a count as 1.
        
    
    ![](https://miro.medium.com/v2/resize:fit:875/0*BhzQZuWxjG9S27bf align="left")
    
    * Once you are done with the newly created instance we can use `terraform destroy` command which will delete the complete infrastructure.
        
    
    ![](https://miro.medium.com/v2/resize:fit:875/0*LzcLShFheZzHeg-r align="left")
    
    * Now from EC2 Instance, we can verify that the newly created EC2 instance is in the terminated state.
        
    
    In this blog, we have learned the essential prerequisites for AWS infrastructure provisioning, including AWS CLI installation, IAM User setup, and AWS Providers installation.
    
    We’ve also embarked on our AWS infrastructure automation journey with Task-01. This blog has set the stage for further learning and exploration in the realm of DevOps, Infrastructure as Code (IAC), and infrastructure management.
    
    Your engagement and feedback are highly encouraged to enhance our collective DevOps and infrastructure skills.
    
* If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.
    
    #Day43 #90daysofdevops
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)