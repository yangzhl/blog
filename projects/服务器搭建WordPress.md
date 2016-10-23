##服务器搭建==WordPress==
###### refence
[1. How To Install Wordpress on Centos 6 ](http://How To Install Wordpress on Centos 6)

* set up LAMP(linux Apache Mysql Php)
	- Install Apache

	```
	sudo yum install httpd
    sudo service httpd start
```


	That’s it. To check if Apache is installed, direct your browser to your server’s IP address (eg. http://12.34.56.789). The page should display the words “It works!" like [this](http://assets.digitalocean.com/tutorial_images/NLSJR.png).
~查找ip 使用命令行ifconfig就可以了~

	- Install Apache
	```
sudo yum install mysql-server
	sudo service mysqld start
```
`sudo /usr/bin/mysql_secure_installation`
给mysql设置root密码
	安装过程会一直问你问题，一直选择y就可以安装了
    Once it is done installing, you can set a root MySQL password:（只允许root用户能够登陆mysql）
    以root身份登陆mysql `mysql -u root -p`
    - Install PHP
    sudo yum install php php-mysql
    **PHP Modules**
	PHP also has a variety of useful libraries and modules that you can add onto your server. You can see the libraries that are available by typing:

	`yum search php-`
	Terminal then will display the list of possible modules. The beginning looks like this:

```
    php-bcmath.x86_64 : A module for PHP applications for using the bcmath library
    php-cli.x86_64 : Command-line interface for PHP
    php-common.x86_64 : Common files for PHP
    php-dba.x86_64 : A database abstraction layer module for PHP applications
    php-devel.x86_64 : Files needed for building PHP extensions
    php-embedded.x86_64 : PHP library for embedding in applications
    php-enchant.x86_64 : Human Language and Character Encoding Support
    php-gd.x86_64 : A module for PHP applications for using the gd graphics library
    php-imap.x86_64 : A module for PHP applications that use IMAP
```
	To see more details about what each module does, type the following command into terminal, replacing the name of the module with whatever library you want to learn about.

`    yum info name of the module`
	Once you decide to install the module, type:

	sudo yum install name of the module
You can install multiple libraries at once by separating the name of each module with a space.

Congratulations! You now have LAMP stack on your droplet!
直至安装成成功了

设置这三个服务开机启动
We should also set the processes to run automatically when the server boots (php will run automatically once Apache starts):

```
sudo chkconfig httpd on
sudo chkconfig mysqld on
```
	- See PHP on your Server
	
    Although LAMP is installed on your virtual server, we can still take a look and see the components online by creating a quick php info page

To set this up, first create a new file:

sudo nano /var/www/html/info.php
Add in the following line:

<?php
phpinfo();
?>
Then Save and Exit.

Restart apache so that all of the changes take effect on your virtual server:

sudo service httpd restart
Finish up by visiting your php info page (make sure you replace the example ip address with your correct one): http://12.34.56.789/info.php

* 安装WordPress
wget http://wordpress.org/latest.tar.gz
tar -xzvf latest.tar.gz 
* 创建WordPress数据库和用户

Now we need to switch gears for a moment and create a new MySQL directory for wordpress.

Go ahead and log into the MySQL Shell:

`mysql -u root -p`

CREATE DATABASE wordpress; (创建数据库名称wordpress)
Query OK, 1 row affected (0.00 sec)

CREATE USER wordpressuser@localhost;（创建用户名wordpressuser）
Query OK, 0 rows affected (0.00 sec)

SET PASSWORD FOR wordpressuser@localhost= PASSWORD("password");（创建密码password）
Query OK, 0 rows affected (0.00 sec)

Finish up by granting all privileges to the new user. Without this command, the wordpress installer will not be able to start up:

GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)
Then refresh MySQL:

FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

- - -
- Setup the WordPress Configuration
	We are almost done uploading Wordpress to the server. The final move that remains is to transfer the unzipped WordPress files to the website's root directory.

	`sudo cp -r ~/wordpress/* /var/www/html`
From here, WordPress has its own easy to follow installation form online.

However, the form does require a specific php module to run. If it is not yet installed on your server, download php-gd:

`sudo yum install php-gd`
Last of all restart Apache:

 sudo service httpd restart
Step Five—RESULTS: Access the WordPress Installation
Once that is all done, the wordpress online installation page is up and waiting for you:

Access the page by adding /wp-admin/install.php to your site's domain or IP address (eg. example.com/wp-admin/install.php) and fill out the short online form (it should look like this).

* * *
关于mysql的一些说明
1. mysql语法必须以;分号结束
2. 如果WordPress忘记密码可以在mysql中重新设置

*  Log into server as root

`mysql -u root -p`
* Enter to MySQL command prompt.
* use user_images
Use WordPress database.

You can check the database name from the WordPress configuration file.
`mysql> use user_images;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A
Database changed
~`

4, Verify user details from “wp_users” table.

We need to select only the following details from “wp_users” table.
mysql> SELECT ID, user_login, user_pass FROM wp_users;
+----+------------+------------------------------------+
| ID | user_login | user_pass                          |
+----+------------+------------------------------------+
|  1 | admin      | $P$BjUKUieEYT1B3TnkQHsv4Y8hfnSK5t. |
+----+------------+------------------------------------+
1 row in set (0.00 sec)

mysql> 
This WordPress has only one user “Admin”. The password displayed here isn’t real, it’s in MD5 encrypted format.
5, Updating user password.

This is the point that we are looking for. As I mentioned, the password displayed is in MD5 format. In latest MySQL versions we can generate the password in MD5 format from the commandline itself. Please see the syntax:
mysql> UPDATE wp_users SET user_pass = MD5('WPEXPLORER') WHERE ID=1 LIMIT 1;(注意WPEXPLORER为新设置的密码，应该要用英文的单引号标记，不要用中文的单引号会出错)
In previous versions we have to enter the password in MD5 format. It’s simple, we can generate it from here >> MD5 <<
Syntax to change the password
mysql> UPDATE wp_users SET user_pass = "61250b88abfe298f2df4821d081a3add"  WHERE ID=1;
Here the user pass in MD5 format.
See the updated password:
mysql> SELECT ID, user_login, user_pass FROM wp_users;
+----+------------+----------------------------------+
| ID | user_login | user_pass                        |
+----+------------+----------------------------------+
|  1 | admin      | 61250b88abfe298f2df4821d081a3add |
+----+------------+----------------------------------+
1 row in set (0.00 sec)

mysql> 