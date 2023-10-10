---
title: "Day 41: Setting up an Application Load Balancer with AWS EC2 🚀 ☁"
datePublished: Tue Oct 10 2023 13:11:48 GMT+0000 (Coordinated Universal Time)
cuid: clnkccn6q000009jqglwg12to
slug: day-41-setting-up-an-application-load-balancer-with-aws-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696944181840/5a9d1c5f-2b58-4600-b253-ef2fa94f9d83.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696944217335/a79e8092-7fbc-45e4-84a9-8d59a37f5993.png
tags: cloud, aws, automation, load-balancer, 90daysofdevops

---

Hi, I hope you had a great day yesterday learning about the launch template and instances in EC2 in Day 40. Today, we are going to dive into one of the most important concepts in EC2: Load Balancing.

## What is Load Balancing?

Load balancing is the process of distributing network traffic across a group of servers. This can be done for a variety of reasons, such as to improve performance, reliability, and scalability.

Load balancers can be either hardware or software-based. They typically sit between the clients and the servers, and they use a variety of algorithms to distribute traffic across the servers.

Some of the most common load balancing algorithms include:

* Round robin: This algorithm distributes traffic evenly across all of the servers in the pool.
    
* Weighted round robin: This algorithm distributes traffic to the servers based on their weight, which can be used to give more powerful servers more traffic.
    
* Least connections: This algorithm distributes traffic to the servers with the fewest active connections.
    
* Fastest response time: This algorithm distributes traffic to the servers that have the fastest response times.
    

Load balancers can also be used to provide failover. If one of the servers in the pool goes down, the load balancer can automatically redirect traffic to the remaining servers. This helps to ensure that the application remains available even if one of the servers is unavailable.

Load balancing is an essential part of many high-traffic websites and applications. It helps to improve performance, reliability, and scalability.

Here is an example of how load balancing works:

A user visits a website that is load-balanced across two servers. The user's request is first sent to the load balancer. The load balancer then uses one of its algorithms to distribute the request to one of the two servers. The server processes the request and returns the response to the load balancer. The load balancer then forwards the response to the user.

Load balancing is a transparent process for the user. They are not aware that their request is being distributed across multiple servers.

Load balancing is a powerful tool that can be used to improve the performance, reliability, and scalability of websites and applications.

## Elastic Load Balancing:

Elastic Load Balancing (ELB) is a cloud-based service that distributes traffic across multiple servers. This helps to improve performance, reliability, and scalability.

Here is a simple analogy:

Imagine a restaurant with a lot of customers. The restaurant has a maître d', who is responsible for seating the customers. The maître d' wants to seat the customers at the tables that are best able to handle them, based on factors such as the size of the party and the type of food they want to order.

ELB is like the maître d'. It distributes traffic across multiple servers in a way that optimizes performance, reliability, and scalability.

Here are some of the benefits of using ELB:

* **Improved performance:** ELB distributes traffic to the servers that are best able to handle it, which helps to improve the overall performance of your application.
    
* **Increased reliability:** ELB distributes traffic across multiple servers so that your application remains available even if one of the servers fails.
    
* **Improved scalability:** ELB can automatically scale its capacity up or down in response to changes in traffic demand. This helps to ensure that your application can handle even the heaviest traffic loads.
    

ELB is a popular choice for load-balancing websites and applications of all sizes. It is easy to use and manage, and it offers a wide range of features and benefits.

### Application Load Balancer (ALB):

Here is the official documentation of the [**Application Load Balancer**](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html).

ALB Functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model.

It intelligently distributes incoming HTTP and HTTPS traffic to target instances, containers, or IP addresses based on the rules and configurations set by the user.

# **Network Load Balancer**

Here is the official documentation of the [**Network Load Balancer**](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html).

NLB functions at the fourth layer of the Open Systems Interconnection (OSI) model. It can handle millions of requests per second.

NLB operates at the transport layer (Layer 4) of the OSI model and is designed to handle TCP, UDP, and TLS traffic.

It is highly scalable, offers low latency, and is suitable for applications that require high performance and extreme scalability.

# **Gateway Load Balancer**

Here is the official documentation of the [**Gateway Load Balancer**](https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/introduction.html).

A Gateway Load Balancer operates at the third layer of the Open Systems Interconnection (OSI) model, the network layer.

It listens for all IP packets across all ports and forwards traffic to the target group that’s specified in the listener rule.

It maintains the stickiness of flows to a specific target appliance using a 5-tuple (for TCP/UDP flows) or 3-tuple (for non-TCP/UDP flows).

# **Classic Load Balancer**

Here is the official documentation of the [**Classic Load Balancer**](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-getting-started.html).

*CLB* operates at both the application layer (Layer 7) and transport layer (Layer 4) of the OSI model and is ideal for applications that require basic load-balancing features.

CLB provides basic load-balancing capabilities for distributing incoming traffic across multiple Amazon EC2 instances.

