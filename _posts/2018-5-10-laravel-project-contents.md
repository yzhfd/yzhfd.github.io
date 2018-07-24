# Laravel5.6 项目文件目录结构
## Laravel 典型项目目录结构
### 根目录 
- APP：应用代码的核心目录
    * Console 控制台相关逻辑代码
    * Events 应用的自定义事件
    * Exceptions 应用异常处理
    * Http 网络请求核心处理逻辑
        * Controllers 所有的应用控制器
        * Middleware 中间件
    * Listeners 事件侦听器
    * Providers 应用的服务器提供者
    * Models 放数据模型         
- bootstrap 用于框架启动和自动载入配置
    * cache 路由和服务提供者等缓存
    * app.php 创建框架实例，自动加载
- config 配置目录
    * app.php 实例名称、运行环境、网站地址、时区设置、
        本地化语言、需要加载的服务提供者、门面类定义别名
    * auth.php 权限验证相关的配置项
    * broadcasting 广播服务相关配置
    * cache 缓存相关配置
    * database 数据库驱动和连接配置
    * filesystems.php 文件系统相关配置
    * hashing.php 哈希加密配置
    * logging.php 日志相关配置
    * mail.php 邮件相关配置
    * queue.php 队列相关配置
    * services.php 第三方服务配置信息
    * session.php 会话相关配置
    * view.php 视图相关配置
- database 数据库迁移相关
    * factories 模型工厂类
    * migrations 数据库迁移文件
    * seeds 加入数据都爱数据库表中
- public 应用入口，一般是域名指向的根目录
    * css 前端css文件
    * js 前端js文件
    * storage 前端文件存放
    * index.php __应用的入口__
- resources 模板文件和语言包文件
    * assets 编译前的sass 和 js 文件
    * lang 语言包文件
    * views 应用的模板文件
- routes 路由配置文件
    * api.php API路由配置
    * channels.php 广播channel
    * console.php 控制台路径
    * web.php 网页路由
- storage 文件存储
    * app/public public/storage指向的实际路径
    * framework 框架编译后的文件、会话、测试以及模板编译后的文件
    * logs 框架日志
- tests 测试
    * Feature 功能测试
    * Unit 单元测试
- vendor Laravel框架核心库以及其他的核心库还有第三方的组件
- .env文件
    * APP相关配置
    * 数据库连接账号信息
    * Redis连接账号信息
    * 邮件系统账号信息
- artisan文件 控制台命令入口文件
- composer.json文件 composer加载库配置



