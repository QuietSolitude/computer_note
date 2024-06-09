# 如何在docker容器里安装wordpress

什么是WordPress
------------------------
WordPress是一个以PHP和MySQL为平台的自由开源的博客软件和内容管理系统。    

WordPress有哪些依赖
-------------------------
WordPress依赖php环境和php的解释器，数据库，还有nginx来代理服务器。

WordPress依赖的安装
------------------------
先安装PHP，在安装前确保容器内的内容都是最新的。    
`apt-get update`      
添加对其他软件源的管理    
`apt -y install software-properties-common`    
安装存储库ppa:ondrej/php，它将为您提供所有版本的 PHP：     
`add-apt-repository ppa:ondrej/php`    
PHP环境配置好后，安装PHP7.4：    
`apt -y install php7.4`    
检查是否安装成功和查看PHP的版本
`PHP -v`
安装一些常用的模块
`pt-get install -y php7.4-cli php7.4-json php7.4-common php7.4-mysql php7.4-zip php7.4-gd php7.4-mbstring php7.4-curl php7.4-xml php7.4-bcmath`    

由于nginx是通过fastcgi连接PHP的,在run/php文件夹里没有的要安装    
`apt install php7.4-fpm`     

什么是Nginx
--------------------------
nginx是一个网页服务器。     

nginx安装
--------------------------
安装nginx     
`apt-get install nginx -y`
安装完后查看nginx的运行状态    
`service nginx status`
如果nginx没有运行就要启动nginx
`service nginx start`    
查看nginx进程
`ps aux | grep nginx`
想要停止nginx
`service nginx stop`
nginx重启
`service nginx restart`

什么是MariaDB
------------------------------
mariaDB是一个数据库。

安装mariadb     
`apt-get install mariadb-server -y`

安装完后查看mariadb运行状态
`service mariadb status`

如果没有运行就要启动    
`service mariadb start`

启动后要登录数据库    
`mysql -u root -p Password`

创建数据库wordress_db    
`CREATE DATABASE wordpress_db;`

对用户进行wordpress_db数据库进行授权，all表示所有操作     
以下命令的用户是wpuser password是密码需要设置。  
`mGRANT ALL ON wordpress_db.* TO 'wpuser'@'localhost' IDENTIFIED BY 'Password' WITH GRANT OPTION; `    
对用户数据和权限有修改后，不想重启数据库让修改的内容直接生效可以用以下命令    
`FLUSH PRIVILEGES;`
设置完之后退出
` exit`

安装完以上内容就需要为WordPress创建Nginx配置文件
--------------------------------------------
使用下面命令来创建
`nano /etc/nginx/sites-enabled/wordpress.conf`
并将下面内容放在这个文件里，告诉nginx在什么时候执行什么。
```
server {             
            listen 80;             
            root /var/www/html/wordpress;             
            index index.php index.html;             
            server_name localhost;             
           
            access_log /var/log/nginx/www.access.log;             
            error_log /var/log/nginx/www.error.log;              

            location / {                            
                 try_files $uri $uri/ /index.php?$args;
            }
         
            location ~ \.php$ {
            include snippets/fastcgi-php.conf;                            
                 fastcgi_pass unix:/run/php/php7.4-fpm.sock;             
            }              

            location ~ /\.ht {                            
                 deny all;             
            }             

            location = /favicon.ico {                            
                 log_not_found off;                            
                 access_log off;             
            }             

            location = /robots.txt {                            
                 allow all;                            
                 log_not_found off;                            
                 access_log off;             
            }             

            location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {                            
                 expires max;                            
                 log_not_found off;             
            }  
}
```
保存后退出检查配置文件是不是正确
`nginx -t`

操作完后需要重新加载Nginx才能应用这些修改的设置。
`service nginx reload`

最后下载和配置 WordPress
------------------------------
先cd到wordpress文件夹里    
`cd /var/www/html/wordpress `
下载WordPress    
`wget https://cn.wordpress.org/latest-zh_CN.tar.gz`
解压WordPress文件    
`tar -zxvf latest-zh_CN.tar.gz`
将wordpress所有文件和目录移动到当前目录下    
`mv wordpress/* . `
删除解压文件
`rm -rf wordpress latest-zh_CN.tar.gz`
将更改文件所有权和应用权限给Wordpress的所有文件

先`cd /var/www/html`    

改变用户组里所有的用户的文件
chown是改变文件的拥有者，R是指文件夹里所有文件，第一个www-data是用户名，第二个是用户组 
`chown -R www-data:www-data *`
给文件赋予权限。     
`chmod -R 755 *`

配置 wp-config.php 文件
---------------------------------     
先`cd /var/www/html/wordpress`

移动wp-config-sample.php wp-config.php    
`mv wp-config-sample.php wp-config.php`

打开wp-config.php文件    
`nano wp-config.php`
找出以下内容，并修改参数 
```
define('DB_NAME', 'wordpress_db');  
define('DB_USER', 'wpuser');  
define('DB_PASSWORD', 'Passw0rd!');  
...  
... 
define( 'AUTH_KEY', 'put your unique phrase here' ); 
define( 'SECURE_AUTH_KEY', 'put your unique phrase here' ); 
define( 'LOGGED_IN_KEY', 'put your unique phrase here' ); 
define( 'NONCE_KEY', 'put your unique phrase here' ); 
define( 'AUTH_SALT', 'put your unique phrase here' ); 
define( 'SECURE_AUTH_SALT', 'put your unique phrase here' ); 
define( 'LOGGED_IN_SALT', 'put your unique phrase here' ); 
define( 'NONCE_SALT', 'put your unique phrase here' ); 
```
为了保证Wordpress网站的安全，在数据库选项配置完后，通过[生成安全密匙](https://api.wordpress.org/secret-key/1.1/salt/)并将内容复制粘贴在配置中

安装完成后在浏览器访问域名。
