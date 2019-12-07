### 一级拆分

>- manage.py
>
>- XXXProejct----项目共享文件
>
>  >- \__init__
>  >
>  >  > - app创建 def create_app(env):---全局统筹管理
>  >  >
>  >  >   创建flask对象，加载各模块
>  >  >
>  >  >   >- 加载配置 app.config.from_object(envs.get(env))
>  >  >   >- 初始化扩展库 init_extensions(app)
>  >  >   >- 加载中间件 init_middleware(app)/钩子函数
>  >  >   >- 加载路由，暴漏入口 init_routes(app)
>  >
>  >  
>  >
>  >- config
>  >
>  >  > 项目配置---通常存在四套环境
>  >  >
>  >  > >开发环境
>  >  > >
>  >  > >测试环境
>  >  > >
>  >  > >演示环境
>  >  > >
>  >  > >生产环境---线上环境
>  >  >
>  >  > >动态自动加载--环境变量实现-
>  >  > >
>  >  > >Env = os.environ.get('FLASK_PROJECT','default')
>  >  > >
>  >  > >Create_app(env)
>  >  > >
>  >  > >envs.get(env) 
>  >
>  >  
>  >
>  >- extension
>  >
>  >  > 第三方扩展库,除了路由
>  >
>  >  
>  >
>  >- middleware
>  >
>  >  > 中间件/钩子函数
>  >  >
>  >  > 中间件
>  >  >
>  >  > 面向切面编程
>  >  >
>  >  > >在不修改代码的情况下实现已有逻辑的控制，扩展
>  >  >
>  >  > 内置钩子
>  >  >
>  >  > >Before_request
>  >  > >
>  >  > >After_request
>  >  > >
>  >  > >error_hander---错误处理
>  >
>  >  
>  >
>  >- route
>  >
>  >  > 管理入口
>  >  >
>  >  > 管理路由
>  >  >
>  >  > 暴露路由
>  >
>  >  
>  >
>  >- settings
>  >
>  >  > 和配置功能一样
>  >
>  >  
>  >
>  >- views---数据管理
>  >
>  >- models---数据定义
>  >
>  >- templates---html

### 二级拆分

>- manage.py
>
>- XXXProejct----项目共享文件
>
>  >- \__init__
>  >
>  >  > - app创建 def create_app(env):---全局统筹管理
>  >  >
>  >  >   创建flask对象，加载各模块
>  >  >
>  >  >   >- 加载配置 app.config.from_object(envs.get(env))
>  >  >   >- 初始化扩展库 init_extensions(app)
>  >  >   >- 加载中间件 init_middleware(app)/钩子函数
>  >  >   >- 加载路由，暴漏入口 init_routes(app)
>  >
>  >  
>  >
>  >- config
>  >
>  >  > app.config.from_object(envs.get(env))
>  >  >
>  >  > 项目配置---通常存在四套环境
>  >  >
>  >  > >开发环境
>  >  > >
>  >  > >测试环境
>  >  > >
>  >  > >演示环境
>  >  > >
>  >  > >生产环境---线上环境
>  >  >
>  >  > >动态自动加载--环境变量实现-
>  >  > >
>  >  > >Env = os.environ.get('FLASK_PROJECT','default')
>  >  > >
>  >  > >Create_app(env)
>  >  > >
>  >  > >envs.get(env) 
>  >
>  >  
>  >
>  >- extension
>  >
>  >  > 第三方扩展库,除了路由
>  >  >
>  >  > init_ext
>  >
>  >  
>  >
>  >- middleware
>  >
>  >  > Load_middleware
>  >  >
>  >  > 中间件/钩子函数
>  >  >
>  >  > 中间件
>  >  >
>  >  > 面向切面编程
>  >  >
>  >  > >在不修改代码的情况下实现已有逻辑的控制，扩展
>  >  >
>  >  > 内置钩子
>  >  >
>  >  > >Before_request
>  >  > >
>  >  > >After_request
>  >  > >
>  >  > >error_hander---错误处理
>  >
>  >  
>  >
>  >- route
>  >
>  >  > Init_route
>  >  >
>  >  > 管理入口
>  >  >
>  >  > 管理路由
>  >  >
>  >  > 暴露路由
>  >
>  >  
>  >
>  >- settings
>  >
>  >  > 和配置功能一样
>
>  
>
>- App1
>
> > * \__init__
> > * models ---写模型
> > * views ---写逻辑
> > * route/api接口 ----写路由
>
>- App2
>
>> * \__init__
>> * models-----模型
>> * views---每一个单独的项目都需要一个blueprint
>> * route/api接口
>
>* AppN
>
> > * \__init__
> > * models
> > * views
> > * route/api接口
>
>* Templates----html
>
>
>- Resource-----脚本文件处理（资源）----脚本（一个特定功能的文件）
>
>* 各种需要使用的脚本文件----一般是json文件（字典类型，从中提取我们需要的数据）
>
>- Migrates---迁移文件，在创建迁移的时候会自动生成
>- Static-----js/css等静态项目文件
>- Common-----app公用的一些工具包