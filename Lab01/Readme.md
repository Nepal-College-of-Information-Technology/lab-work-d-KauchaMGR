# Lab 1: Hosting a Web Server on the Cloud
## Objectives:
1)Access the AWS Console through the sandbox environment <br>
2)Launch an AWS EC2 instance<br>
3)Connect to the EC2 instance and install Nginx<br>
4)Deploy a sample web page<br>
5)Access the hosted web page through a web browser<br>
## Background Theory:
### AWS Console:
The AWS Management Console is a web-based interface for accessing and managing all Amazon Web Services.
It provides a graphical dashboard instead of requiring command-line interaction. A sandbox environment is an isolated, temporary cloud environment used for learning and experimentation 
changes don't affect production systems.
###  EC2 (Elastic Compute Cloud)
EC2 is AWS's virtual server service. It lets you rent computing capacity in the cloud. Key EC2 concepts include instances (virtual machines running on AWS hardware), AMIs (Amazon Machine Images : pre-configured OS templates used to launch instances), instance types (hardware configurations like CPU/RAM), security groups (virtual firewalls controlling inbound/outbound traffic), and key pairs (SSH public/private keys for secure login).
### Nginx web server
Nginx (pronounced "engine-x") is a high-performance open-source web server. It can act as a web server, reverse proxy, and load balancer. Compared to Apache, Nginx is event-driven and handles many concurrent connections efficiently — making it popular for high-traffic sites.
### Web Hosting & HTTP
A web page is served over HTTP/HTTPS. When Nginx is installed and running, it listens on port 80 (HTTP). Your EC2 instance's public IP address acts as the address browsers use to reach the server.
