#!/bin/bash
# update server
yum update -y
#install nano and other apps
yum install nano -y
yum install wget -y
#install apache
yum install httpd httpd-tools -y
systemctl start httpd
systemctl enable httpd
echo <h2>"Welcome to <a href="http://www.geekdecoder.com" target=blank>GEEKDECODER</a></h2>" > /var/www/html/index.html
# install and add http to firewall
yum install firewalld -y
systemctl enable firewalld
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
systemctl reload firewalld
#Install database
yum install mariadb-server mariadb -y
systemctl start mariadb
systemctl enable mariadb
mysql_secure_installation
yum install php php-fpm php-mysqlnd php-opcache php-gd php-curl php-xml php-mbstring -y
systemctl start php-fpm
systemctl enable php-fpm
