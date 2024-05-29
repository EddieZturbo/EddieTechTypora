# Maven高级

## 分模块开发

将原始模块**按照功能拆分成若干个子模块**，**方便模块间的相互调用**，**接口共享**

项目中的**每一层都可以单独维护**，也**可以很方便的被别人使用**

![image-20221108201703441](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108201703441.png)

![image-20221108201635795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108201635795.png)

![image-20221108201803280](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108201803280.png)

![image-20221108202239523](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202239523.png)

![image-20221108202507246](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202507246.png)



## 依赖管理

### 依赖传递 

![image-20221108203155134](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203155134.png)

![image-20221108202831103](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202831103.png)

![image-20221108202604874](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202604874.png)

![image-20221108202810537](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202810537.png)

### 依赖冲突

![image-20221108202909239](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202909239.png)

![image-20221108202958596](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108202958596.png)

![image-20221108203042847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203042847.png)

### 可选依赖 

可选依赖指**对外隐藏**当前所依赖的资源---**不透明**

（角度是站在**我们的依赖要被别人使用** 我们可以**通过可选依赖来设置隐藏我们使用的某些依赖** **不让别人使用**）

![image-20221108203356631](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203356631.png)

![image-20221108203652426](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203652426.png)

### 排除依赖

排除依赖指**主动断开依赖的资源**，被排除的资源无需指定版本---**不需要**

（角度是站在**我们要使用别人的依赖时**，我们**指明要排除的依赖** 从而**不使用即不需要别人的某些依赖**）

![image-20221108203543761](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203543761.png)

![image-20221108203656300](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203656300.png)

## 聚合和继承

### 聚合

**聚合工程主要是用来管理项目**

![image-20221108204552453](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108204552453.png)

![image-20221108204834314](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108204834314.png)

![image-20221108204954767](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108204954767.png)

### 继承

![image-20221108205147507](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108205147507.png)

![image-20221108205129584](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108205129584.png)

![image-20221108220846408](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108220846408.png)

![image-20221108221314374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108221314374.png)

### DependencyManagement

**只是声明依赖**并**不实现引入**；因此**子工程中**需要**显示的声明需要用的依赖**

只有**在子项目中引入了相关依赖**并且**没有指定版本号**；则**是从父项目DependencyManagement中继承**（version和scope都会继承）



通常在**父工程的POM中声明** 目的是**子工程**在声明依赖时**不用显示的声明版本号**；而是**使用和父工程中指定的版本号保持一致**

在子工程中可以省略版本号指定；即和父工程保持一致；（**若子工程单独指定了版本号则以子工程的为准**）

maven会沿着父子层次向上走，直到找到拥有DependencyManagement元素的项目；并使用DependencyManagement指定的版本号

可以**避免**在所有的子项目中**频繁的声明版本号** 同时**避免版本号错乱**（不一致）的麻烦

**若需要对项目中的所有依赖进行版本变更** **只需在父工程**中**更新一处即可**

### 聚合与继承的区别

![image-20221108203908358](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221108203908358.png)

## Pom War Jar

> ### pom工程
>
> pom工程用在父级工程或聚合工程中。用来做jar包的版本控制。
>
> pom打出来可以作为其他项目的maven依赖,比如你写了两个工程，工程a写了一些工具类，然后你可以把它打成pom，再在工程b里面添加a的依赖，然后你在工程b中就可以使用a定义好的工具类。
>
> Maven是以项目为中心的设计。POM(project object model)是Maven对一个单一项目的描述。没有POM的话，Maven是毫无用处的——POM是Maven的核心。是POM实现的并驱动了这种以模型来描述的构建方式。
>
> ### war工程
>
> **需要部署到额外的例如Tomcat服务器上进行项目运行**
>
> war工程将会打包成war，发布在服务器上的工程，如网站或服务。所以service通常打包成war包。war常用于java web工程，但也不是绝对的，war也可以用java -jar xxx.war执行，前提是你有配置main函数入口
>
> war包是Sun提出的一种web应用程序格式，与jar类似，是很多文件的压缩包。war包中的文件按照一定目录结构来组织。根据其根目录下包含有html和jsp文件，或者包含有这两种文件的目录，另外还有WEB-INF目录。通常在WEB-INF目录下含有一个web.xml文件和一个classes目录，web.xml是这个应用的配置文件，而classes目录下则包含编译好的servlet类和jsp，或者servlet所依赖的其他类(如JavaBean)。通常这些所依赖的类也可以打包成jar包放在WEB-INF下的lib目录下。
>
> ### jar工程
>
> jar工程将会打包成jar用作jar包使用。**可直接运行 例如Spring Boot项目内嵌Tomcat服务器**
>
> jar是maven出来之前三方库普遍使用的方式，比较常见的是jdbc驱动包，一般从官网下载下来的都是jar文件。也可以打成可执行文件，类似.exe那样的，用命令java -jar xxx.jar执行。
>
> 一个可执行的jar 文件是一个自包含的 Java 应用程序，它存储在特别配置的JAR 文件中，可以由 JVM 直接执行它而无需事先提取文件或者设置类路径。要运行存储在非可执行的 JAR 中的应用程序，必须将它加入到您的类路径中，并用名字调用应用程序的主类。但是使用可执行的 JAR 文件，我们可以不用提取它或者知道主要入口点就可以运行一个应用程序。可执行 JAR 有助于方便发布和执行 Java 应用程序。

