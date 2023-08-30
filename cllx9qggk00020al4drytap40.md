---
title: "Day 26 Jenkins Declarative Pipeline"
datePublished: Wed Aug 30 2023 05:00:09 GMT+0000 (Coordinated Universal Time)
cuid: cllx9qggk00020al4drytap40
slug: day-26-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693334105845/bb046e59-b5f0-40e6-aeef-a2fef6ad8a0c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693334193491/5800bbea-b720-48fa-8438-2bc1e7f2befc.png
tags: docker, devops, jenkins, cicd-cjy1vtdk2005kjjs17n8couc3, 90daysofdevops

---

### **Introduction:**

The Jenkins Declarative Pipeline is a higher-level abstraction built on top of the traditional Jenkins Pipeline scripting language. It provides a simpler and more structured way to define continuous integration and continuous delivery (CI/CD) pipelines in Jenkins. The Declarative Pipeline uses a predefined set of stages, steps, and directives to cover common CI/CD scenarios, making it easier to create and maintain pipelines compared to writing complex Groovy scripts.

**There are two main types of Jenkins Pipelines:**

**What is a Pipeline -** A pipeline is a collection of steps or jobs interlinked in a sequence.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692366162469/f7934ab5-0942-47ce-a3c1-2d54e682ece6.jpeg?auto=compress,format&format=webp align="center")

1. **Scripted Pipeline:** This is the original Pipeline DSL for Jenkins. It involves writing Groovy scripts to define your pipeline steps. While it offers flexibility, it can sometimes become complex and harder to manage as pipelines grow in size and complexity.
    
2. **Declarative Pipeline:** Introduced as a simpler and more structured way to define pipelines, the Declarative Pipeline allows you to define pipelines using a more concise syntax. It provides a predefined set of stages, steps, and directives to cover common CI/CD scenarios, while still allowing you to customize and extend as needed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692366230454/8f8ad9c0-b7ec-4bcd-ad8e-56971ccc3c5c.jpeg?auto=compress,format&format=webp align="center")
    

# **Why you should have a Pipeline?**

Having a pipeline, specifically a CI/CD (Continuous Integration/Continuous Deployment) pipeline, is crucial for modern software development practices. It offers numerous benefits that contribute to efficient, reliable, and high-quality software delivery. Here are some compelling reasons to have a pipeline:

1. **Automation:** A pipeline automates the entire software delivery process, from code changes to deployment. This reduces the manual effort required for repetitive tasks, minimizes human error, and ensures consistency in the build, test, and deployment process.
    
2. **Faster Releases:** A pipeline facilitates continuous integration, allowing developers to integrate their code changes frequently. This leads to quicker identification and resolution of integration issues, enabling faster and more reliable releases.
    
3. **Quality Assurance:** Automated testing at various stages of the pipeline helps catch bugs and issues early in the development cycle. This ensures that the software meets quality standards and reduces the chances of defects reaching production.
    
4. **Consistency:** Pipelines enforce consistent build, test, and deployment processes across different environments. This reduces the "it works on my machine" problem and ensures that the application behaves the same way across all environments.
    
5. **Traceability:** A pipeline provides a clear record of the entire software delivery process. It becomes easier to trace back which code changes led to specific outcomes or issues, aiding in debugging and troubleshooting.
    

## **A basic example of a Declarative Pipeline:**

```plaintext
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build your application here
            }
        }

        stage('Test') {
            steps {
                // Run tests here
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application here
            }
        }
    }
}
```

### **Tasks:**

Create a New Job, this time select Pipeline instead of Freestyle Project.

Create a Hello World Jenkins declarative pipeline project.

Follow a few steps to create a Hello World declarative pipeline

We created the Jenkins freestyle project and we learned about how to install Jenkins so you can check here on Day 23-24.

**Steps**:

1. Now start your EC2 instance connect your terminal
    
2. Log in to your Jenkins Go on the dashboard and click on a **new item.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693328348610/776cd86f-2636-4b14-92ae-406b88a1739d.png align="center")
    
3. Enter the name of the item as **HelloWorldPipeline**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693328436811/67b0bff9-4bf5-4e22-881b-2e8422fe31e1.png align="center")
    
    Click on **Pipeline** and click **Ok**
    
4. Go to the end of the page, in the **Pipeline section**: Type the **declarative pipeline script** for **Hello World** as shown below and click on **save.**
    
    Here the **script is defined within the pipeline block**.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693328545612/8360b57e-2a72-4bff-898e-194216b1d96c.png align="center")
    
5. Click on **Build Now.**
    
6. The below image shows that the job is to **build** And it's **Successful.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693328612093/1bf89e07-687c-49a7-a287-dd271ab2fc09.png align="center")

Click on Console Output to see the complete Output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693328677232/0ed792ad-7f16-437a-84ea-6a39d6323036.png align="center")

***Conclusion: Wrap-up of the documentation and future improvements.***

By creating a new Jenkins job for your CI/CD pipeline, you automate the entire process from source code management to deployment, ensuring consistent and reliable software delivery. Jenkins orchestrates these steps based on triggers you define, providing a streamlined and efficient workflow for development and deployment.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading! Your support means the world to me. Let's keep learning, growing, and making a positive impact in the tech world together.

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)