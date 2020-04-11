# 3、队列

这里以数据库驱动为例，其它驱动配置请参考 [laravel 手册](https://laravel-china.org/docs/laravel/5.3/queues/1185) 。

## 1、配置队列驱动

配置env文件： QUEUE\_DRIVER=database

**注：** 本地单机测试可设置为：QUEUE\_DRIVER=sync，这时本节第4点可跳过。

## 2、编写任务类

在对应模块中添加处理类，如：

```php
<?php

namespace Modules\Demo\Queues;

use Iegss\Larbase\Queues\QueueBase;

class DemoQueue extends QueueBase
{
    var $data;
    public function __construct($data)
    {
        $this->data = $data;
    }

    public function handle(){
        _logs($this->data);

        // 在这里写需要在队列中执行的代码

        return true;
    }

}
```

## 3、添加执行任务

```php
dispatch(new \Modules\Demo\Queues\DemoQueue($data));
```

## 4、后台执行任务

```bash
# nohup /www/server/php/56/bin/php /程序目录/artisan queue:work > /www/crontab/logs/queue_high.logs 2>&1 &
```

上面是执行默认队列，如任务需要更高的优先执行，需要再开启一个后台执行任务，如： php /程序目录/artisan queue:work --queue=high

同时在添加执行任务时设置优先级参数，如： dispatch\(\(new \Modules\Demo\Queues\DemoQueue\($data\)\)-&gt;onQueue\('high'\)\);

