# WordPress

### 1. 开发环境，可以使用Homestead

### 2. Here is the correct file permissions for Wordpress:  
````
chown www-data:www-data -R *          # Let apache be owner
find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--
````

