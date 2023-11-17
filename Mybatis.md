# Mybatis

![image-20221031165504515](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031165504515.png)

MyBatis 轻量级，性能出色 SQL 和 Java 编码分开，功能边界清晰。Java代码专注业务、SQL语句专注数据 开发效率稍逊于HIbernate，但是完全能够接受

mybatis是一个优秀的基于java的持久层框架，它**内部封装了jdbc**，使**开发者只需要关注sql语句本身**，而不需要花费精力去处理加载驱动、创建连接、创建statement等繁杂的过程。

mybatis通过xml或注解的方式将要执行的各种statement配置起来，并通过java对象和statement中sql的动态参数进行映射生成最终执行的sql语句，最后由mybatis框架执行sql并将结果映射为java对象并返回。

**MyBatis的主要设计目**的就是让我们对执行SQL语句时对输入输出的数据管理更加方便，所以**方便地写出SQL和方便地获取SQL的执行结果才是MyBatis的核心**竞争力。

**Mybatis的功能架构分为三层**：

**API接口层**：提供给外部使用的接口API，开发人员通过这些本地API来操纵数据库。接口层一接收到调用请求就会调用数据处理层来完成具体的数据处理。

**数据处理层**：负责具体的SQL查找、SQL解析、SQL执行和执行结果映射处理等。它主要的目的是根据调用的请求完成一次数据库操作。

**基础支撑层**：负责最基础的功能支撑，包括连接管理、事务管理、配置加载和缓存处理，这些都是共用的东西，将他们抽取出来作为最基础的组件。为上层的数据处理层提供最基础的支撑。

