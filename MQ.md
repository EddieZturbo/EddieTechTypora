# MQ

> 消息队列（Message queue）是一种进程间通信或同一进程的不同线程间的通信方式，软件的贮列用来处理一系列的输入，通常是来自用户。
>
> **“消息队列(Message Queue)”是在消息的传输过程中保存消息的容器**。**消息队列就是一个使用队列来通信的组件。**在消息队列中，通常有生产者和消费者两个角色。生产者只负责发送数据到消息队列，谁从消息队列中取出数据处理，他不管。消费者只负责从消息队列中取出数据处理，他不管这是谁发送的数据。
>
> **消息**指的是两个应用间传递的数据。数据的类型有很多种形式，可能只包含文本字符0串，也可能包含嵌入对象。

![image-20221203103358143](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203103358143.png)

消息队列提供了异步的通信协议，每一个贮列中的纪录包含详细说明的数据，包含发生的时间，输入设备的种类，以及特定的输入参数，也就是说：消息的发送者和接收者不需要同时与消息队列交互。消息会保存在队列中，直到接收者取回它。

> > **消息队列应该有自己的持久化存储系统，能够把消息存储下来，方便后续的回溯、分析等操作**。你总不能让生产者的消息「阅后即焚」吧
> >
> > 
> >
> > **消费模型又分两种**：
> >
> > **1、点对点模式，也叫队列模式**。即每条消息只会被一个消费者消费。
> >
> > ![image-20230726105143719](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230726105143719.png)
> >
> > **2、发布订阅（Pub/Sub）模式**。发送到某个 Topic 的消息，会分发给所有订阅该 Topic 的消费者进行消费。
> >
> > ![image-20230726105159030](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230726105159030.png)
> >
> > 一个成熟的消息队列应该同时支持上述两种消费模型。
> >
> > ![image-20230726105323031](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230726105323031.png)

![image-20221203101220979](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203101220979.png)

- Producer：消息生产者，负责产生和发送消息到 Broker。
- Broker：消息处理中心。负责消息存储、确认、重试等，一般其中会包含多个 queue。
- Consumer：消息消费者，负责从 Broker 中获取消息，并进行相应处理。

![image-20221203101511015](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203101511015.png)

![image-20221203101519510](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203101519510.png)

**异步**
消息队列本身是异步的，它允许接收者在消息发送很长时间后再取回消息，这和大多数通信协议是不同的。很多情况下我们需要异步的通信协议。比如，一个进程通知另一个进程发生了一个事件，但不需要等待回应。

但消息队列的异步特点，也造成了一个缺点，就是接收者必须轮询消息队列，才能收到最近的消息。

**解耦**
消息队列减少了服务之间的耦合性，不同的服务可以通过消息队列进行通信，而不用关心彼此的实现细节，只要定义好消息的格式就行。

比如订单系统，订单最终支付成功之后可能需要给用户发送短信积分什么的，但其实这已经不是核心流程了。如果外部系统速度偏慢（比如短信网关速度不好），那么主流程的时间会加长很多，用户肯定不希望点击支付过好几分钟才看到结果。那么我们只需要通知短信系统“我们支付成功了”，不一定非要等待它处理完成。

**流量削峰与流控**
当上下游系统处理能力存在差距的时候，利用消息队列做一个通用的”载体”。在下游有能力处理的时候，再进行分发与处理。

比如在电商系统中常见的秒杀活动，每秒可能会有成千上万个请求，但是数据库的处理能力是有限的，在这种并发量下后台服务很可能会挂掉。这时就可以通过消息队列将请求压入队列中，后台服务仍然按照之前的数据处理能力处理这些请求。虽然速度会慢一些但是能保证服务正常执行。

![image-20221203103445275](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203103445275.png)

## The role of MQ

> **为什么需要消息队列:**
>
> ### **异步**
>
> 消息队列本身是异步的，它允许接收者在消息发送很长时间后再取回消息，这和大多数通信协议是不同的。很多情况下我们需要异步的通信协议。比如，一个进程通知另一个进程发生了一个事件，但不需要等待回应。
>
> 但消息队列的异步特点，也造成了一个缺点，就是接收者必须轮询消息队列，才能收到最近的消息。
>
> ### **解耦**
>
> 消息队列减少了服务之间的耦合性，不同的服务可以通过消息队列进行通信，而不用关心彼此的实现细节，只要定义好消息的格式就行。
>
> 比如订单系统，订单最终支付成功之后可能需要给用户发送短信积分什么的，但其实这已经不是核心流程了。如果外部系统速度偏慢（比如短信网关速度不好），那么主流程的时间会加长很多，用户肯定不希望点击支付过好几分钟才看到结果。那么我们只需要通知短信系统“我们支付成功了”，不一定非要等待它处理完成。
>
> ### **流量削峰与流控**
>
> 当上下游系统处理能力存在差距的时候，利用消息队列做一个通用的”载体”。在下游有能力处理的时候，再进行分发与处理。
>
> 比如在电商系统中常见的秒杀活动，每秒可能会有成千上万个请求，但是数据库的处理能力是有限的，在这种并发量下后台服务很可能会挂掉。这时就可以通过消息队列将请求压入队列中，后台服务仍然按照之前的数据处理能力处理这些请求。虽然速度会慢一些但是能保证服务正常执行。



如果**两个服务之间需要通信**，



最简单的方案就是**直接让它俩之间建立通信**就行了。但试想一下，如果所有生产数据的服务和消费数据的服务都要彼此相连，那么系统多了之后，各个系统之间的依赖关系会极其复杂。如果其中的某个系统进行一点修改，那**简直是噩梦，真可谓牵一发而动全身**。



而**在生产者和消费者之间引入中间件(MQ)**就是为了解决这个问题：消息的产生者不关心消费者是谁，它只需要把消息一股脑丢到消息队列里面，消费者会从消息队列里面消费数据。

![image-20230130092430821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130092430821.png)

**这就是系统设计中一个最简单实用的技巧：加中间层**。没有什么问题是加一个中间层服务解决不了的，如果真解决不了，那就加两层。

> PS：这不是玩笑，确实有句名言如是说：计算机领域的任何问题都可以通过添加中间层来解决。



综上，消息队列在整个系统中的主要作用就是：

**1、解耦。**使得服务之间的拓扑关系简单了很多。

**2、削峰/异步化。**消息队列可以把大量不需要实时处理的数据暂存下来，等待消费者慢慢消费。



**当然，消息队列中间件看似消除了服务之间的互相依赖，但说到底其实是让所有服务都依赖消息队列了**，如果消息队列突然坏掉，那就全完蛋了。

所以我们对这个消息队列本身的要求就非常高，具体来说有几方面：

**1、高性能。**消息队列作为整个系统的枢纽，它的性能必须足够高，否则很可能成为整个系统的性能瓶颈。

**2、高可用。**说白了就是要抗揍，如果消息队列集群中的少部分节点由于种种原因去世了，也不能影响整个集群的服务。

**3、数据可靠性。**在各种极端情况下（比如突然断网、突然断电），要保证已经收到的消息成功储存（一般是指落到磁盘中）。

**4、可扩展。**业务是发展的，如果消息队列集群快扛不住计算压力了，就需要更多的计算资源（扩容）；如果消息队列集群压力很小，导致很多节点搁那打酱油，那么需要回收计算资源（缩容）。这就需要消息队列在设计时就考虑如何进行灵活的扩缩容。

## Key points to consider

> - **消息可靠性**（如何保证消息不丢失）
> - **消息幂等性**（处理消息重复消费）
> - **消息有序性**（按预期顺序消费消息）
> - **消息堆积**（消费消息的能力不足以应对产生的消息量）

## JMS

**Java 消息服务（Java Message Service，JMS）**应用程序接口是一个 Java 平台中关于面向消息中间件（MOM）的 API，用于在两个应用程序之间，或分布式系统中发送消息，进行异步通信。

Java消息服务是一个与具体平台无关的 API，绝大多数 MOM 提供商都对 JMS 提供支持。



 **JMS 提供者**:

要使用 Java 消息服务，需要有一个 JMS 提供者，来管理会话和队列。现在有很多的开源 JMS 提供者，比如：Kafka、Apache ActiveMQ、RabbitMQ 等。

## Contrast

> **1.ActiveMQ** 
>
> **优点：**
>
> 单机吞吐量万级，时效性 ms 级，可用性高，基于主从架构实现高可用性，消息可靠性较 低的概率丢失数据 
>
> **缺点:**
>
> 官方社区现在对 ActiveMQ 5.x 维护越来越少，高吞吐量场景较少使用。
>
> 
>
> **2.Kafka** (☆)
>
> **大数据的杀手锏**，谈到大数据领域内的消息传输，则绕不开 Kafka，这款为大数据而生的消息中间件， 以其百万级 TPS 的吞吐量名声大噪，迅速成为大数据领域的宠儿，在数据采集、传输、存储的过程中发挥 着举足轻重的作用。目前已经被 LinkedIn，Uber, Twitter, Netflix 等大公司所采纳。 
>
> **优点:** 
>
> 性能卓越，单机写入 TPS 约在百万条/秒，最大的优点，就是吞吐量高。时效性 ms 级可用性非 常高，kafka 是分布式的，一个数据多个副本，少数机器宕机，不会丢失数据，不会导致不可用,消费者采 用 Pull 方式获取消息, 消息有序, 通过控制能够保证所有消息被消费且仅被消费一次;有优秀的第三方 Kafka Web 管理界面 Kafka-Manager；在日志领域比较成熟，被多家公司和多个开源项目使用；功能支持： 功能较为简单，主要支持简单的 MQ 功能，在大数据领域的实时计算以及日志采集被大规模使用 
>
> **缺点：**
>
> Kafka 单机超过 64 个队列/分区，Load 会发生明显的飙高现象，队列越多，load 越高，发送消 息响应时间变长，使用短轮询方式，实时性取决于轮询间隔时间，消费失败不支持重试；支持消息顺序， 但是一台代理宕机后，就会产生消息乱序，社区更新较慢； 
>
> 
>
> **3.RocketMQ** 
>
> RocketMQ 出自**阿里巴巴的开源产品，用 Java 语言实现，在设计时参考了 Kafka**，并做出了自己的一 些改进。被阿里巴巴广泛应用在订单，交易，充值，流计算，消息推送，日志流式处理，binglog 分发等场 景。 
>
> **优点:**
>
> 单机吞吐量十万级,可用性非常高，分布式架构,消息可以做到 0 丢失,MQ 功能较为完善，还是分 布式的，扩展性好,支持 10 亿级别的消息堆积，不会因为堆积导致性能下降,源码是 java 我们可以自己阅 读源码，定制自己公司的 MQ 
>
> **缺点：**
>
> 支持的客户端语言不多，目前是 java 及 c++，其中 c++不成熟；社区活跃度一般,没有在 MQ 核心中去实现 JMS 等接口,有些系统要迁移需要修改大量代码 
>
> 
>
> **4.RabbitMQ**  (☆)
>
> 2007 年发布，是一个在 AMQP(高级消息队列协议)基础上完成的，可复用的企业消息系统，是当前最 主流的消息中间件之一。 
>
> **优点:**
>
> 由于 **erlang 语言**的高并发特性，性能较好；吞吐量到万级，MQ 功能比较完备,健壮、稳定、易 用、跨平台、支持多种语言 如：Python、Ruby、.NET、Java、JMS、C、PHP、ActionScript、XMPP、STOMP 等，支持 AJAX 文档齐全；开源提供的管理界面非常棒，用起来很好用,社区活跃度高；更新频率相当高 https://www.rabbitmq.com/news.html 
>
> **缺点：**
>
> 商业版需要收费,学习成本较高

