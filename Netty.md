# Netty

![image-20230424164005406](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424164005406.png)

> Netty is **an advanced framework for creating high-performance networking applications**. 
> three main points:
> ■ You don’t have to be a networking expert to build applications with Netty.
> ■ Using Netty is much easier than using the underlying Java APIs directly. 
>
> ■ Netty promotes good design practices, such as keeping your application logic decoupled from the network layer.

https://javadoop.com/post/netty-part-1

## Netty Overview

### Feature

![image-20230424164302554](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424164302554.png)

### Application Scenarios

![image-20230424164700157](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424164700157.png)

### Core Component

![image-20230424230926228](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424230926228.png)

![image-20230424230319356](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424230319356.png)

### Netty 线程模型

#### 单线程模式

> **一个线程单独处理客户端连接以及I/O读写操作**，涉及到accept，read，decode，process，encode，send等事件
>
> 
>
> 不适合应用于高负载，高并发，对性能要求较高的场景

![image-20230424233014241](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424233014241.png)

#### 多线程模式

> **一个Acceptor线程只负责监听客户端连接**
>
> **一个NIO线程池负责处理I/O读写**
>
>
> 
> 满足于绝大部分应用场景，并发连接量不是特别大的时候

![image-20230424233301158](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424233301158.png)

![image-20230424233324473](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424233324473.png)

#### 主从多线程模式

> **有一个主线程池，从中挑选一个线程作为Acceptor线程用于绑定监听端口，接收客户端连接；其他的线程负责后续的接入认证等工作完成连接。**
>
> **有一个子线程池，负责具体的I/O读写操作**
>
>
> 多线程模型无法满足需求时，考虑使用主从多线程模型

![image-20230424234017679](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424234017679.png)



## A Quick Guide to Java on Netty

![image-20230424234029813](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424234029813.png)

> Server

![image-20230424231739388](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424231739388.png)

> Client

![image-20230424231801138](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424231801138.png)