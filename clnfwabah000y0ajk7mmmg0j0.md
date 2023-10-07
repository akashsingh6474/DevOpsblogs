---
title: "Day 37 Kubernetes Important interview Questions."
datePublished: Sat Oct 07 2023 10:31:01 GMT+0000 (Coordinated Universal Time)
cuid: clnfwabah000y0ajk7mmmg0j0
slug: day-37-kubernetes-important-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696674620801/973ca057-8b67-4355-9690-9836c693a84d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696674597113/400e65d6-6beb-40a4-bca0-71604dfefd5b.png
tags: kubernetes, automation, devops, k8s, 90daysofdevops

---

1. ### What is Kubernetes and why it is important?
    

Kubernetes, often abbreviated as K8s, is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. Containers are a lightweight and portable way to package and run applications and their dependencies, making it easier to develop and deploy software consistently across different environments.

Here are some key reasons why Kubernetes is important:

1. **Container Orchestration:** Kubernetes provides a powerful framework for managing containers, enabling you to define how containers should run, scale, and interact with each other.
    
2. **Scalability:** Kubernetes allows you to easily scale your applications up or down based on demand. It can automatically distribute containers across multiple servers or nodes to ensure high availability and optimal resource utilization.
    
3. **Self-healing:** Kubernetes monitors the health of your containers and can automatically replace or reschedule them if they fail. This ensures that your applications are highly available and resilient.
    
4. **Portability:** Kubernetes abstracts away the underlying infrastructure, making it easier to move applications between different cloud providers or on-premises data centers without significant code changes.
    
5. **Declarative Configuration:** You define your desired state (how many containers, which resources they need, etc.) in Kubernetes using YAML or JSON configuration files. Kubernetes then works to ensure that the actual state matches the desired state, simplifying deployment and management.
    
6. **Service Discovery and Load Balancing:** Kubernetes includes built-in service discovery and load balancing, making it easy for applications to communicate with each other and ensuring that traffic is distributed evenly to healthy instances of your services.
    
7. **Rolling Updates and Rollbacks:** Kubernetes supports rolling updates, allowing you to seamlessly update your applications without downtime. If an update causes issues, you can quickly roll back to a previous version.
    
8. **Ecosystem and Extensibility:** Kubernetes has a vibrant ecosystem with a wide range of tools and extensions, including Helm for package management, Prometheus for monitoring, and many others that can be integrated to enhance your workflow.
    
9. **Community and Adoption:** Kubernetes has gained widespread adoption in the industry, with a large and active open-source community. This means you can find ample resources, documentation, and support for Kubernetes.
    
10. **Cost Efficiency:** By optimizing resource utilization and automating management tasks, Kubernetes can help reduce infrastructure costs and improve the efficiency of your operations.
    
11. ### What is the difference between docker swarm and Kubernetes?
    

**Docker Swarm** and **Kubernetes** are both container orchestration platforms. They both help you to manage and deploy containerized applications. However, there are some key differences between the two platforms.

**Docker Swarm** is a native clustering tool for Docker. It is easy to set up and use, and it is well-suited for smaller workloads. Docker Swarm is also tightly integrated with the Docker CLI, making it a good choice for users who are already familiar with Docker.

**Kubernetes** is a more complex platform, but it is also more powerful and feature-rich. Kubernetes has built-in support for stateful applications, self-healing, and auto-scaling. Kubernetes is also more widely used than Docker Swarm, and it has a larger community of support.

Here is a table that summarizes the key differences between Docker Swarm and Kubernetes:

| **Feature** | **Docker Swarm** | **Kubernetes** |
| --- | --- | --- |
| Ease of use | Easier to set up and use | More complex to set up and use |
| Features | Fewer features | More features, including support for stateful applications, self-healing, and auto-scaling |
| Community | Smaller community | Larger community |
| Popularity | Less popular | More Popular |

