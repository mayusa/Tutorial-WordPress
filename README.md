# WordPress

### 1. 开发环境，可以使用Homestead(Vagrant)

### 2. Here is the correct file permissions for Wordpress:  
````
sudo chown www-data:www-data -R *          # Let apache be owner
sudo find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
sudo find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--
````
  
### 3. 伪链接的配置    
[5 Simple Steps to Configure WordPress To Use Permalinks On An Ubuntu Server](http://mixeduperic.com/ubuntu/5-simple-steps-to-configure-wordpress-to-use-permalinks-on-an-ubuntu-server.html)
