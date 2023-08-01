# **PROJECT 1**
## INSTALING APACHE
`sudo apt update`

`sudo apt install apache2`

![Apache Install](./images/apache%20install.png)

`sudo systemctl status apache2`

![Apache Status](./images/apache%20status.png)

`ccurl http://localhost:80`

[opened browser to access](http://3.137.143.88:80)

![web browser run](./images/web%20browser%20run.png)

## INSTALLING MYSQL
`sudo apt install mysql-server`

`sudo mysql`

![mysql](./images/mysql%20installation.png)

mysql> 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1'
mysql> exit

`sudo mysql_secure_installation (validate password plugin)`

`sudo mysql -p`
exit

## INSTALLING PHP
`sudo apt install php libapache2-mod-php php-mysql`

`php -v`

![php install](./images/php%20install.png)

## CREATING VIRTUAL HOST
`sudo mkdir /var/www/projectlamp`

`sudo chown -R $USER:$USER /var/www/projectlamp`

`sudo vi /etc/apache2/sites-available/projectlamp.conf`
blank file was created and i pasted <VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

`sudo ls /etc/apache2/sites-available`

`sudo a2ensite projectlamp`

`sudo a2dissite 000-default`

`sudo apache2ctl configtest`

`sudo systemctl reload apache2`

`sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

[virtual host](http://3.137.143.88:80)

![virtual host](./images/virtual%20host.png)

## ENABLE PHP
`sudo vim /etc/apache2/mods-enabled/dir.conf`
changed some input

`sudo systemctl reload apache2`

`vim /var/www/projectlamp/index.php`
insert <?php
phpinfo();

![web preview](./images/web%20browser%20preview.png)

`sudo rm /var/www/projectlamp/index.php`

![php enabled](./images/php%20enabled.png)