1. ### **How does Kubernetes handle network communication between containers?**
    
    Kubernetes handles network communication between containers in two main ways:
    
    * **Pod-to-pod communication:** Containers in the same pod share the same network namespace, which means that they can communicate with each other using localhost.
        
    * **Pod-to-pod communication using services:** Services are a way to expose ports on a pod to other pods in the cluster. To communicate with another pod using a service, a pod can simply send traffic to the service's IP address.
        
    
    Kubernetes uses a container network interface (CNI) plugin to manage the networking between pods. The CNI plugin is responsible for allocating IP addresses to pods and enabling pods to communicate with each other.
    
    Here is an example of how pod-to-pod communication works in Kubernetes:
    
    1. Pod A wants to communicate with Pod B.
        
    2. Pod A looks up the IP address of pod B's service.
        
    3. Pod A sends traffic to the service's IP address.
        
    4. The CNI plugin routes the traffic to pod B.
        
    5. Pod B receives the traffic and responds.
        
    
    Services are the recommended way for pods to communicate with each other in Kubernetes. Services provide a number of benefits, such as:
    
    * **Load balancing:** Services can distribute traffic across multiple pods, which can improve performance and reliability.
        
    * **Service discovery:** Services provide a DNS name for a pod, which makes it easier for pods to find each other.
        
    * **Abstraction:** Services hide the implementation details of the underlying network topology, which makes it easier to deploy and manage applications.
        
    
    Kubernetes also provides a number of other networking features, such as network policies and ingress controllers. These features can be used to control the flow of traffic in and out of your cluster.
    
2. ### **How does Kubernetes handle the scaling of applications?**
    
    Kubernetes handles the scaling of applications in two ways:
    
    * **Horizontal scaling:** Horizontal scaling involves increasing or decreasing the number of replicas of a pod. This can be done manually or automatically using a HorizontalPodAutoscaler (HPA).
        
    * **Vertical scaling:** Vertical scaling involves increasing or decreasing the resources allocated to a pod, such as CPU, memory, or storage. This can be done manually or automatically using a VerticalPodAutoscaler (VPA).
        
    
    Horizontal scaling is the preferred way to scale applications in Kubernetes. Horizontal scaling is more efficient and reliable than vertical scaling, and it is also easier to manage.
    
    Here is an example of how horizontal scaling works in Kubernetes:
    
    1. A pod is running at a high CPU utilization.
        
    2. The HPA detects the high CPU utilization and scales the pod up to two replicas.
        
    3. The two replicas of the pod start running and share the workload.
        
    4. The CPU utilization of each pod decreases.
        
    5. The HPA monitors the CPU utilization and scales the pod down to one replica when the CPU utilization is low enough.
        
    
    Kubernetes also provides a number of other features that can be used to scale applications, such as:
    
    * **StatefulSets:** StatefulSets are used to manage pods that have a specific order or state. StatefulSets can be scaled up or down without losing data.
        
    * **Deployments:** Deployments are used to manage pods that are stateless. Deployments can be rolled out and rolled back in a controlled manner.
        
    * **Autoscalers:** Autoscalers can be used to automatically scale applications based on metrics such as CPU utilization, memory utilization, or request rate.
        
    
    Kubernetes makes it easy to scale applications up or down based on demand. This is one of the key benefits of using Kubernetes to run applications.
    
