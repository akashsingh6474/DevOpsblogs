---
title: "Day 36  Managing Persistent Volumes in Your Deployment 💥"
datePublished: Fri Oct 06 2023 04:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clne3yg85000e09ju0eij7dod
slug: day-36-managing-persistent-volumes-in-your-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696368814217/015ea144-a7c2-46f3-9cba-63e476e3449e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696368859162/0616e3b2-6c52-43d2-9fe9-84b8ff6fc7d2.png
tags: kubernetes, devops, scalability, k8s, 90daysofdevops

---

# **Persistent Volumes (PV) in K8s**

* Persistent Volumes (PVs) are a mechanism to provide persistent storage for applications running in the cluster. PVs represent a piece of network-attached storage that is provisioned by the cluster administrator.
    
* A Persistent Volume is a cluster-level resource that decouples storage from individual pods or applications. It has a lifecycle independent of any specific pod and can be dynamically provisioned or statically created.
    
* PVs have configurable properties such as capacity, access modes (e.g., ReadWriteOnce, ReadOnlyMany, ReadWriteMany), and storage class (a way to dynamically provision PVs). They can be dynamically provisioned by storage providers, or manually created and managed by the cluster administrator.
    
* PVs can be backed by various storage types, including local storage, network-attached storage (NAS), cloud storage, or other external storage systems. They provide a persistent and reliable storage solution for applications, allowing data to persist even if the associated pod is deleted or rescheduled.
    

# **Persistent Volume Claim (PVC) in K8s**

* Persistent Volume Claim (PVC) is a resource that allows applications to request specific storage resources from available Persistent Volumes (PVs). PVCs act as a “claim” on a PV, specifying the desired storage capacity, access modes, and other requirements.
    
* When an application requires persistent storage, it creates a PVC with the desired characteristics. Kubernetes then matches the PVC with an appropriate PV based on the PVC’s specifications, such as storage capacity, access modes, and storage class.
    
* Once a PVC is bound to a PV, the PV becomes exclusively used by the application associated with the PVC. The application can then mount the PVC as a volume in its pods and use it for storing and retrieving data. The PVC provides a stable and portable way for the application to access the requested storage.
    

# **Benefits of having PV and PVC in k8s**

1. **Improved High Availability:** By using PVs and PVCs, applications can achieve high availability and fault tolerance. PVs can be backed by replicated storage systems, ensuring data redundancy and availability.
    
2. **Abstraction and Portability:** PVs and PVCs abstract the underlying storage details from applications. This allows applications to request and use storage resources in a standardized and portable manner.
    
3. **Ease of Scaling and Migration:** With PVs and PVCs, applications can easily scale by dynamically provisioning additional PVs or increasing the capacity of existing PVs.
    
4. **Data Persistence:** PVs and PVCs ensure that data persists even if a pod or application is terminated or rescheduled. The decoupling of storage from pods allows the data to be retained in the PV, ensuring data durability and availability.
    
5. **Resource Management:** PVs and PVCs provide better resource management by separating storage from applications. Administrators can define storage classes and allocate appropriate storage resources to different PVCs based on capacity, access modes, and other criteria.
    
6. **Dynamic Provisioning:** PVCs support dynamic provisioning, where the cluster automatically creates PVs to fulfill the storage requirements specified in the PVC. This enables on-demand storage allocation and eliminates the need for manual PV creation.
    
7. **Flexibility and Customization:** PVCs allow applications to request storage resources with a specific capacity, and access modes (e.g., ReadWriteOnce, ReadOnlyMany, ReadWriteMany). This flexibility enables applications to choose the appropriate storage characteristics that align with their needs, ensuring optimal performance, security, and data access patterns.
    

# **Task 1: Add a Persistent Volume to your Deployment todo app.**

Create a Persistent Volume using a file on your node.

vim pv.yml

```plaintext
  apiVersion: v1
  kind: PersistentVolume
  metadata:
    name: pv-todo-app
  spec:
    capacity:
      storage: 1Gi
    accessModes:
      - ReadWriteOnce
    persistentVolumeReclaimPolicy: Retain
    hostPath:
      path: "/tmp/data"
```

Now apply the persistent volume.

```plaintext
  kubectl apply -f pv.yml
```

Create a Persistent Volume Claim that references the Persistent Volume.

vim pvc.yml

```plaintext
  apiVersion: v1
  kind: PersistentVolumeClaim
  metadata:
    name: pvc-todo-app
  spec:
    accessModes:
      - ReadWriteOnce
    resources:
      requests:
        storage: 500Mi
```

![](https://miro.medium.com/v2/resize:fit:875/1*0cD2GNa_-Pmcfa0byBb-eA.png align="left")

Now apply the Persistent Volume Claim by using following command.

```plaintext
  kubectl apply -f pvc.yml
```

Update your deployment.yml file to include the Persistent Volume Claim. After Applying pv.yml pvc.yml to your deployment file.

```plaintext
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: todo-app-deployment
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: todo-app
    template:
      metadata:
        labels:
          app: todo-app
      spec:
        containers:
          - name: todo-app
            image: akash6474/django-todo
            ports:
              - containerPort: 8000
            volumeMounts:
              - name: todo-app-data
                mountPath: /app
        volumes:
          - name: todo-app-data
            persistentVolumeClaim:
              claimName: pvc-todo-app
```

Apply the updated deployment using the command:

```plaintext
  kubectl apply -f deployment.yml
```

Verify that the Persistent Volume has been added to your Deployment by checking the status of the Pods and Persistent Volumes in your cluster. Use this commands `kubectl get pods` ,`kubectl get pv`

```plaintext
  # Getting details of Persistent Volume
  kubectl get pv

  # Getting details of Persistent Volume Claim
  kubectl get pvc

  # Getting the pvc details of the application
  kubectl describe pvc pvc-todo-app
```

# **Task 2: Accessing data in the Persistent Volume,**

* Connect to a Pod in your Deployment using the command :
    
* `kubectl exec -it -- /bin/bash`
    
* Verify that you can access the data stored in the Persistent Volume from within the Pod by creating a file inside the `/app` directory on the worker node using the following command:
    

```plaintext
  # Getting the pods details
  kubectl get pods

  # Get into one of the pod
  kubectl exec -it <pod-name> /bin/bash

  # Now change dir to /app
  cd /app/

  # Create a file test.txt and put some content into it
  echo "Hello" > /app/test.txt

  # Verify the file is present in the dir or not.
  ls
```

Now, delete that pod where we create a file. By deleting the deployment of pod and checking if the file in the new pod is created after applying the deployment again in the server.

```plaintext
  # Checking total pods
  kubectl get pods

  # Deleting the existing pod
  kubectl delete pod <pod-name>
```

As Auto healing is there, a new pod is generated after the old pod is deleted. Aand verify the file you have created on the worker node:

```plaintext
  #Get the docker container name of newly created pod
  docker ps

  # Now get into the newly cretaed pod
  docker exec -it <pod-name> /bin/bash

  # Then change dir to /app
  cd /app/

  # List down all the file, and we can see the file we create before is present
  ls

  # Now Read the existing file. And we had the same file and file content is also same.
  cat test.txt
```

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**