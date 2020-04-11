# 2、计划任务

## 1、在对应模块中建立计划任务文件

在对应模块中的Console文件夹下建立Crontab.php文件。

## 2、编写执行的代码

内容格式如下：

```php
<?php

namespace Modules\Demo\Console;

use Illuminate\Console\Scheduling\Schedule;

class Crontab
{

    public function schedule(Schedule $schedule)
    {
        // 在这里写需要按计划执行的任务

        $schedule->call(function (){

            // 在这里写需要执行的代码
            _logs('demo crontab log');

        })->cron('* * * * *'); // 与Linux系统的计划任务写法一致

    }

}
```

## 3、配置操作系统执行

以Linux为例：

### 3.1 编辑crontab

如：crontab -e -u www （为防文件权限问题，需要带上站点执行的用户）

### 3.2 重启生效

```bash
# crontab -e -u www
# crontab 添加如下内容：
 * * * * * /www/server/php/56/bin/php /程序目录/artisan schedule:run >> /dev/null 2>&1
# service crond restart
```

