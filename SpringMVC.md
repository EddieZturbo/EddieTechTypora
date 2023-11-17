





# SpringMVC

**针对上层的Web应用**，SpringMVC诞生了，它也是Spring技术栈中最为重要的一个框架。

![image-20221027152017484](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027152017484.png)
**什么是MVC**

![image-20221027152118596](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027152118596.png)

用一种业务逻辑、数据、界面显示分离的方法，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。MVC被独特的发展起来用于映射传统的输入、处理和输出功能在一个逻辑的图形化用户界面的结构中

![image-20221027152137217](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027152137217.png)

**Model**（模型）是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据。

**View**（视图）是应用程序中处理数据显示的部分。通常视图是依据模型数据创建的。

**Controller**（控制器）是应用程序中处理用户交互的部分。通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据。

**什么是Spring MVC**

![image-20221027152240923](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027152240923.png)

**相关特性如下**：

- 让我们能非常简单的设计出干净的Web 层和薄薄的Web 层；
- 进行更简洁的Web 层的开发；
- 天生与Spring 框架集成（如IoC 容器、AOP 等）；
- 提供强大的约定大于配置的契约式编程支持；
- 能简单的进行Web 层的单元测试；
- 支持灵活的URL 到页面控制器的映射；
- 非常容易与其他视图技术集成，如 Velocity、FreeMarker 等等，因为模型数据不放在特定的 API 里，而是放在一个 Model 里（Map 数据结构实现，因此很容易被其他框架使用）；
- 非常灵活的数据验证、格式化和数据绑定机制，能使用任何对象进行数据绑定，不必实现特定框架的API；
- 提供一套强大的JSP 标签库，简化JSP 开发；
- 支持灵活的本地化、主题等解析；
- 更加简单的异常处理；
- 对静态资源的支持；
- 支持Restful 风格。

**SpringMVCh核心框架**

![image-20221027152440555](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027152440555.png)

具体流程：

（1）首先浏览器发送请求——>DispatcherServlet，前端控制器收到请求后自己不进行处理，而是委托给其他的解析器进行处理，作为统一访问点，进行全局的流程控制；

（2）DispatcherServlet——>HandlerMapping，处理器映射器将会把请求映射为HandlerExecutionChain对象（包含一个Handler处理器对象、多个HandlerInterceptor拦截器）对象；

（3）DispatcherServlet——>HandlerAdapter，处理器适配器将会把处理器包装为适配器，从而支持多种类型的处理器，即适配器设计模式的应用，从而很容易支持很多类型的处理器；

（4）HandlerAdapter——>调用处理器相应功能处理方法，并返回一个ModelAndView对象（包含模型数据、逻辑视图名）；

（5）ModelAndView对象（Model部分是业务对象返回的模型数据，View部分为逻辑视图名）——> ViewResolver， 视图解析器将把逻辑视图名解析为具体的View；

（6）View——>渲染，View会根据传进来的Model模型数据进行渲染，此处的Model实际是一个Map数据结构；

（7）返回控制权给DispatcherServlet，由DispatcherServlet返回响应给用户，到此一个流程结束。

完整的（**Filter(ServletFilter)**和考虑国际化(Local)**LocaleResolver**）

![image-20221027153135557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027153135557.png)

![image-20221030165943940](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030165943940.png)

![image-20221030170235874](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030170235874.png)

```
1、SpringMVC常用组件
DispatcherServlet：前端控制器，不需要工程师开发，由框架提供
作用：统一处理请求和响应，整个流程控制的中心，由它调用其它组件处理用户的请求
HandlerMapping：处理器映射器，不需要工程师开发，由框架提供
作用：根据请求的url、method等信息查找Handler，即控制器方法
Handler：处理器，需要工程师开发
作用：在DispatcherServlet的控制下Handler对具体的用户请求进行处理
HandlerAdapter：处理器适配器，不需要工程师开发，由框架提供
作用：通过HandlerAdapter对处理器（控制器方法）进行执行
ViewResolver：视图解析器，不需要工程师开发，由框架提供
作用：进行视图解析，得到相应的视图，例如：ThymeleafView、InternalResourceView、RedirectView
View：视图
作用：将模型数据通过页面展示给用户
```

![image-20221030170127208](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030170127208.png)

![image-20221030170156034](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030170156034.png)

## @RequestMapping注解

