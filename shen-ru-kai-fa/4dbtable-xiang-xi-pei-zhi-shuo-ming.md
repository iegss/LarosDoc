# 4、DBTable 详细配置说明

返回是一个多维数组

## columns 字段

下标名=字段名

```php
'title' => array(
    'type'      => 'varchar(200)',
    'default'   => '',
    'comment'   => _lang('文章标题'),
    'label'     => _lang('文章名'),
    'width'     => 300,
    'in_list'   => true,
    'default_in_list'   => true,
    'search_type'       => 'string',
    'simple_search'     => true,
    'advanced_search'   => true,
    'input_extra'   => array(
        'type'      => 'text',
        'required'  => true,
        'placeholder'   => _lang('请输入标题'),
    ),
),
```

## primarys 主键

## index 索引

## engine

## comment

