# Spring5

![image-20221020124008002](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020124008002.png)

![image-20221020225357977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020225357977.png)

## Spring 框架的**特性**：

- 非侵入式：基于Spring开发的应用中的对象可以不依赖于Spring的API
- **控制反转：IOC——Inversion of Control，指的是将对象的创建权交给 Spring 去创建。使用 Spring 之前，对象的创建都是由我们自己在代码中new创建。而使用 Spring 之后。对象的创建都是给了 Spring 框架。**
- **依赖注入：DI——Dependency Injection，是指依赖的对象不需要手动调用 setXX 方法去设置，而是通过配置赋值。**
- **面向切面编程：Aspect Oriented Programming——AOP**
- 容器：Spring 是一个容器，因为它包含并且管理应用对象的生命周期
- 组件化：Spring 实现了使用简单的组件配置组合成一个复杂的应用。在 Spring 中可以使用XML和Java注解组合这些对象。
- 一站式：在 IOC 和 AOP 的基础上可以整合各种企业应用的开源框架和优秀的第三方类库（实际上 Spring 自身也提供了表现层的 SpringMVC 和持久层的 Spring JDBC）

## 使用Spring 框架的**好处**：

- Spring 可以使开发人员使用 POJOs 开发企业级的应用程序。只使用 POJOs 的好处是你不需要一个 EJB 容器产品，比如一个应用程序服务器，但是你可以选择使用一个健壮的 servlet 容器，比如 Tomcat 或者一些商业产品。
- Spring 在一个单元模式中是有组织的。即使包和类的数量非常大，你只要担心你需要的，而其它的就可以忽略了。
- Spring 不会让你白费力气做重复工作，它真正的利用了一些现有的技术，像 ORM 框架、日志框架、JEE、Quartz 和 JDK 计时器，其他视图技术。
- 测试一个用 Spring 编写的应用程序很容易，因为环境相关的代码被移动到这个框架中。此外，通过使用 JavaBean-style POJOs，它在使用依赖注入注入测试数据时变得更容易。
- Spring 的 web 框架是一个设计良好的 web MVC 框架，它为比如 Structs 或者其他工程上的或者不怎么受欢迎的 web 框架提供了一个很好的供替代的选择。MVC 模式导致应用程序的不同方面(输入逻辑，业务逻辑和UI逻辑)分离，同时提供这些元素之间的松散耦合。模型(Model)封装了应用程序数据，通常它们将由 POJO 类组成。视图(View)负责渲染模型数据，一般来说它生成客户端浏览器可以解释 HTML 输出。控制器(Controller)负责处理用户请求并构建适当的模型，并将其传递给视图进行渲染。
- Spring 对 JavaEE 开发中非常难用的一些 API（JDBC、JavaMail、远程调用等），都提供了封装，使这些API应用难度大大降低。
- 轻量级的 IOC 容器往往是轻量级的，例如，特别是当与 EJB 容器相比的时候。这有利于在内存和 CPU 资源有限的计算机上开发和部署应用程序。
- Spring 提供了一致的事务管理接口，可向下扩展到（使用一个单一的数据库，例如）本地事务并扩展到全局事务（例如，使用 JTA）

## Spring容器（IOC Container）





## IOC

**Spring核心之控制反转(IOC)**

### 引入

1.Spring框架管理这些Bean的创建工作，即由用户管理Bean转变为框架管理Bean，这个就叫**控制反转 - Inversion of Control (IoC)**

2.Spring 框架托管创建的Bean放在哪里呢？ 这便是**IoC Container**;

3.Spring 框架为了更好让用户配置Bean，必然会引入**不同方式来配置Bean？ 这便是xml配置，Java配置，注解配置**等支持

4.Spring 框架既然接管了Bean的生成，必然需要**管理整个Bean的生命周期**等；

5.应用程序代码从Ioc Container中获取依赖的Bean，注入到应用程序中，这个过程叫 **依赖注入(Dependency Injection，DI)** ； 所以说控制反转是通过依赖注入实现的，其实它们是同一个概念的不同角度描述。通俗来说就是**IoC是设计思想，DI是实现方式**

6.在依赖注入时，有哪些方式呢？这就是构造器方式，@Autowired, @Resource, @Qualifier... 同时Bean之间存在依赖（可能存在先后顺序问题，以及**循环依赖问题**等）

### 理解IOC

#### Spring Bean

![image-20221020232643943](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020232643943.png)

#### Bean管理（概念）

Bean 管理指的是两个操作 

（1）Spring 创建对象 

（2）Spirng 注入属性

##### Bean 管理操作有两种常用方式 

##### 注入方式

**一.使用set方法进行注入**

创建属性 提供属性的set方法（这里默认使用类的空参构造器）

```java
/**
* 演示使用 set 方法进行注入属性
*/
public class Book {
     //创建属性
     private String bname;
     private String bauthor;
     //创建属性对应的 set 方法
     public void setBname(String bname) {
        this.bname = bname;
     }
     public void setBauthor(String bauthor) {
        this.bauthor = bauthor;
     }
}
```

在 spring 配置文件配置对象创建，配置属性注入

```xml
<bean id="book" class="com.atguigu.spring5.Book">
 <!--使用 property 完成属性注入
 name：类里面属性名称
 value：向属性注入的值
 -->
 <property name="bname" value="易筋经"></property>
 <property name="bauthor" value="达摩老祖"></property>
</bean>
```

**二.使用有参构造器进行注入**

创建类，定义属性，创建属性对应有参数构造方法

```java
public class Test1 {
    //属性
    private int age;
    private String name;
    private String major;
    //提供有参构造函数
    public Test1(int age, String name, String major) {
        this.age = age;
        this.name = name;
        this.major = major;
    }

}
```

在 spring 配置文件中进行配置

```xml
<!--使用xml的形式配置 bean-->
    <bean id="test1" class="com.eddie.spring5.bean.Test1">
        <!--这里使用constructor标签 name是属性的名称 value是要注入的值-->
        <constructor-arg name="age" value="21"></constructor-arg>
        <constructor-arg name="name" value="EddieZhang"></constructor-arg>
        <constructor-arg name="major" value="Java"></constructor-arg>
    </bean>
<!--使用constructor-arg标签的index指定属性-->
<bean id="test1" class="com.eddie.spring5.bean.Test1">
        <!--这里使用constructor标签 index是属性的索引位置从0开始 value是要注入的值-->
        <constructor-arg index="0" value="21"></constructor-arg>
        <constructor-arg index="1" value="EddieZhang"></constructor-arg>
        <constructor-arg index="2" value="Java"></constructor-arg>
    </bean>
```