3. ### **What is a Kubernetes Deployment and how does it differ from a ReplicaSet?**
    
    A Kubernetes Deployment is a higher-level object that provides declarative updates to Pods along with a lot of other useful features. A Deployment manages ReplicaSets, which are lower-level objects that are responsible for ensuring that a specified number of replicas of your application are running.
    
    In other words, a Deployment is a way to manage and update a set of Pods. It provides a number of features that make it easier to manage and deploy your applications, such as:
    
    * **Rolling updates:** Deployments can be used to perform rolling updates, which are gradual updates to a set of Pods. This allows you to update your applications without downtime.
        
    * **Rollbacks:** Deployments can be rolled back to a previous version if there is a problem with a new update.
        
    * **Self-healing:** Deployments will automatically restart failed Pods and replace Pods that are unhealthy.
        
    
    ReplicaSets, on the other hand, are lower-level objects that are responsible for ensuring that a specified number of replicas of your application are running. ReplicaSets do not provide the same features as Deployments, such as rolling updates, rollbacks, and self-healing.
    
    In general, it is recommended to use Deployments instead of ReplicaSets directly. Deployments provide a number of features that make it easier to manage and deploy your applications.
    
    Here is a table that summarizes the key differences between Deployments and ReplicaSets:
    
    | Feature | Deployment | ReplicaSet |
    | --- | --- | --- |
    | Level | Higher-level | Lower-level |
    | Features | Rolling updates, rollbacks, self-healing | None |
    | Use case | Managing and updating a set of Pods | Ensuring that a specified number of replicas of an application are running |
    
4. ### **Can you explain the concept of rolling updates in Kubernetes?**
    
    A rolling update in Kubernetes is a type of update that gradually updates a set of Pods without downtime. This is done by replacing the old Pods with new Pods one at a time.
    
    To perform a rolling update, you create a new Deployment with the updated container image. The Deployment controller will then start replacing the old Pods with new Pods one at a time. The Deployment controller will only replace a Pod after the new Pod is up and running.
    
    Once all of the old Pods have been replaced with new Pods, the Deployment controller will mark the Deployment as updated.
    
    Rolling updates are a great way to update your applications without downtime. They are also a good way to test new versions of your applications before rolling them out to all of your users.
    
    Here is an example of how a rolling update works in Kubernetes:
    
    1. You create a new Deployment with the updated container image.
        
    2. The Deployment controller starts replacing the old Pods with new Pods one at a time.
        
    3. The Deployment controller ensures that there is always at least one Pod running the old version of your application.
        
    4. Once all of the old Pods have been replaced with new Pods, the Deployment controller marks the Deployment as updated.
        
    
5. ### **How does Kubernetes handle network security and access control?**
    
    Kubernetes handles network security and access control in a number of ways, including:
    
    * **Network policies:** Network policies allow you to control the flow of traffic between pods within a cluster. Network policies can be used to restrict pods from talking to each other, or to restrict pods from talking to certain services or IP addresses.
        
    * **Pod security policies:** Pod security policies allow you to control the capabilities of pods. Pod security policies can be used to restrict pods from running certain commands or accessing certain files or directories.
        
    * **Role-based access control (RBAC):** RBAC allows you to control who has access to Kubernetes resources. RBAC can be used to restrict users from creating or deleting pods, or from accessing certain services.
        
    * **Network isolation:** Kubernetes networks are isolated from each other by default. This means that pods in one cluster cannot communicate with pods in another cluster.
        
    
    1. ### **Can you give an example of how Kubernetes can be used to deploy a highly available application?**
        
    
    To deploy a highly available application using Kubernetes, you would typically follow these steps:
    
    1. Create a Deployment object for your application. The Deployment object will specify the number of replicas of your application that you want to run, and the container image that you want to use.
        
    2. Create a Service object for your application. The Service object will expose your application on a specific port.
        
    3. Configure a load balancer to distribute traffic to your application. The load balancer can be a cloud-based load balancer or a hardware load balancer.
        
    
    Once you have completed these steps, your application will be highly available. This is because Kubernetes will automatically restart failed Pods, and the load balancer will distribute traffic across the healthy Pods.
    
    Here is an example of a Deployment object for a highly available application:
    
    **YAML**
    
    ```plaintext
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: my-app
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: my-app
      template:
        metadata:
          labels:
            app: my-app
        spec:
          containers:
          - name: my-app
            image: my-app:latest
    ```
    
    This Deployment object will create three replicas of the `my-app` container.
    
    Here is an example of a Service object for a highly available application:
    
    **YAML**
    
    ```plaintext
    apiVersion: v1
    kind: Service
    metadata:
      name: my-app
    spec:
      selector:
        app: my-app
      ports:
      - protocol: TCP
        port: 80
        targetPort: 8080
    ```
    
    This Service object will expose the `my-app` container on port 80.
    
    Once you have created the Deployment and Service objects, you can configure a load balancer to distribute traffic to your application.
    
    For example, if you are using Google Cloud Platform, you can create a Cloud Load Balancing instance. To do this, you would specify the external IP address of the Service object.
    
    Once you have configured a load balancer, your application will be highly available. This is because Kubernetes will automatically restart failed Pods, and the load balancer will distribute traffic across the healthy Pods.
    
