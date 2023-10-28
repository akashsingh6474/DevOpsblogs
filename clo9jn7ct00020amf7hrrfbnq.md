---
title: "Day-48 - ECS"
datePublished: Sat Oct 28 2023 04:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clo9jn7ct00020amf7hrrfbnq
slug: day-48-ecs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698442464076/fd56ca79-dace-41e0-bee1-7b4e7552d577.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698442569500/87e128c2-0a81-4e49-be46-ea529f089761.png
tags: cloudformation, devops, ecs, 90daysofdevops, awscloud

---

### **What is ECS?**

Amazon ECS (Elastic Container Service) is a managed container orchestration service provided by AWS, which simplifies the deployment and management of containerized applications, making it easier to run and scale container workloads in the cloud.

Amazon ECS (Elastic Container Service):

1. **Container Orchestration Service**: ECS is a fully managed container orchestration service that helps you deploy, manage, and scale containerized applications. It simplifies the process of running containers at scale.
    
2. **Containers**: Containers are a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. ECS allows you to run containers efficiently and at scale.
    
3. **Managed Service**: ECS takes care of the underlying infrastructure and management of the containerized applications. It handles tasks like provisioning resources, scheduling containers, and monitoring their health.
    
4. **Scalability**: ECS can automatically scale your containerized applications up or down based on CPU and memory utilization, ensuring that your application can handle varying workloads.
    
5. **Integration with AWS Services**: ECS integrates with other AWS services like Elastic Load Balancing, Identity and Access Management (IAM), CloudWatch for monitoring, and more, making it part of the broader AWS ecosystem.
    
6. **Task Definitions**: In ECS, you define the containers you want to run in a task definition. A task definition is a blueprint for your application, specifying which Docker images to use, CPU and memory requirements, networking configuration, and more.
    
7. **Services**: ECS allows you to define services to ensure that a specified number of tasks (containers) are running and automatically replace any that become unhealthy.
    
8. **Fargate**: ECS offers two launch types, one of which is Fargate. With Fargate, you don't need to manage the underlying EC2 instances. It's a serverless compute engine for containers.
    

### **Difference between EKS and ECS?**

Amazon Web Services (AWS) offers two container orchestration services, Amazon Elastic Kubernetes Service (EKS) and Amazon Elastic Container Service (ECS). Here's a comparison of the key differences between EKS and ECS:

1. **Orchestration Technology**: **Amazon EKS (Elastic Kubernetes Service)**: EKS is a managed Kubernetes service. It uses Kubernetes as the underlying orchestration technology. Kubernetes is an open-source container orchestration platform that is highly extensible and widely used in the industry. **Amazon ECS (Elastic Container Service)**: ECS is a container orchestration service that AWS has developed. It is specific to AWS and is not based on Kubernetes.ECS uses its own orchestration technology and concepts, which may be simpler to get started with for some users.
    
2. **Ease of Use**: **Amazon EKS**: Kubernetes has a steeper learning curve and may be more complex to set up and manage, but it provides extensive flexibility and customization.EKS is a better choice for users who are already familiar with Kubernetes or who require Kubernetes-specific features. **Amazon ECS**: ECS is generally considered easier to set up and use for users who want a more straightforward container orchestration solution. It abstracts many of the complexities of container orchestration, making it more accessible for those who don't have prior Kubernetes experience.
    
3. **Serverless Compute Engine**: **Amazon EKS**: EKS does not offer a serverless option for running containers. You need to manage and provision the underlying EC2 instances yourself. **Amazon ECS**: ECS provides a serverless compute engine called AWS Fargate. With Fargate, you don't need to manage the underlying EC2 instances. It's a fully managed serverless option for running containers.
    
4. **Pricing Model**: **Amazon EKS**: You pay for the Kubernetes control plane (master nodes) and the underlying EC2 instances separately. The cost can be more granular but potentially more complex. **Amazon ECS**: Pricing is more straightforward since you are billed based on the resources you use within ECS or Fargate. You don't need to manage the control plane separately.
    
5. **Ecosystem and Community**: **Amazon EKS**: Kubernetes has a large and active open-source community, and there is a vast ecosystem of tools, extensions, and resources available for Kubernetes users.**Amazon ECS**: ECS has a smaller ecosystem compared to Kubernetes but is tightly integrated with other AWS services. It may be a better choice if you are building your application entirely within the AWS ecosystem.
    
6. **Use Cases**: A**mazon EKS**: EKS is suitable for users who require the advanced features and extensibility of Kubernetes, such as managing complex microservices architectures or integrating with on-premises Kubernetes clusters.**Amazon ECS**: ECS is a good choice for users who prefer a simpler and more AWS-native container orchestration solution. It works well for applications that can benefit from easy integration with other AWS services.EKS (Elastic Kubernetes Service) and ECS (Elastic Container Service) are both container orchestration platforms provided by Amazon Web Services (AWS). While both platforms allow you to run containerized applications in the AWS cloud, there are some differences between the two.
    