Here is the link that gives the product differentiation and pricing of the [**different ELBs provided by AWS.**](https://aws.amazon.com/elasticloadbalancing/features/#Product_comparisons)

## [🎯 Today's Tasks:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day41/tasks.md#-todays-tasks)

### [Task 1:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day41/tasks.md#task-1)

* **launch 2 EC2 instances with an Ubuntu AMI and use User Data to install the Apache Web Server.**
    
* **Modify the index.html file to include your name so that when your Apache server is hosted, it will display your name also do it for 2nd instance which includes " TrainWithShubham Community is Super Awesome :) ".**
    
* **Copy the public IP address of your EC2 instances.**
    
* **Open a web browser and paste the public IP address into the address bar.**
    
* **You should see a webpage displaying information about your PHP installation.**
    

Create two EC2 instances with the following details.

Instance name: install-apache

Application and OS Images (Amazon Machine Image): Ubuntu AMI

Instance type: t2.micro

Key pair (login): Select the key pair you want.

Network Settings: Check the boxes “Allow HTTPS traffic from the Internet” & “Allow HTTP traffic from the Internet”

Advanced details:

Scroll down to the User data box and type these commands:

```plaintext
#!/bin/bash
sudo apt-get update -y
sudo apt-get install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

take the number of instances that you want to launch instance ex. 2

Click on Launch Instance. Once the instances are created rename them with numbers so you can easily identify the servers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696882574435/fc2bd0f5-54e9-46ab-b2c6-154333bcd266.png align="center")

To modify the index.html file, we need to modify its content in the directory /var/www/html.

Give the index.html file root user privilege.

```plaintext
sudo chmod +x index.html
```

These are the contents I have used in the index.html file:

```plaintext
<!DOCTYPE html>
<html>
<head>
<title>My New Page for Apache Web Server</title>
</head>
<body>
<h1>Welcome to my webpage my name is akash singh</h1>
</body>
</html>
```

Copy the Public IP of the instance and paste it into the browser. You should be able to see the author’s name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696885948725/d4141337-3ea8-4b34-b647-a3ba1879c3f7.png align="center")

Let’s connect to Apache-Server-1.

go to instance copy the public address and paste into google then you will see your web page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696886069281/7ca3a158-602d-4eb4-ab17-ca690a99397b.png align="center")

Let us do the same thing for the other server with some more additions.

```plaintext
<!DOCTYPE html>
<html>
<head>
<title>My New Page for Apache Web Server</title>
</head>
<body>
<h1>Welcome to my webpage my name is akash singh</h1>
<h2> TrainWithShubham Community is Super Awesome :) <h2>
<h3> I am happy to use the Apache Web Server <h3>
</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696886626556/3fd88518-6337-4400-9278-2db64addd702.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696886646698/46a3c6e5-4e22-43ce-ae48-d5160a7939ff.png align="center")

And yay! We have successfully installed the Apache Web server and edited the index.html file.

### [Task 2:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day41/tasks.md#task-2)

* Create an Application Load Balancer (ALB) in EC2 using the AWS Management Console.
    
* Add EC2 instances that you launch in task-1 to the ALB as target groups.
    
* Verify that the ALB is working properly by checking the health status of the target instances and testing the load-balancing capabilities.
    

Go on ec2 in the left side scroll down there you will see load balancer

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696941524834/1d200bf5-c382-420f-8618-745da94a122b.png align="center")

Click on Create Load balancer. The following page opens up.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696941664646/33758bd5-83ba-4552-94bd-95a0dd2f1563.png align="center")

Select Application Load Balancer and click on Create.

Basic configuration:

> ***Load balancer name: PHP-lb***
> 
> ***Scheme: Internet Facing (access to public)***
> 
> ***Network mapping: Select at least two Availability Zones and one subnet per zone.***
> 
> ***Security Group: default will be selected and select the other security groups you require.***

Before going ahead, let’s create Target Groups. Select Target Groups which is below the Load balancer on your left-hand side.

Click on Create Target groups.

Step 1: Specify group details

> ***Basic configuration: Instances***
> 
> ***Target group name: ALB-apache***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696941888145/a85cb52e-e7f8-4125-8313-8b0ad59161b4.png align="center")

*Click on Create Target groups.*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696941980673/2e80fbe5-9275-4ca4-860a-da0d5391c615.png align="center")

Now go back to the ALB page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696942175037/9efbe766-b41d-40c8-b970-287a4568fa4e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696942287366/52361e93-4cd3-464e-9761-b8a830f457bd.png align="center")

Select the target group you just created.

And click on Create Load Balancer.

Once the ALB is in an active state, copy the DNS of the load balancer and access it from your website.

As per the load, we can observe that sometimes Server 1 comes up and other times Server 2 comes up.

And we have created an ALB, and created the load!

In this blog, I have discussed how to create an AWS Application Load Balancer and use it to balance the load between two web servers. If you have any questions or would like to share your experiences, please leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

* If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.
    
    #Day41 #90daysofdevops
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)