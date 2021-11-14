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

curl -LsS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash -s -- --mariadb-server-version="mariadb-10.5"
sudo apt install mariadb-server

sudo usermod -a -G www-data ubuntu
logout and log back in
sudo chown -R ubuntu:www-data /var/www
sudo chmod 2775 /var/www
find /var/www -type d -exec sudo chmod 2755 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;

## Secure copy
scp -i <privateKey> <sourceFile> <userName>@<machineHost>:<destinationPath>

### Maria DB Install
scp -i mykey.pem someFile.zip me@10.10.10.10:/home/files
unzip osticket.zip
sudo mv upload/ /var/www/html/osticket

### MYSQL install
wget https://repo.mysql.com//mysql-apt-config_0.8.18-1_all.deb
sudo dpkg -i mysql.deb
sudo apt update
sudo apt-cache policy mysql-server
sudo apt install mysql-client mysql-community-server mysql-server
sudo mysql_secure_installation

mysql -u root -p
create database osTicket;
show databases;
sudo apt update
	
sudo apt-get install php-mysql
sudo service apache2 restart
sudo apt update
sudo apt-get install php-gd php-imap php-xml php-mbstring php-intl php-apcu
sudo service apache2 restart
cd /var/www/osTicket
sudo chown -R www-data:www-data /var/www/osTicket
sudo chmod -R 755 /var/www/osTicket
sudo cp include/ost-sampleconfig.php include/ost-config.php
sudo chmod 0666 include/ost-config.php