@RequestMapping注解的作用就是**将请求和处理请求的控制器方法关联 起来**，**建立映射关系**。 SpringMVC 接收到指定的请求，就会来**找到在映射关系中对应的**

**控制器方法**来处理这个请求。

![image-20221027155137667](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027155137667.png)

![image-20221104080050677](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104080050677.png)

### @RequestMapping的value属性

@RequestMapping注解的value属性**通过请求的请求地址匹配请求映射**

@RequestMapping注解的value属性是一个**字符串类型的数组**，表示**该请求映射能够匹配多个请求地址 所对应的请求**

@RequestMapping注解的value属性**必须设置**，至少通过请求地址匹配请求映射

@RequestMapping注解的value属性是默认的 **当只设置value属性时value可以省略** 直接指定请求地址即可

![image-20221027155359619](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027155359619.png)

### @RequestMapping的method属性

@RequestMapping注解的method属性**通过请求的请求方式（get或post）匹配请求映射**

@RequestMapping注解的method属性是一个RequestMethod类型的数组，表示该请求映射能够匹配 多种请求方式的请求

若当前请求的请求地址满足请求映射的value属性，但是**请求方式不满足method属性，则浏览器报错 405：Request method 'POST' not supported**

**当不指定method时表示匹配任意所有的请求method**
**当指定method时表示匹配指定的请求method**

![image-20221027160203014](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027160203014.png)

### @RequestMapping的params属性（了解）

@RequestMapping注解的params属性**通过请求的请求参数匹配请求映射** 

@RequestMapping注解的params属性是一个字符串类型的数组，可以通过四种表达式设置请求参数 和请求映射的匹配关系 

"param"：要求请求映射所匹配的请求必须携带param请求参数 

"!param"：要求请求映射所匹配的请求必须不能携带param请求参数 

"param=value"：要求请求映射所匹配的请求必须携带param请求参数且param=value 

"param!=value"：要求请求映射所匹配的请求必须携带param请求参数但是param!=value

若当前请求满足@RequestMapping注解的value和method属性，但是**不满足params属性，此时 页面回报错400：**

![image-20221027162057554](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027162057554.png)

```java
@RequestMapping(
value = {"/testRequestMapping", "/test"}
,method = {RequestMethod.GET, RequestMethod.POST}
,params = {"username","password!=123456"}
)
public String testRequestMapping(){
return "success";
}
```

```html
<a th:href="@{/test(username='admin',password=123456)">测试@RequestMapping的params属性-->/test</a><br>
<!--此时是不满足的-->
<!--
注：
若当前请求满足@RequestMapping注解的value和method属性，但是不满足params属性，此时
页面回报错400：Parameter conditions "username, password!=123456" not met for actual
request parameters: username={admin}, password={123456}
-->
```

### @RequestMapping注解的headers属性（了解）

@RequestMapping注解的headers属性**通过请求的请求头信息匹配请求映射** 

@RequestMapping注解的headers属性是一个字符串类型的数组，可以通过四种表达式设置请求头信 息和请求映射的匹配关系 

"header"：要求请求映射所匹配的请求必须携带header请求头信息 

"!header"：要求请求映射所匹配的请求必须不能携带header请求头信息 

"header=value"：要求请求映射所匹配的请求必须携带header请求头信息且header=value 

"header!=value"：要求请求映射所匹配的请求必须携带header请求头信息且header!=value 

若当前请求满足@RequestMapping注解的value和method属性，但是**不满足headers属性，此时页面 显示404错误，即资源未找到**

### SpringMVC支持ant风格的路径

```xml
？：表示任意的单个字符(指要有一个任意的单个字符 可以是任意但一定要有一个)
*：表示任意的0个或多个字符(指可以有任意的字符且可有可无)
**：表示任意的一层或多层目录
注意：在使用**时，只能使用/**/xxx的方式(要在目录的中间部分使用
```

### SpringMVC支持路径中的占位符（重点）

原始方式：/deleteUser?id=1 

rest方式：/deleteUser/1 

SpringMVC路径中的占位符常用于**RESTful风格**中，当请求路径中将某些数据通过路径的方式传输到服 务器中，就可以在相应的@RequestMapping注解的value属性中通过占位符{xxx}表示传输的数据，在 **通过@PathVariable注解，将占位符所表示的数据赋值给控制器方法的形参**

![image-20221027163300977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027163300977.png)

