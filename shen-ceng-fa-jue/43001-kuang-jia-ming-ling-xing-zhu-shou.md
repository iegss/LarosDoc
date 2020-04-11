# 4、框架命令行助手

通过命令行 laros:create 指令可以自动创建模块、表、后台管理。

## 指令格式

```bash
#php artisan laros:create {action : tableAdmin|table|module|dbadmin}  名称   简单描述
```

### 1.tableAdmin: 全自动一键创建表文件及管理后台文件

```bash
#php artisan laros:create tableAdmin auto_test_demo 测试demo
```

**注：**该指令无模块时会自动创建对应模块，并会自动创建后台管理菜单及文件。

### 2.table: 一键创建表

```bash
#php artisan laros:create table auto_test_demo 测试demo
```

**注：**该指令无模块时会自动创建对应模块，不会创建后台管理。

### 3.module: 创建模块

```bash
#php artisan laros:create module Auto 模块名称
```

### 4.dbadmin: 创建表的后台管理功能及菜单

```bash
#php artisan laros:create dbadmin auto_test_demo 测试demo
```

**注：**该指令不会自动创建表文件及model类

### 5.api: 创建标准API接口文件及路由

格式:

```bash
#php artisan laros:create api 模块名_表名 简单描述 接口类型 版本号
```

**接口类型：** base: 通用接口类（默认）； shop：商户店铺类； user：会员用户类；

**版本号：** 默认 V1

**注：** api指令不适合部分需要手动编写接口文档的旧版。