P名称空间

![image-20221021225114363](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221021225114363.png)

##### IOC 操作 Bean 管理（xml 注入其他类型属性）

1.字面量

（1）null值

```xml
<!--null 值-->
<property name="address">
 <null/>
</property>
```

（2）属性值包含特殊符号

```xml
<!--属性值包含特殊符号
 1 把<>进行转义 &lt; &gt;
 2 把带特殊符号内容写到 CDATA
-->
<property name="address">
 <value><![CDATA[<<南京>>]]></value>
</property>

```

**属性注入-内部bean**

当 Bean 实例仅仅给一个特定的属性使用时, 可以将其声明为内部 Bean. 内部 Bean 声明直接包含在 <property> 或 <constructor-arg> 元素里, 不需要设置任何 id 或 name 属性

内部 Bean 不能使用在任何其他地方

```java
/*
（1）一对多关系：部门和员工
一个部门有多个员工，一个员工属于一个部门
部门是一，员工是多
（2）在实体类之间表示一对多关系，员工表示所属部门，使用对象类型属性进行表示
*/
//部门类
public class Dept {
     private String dname;
     public void setDname(String dname) {
         this.dname = dname;
     }
}
//员工类
public class Emp {
     private String ename;
     private String gender;
     //员工属于某一个部门，使用对象形式表示
     private Dept dept;
     public void setDept(Dept dept) {
         this.dept = dept;
     }
     public void setEname(String ename) {
         this.ename = ename;
     }
     public void setGender(String gender) {
         this.gender = gender;
     }
}
```

```xml
<!--内部bean-->
    <bean id="Employ" class="com.eddie.spring5.bean.Employ">
        <property name="gender" value="Male"></property>
        <property name="ename" value="EddieZhang"></property>
        <!--设置对象类型属性-->
        <property name="dept">
            <bean id="dept" class="com.eddie.spring5.bean.Dept">
                <property name="dname" value="Java后端"></property>
            </bean>
        </property>
    </bean>
```

**注入属性-级联赋值**(方式一：**先在外部bean中注入属性后，再引用**)

```xml
<!--级联赋值-->
    <!--方式一 先在外部bean中注入属性 再引用-->
    <bean id="Employ" class="com.eddie.spring5.bean.Employ">
        <property name="ename" value="EddieZhang"></property>
        <property name="gender" value="Male"></property>
        <property name="dept" ref="dept"></property>
    </bean>
    <bean id="dept" class="com.eddie.spring5.bean.Dept">
        <property name="dname" value="后端开发"></property>
    </bean>
```

**注入属性-级联赋值**(方式二：**表达式形式，直接引用外部bean的属性**)

**该方式必须在emp实体类中生成dept属性的get方法**，否则会报dept属性找不到

```java
/*
（1）一对多关系：部门和员工
一个部门有多个员工，一个员工属于一个部门
部门是一，员工是多
（2）在实体类之间表示一对多关系，员工表示所属部门，使用对象类型属性进行表示
*/
//部门类
public class Dept {
     private String dname;
     public void setDname(String dname) {
         this.dname = dname;
     }
}
//员工类
public class Emp {
     private String ename;
     private String gender;
     //员工属于某一个部门，使用对象形式表示
     private Dept dept;
    
     public Dept getDept(){//该方式必须在emp实体类中生成dept属性的get方法，否则会报dept属性找不到
         return dept;
     } 
    
     public void setDept(Dept dept) {
         this.dept = dept;
     }
     public void setEname(String ename) {
         this.ename = ename;
     }
     public void setGender(String gender) {
         this.gender = gender;
     }
}
```

```xml
<!--方式二 表达式形式 直接引用外部bean的属性-->
    <bean id="Employ" class="com.eddie.spring5.bean.Employ">
        <property name="ename" value="EddieZhang"></property>
        <property name="gender" value="Male"></property>
        <property name="dept" ref="dept"></property>
        <property name="dept.dname" value="Java后端"></property>
    </bean>
    <bean id="dept" class="com.eddie.spring5.bean.Dept"></bean>
```

**IOC 操作 Bean 管理（xml 注入数组和集合属性）**

```java
/**
 @author EddieZhang
 @create 2022-10-21 23:48
 */
public class Stu {
    @Override
    public String toString() {
        return "Stu{" +
                "courses=" + Arrays.toString(courses) +
                ", list=" + list +
                ", maps=" + maps +
                ", sets=" + sets +
                '}';
    }

    //1 数组类型属性
    private String[] courses;
    //2 list 集合类型属性
    private List<String> list;
    //3 map 集合类型属性
    private Map<String, String> maps;
    //4 set 集合类型属性
    private Set<String> sets;

    public void setSets(Set<String> sets) {
        this.sets = sets;
    }

    public void setCourses(String[] courses) {
        this.courses = courses;
    }

    public void setList(List<String> list) {
        this.list = list;
    }

    public void setMaps(Map<String, String> maps) {
        this.maps = maps;
    }
}
```

```xml
<bean id="stu" class="com.eddie.spring5.bean.Stu">
    <!--xml形式注入数组-->
        <property name="courses">
            <array>
                <value>java</value>
                <value>c</value>
                <value>c++</value>
                <value>c#</value>
            </array>
        </property>
    <!--xml形式注入List集合-->
        <property name="list">
            <list>
                <value>java</value>
                <value>php</value>
                <value>python</value>
                <value>go</value>
            </list>
        </property>
        <!--xml中注入Map集合-->
        <property name="maps">
            <map>
                <entry key="zjh" value="java"></entry>
                <entry key="irving" value="basketball"></entry>
                <entry key="james" value="basketball"></entry>
            </map>
        </property>
        <!--xml中注入Set集合-->
        <property name="sets">
            <set>
                <value>java</value>
                <value>mysql</value>
                <value>spring</value>
            </set>
        </property>
    </bean>
```

**在集合里面设置对象类型值**

