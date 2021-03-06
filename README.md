# WordPress

### 1. 开发环境，可以使用Homestead(Vagrant)

### 2. Here is the correct file permissions for Wordpress:  
  
````
sudo chown www-data:www-data -R *          # Let apache be owner
sudo find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
sudo find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--
````
  


### 3. 配置EC2(Ubuntu)：
-----------------------------------
SETUP: WP + Apache2 + MySQL
-----------------------------------

 // install 
 ````  
sudo apt-get update --fix-missing
sudo apt-get install apache2
sudo add-apt-repository ppa:ondrej/php5
sudo apt-get update

sudo apt-get install php5 libapache2-mod-php5
php --version
sudo apt-get install git-core php5-mcrypt mysql-server
````  
// composer  
````  
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer

sudo apt-get install php5-curl php5-mysql
````  
// source code

########################################
### git clone......
########################################

// Permalinks permission      
// 重要的是，记得touch .htaccess ，设置chmod 664 ,空文件也没问题。     
````   
sudo touch .htaccess  
sudo chown www-data:www-data .htaccess  
sudo chmod 664 .htaccess  
sudo a2enmod rewrite// enabling mod_write in the Apache2 server  
sudo service apache2 restart  
````  
// folder permission  
````  
sudo chown www-data:www-data -R *
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;
````   
// visual host config   
````
sudo nano /etc/apache2/sites-available/000-default.conf  
````    
  
````  
<VirtualHost *:80>
    ServerAdmin admin@example.com
    ServerName hostname.com
    ServerAlias www.hostname.com
    DocumentRoot /var/www/hostname.com
    <Directory "/var/www/hostname.com">  
        AllowOverride All  
        Options -Indexes   
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
````   
  

### 4. Ubuntu中增加apache上传文件大小限制：
-----------------------------------   
方法一：   
````
sudo nano /etc/php5/apache2/php.ini  
````    

upload_max_filesize = 2M   
memory_limit = 128M   
post_max_size = 8M    

命令行执行:    
> sudo service php-fpm restart


方法二：  
在.htaccess头部添加：    
````  
php_value upload_max_filesize 64M
php_value post_max_size 64M

php_value max_execution_time 300
php_value max_input_vars 3000
````  
  
---- 



### 5. 关于WP备份  
-----------------------------------     
1. 使用数据库导入导出比较安全  
2. 如果是展示型网站，尽量不要使用aws s3,直接上传到wp默认的 uploads  



to be continus    
---- 
ashucn@gmail.com  



