---
title: "DevOps Project-01/02"
datePublished: Sun Feb 11 2024 15:14:17 GMT+0000 (Coordinated Universal Time)
cuid: clshnbs6z00000ajt7mahbrnq
slug: devops-project-0102
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707670185476/201d362a-d14b-4385-ab6d-8818214fe56a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707670204305/9645ec19-5061-4aa8-ab7c-25fef64ca091.png
tags: cloud, automation, devops, jenkins, cicd-cjy1vtdk2005kjjs17n8couc3, 90daysofdevops

---

we embark on a DevOps project centered around deploying a Django notes app on an EC2 instance through a Jenkins declarative CI/CD pipeline. Leveraging Docker containers and Docker Hub for efficient containerization and image management, our focus is on automating the deployment process, ensuring a seamless integration and delivery of the application.

![Build a Docker Jenkins Pipeline to Implement CI/CD Workflow | by Âdithya K  | Medium](https://miro.medium.com/v2/resize:fit:1358/1*yOGabRyBdOz3xBlWvN56SQ.jpeg align="left")

**Follow the steps:**

1.     First of all, go to AWS portal, and create a new instance. As,

·       Name: jenkins-server

·       AMI: ubuntu.

·       Instance type: t2.micro (free tier).

·       Key pair login: Create &gt; docker.pem.

·       Allow HTTP.

·       Allow HTTPS.

(Download the .pem file.)

Click on Launch Instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707657793531/586bc05d-2103-4030-b9cf-af68cf0d4e4f.png align="center")

2.     Now, connect to the EC2 instance that you have created. Copy the SSH from server:

3\. Now installation of docker on your Linux Machine.

```plaintext
sudo apt-get install docker.io -y
 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707658148099/b5d822b8-4aec-49aa-81dd-2b9ae891eaea.png align="center")

## 4\. **OpenJDK-17-JRE Installation:**.

```plaintext
 sudo apt install openjdk-17-jre
#verify that is installed or not
java --version 
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707658367476/65169cdf-41f1-4a50-8eba-9ea2c2e48e3f.png align="center")

## **5\.** [**Jenkins Installation:**](https://www.jenkins.io/doc/book/installing/)

```plaintext
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

verify the Jenkins is installed or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707658983966/6cf56269-f757-4183-a527-82a3ff2f19e8.png align="center")

```plaintext
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659042751/6f3e7645-44b8-445f-ad41-67f4ebe0bfcc.png align="center")

### 6.**Docker Compose Installation:**

```plaintext
 sudo apt-get install docker-compose
```

Ensure you have these packages installed on your system. Additionally, add users to the Docker group for proper permissions. Run the following commands:

```plaintext
sudo usermod -aG docker $USER
sudo usermod -aG docker jenkins
sudo reboot
```

7\.  Now, we will allow ports 8080 and 8001 for this machine from a security group. We can find the security group in the VM description. Now, here we need to allow “Inbound Rule” as below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659466044/f1668ba3-acbb-4487-a0b3-bbb0c4e7a070.png align="center")

8.Now, Copy the Public Ip of the machine and paste it to the browser to access the Jenkins portal. As,

54.205.200.200:8080

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659575828/0ad2b00e-eb0e-4fa0-b631-ac5fe4315d4a.png align="center")

We need an Administrator Password to unlock this. For that, go to the provided highlighted path in the upper screenshot.

