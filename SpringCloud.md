# SpringCloud

[Spring Cloud](https://spring.io/projects/spring-cloud)

Spring Cloud 是一款**基于 Spring Boot 实现**的**微服务框架**。Spring Cloud **源自 Spring 社区**，主要由 Pivotal 和 Netflix 两大公司提供技术迭代和维护

- **服务治理**：阿里巴巴开源的 Dubbo 和当当网在其基础上扩展出来的 DubboX、Netflix 的 Eureka 以及 Apache 的 Consul 等。
- **分布式配置管理**：百度的 Disconf、Netflix 的 Archaius、360 的 QConf、携程的 Apollo 以及 Spring Cloud 的 Config 等。
- **批量任务**：当当网的 Elastic-Job、LinkedIn 的 Azkaban 以及 Spring Cloud 的 Task 等。
- **服务跟踪**：京东的 Hydra、Spring Cloud 的 Sleuth 以及 Twitter 的 Zipkin 等。
- **……**

**特点**：

- 对于同一个微服务问题，各互联网公司给出的解决方案各不相同。
- 一个微服务框架或解决方案都只能解决微服务中的某一个或某几个问题，对于其他问题则无能为力

![image-20221204105524272](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204105524272.png)

![image-20221204110449260](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204110449260.png)

![image-20221204110806825](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204110806825.png)

![image-20221204111223491](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204111223491.png)

![image-20221204111301492](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204111301492.png)

## **Spring Cloud 常用组件**

Spring Cloud 包括 Spring Cloud Gateway、Spring Cloud Config、Spring Cloud Bus 等近 20 个服务组件，这些组件提供了**服务治理**、**服务网关**、**智能路由**、**负载均衡**、**熔断器**、**监控跟踪**、**分布式消息队列**、**配置管理**等领域的解决方案

| Spring  Cloud 组件 | 描述                                                         |
| ------------------ | ------------------------------------------------------------ |
| Eureka             | Spring Cloud Netflix 中的服务治理组件，包含服务注册中心、服务注册与发现机制的实现。 |
| Ribbon             | Spring Cloud Netflix 中的服务调用和客户端负载均衡组件。      |
| Hystrix            | 人称“豪猪哥”，Spring Cloud Netflix 的容错管理组件，为服务中出现的延迟和故障提供强大的容错能力。 |
| OpenFeign          | 基于 Ribbon 和 Hystrix 的声明式服务调用组件。                |
| Zuul               | Spring Cloud Netflix 中的网关组件，提供了智能路由、访问过滤等功能。 |
| Gateway            | 一个基于 Spring 5.0，Spring Boot 2.0 和 Project Reactor 等技术开发的网关框架，它使用 Filter 链的方式提供了网关的基本功能，例如安全、监控/指标和限流等。 |
| Config             | Spring Cloud 的配置管理工具，支持使用 Git 存储配置内容，实现应用配置的外部化存储，并支持在客户端对配置进行刷新、加密、解密等操作。 |
| Bus                | Spring Cloud 的事件和消息总线，主要用于在集群中传播事件或状态变化，以触发后续的处理，例如动态刷新配置。 |
| Stream             | Spring Cloud 的消息中间件组件，它集成了 Apache Kafka 和 RabbitMQ 等消息中间件，并通过定义绑定器作为中间层，完美地实现了应用程序与消息中间件之间的隔离。通过向应用程序暴露统一的 Channel 通道，使得应用程序不需要再考虑各种不同的消息中间件实现，就能轻松地发送和接收消息。 |
| Sleuth             | Spring Cloud 分布式链路跟踪组件，能够完美的整合 Twitter 的 Zipkin。 |

## Spring Boot 和 Spring Cloud

Spring Boot 和 Spring Cloud 都是 Spring 大家族的一员，它们在微服务开发中都扮演着十分重要的角色，两者之间既存在区别也存在联系。

**Spring Cloud 是基于 Spring Boot 实现的**，它不能独立创建工程或模块，更不能脱离 Spring Boot 独立运行。

1. **Spring Boot 和 Spring Cloud 分工不同**

Spring Boot 是一个基于 Spring 的快速开发框架，它能够帮助开发者迅速搭 Web 工程。在微服务开发中，Spring Boot 专注于快速、方便地开发单个微服务。

Spring Cloud 是微服务架构下的一站式解决方案。Spring Cloud 专注于全局微服务的协调和治理工作。换句话说，Spring Cloud 相当于微服务的大管家，负责将 Spring Boot 开发的一个个微服务管理起来，并为它们提供配置管理、服务发现、断路器、路由、微代理、事件总线、决策竞选以及分布式会话等服务。

2. **Spring Cloud 是基于 Spring Boot 实现的**

Spring Cloud 是基于 Spring Boot 实现的。与 Spring Boot 类似，Spring Cloud 也为提供了一系列 Starter，这些 Starter 是 Spring Cloud 使用 Spring Boot 思想对各个微服务框架进行再封装的产物。它们屏蔽了这些微服务框架中复杂的配置和实现原理，使开发人员能够快速、方便地使用 Spring Cloud 搭建一套分布式微服务系统。

3. **Spring Boot 和 Spring Cloud 依赖项数量不同**

Spring Boot 属于一种轻量级的框架，构建 Spring Boot 工程所需的依赖较少。

Spring Cloud 是一系列微服务框架技术的集合体，它的每个组件都需要一个独立的依赖项（Starter POM），因此想要构建一套完整的 Spring Cloud 工程往往需要大量的依赖项。

4. **Spring Cloud 不能脱离 Spring Boot 单独运行**

Spring Boot 不需要 Spring Cloud，就能直接创建可独立运行的工程或模块。

> 注意：虽然 Spring Boot 能够用于开发单个微服务，但它并不具备管理和协调微服务的能力，因此它只能算是一个微服务快速开发框架，而非微服务框架。

## Cloud组件升级

![image-20221204114545590](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204114545590.png)

## 微服务架构编码构建

**约定 > 配置 > 编码**

### 父工程Project搭建

**Maven模板引用以及Maven版本选择**

![image-20221204122532043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221204122532043.png)

pom

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>org.eddie</groupId>
  <artifactId>Spring_Cloud</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>pom</packaging>

  <!--关联模块-->
  <modules>
  <module>cloud-provider-payment-8001</module>
    <module>cloud-consumer-order-80</module>
  </modules>

  <!-- 统一管理jar包版本 -->
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
    <junit.version>4.12</junit.version>
    <log4j.version>1.2.17</log4j.version>
    <lombok.version>1.16.18</lombok.version>
    <mysql.version>8.0.30</mysql.version>
    <druid.version>1.1.16</druid.version>
    <mybatis.spring.boot.version>1.3.0</mybatis.spring.boot.version>
  </properties>

  <!-- 子模块继承之后，提供作用：锁定版本+子module不用写groupId和version  -->
  <dependencyManagement>
    <dependencies>
      <!--spring boot 2.2.2-->
      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-dependencies</artifactId>
        <version>2.2.2.RELEASE</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
      <!--spring cloud Hoxton.SR1-->
      <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-dependencies</artifactId>
        <version>Hoxton.SR1</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
      <!--spring cloud alibaba 2.1.0.RELEASE-->
      <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-alibaba-dependencies</artifactId>
        <version>2.1.0.RELEASE</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
      <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>${mysql.version}</version>
      </dependency>
      <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>druid</artifactId>
        <version>${druid.version}</version>
      </dependency>
      <dependency>
        <groupId>org.mybatis.spring.boot</groupId>
        <artifactId>mybatis-spring-boot-starter</artifactId>
        <version>${mybatis.spring.boot.version}</version>
      </dependency>
      <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>${junit.version}</version>
      </dependency>
      <dependency>
        <groupId>log4j</groupId>
        <artifactId>log4j</artifactId>
        <version>${log4j.version}</version>
      </dependency>
      <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>${lombok.version}</version>
        <optional>true</optional>
      </dependency>
    </dependencies>
  </dependencyManagement>

  <build>
    <plugins>
      <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
        <version>2.4.4</version>
        <configuration>
          <fork>true</fork>
          <addResources>true</addResources>
        </configuration>
      </plugin>
    </plugins>
  </build>


</project>
```

### 微服务模块的构建

1）建Module

2）改pom

3）写yml

4）主启类

5）业务类

​	5.1	建表SQL

​	5.2	domain

​	5.3	dao

​	5.4	service

​	5.5	controller

### 支付模块构建

#### **cloud-provider-payment-8001<服务提供者>**

![image-20221205103707947](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205103707947.png)

pom

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>Spring_Cloud</artifactId>
        <groupId>org.eddie</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-provider-payment-8001</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--包含了sleuth+zipkin-->
<!--        <dependency>-->
<!--            <groupId>org.springframework.cloud</groupId>-->
<!--            <artifactId>spring-cloud-starter-zipkin</artifactId>-->
<!--        </dependency>-->
        <!--eureka-client-->
<!--        <dependency>-->
<!--            <groupId>org.springframework.cloud</groupId>-->
<!--            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>-->
<!--        </dependency>-->
<!--        <dependency>&lt;!&ndash; 引入自己定义的api通用包，可以使用Payment支付Entity &ndash;&gt;-->
<!--            <groupId>com.atguigu.springcloud</groupId>-->
<!--            <artifactId>cloud-api-commons</artifactId>-->
<!--            <version>${project.version}</version>-->
<!--        </dependency>-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.16</version>
        </dependency>
        <!--mysql-connector-java-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <!--jdbc-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jdbc</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

application.yml

```yaml
server:
  port: 8001 #服务端口号

spring:
  application:
    name: cloud-payment-service #服务名称
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver # mysql驱动包
    url: jdbc:mysql://localhost:3306/springcloud?rewriteBatchedStatements=TRUE
    username: root
    password: root
    type: com.alibaba.druid.pool.DruidDataSource # 当前数据源操作类型


mybatis:
  mapperLocations: classpath:com/eddie/springcloud/dao/*.xml #mapper映射的xml的location
  type-aliases-package: com.eddie.springcloud.domain    # 所有Entity别名类所在包
```

#### cloud-consumer-order-80<服务消费者>

![image-20221205103728325](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205103728325.png)

pom

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>Spring_Cloud</artifactId>
        <groupId>org.eddie</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-consumer-order-80</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--包含了sleuth+zipkin-->
        <!--        <dependency>-->
        <!--            <groupId>org.springframework.cloud</groupId>-->
        <!--            <artifactId>spring-cloud-starter-zipkin</artifactId>-->
        <!--        </dependency>-->
        <!--eureka-client-->
        <!--        <dependency>-->
        <!--            <groupId>org.springframework.cloud</groupId>-->
        <!--            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>-->
        <!--        </dependency>-->
        <!--        <dependency>&lt;!&ndash; 引入自己定义的api通用包，可以使用Payment支付Entity &ndash;&gt;-->
        <!--            <groupId>com.atguigu.springcloud</groupId>-->
        <!--            <artifactId>cloud-api-commons</artifactId>-->
        <!--            <version>${project.version}</version>-->
        <!--        </dependency>-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
<!--        <dependency>-->
<!--            <groupId>org.mybatis.spring.boot</groupId>-->
<!--            <artifactId>mybatis-spring-boot-starter</artifactId>-->
<!--        </dependency>-->
<!--        <dependency>-->
<!--            <groupId>com.alibaba</groupId>-->
<!--            <artifactId>druid-spring-boot-starter</artifactId>-->
<!--            <version>1.1.16</version>-->
<!--        </dependency>-->
        <!--mysql-connector-java-->
<!--        <dependency>-->
<!--            <groupId>mysql</groupId>-->
<!--            <artifactId>mysql-connector-java</artifactId>-->
<!--        </dependency>-->
        <!--jdbc-->
<!--        <dependency>-->
<!--            <groupId>org.springframework.boot</groupId>-->
<!--            <artifactId>spring-boot-starter-jdbc</artifactId>-->
<!--        </dependency>-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

</project>
```

application.yml

```yaml
server:
  port: 80
```

#### 项目重构 抽离公共部分

cloud-api-commons<公共api>

![image-20221205104301109](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205104301109.png)

![image-20221205104350317](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205104350317.png)

pom

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>Spring_Cloud</artifactId>
        <groupId>org.eddie</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-api-commons</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>cn.hutool</groupId>
            <artifactId>hutool-all</artifactId>
            <version>5.1.0</version>
        </dependency>
    </dependencies>

</project>
```

使用cloud-api-commons<公共api>

引用依赖即可

![image-20221205104420674](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205104420674.png)

#### 单机EurekaServer

**AP理论（Availability -- Partition Tolerance）注重可用性**

![image-20221205221754426](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205221754426.png)

pom

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>Spring_Cloud</artifactId>
        <groupId>org.eddie</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>cloud-eureka-server-7001</artifactId>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!--eureka-server-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>
        <!-- 引入自己定义的api通用包，可以使用Payment支付Entity -->
        <dependency>
            <groupId>org.eddie</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
        <!--boot web actuator-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <!--一般通用配置-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
        </dependency>
    </dependencies>

</project>
```

application.yml

```yaml
server:
  port: 7001

eureka:
  instance:
    hostname: eureka7001.com #eureka服务端的实例名称
  client:
    register-with-eureka: false     #false表示不向注册中心注册自己。
    fetch-registry: false     #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #单机就是7001自己
      defaultZone: http://eureka7001.com:7001/eureka/
```

启动类

```java
package com.eddie.springcloud;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

/**
 @author EddieZhang
 @create 2022-12-05 11:52
 */
@SpringBootApplication
@EnableEurekaServer
public class EurekaMainBoot7001 {
    public static void main(String[] args) {
        SpringApplication.run(EurekaMainBoot7001.class,args);
    }
}
```

#### 支付的provder服务和consumer服务注册进Eureka中

provder

pom

![image-20221205223100431](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223100431.png)

application.yml

![image-20221205223149125](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223149125.png)

启动类

```java
package com.eddie.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

/**
 @author EddieZhang
 @create 2022-12-04 17:01
 */
@SpringBootApplication
@EnableEurekaClient
public class PaymentMainBoot8001 {
    public static void main(String[] args) {
        SpringApplication.run(PaymentMainBoot8001.class,args);
    }
}
```

consumer

pom

![image-20221205223323428](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223323428.png)

application.yml

![image-20221205223356074](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223356074.png)

启动类

```java
package com.eddie.springcloud;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

/**
 @author EddieZhang
 @create 2022-12-04 23:12
 */
@SpringBootApplication
@EnableEurekaClient
public class PaymentMainBoot80 {
    public static void main(String[] args) {
        SpringApplication.run(PaymentMainBoot80.class,args);
    }
}
```

controller

```java
/**
 @author EddieZhang
 @create 2022-12-04 23:02
 */
@RestController
@Slf4j
public class OrderController {

    public static final String PAYMENT_URL = "http://CLOUD-PAYMENT-SERVICE";

    @Autowired
    private RestTemplate restTemplate;

    @GetMapping("/consumer/payment/add")
    public Result<Payment> addPayment(Payment payment){
        return restTemplate.postForObject(PAYMENT_URL + "/payment/add",payment,Result.class);
    }
    @GetMapping("/consumer/payment/{id}")
    public Result<Payment> queryPaymentById(@PathVariable("id") Long id){
        return restTemplate.getForObject(PAYMENT_URL + "/payment/query/" + id,Result.class);
    }
}
```

#### 集群Eureka配置

**Eureka集群**

互相注册 相互守望

![image-20221205223620601](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223620601.png)

application.yml

![image-20221205223655066](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223655066.png)

域名映射

![image-20221205223734475](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223734475.png)

Eureka界面

![image-20221205223805210](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223805210.png)

**Provider集群**

![image-20221205223916220](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223916220.png)

![image-20221205223953002](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205223953002.png)

#### actuator微服务信息完善

![image-20221205224409434](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205224409434.png)

#### 服务发现Discovery

**服务列表**，该列表中包含了所有注册到服务注册中心的服务信息（**包括服务提供者和自身的信息**）

主启动类

![image-20221205230229059](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230229059.png)

Controller

![image-20221205230242828](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230242828.png)

![image-20221205230250322](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230250322.png)

响应结果

![image-20221205230326441](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230326441.png)

![image-20221205230335515](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230335515.png)

![image-20221205230414402](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205230414402.png)

#### Eureka自我保护机制

Eureka 的自我保护机制是一种应对网络异常的安全保护措施。它的架构哲学是：宁可同时保留所有微服务（健康的服务和不健康的服务都会保留）也不盲目移除任何健康的服务。通过 Eureka 的自我保护机制，可以让 Eureka Server 集群更加的健壮、稳定。

> Eureka 的自我保护机制也存在弊端。如果在 Eureka 自我保护机制触发期间，服务提供者提供的服务出现问题，那么服务消费者就很容易获取到已经不存在的服务进而出现调用失败的情况，此时，我们可以通过客户端的容错机制来解决此问题，详情请参考 [Spring Cloud Netflix Ribbon](http://c.biancheng.net/springcloud/ribbon.html) 和 [Spring Cloud Netflix Hystrix](http://c.biancheng.net/springcloud/hystrix.html)。

默认情况下，Eureka 的自我保护机制是开启的，如果想要关闭，则需要在配置文件中添加以下配置。

```yaml
纯文本复制
eureka:  
	server:    
		enable-self-preservation: false # false 关闭 Eureka 的自我保护机制，默认是开启,一般不建议大家修改
```

![image-20221205231938529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205231938529.png)

![image-20221205231947797](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205231947797.png)

#### 单机Zookeeper

**CP理论（Consistance -- Partition Tolerance）注重一致性**

当前注册进Zookeeper上的**节点**表示**注册的一个服务** 对于每一个节点（服务）是**临时的**

对于每一个**节点（服务）出现宕机**后 在进行**心跳探测**时；一段时间**未得到响应**的Zookeeper会将**此节点移除**

**临时节点** - 客户端活跃时，临时节点就是有效的。当客户端与ZooKeeper集合断开连接时，临时节点会自动删除。因此，只有临时节点不允许有子节点。如果临时节点被删除，则下一个合适的节点将填充其位置。临时节点在leader选举中起着重要作用

**Linux服务器上运行Zookeeper**

![image-20221206152459583](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152459583.png)

**provider**

![image-20221206152553783](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152553783.png)

pom

![image-20221206152609309](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152609309.png)

application.yml

![image-20221206152639511](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152639511.png)

启动类

![image-20221206152654857](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152654857.png)

controller

![image-20221206152721853](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206152721853.png)

**consumer**

![image-20221206155217369](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155217369.png)

pom

![image-20221206155237082](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155237082.png)

application.yml

![image-20221206155253616](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155253616.png)

启动类

![image-20221206155304922](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155304922.png)

config配置RestTemplate

![image-20221206155328478](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155328478.png)

controller

![image-20221206155349851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206155349851.png)

#### 单机Consul

**对于每一个服务出现宕机后 心跳检测未得到回应的会立即Deregistered（移除）**

**CP理论（Consistance -- Partition Tolerance）注重一致性**

Linux服务中启动Consul

```
./consul agent -server -bootstrap-expect 1 -data-dir=/tmp/consul -node=n1 -bind=127.0.0.1 -client=0.0.0.0 -ui
```

![image-20221206204208024](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204208024.png)

**Provider注册进Consul**

pom

![image-20221206204234155](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204234155.png)

application.yml

![image-20221206204251217](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204251217.png)

启动类

![image-20221206204309368](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204309368.png)

controller

![image-20221206204324562](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204324562.png)

Consul页面

![image-20221206204343300](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204343300.png)

Consumer注册进Consul

pom

![image-20221206204426304](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204426304.png)

application.yml

![image-20221206204438540](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204438540.png)

启动类

![image-20221206204447414](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204447414.png)

ApplicationContextConfig配置类中注入RestTemplate

![image-20221206204513469](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204513469.png)

Controller

![image-20221206204541705](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204541705.png)

Consul页面

![image-20221206204557618](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206204557618.png)

#### Ribbon

Ribbon 是一个客户端的负载均衡器，它可以与 Eureka 配合使用轻松地实现客户端的负载均衡。Ribbon 会先从 Eureka Server（服务注册中心）去获取服务端列表，然后通过负载均衡策略将请求分摊给多个服务端，从而达到负载均衡的目的

```xml
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
```

![image-20221208205810925](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208205810925.png)

spring-cloud-starter-netflix-eureka-client已经引入了ribbon的依赖 因此无需再次显示的进行引入

**Ribbon 可以与 RestTemplate（Rest 模板）配合使用，以实现微服务之间的调用**

![image-20221208221620218](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208221620218.png)

**@LoadBalanced**注解（表示默认的使用ribbon的负载均衡策略（轮询））

#### OpenFeign

**OpenFeign 实现远程服务调用** 集成了ribbon 使用默认的负载均衡策略（轮询）

![image-20221209101316353](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101316353.png)

pom

![image-20221209101327973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101327973.png)

application.yml

![image-20221209101340279](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101340279.png)

启动类

![image-20221209101354307](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101354307.png)

OpenFeign接口

![image-20221209101421437](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101421437.png)

与调用的服务提供者的方法相匹配

![image-20221209101439034](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101439034.png)

controller

![image-20221209101537155](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101537155.png)



## 服务注册中心

### Eureka

Eureka 是 Netflix 公司开发的一款开源的**服务注册**与**发现**组件

Spring Cloud Netflix Eureka---主要负责 Spring Cloud 的服务注册与发现功能

**Eureka 采用 CS（Client/Server，客户端/服务器） 架构**，它包括以下两大组件：

- **Eureka Server**：Eureka 服务注册中心，主要用于提供服务注册功能。当微服务启动时，会将自己的服务注册到 Eureka Server。Eureka Server 维护了一个可用服务列表，存储了所有注册到 Eureka Server 的可用服务的信息，这些可用服务可以在 Eureka Server 的管理界面中直观看到。
- **Eureka Client**：Eureka 客户端，通常指的是微服务系统中各个微服务，主要用于和 Eureka Server 进行交互。在微服务应用启动后，Eureka Client 会向 Eureka Server **发送心跳（默认周期为 30 秒）**。若 Eureka Server 在多个心跳周期内没有接收到某个 Eureka Client 的心跳，Eureka Server 将它从可用服务列表中**移除（默认 90 秒）**。 

![image-20221205232354112](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205232354112.png)

> 注：“**心跳**”指的是一段定时发送的自定义信息，让对方知道自己“**存活**”，以确保连接的有效性。大部分 CS 架构的应用程序都采用了心跳机制，服务端和客户端都可以发心跳。通常情况下是客户端向服务器端发送心跳包，服务端用于判断客户端是否在线。

#### **Eureka 实现服务注册与发现的原理**

![image-20221205112432588](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205112432588.png)

![image-20221205112158021](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205112158021.png)

Eureka 实现服务注册与发现的流程如下：

1. 搭建一个 Eureka Server 作为服务注册中心；
2. 服务提供者 Eureka Client 启动时，会把当前服务器的信息以服务名（spring.application.name）的方式注册到服务注册中心；
3. 服务消费者 Eureka Client 启动时，也会向服务注册中心注册；
4. 服务消费者还会获取一份可用服务列表，该列表中包含了所有注册到服务注册中心的服务信息（包括服务提供者和自身的信息）；
5. 在获得了可用服务列表后，服务消费者通过 HTTP 或消息中间件远程调用服务提供者提供的服务。

服务注册中心（Eureka Server）所扮演的角色十分重要，它是服务提供者和服务消费者之间的桥梁。服务提供者只有将自己的服务注册到服务注册中心才可能被服务消费者调用，而服务消费者也只有通过服务注册中心获取可用服务列表后，才能调用所需的服务。

#### **Eureka工作流程**



#### **Eureka单机/集群搭建**



#### **服务发现Discovery**



#### **Eureka自我保护机制**

所谓 “Eureka 的自我保护机制”，其中心思想就是“**好死不如赖活着**”

在实际的分布式微服务系统中，健康的服务（Eureka Client）也有可能会由于网络故障（例如网络延迟、卡顿、拥挤等原因）而无法与 Eureka Server 正常通讯。若此时 Eureka Server 因为没有接收心跳而误将健康的服务从服务列表中移除，这显然是不合理的

Eureka 的自我保护机制是一种应对网络异常的安全保护措施。它的架构哲学是：**宁可同时保留所有微服务**（健康的服务和不健康的服务都会保留）**也不盲目移除**任何健康的服务。通过 Eureka 的自我保护机制，可以让 Eureka Server 集群更加的健壮、稳定。

> Eureka 的自我保护机制也存在弊端。如果在 Eureka 自我保护机制触发期间，服务提供者提供的服务出现问题，那么服务消费者就很容易获取到已经不存在的服务进而出现调用失败的情况，此时，我们可以通过客户端的容错机制来解决此问题，详情请参考 [Spring Cloud Netflix Ribbon](http://c.biancheng.net/springcloud/ribbon.html) 和 [Spring Cloud Netflix Hystrix](http://c.biancheng.net/springcloud/hystrix.html)。

默认情况下，Eureka 的自我保护机制是开启的，如果想要关闭，则需要在配置文件中添加以下配置。

```
纯文本复制
eureka:  server:    enable-self-preservation: false # false 关闭 Eureka 的自我保护机制，默认是开启,一般不建议大家修改
```

**默认开启自我保护 可以配置关闭**

默认情况下，Eureka 的自我保护机制是开启的，如果想要关闭，则需要在配置文件中添加以下配置。

```yaml
纯文本复制
eureka:  
	server:    
	enable-self-preservation: false # false 关闭 Eureka 的自我保护机制，默认是开启,一般不建议大家修改
```

![image-20221205231927825](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205231927825.png)

![image-20221205231915856](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221205231915856.png)

### Zookeeper

[Apache ZooKeeper](https://zookeeper.apache.org/)

代替Eureka作为注册中心

### Consul

[Consul by HashiCorp](https://www.consul.io/)

**下载安装**

官网地址:https://www.consul.io/

Linux中下载安装

进入要按照到的目录 下载指定版本的压缩包

```
wget https://releases.hashicorp.com/consul/1.7.2/consul_1.7.2_linux_amd64.zip
```

解压

```
unzip  consul_1.7.2_linux_amd64.zip
```

![image-20221206205854291](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206205854291.png)

查看是否安装成功

```
./consul
```

![image-20221206205928544](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206205928544.png)

启动（默认是8500端口）

```
./consul agent -server -bootstrap-expect 1 -data-dir=/tmp/consul -node=n1 -bind=127.0.0.1 -client=0.0.0.0 -ui

-server 表示是server模式
　　-bootstrap-expect=3 表示是集群中有3台服务器 bootstrap该模式node可以指定自己作为leader ，如果是非leader可不加该参数
　　-data-dir=/tmp/consul 目录
　　-node=n2 该服务器节点名
　　-bind=127.0.0.1 节点绑定的ip
　　-ui 非必须 webui的路径 用web来管理consul
```

![image-20221206210053767](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206210053767.png)

Consul图形化界面

![image-20221206210140446](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206210140446.png)

### 三者比较

![image-20221206210322651](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206210322651.png)

## 负载均衡服务调用

### Ribbon

**Ribbon** 就是一个**基于 HTTP 和 TCP 的客户端负载均衡器**，当我们将 **Ribbon 和 Eureka 一起使用**时，Ribbon 会**从 Eureka Server（服务注册中心）中获取服务端列表**，然后**通过负载均衡策略**将**请求分摊给多个服务提供者**，从而达到**负载均衡**的目的

**Spring Cloud Ribbon** 是一套基于 Netflix Ribbon 实现的**客户端负载均衡和服务调用工具**

Spring Cloud **微服务之间的调用**，**API 网关的请求转发**等内容，实际上都是通过 Spring Cloud Ribbon 来实现的，包括后续我们要介绍的 [OpenFeign](http://c.biancheng.net/springcloud/open-feign.html) 也是基于它实现的

在任何一个系统中，**负载均衡**都是一个十分重要且不得不去实施的内容，它是系统处理**高并发**、**缓解网络压力**和**服务端扩容**的重要手段之一。

负载均衡（Load Balance） ，简单点说就是将用户的**请求平摊分配到多个服务器上运行**，以达到**扩展服务器带宽**、**增强数据处理能力**、**增加吞吐量**、**提高网络的可用性和灵活性**的目的

### 负载均衡

- #### 服务端负载均衡

当客户端发送请求时，该请求不会直接发送到服务端进行处理，而是全部交给负载均衡服务器，由负载均衡服务器按照某种算法（例如轮询、随机等），从其维护的可用服务清单中选择一个服务端，然后进行转发。

服务端负载均衡具有以下特点：

- 需要建立一个独立的负载均衡服务器。
- 负载均衡是在客户端发送请求后进行的，因此客户端并不知道到底是哪个服务端提供的服务。
- 可用服务端清单存储在负载均衡服务器上。

![image-20221208083420713](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208083420713.png)

- #### 客户端负载均衡

客户端负载均衡是将**负载均衡逻辑以代码的形式封装到客户端**上，即**负载均衡器位于客户端**。客户端**通过服务注册中心**（例如 Eureka Server）**获取到一份服务端提供的可用服务清单**。有了服务清单后，负载均衡器会在客户端发送请求前**通过负载均衡算法**选择一个服务端实例再进行访问，以达到负载均衡的目的；

客户端负载均衡也需要心跳机制去维护服务端清单的有效性，这个过程需要配合服务注册中心一起完成。

客户端负载均衡具有以下特点：

- 负载均衡器位于客户端，不需要单独搭建一个负载均衡服务器。
- 负载均衡是在客户端发送请求前进行的，因此客户端清楚地知道是哪个服务端提供的服务。
- 客户端都维护了一份可用服务清单，而这份清单都是从服务注册中心获取的。

![image-20221208083633003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208083633003.png)

- #### 服务端负载均衡 VS 客户端负载均衡

| 不同点                       | 服务端负载均衡                                               | 客户端负载均衡                                               |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 是否需要建立负载均衡服务器   | 需要在客户端和服务端之间建立一个独立的负载均衡服务器。       | 将负载均衡的逻辑以代码的形式封装到客户端上，因此不需要单独建立负载均衡服务器。 |
| 是否需要服务注册中心         | 不需要服务注册中心。                                         | 需要服务注册中心。  在客户端负载均衡中，所有的客户端和服务端都需要将其提供的服务注册到服务注册中心上。 |
| 可用服务清单存储的位置       | 可用服务清单存储在位于客户端与服务器之间的负载均衡服务器上。 | 所有的客户端都维护了一份可用服务清单，这些清单都是从服务注册中心获取的。 |
| 负载均衡的时机               | 先将请求发送到负载均衡服务器，然后由负载均衡服务器通过负载均衡算法，在多个服务端之间选择一个进行访问；即在服务器端再进行负载均衡算法分配。  简单点说就是，先发送请求，再进行负载均衡。 | 在发送请求前，由位于客户端的服务负载均衡器（例如 Ribbon）通过负载均衡算法选择一个服务器，然后进行访问。  简单点说就是，先进行负载均衡，再发送请求。 |
| 客户端是否了解服务提供方信息 | 由于负载均衡是在客户端发送请求后进行的，因此客户端并不知道到底是哪个服务端提供的服务。 | 负载均衡是在客户端发送请求前进行的，因此客户端清楚的知道是哪个服务端提供的服务。 |

### Ribbon 实现服务调用

Ribbon 是一个客户端的负载均衡器，它可以与 Eureka 配合使用轻松地实现客户端的负载均衡。Ribbon 会先从 Eureka Server（服务注册中心）去获取服务端列表，然后通过负载均衡策略将请求分摊给多个服务端，从而达到负载均衡的目的

```xml
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
        </dependency>
```

![image-20221208205810925](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208205810925.png)

spring-cloud-starter-netflix-eureka-client已经引入了ribbon的依赖 因此无需再次显示的进行引入

**Ribbon 可以与 RestTemplate（Rest 模板）配合使用，以实现微服务之间的调用**

![image-20221208221620218](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208221620218.png)

**@LoadBalanced**注解（表示默认的使用ribbon的负载均衡策略（轮询））

### Ribbon默认负载均衡策略

Spring Cloud Ribbon 提供了一个 **IRule 接口**，该接口主要用来定义负载均衡策略，它有 7 个默认实现类，**每一个实现类都是一种负载均衡策略**

![image-20221208222141191](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208222141191.png)

| 序号 | 实现类                    | 负载均衡策略                                                 |
| ---- | ------------------------- | ------------------------------------------------------------ |
| 1    | RoundRobinRule            | 按照线性轮询策略，即按照一定的顺序依次选取服务实例           |
| 2    | RandomRule                | 随机选取一个服务实例                                         |
| 3    | RetryRule                 | 按照 RoundRobinRule（轮询）的策略来获取服务，如果获取的服务实例为 null 或已经失效，则在指定的时间之内不断地进行重试（重试时获取服务的策略还是 RoundRobinRule 中定义的策略），如果超过指定时间依然没获取到服务实例则返回 null 。 |
| 4    | WeightedResponseTimeRule  | WeightedResponseTimeRule 是 RoundRobinRule 的一个子类，它对 RoundRobinRule 的功能进行了扩展。  根据平均响应时间，来计算所有服务实例的权重，响应时间越短的服务实例权重越高，被选中的概率越大。刚启动时，如果统计信息不足，则使用线性轮询策略，等信息足够时，再切换到 WeightedResponseTimeRule。 |
| 5    | BestAvailableRule         | 继承自 ClientConfigEnabledRoundRobinRule。先过滤点故障或失效的服务实例，然后再选择并发量最小的服务实例。 |
| 6    | AvailabilityFilteringRule | 先过滤掉故障或失效的服务实例，然后再选择并发量较小的服务实例。 |
| 7    | ZoneAvoidanceRule         | 默认的负载均衡策略，综合判断服务所在区域（zone）的性能和服务（server）的可用性，来选择服务实例。在没有区域的环境下，该策略与轮询（RandomRule）策略类似。 |

### 切换负载均衡策略

切换负载均衡策略的方法很简单，我们只需要**在服务消费者（客户端）的配置类中**，**将 IRule 的其他实现类注入到容器中**即可。

![image-20221208222522434](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221208222522434.png)

### 定制负载均衡策略

**定制负载均衡策略类 extends AbstractLoadBalancerRule**

```java
/**
* 定制 Ribbon 负载均衡策略
*/
public class MyRandomRule extends AbstractLoadBalancerRule {
    private int total = 0;            // 总共被调用的次数，目前要求每台被调用5次
    private int currentIndex = 0;    // 当前提供服务的机器号
    public Server choose(ILoadBalancer lb, Object key) {
        if (lb == null) {
            return null;
        }
        Server server = null;
        while (server == null) {
            if (Thread.interrupted()) {
                return null;
            }
            //获取所有有效的服务实例列表
            List<Server> upList = lb.getReachableServers();
            //获取所有的服务实例的列表
            List<Server> allList = lb.getAllServers();
            //如果没有任何的服务实例则返回 null
            int serverCount = allList.size();
            if (serverCount == 0) {
                return null;
            }
            //与随机策略相似，但每个服务实例只有在调用 3 次之后，才会调用其他的服务实例
            if (total < 3) {
                server = upList.get(currentIndex);
                total++;
            } else {
                total = 0;
                currentIndex++;
                if (currentIndex >= upList.size()) {
                    currentIndex = 0;
                }
            }
            if (server == null) {
                Thread.yield();
                continue;
            }
            if (server.isAlive()) {
                return (server);
            }
            server = null;
            Thread.yield();
        }
        return server;
    }
    @Override
    public Server choose(Object key) {
        return choose(getLoadBalancer(), key);
    }
    @Override
    public void initWithNiwsConfig(IClientConfig clientConfig) {
        // TODO Auto-generated method stub
    }
}
```

**在启动类外的包下(包扫描策略之外的包下)定制Ribbon负载均衡策略的配置类**

```java
/**
* 定制 Ribbon 负载均衡策略的配置类
* 该自定义 Ribbon 负载均衡策略配置类 不能在启动类所在包及其子包下
* 否则所有的 Ribbon 客户端都会采用该策略，无法达到特殊化定制的目的
*/
@Configuration
public class MySelfRibbonRuleConfig {
    @Bean
    public IRule myRule() {
        //自定义 Ribbon 负载均衡策略
        return new MyRandomRule(); //自定义，随机选择某一个微服务，执行五次
    }
}
```

**启动类上添加@RibbonClient注解 并指定服务name 以及定制的负载均衡配置类类型**

```java
@SpringBootApplication
@EnableEurekaClient
//自定义 Ribbon 负载均衡策略在主启动类上使用 RibbonClient 注解，在该微服务启动时，就能自动去加载我们自定义的 Ribbon 配置类，从而是配置生效
// name 为需要定制负载均衡策略的微服务名称（application name）
// configuration 为定制的负载均衡策略的配置类，
// 且官方文档中明确提出，该配置类不能在 ComponentScan 注解（SpringBootApplication 注解中包含了该注解）下的包或其子包中，即自定义负载均衡配置类不能在启动类所在包及其子包下
@RibbonClient(name = "服务name", configuration = MySelfRibbonRuleConfig.class)
public class MicroServiceCloudConsumerDept80Application {
    public static void main(String[] args) {
        SpringApplication.run(MicroServiceCloudConsumerDept80Application.class, args);
    }
}
```

## 服务调用OpenFeign

[Spring Cloud OpenFeign](https://spring.io/projects/spring-cloud-openfeign)

**Spring Cloud声明式服务调用组件**

**Client端**

OpenFeign 是 Spring Cloud **对 Feign 的二次封装**

OpenFeign **对 [Ribbon](http://c.biancheng.net/springcloud/ribbon.html) 进行了集成**，利用 Ribbon 维护了一份可用服务清单，并**通过 Ribbon 实现了客户端的负载均衡**。

OpenFeign 是一种**声明式服务调用组件**，它**在 RestTemplate 的基础上做了进一步的封装**。通过 OpenFeign ，我们**只需要声明一个接口**并**通过注解**进行简单的**配置**（**类似于 Dao 接口上面的 Mapper 注解一样**）即可**实现对 HTTP 接口的绑定**。

通过 OpenFeign ，我们可以像调用本地方法一样来调用远程服务，而完全感觉不到这是在进行远程调用。

只需**创建一个接口并在接口上添加@FeignClient注解**即可 ；该注解用于**通知 OpenFeign 组件对 @RequestMapping 注解下的接口进行解析**，并**通过动态代理的方式产生实现类**，实现负载均衡和服务调用。

**需要在启动类上声明@EnableFeignClients以启动OpenFeign的使用**

#### OpenFeign 常用注解

| 注解                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| @FeignClient        | 该注解用于通知 OpenFeign 组件对 @RequestMapping 注解下的接口进行解析，并通过动态代理的方式产生实现类，实现负载均衡和服务调用。 |
| @EnableFeignClients | 该注解用于开启 OpenFeign 功能，当 Spring Cloud 应用启动时，OpenFeign 会扫描标有 @FeignClient 注解的接口，生成代理并注册到 Spring 容器中。 |
| @RequestMapping     | Spring MVC 注解，在 Spring MVC 中使用该注解映射请求，通过它来指定控制器（Controller）可以处理哪些 URL 请求，相当于 Servlet 中 web.xml 的配置。 |
| @GetMapping         | Spring MVC 注解，用来映射 GET 请求，它是一个组合注解，相当于 @RequestMapping(method = RequestMethod.GET) 。 |
| @PostMapping        | Spring MVC 注解，用来映射 POST 请求，它是一个组合注解，相当于 @RequestMapping(method = RequestMethod.POST) 。 |

#### OpenFeign 实现远程服务调用



> OpenFeign**服务之间的远程调用** 都是进行JSON格式的数据传输 需要**使用`@RequestBody`**
>
> ```java
> 	 /*
> 	 1、CouponFeignService.saveSpuBounds(spuBoundTo);
>      1）、@RequestBody将这个对象转为json。
>      2）、找到gulimall-coupon服务，给/coupon/spubounds/save发送请求。
>          将上一步转的json放在请求体位置，发送请求；
>      3）、对方服务收到请求。请求体里有json数据。
>          (@RequestBody SpuBoundsEntity spuBounds)；将请求体的json转为SpuBoundsEntity；
> 	 只要json数据模型是兼容的。双方服务无需使用同一个to
> 	 */
> 
> @Component
> @FeignClient("cloud-mall-coupon")
> public interface CouponOpenFeign {         
> 	@PostMapping("mall_coupon/spubounds/save")
>     R saveSpuBounds(@RequestBody SpuBoundTo spuBoundTo);         
> }         
> ```

**取代ribbon+rest Template**

![image-20221209101316353](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101316353.png)

pom

![image-20221209101327973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101327973.png)

application.yml

![image-20221209101340279](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101340279.png)

启动类

![image-20221209101947638](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209101947638.png)

OpenFeign接口

![image-20221209102359970](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209102359970.png)

controller

![image-20221209102445444](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209102445444.png)

#### OpenFeign 超时控制

**OpenFeign 客户端**的**默认超时时间为 1 秒钟**，如果服务端**处理请求的时间超过 1 秒**就会**报错**。为了避免这样的情况，我们**需要对 OpenFeign 客户端的超时时间进行控制**

application.yml 中添加以下配置，将超时时间设置为6秒

```yaml
ribbon:
  ReadTimeout: 6000 #建立连接所用的时间，适用于网络状况正常的情况下，两端两端连接所用的时间
  ConnectionTimeout: 6000 #建立连接后，服务器读取到可用资源的时间
```

注：由于 **OpenFeign 集成了 Ribbon** ，其**服务调用以及负载均衡在底层都是依靠 Ribbon 实现的**，因此 OpenFeign **超时控制也是通过 Ribbon 来实现的**。

#### OpenFeign 日志增强

**OpenFeign 提供了日志打印功能**，我们可以**通过配置调整日志级别**，来了解请求的细节。

Feign 为每一个 FeignClient 都提供了一个 **feign.Logger 实例**，通过它可以对 OpenFeign 服务绑定接口的调用情况进行监控。

**定义Logger.Level**

![image-20221209110336349](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209110336349.png)

![image-20221209110313203](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209110313203.png)

该配置的作用是通过配置的 Logger.Level 对象告诉 OpenFeign 记录哪些日志内容。

 Logger.Level 的具体级别如下：

- NONE：不记录任何信息。
- BASIC：仅记录请求方法、URL 以及响应状态码和执行时间。
- HEADERS：除了记录 BASIC 级别的信息外，还会记录请求和响应的头信息。
- FULL：记录所有请求与响应的明细，包括头信息、请求体、元数据等等。

**yaml配置中配置日志**

```yaml
logging: 
  level:
    #feign 日志以什么样的级别监控该接口
    com.eddie.springcloud.service.OpenFeignService : debug
```

![image-20221209110852429](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209110852429.png)

## 服务降级，熔断Hystrix	

[GitHub - Netflix/Hystrix: Hystrix is a latency and fault tolerance library designed to isolate points of access to remote systems, services and 3rd party libraries, stop cascading failure and enable resilience in complex distributed systems where failure is inevitable.](https://github.com/Netflix/Hystrix)

[Hystrix介绍 - 废物大师兄 - 博客园 (cnblogs.com)](https://www.cnblogs.com/cjsblog/p/9391819.html)

在微服务系统中，Hystrix 能够帮助我们实现以下目标：

- **保护线程资源**：防止单个服务的故障耗尽系统中的所有线程资源。
- **快速失败机制**：当某个服务发生了故障，不让服务调用方一直等待，而是直接返回请求失败。
- **提供降级（FallBack）方案**：在请求失败后，提供一个设计好的降级方案，通常是一个兜底方法，当请求失败后即调用该方法。
- **防止故障扩散**：使用熔断机制，防止故障扩散到其他服务。
- **监控功能**：提供熔断器故障监控组件 Hystrix Dashboard，随时监控熔断器的状态。

Spring Cloud Hystrix 是一款优秀的**服务容错与保护组件**，也是 Spring Cloud 中最重要的组件之一。

Spring Cloud Hystrix 是基于 Netflix 公司的开源组件 Hystrix 实现的，它提供了**熔断器功能**，能够有**效地阻止分布式微服务系统中出现联动故障**，以**提高微服务系统的弹性**。Spring Cloud Hystrix 具有**服务降级**、**服务熔断**、**线程隔离**、**请求缓存**、**请求合并**以及**实时故障监控**等强大功能。

![image-20221209162126269](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209162126269.png)

当微服务系统的一**个服务出现故障**时，**故障会沿着服务的调用链路在系统中疯狂蔓延**，最终**导致整个微服务系统的瘫痪**，这就是**“雪崩效应”**。

为了防止此类事件的发生，微服务架构引入了**“熔断器”**的一系列**服务容错和保护机制**

### Hystrix设计原则是什么

- 防止任何单个依赖项耗尽所有容器（如Tomcat）用户线程。
- 甩掉包袱，快速失败而不是排队。
- 在任何可行的地方提供回退，以保护用户不受失败的影响。
- 使用隔离技术（如隔离板、泳道和断路器模式）来限制任何一个依赖项的影响。
- 通过近实时的度量、监视和警报来优化发现时间。
- 通过配置的低延迟传播来优化恢复时间。
- 支持对Hystrix的大多数方面的动态属性更改，允许使用低延迟反馈循环进行实时操作修改。
- 避免在整个依赖客户端执行中出现故障，而不仅仅是在网络流量中。

### Hystrix是如何实现它的目标的

1. 用一个HystrixCommand 或者 HystrixObservableCommand （这是命令模式的一个例子）包装所有的对外部系统（或者依赖）的调用，典型地它们在一个单独的线程中执行
2. 调用超时时间比你自己定义的阈值要长。有一个默认值，对于大多数的依赖项你是可以自定义超时时间的。
3. 为每个依赖项维护一个小的线程池(或信号量)；如果线程池满了，那么该依赖性将会立即拒绝请求，而不是排队。
4. 调用的结果有这么几种：成功、失败（客户端抛出异常）、超时、拒绝。
5. 在一段时间内，如果服务的错误百分比超过了一个阈值，就会触发一个断路器来停止对特定服务的所有请求，无论是手动的还是自动的。
6. 当请求失败、被拒绝、超时或短路时，执行回退逻辑。
7. 近实时监控指标和配置变化。

### 工作流程

[How it Works · Netflix/Hystrix Wiki · GitHub](https://github.com/Netflix/Hystrix/wiki/How-it-Works)

![image-20221209161112639](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209161112639.png)

### 熔断器

熔断器（Circuit Breaker）一词来源物理学中的电路知识，它的作用是当线路出现故障时，迅速切断电源以保护电路的安全。

在微服务领域，熔断器最早是由 Martin Fowler 在他发表的 《[Circuit Breake](https://martinfowler.com/bliki/CircuitBreaker.html)r》一文中提出。与物理学中的熔断器作用相似，微服务架构中的熔断器能够在某个服务发生故障后，向服务调用方返回一个符合预期的、可处理的降级响应（FallBack），而不是长时间的等待或者抛出调用方无法处理的异常。这样就保证了服务调用方的线程不会被长时间、不必要地占用，避免故障在微服务系统中的蔓延，防止系统雪崩效应的发生。

### Hystrix 服务降级

Hystrix 服务降级 **FallBack** 既可以放在**服务端进行**，也可以放在**客户端进行**。

Hystrix 会在以下场景下进行服务降级处理：

- 程序运行异常
- 服务超时
- 熔断器处于打开状态
- 线程池资源耗尽

服务降级的使用场景有以下 2 种：

- 在服务器压力剧增时，根据实际业务情况及流量，对一些不重要、不紧急的服务进行有策略地不处理或简单处理，从而释放服务器资源以保证核心服务正常运作。
- 当某些服务不可用时，为了避免长时间等待造成服务卡顿或雪崩效应，而主动执行备用的降级逻辑立刻返回一个友好的提示，以保障主体业务不受影响。

可以通过**重写 HystrixCommand 的 getFallBack() 方法**或 **HystrixObservableCommand 的 resumeWithFallback() 方法**，**使服务支持服务降级**。

#### 服务端进行服务降级

![image-20221209170227146](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170227146.png)

pom

![image-20221209170245711](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170245711.png)

application.yml

![image-20221209170315651](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170315651.png)

启动类

![image-20221209170337614](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170337614.png)

service

![image-20221209170359091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170359091.png)

controller

![image-20221209170424071](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170424071.png)

run

![image-20221209170435536](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209170435536.png)

#### 客户端进行服务降级☆

**通常情况下，我们都会在客户端进行服务降级**，当客户端调用的服务端的服务不可用时，客户端直接进行服务降级处理，避免其线程被长时间、不必要地占用

![image-20221209180353853](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180353853.png)

pom

![image-20221209180406011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180406011.png)

application.yml

![image-20221209180425286](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180425286.png)

```yaml
######################配置请求超时时间##########################
hystrix:
  command:
    default:
      execution:
        isolation:
          thread:
            timeoutInMilliseconds: 7000
####################配置具体方法超时时间 为 3 秒########################
    DeptHystrixService#deptInfo_Timeout(Integer):
      execution:
        isolation:
          thread:
            timeoutInMilliseconds: 3000
            
#在配置文件中设计请求的超时时间时，需要注意以下 2 点： 

#1）Hystrix 可以来为所有请求（方法）设置超时时间（单位为毫秒），若请求超时则触发全局的回退方法进行处理。
#hystrix.command.default.execution.isolation.thread.timeoutInMilliseconds=mmm

#2）Hystrix 还可以为某个特定的服务请求（方法）设置超时时间，格式如下：
#hystrix.command.xxx#yyy(zzz).execution.isolation.thread.timeoutInMilliseconds=mmm
#格式说明如下：
#xxx：为包含该服务方法的类的名称（通常为服务绑定接口的名称），例如 DeptHystrixService 接口。
#yyy：服务方法名，例如 deptInfo_Timeout() 方法。
#zzz：方法内的参数类型，例如 Integer、String 等等
#mmm：要设置的超时时间，单位为毫秒（1 秒 =1000 毫秒）
```

启动类

![image-20221209180525469](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180525469.png)

controller

![image-20221209180547633](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180547633.png)

provider端的方法

![image-20221209180723249](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209180723249.png)

run

![image-20221209181841894](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209181841894.png)

##### 全局降级方法

**注意**：**降级（FallBack）方法**必须**与其对应的业务方法**在**同一个类中**，否则无法生效。

**注意**：全局降级方法的优先级较低，只有业务方法没有指定其降级方法时，服务降级时才会触发全局回退方法。若业务方法指定它自己的回退方法，那么在服务降级时，就只会直接触发它自己的回退方法，而非全局回退方法。

![image-20221209201957589](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209201957589.png)

单独指定回退方法

![image-20221209201316537](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209201316537.png)

全局回退方法

![image-20221209201341214](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209201341214.png)

##### 解耦降级逻辑

不管是业务方法指定的降级方法还是全局降级方法，它们都必须和业务方法在同一个类中才能生效，业务逻辑与降级逻辑耦合度极高。

**对业务逻辑与降级逻辑进行解耦：**

![image-20221209202844026](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209202844026.png)

![image-20221209202854001](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209202854001.png)

![image-20221209202926845](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209202926845.png)

![image-20221209202955323](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209202955323.png)

### Hystrix 服务熔断

**熔断机制**是为了**应对雪崩效应**而出现的一种**微服务链路保护机制**。

当微服务系统中的**某个微服务不可用或响应时间太长时**，**为了**保护系统的**整体可用性**，**熔断器**会**暂时切断请求对该服务的调用**，并**快速返回一个友好的错误响应**。这种熔断状态不是永久的，在**经历了一定的时间后**，**熔断器**会再次**检测该微服务是否恢复正常**，若服务**恢复正常则恢复其调用链路**。

![image-20221209203316448](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209203316448.png)

**熔断状态**

在熔断机制中涉及了三种熔断状态：

- 熔断关闭状态（Closed）：当服务访问正常时，熔断器处于关闭状态，服务调用方可以正常地对服务进行调用。
- 熔断开启状态（Open）：默认情况下，在固定时间内接口调用出错比率达到一个阈值（例如 50%），熔断器会进入熔断开启状态。进入熔断状态后，后续对该服务的调用都会被切断，熔断器会执行本地的降级（FallBack）方法。
- 半熔断状态（Half-Open）： 在熔断开启一段时间之后，熔断器会进入半熔断状态。在半熔断状态下，熔断器会尝试恢复服务调用方对服务的调用，允许部分请求调用该服务，并监控其调用成功率。如果成功率达到预期，则说明服务已恢复正常，熔断器进入关闭状态；如果成功率仍旧很低，则重新进入熔断开启状态。

**Hystrix 实现熔断机制**

在 Spring Cloud 中，熔断机制是通过 Hystrix 实现的。Hystrix 会监控微服务间调用的状况，当失败调用到一定比例时（例如 5 秒内失败 20 次），就会启动熔断机制。

Hystrix 实现服务熔断的步骤如下：

1. 当服务的调用出错率达到或超过 Hystix 规定的比率（默认为 50%）后，熔断器进入熔断开启状态。
2. 熔断器进入熔断开启状态后，Hystrix 会启动一个休眠时间窗，在这个时间窗内，该服务的降级逻辑会临时充当业务主逻辑，而原来的业务主逻辑不可用。
3. 当有请求再次调用该服务时，会直接调用降级逻辑快速地返回失败响应，以避免系统雪崩。
4. 当休眠时间窗到期后，Hystrix 会进入半熔断转态，允许部分请求对服务原来的主业务逻辑进行调用，并监控其调用成功率。
5. 如果调用成功率达到预期，则说明服务已恢复正常，Hystrix 进入熔断关闭状态，服务原来的主业务逻辑恢复；否则 Hystrix 重新进入熔断开启状态，休眠时间窗口重新计时，继续重复第 2 到第 5 步。

**代码实例**

![image-20221209220525002](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209220525002.png)

```java
@Override
    @HystrixCommand(commandProperties = {
            @HystrixProperty(name = "circuitBreaker.enabled", value = "true"), //是否开启熔断器
//            @HystrixProperty(name = "metrics.rollingStats.timeInMilliseconds", value = "1000"), //统计时间窗
            @HystrixProperty(name = "circuitBreaker.requestVolumeThreshold", value = "10"), //统计时间窗内请求次数
            @HystrixProperty(name = "circuitBreaker.sleepWindowInMilliseconds", value = "10000"), //休眠时间窗口期
            @HystrixProperty(name = "circuitBreaker.errorThresholdPercentage", value = "40"), //在统计时间窗口期以内，请求失败率达到 60% 时进入熔断状态
    })
    public String testHystrixCircuitBreaker(Integer value) {
        if (value < 0) {
            throw new RuntimeException("不能乱来哦~~");
        } else {
            return Thread.currentThread().getName() + "\t" + "调用成功，流水号为：" + UUID.randomUUID().toString().substring(0, 10);
        }
    }
```

| 参数                                     | 描述                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| metrics.rollingStats.timeInMilliseconds  | 统计时间窗。                                                 |
| circuitBreaker.sleepWindowInMilliseconds | 休眠时间窗，熔断开启状态持续一段时间后，熔断器会自动进入半熔断状态，这段时间就被称为休眠窗口期。 |
| circuitBreaker.requestVolumeThreshold    | 请求总数阀值。  在统计时间窗内，请求总数必须到达一定的数量级，Hystrix 才可能会将熔断器打开进入熔断开启转态，而这个请求数量级就是 请求总数阀值。Hystrix 请求总数阈值默认为 20，这就意味着在统计时间窗内，如果服务调用次数不足 20 次，即使所有的请求都调用出错，熔断器也不会打开。 |
| circuitBreaker.errorThresholdPercentage  | 错误百分比阈值。  当请求总数在统计时间窗内超过了请求总数阀值，且请求调用出错率超过一定的比例，熔断器才会打开进入熔断开启转态，而这个比例就是错误百分比阈值。错误百分比阈值设置为 50，就表示错误百分比为 50%，如果服务发生了 30 次调用，其中有 15 次发生了错误，即超过了 50% 的错误百分比，这时候将熔断器就会打开。 |

当浏览器多次（调用次数大于请求总数阀值）访问“http://localhost/payment/consumer/hystrix/testHystrixCircuitBreaker/-1”，

使**调用出错率大于错误百分比阀值**

**熔断器**进入**open状态**

**一段时间后熔断器会进入半熔断状态**

当服务调用**正确率上升到一定的利率后**，Hystrix **进入熔断关闭状态**

### Hystrix 故障监控

Hystrix 还提供了准实时的调用监控（Hystrix Dashboard）功能，Hystrix 会持续地记录所有通过 Hystrix 发起的请求的执行信息，并以统计报表的形式展示给用户，包括每秒执行请求的数量、成功请求的数量和失败请求的数量等

pom

![image-20221209231533326](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209231533326.png)

application.yml



![image-20221209231621805](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209231621805.png)

启动类

![image-20221209231636471](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209231636471.png)

http://localhost:80/hystrix熔断器监控页面

![image-20221209231955866](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209231955866.png)

http://localhost:8001//actuator/hystrix.stream监控地址

![image-20221209232142875](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209232142875.png)

进行监控

![image-20221209232259867](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221209232259867.png)

## 服务网关

API 网关是一个搭建在**客户端和微服务之间的服务**，我们**可以在 API 网关中处理一些非业务功能的逻辑，例如权限验证、监控、缓存、请求路由等。**

API 网关就像整个微服务系统的门面一样，是**系统对外的唯一入口**。有了它，**客户端会先将请求发送到 API 网关**，然后**由 API 网关根据请求的标识信息将请求转发到微服务实例**。

![image-20221211093258875](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211093258875.png)

对于服务数量众多、复杂度较高、规模比较大的系统来说，使用 API 网关具有以下好处：

- 客户端通过 API 网关与微服务交互时，**客户端只需要知道 API 网关地址即可**，而不需要维护大量的服务地址，简化了客户端的开发。
- **客户端直接与 API 网关通信**，能够减少客户端与各个服务的交互次数。
- **客户端与后端的服务耦合度降低**。
- **节省流量，提高性能，提升用户体验**。
- API 网关还提供了**安全**、**流控**、**过滤**、**缓存**、**计费**以及**监控**等 API 管理功能。

### Zuul



### Gateway☆

[Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/#gateway-starter)

Spring Cloud Gateway 是 Spring Cloud 团队基于 Spring 5.0、Spring Boot 2.0 和 Project Reactor 等技术开发的高性能 API 网关组件。

Spring Cloud Gateway 旨在提供一种简单而有效的途径来发送 API，并为它们提供横切关注点，例如：安全性，监控/指标和弹性。 

> Spring Cloud Gateway 是基于 **WebFlux 框架**实现的，而 WebFlux 框架底层则使用了**高性能的 Reactor 模式通信框架 Netty**。

#### **Spring Cloud Gateway 核心概念**

| 核心概念          | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| Route（路由）     | 网关最基本的模块。它由一个 ID、一个目标 URI、一组断言（Predicate）和一组过滤器（Filter）组成。 |
| Predicate（断言） | 路由转发的判断条件，我们可以通过 Predicate 对 HTTP 请求进行匹配，例如请求方式、请求路径、请求头、参数等，如果请求与断言匹配成功，则将请求转发到相应的服务。 |
| Filter（过滤器）  | 过滤器，我们可以使用它对请求进行拦截和修改，还可以使用它对上文的响应进行再处理。 |

> 注意：其中 Route 和 Predicate 必须同时声明。

#### **Spring Cloud Gateway 的特征**

- 基于 Spring Framework 5、Project Reactor 和 Spring Boot 2.0 构建。
- 能够在任意请求属性上匹配路由。
- predicates（断言） 和 filters（过滤器）是特定于路由的。
- 集成了 Hystrix 熔断器。
- 集成了 Spring Cloud DiscoveryClient（服务发现客户端）。
- 易于编写断言和过滤器。
- 能够限制请求频率。
- 能够重写请求路径。

#### Gateway 的工作流程

![image-20221211093743684](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211093743684.png)

Spring Cloud Gateway 工作流程说明如下：

1. 客户端将请求发送到 Spring Cloud Gateway 上。
2. Spring Cloud Gateway 通过 Gateway Handler Mapping 找到与请求相匹配的路由，将其发送给 Gateway Web Handler。
3. Gateway Web Handler 通过指定的过滤器链（Filter Chain），将请求转发到实际的服务节点中，执行业务逻辑返回响应结果。
4. 过滤器之间用虚线分开是因为过滤器可能会在转发请求之前（pre）或之后（post）执行业务逻辑。
5. 过滤器（Filter）可以在请求被转发到服务端前，对请求进行拦截和修改，例如参数校验、权限校验、流量监控、日志输出以及协议转换等。
6. 过滤器可以在响应返回客户端之前，对响应进行拦截和再处理，例如修改响应内容或响应头、日志输出、流量监控等。
7. 响应原路返回给客户端。


总而言之，客户端发送到 Spring Cloud Gateway 的请求需要通过一定的匹配条件，才能定位到真正的服务节点。在将请求转发到服务进行处理的过程前后（pre 和 post），我们还可以对请求和响应进行一些精细化控制。

Predicate 就是路由的匹配条件，而 Filter 就是对请求和响应进行精细化控制的工具。有了这两个元素，再加上目标 URI，就可以实现一个具体的路由了。

#### Predicate 断言

Spring Cloud Gateway 通过 Predicate 断言来实现 **Route 路由的匹配规则**。简单点说，Predicate 是路由转发的判断条件，**请求只有满足了 Predicate 的条件，才会被转发到指定的服务上进行处理**。

使用 Predicate 断言需要注意以下 3 点：

- Route 路由与 Predicate 断言的对应关系为“一对多”，一个路由可以包含多个不同断言。
- 一个请求想要转发到指定的路由上，就必须同时匹配路由上的所有断言。
- 当一个请求同时满足多个路由的断言条件时，请求只会被首个成功匹配的路由转发。

![image-20221211093843797](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211093843797.png)

常见的 Predicate 断言如下表（假设转发的 URI 为 http://localhost:8001）。

| 断言    | 示例                                                         | 说明                                                         |
| ------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Path    | - Path=/dept/list/**                                         | 当请求路径与 /dept/list/** 匹配时，该请求才能被转发到 http://localhost:8001 上。 |
| Before  | - Before=2021-10-20T11:47:34.255+08:00[Asia/Shanghai]        | 在 2021 年 10 月 20 日 11 时 47 分 34.255 秒之前的请求，才会被转发到 http://localhost:8001 上。 |
| After   | - After=2021-10-20T11:47:34.255+08:00[Asia/Shanghai]         | 在 2021 年 10 月 20 日 11 时 47 分 34.255 秒之后的请求，才会被转发到 http://localhost:8001 上。 |
| Between | - Between=2021-10-20T15:18:33.226+08:00[Asia/Shanghai],2021-10-20T15:23:33.226+08:00[Asia/Shanghai] | 在 2021 年 10 月 20 日 15 时 18 分 33.226 秒 到 2021 年 10 月 20 日 15 时 23 分 33.226 秒之间的请求，才会被转发到 http://localhost:8001 服务器上。 |
| Cookie  | - Cookie=name,c.biancheng.net                                | 携带 Cookie 且 Cookie 的内容为 name=c.biancheng.net 的请求，才会被转发到 http://localhost:8001 上。 |
| Header  | - Header=X-Request-Id,\d+                                    | 请求头上携带属性 X-Request-Id 且属性值为整数的请求，才会被转发到 http://localhost:8001 上。 |
| Method  | - Method=GET                                                 | 只有 GET 请求才会被转发到 http://localhost:8001 上。         |

#### instance

pom

```xml
 		<!--特别注意：在 gateway 网关服务中不能引入 spring-boot-starter-web 的依赖，否则会报错-->
        <!-- Spring cloud gateway 网关依赖-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-gateway</artifactId>
        </dependency>
```

![image-20221211093953594](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211093953594.png)

在 gateway（底层使用netty） 网关服务中**不能引入 spring-boot-starter-web 的依赖**（底层默认使用tomcat服务器），否则会报错

application.yml

动态路由

默认情况下，Spring Cloud Gateway 会根据服务注册中心（例如 Eureka Server）中维护的服务列表，以服务名（spring.application.name）作为路径创建动态路由进行转发，从而实现动态路由功能。

![image-20221211094109639](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211094109639.png)

```yaml
server:
  port: 9527
spring:
  application:
    name: cloud-gateway
  cloud:
    gateway:
      discovery:
        locator:
          enabled: true #开启从注册中心动态创建路由的功能，利用微服务名进行路由
      routes:
        - id: payment_routh #payment_route    #路由的ID，没有固定规则但要求唯一，建议配合服务名
          #uri: http://localhost:8001          #匹配后提供服务的路由地址
          uri: lb://CLOUD-PAYMENT-HYSTRIX-SERVICE #匹配后提供服务的路由地址
          predicates:
            - Path=/payment/query/**         # 断言，路径相匹配的进行路由

        - id: payment_routh2 #payment_route    #路由的ID，没有固定规则但要求唯一，建议配合服务名
          #uri: http://localhost:8001          #匹配后提供服务的路由地址
          uri: lb://CLOUD-PAYMENT-HYSTRIX-SERVICE #匹配后提供服务的路由地址
          predicates:
            - Path=/payment/definitionLB         # 断言，路径相匹配的进行路由

eureka:
  client:
    #表示是否将自己注册进EurekaServer默认为true。
    register-with-eureka: true

    #是否从EurekaServer抓取已有的注册信息，默认为true。单节点无所谓，集群必须设置为true才能配合ribbon使用负载均衡
    fetchRegistry: true
    service-url:
      #单机版
      defaultZone: http://localhost:7001/eureka
  instance:
    #服务器实例名称
    instance-id: gateway9527
    #访问路径可以显示IP地址
    prefer-ip-address: true
    #Eureka客户端向服务端发送心跳的时间间隔，单位为秒(默认是30秒)
    #lease-renewal-interval-in-seconds: 1
    #Eureka服务端在收到最后一次心跳后等待时间上限，单位为秒(默认是90秒)，超时将剔除服务
    #lease-expiration-duration-in-seconds: 2
```

启动类

![image-20221211094244742](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211094244742.png)

run

![image-20221211094312550](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211094312550.png)

![image-20221211234307491](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211234307491.png)

#### Filter

通常情况下，出于**安全方面的考虑**，**服务端**提供的服务往往都会有一定的**校验逻辑**，例如用户**登陆状态校验、签名校验**等。

Spring Cloud Gateway 提供了以下两种类型的过滤器，可以对请求和响应进行精细化控制。

| 过滤器类型 | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| Pre 类型   | 这种过滤器在请求被转发到微服务之前可以对请求进行拦截和修改，例如参数校验、权限校验、流量监控、日志输出以及协议转换等操作。 |
| Post 类型  | 这种过滤器在微服务对请求做出响应后可以对响应进行拦截和再处理，例如修改响应内容或响应头、日志输出、流量监控等。
按照作用范围划分，Spring Cloud gateway 的 Filter 可以分为 2 类： |

- GatewayFilter：应用在单个路由或者一组路由上的过滤器。
- GlobalFilter：应用在所有的路由上的过滤器。

##### GatewayFilter

**GatewayFilter** 是 Spring Cloud Gateway 网关中提供的一种应用在单个或一组路由上的过滤器。它可以对单个路由或者一组路由上传入的请求和传出响应进行拦截，并实现一些与业务无关的功能，比如登陆状态校验、签名校验、权限校验、日志输出、流量监控等。

[Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/#gatewayfilter-factories)

Spring Cloud Gateway 内置了多达 31 种 GatewayFilter，下表中列举了几种常用的网关过滤器及其使用示例。

| 路由过滤器             | 描述                                                         | 参数                                                         | 使用示例                                               |
| ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------ |
| AddRequestHeader       | 拦截传入的请求，并在请求上添加一个指定的请求头参数。         | name：需要添加的请求头参数的 key； value：需要添加的请求头参数的 value。 | - AddRequestHeader=my-request-header,1024              |
| AddRequestParameter    | 拦截传入的请求，并在请求上添加一个指定的请求参数。           | name：需要添加的请求参数的 key； value：需要添加的请求参数的 value。 | - AddRequestParameter=my-request-param,c.biancheng.net |
| AddResponseHeader      | 拦截响应，并在响应上添加一个指定的响应头参数。               | name：需要添加的响应头的 key； value：需要添加的响应头的 value。 | - AddResponseHeader=my-response-header,c.biancheng.net |
| PrefixPath             | 拦截传入的请求，并在请求路径增加一个指定的前缀。             | prefix：需要增加的路径前缀。                                 | - PrefixPath=/consumer                                 |
| PreserveHostHeader     | 转发请求时，保持客户端的 Host 信息不变，然后将它传递到提供具体服务的微服务中。 | 无                                                           | - PreserveHostHeader                                   |
| RemoveRequestHeader    | 移除请求头中指定的参数。                                     | name：需要移除的请求头的 key。                               | - RemoveRequestHeader=my-request-header                |
| RemoveResponseHeader   | 移除响应头中指定的参数。                                     | name：需要移除的响应头。                                     | - RemoveResponseHeader=my-response-header              |
| RemoveRequestParameter | 移除指定的请求参数。                                         | name：需要移除的请求参数。                                   | - RemoveRequestParameter=my-request-param              |
| RequestSize            | 配置请求体的大小，当请求体过大时，将会返回 413 Payload Too Large。 | maxSize：请求体的大小。                                      | - name: RequestSize   args:    maxSize: 5000000        |

```yaml
spring:
  cloud:
    gateway: 
      routes:
        - id: xxxx
          uri: xxxx
          predicates:
            - Path=xxxx
          filters:
            - AddRequestParameter=X-Request-Id,1024 #过滤器工厂会在匹配的请求头加上一对请求头，名称为 X-Request-Id 值为 1024
            - PrefixPath=/dept #在请求路径前面加上 /dept
            ……
```



##### GlobalFilter

**GlobalFilter** 是一种作用于所有的路由上的全局过滤器，通过它，我们可以实现一些统一化的业务功能，例如权限认证、IP 访问限制等。当某个请求被路由匹配时，那么所有的 GlobalFilter 会和该路由自身配置的 GatewayFilter 组合成一个过滤器链。

[Spring Cloud Gateway](https://docs.spring.io/spring-cloud-gateway/docs/current/reference/html/#global-filters)

通常我们都会自定义一些自己的 GlobalFilter 全局过滤器以满足我们自身的业务需求，而很少直接使用 Spring Cloud Config 提供这些默认的 GlobalFilter

##### 自定义GlobalFilter

![image-20221211101915576](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211101915576.png)

```java
package com.eddie.springcloud.filter;

import lombok.extern.slf4j.Slf4j;
import org.springframework.cloud.gateway.filter.GatewayFilterChain;
import org.springframework.cloud.gateway.filter.GlobalFilter;
import org.springframework.core.Ordered;
import org.springframework.http.HttpStatus;
import org.springframework.stereotype.Component;
import org.springframework.web.server.ServerWebExchange;
import reactor.core.publisher.Mono;
import java.util.Date;

/**
 @author EddieZhang
 @create 2022-12-11 10:11
 */
@Component
@Slf4j
public class MyGlobalFilter implements GlobalFilter, Ordered {

    @Override
    public Mono<Void> filter(ServerWebExchange exchange, GatewayFilterChain chain) {
        log.info("进入自定义的全局过滤器 MyGlobalFilter" + new Date());
        String username = exchange.getRequest().getQueryParams().getFirst("username");
        if (username == null) {
            log.info("username can't empty!!");
            exchange.getResponse().setStatusCode(HttpStatus.NOT_ACCEPTABLE);
            return exchange.getResponse().setComplete();
        } else {
            return chain.filter(exchange);
        }
    }

    @Override
    public int getOrder() {
        return 0;//过滤器的顺序，0 表示第一个
    }
}
```

![image-20221211101942987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211101942987.png)

![image-20221211101953219](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211101953219.png)

![image-20221211102006225](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211102006225.png)

![image-20221211102014828](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211102014828.png)

## 分布式配置Config

在分布式微服务系统中，几乎所有服务的运行都离不开配置文件的支持，这些配置文件通常由各个服务自行管理，以 properties 或 yml 格式保存在各个微服务的类路径下，例如 application.properties 或 application.yml 等。

这种将配置文件散落在各个服务中的管理方式，存在以下问题：

- **管理难度大**：配置文件散落在各个微服务中，难以管理。
- **安全性低**：配置跟随源代码保存在代码库中，容易造成配置泄漏。
- **时效性差**：微服务中的配置修改后，必须重启服务，否则无法生效。
- **局限性明显**：无法支持动态调整，例如日志开关、功能开关。

Spring Cloud Config 可以将各个微服务的配置文件集中存储在一个外部的存储仓库或系统（例如 Git 、SVN 等）中，对配置的统一管理，以支持各个微服务的运行。

Spring Cloud Config 包含以下两个部分：

- **Config Server：也被称为分布式配置中心**，它是一个独立运行的微服务应用，用来连接配置仓库并为客户端提供获取配置信息、加密信息和解密信息的访问接口。
- **Config Client：指的是微服务架构中的各个微服务**，它们通过 Config Server 对配置进行管理，并从 Config Sever 中获取和加载配置信息。

Spring Cloud Config 默认使用 Git 存储配置信息，因此使用 Spirng Cloud Config 构建的配置服务器天然就支持对微服务配置的版本管理。我们可以使用 Git 客户端工具方便地对配置内容进行管理和访问。除了 Git 外，Spring Cloud Config 还提供了对其他存储方式的支持，例如 SVN、本地化文件系统等。

![image-20221211162758236](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211162758236.png)

### Spring Cloud Config 工作原理

![image-20221211162753971](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211162753971.png)

Spring Cloud Config 工作流程如下：

1. 开发或运维人员提交配置文件到远程的 Git 仓库。
2. Config 服务端（分布式配置中心）负责连接配置仓库 Git，并对 Config 客户端暴露获取配置的接口。
3. Config 客户端通过 Config 服务端暴露出来的接口，拉取配置仓库中的配置。
4. Config 客户端获取到配置信息，以支持服务的运行。

### Spring Cloud Config 的特点

Spring Cloud Config 具有以下特点：

- Spring Cloud Config 由 Spring Cloud 团队开发，可以说是 Spring 的亲儿子，能够与 Spring 的生态体系无缝集成。
- Spring Cloud Config 将所有微服务的配置文件集中存储在一个外部的存储仓库或系统（例如 Git）中，统一管理。
- Spring Cloud Config 配置中心将配置以 REST 接口的形式暴露给各个微服务，以方便各个微服务获取。
- 微服务可以通过 Spring Cloud Config 向配置中心统一拉取属于它们自己的配置信息。
- 当配置发生变化时，微服务不需要重启即可感知到配置的变化，并自动获取和应用最新配置。
- 一个应用可能有多个环境，例如开发（dev）环境、测试（test）环境、生产（prod）环境等等，开发人员可以通过 Spring Cloud Config 对不同环境的各配置进行管理，且能够确保应用在环境迁移后仍然有完整的配置支持其正常运行。

### 搭建 Config 服务端

![image-20221211172141431](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172141431.png)

pom

![image-20221211172148485](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172148485.png)

application.yml

![image-20221211172159912](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172159912.png)

![image-20221211172232192](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172232192.png)

```yaml
server:
  port: 3344

spring:
  application:
    name:  cloud-config-center #注册进Eureka服务器的微服务名
  cloud:
    config:
      server:
        git:
          uri: https://github.com/EddieZturbo/SpringCloud_Config_Demo.git #GitHub上面的git仓库名字
          ####搜索目录/仓库名
          search-paths:
            - SpringCloud_Config_Demo
      ####读取分支
      label: master


eureka:
  client:
    service-url:
      #单机
      defaultZone: http://localhost:7001/eureka
```

启动类

![image-20221211172300585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172300585.png)

访问配置文件

![image-20221211172326673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211172326673.png)

Spring Cloud Config 规定了一套配置文件访问规则，如下表。

| 访问规则                                  | 示例                   |
| ----------------------------------------- | ---------------------- |
| /{application}/{profile}[/{label}]        | /config/dev/master     |
| /{application}-{profile}.{suffix}         | /config-dev.yml        |
| /{label}/{application}-{profile}.{suffix} | /master/config-dev.yml |


访问规则内各参数说明如下。

- {application}：应用名称，即配置文件的名称，例如 config-dev。
- {profile}：环境名，一个项目通常都有开发（dev）版本、测试（test）环境版本、生产（prod）环境版本，配置文件则以 application-{profile}.yml 的形式进行区分，例如 application-dev.yml、application-test.yml、application-prod.yml 等。
- {label}：Git 分支名，默认是 master 分支，当访问默认分支下的配置文件时，该参数可以省略，即第二种访问方式。
- {suffix}：配置文件的后缀，例如 config-dev.yml 的后缀为 yml。


通过这套规则，我们在浏览器上就直接对配置文件进行访问。

### 搭建 Config 客户端

![image-20221211184738944](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184738944.png)

pom

![image-20221211184745751](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184745751.png)

bootstrap.yml

bootstrap.yml 是系统级别的，加载优先级高于 application.yml ，负责从外部加载配置并解析

![image-20221211184814732](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184814732.png)

启动类

![image-20221211184900700](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184900700.png)

ConfigClientController

![image-20221211184912572](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184912572.png)

run

![image-20221211184921328](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211184921328.png)

### 手动刷新配置

通过该实例，我们可以得到以下 2 点结论，

- 配置更新后，Spring Cloud Config 服务端（Server）可以直接从 Git 仓库中获取最新的配置。
- 除非重启 Spring Cloud Config 客户端（Client），否则无法通过 Spring Cloud Config 服务端获取最新的配置信息。

解决不重启 Config 客户端无法获取最新配置的问题

![image-20221211202211896](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202211896.png)

![image-20221211202229567](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202229567.png)

![image-20221211202249569](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202249569.png)

![image-20221211202310730](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202310730.png)

```
curl -X POST "http://localhost:3355/actuator/refresh"
```

![image-20221211202354959](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202354959.png)

### Config+Bus 实现配置的动态刷新

Spring Cloud Bus 又被称为消息总线，它能够通过轻量级的消息代理（例如 RabbitMQ、Kafka 等）将微服务架构中的各个服务连接起来，实现广播状态更改、事件推送等功能，还可以实现微服务之间的通信功能。

目前 Spring Cloud Bus 支持两种消息代理：RabbitMQ 和 Kafka。

当 Git 仓库中的配置发生了改变，我们只需要向某一个服务（既可以是 Config 服务端，也可以是 Config 客户端）发送一个 POST 请求，Spring Cloud Bus 就可以通过消息代理通知其他服务重新拉取最新配置，以实现配置的动态刷新。

![image-20221211202505026](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211202505026.png)

1. 当 Git 仓库中的配置发生改变后，运维人员向 Config 服务端发送一个 POST 请求，请求路径为“/actuator/refresh”。
2. Config 服务端接收到请求后，会将该请求转发给服务总线 Spring Cloud Bus。
3. Spring Cloud Bus 接到消息后，会通知给所有 Config 客户端。
4. Config 客户端接收到通知，请求 Config 服务端拉取最新配置。
5. 所有 Config 客户端都获取到最新的配置。

#### Spring Cloud Bus 动态刷新配置（全局广播）

![image-20221211225958550](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211225958550.png)

![image-20221211230055319](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230055319.png)

![image-20221211230104798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230104798.png)

**3344**

pom

![image-20221211230009112](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230009112.png)

application.yml

![image-20221211230025739](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230025739.png)

**3355**

pom

![image-20221211230147959](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230147959.png)

bootstrap.yml

![image-20221211230221792](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230221792.png)

controller

![image-20221211230254187](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230254187.png)

**3306**

pom

![image-20221211230317743](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230317743.png)

bootstrap.yml

![image-20221211230331257](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230331257.png)

controller

![image-20221211230346936](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230346936.png)

**cmd**

![image-20221211230359380](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230359380.png)

```
curl -X POST "http://localhost:3344/actuator/bus-refresh"
```

![image-20221211230435897](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211230435897.png)

#### Spring Cloud Bus 动态刷新配置（定点通知）

所谓定点通知，就是不再通知所有的 Config 客户端，而是根据需求只通知其中某一个 Config 客户端。

使用 Spring Cloud Bus 实现定点通知的方法十分简单，只要我们在发送 POST 请求时使用以下格式即可。

```
http://{hostname}:{port}/actuator/bus-refresh/{destination}
```


参数说明如下：

- {hostname}： 表示 Config 服务端的主机地址，既可以是域名，也可以是 IP 地址。
- {port}：表示 Config 服务端的端口号.
- {destination}：表示需要定点通知的 Config 客户端（微服务），由 Config 客户端的服务名（spring.application.name）+端口号（server.port）组成，例如只通知 micro-service-cloud-config-client-3355 刷新配置，则取值为 spring-cloud-config-client:3355。

```
curl -X POST "http://localhost:3344/actuator/bus-refresh/CLOUD-CONFIG-CLIENT-BUS:3355"
```

## Stream消息驱动

[Spring Cloud Stream](https://spring.io/projects/spring-cloud-stream)

[官方文档中文版！Spring Cloud Stream 快速入门 - 邴越 - 博客园 (cnblogs.com)](https://www.cnblogs.com/binyue/p/12222198.html)

![image-20221212141704826](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212141704826.png)

![image-20221212142311058](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212142311058.png)

**通过定义绑定器Binder作为中间层；实现了应用程序与消息中间件细节之间的隔离**

**无感知的使用消息中间件**

Stream解决了开发人员无感知的使用消息中间件的问题，因为Stream对消息中间件的进一步封装，可以做到代码层面对中间件的无感知。

**中间件和服务的高度解耦**

Spring Cloud Stream进行了配置隔离，只需要调整配置，开发中可以动态的切换中间件(如rabbitmq切换为kafka)，使得微服务开发的高度解耦，服务可以关注更多自己的业务流程。

**应用模型**

Spring Cloud Stream由一个中立的中间件内核组成。Spring Cloud Stream会注入输入和输出的channels，应用程序通过这些channels与外界通信，而channels则是通过一个明确的中间件Binder与外部brokers连接。

![image-20221212142048011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212142048011.png)

**各大消息中间件的绑定抽象**

Spring Cloud Stream提供对Kafka，Rabbit MQ，Redis，和Gemfire的Binder实现。Spring Cloud Stream还包括了一个TestSupportBinder，TestSupportBinder预留一个未更改的channel以便于直接地、可靠地和channels通信。

### **集成Kafka**

```xml
    <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-stream-binder-kafka</artifactId>
    </dependency>
XML 复制 全屏
```

### **集成RabbitMQ**

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-stream-rabbit</artifactId>
</dependency>
```

#### 消息驱动生产者

![image-20221212181136573](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181136573.png)

pom

![image-20221212181047567](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181047567.png)

application.yml

![image-20221212185523842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212185523842.png)

```yaml
server:
  port: 8801

spring:
  application:
    name: cloud-stream-provider
  rabbitmq:
    host: 192.168.199.144
    port: 5672
    username: eddie
    password: eddie
  cloud:
    stream:
      binders: # 在此处配置要绑定的rabbitmq的服务信息；
        defaultRabbit: # 表示定义的名称，用于于binding整合
          type: rabbit # 消息组件类型
      bindings: # 服务的整合处理
        output: # 这个名字是一个通道的名称
          destination: studyExchange # 表示要使用的Exchange名称定义
          content-type: application/json # 设置消息类型，本次为json，文本则设置“text/plain”
          binder: defaultRabbit # 设置要绑定的消息服务的具体设置
eureka:
  client: # 客户端进行Eureka注册的配置
    service-url:
      defaultZone: http://localhost:7001/eureka
  instance:
    lease-renewal-interval-in-seconds: 2 # 设置心跳的时间间隔（默认是30秒）
    lease-expiration-duration-in-seconds: 5 # 如果现在超过了5秒的间隔（默认是90秒）
    instance-id: send-8801.com  # 在信息列表时显示主机名称
    prefer-ip-address: true     # 访问的路径变为IP地址
```

启动类

![image-20221212181125365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181125365.png)

MessageProviderImpl

![image-20221212181229854](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181229854.png)

controller

![image-20221212181240530](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181240530.png)

#### 消息驱动消费者

![image-20221212181257326](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181257326.png)

pom

![image-20221212181305429](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181305429.png)

application.yml

![image-20221212185543095](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212185543095.png)

```yaml
server:
  port: 8802
spring:
  application:
    name: cloud-stream-consumer
  rabbitmq:
    host: 192.168.199.144
    port: 5672
    username: eddie
    password: eddie
  cloud:
    stream:
      binders: # 在此处配置要绑定的rabbitmq的服务信息；
        defaultRabbit: # 表示定义的名称，用于于binding整合
          type: rabbit # 消息组件类型
      bindings: # 服务的整合处理
        input: # 这个名字是一个通道的名称
          destination: studyExchange # 表示要使用的Exchange名称定义
          content-type: application/json # 设置消息类型，本次为对象json，如果是文本则设置“text/plain”
          binder: defaultRabbit # 设置要绑定的消息服务的具体设置
          group: eddie-A
eureka:
  client: # 客户端进行Eureka注册的配置
    service-url:
      defaultZone: http://localhost:7001/eureka
  instance:
    lease-renewal-interval-in-seconds: 2 # 设置心跳的时间间隔（默认是30秒）
    lease-expiration-duration-in-seconds: 5 # 如果现在超过了5秒的间隔（默认是90秒）
    instance-id: receive-8802.com  # 在信息列表时显示主机名称
    prefer-ip-address: true     # 访问的路径变为IP地址
```

启动类

![image-20221212181332792](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181332792.png)

controller

![image-20221212181345187](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181345187.png)

#### 运行

![image-20221212181408127](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181408127.png)

![image-20221212181439179](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181439179.png)

![image-20221212181447040](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181447040.png)

#### 重复消费

使用Stream中的**分组（group）进行解决**

Stream中属于**同一组（group）的**多个消费者是**竞争关系**，能够**保证消息只会被其中的一个服务消费一次**

**不同组（group）的**可以全面消费（**重复消费**）

![image-20221212181727040](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181727040.png)

![image-20221212181744476](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212181744476.png)

#### 消息持久化

**分组（group）**

先启动8801发送消息到rabbitMQ	-->	再启动消息消费服务

**有group**的属性配置的**仍然会接收到消息**（持久化）

**无group**的属性配置的则**不会接收到消息**

## Sleuth分布式请求链路跟踪

[Spring Cloud Sleuth](https://spring.io/projects/spring-cloud-sleuth)

[GitHub - spring-cloud/spring-cloud-sleuth: Distributed tracing for spring cloud](https://github.com/spring-cloud/spring-cloud-sleuth#spring-cloud-sleuth)

**Sleuth为追踪** 	**Zipkin为图形化展示**

[分布式链路追踪之Spring Cloud Sleuth+Zipkin最全教程！ - bucaichenmou - 博客园 (cnblogs.com)](https://www.cnblogs.com/cbvlog/p/15571496.html)

**安装zipkin的jar包**

[io.zipkin : zipkin-server : 2.23.4 - Maven Central Repository Search](https://search.maven.org/artifact/io.zipkin/zipkin-server/2.23.4/jar)

**cmd控制台启动zipkin服务端**

![image-20221212193822191](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212193822191.png)

**访问客户端界面**	port：9411

![image-20221212194105519](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212194105519.png)

**搭建sleuth链路跟踪+zipkin客户端**

![image-20221212195503812](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195503812.png)

pom

![image-20221212195515952](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195515952.png)

application.yml

![image-20221212195604054](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195604054.png)

run

![image-20221212195715626](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195715626.png)

![image-20221212195650291](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195650291.png)

![image-20221212195701349](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212195701349.png)

# SpringCloud Alibaba

[Spring Cloud Alibaba](https://spring.io/projects/spring-cloud-alibaba)

[spring-cloud-alibaba/README-zh.md at 2021.x · alibaba/spring-cloud-alibaba · GitHub](https://github.com/alibaba/spring-cloud-alibaba/blob/2021.x/README-zh.md)

| Spring Cloud 第一代实现（Netflix） | 状态                                             | Spring Cloud 第二代实现（Alibaba） | 状态                                                 |
| ---------------------------------- | ------------------------------------------------ | ---------------------------------- | ---------------------------------------------------- |
| Eureka                             | 2.0 孵化失败                                     | Nacos Discovery                    | 性能更好，感知力更强                                 |
| Ribbon                             | 停更进维                                         | Spring Cloud Loadbalancer          | Spring Cloud 原生组件，用于代替 Ribbon               |
| Hystrix                            | 停更进维                                         | Sentinel                           | 可视化配置，上手简单                                 |
| Zuul                               | 停更进维                                         | Spring Cloud Gateway               | 性能为 Zuul 的 1.6 倍                                |
| Spring Cloud Config                | 搭建过程复杂，约定过多，无可视化界面，上手难点大 | Nacos Config                       | 搭建过程简单，有可视化界面，配置管理更简单，容易上手 |

## 主要功能

- **服务限流降级**：默认支持 WebServlet、WebFlux、OpenFeign、RestTemplate、Spring Cloud Gateway、Dubbo 和 RocketMQ 限流降级功能的接入，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。
- **服务注册与发现**：适配 Spring Cloud 服务注册与发现标准，默认集成了 Ribbon 的支持。
- **分布式配置管理**：支持分布式系统中的外部化配置，配置更改时自动刷新。
- **消息驱动能力**：基于 Spring Cloud Stream 为微服务应用构建消息驱动能力。
- **分布式事务**：使用 @GlobalTransactional 注解， 高效并且对业务零侵入地解决分布式事务问题。
- **阿里云对象存储**：阿里云提供的海量、安全、低成本、高可靠的云存储服务。支持在任何应用、任何时间、任何地点存储和访问任意类型的数据。
- **分布式任务调度**：提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。同时提供分布式的任务执行模型，如网格任务。网格任务支持海量子任务均匀分配到所有 Worker（schedulerx-client）上执行。
- **阿里云短信服务**：覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。

更多功能请参考 [Roadmap](https://github.com/alibaba/spring-cloud-alibaba/blob/2021.x/Roadmap-zh.md)

除了上述所具有的功能外，针对企业级用户的场景，Spring Cloud Alibaba 配套的企业版微服务治理方案 [微服务引擎MSE](https://www.aliyun.com/product/aliware/mse?spm=github.spring.com.topbar) 还提供了企业级微服务治理中心，包括全链路灰度、服务预热、无损上下线和离群实例摘除等更多更强大的治理能力，同时还提供了企业级 Nacos 注册配置中心，企业级云原生网关等多种产品及解决方案

## **组件**

**[Sentinel](https://github.com/alibaba/Sentinel)**：把流量作为切入点，从流量控制、熔断降级、系统负载保护等多个维度保护服务的稳定性。

**[Nacos](https://github.com/alibaba/Nacos)**：一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。

**[RocketMQ](https://rocketmq.apache.org/)**：一款开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订阅服务。

**[Seata](https://github.com/seata/seata)**：阿里巴巴开源产品，一个易于使用的高性能微服务分布式事务解决方案。

**[Alibaba Cloud OSS](https://www.aliyun.com/product/oss)**: 阿里云对象存储服务（Object Storage Service，简称 OSS），是阿里云提供的海量、安全、低成本、高可靠的云存储服务。您可以在任何应用、任何时间、任何地点存储和访问任意类型的数据。

**[Alibaba Cloud SchedulerX](https://cn.aliyun.com/aliware/schedulerx)**: 阿里中间件团队开发的一款分布式任务调度产品，提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。

**[Alibaba Cloud SMS](https://www.aliyun.com/product/sms)**: 覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。

更多组件请参考 [Roadmap](https://github.com/alibaba/spring-cloud-alibaba/blob/2022.0/Roadmap-zh.md)。

## Nacos

Nacos 是一个更易于帮助构建云原生应用的动态**服务发现、配置和服务管理**平台（参考自 [Nacos 官网](https://nacos.io/zh-cn/index.html)）。

![image-20221214090146846](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214090146846.png)

| 组成部分 | 全称              | 描述                                                         |
| -------- | ----------------- | ------------------------------------------------------------ |
| Na       | naming/nameServer | 即服务注册中心，与 Spring Cloud **Eureka** 的功能类似。      |
| co       | configuration     | 即配置中心，与 Spring Cloud **Config**+Spring Cloud **Bus** 的功能类似。 |
| s        | service           | 即服务，表示 Nacos 实现的服务注册中心和配置中心都是以服务为核心的。 |

![image-20221214090656608](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214090656608.png)

![image-20221214090556567](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214090556567.png)

在图 中共涉及到以下 3 个角色：

- 服务注册中心（Register Service）：它是一个 Nacos Server，可以为服务提供者和服务消费者提供服务注册和发现功能。
- 服务提供者（Provider Service）：它是一个 Nacos Client，用于对外服务。它将自己提供的服务注册到服务注册中心，以供服务消费者发现和调用。
- 服务消费者（Consumer Service）：它是一个 Nacos Client，用于消费服务。它可以从服务注册中心获取服务列表，调用所需的服务。


Nacos 实现服务注册与发现的流程如下：

1. 从 Nacos 官方提供的下载页面中，下载 Nacos Server 并运行。
2. 服务提供者 Nacos Client 启动时，会把服务以服务名（spring.application.name）的方式注册到服务注册中心（Nacos Server）；
3. 服务消费者 Nacos Client 启动时，也会将自己的服务注册到服务注册中心；
4. 服务消费者在注册服务的同时，它还会从服务注册中心获取一份服务注册列表信息，该列表中包含了所有注册到服务注册中心上的服务的信息（包括服务提供者和自身的信息）；
5. 在获取了服务提供者的信息后，服务消费者通过 HTTP 或消息中间件远程调用服务提供者提供的服务。 

### Nacos 的特性

Nacos 提供了一系列简单易用的特性，能够帮助我们快速地实现动态服务发现、服务配置等功能。

#### 服务发现

Nacos 支持基于 DNS 和 RPC 的服务发现。当服务提供者使用原生 SDK、OpenAPI 或一个独立的 Agent TODO 向 Nacos 注册服务后，服务消费者可以在 Nacos 上通过 DNS TODO 或 HTTP&API 查找、发现服务。

#### 服务健康监测

Nacos 提供对服务的实时健康检查，能够阻止请求发送到不健康主机或服务实例上。Nacos 还提供了一个健康检查仪表盘，能够帮助我们根据健康状态管理服务的可用性及流量。

#### 动态配置服务

动态配置服务可以让我们以中心化、外部化和动态化的方式，管理所有环境的应用配置和服务配置。

动态配置消除了配置变更时重新部署应用和服务的需要，让配置管理变得更加高效、敏捷。

配置中心化管理让实现无状态服务变得更简单，让服务按需弹性扩展变得更容易。

Nacos 提供了一个简洁易用的 UI 帮助我们管理所有服务和应用的配置。Nacos 还提供包括配置版本跟踪、金丝雀发布、一键回滚配置以及客户端配置更新状态跟踪在内的一系列开箱即用的配置管理特性，帮助我们更安全地在生产环境中管理配置变更和降低配置变更带来的风险。

#### 动态 DNS 服务

Nacos 提供了动态 DNS 服务，能够让我们更容易地实现负载均衡、流量控制以及数据中心内网的简单 DNS 解析服务。

Nacos 提供了一些简单的 DNS APIs TODO，可以帮助我们管理服务的关联域名和可用的 IP:PORT 列表。

#### 服务及其元数据管理

Nacos 能让我们从微服务平台建设的视角管理数据中心的所有服务及元数据，包括管理服务的描述、生命周期、服务的静态依赖分析、服务的健康状态、服务的流量管理、路由及安全策略、服务的 SLA 以及 metrics 统计数据。

### Nacos安装运行

[Release 2.0.3 (July 28, 2021) · alibaba/nacos · GitHub](https://github.com/alibaba/nacos/releases/tag/2.0.3)

```
startup.cmd -m standalone
```

![image-20221214091849240](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214091849240.png)

```
http://localhost:8848/nacos
```

![image-20221214091952366](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214091952366.png)

![image-20221214092052532](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214092052532.png)

### Nacos服务注册中心

#### Nacos-Client-Provider

Father_Project-pom

![image-20221214100646477](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100646477.png)

pom

![image-20221214100716381](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100716381.png)

application.yml

![image-20221214100731626](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100731626.png)

启动类

![image-20221214100742525](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100742525.png)

run

![image-20221214100754048](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100754048.png)

#### Nacos-Client-Consumer

Father_Project-pom

![image-20221214100646477](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214100646477.png)

pom

![image-20221214105230447](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105230447.png)

application.yml

![image-20221214105243953](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105243953.png)

![image-20221214105304316](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105304316.png)

启动类

![image-20221214105407912](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105407912.png)

config

![image-20221214105333461](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105333461.png)

controller

![image-20221214105347020](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105347020.png)

run

![image-20221214105419268](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105419268.png)

![image-20221214105429780](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105429780.png)

#### 集成了Ribbon；提供负载均衡

![image-20221214105545706](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105545706.png)

![image-20221214105557486](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214105557486.png)

默认轮询方式

### Nacos服务配置中心

[Nacos config · alibaba/spring-cloud-alibaba Wiki · GitHub](https://github.com/alibaba/spring-cloud-alibaba/wiki/Nacos-config)

#### 配置的优先级

Spring Cloud Alibaba Nacos Config 目前提供了三种配置能力从 Nacos 拉取相关的配置。

- A: 通过 `spring.cloud.nacos.config.shared-configs[n].data-id` 支持多个共享 Data Id 的配置
- B: 通过 `spring.cloud.nacos.config.extension-configs[n].data-id` 的方式支持多个扩展 Data Id 的配置
- C: 通过内部相关规则(应用名、应用名+ Profile )自动生成相关的 Data Id 配置

当三种方式共同使用时，他们的一个优先级关系是:A < B < C

#### 完全关闭配置

通过设置 spring.cloud.nacos.config.enabled = false 来完全关闭 Spring Cloud Nacos Config

#### 基本配置

取代springcloud的config+bus

**自带动态刷新**

![image-20221214114652490](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214114652490.png)

```
${prefix}-${spring.profiles.active}.${file-extension}
微服务名-环境-.yaml

dataId 格式中各参数说明如下：
${prefix}：默认取值为微服务的服务名，即配置文件中 spring.application.name 的值，我们可以在配置文件中通过配置 spring.cloud.nacos.config.prefix 来指定。
${spring.profiles.active}：表示当前环境对应的 Profile，例如 dev、test、prod 等。当没有指定环境的 Profile 时，其对应的连接符也将不存在， dataId 的格式变成 ${prefix}.${file-extension}。
${file-extension}：表示配置内容的数据格式，我们可以在配置文件中通过配置项 spring.cloud.nacos.config.file-extension 来配置，例如 properties 和 yaml。
```

![image-20221214114912531](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214114912531.png)

pom

![image-20221214115059675](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214115059675.png)

application.yml

一定要配active环境 不能为空

![image-20221214115112372](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214115112372.png)

bootstrap.yml

![image-20221214115125933](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214115125933.png)

启动类

![image-20221214115135644](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214115135644.png)

controller

![image-20221214115147314](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214115147314.png)

#### 加载多配置集

![image-20221217102424710](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217102424710.png)

![image-20221217102436522](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217102436522.png)

#### 命名空间-分组-DataId

![image-20221214124351057](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214124351057.png)

![image-20221214121109522](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221214121109522.png)

### Nacos集群

## Sentinel

https://sentinelguard.io/zh-cn/

https://github.com/alibaba/Sentinel

https://sentinelguard.io/zh-cn/docs/introduction.html

![image-20221219091647903](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219091647903.png)

![image-20221219091608139](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219091608139.png)

![image-20221219091714052](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219091714052.png)

![image-20221219091843841](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219091843841.png)

### 整合SpringBoot项目

#### 环境配置

> **①引入spring-cloud-starter-alibaba-sentinel场景启动器**
>
> ```xml
> <dependency>
>     <groupId>com.alibaba.cloud</groupId>
>     <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
> </dependency>
> ```
>
> **②启动官网下载的dashboard的jar包进行可视化监控和配置sentinel-dashboard-1.8.1.jar**
>
> ![image-20230324234155675](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230324234155675.png)
>
> 
>
> **③每个服务中配置**
>
> ```yaml
> spring:
>   cloud:
>     sentinel:
>       transport:
>         #配置sentinel dashboard地址
>         dashboard: localhost:8333
>         #默认8719端口，假如被占用会自动从8719开始依次+1扫描，直至找到未被占用的端口
>         port: 8719
> ```
>
> **④开启实时监控**
> 引入actuator依赖
>
> ```xml
> <dependency>
>     <groupId>org.springframework.boot</groupId>
>     <artifactId>spring-boot-starter-actuator</artifactId>
> </dependency>
> ```
>
> 服务配置
>
> ```properties
> management.endpoints.web.exposure.include=*
> ```

![image-20230325000906373](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325000906373.png)![image-20230324234312746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230324234312746.png)

#### 自定义配置

##### 配置限流的响应数据

```java
@Configuration//TODO 自定义流控响应数据
public class SentinelGlobalConfig implements UrlBlockHandler {

    @Override
    public void blocked(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, BlockException e) throws IOException {

        R error = R.error(BizCodeEnum.CURRENT_LIMITING_EXCEPTION.getCode(), BizCodeEnum.CURRENT_LIMITING_EXCEPTION.getMessage());
        httpServletResponse.setContentType("application/json;charset=utf-8");
        httpServletResponse.getWriter().write(JSON.toJSONString(error));
        /**
         BlockException 异常接口，其子类为Sentinel五种规则异常的实现类
         AuthorityException 授权异常
         DegradeException 降级异常
         FlowException 限流异常
         ParamFlowException 参数限流异常
         SystemBlockException 系统负载异常
         String msg = null;
         if (e instanceof FlowException) {
         msg = "限流了";
         } else if (e instanceof DegradeException) {
         msg = "降级了";
         } else if (e instanceof ParamFlowException) {
         msg = "热点参数限流";
         } else if (e instanceof SystemBlockException) {
         msg = "系统规则（负载/...不满足要求）";
         } else if (e instanceof AuthorityException) {
         msg = "授权规则不通过";
         }
         */
    }
}
```

#### 整合OpenFeign的熔断和降级配置

> 可以对调用方进行服务的熔断和降级配置 也可以对服务方进行降级和熔断的配置



**openFeign的降级需要带降级的框架支持**，（消费端使用）在学习OpenFiegn的时候支持降级的框架使用的是**Hystrix**，这次是**Sentinel**

```xml
		<!--SpringCloud openfeign -->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
        <!--SpringCloud ailibaba nacos -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!--SpringCloud ailibaba sentinel -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
        </dependency>
```

![image-20230325144108081](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325144108081.png)

![image-20230325144425227](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325144425227.png)

![image-20230325144853722](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325144853722.png)

### Sentinel摘要

![image-20221219192750173](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219192750173.png)

#### 组成

Sentinel 主要由以下两个部分组成：

- Sentinel 核心库：Sentinel 的核心库不依赖任何框架或库，能够运行于 Java 8 及以上的版本的运行时环境中，同时对 Spring Cloud、Dubbo 等微服务框架提供了很好的支持。
- Sentinel 控制台（Dashboard）：Sentinel 提供的一个轻量级的开源控制台，它为用户提供了机器自发现、簇点链路自发现、监控、规则配置等功能。


Sentinel 核心库不依赖 Sentinel Dashboard，但两者结合使用可以有效的提高效率，让 Sentinel 发挥它最大的作用。

#### Sentinel 的基本概念

Sentinel 的基本概念有两个，它们分别是：**资源**和**规则**。

| 基本概念 | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| **资源** | 资源是 Sentinel 的关键概念。它可以是 Java 应用程序中的任何内容，例如由应用程序提供的服务或者是服务里的方法，甚至可以是一段代码。  我们可以通过 Sentinel 提供的 API 来定义一个资源，使其能够被 Sentinel 保护起来。通常情况下，我们可以使用方法名、URL 甚至是服务名来作为资源名来描述某个资源。 |
| **规则** | 围绕资源而设定的规则。Sentinel 支持流量控制、熔断降级、系统保护、来源访问控制和热点参数等多种规则，所有这些规则都可以动态实时调整。 |

#### Sentinel 控制台

Sentinel 提供了一个轻量级的开源控制台 Sentinel Dashboard，它提供了机器发现与健康情况管理、监控（单机和集群）、规则管理与推送等多种功能。

Sentinel 控制台提供的功能如下:

- **查看机器列表以及健康情况**：Sentinel 控制台能够收集 Sentinel 客户端发送的心跳包，判断机器是否在线。
- **监控（单机和集群聚合）**：Sentinel 控制台通过 Sentinel 客户端暴露的监控 API，可以实现秒级的实时监控。
- **规则管理和推送**：通过 Sentinel 控制台，我们还能够针对资源定义和推送规则。
- **鉴权**：从 Sentinel 1.6.0 起，Sentinel 控制台引入基本的登录功能，默认用户名和密码都是 sentinel。

Sentinel Dashboard 是我们配置和管理规则（例如流控规则、熔断降级规则等）的重要入口之一。通过它，我们不仅可以对规则进行配置和管理，还能实时查看规则的效果。

**安装启动**

[Releases · alibaba/Sentinel (github.com)](https://github.com/alibaba/Sentinel/releases)

打开命令行窗口，跳转到 Sentinel Dashboard jar 包所在的目录，执行以下命令，启动 Sentinel Dashboard。

```
java -jar sentinel-dashboard-1.8.2.jar
```

“http://localhost:8080/”默认指定的port为8080

![image-20221219094623354](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219094623354.png)

### Sentinel流控

　**流量控制（flow control）**，其原理是**监控应用流量**的 **QPS** 或**并发线程数**等**指标**，当**达到指定的阈值**时**对流量进行控制**，以**避免被瞬时的流量高峰冲垮**，从而**保障应用的高可用**性

![image-20221219113218235](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219113218235.png)

**![image-20221219112659361](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219112659361.png)**

#### 阈值类型

![image-20221219122206180](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219122206180.png)

##### QPS

Query per second--每秒的请求次数（超出阈值就限流）

![image-20221219113452879](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219113452879.png)

##### 线程数

![image-20221219121044943](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219121044943.png)

当有阈值的线程在执行中 后续的线程被限流

![image-20221219121938061](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219121938061.png)

#### 流控模式

##### 直接

直接对此资源进行流控

![image-20221219122102344](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219122102344.png)

##### 关联

可以设定高优先级资源触发阈值，对低优先级资源限流

![image-20221219122225166](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219122225166.png)

![image-20221219144723641](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219144723641.png)

##### 链路

阈值统计时，只统计从指定资源进入当前资源的请求，是对请求来源的限流

`NodeSelectorSlot` 中记录了资源之间的调用链路，这些资源通过调用关系，相互之间构成一棵调用树。这棵树的根节点是一个名字为 `machine-root` 的虚拟节点，调用链的入口都是这个虚节点的子节点。

一棵典型的调用树如下图所示：

```
     	          machine-root
                    /       \
                   /         \
             Entrance1     Entrance2
                /             \
               /               \
      DefaultNode(nodeA)   DefaultNode(nodeA)
```

上图中来自入口 `Entrance1` 和 `Entrance2` 的请求都调用到了资源 `NodeA`，Sentinel 允许只根据某个入口的统计信息对资源限流。比如我们可以设置 `FlowRule.strategy` 为 `RuleConstant.CHAIN`，同时设置 `FlowRule.ref_identity` 为 `Entrance1` 来表示只有从入口 `Entrance1` 的调用才会记录到 `NodeA` 的限流统计当中，而对来自 `Entrance2` 的调用漠不关心。

调用链的入口是通过 API 方法 `ContextUtil.enter(name)` 定义的

#### 流控效果（只有QPS支持选项）

##### 快速失败

**直接拒绝**（`RuleConstant.CONTROL_BEHAVIOR_DEFAULT`）方式。该方式是默认的流量控制方式，当QPS超过任意规则的阈值后，新的请求就会被立即拒绝，拒绝方式为抛出`FlowException`。这种方式适用于对系统处理能力确切已知的情况下，比如通过压测确定了系统的准确水位时

##### Warm up

预热

**冷启动**（`RuleConstant.CONTROL_BEHAVIOR_WARM_UP`）方式。该方式主要用于系统长期处于低水位的情况下，当流量突然增加时，直接把系统拉升到高水位可能瞬间把系统压垮。通过"冷启动"，让通过的流量缓慢增加，在一定时间内逐渐增加到阈值上限，给冷系统一个预热的时间，避免冷系统被压垮的情况

![image-20221219145341147](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219145341147.png)

![image-20221219145302667](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219145302667.png)

![image-20221219145322214](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219145322214.png)

通常冷启动的过程系统允许通过的 QPS 曲线如下图所示：

![image-20221219145112529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219145112529.png)

##### 排队等待

1. 匀速器（`RuleConstant.CONTROL_BEHAVIOR_RATE_LIMITER`）方式。这种方式严格控制了请求通过的间隔时间，也即是让请求以均匀的速度通过，对应的是漏桶算法。具体的例子参见 [PaceFlowDemo](https://github.com/alibaba/Sentinel/blob/master/sentinel-demo/sentinel-demo-basic/src/main/java/com/alibaba/csp/sentinel/demo/flow/PaceFlowDemo.java)。

该方式的作用如下图所示：

![image-20221219145526064](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219145526064.png)

这种方式主要用于**处理间隔性突发的流量**，例如消息队列。想象一下这样的场景，在**某一秒有大量的请求到来，而接下来的几秒则处于空闲状态**，我们希望系统能够**在接下来的空闲期间逐渐处理这些请求**，而不是在第一秒直接拒绝多余的请求。

![image-20221219150405238](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219150405238.png)

![image-20221219150254298](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219150254298.png)

![image-20221219150336314](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219150336314.png)

![image-20221219150351363](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219150351363.png)

### cmd显示资源的实时统计信息

```
curl http://localhost:8719/cnode?id=testD-resource
```

```
idx id                thread    pass      blocked   success    total    aRt   1m-pass   1m-block   1m-all   exceptio
2   testD-resource      0        0.0       0.0       0.0        0.0      0.0   10        16         26       0.0
```

实时统计信息各列名说明如下：

- thread： 代表当前处理该资源的并发数；
- pass： 代表一秒内到来到的请求；
- blocked： 代表一秒内被流量控制的请求数量；
- success： 代表一秒内成功处理完的请求；
- total： 代表到一秒内到来的请求以及被阻止的请求总和；
- RT： 代表一秒内该资源的平均响应时间；
- 1m-pass： 则是一分钟内到来的请求；
- 1m-block： 则是一分钟内被阻止的请求；
- 1m-all： 则是一分钟内到来的请求和被阻止的请求的总和；
- exception： 则是一秒内业务本身异常的总和。

### Sentinel熔断降级

#### 熔断规则

![image-20221219155826676](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219155826676.png)

| 熔断策略                         | 说明                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| 慢调用比例 (SLOW_REQUEST_RATIO） | 选择以慢调用比例作为阈值，需要设置允许的慢调用 RT（即最大响应时间），若请求的响应时间大于该值则统计为慢调用。  当单位统计时长（statIntervalMs）内请求数目大于设置的最小请求数目，且慢调用的比例大于阈值，则接下来的熔断时长内请求会自动被熔断。  经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求响应时间小于设置的慢调用 RT 则结束熔断，若大于设置的慢调用 RT 则再次被熔断。 |
| 异常比例 (ERROR_RATIO)           | 当单位统计时长（statIntervalMs）内请求数目大于设置的最小请求数目且异常的比例大于阈值，则在接下来的熔断时长内请求会自动被熔断。  经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求成功完成（没有错误）则结束熔断，否则会再次被熔断。异常比率的阈值范围是 [0.0, 1.0]，代表 0% - 100%。 |
| 异常数 (ERROR_COUNT)             | 当单位统计时长内的异常数目超过阈值之后会自动进行熔断。  经过熔断时长后熔断器会进入探测恢复状态（HALF-OPEN 状态），若接下来的一个请求成功完成（没有错误）则结束熔断，否则会再次被熔断。 |

##### RT

![image-20221219161836692](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219161836692.png)

![image-20221219165205209](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219165205209.png)

##### 异常比例

![image-20221219175011088](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219175011088.png)

##### 异常数

![image-20221219174957968](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219174957968.png)

#### 熔断状态

![image-20221219155930496](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219155930496.png)

| 状态                       | 说明                                                         | 触发条件                                                     |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 熔断关闭状态 （CLOSED）    | 处于关闭状态时，请求可以正常调用资源。                       | 满足以下任意条件，Sentinel 熔断器进入熔断关闭状态：全部请求访问成功。单位统计时长（statIntervalMs）内请求数目小于设置的最小请求数目。未达到熔断标准，例如服务超时比例、异常数、异常比例未达到阈值。处于探测恢复状态时，下一个请求访问成功。 |
| 熔断开启状态 （OPEN）      | 处于熔断开启状态时，熔断器会一定的时间（规定的熔断时长）内，暂时切断所有请求对该资源的调用，并调用相应的降级逻辑使请求快速失败避免系统崩溃。 | 满足以下任意条件，Sentinel 熔断器进入熔断开启状态：单位统计时长内请求数目大于设置的最小请求数目，且已达到熔断标准，例如请求超时比例、异常数、异常比例达到阈值。处于探测恢复状态时，下一个请求访问失败。 |
| 探测恢复状态 （HALF-OPEN） | 处于探测恢复状态时，Sentinel 熔断器会允许一个请求调用资源。则若接下来的一个请求成功完成（没有错误）则结束熔断，熔断器进入熔断关闭（CLOSED）状态；否则会再次被熔断，熔断器进入熔断开启（OPEN）状态。 | 在熔断开启一段时间（降级窗口时间或熔断时长，单位为 s）后，Sentinel 熔断器自动会进入探测恢复状态。 |



#### Sentinel 实现熔断降级过程

 Sentinel 实现熔断降级的步骤如下：

1. 在项目中，使用 @SentinelResource 注解的 fallback 属性可以为资源指定熔断降级逻辑（方法）。
2. 通过 Sentinel 控制台或代码定义熔断规则，包括熔断策略、最小请求数、阈值、熔断时长以及统计时长等。
3. 若单位统计时长（statIntervalMs）内，请求数目大于设置的最小请求数目且达到熔断标准（例如请求超时比例、异常数、异常比例达到阈值），Sentinel 熔断器进入熔断开启状态（OPEN）。
4. 处于熔断开启状态时， @SentinelResource 注解的 fallback 属性指定的降级逻辑会临时充当主业务逻辑，而原来的主逻辑则暂时不可用。当有请求访问该资源时，会直接调用降级逻辑使请求快速失败，而不会调用原来的主业务逻辑。
5. 在经过一段时间（在熔断规则中设置的熔断时长）后，熔断器会进入探测恢复状态（HALF-OPEN），此时 Sentinel 会允许一个请求对原来的主业务逻辑进行调用，并监控其调用结果。
6. 若请求调用成功，则熔断器进入熔断关闭状态（CLOSED ），服务原来的主业务逻辑恢复，否则重新进入熔断开启状态（OPEN）。

#### 降级（兜底）

##### 系统定义兜底方法返回

![image-20221219175542668](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219175542668.png)

##### 自定义兜底方法方法

使用自定义全局降级方法类的形式 与业务代码进行解耦

![image-20221219180520864](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219180520864.png)

##### 整合OpenFeign实现服务间降级兜底

**openFeign的降级需要带降级的框架支持**，（消费端使用）在学习OpenFiegn的时候支持降级的框架使用的是**Hystrix**，这次是**Sentinel**

```xml
		<!--SpringCloud openfeign -->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
        <!--SpringCloud ailibaba nacos -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
        </dependency>
        <!--SpringCloud ailibaba sentinel -->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
        </dependency>
```

![image-20230325144108081](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325144108081.png)

![image-20230325144425227](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230325144425227.png)

#### 热点规则

![image-20221219190050996](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219190050996.png)

### @SentinelResource 注解☆

@SentinelResource 注解是 Sentinel 提供的最重要的注解之一，它还包含了多个属性，如下表。

| 属性                   | 说明                                                         | 必填与否                       | 使用要求                                                     |
| ---------------------- | ------------------------------------------------------------ | ------------------------------ | ------------------------------------------------------------ |
| value                  | 用于指定资源的名称                                           | 必填                           | -                                                            |
| entryType              | entry 类型                                                   | 可选项（默认为 EntryType.OUT） | -                                                            |
| **blockHandler**       | 服务限流后会抛出 BlockException 异常，而 blockHandler 则是用来指定一个函数来处理 BlockException 异常的。  简单点说，该属性用于指定服务限流后的后续处理逻辑。 | 可选项                         | blockHandler 函数访问范围需要是 public；返回类型需要与原方法相匹配；参数类型需要和原方法相匹配并且最后加一个额外的参数，类型为 BlockException；blockHandler 函数默认需要和原方法在同一个类中，若希望使用其他类的函数，则可以指定 blockHandler 为对应的类的 Class 对象，注意对应的函数必需为 static 函数，否则无法解析。 |
| **blockHandlerClass**  | 若 blockHandler 函数与原方法不在同一个类中，则需要使用该属性指定 blockHandler 函数所在的类。 | 可选项                         | 不能单独使用，必须与 blockHandler 属性配合使用；该属性指定的类中的 blockHandler 函数必须为 static 函数，否则无法解析。 |
| **fallback**           | 用于在抛出异常（包括 BlockException）时，提供 fallback 处理逻辑。  fallback 函数可以针对所有类型的异常（除了 exceptionsToIgnore 里面排除掉的异常类型）进行处理。 | 可选项                         | 返回值类型必须与原函数返回值类型一致；方法参数列表需要和原函数一致，或者可以额外多一个 Throwable 类型的参数用于接收对应的异常；fallback 函数默认需要和原方法在同一个类中，若希望使用其他类的函数，则可以指定 fallbackClass 为对应的类的 Class 对象，注意对应的函数必需为 static 函数，否则无法解析。 |
| **fallbackClass**      | 若 fallback 函数与原方法不在同一个类中，则需要使用该属性指定 blockHandler 函数所在的类。 | 可选项                         | 不能单独使用，必须与 fallback 或 defaultFallback 属性配合使用；该属性指定的类中的 fallback 函数必须为 static 函数，否则无法解析。 |
| defaultFallback        | 默认的 fallback 函数名称，通常用于通用的 fallback 逻辑（即可以用于很多服务或方法）。  默认 fallback 函数可以针对所以类型的异常（除了 exceptionsToIgnore 里面排除掉的异常类型）进行处理。 | 可选项                         | 返回值类型必须与原函数返回值类型一致；方法参数列表需要为空，或者可以额外多一个 Throwable 类型的参数用于接收对应的异常；defaultFallback 函数默认需要和原方法在同一个类中。若希望使用其他类的函数，则可以指定 fallbackClass 为对应的类的 Class 对象，注意对应的函数必需为 static 函数，否则无法解析。 |
| **exceptionsToIgnore** | **忽略异常兜底**    用于**指定哪些异常被排除掉**，**不会计入异常统计中**，也**不会进入 fallback 逻辑**中，而是会原样抛出。 | 可选项                         | -                                                            |

> 注：在 Sentinel 1.6.0 之前，fallback 函数只针对降级异常（DegradeException）进行处理，不能处理业务异常。

#### BlockHandler	&	FallBack对比（都是降级兜底方法）

**BlockHandler------------------配置规则异常**

**FallBack--------------------------Java异常**

若都配置都会生效

​			----------且同时出现配置规则异常以及Java异常则-------------`blockHandler`优先级更大

### Sentinel规则持久化

**搭配Nacos**	(配置规则在Nacos中进行 若服务器关闭后重启 Nacos会将规则写入Sentinel中)

pom

```xml
		<!--SpringCloud ailibaba sentinel-datasource-nacos 后续做持久化用到-->
        <dependency>
            <groupId>com.alibaba.csp</groupId>
            <artifactId>sentinel-datasource-nacos</artifactId>
        </dependency>
```

application.yml

![image-20221219200222047](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219200222047.png)

![image-20221219201049545](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219201049545.png)

![image-20221219201303110](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221219201303110.png)
