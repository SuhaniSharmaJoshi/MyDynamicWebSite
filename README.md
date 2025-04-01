# MyDynamicWebSite
🌐 Dynamic Web Page with AWS EC2 & RDS
📌 Project Overview
This project is a dynamic web application hosted on an Amazon EC2 instance using Apache/Nginx and PHP. It connects to an Amazon RDS MySQL database to fetch and display data dynamically.

Features
✅ Web Server: Hosted on an EC2 instance with Apache/Nginx
✅ Dynamic Content: PHP-based web page fetching data from MySQL RDS
✅ Database: Amazon RDS MySQL for persistent storage
✅ Scalable & Secure: Uses AWS Security Groups for controlled access

Technologies Used
✅ AWS EC2 (Amazon Linux 2023)
✅ Apache/Nginx as Web Server
✅ PHP for backend logic
✅ Amazon RDS (MySQL) for database

/project-directory
│── index.php           # Main PHP file displaying data from MySQL
│── db_config.php       # Database connection file
│── README.md           # Documentation

📌 Setup Instructions
1️⃣ Launch an EC2 Instance
Select Amazon Linux 2023

Install necessary packages:
sudo yum update -y
sudo yum install -y httpd php-mysqlnd php

Start the web server:
sudo systemctl start httpd
sudo systemctl enable httpd

2️⃣ Deploy Your Web Application
Upload your PHP files to /var/www/html/

sudo cp index.php db_config.php /var/www/html/

3️⃣ Set Up Amazon RDS (MySQL)
Create a MySQL RDS database

Modify Security Group to allow EC2 to connect (port 3306)

Use the RDS endpoint in db_config.php:
<?php
$host = "your-rds-endpoint.rds.amazonaws.com";
$user = "admin";
$password = "yourpassword";
$database = "yourdatabase";
$conn = new mysqli($host, $user, $password, $database);
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>

4️⃣ Connect EC2 to RDS
Install MySQL client:
sudo dnf install mysql -y
Test connection:


mysql -h your-rds-endpoint.rds.amazonaws.com -u admin -p
5️⃣ Access the Web App
Open EC2 Public IP in your browser:
http://your-ec2-public-ip/index.php
