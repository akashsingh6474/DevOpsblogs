---
title: "Day 51: CI/CD pipeline on AWS - Part 2 🚀 ☁"
datePublished: Mon Oct 30 2023 17:17:15 GMT+0000 (Coordinated Universal Time)
cuid: clod5xbkn000108l5and4d4iv
slug: day-51-cicd-pipeline-on-aws-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698686175918/558d35c7-4c9c-448a-86b3-109c9ecb919f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698686225459/ced47385-d06c-46f7-8293-65b488fd7fc2.png
tags: aws, 90daysofdevops, codebuild, s3-bucket

---

## What is CodeBuild ?

* AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. You don’t need to provision, manage, and scale your own build servers. CodeBuild can use either GitHub, GitHub Enterprise, BitBucket, AWS CodeCommit, or Amazon S3 as a source provider.
    
    CodeBuild scales continuously and can process multiple builds concurrently. CodeBuild offers various pre-configured environments for various versions of Microsoft Windows and Linux. Customers can also bring their customized build environments as Docker containers. CodeBuild also integrates with open-source tools such as Jenkins and Spinnaker.
    
    CodeBuild can also create reports for unit, functional, or integration tests. These reports provide a visual view of how many tests cases were run and how many passed or failed. The build process can also be run inside an [Amazon Virtual Private Cloud](https://aws.amazon.com/vpc) (Amazon VPC) which can be helpful if your integration services or databases are deployed inside a VPC.
    

# **How CodeBuild Works?**

![](https://miro.medium.com/v2/resize:fit:829/0*yHRcrd8jWlBJQ_DS.png align="left")

1. As input, you must provide CodeBuild with a build project.
    
2. A *build project* includes information about how to run a build, including where to get the source code, which build environment to use, which build commands to run, and where to store the build output.
    
3. A *build environment* represents a combination of operating systems, programming language runtime, and tools that CodeBuild uses to run a build. For more information, see:
    

* [**Create a build project**](https://docs.aws.amazon.com/codebuild/latest/userguide/create-project.html)
    
* [**Build environment reference**](https://docs.aws.amazon.com/codebuild/latest/userguide/build-env-ref.html)
    

1. CodeBuild uses the build project to create the build environment.
    
2. CodeBuild downloads the source code into the build environment and then uses the build specification (buildspec), as defined in the build project or included directly in the source code. A *buildspec* is a collection of build commands and related settings, in YAML format, that CodeBuild uses to run a build. For more information, see the [**Buildspec reference**](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html).
    
3. If there is any build output, the build environment uploads its output to an S3 bucket. The build environment can also perform tasks that you specify in the buildspec. For an example, see [**Build notifications sample**](https://docs.aws.amazon.com/codebuild/latest/userguide/sample-build-notifications.html).
    
4. While the build is running, the build environment sends information to CodeBuild and Amazon CloudWatch Logs.
    
5. While the build is running, you can use the AWS CodeBuild console, AWS CLI, or AWS SDKs to get summarized build information from CodeBuild and detailed build information from Amazon CloudWatch Logs. If you use AWS CodePipeline to run builds, you can get limited build information from CodePipeline.
    

# **Buildspec file**

A buildspec file is a YAML file used in AWS CodeBuild to define the build and deployment stages of your project.

It provides instructions on how CodeBuild should build, test, and deploy your application.

# **Buildspec file name and storage location**

In AWS CodeBuild, the buildspec file should be named `buildspec.yml` or `buildspec.yaml`. It should be placed in the root directory of your source code repository.

You can use the `buildspecOverride` parameter to specify the file name and location of your buildspec.

You can specify only one buildspec for a build project, regardless of the buildspec file’s name.

# **Buildspec syntax**

The syntax used in a buildspec file is:

**COPY**

**COPY**

```plaintext
version: 0.3

phases:
  pre_build:
    commands:
      - echo "Installing dependencies..."
      - npm install

  build:
    commands:
      - echo "Building the application..."
      - npm run build

  post_build:
    commands:
      - echo "Running tests..."
      - npm test

artifacts:
  files:
    - index.html
    - dist/**
  discard-paths: yes
```

version

Required mapping. Represents the buildspec version. We recommend that you use `0.2`.

run-as

Optional sequence. Available to Linux users only. Specifies a Linux user that runs commands in this buildspec file. `run-as` grants the specified user read and run permissions. When you specify `run-as` at the top of the buildspec file, it applies globally to all commands.

env

Optional sequence. Represents information for one or more custom environment variables.

* env/shell: Optional sequence. Specifies the supported shell for Linux or Windows operating systems.
    
* env/variables: Required if `env` is specified, and you want to define custom environment variables in plain text.
    
* env/parameter-store: Required if `env` is specified, and you want to retrieve custom environment variables stored in Amazon EC2 Systems Manager Parameter Store.
    
* env/secrets-manager: Required if you want to retrieve custom environment variables stored in AWS Secrets Manager.
    
* env/exported-variables: Used to list environment variables you want to export.
    
* env/git-credential-helper: Used to indicate if CodeBuild uses its Git credential helper to provide Git credentials.
    

proxy

Used to represent settings if you run your build in an explicit proxy server. Optional setting.

phases

Required sequence. Represents the commands CodeBuild runs during each phase of the build.

artifacts

Optional sequence. Represents information about where CodeBuild can find the build output and how CodeBuild prepares it for uploading to the S3 output bucket.

# [Task-01 :](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day51/tasks.md#task-01-)

* Read about the Buildspec file for Codebuild.
    
* create a simple index.html file in the CodeCommit Repository
    
* you have to build the index.html using nginx server
    

I am using the repository that was used.

Clone the repository using git clone.

Create an index.html file.

```plaintext
vim index.html
```

The contents of index.html would be:

```plaintext
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Akash Singh - DevOps Engineer</title>
    <link rel="stylesheet" href="styles.css"> <!-- Link to your CSS file -->
</head>
<body>
    <header style="background-color: #333; color: #f0f0f0;">
        <h1>Akash Singh</h1>
        <p>DevOps Engineer</p>
    </header>

    <section id="about" style="background-color: #f0f0f0; color: #333;">
        <h2>About Me</h2>
        <p>Hello, I'm Akash Singh, a passionate DevOps engineer with expertise in automating, optimizing, and streamlining development and deployment processes. I am dedicated to enhancing collaboration between development and IT operations to deliver high-quality software efficiently.</p>
    </section>

    <section id="skills" style="background-color: #333; color: #f0f0f0;">
        <h2>Skills</h2>
        <ul>
            <li>Continuous Integration/Continuous Deployment (CI/CD)</li>
            <li>Containerization (Docker, Kubernetes)</li>
            <li>Infrastructure as Code (Terraform, Ansible)</li>
            <li>Scripting and Automation (Bash, Python)</li>
            <li>Version Control (Git)</li>
        </ul>
    </section>

    <section id="projects" style="background-color: #f0f0f0; color: #333;">
        <h2>Projects</h2>
        <div class="project">
            <h3>Project 1 Title</h3>
            <p>Description of Project 1. This project involved implementing a CI/CD pipeline for an e-commerce application, resulting in faster and more reliable deployments.</p>
        </div>

        <div class="project">
            <h3>Project 2 Title</h3>
            <p>Description of Project 2. This project focused on containerizing legacy applications and managing them with Kubernetes for scalability and resilience.</p>
        </div>
        <!-- Add more projects as needed -->
    </section>

    <section id="contact" style="background-color: #333; color: #f0f0f0;">
        <h2>Contact Me</h2>
        <p>If you'd like to contact me, please send an email to <a href="mailto:akash@example.com">akash@example.com</a>.</p>
    </section>

    <footer style="background-color: #f0f0f0; color: #333;">
        <p>&copy; 2023 Akash Singh</p>
    </footer>

    <script src="script.js"></script> <!-- Link to your JavaScript file -->
</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698664266803/6c44672e-cd3f-46fc-b0f6-28d191ea2876.png align="center")

Add these changes and commit to the repository.

```plaintext
git add. 
git status
git commit -m "this is my index file"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698664451823/7a3a5cb9-cd60-48a9-a678-affdd5f4a66a.png align="center")

Let us push these changes to the CodeCommit repository.

```plaintext
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698664541772/b935a231-dda3-4ce7-8165-5a1adb2094f1.png align="center")

Verify the same in the CodeCommit.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698664613067/f86b89b6-f4fd-4b57-b0b7-341d9b8137f7.png align="center")

Now Let us create the buildspec.yaml file and push it to our repository.

```plaintext
vim buildspec.yml
```

```plaintext
version: 0.2

phases:
  install:
    commands:
      - echo Installing NGINX
      - sudo apt-get update
      - sudo apt-get install nginx -y
  build:
    commands:
      - echo Build started on 'date'
      - cp index.html /var/www/html/
  post_build:
    commands:
      - echo Configuring NGINX

artifacts:
  files:
    - /var/www/html/index.html
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698664912996/cc403c77-9872-4e03-a1b1-abbee553c551.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665028568/51853b5c-56ee-4c8b-9ef4-6a5d73e1d886.png align="center")

Now push to Rrepository

```plaintext
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665139522/76717503-a3f1-439d-beb1-ae98149b551f.png align="center")

And now verify in the repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665204296/01d27fe3-af5f-4692-81a1-291a1b277db8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665224349/5d973bf7-fcad-4e3d-a449-cf635110e210.png align="center")

In the left navigation panel &gt; Go to Build: CodeBuild &gt; Build Projects &gt; Click on Create Build Projects

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665352149/5b8a7eb4-d60a-4b5f-ba34-7a410cc58fa6.png align="center")

Project name: codebuild

In the source section, Select AWS CodeCommit as Source Provider and select the repository, and branch your code is hosted.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665631546/c94389ca-d77e-4042-80ea-79cc2ad488be.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665828016/5c0b9b35-d740-449c-ad32-49a0ef95ce21.png align="center")

In the Environment section, Select OS as Ubuntu.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698665918058/a6c0844e-3e0d-40f1-9964-f018e430a5f7.png align="center")

And create a New Service Role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698666016234/f44d1cef-93ce-4494-bd0f-10729f93ddfb.png align="center")

And let others be the default, click on Create build project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698666124419/1e725985-2686-4423-9a8a-a91a214c87cc.png align="center")

Click on Start Build. Wait until the build succeeds.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698666217326/84f7ee21-e004-4d63-a311-b4fad85068ab.png align="center")

We add these artifacts to the project and store them in an S3 bucket.

First, let us create an S3 Bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698684771051/1510b978-1d11-4d3f-b9a4-806fde9fd1c5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698684795616/54d1f96a-16b8-406a-b552-7be156aa1086.png align="center")

Now In the CodeBuild &gt; Build console &gt; Click on Edit &gt; Artifacts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698684961433/e92ba5cd-5434-4717-972c-751e962bb84c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698685614962/cf6af73a-1f9c-49d0-9095-228cdc9b36ca.png align="center")

Click on Build again.

Once the build is successful, you can see that the artifacts are uploaded to the S3 bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698685712519/56a9c036-383a-4735-a73f-2a19ec2fa825.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698685745638/754119eb-5b05-48cd-bdb7-c81b621bc008.png align="center")

Navigate through the index.html file in the CodeBuild:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698685796546/f93fc41a-08cc-4246-9c04-cdd3ac3f42e5.png align="center")

Use the Open tab to reach the server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698685857287/208e9d9d-cd2b-43ce-9a26-dbb953d40777.png align="center")

In this blog, I have created a repository in CodeCommit, cloned it to the local, and pushed the files from local to the CodeCommit. Then using the CodeBuild, build the application using the Nginx server and uploaded the artifacts to S3. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [**Akash**](https://www.linkedin.com/in/akash-singh-70o/) **Singh**. Do reach me, and I am open to suggestions and corrections.

#Day51 #90daysofdevops #happylearning #AWS