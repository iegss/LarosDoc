# 2.2 Controllres 详解

## BaseAdminController 常用方法

index 数据列表 add 添加一条数据 del 删除数据 edit 编辑修改数据

## add、edit 重写

1、提交后数据重写

```text
if($request->isMethod('post')){
            $request->offsetSet('source', 'LarOS - '.$request->input('source'));
        }
```

2、修改字段配置

```text
$this->modifyColmns = [
    'source' => [
        'input_extra'   => array(
            'type'      => 'text',
            'placeholder'   => _lang('请输入作者名'),
        ),
    ]
];
```