## 跳过Test

![image-20221204162053284](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204162053284.png)

## 发布到仓库

![image-20221204162146471](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204162146471.png)

## 属性



## 多环境配置与应用



## 私服



## mvn命令

> 常见的mvn运行参数：
>
> 1. clean：删除target目录，即删除编译后生成的文件，包括编译产生的class文件、jar包、war包等。
>
> 2. compile：编译Java源代码。
>
> 3. test：运行测试用例。
>
> 4. package：打包，将编译后的Java源代码打包成jar或war包。
>
> 5. install：安装打包好的jar或war包到本地仓库，以便其他项目可以引用。
>
> 6. deploy：将打包好的jar或war包部署到远程仓库，以便其他开发人员或项目可以引用。
>
> 7. -D参数：通过-D参数可以设置系统属性，例如mvn -Dmaven.test.skip=true表示跳过测试。
>
>    > 常见的-D参数：
>    >
>    > 1. -Dmaven.test.skip=true：跳过测试，不执行单元测试。
>    > 2. -DskipTests=true：跳过测试，不执行单元测试。
>    > 3. -Dmaven.compiler.source=1.8：指定Java源代码的版本，例如1.6、1.7、1.8等。
>    > 4. -Dmaven.compiler.target=1.8：指定生成的Java字节码的版本，例如1.6、1.7、1.8等。
>    > 5. -Dmaven.compiler.encoding=UTF-8：指定编译时使用的字符集，例如UTF-8、GBK等。
>    > 6. -Dfile.encoding=UTF-8：指定运行时使用的字符集，例如UTF-8、GBK等。
>    > 7. -Djava.net.preferIPv4Stack=true：启用IPv4协议。
>    > 8. -Djava.net.preferIPv6Addresses=true：启用IPv6协议。
>    > 9. -Dmaven.repo.local=/path/to/local/repository：指定本地仓库的位置。
>    > 10. -Dmaven.home=/path/to/maven：指定Maven安装的路径。
>    > 11. -Dhttps.protocols=TLSv1.2：指定使用的HTTPS协议版本，例如TLSv1、TLSv1.1、TLSv1.2等。
>    > 12. -Djavax.net.ssl.trustStore=/path/to/truststore.jks：指定SSL证书的信任库路径。
>    > 13. -Djavax.net.ssl.trustStorePassword=password：指定SSL证书的信任库密码。
>    > 14. -Dmaven.wagon.http.ssl.insecure=true：跳过SSL验证。
>    >
>    > 以上是一些常用的-D参数，可以根据需要组合使用。使用-D参数可以在不修改POM文件的情况下，对Maven进行配置和定制。
>
> 8. -X参数：启用debug模式，输出更详细的日志信息。
>
> 9. -U参数：强制更新依赖项，即使它们已经存在于本地仓库中也要重新下载。
>
> 10. -e参数：输出详细的错误信息，包括堆栈跟踪等。
>
> 11. -P参数：指定使用哪个profile。例如，mvn clean install -P dev表示使用名为dev的profile。
>
> 12. -pl参数：指定构建哪些模块。例如，mvn clean install -pl module1,module2表示只构建module1和module2模块。
>
> 13. -am参数：同时构建依赖该模块的所有模块。例如，mvn clean install -pl module1 -am表示构建module1以及依赖module1的所有模块。
>
> 以上是一些常用的mvn运行参数，可以根据需要组合使用。使用mvn命令时，可以通过mvn -h或mvn --help命令获取更多帮助信息。

```bash
git clone https://github.com/crossoverJie/cim.git
cd cim
mvn -Dmaven.test.skip=true clean package
```