## SpringMVC获取请求参数

### 通过ServletAPI获取（了解）

**将HttpServletRequest作为控制器方法的形参**，此时HttpServletRequest类型的参数表示封装了当前请求的请求报文的对象

```java
@RequestMapping("/testParam")
public String testParam(HttpServletRequest request){
    String username = request.getParameter("username");
    String password = request.getParameter("password");
    System.out.println("username:"+username+",password:"+password);
    return "success";
}
```

### 通过控制器方法的形参获取请求参数

注意 此时的**形参的名必须和参数的名保持一致** 若不一致需使用@RequestParam

在控制器方法的形参位置，设置和请求参数同名的形参，当浏览器发送请求，匹配到请求映射时，在 DispatcherServlet中就会将请求参数赋值给相应的形参

```html
<a th:href="@{/testParam(username='admin',password=123456)}">测试获取请求参数-->/testParam</a><br>
```

```java
@RequestMapping("/testParam")
public String testParam(String username, String password){
    System.out.println("username:"+username+",password:"+password);
    return "success";
}
```

注： 若请求所传输的请求参数中有多个同名的请求参数，此时可以在控制器方法的形参中设置字符串 数组或者字符串类型的形参接收此请求参数 若使用字符串数组类型的形参，此参数的数组中包含了每一个数据 若使用字符串类型的形参，此参数的值为每个数据中间使用逗号拼接的结果

![image-20221027165958813](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027165958813.png)

![image-20221027170006027](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027170006027.png)

![image-20221027200702075](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027200702075.png)

### @RequestParam

@RequestParam是将请求参数和控制器方法的形参创建映射关系

@RequestParam注解一共有三个属性：value、required、defaultValue

value：指定为形参赋值的请求参数的参数名

required：设置是否必须传输此请求参数，默认值为true

若设置为true时，则当前请求必须传输value所指定的请求参数，若没有传输该请求参数，且没有设置 defaultValue属性，则页面报错400：Required String parameter 'xxx' is not present；若设置为 false，则当前请求不是必须传输value所指定的请求参数，若没有传输，则注解所标识的形参的值为 null

defaultValue：不管required属性值为true或false，当value所指定的请求参数没有传输或传输的值 为""时，则使用默认值为形参赋值

![image-20221027200648945](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027200648945.png)

### @RequestHeader

@RequestHeader是将请求头信息和控制器方法的形参创建映射关系

@RequestHeader注解一共有三个属性：value、required、defaultValue，用法同@RequestParam

### @CookieValue

@CookieValue是将cookie数据和控制器方法的形参创建映射关系

@CookieValue注解一共有三个属性：value、required、defaultValue，用法同@RequestParam

### 通过POJO获取请求参数

可以**在控制器方法的形参位置**设置一个**实体类类型的形参**，此时若浏览器传输的请求参数的参数名和实 体类中的属性名一致，那么请求参数就会为此属性赋值

![image-20221027201427772](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027201427772.png)

### 解决获取请求参数的乱码问题

请求参数的乱码分为**get请求乱码**以及**post请求乱码** 

其中的get请求乱码问题由TomCat（8.0之后的版本）服务器解决

我们要解决的是post请求的乱码问题 需要通过filter过滤器的init初始化参数进行配置 指定编码集为UTF-8

解决获取请求参数的乱码问题，可以使用SpringMVC提供的**编码过滤器CharacterEncodingFilter**，但是 **必须在web.xml中进行注册**

 (编码过滤器始终第一个进行注册)

过滤器的启动总是优先于控制器 

过滤器中的启动顺序取决于过滤器在xml配置的先后顺序

![image-20221027203513992](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027203513992.png)

## 域对象共享数据

Session 、request 以及 ServletContext 合称为 Servlet 的三大域对象，它们都能保存和传递数据，但是三者也存在许多差异，如下表。

域对象的三个方法

```java
setAttribute("key","value")//存
getAttribute("key")//取
removeAttribute("key")//清除
```

