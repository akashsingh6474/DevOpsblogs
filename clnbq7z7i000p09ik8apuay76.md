---
title: "Day 34 Working with Services in Kubernetes"
datePublished: Wed Oct 04 2023 12:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clnbq7z7i000p09ik8apuay76
slug: day-34-working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696365553091/0ba78a58-4e09-48dc-9bda-b28b13b553a6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696365594905/ba9ae9bf-5711-4aa4-94fd-ffac94249216.png
tags: aws, kubernetes, devops, services, 90daysofdevops

---

In Kubernetes, a "service" is like a traffic cop for your applications. It helps the different parts of an application talk to each other and ensures that your users can access your app.

Imagine you have multiple copies of your app running in different places (called "pods") for reliability and performance. These pods can come and go as your app scales or if there are issues. A Kubernetes service provides a stable address that doesn't change, so your app parts can always find each other.

There are different types of services:

1. **ClusterIP**: For communication between different parts of your app inside the cluster.
    
2. **NodePort**: If you want people outside the cluster to access your app.
    
3. **LoadBalancer**: When you need an external load balancer to distribute traffic to your app.
    
4. **ExternalName**: To connect your app to an external service by name.
    
5. **Headless**: When you need to discover the individual pod addresses without load balancing.
    

In simple terms, a Kubernetes service ensures that your app's parts can find and talk to each other reliably, no matter how many pods are running or where they are located.

### **Task01:**

### **Create a Service for your todo-app Deployment from Day 32.**

Here are the few steps to create a service for todo-app Deployment

Create a Service definition for your todo-app Deployment in a YAML file.

Now create a service.yml where we will deploy NodePort.

```plaintext
 apiVersion: v1
 kind: Service
 metadata:
   name: my-django-app-service
   namespace: my-django-app
 spec:
   type: NodePort
   selector:
     app: django-app
   ports:
       # By default and for convenience, the 'targetPort' is set to the same value as the 'port' field.
     - port: 80
       targetPort: 8000
       # Optional field
       # By default and for convenience, the Kubernetes control plane will allocate a port from a range (default: 30000-32767)
       nodePort: 30009
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696356021749/b8157ee0-dc37-41a3-8bda-8bdf43b7bbfc.png align="center")

**The connection to the server 192.168.49.2:8443 was refused - did you specify the right host or port?**

if you get this type of error when you want to create any pod, deployment, or service file then once start your machine if you are working on minikube.

```plaintext
#write this command
minibuke start
then after create service file
kubectl apply -f service.yml
 # Getting the service. (svc is short form of service)
 kubectl get svc -n=my-django-app
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696359376601/5f88d03a-a644-4f4d-84d3-4595dc483df6.png align="center")

Now go to your instance machine go into security and edit inbound rules expose the port that you describe in the service file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696356488079/ffc0ae38-82db-4694-8511-6789b764c230.png align="center")

So edit the inbound rule of the worker node and add port number 30009 so that we can access the pod outside

Verify that the Service is working by accessing the todo-app using the Service’s IP and Port in your Namespace.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696362585597/325e4e43-91b6-46bf-939c-1125a2ff7b5e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696362550008/234feda8-4577-4a71-b5cf-2770e5a49de4.png align="center")

# **Task 2 Create a ClusterIP Service for accessing the todo-app**

1. Create a ClusterIP Service for accessing the todo-app from within the cluster
    

```plaintext
vim cluster-ip-service.yml
cat cluster-ip-service.yml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696362895018/191dfdef-4af5-4bce-b72a-991b0d272d58.png align="center")

2\. Apply the Service definition to the cluster using the following command:

```plaintext
 kubectl apply -f cluster-ip-service.yml -n my-django-app
```

3\. Verify that the service is running by running the following command:

```plaintext
kubectl get svc -n my-django-app
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696362974307/f5f503c7-05b5-4f3b-8cc9-a071f360ef23.png align="center")

4\. Deploy another Pod in the my-django-app namespace to test the service. You can use the following YAML definition to create a simple test Pod:

```plaintext
 apiVersion: v1
 kind: Pod
 metadata:
   name: test-pod
   namespace: my-django-app
 spec:
   containers:
   - name: busybox
     image: busybox
     command: ['sh', '-c', 'while true; do wget -q -O- my-django-app-cluster-ip:8000; done']
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696363508387/de0e5c78-3d7c-4856-b7d0-da0d0385d23b.png align="center")

5\. Apply the Pod definition using the following command:

```plaintext
 kubectl apply -f test-pod.yml -n my-django-app
```

**Now go into the test pod and expose the port**

```plaintext
 kubectl exec -it test-pod -n my-django-app -- /bin/sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696363602062/468dbd3c-2999-456c-a75a-36f5f45d5f41.png align="center")

* Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696364310677/b564ce1d-e50c-4550-a6eb-6bb8837e342b.png align="center")

## [Task-3](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day34/tasks.md#task-3)

* Create a LoadBalancer Service for accessing the todo-app from outside the cluster
    
    1. Create a YAML file named load-balancer-service.yml with the following contents:
        
    
    ```plaintext
     apiVersion: v1
     kind: Service
     metadata:
       name: my-django-app-cluster-ip
       namespace: my-django-app
     spec:
       selector:
         app: django-app
       ports:
         - port: 80
           targetPort: 8000
       type: LoadBalancer
    ```
    
    Apply the LoadBalancer Service definition to your K8s cluster using the `kubectl apply -f load-balancer-service.yml -n <namespace-name>` command
    
    ```plaintext
     kubeApply the LoadBalancer Service definition to your K8s cluster using the following command:ctl apply -f load-balancer-service.yml -n my-django-app
    ```
    
    * Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster in your Namespace.
        
* ```plaintext
       kubectl get service -n=my-django-app
    ```
    
    * Verify that the LoadBalancer Service is working by accessing the todo-app from outside the cluster in your Namespace.
        
    * copy the Public IPv4 DNS and access through the browser by providing the port number in the URL
        
    * ```plaintext
         Public-IPv4-DNS:<loadbalancer-port-number>
        ```
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696364528385/bcc4ab38-8ed1-46c2-835b-49e0a0e4a4ce.png align="center")
    
* Overall, Kubernetes provides a powerful networking model that allows you to build scalable, resilient, and well-connected applications within the cluster and exposes them to external users when needed.
    
    So I encourage you to try this on your own and let me know in the comment section about your learning experience
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)