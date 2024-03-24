---
title: "DevOps Project-4"
datePublished: Sun Mar 24 2024 07:19:47 GMT+0000 (Coordinated Universal Time)
cuid: clu56vckd000c0ajz8b4p42a7
slug: devops-project-4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711264613183/c66e777d-e577-4e92-a706-b38bc485c110.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1711264766823/6cf07a50-80eb-4284-bc4f-0424d4242ff0.png
tags: cloud, docker, aws, devops, 90daysofdevops, happy-learning, dockerswarm

---

# Project Description

The project aims to deploy a web application using Docker Swarm, a container orchestration tool that allows for easy management and scaling of containerized applications. The project will utilize Docker Swarm's production-ready features such as load balancing, rolling updates, and service discovery to ensure high availability and reliability of the web application. The project will involve creating a Dockerfile to package the application into a container and then deploying it onto a Swarm cluster. The Swarm cluster will be configured to provide automated failover, load balancing, and horizontal scaling to the application. The goal of the project is to demonstrate the benefits of Docker Swarm for deploying and managing containerized applications in production environments.

### **project - 4 Step-By-Step Implementation.**

### Deploying web app using Docker Swarm. (Production Ready).

Follow the steps:

1. first of all Go to AWS cloud and create three EC2 instance.
    

\-&gt; D-swarm-manager

\-&gt; D-swarm-worker-1

\-&gt; D-swarm-worker-2

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711260203864/1df659b0-f429-4d55-a093-694684198d29.png align="center")

2\. In all three instances, inside the inbound rules, allow

\-&gt; Custom TCP — 2377 — Anywhere IPv4

\-&gt; Custom TCP — 3000 — Anywhere IPv4

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711263367504/ed1191ba-901d-4e96-916b-76b65c7c39b1.png align="center")

3\. Install docker with docker engine on all three nodes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711260650890/3cb4c678-2218-4de2-9d41-9d5b0e05bbac.png align="center")

4\. Now, Open the “Swarm Manager” node and run the command,

```plaintext
sudo docker swarm init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711260749136/ba77d27c-0c00-4281-8d8f-1d8ff7264173.png align="center")

This will be creating empty swarm.

5\. After initializing the swarm on the “swarm-manager” node, there will be one key generated to add other nodes into the swarm as a worker. Copy and run that key on the rest of the servers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711260901774/c58afc39-9257-4238-9f40-9f8a7d5c008a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711260935470/3e109e3f-5b81-43b3-a857-2e35f522f324.png align="center")

6\. To check about all the nodes in the manager, run command on manager

```plaintext
sudo docker node ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711261045649/727ca308-0aef-4213-8293-06000f3949e7.png align="center")

7\. Now, on Manager Node we will create a service,

```plaintext
sudo docker service create --name flask-calculator --replicas 3 --publish 3000:3000 bandank/flask-calculator:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711262569038/3b35554a-eb3b-45ab-b9c2-ec15f7b0f8e9.png align="center")

8\. Now, run command

```plaintext
sudo docker service ls
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711262674875/3a5eaf64-a94c-474c-97ac-26bb81572e29.png align="center")

9\. Now, this service will create a container in the Manager node. To check, run the command:

```plaintext
sudo docker ps 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711262841905/89e611ce-d5a2-45db-8866-1af95a03b227.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711262958561/c7dbbdd1-617c-4924-a6ce-b200b4cc3a62.png align="center")

10\. Now, this service will be running on all three nodes. To check this, just grab the Ip Address of any of the nodes followed by port 3000. As

```plaintext
<Any_ip_of_3_vms>:3000
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711263320981/d27affe3-471b-4419-830d-92f2ff8663f7.png align="center")

11\. If you want to remove any node from the environment, just run

```plaintext
“sudo docker swarm leave”
```

From specific worker nodes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711263668485/1ed84bbf-1b24-4d12-9933-398ab2ddd757.png align="center")

As we removed, one of the workers and inside the status, we can see it’s down.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711263755568/152a8bef-fa0f-4ec9-afcb-5f5bdcea05f3.png align="center")

* Thank you for enjoying my DevOps blog! Your positive response fuels my passion to dive deeper into technology and innovation.
    
* Stay tuned for more captivating DevOps articles, where we'll explore this dynamic field together. Follow me on **Hashnode** and connect on
    
* LinkedIn [AkashSingh](https://www.linkedin.com/in/akashs01) for the latest updates and discussions.
    

#90daysofdevOps#aws#docker#cloud#dockerswarm#dockercompose #happylearning