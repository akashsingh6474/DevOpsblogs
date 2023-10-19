---
title: "Day-46: Set up Cloud Watch alarms and SNS topic in AWS"
datePublished: Thu Oct 19 2023 20:22:04 GMT+0000 (Coordinated Universal Time)
cuid: clnxmon4e000009kz64kheham
slug: day-46-set-up-cloud-watch-alarms-and-sns-topic-in-aws
tags: cloud, aws, sns, 90daysofdevops, awscloud

---

Hey learners, you have been using aws services atleast for last 45 days. Have you ever wondered what happen if for any service is charging you bill continously and you don't know till you loose all your pocket money ?

Hahahaha😁, Well! we, as a responsible community ,always try to make it under free tier , but it's good to know and setup something , which will inform you whenever bill touches a Threshold.

## What is Amazon CloudWatch?

Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real time. You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications.

The CloudWatch home page automatically displays metrics about every AWS service you use. You can additionally create custom dashboards to display metrics about your custom applications and display custom collections of metrics that you choose.

You can create alarms that watch metrics and send notifications or automatically make changes to the resources you are monitoring when a threshold is breached. For example, you can monitor the CPU usage and disk reads and writes of your Amazon EC2 instances and then use that data to determine whether you should launch additional instances to handle increased load. You can also use this data to stop under-used instances to save money.

## What is Amazon SNS?

Amazon Simple Notification Service (Amazon SNS) is a managed service that provides message delivery from publishers to subscribers (also known as *producers* and *consumers*). Publishers communicate asynchronously with subscribers by sending messages to a *topic*, which is a logical access point and communication channel. Clients can subscribe to the SNS topic and receive published messages using a supported endpoint type, such as Amazon Kinesis Data Firehose, Amazon SQS, AWS Lambda, HTTP, email, mobile push notifications, and mobile text messages (SMS).

![
A publisher sends a message to an Amazon SNS topic, and subscribers receive the
message.
](https://docs.aws.amazon.com/images/sns/latest/dg/images/sns-delivery-protocols.png align="left")

## Task :

* Create a CloudWatch alarm that monitors your billing and sends an email to you when it reaches $2.
    
* Delete your billing Alarm that you created now.
    
* Steps:
    
    1. Go to Cloudwatch alarms and create a new alarm.
        
    2. Select Metrics - Billing &gt; Total Estimate Charge
        
        1. Select Condition =&gt;$2
            
    3. Create a new topic to send email notifications.
        
    4. Select the created topic
        
    5. Create the alarm
        
    6. The alarm is created but it gives a warning that the SNS subscription is pending.
        
    7. Go to your Gmail and confirm the subscription.
        
    8. Validate the same by refreshing the Alarm page. The alarm is created and we will receive an email alert if the billing is crossing the threshold of $2.
        
        Thank you :)  
          
        In this blog, I have discussed Set up CloudWatch alarms and SNS topic in AWS If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.
        
        If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.
        
        #Day46 #90daysofdevops
        
        Thank you for reading!
        
        Thank You! Stay Connected ☁️👩‍💻🌈
        
        Contact me at :
        
        LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
        
        E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)