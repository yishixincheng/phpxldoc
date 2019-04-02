## 1.2 环境依赖与web服务器安装


### 环境依赖

* PHP >= 7.0.0
* Redis及扩展
* Linux或Windows系统
* Mysql5.7以上或Sqlserver
* linux或apache

Linux操作系统下，安装web服务器流程如下

一键安装web集成环境[lnmp](https://lnmp.org/install.html)。
安装完成后安装相关[扩展](https://lnmp.org/faq/addons.html)。

推荐安装Memcached，Redis,imageMagick扩展


### 安装nginx后进行配置

a. 打开/usr/local/nginx/conf目录

b. 创建xlrouter.conf文件，内容如下
```text
location / {
    try_files $uri $uri/ /index.php?$query_string;
}
```

c. 配置网站根目录。打开/usr/local/nginx/conf/nginx.conf
```text

server
    {
        listen 80 default_server;
        #listen [::]:80 default_server ipv6only=on;
        server_name www.yourdomian.com
        index index.html index.htm index.php;
        root  网站根目录; #配置网站根目录

        #error_page   404   /404.html;

        # Deny access to PHP files in specific directory
        #location ~ /(wp-content|uploads|wp-includes|images)/.*\.php$ { deny all; }

        include enable-php.conf;
        include xlrouter.conf; # 加上这一行
        ...
     }

```
d. 打开配置文件。/usr/local/nginx/conf/fastcgi.conf

```text

fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
fastcgi_param  QUERY_STRING       $query_string;
fastcgi_param  REQUEST_METHOD     $request_method;
fastcgi_param  CONTENT_TYPE       $content_type;
fastcgi_param  CONTENT_LENGTH     $content_length;

...

# PHP only, required if PHP was built with --enable-force-cgi-redirect
fastcgi_param  REDIRECT_STATUS    200;
fastcgi_param PHP_ADMIN_VALUE "open_basedir=/home/wwwroot:/tmp/:/proc/"; #如果我们把phpxl安装在/home/wwwroot目录下，则加上/home/wwwroot:，即php可以访问的目录
                                                                          

```


e. 打开php配置文件
```text
   cd /usr/local/php/etc/php.ini
``` 

找到disable_functions= 移除后面的函数

错误级别修改如下
error_reporting = E_ALL & ~E_NOTICE
 

f. 重新nginx服务器,命令行输入以下代码
```text
   /etc/init.d/nginx restart
```

完成以上步骤，即为xl框架搭建好所需要的web环境。
