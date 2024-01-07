---
title: "Day 65 - Working with Terraform Resources 🚀"
datePublished: Sun Jan 07 2024 14:10:08 GMT+0000 (Coordinated Universal Time)
cuid: clr3kmhb8000008l7hz4tfylx
slug: day-65-working-with-terraform-resources
tags: cloudformation, linux, devops, terraform, 90daysofdevops

---

Yesterday, we saw how to create a Terraform script with Blocks and Resources. Today, we will dive deeper into Terraform resources.

### **Terraform Resources:**

A resource in Terraform represents a component of your infrastructure, such as a physical server, a virtual machine, a DNS record, or an S3 bucket. Resources have attributes that define their properties and behaviors, such as the size and location of a virtual machine or the domain name of a DNS record.

When you define a resource in Terraform, you specify the type of resource, a unique name for the resource, and the attributes that define the resource. Terraform uses the resource block to define resources in your Terraform configuration.

A resource block typically includes the following elements:

* Resource Type: Specifies the type of resource being defined, such as “aws\_instance” for an Amazon EC2 instance.
    
* Resource name: Provides a unique name for the resource within your configuration.
    
* Resource configuration: Specifies the desired settings and attributes for the resource, such as the instance type, disk size, or access control rules.
    

## Task 1: Create a security group

To allow traffic to the EC2 instance, you need to create a security group. Follow these steps:

In your [main.tf](http://main.tf) file, add the following code to create a security group:

```plaintext
  terraform {
    required_providers {
      aws = {
        source  = "hashicorp/aws"
        version = "~> 4.0"
      }
    }
  }

  provider "aws" {
    region = "us-east-1"
  }
```

* Now add the following code in your [`main.tf`](http://main.tf/) file to create a security group:
    

```plaintext
  resource "aws_security_group" "web_server" {
    name_prefix = "web-server-sg"
    ingress { 
       from_port   = 22 
       to_port     = 22 
       protocol    = "tcp" 
       cidr_blocks = ["0.0.0.0/0"] 
     } 

    ingress {
      from_port   = 80
      to_port     = 80
      protocol    = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }

    ingress { 
       from_port   = 443 
       to_port     = 443 
       protocol    = "tcp" 
       cidr_blocks = ["0.0.0.0/0"] 
     } 

    egress { 
       from_port   = 0 
       to_port     = 0 
       protocol    = "-1" 
       cidr_blocks = ["0.0.0.0/0"] 
     }
  }
```

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704449958624/62caf6fa-988e-45d8-8a5d-142106387276.png align="center")
    
* Run the `terraform init` to initialize the Terraform project and.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704449987060/856a4fd9-bfba-4d62-8823-699f4ca66a4b.png align="center")
    
* Run the `terraform apply` to create the security group.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386276545/cc88c4bd-39ce-4c3c-8188-78293c6b813c.png?auto=compress,format&format=webp align="left")
    
    ### **🔶 Task 2: Create an EC2 instance**
    
    Now you can create an EC2 instance with Terraform. Follow these steps:
    
* In your [**main.tf**](http://main.tf/) file, add the following code to create an EC2 instance:  
    
* ```plaintext
    terraform {
      required_providers {
        aws = {
          source = "hashicorp/aws"
          version = "~>4.0"
        }
      }
    }
    
    provider "aws" {
      region = "us-east-1"
    }
    
    resource "aws_security_group" "web_server" {
      name_prefix = "web-server-sg"
    
      ingress {
        from_port   = 80
        to_port     = 80
        protocol    = "tcp"
        cidr_blocks = ["0.0.0.0/0"]
      }
    
      ingress {
        from_port   = 22
        to_port     = 22
        protocol    = "tcp"
        cidr_blocks = ["0.0.0.0/0"]
      }
    
     egress {
            from_port  = 0
            to_port    = 0
            protocol    = "-1"
            cidr_blocks = ["0.0.0.0/0"]
            }
    }
    
    resource "aws_instance" "web_server" {
      ami           = "ami-053b0d53c279acc90"
      instance_type = "t2.micro"
      key_name      = "CP-keys"
    
    security_groups = [
        aws_security_group.web_server.name
      ]
    
    tags = {
            Name= "TfInstanceByakash"
            }
      user_data = "${file("index.sh")}"
    }
    ```
    
    Now create an [**index.sh**](http://index.sh/) file in the same directory
    

```plaintext
#!/bin/bash
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
echo "<html><body><h1>Welcome to my website, My name is Chandresh Patle!</h1></body></html>" > /var/www/html/index.html
```

Note: Replace the ami and key\_name values with your own. You can find a list of available AMIs in the AWS documentation.

Run terraform apply to create the EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695386820307/c3e189f2-a155-459f-8601-39b9457c750c.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695393797264/baa6696f-7508-410b-85bd-f8c5c93691e5.png?auto=compress,format&format=webp align="left")

### **🔶 Task 3: Access your website**

*   
    Now that your EC2 instance is up and running, you can access the website you just hosted on it.
    
      
    Now Open the web browser by using the new instance Public IP address.
    
      
    ***Happy Learning :)***
    
    Stay in the loop with my latest insights and articles on cloud ☁️ and DevOps ♾️ by following me on Hashnode, LinkedIn [Akash Singh](https://www.linkedin.com/in/akash-singh-70o/) and GitHub ([**https://github.com/**](https://www.linkedin.com/in/chandreshpatle28/)**akashsingh6474**).
    
    Thank you for reading! Your support means the world to me. Let's keep learning, growing, and making a positive impact in the tech world together.
    
    #Git #[**Linux**](https://chandreshpatle.hashnode.dev/tag/linux) [**Devops**](https://chandreshpatle.hashnode.dev/tag/devops) [**#Devopscommunity**](https://chandreshpatle.hashnode.dev/tag/devopscommunity) [**#90daysofdevopschallenge**](https://chandreshpatle.hashnode.dev/tag/90daysofdevopschallenge) #python #docker #Jenkins #Kubernetes #Terraform #cloud