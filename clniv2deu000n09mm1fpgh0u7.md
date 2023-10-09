---
title: "Day 40 AWS EC2 Automation ☁"
datePublished: Mon Oct 09 2023 12:20:09 GMT+0000 (Coordinated Universal Time)
cuid: clniv2deu000n09mm1fpgh0u7
slug: day-40-aws-ec2-automation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696797985770/2b5e12d1-8efe-46fc-a046-45736911ff1a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696798209203/fa6867b5-3e62-4a37-80a6-866f35dd56f3.png
tags: aws, automation, devops, autoscaling, 90daysofdevops

---

## Automation in EC2:

Amazon Elastic Compute Cloud (Amazon EC2) is a fundamental service within Amazon Web Services (AWS) that provides scalable and resizable compute capacity in the cloud. Essentially, it allows users to launch and manage virtual machines (VMs), known as "instances," to run applications and workloads. EC2 instances are commonly used for a wide range of tasks, from hosting websites and applications to running complex data analysis jobs.

Key features and concepts of Amazon EC2 include:

1. **Instances**: These are virtual servers that can be configured with different CPU, memory, storage, and network capacities based on your needs. EC2 offers a variety of instance types optimized for different use cases.
    
2. **AMI (Amazon Machine Image)**: An AMI is a pre-configured template used to launch EC2 instances. AMIs contain the necessary information to launch an instance, including the operating system, software, and configuration settings.
    
3. **Instance Types**: EC2 provides a range of instance types optimized for various workloads, such as general-purpose, compute-optimized, memory-optimized, and storage-optimized instances.
    
4. **Regions and Availability Zones**: EC2 instances can be launched in different geographical regions worldwide, each consisting of multiple Availability Zones. This architecture provides redundancy and high availability for applications.
    
5. **Elastic IPs**: Elastic IP addresses are static IP addresses that can be associated with EC2 instances. They are useful for ensuring that your instance retains the same IP address even after stopping and restarting.
    
6. **Security Groups**: Security Groups act as virtual firewalls, controlling inbound and outbound traffic to and from EC2 instances. You can define rules to allow or deny specific types of traffic.
    
7. **Key Pairs**: Key pairs are used for secure SSH (Secure Shell) access to EC2 instances. You create a key pair, and the private key is used to access the instance securely.
    
8. **EBS (Elastic Block Store)**: EBS provides scalable block storage volumes that can be attached to EC2 instances. These volumes are used for data storage and can be easily backed up and resized.
    
9. **Auto Scaling**: Auto Scaling is a feature that allows you to automatically adjust the number of EC2 instances based on predefined scaling policies. This ensures your application can handle varying workloads efficiently.
    
10. **Load Balancers**: AWS offers load balancing services such as Elastic Load Balancing (ELB) to distribute incoming traffic across multiple EC2 instances for better availability and fault tolerance.
    

EC2 is a fundamental building block of AWS and is widely used by businesses and developers to deploy, manage, and scale applications in the cloud. Its flexibility, scalability, and cost-effectiveness make it a core component of cloud computing solutions.

The below image depicts the lifecycle of an Instance:

![](https://miro.medium.com/v2/resize:fit:623/0*aRa5NXSkVkW8Xltj.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*oL_r54qMdt2BVnj3axnmEQ.png align="left")

# **Instance Sizes**

![](https://miro.medium.com/v2/resize:fit:875/1*1PJAuuOLy86H5iAbM3Bm3g.png align="left")

### [Task1:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day40/tasks.md#task1)

* Create a launch template with Amazon Linux 2 AMI and t2.micro instance type with Jenkins and Docker setup (You can use the Day 39 User data script for installing the required tools.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696793170668/faae0436-2c71-4429-a4d7-4d5aa4c4c1b2.png align="center")
    
    Click on the launch template
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696793450165/1cd30b94-07b7-41e1-a73c-b0663ff9cd69.png align="center")
    
    *Application and OS Images (Amazon Machine Image): Ubuntu*
    
    *Instance Type: t2.micro*
    
    ![]( align="center")
    
    *Advanced Details: Use the following script-*
    
* ```plaintext
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
        sudo apt-get update
        sudo apt-get install docker.io -y
        sudo systemctl start docker
    ```
    
    Click on Create Launch Template.
    
    In the Launch Templates Dashboard, select the template you created and click on Actions. Select Launch Instance from the template.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696795500238/35af9b85-bcd0-43fe-8744-2c2a37d1a76d.png align="center")
    
    * Create 3 Instances using Launch Template, there must be an option that shows a number of instances to be launched,can you find it? :)
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696795616617/93573779-c01d-44de-8b61-f29c596085b7.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696795684164/6b8471f0-736b-4a22-9361-0c9533ce0d25.png align="center")
    
    We can see that 3 instances are running.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696795771555/a6eec836-6e76-4dd1-a70e-31c484f98746.png align="center")
    
    * You can go one step ahead and create an auto-scaling group, sounds tough?
        
    
    Let’s create ASG(Auto Scaling Group) and make the process more automated depending on the usage.
    
    On the left side of your screen, you can find Auto Scaling Groups.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696795925075/83c0fe1b-8c10-4515-947d-cefd0acceded.png align="center")
    
    * Click on Create Auto Scaling Group.
        
        Step 1: Choose the launch template or configuration
        
        > ***Auto Scaling group name: JenkinsDockerScaling***
        > 
        > ***Launch template: DockerJenkinsTemplate***
        > 
        > ***Version: 2***
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796127462/d8da3e94-0dae-4ef4-9706-05869dd22d62.png align="center")
    
    Click Next.
    
    Step 2: Choose instance launch options
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796264807/55b506b4-78f9-4cbb-bf58-2982e749ca55.png align="center")
    
    Select the availability zones and click on Next.
    
    Step 3: Configure advanced options
    
    *Load balancing: Attach to a new load balancer*
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796406326/b4e343a3-ac7b-45d9-a7f2-7047c4b6357d.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796526107/093a74d3-0da2-400f-be1a-c6c8a57844be.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796561585/e0d74bcc-e3ac-4405-b24b-68c45e2c57f1.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796616209/7b7c32ef-e067-4d55-ba8a-27a86be033c3.png align="center")
    
    Let the other options be the default, and click on Next.
    
    Step 4\*:\* Configure group size and scaling policies
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796761621/593493ad-5766-4b74-942a-e8b1a742a018.png align="center")
    
    *Desired capacity: 2*
    
    *Minimum capacity: 1*
    
    *Maximum capacity: 5*
    
    Click on Next.
    
    Step 5: Add notifications
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796869000/bf8d239c-28e6-4d9a-a974-cf653a7bcf5f.png align="center")
    
* Step 6: Add Tags
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696796902426/9989eea0-aa04-4e87-8014-3471d468e815.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696797134062/a7c54568-6bcb-4c01-ad4c-9b7d1c532d84.png align="center")
    
    When the utilization increases or decreases, the instances are scaled up or down automatically, based on the criteria you have given.
    
    In this blog, I have discussed how to automate EC2 instance creation using Launch Templates and Auto Scaling Groups. If you have any questions or would like to share your experiences, please leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.
    
* If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.
    
    #Day38 #90daysofdevops
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/akashsinghtech9@gmail.com**