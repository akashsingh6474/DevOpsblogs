---
title: "Day 62 - Terraform and Docker 🔥"
datePublished: Fri Dec 22 2023 14:37:30 GMT+0000 (Coordinated Universal Time)
cuid: clqgqk1ij000d08l0cxj6bsee
slug: day-62-terraform-and-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703255082086/6612bff2-d08a-4c22-a5ef-e3e2df0759db.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1703255795203/457b8db2-213e-4a92-abf0-fb83ae7814fd.png
tags: aws, devops, terraform, infrastructure-as-code, 90daysofdevops

---

Welcome to our blog, where we dive into the fascinating world of Terraform! In this space, we will explore Blocks and Resources in Terraform, offering insights and practical guidance to help you harness the full power of this infrastructure as code tool.

In our first task, we’ll guide you through creating a Terraform script with Blocks and Resources, including the essential Provider Block, as well as a Terraform Docker script.

Then, in our second task, we’ll focus on crafting a Resource Block for an Nginx Docker image, providing you with a hands-on approach to understanding Terraform’s capabilities. Join us as we embark on this Terraform journey, and let’s learn and grow together!

Terraform needs to be told which provider to use in the automation, hence we need to give the provider name with source and version. For Docker, we can use this block of code in your [**main.tf**](http://main.tf/)

## Blocks and Resources in Terraform

**Terraform Blocks?**

* A block is a section within a configuration file that defines a specific object or behavior. Blocks are used to organize and configure resources, providers, variables, outputs, and other components of a Terraform configuration.
    
* A block is a container for the each content and An argument assigns a value to a particular name
    
* A resource block is a specific type of block used to define and manage a resource within an infrastructure provider. It describes the desired state of a resource and instructs Terraform on how to create, update, or destroy that resource. A resource block typically includes properties such as the resource type, name, and configuration options specific to the provider.
    

here is some examples of block and resources that will help you to understand more about the terraform blocks & resources.

```plaintext
resource "docker_image" "my_nginx" {
            name = "nginx:latest"
            keep_locally = false
}
```

## Task-01

* Create a Terraform script with Blocks and Resources
    
    create a terra\_docker.tf and pass the docker provider
    
* ```plaintext
    terraform {
      required_providers {
        docker = {
          source  = "kreuzwerker/docker"
          version = "~> 2.21.0"
    }
    }
    }
    ```
    
    * Note: kreuzwerker/docker, is a shorthand Docker installation. [**kreuzwerker docker registry**](https://registry.terraform.io/providers/kreuzwerker/docker/latest/docs)
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703250421912/e4516514-e403-4567-8427-710b253edf48.png align="center")
    
    ## Provider Block:
    
    The provider block configures the specified provider, in this case, docker. A provider is a plugin that Terraform uses to create and manage your resources.
    
    ```plaintext
    provider "docker" {}
    ```
    
    ## Resource:
    
    Use resource blocks to define components of your infrastructure. A resource might be a physical or virtual component such as a Docker container, or it can be a logical resource such as a Heroku application.
    
    Resource blocks have two strings before the block: the resource type and the resource name. In this example, the first resource type is docker\_image and the name is Nginx.
    
    ## Task-02
    
    Create a resource Block for an nginx docker image
    
    ```plaintext
    resource "docker_image" "nginx" {
     name         = "nginx:latest"
     keep_locally = false
    }
    ```
    
    * Create a resource Block for running a docker container for nginx
        
    
    ```plaintext
    resource "docker_container" "nginx" {
     image = docker_image.nginx.latest
     name  = "tutorial"
     ports {
       internal = 80
       external = 80
     }
    }
    ```
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703250699101/2058edf7-e3f8-47c3-a6e2-436f8290d75c.png align="center")
    
    Initializes a new or existing Terraform working directory by downloading the necessary provider plugins using `terraform init` command.
    
* ```plaintext
    terraform init
    ```
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703250822699/99baf2e2-51e4-4940-ba91-455a8c25a2da.png align="center")
    
    Now execute the `terraform plan` command which will create an execution plan by comparing the desired state in the configuration to the current state of the infrastructure.
    
* ```plaintext
    terraform plan
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251155586/6d257677-0b71-4848-afc6-110012f70fa5.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251255859/01098b92-2e53-4499-ab7c-e63ed881fe14.png align="center")
    
    * Execute the `terraform apply` command so all the configurations get [**executed.It**](http://executed.it/) creates, modifies, or deletes resources as necessary to achieve the desired state, based on the execution plan generated by `terraform plan`.
        
        ```plaintext
        terraform apply
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251337329/cf3087ce-e54a-4562-bbea-ce2f74e4d29b.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251406289/a3ea4f87-5d56-454b-95e8-ff140d9aa87e.png align="center")
    
    * In case Docker is not installed on your Linux system use the below commands:
        
    * ```plaintext
          sudo apt-get install docker.io -y
        
          sudo chown $USER /var/run/docker.sock
        
          docker --version
        ```
        
        * Check docker container is created using the below command:
            
        * ```plaintext
            docker ps
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251529481/044ad7a9-e3df-4b44-a2a2-6f7ca6fa579c.png align="center")
            
            * Browse public IP address, you can see the Nginx default page.
                
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703251597429/7011570d-e97f-429f-9792-98ed51f29eae.png align="center")
            
            * Execute the `terraform destroy` so it will prompt for confirmation and then proceeds to delete the resources, reverting the infrastructure to its pre-Terraform state.
                
            
              
            
        
        ![](https://miro.medium.com/v2/resize:fit:875/0*0_xYcAB73pzy1UWF align="left")
        
        ![](https://miro.medium.com/v2/resize:fit:875/0*Zew1UXkyCoJHuTEA align="left")
        
        ![](https://miro.medium.com/v2/resize:fit:875/0*GOn9sKBf1UC_Szs1 align="left")
        
        In Day 62 of my ’90 Days of DevOps’ journey, I delved into the exciting world of Terraform Blocks and Resources. I acquired knowledge about the crucial elements that make up Terraform scripts:
        
        \- The **<mark>Provider Block</mark>**, which serves as the gateway to define the cloud or infrastructure provider for our resources. It’s the starting point that sets the stage for our infrastructure management.
        
        \- The **<mark>Resource Block</mark>**, which I explored in depth. This component allows us to create, configure, and manage specific infrastructure resources. In this task, I put this knowledge to use by creating a Resource Block to provision an Nginx Docker image, covering key details like image name, ports, and other configurations.
        
        I’m thrilled to share my learning journey with you, and I’m always open to questions, discussions, and insights related to DevOps, Infrastructure as Code (IAC), or infrastructure management. If you’d like to connect with me and explore these topics further, please find me on LinkedIn As [Akash Singh](https://www.linkedin.com/in/akash-singh-70o/) . Your feedback and contributions are invaluable as we all strive to enhance our DevOps and infrastructure skills.