```xml
<!--创建多个 course 对象-->
<bean id="course1" class="com.atguigu.spring5.collectiontype.Course">
 <property name="cname" value="Spring5 框架"></property>
</bean>
<bean id="course2" class="com.atguigu.spring5.collectiontype.Course">
 <property name="cname" value="MyBatis 框架"></property>
</bean>
<!--注入 list 集合类型，值是对象-->
<property name="courseList">
 <list>
 <ref bean="course1"></ref>
 <ref bean="course2"></ref>
 </list>
</property>

```

**把集合注入部分提取出来**

在 spring 配置文件中**引入名称空间 util**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:p="http://www.springframework.org/schema/p"
 xmlns:util="http://www.springframework.org/schema/util"
 xsi:schemaLocation="http://www.springframework.org/schema/beans 
http://www.springframework.org/schema/beans/spring-beans.xsd
 http://www.springframework.org/schema/util 
http://www.springframework.org/schema/util/spring-util.xsd">
```

```xml
<!--1 提取 list 集合类型属性注入-->
<util:list id="bookList">
 <value>易筋经</value>
 <value>九阴真经</value>
 <value>九阳神功</value>
</util:list>
<!--2 提取 list 集合类型属性注入使用--><!--有多个bean 都可以使用ref引入提取出来的list集合-->
<bean id="book" class="com.atguigu.spring5.collectiontype.Book">
 <property name="list" ref="bookList"></property>
</bean>
<bean id="book1" class="com.atguigu.spring5.collectiontype.Book">
 <property name="list" ref="bookList"></property>
</bean>

```

###### （1）基于 xml 配置文件方式实现 

![image-20221021223441552](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221021223441552.png)

1.需要在Spring的xml文件中使用<bean id="标识名 类名的首字母小写" class="类的全类名"><bean/>标签配置Bean

![image-20221021214624461](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221021214624461.png)

2.加载Spring的xml配置文件

| **①使用ApplicationContext（推荐程序员使用此方式）**          | **②使用BeanFactory**                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 应用上下文，继承BeanFactory接口，它是Spring的一各更高级的容器，提供了更多的有用的功能； | 是Spring里面最低层的接口，提供了最简单的容器的功能，只提供了实例化对象和拿对象的功能 |
| \1) 国际化（MessageSource）                                  |                                                              |
| \2) 访问资源，如URL和文件（ResourceLoader）                  |                                                              |
| \3) 载入多个（有继承关系）上下文 ，使得每一个上下文都专注于一个特定的层次，比如应用的web层 |                                                              |
| \4) 消息发送、响应机制（ApplicationEventPublisher）          |                                                              |
| \5) AOP（拦截器）                                            |                                                              |
|                                                              |                                                              |
| **两者装载bean的区别**                                       | **两者装载bean的区别**                                       |
| ApplicationContext在启动的时候就把所有的Bean全部实例化了。它还可以为Bean配置lazy-init=true来让Bean延迟实例化； | BeanFactory在启动的时候不会去实例化Bean，有从容器中拿Bean的时候才会去实例化； |
|                                                              |                                                              |
| 不延迟实例化的优点： （**ApplicationContext**）              | 延迟实例化的优点：（**BeanFactory**）                        |
| \1. 所有的Bean在启动的时候都加载，系统运行的速度快；         | 应用启动的时候占用资源很少；对资源要求较高的应用，比较有优势； |
| \2. 在启动的时候所有的Bean都加载了，我们就能在系统启动的时候，尽早的发现系统中的配置问题 |                                                              |
| \3. 建议web应用，在启动的时候就把所有的Bean都加载了。（把费时的操作放到系统启动中完成） |                                                              |

3.获取配置创建的对象

![image-20221021214843700](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221021214843700.png)

###### （2）基于注解方式实现

Spring **针对 Bean 管理中创建对象提供注解**

 （1）@Component （2）@Service (逻辑层)（3）@Controller （web层）（4）@Repository （dao层）

上面四个注解功能是一样的，都可以用来创建 bean 实例

```xml
第一步 引入依赖
    spring-aop-5.2.3.RELEASE.jar
第二步 开启组件扫描
<!--开启组件扫描
 1 如果扫描多个包，多个包使用逗号隔开
 2 扫描包上层目录
-->
<context:component-scan base-package="com.atguigu"></context:component-scan>
    <!--base-package="指明要scan的包"-->
	<!--base-package="com.eddie.dao,com.eddie.service"-->
    或者扫描上层目录<!--base-package="com.eddie"-->
第三步 创建类，在类上面添加创建对象注解
//在注解里面 value 属性值可以省略不写，
//默认值是类名称，首字母小写
```

```java
/**
 @author EddieZhang
 @create 2022-10-22 19:44
 */
@Service(value = "serviceTest")//value可以省略不写 默认是类名的首字母小写
public class ServiceTest {
    @Autowired//自动装配 默认使用byType 可以结合@Qualifier使用byName value指明name
    @Qualifier(value = "daoTest")
    private DaoTest daoTest;
    public void talk(){
        System.out.println("我是ServiceTest");
    }

    @Override
    public String toString() {
        return "ServiceTest{" +
                "daoTest=" + daoTest +
                '}';
    }
}
```

```java
@Test
    public void test2(){
        //读取xml文件 xml文件中开启了组件扫描 会扫描指定包中的注解
        ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
        //获取bean
        ServiceTest serviceTest = context.getBean("serviceTest", ServiceTest.class);
        System.out.println(serviceTest);
    }
```

开启扫描组件中的配置细节

![image-20221022203144526](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221022203144526.png)

![image-20221022203540004](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221022203540004.png)

```xml
<context:component-scan base-package="com.atguigu"></context:component-scan>
<!--以上是默认根据filter进行扫描 我们可以根据需要自己配置扫描filter的扫描规则-->

<!--示例 1
 use-default-filters="false" 表示现在不使用默认 filter，自己配置 filter
 context:include-filter ，设置扫描哪些内容
-->
<context:component-scan base-package="com.atguigu" use-default-filters="false">
<context:include-filter type="annotation" 
 
expression="org.springframework.stereotype.Controller"/><!--表明只扫描带Controller注解的类-->
</context:component-scan>

<!--示例 2
 下面配置扫描包所有内容
 context:exclude-filter： 设置哪些内容不进行扫描
-->
<context:component-scan base-package="com.atguigu">
<context:exclude-filter type="annotation" 
 
