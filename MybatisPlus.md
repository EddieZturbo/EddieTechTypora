# MybatisPlus

[简介 | MyBatis-Plus (baomidou.com)](https://www.baomidou.com/pages/24112f/)

![image-20221111085121608](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111085121608.png)

![image-20221111085129832](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111085129832.png)

![image-20221111085140743](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111085140743.png)

## 快速开始

搭建Spring Boot

![image-20221111085409562](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111085409562.png)

导入依赖

配置信息在yml文件中

![image-20221111085700459](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111085700459.png)

Lombok方式编写实体类

![image-20221111092035023](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111092035023.png)

DAO接口 extends BaseMpper<实体类>

@Mapper注解配置Mapper映射

或者在启动类上添加@MapperScan（“指明dao所在包”）将所有的dao接口进行Mapper映射

![image-20221111092215679](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111092215679.png)

测试

![image-20221111092308756](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111092308756.png)

## Lombok

![image-20221111095846064](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095846064.png)

![image-20221111095837069](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095837069.png)

![image-20221111095900057](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095900057.png)

## 标准数据层开发

### 标准CRUD使用

![image-20221111095314547](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095314547.png)

![image-20221111095322557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095322557.png)

![image-20221111095526688](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095526688.png)

![image-20221111095710154](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111095710154.png)

### 分页功能

配置MybatisPlus的分页拦截器

![image-20221111101701780](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111101701780.png)

![image-20221111101710557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111101710557.png)

在yml文件中配置打印日志输出到console

![image-20221111102039181](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111102039181.png)

![image-20221111102029361](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111102029361.png)

## Console简化输出

**取消初始化spring日志打印**

**取消banner的打印**

![image-20221111102934041](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111102934041.png)

## DQL（查询）编程控制

### 条件查询

![image-20221111102333006](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111102333006.png)

#### QueryWrapper

**colunm的值容易写错 建议使用lambda表达式 方法引用getXxx**

![image-20221111103900392](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111103900392.png)

![image-20221111103617857](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111103617857.png)

#### QueryWrapper的基础上使用lambda

![image-20221111104304195](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111104304195.png)

#### LambdaQueryWrapper

![image-20221111104656272](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111104656272.png)

![image-20221112110902681](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112110902681.png)

### 多条件

#### and&or

![image-20221111105652319](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221111105652319.png)

#### null判定

![image-20221112105353121](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112105353121.png)

![image-20221112105918106](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112105918106.png)

### 查询投影 

#### 查询指定字段

**属性中有的字段就直接使用lamba方式**

**属性中没有的字段（聚合查询）就使用QueryWapper**

目前我们在查询数据的时候，什么都没有做**默认就是查询表中所有字段**的内容，我们所说的**查询投影** 即不查询所有字段，**只查询出指定内容的数据**

![image-20221112111818746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112111818746.png)

#### 聚合查询

**属性中没有的字段** 无法使用LambdaQueryWapper **要使用QueryWapper**

![image-20221112111952000](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112111952000.png)

![image-20221112114400168](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112114400168.png)

![image-20221112114048877](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112114048877.png)

![image-20221112114101398](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112114101398.png)

![image-20221112113716169](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112113716169.png)

![image-20221112114330928](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112114330928.png)

#### Group By分组

![image-20221112115206341](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112115206341.png)

### 查询条件设定

![image-20221112115856635](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112115856635.png)

#### 等值查询

![image-20221112120444473](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112120444473.png)

#### 范围查询

![image-20221112120458138](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112120458138.png)

|                         |                     |
| ----------------------- | ------------------- |
| lt()------小于--------< | less than           |
| le()-----小于等于--<=   | less than equals    |
| gt()-----大于-------->  | greater than        |
| ge()----大于等于-->=    | greater than equals |

![image-20221112120841431](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112120841431.png)

![image-20221112121000954](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112121000954.png)

#### 模糊查询

![image-20221112121259107](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112121259107.png)

![image-20221112130104571](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112130104571.png)

#### 排序查询

![image-20221112130608383](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112130608383.png)

![image-20221112130550900](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112130550900.png)

### 映射匹配兼容性

![image-20221112131616130](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112131616130.png)

## DML（增删改）编程控制

### id生成策略控制

![image-20221112132759231](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112132759231.png)

![image-20221112132934173](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112132934173.png)

![image-20221112133350597](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133350597.png)

![image-20221112133706356](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133706356.png)

![image-20221112133301157](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133301157.png)

![image-20221112133442693](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133442693.png)

![image-20221112133510063](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133510063.png)

![image-20221112133522570](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133522570.png)

### 雪花算法

![image-20221112133636070](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112133636070.png)

### 简化数据库表映射id生成策略的配置（.yml配置）

![image-20221112134154231](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112134154231.png)

### 多记录（批量）操作

#### 批量删除

![image-20221112134917848](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112134917848.png)

#### 批量查询

![image-20221112135134307](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112135134307.png)

### 逻辑删除

**非直接执行delete操作** 而**是执行update操作将deleted字段的值进行改变** 在**执行select语句时使用上where将已经删除的排除掉**

![image-20221112143339336](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112143339336.png)

![image-20221112141547154](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112141547154.png)

![image-20221112141527000](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112141527000.png)

![image-20221112142145411](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112142145411.png)

![image-20221112142314523](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112142314523.png)

### 全局配置逻辑删除

.yml中配置

![image-20221112142817587](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112142817587.png)

### 乐观锁

**秒杀场景**

类似于**CAS**的操作

这里**要配置OptimisticLockInterceptor**拦截器

会**在原本的update语句中**加上**set version+=1** 以及 **where version=version**

也就是会对version进行were条件判断 并且更新数据的同时 将version的值加上1

此时**一个用户更新后 version值被此用户改变了** **后面的用户在进行version值的were匹配**时就**无法匹配**上**进而无法进行update**

**保证了一个数据只能被一个用户更改**--秒杀中 当有用户抢到商品后 后续的用户无法进行购买

![image-20221112160123297](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112160123297.png)

![image-20221112160050590](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112160050590.png)

![image-20221112155452515](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112155452515.png)

![image-20221112154350792](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112154350792.png)

## 代码生成器

![image-20221112163135795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112163135795.png)

### 代码生成器实现

#### 步骤1:创建一个Maven项目

#### 代码2:导入对应的jar包

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.5.1</version>
    </parent>
    <groupId>com.itheima</groupId>
    <artifactId>mybatisplus_04_generator</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <properties>
        <java.version>1.8</java.version>
    </properties>
    <dependencies>
        <!--spring webmvc-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!--mybatisplus-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.4.1</version>
        </dependency>

        <!--druid-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.1.16</version>
        </dependency>

        <!--mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>

        <!--test-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!--lombok-->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.12</version>
        </dependency>

        <!--代码生成器-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-generator</artifactId>
            <version>3.4.1</version>
        </dependency>

        <!--velocity模板引擎-->
        <dependency>
            <groupId>org.apache.velocity</groupId>
            <artifactId>velocity-engine-core</artifactId>
            <version>2.3</version>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>

```

#### 步骤3:编写引导类

```java
@SpringBootApplication
public class Mybatisplus04GeneratorApplication {

    public static void main(String[] args) {
        SpringApplication.run(Mybatisplus04GeneratorApplication.class, args);
    }

}
```

#### 步骤4:创建代码生成类

```java
public class CodeGenerator {
    public static void main(String[] args) {
        //1.获取代码生成器的对象
        AutoGenerator autoGenerator = new AutoGenerator();

        //设置数据库相关配置
        DataSourceConfig dataSource = new DataSourceConfig();
        dataSource.setDriverName("com.mysql.cj.jdbc.Driver");
        dataSource.setUrl("jdbc:mysql://localhost:3306/mybatisplus_db?serverTimezone=UTC");
        dataSource.setUsername("root");
        dataSource.setPassword("root");
        autoGenerator.setDataSource(dataSource);

        //设置全局配置
        GlobalConfig globalConfig = new GlobalConfig();
        globalConfig.setOutputDir(System.getProperty("user.dir")+"/mybatisplus_04_generator/src/main/java");    //设置代码生成位置
        globalConfig.setOpen(false);    //设置生成完毕后是否打开生成代码所在的目录
        globalConfig.setAuthor("黑马程序员");    //设置作者
        globalConfig.setFileOverride(true);     //设置是否覆盖原始生成的文件
        globalConfig.setMapperName("%sDao");    //设置数据层接口名，%s为占位符，指代模块名称
        globalConfig.setIdType(IdType.ASSIGN_ID);   //设置Id生成策略
        autoGenerator.setGlobalConfig(globalConfig);

        //设置包名相关配置
        PackageConfig packageInfo = new PackageConfig();
        packageInfo.setParent("com.aaa");   //设置生成的包名，与代码所在位置不冲突，二者叠加组成完整路径
        packageInfo.setEntity("domain");    //设置实体类包名
        packageInfo.setMapper("dao");   //设置数据层包名
        autoGenerator.setPackageInfo(packageInfo);

        //策略设置
        StrategyConfig strategyConfig = new StrategyConfig();
        strategyConfig.setInclude("tbl_user");  //设置当前参与生成的表名，参数为可变参数
        strategyConfig.setTablePrefix("tbl_");  //设置数据库表的前缀名称，模块名 = 数据库表名 - 前缀名  例如： User = tbl_user - tbl_
        strategyConfig.setRestControllerStyle(true);    //设置是否启用Rest风格
        strategyConfig.setVersionFieldName("version");  //设置乐观锁字段名
        strategyConfig.setLogicDeleteFieldName("deleted");  //设置逻辑删除字段名
        strategyConfig.setEntityLombokModel(true);  //设置是否启用lombok
        autoGenerator.setStrategy(strategyConfig);
        //2.执行生成操作
        autoGenerator.execute();
    }
}
```

对于代码生成器中的代码内容，我们可以直接从官方文档中获取代码进行修改，

`https://mp.baomidou.com/guide/generator.html`

#### 步骤5:运行程序

运行成功后，会在当前项目中生成很多代码，代码包含`controller`,`service`，`mapper`和`entity`。

至此代码生成器就已经完成工作，我们能快速根据数据库表来创建对应的类，简化我们的代码开发。

### MP中Service的CRUD

回顾我们之前业务层代码的编写，编写接口和对应的实现类:

```java
public interface UserService{
	
}

@Service
public class UserServiceImpl implements UserService{

}
```

接口和实现类有了以后，需要在接口和实现类中声明方法

```java
public interface UserService{
	public List<User> findAll();
}

@Service
public class UserServiceImpl implements UserService{
    @Autowired
    private UserDao userDao;
    
	public List<User> findAll(){
        return userDao.selectList(null);
    }
}
```

MP看到上面的代码以后就说这些方法也是比较固定和通用的，那我来帮你抽取下，所以MP提供了一个Service接口和实现类，分别是:`IService`和`ServiceImpl`,后者是对前者的一个具体实现。

以后我们自己写的Service就可以进行如下修改:

```java
public interface UserService extends IService<User>{
	
}

@Service
public class UserServiceImpl extends ServiceImpl<UserDao, User> implements UserService{

}
```

修改以后的好处是，MP已经帮我们把业务层的一些基础的增删改查都已经实现了，可以直接进行使用。

编写测试类进行测试:

```java
@SpringBootTest
class Mybatisplus04GeneratorApplicationTests {

    private IUserService userService;

    @Test
    void testFindAll() {
        List<User> list = userService.list();
        System.out.println(list);
    }

}
```

**注意:**mybatisplus_04_generator项目中对于MyBatis的环境是没有进行配置，如果想要运行，需要提取将配置文件中的内容进行完善后在运行。

思考:在MP封装的Service层都有哪些方法可以用?

查看官方文档:`https://mp.baomidou.com/guide/crud-interface.html`,这些提供的方法大家可以参考官方文档进行学习使用，方法的名称可能有些变化，但是方法对应的参数和返回值基本类似。
