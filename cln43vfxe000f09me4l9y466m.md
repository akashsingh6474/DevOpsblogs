---
title: "Day 32  Launching your Kubernetes Cluster with Deployment"
datePublished: Fri Sep 29 2023 04:30:10 GMT+0000 (Coordinated Universal Time)
cuid: cln43vfxe000f09me4l9y466m
slug: day-32-launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695851282922/677d7771-fbff-451c-8e1d-806a70966e48.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695851362387/38e340b2-5edd-4e2a-8d27-02fd36e94340.png
tags: aws, deployment, k8s, cluster, 90daysofdevops

---

### **What is Pod in k8s?**

A *Pod* (as in a pod of whales or pea pod) is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers that are relatively tightly coupled. In non-cloud contexts, applications executed on the same physical or virtual machine are analogous to cloud applications executed on the same logical host.

### **What is Deployment in k8s?**

A *Deployment* provides declarative updates for [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) and [ReplicaSets](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/).

You describe a *desired state* in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets or to remove existing Deployments and adopt all their resources with new Deployments.

**Here are the key aspects of a Kubernetes Deployment:**

1. Desired State
    
2. Rolling Updates and Rollbacks
    
3. Scaling
    
4. High Availability
    
5. Self-healing
    

### **Task:**

**Create one Deployment file to deploy a sample todo-app on K8s using the "Auto-healing" and "Auto-Scaling" feature**

First set up the Kubernetes cluster with the master node and the worker node.

now create a manifest file for our nodo-todo application

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  labels:
    app: todo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
      - name: todo
        image: rishikeshops/todo-app
        ports:
        - containerPort: 3000
```

Create the deployment using **kubectl apply -f todo-deployment.yml**

Scale the replicas of deployment if required

Here I have scaled the replicas to 2,

```plaintext
using
kubectl scale --replicas=2 deploy/todo-deployment.yml
```

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**