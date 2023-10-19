---
title: "Day 45: Deploy WordPress website on AWS"
datePublished: Thu Oct 19 2023 19:26:27 GMT+0000 (Coordinated Universal Time)
cuid: clnxkp3t4000708l2hivj7hqf
slug: day-45-deploy-wordpress-website-on-aws
tags: cloud, aws, wordpress, devops, 90daysofdevops

---

Over 30% of all websites on the internet use WordPress as their content management system (CMS). It is most often used to run blogs, but it can also be used to run e-commerce sites, message boards, and many other popular things. This guide will show you how to set up a WordPress blog site.

Here’s the guide to official documentation from AWS [**to deploy this project.**](https://aws.amazon.com/getting-started/hands-on/deploy-wordpress-with-amazon-rds/)  
Database maintenance for your WordPress site is critical. Your database instance holds all of your important data for your WordPress site. If the database goes down, your website may go down with it, and you could even lose your data.

* Database maintenance can also be difficult, and database administrators have years of specialized experience. When setting up a WordPress site, you want to stay focused on designing your page and generating your content, not worrying about database performance and backups.
    

Amazon RDS for MySQL helps with both of these problems. Amazon RDS for MySQL is a managed database offering from AWS. With Amazon RDS for MySQL, you get:

* Automated backup and recovery so that you won’t lose data in the event of an accident
    
* Regular updates and patches, keeping your database secure and performant
    
* Easy installation with smart default parameters.
    

Let’s start the project now.

## **Steps -**

1. Create an RDS MySQL database as we created on Day44 - [**Day44-RDS-Setup**](https://hashnode.com/post/clnt54wu3000309jw0rwq5apw). Follow [**Documentation**](https://aws.amazon.com/tutorials/deploy-wordpress-with-amazon-rds/module-one/) to create the database.
    
2. Launch a new EC2 instance with port 3306 enabled for MYSQL.
    
3. Go to the MySQL database you created and edit the Security Group.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697734847435/36d43e4a-5af1-4599-b7c6-200bcc897633.png align="center")

Edit the inbound rules and update the All traffic security group to MySQL/Aurora. Change the **Type** property to **MYSQL/Aurora**, which will update the **Protocol** and **Port range** to the proper values. Then, remove the current security group value configured for the **Source**. The console will show the available security groups that are configured. Choose the **database02** security group that you used for your EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697734914187/219849a0-334f-49b1-a141-9ec3a109c14c.png align="center")

1. SSH to the EC2 instance and install MySQL Client using the below commands.
    

```plaintext
sudo apt update -y && sudo apt install mysql-client -y
ubuntu@ip-172-31-91-94:~$ mysql --version
mysql  Ver 8.0.34-0ubuntu0.22.04.1 for Linux on x86_64 ((Ubuntu))
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735018899/9555f74b-1dcf-48dd-883e-da6159b73cfb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735055218/b8d6bfdc-6146-49aa-86d5-4b333b450e83.png align="center")

```plaintext
mysql -h <endpoint> -P 3306 -u admin -p
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735092363/9c37f309-b10d-4f41-b336-a84aa6f14397.png align="center")

Once you're logged in to the MySQL client, create the below database

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697735138701/d8d492e3-d134-4563-b8ad-d0e5c66ef813.png align="center")

1. Now, to run a web server, we need to install Apache using the below command
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697740865301/1f974e17-fd51-4783-b491-d01d982ad8a9.png align="center")

verify that Apache server is running or not.

```plaintext
sudo systemctl status apache2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697741070673/2c704f52-f0dc-4366-9ba5-381d80d454ad.png align="center")

1. Validate if you can access the apache2 default page using EC2 public IP (Open port 80 if the page is not accessible).
    
2. Now Go to instance and copy public ip and paste in google chrome.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697741154258/7574c72f-d3f5-4c78-b70c-78477cf80e10.png align="center")

1. Go back to SSH and download and configure WordPress.
    

```plaintext
wget https://wordpress.org/latest.tar.gz
tar -xzf latest.tar.gz
cd wordpress
cp wp-config-sample.php wp-config.php
```

1. Edit the file wp-config.php and update the below entries with your configuration values.
    

```plaintext
define( 'DB_NAME', 'wordpress' );

/** Database username */
define( 'DB_USER', 'wordpress' );

/** Database password */
define( 'DB_PASSWORD', 'wordpress1' );

/** Database hostname */
define( 'DB_HOST', 'wordpress.cf2bhn2hoqgz.us-east-1.rds.amazonaws.com' );

/** Database charset to use in creating database tables. */
define( 'DB_CHARSET', 'utf8' );
```

1. Update the below entries with random values, you can get the values from [**Here**](https://api.wordpress.org/secret-key/1.1/salt/)
    
2. ```plaintext
     define('AUTH_KEY',         'BpYQ&/2P]nFr.+3S;_<p#`zu|JT3h>3`|tQ-d5wiPuw_J-v/?(Rw+yw|=gtHmHMn');
     define('SECURE_AUTH_KEY',  'opLk-KS|.#-CtMU5(rm1_DOX@?BaNB[J8T3WjNby~CJTr]XnG4:S5GFB@n*(2WU9');
     define('LOGGED_IN_KEY',    '$&-hv~wtRrI8j~*C-=#4kion2|*)7_Y7.~0{lZ}C(a4`aaV6;h[{-s4S?29CY~{y');
     define('NONCE_KEY',        'WF0AG@%n~|$/`hIP5tL)>aYj6vdPQ<L-:f#!F9i]Tf0u(RGdUGFg&}~K |AJ]mW!');
     define('AUTH_SALT',        'o]L,!st#[~&nNUPM2D[_QCVc,MjtIgwT`B]{Cg?bd=+FRp,;A}J@.R?Ay=QQhxA7');
     define('SECURE_AUTH_SALT', 'y.nOeeu?}.UK!*0<T3/MKrVU8?5J?oZ93+B5-qbGB$;x|-vf<|kKy^K5AhpsN|t+');
     define('LOGGED_IN_SALT',   '=AAy>Wg;q~lfe}+-oijOcz>HLBTI^/vMp]U%s)Dne]*nqhvEjJwWlidTU2l{D&c_');
     define('NONCE_SALT',       'HZx J=w=fTG-hRV7 s^dwAtbi8HXwy[KzVP]jC.-~ DamErl{R%rs1:nh&%9vcK3');
    ```
    
3. Now, install the dependencies and copy the WordPress files to /var/www/html/ path to run the webpage.
    
4. Install the apache2 service.
    

```plaintext
sudo apt install php libapache2-mod-php php-mysql -y
sudo cp -r wordpress/* /var/www/html/
sudo systemctl restart apache2
```

1. Access the public IP and you should be able to access the WordPress webpage with database connectivity. -
    

In this blog, I have discussed Deploy Wordpress website on AWS. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day43 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)