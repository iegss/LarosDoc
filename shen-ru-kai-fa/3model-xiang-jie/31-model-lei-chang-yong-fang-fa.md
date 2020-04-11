# 3.1 Model 类常用方法

1. getList 得到数据列表
2. getAll 得到所有数据
3. getRow 得到一行数据
4. getDetail 得到数据表定义及值 
5. addOrModify 添加或修改一行数据 
6. add 添加一条数据 
7. insert 添加一条或多条数据
8. modifies 修改一条或多条数据 
9. del 删除数据 
10. getCount 统计多少行 
11. getSum 求和

## getList 得到数据列表

```php
     /**
     * @param string $cols  字段
     * @param string|array $filter 条件
     * @param int $offset 从第条开始
     * @param int $limit 多少条
     * @param string $orderBy 排序
     * @param bool $format_data 是否格式输出
     * @return \Illuminate\Support\Collection
     */
    public function getList($cols = '*', $filter = '', $offset = 0, $limit = 1000, $orderBy = '', $format_data = false)
```

## getAll 得到所有数据

```php
     /**
     * @param bool $format_data
     * @param string $cols 字段
     * @param string $filter 条件
     * @param string $orderBy 排序
     * @param bool $format_data 是否格式输出
     * @return \Illuminate\Support\Collection
     */
    public function getAll($cols = '*',$filter = '',$orderBy = '', $format_data = false)
```

## getRow 得到一行数据

```php
     /**
     * @param string $cols 字段
     * @param string|array $filter 条件
     * @param string $orderBy 排序
     * @param bool $format_data 是否格式输出
     * @return array|null|\stdClass
     */
    public function getRow($cols = '*', $filter = '', $orderBy = '', $format_data = false)
```

### getRow、getList、getAll 参数说明

```php
$cols = ['字段1','字段2']; // 字段
$filter = [
     ['字段','值'],
     ['字段','条件','值'], 
     'sql',
];
$orderBy = '字段1 desc, 字段2 asc';
```

## getDetail 得到数据表定义及值

```php
     /**
     * @param int $id 表的主键值
     * @return bool|mixed
     */
    public function getDetail($id = 0)
```

## addOrModify 添加或修改一行数据

```php
     /**
     * 添加或修改一行数据
     * 创建: $filter = NULL && $values['主键'] <= 0
     * 修改: $filter != NULL || $values['主键'] > 0
     *
     * @param  array  $values 要修改的数据 ['字段1'=> '值1','字段2'=> '值2']
     * @param  array  $where 条件  ['字段1'=> '值1','字段2'=> '值2']
     * @return \Iegss\Larbase\Model\BaseModel
     */
    public function addOrModify(array $values = [], array $where = [] )
```

注：  
addOrModify 值为一维数组，条件一维或二维数组， 建议使用一维。  
addOrModify 只能添加或修改一行数据，

## add 添加一条数据

```php
     /**
     * 添加一条数据
     *
     * @param array $values 一维数组,添加一条记录
     * @return \Iegss\Larbase\Model\BaseModel
     */
     public function add(array $values)
```

## insert 添加一条或多条数据

## modifies 修改一条或多条数据

```php
     /**
     * 修改一条或多条数据
     *
     * @param array $values 一维数组
     * @param array $filter 多维数据
     * @return bool|int  影响行数
     */
    public function modifies(array $values, array $filter)
```

## del 删除数据

```php
     /**
     *
     * 通过主键删除：ids int|array   1|[5,6,7]
     * 通过条件删除：ids=0， $filter = array()
     *
     * @param int $ids  主键ID
     * @param array $filter 条件
     * @return bool|int 返回删除的行数
     */
     public function del($ids = 0, $filter = [])
```

注：$filter 优先

## getCount 统计多少行

```php
     /**
     * @param string $filter 条件
     * @param string $cols 字段
     * @return int
     */
    public function getCount($filter = '', $cols = '*')
```

## getSum 求和

```php
     /**
     * @param string $filter 条件
     * @param string $cols 字段
     * @return mixed
     */
    public function getSum($filter = '', $cols = '*')
```

