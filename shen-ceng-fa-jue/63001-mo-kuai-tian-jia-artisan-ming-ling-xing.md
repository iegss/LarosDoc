# 1、Artisan 命令行

## 1. 建立文件夹

在对应模块下建立文件夹, 如：Demo\Console\Commands

## 2、建立命令行执行类

如：

```php
<?php

namespace Modules\Demo\Console\Commands;

use Iegss\Larbase\Console\Command;  // 注意继承的类

class DemoCommand extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'Demo:DemoCommand {action : start|stop|restart|reload|infos}';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = 'Demo commands';

     /**
     * Execute the console command.
     *
     * @return mixed
     */
    public function handle()
    {
        // 在这里写需要执行的代码

        $this->action = $this->argument('action');
        echo $this->action;
        return true;
    }
}
```

## 3、配置生效

在对应模块的配置文件（Config/config.php）中添加console\_commands 参数类 如：

```php
<?php
'console_commands' => [
      'Modules\Demo\Console\Commands\DemoCommand',
    ],
```

## 4、在命令行中执行

php artisan Demo:DemoCommand start

