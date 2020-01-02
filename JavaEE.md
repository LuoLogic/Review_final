# javaEE复习

## 第二至五章

1. http默认端口：`80`
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

10. web.xml配置
    1. \<servlet>
       1. \<servlet-name>:指定名称
       2. \<servlet-class>：指定路劲

    2. \<servlet-mapping>:映射一个已注册的Servlet的对外访问路径
       1. \<servlet-name>：指定访问路径的Servlet名称
       2. \<url-pattern>:用于指定Servlet访问路径

    3. 注解`@WebServlet("\\RegisterServlet")`

11. 判断转发重定向
    1. \<a href="index.jsp">,客户端，重定向
    2. errorPage,服务端，转发
    3. getDispather.forward,服务端 转发
    4. setHeader 客户端
    5. sendRedirect("url") 客户端 重定向
    6. \<jsp:forward> 服务端 转发

12. Tomcat
    1. bin:启动Tomcat命令
    2. conf:配置文件
    3. work：jsp转为servlet
    4. server.xml：配置文件定义端口，web应用目录

13. Tomcat默认端口`8080`

14. 编写第一个Servlet

    ```HTML
    <form id="login" method="post" action="/ServletDemo/Servlet/LoginServlet">
        用户名：<input type="text" name="username" width="50"/><br>
        密码:<input type="password" name="pass" width="50"/><br>
        <input type="submit" value="登录"/><br>
    </form>
    ```

    ```java
    protected void doPost(HttpServletRequest request,HttpServletResponse response)throws ServletException,IOException{
        request.setCharacterEncoding("utf-8");
        String username=request.getParameter("username");
        String password=request.getParameter("pass");
        response.setContentType("text/html;charset=utf-8");
        PrintWriter out=response.getWriter();
        out.println("<html><head><title>登录结果<title><head>");
        out.println("<body>您输入的用户名是："+username+"<br>");
        out.close();
    }
    ```

    ```xml
    <servlet>
        <servlet-name>loginServlet</servlet-name>
        <servlet-class>edu.hdu.web.LoginServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>loginServlet</servlet-name>
        <url-pattern>/Servlet/LoginServlet</url-pattern>
    </servlet-mapping>
    ```

15. web.xml配置HTML字符编码

    ```xml
    <servlet>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>GBK</param-value>
        </init-param>
    </servlet>
    ```

    ```java
    ServletConfig config=this.getServletConfig();
    String encoding=config.getInitParameter("encoding");
    response.setContentType("text/html;charSet="+encoding);
    ```

16. 过滤器
    1. filter是针对url的
    2. 注解：`@WebFilter(filterName="encodingFilter",urlPatterns="/*")`
    3. 放行请求：`chain.doFilter(,request,response);`

17. 过滤器生命周期
    1. 初始化：`init()`
    2. 过滤：`doFilter()`
    3. 销毁：`destory()`

18. doFilter()示例

    ```java
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        String encoding =config.getInitParameter("encoding");

        request.setCharacterEncoding(encoding);
        HttpServletRequest requ=(HttpServletRequest)request;
        HttpSession session=requ.getSession(true);

        //获取客户请求页面
        String requestPath=requ.getServletPath();
        //如果Session范围的user为null，即表明没有登录
        //且用户请求的不是登录页面
        //且用户请的既不是登录页面，也不是处理登录的Servlet页面
        if(session.getAttribute("user")==null&&!reqestPath.endsWith("login.jsp"
        )&&!requestPath.endsWith("LoginServlet")){
            ((HttpServletResponse)response).sendRedirect("login.jsp");
            return;
        }else(
            //放行请求
            chain.doFilter(,request,response);
        )
    }
    ```

19. 配置Filter

    ```xml
    <filter>
        <filter-name>log</filter-name>
        <!-- filter的实现类 -->
        <filter-class>edu.hdu.web.LogFilter</filter-class>
        <init-param>
            <param-name>encoding<param-name>
            <param-value>GBK<param-value>
        <init-param>
    </filter>
    <!-- 定义filter的拦截地址 -->
    <filter-mapping>
        <filter-name>log<filter-name>
        <!-- filter负责拦截的URL -->
        <url-pattern>/*<url-pattern>
    <filter-mapping>

    ```

## 第六章JSP&&JSTL&&EL

1. JSP工作原理：本质Servlet，当jsp第一次被请求时，web服务器上的jsp容器将其转为相应的servlet文件，再便以为相应的servlet类文件，并且被装载和实例化，本次以及以后对此jsp的请求都将通过调用已经实例化的Servlet对象中的方法来产生响应
2. jsp执行过程：翻译，编译，执行

3. jsp生命周期![jsp1](img/jsp1.png)

4. jsp注释
   1. `<%//单行注释%>`注释单行
   2. `<%/*多行注释 */%>`注释多行
   3. `<!--comment<%=expression%>-->`,客户端注释
   4. `<%--注释--%>`隐式注释，服务器端

5. `page`指令`<%@page %>`
   1. import="java.io.*"
   2. errorPage="url"
   3. isErrorPage="true|false"
   4. language="java"
   5. session="true|false"

6. include指令

7. `taglib`指令：用于提供类似xml中自定义新标记的功能，其基本语法如下:
   * <%@ taglib url="relative taglibURL" prefix="taglibPrefix" %>
