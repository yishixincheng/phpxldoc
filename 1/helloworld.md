## 1.5 输出hello world
 
 
* 打开project/default/module/IndexModule.php 文件

```php

<?php
namespace lftsoft\module;

/**
 * Class IndexModule
 * @package lftsoft\module
 * @path("/")
 */
class IndexModule extends MasterModule{

    public function __construct(){
        parent::__construct();
    }
    /**
     * @path({"","GET"})
     */
    public function init(){

         echo "hello world";
    }
}

```

注解：

1. namespace lftsoft\module;

lftsoft这是项目命名空间的根。

打开 project/default/www/index.php，网站程序的统一入口文件

```php

<?php

require __DIR__ . '/../../../xlcloud/XlLead.php';
define('IS_DEBUG', true);           //是否是debug模式，正式上线设置false
define('TIMEOUT_METACACHE', 50);   //Meta缓存时间
define('TIMEOUT_ROUTETIME', 3600); //路由缓存时间
\xl\XlLead::run(__FILE__, ['namespace'=>'lftsoft']);  //设置项目的根命名空间

```

2. project/default/module/ 文件夹下，任意以Module.php对应的Module类文件都是路由解析的对象。

```text
/**
 * Class IndexModule
 * @package lftsoft\module
 * @path("/")      //类注解，注解根路径
 */
class IndexModule extends MasterModule
 
 /**
  * @path({"","GET"})     #方法注解，类注解的路径加上这里注解的路径即是域名访问的目录
  */
 public function init(){

      echo "hello world";
 }

 
```

如上注解，则用户访问http://localhost/ 即可调用对应的init方法，输出“hello world”

举一反三，若类前注解  @path("/test"), 则访问http://localhost/test/,则调用对应的init方法

若类前注解 @path("/test"), init方法前注解 @path({"hello","GET"}),则访问http://localhost/test/hello,则调用init方法

遵循规律，依次类推。