## 1.6 目录结构

```text

phpxl 项目外层目录
│  
├─ project 项目总包 
│     ├─ default 默认的项目
│             ├─cli     脚本目录
│             ├─config  配置文件目录
│             ├─dataset 数据源目录
│             ├─event   事件目录
│             ├─func    自定义扩展函数目录
│             ├─iapi    与插件通信接口目录
│             ├─logic   逻辑层目录
│             ├─model   数据模型目录
│             ├─module  路由层目录
│             ├─plugin  插件目录
│             ├─point   埋点目录
│             ├─rpc     rpc目录
│             ├─task    任务节点目录
│             ├─www     网站根目录
│                 ├─static  js及图片目录
│                 ├─third   第三方sdk包
│                 ├─vendor  用户自引用第三方组件库
│                 ├─view    模版目录
│                 ├─clipure.php cli模式下入口文件
│                 ├─index.php   网站统一入口文件
│
├─ xlcloud xl框架目录
        ├─ api 一些api接口
        ├─ base 基类目录
        ├─ classs 常用类
        ├─ core 一些核心文件
        ├─ func 全局函数目录
        ├─ third 框架用到的第三方sdk目录
        ├─ until 常用工具类文件目录
        ├─ vendor 框架集成的第三方组件库
        ├─ AutoLoad.php 自动加载类
        ├─ XlConfig.php 配置文件读写类
        ├─ XlContainer.php 依赖注入容器
        ├─ XlInjector.php 依赖注入工厂
        ├─ XlLead.php 框架入口文件
        ├─ XlRouter.php 路由解析类
        ├─ XlStatic.php 框架常量定义文件
```