```plaintext
 sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659651409/1512a2b3-bc23-459b-b788-305185992ad0.png align="center")

Paste this password in the “Administrator Password” Column.

9. Now Click on, “Install Suggested Plugins”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659778811/c9f5b6bb-bd3e-46ba-911d-4fffeb7871fb.png align="center")

10.  This will now install the suggested plugins. As

![No alt text provided for this image](https://media.licdn.com/dms/image/D4E12AQFnnAIlqOHZuQ/article-inline_image-shrink_1500_2232/0/1671638236172?e=1713398400&v=beta&t=sICOtp6wVe-p92gf85E-xpSfci9MIYdZvZAy5yfbnmc align="left")

11.  Now, Jenkins will ask us to create the First Admin User.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707659958308/537d3d6a-334a-4422-aacd-ce9fd30dd6cc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660006064/8c815409-4361-49a6-9714-a8c0bdc9a28b.png align="center")

Jenkins dashboard Look like this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660070078/9c2ff1c4-39b9-4fa2-8a76-7c53311d0e0c.png align="center")

12.  Now, we will create a CI/CD pipeline, which will fetch the code from GitHub.

13.From Jenkins Dashboard, Click on “New Item”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660190292/fff01c88-a88a-4416-b512-727f3ecc8634.png align="center")

Now, Add name as

Name: todo-app

Project: Freestyle project

Click “Ok”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660258144/6f08284b-e972-4151-942e-7dd5becd55bd.png align="center")

14\. Here give the description about the project and give the information about the source code management etc.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660317511/2ab8b5e5-95cb-448e-bd6d-762436a2dbb3.png align="center")

 15. Now we have to configure pipeline as follows

Dashboards &gt; node-todo &gt; configuration &gt; general

Check✅Github project

project url: [https://github.com/akashsingh6474/node-todo-app](https://github.com/akashsingh6474/node-todo-app)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660730824/357d2517-6b7f-4e3d-9b02-be02e218a1cd.png align="center")

Check ✅GitHub hook trigger for GITScm polling

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707660786410/225affaa-0c19-43d9-be74-9174e50c9853.png align="center")

Put this basic Declarative pipeline code in script dialog box

```plaintext
pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Cloning the code'
            }
        }
        stage('Build') {
            steps {
                echo 'This is Build Stage'
            }
        }
        stage('Push to Docker hub') {
            steps {
                echo 'This is Test stage'
            }
        }
        stage('Deployement') {
            steps {
                echo 'Deploying container'
            }
        }
    }
}
```

This Jenkins declarative pipeline outlines a flexible CI/CD workflow:

1. `agent any:`: Allows the pipeline to run on any available Jenkins agent.
    
2. `stages:`: Defines logical steps in the process.
    
    a. `stage('Clone Code'):`: Clones the source code repository.
    
    b. `stage('Build'):`: Builds the application, running tests and generating artifacts. c. `stage('Push to Docker Hub'):`: Pushes built artifacts to Docker Hub.
    
    d. `stage('Deployment'):`: Deploys the application or container to the target environment.
    
    Each stage can include more complex logic. By automating these stages, Jenkins ensures a consistent and reproducible workflow for software CI/CD. 🚀
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707661012136/8a9327ff-1088-48b6-84b5-50a12b93e8b7.png align="center")
    
      
    Now Click on Save button and start the build on pipeline page.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707661321040/719c083f-ae3b-43b7-b281-2e298ccd2dcc.png align="center")
    
    * After getting success, you can see stages are green boxes with execution time.
        
    
    ## **  
    Developing the Notes App Code: To develop the Django notes app code, follow these steps:**
    
    1. Clone the code: In the pipeline script, add the following code to clone the code from your repository:
        
    2. ```plaintext
        git url : "https://github.com/akashsingh6474/django-notes-app.git", branch: "main"
        ```
        
    
    Build the code: Add the following code to build the application and create docker image with tag.
    
3. ```plaintext
    sh "docker build -t notes-app ."
    ```
    
    Push to Docker Hub: Add the code to push the Docker image to Docker Hub:
    
    For docker login in pipeline you have to create docker credentials and use them as environment variable
    
    Create Credentials in Dashboard &gt; Manage jenkins &gt; Credentials &gt; System &gt; Global credentials
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707661724384/0d8967c9-038f-4a13-ae60-b5dc35bae51e.png align="center")
    
4. ```plaintext
    withCredentials([usernamePassword(credentialsId:"dockerhub-login",passwordVariable:"dockerhubpass",usernameVariable:"dockerhubuser" )]){
        sh "docker tag notes-app ${env.dockerhubuser}/notes-app:latest"
        sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}" 
        sh "docker push ${env.dockerhubuser}/notes-app:latest"
    }
    ```
    
    1. `withCredentials`: This is a Jenkins pipeline step provided by the "Credentials Binding Plugin." It allows you to securely retrieve and use credentials within the block. In this case, we are retrieving the Docker Hub credentials using the `usernamePassword` method.
        
    2. `usernamePassword(credentialsId: "dockerhub-login", passwordVariable: "dockerhubpass", usernameVariable: "dockerhubuser")`: This line retrieves the username and password from the Jenkins credentials store. The `credentialsId` parameter specifies the unique identifier of the stored Docker Hub credentials. The `usernameVariable` and `passwordVariable` parameters define the environment variables where the username and password will be stored, respectively. The environment variables are prefixed with `env.` in Jenkins, which is why you see `env.dockerhubuser` and `env.dockerhubpass` later in the code.
        
    3. `sh "docker tag notes-app ${env.dockerhubuser}/notes-app:latest"`: This line creates a new Docker image tag with the Docker Hub username as a prefix. The `notes-app` is the original local image name, and we're tagging it with the new name `${env.dockerhubuser}/notes-app:latest`. This is necessary to ensure that the image can be pushed to the Docker Hub registry with the correct repository name.
        
    4. `sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}"`: This line runs the `docker login` command to authenticate with Docker Hub using the username and password retrieved from the Jenkins credentials store. The `-u` flag specifies the Docker Hub username, and the `-p` flag specifies the password.
        
    5. `sh "docker push ${env.dockerhubuser}/notes-app:latest"`: This line pushes the tagged Docker image to the Docker Hub registry using the `docker push` command. After authentication, the image is pushed to the repository specified by `${env.dockerhubuser}/notes-app:latest`.
        
    
    ### **Deployment: Finally, deploy the code on the EC2 instance using the following code:**
    
    ```plaintext
    sh "docker-compose down && docker-compose up -d"
    ```
    
    Here is the full Declarative pipeline code for django-notes-app deployment on ec2 using docker container.
    
