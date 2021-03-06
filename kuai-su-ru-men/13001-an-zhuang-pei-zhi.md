# 1、安装配置

## 安装主要步骤：

**1、下载代码（暂未开放）。**

git clone [https://github.com/iegss/LarOS.git](https://github.com/iegss/LarOS.git)

**2、下载更新第三方库。**

使用 composer update 命令进行安装。  
注：未装composer，可解压doc中的vendor.zip到跟目录.

**3、配置环境。**

配置好PHP运行环境，网站根目录指向pubic。并设置storage、config目录可写。

**4、安装基础LarOS软件系统**

访问 [http://\*\*\*\*/install](http://****/install) 进行安装操作。

=======================================================================

## \(php5.6\) 环境安装

### 环境要求：

PHP 5.6.\*  
Mysql 5.6 +  
php 扩展库 Zend Guard Loader v3.3

#### Windows 开发平台推荐安装步骤：

* 1、下载phpStudy并安装, [http://www.phpstudy.net/phpstudy/phpStudy20161103.zip](http://www.phpstudy.net/phpstudy/phpStudy20161103.zip)
* 2、切换版本（php-5.6.27-nts + Apache/nginx）, 如是nginx需要配置重写。
* 3、复制 doc/ZendLoader/php5.6/ZendLoader.dll 到phpStudy安装对应的php扩展目录下。

如：D:\phpStudy\php\php-5.6.27-nts\ext

* 4、配置php.ini。

  4.1 其它选项菜单-》打开配置文件-》php.ini 文件

  4.2 php.ini 在最后加入：

```text
zend_extension="ZendLoader.dll"
zend_loader.enable=1
zend_loader.disable_licensing=0
zend_loader.obfuscation_level_support=3
zend_loader.license_path=""
```

* 5、重启环境并检查是否安装成功。

#### Linux 开发平台推荐安装步骤 （CentOS）

推荐安装宝塔Linux面板  
[https://www.bt.cn/](https://www.bt.cn/)

=======================================================================

## \(php7.1\) 环境安装

### 环境要求：

PHP 7.1.\*

Mysql 5.6

Nginx 1.12 +

php 扩展库：

```text
PATH_INFO 扩展配置开启
ionCube Encoder加密脚本库
fileinfo 文件信息库
```

**注：**如使用宝塔Linux面板安装php7.1, putenv函数默认禁用了，需要在禁用函数中删除。

=======================================================================

### 重写配置

重写去除URL中 index.php 入口的输入。

1、Nginx 环境重写配置

```text
location / {
    try_files $uri $uri/ /index.php$is_args$query_string;
}
```

2、Apache 环境.htaccess重写配置

```text
Options +FollowSymLinks
RewriteEngine On

RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]
```

