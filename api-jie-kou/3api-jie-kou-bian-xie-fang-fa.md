# 3、API 接口编写方法

## 一、配置数据表的增删改查类接口

## 1、配置接口路由

在对应模块Config目录下建立 api\_config.php  
内容如下：

```php
<?php
return [
    [
        'cate_name' => 'Demo接口',  // 接口分类
        'api_routes'=> [   // 路由配置
            'namespace' => 'Modules\Demo\Api\V1', // 命名空间, 一定要
            'prefix' => 'api/v1/demo',  // url 前缀, 一定要
            'middleware' => ['Base.ApiRequestVerify'], // 中间件, 接口认证
        ],
        'child' => [
            [
                'api_title' => '文章 - 列表',   //接口名称
                'api_url' => 'v1/demo/article/getList', // 不包含api入口的接口详情路径,
            ],
            [
                'api_title' => '文章 - 添加',
                'api_url' => 'v1/demo/article/add',
            ],
            [
                'api_title' => '文章 - 得到一行',
                'api_url' => 'v1/demo/article/getRow',
            ],
            [
                'api_title' => '文章 - 修改',
                'api_url' => 'v1/demo/article/edit',
            ],
            [
                'api_title' => '文章 - 删除',
                'api_url' => 'v1/demo/article/del',
            ]
        ],
    ]
];
```

## 2、建立接口处理类

如：在Demo/Api/V1目录下建立ArticleApi.php ，并配置 $api\_table\_name 参数。  
\(注：文件名和类名一致，命名规则: 表名 + Api, 表名可以任一写，但必需加Api\)。

ArticleApi.php 代码如下

```php
<?php

namespace Modules\Demo\Api\V1;

use Illuminate\Http\Request;
use Modules\Base\Api\BaseApiController;


class ArticleApi extends BaseApiController
{
    var $api_table_name = 'demo_article'; //默认接口管理的表名
}
```

#### \* 也可使用“框架命令助手”一键建立对表的增删改查类接口

命令格式:

```bash
#php artisan laros:create api 模块名_表名 简单描述 接口类型 版本号
```

## 二、自定义处理接口

### 1. 在接口处理类中写自定义方法

如：

```php
    public function mdf_article(Request $request){
        $id = $request->input('id');
        $title = $request->input('title');

        $params = [
            'id' => $id,
            'title' => $title,
        ];
        $data =model($this->api_table_name)->addOrModify($params);

        if ($data) {
            return $this->apiReturn('修改成功', 'succ', $add_data, '0');
        }
        return $this->apiReturn('修改失败！', 'fail', [], '403');
    }
```

### 2. 配置api\_config中对应方法路由

```php
 [
     'api_title' => '文章 - 修改文章名',
     'api_url' => 'v1/demo/article/mdf_article',
 ]
```

### 3. 在接口类的方法 apiParams 中配置接口工具参数说明

```php
    public function apiParams()
    {
        $params = [
            'mdf_article' => [
                'detail' => [
                    'api_description' => _lang('修改文章标题'),
                ],
                'reqParams' => [
                    'id' => [
                        'type' => 'int',
                        'valid' => 'required',
                        'desc' => _lang('文章ID'),
                        'example' => '0',
                        'msg' => ''
                    ],
                    'title' => [
                        'type' => 'String',
                        'valid' => 'required',
                        'desc' => _lang('文章标题'),
                        'example' => '20',
                        'msg' => ''
                    ]
                ],
                'retParams' => [
                    'param_name' =>[ // 返回的参数名
                        'label' => '说明'
                    ]
                ]
            ],
        ];

        return $params;
    }
```