6. ### **What is a namespace in Kubernetes? Which namespace any pod takes if we don't specify any namespace?**
    

A namespace in Kubernetes is a logical isolation of resources within a cluster. Namespaces allow you to group resources together and restrict access to them. For example, you could create a namespace for each of your applications, or a namespace for each team in your organization.

If you do not specify a namespace when creating a pod, the pod will be created in the default namespace. The default namespace is a special namespace that is created automatically when you create a Kubernetes cluster.

It is recommended to use namespaces to organize your Kubernetes resources. This will help to reduce conflicts and improve security.

Here is an example of how to create a pod in a specific namespace:

```plaintext
kubectl create -n my-namespace pod my-pod --image my-image:latest
```

This command will create a pod named `my-pod` in the `my-namespace` namespace.

You can also use namespaces to restrict access to resources. For example, you could create a role that only allows users to create and delete pods in the `my-namespace` namespace.

Namespaces are a powerful feature of Kubernetes that can help you to organize and manage your resources.

1. ### **How does ingress help in Kubernetes?**
    

Ingress in Kubernetes helps to control incoming traffic to your applications. It allows you to expose your applications to the outside world without having to expose them directly to the internet.

Ingress is implemented using a Kubernetes Ingress object. The Ingress object specifies the rules for routing traffic to your applications. For example, you can use an Ingress object to route traffic to your application based on the domain name or the path of the request.

Ingress is typically used in conjunction with a load balancer. The load balancer will distribute traffic to your application based on the rules specified in the Ingress object.

1. ### Explain different types of services in Kubernetes.
    
    There are four different types of services in Kubernetes:
    
    * **ClusterIP:** ClusterIP services are the most common type of service. They expose a service to other pods within the cluster. ClusterIP services are not accessible from outside the cluster.
        
    * **NodePort:** NodePort services expose a service on a specific port on each node in the cluster. This allows the service to be accessed from outside the cluster using the NodePort port.
        
    * **LoadBalancer:** LoadBalancer services expose a service using a cloud load balancer. This allows the service to be accessed from outside the cluster using the load balancer's DNS name or IP address.
        
    * **ExternalName:** ExternalName services map a service to a pre-existing DNS name. This is useful for exposing services that are running outside of the Kubernetes cluster.
        
    
    Here is a table that summarizes the key differences between the four types of services:
    
    | Type | Description | Accessibility |
    | --- | --- | --- |
    | ClusterIP | Exposes a service to other pods within the cluster. | Not accessible from outside the cluster. |
    | NodePort | Exposes a service on a specific port on each node in the cluster. | Accessible from outside the cluster using the NodePort port. |
    | LoadBalancer | Exposes a service using a cloud load balancer. | Accessible from outside the cluster using the load balancer's DNS name or IP address. |
    | ExternalName | Maps a service to a pre-existing DNS name. | Accessible from outside the cluster using the pre-existing DNS name. |
    
    Which type of service you should use depends on your specific needs. If you need to expose a service to other pods within the cluster, then you should use a ClusterIP service. If you need to expose a service to the outside world, then you should use a NodePort, LoadBalancer, or ExternalName service.
    
    Here are some examples of when you might use each type of service:
    

* **ClusterIP:** You might use a ClusterIP service to expose a database service to other pods in the cluster.
    
* **NodePort:** You might use a NodePort service to expose a web service to the outside world.
    
* **LoadBalancer:** You might use a LoadBalancer service to expose a high-traffic web service to the outside world.
    
