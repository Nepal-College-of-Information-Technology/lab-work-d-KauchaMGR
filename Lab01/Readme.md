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

## Procedure
### Step 1: Access the AWS Console

1. Open a web browser and navigate to the AWS Management Console
2. Log in with your sandbox credentials
3. Verify you're in the correct region (typically `us-east-1` for this lab)
4. Ensure you have EC2 access permissions
### Step 2: Launch an AWS EC2 Instance

1. Navigate to the **EC2 Dashboard**
2. Click **Launch Instances**
3. **Select AMI** (Amazon Machine Image):
   - Choose "Amazon Linux 2" or "Ubuntu Server 20.04 LTS"
   - Select the free-tier eligible option
4. **Choose Instance Type**:
   - Select `t2.micro` (eligible for free tier)
5. **Configure Instance Details**:
   - Number of instances: 1
   - Subnet: Default VPC
   - Auto-assign public IP: Enable
6. **Add Storage**:
   - Default 30GB gp2 volume is sufficient
7. **Add Tags**:
   - Add a meaningful tag: Key: `Name`, Value: `WebServerLab1`
8. **Configure Security Group**:
   - Create a new security group: `WebServer-SG`
   - Add inbound rules:
     - HTTP (Port 80) - Source: 0.0.0.0/0 (Allow from anywhere)
     - HTTPS (Port 443) - Source: 0.0.0.0/0 (Optional)
     - SSH (Port 22) - Source: Your IP or 0.0.0.0/0
9. **Review and Launch**:
   - Review settings and click **Launch**
   - Select or create a key pair (save the `.pem` file securely)
   - Click **Launch Instances**
10. Wait for the instance to reach "Running" state

### Step 3: Connect to EC2 Instance and Install Nginx

#### Connect via SSH:

**On Windows (using PuTTY or WSL):**
```bash
ssh -i "your-key.pem" ec2-user@your-instance-public-ip
# or for Ubuntu
ssh -i "your-key.pem" ubuntu@your-instance-public-ip
```

**On macOS/Linux:**
```bash
chmod 600 your-key.pem
ssh -i your-key.pem ec2-user@your-instance-public-ip```
#### Install Nginx:

**For Amazon Linux 2:**
```bash
sudo yum update -y
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

**For Ubuntu:**
```bash
sudo apt-get update
sudo apt-get install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

#### Verify Nginx is Running:
```bash
sudo systemctl status nginx
```

### Step 4: Deploy a Sample Web Page

1. Navigate to the Nginx root directory:
```bash
cd /var/www/html
# or for Ubuntu
cd /var/www/html
```

2. Create a sample HTML page:
```bash
sudo nano index.html
```

3. Add the following HTML content:
   <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kathmandu Weather</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #87CEEB, #E0F7FA);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .weather-card {
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            text-align: center;
            width: 350px;
        }

        .weather-icon {
            font-size: 60px;
        }

        h1 {
            color: #333;
            margin-bottom: 10px;
        }

        .temperature {
            font-size: 40px;
            font-weight: bold;
            color: #0077cc;
        }

        .details {
            margin-top: 15px;
            text-align: left;
        }

        .details p {
            margin: 8px 0;
            font-size: 18px;
        }
    </style>
</head>
<body>

    <div class="weather-card">
        <div class="weather-icon">☀️</div>
        <h1>Kathmandu, Nepal</h1>
        <div class="temperature">28°C</div>
        <p><strong>Sunny</strong></p>

        <div class="details">
            <p>🌡️ Feels Like: 30°C</p>
            <p>💧 Humidity: 55%</p>
            <p>🌬️ Wind Speed: 12 km/h</p>
            <p>☁️ Cloud Cover: 10%</p>
            <p>👁️ Visibility: 10 km</p>
        </div>
    </div>

</body>
</html>

4. Save the file (Ctrl+X, then Y, then Enter if using nano)

5. Set proper permissions:
```bash
sudo chmod 644 /var/www/html/index.html
```

### Step 5: Access the Web Page

1. Get your instance's public IP:
   - Go to EC2 Dashboard → Instances
   - Select your instance and note the "Public IPv4 address"

2. Open a web browser and navigate to:
   ```
   http://your-public-ip
   ```

3. Verify the custom web page is displayed correctly

---
### Web Page Output
<img width="545" height="498" alt="image" src="https://github.com/user-attachments/assets/f9d9a55d-b4bd-4124-b121-26426a98e503" />



## Conclusion

This lab successfully demonstrated:

1. **AWS Console Navigation**: Gained hands-on experience accessing and managing the AWS Management Console
2. **EC2 Instance Deployment**: Successfully launched an EC2 instance with proper configuration and security settings
3. **SSH Connectivity**: Established secure shell connections to cloud instances
4. **Web Server Installation**: Installed and configured Nginx on a Linux-based cloud instance
5. **Web Content Deployment**: Deployed a custom HTML web page and made it accessible via HTTP
6. **Cloud Computing Benefits**: Experienced firsthand the advantages of cloud computing:
   - Rapid infrastructure provisioning
   - On-demand scalability
   - Global accessibility
   - Cost efficiency (pay only for what you use)