**Architecture**: ECS is based on a centralized architecture, where there is a control plane that manages the scheduling of containers on EC2 instances. On the other hand, EKS is based on a distributed architecture, where the Kubernetes control plane is distributed across multiple EC2 instances.

**Kubernetes Support**: EKS is a fully managed Kubernetes service, meaning that it supports Kubernetes natively and allows you to run your Kubernetes workloads on AWS without having to manage the Kubernetes control plane. ECS, on the other hand, has its own orchestration engine and does not support Kubernetes natively.

**Scaling**: EKS is designed to automatically scale your Kubernetes cluster based on demand, whereas ECS requires you to configure scaling policies for your tasks and services.

**Flexibility**: EKS provides more flexibility than ECS in terms of container orchestration, as it allows you to customize and configure Kubernetes to meet your specific requirements. ECS is more restrictive in terms of the options available for container orchestration.

**Community**: Kubernetes has a large and active open-source community, which means that EKS benefits from a wide range of community-driven development and support. ECS, on the other hand, has a smaller community and is largely driven by AWS itself.

## Task:

**Set up ECS (Elastic Container Service) by setting up Nginx on ECS.**

There are some steps to create ECS for Nginx.

GO to your AWS account and search ECS. click on ECS and click on Cluster.

Now create a cluster and give the name of your cluster . nginx-cluster-day48 Let the Networking be default &gt; And by default Infrastructure AWS Fargate (Serverless) is selected.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441330473/e3bb5a64-ee70-45d5-a3da-de5353c2b2c3.png align="center")

  
And Click on Create.

# **Create a Task Definition**

In the left Panel of ECS &gt; Select Task Definitions

Click on Create new task definitions &gt; Create new task definition

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441512153/dd9e4e34-0436-4967-9514-ea25d43f13e0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441527053/1a8eb6eb-75be-4b84-8503-e2ad4debd40e.png align="center")

# **Configure task definition and containers**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441561961/9963117b-2b95-4fb3-8829-8a05a6d20587.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441592929/f2630794-87b4-4c0a-8143-145b6395adb5.png align="center")

Task definition family: nginx-task-day48

Under Container details:

Name: nginx-container

Image URI: [public.ecr.aws/nginx/nginx:mainline-alpine](http://public.ecr.aws/nginx/nginx:mainline-alpine)

You can get this Image URL from [**Amazon ECR Public Gallery**](https://gallery.ecr.aws/).

Let other things be as it is and click on default.

# **Configure environment, storage, monitoring, and tags**

I am letting the app environment by default which is AWS Fargate.

Let other default things be as it is and click on Next.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441639492/86b5bc77-a1b8-49f5-b201-4421609437b1.png align="center")

# **Review and create**

Review the configuration and click on Create Task Definition.

# **Create a Service**

Go to ECS &gt; Select & open the Cluster you created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441750609/5e06de1b-fa84-48a0-a13e-c9ff085c491a.png align="center")

Click on Create which is next to Services.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441761686/2bda580e-0516-41d7-b7b8-825ab136a1f7.png align="center")

Let the Environment section be the default.

In the Deployment Configuration section &gt; Select Service &gt; Give the Service Name &gt; Select the task definition you created.

In the Networking Tab &gt; Let the things be default except for SG &gt; Click on Create new SG.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441772318/65ea1651-fa4a-4a39-9279-695aa76bd67c.png align="center")

Security group name: nginx-SG

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441784314/17a8f4de-9f3b-49f3-b1f1-2860184a85cd.png align="center")

Security group description: Security Group for Nginx Cluster

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441819778/1678e273-b936-43bf-b628-80053040cbfa.png align="center")

Let’s test by accessing the Nginx container using the Public IPv4 of Fargate.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698441937982/cdaa8a41-dcbc-4544-9012-3a07b7a6b922.png align="center")

> ***For the IP go to the Tasks tab in the ECS Cluster dashboard &gt; Select the Task number of your task required &gt; You can find the Public IPv4.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698442073704/06582c39-0cec-474e-92e4-41ed6a25e266.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698442106382/afd0bd05-1101-4f0c-aaee-7a0fb980bdd1.png align="center")

This can be further done by exposing Nginx publicly, by setting up an Application Load Balancer (ALB). And then can be reached by the public IP address of your load balancer.

In this blog, I have explained ECS and set up an Nginx cluster in ECS. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [**Akash Singh.**](https://www.linkedin.com/in/akash-singh-70o/) Do reach me and I am open to suggestions and corrections.

#Day48 #90daysofdevops