## ActiveMQ

[ActiveMQ (apache.org)](https://activemq.apache.org/)

![image-20221123095829247](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123095829247.png)

消息中间件

**异步化提升性能**

**降低耦合度**

**流量削峰**

![image-20221123164358785](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123164358785.png)

### ActiveMQ安装&运行

![image-20221123135904127](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123135904127.png)

![image-20221123135755851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123135755851.png)

![image-20221123135804516](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123135804516.png)

![image-20221123140047621](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123140047621.png)

![image-20221123140143701](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123140143701.png)

### 控制台访问

![image-20221123162424750](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123162424750.png)

![image-20221123162218961](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221123162218961.png)

### Java实现ActiveMQ通信

![image-20221125194440358](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125194440358.png)

### Queue

**点对点**

![image-20221125193948442](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125193948442.png)

![image-20221125135715308](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125135715308.png)

![image-20221125140823100](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125140823100.png)

引入依赖

```java
<!--activemq所需要的依赖-->
<dependency>
    <groupId>org.apache.activemq</groupId>
    <artifactId>activemq-all</artifactId>
    <version>5.15.9</version>
</dependency>
<dependency>
    <groupId>org.apache.xbean</groupId>
    <artifactId>xbean-spring</artifactId>
    <version>3.16</version>
</dependency>
```

生产者

```java
package com.eddie.produce;

import org.apache.activemq.ActiveMQConnectionFactory;

import javax.jms.*;

/**
 @author EddieZhang
 @create 2022-11-25 2:17
 */
public class MQProduce {

    public static final String ACTIVEMQ_URL = "tcp://192.168.199.135:61616";//ActiveMQ的uri地址

    public static final String QUEUE_NAME = "queue01";//queue队列的name、
    public static void main(String[] args) throws JMSException {
        //创建连接工厂，按照指定的url地址 并按照默认的用户名和密码
        ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        //通过连接工厂，获得连接
        Connection connection = activeMQConnectionFactory.createConnection();
        connection.start();

        //创建session会话
        Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);//事务，接收方式
        //创建destination（队列/topic）
        Queue queue = session.createQueue(QUEUE_NAME);
        //创建消息的生产者
        MessageProducer messageProducer = session.createProducer(queue);

        //通过MessageProducer生产三条消息到ActiveMQ的消息队列中
        for(int i = 0;i < 3;i++){
            TextMessage message = session.createTextMessage("这里是第\t" + i + "\t条消息");//创建message
            messageProducer.send(message);//发送message
        }

        //关闭资源
        messageProducer.close();
        session.close();
        connection.close();

        System.out.println("Message send success~~");

    }
}
```

消费者（接收receive方式）

```java
package com.eddie.consumer;

import org.apache.activemq.ActiveMQConnectionFactory;

import javax.jms.*;

/**
 @author EddieZhang
 @create 2022-11-25 13:17
 */
public class MQConsumer {
    public static final String ACTIVEMQ_URL = "tcp://192.168.199.135:61616";//ActiveMQ的uri地址
    public static final String QUEUE_NAME = "queue01";//queue队列的name、

    public static void main(String[] args) throws JMSException {
        //创建ActiveConnectionFactory 按照默认的用户名和密码进行连接
        ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        //使用连接Factory创建连接
        Connection connection = activeMQConnectionFactory.createConnection();
        connection.start();
        //启动连接 并创建session会话 并指定事务以及接收方式
        Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
        //创建目的地 destination queue或者topic
        Queue queue = session.createQueue(QUEUE_NAME);
        
        //创建接收者
        MessageConsumer messageConsumer = session.createConsumer(queue);
        
        //接收queue中的消息 （接收的消息类型要和消息队列中的保持一致）
        while(true){
            //指定接收时间过时不候 未指定永远接收
            TextMessage textMessage = (TextMessage) messageConsumer.receive();
            if (textMessage != null){
                System.out.println("接收到了消息:\t" + textMessage.getText());
            }else {//循环进行消息的接收 直到接收完所有消息 退出循环
                break;
            }
        }

        //释放资源
        messageConsumer.close();
        session.close();
        connection.close();
    }

}
```

消费者（接收listener监听器方式）

```java
package com.eddie.consumer;

import org.apache.activemq.ActiveMQConnectionFactory;

import javax.jms.*;
import java.io.IOException;

/**
 @author EddieZhang
 @create 2022-11-25 13:17
 */
public class MQConsumer {
    public static final String ACTIVEMQ_URL = "tcp://192.168.199.135:61616";//ActiveMQ的uri地址
    public static final String QUEUE_NAME = "queue01";//queue队列的name、

    public static void main(String[] args) throws JMSException, IOException {
        //创建ActiveConnectionFactory 按照默认的用户名和密码进行连接
        ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        //使用连接Factory创建连接
        Connection connection = activeMQConnectionFactory.createConnection();
        connection.start();
        //启动连接 并创建session会话 并指定事务以及接收方式
        Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
        //创建目的地 destination queue或者topic
        Queue queue = session.createQueue(QUEUE_NAME);
        
        //创建接收者
        MessageConsumer messageConsumer = session.createConsumer(queue);
        
        //接收queue中的消息 （接收的消息类型要和消息队列中的保持一致）
        messageConsumer.setMessageListener(new MessageListener() {//监听器接口的匿名实现类
            @Override
            public void onMessage(Message message) {
                //判断消息不为null 并且 消息属于和队列中的消息类型一致
                if(null != message && message instanceof TextMessage){
                    //将消息类型强制转换成和队列中的消息类型一致
                    TextMessage textMessage = (TextMessage) message;
                    try {
                        System.out.println("接收到了消息:\t" + textMessage.getText());
                    } catch (JMSException e) {
                        e.printStackTrace();
                    }
                }
            }
        });
        System.in.read();//一定要让程序等待接收完成再关闭资源
        //释放资源
        messageConsumer.close();
        session.close();
        connection.close();
    }

}
```

![image-20221125135022259](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125135022259.png)

#### 消费者接受消息的两种类型

![image-20221125194145356](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125194145356.png)

**receive（同步阻塞方式）可以指定阻塞时间**

```java
//接收queue中的消息 （接收的消息类型要和消息队列中的保持一致）

while(true){
    TextMessage textMessage = (TextMessage) messageConsumer.receive();
    if (textMessage != null){
        System.out.println("接收到了消息:\t" + textMessage.getText());
    }else {//循环进行消息的接收 直到接收完所有消息 退出循环
        break;
    }
}
```

**listener监听器方式（异步非阻塞）**

```java
messageConsumer.setMessageListener(new MessageListener() {//消息监听器的匿名实现类
    @Override
    public void onMessage(Message message) {
        if(null != message && message instanceof TextMessage){
            TextMessage textMessage = (TextMessage) message;
            try {
                System.out.println("接收到了消息:\t" + textMessage.getText());
            } catch (JMSException e) {
                e.printStackTrace();
            }
        }
    }
});
System.in.read();//一定要让程序等待接收完成再关闭资源
```

#### 消费者消费的三种情况

**情况一：**

生产了一批消息到消息队列中先 

开启一个消费者 则可以接收所有消息队列中的消息

**情况二：**

生产了一批消息到消息队列中先 

先开启消费者一 后开启消费者二 

消费者一接收消息队列中的所有消息 消费者二则不会再接收到消息

**情况三：**

同时开启消费者一和消费者二

再生产一批消息到消息队列中

消费者轮询（交替接收）的方式接收消息（负载均衡）

![image-20221125193113055](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125193113055.png)

![image-20221125193125955](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125193125955.png)

### Topic

**一对多**

![image-20221125194645114](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221125194645114.png)

消费者

```java
package com.eddie.consumer;

import org.apache.activemq.ActiveMQConnectionFactory;

import javax.jms.*;
import java.io.IOException;

/**
 @author EddieZhang
 @create 2022-11-25 19:55
 */
public class TopicMQConsumer {
    public static final String ACTIVEMQ_URL = "tcp://192.168.199.136:61616";//ActiveMQ的uri地址
    public static final String TOPIC_NAME = "topic01";//topic的name

    public static void main(String[] args) throws JMSException, IOException {
        //创建ActiveMQ的连接工厂 使用默认用户名和密码的方式
        ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        //获得工厂中的连接
        Connection connection = activeMQConnectionFactory.createConnection();
        connection.start();//开启连接
        //创建session会话
        Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);//是否开启事务，接收方式

        //使用session创建消费者 并指定destination
        Topic topic = session.createTopic(TOPIC_NAME);//创建消息类型
        MessageConsumer messageConsumer = session.createConsumer(topic);

        //接收消息 使用listener监听方式（异步不阻塞）
        messageConsumer.setMessageListener((message) -> {
            if(null != message && message instanceof TextMessage){
                TextMessage textMessage = (TextMessage) message;
                try {
                    System.out.println("消费者三接收到了消息:\t" + textMessage.getText());
                } catch (JMSException e) {
                    e.printStackTrace();
                }
            }
        });
        System.in.read();//控制台不关闭 等待接收完毕
        //释放资源
        messageConsumer.close();
        session.close();
        connection.close();
    }
}
```

生产者

```java
package com.eddie.produce;

import org.apache.activemq.ActiveMQConnectionFactory;

import javax.jms.*;

/**
 @author EddieZhang
 @create 2022-11-25 19:55
 */
public class TopicMQProducer {
    public static final String ACTIVEMQ_URL = "tcp://192.168.199.136:61616";//ActiveMQ的uri地址
    public static final String TOPIC_NAME = "topic01";//topic的name

    public static void main(String[] args) throws JMSException {
        //创建ActiveMQ的连接工厂 使用默认用户名和密码的方式
        ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        //获得工厂中的连接
        Connection connection = activeMQConnectionFactory.createConnection();
        connection.start();//开启连接
        //创建session会话
        Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);//是否开启事务，接收方式

        //使用session创建生产者 并指定destination
        Topic topic = session.createTopic(TOPIC_NAME);//创建消息类型
        MessageProducer messageProducer = session.createProducer(topic);

        //创建消息 并发送消息
        for (int i = 0; i < 3; i++) {
            TextMessage textMessage = session.createTextMessage("这里是第\t" + i + "\t条消息");//创建消息
            messageProducer.send(textMessage);//发送消息
        }
        System.out.println("message send success~~");

        //释放志愿
        messageProducer.close();
        session.close();
        connection.close();
    }
}
```

![image-20221126002114321](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126002114321.png)

![image-20221126002125412](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126002125412.png)

![image-20221126002050924](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126002050924.png)

### JMS

**Java massage server（Java消息服务）**

**两个应用程序之间进行异步通信的API**

**需要有实现JMS接口和规范的消息中间件（ActiveMQ）**

![image-20221126101828087](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126101828087.png)

### Message

#### **消息头**

![image-20221126103731867](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126103731867.png)

![image-20221126103822669](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126103822669.png)  

![image-20221126103845229](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126103845229.png)

#### **消息体**

**发送和接收消息类型必须一致**

![image-20221126182855963](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126182855963.png)

![image-20221126183215922](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126183215922.png)

#### **消息属性**

**对消息的标注，使消息更具有识别性**

![image-20221126183915244](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126183915244.png)

![image-20221126184010903](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126184010903.png)

![image-20221126184039585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126184039585.png)

### 消息可靠性

![image-20221126184650763](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126184650763.png)

#### persistent：持久性

![image-20221126184756864](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126184756864.png)

##### **队列的持久性**

![image-20221126185439225](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126185439225.png)



![image-20221126184839559](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126184839559.png)

**非持久化**模式消息会为空

**持久化模式**消息还在（只是消息进去队列的会清空）消息消费者还可以接收消息；

![image-20221126185114587](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126185114587.png)

##### Topic的持久性

1）：一定要先运行一次消费者，等于向MQ注册；类似订阅了这个topic

2）：然后再运行生产者发送消息

3）：无论消费者是否在线，都会接收到；不在线的话，下次连接在线时会接收到（把没收到的消息接收）

**topic的消费者**

![image-20221127000209553](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127000209553.png)

**topic的生产者**

![image-20221126232720937](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221126232720937.png)

#### 事务

偏生产者

ActiveMQProducer	

![image-20221127002034861](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127002034861.png)

ActiveMQConsumer

![image-20221127004754179](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127004754179.png)

#### acknowledge：签收

偏消费者

![image-20221127011205415](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127011205415.png)

![image-20221127005535186](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127005535186.png)

![image-20221127005636131](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127005636131.png)

![image-20221127005824821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127005824821.png)

**开了事务并且设置签收为手动签收的 可以省略手动签收**

**只要开启了事务 必须commit**

![image-20221127010808822](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127010808822.png)

ActiveMQ的Broker

相当于**内嵌式**的**ActiveMQ的实例** **嵌入Java代码中**以便**随时启用**（**随用随启 节约资源 保证可靠**）

### 嵌入式Broker

![image-20221127145223756](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127145223756.png)

```java
<!--嵌入式Broker需要依赖-->
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>2.13.3</version>
        </dependency>
```

```java
public class EmbedBroker {
    public static void main(String[] args) throws Exception{
        //ActiveMQ支持在VM中通信基于嵌入式的Broker
        BrokerService brokerService = new BrokerService();
        brokerService.setUseJmx(true);
        brokerService.addConnector("tcp://localhost:61616");
        brokerService.start();
    }
}
```

![image-20221127150146284](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127150146284.png)

![image-20221127150308644](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127150308644.png)

![image-20221127150748778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127150748778.png)

### **使用不同的conf配置文件启动不同的ActiveMQ实例**

![image-20221127142835504](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127142835504.png)

```
./activemq start xbean:file:/opt/apache-activemq-5.16.5/conf/activemq02.xml
```

![image-20221127143655754](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127143655754.png)

### Spring整合ActiveMQ

pom.xml引入相关依赖

```java
<!--spring整合activemq相关依赖active对jms的支持-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jms</artifactId>
            <version>4.3.23.RELEASE</version>
        </dependency>
        <!--activemq所需要的pool包配置-->
        <dependency>
            <groupId>org.apache.activemq</groupId>
            <artifactId>activemq-pool</artifactId>
            <version>5.15.9</version>
        </dependency>
        <!-- Spring5相关依赖 -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.2.6.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>5.2.6.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-beans</artifactId>
            <version>5.2.6.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.aspectj</groupId>
            <artifactId>aspectjweaver</artifactId>
            <version>1.8.7</version>
        </dependency>
```

spring的xml配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                          http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
    <!--开启组件扫描并指定要扫描的包-->
    <context:component-scan base-package="com.eddie.spring_activemq"></context:component-scan>
    <!--配置生产者-->
    <bean id="jmsFactory" class="org.apache.activemq.pool.PooledConnectionFactory">
        <property name="connectionFactory">
            <bean class="org.apache.activemq.ActiveMQConnectionFactory">
                <property name="brokerURL" value="tcp://192.168.199.138:61616"></property>
            </bean>
        </property>
        <property name="maxConnections" value="100"></property>
    </bean>

    <!--队列的目的地-->
    <bean id="destinationQueue" class="org.apache.activemq.command.ActiveMQQueue">
        <constructor-arg index="0" value="spring-active-queue"></constructor-arg>
    </bean>

    <!--spring提供的jms工具类 可以进行消息的发送和接收-->
    <bean id="jmsTemplate" class="org.springframework.jms.core.JmsTemplate">
        <property name="connectionFactory" ref="jmsFactory"></property>
        <property name="defaultDestination" ref="destinationQueue"></property>
        <property name="messageConverter">
            <bean class="org.springframework.jms.support.converter.SimpleMessageConverter"></bean>
        </property>
    </bean>
</beans>
```

![image-20221127163743157](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127163743157.png)

![image-20221127162925416](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127162925416.png)

SpringConsumer

```java
package com.eddie.spring_activemq;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.jms.core.JmsTemplate;
import org.springframework.stereotype.Service;

import javax.jms.JMSException;

/**
 @author EddieZhang
 @create 2022-11-27 16:06
 */
@Service
public class SpringConsumer {
    @Autowired
    private JmsTemplate jmsTemplate;

    public static void main(String[] args) throws JMSException {
        ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
        SpringConsumer springConsumer = context.getBean("springConsumer", SpringConsumer.class);
        String message = (String) springConsumer.jmsTemplate.receiveAndConvert();
        System.out.println("here is receive \t" + message);
    }
}
```

SpringProducer

```java
package com.eddie.spring_activemq;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.jms.core.JmsTemplate;
import org.springframework.stereotype.Service;

/**
 @author EddieZhang
 @create 2022-11-27 15:55
 */
@Service
public class SpringProducer {
    @Autowired
    private JmsTemplate jmsTemplate;

    public static void main(String[] args) {
        ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
        SpringProducer springProducer = context.getBean("springProducer", SpringProducer.class);
        springProducer.jmsTemplate.send(session -> session.createTextMessage("spring整合ActiveMQ的case"));
//        springProducer.jmsTemplate.send(new MessageCreator() {
//            @Override
//            public Message createMessage(Session session) throws JMSException {
//                return session.createTextMessage("spring整合ActiveMQ的case");
//            }
//        });
        System.out.println("send message success~~");
    }
}
```

Spring配置监听器

MessageListener的实现类

```java
package com.eddie.spring_activemq;

import org.springframework.stereotype.Component;

import javax.jms.JMSException;
import javax.jms.Message;
import javax.jms.MessageListener;
import javax.jms.TextMessage;

/**
 @author EddieZhang
 @create 2022-11-27 16:44
 */
@Component
public class MyMessageListener implements MessageListener {
    @Override
    public void onMessage(Message message) {
        if(null != message && message instanceof TextMessage){
            TextMessage textMessage = (TextMessage) message;
            try {
                System.out.println("监听器接收消息\t" + textMessage.getText());
            } catch (JMSException e) {
                e.printStackTrace();
            }
        }
    }
}
```

spring的xml配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
                          http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd">
    <!--开启组件扫描并指定要扫描的包-->
    <context:component-scan base-package="com.eddie.spring_activemq"></context:component-scan>
    <!--配置生产者-->
    <bean id="jmsFactory" class="org.apache.activemq.pool.PooledConnectionFactory">
        <property name="connectionFactory">
            <bean class="org.apache.activemq.ActiveMQConnectionFactory">
                <property name="brokerURL" value="tcp://192.168.199.138:61616"></property>
            </bean>
        </property>
        <property name="maxConnections" value="100"></property>
    </bean>

    <!--队列的目的地-->
    <bean id="destinationQueue" class="org.apache.activemq.command.ActiveMQQueue">
        <constructor-arg index="0" value="spring-active-queue"></constructor-arg>
    </bean>
    <!--Topic的目的地-->
    <bean id="activeMQTopic" class="org.apache.activemq.command.ActiveMQTopic">
        <constructor-arg index="0" value="spring-active-topic"></constructor-arg>
    </bean>
	<!--MessageListener监听器配置-->
    <bean id="listenerContainer" class="org.springframework.jms.listener.DefaultMessageListenerContainer">
        <property name="connectionFactory" ref="jmsFactory"></property>
        <property name="destination" ref="activeMQTopic"></property>

        <property name="messageListener" ref="myMessageListener"></property>
    </bean>
    <!--<bean id="myMessageListener" class="com.eddie.spring_activemq.MyMessageListener"></bean>-->

    <!--spring提供的jms工具类 可以进行消息的发送和接收-->
    <bean id="jmsTemplate" class="org.springframework.jms.core.JmsTemplate">
        <property name="connectionFactory" ref="jmsFactory"></property>
        <property name="defaultDestination" ref="activeMQTopic"></property><!--指明destination-->
        <property name="messageConverter">
            <bean class="org.springframework.jms.support.converter.SimpleMessageConverter"></bean>
        </property>
    </bean>
</beans>
```

只启动Producer即可 不同提前启动消费者 （监听器一直在监听）

![image-20221127165204909](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221127165204909.png)

SpringBoot整合ActiveMQ

### 队列

```java
        <!--activemq依赖-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-activemq</artifactId>
            <version>2.1.5.RELEASE</version>
        </dependency>
    </dependencies>
```

#### Producer

**手动触发启动**
**定时投递**--@Scheduled

![image-20221128005037552](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128005037552.png)

```yaml
server:
  port: 8081

spring:
  activemq:
    broker-url: tcp://192.168.199.138:61616 #activemq服务器地址
    user: admin
    password: admin
  jms:
    pub-sub-domain: false #false相当于queue true相当于topic 默认false（queue）

myqueue: boot-activemq-queue01 #自定义queue的name
```

```java
package com.eddie.config;
import org.apache.activemq.command.ActiveMQQueue;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jms.annotation.EnableJms;
import javax.jms.Queue;

/**
 @author EddieZhang
 @create 2022-11-27 23:56
 */
@Configuration
@EnableJms
public class ConfigBean {
    @Value("${myqueue}")
    private String  myQueue;

    @Bean
    public Queue queue(){
        return new ActiveMQQueue(myQueue);
    }
}
```

```java
package com.eddie.produce;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jms.core.JmsMessagingTemplate;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Component;
import javax.jms.Queue;
import java.util.UUID;

/**
 @author EddieZhang
 @create 2022-11-28 0:00
 */
@Component
public class QueueProduce {
    @Autowired
    private JmsMessagingTemplate jmsMessagingTemplate;

    @Autowired
    private Queue queue;

    public void produceMessage(){
        jmsMessagingTemplate.convertAndSend(queue,"-----\t" + UUID.randomUUID().toString().substring(0,6));
        System.out.println("send message success~~");
    }

    /**
     * 定时投递消息
     */
    @Scheduled(fixedDelay = 3000L)
    public void produceMessageScheduled(){
        jmsMessagingTemplate.convertAndSend(queue,"-----\t" + UUID.randomUUID().toString().substring(0,6));
        System.out.println("send message success~~");
    }
}
```

```java
package com.eddie;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.scheduling.annotation.EnableScheduling;

@SpringBootApplication
@EnableScheduling
public class SpringBootActiveMqApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootActiveMqApplication.class, args);
    }

}
```

![image-20221128005954563](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128005954563.png)

#### Consumer

![image-20221128005850627](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128005850627.png)

```yaml
server:
  port: 8082

spring:
  activemq:
    broker-url: tcp://192.168.199.138:61616 #activemq服务器地址
    user: admin
    password: admin
  jms:
    pub-sub-domain: false #false相当于queue true相当于topic 默认false（queue）

myqueue: boot-activemq-queue01 #自定义queue的name
```

```java
package com.eddie.config;
import org.apache.activemq.command.ActiveMQQueue;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jms.annotation.EnableJms;
import javax.jms.Queue;

/**
 @author EddieZhang
 @create 2022-11-27 23:56
 */
@Configuration
@EnableJms
public class ConfigBean {
    @Value("${myqueue}")
    private String  myQueue;

    @Bean
    public Queue queue(){
        return new ActiveMQQueue(myQueue);
    }
}
```

```java
package com.eddie.consumer;
import org.springframework.jms.annotation.JmsListener;
import org.springframework.stereotype.Component;
import javax.jms.JMSException;
import javax.jms.TextMessage;

/**
 @author EddieZhang
 @create 2022-11-28 0:56
 */
@Component
public class Consumer {

    @JmsListener(destination = "${myqueue}")
    public void receive(TextMessage textMessage) throws JMSException {
        System.out.println("receive message\t" + textMessage.getText());
    }
}
```

```java
@SpringBootApplication
public class SpringBootActiveMqApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootActiveMqApplication.class, args);
    }

}
```

![image-20221128010008791](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128010008791.png)

### Topic

```java
        <!--activemq依赖-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-activemq</artifactId>
            <version>2.1.5.RELEASE</version>
        </dependency>
    </dependencies>
```

#### Producer

![image-20221128011713267](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128011713267.png)

```yaml
server:
  port: 8083

spring:
  activemq:
    broker-url: tcp://192.168.199.138:61616 #activemq服务器地址
    user: admin
    password: admin
  jms:
    pub-sub-domain: true #false相当于queue true相当于topic 默认false（queue）

myqueue: boot-activemq-queue01 #自定义queue的name
mytopic: boot-activemq-topic01 #自定义topic的name
```

```java
package com.eddie.config;

import org.apache.activemq.command.ActiveMQTopic;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jms.annotation.EnableJms;
import javax.jms.Topic;

/**
 @author EddieZhang
 @create 2022-11-27 23:56
 */
@Configuration
@EnableJms
public class ConfigBean {
    @Value("${mytopic}")
    private String  myTopic;

    @Bean
    public Topic topic(){
        return new ActiveMQTopic(myTopic);
    }
}
```

```java
package com.eddie.produce;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jms.core.JmsMessagingTemplate;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Component;
import javax.jms.Topic;
import java.util.UUID;

/**
 @author EddieZhang
 @create 2022-11-28 1:07
 */
@Component
public class TopicProducer {
    @Autowired
    private JmsMessagingTemplate jmsMessagingTemplate;
    @Autowired
    private Topic topic;

    @Scheduled(fixedDelay = 3000L)
    public void produceMessageTopicScheduled(){
        jmsMessagingTemplate.convertAndSend(topic,"---\t" + UUID.randomUUID().toString().substring(0,6));
        System.out.println("send message success~~");
    }
}
```

```java
package com.eddie;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.scheduling.annotation.EnableScheduling;

@SpringBootApplication
@EnableScheduling
public class SpringBootActiveMqApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootActiveMqApplication.class, args);
    }

}
```

![image-20221128011818476](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128011818476.png)

#### Consumer

![image-20221128014340127](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128014340127.png)

```yaml
server:
  port: 8083

spring:
  activemq:
    broker-url: tcp://192.168.199.138:61616 #activemq服务器地址
    user: admin
    password: admin
  jms:
    pub-sub-domain: true #false相当于queue true相当于topic 默认false（queue）

myqueue: boot-activemq-queue01 #自定义queue的name
mytopic: boot-activemq-topic01 #自定义topic的name
```

```java
package com.eddie.consumer;
import org.springframework.jms.annotation.JmsListener;
import org.springframework.stereotype.Component;
import javax.jms.JMSException;
import javax.jms.TextMessage;

/**
 @author EddieZhang
 @create 2022-11-28 1:37
 */
@Component
public class TopicConsumer {

    @JmsListener(destination = "${mytopic}")
    public void receiveTopicMessage(TextMessage textMessage) throws JMSException {
        System.out.println("receive Topic message\t" + textMessage.getText());
    }
}
```

```java
package com.eddie;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.scheduling.annotation.EnableScheduling;

@SpringBootApplication
@EnableScheduling
public class SpringBootActiveMqApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootActiveMqApplication.class, args);
    }

}
```

![image-20221128014519672](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128014519672.png)

ActiveMQ的传输协议

[ActiveMQ (apache.org)](https://activemq.apache.org/configuring-version-5-transports.html)

![image-20221128092954556](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128092954556.png)

**默认使用TCP Transport**

**BIO**网络传输模型

![image-20221128100109248](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128100109248.png)

![image-20221128100054012](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128100054012.png)

### NIO Transport

**Better Performance**

**以TCP协议为基础**的**NIO网络IO模型**

**配置NIO**

![image-20221128100109248](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128100109248.png)

![image-20221128100721331](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128100721331.png)

![image-20221128101758589](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128101758589.png)

![image-20221128100914656](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128100914656.png)

![image-20221128101824442](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128101824442.png)

### AUTO over NIO★

![image-20221128105558942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105558942.png)

**统一了Port**

![image-20221128102531564](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128102531564.png)

```xml
<transportConnector name="auto+nio" uri="auto+nio://0.0.0.0:61608?maximumConnections=1000&amp;wireFormat.maxFrameSize=104857600&amp;org.apache.activemq.transport.nio.SelectorMannager.corePoolSize=20&amp;org.apache.activemq.transport.nio.SelectorManager.maximumPoolSize=50"/>
```

![image-20221128105010142](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105010142.png)

![image-20221128105305947](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105305947.png)

![image-20221128105249030](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105249030.png)

![image-20221128105351017](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105351017.png)

![image-20221128105446511](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128105446511.png)

### ActiveMQ可持久化

**避免AMQ挂掉后**，重启可以**恢复所有的消息队列**；消息系统会**采用持久化机制**

将消息发出后，**消息中心首先将消息存储到本地数据文件**，内存数据库，或者远程数据库...；

**再将消息发送给接收者**

**成功**发送给接收者则**将储存的数据删除**

**失败**则尝试**继续发送**

**消息中心启动后首先**要**检测**指定的**储存位置**；如果**有未发送成功的消息**，则需要**将消息发送出去**

![image-20221129003320854](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129003320854.png)

![image-20221128122936173](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128122936173.png)

[ActiveMQ (apache.org)](https://activemq.apache.org/persistence)

![image-20221128113134553](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128113134553.png)

### KahaDB（default）

[ActiveMQ (apache.org)](https://activemq.apache.org/kahadb)

![image-20221128121259420](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128121259420.png)

![image-20221128121222189](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128121222189.png)

![image-20221128121438941](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128121438941.png)

![image-20221128122146161](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128122146161.png)

![image-20221128122159522](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128122159522.png)

![image-20221128122218946](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128122218946.png)

![image-20221128122308677](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128122308677.png)

### JDBC

![image-20221128142817501](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128142817501.png)

![image-20221128154450092](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128154450092.png)

![image-20221128213354371](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128213354371.png)

![image-20221128161211516](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128161211516.png)

```xml
<bean id="mysql-ds" class="com.alibaba.druid.pool.DruidDataSource" destroy-method="close">
      <property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
      <property name="url" value="jdbc:mysql://192.168.1.8:3306/activemq?rewriteBatchedStatements=TRUE"/>
      <property name="username" value="root"/>
      <property name="password" value="root"/>
      <property name="poolPreparedStatements" value="true"/>
</bean>
```

![image-20221128213254591](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128213254591.png)

#### Queue

![image-20221128223129469](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128223129469.png)

![image-20221128223036666](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128223036666.png)

#### Topic

![image-20221128224715014](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128224715014.png)

```java
package com.eddie.config;
import org.apache.activemq.command.ActiveMQTopic;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jms.annotation.EnableJms;
import org.springframework.jms.config.DefaultJmsListenerContainerFactory;
import org.springframework.jms.config.JmsListenerContainerFactory;
import org.springframework.jms.connection.SingleConnectionFactory;
import org.springframework.jms.listener.DefaultMessageListenerContainer;
import javax.jms.ConnectionFactory;
import javax.jms.Topic;

/**
 @author EddieZhang
 @create 2022-11-27 23:56
 */
@Configuration
@EnableJms
public class ConfigBean {
    @Value("${mytopic}")
    private String  topic;

    @Bean
    public Topic topic(){
        return new ActiveMQTopic(topic);
    }

    @Bean(name = "topicListenerFactory")
    public JmsListenerContainerFactory<DefaultMessageListenerContainer> topicListenerFactory(SingleConnectionFactory connectionFactory){
        DefaultJmsListenerContainerFactory factory = new DefaultJmsListenerContainerFactory();

        factory.setSubscriptionDurable(true);// Set this to "true" to register a durable subscription,

        factory.setPubSubDomain(true);

        connectionFactory.setClientId("Topic_Durable01");

        factory.setConnectionFactory(connectionFactory);
        return factory;

    }

}
```

```java
package com.eddie.consumer;
import org.springframework.jms.annotation.JmsListener;
import org.springframework.stereotype.Component;
import javax.jms.JMSException;
import javax.jms.TextMessage;

/**
 @author EddieZhang
 @create 2022-11-28 1:37
 */
@Component
public class TopicConsumer {

    @JmsListener(destination = "${mytopic}",containerFactory = "topicListenerFactory")
    public void receiveTopicMessage(TextMessage textMessage) throws JMSException {
        System.out.println("receive Topic message\t" + textMessage.getText());
    }
}
```

```java
package com.eddie.produce;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jms.core.JmsMessagingTemplate;
import org.springframework.scheduling.annotation.Scheduled;
import org.springframework.stereotype.Component;
import javax.jms.Topic;
import java.util.UUID;

/**
 @author EddieZhang
 @create 2022-11-28 1:07
 */
@Component
public class TopicProducer {
    @Autowired
    private JmsMessagingTemplate jmsMessagingTemplate;
    @Autowired
    private Topic topic;

    @Scheduled(fixedDelay = 3000L)
    public void produceMessageTopicScheduled(){
        jmsMessagingTemplate.convertAndSend(topic,"---\t" + UUID.randomUUID().toString().substring(0,6));
        System.out.println("send message success~~");
    }
}
```

![image-20221128235727367](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128235727367.png)

![image-20221128235812579](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221128235812579.png)

### JDBC With Journal

相当于在ActiveMQ和MySQL中多增加了一层即Journal高速缓存日志

先写进Journal高速缓存日志中 若长时间未被消费 则写进MySQL数据库中 缓解数据库的压力 

![image-20221129000544050](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129000544050.png)

```xml
<persistenceFactory>
	<journalPersistenceAdapterFactory
	journalLogFiles="4"
	journalLogFileSize="32768"
	useJournal="true"
	useQuickJournal="true"
	dataSource="#mysql-ds"
	dataDirectory="activemq-data"/>
</persistenceFactory>
```

![image-20221129000034974](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129000034974.png)

### ActiveMQ多节点集群

ActiveMQ支持Sync和Async两种消息发送模式发送消息到Broker

**默认使用Async**

**Sync**：**没有使用事务并且发送的是持久化消息**，每一次发送都是同步发送的且会**阻塞producer直到broker返回一个确认**；表示已经将消息持久化到磁盘，确认机制确保了消息安全；但是会阻塞客户端从而带来巨大的延迟



**Async**：producer的发送**效率很高**；

​			  可能带来少量的数据丢失；当发送的消息很多时会造成broker性能的损耗增加；**无法确保消息发送成功**

![image-20221129004827374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129004827374.png)

![image-20221129004836580](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129004836580.png)

### 高级特性

[ActiveMQ (apache.org)](https://activemq.apache.org/features)

#### 异步投递

![image-20221129012043921](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129012043921.png)

![image-20221129010400654](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129010400654.png)

![image-20221129013140456](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129013140456.png)

![image-20221129010920697](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129010920697.png)

#### 异步投递回调确认消息发送情况

![image-20221129013659348](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129013659348.png)

![image-20221129013453836](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129013453836.png)

#### 延时投递&定时投递

[ActiveMQ (apache.org)](https://activemq.apache.org/delay-and-schedule-message-delivery.html)

It is enabled by setting the broker **schedulerSupport** attribute to true in the [Xml Configuration](https://activemq.apache.org/xml-configuration). An ActiveMQ client can take advantage of a delayed delivery by using the following message properties:

![image-20221129014712224](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129014712224.png)

```xml
<broker xmlns="http://activemq.apache.org/schema/core" brokerName="localhost" dataDirectory="${activemq.data}" schedulerSupport="true">
```

![image-20221129015309938](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129015309938.png)

![image-20221129015809007](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129015809007.png)

| Property name        | type   | description                                                  |
| -------------------- | ------ | ------------------------------------------------------------ |
| AMQ_SCHEDULED_DELAY  | long   | The time in milliseconds that a message will wait before being scheduled to be delivered by the broker：**延迟投递时间** |
| AMQ_SCHEDULED_PERIOD | long   | The time in milliseconds to wait after the start time to wait before scheduling the message again：**重复投递的时间间隔** |
| AMQ_SCHEDULED_REPEAT | int    | The number of times to repeat scheduling a message for delivery：**重复投递的次数** |
| AMQ_SCHEDULED_CRON   | String | Use a Cron entry to set the schedule：**Cron表达式**         |

#### 分发策略

项目中多线程涉及到

#### 重试机制

[ActiveMQ (apache.org)](https://activemq.apache.org/redelivery-policy)

![image-20221129020513931](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129020513931.png)

#### 重发的三种情况&有毒消息

![image-20221129020143551](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129020143551.png)

![image-20221129020155161](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129020155161.png)

![image-20221129020215019](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129020215019.png)

![image-20221129021004073](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129021004073.png)

| Property                   | Default Value | Description                                                  |
| -------------------------- | ------------- | ------------------------------------------------------------ |
| `backOffMultiplier`        | `5`           | The back-off multiplier.                                     |
| `collisionAvoidanceFactor` | `0.15`        | The percentage of range of collision avoidance if enabled.   |
| `initialRedeliveryDelay`   | `1000L`       | The initial redelivery delay in milliseconds.                |
| `maximumRedeliveries`      | `6`           | Sets the maximum number of times a message will be redelivered before it is considered a **poisoned pill** and returned to the broker so it can go to a Dead Letter Queue. Set to `-1` for unlimited redeliveries. |
| `maximumRedeliveryDelay`   | `-1`          | Sets the maximum delivery delay that will be applied if the `useExponentialBackOff` option is set. (use value `-1` to define that no maximum be applied) (v5.5). |
| `redeliveryDelay`          | `1000L`       | The delivery delay if `initialRedeliveryDelay=0` (v5.4).     |
| `useCollisionAvoidance`    | `false`       | Should the redelivery policy use collision avoidance.        |
| `useExponentialBackOff`    | `false`       | Should exponential back-off be used, i.e., to exponentially increase the timeout. |

![image-20221129020533495](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129020533495.png)

#### 消费者手动设置重发策略

![image-20221129021517755](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129021517755.png)

```java
//创建ActiveConnectionFactory 按照默认的用户名和密码进行连接
ActiveMQConnectionFactory activeMQConnectionFactory = new ActiveMQConnectionFactory(ACTIVEMQ_URL);
        RedeliveryPolicy redeliveryPolicy = new RedeliveryPolicy();//Consumer手动设置重发策略
        redeliveryPolicy.setMaximumRedeliveries(3);//指定最大重复发送次数为3
        activeMQConnectionFactory.setRedeliveryPolicy(redeliveryPolicy);
```

#### Spring中配置重发机制

![image-20221129023255121](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129023255121.png)

![image-20221129022627557](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129022627557.png)

```java
@Bean
public RedeliveryPolicy redeliveryPolicy(){
    RedeliveryPolicy redeliveryPolicy = new RedeliveryPolicy();
    redeliveryPolicy.setUseExponentialBackOff(true);//是否在每次尝试重新发送失败后增加等待时间
    redeliveryPolicy.setMaximumRedeliveries(3);//重复发送次数
    redeliveryPolicy.setInitialRedeliveryDelay(1000L);//重复发送间隔
    redeliveryPolicy.setBackOffMultiplier(2);//第一次失败后重新发送前等待500毫秒 第二次失败再等待500 * 2毫秒
    redeliveryPolicy.setMaximumRedeliveryDelay(1000L);//最大传送延时；setUseExponentialBackOff(true)时有效
    //首次重连间隔为10毫秒 倍数为2 那么第二次为20毫秒 第三次为40毫秒 直到达到设置的最大重连间隔时间 后续的每次都为设置的最大重连间隔时间
    return redeliveryPolicy;
}
```

#### 死信队列

![image-20221129130944828](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129130944828.png)

![image-20221129131021344](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131021344.png)

![image-20221129131102260](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131102260.png)

![image-20221129131416823](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131416823.png)

![image-20221129131613821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131613821.png)

![image-20221129131626223](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131626223.png)

#### 防止重复调用

方式一：使用数据库对消息做插入操作 并给消息指定唯一ID 从而避免重复

**推荐方式：使用redis缓存；给消息分配一个全局ID 消费过的消息以<id,message>的k-v的形式写入redis中；**

**消费前去redis中查询是否消费过即可**

![image-20221129131827947](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129131827947.png)

## RabbitMQ

![image-20230109155719111](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109155719111.png)

[Messaging that just works — RabbitMQ](https://www.rabbitmq.com/)

https://www.rabbitmq.com/admin-guide.html

https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html#this-blog-series-is-a-living-document-that-is-continually-updated-last-updated-january-2022

web--port   :   15672

port   :   5672

###  工作原理核心概念

![image-20230109183131916](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109183131916.png)

![image-20230109184409076](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109184409076.png)

![image-20221203103808965](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203103808965.png)

**概念介绍**

**Broker**：简单来说就是消息队列服务器实体。

**Exchange**：消息交换机，它指定消息按什么规则，路由到哪个队列。message 到达 broker 的第一站，根据分发规则，匹配查询表中的 routing key，分发 消息到 queue 中去。常用的类型有：direct (point-to-point), topic (publish-subscribe) and fanout  (multicast)

**Queue**：消息队列载体，每个消息都会被投入到一个或多个队列。

**Binding**：绑定，它的作用就是把exchange和queue按照路由规则绑定起来。exchange 和 queue 之间的虚拟连接，binding 中可以包含 routing key，Binding 信息被保 存到 exchange 中的查询表中，用于 message 的分发依据

**Routing Key**：路由关键字，exchange根据这个关键字进行消息投递。

**Virtual host**：虚拟主机，**一个broker里可以开设多个vhost，用作不同用户的权限分离**。出于多租户和安全因素设计的，把 AMQP 的基本组件划分到一个虚拟的分组中，类似 于网络中的 namespace 概念。当多个不同的用户使用同一个 RabbitMQ server 提供的服务时，可以划分出 多个 vhost，每个用户在自己的 vhost 创建 exchange／queue 等

**producer**：消息生产者，就是投递消息的程序。

**consumer**：消息消费者，就是接受消息的程序。

**channel**：消息通道，在客户端的每个连接里，可建立多个channel，每个channel代表一个会话任务。如果每一次访问 RabbitMQ 都建立一个 Connection，在消息量大的时候建立 TCP  Connection 的开销将是巨大的，效率也较低。Channel 是在 connection 内部建立的逻辑连接，如果应用程 序支持多线程，通常每个 thread 创建单独的 channel 进行通讯，AMQP method 包含了 channel id 帮助客 户端和 message broker 识别 channel，所以 channel 之间是完全隔离的。**Channel 作为轻量级的 Connection 极大减少了操作系统建立 TCP connection 的开销**

### Exchange Types(交换器类型)

![image-20230227105849825](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230227105849825.png)

> - **Direct:** The message is routed to the queues whose binding key exactly matches the routing key of the message. For example, if the queue is bound to the exchange with the binding key *pdfprocess, a message published to* the exchange with a routing key *pdfprocess is routed to that queue.*
> - **Fanout:** A fanout exchange routes messages to all of the queues bound to it.
> - **Topic:** The topic exchange does a wildcard match between the routing key and the routing pattern specified in the binding.
> - **Headers:** Headers exchanges use the message header attributes for routing.

#### Direct

direct 类型的Exchange路由规则也很简单，它会把消息**路由到**那些 **Bindingkey 与 RoutingKey 完全匹配**的 Queue 中。

direct 类型常用在处理有优先级的任务，根据任务的优先级把消息发送到对应的队列，这样可以指派更多的资源去处理高优先级的队列.

![image-20230109182329982](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109182329982.png)

#### Topic

direct类型的交换器路由规则是完全匹配 BindingKey 和 RoutingKey ，但是这种严格的匹配方式在很多情况下不能满足实际业务的需求。topic类型的交换器在匹配规则上进行了扩展，它与 direct 类型的交换器相似，也是将消息路由到 BindingKey 和 RoutingKey 相匹配的队列中，但这里的匹配规则有些不同，它约定：

- RoutingKey 为一个点号“．”分隔的字符串（被点号“．”分隔开的每一段独立的字符串称为一个单词），如 “com.rabbitmq.client”、“java.util.concurrent”、“com.hidden.client”;
- BindingKey 和 RoutingKey 一样也是点号“．”分隔的字符串；
- BindingKey 中可以存在两种特殊字符串"\*"和“#”，用于做模糊匹配，其中"\*"用于匹配一个单词，“#”用于匹配多个单词(可以是零个)。

![image-20230109182608582](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109182608582.png)

#### Fanout

fanout 类型的Exchange路由规则非常简单，它会**把所有发送到该Exchange的消息路由到所有与它绑定的Queue中**，不需要做任何判断操作，所以 fanout 类型是所有的交换机类型里面速度最快的。fanout 类型常用来**广播消息**。

![image-20230109182917141](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109182917141.png)

#### Headers(不推荐)

headers 类型的交换器不依赖于路由键的匹配规则来路由消息，而是根据发送的消息内容中的 headers 属性进行匹配。在绑定队列和交换器时指定一组键值对，当发送消息到交换器时，RabbitMQ会获取到该消息的 headers（也是一个键值对的形式)，对比其中的键值对是否完全匹配队列和交换器绑定时指定的键值对，如果完全匹配则消息会路由到该队列，否则不会路由到该队列。headers 类型的交换器性能会很差，而且也不实用，基本上不会看到它的存在。

### 四大核心

![image-20221203104014375](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203104014375.png)

### 六大模式

![image-20221203104221284](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203104221284.png)

### Linux上安装

- 由于RabbitMQ是基于Erlang语言开发, 所以在安装RabbitMQ之前, 需要先安装Erlang
- rabbitmq需要socat依赖, 所以需要先安装socat

**安装erlang**--erlang语言支持

[el/7/erlang-23.2.7-2.el7.x86_64.rpm - rabbitmq/erlang · packagecloud](https://packagecloud.io/rabbitmq/erlang/packages/el/7/erlang-23.2.7-2.el7.x86_64.rpm)

其中的`el7`表示Red Hat 7.x，即`CentOS 7.x`

**下载RabbitMQ**

[Release RabbitMQ 3.8.14 · rabbitmq/rabbitmq-server · GitHub](https://github.com/rabbitmq/rabbitmq-server/releases/tag/v3.8.14)

**安装到usr/local/src/rabbitmq**

![image-20221203122048352](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203122048352.png)

**分别进行安装**

在`RabiitMQ`安装过程中需要依赖`socat`插件，首先安装该插件

```
# 解压
rpm -Uvh erlang-23.2.7-2.el7.x86_64.rpm
# 安装
yum install -y erlang
# 查看版本
erl -v

#安装 socat 插件
yum install socat -y

# 解压
rpm -Uvh rabbitmq-server-3.8.14-1.el7.noarch.rpm
# 安装
yum install -y rabbitmq-server
```

**常用命令**

**添加开机自启**

```
chkconfig rabbitmq-server on
```

**启动rabbitmq**

**查看服务状态**

```
# 启动rabbitmq
systemctl start rabbitmq-server

# 查看rabbitmq状态
systemctl status rabbitmq-server
```

**启动失败解决**

```
[root@192 rabbitmq]# vi  /etc/selinux/config
SELINUX=disabled
[root@192 rabbitmq]# vi /etc/rabbitmq/rabbitmq-env.conf
NODENAME=rabbit@localhost
```

**停止服务**

```
systemctl stop rabbitmq-server
```

**RabbitMQWeb管理界面及授权操作**

**开启 web 管理插件**

```
rabbitmq-plugins enable rabbitmq_management
```

**防护墙端口访问权限打开**

```
开放指定端口
firewall-cmd --zone=public --add-port=1935/tcp --permanent
命令含义：
–zone #作用域
–add-port=1935/tcp#添加端口，格式为：端口/通讯协议
–permanent#永久生效，没有此参数重启后失效

重启防火墙
firewall-cmd --reload

查看所有开放的端口
firewall-cmd --zone=public --list-ports
```

![image-20221203163751408](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203163751408.png)

`rabbitmq`有一个**默认的账号密码`guest`**，但该情况**仅限于本机localhost进行访问**，所以**需要添加一个远程登录的用户**

**添加远程用户**

```
# 添加用户
rabbitmqctl add_user 用户名 密码

# 设置用户角色,分配操作权限
rabbitmqctl set_user_tags 用户名 角色

# 为用户添加资源权限(授予访问虚拟机根节点的所有权限)
rabbitmqctl set_permissions -p / 用户名 ".*" ".*" ".*"
set_permissions [-p <vhostpath>] <user> <conf> <write> <read>

```

**角色有四种**：

- `administrator`：可以登录控制台、查看所有信息、并对rabbitmq进行管理
- `monToring`：监控者；登录控制台，查看所有信息
- `policymaker`：策略制定者；登录控制台指定策略
- `managment`：普通管理员；登录控制

![image-20221203164301501](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203164301501.png)

其他指令：

```
# 修改密码
rabbitmqctl change_ password 用户名 新密码

# 删除用户
rabbitmqctl delete_user 用户名

# 查看用户清单
rabbitmqctl list_users

# 关闭应用的命令为
rabbitmqctl stop_app

# 清除的命令为
rabbitmqctl reset

# 重新启动命令为
rabbitmqctl start_app
```

![image-20221203164442605](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203164442605.png)

### Docker安装

```bash
docker run -d --name rabbitmq -p 5761:5761 -p 5672:5672 -p 4369:4369 -p 25672:25672 -p 15671:15671 -p 15672:15672 rabbitmq:management
```

![image-20230109165306749](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109165306749.png)

![image-20230109165320985](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109165320985.png)

![image-20230109165552116](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109165552116.png)

> 默认账号密码
>
> guest

**配置随着docker自动restart**

```bash
docker update rabbitmq --restart=always
```

![image-20230226211717905](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230226211717905.png)

### Spring Boot 整合 RabbitMQ

#### Prepare And Config

![image-20230109222656726](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109222656726.png)

![image-20230109224303187](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109224303187.png)

pom.xml

```xml
		<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-amqp</artifactId>
        </dependency>
```

application.yml

```yaml
server:
  port: 8081
spring:
  rabbitmq:
    host: 192.168.199.180
    port: 5672
    virtual-host: /
    username: guest
    password: guest
```

启动类

![image-20230109221801922](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230109221801922.png)

RabbitMQConfig

```java
package com.eddie.config;

import org.springframework.amqp.support.converter.Jackson2JsonMessageConverter;
import org.springframework.amqp.support.converter.MessageConverter;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

/**
 @author EddieZhang
 @create 2023-01-09 21:14
 */
@Configuration
public class RabbitMQConfig {
    @Bean
    public MessageConverter messageConverter(){
        MessageConverter messageConverter = new Jackson2JsonMessageConverter();
        return messageConverter;
    }
}

```

#### Producer Send Message

> **创建和声明Exchange&Queue并创建和声明Binding**
>
> ```java
> public void declareExchangeQueueBinding() {
>         //创建exchange
>         Exchange directExchange = new DirectExchange("eddie-exchange-direct", true, false);
>         //String name, boolean durable, boolean autoDelete, Map<String, Object> arguments
> 
>         //声明exchange
>         amqpAdmin.declareExchange(directExchange);
> 
>         //创建Queue
>         Queue queue = new Queue("eddie-queue-1", true, false, false);
>         //String name, boolean durable, boolean exclusive, boolean autoDelete, @Nullable Map<String, Object> arguments
> 
>         //声明Queue
>         amqpAdmin.declareQueue(queue);
> 
>         //创建Binding
>         Binding binding = new Binding("eddie-queue-1", Binding.DestinationType.QUEUE, "eddie-exchange-direct", "eddie-queue-1", null);
>         //String destination, Binding.DestinationType destinationType, String exchange, String routingKey, @Nullable Map<String, Object> arguments)
> 
>         //声明Binding
>         amqpAdmin.declareBinding(binding);
>     }
> ```
>
> **Send Message**
>
> ```java
> @Override
> public void convertAndSend(
>     String exchange, //指明交换机
>     String routingKey, //指明路由键
>     final Object object,//消息实体数据
>       @Nullable CorrelationData correlationData//关联数据用于给消息指定唯一的id 消费者和生产者端的通用数据
> ) throws AmqpException {
>    send(exchange, routingKey, convertMessageIfNecessary(object), correlationData);
> }
> ```

```java
package com.eddie.controller;

import com.eddie.entity.Person;
import com.eddie.entity.User;
import org.springframework.amqp.core.*;
import org.springframework.amqp.rabbit.core.RabbitTemplate;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

/**
 @author EddieZhang
 @create 2023-01-09 20:16
 */
@RestController
@RequestMapping("/messageProducer")
public class MessageProducerController {
    @Autowired
    private AmqpAdmin amqpAdmin;
    @Autowired
    private RabbitTemplate rabbitTemplate;

    @RequestMapping("/declareExchangeQueueBinding")
    public void declareExchangeQueueBinding() {
        //创建exchange
        Exchange directExchange = new DirectExchange("eddie-exchange-direct", true, false);
        //String name, boolean durable, boolean autoDelete, Map<String, Object> arguments

        //声明exchange
        amqpAdmin.declareExchange(directExchange);

        //创建Queue
        Queue queue = new Queue("eddie-queue-1", true, false, false);
        //String name, boolean durable, boolean exclusive, boolean autoDelete, @Nullable Map<String, Object> arguments

        //声明Queue
        amqpAdmin.declareQueue(queue);

        //创建Binding
        Binding binding = new Binding("eddie-queue-1", Binding.DestinationType.QUEUE, "eddie-exchange-direct", "eddie-queue-1", null);
        //String destination, Binding.DestinationType destinationType, String exchange, String routingKey, @Nullable Map<String, Object> arguments)

        //声明Binding
        amqpAdmin.declareBinding(binding);
    }

    /**
     * 发送消息
     */
    @RequestMapping("/sendMessage")
    public void sendMessage() {
        for (int i = 0; i < 10; i++) {
            if (i % 2 == 0) {
                rabbitTemplate.convertAndSend(
                        "eddie-exchange-direct",
                        "eddie-queue-1",
                        new User("Eddie_" + i,
                                "male",
                                "Java-Backend-Development",
                                21),
                        new CorrelationData(UUID.randomUUID().toString()));
            }else {
                rabbitTemplate.convertAndSend(
                        "eddie-exchange-direct",
                        "eddie-queue-1",
                        new Person("EddieZhang_" + i,
                                "male",
                                "Java-Backend-Development",
                                21),
                        new CorrelationData(UUID.randomUUID().toString()));
            }
        }
}

```

#### Consumer Receive Message

> 默认是auto自动签收（不论消息是否成功消费完成都会签收）【不建议】
>
> 将签收设置为manual手动模式（确保消息成功消费后手动ack确保消息的可靠性）【建议】

```java
package com.eddie.controller;

import com.eddie.entity.Person;
import com.eddie.entity.User;
import com.rabbitmq.client.Channel;
import org.springframework.amqp.core.Message;
import org.springframework.amqp.rabbit.annotation.RabbitHandler;
import org.springframework.amqp.rabbit.annotation.RabbitListener;
import org.springframework.stereotype.Controller;

/**
 @author EddieZhang
 @create 2023-01-09 20:17
 */
@Controller
@RabbitListener(queues = {"eddie-queue-1"})//多个消费者可以订阅同一队列，这时队列中的消息会被平摊（轮询）给多个消费者进行处理
public class MessageConsumerController {

    @RabbitHandler//使用在方法上 可以根据不同的类型的形参来指定接收不同类型的消息
    //method不能有返回值
    public void receiveMessage1(Message message, User user/*指定消息转换成的Java对象*/, Channel channel){
        System.out.println("Consumer1\tReceive\t" + "Message:\t" + message);
        System.out.println("Consumer1\tReceive\t" + "User:\t" + user);
        System.out.println("Consumer1\tReceive\t" + "Channel:\t" + channel);
        try {
            Thread.sleep(1000);
            System.out.println("Consumer1\tsleep了3s");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    @RabbitHandler//使用在方法上 可以根据不同的类型的形参来指定接收不同类型的消息
    //method不能有返回值
    public void receiveMessage2(Message message, Person person/*指定消息转换成的Java对象*/, Channel channel){
        System.out.println("Consumer2\tReceive\t" + "Message:\t" + message);
        System.out.println("Consumer2\tReceive\t" + "Person:\t" + person);
        System.out.println("Consumer2\tReceive\t" + "Channel:\t" + channel);
        try {
            Thread.sleep(1000);
            System.out.println("Consumer2\tsleep了3s");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

#### Consumer Reject(Nack) Message

> ```java
> //拒收消息的方法
> void basicNack(
>     long deliveryTag, //消息在queue中的Tag（自动生成并递增的）
>     boolean multiple, //是否批量拒收
>     boolean requeue)//true发回服务器重新入队（不丢弃 重新返回队列中）/false不重新入队(直接丢弃消息)
> ```

```java
@RabbitHandler//声明在方法上 根据方法的不同形参（重载）接收不同的消息
    //method不能有返回值
    public void receiveMessage2(Message message, Person person, Channel channel){
        try {
            channel.basicNack(message.getMessageProperties().getDeliveryTag(),false,false);
            //void basicNack(long deliveryTag, boolean multiple, boolean requeue)
            log.info("拒绝接收消息{{}}并要求不进行requeue(直接丢弃消息)",message.getMessageProperties().getDeliveryTag());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```

### Reliable Message☆

> ==**消息的可靠性**==保证可以采用**事务（throughput损失）**以及`manual Ack（推荐）`
>
> 
>
> 【Unacked(**手动Nack**或者**由于其他原因导致consumer未进行ack**)的消息会在Queue的ready状态下直到consumer进行消费并ack】
>
> 
>
> :rotating_light:**事务与ack不能共存**

![image-20230227112605556](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230227112605556.png)

```yaml
spring:
  rabbitmq:
    host: 192.168.199.180
    port: 5672
    virtual-host: /
    username: guest
    password: guest
    publisher-confirms: true #消息可靠到达MessageBroker的确认回调==============================producer端的confirm
    publisher-returns: true #消息到queues确认回调（失败会进行returns）==========================producer端的returns
    listener:
      simple:
        acknowledge-mode: manual #将ack的模式设置为手动确保消息消费完成后进行ack（默认为auto）======consumer端的ack
```

#### Producer

> publisher-confirms: true #消息可靠**到达MessageBroker的确认回调**
>
> - ConfirmCallback()
>
>   ```java
>   	/**
>   	 * A callback for publisher confirmations.
>   	 *
>   	 */
>   	@FunctionalInterface
>   	public interface ConfirmCallback {
>               
>   		/**
>   		 * Confirmation callback.
>   		 * @param correlationData correlation data for the callback.
>   		 * @param ack true for ack, false for nack
>   		 * @param cause An optional cause, for nack, when available, otherwise null.
>   		 */
>   		void confirm(@Nullable CorrelationData correlationData, boolean ack, @Nullable String cause);
>               
>   	}
>   ```
>
> publisher-returns: true #消息**到queues确认回调（失败会进行returns）**
>
> - ReturnCallback()
>
>   ```java
>   	/**
>   	 * A callback for returned messages.
>   	 *
>   	 */
>   	@FunctionalInterface
>   	public interface ReturnCallback {
>               
>   		/**
>   		 * Returned message callback.
>   		 * @param message the returned message.
>   		 * @param replyCode the reply code.
>   		 * @param replyText the reply text.
>   		 * @param exchange the exchange.
>   		 * @param routingKey the routing key.
>   		 */
>   		void returnedMessage(Message message, int replyCode, String replyText,
>   				String exchange, String routingKey);
>   	}
>   ```

```yaml
spring:
  rabbitmq:
    host: 192.168.199.180
    port: 5672
    virtual-host: /
    username: guest
    password: guest
    publisher-confirms: true #消息可靠到达MessageBroker的确认回调
    publisher-returns: true #消息到queues确认回调（失败会进行returns）
```



```java
@Configuration
@Slf4j
public class RabbitMQConfig {
    @Autowired
    RabbitTemplate rabbitTemplate;
    @Bean
    public MessageConverter messageConverter(){
        MessageConverter messageConverter = new Jackson2JsonMessageConverter();
        return messageConverter;
    }

    /**
     * 消息可靠到达交换机的确认回调
     */
    @PostConstruct
    public void confirmMessage(){
        rabbitTemplate.setConfirmCallback(new RabbitTemplate.ConfirmCallback() {
            /**
             * 消息可靠到达MessageBroker的确认回调
             * @param correlationData 消息的关联值(消息的唯一id)
             * @param b 消息是否可靠送达
             * @param s 原因
             */
            @Override
            public void confirm(CorrelationData correlationData, boolean b, String s) {
                log.info("消息的关联值(消息的唯一id)==>{{}}\t是否可靠送达==>{{}}\t原因==>{{}}",correlationData.getId(),b,s);
            }
        });
    }

    /**
     * 消息到queues确认回调（失败会进行returns）
     */
    @PostConstruct
    public void returnsMessage(){
        rabbitTemplate.setReturnCallback(new RabbitTemplate.ReturnCallback() {
            /**
             * 消息到queues确认回调（失败会进行returns）
             * @param message 投递失败的消息详情
             * @param i 返回的状态码
             * @param s 文本内容
             * @param s1 交换机
             * @param s2 路由键
             */
            @Override
            public void returnedMessage(Message message, int i, String s, String s1, String s2) {
                log.info("投递失败的消息详情==>{{}}\t状态码==>{{}}\t文本内容==>{{}}\t交换机==>{{}}\t路由键==>{{}}",message,i,s,s1,s2);
            }
        });
    }
}
```

```shell
`[消息可靠到达MessageBroker的确认回调]`
消息的关联值(消息的唯一id)==>{09d26ee9-509f-48a8-b582-daf411c57945}	是否可靠送达==>{true}	原因==>{null}
`[消息到queues确认回调（失败会进行returns）]`
投递失败的消息详情==>{(Body:'{"name":"EddieZhang_1","gender":"male","major":"Java-Backend-Development","age":21}' MessageProperties [headers={spring_returned_message_correlation=651acfa7-8151-4cf0-a48a-fef562607769, __TypeId__=com.eddie.entity.Person}, contentType=application/json, contentEncoding=UTF-8, contentLength=0, receivedDeliveryMode=PERSISTENT, priority=0, deliveryTag=0])}	
状态码==>{312}	文本内容==>{NO_ROUTE}	
交换机==>{eddie-exchange-direct}	
路由键==>{eddies-queue-1}
```

#### Consumer

> listener:
>       simple:
>         acknowledge-mode: manual #将ack的模式设置为手动确保消息消费完成后进行ack（默认为auto）
>
> ```java
> //ack的方法
> channel.basicAck(message.getMessageProperties().getDeliveryTag(),false);
> 
> void basicAck(
>     long deliveryTag, //消息在queue中的Tag（自动生成并递增的）
>     boolean multiple///是否批量签收
> ) throws IOException;
> ```

```yaml
spring:
  rabbitmq:
    host: 192.168.199.180
    port: 5672
    virtual-host: /
    username: guest
    password: guest
    publisher-confirms: true #消息可靠到达MessageBroker的确认回调
    publisher-returns: true #消息到queues确认回调（失败会进行returns）
    listener:
      simple:
        acknowledge-mode: manual #将ack的模式设置为手动确保消息消费完成后进行ack（默认为auto）
```

```java
@Controller
@RabbitListener(queues = {"eddie-queue-1"})//声明在类上 指定要接收的queue
@Slf4j
public class MessageConsumerController {

    @RabbitHandler//声明在方法上 根据方法的不同形参（重载）接收不同的消息
    //method不能有返回值
    public void receiveMessage1(Message message, User user, Channel channel){
        try {
            channel.basicAck(message.getMessageProperties().getDeliveryTag(),false);//手动签收确认ack
            //void basicAck(long deliveryTag, boolean multiple) throws IOException;
            log.info("消息{{}}签收了==>{{}}",message.getMessageProperties().getDeliveryTag(),user.toString());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    @RabbitHandler//声明在方法上 根据方法的不同形参（重载）接收不同的消息
    //method不能有返回值
    public void receiveMessage2(Message message, Person person, Channel channel){
        try {
            channel.basicAck(message.getMessageProperties().getDeliveryTag(),false);//手动签收确认ack
            //void basicAck(long deliveryTag, boolean multiple) throws IOException;
            log.info("消息{{}}签收了==>{{}}",message.getMessageProperties().getDeliveryTag(),person.toString());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

![image-20230227114421092](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230227114421092.png)

### 持久化消息

#### Spring Boot配置消息持久化

> RabbitMQ允许你持久化消息以确保消息不会在服务器重启或故障时丢失。
>
> 1. **队列持久化**：首先，你需要确保你的队列是持久化的。在声明队列时，设置队列的`durable`参数为`true`，这将使队列持久化。
>
>    ![image-20231016095221854](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231016095221854.png)
>
> 2. **消息持久化**：接下来，当你发布消息时，你需要将消息设置为持久化。这可以通过将消息的`delivery_mode`属性设置为`2`来实现。在大多数编程语言中，你可以通过消息的属性来设置它。
>
>    ```java
>    import org.springframework.amqp.rabbit.core.RabbitTemplate;
>    import org.springframework.amqp.rabbit.support.CorrelationData;
>    import org.springframework.amqp.rabbit.support.MessageProperties;
>    
>    @Autowired
>    private RabbitTemplate rabbitTemplate;
>    
>    public void sendMessage(String message) {
>        MessageProperties properties = new MessageProperties();
>        properties.setDeliveryMode(MessageProperties.PERSISTENT); // 设置消息为持久化
>    
>        CorrelationData correlationData = new CorrelationData();
>        rabbitTemplate.convertAndSend("my_queue", (Object) message, properties, correlationData);
>    }
>    ```
>
>    ```java
>    /**
>     * Message Properties for an AMQP message.
>     *
>     * @author Mark Fisher
>     * @author Mark Pollack
>     * @author Gary Russell
>     * @author Dmitry Chernyshov
>     * @author Artem Bilan
>     * @author Csaba Soti
>     */
>    public class MessageProperties implements Serializable {
>    
>    	public static final MessageDeliveryMode DEFAULT_DELIVERY_MODE = MessageDeliveryMode.PERSISTENT;
>        ...
>    {
>    ```
>
>    注意，持久化消息可能会对性能产生一些影响，因为消息需要写入磁盘。

#### RabbitMQ持久化消息工作流程和原理

> **RabbitMQ 通过`磁盘日志`来确保消息的持久化**，即使在服务器重启或故障发生时也能够恢复消息。下面是 RabbitMQ 磁盘日志的详细讲解，包括其工作流程和原理：
>
> **工作原理：**
>
> 1. **事务日志：** RabbitMQ 使用事务日志将消息和元数据写入磁盘。当你**发布一条持久化消息时，消息会首先被写入事务日志**。
> 2. **写入缓冲：** RabbitMQ 将消息写入一个写入缓冲区，并在接收到消息后立即确认写入操作。这确保了消息被快速写入，以提高消息传递的性能。
> 3. **刷新到磁盘：** 写入缓冲区的消息会定期刷新到磁盘上的事务日志。这个过程可以由操作系统的缓冲刷新机制或者 RabbitMQ 内部的刷新机制来完成。
> 4. **持久化队列：** 如果队列被声明为持久化的，队列的定义和元数据也会被写入磁盘。这确保了在服务器重启后，RabbitMQ 可以重新声明队列，并从磁盘日志中恢复队列的状态。
> 5. **消息投递确认：** RabbitMQ 在将消息投递到队列之前，会等待消息写入磁盘的确认。这确保了**消息在被确认投递到队列之前已经被持久化**。
>
> **流程概述：**
>
> 1. 发布持久化消息时，将消息写入事务日志。
> 2. 写入缓冲区立即确认消息写入。
> 3. 定期将写入缓冲区的消息刷新到磁盘事务日志中。
> 4. 如果队列是持久化的，则队列的定义和元数据也会被写入磁盘。
> 5. 等待消息写入磁盘的确认后，将消息投递到队列中。
>
> **优势和注意事项：**
>
> - 磁盘日志确保了消息的可靠性和持久性，即使在服务器故障或重启时也能够恢复消息。s
> - 这种机制提供了一定程度的安全性，但也会带来一些性能开销。因此，在高性能要求的场景中，需要权衡性能和可靠性。
>
> 通过磁盘日志，RabbitMQ 可以保证消息在服务器重启后的可靠性和恢复性，这使得它成为处理关键数据和任务的可靠消息代理系统。

### 实例

#### Hello World

![image-20221203171555433](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203171555433.png)

pom.xml

```java
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>RabbitMQ_Hello</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>
    <dependencies>
        <!--rabbitmq 依赖客户端-->
        <dependency>
            <groupId>com.rabbitmq</groupId>
            <artifactId>amqp-client</artifactId>
            <version>5.8.0</version>
        </dependency>
        <!--操作文件流的一个依赖-->
        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.6</version>
        </dependency>
    </dependencies>

</project>
```

Producer

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

import java.util.Queue;

/**
 @author EddieZhang
 @create 2022-12-03 17:05
 */
public class Producer {
    private static final String QUEUE_NAME = "Queue_Hello1";//队列name

    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();
        //channel进行队列声明
        /**
         * 生成一个队列
         * 1.队列名称
         * 2.队列里面的消息是否持久化 默认消息存储在内存中
         * 3.该队列是否只供一个消费者进行消费 是否进行共享 true 可以多个消费者消费
         * 4.是否自动删除 最后一个消费者端开连接以后 该队列是否自动删除 true 自动删除
         * 5.其他参数
         */
        channel.queueDeclare(QUEUE_NAME,false,false,false,null);
        //发送消息
        /**
         * 发送一个消息
         * 1.发送到那个交换机
         * 2.路由的 key 是哪个
         * 3.其他的参数信息
         * 4.发送消息的消息体
         */
        channel.basicPublish(null,QUEUE_NAME,null,"Hello World".getBytes());

        System.out.println("basic publish success~");

        //释放资源
        channel.close();
    }
}
```

![image-20221203174619435](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203174619435.png)

consumer

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

/**
 @author EddieZhang
 @create 2022-12-03 17:16
 */
public class Consumer {
    private static final String QUEUE_NAME = "Queue_Hello1";//队列name
    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        System.out.println("等待接收消息.........");

        //推送的消息如何进行消费的接口回调

        //消费者接收消息
        /**
         * 消费者消费消息
         * 1.消费哪个队列
         * 2.消费成功之后是否要自动应答 true 代表自动应答 false 手动应答
         * 3.消费者未成功消费的回调
         * 4.取消消费的一个回调
         */
        channel.basicConsume(QUEUE_NAME, true,(consumerTag, message) -> {
            System.out.println(new String(message.getBody()));
        },consumerTag -> {
            System.out.println("消息被中断");
        });



    }
}
```

![image-20221203174653601](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203174653601.png)

#### Work Queue

**工作队列**(又称任务队列)的主要思想是**避免立即执行资源密集型任务**，而不得不等待它完成。 相反我们安排任务在之后执行。我们把任务封装为消息并将其发送到队列。在后台运行的工作进 程将弹出任务并最终执行作业。当**有多个工作线程时**，这些工作线程**将一起处理这些任务**

**轮训分发消息**

![image-20221203220328117](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221203220328117.png)

consumer

启动多个消费者实例（轮询接收producer生产到队列中的message）

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;
import com.rabbitmq.client.Delivery;

/**
 @author EddieZhang
 @create 2022-12-03 20:25
 */
public class Consumer1 {
    private static final String QUEUE_NAME = "Queue_Work1";//队列name
    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        System.out.println("消费者3号等待接收消息.........");

        //消费者接收消息
        /**
         * 消费者消费消息
         * 1.消费哪个队列
         * 2.消费成功之后是否要自动应答 true 代表自动应答 false 手动应答
         * 3.消费者未成功消费的回调
         * 4.取消消费的一个回调
         */
        channel.basicConsume(QUEUE_NAME, true,(String consumerTag, Delivery message) -> {
            String receiveMessage = new String(message.getBody());
            System.out.println("接受到的消息\t" + receiveMessage);
        },(String consumerTag) -> {
            System.out.println(consumerTag + "消费者取消消费接口回调逻辑");
        });


    }
}
```

producer

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

import java.util.Scanner;

/**
 @author EddieZhang
 @create 2022-12-03 21:26
 */
public class producer1 {
    private static final String QUEUE_NAME = "Queue_Work1";//队列name
    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        //声明一个队列
        /**
         * 生成一个队列
         * 1.队列名称
         * 2.队列里面的消息是否持久化 默认消息存储在内存中
         * 3.该队列是否只供一个消费者进行消费 是否进行共享 true 可以多个消费者消费
         * 4.是否自动删除 最后一个消费者端开连接以后 该队列是否自动删除 true 自动删除
         * 5.其他参数
         */
        channel.queueDeclare(QUEUE_NAME,false,false,false,null);

        //从控制台接收消息
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNext()){
            String message = scanner.next();
            /**
             * 发送一个消息
             * 1.发送到那个交换机
             * 2.路由的 key 是哪个
             * 3.其他的参数信息
             * 4.发送消息的消息体
             */
            channel.basicPublish("",QUEUE_NAME,null,message.getBytes());
            System.out.println("message send success " + message);
        }
        //释放资源
        channel.close();

    }

}
```

#### 消息应答

为了**保证消息**在发送过程中**不丢失**，rabbitmq 引入**消息应答机制**，消息应答就是:**消费者在接收到消息并且处理该消息之后**，**告诉 rabbitmq 它已经处理了**，rabbitmq **才可以把该消息删除了**

##### **自动应答：**

**消息发送后**立即**被认为已经传送成功**，这种模式需要在高吞吐量和数据传输安全性方面做权衡；没有对传递的消息数量进行限制，所以这种模式仅适用在消费者可以**高效**并以某种速率能够处理这些消息的情况下使用。但对于发送的消息**不具备保障性**。

##### **手动应答：**

A.Channel.basicAck(用于**肯定确认**) RabbitMQ 已知道该消息并且成功的处理消息，可以将其丢弃了 

B.Channel.basicNack(用于**否定确认**) 

C.Channel.basicReject(用于**否定确认**) 与 Channel.basicNack 相比少一个参数 不处理该消息了直接拒绝，可以将其丢弃了

**Multiple 的解释**：手动应答的好处是可以批量应答并且减少网络拥堵

multiple 的 true 和 false 代表不同意思 

true 代表批量应答 channel 上未应答的消息 比如说 channel 上有传送 tag 的消息 5,6,7,8 当前 tag 是 8 那么此时 5-8 的这些还未应答的消息都会被确认收到消息应答 （当接收到Chanel中的一条消息就会批量应答Channel中的所有消息）

false 同上面相比 只会应答 tag=8 的消息 5,6,7 这三个消息依然不会被确认收到消息应答（**建议使用false不批量进行应答确保消息的可靠性**）

 **消息自动重新入队**:

如果消费者由于某些原因失去连接(其通道已关闭，连接已关闭或 TCP 连接丢失)，导致消息 **未发送 ACK 确认**，RabbitMQ 将了解到**消息未完全处理**，并**将对其重新排队**。如果**此时其他消费者 可以处理**，它将很快将其重新分**发给另一个消费者**。这样，即使某个消费者偶尔死亡，也可以**确 保不会丢失任何消息**

##### Instance

生产者生产的消息由多个消费者轮询进行消费同时消费者消费后的消息要进行手动签收（**确保消息**可靠的**被签收**后才会对队列中的消息进行删除）

多个消费者中若存在其中的**消费者在进行消费时出现宕机等未完成消费**（未手动签收）；会将**消息自动重新入队**并**交由另外的消费者进行消费**（**消息可靠**性）

Producer

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

import java.util.Scanner;

/**
 @author EddieZhang
 @create 2022-12-05 9:27
 */
public class Producer2 {
    private static final String QUEUE_NAME = "Message_Ack";//队列name

    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        //声明queue
        /**
         * 参数
         * 1.队列name
         * 2.持久化
         * 3.共享
         * 4.自动删除队列
         * 5.其他参数
         */
        channel.queueDeclare(QUEUE_NAME,false,false,false,null);

        //获取控制台的内容并发送到队列中
        Scanner scanner = new Scanner(System.in);
        System.out.println("Talk something~~");
        while (scanner.hasNext()){
            String message = scanner.next();
            channel.basicPublish("",QUEUE_NAME,null,message.getBytes());
            System.out.println("send message success~\t" + message);
        }
        //释放资源
        channel.close();
    }
}
```

consumer_01

```java
package com.eddie;
import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

/**
 @author EddieZhang
 @create 2022-12-05 9:27
 */
public class Consumer201 {
    private static final String QUEUE_NAME = "Message_Ack";//队列name

    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        System.out.println("consumer01 等待消费且消费效率高");

        //消费消息
        /**
         * 消费者消费消息
         * 1.消费哪个队列
         * 2.消费成功之后是否要自动应答 true 代表自动应答 false 手动应答
         * 3.消费者未成功消费的回调
         * 4.取消消费的一个回调
         */
        channel.basicConsume(QUEUE_NAME,false,(consumerTag,delivery) -> {
            try {
                Thread.sleep(1000L);//休眠1s
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("consumer01 接收到了消息\t" + new String(delivery.getBody()));//打印message
            //手动签收
            /**
             * 参数
             * 1.消息标记
             * 2.是否批量签收
             */
            channel.basicAck(delivery.getEnvelope().getDeliveryTag(),false);
            System.out.println(
                    delivery.getEnvelope().getDeliveryTag()
            );

        },consumerTag -> {
            System.out.println(consumerTag+"消费者取消消费接口回调逻辑");
        });
    }
}
```

consumer_02

```java
package com.eddie;

import com.rabbitmq.client.Channel;
import com.rabbitmq.client.ConnectionFactory;

/**
 @author EddieZhang
 @create 2022-12-05 9:27
 */
public class Consumer202 {
    private static final String QUEUE_NAME = "Message_Ack";//队列name

    public static void main(String[] args) throws Exception{
        //创建连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        connectionFactory.setHost("192.168.199.142");//指定连接Host
        connectionFactory.setUsername("eddie");//指定登录账号
        connectionFactory.setPassword("eddie");//登录密码

        //指定connection并指定channel
        Channel channel = connectionFactory.newConnection().createChannel();

        System.out.println("consumer02 等待消费且消费效率很低");

        //消费消息
        /**
         * 消费者消费消息
         * 1.消费哪个队列
         * 2.消费成功之后是否要自动应答 true 代表自动应答 false 手动应答
         * 3.消费者未成功消费的回调
         * 4.取消消费的一个回调
         */
        channel.basicConsume(QUEUE_NAME,false,(consumerTag,delivery) -> {
            try {
                Thread.sleep(30000L);//休眠30s
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("consumer02 接收到了消息\t" + new String(delivery.getBody()));//打印message
            //手动签收
            /**
             * 参数
             * 1.消息标记
             * 2.是否批量签收
             */
            channel.basicAck(delivery.getEnvelope().getDeliveryTag(),false);
            System.out.println(
                    delivery.getEnvelope().getDeliveryTag()
            );

        },consumerTag -> {
            System.out.println(consumerTag+"消费者取消消费接口回调逻辑");
        });
    }
}
```
