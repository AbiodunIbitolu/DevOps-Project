# WEB STACK IMPLEMENTATION (LEMP STACK)

### Navigate to the directory with the key via the terminal. SSH connection to the Ubuntu instance.

![Alt text](<images/Screenshot 2023-09-18 at 18.29.45.png>)

## Step 1 - Installing the Nginx Web Server

### Update server's package index

'sudo apt update'


![Alt text](<images/Screenshot 2023-09-18 at 18.36.36.png>)

### Nginx installation.

'sudo apt install nginx'

![Alt text](<images/Screenshot 2023-09-18 at 18.38.38.png>)
![Alt text](<images/Screenshot 2023-09-18 at 18.39.16.png>)

### Check the Nginx was successfully installed.

'sudo systemctl status nginx'

![Alt text](<images/Screenshot 2023-09-18 at 18.42.17.png>)

### Open port 80 by editing the inbounds rules under security groups

![Alt text](<images/Screenshot 2023-09-18 at 18.47.55.png>)

![Alt text](<images/Screenshot 2023-09-18 at 18.50.02.png>)

![Alt text](<images/Screenshot 2023-09-18 at 18.50.42.png>)

![Alt text](<images/Screenshot 2023-09-18 at 18.53.03.png>)

![Alt text](<images/Screenshot 2023-09-18 at 18.54.42.png>)

### Request Nginx on port 80.

'curl http://127.0.0.1:80'

![Alt text](<images/Screenshot 2023-09-18 at 19.03.48.png>)

### Test that Nginx server can respond to requests from the internet.

'http://35.179.96.37:80'

![Alt text](<images/Screenshot 2023-09-18 at 19.18.36.png>)

## Step 2 - Installing MySQL

### Install MySQL

'sudo apt install mysql-server -y'

![Alt text](<images/Screenshot 2023-09-18 at 19.24.21.png>)

![Alt text](<images/Screenshot 2023-09-18 at 19.24.51.png>)

### Connect to the MySQL server as the administarative database user root.

'sudo mysql'

### Set a password for the root user

'ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';'

### Exit SQL shell

'exit'

![Alt text](<images/Screenshot 2023-09-18 at 19.35.26.png>)

### Setup database password criteria.

'sudo mysql_secure_installation'

![Alt text](<images/Screenshot 2023-09-18 at 20.02.57.png>)

![Alt text](<images/Screenshot 2023-09-18 at 20.03.31.png>)

### Login with root user password

'sudo mysql -p'

![Alt text](<images/Screenshot 2023-09-18 at 20.06.15.png>)

## Step 3 - Installing PHP

### Install php fastCGI process manager and php mysql

'sudo apt install php-fpm php-mysql'

![Alt text](<images/Screenshot 2023-09-18 at 20.12.23.png>)

![Alt text](<images/Screenshot 2023-09-18 at 20.12.48.png>)

## Step 4 - Configuring Nginx to Use PHP Processor

### Create root web directory for your domain.

'sudo mkdir /var/www/projectLEMP'

### Assign ownership of the directory with User environment variable.

'sudo chown -R $USER:$USER /var/www/projectLEMP'

### Open new configration file in Ngnix site-available directory using Nano editor.

'sudo nano /etc/nginx/sites-available/projectLEMP'

![Alt text](<images/Screenshot 2023-09-18 at 22.54.46.png>)

### Activate your configuration by linking to the config file from the Nginx site-enabled directory

'sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/'

### Test configuration for syntax errors.

'sudo nginx -t'

### Disable default Nginx host that is currently configured to listen on port 80, for this run

'sudo unlink /etc/nginx/sites-enabled/default'

### Reload Nginx to apply changes

'sudo systemctl reload nginx'

'sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html'

![Alt text](<images/Screenshot 2023-09-18 at 23.11.19.png>)

![Alt text](<images/Screenshot 2023-09-18 at 23.05.02.png>)

## Step 5 - Testing PHP with Nginx

### Create a test PHP file in your document root

'nano /var/www/projectLEMP/info.php'

![Alt text](<images/Screenshot 2023-09-19 at 05.51.32.png>)

### Paste and save PHP code in the nano text editor

'<?php
phpinfo();'

![Alt text](<images/Screenshot 2023-09-19 at 05.39.29.png>)

### Access the page in a web browser

'http://35.179.96.37/info.php'

![Alt text](<images/Screenshot 2023-09-19 at 05.46.57.png>)

### Remove the file

'sudo rm /var/www/projectLEMP/info.php'

![Alt text](<images/Screenshot 2023-09-19 at 05.54.44.png>)

## Step 6 - Retrieving data from MySQL database with PHP

### Connect to MySQL console using the root account

'sudo mysql'

'sudo mysql -p'

![Alt text](<images/Screenshot 2023-09-19 at 06.12.38.png>)

### Create a new database from the MySql console

'mysql> CREATE DATABASE `example_database`;'

![Alt text](<images/Screenshot 2023-09-19 at 06.16.59.png>)

### Create a new user and define user's password

'mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';'

![Alt text](<images/Screenshot 2023-09-19 at 06.18.57.png>)

### Grant the user permission over the database

'mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';'

![Alt text](<images/Screenshot 2023-09-19 at 06.21.34.png>)
![Alt text](<images/Screenshot 2023-09-19 at 06.23.03.png>)

### Test new user has proper permission by logging in

'mysql -u example_user -p'

![Alt text](<images/Screenshot 2023-09-19 at 06.26.30.png>)

### Confirm new user access to the database

'mysql> SHOW DATABASES;'

![Alt text](<images/Screenshot 2023-09-19 at 06.28.05.png>)

### Create a test table

'mysql> CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT,content VARCHAR(255),PRIMARY KEY(item_id));'

![Alt text](<images/Screenshot 2023-09-19 at 06.32.39.png>)

### Insert a few rows of content in the test table

'mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");'

'mysql> INSERT INTO example_database.todo_list (content) VALUES ("My second important item");'

'mysql> INSERT INTO example_database.todo_list (content) VALUES ("My third important item");'

'mysql> INSERT INTO example_database.todo_list (content) VALUES ("My fourth important item");'

![Alt text](<images/Screenshot 2023-09-19 at 06.48.36.png>)

### Confirm data was successfully saved to the table

'mysql>  SELECT * FROM example_database.todo_list;'

![Alt text](<images/Screenshot 2023-09-19 at 06.50.51.png>)

### Exit MySQL console

'mysql> exit'

![Alt text](<images/Screenshot 2023-09-19 at 06.55.46.png>)

### Create a PHP script that will connect to MySQL and query for your content

'nano /var/www/projectLEMP/todo_list.php'

![Alt text](<images/Screenshot 2023-09-19 at 07.01.15.png>)

### Add content to PHP script

![Alt text](<images/Screenshot 2023-09-19 at 07.00.02.png>)

### Access page in Web browser

'http://35.179.96.37/todo_list.php'

![Alt text](<images/Screenshot 2023-09-19 at 07.03.34.png>)