expression="org.springframework.stereotype.Controller"/><!--表明不扫描带Controller注解的类其他的都扫描-->
</context:component-scan>
```

**基于注解方式进行属性的注入**

@AutoWired(根据属性类型进行自动装配)

@Qualifier(根据属性名称进行注入 可以和@AutoWired搭配使用实现根据名称进行自动装配)

使用@Qualifier 时候，如何设置的指定名称的Bean不存在，则会抛出异常，如果防止抛出异常，可以使用

```java
@Qualifier("xxxxyyyy")
@Autowired(required = false)
private HelloDao helloDao;


//会输出为null
ServiceTest{name='Eddie', age=21, major='java', daoTest=null}
```

不需要添加set方法

建议使用上面两个 是Spring提供的 @Resource是javax包下的

```java
@Service(value = "serviceTest")//value可以省略不写 默认是类名的首字母小写
public class ServiceTest {
    @Autowired//自动装配 默认使用byType(byType有一个弊端就是不能出现第二个同类型的对象 会无法确认二报错) 
    //可以结合@Qualifier使用byName value指明name
    @Qualifier(value = "daoTest")
    private DaoTest daoTest;
    public void talk(){
        System.out.println("我是ServiceTest");
    }
    
    @Test
    public void test2(){
        //读取xml文件 xml文件中开启了组件扫描 会扫描指定包中的注解
        ApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
        //获取bean
        ServiceTest serviceTest = context.getBean("serviceTest", ServiceTest.class);
        System.out.println(serviceTest);
        serviceTest.talk();
    }
    
    console
        ServiceTest{name='Eddie', age=21, major='java', daoTest=com.eddie.dao.DaoTest@264f218}
        我是ServiceTest
        我是DaoTest
```

@Resource

```java
@Resource：可以根据类型注入，可以根据名称注入
//@Resource //根据类型进行注入
@Resource(name = "userDaoImpl1") //根据名称进行注入
private UserDao userDao;
```

以上是注入对象类型的

@Value(注入普通属性)

```java
public class ServiceTest {
    @Value(value = "Eddie")
    private String name;
    @Value(value = "21")
    private int age;
    @Value(value = "java")
    private String major;
    
    console
        ServiceTest{name='Eddie', age=21, major='java', daoTest=com.eddie.dao.DaoTest@264f218}
```

###### （3）完全注解方式实现

**创建配置类，替代 xml 配置文件**

![image-20221022211617765](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221022211617765.png)

```java
/**创建配置类 取代xml配置文件 实现全注解方式管理bean
 @author EddieZhang
 @create 2022-10-22 21:10
 */
@Configuration//作为配置类 取代xml配置文件
@ComponentScan(basePackages = {"com.eddie"})//开启组件扫描 设置扫描的范围
//@ComponentScan(basePackages = {"com.eddie.bean","com.eddie.service"})//数组的形式可以指定扫描多个包 或者选择上一层目录扩大扫描范围
//相当于<context:component-scan base-package="com.eddie"></context:component-scan>
public class SpringConfig {
}

@Test
    public void test1(){
        //获取配置文件 基于全注解方法 要读取配置类
        //创建AnnotationConfigApplicationContext实现类对象
        ApplicationContext context = new AnnotationConfigApplicationContext(SpringConfig.class);
        ServiceTest serviceTest = context.getBean("serviceTest", ServiceTest.class);
        System.out.println(serviceTest);
        serviceTest.talk();
    }

console
    ServiceTest{name='Eddie', age=21, major='java', daoTest=com.eddie.dao.DaoTest@6a6afff2}
    我是ServiceTest
    我是DaoTest
```



#### IOC 操作 Bean 管理（FactoryBean）

1、Spring 有两种类型 bean，一种**普通 bean**，另外一种**工厂 bean（FactoryBean）** 

2、**普通 bean：在配置文件中定义 bean 类型就是返回类型** 

3、**工厂 bean：(Spring 内置的bean) 在配置文件定义 bean 类型可以和返回类型不一样** 

FactoryBean的特殊之处在于它可以向容器中注册两个Bean，一个是它本身，一个是FactoryBean.getObject()方法返回值所代表的Bean

[FactoryBean——Spring的扩展点之一 - 掘金 (juejin.cn)](https://juejin.cn/post/6844903954615107597)

```java
//第一步 创建类，让这个类作为工厂 bean，实现接口 FactoryBean 
//第二步 实现接口里面的方法，在实现的方法中定义返回的 bean 类型
/**
 @author EddieZhang
 @create 2022-10-22 10:10
 */
public class MyBean implements FactoryBean {
    /**
     * 实现了FactoryBean接口的bean是一个特殊的bean
     * 特殊之处在于它可以向容器中注册两个Bean，一个是它本身，一个是FactoryBean.getObject()方法返回值所代表的Bean
     * @return
     * @throws Exception
     */
    @Override
    public Employ getObject() throws Exception {
        Employ employ = new Employ();
        employ.setEname("Eddie");
        return employ;
    }

