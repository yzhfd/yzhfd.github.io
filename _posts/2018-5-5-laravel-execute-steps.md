# 框架执行流程
## Laravel 框架执行的顺序
### 一个web页面请求正常的流程
1. public/index.php 这个是整个应用的入口，这个文件主要干以下几件事情
	* 注册 Composer 的文件自动加载机制
	* 加载bootstrap文件下面的app.php，app.php 会返回整个 application 对象
	* 在服务容器里面创建Http内核，Http 内核处理客户端的请求
	* 响应客户端
2. 进入bootstrap里面的app.php，我们看一下如何创建应用实例
	*  应用是Illuminate\Foundation\Application 类的实例，创建一个应用实例
	*  在应用实例上，利用单例的方式绑定三个重要的接口到服务容器里面，分别是：App\Http\Kernel 处理web请求的HTTP内核，App\Console\Kernel 处理CLI请求的内核以及App\Exceptions\Handler 处理异常机制
3. 进入Illuminate\Foundation\Application 看一下应用实例化的过程（单例）
	* Appication 类继承自容器类，扩展了ApplicationContract契约和HttpKernelInterface接口
	* Application 类有如下字段：
		-  VERSION ： 版本号
		-  $basePath ： Laravel框架安装的路径
		-  $hasBeenBootstrapped ： 该类是否被引导完成
		-  $booted ： 该类是否已经引导过了
		-  $bootingCallbacks ： 正在引导的回调
		-  $bootedCallbacks ： 引导完成后的回调
		-  $terminatingCallbacks ：终止后的回调
		-  $serviceProviders： 服务提供者
		-  $loadedProviders ：已经被加载过的服务提供者
		-  $deferredServices ：延迟加载的服务提供者
		-  $databasePath ：数据库路径
		-  $storagePath ：存储路径
		-  $environmentPath ： 当前环境路径
		-  $environmentFile ：环境配置文件，默认 .env
		-  $namespace : 应用的命名空间
4. 应用实例初始化-注册框架基础类绑定到容器里面
		* 当前应用实例 $this 绑定到容器里面 app 这个标签名上
		* 注册绑定 PackageManifest 类到容器里
5. 注册框架基本的服务提供者
	* 注册EventServiceProvider事件服务提供者到容器
	* 注册LogServiceProvider日志服务提供者到容器
	* 注册RoutingServiceProvider路由服务提供者容器
6. 注册核心类的别名到容器中
核心类有：app、auth、auth.driver、blade.compiler、cache、cache.store、config、cookie、encrypter、db、db.connection、events、files、filesystem、filesystem.disk、filesystem.cloud、hash、hash.driver、translator、log、mailer、auth.password、auth.password.broker、queue、queue.connection、queue.failer、redirect、redis、request、router、session、session.store、url、validator、view
7. 接下来回到了 public/index.php 中创建HTTP 内核的实例，该类之前已经在容器中注册过了，所以用$app->make(Illuminate\Contracts\Http\Kernel::class)即可创建。
8. 捕获HTTP的Request请求，封装到Request类中，开启HTTP 方法可以被重写，然后重写PHP原生的HTTP请求中的query、request、cookies、files、server全局数组
9. 
