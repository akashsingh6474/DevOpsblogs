---
title: "Day 30 Kubernetes Architecture"
datePublished: Tue Sep 26 2023 03:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clmzrepks00000alce6x573pz
slug: day-30-kubernetes-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695660615663/5ad0fc5d-7161-4d41-9175-13fc8e44815d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695660809433/017456ce-cb04-4bf0-a427-e1b75a87d1d5.png
tags: docker, aws, kubernetes, jenkins, 90daysofdevops

---

### Introduction of Kubernetes:

Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

The name Kubernetes originates from Greek, meaning helmsman or pilot. K8s as an abbreviation results from counting the eight letters between the "K" and the "s". Google open-sourced the Kubernetes project in 2014. Kubernetes combines over 15 years of Google's experience running production workloads at scale with best-of-breed ideas and practices from the community.

## [Tasks](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day30/tasks.md#tasks):

### What is Kubernetes?

Kubernetes is an open-source container management tool that automates container deployment, scaling and load balancing. It schedules, runs and manages isolated containers that are running on virtual/physical/cloud machines. all top cloud providers support Kubernetes. One popular name of Kubernetes is **k8s** because it has 8 letters of character in Kubernetes name.

1. **Organization**: It organizes these containers into groups called "pods" so they can work together easily.
    
2. **Balance**: It makes sure these pods are spread out evenly on your computer servers, so no single server gets overloaded.
    
3. **Replacement**: If one of these containers breaks, Kubernetes quickly replaces it with a new one to keep your programs running smoothly.
    
4. **Updates**: When you want to update your programs, Kubernetes can do it without causing any downtime or disruptions.
    
5. **Access**: It also helps your programs talk to each other and makes sure they're accessible to other parts of your system.
    

### **What are the benefits of using k8s?**

Using Kubernetes (K8s) offers several key benefits:

1. **Efficient Container Management**: K8s simplifies the management of containerized applications, making it easier to develop, deploy, and scale them.
    
2. **Scalability**: It allows you to easily scale your applications up or down to handle changing workloads and traffic.
    
3. **High Availability**: K8s helps ensure that your applications are highly available by distributing them across multiple servers (nodes) and automatically recovering from failures.
    
4. **Zero-Downtime Updates**: You can update your applications without causing downtime or disruptions to your users.
    
5. **Resource Efficiency**: It optimizes resource allocation, which can lead to cost savings by using server resources efficiently.
    
6. **Portability**: Kubernetes is cloud-agnostic, allowing you to run your applications on various cloud providers or on your own infrastructure.
    
7. **Self-Healing**: K8s automatically detects and replaces failed containers, improving application reliability.
    
8. **Service Discovery and Load Balancing**: It handles routing traffic to the right containers and balances the load, ensuring even distribution.
    
9. **Security**: Kubernetes provides tools for managing secrets, controlling access, and enforcing network policies to enhance application security.
    
10. **Declarative Configuration**: You define your application's desired state, and K8s ensures that state is maintained, reducing manual configuration.
    
11. **Ecosystem**: A wide range of tools and extensions can enhance Kubernetes' capabilities for monitoring, logging, and managing applications.
    
12. **Community Support**: Kubernetes has a large and active open-source community, providing access to documentation, tutorials, and support.
    
13. **Cost Efficiency**: By optimizing resource usage and enabling efficient scaling, Kubernetes can lead to cost savings.
    
14. **DevOps and CI/CD Integration**: It integrates well with DevOps practices and continuous integration/continuous deployment (CI/CD) pipelines, streamlining development workflows.
    
15. **Immutable Infrastructure**: Kubernetes encourages immutable infrastructure principles, promoting predictability and reliability in deployments.
    

In summary, Kubernetes simplifies container management, improves application availability, optimizes resource usage, enhances security, and fosters flexibility and automation in modern application deployment.

### **Explain the architecture of Kubernetes:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695658012532/544efd4c-1ca1-4ab4-be71-b763198c4e30.png align="center")

### **kube-scheduler:**

Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on.

### **etcd:**

etcd is a distributed key-value store that plays a crucial role in Kubernetes. It serves as the primary data store and communication hub for all cluster-related information

### **Controller-manager:**

The Controller Manager in Kubernetes is like a traffic cop for your applications. It watches over your apps and makes sure they're running as you want them to.

1. **Traffic Cop**: It keeps an eye on your apps and checks if they're behaving correctly.
    
2. **Fixes Problems**: If an app crashes or if you want more of them, it takes care of it automatically.
    
3. **Scales Apps**: It can make your apps bigger or smaller based on how much work they have to do.
    
4. **Updates Apps Safely**: When you update your apps, do it carefully so your users don't notice any glitches.
    
5. **Balances Traffic**: It helps spread out the people using your apps so that no one server gets too busy.
    

### **Episerver**:

The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane.

