---
title: "Day 31  Launching your First Kubernetes Cluster with Nginx running"
datePublished: Thu Sep 28 2023 04:30:09 GMT+0000 (Coordinated Universal Time)
cuid: cln2ofkyl000e08mj8x5mbbjq
slug: day-31-launching-your-first-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695847577893/fd16f3ed-e657-4b51-b092-a586795cf3ba.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695847884356/38458cb8-2782-45fe-8107-f495119b099d.png
tags: aws, kubernetes, jenkins, k8s, 90daysofdevops

---

### **Introduction:**

Welcome to the 31st blog of the "90 Days of DevOps" series! Today, we will dive into the minikube, features of minikube and installation and setup of minikube on local machine. Launching our First Kubernetes Cluster with Nginx running for DevOps Engineers.

### **What is minikube?**

Minikube is a tool that quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows. It can deploy as a VM, a container, or on bare metal.

Minikube is a pared-down version of Kubernetes that gives you all the benefits of Kubernetes with a lot less effort.

This makes it an interesting option for users who are new to containers, and also for projects in the world of edge computing and the Internet of Things.

### **Features of minikube:**

* Supports the latest Kubernetes release (+6 previous minor versions)
    
* Cross-platform (Linux, macOS, Windows)
    
* Deploy as a VM, a container, or on bare-metal
    
* Multiple container runtimes (CRI-O, containerd, docker)
    
* Direct API endpoint for blazing-fast image load and build
    
* Advanced features such as LoadBalancer, filesystem mounts, FeatureGates, and network policy
    
* Addons for easily installed Kubernetes applications
    
* Supports common CI environments
    

## [Task-01:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day31/tasks.md#task-01)

## [Install minikube on your local](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day31/tasks.md#install-minikube-on-your-local)

There are a few steps to setup Minikube on your local machine

\-&gt; First Go to AWS(Amazon Web Services) lunch a instance take the t2-medium because minikube takes more stores than it needs on 4GB RAM.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695844405676/e2b81e74-2786-417c-b77c-ad582ff12beb.png align="center")

Now update your machine

```plaintext
sudo apt update
```

Install necessary essential packages including curl, wget, and apt-transport-https:

```plaintext
  sudo apt install -y curl wget apt-transport-https
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695844708460/97e64724-1d9b-4b15-9a9d-b329bad56dc1.png align="center")

Install and start docker and configure it to launch on system startup:

```plaintext
 # Install docker
  sudo apt install docker.io

  # add the current user to the "docker" group
  sudo usermod -aG docker $USER

  # Start & enable docker
  sudo systemctl start docker
  sudo systemctl enable docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695844788044/274d4725-6afb-4fac-9438-2da1ed9f3898.png align="center")

Download the Minikube binary using curl, make it executable, and add it to your system's PATH:

```plaintext
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube
sudo mv minikube /usr/local/bin/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695844820706/8becb8b8-af46-425c-8842-7cc148cc51b4.png align="center")

Download the kubectl binary using curl, make it executable, and add it to your system's PATH:

```plaintext
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695844905778/67afb2cf-c17c-4429-b912-2b013f6fb879.png align="center")

Now start minikube

```plaintext
minikube start-driver-docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695845113357/7668f182-e719-43a1-b4f1-f12921b7ff28.png align="center")

check the minikube status is it installed or not and check the nodes

```plaintext
minikube status
kubect get nodes
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695845191617/29b79900-60c0-4af6-b664-b18b89f4a63c.png align="center")

### **Task-02:**

### **Create your first pod on Kubernetes through minikube.**

1. **Start Minikube (if not running):**
    

```plaintext
minikube start
```

**\-&gt; Create a Pod YAML Manifest:**

```plaintext
vim first-pod.yml
```

Create a YAML file that describes your pod. In the K8s for every task create a manifest file

For example, you can create a simple **pod named first-pod** in the **YAML file named first-pod.yml** with the following content:

```plaintext
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695845552402/7492cb18-26b8-424a-a0c2-04a503167dae.png align="center")

That's it! We have created and accessed your first pod on Kubernetes.

Pods are the fundamental units in Kubernetes.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**