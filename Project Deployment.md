# Project Deployment

![image-20240228181851962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228181851962.png)

## Front-end Project

### Vue

#### Tomcat

> - config
>   - 配置应用的基础路径
>   - 设置构建后的输出目录（dist）
> - 执行build命令 将Vue项目打包构建到dist目录中

![image-20240228185757804](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228185757804.png)

> - 在Tomcat的webapps目录下新建一个与应用的基础路径一致的文件夹
> - 将构建好的dist目录中的所有项目 cp到 与应用的基础路径一致的文件夹中

![image-20240228185031009](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228185031009.png)

> - 运行Tomcat服务器
> - 访问 Tomcat所运行端口+应用的基础路径 即可正常访问部署好的Vue前端项目

![image-20240228185214977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228185214977.png)

#### Nginx

> - config
>   - 配置应用的基础路径
>   - 设置构建后的输出目录（dist）
> - 执行build命令 将Vue项目打包构建到dist目录中

![image-20240228185757804](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228185757804.png)

> 将构建好的dist文件夹 cp到 Nginx 的 html 目录下 并重命名文件夹名为应用的基础路径

![image-20240229161551730](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229161551730.png)

> 修改配置 Nginx 配置文件
> ```bash
> vim /etc/nginx/nginx.conf
> ```

![image-20240229162347854](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229162347854.png)

> 启动Nginx 访问项目

![image-20240229163355437](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229163355437.png)

#### Docker

#### Cloud

## Back-end Project

### Spring Boot

#### Tomcat（.war）

> - Extends the **SpringBootServletInitializer** class in the main class.
> - Override the **Configure** method.

![image-20240229090848551](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229090848551.png)

> - Marked the embedded servlet container（Tomcat） as **provided**.

![image-20240229091129160](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229091129160.png)

> - 修改pom.xml文件 配置项目打包方式为war

![image-20240228235416776](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228235416776.png)

> - 使用Maven命令进行打包
>   - 先clean项目
>   - 然后package项目
> - 获取到target包下的.war包

![image-20240228235728721](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240228235728721.png)

> - 将构建好的.war包cp到Tomcat服务的webapps目录下

![image-20240229000107640](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229000107640.png)

> startup

![image-20240229091712335](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229091712335.png)

> 根据运行起来的Tomcat服务 调整前端应用请求到后端服务的URL(Tomcat运行端口号/war文件名)

![image-20240229092730878](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229092730878.png)

#### .jar

> 使用spring boot initializer 创建的项目 默认的配置是使用内嵌的Tomcat 项目打包方式为jar包 可直接运行

> 使用Maven命令进行打包
>
> - 先clean项目
> - 然后package项目

![image-20240229093938797](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229093938797.png)

> java -jar [项目.jar] 命令运行项目

![image-20240229093635193](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229093635193.png)

![image-20240229094637742](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229094637742.png)

##### java -jar

> `java -jar` 命令是 Java 运行时环境（JRE）提供的一个命令行工具，**用于执行 Java 应用程序的 JAR 文件**
>
> ```bash
> java -jar <JAR文件路径> [可选参数]
> ```
>
> 

**配置参数**

> ```bash
> java -jar -Xms512m -Xmx2g .\JobManagement_BackEnd-0.0.1-SNAPSHOT.jar --server.port=9668 --spring.profiles.active=dev
> ```
>
> - **指定端口**：
>   - 使用 `--server.port` 参数来指定端口
>     `java -jar your-application.jar --server.port=8080`。
> - **JVM 参数**：
>   - 通过 `-X` 参数来设置 JVM 的一些配置
>     `-Xms` 和 `-Xmx` 来设置堆内存的初始大小和最大大小。
>   - 通过 `-D` 参数来设置系统属性
>     `-Dfile.encoding=UTF-8` 来设置文件编码为 UTF-8。
> - **指定 Spring Boot 配置文件**：
>   - 使用 `--spring.config.location` 参数来指定配置文件的位置
>     `java -jar your-application.jar --spring.config.location=classpath:/application.properties`。
>   - 使用 `--spring.profiles.active` 参数来指定活动配置文件
>      `java -jar your-application.jar --spring.profiles.active=dev`。

![image-20240229110636950](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229110636950.png)

![image-20240229110450163](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229110450163.png)

**传递参数**

> `[可选参数]` 是用于向 Java 应用程序传递命令行参数的。这些参数会被传递给应用程序的 `main` 方法
>
> ```bash
> java -jar myapp.jar arg1 arg2
> ```
>
> ```java
> public static void main(String[] args) {
>     for (String arg : args) {
>         System.out.println(arg);
>     }
> }
> ```



#### Docker

#### Cloud