| 不同     | request                                                      | Session                                                      | ServletContext                                               |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 类型     | javax.servlet.http.HttpServletRequest                        | javax.servlet.http.HttpSession                               | javax.servlet.ServletContext                                 |
| 创建     | 客户端向容器发送请求时创建。                                 | 容器第一次调用 getSession() 方法时创建。                     | Servlet 容器启动时创建。                                     |
| 销毁     | 容器对这次请求做出响应后销毁。                               | Session 销毁的时机： 关闭服务器或应用被卸载。Session 过期，默认为 30 分钟。手动调用 session.invalidate() 方法进行销毁。 | 容器关闭或者 Web 应用被移除时销毁。                          |
| 有效范围 | 只对当前请求涉及的 Servlet 有效。                            | Session 对本次会话期间的所有 Servlet 都有效。                | 对整个 Web 应用内的所有 Servlet 有效。                       |
| 数量     | Web 应用中的所有 Servlet 实例都可以有多个 request 对象。     | Web 应用中可以有多个 Session，多个 Servet 实例可以共享同一 Session 对象。 | 在整个 Web 应用中只有一个 Context 对象。                     |
| 数据共享 | 每一次请求都是一个新的 request 对象。 通过和请求转发的配合使用可以实现一次请求中 Web 组件之间共享的数据。 | 每一次会话都是一个新的 Session 对象。 通过 Session 域对象可以实现一次会话中的多个请求之间共享数据。 | 在一个应用中有且只有一个 Context 对象，作用于整个 Web 应用，可以实现多次会话之间的数据共享。 |

### 使用ServletAPI向request域对象共享数据（了解）

将HttpServletRequest 对象作为控制器方法的形参 即可直接使用

```java
@RequestMapping("/testServletAPI")
    public String testServletAPI(HttpServletRequest request){
    request.setAttribute("testScope", "hello,servletAPI");
    return "success";
}
```

### 使用ModelAndView向request域对象共享数据（重点掌握）

将ModeAndView设置为控制器方法的方法返回值

在控制器方法中new  ModeAndView的实例 

**调用.addObject("testScope", "hello,ModelAndView");向请求域中设置共享数据**

**调用.setViewName("success");设置视图，实现页面跳转**

```java
@RequestMapping("/testModelAndView")
public ModelAndView testModelAndView(){
    /**
    * ModelAndView有Model和View的功能
    * Model主要用于向请求域共享数据
    * View主要用于设置视图，实现页面跳转
    */
    ModelAndView mav = new ModelAndView();
    //向请求域共享数据
    mav.addObject("testScope", "hello,ModelAndView");
    //设置视图，实现页面跳转
    mav.setViewName("success");
    return mav;
}
```

![image-20221027211353838](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027211353838.png)

### 使用Model向request域对象共享数据

```java
@RequestMapping("/testModel")
public String testModel(Model model){
    model.addAttribute("testScope", "hello,Model");
    return "success";
}
```

### 使用map向request域对象共享数据

```java
@RequestMapping("/testMap")
public String testMap(Map<String, Object> map){
    map.put("testScope", "hello,Map");
    return "success";
}
```

### 使用ModelMap向request域对象共享数据

```java
@RequestMapping("/testModelMap")
public String testModelMap(ModelMap modelMap){
    modelMap.addAttribute("testScope", "hello,ModelMap");
    return "success";
}

```

### Model、ModelMap、Map的关系

Model、ModelMap、Map类型的参数其实本质上都是 BindingAwareModelMap 类型的

```java
public interface Model{}
public class ModelMap extends LinkedHashMap<String, Object> {}
public class ExtendedModelMap extends ModelMap implements Model {}
public class BindingAwareModelMap extends ExtendedModelMap {}
```

> **无论使用哪种方式最终都会封装成ModelAndView**

### RedirectAttributes域对象

> 当controller层需要**重定向到指定页面**时,如何**携带数据?**
>
> - 传统使用session
> - **使用RedirectAttributes. (利用session原理)**优点: 提供了addFlashAttribute 等方法.确保数据只能被使用一次后删除
>   将设置的属性放到 **session** 中，session 中的属性在跳到页面后**马上销毁**
>   - 直接在Controller的参数中添加RedirectAttributes.
>   - addFlashAttribute会在重定向到下一个页面取出这个数据以后,将**session**里面的数据删除
>   - addFlashAttribute 方法会将数据存储在session中,访问一次后失效
>   - addAttribute 方法会将数据拼接在url后(get的形式)

```java
@PostMapping("/regist")
public String register(RedirectAttributes attribdatautes){
    int data = 1;
    attributes.addFlashAttribute("data",data);
    return "redirect:http://auth.gulimail.com/reg.html";
}
```

### 向session域共享数据

> 分布式情况下session会出现问题需要特殊解决

