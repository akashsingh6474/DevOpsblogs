---
title: "Day 44: Relational Database Service in AWS"
datePublished: Mon Oct 16 2023 16:59:46 GMT+0000 (Coordinated Universal Time)
cuid: clnt54wu3000309jw0rwq5apw
slug: day-44-relational-database-service-in-aws
tags: cloud, aws, devops, aws-rds, 90daysofdevops

---

### **Relational Database Service**

Amazon Relational Database Service (Amazon RDS) is a web service that makes it easier to set up, operate, and scale a relational database in the AWS Cloud. It provides cost-efficient, resizable capacity for an industry-standard relational database and manages common database administration tasks.”

RDS offers six database engines:

* MySQL: A widely-used open-source relational database management system known for its stability, ease of use, and compatibility.
    
* MariaDB: A community-developed, open-source fork of MySQL, offering similar features and compatibility.
    
* PostgreSQL: An open-source object-relational database management system known for its robustness, extensibility, and support for advanced features.
    
* Oracle: A commercial relational database management system that provides enterprise-level features and capabilities.
    
* SQL Server: A commercial relational database management system developed by Microsoft, offering scalability, security, and integration with Microsoft products.
    
* Amazon Aurora: A MySQL and PostgreSQL-compatible database engine developed by AWS. It offers high performance, scalability, and durability. It is up to five times faster than MySQL.
    

## Task-01:

* Create a Free tier RDS instance of MySQL
    
* Follow to create RDS on AWS..
    
* login on your AWS account &gt; GO to search bar and search RDS.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697452920804/18b09cb9-8dd4-4aab-8a88-7b3fb917bdea.png align="center")
    
* Go to your AWS console &gt; Search RDS &gt; Choose to Create database &gt; Select Standard Create &gt; Under “Engine options”, choose “MySQL”
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697452998198/946bdc25-71b3-4def-a18f-8bb544b40aed.png align="center")

Select template &gt; Free Tier.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697453032732/4819198c-9340-482a-a605-8b68e678c8c4.png align="center")

Under Settings, I am providing the following details:

> ***DB instance identifier: database-44***
> 
> ***Credentials Settings:***
> 
> ***Master username: admin***
> 
> ***And provide the password of your choice according to the constraints mentioned.***
> 
> ***Configure other settings like storage, backups, VPC, and security groups according to your requirements. Review the configuration and click “Create Database”.***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697453792757/7d972acd-26d3-40b0-a9e2-d073676cfb15.png align="center")

*Create an EC2 instance*

I am creating an instance named instance-44rds.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697453686991/3ff3da7e-dbad-4311-9c40-00088655c3e2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697453825220/370d667c-7fdb-42e8-811c-910a765d943b.png align="center")

I am configuring the security group to allow inbound traffic on the MySQL port (default is 3306)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697454618434/0b27c628-0c79-4cbb-8906-59fc9ecff62c.png align="center")

*Create an IAM role with RDS access. Assign the role to EC2 so that your EC2 Instance can connect with RDS.*

Go to IAM Dashboard &gt; Click on Roles &gt; Create Role &gt; Select the EC2 service for the trusted entity &gt; In permission policies, attach the permission [**AmazonRDSFullAccess**](https://us-east-1.console.aws.amazon.com/iamv2/home?region=ap-south-1#/policies/details/arn%3Aaws%3Aiam%3A%3Aaws%3Apolicy%2FAmazonRDSFullAccess) &gt; Name the role as “rds-data” &gt; Create Role.

The role is created.

Let’s connect to the EC2 instance using SSH.

And then install the MySQL client in the instance:

```plaintext
sudo apt-get update
sudo apt-get install mysql-client
mysql --version
```

![](https://miro.medium.com/v2/resize:fit:875/1*PN10Uhx-HJy1QXoGd_4KYg.png align="left")

To connect to the RDS instance using the MySQL client and the endpoint address, username, and password, we use the following command:

```plaintext
mysql -h <RDS_ENDPOINT> -P <RDS_PORT> -u <MASTER_USERNAME> -p
#The below details we copied when we created the RDS instance:
#<RDS_ENDPOINT> with the endpoint of your RDS instance
#<RDS_PORT> with the port number (default is 3306)
#<MASTER_USERNAME> with the master username
# '-h' is used to specify the endpoint of MySQL server to which we want to connect (basically the host)
```

```plaintext
mysql -h database-example-rd-1.cg9zuoghw8tf.ap-south-1rds.amazonaws.com -P 3306 -u admin -p
```

After running this command, you will be prompted for the password. Give the password you created while creating RDS:

![](https://miro.medium.com/v2/resize:fit:875/1*MH5KgJ-PRl2F-rTUEBjFOA.png align="left")

Now you can verify the CRUD operations confirming the MYSQL is working properly.

![](https://miro.medium.com/v2/resize:fit:411/1*Rkq3H8QEHbFkaqqNWenYoA.png align="left")

And Yay! We have created a Free tier RDS instance of MySQL, an EC2 instance, assigned an IAM role with RDS access to the EC2 instance, and connected to the RDS instance from the EC2 instance using a MySQL client.

In this blog, I have discussed Relational Database Services in AWS. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day43 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)