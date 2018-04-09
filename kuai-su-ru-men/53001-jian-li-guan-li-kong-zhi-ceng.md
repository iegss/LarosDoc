# 建立管理控制层

#### 在Demo/Dbtables下建立数据表文件 article.php


```

<?php

namespace Modules\Demo\Controllers\Admin;

use Modules\Base\Controllers\Admin\BaseAdminController;

class ArticleController extends BaseAdminController
{
    var $admin_table_name = 'demo_article';
    var $admin_url_prefix = 'demo/admin/article';

}
```