the API server in Kubernetes is like a front door to your cluster:

1. **Access Point**: It's the main way you talk to your Kubernetes cluster. You send requests to the API server to tell it what you want to do with your applications.
    
2. **Control Center**: The API server is the boss that decides if your requests are allowed or not. It checks permissions and makes sure you're not doing anything you're not supposed to.
    
3. **Cluster Brain**: It's where all the information about your cluster is stored. When you ask about your apps, the API server checks its brain (the cluster's state) and tells you what's happening.
    

### **kubectl:**

`kubectl` is a command-line tool for controlling and managing Kubernetes clusters. It lets you do things like creating, updating, and inspecting applications running in Kubernetes, making it easier to work with containerized applications.

## **Node Components**

Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

### **kubelet:**

An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.

The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. The Kubelet doesn't manage containers that were not created by Kubernetes.

### **Service-proxy:**

Service Proxy is like a receptionist at an office building:

1. **Routing Traffic**: Just like a receptionist directs visitors to the right offices, the Service Proxy directs network traffic to the right parts of your applications inside the cluster.
    
2. **Load Balancing**: If lots of people want to talk to your applications, the Service Proxy helps distribute the requests evenly so that no one part gets overwhelmed.
    
3. **Stable Address**: It gives your applications a stable and easy-to-remember address so other parts of your system can find them, even if they move around or change.
    
4. **Health Checks**: The Service Proxy checks if your applications are healthy and working. If something goes wrong, it knows not to send traffic there.
    

So, in simple terms, the Service Proxy helps manage the flow of traffic to your applications in a Kubernetes cluster, ensuring they're reachable, balanced, and healthy.

### CNI Network:

CNI stands for "Container Network Interface." It's not a network itself but rather a standardized way to set up and manage networking for containers in a cluster.

### What is a Control Plane?

the Control Plane serves as the central management system for the entire cluster. It's akin to the brain or control center of the Kubernetes cluster. Here's a simplified breakdown:

1. **API Server**: The entry point for cluster commands.
    
2. **Controller Manager**: Ensures the cluster stays as you want it, with controllers for specific tasks.
    
3. **Scheduler**: Places new tasks efficiently across the cluster.
    
4. **etcd**: The cluster's memory, storing data.
    

### **Write the difference between kubectl and kubelets.**

**kubectl**:

* **Purpose**: `kubectl` is a tool you use to talk to and manage your Kubernetes cluster.
    
* **Interface**: It's like your remote control for Kubernetes. You can use it to give commands to the cluster, like starting or stopping applications.
    
* **User-Friendly**: `kubectl` is designed for people to use, so it has a user-friendly interface and commands.
    
* **Location**: It runs on your computer and connects to the Kubernetes cluster to control it.
    
* **Examples**: You use `kubectl` to create and manage things like applications, services, and configurations in your Kubernetes cluster.
    

**kubelet**:

* **Purpose**: `kubelet` is like the worker on each computer in your Kubernetes cluster.
    
* **Node Manager**: It makes sure the containers (the parts of your applications) on that computer are running as they should be.
    
* **Container Manager**: It specifically takes care of starting, stopping, and keeping an eye on the containers.
    
* **Node Health**: `kubelet` checks if the computer (node) is healthy and tells the main control center if there's a problem.
    
* **Not for Users**: You don't use `kubelet` directly. It quietly does its job in the background on each computer in the cluster.
    

In short, `kubectl` is like your remote control for managing the whole cluster, while `kubelet` is the worker on each computer, making sure the applications (containers) on that computer run smoothly.

### **Explain the role of the API server.**

The API Server in Kubernetes plays a pivotal role as the primary control point and communication hub for the entire cluster. Here's a simplified explanation of its role:

1. **Cluster Gateway**: Think of the API Server as the main gateway or entrance to your Kubernetes cluster. All interactions with the cluster, such as creating, updating, or deleting resources, go through the API Server.
    
2. **Request Processor**: When you or any component in the cluster (like `kubectl`) wants to do something in the cluster, you send a request to the API Server. The API Server processes your request and determines if it's allowed and how it should be executed.
    
3. **Authentication and Authorization**: The API Server handles authentication to ensure you are who you say you are. It also performs authorization checks to determine if you have the necessary permissions to perform the requested action.
    
4. **Data Source**: The API Server acts as the source of truth for your cluster's configuration and state. It stores information about all the resources and their current status in a database.
    
5. **Communication Hub**: Different components within the cluster communicate with each other through the API Server. For example, the Scheduler talks to the API Server to find out where to place new workloads.
    
6. **Security**: The API Server enforces security policies and ensures secure communication within the cluster. It encrypts data in transit and provides secure APIs.
    
7. **RESTful API**: The API Server exposes a RESTful API, which means it uses standard HTTP methods (GET, POST, PUT, DELETE) for communication. This makes it accessible and easy to work with.