    @Override
    public Class<?> getObjectType() {
        return null;
    }
}
```

```xml
<bean id="myBean" class="com.atguigu.spring5.factorybean.MyBean">
</bean>
```

```java
//测试类
/**
 @author EddieZhang
 @create 2022-10-22 10:13
 */
public class FactoryBeanTest {
    @Test
    public void test1(){
        //读取xml文件
        ApplicationContext context = new ClassPathXmlApplicationContext("bean2.xml");
        Object myBean = context.getBean("myBean",Employ.class);
        //Object myBean = context.getBean("myBean",MyBean.class)报异常
        System.out.println(myBean);//com.eddie.spring5.bean.Employ@4466af20
    }
    @Test
    public void test2(){
        //读取xml文件
        ApplicationContext context = new ClassPathXmlApplicationContext("bean2.xml");
        Object myBean = context.getBean("&myBean",MyBean.class);
        System.out.println(myBean);//com.eddie.spring5.bean.MyBean@4f6ee6e4
    }
}
```

**FactoryBean的创建流程**

![image-20221022100712785](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221022100712785.png)

#### IOC 操作 Bean 管理（xml 自动装配）

根据指定装配规则（属性名称或者属性类型），Spring 自动将匹配的属性值进行注入

| 限制         | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| 重写的可能性 | 你可以使用总是重写自动装配的 <constructor-arg>和 <property> 设置来指定依赖关系。 |
| 原始数据类型 | 你不能自动装配所谓的简单类型包括基本类型，字符串和类。       |
| 混乱的本质   | 自动装配不如显式装配精确，所以如果可能的话尽可能使用显式装配。 |

| 模式                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| no                                                           | 这是默认的设置，它意味着没有自动装配，你应该使用显式的bean引用来连线。你不用为了连线做特殊的事。在依赖注入章节你已经看到这个了。 |
| [byName](https://www.w3cschool.cn/wkspring/fwdz1mmb.html)    | 由属性名自动装配。Spring 容器看到在 XML 配置文件中 bean 的自动装配的属性设置为 byName。然后尝试匹配，并且将它的属性与在配置文件中被定义为相同名称的 beans 的属性进行连接。 |
| [byType](https://www.w3cschool.cn/wkspring/8dhy1mmd.html)    | 由属性数据类型自动装配。Spring 容器看到在 XML 配置文件中 bean 的自动装配的属性设置为 byType。然后如果它的**类型**匹配配置文件中的一个确切的 bean 名称，它将尝试匹配和连接属性的类型。如果存在不止一个这样的 bean，则一个致命的异常将会被抛出。 |
| [constructor](https://www.w3cschool.cn/wkspring/jtlb1mmf.html) | 类似于 byType，但该类型适用于构造函数参数类型。如果在容器中没有一个构造函数参数类型的 bean，则一个致命错误将会发生。 |
| autodetect（3.0版本不支持）                                  | Spring首先尝试通过 constructor 使用自动装配来连接，如果它不执行，Spring 尝试通过 byType 来自动装配。 |

常用的两种 **根据名称 ByName** **根据类型 ByType**

```xml
根据属性名称自动注入
<!--实现自动装配
 bean 标签属性 autowire，配置自动装配
 autowire 属性常用两个值：
 byName 根据属性名称注入 ，注入值 bean 的 id 值和类属性名称一样
 byType 根据属性类型注入
-->
<bean id="emp" class="com.atguigu.spring5.autowire.Emp" autowire="byName">
 <!--<property name="dept" ref="dept"></property>-->
</bean>
<bean id="dept" class="com.atguigu.spring5.autowire.Dept"></bean>
```

```xml
<!--根据属性类型自动注入 注意 此方式同类的只能有一个 出现第二个无法确定具体要装配哪一个 会报错-->
<!--实现自动装配
 bean 标签属性 autowire，配置自动装配
 autowire 属性常用两个值：
 byName 根据属性名称注入 ，注入值 bean 的 id 值和类属性名称一样
 byType 根据属性类型注入
-->
<bean id="emp" class="com.atguigu.spring5.autowire.Emp" autowire="byType">
 <!--<property name="dept" ref="dept"></property>-->
</bean>
<bean id="dept" class="com.atguigu.spring5.autowire.Dept"></bean>
```

#### IOC 操作 Bean 管理(外部属性文件)

列如：配置数据库信息

```xml

<!--直接配置连接池-->
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
 <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
 <property name="url" 
value="jdbc:mysql://localhost:3306/userDb"></property>
 <property name="username" value="root"></property>
 <property name="password" value="root"></property>
</bean>

```

**在 spring 配置文件使用标签引入外部属性文件**(推荐使用 灵活性更高)

```xml
<!--引入外部属性文件-->
<context:property-placeholder location="classpath:jdbc.properties"/>
<!--配置连接池-->
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${prop.driverClassName}"></property>
        <property name="url" value="${prop.url}"></property>
        <property name="username" value="${prop.username}"></property>
        <property name="password" value="${prop.password}"></property>
    </bean>
```

#### Bean的作用域

![image-20221025121503067](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121503067.png)

在 Spring 里面，**设置创建 bean 实例**是**单实例**还是**多实例**

在 Spring 里面，**默认情况**下，bean 是**单实例对象**

![image-20221020233712330](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020233712330.png)

**设置单实例还是多实例**

在 spring 配置文件 bean 标签里面有**属性（scope）**用于**设置单实例还是多实例** 

scope 属性值 第一个值 默认值，**singleton，表示是单实例对象** 第二个值 **prototype，表示是多实例对象**

![image-20221020233847585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020233847585.png)

**singleton 和 prototype 区别** 

第一 

singleton 单实例，prototype 多实例

第二 

设置 scope 值是 singleton 时候，加载 spring 配置文件时候就会创建单实例对象 

设置 scope 值是 prototype 时候，不是在加载 spring 配置文件时候创建 对象，在调用 getBean 方法时候创建多实例对象

#### Bean的生命周期★

1、生命周期 （1）从对象创建到对象销毁的过程 

Spring Bean 的生命周期在整个 Spring 中占有很重要的位置，从BeanFactory或ApplicationContext取得的实例为Singleton，也就是预设为每一个Bean的别名只能维持一个实例，而不是每次都产生一个新的对象使用Singleton模式产生单一实例，在spring中，singleton属性默认是true，只有设定为false，则每次指定别名取得的Bean时都会产生一个新的实例，**Spring只帮我们管理单例模式Bean的完整生命周期**，**对于prototype的bean，Spring在创建好交给使用者之后则不会再管理后续的生命周期**

![image-20221025121432095](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121432095.png)

![image-20230325110434458](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325110434458.png)

![image-20221025121156701](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121156701.png)

![image-20221025121628743](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121628743.png)

![image-20221025121534856](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121534856.png)

![image-20221025121238898](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025121238898.png)

**2、bean 生命周期** （不包括后置处理器）

（1）通过构造器创建 bean 实例（无参数构造）

（2）为 bean 的属性设置值和对其他 bean 引用（调用 set 方法）

（3）调用 bean 的初始化的方法（需要进行配置初始化的方法）

（4）bean 可以使用了（对象获取到了） 

（5）当容器关闭时候，调用 bean 的销毁的方法（需要进行配置销毁的方法）

```java
//Java代码Orders类
public class Orders {
    //无参数构造
    public Orders() {
        System.out.println("第一步 执行无参数构造创建 bean 实例");
    }
    private String oname;
    public void setOname(String oname) {
        this.oname = oname;
        System.out.println("第二步 调用 set 方法设置属性值");
    }
    //创建执行的初始化的方法
    public void initMethod() {
        System.out.println("第三步 执行初始化的方法");
    }
    //创建执行的销毁的方法
    public void destroyMethod() {
        System.out.println("第五步 执行销毁的方法");
    }
}
```

```xml
<!--Spring.xml配置文件代码-->
<!--配置Orders对象-->
    <bean id="orders" class="com.eddie.spring5.bean.Orders" init-method="initMethod" destroy-method="destroyMethod">
        <!--属性注入-->
        <property name="oname" value="手机"></property>
</bean>
```

```java
//测试文件代码
public class TestBean {
    @Test
    public void test1(){
        //读取xml文件
        ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("bean1.xml");
        //获取bean
        Orders orders = context.getBean("orders", Orders.class);
        System.out.println("第四步 这里是获得的bean对象" + orders);
        //手动让bean实例销毁
        context.close();
    }
}
```

console输出

![image-20221021003124970](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221021003124970.png)

**bean 的后置处理器，bean 生命周期有七步**（完整的）

（1）通过构造器创建 bean 实例（无参数构造） 

（2）为 bean 的属性设置值和对其他 bean 引用（调用 set 方法） 

（3）把 bean 实例传递 bean 后置处理器的方法 postProcessBeforeInitialization  

（4）调用 bean 的初始化的方法（需要进行配置初始化的方法） 

（5）把 bean 实例传递 bean 后置处理器的方法 postProcessAfterInitialization 

（6）bean 可以使用了（对象获取到了） 

（7）当容器关闭时候，调用 bean 的销毁的方法（需要进行配置销毁的方法）

```java

//Orders类
/**
 @author EddieZhang
 @create 2022-10-21 0:14
 */
public class Orders {
    //无参数构造
    public Orders() {
        System.out.println("第一步 执行无参数构造创建 bean 实例");
    }
    //有参构造器注入

