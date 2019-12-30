# javaEE复习

## 第二章

1. 默认端口：`80`
2. HTTP特点：
   1. 简单快速
   2. 灵活
   3. 无连接
   4. 无状态

3. http请求
   1. 请求行
   2. 消息报头
   3. 请求正文

4. 请求方法
   1. GET：请求获取Request-URI所标识的资源
   2. POST：在Request-URI所标识的资源后附加新的数据
   3. HEAD：请求获取由Request-URI所标识的资源的响应消息报头
   4. PUT：请求服务器存储一个资源，并用Request-URI作为其标识
   5. DELETE：请求服务器删除Request-URI所标识的资源
   6. TRACE：请求服务器回送收到的请求信息，主要用于测试或诊断
   7. CONNECT：保留将来使用
   8. OPTIONS：请求查询服务器的性能，或者查询与资源相关的选项和需求

5. 状态代码
   1. 1xx:提示已接收
   2. 2xx:成功
   3. 3xx:重定向
   4. 4xx：客户端错误
   5. 5xx:服务端错误

6. XMLhttpRequest的常用方法和属性 66页
   1. open
   2. send
   3. onreadystatechange
   4. readyState
   5. status

7. Servlet容器
   1. 如果装在并创建了servlet实例化对象则用`service`方法将创建的请求和相应对象作为参数传递进去
   2. 若没有则用`init`创建
   3. 卸载用`destroy`

8. Servlet生命周期
   1. 加载和实例化，第一次访问创建或启动创建\<load-on-startup>
   2. 初始化：用init，目的是如建立数据库连接，获取配置信息，异常ServletException
   3. 请求处理:用service处理，ServletRequest，ServletResponse
   4. 服务终止：`destroy`
   5. init,destroy都只执行一次

9. Servlet接口(p75)
   1. init()
   2. getServletConfig()
   3. Service()
   4. destroy()
