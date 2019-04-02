## 1.4 初始化配置

假设框架安装目录在 /home/wwwroot/phpxl/ 目录下

1. 打开nginx 配置文件，设置网站对应的根目录

```text
   vim /usr/local/nginx/config/nginx.conf
```

```text

server
    {
        listen 80 default_server;
        #listen [::]:80 default_server ipv6only=on;
        server_name www.yourdomian.com
        index index.html index.htm index.php;
        root  /home/wwwroot/phpxl/project/default/www; #配置网站根目录
        ...
     }
```

重启nginx 服务器


2. 打开数据库配置文件
```text

   vim /home/wwwroot/phpxl/project/default/config/database.php

```

```php

<?php
return [
    'master'=>'host=localhost;port=3360;username=数据库帐号;password=数据库密码;',
    'slaves'=>[
        0=>'host=localhost;port=3306;username=数据库帐号;password=数据库密码;',
    ],
    'driver'=>'mysql', //mysql,sqlsrv
    'database'=>'defaultdb', //默认的数据库名
    'tablepre'=>'xl_',       //数据库浅醉
    'engine'=>'InnoDB', //InnoDB,MyISAM,MEMORY
    'charset'=>'utf8',
    'type'=>'pdo',
    'debug'=>true,
    'pconnect'=>0,
    'autoconnect'=>0
]; 

```

3. 打开缓存配置文件

````text
    vim /home/wwwroot/phpxl/project/default/config/cache.php
```

```php
<?php

return [
    'file'=>[
        'type'=>'file',
        'debug'=>true,
        'pconnect'=>0,
        'autoconnect'=>0,
    ],
    'memcache'=>[
        'hostname'=>'localhost',
        'port'=>11211,
        'type'=>'memcache',
        'debug'=>true,
        'pconnect'=>0,
        'autoconnect'=>0,
        'pre'=>'@ns_ls_',
        'ismaster'=>true,
    ],
    'redis'=>[
        'hostname'=>'127.0.0.1',
        'port'=>6379,
        'timeout'=>0,
        'type'=>'redis',
        'debug'=>true,
        'pconnect'=>0,
        'autoconnect'=>0,
        'pre'=>'@ns_ls_',
        'isusecluster'=>false,
    ],
    'apc'=>[
        'type'=>'apc',
        'pre'=>'@ns_ls_',
    ],
        'xcache'=>[
        'type'=>'xcache',
        'pre'=>'@ns_ls_',
    ],
    'eaccelerator'=>[
        'type'=>'eaccelerator',
        'pre'=>'@ns_ls_',
    ],
    '__pre'=>'TnPGcc_',
];

```
这是默认配置，如有需要改的，可以手动修改。