![image-20221027210332810](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027210332810.png)

### 向application(Context域)域共享数据

获取Context域的方式有多种 

```java
ServletContext servletContext = session.getServletContext();
```

```java
ServletContext servletContext = servletConfig.getServletContext();
```

```java
ServletContext servletContext = servletRequest.getServletContext();
```

![image-20221027212851483](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027212851483.png)

## SpringMVC的视图

SpringMVC中的视图是View接口，**视图的作用渲染数据，将模型Model中的数据展示给用户**

SpringMVC视图的种类很多，**默认有转发视图和重定向视图**

**当工程引入jstl的依赖**，转发**视图会自动转换为JstlView**

若**使用的视图技术为Thymeleaf**，在SpringMVC的配置文件中**配置了Thymeleaf的视图解析器**，由此**视图解析器解析之后所得到的是ThymeleafView**

### ThymeleafView

当控制器方法中所设置的视图名称**没有任何前缀时**，此时的**视图名称会被SpringMVC配置文件中所配置 的视图解析器解析**，**视图名称拼接视图前缀**和**视图后缀所得到的最终路径**，会**通过转发的方式实现跳转**

![image-20221027230642841](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027230642841.png)

### 转发视图（InternalResourceView）

SpringMVC中**默认的转发视图是InternalResourceView**

SpringMVC中创建转发视图的情况：

当控制器方法中所设置的**视图名称以"forward:"为前缀时**，**创建InternalResourceView视图**，**此时的视图名称不会被SpringMVC配置文件中所配置的视图解析器解析**，而是**会将前缀"forward:"去掉，剩余部分作为最终路径通过转发的方式实现跳转**

例如"forward:/"，"forward:/employee"

![image-20221027233312939](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027233312939.png)

### 重定向视图（RedirectView）

SpringMVC中默认的重定向视图是RedirectView

当控制器方法中所设置的视图名称以"redirect:"为前缀时，创建RedirectView视图，此时的视图名称不 会被SpringMVC配置文件中所配置的视图解析器解析，而是会将前缀"redirect:"去掉，剩余部分作为最 终路径通过重定向的方式实现跳转

例如"redirect:/"，"redirect:/employee"

![image-20221027234846336](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027234846336.png)

### 请求转发和请求重定向的区别

![image-20220930103300851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220930103300851.png)

### 视图控制器view-controller

**控制器方法中**，**仅仅用来实现页面跳转，即只需要设置视图名称时**，可以**将处理器方法使用view-controller标签进行表示**

![image-20221028003901162](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221028003901162.png)

**当SpringMVC中设置任何一个view-controller时**，**其他控制器中的请求映射将全部失效**，此时**需 要在SpringMVC的核心配置文件中设置开启mvc注解驱动的标签：**

![image-20221028004302962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221028004302962.png)

## 处理静态资源

![image-20221029144327987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029144327987.png)

## HTTPMessageConverter

HttpMessageConverter，**报文信息转换器**，将**请求报文转换为Java对象**，或将**Java对象转换为响应报文**

| 注解              | 实现类             |
| ----------------- | ------------------ |
|                   |                    |
| @RequestBody      | RequestEntiry      |
| **@ResponseBody** | **ResponseEntity** |

![image-20221030112414694](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030112414694.png)

### @RequestBody

