# 创建表设置字段属性,并建立Model文件

#### 在Demo/Dbtables下建立数据表文件 article.php，并设置好各字段属性如：


```php
<?php

return array(
    'columns' => array(
        'id'    => array(
            'type'  => 'integer',
            'extra' => 'unsigned',
            'auto_increment' => true,
            'comment' => _lang('ID'),
            'in_list' => true,
            'default_in_list' => true,
            'input_extra' => array(
                'type' => 'hidden',
            ),
        ),
        'title' => array(
            'type'      => 'varchar(200)',
            'default'   => '',
            'comment'   => _lang('文章标题'),
            'label'     => _lang('文章标题'),
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
        'author'    => array(
            'type'      => 'varchar(50)',
            'comment'   => _lang('作者'),
            'label'     => _lang('作者'),
            'default'   => '',
            'editable'  => true,
            'width'     => 80,
            'in_list'   => true,
            'default_in_list'   => true,
            'input_extra'   => array(
                'type'      => 'text',
                'placeholder'   => _lang('请输入作者名'),
            ),
        ),
        'recomm_type' => array(
            'type' => array(
                'normal'    => _lang('不推荐'),
                'notice'    => _lang('公告通知'),
                'ad'        => _lang('广告'),
                'recomm'    => _lang('精彩资讯'),
            ),
            'default'   => 'normal',
            'comment'   => _lang('首页推荐'),
            'label'     => _lang('首页推荐'),
            'in_list'   => true,
            'width'     => 40,
            'default_in_list'   => true,
            'search_type'   => 'enum',
            'input_extra'   => array(
                'type'  => 'radio',
                'required'  => true
            ),
        ),
        'image_url'     => array(
            'type'      => 'varchar(255)',
            'comment'   => _lang('列表图'),
            'label'     => _lang('列表图'),
            'default'   => '',
            'input_extra' => array(
                'type'      => 'images',
                'required'  => true,
                'placeholder'   => _lang('请输入图片地址'),
                'filenum'   => 1,  //可上传文件数限制,默认1
                'filesize'  => 10, //单位M, 上传文件大小限制,默认10M
            ),
        ),
        'brief' => array (
            'type'      => 'text',
            'default'   => '',
            'comment'   => _lang('文章简介'),
            'label'     => _lang('文章简介'),
            'width'     => 110,
            'in_list'   => true,
            'default_in_list'   => true,
            'input_extra'   => array (
                'type'      => 'textarea',
                'required'  => true,
                'placeholder'   => _lang('文章简介'),
            ),
        ),
        'content' => array(
            'type' => 'longtext',
            'label'     => _lang('文章内容'),
            'comment'   => _lang('文章内容'),
            'default'   => '',
            'input_extra'   => array(
                'type'      => 'editor',
                'required'  => true,
                'placeholder'   => _lang('文章内容'),
            ),
        ),
        'ishot'     => array (
            'type'  => array('1' => _lang('是'), '0' => _lang('否')),
            'default'   => '0',
            'comment'   => _lang('精选'),
            'label'     => _lang('精选'),
            'in_list'   => true,
            'width'     => 40,
            'default_in_list' => true,
            'search_type' => 'enum',
        ),
        'sort' => array(
            'type'      => 'number',
            'required'  => true,
            'comment'   => _lang('排序'),
            'label'     => _lang('排序'),
            'default'   => 50,
            'input_extra' => array(
                'type'      => 'text',
                'required'  => true,
                'placeholder' => _lang('排序数字小排前'),
                'style'     => 'width:50px;'
            ),
        ),
        'push_time' => array(
            'type'  => 'time',
            'default'   => '0',
            'label'     => _lang('发布时间'),
            'comment'   => _lang('发布时间'),
            'in_list'   => true,
            'search_type' => 'datetime',
            'advanced_search' => true,
        ),
        'created_at' => array(
            'type' => 'timestamp',
            'default' => '0000-00-00 00:00:00',
            'comment' => _lang('创建时间'),
            'in_list' => true,
            'search_type' => 'datetime',
            'advanced_search' => true,
        ),
        'updated_at' => array(
            'type' => 'timestamp',
            'default' => '0000-00-00 00:00:00',
            'comment' => _lang('更新时间'),
            'in_list' => true,
            'search_type' => 'datetime',
            'advanced_search' => true,
        ),
    ),
    'primarys' => array('id'),
    'index' => array(
        'ind_recomm_type' => [
            'columns' => ['recomm_type']
        ],
    ),
    'engine'    => 'InnoDB',
    'comment'   => _lang('文章表'),
);

```


