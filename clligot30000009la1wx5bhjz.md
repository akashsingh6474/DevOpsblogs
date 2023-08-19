---
title: "Day 21  Docker Important interview Questions."
datePublished: Sat Aug 19 2023 20:18:17 GMT+0000 (Coordinated Universal Time)
cuid: clligot30000009la1wx5bhjz
slug: day-21-docker-important-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692476158629/79e84658-3ad2-4ff8-ae4c-6ac68198f3c1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692476290410/8483aee5-271b-48db-bc5e-a0f096b8b099.png
tags: cloud, docker, devops, 2articles1week, 90daysofdevops

---

### **What is the Difference between an Image, Container and Engine?**

**<mark>Docker Image:-</mark>** Docker image is just a blueprint of the docker container.

**<mark>Docker Container:-</mark>** Docker container is the running instance of the docker image

**<mark>Docker Engine:- </mark>** Docker engine is platform software to manage the image and docker container to store the data.

### **What is the Difference between the Docker command COPY vs ADD?**

**<mark>Copy:- </mark>** the copy command used to copy the data from local directories to a specific location with the docker image.

**<mark>ADD:-</mark>** The `ADD` command has a similar purpose as `COPY` but offers some additional functionality. It can copy local files and directories from the host machine to the Docker image, but it also has some extra features, such as automatic URL fetching and extraction of compressed archives. The syntax of the `ADD` command is similar to `COPY`.

### **What is the Difference between the Docker command CMD vs RUN?**

<mark>RUN:- </mark> Run is used to execute commands during the image build process to modify the image's filesystem.

**<mark>CMD:-</mark>** Cmd is used to define the default command that should be executed when a container is started from the image.

Both commands play important roles in Dockerfiles to define how images are built and how containers behave when run.

### **How Will you reduce the size of the Docker image?**

You can reduce the size of the Docker images by following the below steps:

\-Use a smaller base image.

\-Minimize the number of layers.

\-Clean up unnecessary files and dependencies.

### **Why and when to use Docker?**

Docker is an open-source platform for developing, shipping and running applications in a consistent and isolated environment. It uses containerization technology to package an application and its dependencies into a single, lightweight, and portable container. Here are some key reasons why and when to use Docker:

Docker containers encapsulate an application along with its dependencies, runtime, and configuration. This ensures that the application runs consistently across different environments, from development to production. This eliminates the "it works on my machine" problem and reduces environment-related issues.

Docker images can be versioned, allowing you to roll back to previous versions of your application easily. This is useful for maintaining and reverting to known working states.

### **Explain the Docker components and how they interact with each other.**

Docker is an open-source platform for developing, shipping and running applications in a consistent and isolated environment. It uses containerization technology to package an application and its dependencies into a single, lightweight, and portable container.

**<mark>Docker Deamon:</mark>** This is the background service responsible for building, running, and managing containers.

**<mark>Docker Clients: </mark>** The command-line tool or API that interacts with the Docker Daemon.  
**<mark>Docker Images:</mark>** Images are the templates used to create Docker containers.  
**<mark>Docker Containers:</mark>** Containers are instances created from Docker images.  
**<mark>Docker Registry:</mark>** A repository for Docker images.  
**<mark>Docker Compose</mark>** A tool for defining and running multi-container applications using a YAML file.  
**<mark>Docker Networking:</mark>** Docker provides various network drivers to facilitate communication between containers and with the outside world.  
**<mark>Docker Volumes:</mark>** Volumes provide persistent data storage for containers.  
**<mark>Dockerfile:</mark>** A text file containing instructions to build a Docker image.

### **Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?**

**<mark>Docker-Compose:-</mark>** Docker compose is reduced few steps to create a docker image and docker container with the help of docker-compose you can create multiple docker containers in a single step for docker-compose to write the yaml script. then the docker container will be created in a few sec. by reducing lots of steps

**<mark>Dockerfile:-</mark>** Script for building a Docker image.

**<mark>Docker image:-</mark>** Blueprint for creating containers.

**<mark>Docker Container:-</mark>** Running instance of an image.

### **In what real scenarios have you used Docker?**

I have used Docker for:  
Development environment replication.  
Microservices deployment and scaling.