    public Orders(String oname) {
        this.oname = oname;
        System.out.println("第一步 执行有参构造器创建bean实例");
    }

    private String oname;
    public void setOname(String oname) {
        this.oname = oname;
        System.out.println("第二步 调用 set 方法设置属性值");
    }
    //创建执行的初始化的方法
    public void initMethod() {
        System.out.println("第三步 执行初始化的方法");
    }
    //创建执行的销毁的方法
    public void destroyMethod() {
        System.out.println("第五步 执行销毁的方法");
    }
}

//后置处理器类
/**
 @author EddieZhang
 @create 2022-10-22 11:25
 */
public class MyBeanPost implements BeanPostProcessor {
    @Override
    public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
        System.out.println("这里是后置处理器的postProcessBeforeInitialization");
        return BeanPostProcessor.super.postProcessBeforeInitialization(bean, beanName);
    }

    @Override
    public Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
        System.out.println("这里是后置处理器的postProcessAfterInitialization");
        return BeanPostProcessor.super.postProcessAfterInitialization(bean, beanName);
    }
}

```

```xml
    <!--配置后置处理器-->
    <bean id="myBeanPost" class="com.eddie.spring5.bean.MyBeanPost"></bean>
    <!--配置bean--><!--在配置中设置初始化和销毁方法-->
    <bean id="orders" class="com.eddie.spring5.bean.Orders" destroy-method="destroyMethod" init-method="initMethod">
        <property name="oname" value="orders1"></property>
    </bean>
```

```java
    /**测试类
     * 带上后置处理器的bean的完整的生命周期
     */
    @Test
    public void test2(){
        //读取xml文件
        AbstractApplicationContext context = new ClassPathXmlApplicationContext("bean3.xml");
        //获取Orders对象
        Orders orders = context.getBean("orders", Orders.class);
        System.out.println("第四步 这里是获得bean" + orders);
        //获取后置处理器
        MyBeanPost myBeanPost = context.getBean("myBeanPost", MyBeanPost.class);
        //手动销毁Order对象Bean
        context.close();

    }
