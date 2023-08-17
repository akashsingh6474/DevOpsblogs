---
title: "Day-20 Docker Cheat-sheet"
datePublished: Thu Aug 17 2023 20:18:31 GMT+0000 (Coordinated Universal Time)
cuid: cllflteqk000109lhc46ua95v
slug: day-20-docker-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692303334839/3a86f993-bcd9-4d62-86a5-d275134da5e2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692303496820/9175e910-4b1b-4b02-99ac-19947ac37273.png
tags: docker, devops, 2articles1week, 90daysofdevops, docker-cheat-sheet

---

## **⚓🛞Docker Commands Cheat Sheet**

Now that you know how Docker functions, let’s look at some of the most popular Docker command examples.

### **Docker installation and important commands:**

![Docker image management cheat sheet.](https://phoenixnap.com/kb/wp-content/uploads/2022/12/image-management-cheat-sheet.png align="left")

Create a machine on AWS with Docker installed AMI, and install Docker if not installed.

```bash
sudo apt-get install docker.io
```

To see all the images present in the local machine

```bash
docker images
```

find the images in the docker hub.

```bash
docker search <image_name>
```

To download an image from the docker hub.

```bash
docker pull <image_name>
```

To give a name to the container and run

```bash
docker run -it --name <container-name> <image_name> /bin/bash
```

To check service is starting on not

```bash
service docker status
```

```bash
service docker info
```

To start the service

```bash
service docker start
systemctl docker start
```

To stop the service.

```bash
service docker stop
```

To start the container

```bash
docker start <container-name>
```

stop container

```bash
docker stop <container_name>
```

To go inside the container

```bash
docker attach <container_name>
```

To see all the container

```bash
docker ps -a
```

to see the running container

```bash
docker ps
```

To delete the container

```bash
docker rm <container-id>
```

Exit from the container

```bash
exit
```

To delete the images.

```bash
docker rm <image_name>
```

to delete all stop container

```bash
docker rm $(docker ps -a -q)
```

to delete multiple images

```bash
docker rmi - $(docker images -q)
```

### **For creating images from docker file commands.**

```bash
docker build . -t <image_name> {-t stands for tag}
```

check process state.

```bash
docker ps -a
```

to check the images

```bash
docker images
```

To create a container from the docker image

```bash
docker run -it --name <container-name> <img-name>
```

Create docker volume

```bash
bash image
FROM OS NAME
Volume["/myvolume"]
```

create an image from Dockerfile

```bash
docker build . -t <image_name>
```

Now create container from this image

```bash
docker run -it --name <container_name> <image_name>
```

### **Docker Volume Commands.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692305807613/9551cef9-63c5-44f3-9680-bdc9fef7e755.gif align="center")

to see all the volumes

```bash
docker volume ls
```

To Create volume

```bash
docker volume create <volume_name>
```

To delete the volume.

```bash
docker volume rm <volume_name>
```

to delete all unused docker volumes

```bash
docker volume prune
```

To get volume details

```bash
docker volume inspect <volume_name>
```

To check container details

```bash
docker container inspect <container_name>
```

### **☁️Registry Commands**

If you need to interact with Docker Hub, use the following commands:

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Command</strong></p></td><td colspan="1" rowspan="1"><p><strong>Explanation</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>docker login</p></td><td colspan="1" rowspan="1"><p>Logs in to a registry</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker logout</p></td><td colspan="1" rowspan="1"><p>Logs out from a registry</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker pull mysql</p></td><td colspan="1" rowspan="1"><p>Pulls an image from a registry</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker push repo/ rhel-httpd:latest</p></td><td colspan="1" rowspan="1"><p>Pushes an image to a registry</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker search term</p></td><td colspan="1" rowspan="1"><p>Searches Docker Hub for images with the specified term</p></td></tr></tbody></table>

### **🌏Network Commands**

If you need to interact with the Docker network, use one of the following commands:

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Command</strong></p></td><td colspan="1" rowspan="1"><p><strong>Explanation</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network create networkname</p></td><td colspan="1" rowspan="1"><p>Creates a new network</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network rm networkname</p></td><td colspan="1" rowspan="1"><p>Removes a specified network</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network ls</p></td><td colspan="1" rowspan="1"><p>Lists all networks</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network connect networkname container</p></td><td colspan="1" rowspan="1"><p>Connects a container to a network</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network disconnect networkname container</p></td><td colspan="1" rowspan="1"><p>Disconnects a container from a network</p></td></tr><tr><td colspan="1" rowspan="1"><p>docker network inspect networkname</p></td><td colspan="1" rowspan="1"><p>Displays detailed information about a network</p></td></tr></tbody></table>

### **💡Conclusion:**

Docker is a great tool for anyone willing to try out containers. The learning curve can be steep if you’re unfamiliar with container-based development. Luckily, having a cheat sheet at hand can speed up the process, as all common commands are easily reachable, and you don’t need to look them up on the internet.

In this tutorial, we’ve covered the basics of Docker architecture and gone through all the basic Docker commands, all of which can be found in our downloadable Docker cheat sheet.

We hope that you found this Docker tutorial useful. If you have any questions, leave them in the comments section below.

Thank you for reading!

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)