# Flight Ticket Architecture Description 

## Application View
* Public Flight Ticketing Apps : PC(web) and Mobile(web app)
* Private Back-Office Apps : PC(web)
* API : API Gateway for interface
* Batch : Scheduled batch programs
* CI : Continuous Integration
* Monitoring : APM, Slack
* Library Interface : SSO, CDN, Redis, Push, SMS, Mail, Search Engine
* Solutions : Oracle DBMS, MongoDB, FTP

### Public Flight Ticketing Apps
* Front-end : Nginx Web Server, Static Contents
* Back-end : Tomcat AS Server, Spring, JSP/Tiles framework, MyBatis
* Runtime : JDK 1.8 64bit
* OS : CentOS

### Private Back-Office Apps
* Front-end : JSP
* Back-end : Tomcat AS Server
* Runtime : JDK 1.7 64bit
* OS : CentOS

### API Gateway
* Umbrella API Gateway with Nginx
* Tomcat AS Server
* Runtime : JDK 1.8 64bit
* OS : CentOS

### Batch Apps
* Spring Framwork Scheduler
* Runtime : JDK 1.8 64bit
* OS : CentOS

### Library Interface
* SSO : Custom SSO Library Module
* Redis : Session Clustering 
* Search Engine : Journey Searching

## Deployment View
### Public Flight Ticketing Apps : AIR
* Nginx : PC - 7080, Mobile - 7090
* Tomcat multi-container : PC - air_pc.war - 7081, Mobile - air_mo.war - 7091 
* Server count : 12ea

### Public BackOffice - Agency
* Internet Accessable
* Tomcat : back.war - 9080
* Server count : 2ea

### Private BackOffice - Admin & Batch
* Private Network only
* Tomcat : back.war - 9080, batch.war - 5080 (connect with FTP server)
* Server count : 2ea

### API Gateway
* Umbrella with Nginx
* Tomcat : api.war - 6080
* Server count : 2ea

### Stage
* Nginx & Tomcat : /air.war - 8080, /back.war - 5080, /api.war - 6080
* Server count : 1ea

### Development
* /jenkins - 8080
* /nexus - 8080
* /gitbucket - 8080 - private git
* /xwiki - 8080
* /api - 9080
* /air - 1080
* /back - 6090 - backoffice
* /cdn - 9000
* Redis - 6379
* Server count : 1ea