[MyBatis3 官方网站](https://mybatis.org/mybatis-3/)

![image-20230302143022452](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230302143022452.png)

![image-20230302143132973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230302143132973.png)

## **什么是ORM**

**对象关系映射（Object Relational Mapping，简称ORM）**， 简单的说，**ORM是通过使用描述对象和数据库之间映射的元数据，将java程序中的对象自动持久化到关系数据库中**。本质上就是将数据从一种形式转换到另外一种形式，具体如下：

具体映射：

1. 数据库的表（table） --> 类（class）
2. 记录（record，行数据）--> 对象（object）
3. 字段（field）--> 对象的属性（attribute）

![image-20221031170018003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031170018003.png)

### 什么是全自动ORM？

ORM框架可以根据对象关系模型直接获取，查询关联对象或者关联集合对象，**简单而言使用全自动的ORM框架查询时可以不再写SQL**。**典型的框架如Hibernate**； 因为Spring-data-jpa很多代码也是Hibernate团队贡献的，所以spring-data-jpa也是全自动ORM框架。

### MyBatis是半自动ORM？

Mybatis 在查询关联对象或关联集合对象时，**需要手动编写 sql 来完成，所以，称之为半自动ORM 映射工具。**

（PS: 正是由于MyBatis是半自动框架，基于MyBatis技术栈的框架开始考虑兼容MyBatis开发框架的基础上提供自动化的能力，比如**MyBatis-plus等框架**）

## 搭建MyBatis

引入相关依赖

![image-20221031181555799](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031181555799.png)

创建MyBatis的核心配置文件

![image-20221031181949395](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031181949395.png)

创建mapper接口

![image-20221031182129813](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031182129813.png)

创建MyBatis的映射文件

![image-20221031182753047](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031182753047.png)

加入log4j日志功能

![image-20221031183258692](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031183258692.png)

通过junit测试功能

![image-20221031183047509](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031183047509.png)

执行Test console输出

![image-20221031183328746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031183328746.png)

## CRUD操作

![image-20221031192649874](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031192649874.png)

## 核心配置文件

![image-20221031225603699](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031225603699.png)

![image-20221031230703843](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031230703843.png)

## IDEA中设置file模板templates

![image-20221031232628668](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221031232628668.png)



## MyBatis获取参数值的两种方式（重点）

> 在MyBatis中，`#{} `和 `${}` 是两种不同的参数占位符，它们的主要区别在于参数替换的时机和安全性。
>
> - `#{} `参数占位符是预编译的，会将传入的参数都当作一个字符串，然后将其转义，最终生成一个带有占位符的SQL语句。在执行SQL语句的时候，MyBatis会使用预编译语句来替换这个占位符，这样可以有效避免SQL注入攻击。**#{}会自动在左右两边加`' '`**
>
> - `${}` 参数占位符是直接替换传入的参数，不进行任何处理。在生成SQL语句时，MyBatis会将`${}`替换为传入的参数值，这样容易导致SQL注入攻击。因此，`${}` 参数占位符不太安全，不建议在动态SQL语句中使用。

### ${} 

（相当于字符串拼接 需要'${}'使用单引号）

### **#{}** 

(相当于？占位符 推荐使用)

### 实体类类型的参数

![image-20221101141054950](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101141054950.png)

### 使用@Param标识参数

**单个字面量类型的参数**

**多个字面量类型的参数**

**map集合类型的参数**

![image-20221101142601574](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101142601574.png)

![image-20221101143018973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101143018973.png)

## @Param注解

识别到使用了@Param注解的话

底层在在map集合中储存**以@Param的value为键** **以及 param*为键**  **以参数为值**

![image-20221101150032157](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101150032157.png)

## Mybatis的各种查询功能

### 查询一个实体类对象（一条记录）

#### 可以使用User对象来作为返回值

![image-20221101152837265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101152837265.png)

#### 也可以使用List<User>集合来作为返回值

![image-20221101153457874](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101153457874.png)

### 查询多条记录

#### 只能使用List<User>集合来作为返回值

![image-20221101153707383](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101153707383.png)

### 查询单行单列

#### 可以使用对应的数据类型来作为返回值

![image-20221101154345506](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101154345506.png)

### 查询一条数据为map集合

**Map集合是无序的 不可重复的**

**查询多条数据的时候不能直接使用Map<String,Integer>作为返回值类型**

![image-20221101154925686](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101154925686.png)

### 查询多条数据为map集合

#### List<Map<String,Object>>

![image-20221101155545213](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101155545213.png)

#### @MapKey

**使用@MapKey注解指定的value为要作为Map集合的键** 
**使用一个Primary Key的作为Map集合的键**

![image-20221101160203246](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101160203246.png)

## 特殊的SQL执行（使用${}）

### 模糊查询

**注意#{}会自动在左右两边加' '**

![image-20221101184809634](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101184809634.png)

### 批量删除

delete from table **where id in** (1,2,3,4,5,6)方式实现批量删除时候是要使用**${}**的 

![image-20221101190022473](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101190022473.png)

### 动态设置表名字

由于mysql的sql语句的表名不能加 ' ' 单引号 因此在动态的设置表名的时候要使用${}

![image-20221101191145795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101191145795.png)

## 获取自动递增的主键

处理数据中 **遇到一对多或者多对多的情况时**需要考虑到**获取自增的主键** 使用以下两个属性进行配置

**useGeneratedKeys="true"**

**keyProperty="参数对象的某个属性"**

![image-20221101192819637](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101192819637.png)

![image-20221101192632541](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101192632541.png)

## 内部类指定使用$

![image-20230207214120896](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230207214120896.png)

## 自定义映射resultMap

### resultMap处理字段和属性的映射关系

#### 问题：

**在select查询的sql是通过底层反射调用setXxx()方法来将查询到的结果转换成一个Java的实体类对象**
**要求setXxx()的方法名要与数据库表中的字段名保持一致**

![image-20221101223048284](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101223048284.png)

#### 解决方式

方式二：在select查询语句中给字段名as一个别名

![image-20221101223347318](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101223347318.png)

方式二：

```xml
<!--设置Mybatis的全局settings-->
    <settings>
        <!--将_自动映射为驼峰式 emp_name > empName-->
        <setting name="mapUnderscoreToCamelCase" value="true"/><!--这里默认为false 手动设置为true即可 -->
    </settings>
```

![image-20221101223821044](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101223821044.png)

方式三：

**自定义映射resultMap**

![image-20221101225450472](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101225450472.png)

![image-20221101225109268](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221101225109268.png)

### 多对一映射处理

![image-20221102003659457](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102003659457.png)

#### 级联方式处理映射关系

```java
<resultMap id="empDeptMap" type="Emp">
    <id column="eid" property="eid"></id>
    <result column="ename" property="ename"></result>
    <result column="age" property="age"></result>
    <result column="sex" property="sex"></result>
    <result column="did" property="dept.did"></result>
    <result column="dname" property="dept.dname"></result>
</resultMap>
<!--Emp getEmpAndDeptByEid(@Param("eid") int eid);-->
<select id="getEmpAndDeptByEid" resultMap="empDeptMap">
    select emp.*,dept.* from t_emp emp left join t_dept dept on emp.did = dept.did where emp.eid = #{eid}
</select>
```

#### 使用association处理映射关系(常用)

![image-20221102003503641](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102003503641.png)

#### 分步查询（重点掌握 ）

分步查询的优点：**可以实现延迟加载**，但是必须在核心配置文件中设置全局配置信息：

**将sql以及查询结果中的某个字段设置为分步查询的条件**

![image-20221102012829838](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102012829838.png)

## 一对多映射关系处理

### Collection

![image-20221102102506767](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102102506767.png)

### 分布查询

![image-20221102104732987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102104732987.png)

**collection标签效果一样**

![image-20221102105134119](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102105134119.png)

## 延迟加载（分布查询的好处）

### **全局设置：**

**开启延迟加载需要进行全局配置**

**lazyLoadingEnabled：**延迟加载的全局开关。当开启时，所有关联对象都会延迟加载

aggressiveLazyLoading：当开启时，任何方法的调用都会加载该对象的所有属性。 否则，每个 属性会按需加载（目前版本默认false 无需手动设置）

### **局部设置：**

collection中的**fetchType属性**设置当前的分步查询是否使用延迟加载，**fetchType="lazy(延迟加 载)|eager(立即加载)"**

#### Instance：

![image-20221102094947130](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102094947130.png)

## 动态SQL

Mybatis框架的动态SQL技术是一种**根据特定条件动态拼装SQL语句**的功能，它存在的意义是为了**解决拼接SQL语句字符串时的痛点问题**

| 元素                                                         | 作用                              | 备注                    |
| ------------------------------------------------------------ | --------------------------------- | ----------------------- |
| [if](http://c.biancheng.net/mybatis/if.html)                 | 判断语句                          | 单条件分支判断          |
| [choose（when、otherwise）](http://c.biancheng.net/mybatis/choose-when-otherwise.html) | 相当于 Java 中的 switch case 语句 | 多条件分支判断          |
| [trim](http://c.biancheng.net/mybatis/trim.html)、[where](http://c.biancheng.net/mybatis/where.html) | 辅助元素                          | 用于处理一些SQL拼装问题 |
| [foreach](http://c.biancheng.net/mybatis/foreach.html)       | 循环语句                          | 在in语句等列举条件常用  |
| [bind](http://c.biancheng.net/mybatis/bind.html)             | 辅助元素                          | 拼接参数                |

### if

if标签可**通过test属性的表达式进行判断**，若**表达式的结果为true，则标签中的内容会执行**；反之标签中的内容不会执行

```xml
<if test="判断条件">
    SQL语句
</if>
```

![image-20221102214520527](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102214520527.png)

### where

**where和if一般结合使用：** 

a>**若where标签中的if条件都不满足**，则where标签没有任何功能，即**不会添加where关键字** 

b>**若where标签中的if条件满足**，则where标签**会自动添加where关键字**，并将条件**最前方多余的 and去掉** 

**注意：where标签不能去掉条件最后多余的and**

```xml
<where>
    <if test="判断条件">
        AND/OR ...
    </if>
</where>
```

![image-20221102215324477](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102215324477.png)

### trim

**trim可以实现where的功能 并且解决where无法去除掉sql语句中后面的内容的问题**

where xxx and xxx

```
trim用于去掉或添加标签中的内容
常用属性：
prefix：在trim标签中的内容的前面添加某些内容
prefixOverrides：在trim标签中的内容的前面去掉某些内容
suffix：在trim标签中的内容的后面添加某些内容
suffixOverrides：在trim标签中的内容的后面去掉某些内容
```

![image-20221102220542754](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102220542754.png)

### choose、when、otherwise

**choose、when、otherwise**相当于**if.......else if.......else**

```xml
<choose>
    <when test="判断条件1">---------<!--<if>-->
        SQL语句1
    </when >
    <when test="判断条件2">---------<!--<else if>-->
        SQL语句2
    </when >
    <when test="判断条件3">---------<!--<else if>-->
        SQL语句3
    </when >
    <otherwise>--------------------<!--<else>-->
        SQL语句4
    </otherwise>
</choose>
```

![image-20221102224438964](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102224438964.png)

### foreach

对于一些 SQL 语句中含有 in 条件，需要迭代条件集合来生成的情况，**可以使用 foreach 来实现 SQL 条件的迭代**

Mybatis **foreach 标签用于循环语句**，**它很好的支持了数据和 List、set 接口的集合**

foreach 标签主要有以下属性，说明如下。

- **item：**表示集合中每一个元素进行迭代时的别名。
- **index：**指定一个名字，表示在迭代过程中每次迭代到的位置。
- **open：**表示该语句以什么开始（既然是 in 条件语句，所以必然以`(`开始）。
- **separator：**表示在每次进行迭代之间以什么符号作为分隔符（既然是 in 条件语句，所以必然以`,`作为分隔符）。
- **close：**表示该语句以什么结束（既然是 in 条件语句，所以必然以`)`开始）。
- 使用 foreach 标签时，**最关键、最容易出错的是 collection 属性**，该属性是**必选的**，但在不同情况下该属性的值是不一样的，主要有以下 3 种情况：
  - 如果传入的是单参数且参数类型是一个 List，collection 属性值为 list。
  - 如果传入的是单参数且参数类型是一个 array 数组，collection 的属性值为 array。
  - 如果传入的参数是多个，需要把它们封装成一个 Map，当然单参数也可以封装成 Map。Map 的 key 是参数名，collection 属性值是传入的 List 或 array 对象在自己封装的 Map 中的 key。

```xml
<foreach item="item" index="index" collection="list|array|map key" open="(" separator="," close=")">
    参数值
</foreach>
```

List集合

![image-20221102233421399](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102233421399.png)

数组

![image-20221102233707056](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102233707056.png)

### SQL片段

sql片段，可以**记录一段公共sql片段**，在使用的地方**通过include标签进行引入**

![image-20221102234610040](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221102234610040.png)

### set

在 Mybatis 中，**update 语句可以使用 set 标签动态更新列**。set 标签可以**为 SQL 语句动态的添加 set 关键字**，**剔除追加到条件末尾多余的逗号** 	

## MyBatis的缓存

**缓存**可以**将数据保存在内存中**，是互联网系统常常用到的。目前流行的缓存服务器有 **MongoDB、Redis、Ehcache** 等。**缓存是在计算机内存上保存的数据，读取时无需再从磁盘读入**，因此**具备快速读取和使用的特点**

### 一级缓存

一级缓存是**SqlSession级别**的，通过**同一个SqlSession查询的数据会被缓存**，**下次查询相同的数据**，就会**从缓存中直接获取**，**不会从数据库重新访问**

**默认情况下，MyBatis 只开启一级缓存**

一级缓存是基于 **PerpetualCache（MyBatis自带）**的 **HashMap 本地缓存**，作用范围为 session 域内。**当 session flush（刷新）或者 close（关闭）之后**，**该 session 中所有的 cache（缓存）就会被清空**

![image-20221103160304108](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103160304108.png)

![image-20221103160638484](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103160638484.png)

#### 使一级缓存失效的四种情况：

##### **不同的SqlSession对应不同的一级缓存** 

##### **同一个SqlSession但是查询条件不同**

##### **同一个SqlSession两次查询期间执行了任何一次增删改操作** 

##### **同一个SqlSession两次查询期间手动清空了缓存**

![image-20221103163509347](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103163509347.png)

![image-20221103163715991](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103163715991.png)

### 二级缓存

**二级缓存是SqlSessionFactory级别**，通过**同一个SqlSessionFactory创建的SqlSession查询的结果会被缓存**；此后若再次执行相同的查询语句，结果就会从缓存中获取

**开启二级缓存后**，会使用CachingExecutor装饰Executor，进入一级缓存的查询流程前，先在CachingExecutor进行二级缓存的查询，具体的工作流程如下所示。

二级缓存开启后，**同一个namespace下的所有操作语句，都影响着同一个Cache**，即**二级缓存被多个SqlSession共享**，**是一个全局的变量**。
 当开启缓存后，数据的查询执行的流程就是 **二级缓存 -> 一级缓存 -> 数据库。**

![image-20221103164144414](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103164144414.png)

#### 二级缓存配置

![image-20221103164306706](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103164306706.png)

![image-20221103164609940](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103164609940.png)

| 属性          | 说明                                                         |
| ------------- | ------------------------------------------------------------ |
| eviction      | 代表的是缓存回收策略，目前 MyBatis 提供以下策略。LRU：使用较少，移除最长时间不用的对象；FIFO：先进先出，按对象进入缓存的顺序来移除它们；SOFT：软引用，移除基于垃圾回收器状态和软引用规则的对象；WEAK：弱引用，更积极地移除基于垃圾收集器状态和弱引用规则的对象。 |
| flushInterval | 刷新间隔时间，单位为毫秒，这里配置的是 100 秒刷新，如果省略该配置，那么只有当 SQL 被执行的时候才会刷新缓存。 |
| size          | 引用数目，正整数，代表缓存最多可以存储多少个对象，不宜设置过大。设置过大会导致内存溢出。这里配置的是 1024 个对象。 |
| readOnly      | 只读，默认值为 false，意味着缓存数据只能读取而不能修改，这样设置的好处是可以快速读取缓存，缺点是没有办法修改缓存。 |

![image-20221103165713909](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103165713909.png)

![image-20221103165754661](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103165754661.png)

#### 使二级缓存失效的情况：

**两次查询之间执行了任意的增删改**，会使一级和二级缓存同时失效

### MyBatis缓存查询的顺序

**先查询二级缓存**，因为二级缓存中可能会有其他程序已经查出来的数据，可以拿来直接使用。 

**如果二级缓存没有命中，再查询一级缓存** 

**如果一级缓存也没有命中，则查询数据库** 

**SqlSession关闭之后，一级缓存中的数据会写入二级缓存**

## 整合第三方缓存EHCache

| jar包名称       | 作用                     |
| --------------- | ------------------------ |
| mybatis-ehcache | Mybatis和EHCache的整合包 |
| ehcache         | EHCache核心包            |

![image-20221103183151226](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103183151226.png)

### EHCache配置文件说明

![image-20221103183727701](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103183727701.png)

## 加入logback日志

| jar包名称       | 作用                            |
| --------------- | ------------------------------- |
| slf4j-api       | SLF4J日志门面包                 |
| logback-classic | 支持SLF4J门面接口的一个具体实现 |

![image-20221103183240888](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103183240888.png)

![image-20221103183436401](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103183436401.png)

## Mybatis逆向工程



![image-20221103183804217](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103183804217.png)

![image-20221103202939778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103202939778.png)

![image-20221103203142791](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103203142791.png)

## **Query By Criteria**--QBC

[代码生成器原理和使用、QBC、Mybattis扩展 - payn - 博客园 (cnblogs.com)](https://www.cnblogs.com/-zhuang/articles/10369082.html)

## 分页插件

![image-20221103210955589](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103210955589.png)

![image-20221103211817252](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221103211817252.png)

**常用数据：** 

pageNum：当前页的页码 

pageSize：每页显示的条数 

size：当前页显示的真实条数 

total：总记录数 

pages：总页数 

prePage：上一页的页码 

nextPage：下一页的页码

isFirstPage/isLastPage：是否为第一页/最后一页 

hasPreviousPage/hasNextPage：是否存在上一页/下一页 

navigatePages：导航分页的页码数 

navigatepageNums：导航分页的页码，[1,2,3,4,5]