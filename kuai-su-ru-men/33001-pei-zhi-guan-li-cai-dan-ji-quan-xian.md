# 6、配置管理菜单及路由

## 配置管理菜单文件 Demo/Config/config.php, 如下：

```php
<?php

return [
    'module_name' => 'Demo',
    'colse' => false,
    'service_provider' => \Modules\Demo\BootServiceProvider::class,
    'description' =>  'Demo模块应用',
    'author' => 'iegss',
    'admin_permission' => [
        [
            'name' => 'Demo内容管理',
            'is_menu' => true,
            'uri' => 'demo/admin/article/index',
            'slug' => 'demo.admin.article@index',
            'icon' => 'fa fa-file-text-o',
            'order_by' => 1,
            'son' => [
                [
                    'name' => '文章列表',
                    'small_title' => '文章数据列表',
                    'is_menu' => true,
                    'uri' => 'demo/admin/article/index',
                    'slug' => 'demo.admin.article@index',
                    'icon' => 'fa fa-list',
                    'order_by' => 1,
                    'son' => [
                        [
                            'name' => '文章添加',
                            'small_title' => '文章内容添加',
                            'is_menu' => false,
                            'uri' => 'demo/admin/article/add',
                            'slug' => 'demo.admin.article@add',
                            'icon' => '',
                            'order_by' => 1
                        ],
                        [
                            'name' => '文章编辑',
                            'is_menu' => false,
                            'uri' => 'demo/admin/article/edit',
                            'slug' => 'demo.admin.article@edit',
                            'icon' => '',
                            'order_by' => 1
                        ],
                        [
                            'name' => '文章删除',
                            'is_menu' => false,
                            'uri' => 'demo/admin/article/del',
                            'slug' => 'demo.admin.article@del',
                            'icon' => '',
                            'order_by' => 1
                        ]
                    ]
                ],
            ]
        ]
    ]
];
```

## 配置路由文件 Demo/routes.php, 如下：

```php
<?php

//这里写前端访问的路由
$this->app->group(['namespace' => 'Modules\Demo\Controllers', 'prefix' => 'demo'],  function ($app) {

});

//这里写后端管理路由
$this->app->group([
    'middleware' => ['admin.login','admin.permission'],
    'namespace' => 'Modules\Demo\Controllers\Admin',
    'prefix' => 'demo/admin'],  function ($app) {

    $app->registerAdminRoutes('article');

});
```

