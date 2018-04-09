# 建立管理控制层

#### 在Demo/Controllers/Admin下建立文件 ArticleController.php

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