Continuous integration and delivery pipelines.

### **Docker vs Hypervisor?**

**<mark>Hypervisor:-</mark>** hypervisor is a piece of software or firmware that creates and runs the virtual machine. A hypervisor is sometimes also called a virtual machine manager (VMM).

**<mark>Docker:-</mark>** Docker is an open-source centralized platform designed to create, deploy and run applications.

docker uses a container on the host o.s. to run applications. it allows applications to use the same Linux kernel as a system on the host computer, rather than creating a whole virtual O.S.

We can install docker on any O.S. but docker can run only the same O.S.

docker is written in the 'GO' language.

### **What are the advantages and disadvantages of using docker?**

**<mark>Advantage:-</mark>**

1. No pre-allocation of RAM.
    
2. **CI Efficiency** Docker enables you to build a container image and use that same image across every step of the deployment process.
    
3. it is light in weight
    
4. It can run on physical H/w virtual H/W or on the cloud.
    
5. you can re-use the image
    
6. It took very less time to create a container.
    
    image -------&gt;container
    

**<mark>Disadvantages:</mark>**

1. Docker is not a good solution for application that requires rich GUI.
    
2. Difficult to manage a Large number of containers.
    
3. Docker doesn't provide cross-platform compatibility means if an application is designed to run in a docker container on Windows that it can't run on Linux or vice-versa.
    
4. docker is suitable when the development O.S. and testing O.S. are the same if the O.S. is different we should VM.
    

### **What is a Docker namespace?**

Mechanism to isolate processes, users, and resources in containers.

### **What is a Docker registry?**

Storage for Docker images, on Docker Hub(public) or private registries.

### **What is an entry point?**

Default command to execute when a container starts.

Using the entry point allows you to define the core functionality of the container and ensures that the desired process is always executed when the container starts. This helps make your Docker images more self-contained and easier to manage.

### **How to implement CI/CD in Docker?**

Use Docker images for consistent build and deployment environments.

Automate image creation and deployment using tools like Jenkins or GitLab CI/CD.

### **Will data on the container be lost when the docker container exits?**

Data in a container is lost if not stored in a persistent volume.

### **What is a Docker swarm?**

Native clustering and orchestration solution for Docker, managing a group of Docker nodes as a single virtual system.

### **What are the docker commands for the following:**

* view running containers
    
    ```bash
    docker ps
    ```
    

* command to run the container under a specific name
    
    ```bash
    docker run --name <container_name> <image_name>
    ```
    

* command to export a docker
    
    ```bash
    ocker export <container_id> > <output_file>.tar
    ```
    

* command to import an already existing docker image
    
    ```bash
    docker import <input_file>.tar <image_name>:
    ```
    

* commands to delete a container
    
    ```bash
    docker rm <container-name> or <container-id>
    ```
    

* command to remove all stopped containers, unused networks, build caches, and dangling images?
    
    ```bash
    docker prune -a
    ```
    

* What are the common Docker practices to reduce the size of Docker Images?
    
    **<mark>Use a Minimal Base Image:</mark>** Start with a minimal base image, such as Alpine Linux, to reduce the initial image size
    
    **<mark>Multi-Stage Builds:</mark>** This helps discard unnecessary build dependencies, resulting in a smaller final image.
    
    **<mark>Minimize Layers:</mark>** Reduce the number of layers in your Dockerfile. Combine multiple RUN commands into a single command.
    
    **<mark>Minimize Image Layers: </mark>** Avoid installing software, copying files, and running commands in separate layers if they can be combined.  
    **<mark>Remove Unnecessary Dependencies:</mark>** Avoid installing packages or dependencies that your application doesn't need.
    
    **<mark>Clean Up after installation: </mark>** Remove temporary files, caches, and unnecessary artifacts after each build step to minimize the size of the final image.
    
    **<mark>Use .dockerignore:</mark>** Use a .dockerignore file to exclude unnecessary files and directories from being copied into the image during the build process.  
    **<mark>Use COPY Instead of ADD:</mark>** Use the COPY command instead of ADD to copy files into the image. COPY only handles local files, which is safer and more predictable.  
    **<mark>Avoid running unnecessary services:</mark>** Minimize services and processes running in the container, only including what's essential for the application to function`.`