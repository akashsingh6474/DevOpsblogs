---
title: "Day 52: Your CI/CD pipeline on AWS - Part 3 🚀 ☁"
datePublished: Tue Oct 31 2023 17:31:57 GMT+0000 (Coordinated Universal Time)
cuid: cloelw2q3000709l04ocs27zn
slug: day-52-your-cicd-pipeline-on-aws-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698773439433/1bf2d890-6ecf-4edb-a1c7-7e2677df73fa.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698773505326/3813cff6-8974-403b-9642-22a976f60fe8.png
tags: aws, codedeploy, codecommit, 90daysofdevops, awscloud

---

## What is CodeDeploy ?

[AWS CodeDeploy](https://aws.amazon.com/codedeploy) is a fully managed deployment service that automates software deployments to a variety of compute services such as [Amazon Elastic Compute Cloud](https://aws.amazon.com/ec2) (Amazon EC2), [AWS Fargate](https://aws.amazon.com/fargate), AWS Lambda, and your on-premises servers. AWS CodeDeploy makes it easier for you to rapidly release new features, helps you avoid downtime during application deployment, and handles the complexity of updating your applications. You can use CodeDeploy to automate software deployments, reducing the need for error-prone manual operations. The service scales to match your deployment needs.

CodeDeploy has several benefits that align with the DevOps principle of continuous deployment:

* **Automated deployments** — CodeDeploy fully automates software deployments, allowing you to deploy reliably and rapidly.
    
* **Centralized control** — CodeDeploy enables you to easily launch and track the status of your application deployments through the AWS Management Console or the AWS CLI. CodeDeploy gives you a detailed report enabling you to view when and to where each application revision was deployed. You can also create push notifications to receive live updates about your deployments.
    
* **Minimize downtime** — CodeDeploy helps maximize your application availability during the software deployment process. It introduces changes incrementally and tracks application health according to configurable rules. Software deployments can easily be stopped and rolled back if there are errors.
    
* **Easy to adopt** — CodeDeploy works with any application, and provides the same experience across different platforms and languages. You can easily reuse your existing setup code. CodeDeploy can also integrate with your existing software release process or continuous delivery toolchain (for example, AWS CodePipeline, GitHub, Jenkins).
    

# [Task-01 :](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day52/tasks.md#task-01-)

* Read about Appspec.yaml file for CodeDeploy.
    
* Deploy index.html file on EC2 machine using nginx
    
* you have to setup a CodeDeploy agent in order to deploy code on EC2
    

You can refer to this link to understand how to utilize the AWS CodeCommit and CodeBuild services: [day51](https://hashnode.com/post/clod5xbkn000108l5and4d4iv) [Day50](https://hashnode.com/post/clocrj9lp000d09l8f7lb0ygl)

Let’s create a CodeDeploy application:

Navigate to CodeDeploy &gt; Applications &gt; Click on Create Application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698687343508/01ac4fd5-f84a-4a9e-aa83-6dc6f3c42a4c.png align="center")

give some details:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698687407758/c0f6366a-f587-4859-a51c-2e49f33e15af.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698687476094/27a66c24-c105-4e3a-b4bd-921b2c4b6bbc.png align="center")

We need to establish connections between CodeDeploy and other AWS services. How do we do it? We can connect the CodeDeploy to other AWS services by creating a service role in the IAM.

Navigate to Roles in IAM. And Create a New Role having these permissions:

[**AmazonEC2FullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonEC2FullAccess), [**AmazonEC2RoleforAWSCodeDeploy**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2Fservice-role%2FAmazonEC2RoleforAWSCodeDeploy), [**AmazonS3FullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonS3FullAccess), [**AWSCodeDeployRole**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2Fservice-role%2FAWSCodeDeployRole), [**AWSCodeDeployFullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAWSCodeDeployFullAccess), [**AmazonEC2RoleforAWSCodeDeployLimited**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2Fservice-role%2FAmazonEC2RoleforAWSCodeDeployLimited).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698687874619/b29a6b62-8c84-4a33-bdeb-cdb5a5795400.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698688734060/cb2e7b78-e541-4c84-9ce8-118820214aa3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698688767445/7db0af14-4bdd-425c-adcb-830698eaa4fe.png align="center")

Let us change the trust relationship:

We will need to have an EC2 instance to deploy the index.html file.

Let us create a deployment group:

In the CodeDeploy console &gt; Go to the Deployment Groups Tab &gt; Click on Create deployment group:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698688938401/7cc8c95a-6fc9-4bd0-9ac5-2cec8aec9d44.png align="center")

Deployment group name: codedeploy-group

Service role: Select the service role which you created previously with all the permissions.

Deployment type: In-place

Environment configuration: Select Amazon EC2 instances. Select the key and value to select the EC2 instance you created for this activity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698689148368/19889462-6d55-48b9-8622-a83a77efd3e8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698689231032/e1e2b7cb-a92d-4871-b6c3-8eaa3805b837.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698689456746/5de7e5a5-db97-4020-9b9e-f6e82e2dc898.png align="center")

