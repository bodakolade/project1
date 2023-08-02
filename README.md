Project 1
INSTALLING APACHE
run 
        sudo apt update
          sudo apt install apache2
           sudo systemctl status apache2
            curl http://localhost:80
Open web browser to access 
         http://3.137.143.88:80
INSTALLING MYSQL
run
      sudo apt install mysql-server
	sudo mysql
         'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1'
           exit mysql
             sudo mysql_secure_installation (validate password plugin)
               sudo mysql -p
                 exit
INSTALLING PHP
run
      sudo apt install php libapache2-mod-php php-mysql
       php -v
CREATING VIRTUAL HOST
run
       sudo mkdir /var/www/projectlamp
	sudo chown -R $USER:$USER /var/www/projectlamp
         sudo vi /etc/apache2/sites-available/projectlamp.conf (blank file was created and pasted <VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>  :wq to save and quit
             sudo ls /etc/apache2/sites-available
              sudo a2ensite projectlamp
   		sudo a2dissite 000-default
		 sudo apache2ctl configtest
		  sudo systemctl reload apache2
		   sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
Open web browser to access http://3.137.143.88:80
ENABLE PHP
run
       sudo vim /etc/apache2/mods-enabled/dir.conf then change 
<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
         sudo systemctl reload apache2
          vim /var/www/projectlamp/index.php (insert <?php
phpinfo();
            sudo rm /var/www/projectlamp/index.php (to remove file)

PROJECT 1 COMPLETED SUCCESSFULLY
