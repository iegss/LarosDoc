# 安装主要步骤：

#### 1、下载代码。

git clone [https://git.oschina.net/iegss/laros.git](https://git.oschina.net/iegss/laros.git)

#### 2、下载更新第三方库。

使用 composer update 命令进行安装。  
注：未装composer，可解压doc中的vendor.zip到跟目录.

#### 3、配置环境。

配置好PHP运行环境，网站根目录指向pubic。并设置storage、config目录可写。

#### 4、安装基础LarOS软件系统

访问 [http://\*\*\*\*/insatll](http://****/insatll) 进行安装操作。

# 环境安装 及 Zend Guard Loader 库安装说明

## 环境要求：

PHP 5.6.\*  
Mysql 5.6 +  
php 扩展库 Zend Guard Loader v3.3

### Windows 开发平台推荐安装步骤：

* 1、下载phpStudy并安装, [http://www.phpstudy.net/phpstudy/phpStudy20161103.zip](http://www.phpstudy.net/phpstudy/phpStudy20161103.zip)

* 2、切换版本（php-5.6.27-nts + Apache/nginx）, 如是nginx需要配置重写。

* 3、复制 doc/ZendLoader/php5.6/ZendLoader.dll 到phpStudy安装对应的php扩展目录下。

如：D:\phpStudy\php\php-5.6.27-nts\ext

* 4、配置php.ini。

4.1 其它选项菜单-》打开配置文件-》php.ini 文件

4.2 php.ini 在最后加入：

`zend_extension="ZendLoader.dll"`

`zend_loader.enable=1`

`zend_loader.disable_licensing=0`

`zend_loader.obfuscation_level_support=3`

`zend_loader.license_path=""`

* 5、重启环境并检查是否安装成功。

--------- nginx 环境重写配置 ---------

