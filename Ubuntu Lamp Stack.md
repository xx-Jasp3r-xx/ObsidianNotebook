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
sudo chown -R ubuntun:www-data /var/www
sudo chmod 2775 /var/www
find /var/www -type -d -exec sudo chmod 2755 {} \;
find /var/www -type f -exe sudo chmod 0664 {} \;