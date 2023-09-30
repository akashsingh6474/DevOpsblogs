---
title: "Day 33  Working with Namespaces and Services in Kubernetes"
datePublished: Sat Sep 30 2023 17:16:08 GMT+0000 (Coordinated Universal Time)
cuid: cln6aoc7k000l0ajv2hhsfymi
slug: day-33-working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696094096621/be4bd451-f9d7-49fb-a45f-4f6224e386d4.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696094115098/7a09de99-8bca-40df-8de2-23e8e2371516.png
tags: aws, deployment, kubernetes, 90daysofdevops, namespaces

---

### **What are Namespaces?**

A namespace is a group of related elements that each have a unique name and identifier. A namespace is used to uniquely identify one or more names from other similar names of different objects, groups, or the namespace in general.

A mechanism to attach authorization and policy to a subsection of the cluster

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696091018922/004d2473-815b-490c-804c-e3f21513081c.png align="center")

### **Services in k8s:**

In Kubernetes (K8s), a Service is an abstraction that defines a logical set of pods and a policy by which to access them. Services provide a consistent way to access and discover the network endpoints of applications running within a Kubernetes cluster. They act as a bridge between the internal network of the cluster and the applications running inside it.

Here are the key points about Kubernetes Services:

1. **Stable Network Endpoint**: Services define a stable network endpoint (usually an IP address and port) that remains consistent even if the underlying pods are scaled, rescheduled, or replaced. This ensures that clients can reliably connect to the service.
    
2. **Load Balancing**: Services provide load balancing across multiple pods that belong to the same service. Traffic sent to the service's IP address is distributed among the pods, helping to evenly distribute workloads and improve availability.
    
3. **Service Types**: Kubernetes offers different types of services, including:
    
    * **ClusterIP**: Exposes the service only within the cluster. It's not accessible from outside the cluster.
        
    * **NodePort**: Exposes the service on a static port on each node's IP address, making it accessible from outside the cluster.
        
    * **LoadBalancer**: Exposes the service through an external load balancer, typically in cloud environments.
        
    * **ExternalName**: Maps the service to an external domain name, allowing access to services outside the cluster.
        
4. **Selectors**: Services use label selectors to determine which pods to route traffic to. Pods with matching labels are part of the service.
    
5. **Service Discovery**: Kubernetes DNS (Domain Name System) allows you to discover services by their DNS names within the cluster. For example, if you have a service named "my-service" in the "my-namespace" namespace, it can be accessed using the DNS name "my-service.my-namespace.svc.cluster.local."
    
6. **Internal Communication**: Services are commonly used for internal communication between microservices or different components of an application.
    
7. **External Access**: When combined with other Kubernetes resources like Ingress, services can be used to provide external access to applications.
    
8. **Session Affinity**: Services can be configured to support session affinity (sticky sessions) using the "session affinity" field. This directs traffic from a client to the same pod for the duration of a session.
    

Services play a crucial role in providing network connectivity and load balancing within a Kubernetes cluster, making it easier to build scalable and resilient applications.

### **Task:01**

* ### Create a Namespace for your Deployment
    
* Use the command `kubectl create namespace <namespace-name>` to create a Namespace
    
* Update the deployment.yml file to include the Namespace
    
* Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
    
* Verify that the Namespace has been created by checking the status of the Namespaces in your cluster.
    

step:01 check the in-build namespace in the cluster

you can write kubectl = k and namespace = ns

```plaintext
kubectl get ns # to check the namespace
kubectl create namespace <namespace-name> # to create the namespace
kubctl create namespace todo
kubectl get ns #to gets the namespace
```

Update the deployment.yml file to include the Namespace

```plaintext
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
  namespace: todo
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

Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`

```plaintext
kubeclt apply -f deployment.yml -n todo
```

* Verify that the Namespace has been created by checking the status of the Namespaces in your cluster.
    
* ```plaintext
    kubectl get namespaces
    ```
    

### **Task 2:**

### Services in Kubernetes:

**Services** in Kubernetes provide a way to abstract and expose a set of Pods as a network service. They act as an intermediary between clients and Pods, ensuring that clients can reliably connect to the appropriate Pods, even if the Pods are scaled up, down, or replaced. Services come in several types:

1. **ClusterIP**: This is the default type. It exposes the Service on an internal cluster IP, making it accessible only within the cluster. It's commonly used for internal communication between components.
    
2. **NodePort**: It exposes the Service on a static port on each node's IP address. This allows external access to the Service. While it's accessible from outside the cluster, it typically requires some form of external load balancing for production use.
    
3. **LoadBalancer**: This type requests a cloud provider's load balancer to expose the Service externally. It's suitable for applications that need external access, and it works with cloud providers that support load balancers.
    
4. **ExternalName**: This type maps the Service to an external DNS name, redirecting requests to that DNS name. It's used for accessing services outside the cluster.
    

### Load Balancing in Kubernetes:

Kubernetes uses load balancing to distribute incoming network traffic across multiple Pods or endpoints that belong to a Service. This provides high availability, scalability, and fault tolerance for applications. Here's how it works:

* When you create a Service of type `ClusterIP` or `NodePort`, Kubernetes sets up a virtual IP address for the Service. For `NodePort`, it also opens a specific port on each node.
    
* When clients send requests to the Service's IP address and port, the Kubernetes Service acts as a load balancer. It selects one of the Pods that match the Service's selector and forwards the request to that Pod.
    
* The load balancer evenly distributes traffic across all available Pods, ensuring that no single Pod is overwhelmed with requests.
    
* If a Pod becomes unhealthy or is scaled down, the load balancer automatically adjusts and routes traffic only to healthy Pods.
    
* This load-balancing mechanism simplifies scaling applications up or down without affecting external or internal client access.
    

### Networking in Kubernetes:

Kubernetes provides a flexible and robust networking model to facilitate communication between Pods and Services. Key networking concepts include:

1. **Pod-to-Pod Communication**: Pods can communicate with each other directly using their IP addresses. Kubernetes assigns each Pod an IP within the cluster's network, allowing seamless communication.
    
2. **Service Discovery**: Kubernetes DNS (Domain Name System) allows Pods and Services to discover each other by name. Pods can access Services using the Service name as a DNS entry.
    
3. **Network Policies**: Network policies allow you to define rules for network communication between Pods, providing fine-grained control over traffic flow and access within the cluster.
    
4. **Ingress Controllers**: Ingress controllers manage external access to Services, typically by providing HTTP and HTTPS routing and load balancing. They allow you to define routing rules to access Services from outside the cluster.
    
5. **CNI (Container Network Interface)**: Kubernetes supports multiple CNI plugins that enable network providers to integrate their network solutions with Kubernetes. CNI plugins handle network configuration and management for Pods.
    

Overall, Kubernetes provides a powerful networking model that allows you to build scalable, resilient, and well-connected applications within the cluster and exposes them to external users when needed.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)