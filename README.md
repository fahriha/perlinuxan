=======================

sudo su
apt update
apt -y install software-properties-common net-tools

=======================

apt-get -y install apache2 mariadb-client mariadb-server \
libphp-adodb libgd3 libgd-dev php-mysql php-gd php-curl \
php-pear php php-cli php-dev php-intl php-mbstring

================================
pecl channel-update pecl.php.net
apt -y install yaz libyaz-dev

pear upgrade --force
update-alternatives --config php-config
pecl install yaz
pear config-show | grep ext_dir

================================
sudo update-alternatives --config php

EDIT
vi /etc/php/8.3/apache2/php.ini
vi /etc/php/8.3/cli/php.ini

INTO EDIT :
extension=yaz.so

COMANDER RESTART :
/etc/init.d/apache2 reload

sudo systemctl restart apache2
sudo systemctl status apache2

====================\\\\\\\\\\\\\\\\\\\\\\\\\\\\ INSTALL APPS
cd /usr/local/src
wget https://github.com/slims/slims9_bulian/releases/download/v9.6.1/slims9_bulian-9.6.1.tar.gz
tar zxvf slims9_bulian-9.6.1.tar.gz
mv slims9_bulian-9.6.1 /var/www/html/slims
chown -Rf www-data:www-data /var/www/html/slims/

**Siapkan database MySQL jika di operasikan di Internet**

mysql -u root -p
password:
create database senayan;
GRANT ALL PRIVILEGES ON senayan.* TO 'senayanuser'@'localhost' IDENTIFIED BY 'password_senayanuser';
GRANT ALL PRIVILEGES ON senayan.* TO 'senayanuser' IDENTIFIED BY 'password_senayanuser';
quit

**Bagi anda yang masih belajar di LAN lokal, dengan asumsi password root 123456, dapat menggunakan**
mysql -u root -p123456

create database slims;
GRANT ALL PRIVILEGES ON slims.* TO slims@localhost IDENTIFIED BY 'slims';
GRANT ALL PRIVILEGES ON slims.* TO 'slims' IDENTIFIED BY 'slims';
QUIT

sudo systemctl restart mariadb 
sudo systemctl status mariadb

================ VIA WEB HTTP
chown -Rf www-data:www-data /var/www/html/slims

**Akses ke Web Digital Library Senayan Melalui**

http://ip-address/slims/install/index.php
http://192.168.0.190/slims/install/index.php

**preview**

Get Started

Pastikan
  GD : installed
  Mbstring : installed
  Gettext : installed
  PDO MySQL : installed
  YAZ : installed
Next

Install SLiMS
Text Connection
Connection OK, Next
  username admin
  password admin
Run Installation

rm -Rf /var/www/html/slims/install/








