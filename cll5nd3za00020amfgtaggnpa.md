---
title: "Day 17  Docker Project for DevOps Engineers."
datePublished: Thu Aug 10 2023 21:04:08 GMT+0000 (Coordinated Universal Time)
cuid: cll5nd3za00020amfgtaggnpa
slug: day-17-docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691700236355/7460ca5f-3977-46e6-85a9-9c088fe66da6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691700411689/d21dbf56-b3ee-476c-8437-a43292ebdf4e.png
tags: docker, nodejs, devops, 2articles1week, 90daysofdevops

---

### **🛳️What is Dockerfile?**

Dockerfile is a text file that contains some set of instructions automation of Docker image creation. A Dockerfile specifies everything needed to set up an application or service within a container.

There are a few steps inside the Dockerfile to create a Docker image.

1. **Base Image**: The Dockerfile starts with selecting a base image from which your application will be built. The base image provides a foundation with a specific operating system and pre-installed software. For example, you might use an official Ubuntu or Alpine Linux base image.
    
2. **Instructions**: Dockerfiles consist of a series of instructions, each representing a step in the process of building the image. Common instructions include:
    
    * `FROM`: Specifies the base image.
        
    * `RUN`: Executes commands in the container during the build process.
        
    * `COPY` or `ADD`: Copies files from the host machine into the image.
        
    * `WORKDIR`: Sets the working directory within the image.
        
    * `EXPOSE`: Documents which ports the container will listen on at runtime.
        
    * `CMD` or `ENTRYPOINT`: Defines the command or executable that will run when the container starts.
        

### **\*️⃣Tasks**:

**✅Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)**

there are a few steps to creating a Dockerfile for an application

1. create a directory like a web-application name eg. node-app
    
2. Go inside the directory
    
3. git clone that from the developer repo.
    
4. Now go inside the developer repo
    
5. Now create Dockerfile and write a set of instructions that require to create a Docker image.
    
    ```bash
    mkdir node-app
    cd node-app/
    node-app git clone repository url
    node-app/repo-project-name
    vi Dockerfile
    ```
    
    ! Remember that when you create Dockerfile write <mark>D </mark> always capital
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691697545487/032e802f-8d98-410c-b369-5b2517597f46.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691697587542/d4a4666c-4117-40e2-8c7a-de676e097c16.png align="center")

**✅Build the image using the Dockerfile and run the container**

1. Now after completing the Dockerfile create a Docker image
    

```bash
docker build . -t node-app:latest
Docker images
docker run -d -p 8000:8000 node-app:latest
```

**✅Verify that the application is working as expected by accessing it in a web browser**

1. Now go to the Ec2 instance click on security click on security group
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691698170851/7af45a9f-e6f4-4d6e-a46c-4bff2b28dc0b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691698219949/18b5b892-100a-498f-8828-b5136bbfc2e2.png align="center")

1. Now click on edit inbound rules. and add rules and enable port 8000
    

with anywhere IPv4

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691698344589/4a83548b-ebe0-4aac-91b1-4a7f9b4d1d32.png align="center")

Now go on Google and copy your public address with port no.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691698441391/3a491795-08ae-4dec-ae45-59f2c43f3b94.png align="center")

Congrats your application has been deployed on AWS successfully

**✅Push the image to a public or private repository (e.g. Docker Hub )**

* Follow some steps to push your image on the docker hub/registry(private)
    
* After creating a docker image.
    
* docker login
    
* Enter your username and password
    
* Now give the tag to your image name that you have created with the new image name that you want to show on your docker hub account.
    

```bash
docker tag imagename dockerid/newimagename
```

* Now push your image on the docker hub
    

```bash
docker push dockerid/newimagename
```

* Now you can see your image on your docker hub
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691699341409/81289680-8fec-4172-8fc8-b38a1070d71f.png align="center")

you can make your docker image private:

* Click on the image that you want to do private
    
* click on public then click on setting Go on visibility mode then you can make your image privately
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691699515382/478198c4-827b-4452-82f3-1b198e562c15.png align="center")

**✅Create a Dockerfile for a simple web application Django Python app**

there are a few steps to creating a Dockerfile for an application

1. create a directory like a web-application name eg. django-app
    
2. Go inside the directory
    
3. git clone that from the developer repo.
    
4. Now go inside the developer repo
    
5. Now create Dockerfile and write a set of instrumentation that require to create a Docker image.
    
    ```bash
    mkdir django-app
    cd django-app/
    django-app git clone repository url
    django-app/repo-project-name
    vi Dockerfile
    ```
    

! Remember that when you create Dockerfile write <mark>D </mark> always capital

* Now after completing the Dockerfile create a Docker image
    

```bash
docker build . -t django-app:latest
Docker images
docker run -d -p 8000:8000 django-app:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691701385377/f4b8f05a-74dd-4d97-943f-cbc3f0c665d7.png align="center")

### **📍Conclusion:**

Above mentioned information is much important for a DevOps engineer we have leant about the docker file and what is docker file uses of docker file to create a docker image and we created a node. js and django application on AWS and push the docker image on the docker hub Embrace version control and collaboration, and your coding adventures shall know no bounds!

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn:[Akash Singh](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**