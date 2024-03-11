# Java Web

![image-20220924232505043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924232505043.png)

JavaWeb 是指，**所有通过 Java 语言编写可以通过浏览器访问的程序的总称**，叫 JavaWeb。 JavaWeb 是**基于请求和响应来开发的**

**请求**是指客户端给服务器发送数据，叫请求 Request

**响应**是指服务器给客户端回传数据，叫响应 Response

**请求和响应是成对出现的，有请求就有响应**

Web 应用程序：可以提供浏览器访问的程序；（提供DOS命令访问的程序，CS架构。😖）

- a.html、b.html…多个web资源，这些资源可以被外界访问，对外界提供服务。

**在互联网上能够访问到的任何一个页面或者资源，都存在于世界的某一个角落的计算机上**

资源是真实存在的，**URL(统一资源定位符)，网络世界的通讯地址**。
URL，这些统一的web资源会被放在同一个文件夹下，
通过 web 应用程序，（Tomcat服务器）来提供。
一个web应用程序由多部分组成：（静态web，动态web）
html，css，js(前端三剑客)
jsp，servlet
java程序
jar包
配置文件（Properties）

web应用程序编写完毕之后，若想提供给外界访问：需要一个服务器来统一管理

![image-20220924195242564](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924195242564.png)



Web资源按照实现的技术和呈现的样式不同 分为**静态资源**和**动态资源**两种

![image-20220924195552959](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924195552959.png)

![image-20220924195608650](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924195608650.png)

## Web服务器_Tomcat

![.](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924200940734.png)

**启动**

cmd ：catalina run

**停止**

cmd : control + c

![image-20220924201025409](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201025409.png)
**修改端口号 ：默认8080 当端口被占用 可以进行修改 1000-65535** 

![image-20220924201133322](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201133322.png)

![image-20220924201143746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201143746.png)

![image-20220924201201904](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201201904.png)

## 将Web工程部署到Tomcat服务器上

![image-20220924201727741](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201727741.png)

方式一：**webapps下的一个目录代表一个工程 将工程直接放入目录中即可**	Tomcat默认启动webapps下的一个目录（ROOT）

![image-20220924201739424](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924201739424.png)

**推荐：方式二：**

![image-20220924222727726](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924222727726.png)

![image-20220924222751091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924222751091.png)

```xml
<!-- Context 表示一个工程上下文
path 表示工程的访问路径:/abc
docBase 表示你的工程目录在哪里
-->
<Context path="/abc" docBase="E:\Book" />
```

![image-20220924222924122](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924222924122.png)

**默认ROOT 的工程的访问，以及 默认 index.html 页面的访问**

当我们在浏览器地址栏中输入访问地址如下： http://ip:port/ ====>>>> 没有工程名的时候，默认访问的是 ROOT 工程。 

当我们在浏览器地址栏中输入的访问地址如下： http://ip:port/工程名/ ====>>>> 没有资源名，默认访问 index.html 页

## IDEA - Tomcat 服务器

![image-20220924223149982](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924223149982.png)

**新建动态web**

**先new一个普通的Mudule**

![image-20220924225226015](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225226015.png)

![image-20220924225307858](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225307858.png)

![image-20220924225322234](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225322234.png)

![image-20220924225339748](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225339748.png)

![image-20220924225400313](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225400313.png)

![image-20220924225428480](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924225428480.png)

![image-20220924230613517](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924230613517.png)

**导jar包**

![image-20220924230603920](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924230603920.png)

![image-20220924230644407](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924230644407.png)

![image-20220924230705316](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924230705316.png)

**建议web工程名为对应的Tomcat运行实例的名**

**把Name 更改为模块名 ---->点击Deployment ----> 点击+号 ---->选择模块名相同的----->application context 可以修改工程路径 --->点击OK**

![image-20220924230918400](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924230918400.png)

![image-20220924231034957](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924231034957.png)

![image-20220924231505997](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924231505997.png)

![image-20220924234724247](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924234724247.png)

## Tomcat和Servlet的关系

**Tomcat 是Web应用服务器,是一个Servlet/JSP容器**

![image-20220925114831366](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114831366.png)

![image-20220925114951389](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114951389.png)

## Servlet

**Servlet 是 JavaEE 规范之一。规范就是接口** 

**Servlet 就 JavaWeb 三大组件之一。三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监听器。** 

**Servlet 是运行在服务器上的一个 java 小程序，它可以接收客户端发送过来的请求，并响应数据给客户端**

 Servlet（Server Applet），全称Java Servlet，未有中文译文。是用Java编写的**服务器端程序**。其**主要功能在于交互式地浏览和修改数据**，**生成动态Web内容**。狭义的**Servlet是指Java语言实现的一个接口**，广义的Servlet是指任何实现了这个Servlet接口的类，一般情况下，人们将Servlet理解为后者。

Servlet运行于支持Java的应用服务器中。从实现上讲，Servlet可以响应任何类型的请求，但绝大多数情况下**Servlet只用来扩展基于HTTP协议的Web服务器**。

**处理请求和发送响应的过程是由一种叫做Servlet的程序来完成**

![image-20220925114713441](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114713441.png)

### Servlet工作流程

![image-20221027151801712](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027151801712.png)

### Servlet的工作模式

- 客户端发送请求至服务器
- **服务器启动并调用Servlet**，**Servlet根据客户端请求生成响应内容并将其传给服务器**
- **服务器将响应返回客户端**

### Servlet 的使用方法

Servlet技术的核心是Servlet，***\*它是所有Servlet类必须直接或者间接实现的一个接口\****。在编写实现Servlet的Servlet类时，直接实现它。在扩展实现这个这个接口的类时，间接实现它。

### Servlet 的工作原理

 **Servlet接口定义了Servlet与servlet容器之间的契约**。这个契约是：Servlet容器将Servlet类载入内存，并产生Servlet实例和调用它具体的方法。但是要注意的是，在一个应用程序中，每种Servlet类型只能有一个实例。

用户请求致使Servlet容器调用Servlet的Service（）方法，并传入一个ServletRequest对象和一个ServletResponse对象。ServletRequest对象和ServletResponse对象都是由Servlet容器（例如TomCat）封装好的，并不需要程序员去实现，程序员可以直接使用这两个对象。

ServletRequest中封装了当前的Http请求，因此，开发人员不必解析和操作原始的Http数据。ServletResponse表示当前用户的Http响应，程序员只需直接操作ServletResponse对象就能把响应轻松的发回给用户。

对于每一个应用程序，Servlet容器还会创建一个ServletContext对象。这个对象中封装了上下文（应用程序）的环境详情。每个应用程序只有一个ServletContext。每个Servlet对象也都有一个封装Servlet配置的ServletConfig对象。

### 手动实现 Servlet 程序

1、编写一个类去实现 Servlet 接口

 2、实现 service 方法，处理请求，并响应数据

 3、到  web.xml 中去配置 servlet 程序的访问地址

![image-20220924235103090](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924235103090.png)

![image-20220925000021043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925000021043.png)

![image-20220925000002395](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925000002395.png)



![image-20220925001256226](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925001256226.png)

默认访问

![image-20220925001520712](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925001520712.png)

![image-20220925102940545](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925102940545.png)



![image-20220925103634089](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925103634089.png)

### Servlet生命周期

![image-20220925114506664](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114506664.png)

1、执行 Servlet 构造器方法 创建Servlet实例

2、执行 init 初始化方法 **Web容器调用Servlet的init()方法，对Servlet进行初始化。**

**第一、二步，是在第一次访问，的时候创建 Servlet 程序会调用。** 

3、执行 service 方法 第三步，每次访问都会调用。 

4、执行 destroy 销毁方法 第四步，在 web 

![image-20220925104415322](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925104415322.png)
**GET 和 POST 请求的分发处理** getMethod()方法在HttpServletRequest接口中

![image-20220925111341046](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925111341046.png)

### 通过继承 HttpServlet 实现 Servlet 程序(开发常用)

一般在实际项目开发中，都是使用继承 HttpServlet 类的方式去实现 Servlet 程序。 

1、编写一个类去继承 HttpServlet 类 

2、根据业务需要重写 doGet 或 doPost 方法 

3、到 web.xml 中的配置 Servlet 程序的访问地址

![image-20220925112916298](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925112916298.png)

![image-20220925112929814](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925112929814.png)

![image-20220925112937821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925112937821.png)

![image-20220925112945865](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925112945865.png)

#### 使用 IDEA 创建 Servlet 程序

![image-20220925113711512](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925113711512.png)

![image-20220925113731368](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925113731368.png)

![image-20220925114013038](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114013038.png)

![image-20220925113817214](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925113817214.png)

![image-20220925114211922](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925114211922.png)

### Servlet的继承体系

![image-20220925115552021](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925115552021.png)

![image-20220925160129166](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925160129166.png)

**我们 extends 于HttpServlet 并根据业务需要重写doGet()&doPost()方法即可；**

## ServletConfig

**封装了Servlet程序初始化配置信息**

Servlet程序和ServletConfig对象都是由Tomcat服务器负责创建。

Servlet程序默认第一次访问的时候创建，每个Servlet程序创建时，就创建一个ServletConfig对象。作为形参传入Servlet的init（）方法。

**在Servlet初始化的时候，会自动调用init(ServletConfig config)，Container会自动收集一些该Servlet的配置信息，生成一个ServletConfig的实例，通过调用该实例的四个getXXX方法（即ServletConfig接口中的四个方法），我们可以得到该Servlet的这些配置信息**

![image-20220925163944354](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925163944354.png)

![image-20220925160859508](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925160859508.png)

**ServletConfig**

ServletConfig代表的是当前servlet在web.xml中的配置信息


```java
String getServletName()  -- 获取当前Servlet在web.xml中配置的名字

String getInitParameter(String name) -- 获取当前Servlet指定名称的初始化参数的值

Enumeration getInitParameterNames()  -- 获取当前Servlet所有初始化参数的名字组成的枚举

ServletContext getServletContext()  -- 获取代表当前web应用的ServletContext对象
```

在**Servlet的配置文件中**，可以**使用一个或多个<init-param>标签**为servlet**配置一些初始化参数**。

当servlet配置了初始化参数后，web容器在创建servlet实例对象时，会自动将这些初始化参数封装到ServletConfig对象中，并在调用 servlet的init方法时，将ServletConfig对象传递给servlet。进而，程序员通过ServletConfig对象就可以得到当前servlet的初始化参数信息。

这样做的好处是：如果将数据库信息、编码方式等配置信息放在web.xml中，如果以后数据库的用户名、密码改变了，则直接很方便地修改web.xml就行了，避免了直接修改源代码的麻烦

![image-20220925163944354](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925163944354.png)

![image-20220925163841339](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925163841339.png)

![image-20220925163855770](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925163855770.png)

![image-20220925163915402](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925163915402.png)

**如果@overwrite了init()方法 一定要super.init();**

**调用父类GenericServlet的init()方法**		父类对config进行赋值到this.config

![image-20220925164340440](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925164340440.png)

![image-20220925164243026](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925164243026.png)

![image-20220925164525631](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925164525631.png)

![image-20220925164550802](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925164550802.png)

## ServletContext

ServletContext官方叫[servlet](https://so.csdn.net/so/search?q=servlet&spm=1001.2101.3001.7020)上下文。服务器会为每一个工程创建一个对象，这个对象就是ServletContext对象。这个对象全局唯一，而且工程内部的所有servlet都共享这个对象。所以叫全局应用程序共享对象

![image-20220925193619760](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925193619760.png)

1、ServletContext 是一个接口，它表示 Servlet 上下文对象 

2、**一个 web 工程，只有一个 ServletContext 对象实例**。 

3、ServletContext 对象是一个域对象。 

4、ServletContext 是在 **web 工程部署启动的时候创建**。在 **web 工程停止的时候销毁**。

**未存储数据 数据为空 当存储了数据	只要web工程未停止 数据就一直存在 并且在任何Servlet中都可以获取到**

域对象:

域对象，是可以像 Map 一样存取数据的对象，叫域对象。 

这里的域指的是存取数据的操作范围，整个 web 工程

|        | 存数据         | 取数据         | 删除数据          |
| ------ | -------------- | -------------- | ----------------- |
| Map    | put()          | get()          | remove()          |
| 域对象 | setAttribute() | getAttribute() | removeAttribute() |

![image-20220925193725402](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925193725402.png)

### 获取ServletContext

```java
this.getServletContext();  
ServletContext servletContext1 = getServletContext();

this.getServletConfig().getServletContext();
ServletContext servletContext = servletConfig.getServletContext();
```

### ServletContext方法

```java
//1、获取 web.xml 中配置的上下文参数 context-param 
servletContext.getInitParameter("username");//root
//2、获取当前的工程路径，格式: /工程路径 
servletContext.getContextPath();/////ServletTest
//3、获取工程部署后在服务器硬盘上的绝对路径	斜杠被服务器解析地址为:http://ip:port/工程名/ 映射到 IDEA 代码
servletContext.getRealPath( "/");//D:\Java18.0.0.0\IntelliJ_IDLE\Java_web\out\artifacts\ServletTest_war_exploded\
//4、像 Map 一样存取数
	setAttribute("key","value")//存
    getAttribute("key")//取
    removeAttribute("key")//除

```

1、获取 web.xml 中配置的上下文参数 context-param 

```java
//获取 web.xml 中配置的上下文参数 context-param
System.out.println(servletContext.getInitParameter("username"));
//root
```

2、获取当前的工程路径，格式: /工程路径 

```java
//获取当前的工程路径，格式: /工程路径
System.out.println(servletContext.getContextPath());
///ServletTest
```

3、获取工程部署后在服务器硬盘上的绝对路径

```java
//获取工程部署后在服务器硬盘上的绝对路径
//斜杠被服务器解析地址为:http://ip:port/工程名/ 映射到 IDEA 代码
System.out.println("绝对路径" + servletContext.getRealPath( "/"));
//绝对路径D:\Java18.0.0.0\IntelliJ_IDLE\Java_web\out\artifacts\ServletTest_war_exploded\
```

![image-20220925194316600](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925194316600.png)

![image-20220925194330141](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925194330141.png) 

4、像 Map 一样存取数

```java
context.setAttribute("key1", "value1");
context.getAttribute("key1")//value1
removeAttribute("key1")
```

## HTTP

HTTP协议

**超文本传输协议**（英文：**H**yper**T**ext **T**ransfer **P**rotocol，缩写：HTTP）是一种用于分布式、协作式和超媒体信息系统的应用层协议。**HTTP是万维网的数据通信的基础**

**HTTP是一个客户端终端（用户）和服务器端（网站）请求和应答的标准（TCP）。**通过使用网页浏览器、网络爬虫或者其它的工具，**客户端发起一个HTTP请求到服务器上指定端口（默认端口为80）。**我们称这个客户端为用户代理程序（user agent）。应答的服务器上存储着一些资源，比如HTML文件和图像。我们称这个应答服务器为源服务器（origin server）。在用户代理和源服务器中间可能存在多个“中间层”，比如代理服务器、网关或者隧道（tunnel）。

### HTTP原理

HTTP协议定义Web客户端如何从Web服务器请求Web页面，以及服务器如何把Web页面传送给客户端。**HTTP协议采用了请求/响应模型**。客户端向服务器发送一个请求**报文**，请求报文包含请求的方法、URL、协议版本、请求头部和请求数据。服务器以一个状态行作为响应，响应的内容包括协议的版本、成功或者错误代码、服务器信息、响应头部和响应数据。

![image-20220925235803285](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235803285.png)

![image-20220925235622150](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235622150.png)

![image-20220925235652813](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235652813.png)

![image-20220925235700203](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235700203.png)

**使用HTTP协议,每当有新的请求发送时,就会有对应的新响应产生。协议本身并不保留之前一切的请求或响应报文的信息**。这是为了更快地处理大量事务,确保协议的可伸缩性,而特意把HTTP协议设计成 如此简单的。可是,随着Web的不断发展,因无状态而导致业务处理变得棘手 的情况增多了。比如,用户登录到一家购物网站,即使他跳转到该站的 其他页面后,也需要能继续保持登录状态。针对这个实例,网站为了能 够掌握是谁送出的请求,需要保存用户的状态。HTTP/1.1虽然是无状态协议,但为了实现期望的保持状态功能, 于是引入了**Cookie技术**。有了**Cookie**再用HTTP协议通信,就可以**管理状态**了

![image-20220926000137848](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926000137848.png)

### HTTP请求

![image-20220926000216937](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926000216937.png)

#### GET 请求

**1、请求行** 

(1) 请求的方式 GET 

(2) 请求的资源路径[+?+请求参数] 

(3) 请求的协议的版本号 HTTP/1.1 

**2、请求头 key : value 组成 不同的键值对，表示不同的含**

**常用请求头：**

Accept: 表示客户端可以接收的数据类型 

Accpet-Languege: 表示客户端可以接收的语言类型 

User-Agent: 表示客户端浏览器的信息 

Host： 表示请求时的服务器 ip 和端口号

![image-20220926102438946](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926102438946.png)

#### POST请求

**1、请求行** 

(1) 请求的方式 POST 

(2) 请求的资源路径[+?+请求参数] 

(3) 请求的协议的版本号 HTTP/1.1 

**2、请求头 1) key : value 不同的请求头，有不同的含义** 

