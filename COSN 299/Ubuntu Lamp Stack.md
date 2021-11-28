# Professor Lu Commands
sudo apt install
sudo apt upgrade
sudo apt install apache2
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.0 php8.0-{fpm,mysql,curl,gd,mbstring,xml,mcrypt,zip,ldap} libapache2-mod-php8.0
sudo a2enmod proxy_fcgi setenvif
sudo a2enconf php8.0-fpm
sudo a2dismod php8.0
sudo systemctl enable php.8.0-fpm
sudo service apache2 restart; sudo service php8.0-fpm restart

sudo usermod -a -G www-data ubuntu
logout and log back in
sudo chown -R ubuntu:www-data /var/www
sudo chmod 2775 /var/www
find /var/www -type d -exec sudo chmod 2755 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;

## Install Apache Server
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y

## Install Database Server

### Maria DB Install
sudo apt install mariadb-server mariadb-client -y

This is another way to install it
curl -LsS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash -s -- --mariadb-server-version="mariadb-10.5"
sudo apt install mariadb-server
scp -i mykey.pem someFile.zip me@10.10.10.10:/home/files
unzip osticket.zip
sudo mv upload/ /var/www/html/osticket

### MYSQL install
sudo apt install mysql-server -y
sudo mysql_secure_Installation

This is another way to install it
wget https://repo.mysql.com//mysql-apt-config_0.8.18-1_all.deb
sudo dpkg -i mysql.deb
sudo apt update
sudo apt-cache policy mysql-server
sudo apt install mysql-client mysql-community-server mysql-server
sudo mysql_secure_installation

#### Create database
sudo mysql -u root -p
create database osTicket;
show databases
create user 'test_user'@'localhost' identified by 'weakPassword1!'
grant all privileges on osTicket.* to 'test_user'@'localhost';
flush privileges;
exit;

## Install PHP
sudo apt install php -y
sudo apt install -y php-{common,mysql,xml,xmlrpc,curl,gd,imagick,cli,dev,imap,mbstring,opcache,soap,zip,intl,apcu,json}
sudo systemctl restart apache2
sudo vim /var/www/html/info.php
```php
<?php
	phpinfo();
?>
```
sudo vim /var/www/html/database_test.php
```php
<?php

$conn = new mysqli('localhost', 'test_user', 'weakPassword1!', 'osTicket');

if ($conn->connect_error) {
    die("Database connection failed: " . $conn->connect_error);
}

echo "Database connection was successful";
```

## Install OSTicket
```bash
sudo apt install -y php-common php-gd php-imap php-intl php-apcu php-cli php-mbstring php-curl php-mysql php-json php-xml
sudo systemctl restart apache2
sudo apt install unzip -y
sudo mkdir -p /var/www/osTicket
sudo chown -R $USER:$USER /var/www/osTicket/
cd /var/www/osTicket/
wget https://github.com/osTicket/osTicket/releases/download/v1.15.2/osTicket-v1.15.2.zip
unzip osticket.zip
rm ofticket.zip
sudo cp upload/include/ost-sampleconfig.php upload/include/ost-config.php
sudo chwon -R www-data:www-data /var/www/osTicket
sudo chmod -R 755 /var/www/osTicket
```