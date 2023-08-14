---
title: "Day 18 Docker Compose for DevOps Engineers"
datePublished: Mon Aug 14 2023 13:15:57 GMT+0000 (Coordinated Universal Time)
cuid: cllawefjl000808mb13dw9b6i
slug: day-18-docker-compose-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692018328076/89051fba-7dd8-4dde-bc5e-181a698da99a.png
tags: devops, yaml, docker-compose, 2articles1week, 90daysofdevops

---

### **⚓🦈Docker Compose:**

docker Compose is a tool that helps to build and run the container in one command if you use docker Compose you don't need to write 3-4 commands manually.

With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691500763314/ad649202-f945-45dd-ba59-59b3d2c91bbc.jpeg?auto=compress,format&format=webp align="left")
    

## **⚓What is YAML?**

Yaml is a human-readable data serialization language that is often used for writing the configuration file deploying whom you ask. Yaml stands for yet another markup language or aint markup language (a recursive acronym) with emphasizes that YAML is for data, not documents.

It is easy to read and understand.

Yaml is used by the Ansible automation tool to create automation processes in the form of an Ansible playbook.

Yaml files use a.yml or .yaml

It supports JSON files.

There are no format symbols, like closing tags, curly brushes square bracts.

It is simple to use and in the Python style.

In the 3 dashes is used to signal the stand of a document and (...) is used to and the document.

### **🦋Tasks:**

Learn how to use the docker-compose.yml file, to set up the environment, configure the services and links between different containers, and also to use environment variables in the docker-compose.yml file.

`docker-compose.yml` is a configuration file used by Docker Compose to define and manage multi-container Docker applications. This YAML file allows you to specify various components of your application, such as services, networks, and volumes, along with their configurations and relationships.

1. **Services**: Each service represents a container in your application. You can specify the image to use, environment variables, ports, volumes, and other container-specific settings for each service.
    
2. **Networks**: You can define custom networks for your services to communicate with each other. This helps in isolating and securing communication between containers.
    
3. **Volumes**: Define persistent data storage locations (volumes) that can be mounted into containers. Volumes ensure that data is preserved even if containers are destroyed and recreated.
    
4. **Environment Variables**: Set environment variables for your services to configure their behavior.
    
5. **Dependencies**: You can define dependencies between services, ensuring that one service starts only after another service is up and running.
    
6. **Scaling**: You can specify the desired number of replicas for each service to scale horizontally based on demand.
    
7. **Resource Limits**: Configure resource limits for each service, such as CPU and memory limits.
    

By using a `docker-compose.yml` file, you can describe your entire application stack in a single document, making it easier to manage complex applications and their interdependencies. Docker Compose reads this configuration file and handles the orchestration of containers, networks, and volumes according to the defined specifications. This simplifies the deployment and management of multi-container applications while promoting consistency and reproducibility across different environments.

The simple yaml file is here.

```bash
version : "3.3"
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: mysql
    ports:
      - "3306:3306"
    environment:
      - "MYSQL_ROOT_PASSWORD=test@123"
```

**\*️⃣Pull a pre-existing Docker image from a public repository (e.g. Docker Hub) and run it on your local machine. Run the container as a non-root user (Hint- Use** `usermod` **command to give the user permission to docker). Make sure you reboot the instance after giving permission to the user.**

* To pull the existing image from the docker hub use this
    

command.

```bash
docker pull akash6474/node-app-latest:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692006443296/59c880b9-733c-43cb-b52c-97fbc993b801.png align="center")

After pulling the image then run the container.

```bash
#To run docker
docker run chandreshpatle28/todo-app:latest
#To check docker process status
docker ps
docker images
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692006857653/64604b4e-36af-4218-a280-312da64cba94.png align="center")

**\*️⃣Inspect the container's running processes and exposed ports using the docker inspect command.**

* ```bash
        #to docker inspect to check the lots of details in side the docker image
        docker inspect <image-id>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692007071312/d78f312e-6053-42f2-92a1-ffbb6edc1071.png align="center")
    
    * **Use the docker logs command to view the container's log output.**
        
    * ```bash
            docker logs <container-id>
        ```
        
    * **Use the docker stop and docker start commands to stop and start the container.**
        
    * ```bash
            #To stop docker container
            docker stop <container-id>
            #To start docker container
            docker start <container-id>
        ```
        
    * **Use the docker rm command to remove the container when you're done.**
        
    * ```bash
          docker kill <container-id>
          dokcer rm <container-id>
        ```
        
    

### **🦋How to run Docker commands without sudo?**

Make sure docker is installed and the system is updated (This is already been completed as a part of previous tasks):

sudo usermod -a -G docker $USER

Reboot the machine.

### **📍Conclusion:**

Above mentioned information is much important for a DevOps engineer we have learned about the docker-compose and learned about Yaml language what is yaml language and explained about yaml services, uses learned how to pull existing images from the docker hub and many more command about docker Embrace version control and collaboration, and your coding adventures shall know no bounds!

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [Akash Singh](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**