```

console输出

```
第一步 执行无参数构造创建 bean 实例
第二步 调用 set 方法设置属性值
第三步 这里是后置处理器的postProcessBeforeInitialization
第四步 执行初始化的方法
第五步 这里是后置处理器的postProcessAfterInitialization
第六步 这里是获得beancom.eddie.spring5.bean.Orders@7b98f307
第七步 执行销毁的方法
```



#### IOC是什么

![image-20221020232743798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020232743798.png)

**（1）控制反转，把对象创建和对象之间的调用过程，交给 Spring 进行管理** 

（2）使用 IOC 目的：为了耦合度降低

**传统Java SE程序设计**，我们直接在对象内部通过new进行创建对象，是**程序主动去创建依赖对象**；

**而IoC（IOC容器）是有专门一个容器来创建这些对象**，即由Ioc容器来控制对 象的创建；谁控制谁？当然是IoC 容器控制了对象；控制什么？那就是主要控制了外部资源获取（不只是对象包括比如文件等）

#### 有了IOC容器与传统程序设计的对比

**传统程序设计**

![image-20221020233118180](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020233118180.png)

**当有了IoC/DI的容器后**

![image-20221020233145006](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221020233145006.png)

#### IOC能做什么

#### IOC和DI



## AOP

### AOP的核心概念

目标对象、连接点、切入点
通知类、通知
切面
代理

AOP为Aspect Oriented Programming的缩写，意为：**面向切面编程**

![image-20230111205206087](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230111205206087.png)

**Spring AOP 就是基于动态代理的**，如果要代理的对象，实现了某个接口，那么 Spring AOP 会使用 **JDK Proxy**，去创建代理对象，而对于没有实现接口的对象，就无法使用 JDK Proxy 去进行代理了，这时候 Spring AOP 会使用 **Cglib** 生成一个被代理对象的子类来作为代理，如下图所示：

![image-20230111205219444](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230111205219444.png)

![image-20230111230423149](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230111230423149.png)

### AOP 切面编程专业术语：

> 首先让我们从一些重要的AOP概念和术语开始。**这些术语不是Spring特有的**。

- **连接点（Jointpoint）**：表示需要在程序中插入横切关注点的扩展点，**连接点可能是类初始化、方法执行、方法调用、字段调用或处理异常等等**，Spring只支持方法执行连接点，在AOP中表示为**在哪里干**；
- **切入点（Pointcut）**： 选择一组相关连接点的模式，即可以认为连接点的集合，Spring支持perl5正则表达式和AspectJ切入点模式，Spring默认使用AspectJ语法，在AOP中表示为**在哪里干的集合**；
- **通知（Advice）**：在连接点上执行的行为，通知提供了在AOP中需要在切入点所选择的连接点处进行扩展现有行为的手段；包括前置通知（before advice）、后置通知(after advice)、环绕通知（around advice），在Spring中通过代理模式实现AOP，并通过拦截器模式以环绕连接点的拦截器链织入通知；在AOP中表示为**干什么**；
- **方面/切面（Aspect）**：横切关注点的模块化，比如上边提到的日志组件。可以认为是通知、引入和切入点的组合；在Spring中可以使用Schema和@AspectJ方式进行组织实现；在AOP中表示为**在哪干和干什么集合**；
- **引入（inter-type declaration）**：也称为内部类型声明，为已有的类添加额外新的字段或方法，Spring允许引入新的接口（必须对应一个实现）到所有被代理对象（目标对象）, 在AOP中表示为**干什么（引入什么）**；
- **目标对象（Target Object）**：需要被织入横切关注点的对象，即该对象是切入点选择的对象，需要被通知的对象，从而也可称为被通知对象；由于Spring AOP 通过代理模式实现，从而这个对象永远是被代理对象，在AOP中表示为**对谁干**；
- **织入（Weaving）**：把切面连接到其它的应用程序类型或者对象上，并创建一个被通知的对象。这些可以在编译时（例如使用AspectJ编译器），类加载时和运行时完成。Spring和其他纯Java AOP框架一样，在运行时完成织入。在AOP中表示为**怎么实现的**；
- **AOP代理（AOP Proxy）**：AOP框架使用代理模式创建的对象，从而实现在连接点处插入通知（即应用切面），就是通过代理来对目标对象应用切面。在Spring中，AOP代理可以用JDK动态代理或CGLIB代理实现，而通过拦截器模型应用切面。在AOP中表示为**怎么实现的一种典型方式**；

> **通知类型**：

- **前置通知（Before advice）**：在某连接点之前执行的通知，但这个通知不能阻止连接点之前的执行流程（除非它抛出一个异常）。
- **后置通知（After returning advice）**：在某连接点正常完成后执行的通知：例如，一个方法没有抛出任何异常，正常返回。
- **异常通知（After throwing advice）**：在方法抛出异常退出时执行的通知。
- **最终通知（After (finally) advice）**：当某连接点退出的时候执行的通知（不论是正常返回还是异常退出）。
- **环绕通知（Around Advice）**：包围一个连接点的通知，如方法调用。这是最强大的一种通知类型。环绕通知可以在方法调用前后完成自定义的行为。它也会选择是否继续执行连接点或直接返回它自己的返回值或抛出异常来结束执行。

环绕通知是最常用的通知类型。和AspectJ一样，Spring提供所有类型的通知，我们推荐你使用尽可能简单的通知类型来实现需要的功能。例如，如果你只是需要一个方法的返回值来更新缓存，最好使用后置通知而不是环绕通知，尽管环绕通知也能完成同样的事情。用最合适的通知类型可以使得编程模型变得简单，并且能够避免很多潜在的错误。比如，你不需要在JoinPoint上调用用于环绕通知的proceed()方法，就不会有调用的问题。

### Spring AOP 和 AspectJ AOP 区别

> **Spring AOP 属于运行时增强，而 AspectJ 是编译时增强。** Spring AOP 基于代理(Proxying)，而 AspectJ 基于字节码操作(Bytecode Manipulation)。
>
> - **Spring AOP**
>
>   https://www.springcloud.io/post/2022-01/springboot-aop/#gsc.tab=0
>
>   (If the proxy object implements the interface, use the JDK dynamic proxy. else it is a direct Cglib dynamic proxy.) 
>
>   **starting with Spring Boot 2.0, if the user does not configure anything, the Cglib proxy is used by default.**
>
>   - JDK Dynamic proxy can only proxy **by interface** (so your target class needs to implement an interface, which is then also implemented by the proxy class).
>   - CGLIB (and javassist) can create a proxy **by subclassing**. In this scenario the proxy becomes a subclass of the target class. No need for interfaces.
>
>   | No.  |       Key       |                      JDK dynamic proxy                       |                  CGLIB proxy                  |
>   | :--: | :-------------: | :----------------------------------------------------------: | :-------------------------------------------: |
>   |  1   | impl interface? | It can be only proxy by interface so target class needs to implement interface |      It can create proxy by subclassing       |
>   |  2   |     Package     |                It is available with the Java                 |            It is a third  library.            |
>   |  3   |   Performance   |              It is a bit slow than CGLIB proxy               |      It is faster than JDK dynamic proxy      |
>   |  4.  |      Final      |        Final class and Final method can not be proxy         | Final class and Final method can not be proxy |
>
> - **AspectJ**



Spring AOP 已经集成了 AspectJ ，AspectJ 应该算的上是 Java 生态系统中最完整的 AOP 框架了。AspectJ 相比于 Spring AOP 功能更加强大，但是 Spring AOP 相对来说更简单，

如果我们的切面比较少，那么两者性能差异不大。但是，当切面太多的话，最好选择 AspectJ ，它比 Spring AOP 快很多。

![image-20230111205557141](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230111205557141.png)

### AspectJ 定义的通知类型

- **Before**（前置通知）：目标对象的方法调用之前触发
- **After** （后置通知）：目标对象的方法调用之后触发
- **AfterReturning**（返回通知）：目标对象的方法调用完成，在返回结果值之后触发
- **AfterThrowing**（异常通知） ：目标对象的方法运行中抛出 / 触发异常后触发。AfterReturning 和 AfterThrowing 两者互斥。如果方法调用成功无异常，则会有返回值；如果方法抛出了异常，则不会有返回值。
- **Around** （环绕通知）：编程式控制目标对象的方法调用。环绕通知是所有通知类型中可操作范围最大的一种，因为它可以直接拿到目标对象，以及要执行的方法，所以环绕通知可以任意的在目标对象的方法调用前后搞事，甚至不调用目标对象的方法

前置通知
后置通知
**环绕通知（重点）**
		环绕通知依赖**形参ProceedingJoinPoint才能实现对原始方法的调用**
		环绕通知可以隔离原始方法的调用执行
		环绕通知返回值设置为Object类型
		环绕通知中可以对原始方法调用过程中出现的异常进行处理
返回后通知
抛出异常后通知

### AOP常用注解

|                         | 作用                                           | 使用位置                                   |
| ----------------------- | ---------------------------------------------- | ------------------------------------------ |
| @EnableAspectJAutoProxy | 开启注解格式AOP功能                            | 配置类定义上方（常用于SpringBoot启动类上） |
| @Aspect                 | 设置当前类为AOP切面类                          | 切面类定义上方                             |
| @Pointcut               | 设置切入点方法                                 | 切入点方法定义上方                         |
| @Before                 | 设置方法的前置通知                             | 增强方法的上方                             |
| @After                  | 当前通知方法在原始切入点方法后运行             | 增强方法的上方                             |
| @AfterReturning         | 当前通知方法在原始切入点方法正常执行完毕后执行 | 增强方法的上方                             |
| @AfterThrowing          | 当前通知方法在原始切入点方法运行抛出异常后执行 | 增强方法的上方                             |
| @Around                 | 当前通知方法在原始切入点方法前后运行           | 增强方法的上方                             |

### AOP切入点表达式

#### 语法格式

切入点表达式标准格式：动作关键字**(访问修饰符 返回值 包名.类/接口名.方法名（参数）异常名)**

```java
@Pointcut(execution(public User com.itheima.service.UserService.findById(int)))
/*
execution：动作关键字，描述切入点的行为动作，例如execution表示执行到指定切入点
public:访问修饰符,还可以是public，private等，可以省略
User：返回值，写返回值类型
com.itheima.service：包名，多级包使用点连接
UserService:类/接口名称
findById：方法名
int:参数，直接写参数的类型，多个类型用逗号隔开
异常名：方法定义中抛出指定异常，可以省略
*/
```

#### 通配符

\* :	单个独立的任意符号，可以独立出现，也可以作为前缀或者后缀的匹配符出现

.. ： 多个连续的任意符号，可以独立出现，常用于简化包名与参数的书写

\+ ：专用于匹配子类类型

#### 书写技巧

```java
/*
所有代码按照标准规范开发，否则以下技巧全部失效

1.描述切入点通常描述接口，而不描述实现类,如果描述到实现类，就出现紧耦合了
2.访问控制修饰符针对接口开发均采用public描述（可省略访问控制修饰符描述）
3.返回值类型对于增删改类使用精准类型加速匹配，对于查询类使用*通配快速描述
4.包名书写尽量不使用..匹配，效率过低，常用*做单个包描述匹配，或精准匹配
5.接口名/类名书写名称与模块相关的采用*匹配，例如UserService书写成*Service，绑定业务层接口名
6.方法名书写以动词进行精准匹配，名词采用匹配，例如getById书写成getBy,selectAll书写成selectAll参数规则较为复杂，根据业务方法灵活调整
7.通常不使用异常作为匹配规则
*/
```

### 通知中获取参数

获取切入点方法的参数，所有的通知类型都可以获取参数
**JoinPoint：适用于前置、后置、返回后、抛出异常后通知**
**ProceedingJoinPoint：适用于环绕通知**

### AOP-定义Aspect实例





## Spring三级缓存

[Spring 为何需要三级缓存解决循环依赖，而不是二级缓存 - 半分、 - 博客园 (cnblogs.com)](https://www.cnblogs.com/semi-sub/p/13548479.html)



> **所以如果没有AOP的话确实可以两级缓存就可以解决循环依赖的问题，如果加上AOP，两级缓存是无法解决的，不可能每次执行singleFactory.getObject()方法都给我产生一个新的代理对象，所以还要借助另外一个缓存来保存产生的代理对象**


![image-20230330132116900](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230330132116900.png)

![image-20230330140832793](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230330140832793.png)

![image-20230330134300280](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230330134300280.png)



## SpringJDBC

## SpringJDBCTransaction

## Spring Propagation levels

> Spring框架提供了不同的事务传播级别（Transaction Propagation Levels），用于定义事务方法在调用另一个事务方法时，如何管理和处理事务。每个传播级别都对应不同的行为，以确保在复杂的事务场景中维护数据的一致性和隔离性。以下是Spring框架支持的事务传播级别：
>
> 1. **REQUIRED（默认）：** 如果当前没有事务，就新建一个事务；如果已经存在一个事务中，加入到这个事务中。这是最常见的传播级别，适用于大多数情况。
> 2. **SUPPORTS：** 如果当前没有事务，就以非事务方式执行；如果已经存在一个事务，就加入到这个事务中。适用于不需要强制执行事务的情况，允许在事务上下文中执行，也允许在非事务上下文中执行。
> 3. **MANDATORY：** 强制要求当前存在一个事务，否则抛出异常。适用于需要强制执行事务的情况，如果没有事务，将会抛出异常。
> 4. **REQUIRES_NEW：** 总是新建一个事务，如果当前存在一个事务，就将其挂起。适用于需要独立的事务，不受外部事务影响的情况。
> 5. **NOT_SUPPORTED：** 总是以非事务方式执行，如果当前存在一个事务，就将其挂起。适用于不需要事务支持的情况，不论外部是否存在事务。
> 6. **NEVER：** 总是以非事务方式执行，如果当前存在一个事务，就抛出异常。适用于不允许在事务中执行的情况。
> 7. **NESTED：** 如果当前存在一个事务，就在嵌套事务内执行；如果没有事务，就新建一个事务。它类似于`REQUIRED`，但允许嵌套事务，嵌套事务独立于外部事务，但受其影响。
>
> 这些传播级别可以通过`@Transactional`注解或XML配置来指定，用于控制方法之间的事务行为。选择适当的传播级别取决于具体的业务需求和数据访问模式，以确保事务的一致性和隔离性。
>
>
> ![image-20230927174047795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230927174047795.png)
>
> ```java
> (rolling back on {@link RuntimeException} and {@link Error} but not on checked exceptions).
> ```
>
> 可以使用`@Transactional`注解的`rollbackFor`和`noRollbackFor`属性来自定义回滚规则



# Spring整合Mybatis

![image-20221104134421963](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104134421963.png)

![image-20221104135114409](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104135114409.png)

**与原本配置的对照**

![image-20221104141004084](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104141004084.png)

![image-20221104141012970](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104141012970.png)

![image-20221104141026421](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104141026421.png)

# Spring整合Junit

![image-20221104185942928](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104185942928.png)

![image-20221104185604997](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104185604997.png)

![image-20221104185854032](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221104185854032.png)