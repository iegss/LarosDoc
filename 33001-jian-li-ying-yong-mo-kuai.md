# 建立应用模块

## 手动建立应用模块

1. 建立应用模块主文件夹。如：Demo
2. 建立应用模块子文件夹。Config、Controllers、Dbtables、Model、Views
3. 建立应用模块必要的文件。

   ##### Config/config.php

   ```php
    <?php

    return [
        'module_name' => 'Demo',
        'colse' => false,
        'service_provider' => \Modules\Demo\BootServiceProvider::class,
    ];
   ```

   ##### BootServiceProvider.php

   ```php
   <?php

    namespace Modules\Demo;

    use Iegss\Larbase\BootServiceProvider as MServiceProvider;

    class BootServiceProvider extends MServiceProvider {

        public function register(){
            $this->initRegister();
        }

        public function boot(){

        }
    }
   ```

   ##### routes.php
    
    ```php
   <?php
    
   $this->app->group(['namespace' => 'Modules\Demo\Controllers', 'prefix' => 'demo'],  function ($app) {
    
   });
    ```