* **ExternalName:** You might use an ExternalName service to expose a service that is running outside of the Kubernetes cluster, such as a database that is running on a bare metal server.
    

1. ### **Can you explain the concept of self-healing in Kubernetes and give examples of how it works?**
    
    Self-healing in Kubernetes is a process by which Kubernetes automatically detects and recovers from pod failures. This is done by continuously monitoring the health of pods and restarting failed pods.
    
    Kubernetes uses a number of mechanisms to achieve self-healing, including:
    
    * **Liveness probes:** Liveness probes are used to check if a pod is still alive. If a pod fails a liveness probe, Kubernetes will restart the pod.
        
    * **Readiness probes:** Readiness probes are used to check if a pod is ready to receive traffic. If a pod fails a readiness probe, Kubernetes will not direct traffic to the pod.
        
    * **Restart policies:** Restart policies define how Kubernetes should restart failed pods. For example, a restart policy of Always will always restart failed pods, while a restart policy of Never will never restart failed pods.
        
    
    Here is an example of how self-healing works in Kubernetes:
    
    1. A pod fails due to a hardware failure.
        
    2. Kubernetes detects the pod failure.
        
    3. Kubernetes restarts the pod.
        
    4. The pod comes back up and starts serving traffic.
        
    
    Self-healing is a key feature of Kubernetes that helps to ensure the reliability of your applications. By automatically restarting failed pods, Kubernetes helps to keep your applications running even when there are problems.
    
    Here are some additional examples of how self-healing works in Kubernetes:
    
    * If a node in the cluster fails, Kubernetes will reschedule the pods on the failed node to other nodes in the cluster.
        
    * If a container within a pod fails, Kubernetes will restart the container.
        
    * If a service is unavailable, Kubernetes will redirect traffic to other instances of the service.
        
    
2. ### How does Kubernetes handle storage management for containers?
    

Kubernetes provides a variety of ways to manage storage for containers. The most common way is to use PersistentVolumes. PersistentVolumes are Kubernetes resources that provide persistent storage to containers. PersistentVolumes can be backed by a variety of storage providers, such as local disk, NFS, or cloud storage providers.

Once you have created a PersistentVolume, you can create a PersistentVolumeClaim (PVC). A PVC is a request for storage from a container. When you create a PVC, Kubernetes will automatically bind it to a PersistentVolume.

Once a PVC is bound to a PersistentVolume, you can mount the PersistentVolume to a container using a volume mount. A volume mount is a configuration option that tells Kubernetes to mount the PersistentVolume to a specific directory in the container.

1. ### **How does the NodePort service work?**
    

A NodePort service in Kubernetes is a type of service that exposes an application running inside the cluster on a specific port of each node in the cluster. This type of service makes the application accessible from outside the cluster by binding a port on each node's IP address to the service. Here's how a NodePort service works:

1. **Service Definition:** To create a NodePort service, you define it using a Kubernetes YAML or JSON configuration file. In the service definition, you specify the service type as "NodePort."
    
    Example NodePort service definition:
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-nodeport-service
    spec:
      type: NodePort
      selector:
        app: my-app
      ports:
        - targetPort: 80
          port: 8080
          nodePort: 30000
    ```
    
    In this example, the service is named "my-nodeport-service," and it exposes pods with the label "app: my-app" on port 8080. The `nodePort` field (e.g., 30000) specifies the port on each node where the service will be exposed.
    
2. **Port Allocation:** When you create or apply the service definition, Kubernetes will allocate a port from a predefined range (typically 30000-32767) on each node in the cluster. This port is the same on every node and is chosen randomly unless you specify a specific `nodePort` value in your service definition.
    
3. **Mapping to Pods:** The NodePort service forwards traffic from the allocated node ports to the pods selected by the service based on the defined selector. In the example above, pods with the label "app: my-app" are selected.
    
4. **Access from Outside the Cluster:** To access the service from outside the cluster, you need to know the IP address of any node in the cluster and the allocated node port. You can then access the service using this node's IP address and the allocated node port.
    
    For example, if you have a node with IP address 192.168.1.100 and the allocated node port is 30000, you can access the service using [`http://192.168.1.100:30000`](http://192.168.1.100:30000).
    
