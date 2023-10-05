---
title: "Day 35: Mastering ConfigMaps and Secrets in Kubernetes🔒🔑🛡️"
datePublished: Thu Oct 05 2023 04:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clncoijs1000309mieiaihobu
slug: day-35-mastering-configmaps-and-secrets-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696368117953/ba47aeef-e5aa-4ba4-98d8-bf6d8bbbf4dc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696368173285/ae85ac2a-224f-496e-b643-3f09c990544c.png
tags: aws, k8s, secrets, configmap, 90daysofdevops

---

What is **ConfigMaps.**

In Kubernetes, a ConfigMap is a resource object that allows you to store configuration data separately from your application code. It is a key-value store where you can store configuration settings, environment variables, or any other configuration-related data that your application needs. ConfigMaps are typically used to decouple configuration from application code, making it easier to manage and update configurations without changing the code itself.

ConfigMaps are often used to store configuration files in a key-value format, such as INI files, JSON, or YAML. When you create a ConfigMap, you specify the configuration data as key-value pairs. This data can then be mounted as volumes in your pods or injected into container environments as environment variables.

### **Secrets in k8s:**

Kubernetes Secret is a way to securely store sensitive information, like passwords or API keys, that your applications running in Kubernetes need. Think of it as a locked safe for your secrets. It helps keep this sensitive data separate from your application code and makes it available to your applications when they need it, like a hidden key to access a treasure chest. This helps ensure the security of your sensitive information and makes it easier to manage.

Here are some key points about Kubernetes Secrets:

1. **Data Storage**: Secrets can store arbitrary key-value pairs of data. While they are commonly used for storing credentials, they can also be used for other types of sensitive data.
    
2. **Base64 Encoding**: Data stored in a Secret is base64-encoded. While this encoding is not secure on its own, it provides a basic level of obfuscation. Note that Kubernetes Secrets are not meant to be a strong security solution for highly sensitive data. For more secure storage and management of secrets, you might consider using a specialized secret management tool.
    
3. **Immutable**: Once created, Secrets are intended to be immutable. You cannot update the data stored in a Secret directly. Instead, you should delete and recreate the Secret with the updated data. This is done to maintain a history of changes for auditing purposes.
    
4. **Use Cases**: Secrets can be used in various scenarios, including providing database credentials to applications, supplying API tokens to services, and storing TLS certificates for secure communication.
    
5. **Mounting Secrets**: You can mount Secrets as volumes in pods or inject them as environment variables, making the sensitive data available to your application containers.
    

## [Task 1:](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day35/tasks.md#task-1)

* Create a ConfigMap for your Deployment
    
* # **Set Up MySQL Client using ConfigMap & Secrets**
    
* Create a ConfigMap for your Deployment using a file or the command line.
    
    vim configMap.yml
    
* ```plaintext
        kind: ConfigMap
        apiVersion: v1
        metadata:
          name: mysql-config
          labels:
            app: todo
        data:
          MYSQL_DB: "todo-db"
    ```
    
* Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
    

```plaintext
kubectl apply -f configMap.yml
```

* Update the deployment.yml file to include the ConfigMap
    
* Verify that the ConfigMap has been created by checking the status of the ConfigMaps in your Namespace.
    
* ```plaintext
        kubectl get configmap
    ```
    
    ## [Task 2](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day35/tasks.md#task-2)
    
    * Create a Secret for your Deployment using a file or the command line
        
    
    ```plaintext
      apiVersion: v1
      kind: Secret
      metadata:
        name: mysql-secret
      type: Opaque
      data:
        password: dHJhaW53aXRoc2h1YmhhbQ==
    ```
    
    We can Encode & decode the Base64 key by ourselves.
    
* Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
    
* Verify that the Secret has been created by checking the status of the Secrets in your Namespace.
    
* ```plaintext
        kubectl get secrets
    ```
    
    Now update the deployment.yml file to include the configMap & Secret
    

```plaintext
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: mysql
    labels:
      app: mysql
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: mysql
    template:
      metadata:
        labels:
          app: mysql
      spec:
        containers:
        - name: mysql
          image: mysql:8
          ports:
          - containerPort: 3306
          env:
          - name: MYSQL_ROOT_PASSWORD
            valueFrom:
              secretKeyRef:
                name: mysql-secret
                key: password
          - name: MYSQL_DATABASE
            valueFrom:
              configMapKeyRef:
                name: mysql-config
                key: MYSQL_DB
```

```plaintext
kubectl apply -f deployment.yml
```

To verify the MySQL pods are running, we can get the MySQL pod by running the following command.

```plaintext
  kubectl get pods
```

To expose the MySQL use the K8s service, Create a service.yml file and make the configuration by headless service.

```plaintext
  apiVersion: v1
  kind: Service
  metadata:
    name: mysql-service
  spec:
    ports:
    - name: mysql
      port: 3306
    clusterIP: None
    selector:
      app: mysql
```

Now apply for the service, so that the pod is exposed.

```plaintext
  kubectl apply -f service.yml
```

Now on the Worker Node install the MySQL client on it.

```plaintext
  sudo apt install mysql-client-core-8.0
```

Now connect the MySQL to the Master node using the below command

```plaintext
  # Get inside of the mysql pod 
  kubectl exec -it mysql-b7f864b95-stmsw /bin/sh

  # Now connect the mysql using username root and password from Secret
  mysql -u root -p${MYSQL_ROOT_PASSWORD}
```

In this blog, we delved into the world of Kubernetes and explored two essential concepts: ConfigMaps and Secrets. These are crucial for managing configuration data and sensitive information in your Kubernetes applications.

In Task 1, we defined ConfigMaps and discussed how to use them to store configuration data that can be injected into your pods. This is incredibly handy for maintaining flexibility in your deployments.

Task 2 introduced us to Secrets in Kubernetes, which are designed to securely store sensitive information like passwords and API keys. We learned how to create and manage Secrets to enhance the security of our applications.

But that’s not all! We also walked through the process of setting up a MySQL client using ConfigMaps and Secrets, demonstrating real-world application of these concepts.

If you’re eager to dive deeper into the world of DevOps and Kubernetes, stay tuned for more exciting blogs. I’m always eager to hear your questions, experiences, and suggestions, so please don’t hesitate to leave a comment below.