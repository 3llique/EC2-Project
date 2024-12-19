# EC2 Apache Web Server Deployment Project

## Overview

This project involves deploying an Apache web server on an AWS EC2 instance using a Bash script. It includes automation of server setup, web server configuration, and implementation of security measures.

---

## Project Features

- Automated EC2 instance provisioning and configuration.
- Installation and setup of Apache web server.
- Deployment of a custom web page via a Bash script.
- Implementation of basic and advanced security measures.

---

## Steps to Deploy
1. Provision the EC2 Instance
Launch an EC2 instance using Amazon Linux AMI.
![Step 1](https://github.com/user-attachments/assets/6754adc1-f032-4a22-b714-06a4d7675b74)

1.1. Configure the security group to allow HTTP (80) and SSH (22) traffic.
![Step 3](https://github.com/user-attachments/assets/2e28abc8-258e-48b4-af01-6cc005de47ef)

1.2. Assign a public IP to the instance.
![Step 2](https://github.com/user-attachments/assets/28cfa9cc-7f6e-4812-8ee7-55a2b9d166b9)
   
2. Connect to instance using EC2 Instance Connect
![Step 5](https://github.com/user-attachments/assets/36087f31-a400-41d3-bdec-5cddc18b4642)

2.1. Make the script executable and run it:
chmod +x  firstscript.sh
sudo ./firstscript.sh
![Screenshot 2024-12-18 at 4 47 31 PM](https://github.com/user-attachments/assets/bbf7fb3c-43d7-4dae-9ef1-1405259997ee)


3. Test the Web Server:
http was used to connect to my public IP because I did not setup an https certificate for validation.
This will be apart of my next project of securing the web server!
![Step 8 - DEPLOYED](https://github.com/user-attachments/assets/aa5ccffd-03ce-4562-8ca1-235d0c97507a)


## Deployment Script

Below is the Bash script used to deploy the Apache web server:

```bash
#!/bin/bash
# Update the package repository
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Start and enable Apache
systemctl start httpd
systemctl enable httpd

# Create a webpage with the desired message
echo "<!DOCTYPE html>
<html>
<head>
    <title>EC2 Deployment</title>
</head>
<body style='text-align: center; margin-top: 50px; font-family: Arial, sans-serif;'>
    <h1>We have deployed our first EC2 with a script</h1>
</body>
</html>" > /var/www/html/index.html

# Restart Apache to load the webpage
systemctl restart httpd

---





