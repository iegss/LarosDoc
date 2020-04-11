# 5、建立管理控制层

**注：**你也可以通过[框架命令行助手](../shen-ceng-fa-jue/43001-kuang-jia-ming-ling-xing-zhu-shou.md)自动建立。

## 在 Demo/Controllers/Admin 下建立管理控制层文件 ArticleController.php

```php
<?php

namespace Modules\Demo\Controllers\Admin;

use Modules\Base\Controllers\Admin\BaseAdminController;

class ArticleController extends BaseAdminController
{
    var $admin_table_name = 'demo_article';
    var $admin_url_prefix = 'demo/admin/article';

}
```

