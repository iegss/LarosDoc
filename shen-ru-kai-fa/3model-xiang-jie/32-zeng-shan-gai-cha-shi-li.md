# 3.2 增删改查实例

## 添加

### 添加插入一行

```php
$values = [
    'cat_id' => '1',
    'title' => '标题',
    'content' => '测试内容'
];
model('demo_article')->add($values); // 返回model对象,会写入 created_at,updated_at 值
model('demo_article')->create($values); // 返回model对象, 会写入 created_at,updated_at 值
model('demo_article')->addOrModify($values); // 返回model对象, $values中无主键写入, 会写入 created_at,updated_at 值

model('demo_article')->insert($values); // 返回 bool, 注意:一维数组一行,多维数据多行, 不会写入 created_at,updated_at 值
```

### 添加插入多行

```php
$values = [
    [
        'cat_id' => 1,
        'title' => '标题1',
        'content' => '测试内容1'
    ],
    [
        'cat_id' => 1,
        'title' => '标题2',
        'content' => '测试内容2'
    ],
    [
        'cat_id' => 1,
        'title' => '标题3',
        'content' => '测试内容3'
    ]
];
model('demo_article')->insert($values); // 返回 bool, 不会写入 created_at,updated_at 值
```

## 删除

```php
model('demo_article')->del(1); // 删除主键值为1的数据, 返回删除的行数
model('demo_article')->del([5,6,7]); // 删除主键值为5,6,7的数据, 返回删除的行数

model('demo_article')->delByPrimary(11); // 通过主键删除, 删除主键值为11的数据, 返回删除的行数
model('demo_article')->delByPrimary([11,12,13,14]); // 通过主键删除, 删除主键值为11,12,13,14的数据, 返回删除的行数

$filter = [
    ['id','<',10]
];
echo model('demo_article')->del(0, $filter); // 按条件删除, 返回删除的行数
$filter = [
    ['id','>',10],
    ['id','<',20]
];
echo model('demo_article')->delByFilter($filter); // 按条件删除, 返回删除的行数
```

## 修改

### 修改一行数据

```php
$values = [
    'id' => '10',
    'cat_id' => '1',
    'title' => '标题12',
    'content' => '测试内容10'
];
model('demo_article')->addOrModify($values); //$values 主键大于0, 且数据存在。

$values = [
    'cat_id' => '1',
    'title' => '标题10',
    'content' => '测试内容10'
];
$where = [
    'title' => '标题',
];
//按$where条件修改一条数,条件未找到则添加。注: 该方法只能修改或添加一条数据
model('demo_article')->addOrModify($values, $where);
```

### 修改多行数据

```php
$values = [
    'cat_id' => '1',
    'title' => '标题11',
    'content' => '测试内容11'
];
$filter = [
    ['title', '标题10'],
];
// 按条件修改多行数据,返回影响的行数。不会更新updated_at值
model('demo_article')->modifies($values, $filter);
```

## 查询

### 查询一行数据

```php
$cols = ['*']; // 字段
$filter = [
    ['cat_id','1'],
];
$orderBy = 'id desc';
$row = model('demo_article')->getRow($cols,$filter,$orderBy,true);
if(!$row)
    echo '无数据';
print_r($row);
echo '-------------';
```

### 查询多行数据

```php
$list = model('demo_article')->getList($cols,$filter,0,-1,$orderBy,true);
if(!$list->toArray())
    echo '无数据';

foreach ($list as $key => $value){
    print_r($value);
}
```