[@RequestBody的使用_justry_deng的博客-CSDN博客_@requestbody](https://blog.csdn.net/justry_deng/article/details/80972817)

@RequestBody可以**获取请求体**，需要**在控制器方法设置一个形参**，**使用@RequestBody进行标识**，当前请求的请求体就会为当前注解所标识的形参赋值

![image-20221030095032750](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030095032750.png)

### RequestEntiry

![image-20221030095402984](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030095402984.png)

### **@ResponseBody** ☆

![image-20221030095715314](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030095715314.png)

### SpringMVC处理JSON

![image-20221030110854371](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030110854371.png)

### SpringMVC处理Axios

1、可以在浏览器中发送 XMLHttpRequests
2、可以在 node.js 发送 http 请求
3、支持 Promise API
4、拦截请求和响应
5、转换请求数据和响应数据
6、能够取消请求
7、自动转换 JSON 数据
8、客户端支持保护安全免受 XSRF 攻击

在特性里面已经有提到，浏览器发送请求，或者Node.js发送请求都可以用到Axios。像Vue、React、Node等项目就可以使用Axios，如果你的项目里面用了Jquery，此时就不需要多此一举了，jquery里面本身就可以发送请求。

![image-20221030105219594](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030105219594.png)

### @RestController

@RestController注解是springMVC提供的一个**复合注解**，**标识在控制器的类上**，

就**相当于为类添加了 @Controller注解**，并且**为其中的每个方法添加了@ResponseBody注解**

![image-20221030111604643](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030111604643.png)

### **ResponseEntity**

ResponseEntity用于**控制器方法的返回值类型**，该控制器方法的返回值**就是响应到浏览器的响应报文**

![image-20221030135144341](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030135144341.png)



## 文件的上传和下载

#### 文件下载

![image-20221030135216329](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030135216329.png)

#### 文件上传

![image-20221030135717025](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030135717025.png)

![image-20221030135549852](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030135549852.png)

## 拦截器

Spring MVC 提供了 Interceptor 拦截器机制，用于请求的预处理和后处理。

![image-20221107183528696](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221107183528696.png)

![image-20221029234824030](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029234824030.png)

### 拦截器的配置

SpringMVC中的拦截器需要**实现HandlerInterceptor**

SpringMVC的拦截器必须在**SpringMVC的配置文件中进行配置**

![image-20221030001150562](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030001150562.png)

### 拦截器的三个抽象方法

```java
@Component
public class FirstInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        System.out.println("这里时拦截器的preHandle");
        return true;//这里为true表示放行 false表示不放行
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        System.out.println("这里时拦截器的postHandle");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        System.out.println("这里时拦截器的afterCompletion");
    }
}
/*
preHandle：控制器方法执行之前执行preHandle()，其boolean类型的返回值表示是否拦截或放行，返回true为放行，即调用控制器方法；返回false表示拦截，
即不调用控制器方法
postHandle：控制器方法执行之后执行postHandle()
afterComplation：处理完视图和模型数据，渲染视图完毕之后执行afterComplation()
*/
```

![image-20221030002054149](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030002054149.png)

![image-20221030093026744](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030093026744.png)

![image-20221107183457753](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221107183457753.png)

![image-20221107183511427](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221107183511427.png)

### 多个拦截器的执行顺序

![image-20221107183408619](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221107183408619.png)

**若每个拦截器的preHandle()都返回true** 此时多个拦截器的执行顺序和拦截器在**SpringMVC的配置文件的配置顺序有关**： **preHandle()会按照配置的顺序执行**，而**postHandle()和afterComplation()会按照配置的反序执行**

![image-20221030002227348](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030002227348.png)

![image-20221030003404710](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030003404710.png)

**若某个拦截器的preHandle()返回了false**

**preHandle()返回false和它之前的拦截器的preHandle()都会执行**，

**postHandle()都不执行，**

**返回false 的拦截器之前的拦截器的afterComplation()会执行**

![image-20221030003855721](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030003855721.png)

![image-20221030013224296](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030013224296.png)

## 异常处理器

### 基于配置的异常处理

SpringMVC提供了一个处理控制器方法执行过程中所出现的异常的接口：**HandlerExceptionResolver**

HandlerExceptionResolver接口的实现类有：DefaultHandlerExceptionResolver和 **SimpleMappingExceptionResolver**

SpringMVC提供了自定义的异常处理器**SimpleMappingExceptionResolver**，使用方式：

![image-20221030150140745](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030150140745.png)

### 基于注解的异常处理

![image-20221030151218643](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030151218643.png)

## 注解配置SpringMVC

使用配置类和注解代替web.xml和SpringMVC配置文件的功能

 [SpringMVC完全注解配置取代xml文件配置.drawio](E:\Draw.io\Draw_Java_Graph\SpringMVC完全注解配置取代xml文件配置.drawio) 

![image-20221030215558329](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030215558329.png)

![image-20221030215613432](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030215613432.png)

```java
package com.eddie.config;

import org.springframework.web.filter.CharacterEncodingFilter;
import org.springframework.web.filter.HiddenHttpMethodFilter;
import org.springframework.web.servlet.support.AbstractAnnotationConfigDispatcherServletInitializer;

import javax.servlet.Filter;

/**
 @author EddieZhang
 @create 2022-10-30 19:15
 */
//使用配置类和注解代替web.xml
public class WebInit extends AbstractAnnotationConfigDispatcherServletInitializer {
    /**
     * 指定spring配置类
     * @return
     */
    @Override
    protected Class<?>[] getRootConfigClasses() {
        return new Class[]{SpringConfig.class};
    }

    /**
     * 指定springMVC的配置类
     * @return
     */
    @Override
    protected Class<?>[] getServletConfigClasses() {
        return new Class[]{WebConfig.class};
    }

    /**
     * 指定DispatcherServlet的映射规则 即url-pattern
     * @return
     */
    @Override
    protected String[] getServletMappings() {
        return new String[]{"/"};
    }

    /**
     * 配置过滤器Filter
     * @return
     */
    @Override
    protected Filter[] getServletFilters() {
        CharacterEncodingFilter characterEncodingFilter = new CharacterEncodingFilter();
        characterEncodingFilter.setEncoding("UTF-8");
        characterEncodingFilter.setForceResponseEncoding(true);
        HiddenHttpMethodFilter hiddenHttpMethodFilter = new HiddenHttpMethodFilter();
        return new Filter[]{characterEncodingFilter,hiddenHttpMethodFilter};
    }
}

```

![image-20221030215645712](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030215645712.png)

```java
package com.eddie.config;

import com.eddie.intercepter.FirstInterceptor;
import com.eddie.intercepter.SecondInterceptor;
import com.eddie.intercepter.ThirdInterceptor;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.context.ContextLoader;
import org.springframework.web.context.WebApplicationContext;
import org.springframework.web.multipart.commons.CommonsMultipartResolver;
import org.springframework.web.servlet.HandlerExceptionResolver;
import org.springframework.web.servlet.ViewResolver;
import org.springframework.web.servlet.config.annotation.*;
import org.springframework.web.servlet.handler.SimpleMappingExceptionResolver;
import org.thymeleaf.spring5.SpringTemplateEngine;
import org.thymeleaf.spring5.view.ThymeleafViewResolver;
import org.thymeleaf.templatemode.TemplateMode;
import org.thymeleaf.templateresolver.ITemplateResolver;
import org.thymeleaf.templateresolver.ServletContextTemplateResolver;

import java.util.List;
import java.util.Properties;

/**
 @author EddieZhang
 @create 2022-10-30 19:19
 */
@Configuration//代替SpringMVC.xml
@ComponentScan("com.eddie")//开启组件扫描
@EnableWebMvc//开启注解驱动
public class WebConfig implements WebMvcConfigurer {
    /**
     * 配置默认的servlet处理静态资源
     * @param configurer
     */
    @Override
    public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
        configurer.enable();
    }

    /**
     * 配置拦截器
     * @param registry
     */
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        FirstInterceptor firstInterceptor = new FirstInterceptor();
        SecondInterceptor secondInterceptor = new SecondInterceptor();
        ThirdInterceptor thirdInterceptor = new ThirdInterceptor();
        registry.addInterceptor(firstInterceptor).addPathPatterns("/**").excludePathPatterns("/");
        registry.addInterceptor(secondInterceptor).addPathPatterns("/**").excludePathPatterns("/");
        registry.addInterceptor(thirdInterceptor).addPathPatterns("/**").excludePathPatterns("/");
    }

    /**
     * 配置上下文解析器 用于文件上传
     * @return
     */
    @Bean
    public CommonsMultipartResolver multipartResolver(){
        return new CommonsMultipartResolver();
    }

    /**
     * 配置异常处理器
     * @param resolvers
     */
    @Override
    public void configureHandlerExceptionResolvers(List<HandlerExceptionResolver> resolvers) {
        SimpleMappingExceptionResolver simpleMappingExceptionResolver = new SimpleMappingExceptionResolver();
        Properties properties = new Properties();
        properties.setProperty("java.lang.ArithmeticException","error");
        properties.setProperty("java.lang.NullPointerException","error");
        //设置异常映射
        simpleMappingExceptionResolver.setExceptionMappings(properties);
        //设置request域中共享异常信息的键
        simpleMappingExceptionResolver.setExceptionAttribute("ex");

        resolvers.add(simpleMappingExceptionResolver);
    }

    /**
     * 配置视图控制器
     * @param registry
     */
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/").setViewName("index");
        registry.addViewController("/target").setViewName("target");
    }

    /**
     * 配置生产模板解析器
     * @return
     */
    @Bean
    public ITemplateResolver iTemplateResolver(){
        WebApplicationContext webApplicationContext = ContextLoader.getCurrentWebApplicationContext();
        ServletContextTemplateResolver templateResolver = new ServletContextTemplateResolver(webApplicationContext.getServletContext());
        templateResolver.setPrefix("/WEB-INF/templates/");
        templateResolver.setSuffix(".html");
        templateResolver.setCharacterEncoding("UTF-8");
        templateResolver.setTemplateMode(TemplateMode.HTML);
        return templateResolver;
    }

    /**
     * 生成配置模板引擎 并为模板引擎注入模板解析器
     * @param templateResolver
     * @return
     */
    @Bean
    public SpringTemplateEngine templateEngine(ITemplateResolver templateResolver){
        SpringTemplateEngine springTemplateEngine = new SpringTemplateEngine();
        springTemplateEngine.setTemplateResolver(templateResolver);
        return springTemplateEngine;
    }


    /**
     * 生成视图解析器并为解析器注入模板引擎
     * @param springTemplateEngine
     * @return
     */
    @Bean
    public ViewResolver viewResolver(SpringTemplateEngine springTemplateEngine){
        ThymeleafViewResolver viewResolver = new ThymeleafViewResolver();
        viewResolver.setCharacterEncoding("UTF-8");
        viewResolver.setTemplateEngine(springTemplateEngine);
        return viewResolver;
    }
}

```

![image-20221030215712932](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030215712932.png)

```java
package com.eddie.config;

import org.springframework.context.annotation.Configuration;

/**
 @author EddieZhang
 @create 2022-10-30 19:18
 */
@Configuration
public class SpringConfig {
    //ssm整合之后，spring的配置信息写在此类中
}

```

## SpringMVC执行流程

 [SpringMVC执行流程.drawio](E:\Draw.io\Draw_Java_Graph\SpringMVC执行流程.drawio) 

![image-20221030232004800](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221030232004800.png)

> - **首先用户发送请求——>DispatcherServlet**，前端控制器收到请求后自己不进行处理，而是委托给其他的解析器进行 处理，作为统一访问点，进行全局的流程控制；
> - **DispatcherServlet——>HandlerMapping**， HandlerMapping 将会把请求映射为 HandlerExecutionChain 对象（包含一 个Handler 处理器（页面控制器）对象、多个HandlerInterceptor 拦截器）对象，通过这种策略模式，很容易添加新 的映射策略；
> - **DispatcherServlet——>HandlerAdapter**，HandlerAdapter 将会把处理器包装为适配器，从而支持多种类型的处理器， 即适配器设计模式的应用，从而很容易支持很多类型的处理器；
> - **HandlerAdapter——>处理器功能处理方法的调用**，HandlerAdapter 将会根据适配的结果调用真正的处理器的功能处 理方法，完成功能处理；并返回一个ModelAndView 对象（包含模型数据、逻辑视图名）；
> - **ModelAndView 的逻辑视图名——> ViewResolver**，ViewResolver 将把逻辑视图名解析为具体的View，通过这种策 略模式，很容易更换其他视图技术；
> - **View——>渲染**，View 会根据传进来的Model 模型数据进行渲染，此处的Model 实际是一个Map 数据结构，因此 很容易支持其他视图技术；
> - **返回控制权给DispatcherServlet**，由DispatcherServlet 返回响应给用户，到此一个流程结束。

![image-20221027153135557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221027153135557.png)

![image-20230212123432209](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230212123432209.png)

## SpringMVC常用组件

**DispatcherServlet：前端控制器**，不需要工程师开发，由框架提供
作用：统一处理请求和响应，整个流程控制的中心，由它调用其它组件处理用户的请求
**HandlerMapping：处理器映射器**，不需要工程师开发，由框架提供
作用：根据请求的url、method等信息查找Handler，即控制器方法
**Handler：处理器**，**需要工程师开发**
作用：在DispatcherServlet的控制下Handler对具体的用户请求进行处理
**HandlerAdapter：处理器适配器**，不需要工程师开发，由框架提供
作用：通过HandlerAdapter对处理器（控制器方法）进行执行
**ViewResolver：视图解析器**，不需要工程师开发，由框架提供
作用：进行视图解析，得到相应的视图，例如：ThymeleafView、InternalResourceView、RedirectView
**View：视图**
作用：将模型数据通过页面展示给用户