5. **Load Balancing:** If you have multiple nodes in your cluster, you can access the service through any of them. Additionally, you can use an external load balancer to distribute traffic across the nodes, providing load balancing for the service.
    

NodePort services are often used for development and testing purposes, but they are not recommended for production environments due to security and manageability concerns. In production, it's common to use LoadBalancer services or other Ingress controllers to expose services externally in a more controlled and secure way.

1. ### **What is a multinode cluster and a single-node cluster in Kubernetes?**
    

A multinode Kubernetes cluster is a cluster that consists of multiple nodes. A single-node Kubernetes cluster is a cluster that consists of a single node.

Multinode clusters are the most common type of Kubernetes cluster. They offer a number of advantages over single-node clusters, such as:

* **Scalability:** Multinode clusters can be scaled up or down to meet the needs of your applications.
    
* **Reliability:** Multinode clusters are more reliable than single-node clusters. If a node in a multinode cluster fails, the other nodes in the cluster will continue to operate.
    
* **Performance:** Multinode clusters can offer better performance than single-node clusters. This is because multinode clusters can distribute the workload across multiple nodes.
    

Single-node clusters are less common than multinode clusters. They are primarily used for development and testing purposes. Single-node clusters are also sometimes used for small production workloads.

Here is a table that summarizes the key differences between multinode and single-node Kubernetes clusters:

| Feature | Multinode cluster | Single-node cluster |
| --- | --- | --- |
| Number of nodes | Multiple nodes | Single node |
| Scalability | Scalable | Not scalable |
| Reliability | More reliable | Less reliable |
| Performance | Can offer better performance | Can offer good performance, but not as good as a multinode cluster |
| Use cases | Production, development, and testing | Development and testing, and small production workloads |

1. ### Difference between create and apply in Kubernetes?
    
    In Kubernetes, both `kubectl create` and `kubectl apply` are commands used to create or update Kubernetes resources, such as pods, services, deployments, and config maps, based on the definitions provided in YAML or JSON files. However, they have some key differences in how they handle resource creation and updates:
    
    1. **Create (**`kubectl create`):
        
        * `kubectl create` is primarily used for resource creation, not updates.
            
        * When you use `kubectl create` to create a resource, it will create the resource specified in the YAML or JSON file, but it won't check if the resource already exists.
            
        * If you try to create a resource that already exists (e.g., a pod with the same name), `kubectl create` will return an error, and you'll need to manually handle the conflict.
            
        * `kubectl create` is suitable for creating resources that are guaranteed not to exist in the cluster, such as during the initial setup of your application.
            
        
        Example of creating a resource:
        
        ```bash
        kubectl create -f my-pod.yaml
        ```
        
    2. **Apply (**`kubectl apply`):
        
        * `kubectl apply` is used for resource creation and updates, making it more suitable for managing resources throughout their lifecycle.
            
        * When you use `kubectl apply`, it will create the resource if it doesn't exist or update it if it does.
            
        * `kubectl apply` uses a declarative approach, where you define the desired state of the resource in the YAML or JSON file, and Kubernetes ensures that the actual state matches the desired state. If the resource already exists, it will be updated to match the new configuration.
            
        * `kubectl apply` is useful for making changes to existing resources, applying configuration updates, or ensuring that resources are consistently maintained in the desired state.
            
        
        Example of applying a resource:
        
        ```bash
        kubectl apply -f my-deployment.yaml
        ```
        
    
    Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications. It abstracts infrastructure complexities, offers robust orchestration, and supports declarative configuration. Kubernetes provides scalability, high availability, and a rich ecosystem, making it a vital tool for modern application deployment and management.
    
    So I encourage you to try this on your own and let me know in the comment section about your learning experience
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)