👇

🚀 AWS RDS MySQL Integration with Java Web Application
📌 Project Overview

This project demonstrates the deployment of a Java-based Login & User Registration Web Application on Amazon Web Services (AWS) using:

Amazon EC2 as the application server
Amazon RDS (MySQL) as the backend database
Apache Tomcat as the web server

The goal of this project is to validate end-to-end connectivity between EC2, RDS, and a Java JSP application, and ensure successful data persistence.

🏗️ Architecture
User Browser
     │
     ▼
EC2 Instance (Tomcat + Java App)
     │
     ▼
Amazon RDS MySQL
(Database: jwt → Table: users)
⚙️ Tech Stack
Java (JSP/Servlets)
MySQL
Apache Tomcat
AWS EC2
AWS RDS
Linux (Ubuntu)
☁️ AWS Services Used
🔹 EC2 (Elastic Compute Cloud)
Hosts the Java web application
Acts as application server and MySQL client
🔹 RDS (MySQL)
Managed database service
Stores user login & registration data
🔹 Security Groups
Allow EC2 → RDS (port 3306)
Allow Browser → EC2 (port 8080)
🔹 VPC
Enables secure communication between services
🚀 Deployment Steps
1️⃣ Launch EC2 Instance

Installed required dependencies:

sudo apt update
sudo apt install openjdk-11-jdk -y
sudo apt install tomcat9 -y
sudo apt install mysql-client-core-8.0 -y
2️⃣ Create RDS MySQL Instance
Parameter	Value
Engine	MySQL
Port	3306
Database	jwt
Username	admin
3️⃣ Configure Security Groups
EC2 Security Group
Type	Port
SSH	22
HTTP	8080
RDS Security Group
Type	Port	Source
MySQL	3306	EC2 SG
4️⃣ Deploy Application

Clone repository:

https://github.com/kartiksiriya27/AWS-RDS-TASK.git

Copy to Tomcat:

sudo cp -r aws-rds-java/LoginWebApp /var/lib/tomcat9/webapps/
sudo systemctl restart tomcat9
🗄️ Database Setup
USE jwt;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email VARCHAR(150),
  username VARCHAR(100),
  password VARCHAR(100),
  regdate DATE
);
🌐 Application URLs
Registration Page
http://<EC2-Public-IP>:8080/LoginWebApp/userRegistration.jsp
Login Page
http://<EC2-Public-IP>:8080/LoginWebApp/login.jsp
✅ Testing & Verification
✔ Registration
Form submitted successfully
Data stored in RDS
✔ Login
Credentials validated
User redirected correctly
✔ Database Check
SELECT * FROM users;

📌 Sample Output:

+----+------------+-----------+--------------------------+----------+-----------+------------+
| id | first_name | last_name | email                    | username | password  | regdate    |
+----+------------+-----------+--------------------------+----------+-----------+------------+
|  1 | KARTIK     | SIRIYA    | kartiksiriya27@gmail.com | Siri     | Siri@2709 | 2026-04-16 |
+----+------------+-----------+--------------------------+----------+-----------+------------+
📚 Key Learnings
EC2 instance setup & configuration
RDS MySQL provisioning
Security group networking
Deploying Java apps on Tomcat
Connecting application to cloud database
Verifying real-time data persistence
🎯 Conclusion

This project successfully demonstrates a full-stack cloud deployment:

🌐 EC2 → Application Hosting
🗄️ RDS → Database Management

⚙️ Tomcat → Application Server

✔ Verified end-to-end connectivity
✔ Successfully stored and retrieved user data

🔗 GitHub Repository

👉 https://github.com/kartiksiriya27/AWS-RDS-TASK.git