Now let us set up a CodeDeploy agent to deploy code on EC2.

`The AWS CodeDeploy agent is a software package that is installed on instances in an Amazon EC2 Auto Scaling group or an Amazon EC2 instance. It enables the deployment of applications to these instances by interacting with the AWS CodeDeploy service.`

Install the CodeDeploy agent on your EC2 instance using the installation script.

```plaintext
#!/bin/bash
sudo apt-get update
sudo apt-get install ruby-full ruby-webrick wget -y
cd /tmp
wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/releases/codedeploy-agent_1.3.2-1902_all.deb
mkdir codedeploy-agent_1.3.2-1902_ubuntu22
dpkg-deb -R codedeploy-agent_1.3.2-1902_all.deb codedeploy-agent_1.3.2-1902_ubuntu22
sed 's/Depends:.*/Depends:ruby3.0/' -i ./codedeploy-agent_1.3.2-1902_ubuntu22/DEBIAN/control
dpkg-deb -b codedeploy-agent_1.3.2-1902_ubuntu22/
sudo dpkg -i codedeploy-agent_1.3.2-1902_ubuntu22.deb
systemctl list-units --type=service | grep codedeploy
sudo service codedeploy-agent status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698689804810/4dd9367e-0fdc-4223-908a-388f68c4a325.png align="center")

```plaintext
bash install_codedeploy_agent.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698689926446/ad23c791-0e63-4a76-9f7e-ce19f275b0fe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698690009555/916f6e74-b245-4f28-bb30-7c1654114f18.png align="center")

We can see that the CodeDeploy agent is installed and running successfully.

Let us create an index.html file. I am using my previous day’s tasks index.html file

# Task-02 :

* Add appspec.yaml file to CodeCommit Repository and complete the deployment process.
    

The contents of the appspec.yml file would look like:

```plaintext
version: 0.0
os: linux
files:
  - source: /
    destination: /var/wwiw/html
hooks:
  AfterInstall:
    - location: scripts/install_nginx.sh
      timeout: 300
      runas: root
  ApplicationStart:
    - location: scripts/start_nginx.sh
      timeout: 300
      runas: root
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698691795512/ba941101-b5e6-4775-a4ae-f0c0ac1fcb51.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698692876009/0aac3288-6eb1-42a6-a1b3-c4e3cf7ee73a.png align="center")

Let us push all the files to our CodeCommit repo.

```plaintext
git add .
git commit -m "added appspec "
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698696268482/98bb90f5-d605-4463-b278-a579e753ed78.png align="center")

```plaintext
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698696636228/d9099bcc-acea-4257-97d5-4680b305452b.png align="center")

Now let us build the project using CodeBuild. While building select the S3 for Artifacts and also enable artifact packaging (.zip).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698696968049/a74c7d84-d50c-4d9f-8e63-bede7acd2172.png align="center")

Click on Create Build project.

We can see that our build is succeeded.

Now go to the S3 and copy the location where the .zip file is located.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698700734211/34eeecb0-b074-46eb-b59a-05dd9c5d2c03.png align="center")

Click on Create Build project.

We can see that our build is succeeded.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698700910005/e3f732de-668e-428e-b8ce-369c84258157.png align="center")

Now go to the S3 and copy the location where the .zip file is located.

![](https://miro.medium.com/v2/resize:fit:875/0*XERlfTWuxFmXY7e3 align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*8i2-KZl9avfnImUi align="left")

Before that, I will have to create a Service role named new-service-role-for-ec2-s3-codedeploy for the EC2, S3, and CodeDeploy to communicate with each other, with the following permissions: [**AmazonEC2FullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonEC2FullAccess), [**AmazonS3FullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonS3FullAccess), [**AWSCodeDeployFullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAWSCodeDeployFullAccess).

We will have to attach this role to our EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698772946126/80c87a04-0c4c-476e-a7b4-a578a0d6aa6a.png align="center")

Now go to Deployment Groups &gt; For the group which we created before &gt; Revision type, S3, and paste the above S3 URL:

![](https://miro.medium.com/v2/resize:fit:875/0*i84rUXSVlfZfOs3s align="left")

And click on Create the Deployment.

Once the deployment is successful, you should be able to reach it the output file of index.html.

In this blog, I have created a repository in CodeCommit, cloned it to the local, and pushed the files from local to the CodeCommit. Then using the CodeBuild, build the application using the Nginx server and upload the artifacts to S3. CodeDeploy can deploy application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories. CodeDeploy can also deploy a serverless Lambda function.

If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [**Akash Singh.**](https://www.linkedin.com/in/akash-singh-70o) Do reach me, and I am open to suggestions and corrections.

#Day52 #90daysofdevops