**常用请求头：**

Accept: 表示客户端可以接收的数据类型 

Accpet-Languege: 表示客户端可以接收的语言类型 

User-Agent: 表示客户端浏览器的信息 

Host： 表示请求时的服务器 ip 和端口号

 **空行**（隔开）

**3、请求体 ===>>> 就是发送给服务器的数据**

![image-20220926103227830](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926103227830.png)

#### 常用的GET&POST请求

**GET 请求有：** 

1、form 标签 method=get 

2、a 标签 

3、link 标签引入 css 

4、Script 标签引入 js 文件 

5、img 标签引入图片 

6、iframe 引入 html 页面 

7、在浏览器地址栏中输入地址后敲回车 

**POST 请求有：** 

8、form 标签 method=post

### HTTP响应

**响应的 HTTP 协议格式** 

**1、响应行** 

(1) 响应的协议和版本号 

(2) 响应状态码 

**常用的响应码说明：**

200 表示请求成功 

302 表示请求重定向 

404 表示请求服务器已经收到了，但是你要的数据不存在（请求地址错误） 

500 表示服务器已经收到请求，但是服务器内部错误（代码错误）

(3) 响应状态描述符 

**2、响应头** 

(1) key : value 不同的响应头，有其不同含义 

**空行** （隔开）

**3、响应体 ---->>> 就是回传给客户端的数据**

![image-20220926104222306](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926104222306.png)

### MIME 类型

**MIME 是 HTTP 协议中数据**

**MIME 的英文全称是"Multipurpose Internet Mail Extensions" 多功能 Internet 邮件扩充服务。MIME 类型的格式是“大类型/小 类型”，并与某一种文件的扩展名相对应**

常见的 MIME 类型：

| 文件               | MIME 类型                         |
| ------------------ | --------------------------------- |
| 超文本标记语言文本 | .html , .htm text/html            |
| 普通文本           | .txt text/plain                   |
| RTF文本            | .rtf application/rtf              |
| GIF 图形           | .gif image/gif                    |
| JPEG 图形          | .jpeg,.jpg image/jpeg             |
| au 声音文件        | .au audio/basic                   |
| MIDI 音乐文件      | mid,.midi audio/midi,audio/x-midi |
| RealAudio 音乐文件 | .ra, .ram audio/x-pn-realaudio    |
| MPEG 文件          | .mpg,.mpeg video/mpeg             |
| AVI 文件           | .avi video/x-msvideo              |
| GZIP 文件          | .gz application/x-gzip            |
| TAR 文件           | .tar application/x-tar            |

### Google查看HTTP协议 

![image-20220926110803516](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926110803516.png)

### Firefox查看HTTP协议

![image-20220926110814790](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926110814790.png)

## HTTPServletRequest

![image-20220925115552021](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925115552021.png)

### HTTPServletRequest类的作用

**在 Servlet API 中，定义了一个 HttpServletRequest 接口，它继承自 ServletRequest 接口。HttpServletRequest 对象专门用于封装 HTTP 请求消息，简称 request 对象。**

**每次只要有请求进入Tomcat服务器，Tomcat服务器就会将请求到的HTTP协议的信息解析好封装到Request对象中。**

**然后传递到Servlet（）方法（doGet和doPost）中供我们使用。**我们可以通过HTTPServletRequest对象，获取到所有请求的信息。



![image-20220927185931326](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927185931326.png)

### HttpServletRequest 类的常用方法

| **getRequestURI()**           | 获取请求的资源路径                       |
| ----------------------------- | ---------------------------------------- |
| **getRequestURL()**           | **获取请求的统一资源定位符（绝对路径）** |
| **getRemoteHost()**           | **获取客户端的 ip 地址**                 |
| **getHeader()**               | **获取请求头**                           |
| **getParameter()**            | **获取请求的参数**                       |
| **getParameterValues()**      | **获取请求的参数（多个值的时候使用）**   |
| **getMethod()**               | **获取请求的方式 GET 或 POST**           |
| **setAttribute(key, value);** | **设置域数据**                           |
| **getAttribute(key);**        | **获取域数据**                           |
| **getRequestDispatcher()**    | **获取请求转发对象**                     |

**HTTP 请求消息分为请求行、请求消息头和请求消息体三部分，所以 HttpServletRequest 接口中定义了获取请求行、请求头和请求消息体的相关方法。**

#### 获取请求行信息

![image-20220927190137689](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927190137689.png)

#### 获取请求头信息

![image-20220927232211149](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927232211149.png)

#### 获取Form表单信息

![image-20220927232245446](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927232245446.png)

#### 中文乱码问题

##### POST 请求

![image-20220927232540729](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927232540729.png)

##### doGet请求

![image-20220927232606504](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927232606504.png)

![image-20220927232618210](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927232618210.png)

### 读取请求信息

#### doGet请求

```java
/**
 @author EddieZhang
 @create 2022-09-27 21:58
 */
public class HTTPServletRequest extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("-----------------doGet-----------------");
        System.out.println("URL" + req.getRequestURL());
        System.out.println("客户的IP地址" + req.getRemoteHost());
        System.out.println("请求头user 的Agent" + req.getHeader("User-Agent"));
        System.out.println("请求方式" + req.getMethod());
        //请求参数
        System.out.println("Name\t" + req.getParameter("name"));
        System.out.println("Sex\t" + req.getParameter("sex"));
        String[] majors = req.getParameterValues("major");
        System.out.println(Arrays.asList(majors));
        //-----------------doGet-----------------
        //URLhttp://localhost:8080/ServletTest/request
        //客户的IP地址127.0.0.1
        //请求头user 的AgentMozilla/5.0 (Windows NT 10.0; Win64; x64; rv:105.0) Gecko/20100101 Firefox/105.0
        //请求方式GET
        //Name	我是一个程序员
        //Sex	Male
        //[Java, C++, Python, PHP]
    }
```

#### post请求

**post请求一定要setCharacterEncoding("UTF-8");//设置字符集 防止中文乱码**

**一定要在获取请求信息前使用**

```java
//post请求一定要setCharacterEncoding("UTF-8");//设置字符集 防止中文乱码
@Override
protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    req.setCharacterEncoding("UTF-8");//设置字符集 防止中文乱码  **一定要再获取请求信息前使用**
    System.out.println("-----------------doPost-----------------");
    System.out.println("URL" + req.getRequestURL());
    System.out.println("客户的IP地址" + req.getRemoteHost());
    System.out.println("请求头user 的Agent" + req.getHeader("User-Agent"));
    System.out.println("请求方式" + req.getMethod());
    //请求参数
    System.out.println("Name\t" + req.getParameter("name"));
    System.out.println("Sex\t" + req.getParameter("sex"));
    String[] majors = req.getParameterValues("major");
    System.out.println(Arrays.asList(majors));
    //-----------------doPost-----------------
    //URLhttp://localhost:8080/ServletTest/request
    //客户的IP地址127.0.0.1
    //请求头user 的AgentMozilla/5.0 (Windows NT 10.0; Win64; x64; rv:105.0) Gecko/20100101 Firefox/105.0
    //请求方式POST
    //Name	我是一个程序员
    //Sex	Male
    //[Java, C++, Python, PHP]
}
```

## Servlet请求的转发

**问题引入：**

Web 应用在处理客户端的请求时，经常需要多个 Web 资源共同协作才能生成响应结果。但由于 Serlvet 对象无法直接调用其他 Servlet 的 service() 方法，所以 Servlet 规范提供了请求转发（RequestDispatcher 接口）

**请求转发：**

请求转发属于服务器行为。容器接收请求后，Servlet 会先对请求做一些预处理，然后将请求传递给其他 Web 资源，来完成包括生成响应在内的后续工作

**RequestDispatcher 接口**

javax.servlet 包中定义了一个 RequestDispatcher 接口，RequestDispatcher 对象由 Servlet 容器创建，用于封装由路径所标识的 Web 资源。利用 RequestDispatcher 对象可以把请求转发给其他的 Web 资源

**Servlet 可以通过 2 种方式获得 RequestDispatcher 对象：**

1. 调用 ServletContext 的 getRequestDispatcher(String path) 方法，参数 path 指定目标资源的路径，必须为绝对路径；
2. 调用 ServletRequest 的 getRequestDispatcher(String path) 方法，参数 path 指定目标资源的路径，可以为绝对路径，也可以为相对路径

**RequestDispatcher 接口中提供了以下方法。**

![image-20220927233518818](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927233518818.png)

### 请求转发的工作原理

![image-20220927233549646](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927233549646.png)

### 请求转发的特点

请求转发具有以下特点：

1. 请求转发不支持跨域访问，只能跳转到当前应用中的资源。
2. 请求转发之后，浏览器地址栏中的 **URL 不会发生变化**，因此浏览器不知道在服务器内部发生了转发行为，更无法得知转发的次数。
3. 参与请求转发的 Web 资源之间共享同一 request 对象和 response 对象。
4. 由于 **forward() 方法会先清空 response 缓冲区**，因此只有转发到最后一个 Web 资源时，生成的响应才会被发送到客户端。

### request 域对象

**request 是 Servlet 的三大域对象之一，它需要与请求转发配合使用，才可以实现动态资源间的数据传递。**

![image-20220930100311639](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930100311639.png)

#### Context 域对象和 request 域对象

![image-20220930100347026](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930100347026.png)

## Servlet-base标签

**设置页面的相对路径；**工作时参照的地址 href 属性就是参数的地址值

base标签可以设置当前页面中所有相对路径工作时，参照指定的路径来进行跳转

For instance

![image-20220929224433011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929224433011.png)

![image-20220929225921776](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929225921776.png)

![image-20220929225843331](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929225843331.png)

![image-20220929225856876](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929225856876.png)

当未指定base标签的时候

我们点击跳转到一个页面的时候 相对路径在工作时候都是参照当前浏览器地址栏中的地址进行跳转

![image-20220929223424225](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929223424225.png)

指定base标签的时候

我们点击跳转到一个页面的时候 相对路径在工作时候都是参照我们指定的路径进行跳转

## web中的绝对&相对路径

在Java web中路径分为绝对路径和相对路径两种

### 相对路径：

| **.**      | 表示当前目录            |
| ---------- | ----------------------- |
| **..**     | **表示上一层目录**      |
| **资源名** | **表示当前目录/资源名** |

### 绝对路径：

http://ip:port/工程路径/资源路径

**开发中路径使用绝对路径而不是简单的使用相对路径**

1.绝对路径

2.base+相对路径

## web中的/

/ 作为一种绝对路径在web中

### / 被浏览器解析：

http://ip:port/

![image-20220930095324568](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930095324568.png)

### / 被服务器解析：

![image-20220930095200941](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930095200941.png)

servletContext.getRealPath(“/”); 

request.getRequestDispatcher(“/”);

http://ip:port/工程路径

### 特殊情况：

response.sendRedirect("/");重定向

把斜杠发给浏览器解析得到：

http://ip:prot/

## HttpServletResponse

### HttpServletResponse类的作用

在 Servlet API 中，定义了一个 HttpServletResponse 接口，它继承自 ServletResponse 接口。HttpServletResponse 对象专门用来封装 HTTP 响应消息，简称 response 对象。

