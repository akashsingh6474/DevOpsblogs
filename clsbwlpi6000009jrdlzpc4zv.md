---
title: "Day 75 - Sending Docker Log to Grafana"
datePublished: Wed Feb 07 2024 14:47:19 GMT+0000 (Coordinated Universal Time)
cuid: clsbwlpi6000009jrdlzpc4zv
slug: day-75-sending-docker-log-to-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707317084771/e86449d3-8de1-4f2b-a7b3-9e66ba7064a1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707317191700/ee31bb25-ca9b-457d-9381-146edc8bb211.png
tags: cloud, monitoring, devops, loki, grafana, 90daysofdevops, promtail

---

We learned how to install and start Grafana, set up Loki and Promtail via Docker, and configure Loki as a data source in Grafana.

Armed with these insights, you’re now well-prepared to navigate the world of efficient data visualization and comprehensive system monitoring. Stay tuned for more exciting explorations in our upcoming blogs!

For installation and Setup Grafana Server

Checkout my [73 day](https://akashblogs-1689395803240.hashnode.dev/day-73-grafana-setup) blog. **"Grafana Installation"**

# **Install Loki & Promtail using Docker.**

* Before installing Loki & Promtail make sure you have docker installed in your instance.
    

```plaintext
sudo apt-get update

sudo apt-get install docker.io -y

 # Giving docker permission to current user
  sudo usermod -aG docker $USER
  sudo reboot
# verfiy the installation of docker
  docker --version

sudo systemctl enable docker
sudo systemctl start docker
sudo systemctl docker status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707305811284/c94a7f73-bacf-4ed7-b883-6757da4554ea.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306106870/022210d0-f6fe-4687-8c2b-28d837411b23.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306123384/b2d4eb48-f408-4478-bde6-4c56d2d83860.png align="center")

* Download the Loki Config file into your current directory.
    
* ```plaintext
      wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306169227/fa848ef6-f67f-4f79-ab0c-e5ed6e62a5ba.png align="center")
    
    * Run the Loki container using the following Docker command.
        
    
    ```plaintext
    docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306216571/0050ffff-d68b-4050-8536-de9ee2ecce4b.png align="center")
    
    * We can verify Loki is running using the docker container by using the following Docker command :
        
    * ```plaintext
          docker ps
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306770147/8f13ecc6-4e5c-4e34-87ff-dc9b2e39902c.png align="center")
        
        * Now to access Loki, Go to the Security Group of your EC2 instance and add port 3100.
            
        * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306927019/a5e1339d-2c92-4cdf-926d-7919feda3c50.png align="center")
            
        * We can see Loki’s metrics using the IPv4 address followed by port 3100 and metrics.
            
        * ```plaintext
                http://<public_ipV4>:3100/metrics
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307156977/6f798369-3fbf-4914-a9dd-5ee9e7c08468.png align="center")
            
            * To verify whether Loki is ready or not, access the IPv4 address followed by port 3100 and ready.
                
            
            ```plaintext
              http://public_ipV4:3100/ready
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307198128/cb732b21-b156-4fa5-91a9-aa04bf4ce802.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307264671/617ee6c8-e0d2-423f-be10-cbb62fb0cf7e.png align="center")
            
            * Now download the Promtail Config yaml file into your directory by using the following command:
                
            * ```plaintext
                  wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-config.yaml -O promtail-config.yaml
                ```
                
                * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307431193/fff46c10-1bb2-4e3e-910b-3713d3720dda.png align="center")
                    
                * We can verify Promtail configuration file is there in the directory by using the following command:
                    
                
                ```plaintext
                  ls
                
                  cat promtail-config.yaml
                ```
                
                * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307483133/c5391df6-3915-4de1-89c0-ef827968b578.png align="center")
                    
                * Now execute the Promtail container by using the following Docker command:
                    
                
                ```plaintext
                  docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 --config.file=/mnt/config/promtail-config.yaml
                ```
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307535632/fa58e07e-0126-4c25-b869-1671c8088893.png align="center")
                
                * We can verify both Loki and Promtail are running using `docker ps` command.
                    
                * ```plaintext
                      docker ps
                    ```
                    
                    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707307569595/552d55da-36db-449d-8c1f-7b936edfd0cc.png align="center")
                    
                
                # **Configure Loki as a Data Source**
                
                * Once both Loki and Promtail are configured in the instance, Login to the Grafana Home Page
                    
                * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707312424081/e85c3cb0-969c-4950-aa8f-0845acfb456a.png align="center")
                    
                * In the navigation drawer either there is DataSource click on it or you can get it by clicking on the left hamburger menu, hovering over there is a gear icon (second last one) and clicking on “Data Sources”.
                    
                * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707312478834/ee388a05-86a4-4bce-a247-92a5cb47ffef.png align="center")
                    
                    Click on “Add data source” and search for “Loki”. Click on it.
                    
                * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707312557507/3db0cf55-9154-4e15-b47a-b1a0ce6d0214.png align="center")
                    
                    * As the Loki prompt is opened fill in the details like Name and in the HTTP provide the URL i.e, [**http://127.0.0.1:3100**](http://127.0.0.1:3100)
                        
                    
                
                ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707312680303/047f3ac8-3b5e-4499-9a7c-31aa18af7ea2.png align="center")
                
                * We will create metrics that will show logs containing Docker in it.
                    
                
                ```plaintext
                  Name -> System Generated Logs
                  Label Filters -> jobs, varlogs
                  Line Contains -> docker
                ```
                
                ![](https://miro.medium.com/v2/resize:fit:875/1*R-fr-AidowmHUsALzZNB2g.png align="left")
                
                ![](https://miro.medium.com/v2/resize:fit:875/1*-FGrzyvzdNiYt72ia3WTsA.png align="left")
                
                * Once you get the output we can put the result into a new dashboard, before that named it.
                    
                * ![](https://miro.medium.com/v2/resize:fit:875/1*4Bu6DCpwiws1PoF-Z18i3g.png align="left")
                    
                    ![](https://miro.medium.com/v2/resize:fit:875/1*WrjunO-TjkERm-XAB0Ck3w.png align="left")
                    
                    Thanks for delving into Grafana, Loki, and Promtail through Docker installation! Now equipped with powerful monitoring tools, from Grafana setup to Loki and Promtail configuration, you’re ready for efficient system monitoring and visualization.[  
                    ](http://127.0.0.1:3100/)
                    
                
                * Hope you found this helpful.
                    
                    Embrace the challenges ahead and stay excited for continued growth and learning!So I encourage you to try this on your own and let me know in the comment section about your learning experience
                    
                    Thank you for reading!
                    
                    Thank You! Stay Connected ☁️👩‍💻🌈
                    
                    Contact me at :
                    
                    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
                    
                    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech40@gmail.com**](mailto:akashsinghtech40@gmail.com)