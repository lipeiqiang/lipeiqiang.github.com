---
layout: post
title: CodeIgniter 去掉URL中的index.php
categories:
- Programming
tags:
- PHP
- PHP
---



CodeIgniter 去掉URL中的index.php

在CI根目录下创建一个.htaccess文件
内容如下:

		RewriteEngine on   
		RewriteCond $1 !^(index\.php|images|js|css|robots\.txt)
		RewriteRule ^(.*)$ /index.php/$1 [L]	
上面第二行，是为了设置这些文件和目录可以直接访问。		

在Mac上创建.htaccess文件
		 
		 sudo touch .htaccess
然后修改权限，通过vim上面的配置内容。

检查apache配置，httpd.conf文件
* 是否加载了LoadModule rewrite_module modules/mod_rewrite.so
* 打开配置文件

		sudo vi /etc/apache2/httpd.conf
	查看var/www/html目录是否

		<Directory "/usr/local/www/html">
	    Options FollowSymLinks
	    AllowOverride All
	    Order allow,deny
	    Allow from all
		</Directory> 
		
		
以上完成，就可以去掉URL中的index.php了。我是在Mac OSX 10.8.2下操作的。