Servlet 容器会针对每次请求创建一个 response 对象，并把它作为参数传递给 Servlet 的 service 方法。Servlet 处理请求后，会将响应信息封装到 response 对象中，并由容器解析后返回给客户端。

由于 HTTP 响应消息由响应行、响应头、消息体三部分组成，所以 HttpServletResponse 接口中定义了向客户端发送响应状态码、响应头、响应体的方法

### HttpServletResponse类的常用方法

#### 响应行相关的方法

![image-20220930101541972](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930101541972.png)

#### 响应头相关的方法

![image-20220930101551177](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930101551177.png)

#### 响应体相关的方法

![image-20220930101600509](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930101600509.png)

**注意：getOutputStream() 和 getWriter() 方法互相排斥，不可同时使用，否则会发生 IllegalStateException 异常。**

### response 中文乱码问题

#### 使用字节流输出中文

![image-20220930101852561](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930101852561.png)

#### 使用字符流输出中文

![image-20220930101903787](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930101903787.png)

**注意：在使用第二种方式更加方便 但是一定要在获取响应流之前进行设置 否则无效**

![image-20220930102012036](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930102012036.png)

## 请求重定向

重定向属于客户端行为。服务器在收到客户端请求后，会通知客户端浏览器重新向另外一个 URL 发送请求，这称为请求重定向。它本质上是两次 HTTP 请求，对应两个 request 对象和两个 response 对象

### 重定向的工作流程

![image-20220930103216468](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930103216468.png)

### 请求转发和请求重定向的区别

![image-20220930103300851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930103300851.png)

### response.sendRedirect()方法

![image-20220930103321576](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930103321576.png)

## Listener监听器

服务器端三大组件之一

![image-20221008182220550](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008182220550.png)

监听器 Listener 是一个实现特定接口的 Java 程序，这个程序专门用于**监听另一个 Java 对象的方法调用或属性改变**，当被监听对象发生上述事件后，监听器某个方法将立即自动执行

Listener 它是 JavaEE的规范，就是接口

监听器的相关概念：

- 事件：方法调用、属性改变、状态改变等。
- 事件源：被监听的对象（ 例如：request、session、servletContext）。
- 监听器：用于监听事件源对象 ，事件源对象状态的变化都会触发监听器。
- 注册监听器：将监听器与事件源进行绑定。

### ServletContextListener 监听器

**能够监听 ServletContext 对象的生命周期，实际上就是监听 Web 应用的生命周期**

**当Servlet 容器启动或终止Web 应用时，会触发ServletContextEvent 事件，该事件由ServletContextListener 来处理。在 ServletContextListener 接口中定义了处理ServletContextEvent 事件的两个方法**

ServletContextListener 它可以监听 ServletContext 对象的创建和销毁。 

ServletContext 对象在 web 工程启动的时候创建，在 web 工程停止的时候销毁。 

监听到创建和销毁之后都会分别调用 ServletContextListener 监听器的方法反馈

**两个方法分别是：**

```java
public interface ServletContextListener extends EventListener {
/**
* 在 ServletContext 对象创建之后马上调用，做初始化
*/
public void contextInitialized(ServletContextEvent sce);
/**
* 在 ServletContext 对象销毁之后调用
*/
public void contextDestroyed(ServletContextEvent sce);
}
```

**使用 ServletContextListener 监听器监听 ServletContext 对象**

**1、编写一个类去实现 ServletContextListener** 

**2、实现其两个回调方法** 

**3、到 web.xml 中去配置监听器**



**1、编写一个类去实现 ServletContextListener** 

![image-20221008185900298](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008185900298.png)

**2、实现其两个回调方法** 

```java
public class MyServletContextListenerImpl implements ServletContextListener {
    @Override
    public void contextInitialized(ServletContextEvent sce) {
        System.out.println("ServletContext对象被创建了");
    }

    @Override
    public void contextDestroyed(ServletContextEvent sce) {
        System.out.println("ServletContext对象被销毁了");

    }
}
```

**3、到 web.xml 中去配置监听器**

![image-20221008185949678](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008185949678.png)

## JSP

jsp 的**主要作用是代替 Servlet 程序回传 html 页面的数据**。 

**因为 Servlet 程序回传 html 页面数据是一件非常繁锁的事情**。开发成本和维护成本都极高。

![image-20221007204246205](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204246205.png)

![image-20221007204135376](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204135376.png)

### Servlet与JSP

![image-20221007204220557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204220557.png)

### JSP生命周期

JSP 生命周期定义了 JSP 从创建到销毁的整个过程。这**类似于 Servlet 生命周期**，**不同的是，JSP 需要先被编译成 Servlet**。

![image-20221007204409110](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204409110.png)

#### 1. JSP编译

![image-20221007204513598](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204513598.png)

#### 2. JSP初始化

![image-20221007204540518](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204540518.png)

#### 3. JSP执行

![image-20221007204619359](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204619359.png)

#### 4. JSP销毁

![image-20221007204653990](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007204653990.png)

### JSP的介绍与创建

![image-20221007225754832](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007225754832.png)

### JSP的本质

![image-20221007225818285](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007225818285.png)

### JSP的指令

![image-20221008095118770](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095118770.png)

#### page指令：

![image-20221008095149369](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095149369.png)

**默认值即可 不建议修改**

| 属 性        | 取 值                                                        | 说 明                                                       | 举 例                                                        |
| ------------ | ------------------------------------------------------------ | ----------------------------------------------------------- | ------------------------------------------------------------ |
| buffer       | none、缓冲区大小（默认值为 8kb）                             | 指定输出流是否有缓冲区                                      | <%@ page buffer="16kb" %>                                    |
| autoFlush    | true（默认值）、false                                        | 指定缓冲区是否自动清除                                      | <%@ page autoFlush="true" %>                                 |
| contentType  | text/html; charset = ISO-8859-1、 text/xml；charset = UTF-8 等 | 指定 MIME 类型和字符编码                                    | <%@ page contentType="text/html;charset=UTF-8" %>            |
| errorpage    | 页面路径                                                     | 指定当前 JSP 页面发生异常时，需要重定向的错误页面           | <%@ page errorpage="myerrorpage.jsp" %>  注意：myerrorpage.jsp 的 isErrorpage 值必须为 true |
| isErrorpage  | true、false（默认值）                                        | 指定当前页面为错误页面                                      | <%@ page isErrorpage="true" %>                               |
| extends      | 包名.类名                                                    | 指定当前页面继承的父类，一般很少使用                        | <%@ page extends="mypackage.SampleClass"%>                   |
| import       | 类名、接口名、包名                                           | 导入类、接口、包，类似于 Java 的 import 关键字              | <％@ page import = " java.util.Date" ％> <%@ page import="java.io.*, java.lang.*"%> |
| info         | 页面的描述信息                                               | 定义 JSP 页面的描述信息，可以使用 getServletInfo() 方法获取 | <%@ page info="这里是编程帮的页面信息"%>                     |
| isThreadSafe | true（默认值）、false                                        | 是否允许多线程使用                                          | <%@ page isThreadSafe="false" %>                             |
| language     | 脚本语言                                                     | 指定页面中使用的脚本语言                                    | <%@ page language= "java" %>                                 |
| session      | true（默认值）、false                                        | 指定页面是否使用 session                                    | <%@ page session="false" %>                                  |
| isELIgnored  | true（默认值）、false                                        | 指定页面是否忽略 JSP 中的 EL                                | <%@ page isELIgnored="false" %>                              |

**以上属性除了 import 可以声明多个外，其它属性都只能出现一次。**

![image-20221008095435822](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095435822.png)

![image-20221007225842190](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007225842190.png)

#### include指令

JSP可以**通过include指令来包含其他文件**。被包含的文件可以是JSP文件、HTML文件或文本文件。包含的文件就好像是该JSP文件的一部分，会被同时编译执行

![image-20221008095526757](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095526757.png)

![image-20221008095705551](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095705551.png)



#### taglib指令

![image-20221008095746847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095746847.png)![image-20221008095812605](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008095812605.png)

### JSP脚本

![image-20221008093935186](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008093935186.png)

#### 声明脚本(极少使用)

![image-20221008094010776](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094010776.png)

#### JSP脚本和声明的区别

![image-20221008094048165](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094048165.png)

#### 表达式脚本（常用）

![image-20221008094332655](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094332655.png)

#### 代码脚本

![image-20221008094435042](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094435042.png)

![image-20221008094456827](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094456827.png)

![image-20221008094527819](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008094527819.png)

### JSP注释

**对程序代码的解释和说明**。注释可以**提高代码的可读性**，让他人能够更加轻松地了解代码，从而**提高团队合作开发的效率**

#### HTML 注释

![image-20221008110753429](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008110753429.png)

#### 带有 JSP 表达式的注释

![image-20221008110905216](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008110905216.png)

![image-20221008110917777](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008110917777.png)

#### 隐藏注释

![image-20221008110957971](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008110957971.png)

#### 脚本程序（Scriptlet）中的注释

脚本程序中包含的是一段 Java 代码，所以在脚本程序中的注释**与在 Java 中的注释是相同的**

脚本程序中包括下面 3 种注释方法。

- 单行注释
- 多行注释
- 文档注释

![image-20221008111135661](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008111135661.png)

![image-20221008111149142](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008111149142.png)

![image-20221008111159987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008111159987.png)

### JSP内置对象

![image-20221008111345957](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008111345957.png)

#### 九大内置对象

