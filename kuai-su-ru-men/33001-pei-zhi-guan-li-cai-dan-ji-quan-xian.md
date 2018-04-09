#配置管理菜单及路由

#### 配置管理菜单文件 Demo/Config/config.php, 如下：

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