5. ```plaintext
    pipeline {
        agent any
    
        stages {
            stage('Clone Code') {
                steps {
                    echo 'Cloning the code'
                    git url: "https://github.com/akashsingh6474/django-notes-app.git", branch:"main"
                }
            }
            stage('Build') {
                steps {
                    echo 'This is Build Stage'
                    sh "docker build -t notes-app ."
                }
            }
            stage('Push to Docker hub') {
                steps {
                    echo 'Pushing image to dockerhub'
                    withCredentials([usernamePassword(credentialsId:"dockerhub_login",passwordVariable:"dockerhubpass",usernameVariable:"dockerhubuser" )]){
                    sh "docker tag notes-app ${env.dockerhubuser}/notes-app:latest"
                    sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass}" 
                    sh "docker push ${env.dockerhubuser}/notes-app:latest"
                    }
    
                }
            }
            stage('Deployement') {
                steps {
                    echo 'Deploying container'
                    sh "docker-compose down && docker-compose up -d"
                }
            }
        }
    }
    ```
    

Whenever the developer commits their code in GitHub, after every commit, it should reflect in the live web app.

· For that, we will use “github webhook”.

· Every time, a developer made a commit, a trigger will run automatically, which will rebuild the image and run a container on your behalf as a part of automation that will run the pipeline automatically.

* go to on your github repository &gt; setttings &gt; Webhook &gt; Payload URL &gt; put your jenkins public ip address &gt; “add webhook”
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707662761701/2c08fdd2-febb-4cae-9629-db0a9f1099a6.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707662805089/bf0c3976-47c9-417b-94f5-27e82defde89.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707662923304/10213cb6-ea13-4dc7-8a36-0c84514d5dbf.png align="center")
    
    * Do some changes in the code and push to GitHub, this will automatically run a pipeline, and the new code will be Live.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707663272922/537ab63d-0958-4154-aecb-c0740d545297.png align="center")
    
    * Now Here is the our app is live and working fine.
        
    
    54.205.200.200:8000
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707663315126/0de95672-a481-47ce-a27b-895684d7cd31.png align="center")
    
    Thank you for enjoying my DevOps blog! Your positive response fuels my passion to dive deeper into technology and innovation.
    
* Stay tuned for more captivating DevOps articles, where we'll explore this dynamic field together. Follow me on **Hashnode** and connect on **LinkedIn** ([https://www.linkedin.com/in/akash-singh-70o/](https://www.linkedin.com/in/akash-singh-70o/)) for the latest updates and discussions.