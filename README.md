# task-14

# Task 14: Free VM Setup and Web Application Deployment

## Overview

In this task, I created a free virtual machine (VM) in my cloud account (AWS/GCP/Azure), set up an Apache web server, and deployed a web application to demonstrate the deployment process and user registration functionality. This README documents the steps taken, along with screenshots of the process.

## Steps Taken

1. Login to Your Cloud VM via SSH from Kali Linux
   - Open your Kali Linux terminal.
   - Use the following SSH command to log in to the VM:
     "<ssh -i /home/kali/task13/kali_key.pem azureuser@20.192.9.221"
   -  Capture a screenshot showing successful SSH login which is (auzre1.png).

2. Clone the Repo from Taskten (HTML Page)
   - After logging into the VM, clone your taskten repository from GitHub:
     "git clone https://github.com/hazeenakhalid/task-12.git"

3. Copy the Cloned Files to Apache Web Server Root Directory
   - Copy the HTML and related files from the cloned taskten folder to the root directory of the Apache web server:
   - step 1: "ls"
   - step 2: "cd /var/www/html"
   - step 3: "sudo cp -r /var/www/html/register.php/* /var/www/html/"

4. Start the Apache Web Server
   - Start the Apache web server on the VM:
     "sudo systemctl start apache2"
   - Ensure the web server is running by checking its status:
     "sudo systemctl status apache2"

5. Access the Web Page via Local Browser
   - Open a web browser on your local machine and enter the public IP of your cloud VM:
     "http://<your-vm-public-ip>"
     "http://20.192.9.221/"
   - Capture a screenshot of the webpage being served from the cloud VM.

6. Install PHP and MySQL on the VM
   - If PHP and MySQL are not already installed, use the following commands to install them:

   Install PHP(register2.png):
    "sudo apt update"
    "sudo apt install php libapache2-mod-php"
   
   Install MySQL(SQL start3.png):
    "sudo apt install mysql-server"

7. Start MySQL Server and Login
   - Start the MySQL service:
   "sudo systemctl start MySQL"
   - Login to MySQL as the root user:
   "sudo mysql -u root -p"

8. Create Database, Table, and User
   - Inside the MySQL shell, create a database, table, and user using the following commands:

   - Create a Database:
     a)."CREATE DATABASE user_registration;"
     b)."CREATE USER 'webuser'@'localhost' IDENTIFIED BY 'password123';
        GRANT ALL PRIVILEGES ON user_registration.* TO 'webuser'@'localhost';
        FLUSH PRIVILEGES;"
     c)."USE user_registration;"

   - Create a Users Table:
       a)."USE user_registration;
    CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    phone VARCHAR(15) NOT NULL,
    password VARCHAR(255) NOT NULL
   );"


   - Take a screenshot showing the creation of the database, table, and user in MySQL (database creation4.png).

9. Create/Register a User via PHP Script(registeration page5.png)
   - Write or copy a PHP registration script that allows users to register their details (username, email, password) and stores them in the users table.
   - Ensure the registration form connects to the MySQL database and inserts data correctly.
   - Test the registration page by accessing it from your browser:
     "http://20.192.9.221/register.php"

10. Login as the Created User
    - After registering a new user, log in using the same credentials.
    - Take a screenshot showing the successful login page in (login.png).
    - after login dashboard open(dashboard.png)

11. Share the Public IP of Your Web Server
    - Share your web server’s public IP with friends or colleagues to verify if they can access the registration and login pages.

## Public IP
- The public IP address of the VM is: `20.192.9.221`

## Conclusion
This task demonstrated the process of setting up a free VM, deploying a web application, and creating a user registration system. The web application is now accessible to anyone using the public IP.
