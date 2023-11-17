# Zookeeper

![image-20221206112643989](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206112643989.png)

![image-20230408170626313](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230408170626313.png)

> **分布式应用程序协调服务软件**

[Apache ZooKeeper](https://zookeeper.apache.org/)

[**ZooKeeper源码分析与实战**](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/ZooKeeper%E6%BA%90%E7%A0%81%E5%88%86%E6%9E%90%E4%B8%8E%E5%AE%9E%E6%88%98-%E5%AE%8C)

## Zookeeper - OverView

> ZooKeeper 是 Apache 软件基金会的一个软件项目，它为大型**分布式**计算提供开源的**分布式配置服务**、**同步服务**和**命名注册**。
>
> ZooKeeper 的架构通过冗余服务实现高可用性。
>
> Zookeeper 的设计目标是将那些复杂且容易出错的分布式一致性服务封装起来，构成一个高效可靠的原语集，并以一系列简单易用的接口提供给用户使用。
>
> 一个典型的分布式数据一致性的解决方案，分布式应用程序可以基于它实现诸如数据**发布/订阅**、**负载均衡**、**命名服务**、**分布式协调/通知**、**集群管理**、**Master 选举**、**分布式锁**和**分布式队列**等功能。
>
> - **命名服务** - 按名称标识集群中的节点。它类似于DNS，但仅对于节点。
> - **配置管理** - 加入节点的最近的和最新的系统配置信息。
> - **集群管理** - 实时地在集群和节点状态中加入/离开节点。
> - **选举算法** - 选举一个节点作为协调目的的leader。
> - **锁定和同步服务** - 在修改数据的同时锁定数据。此机制可帮助你在连接其他分布式应用程序（如Apache HBase）时进行自动故障恢复。
> - **高度可靠的数据注册表** - 即使在一个或几个节点关闭时也可以获得数据。
>
> 分布式应用程序提供了很多好处，但它们也抛出了一些复杂和难以解决的挑战。ZooKeeper框架提供了一个完整的机制来克服所有的挑战。竞争条件和死锁使用**故障安全同步方法**进行处理。另一个主要缺点是数据的不一致性，ZooKeeper使用**原子性**解析。
>
> 
>
> #### **Benefits of ZooKeeper**
>
> Here are the benefits of using ZooKeeper −
>
> - **Simple distributed coordination process**
> - **Synchronization** − Mutual exclusion and co-operation between server processes. This process helps in Apache HBase for configuration management.
> - **Ordered Messages**
> - **Serialization** − Encode the data according to specific  rules. Ensure your application runs consistently. This approach can be  used in MapReduce to coordinate queue to execute running threads.
> - **Reliability**
> - **Atomicity** − Data transfer either succeed or fail completely, but no transaction is partial.
>
> #### **Benefits of Distributed Applications**
>
> - **Reliability** − Failure of a single or a few systems does not make the whole system to fail.
> - **Scalability** − Performance can be increased as and when  needed by adding more machines with minor change in the configuration of the application with no downtime.
> - **Transparency** − Hides the complexity of the system and shows itself as a single entity / application.
>
> #### **Challenges of Distributed Applications**
>
> - **Race condition** − Two or more machines trying to perform a  particular task, which actually needs to be done only by a single  machine at any given time. For example, shared resources should only be  modified by a single machine at any given time.
> - **Deadlock** − Two or more operations waiting for each other to complete indefinitely.
> - **Inconsistency** − Partial failure of data.

![image-20221206112822848](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206112822848.png)



Each one of the components that is a part of the ZooKeeper architecture has been explained in the following table.

| Part                   | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| Client                 | Clients, one of the nodes in our distributed application cluster, access information from the server. For a particular time interval,  every client sends a message to the server to let the sever know that  the client is alive. Similarly, the server sends an acknowledgement when a client  connects. If there is no response from the connected server, the client  automatically redirects the message to another server. |
| Server                 | Server, one of the nodes in our ZooKeeper ensemble, provides all the services to clients. Gives acknowledgement to client to inform that the server is alive. |
| Ensemble<br />(ZK集群) | Group of ZooKeeper servers. The minimum number of nodes that is required to form an ensemble is 3. |
| Leader                 | Server node which performs automatic recovery if any of the connected node failed. Leaders are elected on service startup. |
| Follower               | Server node which follows leader instruction.                |

## Zookeeper - Workflow

![image-20230408170626313](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230408170626313.png)

| Component           | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| Write               | Write process is handled by the leader node. The leader forwards the write request to all the znodes and waits for answers from the znodes.  If half of the znodes reply, then the write process is complete. |
| Read                | Reads are performed internally by a specific connected znode, so there is no need to interact with the cluster. |
| Replicated Database | It is used to store data in zookeeper. Each znode has its own  database and every znode has the same data at every time with the help  of consistency. |
| Leader              | Leader is the Znode that is responsible for processing write requests. |
| Follower            | Followers receive write requests from the clients and forward them to the leader znode. |
| Request Processor   | Present only in leader node. It governs write requests from the follower node. |
| Atomic broadcasts   | Responsible for broadcasting the changes from the leader node to the follower nodes. |

> Once a ZooKeeper ensemble starts, it will wait for the clients to  connect. Clients will connect to one of the nodes in the ZooKeeper  ensemble. It may be a leader or a follower node. Once a client is  connected, the node assigns a session ID to the particular client and  sends an acknowledgement to the client. If the client does not get an  acknowledgment, it simply tries to connect another node in the ZooKeeper ensemble. Once connected to a node, the client will send heartbeats to  the node in a regular interval to make sure that the connection is not  lost.
>
> - **If a client wants to read a particular znode,** it sends a **read request** to the node with the znode path and the node returns the requested  znode by getting it from its own database. For this reason, reads are  fast in ZooKeeper ensemble.
> - **If a client wants to store data in the ZooKeeper ensemble**, it sends the znode path and the data to the server. The connected  server will forward the request to the leader and then the leader will  reissue the writing request to all the followers. If only a majority of  the nodes respond successfully, then the write request will succeed and a successful return code will be sent to the client. Otherwise, the write request will fail. The strict majority of nodes is called as **Quorum**.
>
> **Nodes in a ZooKeeper Ensemble**
>
> Let us analyze the effect of having different number of nodes in the ZooKeeper ensemble.
>
> - If we have **a single node**, then the ZooKeeper ensemble  fails when that node fails. It contributes to “Single Point of Failure”  and it is not recommended in a production environment.
> - If we have **two nodes** and one node fails, we don’t have majority as well, since one out of two is not a majority.
> - If we have **three nodes** and one node fails, we have  majority and so, it is the minimum requirement. It is mandatory for a  ZooKeeper ensemble to have at least three nodes in a live production  environment.
> - If we have **four nodes** and two nodes fail, it fails again  and it is similar to having three nodes. The extra node does not serve  any purpose and so, it is **better to add nodes in odd numbers, e.g., 3,  5, 7.** 

## zookeeper 系统结构

zookeeper 提供的名称空间非常类似于标准文件系统，key-value 的形式存储。名称 key 由斜线 **/** 分割的一系列路径元素，zookeeper 名称空间中的每个节点都是由一个路径标识

> 最主要的是 znode 有四种类型：
>
> - 永久节点（除非手动删除，节点永远存在）
> - 永久有序节点（按照创建顺序会为每个节点末尾带上一个序号如：`root-1`）
> - 瞬时节点（创建客户端与 Zookeeper 保持连接时节点存在，断开时则删除并会有相应的通知）
> - 瞬时有序节点（在瞬时节点的基础上加上了顺序）
>
> 考虑下上文使用 Redis 最大的一个问题是什么？
>
> 其实就是不能实时的更新服务提供者的信息。
>
> 那利用 Zookeeper 是怎么实现的？
>
> 主要看第三个特性：**瞬时节点**
>
> Zookeeper 是一个典型的观察者模式。
>
> - 由于瞬时节点的特点，我们的消费者可以订阅瞬时节点的父节点。
> - 当新增、删除节点时所有的瞬时节点也会自动更新。
> - 更新时会给订阅者发起通知告诉最新的节点信息。
>
> 这样我们就可以实时获取服务节点的信息，同时也只需要在第一次获取列表时缓存到本地；也不需要频繁和 Zookeeper 产生交互，只用等待通知更新即可。
>
> 并且不管应用什么原因节点 down 掉后也会在 Zookeeper 中删除该信息。

![image-20230408181233501](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230408181233501.png)

![image-20221206112136402](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206112136402.png)



## 相关理论

### CAP理论

CAP 理论指出对于一个分布式计算系统来说，**不可能同时满足以下三点**：

- **一致性(Consistency)**：在分布式环境中，一致性是指数据在多个副本之间是否能够保持一致的特性，等同于所有节点访问同一份最新的数据副本。在一致性的需求下，当一个系统在数据一致的状态下执行更新操作后，应该保证系统的数据仍然处于一致的状态。
- **可用性(Availability)：**每次请求都能获取到正确的响应，但是不保证获取的数据为最新数据。
- **分区容错性(Partition Tolerance)：**分布式系统在遇到任何网络分区故障的时候，仍然需要能够保证对外提供满足一致性和可用性的服务，除非是整个网络环境都发生了故障。

![image-20221206113122527](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206113122527.png)

一个分布式系统最多只能同时满足一致性（Consistency）、可用性（Availability）和分区容错性（Partition tolerance）这三项中的两项。

在这三个基本需求中，最多只能同时满足其中的两项，**P 是必须的**，因此只能在 **CP** 和 **AP** 中选择，**zookeeper 保证的是 CP**，对比 spring cloud 系统中的注册中心 **Eureka 实现的是 AP**。

### BASE 理论

BASE 是 ==Basically Available(基本可用)==、==Soft-state(软状态)== 和 ==Eventually Consistent(最终一致性)== 三个短语的缩写。

- **基本可用：**在分布式系统出现故障，允许损失部分可用性（服务降级、页面降级）。
- **软状态：**允许分布式系统出现中间状态。而且中间状态不影响系统的可用性。这里的中间状态是指不同的 data replication（数据备份节点）之间的数据更新可以出现延时的最终一致性。
- **最终一致性：**data replications 经过一段时间达到一致性。

**BASE 理论是对 CAP 中的一致性和可用性进行一个权衡的结果**，理论的核心思想就是：我们无法做到强一致，但每个应用都可以根据自身的业务特点，采用适当的方式来使系统达到最终一致性。

## Zookeeper 安装配置

### Linux 安装

[Apache ZooKeeper](https://zookeeper.apache.org/releases.html)

![image-20221206114549536](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206114549536.png)

![image-20221206114605315](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221206114605315.png)

```
[root@192 opt]# tar -zxvf zookeeper-3.4.9.tar.gz #解压缩
$ cd zookeeper-3.4.14 
$ cd conf/ #进去配置文件目录
$ cp zoo_sample.cfg zoo.cfg #复制一份配置文件模板 并命名为zoo.cfg用于启动
$ cd ..
$ cd bin/ #进去到bin目录下
$ sh zkServer.sh start #启动zookeeper
$ sh zkServer.sh status #查看zookeeper状态
$ sh zkCli.sh #启动客户端
```

