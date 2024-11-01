# WSL-Web-Server
This project demonstrates how to set up an attractive web server using Windows Subsystem for Linux (WSL) and Nginx. The web server hosts a simple HTML page styled with CSS to create a welcoming interface.

**Project Overview**

The aim of this project is to set up and configure a web server on WSL with a user-friendly interface. Steps include configuring Nginx, creating an HTML/CSS front end, and troubleshooting permissions to avoid common issues like "403 Forbidden" errors.

**Prerequisites**
Windows with WSL and a Linux distribution installed (e.g., Ubuntu).
Basic understanding of HTML, CSS, and Linux command-line operations.
Installation and Setup
1. Install WSL and a Linux Distribution (if not installed)

wsl --install
2. Update System Packages in WSL

sudo apt update && sudo apt upgrade -y
3. Install and Start Nginx

sudo apt install nginx -y
sudo service nginx start
sudo systemctl enable nginx
4. Configure the Web Server Directory

cd /var/www/html
sudo rm index.nginx-debian.html
5. Create an HTML Page with CSS
Create index.html:

sudo nano index.html
HTML Content:

html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Attractive Web Server on WSL</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f3f4f6; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .container { text-align: center; background-color: #ffffff; padding: 20px; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); border-radius: 8px; width: 90%; max-width: 600px; }
        h1 { color: #4CAF50; }
        p { color: #555; }
        .button { display: inline-block; padding: 10px 20px; color: #ffffff; background-color: #4CAF50; text-decoration: none; border-radius: 5px; margin-top: 10px; transition: background-color 0.3s; }
        .button:hover { background-color: #45a049; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to My Web Server!</h1>
        <p>This server is running on Windows Subsystem for Linux with Nginx.</p>
        <a href="#" class="button">Learn More</a>
    </div>
</body>
</html>
Save and Exit:

In Nano, press CTRL + O, Enter to save, then CTRL + X to exit.

6. Fix "403 Forbidden" Errors (if needed)
bash
Copy code
sudo chown -R www-data:www-data /var/www/html
sudo find /var/www/html -type d -exec chmod 755 {} \;
sudo find /var/www/html -type f -exec chmod 644 {} \;

7. Allow WSL Traffic in Windows Firewall
Open Windows Firewall with Advanced Security.
Add an Inbound Rule to allow TCP traffic on port 80.
Troubleshooting
403 Forbidden Error: Check and fix permissions as in step 6.
Access Issues: Ensure the Windows firewall rule for port 80 is enabled.
Learning Outcomes
By completing this project, you will:

Understand WSL setup and basic Linux commands.
Gain experience with web server configuration using Nginx.
Learn to create and style web pages with HTML and CSS.
Troubleshoot common server and permissions issues.

**License**

This project is open-source and available for modification.