| 对 象                                                       | 类型                                   | 说 明                                                        |
| ----------------------------------------------------------- | -------------------------------------- | ------------------------------------------------------------ |
| [request](http://c.biancheng.net/jsp2/request.html)         | javax.servlet.http.HttpServletRequest  | 获取用户请求信息                                             |
| [response](http://c.biancheng.net/jsp2/response.html)       | javax.servlet.http.HttpServletResponse | 响应客户端请求，并将处理信息返回到客户端                     |
| [out](http://c.biancheng.net/jsp2/out.html)                 | javax.servlet.jsp.JspWriter            | 输出内容到 HTML 中                                           |
| [session](http://c.biancheng.net/jsp2/session.html)         | javax.servlet.http.HttpSession         | 用来保存用户信息                                             |
| [application](http://c.biancheng.net/jsp2/application.html) | javax.servlet.ServletContext           | 所有用户共享信息                                             |
| [config](http://c.biancheng.net/jsp2/config.html)           | javax.servlet.ServletConfig            | 这是一个 Servlet 配置对象，用于 Servlet 和页面的初始化参数   |
| [pageContext](http://c.biancheng.net/jsp2/pagecontext.html) | javax.servlet.jsp.PageContext          | JSP 的页面容器，用于访问 page、request、application 和 session 的属性 |
| [page](http://c.biancheng.net/jsp2/page_object.html)        | javax.servlet.jsp.HttpJspPage          | 类似于 Java 类的 this 关键字，表示当前 JSP 页面              |
| [exception](http://c.biancheng.net/jsp2/page.html)          | java.lang.Throwable                    | 该对象用于处理 JSP 文件执行时发生的错误和异常；只有在 JSP 页面的 page 指令中指定 isErrorPage 的取值 true 时，才可以在本页面使用 exception 对象。 |

SP 的内置对象主要有以下特点：

- 由 JSP 规范提供，不用编写者实例化；
- 通过 Web 容器实现和管理；
- 所有 JSP 页面均可使用；
- 只有在脚本元素的表达式或代码段中才能使用。

##### jsp 中的 out 输出和 response.getWriter 输出

**使用out.print（）**

**默认使用out输出**

out.write() 输出字符串没有问题 **输出整型有问题 底层使用char型存储**

![image-20221008120037156](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008120037156.png)

![image-20221008115541997](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008115541997.png)

out.print() 输出任意数据都没有问题（**都转换成为字符串后调用的 write 输出**）

深入源码，浅出结论：在 jsp 页面中，**可以统一使用 out.print()来进行输出**

**共同点 都是进行输出**

response 中表示响应，我们经常用于设置返回给客户端的内容（输出） out 也是给用户做输出使用的

**不同点**

![image-20221008114942519](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008114942519.png)

#### 四大域对象

pageContext（page 域对象）、request（request 域对象）、session（session 域对象）、以及 application（application 域对象）

| 作用域      | 描述                                                         | 作用范围                                                     |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| page        | 如果把属性保存到 pageContext 中，则它的作用域是 page。       | 该作用域中的属性只在当前 JSP 页面有效，跳转页面后失效。      |
| request     | 如果把属性保存到 request 中，则它的作用域是 request。        | 该作用域中的属性只在当前请求范围内有效。服务器跳转页面后有效，例如<jsp:forward>；客户端跳转页面后无效，例如超链接。 |
| session     | 如果把属性保存到 session 中，则它的作用域是 session。        | 该作用域中的属性只在当前会话范围内有效，网页关闭后失效。     |
| application | 如果把属性保存到 application 中，则它的作用域是 application。 | 该作用域中的属性在整个应用范围内有效，服务器重启后失效。     |

**四个域在使用的时候，优先顺序**

pageContext ====>>> request ====>>> session ====>>> application（**范围从小到大**）

JSP 中的 4 个域对象都能通过以下 3 个方法，对属性进行保存、获取和移除操作。

| 返回值类型 | 方法                                | 作用                 |
| ---------- | ----------------------------------- | -------------------- |
| void       | setAttribute(String name, Object o) | 将属性保存到域对象中 |
| Object     | getAttribute(String name)           | 获取域对象中的属性值 |
| void       | removeAttribute(String name)        | 将属性从域对象中移除 |

### 常用标签-包含

##### 静态包含

**项目中一些通用的可以写入一个jsp中 然后使用静态包含引用jsp 后期维护或修改 只需要维护一次jsp即可**

![image-20221008144229289](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144229289.png)

分为以下三步：

1. 将被包含的 jsp文件1 放入 jsp文件2 中
2. 将文件2 放入服务器解析
3. 生成一个.java 文件

![image-20221008144244936](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144244936.png)

![image-20221008144327913](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144327913.png)

![image-20221008144346257](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144346257.png)

##### 动态包含

![image-20221008144218073](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144218073.png)

![image-20221008144410705](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144410705.png)

分为以下五步：

1. 将被包含的 jsp文件1 直接放入服务器解析
2. 生成文件1.java文件
3. 将文件1的结果放入文件2中
4. 再将文件2 放入服务器解析
5. 生成一个文件2.java 文件

![image-20221008144436941](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144436941.png)

![image-20221008144502265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144502265.png)

##### 动态包含&静态包含区别

**过程是最主要的区别**，除了以上之外，还有一下的区别（主要是2 3 **传递参数和url地址的区别**）。

```java
1 	<jsp:include>是动态包含
	而<%@ include%>是静态包含。		
2	动态包含可以给被包含的页面传递参数。	
	静态包含不能给被包含的页面传递参数。
3	动态包含的地址可以是变量。
	静态包含的地址是常量。
4	<jsp:include page=“file” flush=“true” />它总是会检查所含文件中的变化。
	而<%@include file=“file”%>不会检查所含文件的变化，适用于包含静态页面。
```

![image-20221008144745873](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008144745873.png)

JSP中，include是一个经常用到的标签。当应用程序中所有的页面的某些部分(如标题、页脚和导航栏)都相同的时候,我们就可以考虑用include。但是相同的部分有静态的（装载进页面显示后再也不变的），有动态的（装载进页面后还会改变，如：随时间改变、随用户行为改变等）。那么，对这两种类型的内容的包含方式一样吗？当然不一样。

　　一、静态包含：＜%@ include file=”包含页面”%＞ 

　　静态包含一般用于加载进页面显示后就再也不变的东西，比如页眉、背景、标题等等。静态包含不会检查所含文件的变化，把文件包含进来后，被包含文件的修改变化是不会影响已被包含进来的内容的。因为，静态包含发生在编译阶段。比如：a.jsp中使用了语句 <%@ include file="b.jsp"%>，把b.jsp包含了进来，那么在编译a.jsp文件时，会直接把b.jsp文件的内容全部内嵌到a.jsp文件中包含b的语句的位置。然后运行a，显示a页面。也就是说，静态include是先把被包含文件的内容全部复制内嵌到包含文件中，再进行编译运行的。也正是因为要把b包含进a，所以b中的变量等不能与a重复，否则会报错。

![img](https://images2015.cnblogs.com/blog/1018541/201611/1018541-20161108215013639-1042637239.png)

　　二、动态包含：<jsp:include page=" " flush="true"/> 

　　动态包含用于加载经常变化的、要求显示最新版本内容的东西，比如提交时间戳：用户打开博客编辑页面时，有一个时间加载进来了。用户编写完博客，点击提交时，就应该使用/显示提交瞬间的时间而不是打开编辑页面时的那个时间。所以这里要用的就是最新时间。由上面我们知道，静态include是先包含进来，再编译，运行并传回浏览器显示的，所以不能满足我们要求某些部分使用最新内容的要求。那么，我们就要用到动态include。

　　动态include与静态include的最大不同在于：包含文件与被包含文件都是先编译执行，再包含。二者的编译阶段是相互独立的，只有在包含文件的include语句处把被包含文件的执行结果包含进来。换言之，包含文件先编译，执行。执行到了include语句的时候才触发被包含文件的编译、执行，并实时把结果包含进来。从而达到获取最新的被包含内容的目的。同样使用a.jsp包含b.jsp的例子：加入a.jsp中动态include了b.jsp。现在，a先编译成servlet类文件，然后运行，当运行到包含b的语句处，引起b的编译，运行，并把b的运行servlet运行结果包含进a。最后a顺利运行完毕，把a的servlet类运行结果输出到浏览器显示。

![img](https://images2015.cnblogs.com/blog/1018541/201611/1018541-20161108214858342-1503593420.png)

　　

　　综上所述，我们可以一句话辨析静态include与动态include的区别：**静态include是编译阶段的代码拼接，动态include是编译后的servlet的运行结果的拼接**。

　　三、混合搭配的使用方案

　　通过上面两点，我们知道了一个网页可以通过静态包含、动态包含两种方式来使用来自外部的内容。而在我们实际应用中，很少说一个页面只用静态包含或只用动态包含的。而是根基实际情况，对页眉页脚、导航栏之类的静态内容我们就用静态包含，对数据库实时查询、时间戳等动态内容我们就用动态包含。具体情况，具体使用，动静结合，灵活搭配



### 常用标签-请求转发

```jsp
<%--
<jsp:forward page=""></jsp:forward> 是请求转发标签，它的功能就是请求转发
page 属性设置请求转发的路径
--%>
<jsp:forward page="/scope2.jsp"></jsp:forward>
```

For instance:

![image-20221008174243206](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008174243206.png)

注意不能直接访问jsp页面

一定要先从客户端先请求Servlet程序 再访问jsp request域中才会有Servlet程序保存的数据

需要先通过Servlet程序将数据保存到request域中 jsp页面中才能获取到request域中的数据 否则会出现空指针异常

![image-20221008181021420](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008181021420.png)

**SearchStudentServlet程序**

```java
/**
 @author EddieZhang
 @create 2022-10-08 17:48
 */
public class SearchStudentServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 获取请求的参数
        // 发 sql 语句查询学生的信息
        // 使用 for 循环生成查询到的数据做模拟
            List<Student> studentList = new ArrayList<>();
        for (int i = 0; i < 10; i++) {
            studentList.add(new Student(i,"name" + i,i,"123456" + i));
        }
        // 保存查询到的结果（学生信息）到 request 域中
        req.setAttribute("stuList",studentList);
        // 请求转发到 showStudent.jsp 页面
        req.getRequestDispatcher("/Test/showStudent.jsp").forward(req,resp);
    }
}
```

**showStudent.jsp**

```jsp
<html>
<head>
    <title>Title</title>
    <style>
        table{
            border: 1px blue solid;
            width: 600px;
            border-collapse: collapse;
        }
        td,th{
            border: 1px blue solid;
        }
    </style>
</head>
<body>
<%
    //从request域中获取数据
    List<Student> studentList = (List<Student>) request.getAttribute("stuList");
%>
<table>
    <tr>
        <td>编号</td>
        <td>姓名</td>
        <td>年龄</td>
        <td>电话</td>
        <td>操作</td>
    </tr>
    <% for (Student student : studentList) { %>
    <tr>
        <td><%=student.getId()%></td>
        <td><%=student.getName()%></td>
        <td><%=student.getAge()%></td>
        <td><%=student.getPhone()%></td>
        <td>删除、修改</td>
    </tr>
    <% } %>
</table>

</body>
</html>
```

### EL表达式

**（Expression Language）表达式语言**

![image-20221008190157873](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008190157873.png)

#### EL表达式的语法

![image-20221008190236201](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008190236201.png)

**EL 表达式在输出 null 值的时候，输出的是空串**。**jsp 表达式脚本输出 null 值的时候，输出的是 null** 

![image-20221008193722984](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008193722984.png)

#### EL 表达式搜索域数据的顺序

EL 表达式主要是在 jsp 页面中输出数据。 主要是输出域对象中的数据。 

**当四个域中都有相同的 key 的数据的时候**，EL 表达式会**按照四个域的从小到大的顺序**去进行搜索，**找到就输出**

pageContext（page 域对象）、request（request 域对象）、session（session 域对象）、以及 application（application 域对象）

| 作用域      | 描述                                                         | 作用范围                                                     |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| page        | 如果把属性保存到 pageContext 中，则它的作用域是 page。       | 该作用域中的属性只在当前 JSP 页面有效，跳转页面后失效。      |
| request     | 如果把属性保存到 request 中，则它的作用域是 request。        | 该作用域中的属性只在当前请求范围内有效。服务器跳转页面后有效，例如<jsp:forward>；客户端跳转页面后无效，例如超链接。 |
| session     | 如果把属性保存到 session 中，则它的作用域是 session。        | 该作用域中的属性只在当前会话范围内有效，网页关闭后失效。     |
| application | 如果把属性保存到 application 中，则它的作用域是 application。 | 该作用域中的属性在整个应用范围内有效，服务器重启后失效。     |

#### EL 表达式输出 Bean 的普通属性，数组属性。List 集 合属性，map 集合属

**EL表达式中是针对与寻找属性对应的getXxx( )方法 若未提供getXxx( )方法则无法找到；**

![image-20221008195219479](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008195219479.png)

![image-20221008193754783](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008193754783.png)

![image-20221008194510633](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008194510633.png)

```jsp
<%
pageContext.setAttribute("person",person);
%>
输出person---------   ${person}<br/>
输出person的name属性---------   ${person.name}<br/>
输出person的citiesList集合---------   ${person.cities}<br/>
输出person的citiesList集合中的某一个元素---------   ${person.cities[3]}<br/>//底层相当于调用了get()方法
输出person的citiesList集合中的某一个元素---------   ${person.cities.get(3)}<br/>
输出person的phones数组---------   ${person.phones}<br/>
输出person的phones数组中的某一个元素---------   ${person.phones[0]}<br/>
输出person的map集合---------   ${person.map}<br/>
输出person的map集合中的指定key值的value---------   ${person.map.get("key1")}<br/>
```

#### EL表达式--运算

##### 关系（比较）运算

| EL比较运算符 | 说明     | 范例                                              | 结果        |
| ------------ | -------- | ------------------------------------------------- | ----------- |
| == 或 eq     | 等于     | ${6==6} 或 ${6 eq 6} ${"A"="a"} 或 ${"A" eq "a"}  | true false  |
| != 或 ne     | 不等于   | ${6!=6} 或 ${6 ne 6} ${“A"!=“a”} 或 ${“A” ne “a”} | false true  |
| < 或 lt      | 小于     | ${3<8} 或 ${3 lt 8} ${"A"<"a"} 或 ${"A" lt "a"}   | true true   |
| > 或 gt      | 大于     | ${3>8} 或 ${3 gt 8} ${"A">"a"} 或 ${"A" gt "a"}   | false false |
| <= 或 le     | 小于等于 | ${3<=8} 或 ${3 le 8} ${"A"<="a"} 或 ${"A" le "a"} | true true   |
| >= 或 ge     | 大于等于 | ${3>=8} 或 ${3 ge 8} ${"A">="a"} 或 ${"A" ge "a"} | false false |

##### 逻辑运算

逻辑运算符两边的表达式必须是**布尔型（Boolean）变量**，其**返回结果也是布尔型（Boolean）**

| EL逻辑运算符 | 说明 | 范例                          | 结果  |
| ------------ | ---- | ----------------------------- | ----- |
| && 或 and    | 与   | ${2>1&&3<4 } 或 ${2>1and3<4 } | true  |
| \|\| 或 or   | 或   | ${2<1\|\|3>4} 或 ${2<1or3>4}  | false |
| ! 或 not     | 非   | ${!(2>4)} 或 ${not (2>4)}     | true  |

##### 算数运算

注意：EL 的`+`运算符与 Java 的`+`运算符不一样，它**无法实现两个字符串的连接运算**。**如果该运算符连接的两个值不能转换为数值型的字符串，则会拋出异常**；反之，EL 会自动将这两个字符转换为数值型数据，再进行运算。

EL 表达式中还**可以使用 `( )` 改变优先级**，例如：`${2+3*2}` 等于 8，`${(2+3)*2}` 等于 10。

| EL算术运算符 | 说明 | 范例   | 结果 |
| ------------ | ---- | ------ | ---- |
| +            | 加   | ${5+2} | 7    |
| -            | 减   | ${5-2} | 3    |
| *            | 乘   | ${5*2} | 10   |
| / 或 div     | 除   | ${5/2} | 2    |
| % 或 mod     | 求余 | ${5%2} | 1    |

##### empty运算

empty 用来判断 EL 表达式中的对象或者变量是否为空。若为空或者 null，返回 true，否则返回 false

以下几种情况为空： 

1、值为 null 值的时候，为空 

2、值为空串的时候，为空 

3、值是 Object 类型数组，长度为零的时候 

4、list 集合，元素个数为零 

5、map 集合，元素个数为零

![image-20221008200821868](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008200821868.png)

##### 三元运算

![image-20221008200151012](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008200151012.png)

##### . 和 [ ]运算

![image-20221008200327482](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008200327482.png)

.点运算，可以输出 Bean 对象中某个属性的值。 

[]中括号运算，可以输出有序集合中某个元素的值。 并且[]中括号运算，还可以输出 map 集合中 key 里含有特殊字

```jsp
//[]中括号运算，还可以输出 map 集合中 key 里含有特殊字
<body>
<%
Map<String,Object> map = new HashMap<String, Object>();
map.put("a.a.a", "aaaValue");
map.put("b+b+b", "bbbValue");
map.put("c-c-c", "cccValue");
request.setAttribute("map", map);
%>
${ map['a.a.a'] } <br>
${ map["b+b+b"] } <br>
${ map['c-c-c'] } <br>
</body>
```

##### EL运算符优先级

在 EL 表达式中，多种运算符混合运算时，优先级如下表所示（由高至低，由左至右）。

| 序号 | 优先级                       |
| ---- | ---------------------------- |
| 1    | [] .                         |
| 2    | ()                           |
| 3    | -（负）、not、! 、empty      |
| 4    | * 、 / 、 div 、% 、mod      |
| 5    | +、-（减）                   |
| 6    | <、>、<=、>=、lt、gt、le、ge |
| 7    | ==、!-、eq、ne               |
| 8    | &&、and                      |
| 9    | \|\|、or                     |
| 10   | ${A?B:C}                     |

#### EL内置对象

为了显示方便，EL 表达式语言提供了许多内置对象，可以通过不同的内置对象来输出不同的内容

| 内置对象         | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| pageScope        | 获取 page 范围的变量                                         |
| requestScope     | 获取 request 范围的变量                                      |
| sessionScope     | 获取 session 范围的变量                                      |
| applicationScope | 获取 application 范围的变量                                  |
| param            | 相当于 request.getParameter(String name)，获取单个参数的值   |
| paramValues      | 相当于 request.getParameterValues(String name)，获取参数集合中的变量值 |
| header           | 相当于 request.getHeader(String name)，获取 HTTP 请求头信息  |
| headerValues     | 相当于 request.getHeaders(String name)，获取 HTTP 请求头数组信息 |
| initParam        | 相当于 application.getInitParameter(String name)，获取 web.xml 文件中的参数值 |
| cookie           | 相当于 request.getCookies()，获取 cookie 中的值              |
| pageContext      | 表示当前 JSP 页面的 pageContext 对象                         |

从以上方法可以看出，EL 表达式**可以输出 4 种属性范围的内容**。如果在不同的属性范围中设置了同一个属性名称，则按照 page、request、session、application 的顺序依次查找。我们也可以指定要取出哪一个范围的变量，例如：`${pagesScope.name}`，表示取出 page 范围的 name 变量

```jsp
	变量 						类型 							作用 

pageContext 		PageContextImpl 		它可以获取 jsp 中的九大内置对象 

pageScope 			Map<String,Object> 		它可以获取 pageContext 域中的数据 

requestScope 		Map<String,Object> 		它可以获取 Request 域中的数据 

sessionScope 		Map<String,Object> 		它可以获取 Session 域中的数据 

applicationScope 	Map<String,Object> 		它可以获取 ServletContext 域中的数据 

param 				Map<String,String> 		它可以获取请求参数的值 

paramValues 		Map<String,String[]> 	它也可以获取请求参数的值，获取多个值的时候使用。 

header 				Map<String,String> 		它可以获取请求头的信息 
	
headerValues 		Map<String,String[]> 	它可以获取请求头的信息，它可以获取多个值的情况 

cookie 				Map<String,Cookie> 		它可以获取当前请求的 Cookie 信息 

initParam 			Map<String,String> 		它可以获取在 web.xml 中配置的上下文参数
```

##### EL 获取四个特定域中的属性

pageScope ====== pageContext 域 

requestScope ====== Request 域 

sessionScope ====== Session 域 

applicationScope ====== ServletContext 域

```jsp
<body>
<%
pageContext.setAttribute("key1", "pageContext1");
pageContext.setAttribute("key2", "pageContext2");
request.setAttribute("key2", "request");
session.setAttribute("key2", "session");
application.setAttribute("key2", "application");
%>
${key2}//未指定域的**按照四个域的从小到大的顺序**去进行搜索，**找到就输出**  
${ applicationScope.key2 }//选择性的输出指定域中的value
</body>
```

##### pageContext 对象的使用

它可以获取 jsp 中的九大内置对象

![image-20221008203245008](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008203245008.png)

1. 协议： 2. 服务器 ip： 3. 服务器端口： 4. 获取工程路径： 5. 获取请求方法： 6. 获取客户端 ip 地址： 7. 获取会话的 id 编号：

![image-20221008203140450](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008203140450.png)

##### EL 表达式其他隐含对象的使用

###### 获取请求参数的值

![image-20221008203633418](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008203633418.png)

![image-20221008204402253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008204402253.png)

![image-20221008204435116](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008204435116.png)

###### 获取请求头的信息

![image-20221008212619333](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008212619333.png)

![image-20221008213144556](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008213144556.png)

###### 获取当前请求的 Cookie 信息

![image-20221008213208105](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008213208105.png)

![image-20221008213515335](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008213515335.png)

###### 获取在 web.xml 中配置的上下文参数

![image-20221008213542481](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008213542481.png)

![image-20221008214004798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008214004798.png)

![image-20221008214215085](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008214215085.png)

#### 禁用EL表达式

![image-20221008214411738](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008214411738.png)

### JSTL 标签库

JSTL 标签库 全称是指 JSP Standard Tag Library JSP 标准标签库。是一个不断完善的开放源代码的 JSP 标 签库。 

EL 表达式主要是为了替换 jsp 中的表达式脚本，而标签库则是为了替换代码脚本。这样使得整个 jsp 页面 变得更佳简洁

![image-20221008215405852](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008215405852.png)

**JSTL 标签库的使用步**

```jsp
1、先导入 jstl 标签库的 jar 包。 taglibs-standard-impl-1.2.1.jar taglibs-standard-spec-1.2.1.jar 

2、第二步，使用 taglib 指令引入标签库。 <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

![image-20221008215248268](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008215248268.png)

![image-20221008215524348](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221008215524348.png)

#### core 核心库使用

```jsp
<%--
i.<c:set />//很少使用
作用：set 标签可以往域中保存数据
域对象.setAttribute(key,value);
scope 属性设置保存到哪个域
page 表示 PageContext 域（默认值）
request 表示 Request 域
session 表示 Session 域
application 表示 ServletContext 域
var 属性设置 key 是多少
value 属性设置值
--%>
保存之前：${ sessionScope.abc } <br>
<c:set scope="session" var="abc" value="abcValue"/>
保存之后：${ sessionScope.abc } <br>



<%--
ii.<c:if />
if 标签用来做 if 判断。
test 属性表示判断的条件（使用 EL 表达式输出）
--%>
<c:if test="${ 12 == 12 }">
<h1>12 等于 12</h1>
</c:if>
<c:if test="${ 12 != 12 }">
<h1>12 不等于 12</h1>
</c:if>


<%--
iii.<c:choose> <c:when> <c:otherwise>标签
作用：多路判断。跟 switch ... case .... default 非常接近
choose 标签开始选择判断
when 标签表示每一种判断情况
test 属性表示当前这种判断情况的值
otherwise 标签表示剩下的情况
//<c:choose> <c:when> <c:otherwise>标签使用时需要注意的点：
1、标签里不能使用 html 注释，要使用 jsp 注释
2、when 标签的父标签一定要是 choose 标签
--%>
<%
request.setAttribute("height", 180);
%>
<c:choose>
<%-- 这是 html 注释 --%>
<c:when test="${ requestScope.height > 190 }">
<h2>小巨人</h2>
</c:when>
<c:when test="${ requestScope.height > 180 }">
<h2>很高</h2>
</c:when>
<c:when test="${ requestScope.height > 170 }">
<h2>还可以</h2>
</c:when>
<c:otherwise>
<c:choose>
<c:when test="${requestScope.height > 160}">
<h3>大于 160</h3>
</c:when>
<c:when test="${requestScope.height > 150}">
<h3>大于 150</h3>
</c:when>
<c:when test="${requestScope.height > 140}">
<h3>大于 140</h3>
</c:when>
<c:otherwise>
其他小于 140
</c:otherwise>
</c:choose>
</c:otherwise>
</c:choose>



<%--1.遍历 1 到 10，输出
begin 属性设置开始的索引
end 属性设置结束的索引
var 属性表示循环的变量(也是当前正在遍历到的数据)
for (int i = 1; i < 10; i++)
--%>
<table border="1">
<c:forEach begin="1" end="10" var="i">
<tr>
<td>第${i}行</td>
</tr>
</c:forEach>
</table>



<%-- 2.遍历 Object 数组
for (Object item: arr)
items 表示遍历的数据源（遍历的集合）
var 表示当前遍历到的数据
--%>
<%
request.setAttribute("arr", new String[]{"18610541354","18688886666","18699998888"});
%>
<c:forEach items="${ requestScope.arr }" var="item">
${ item } <br>
</c:forEach>



//遍历 List 集合---list 中存放 Student 类，有属性：编号，用户名，密码，年龄，电话信息
<%
List<Student> studentList = new ArrayList<Student>();
for (int i = 1; i <= 10; i++) {
studentList.add(new Student(i,"username"+i ,"pass"+i,18+i,"phone"+i));
}
request.setAttribute("stus", studentList);
%>
<table>
<tr>
<th>编号</th>
<th>用户名</th>
<th>密码</th>
<th>年龄</th>
<th>电话</th>
<th>操作</th>
</tr>
<%--
items 表示遍历的集合
var 表示遍历到的数据
begin 表示遍历的开始索引值
end 表示结束的索引值
step 属性表示遍历的步长值
varStatus 属性表示当前遍历到的数据的状态
for（int i = 1; i < 10; i+=2）
--%>
<c:forEach begin="2" end="7" step="2" varStatus="status" items="${requestScope.stus}" var="stu">
<tr>
<td>${stu.id}</td>
<td>${stu.username}</td>
<td>${stu.password}</td>
<td>${stu.age}</td>
<td>${stu.phone}</td>
<td>${status.step}</td>
</tr>
</c:forEach>
</table>

<!--
varStatus 属性表示当前遍历到的数据的状态
源码
class Status implements LoopTagStatus {
                Status() {
                }

                public Object getCurrent() {	获取当前遍历到的数据
                    return LoopTagSupport.this.getCurrent();
                }

                public int getIndex() {		获取遍历的索引
                    return LoopTagSupport.this.index + LoopTagSupport.this.begin;
                }

                public int getCount() {		获取遍历到的个数 第几个遍历的
                    return LoopTagSupport.this.count;
                }

                public boolean isFirst() {		是否是第一个元素
                    return LoopTagSupport.this.index == 0;
                }

                public boolean isLast() {		是否是最后一个元素
                    return LoopTagSupport.this.last;
                }

                public Integer getBegin() {		获取第一个元素
                    return LoopTagSupport.this.beginSpecified ? new Integer(LoopTagSupport.this.begin) : null;
                }

                public Integer getEnd() {		获取最后一个元素
                    return LoopTagSupport.this.endSpecified ? new Integer(LoopTagSupport.this.end) : null;
                }

                public Integer getStep() {  	获取步长值
                    return LoopTagSupport.this.stepSpecified ? new Integer(LoopTagSupport.this.step) : null;
                }
            }
    
-->
```

### jsp的文件上传

文件上传就是对文件进行读写

我们在 JSP 中使用 Commons-FileUpload 组件来实现文件上传

#### 文件上传HTTP协议说明

请求头

![image-20221009145253507](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221009145253507.png)

请求体

![image-20221009150007979](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221009150007979.png)

#### Commons-FileUpload 组件

Commons-FileUpload 组件具有以下特点：

- 使用简单：Commons-FileUpload 可以内嵌到 JSP 页面中，所以只需要编写少量的代码就可以完成文件的上传功能。
- 能够全程控制上传内容：使用 Commons-FileUpload 组件提供的对象及操作方法，可以获得上传文件的信息，即文件名称、类型和大小等。
- 能够控制上传文件的大小和类型：为了避免在上传过程中出现异常数据，Commons-FileUpload 组件提供了相应的方法来控制上传文件。

**使用前需要导jar包**

Commons-FileUpload 组件依赖于 FileUpload 和 Commons，需要 commons-fileupload-xx.jar 和 commons-io-xx.jar 文件。

- commons-fileupload-xx.jar 下载地址：https://commons.apache.org/fileupload/
- commons-io-xx.jar 下载地址：https://commons.apache.org/io/

**JSP 和 HTML Form 标签一起使用，来允许用户把文件上传到服务器。上传的文件可以是文本文件、图像文件或其它任何文档。**

**创建上传文件表单时，需要注意以下几点：**

- 表单的 method 属性必须设置为 POST 方法，不能使用 GET 方法。
- 表单 enctype 属性应设置为 multipart/form-data。
- encType=multipart/form-data 表示提交的数据，以多段（每一个表单项一个数据段）的形式进行拼 接，然后以二进制流的形式发送给服务器
- 表单 action 属性应设置为对应的 Servlet，用来处理文件上传的逻辑代码，下面示例中使用 FileUploadServlet 处理逻辑。
- 使用 <input.../> 标签上传单个文件，属性 type="file"。上传多个文件需添加多个 <input .../> 标签。

![image-20221009142831486](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221009142831486.png)

**拓展**

表单的 enctype 属性有以下 3 个值：

1. application/x-www-form-urlencoded：默认值，用于处理少量文本数据的传递。向服务器发送大量的文件或二进制数据时，效率很低。
2. multipart/form-data：上传二进制数据，只有使用了 multipart/form-data 才能完整的传递文件数据，进行上传操作。
3. text/plain：用于向服务器传递大量文本数据，适用于电子邮件的应用。

**对应的Servlet**

```java
public class Servlet1 extends HttpServlet {
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
//        System.out.println("接收到了文件");
//
//        ServletInputStream inputStream = req.getInputStream();
//        byte[] bytes = new byte[1024];
//        int len;
//        while ((len = inputStream.read(bytes)) != -1) {
//            System.out.println(new String(bytes, 0, len));
//
//        }

        
        //解析上传数据的代码
        //判断上传的数据是否为多段的数据（只有是多段的数据才是文件上传）
        if (ServletFileUpload.isMultipartContent(req)) {
            //是文件上传
            //创建工厂实现类
            FileItemFactory fileItemFactory = new DiskFileItemFactory();
            //创建用于解析上传数据的工具类ServletFileUpload类
            ServletFileUpload servletFileUpload = new ServletFileUpload(fileItemFactory);
            //解析上传的数据 得到表单的每一项
            try{

            List<FileItem> list = servletFileUpload.parseRequest(req);
            for (FileItem item :
                    list) {
                if (item.isFormField()) {//判断如果是普通的表单
                    System.out.println("表单项的name值" + item.getFieldName());
                    System.out.println("表单项的value值" + item.getString("UTF-8"));
                } else {//上传的是文件
                    System.out.println("表单项的name值" + item.getFieldName());
                    System.out.println("上传的文件名" + item.getName());
                    //写入到磁盘中
                    item.write(new File("e:\\" + item.getName()));

                }
            }
            }catch (Exception e){
                e.printStackTrace();
            }
        }
    }
}
```

![image-20221009143147560](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221009143147560.png)

![image-20221009143201089](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221009143201089.png)

#### Commons-FileUpload组件API

##### ServletFileUpload类

ServletFileUpload 类用于实现文件上传操作，常用方法如下：

| 方 法                                                        | 说 明                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| public void setSizeMax(long sizeMax)                         | 设置上传文件总量的最大值 (包含文件和表单数据)                |
| public List parseRequest(HttpServletRequest req)             | 解析 form 表单提交的数据，返回一个 FileItem 实例的集合       |
| public static final boolean isMultipartContent(HttpServletRequest req) | 判断请求信息中的内容是否是”multipart/form-data“类型，是则返回 true，否则返回 false。 |
| public void setHeaderEncoding(String encoding)               | 设置转换时所使用的字符集编码                                 |

##### FileItem接口

FileItem 接口用于封装单个表单字段元素的数据，一个表单字段对应一个 FileItem 实例，本节示例中使用的是其实现类 DiskFileItem。FileItem 接口提供的常用方法如下：

| 方 法                        | 说 明                                                        |
| ---------------------------- | ------------------------------------------------------------ |
| public boolean isFormField() | 用于判断 FileItem 类对象封装的数据是一个普通文本表单字段，还是一个文件表单字段，如果是普通表单字段则返回 true，否则返回 false。因此，可以使用该方法判断是否为普通表单域，还是文件上传表单域。 |
| public String getName()      | 获取文件上传的文件名                                         |
| public String getFieldName() | 返回表单字段元素的 name 属性值                               |
| public long getSize()        | 获取上传文件的大小                                           |
| public String getString()    | 将 FileItem 对象中保存的主体内容以一个字符串返回。其重载方法 public String getString(String encoding) 中的参数用指定的字符集编码方式 |
| public void write()          | 将 FileItem 对象中保存的主体内容保存到指定的文件中。         |

##### FileItemFactory接口与实现类

创建 ServletFileUpload 实例需要依赖 FileItemFactory 工厂接口。DiskFileItemFactory 是 FileItemFactory 接口的实现类，该类的常用方法如下。

| 方 法                                           | 说 明                  |
| ----------------------------------------------- | ---------------------- |
| public void setSizeThreshold(int sizeThreshold) | 设置内存缓冲区的大小   |
| public void setRepository(String path)          | 设置临时文件存放的目录 |

### 文件下载

服务器端的文件下载到客户端（浏览器端）

#### 下载的常用API

response.getOutputStream(); 响应输出流

servletContext.getResourceAsStream(); Context写入资源的写入流

servletContext.getMimeType(); 获取要下载文件的文件类型

response.setContentType();响应头告诉客户端（浏览器端）返回的数据类型

resp.setHeader("Content-Disposition", "attachment; filename=" + downloadFileName);

告诉客户端收到的数据是用于下载使用（还是使用响应头） 

// Content-Disposition 响应头，表示收到的数据怎么处理 

// attachment 表示附件，表示下载使用 

// filename= 表示指定下载的文件名

#### 文件下载示例：

```java
public class Download extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取要下载文件的文件名
        String downloadFileName = "1 wbNftKjM0CGqzH-7AnHrYQ.jpeg";
        //读取要下载的文件内容(通过ServletContext对象读取)
        ServletContext servletContext = getServletContext();
        //获取要下载的文件类型
        String mimeType = servletContext.getMimeType("/file/" + downloadFileName);//文件路径
        //显示要下载的文件的类型
        System.out.printf("%s类型文件要被下载",mimeType);
        //在回传前 通过响应头告诉客户端返回的数据类型
        resp.setContentType(mimeType);
        //要告诉客户端收到的数据是用于下载的 （使用响应头）
        // Content-Disposition 响应头，表示收到的数据怎么处理
        // attachment 表示附件，表示下载使用
        // filename= 表示指定下载的文件名
        resp.setHeader("Content-Disposition","attachment; filename=" + downloadFileName);
        //下载的文件名可以和源文件名不同 

        //将文件写入(servletContext.getResourceAsStream获取输入流)
        InputStream resourceAsStream = servletContext.getResourceAsStream("/file/" + downloadFileName);
        //获取响应的输出流
        ServletOutputStream outputStream = resp.getOutputStream();


        //把下载的文件内容传回给客户端
        // 读取输入流中全部的数据，复制给输出流，输出给客户端（使用commons-io的jar包中的IOUtils流工具）
        IOUtils.copy(resourceAsStream,outputStream);
    }
}
```

## Cookie

### HTTP是无状态保存

HTTP（超文本传输协议）是一个基于请求与响应模式的无状态协议

![image-20220925235700203](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235700203.png)

无状态主要指 2 点：

1. 协议对于事务处理没有记忆能力，服务器不能自动维护用户的上下文信息，无法保存用户状态；
2. 每次请求都是独立的，不会受到前面请求的影响，也不会影响后面的请求。


当浏览器发送 HTTP 请求到服务器时，服务器会响应客户端的请求，但当同一个浏览器再次发送请求到该服务器时，服务器并不知道它就是刚才那个浏览器，即 HTTP 协议的请求无法保存用户状态。

通常情况下，用户通过浏览器访问 Web 应用时，服务器都需要保存和跟踪用户的状态。例如，用户在某购物网站结算商品时，Web 服务器必须根据请求用户的身份，找到该用户所购买的商品。由于 HTTP 协议是无协议的，无法保存和跟踪用户状态，所以需要其他的方案来解决问此题，它就是会话技术。

### 会话技术

从打开浏览器访问某个网站，到关闭浏览器的过程，称为一次会话。会话技术是指在会话中，帮助服务器记录用户状态和数据的技术。

常用的会话技术分为两种：

1. Cookie ：客户端会话技术
2. Session ：服务端会话技术

### Cookie

**Cookie 属于客户端会话技术**，它是服务器发送给浏览器的小段文本信息，**存储在客户端浏览器的内存中或硬盘上**。**当浏览器保存了 Cookie 后，每次访问服务器，都会在 HTTP 请求头中将这个 Cookie 回传给服务器**。

### Cookie 的分类

Cookie分为两种：

1. **会话级别 Cookie（默认）**：Cookie 保存到浏览器的内存中，浏览器关闭则 Cookie 失效。
2. **持久的 Cookie**：Cookie 以文本文件的形式保存到硬盘上。

#### Cookie 的工作流程

![image-20221017150024567](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017150024567.png)

### Cookie API

javax.servlet.http 包中定义了一个 Cookie 类，利用它的带参构造方法，可以创建 Cookie 对象。例如：

```
Cookie c = new Cookie("url", "www.biancheng.net"); 
```

其中参数 name 为 Cookie 的名称，参数 value 为 Cookie 的值，name 与 value 的取值不能包含 `[ ] ( ) = , " / ? @ : ;`等字符

![image-20221017150235858](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017150235858.png)

### Cookie 相关的方法

**HttpServletResponse 接口和 HttpServletRequest 接口定义了与 Cookie 相关的方法**

| 方法                          | 描述                                             | 所属接口                               |
| ----------------------------- | ------------------------------------------------ | -------------------------------------- |
| void addCookie(Cookie cookie) | 用于在响应头中增加一个相应的 Set-Cookie 头字段。 | javax.servlet.http.HttpServletResponse |
| Cookie[] getCookies()         | 用于获取客户端提交的 Cookie。                    | javax.servlet.http.HttpServletRequest  |

![image-20221017150544216](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017150544216.png)

**javax.servlet.http.Cookie 类中提供了一系列获取或者设置 Cookie 的方法**

| 返回值类型 | 方法                      | 描述                                                         |
| ---------- | ------------------------- | ------------------------------------------------------------ |
| int        | getMaxAge()               | 用于获取指定 Cookie 的最大有效时间，以秒为单位。 默认情况下取值为 -1，表示该 Cookie 保留到浏览器关闭为止。 |
| String     | getName()                 | 用于获取 Cookie 的名称。                                     |
| String     | getPath()                 | 用于获取 Cookie 的有效路径。                                 |
| boolean    | getSecure()               | 如果浏览器只通过安全协议发送 Cookie，则返回 true；如果浏览器可以使用任何协议发送 Cookie，则返回 false。 |
| String     | getValue()                | 用于获取 Cookie 的值。                                       |
| int        | getVersion()              | 用于获取 Cookie 遵守的协议版本。                             |
| void       | setMaxAge(int expiry)     | 用于设置 Cookie 的最大有效时间，以秒为单位。 取值为正值时，表示 Cookie 在经过指定时间后过期。取值为负值时，表示 Cookie 不会被持久存储，在 Web 浏览器退出时删除。取值为 0 时，表示删除该 Cookie。 |
| void       | setPath(String uri)       | 用于指定 Cookie 的路径。                                     |
| void       | setSecure(boolean flag)   | 用于设置浏览器是否只能使用安全协议（如 HTTPS 或 SSL）发送 Cookie。 |
| void       | setValue(String newValue) | 用于设置 Cookie 的值。                                       |

### Cookie的创建

![image-20221017151047448](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017151047448.png)

### 服务器获取cookie

![image-20221017151129884](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017151129884.png)

### Cookie 的工具类：

```java
/**
 @author EddieZhang
 @create 2022-10-17 15:12
 */
public class CookieUtils {
    /**
     * 查找指定cookie的utils
     * @param name cookie的name
     * @param cookies 要查询的cookie数组
     * @return 查询到的对应name的cookie
     */
    public static Cookie findCookie(String name,Cookie[] cookies){
        if(name == null || cookies == null || cookies.length == 0){
            return null;
        }
        for (Cookie c:
             cookies) {
            if (name.equals(c.getName())){
                return c;
            }
        }
        return null;
    }
}
```

```java
Cookie[] cookies = req.getCookies();//通过request获取包含所有cookie的数组
Cookie searchCookie = CookieUtils.findCookie("key1", cookies);//通过定义的工具类查找是否存在指定name的cookie
if(searchCookie != null){
    resp.getWriter().write("找到了需要的 Cookie");
}
```

### Cookie 值的修改

方案一： 1、先创建一个要修改的同名（指的就是 key）的 Cookie 对象 2、在构造器，同时赋于新的 Cookie 值。 3、调用 response.addCookie( Cookie )

浏览器中收到响应后 发现有set-cookie响应头就查看是否已经存在这个cookie

有就修改 没有就创建

```java
// 方案一： 

// 1、先创建一个要修改的同名的 Cookie 对象 

// 2、在构造器，同时赋于新的 Cookie 值。 

Cookie cookie = new Cookie("key1","newValue1"); 

// 3、调用 response.addCookie( Cookie ); 通知 客户端 保存修改 

resp.addCookie(cookie);
```

方案二： 1、先查找到需要修改的 Cookie 对象 2、调用 setValue()方法赋于新的 Cookie 值。 3、调用 response.addCookie()通知客户端保存修改

```java
// 方案二：

// 1、先查找到需要修改的 Cookie 对象

Cookie cookie = CookieUtils.findCookie("key2", req.getCookies());

if (cookie != null) {
// 2、调用 setValue()方法赋于新的 Cookie 值。
cookie.setValue("newValue2");
// 3、调用 response.addCookie()通知客户端保存修改
resp.addCookie(cookie);
}
```

### Cookie 生命控制

Cookie 的生命控制指的是如何管理 Cookie 什么时候被销毁（删除）

**setMaxAge()** 

正数，表示在指定的秒数后过期 

负数，表示浏览器一关，Cookie 就会被删除（默认值是-1） 

零，表示马上删除 Cookie

```java
/**
* 设置存活 1 个小时的 Cooie
* @param req
* @param resp
* @throws ServletException
* @throws IOException
*/
protected void life3600(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
IOException {
Cookie cookie = new Cookie("life3600", "life3600");
cookie.setMaxAge(60 * 60); // 设置 Cookie 一小时之后被删除。无效
resp.addCookie(cookie);
resp.getWriter().write("已经创建了一个存活一小时的 Cookie");
}
/**
* 马上删除一个 Cookie
* @param req
* @param resp
* @throws ServletException
* @throws IOException
*/
protected void deleteNow(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
IOException {
// 先找到你要删除的 Cookie 对象
Cookie cookie = CookieUtils.findCookie("key4", req.getCookies());
if (cookie != null) {
// 调用 setMaxAge(0);
cookie.setMaxAge(0); // 表示马上删除，都不需要等待浏览器关闭
// 调用 response.addCookie(cookie);
resp.addCookie(cookie);
resp.getWriter().write("key4 的 Cookie 已经被删除");
}
}
/**
* 默认的会话级别的 Cookie
* @param req
* @param resp
* @throws ServletException
* @throws IOException
*/
protected void defaultLife(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
IOException {
Cookie cookie = new Cookie("defalutLife","defaultLife");
cookie.setMaxAge(-1);//设置存活时间
resp.addCookie(cookie);
}
```

### Cookie 有效路径 Path 的设置

Cookie 的 path 属性可以有效的过滤哪些 Cookie 可以发送给服务器。哪些不发。

path 属性是通过请求的地址来进行有效的过滤。

![image-20221017153202195](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017153202195.png)

```java
protected void testPath(HttpServletRequest req, HttpServletResponse resp) throws ServletException,IOException {
	Cookie cookie = new Cookie("path1", "path1");
	// getContextPath() ===>>>> 得到工程路径
	cookie.setPath( req.getContextPath() + "/abc" ); // ===>>>> /工程路径/abc
	resp.addCookie(cookie);
	resp.getWriter().write("创建了一个带有 Path 路径的 Cookie");
}
```

### Cookie 的使用细节

使用 Cookie 开发时需要注意以下细节：

- 一个 Cookie 只能标识一种信息，它至少包含一个名称（NAME）和一个值（VALUE）。
- **如果创建了一个 Cookie，并发送到浏览器，默认情况下它是一个会话级别的 Cookie。用户退出浏览器就被删除。如果希望将 Cookie 存到磁盘上，则需要调用 setMaxAge(int maxAge) 方法设置最大有效时间，以秒为单位。**
- 使用 setMaxAge(0) 手动删除 Cookie时，需要使用 setPath 方法指定 Cookie 的路径，且该路径必须与创建 Cookie 时的路径保持一致。

### Cookie 的缺点

Cookie 虽然可以解决服务器跟踪用户状态的问题，但是它具有以下缺点：

- 在 HTTP 请求中，Cookie 是**明文传递的**，容易泄露用户信息，**安全性不高**。
- **浏览器可以禁用 Cookie**，一旦被禁用，Cookie 将无法正常工作。
- Cookie 对象中**只能设置文本（字符串）信息**。
- **客户端浏览器保存 Cookie 的数量和长度是有限制的。**

## Session

### HTTP是无状态保存

HTTP（超文本传输协议）是一个基于请求与响应模式的无状态协议

![image-20220925235700203](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925235700203.png)

无状态主要指 2 点：

1. 协议对于事务处理没有记忆能力，服务器不能自动维护用户的上下文信息，无法保存用户状态；
2. 每次请求都是独立的，不会受到前面请求的影响，也不会影响后面的请求。


当浏览器发送 HTTP 请求到服务器时，服务器会响应客户端的请求，但当同一个浏览器再次发送请求到该服务器时，服务器并不知道它就是刚才那个浏览器，即 HTTP 协议的请求无法保存用户状态。

通常情况下，用户通过浏览器访问 Web 应用时，服务器都需要保存和跟踪用户的状态。例如，用户在某购物网站结算商品时，Web 服务器必须根据请求用户的身份，找到该用户所购买的商品。由于 HTTP 协议是无协议的，无法保存和跟踪用户状态，所以需要其他的方案来解决问此题，它就是会话技术。

### 会话技术

从打开浏览器访问某个网站，到关闭浏览器的过程，称为一次会话。会话技术是指在会话中，帮助服务器记录用户状态和数据的技术。

常用的会话技术分为两种：

1. Cookie ：客户端会话技术
2. Session ：服务端会话技术

### Session

**Session 是服务器端会话技术**。当浏览器访问 Web 服务器的资源时，服务器可以为每个用户浏览器创建一个 Session 对象，**每个浏览器独占一个 Session 对象**。

由于每个浏览器独占一个 Session，所以用户在访问服务器的资源时，可以把数据保存在各自的 Session 中。当用户再次访问该服务器中的其它资源时，其它资源可以从 Session 中取出数据，为用户服务。

![image-20221017153743082](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017153743082.png)

### Session 的工作原理

![image-20221017153629052](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017153629052.png)

注意：

- **流程中的 Cookie 是容器自动生成的，它的 maxAge 属性取值为 -1，表示仅当前浏览器有效。**
- 浏览器关闭时，对应的 Session 并没有失效，但此时与此 Session 对应的 Cookie 已失效，导致浏览器无法再通过 Cookie 获取服务器端的 Session 对象。
- **同一浏览器的不同窗口共享同一 Session 对象**，但不同浏览器窗口之间不能共享 Session 对象。

### Session API

Session 对象由服务器创建，通过 HttpServletRequest.getSession() 方法可以获得 HttpSession 对象，例如：

```java
//获取session对象
HttpSession session=request.getSession();
```

| 返回值类型     | 方法                                 | 描述                                                         |
| -------------- | ------------------------------------ | ------------------------------------------------------------ |
| long           | getCreationTime()                    | 返回创建 Session 的时间。                                    |
| String         | getId()                              | 返回获取 Seesion 的唯一的 ID。                               |
| long           | getLastAccessedTime()                | 返回客户端上一次发送与此 Session 关联的请求的时间。          |
| int            | getMaxInactiveInterval()             | 返回在无任何操作的情况下，Session 失效的时间，以秒为单位。   |
| ServletContext | getServletContext()                  | 返回 Session 所属的 ServletContext 对象。                    |
| void           | invalidate()                         | 使 Session 失效。                                            |
| void           | setMaxInactiveInterval(int interval) | 指定在无任何操作的情况下，Session 失效的时间，以秒为单位。负数表示 Session 永远不会失效。 |

### 创建 Session 和获取(id 号,是否为新)

如何创建和获取 Session。

它们的 API 是一样的。 

**request.getSession()** 

**第一次调用是：创建 Session 会话** 

**之后调用都是：获取前面创建好的 Session 会话对象。** 

isNew(); 判断到底是不是刚创建出来的（新的） true 表示刚创建 false 表示获取之前创建 

getId() 得到 Session 的会话 id 值;每个会话都有一个身份证号。也就是 ID 值。而且这个 ID 是唯一的。 

### Session域对象

| 返回值类型  | 方法                                | 描述                                                         |
| ----------- | ----------------------------------- | ------------------------------------------------------------ |
| void        | setAttribute(String name, Object o) | 把一个 Java 对象与一个属性名绑定，并将它作为一个属性存放到 Session 对象中。 参数 name 为属性名，参数 object 为属性值。 |
| Object      | getAttribute(String name)           | 根据指定的属性名 name，返回 Session 对象中对应的属性值。     |
| void        | removeAttribute(String name)        | 从 Session 对象中移除属性名为 name 的属性。                  |
| Enumeration | getAttributeNames()                 | 用于返回 Session 对象中的所有属性名的枚举集合。              |

Session 、request 以及 ServletContext 合称为 Servlet 的三大域对象，它们都能保存和传递数据，但是三者也存在许多差异，如下表。

| 不同     | request                                                      | Session                                                      | ServletContext                                               |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 类型     | javax.servlet.http.HttpServletRequest                        | javax.servlet.http.HttpSession                               | javax.servlet.ServletContext                                 |
| 创建     | 客户端向容器发送请求时创建。                                 | 容器第一次调用 getSession() 方法时创建。                     | Servlet 容器启动时创建。                                     |
| 销毁     | 容器对这次请求做出响应后销毁。                               | Session 销毁的时机： 关闭服务器或应用被卸载。Session 过期，默认为 30 分钟。手动调用 session.invalidate() 方法进行销毁。 | 容器关闭或者 Web 应用被移除时销毁。                          |
| 有效范围 | 只对当前请求涉及的 Servlet 有效。                            | Session 对本次会话期间的所有 Servlet 都有效。                | 对整个 Web 应用内的所有 Servlet 有效。                       |
| 数量     | Web 应用中的所有 Servlet 实例都可以有多个 request 对象。     | Web 应用中可以有多个 Session，多个 Servet 实例可以共享同一 Session 对象。 | 在整个 Web 应用中只有一个 Context 对象。                     |
| 数据共享 | 每一次请求都是一个新的 request 对象。 通过和请求转发的配合使用可以实现一次请求中 Web 组件之间共享的数据。 | 每一次会话都是一个新的 Session 对象。 通过 Session 域对象可以实现一次会话中的多个请求之间共享数据。 | 在一个应用中有且只有一个 Context 对象，作用于整个 Web 应用，可以实现多次会话之间的数据共享。 |

**Session 域数据的存取**

```java
/**
* 往 Session 中保存数据
* @param req
* @param resp
* @throws ServletException
* @throws IOException
*/
protected void setAttribute(HttpServletRequest req, HttpServletResponse resp) throws ServletException,IOException {
    req.getSession().setAttribute("key1", "value1");
    resp.getWriter().write("已经往 Session 中保存了数据");
}
/**
* 获取 Session 域中的数据
* @param req
* @param resp
* @throws ServletException
* @throws IOException
*/
protected void getAttribute(HttpServletRequest req, HttpServletResponse resp) throws ServletException,IOException {
    Object attribute = req.getSession().getAttribute("key1");
    resp.getWriter().write("从 Session 中获取出 key1 的数据是：" + attribute);
}
```

### Session 生命周期控制

![image-20221017160537786](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017160537786.png)

### **设置 Session 过期时间**

**session的超时时间指的是客户端两次请求之间最大的间隔时长**

![image-20221017160607544](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017160607544.png)

![image-20221017160636145](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017160636145.png)

### Session 与 Cookie 对比

Session 和 Cookie 都属于会话技术，都能帮助服务器保存和跟踪用户状态，但两者也存在差异，如下表。

| 不同点                 | Cookie                                                       | Session                                                      |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 存储位置不同           | Cookie 将数据存放在客户端浏览器内存中或硬盘上。              | Session 将数据存储在服务器端。                               |
| 大小和数量限制不同     | 浏览器对 Cookie 的大小和数量有限制。                         | Session 的大小和数量一般不受限制。                           |
| 存放数据类型不同       | Cookie 中保存的是字符串。                                    | Session 中保存的是对象。                                     |
| 安全性不同             | Cookie 明文传递，安全性低，他人可以分析存放在本地的 Cookie 并进行 Cookie 欺骗。 | Session 存在服务器端，安全性较高。                           |
| 对服务器造成的压力不同 | Cookie 保存在客户端，不占用服务器资源。                      | Session 保存在服务端，每一个用户独占一个 Session。若并发访问的用户十分多，就会占用大量服务端资源。 |
| 跨域支持上不同         | Cookie 支持跨域名访问。                                      | Session 不支持跨域名访问。                                   |

### 浏览器和 Session 之间关联的技术内幕

Session 技术，底层其实是基于 Cookie 技术来实现的。

![image-20221017161304629](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221017161304629.png)



## 三大域对象

Session 、request 以及 ServletContext 合称为 Servlet 的三大域对象，它们都能保存和传递数据，但是三者也存在许多差异，如下表。

| 不同     | request                                                      | Session                                                      | ServletContext                                               |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 类型     | javax.servlet.http.HttpServletRequest                        | javax.servlet.http.HttpSession                               | javax.servlet.ServletContext                                 |
| 创建     | 客户端向容器发送请求时创建。                                 | 容器第一次调用 getSession() 方法时创建。                     | Servlet 容器启动时创建。                                     |
| 销毁     | 容器对这次请求做出响应后销毁。                               | Session 销毁的时机： 关闭服务器或应用被卸载。Session 过期，默认为 30 分钟。手动调用 session.invalidate() 方法进行销毁。 | 容器关闭或者 Web 应用被移除时销毁。                          |
| 有效范围 | 只对当前请求涉及的 Servlet 有效。                            | Session 对本次会话期间的所有 Servlet 都有效。                | 对整个 Web 应用内的所有 Servlet 有效。                       |
| 数量     | Web 应用中的所有 Servlet 实例都可以有多个 request 对象。     | Web 应用中可以有多个 Session，多个 Servet 实例可以共享同一 Session 对象。 | 在整个 Web 应用中只有一个 Context 对象。                     |
| 数据共享 | 每一次请求都是一个新的 request 对象。 通过和请求转发的配合使用可以实现一次请求中 Web 组件之间共享的数据。 | 每一次会话都是一个新的 Session 对象。 通过 Session 域对象可以实现一次会话中的多个请求之间共享数据。 | 在一个应用中有且只有一个 Context 对象，作用于整个 Web 应用，可以实现多次会话之间的数据共享。 |

## Filter过滤器

### **Filter 过滤器**

**是服务端三大组件之一**

![image-20221018234814598](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221018234814598.png)



**Filter过滤器是JavaEE的规范 即接口**

**作用是     拦截请求☆     过滤响应**

拦截请求的常用场景：

1.权限检查

2.日记操作

3.事务管理

​	...

### Filter的使用

#### Filter工作流程

![image-20221018235257028](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221018235257028.png)

#### 运用Filter

![image-20221018235620883](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221018235620883.png)

1.建立Filter过滤器的包 存放创建的Filter过滤器（可以创建多个Filter）

2.Filter类要implements （package javax.servlet） 下的Filter接口并实现其方法

3.其中最为重要的方法是doFilter（）专门用于拦截请求可以做权限检查

4.在web.xml文件中配置Filter

![image-20221019001448269](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221019001448269.png)

**Filter 的拦截路径**(三种匹配方式)

Filter 过滤器它只关心请求的地址是否匹配，不关心请求的资源是否存在！！！

```xml
--精确匹配
<url-pattern>/target.jsp</url-pattern>
以上配置的路径，表示请求地址必须为：http://ip:port/工程路径/target.jsp 

--目录匹配
<url-pattern>/admin/*</url-pattern>
以上配置的路径，表示请求地址必须为：http://ip:port/工程路径/admin/* 

--后缀名匹配
<url-pattern>*.html</url-pattern>
以上配置的路径，表示请求地址必须以.html 结尾才会拦截到
<url-pattern>*.do</url-pattern>
以上配置的路径，表示请求地址必须以.do 结尾才会拦截到
<url-pattern>*.action</url-pattern>
以上配置的路径，表示请求地址必须以.action 结尾才会拦截到

```

**运用Filter实例**

1.建立Filter过滤器的包 存放创建的Filter过滤器（可以创建多个Filter）

2.Filter类要implements （package javax.servlet） 下的Filter接口并实现其方法

3.其中最为重要的方法是doFilter（）专门用于拦截请求可以做权限检查

4.在web.xml文件中配置Filter

完成以上Filter定义后

在doFilter()方法中定义拦截请求 做权限检查

**执行 filterChain.doFilter(servletRequest,servletResponse);让程序继续往下访问用户的目标资源**

```java
public class AdminFilter implements Filter {
/**
* doFilter 方法，专门用于拦截请求。可以做权限检查
*/
@Override
public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
	HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
	HttpSession session = httpServletRequest.getSession();
	Object user = session.getAttribute("user");
	// 如果等于 null，说明还没有登录
	if (user == null) {
	servletRequest.getRequestDispatcher("/login.jsp").forward(servletRequest,servletResponse);
	return;
	} else {
	// 让程序继续往下访问用户的目标资源
	filterChain.doFilter(servletRequest,servletResponse);
	}
	}
}
```



### Filter的生命周期

**1.构造器方法** 	（由服务器调用创建Filter）

**2.init初始化方法**	（由服务器调用初始化方法初始化Filter）

**3.doFilter过滤方法**	（每次拦截到请求就会执行）

**4.destroy销毁**	（当web工程停止 就会执行destory方法 销毁Filter过滤器）

```java
public class Filter1 implements Filter {
    /*
    服务器会调用Filter的构造器方法创建Filter
    在创建Filter的同时会创建一个FilterConfig对象将读取web.xml文件中的Filter配置信息封装成FilterConfig对象
    将封装了Filter配置信息的FilterConfig对象作为参数传进init()方法初始化Filter
    */
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        Filter.super.init(filterConfig);
    }

    /*
    每次拦截到请求就会执行doFilter过滤方法
    */
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {

    }

    /*
    当停止web工程的时候就会执行destory()方法销毁Filter
    */
    @Override
    public void destroy() {
        Filter.super.destroy();
    }
}
```

### FilterConfig类

封装了Filter的配置信息（读取web.xml中的配置信息并封装为FilterConfig）

服务器会调用Filter的构造器方法创建Filter
**在创建Filter的同时会创建一个FilterConfig对象将读取web.xml文件中的Filter配置信息封装成FilterConfig对象**
将封装了Filter配置信息的FilterConfig对象作为参数传进init()方法初始化Filter

![image-20221019002412699](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221019002412699.png)

```java
	/*
    在创建Filter的同时会创建一个FilterConfig对象将读取web.xml文件中的Filter配置信息封装成FilterConfig对象
    将封装了Filter配置信息的FilterConfig对象作为参数传进init()方法初始化Filter
    */
@Override
    public void init(FilterConfig filterConfig) throws ServletException {
        Filter.super.init(filterConfig);
    }
```

### FilterChain过滤器链

FilterChain 就是过滤器链（多个过滤器如何一起工作）

过滤器的工作顺序是与web.xml中Filter配置顺序对应

![image-20221019003147025](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221019003147025.png)

![image-20221019003002849](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221019003002849.png)

## JSON

SON，全称是 JavaScript Object Notation，即 JavaScript对象标记法

JSON是一种轻量级（Light-Meight)、基于文本的(Text-Based)、可读的(Human-Readable)格式

**数据交换格式**

### JSON 的语法规则

![image-20221029093713034](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029093713034.png)

### JSON的解析和生成（JSON 和 JS 对象互转）

- **在JavaScript中，有两个方法与此相关: `JSON.parse`和 `JSON.stringify` 。**

- 要实现从**JSON字符串**转换为**JS对象**，使用 `JSON.parse()` 方法：

  要实现从**JS对象**转换为**JSON字符串**，使用 `JSON.stringify()` 方法：

![image-20221029100909731](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029100909731.png)

### JavaBean和JSON的互转

![image-20221029101729247](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029101729247.png)

### List集合和JSON对象的相互转换

![image-20221029104350347](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029104350347.png)

![image-20221029105234082](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029105234082.png)

```java
public class GenericTest {
    public static void main(String[] args) {
        Class<?> aClass = null;
        try {
            aClass = Class.forName("com.eddie.domain.Son");
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }

        Type genericSuperclass = aClass.getGenericSuperclass();
        System.out.println(genericSuperclass);//com.eddie.domain.Person<com.eddie.domain.Son, java.lang.Integer, java.lang.Boolean>
        Class<?> superclass = aClass.getSuperclass();
        System.out.println(superclass);//class com.eddie.domain.Person

        ParameterizedType parameterizedType = (ParameterizedType)genericSuperclass;
        System.out.println(parameterizedType);//com.eddie.domain.Person<com.eddie.domain.Son, java.lang.Integer, java.lang.Boolean>
        System.out.println(parameterizedType.getActualTypeArguments()[0]);//class com.eddie.domain.Son
        System.out.println(parameterizedType.getActualTypeArguments()[1]);//class java.lang.Integer
        System.out.println(parameterizedType.getActualTypeArguments()[2]);//class java.lang.Boolean
    }
}
```

### Map和JSON对象的相互转换(泛型相关参考List)

```java
/**
 * Map和JSON对象的相互转换
 */
@Test
public void test3(){
    Gson gson = new Gson();//创建Gson对象

    Map<Integer,Person> map = new HashMap<>();
    map.put(1,new Person(21, "EddieZhang", new BigDecimal(100500), "Java"));
    map.put(1,new Person(33, "Irving", new BigDecimal(1000000500), "Basketball"));

    //Map集合转为JSON对象
    String toJson = gson.toJson(map);
    System.out.println(toJson);//{"1":{"age":33,"name":"Irving","salary":1000000500,"major":"Basketball"}}

    //将JSON对象转换成Map集合
    Object fromJson = gson.fromJson(toJson, new TypeToken<Map<Integer, Person>>() {}.getType());//参数为JSON对象 以及要转换成什么类型的Java对象
    System.out.println(fromJson);//{1=Person{age=33, name='Irving', salary=1000000500, major='Basketball'}}
}
```

## AJAX

![image-20221029105534055](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029105534055.png)

ajax 全名 async javascript and XML(异步JavaScript和XML)

是前后台交互的能⼒ 也就是我们客户端给服务端发送消息的⼯具，以及接受响应的⼯具

AJAX 不是新的编程语言，而是一种使用现有标准的新方法。

AJAX 是**与服务器交换数据**并**局部更新部分网页**的艺术，在不重新加载整个页面的情况下。

是⼀个 **默认异步执⾏**机制的功能,AJAX分为同步（async = false）和异步（async = true）

**-同步请求？(false)**

```
 同步请求是指当前发出请求后，浏览器什么都不能做，
 必须得等到请求完成返回数据之后，才会执行后续的代码，
 相当于生活中的排队，必须等待前一个人完成自己的事物，后一个人才能接着办。
 也就是说，当JS代码加载到当前AJAX的时候会把页面里所有的代码停止加载，页面处于一个假死状态，
 当这个AJAX执行完毕后才会继续运行其他代码页面解除假死状态
```

**异步请求？(默认:true)**

```
默认异步：异步请求就当发出请求的同时，浏览器可以继续做任何事，
Ajax发送请求并不会影响页面的加载与用户的操作，相当于是在两条线上，各走各的，互不影响。
一般默认值为true，异步。异步请求可以完全不影响用户的体验效果，
无论请求的时间长或者短，用户都在专心的操作页面的其他内容，并不会有等待的感觉。
```

### AJAX 的优势

- 不需要插件的⽀持，**原⽣ js 就可以使⽤**
- ⽤户体验好（`不需要刷新⻚⾯就可以更新数据`）
- `减轻服务端和带宽的负担`
- 缺点：搜索引擎的⽀持度不够，因为数据都不在⻚⾯上，搜索引擎搜索不到

### AJAX 的操作流程

![image-20221029105814215](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029105814215.png)

具体操作流程：

首先通过PHP页面将数据库中的数据取出
取出后转成json格式的字符串，后利用ajax把字符串返还给前台
再利用json.parse解析通过循环添加到页面上
那么反之，前端的数据可以利用ajax提交到后台
但是后台是没有办法直接把这些数据插入到数据库中，所以要先提交到PHP页面上
最后再由PHP将数据插入到数据库中

## 跨域问题

[跨域问题及CORS解决跨域问题方法 - 腾讯云开发者社区-腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1804537)

[JAVA | Java 解决跨域问题 - 双鬼带单 - 博客园 (cnblogs.com)](https://www.cnblogs.com/zyndev/p/13697313.html)

![image-20221222171545842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221222171545842.png)

![image-20221222171556767](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221222171556767.png)

==覆盖默认的CorsWebFilter来解决该问题==

```java
/** TODO 配置CorsWebFilter 解决跨域问题
 @author EddieZhang
 @create 2022-12-20 9:16
 */
@Configuration
public class CorsWebFilterConfig {

    @Bean
    public CorsWebFilter corsWebFilter(){
        UrlBasedCorsConfigurationSource urlBasedCorsConfigurationSource = new UrlBasedCorsConfigurationSource();
        CorsConfiguration corsConfiguration = new CorsConfiguration();
        corsConfiguration.addAllowedHeader("*");//放行全部原始头信息
        corsConfiguration.addAllowedMethod("*");//允许所有请求方法跨域调用
        corsConfiguration.addAllowedOrigin("*");//允许所有域名进行跨域调用
        corsConfiguration.setAllowCredentials(true);//允许跨越发送cookie
        urlBasedCorsConfigurationSource.registerCorsConfiguration("/**",corsConfiguration);
        return new CorsWebFilter(urlBasedCorsConfigurationSource);
    }
}
```

**同时要注意cookie的使用问题**

![image-20221222172201341](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221222172201341.png)

## SSO

![image-20230612104217742](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612104217742.png)

> 单点登录（SSO）是一种身份验证解决方案，可让用户通过一次性用户身份验证登录多个应用程序和网站。鉴于当今的用户经常直接从其浏览器访问应用程序，因此组织正在优先考虑改善安全性和用户体验的访问管理策略。SSO 兼具这两方面的优点，因为一旦验证身份，用户就可以访问所有受密码保护的资源，而无需重复登录。
>
> SSO 流程如下：
>
> 1. 当用户登录应用程序时，应用程序会生成 SSO 令牌并向 SSO 服务发送身份验证请求。 
> 2. 该服务会检查用户之前是否在系统中进行了身份验证。如果是，它会向应用程序发送一个身份验证确认响应，以授予用户访问权限。 
> 3. 如果用户没有经过验证的凭证，SSO 服务会将用户重定向到中央登录系统并提示用户提交其用户名和密码。
> 4. 提交后，服务会验证用户凭证并将肯定响应发送到应用程序。 
> 5. 否则，用户会收到错误消息并且必须重新输入凭证。多次尝试登录失败可能会导致服务阻止用户在固定的时间段内进行更多尝试。 
>
> 
>
> SSO 在应用程序或服务与外部服务提供商（也称为身份提供者（IdP））之间建立信任。这是通过在应用程序和集中式 SSO 服务之间执行的一系列身份验证、验证和通信步骤来实现的。SSO 解决方案中的重要组件如下所示。
>
> ##### **SSO 服务**
>
> SSO 服务是用户登录时应用程序依赖的中心服务。如果未经身份验证的用户请求访问应用程序，应用程序会将他们重定向到 SSO 服务。然后，该服务对用户进行身份验证并将用户重定向回原始应用程序。该服务通常在专用的 SSO 策略服务器上运行。
>
> ##### **SSO 令牌**
>
> SSO 令牌是包含用户识别信息的数字文件，例如用户名或电子邮件地址。当用户请求访问应用程序时，应用程序会与 SSO 服务交换 SSO 令牌以对用户进行身份验证。 

![image-20230612104840665](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612104840665.png)

![image-20230612104924189](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612104924189.png)







![image-20230612104430734](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612104430734.png)

1. 用户访问系统1的受保护资源，系统1发现用户未登录，跳转至sso认证中心，并将自己的地址作为参数
2. sso认证中心发现用户未登录，将用户引导至登录页面（带系统1地址）
3. 用户输入用户名密码提交登录申请
4. sso认证中心校验用户信息，创建用户与sso认证中心之间的会话，称为全局会话（这时该会话信息保存到cookie中），同时创建授权令牌
5. sso认证中心带着令牌跳转到最初的请求地址（系统1）
6. 系统1拿到令牌，去sso认证中心校验令牌是否有效
7. sso认证中心校验令牌，返回有效，注册系统1
8. 系统1使用该令牌创建与用户的会话，称为局部会话(seesion)，返回受保护资源
9. 用户访问系统2的受保护资源
10. 系统2发现用户未登录，跳转至sso认证中心，并将自己的`地址`和之前和`sso认证中心的会话cookie信`息作为参数
11. sso认证中心发现用户已登录，跳转回系统2的地址，并附上令牌
12. 系统2拿到令牌，去sso认证中心校验令牌是否有效
13. sso认证中心校验令牌，返回有效，注册系统2
14. 系统2使用该令牌创建与用户的局部会话，返回受保护资源

## JWT

### **Specification**

[JWT 超详细分析 | Laravel China 社区 (learnku.com)](https://learnku.com/articles/17883)

> **JWT** 全称 **JSON Web Tokens** ，是一种规范化的 token。可以理解为对 token 这一技术提出一套规范，是在 **[RFC 7519](https://tools.ietf.org/html/rfc7519)** 中提出的。
>
> - 防 CSRF
> - 适合移动应用
> - 无状态
> - 编码数据
>
> 前两个是 token 的优势，后两个是 JWT 独特的优势。
>
> ![image-20230612115929065](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612115929065.png)
>
> 
>
> 一个 JWT token 是一个字符串，它由三部分组成，头部、载荷与签名，中间用 `.` 分隔，例如：`xxxxx.yyyyy.zzzzz`
>
> ![image-20230612115656090](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612115656090.png)
>
> ![image-20230612115615549](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612115615549.png)
>
> 
>
> ![image-20230612115332979](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612115332979.png)

### Header

Header 通常由两部分组成：

- `typ`（Type）：令牌类型，也就是 JWT。
- `alg`（Algorithm）：签名算法，比如 HS256。

示例：



```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

JSON 形式的 Header 被转换成 Base64 编码，成为 JWT 的第一部分。

### Payload

Payload 也是 JSON 格式数据，其中包含了 Claims(声明，包含 JWT 的相关信息)。

Claims 分为三种类型：

- **Registered Claims（注册声明）**：预定义的一些声明，建议使用，但不是强制性的。
- **Public Claims（公有声明）**：JWT 签发方可以自定义的声明，但是为了避免冲突，应该在 [IANA JSON Web Token Registryopen in new window](https://www.iana.org/assignments/jwt/jwt.xhtml) 中定义它们。
- **Private Claims（私有声明）**：JWT 签发方因为项目需要而自定义的声明，更符合实际项目场景使用。

下面是一些常见的注册声明：

- `iss`（issuer）：JWT 签发方。
- `iat`（issued at time）：JWT 签发时间。
- `sub`（subject）：JWT 主题。
- `aud`（audience）：JWT 接收方。
- `exp`（expiration time）：JWT 的过期时间。
- `nbf`（not before time）：JWT 生效时间，早于该定义的时间的 JWT 不能被接受处理。
- `jti`（JWT ID）：JWT 唯一标识。

示例：



```json
{
  "uid": "ff1212f5-d8d1-4496-bf41-d2dda73de19a",
  "sub": "1234567890",
  "name": "John Doe",
  "exp": 15323232,
  "iat": 1516239022,
  "scope": ["admin", "user"]
}
```

Payload 部分默认是不加密的，**一定不要将隐私信息存放在 Payload 当中！！！**

JSON 形式的 Payload 被转换成 Base64 编码，成为 JWT 的第二部分。

### Signature

Signature 部分是对前两部分的签名，作用是防止 JWT（主要是 payload） 被篡改。

这个签名的生成需要用到：

- Header + Payload。
- 存放在服务端的密钥(一定不要泄露出去)。
- 签名算法。

签名的计算公式如下：



```text
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

算出签名以后，把 Header、Payload、Signature 三个部分拼成一个字符串，每个部分之间用"点"（`.`）分隔，这个字符串就是 JWT 。

### JWT decoder

[JSON Web Tokens - jwt.io](https://jwt.io/)

![image-20230612114617061](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230612114617061.png)


# JavaEE三层架构
**表示层（UI）-------------表示层（web层）**

web层：与客户端交互，包括获取用户请求，传递数据，封装数据，展示数据

**业务逻辑层（BLL）-----业务逻辑层（service层）**

service层：复杂的业务处理，包括各种实际的逻辑运算

**数据访问层（DAL）-----数据访问层（dao层）**

dao层：与数据库进行交互，与数据库相关的代码在此处实现

![image-20220930110347859](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930110347859.png)

![image-20220930105933905](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930105933905.png)

## **web 层** 

com.atguigu.web/servlet/controller 

## **service 层** 

com.atguigu.service Service 接口包 

com.atguigu.service.impl Service 接口实现类 

## **dao 持久层** 

com.atguigu.dao Dao 接口包 

com.atguigu.dao.impl Dao 接口实现类 

实体 bean 对象 com.atguigu.pojo/entity/domain/bean JavaBean 类 

## 测试包 

com.atguigu.test/junit 

## 工具类 

com.atguigu.util
