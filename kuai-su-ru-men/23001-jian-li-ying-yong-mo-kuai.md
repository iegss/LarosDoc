# 目录结构



```

├─bootstrap
│  └─app.php    					启动文件
│
├─config                            配置目录
│  ├─captcha.php 					图形验证码配置文件
│  └─session.php 					Session 配置文件
│
├─core 								larOS框架核心目录
│  └─iegss                        
│     └─larbase                   
│        └─src                  		
│         	├─Captcha              		图形验证码目录
│           ├─Console              		命令行处理目录
│           ├─Datatables            	数据列表管理区目录
│           ├─Db              			数据库表目录
│           ├─Exception             	异常处理目录
│           ├─Helpers              		助手（全局方法）目录
│           ├─Http              		Http 跳转处理目录
│           ├─Lib              			工具库
│           ├─Model              		数据模型目录
│           ├─Rbac              		权限控制目录
│           ├─Routing              		路由控制目录
│           ├─Application.php       	主应用程序文件
│           └─BootServiceProvider.php  	框架服务处理文件
│                          
├─modules						模块目录
│  ├─Api						API接口工具模块目录
│  ├─Base						框架基础模块目录
│  ├─Content					文章内容模块目录
│  ├─Laradmin					后台管理模块目录
│  │ ├─Config             		模块配置目录
│  │ ├─Controllers              控制层目录
│  │ ├─Middleware               中间层目录
│  │ ├─Model                 	数据模型目录
│  │ ├─Views                 	视图目录
│  │ ├─BootServiceProvider.php  模块服务处理文件
│  │ └─routes.php  				模块路由文件
│  │ 
│ 
├─public                        外部资源目录
│  ├─statics                    CSS,JS,Images资源目录
│  ├─uploads                   	文件上传目录
│  ├─.htaccess 					Apache环境重写文件
│  └─index.php 					系统统一入口文件
│
├─storage                       存储目录
│  ├─app                    	模块应用存储目录
│  ├─framework                  底层框架运行缓存目录
│  └─logs						日志目录
│
└─vendor                            第三方类库目录（Composer）
```


