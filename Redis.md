# Redis

https://redis.io/

![image-20230130205947937](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130205947937.png)

![image-20240130162356393](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240130162356393.png)

> Redis是一个开源的**内存数据存储系统**，可以用作数据库、缓存和消息中间件。它支持多种数据结构，包括字符串、哈希表、列表、集合和有序集合等，并提供了丰富的API以及高可用性、分布式、事务等特性。Redis被广泛用于互联网应用领域，如社交网络、电子商务、游戏等。
>
> 以下是Redis的一些使用场景：
>
> 1. **缓存**：Redis最常见的使用场景是作为缓存，将热点数据放在内存中，以提高数据访问的速度。它支持缓存的自动过期、LRU淘汰等机制，并可以设置最大内存使用量。
> 2. **消息中间件**：Redis提供了发布-订阅（Pub/Sub）功能，可以用作消息中间件。它支持多个消费者订阅同一个频道，支持按照模式匹配订阅多个频道，适合用于实时推送、实时聊天等场景。
> 3. **计数器**：Redis的原子性操作可以用于计数器的实现，如统计网站访问量、商品销售量等。
> 4. **分布式锁**：Redis提供了SETNX命令可以实现分布式锁，保证在分布式环境下同一时刻只有一个客户端可以访问某个资源，防止数据竞争问题的发生。
> 5. **排行榜**：Redis的有序集合（Sorted Set）可以用于实现排行榜，按照某种指标进行排序，如根据用户积分、粉丝数等。
> 6. **地理位置**：Redis提供了地理位置索引功能，可以将经纬度作为score存储在有序集合中，实现附近的人、附近的店等功能。

## Why is Redis so fast?★

![image-20230212120504791](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230212120504791.png)

> Redis is a fast data store due to several design choices made in its development:
>
> 1. **In-Memory Storage**: Redis stores all data in-memory, which eliminates the overhead of disk I/O, making it much faster than traditional disk-based databases.
> 2. **Data Structures**: Redis supports a variety of data structures like strings, hashes, lists, sets, and sorted sets. These data structures are optimized for speed and are implemented in a way that is efficient and lightweight.
> 3. **Single-Threaded**: Redis is single-threaded, which means that it processes all requests on a single CPU core, avoiding the overhead of context switching between threads or processes.
> 4. **Non-Blocking I/O**: Redis uses non-blocking I/O, which allows it to handle a large number of simultaneous connections without blocking or slowing down other connections.
> 5. **Asynchronous Operations**: Redis supports asynchronous operations, which means that a client can send multiple requests to Redis without waiting for a response to each request. This feature reduces latency and increases throughput.
> 6. **Optimized Algorithms**: Redis uses several optimized algorithms, such as the LRU (Least Recently Used) eviction algorithm for cache expiration and the Skip List data structure for fast indexing and searching.

## Redis起步安装

![image-20221115141221935](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115141221935.png)

![image-20221115141239112](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115141239112.png)

## Redis五大基本数据类型★

> **5种基础数据类型**，字符串(String)、列表(List)、集合(Set)、有序集合(ZSet)和哈希(Hash)。
>
> - ### **字符串(String)**
>
>   - 应用场景：字符串类型**主要用于存储单个值，例如用户名、密码、手机号等**。此外，字符串**还可以用于计数器**、**缓存和分布式锁**等。
>
>   - 特点：字符串类型的最大特点是**简单、高效，它可以快速地存储、获取、修改和删除单个值，并且支持原子性操作**。此外，字符串类型还**支持自增、自减等操作，可以方便地实现计数器**等功能。
>   - 常用操作指令：
>     - SET key value：设置key对应的value
>     - GET key：获取key对应的value
>     - INCR key：将key对应的value加1
>     - DECR key：将key对应的value减1
>     - APPEND key value：在key对应的value后追加字符串value
>
> - ### **列表(List)**
>
>   - 应用场景：列表类型主要用于**存储多个值**，例如**任务队列、消息队列、用户行为记录**等。列表类型还可以用于**实现简单的缓存和排行榜**等。
>
>   - 特点：列表类型的最大特点是**有序、可重复**。它**可以快速地在两端添加、删除元素，并且支持范围查询、修剪等操作**，非常**适合用作队列和栈**等数据结构。
>   - 常用操作指令：
>     - LPUSH key value [value...]：将一个或多个值插入到列表的头部
>     - RPUSH key value [value...]：将一个或多个值插入到列表的尾部
>     - LPOP key：移除并返回列表的第一个元素
>     - RPOP key：移除并返回列表的最后一个元素
>     - LRANGE key start stop：获取列表从start到stop范围内的元素
>
> - ### **集合(Set)**
>
>   - 应用场景：集合类型主要用于**存储唯一值**，例如**用户标签、好友关系、点赞记录**等。集合类型还可以**用于计算共同关注、共同点赞**等。
>
>   - 特点：集合类型的最大特点是**无序、不可重复**。它**可以快速地添加、删除元素**，并且支持**求交、求并、求差**等操作，非常适合用作**去重和筛选数据**。
>   - 常用操作指令：
>     - SADD key member [member...]：将一个或多个元素添加到集合中
>     - SMEMBERS key：获取集合中的所有元素
>     - SINTER key [key...]：获取多个集合的交集
>     - SUNION key [key...]：获取多个集合的并集
>     - SREM key member [member...]：从集合中移除一个或多个元素
>
> - ### **有序集合(ZSet)**
>
>   - 应用场景：有序集合类型主要用于**存储带权值的唯一值**，例如**排行榜、搜索建议**等。有序集合类型还可以用于**实现简单的限流、延时队列**等。
>
>   - 特点：有序集合类型的最大特点是**有序、不可重复**。它可以**快速地添加、删除元素**，并且支持**按照权值范围查询、修剪等操作**，非常适合用作**排行榜和排序**等。
>   - 常用操作指令：
>     - ZADD key score member [score member...]：向有序集合中添加一个或多个元素
>     - ZRANGE key start stop [WITHSCORES]：获取有序集合从start到stop范围内的元素
>     - ZRANK key member：获取有序集合中元素的排名
>     - ZINCRBY key increment member：将有序集合中元素的分值增加指定的increment
>
> - ### **哈希(Hash)**
>
>   - 应用场景：哈希类型主要用于**存储多个字段和值的映射关系**，例如**用户信息、商品信息**等，**购物车**。哈希类型还可以用于**实现简单的缓存和计数器**等。
>   - 特点：可以**存储多个键值对**支持**对单个字段进行读写操作**，适合存储结构化数据可以对字段进行自增、自减等操作常用于存储结构化数据
>   - 常用操作指令：
>     - HSET key field value：设置哈希key中的一个字段的值
>     - HGET key field：获取哈希key中的一个字段的值
>     - HGETALL key：获取哈希key中的所有字段和值
>     - HINCRBY key field increment：将哈希key中的一个字段的值增加指定的increment
>     - HDEL key field [field...]：删除哈希key中的一个或多个字段

![image-20230328104653679](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230328104653679.png)

### 五种对象类型

![image-20230409141916190](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409141916190.png)

![image-20230409140910581](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409140910581.png)

![image-20230409142100603](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409142100603.png)

![image-20230409141032351](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409141032351.png)

![image-20230409140605779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409140605779.png)

![image-20230409141104918](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409141104918.png)

![image-20230409141134881](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409141134881.png)





### 底层数据结构

![image-20230328104955156](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230328104955156.png)

#### SDS（Simple Dynamic String）

![image-20230409122612787](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409122612787.png)

![image-20230409121348233](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409121348233.png)

#### 链表(Linked List)

![image-20230409122951549](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409122951549.png)

![image-20230409122856697](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409122856697.png)

![image-20230409122906810](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409122906810.png)

![image-20230409122824254](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409122824254.png)

#### 字典（Dict）

![image-20230409123217972](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409123217972.png)

![image-20230409124754271](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409124754271.png)



![image-20230409123429176](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409123429176.png)



![image-20230409124241957](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409124241957.png)

![image-20230409124538504](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409124538504.png)

![image-20230409123702230](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409123702230.png)

![image-20230409124838687](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409124838687.png)

![image-20230409124850690](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409124850690.png)

![image-20230409125551609](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409125551609.png)

#### SkipList

![image-20230409132010588](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409132010588.png)

![image-20230409130137039](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409130137039.png)

![image-20230409131228487](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409131228487.png)

![image-20230409130434768](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409130434768.png)



#### Intset

![image-20230409132318202](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409132318202.png)

![image-20230409132436926](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409132436926.png)

![image-20230409132618190](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409132618190.png)

![image-20230409132629259](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409132629259.png)

![image-20230409133126113](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409133126113.png)

![image-20230409133149043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409133149043.png)

#### ZipList

![image-20230409134849566](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409134849566.png)

![image-20230409134957339](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409134957339.png)

![image-20230409134922408](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409134922408.png)

![image-20230409134939508](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409134939508.png)

![image-20230409135125113](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409135125113.png)

![image-20230409135451618](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409135451618.png)

![image-20230409135505088](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409135505088.png)

![image-20230409135525066](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409135525066.png)



## Redis6新的数据类型

### BitMap

专门**进行位操作的字符串**

位图[Bitmap简介 - 废物大师兄 - 博客园 (cnblogs.com)](https://www.cnblogs.com/cjsblog/p/11613708.html)

![image-20221115210832052](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115210832052.png)

若**活跃用户量并不大** 则**不推荐使用bitmap**

![image-20221115211029253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115211029253.png)

![image-20221115210557976](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115210557976.png)

#### 位图应用原理

![image-20221115210707353](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115210707353.png)

#### 位图常用命令

##### 1) SETBIT命令

用来设置或者清除某一位上的值，其返回值是原来位上存储的值。key 在初始状态下所有的位都为 0 ，语法格式如下：

```
SETBIT key offset value
```

其中 offset 表示偏移量，从 0 开始。示例如下：

```
127.0.0.1:6379> SET user:1 a
OK
#设置偏移量为0
127.0.0.1:6379> SETBIT user:1 0 1
(integer) 0
#当对应位的字符是不可打印字符，redis会以16进制形式显示
127.0.0.1:6379> GET user:1
"\xe1"
```

##### 2) GETBIT命令

用来获取某一位上的值。示例如下：

```
127.0.0.1:6379> GETBIT user:1 0
(integer) 1
```

当偏移量 offset 比字符串的长度大，或者当 key 不存在时，返回 0。

```
redis> EXISTS bits
(integer) 0
redis> GETBIT bits 100000
(integer) 0
```

##### 3) BITCOUNT命令

统计指定位区间上，值为 1 的个数。语法格式如下：

```
BITCOUNT key [start end]
```

示例如下：

```
127.0.0.1:6379> BITCOUNT user:1
(integer) 8
```

通过指定的 start 和 end 参数，可以让计数只在特定的字节上进行。start 和 end 参数和 [GETRANGE](http://c.biancheng.net/redis2/getrange.html) 命令的参数类似，都可以使用负数，比如 -1 表示倒数第一个位， -2 表示倒数第二个位。

##### 4）BITOP命令

and

or

### Hyperloglog

**高效计算基数**

基数（不重复元素个数）

统计的**误差率是0.81%。**

```
例如集合中元素有{1，3，5，7，5，3，8}
基数（不重复元素）则为5{1，3，5，7，8}
```

解决基数问题的多种方案

**MySQL**中的 **select distinct count** 计算不重复元素

**Redis**中 **hash，set，bitmap**等数据结构处理

上述方式虽然可以完成需求且精确 但是**随着数据量的剧增** 会**导致空间占用问题** 对于大数据量的数据是不切实际的

因此推出**Hyperloglog（基数统计算法）**

在Redis中；每个HyperLogLog键只需要花费12KB内存，就可以计算出2^64个不同元素的基数。

#### 应用场景

开发中：统计网站PV（**PageView页面访问量**）**允许一定的误差**

#### 命令

pfadd datalist （添加数据集-无法添加重复的）

pfcount datalist （统计数据集）

pfmerge 合并为哪个key 要合并的key1 要合并的key2 （合并数据-自动去重）

### Grographic

**地理位置 城市经纬度查询 范围查询 距离查询 经纬度hash值 相关操作**

![image-20221115233106371](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115233106371.png)

##### ①geoadd（添加）、geopos（查看）、geodist（计算距离）操作

```
127.0.0.1:6379> geoadd city 118.8921 31.32751 nanjing 197.30794 31.79322  
#当经纬度其中一个或者两个超过界限值，报错，信息如下：
(error) ERR syntax error. Try GEOADD key [x1] [y1] [name1] [x2] [y2] [name2] ...
#添加城市经纬度 语法格式： geoadd key 经度 纬度 name +++可多个添加
#添加成功后返回添加成功的数量值
127.0.0.1:6379> geoadd city 118.8921 31.32751 nanjing 117.30794 31.79322 hefei 102.82147 24.88554 kunming 91.13775 29.65262 lasa 116.23128 40.22077 beijing 106.54041 29.40268 chongqing  
(integer) 6
127.0.0.1:6379> ZRANGE city 0 -1  #注意：geo的查看方式和zset的命令是一致的，
#由此可知，geo本质上还是个集合，不过Redis官方对其进行了二次封装
1) "lasa"
2) "kunming"
3) "chongqing"
4) "hefei"
5) "nanjing"
6) "beijing"
127.0.0.1:6379> geopos city nanjing  #查看看指定城市的经纬度信息
1) 1) "118.89209836721420288"
   2) "31.32750976275760735"
127.0.0.1:6379> geopos city nanjing beijing  #查看看多个城市的经纬度信息
1) 1) "118.89209836721420288"
   2) "31.32750976275760735"
2) 1) "116.23128265142440796"
   2) "40.22076905438526495"
127.0.0.1:6379> geodist city nanjing beijing   #计算南京到北京之间的距离，默认返回单位是m
"1017743.1413"
127.0.0.1:6379> geodist city nanjing beijing km  #km  千米
"1017.7431"
127.0.0.1:6379> geodist city nanjing beijing mi  #mi  英里
"632.3978"
127.0.0.1:6379> geodist city nanjing beijing ft  #ft  英尺
"3339052.3010"
```

##### ②georadius（查询附近位置）操作

```
127.0.0.1:6379> ZRANGE city 0 -1  #查看城市
1) "lasa"
2) "kunming"
3) "chongqing"
4) "hefei"
5) "nanjing"
6) "beijing"
#查看指定位置的1000公里范围内有哪些城市
127.0.0.1:6379> georadius city 120 38 1000 km  
1) "beijing"
2) "hefei"
3) "nanjing"
127.0.0.1:6379> georadius city 120 38 400 km  #查看指定位置的400公里范围内有哪些城市
(empty array)
127.0.0.1:6379> georadius city 120 38 550 km  #查看指定位置的550公里范围内有哪些城市
1) "beijing"
#查看指定位置的550公里范围内有哪些城市,withcoord指定返回城市的name
127.0.0.1:6379> georadius city 120 38 1000 km withcoord
1) 1) "beijing"
   2) 1) "116.23128265142440796"
      2) "40.22076905438526495"
2) 1) "hefei"
   2) 1) "117.30793744325637817"
      2) "31.79321915080526395"
3) 1) "nanjing"
   2) 1) "118.89209836721420288"
      2) "31.32750976275760735"
#查看指定位置的550公里范围内有哪些城市,withdist指定返回城市的’经纬度‘值
127.0.0.1:6379> georadius city 120 38 1000 km withcoord withdist
1) 1) "beijing"
   2) "408.3496"
   3) 1) "116.23128265142440796"
      2) "40.22076905438526495"
2) 1) "hefei"
   2) "732.6371"
   3) 1) "117.30793744325637817"
      2) "31.79321915080526395"
3) 1) "nanjing"
   2) "749.0265"
   3) 1) "118.89209836721420288"
      2) "31.32750976275760735"
#查看指定位置的550公里范围内有哪些城市,withhash指定返回城市的’经纬度‘的hash值
#如果两个城市的hash值越’像‘，证明城市距离越近！
127.0.0.1:6379> georadius city 120 38 1000 km withcoord withdist withhash
1) 1) "beijing"
   2) "408.3496"
   3) (integer) 4069896088584598
   4) 1) "116.23128265142440796"
      2) "40.22076905438526495"
2) 1) "hefei"
   2) "732.6371"
   3) (integer) 4052763834193093
   4) 1) "117.30793744325637817"
      2) "31.79321915080526395"
3) 1) "nanjing"
   2) "749.0265"
   3) (integer) 4054278565840695
   4) 1) "118.89209836721420288"
      2) "31.32750976275760735"
#查看指定位置的550公里范围内有哪些城市,count num 指定返回’num‘个城市数据量
127.0.0.1:6379> georadius city 120 38 1000 km withcoord withdist withhash count 2
1) 1) "beijing"
   2) "408.3496"
   3) (integer) 4069896088584598
   4) 1) "116.23128265142440796"
      2) "40.22076905438526495"
2) 1) "hefei"
   2) "732.6371"
   3) (integer) 4052763834193093
   4) 1) "117.30793744325637817"
      2) "31.79321915080526395"
```

##### ③ georadiusbymember （查找指定元素指定范围内的元素）、geohash （返回经纬度的hash值）、zrange、zrem（使用zset命令操作geo）

```
#查询南京 500公里范围有哪些城市
127.0.0.1:6379> georadiusbymember city nanjing 500 km
1) "hefei"
2) "nanjing"
#查询重庆 1500公里范围有哪些城市
127.0.0.1:6379> georadiusbymember city chongqing 1500 km
1) "lasa"
2) "kunming"
3) "chongqing"
4) "hefei"
5) "nanjing"
6) "beijing"
#返回北京和南京的经纬度的 hash值
127.0.0.1:6379> geohash city beijing nanjing
1) "wx4sucvncn0"
2) "wtsd1qyxfx0"
#查看所有城市name
127.0.0.1:6379> ZRANGE city 0 -1
1) "lasa"
2) "kunming"
3) "chongqing"
4) "hefei"
5) "nanjing"
6) "beijing"
#根据geo中的name删除g元素
127.0.0.1:6379> ZREM city lasa
(integer) 1
#删除成功
127.0.0.1:6379> ZRANGE city 0 -1
1) "kunming"
2) "chongqing"
3) "hefei"
4) "nanjing"
5) "beijing"
```

## 配置文件

![image-20221115203607198](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115203607198.png)

![image-20221115203549707](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115203549707.png)

**主要的配置项**

| 配置项                          | 参数                                                        | 说明                                                         |
| ------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| daemonize                       | no/yes                                                      | 默认为 no，表示 Redis 不是以守护进程的方式运行，通过修改为 yes 启用守护进程。 |
| pidfile                         | 文件路径                                                    | 当 Redis 以守护进程方式运行时，会把进程 pid 写入自定义的文件中。 |
| port                            | 6379                                                        | 指定 Redis 监听端口，默认端口为 6379。                       |
| bind                            | 127.0.0.1                                                   | 绑定的主机地址。                                             |
| timeout                         | 0                                                           | 客户端闲置多长秒后关闭连接，若指定为 0 ，表示不启用该功能。  |
| loglevel                        | notice                                                      | 指定日志记录级别，支持四个级别：debug、verbose、notice、warning，默认为 notice。 |
| logfile                         | stdout                                                      | 日志记录方式，默认为标准输出。                               |
| databases                       | 16                                                          | 设置数据库的数量（0-15个）共16个，Redis 默认选择的是 0 库，可以使用 SELECT 命令来选择使用哪个数据库储存数据。 |
| save[seconds] [changes]         | 可以同时配置三种模式： save 900 1 save 300 10 save 60 10000 | 表示在规定的时间内，执行了规定次数的写入或修改操作，Redis 就会将数据同步到指定的磁盘文件中。比如 900s 内做了一次更改，Redis 就会自动执行数据同步。 |
| rdbcompression                  | yes/no                                                      | 当数据存储至本地数据库时是否要压缩数据，默认为 yes。         |
| dbfilename                      | dump.rdb                                                    | 指定本地存储数据库的文件名，默认为 dump.rdb。                |
| dir                             | ./                                                          | 指定本地数据库存放目录。                                     |
| slaveof <masterip> <masterport> | 主从复制配置选项                                            | 当本机为 slave 服务时，设置 master 服务的 IP 地址及端口，在 Redis 启动时，它会自动与 master 主机进行数据同步。 |
| requirepass                     | foobared 默认关闭                                           | 密码配置项，默认关闭，用于设置 Redis 连接密码。如果配置了连接密码，客户端连接 Redis 时需要通过<password> 密码认证。 |
| maxmemory <bytes>               | 最大内存限制配置项                                          | 指定 Redis 最大内存限制，Redis 在启动时会把数据加载到内存中，达到最大内存后，Redis 会尝试清除已到期或即将到期的 Key，当此方法处理 后，若仍然到达最大内存设置，将无法再进行写入操作，但可以进行读取操作。 |
| appendfilename                  | appendonly.aof                                              | 指定 AOF 持久化时保存数据的文件名，默认为 appendonly.aof。   |
| glueoutputbuf                   | yes                                                         | 设置向客户端应答时，是否把较小的包合并为一个包发送，默认开启状态。 |

## Redis发布和订阅

**是一种消息的通信模式（消息传递系统）**

![image-20221115203937712](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115203937712.png)

### 发布订阅流程

![image-20221115204015851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221115204015851.png)

### 命令行实现发布和订阅演示

> #### 发布消息`PUBLISH`
>
> ✏️语法：PUBLISH channel message 
>  📃说明：将信息message发送到指定的频道channel。
>  🆗返回值：接收到信息message的订阅者数量。
>
> #### 订阅频道消息： `SUBSCRIBE`
>
> ✏️语法：SUBSCRIBE channel [channel ...]
> 📃说明：订阅一个或者多个频道
> 🆗返回值：返回订阅的频道信息和消息内容。

> 1️⃣ 客户端执行订阅指令之后，就会进入订阅状态，之后就只能接收 `subscribe`、`psubscribe`、`unsubscribe`、`punsubscribe` 这四个命令。
>
> 2️⃣ 新订阅的客户端，是**无法收到这个频道之前的消息**，这是因为 Redis 并不会对发布的消息持久化的。



订阅者/等待接收消息

```shell
#订阅channel
127.0.0.1:6379> SUBSCRIBE www.biancheng.net
Reading messages... (press Ctrl-C to quit)
1) "subscribe"
2) "www.biancheng.net"
3) (integer) 1 
```

 发布者/发送消息 `PUBLISH`命令发布

```shell
127.0.0.1:6379> PUBLISH www.biancheng.net "this is website"
(integer) 1
127.0.0.1:6379> PUBLISH www.biancheng.net "hello world"
(integer) 1
127.0.0.1:6379> PUBLISH www.biancheng.net "how are you"
(integer) 1
```

订阅者/成功接收消息

```shell
127.0.0.1:6379> SUBSCRIBE www.biancheng.net
Reading messages... (press Ctrl-C to quit)
1) "subscribe"
2) "www.biancheng.net"
3) (integer) 1
1) "message"
2) "www.biancheng.net"
3) "this is website"
1) "message"
2) "www.biancheng.net"
3) "hello world"
1) "message"
2) "www.biancheng.net"
3) "how are you"
```

> 除了上面的精准发布订阅channel以外的，Redis 还支持**模式匹配**的订阅方式。简单来说，客户端可以订阅一个带 `*` 号的模式，
>
> 如果某些频道的名字与这个模式匹配，那么当其他客户端发送给消息给这些频道时，订阅这个模式的客户端也将会到收到消息
>
> 使用 Redis 订阅模式，我们需要使用一个新的指令 `psubscribe`:
>
> ```shell
> psubscribe pay.*
> ```
>
> 那么一旦有其他客户端往 `pay` 开头的频道，比如 `pay_result_channel`、`pay_xxx`，我们都可以收到消息。
>
> 如果需要取消订阅模式，我们需要使用相应`punsubscribe` 指令，比如取消上面订阅的模式：
>
> ```shell
> punsubscribe pay.*
> ```

### 常用命令

Redis Pub Sub常用命令

> `subscribe channel [channel ...]` 订阅一个或多个频道
>
> `unsubscribe channel` 退订指定频道
>
> `publish channel message` 发送消息
>
> `psubscribe pattern` 订阅指定模式
>
> `punsubscribe pattern` 退订指定模式

| 命令                                        | 说明                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| PSUBSCRIBE pattern [pattern ...]            | 订阅一个或多个符合指定模式的频道。                           |
| PUBSUB subcommand [argument [argument ...]] | 查看发布/订阅系统状态，可选参数 1) channel 返回在线状态的频道。 2) numpat 返回指定模式的订阅者数量。 3) numsub 返回指定频道的订阅者数量。 |
| PUBSUB subcommand [argument [argument ...]] | 将信息发送到指定的频道。                                     |
| PUNSUBSCRIBE [pattern [pattern ...]]        | 退订所有指定模式的频道。                                     |
| SUBSCRIBE channel [channel ...]             | 订阅一个或者多个频道的消息。                                 |
| UNSUBSCRIBE [channel [channel ...]]         | 退订指定的频道。                                             |

```shell
#订阅指定模式的频道，*代表通配符，会匹配所有www开头的频道
127.0.0.1:6379> PSUBSCRIBE www*
Reading messages... (press Ctrl-C to quit)
1) "psubscribe"
2) "www*"
3) (integer) 1
#按ctrl+c退出阻塞状态
^C
C:\Users\Administrator>redis-cli
#查看发布订阅系统状态，返回相应的频道
127.0.0.1:6379> PUBSUB channels
1) "www.biancheng.net"
#退订指定模式的频道
127.0.0.1:6379> PUNSUBSCRIBE www*
1) "punsubscribe"
2) "www*"
3) (integer) 0
#退订指定频道
127.0.0.1:6379> UNSUBSCRIBE www.biancheng.net
1) "unsubscribe"
2) "www.biancheng.net"
3) (integer) 0
```

## Jedis操作Redis

### Java使用Redis

![image-20221116002433987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116002433987.png)

### 模拟验证码发送和验证

```java
package com.eddie.jedis;
import org.junit.Test;
import redis.clients.jedis.Jedis;
import java.util.Random;

/**
 @author EddieZhang
 @create 2022-11-15 23:47
 */
public class JedisDemo1 {
    public static void main(String[] args) {

    }

    @Test
    public void getCodeTest() {
        //获取验证码
        System.out.println(generateCode("19880895770"));
    }

    @Test
    public void verifyCodeTest() {
        //输入验证码进行验证
        System.out.println(verifyCode("19880895770", "66072"));
    }


    /**
     * 随机生成6为的验证码
     * @return
     */
    public static String getCode() {
        Random random = new Random();
        String code = "";
        for (int i = 0; i < 5; i++) {
            code += random.nextInt(10);
        }
        return code;
    }

    /**
     * 每个手机号码每天最多只能验证三次验证码 设置验证码的过期时间为2second
     * @param phoneNumber
     */
    public static String generateCode(String phoneNumber) {
        Jedis jedis = new Jedis("192.168.199.133", 6379);
        //手机发送次数的key
        String countKey = "verifyCode" + phoneNumber + ":count";
        //验证码的key
        String codeKey = "verifyCode" + phoneNumber + ":code";

        //每个手机每天只能发送三次
        String count = jedis.get(countKey);//取手机的发送次数
        if (count == null) {//当获取此手机的count为null时表明尚未验证过 则进行第一次set且设置过期时间为24H
            jedis.setex(countKey, 60 * 60 * 24, "1");
            //随机生成的验证码存放到redis中 并设定expire时效为2second
            jedis.setex(codeKey, 60 * 2, getCode());
            jedis.close();
            return jedis.get(codeKey);
        } else if (Integer.parseInt(count) <= 2) {//当获取到此手机的count为3次以下时 则对count进行incr操作
            jedis.incr(countKey);
            //随机生成的验证码存放到redis中 并设定expire时效为2second
            jedis.setex(codeKey, 60 * 2, getCode());
            jedis.close();
            return jedis.get(codeKey);
        } else {//当获取到此手机的count满3次时 则提示用户无法再进行验证 并且jedis.close()
            return "您当天的三次验证次数满了哦 明天再进行验证吧~";
        }
    }

    /**
     * 验证码的校验
     * @param phoneNumber
     * @param code
     * @return
     */
    public static String verifyCode(String phoneNumber, String code) {
        Jedis jedis = new Jedis("192.168.199.133", 6379);
        if (code.equals(jedis.get("verifyCode" + phoneNumber + ":code"))) {
            jedis.close();
            return "verify success~";
        } else {
            jedis.close();
            return "sorry is wrong! try again";
        }
    }
}
```

## SpringBoot整合Redis★

![image-20221116190736845](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116190736845.png)

![image-20221116190758797](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116190758797.png)

```java
package com.example.config;
import com.fasterxml.jackson.annotation.JsonAutoDetect;
import com.fasterxml.jackson.annotation.PropertyAccessor;
import com.fasterxml.jackson.databind.ObjectMapper;
import org.springframework.cache.CacheManager;
import org.springframework.cache.annotation.CachingConfigurerSupport;
import org.springframework.cache.annotation.EnableCaching;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.cache.RedisCacheConfiguration;
import org.springframework.data.redis.cache.RedisCacheManager;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.serializer.Jackson2JsonRedisSerializer;
import org.springframework.data.redis.serializer.RedisSerializationContext;
import org.springframework.data.redis.serializer.RedisSerializer;
import org.springframework.data.redis.serializer.StringRedisSerializer;
import java.time.Duration;

/**
 @author EddieZhang
 @create 2022-11-16 13:45
 */
@EnableCaching//允许缓存
@Configuration
public class RedisConfig extends CachingConfigurerSupport {

    @Bean()
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory factory) {
        RedisTemplate<String, Object> template = new RedisTemplate<>();
        RedisSerializer<String> redisSerializer = new StringRedisSerializer();
        Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
        ObjectMapper om = new ObjectMapper();
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        om.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
        jackson2JsonRedisSerializer.setObjectMapper(om);
        template.setConnectionFactory(factory);
        //key序列化方式
        template.setKeySerializer(redisSerializer);
        //value序列化
        template.setValueSerializer(jackson2JsonRedisSerializer);
        //value hashmap序列化
        template.setHashValueSerializer(jackson2JsonRedisSerializer);
        return template;
    }

    @Bean
    public CacheManager cacheManager(RedisConnectionFactory factory) {
        RedisSerializer<String> redisSerializer = new StringRedisSerializer();
        Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
        //解决查询缓存转换异常的问题
        ObjectMapper om = new ObjectMapper();
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        om.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
        jackson2JsonRedisSerializer.setObjectMapper(om);
        // 配置序列化（解决乱码的问题）,过期时间600秒
        RedisCacheConfiguration config = RedisCacheConfiguration.defaultCacheConfig()
                .entryTtl(Duration.ofSeconds(600))
                .serializeKeysWith(RedisSerializationContext.SerializationPair.fromSerializer(redisSerializer))
                .serializeValuesWith(RedisSerializationContext.SerializationPair.fromSerializer(jackson2JsonRedisSerializer))
                .disableCachingNullValues();
        RedisCacheManager cacheManager = RedisCacheManager.builder(factory)
                .cacheDefaults(config)
                .build();
        return cacheManager;
    }
}
```

![image-20221116190838128](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116190838128.png)

## Redis的事务操作

> Redis 事务的本质是一组命令的集合。事务支持一次执行多个命令，一个事务中所有命令都会被序列化。在事务执行过程，会按照顺序串行化执行队列中的命令，其他客户端提交的命令请求不会插入到事务执行命令序列中。
>
> **总结说：redis事务就是一次性、顺序性、排他性的执行一个队列中的一系列命令。**

**Redis 事务的目的**是方便用户一次执行多个命令（**串联多个命令**）防止别的命令插队。执行 Redis 事务可分为三个阶段：

- 开始事务【MULTI】
- 命令入队
- 执行事务【EXEC】

### Redis事务特性

Redis 事务

重要特性：

#### 1) 单独的隔离操作

事务中的所有命令都会被序列化，它们将按照顺序执行，并且在执行过的程中，不会被其他客户端发送来的命令打断。

#### 2) 不保证原子性

在 Redis 的事务中，如果存在命令执行失败的情况，那么其他命令依然会被执行，不支持事务回滚机制。

注意：Redis 不支持事务回滚，原因在于 Redis 是一款基于内存的存储系统，其内部结构比较简单，若支持回滚机制，则让其变得冗余，并且损耗性能，这与 Redis 简单、快速的理念不相符合。

使用lua脚本解决（lua脚本（类似于悲观锁的实现）主要解决redis事务（乐观锁）无法保证原子性的问题）

#### 3)没有隔离级别的概念

队列中的命令没有提交之前都不会实际被执行，因为事务提交前任何指令都不会被实际执行

### Redis事务命令

| 命令                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| MULTI               | 开启一个事务                                                 |
| EXEC                | 执行事务中的所有命令                                         |
| DISCARD             | 取消事务。                                                   |
|                     |                                                              |
| WATCH key [key ...] | 在**开启事务之前**用来**监视一个或多个key** 。如果**事务执行时这些 key 被改动过**，那么事**务将被打断**。 |
| UNWATCH             | 取消 WATCH 命令对 key 的监控。                               |

![image-20221116141928493](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116141928493.png)

![image-20221116162757393](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116162757393.png)

![image-20221116162809864](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116162809864.png)

从输入**Multi命令开始**，输入的命令都会依次进入命令队列中，但不会执行，

直到输入**Exec**后，Redis会**将之前的命令队列中的命令依次执行**。

组队的过程中可以**通过discard来放弃组队**

```
127.0.0.1:6379> multi 开启事务
OK
127.0.0.1:6379(TX)> set key1 eddie
QUEUED
127.0.0.1:6379(TX)> set key2 irving
QUEUED
127.0.0.1:6379(TX)> set key3 james
QUEUED
127.0.0.1:6379(TX)> set key4 curry
QUEUED
127.0.0.1:6379(TX)> set key5 durant
QUEUED
127.0.0.1:6379(TX)> exec 执行事务
1) OK
2) OK
3) OK
4) OK
5) OK
127.0.0.1:6379> multi 开启事务
OK
127.0.0.1:6379(TX)> set key1 eddie
QUEUED
127.0.0.1:6379(TX)> set key2 irving
QUEUED
127.0.0.1:6379(TX)> set key3 james
QUEUED
127.0.0.1:6379(TX)> set key4 curry
QUEUED
127.0.0.1:6379(TX)> set key5 durant
QUEUED
127.0.0.1:6379(TX)> discard 取消事务
OK
```

### Redis乐观锁实现

| WATCH key [key ...] | 在开启事务之前用来监视一个或多个key 。如果事务执行时这些 key 被改动过，那么事务将被打断。 |
| ------------------- | ------------------------------------------------------------ |
| UNWATCH             | 取消 WATCH 命令对 key 的监控。                               |

![image-20221116191251821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116191251821.png)

总结：乐观锁和悲观锁的区别。
**悲观锁：** 什么时候都会出问题，所以一直监视着，没有执行当前步骤完成前，不让任何线程执行，十分浪费性能！一般不使用！
**乐观锁：** 只有更新数据的时候去判断一下，在此期间是否有人修改过被监视的这个数据，没有的话正常执行事务，反之执行失败！

![image-20221116191232703](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116191232703.png)

![image-20221116191146824](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116191146824.png)

![image-20221116191155778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116191155778.png)

### 秒杀案例体会redis事务

#### 秒杀案例中会出现的问题

连接超时的问题-----使用连接池解决

超卖的问题-----------使用redis事务解决

库存遗留问题--------使用lua脚本解决（lua脚本（类似于悲观锁的实现）主要解决redis事务（乐观锁）无法保证原子性的问题）

#### 项目案例

![image-20221116233901248](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116233901248.png)

![image-20221116234117079](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234117079.png)

```java
package com.eddie.lua;
import com.eddie.utils.JedisPoolUtil;
import org.slf4j.LoggerFactory;
import redis.clients.jedis.HostAndPort;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisPool;
import java.io.IOException;
import java.util.HashSet;
import java.util.Set;

/**
 @author EddieZhang
 @create 2022-11-16 22:21
 */
public class Script {
    private static final  org.slf4j.Logger logger = LoggerFactory.getLogger(Script.class) ;

    public static void main(String[] args) {
        JedisPool jedispool =  JedisPoolUtil.getJedisPoolInstance();

        Jedis jedis=jedispool.getResource();
        System.out.println(jedis.ping());

        Set<HostAndPort> set=new HashSet<HostAndPort>();

        //	doSecKill("201","sk:0101");
    }

    static String secKillScript ="local userid=KEYS[1];\r\n" +
            "local prodid=KEYS[2];\r\n" +
            "local qtkey='sk:'..prodid..\":qt\";\r\n" +
            "local usersKey='sk:'..prodid..\":usr\";\r\n" +
            "local userExists=redis.call(\"sismember\",usersKey,userid);\r\n" +
            "if tonumber(userExists)==1 then \r\n" +
            "   return 2;\r\n" +
            "end\r\n" +
            "local num= redis.call(\"get\" ,qtkey);\r\n" +
            "if tonumber(num)<=0 then \r\n" +
            "   return 0;\r\n" +
            "else \r\n" +
            "   redis.call(\"decr\",qtkey);\r\n" +
            "   redis.call(\"sadd\",usersKey,userid);\r\n" +
            "end\r\n" +
            "return 1" ;

    static String secKillScript2 =
            "local userExists=redis.call(\"sismember\",\"{sk}:0101:usr\",userid);\r\n" +
                    " return 1";

    public static boolean doSecKill(String uid,String prodid) throws IOException {

        JedisPool jedispool =  JedisPoolUtil.getJedisPoolInstance();
        Jedis jedis=jedispool.getResource();

        //String sha1=  .secKillScript;
        String sha1=  jedis.scriptLoad(secKillScript);
        Object result= jedis.evalsha(sha1, 2, uid,prodid);

        String reString=String.valueOf(result);
        if ("0".equals( reString )  ) {
            System.err.println("已抢空！！");
        }else if("1".equals( reString )  )  {
            System.out.println("抢购成功！！！！");
        }else if("2".equals( reString )  )  {
            System.err.println("该用户已抢过！！");
        }else{
            System.err.println("抢购异常！！");
        }
        jedis.close();
        return true;
    }
}
```

![image-20221116234132560](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234132560.png)

```java
package com.eddie.redis;

import com.eddie.utils.JedisPoolUtil;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.Transaction;

import java.io.IOException;
import java.util.List;

/**
 @author EddieZhang
 @create 2022-11-16 22:18
 */
public class Redis {

    public static void main(String[] args) {
        Jedis jedis =new Jedis("192.168.199.133",6379);
        System.out.println(jedis.ping());
        jedis.close();
    }

    //秒杀过程
    public static boolean doSecKill(String uid,String prodid) throws IOException {
        //1 uid和prodid非空判断
        if(uid == null || prodid == null) {
            return false;
        }

        //2 连接redis
        //Jedis jedis = new Jedis("192.168.44.168",6379);
        //通过连接池得到jedis对象
        JedisPool jedisPoolInstance = JedisPoolUtil.getJedisPoolInstance();
        Jedis jedis = jedisPoolInstance.getResource();

        //3 拼接key
        // 3.1 库存key
        String kcKey = "sk:"+prodid+":qt";
        // 3.2 秒杀成功用户key
        String userKey = "sk:"+prodid+":user";

        //监视库存
        jedis.watch(kcKey);

        //4 获取库存，如果库存null，秒杀还没有开始
        String kc = jedis.get(kcKey);
        if(kc == null) {
            System.out.println("秒杀还没有开始，请等待");
            jedis.close();
            return false;
        }

        // 5 判断用户是否重复秒杀操作
        if(jedis.sismember(userKey, uid)) {
            System.out.println("已经秒杀成功了，不能重复秒杀");
            jedis.close();
            return false;
        }

        //6 判断如果商品数量，库存数量小于1，秒杀结束
        if(Integer.parseInt(kc)<=0) {
            System.out.println("秒杀已经结束了");
            jedis.close();
            return false;
        }

        //7 秒杀过程
        //使用事务
        Transaction multi = jedis.multi();

        //组队操作
        multi.decr(kcKey);
        multi.sadd(userKey,uid);

        //执行
        List<Object> results = multi.exec();

        if(results == null || results.size()==0) {
            System.out.println("秒杀失败了....");
            jedis.close();
            return false;
        }

        //7.1 库存-1
        //jedis.decr(kcKey);
        //7.2 把秒杀成功用户添加清单里面
        //jedis.sadd(userKey,uid);

        System.out.println("秒杀成功了..");
        jedis.close();
        return true;
    }
}

```

![image-20221116234143307](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234143307.png)

```java
package com.eddie.servlet;
import com.eddie.lua.Script;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Random;

/**
 @author EddieZhang
 @create 2022-11-16 22:08
 */
public class Servlet extends HttpServlet {
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String userid = new Random().nextInt(50000) +"" ;
        String prodid =req.getParameter("prodid");

//        boolean isSuccess= Redis.doSecKill(userid,prodid);
        boolean isSuccess= Script.doSecKill(userid,prodid);
        resp.getWriter().print(isSuccess);
    }
}

```

![image-20221116234154713](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234154713.png)

```java
package com.eddie.utils;

import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

/**
 @author EddieZhang
 @create 2022-11-16 22:20
 */
public class JedisPoolUtil {
    private static volatile JedisPool jedisPool = null;

    private JedisPoolUtil() {
    }

    public static JedisPool getJedisPoolInstance() {
        if (null == jedisPool) {
            synchronized (JedisPoolUtil.class) {
                if (null == jedisPool) {
                    JedisPoolConfig poolConfig = new JedisPoolConfig();
                    poolConfig.setMaxTotal(200);
                    poolConfig.setMaxIdle(32);
                    poolConfig.setMaxWaitMillis(100*1000);
                    poolConfig.setBlockWhenExhausted(true);
                    poolConfig.setTestOnBorrow(true);  // ping  PONG

                    jedisPool = new JedisPool(poolConfig, "192.168.199.133", 6379, 60000 );
                }
            }
        }
        return jedisPool;
    }

    public static void release(JedisPool jedisPool, Jedis jedis) {
        if (null != jedis) {
            jedisPool.returnResource(jedis);
        }
    }

}

```

![image-20221116234208013](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234208013.png)

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<body>
<h2>Hello World!</h2>
<h1>秒杀！！！
</h1>
<h2></h2>

<form id="msform" action="/servlet" enctype="application/x-www-form-urlencoded">
    <input type="hidden" id="prodid" name="prodid" value="0101">
    <input type="button"  id="miaosha_btn" name="seckill_btn" value="秒杀点我"/>
</form>
<script  type="text/javascript" src="/script/jquery/jquery-3.1.0.js"></script>
<script  type="text/javascript">
    $(function(){
        $("#miaosha_btn").click(function(){
            var url=$("#msform").attr("action");
            $.post(url,$("#msform").serialize(),function(data){
                if(data=="false"){
                    alert("抢光了" );
                    $("#miaosha_btn").attr("disabled",true);
                }
            } );
        })
    })
</script>
</body>
</html>
```

![image-20221116234220105](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234220105.png)

```xml
<!DOCTYPE web-app PUBLIC
 "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
 "http://java.sun.com/dtd/web-app_2_3.dtd" >

<web-app>
  <display-name>Archetype Created Web Application</display-name>
  <servlet>
    <servlet-name>Servlet</servlet-name>
    <servlet-class>com.eddie.servlet.Servlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>Servlet</servlet-name>
    <url-pattern>/servlet</url-pattern>
  </servlet-mapping>
</web-app>
```

#### 使用AB进行并发测试

![image-20221116234521901](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234521901.png)

![image-20221116234455146](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234455146.png)

![image-20221116234557703](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221116234557703.png)

ab -n 2000 -c 200 -p ~/postfile -T application/x-www-form-urlencoded http://172.17.89.71:8080/servlet

## Redis持久化★

[Redis进阶 - 持久化：RDB和AOF机制详解 | Java 全栈知识体系 (pdai.tech)](https://www.pdai.tech/md/db/nosql-redis/db-redis-x-rdb-aof.html)

[(5条消息) Redis（七）进阶：Redis持久化之RDB和AOF_大鱼等于负的博客-CSDN博客](https://blog.csdn.net/weixin_43829443/article/details/113173849)

#### 简介

Redis是**基于内存**的数据库。

![image-20221117181810508](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221117181810508.png)

#### 服务启动时如何加载持久化数据

> 默认**只开启了RDB则载入RDB文件的数据**。RDB 文件是经过压缩的二进制文件，占用空间很小。RDB 在恢复大数据集时的速度比 AOF 的恢复速度要快。
>
> 
>
> 简单来说，如果**同时启用了 AOF 和 RDB**，Redis 重新启动时，**会使用 AOF 文件来重建数据集**，因为通常来说， **AOF 的数据会更完整**。
>
> 
>
> 而在**引入了混合持久化之后**，使用 AOF 重建数据集时，会**通过文件开头是否为“REDIS”来判断是否为混合持久化**。

![image-20230411151612003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230411151612003.png)

#### RDB持久化(default)

> 在指定的**时间间隔**内将内存中的数据集**快照（snapshot）**写入磁盘。**RDB 文件是是经过压缩的二进制文件，占用空间很小。**
>
> **RDB 在恢复大数据集时的速度比 AOF 的恢复速度要快。**
>
> When using only snapshots for saving data, you must remember that **if a crash were to happen, you d lose any data changed since the last snapshot.**
>
> RDB 持久化的方式是将 Redis 内存中的数据快照写入到磁盘文件中。快照是指 Redis  当前时刻内存中的数据在某个时刻的拷贝，将这个拷贝保存到文件中，这个文件就是 RDB 文件。当 Redis 需要进行持久化时，Redis  将内存中的数据进行快照，然后将快照写入到 RDB 文件中。RDB 文件是一个二进制文件，可以被 Redis 读取和加载到内存中。
>
> 
>
> - **BGSAVE**:■ Any Redis client can initiate a snapshot by calling the BGSAVE command. 
>
>   **Redis will fork**（Redis 中的 fork 操作通常用于 RDB 持久化和 AOF 重写操作。当 Redis 需要进行 RDB 持久化或 AOF 重写时，它会执行 fork 操作来创建一个子进程，不会影响父线程继续处理客户端的请求。但是在 fork 操作中，父进程的整个地址空间都会被复制到子进程中，这样可能会带来一些内存消耗。当数据量很大时会影响整体性能。）
>
>   1. 创建子进程：Redis 使用 C 语言中的 fork 函数来创建子进程，fork 函数会将父进程的整个地址空间完全复制到子进程中，包括代码、数据和堆栈等。在创建子进程之后，父进程和子进程都将拥有相同的程序代码和数据。
>   2. 执行不同的代码：在 fork 操作之后，父进程和子进程会继续执行相同的代码，但是可以通过返回值区分是父进程还是子进程。在 Redis 中，父进程通常会继续处理客户端请求，而子进程则会进行 RDB 持久化或 AOF 重写操作。
>
> - **SAVE**■ A Redis client can also initiate a snapshot by calling the SAVE command, which causes **Redis to stop responding to any/all commands until the snapshot completes.** This command isn’t commonly used, except in situations where we need our data on disk, and either we’re okay waiting for it to complete, or we don’t have enough memory for a BGSAVE.
>
> :o:Linux **fork 子进程采用的是 copy-on-write 的方式**。在 Redis 执行 RDB 持久化期间，如果 client 写入数据很频繁，那么将增加 Redis 占用的内存，最坏情况下，内存的占用将达到原先的2倍。
>
> 当数据量十分庞大时，使用BGSAVE反而效率更低（需要fork），可以根据自身的应用场景取消自动BGSAVE；采用手动SAVE的方式在凌晨冷场时期停止使用缓存，专门进行数据的持久化，反而效率更高。
>
> 
>
> RDB 持久化的优点：
>
> 1. **效率高**：RDB 持久化方式比 AOF 持久化方式的效率更高，因为 RDB 持久化方式只需要进行一次快照，就能够将所有数据保存到磁盘中，而 AOF 持久化方式需要频繁地将操作写入到 AOF 文件中，导致效率低下。
> 2. **文件小**：RDB 文件的大小相对于 AOF 文件来说更小，因为 RDB 文件只保存了 Redis 内存中的数据快照，而 AOF 文件需要保存每一次写操作的详细信息，导致文件比较大。
> 3. **恢复数据方便**：在某些情况下，Redis 需要进行数据恢复，使用 RDB 持久化方式可以方便地将数据从 RDB 文件中恢复。
>
> 
>
> RDB 持久化的不足：
>
> 1. **数据丢失**：上一个快照完成后下一个快照开始前的数据会丢失如果此时Redis出现Failure的话。因为 RDB 持久化方式是将内存中的数据快照写入到磁盘中，如果 Redis 挂掉了并且最后一次持久化的 RDB 文件没有完全写入磁盘，就会导致数据丢失。
> 2. **持久化间隔**：RDB 持久化方式需要设置持久化间隔，间隔时间过长会导致数据丢失，间隔时间过短则会影响 Redis 的性能。
> 3. **写入磁盘的频率**：RDB 持久化方式需要将快照写入磁盘，如果写入磁盘的频率过高，会导致 Redis 的性能降低。

![image-20221117182541480](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221117182541480.png)

![image-20221129163023942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129163023942.png)

![image-20221129230655071](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129230655071.png)

![image-20221129230703297](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129230703297.png)

![image-20221129231202363](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221129231202363.png)

##### 手动触发

手动触发是通过`SAVE`命令或者`BGSAVE`命令将内存数据保存到磁盘文件中。如下所示：

```
127.0.0.1:6379> SAVE
OK
127.0.0.1:6379> BGSAVE
Background saving started
127.0.0.1:6379>  LASTSAVE
(integer) 1611298430
```

上述命令`BGSAVE`从后台执行数据保存操作，其可用性要优于执行 SAVE 命令。

**SAVE 命令会阻塞 Redis 服务器进程**，直到 dump.rdb 文件创建完毕为止，在这个过程中，服务器不能处理任何的命令请求。

**`BGSAVE`命令是非阻塞式的**，所谓非阻塞式，指的是在该命令执行的过程中，并不影响 Redis 服务器处理客户端的其他请求。这是因为 **Redis 服务器会 fork() 一个子进程来进行持久化操作（比如创建新的 dump.rdb 文件）**，而父进程则继续处理客户端请求。当子进程处理完后会向父进程发送一个信号，通知它已经处理完毕。此时，父进程会用新的 dump.rdb 文件覆盖掉原来的旧文件。

**因为`SAVE`命令无需创建子进程**，所以**执行速度要略快于`BGSAVE`命令**，但是`SAVE`命令是阻塞式的，因此其可用性欠佳，如果在数据量较少的情况下，基本上体会不到两个命令的差别，不过仍然**建议您使用 `BGSAVE`命令。**

注意：**LASTSAVE 命令用于查看 BGSAVE 命令是否执行成功。**

##### 自动触发

> If Redis is configured with save lines, such as save 60 10000, Redis will auto- matically trigger a BGSAVE operation if 10,000 writes have occurred within 60 seconds since the last successful save has started (using the configuration option described). When multiple save lines are present, any time one of the
> rules match, a BGSAVE is triggered. 

自动触发策略，是**指 Redis 在指定的时间内，数据发生了多少次变化时**，**会自动执行`BGSAVE`命令**。自动**触发的条件**包含在了 **Redis 的配置文件**中

![image-20221130004943280](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130004943280.png)

上图所示， save m n 的含义是在时间 m 秒内，如果 Redis 数据至少发生了 n 次变化，那么就自动执行`BGSAVE`命令。配置策略说明如下：

- save 900 1 表示在 900 秒内，至少更新了 1 条数据，Redis 自动触发 BGSAVE 命令，将数据保存到硬盘。
- save 300 10 表示在 300 秒内，至少更新了 10 条数据，Redis 自动触 BGSAVE 命令，将数据保存到硬盘。
- save 60 10000 表示 60 秒内，至少更新了 10000 条数据，Redis 自动触发 BGSAVE 命令，将数据保存到硬盘。


只要上述三个条件任意满足一个，服务器就会自动执行`BGSAVE`命令。当然您可以根据实际情况自己调整触发策略。

**注意：每次创建 RDB 文件之后，Redis 服务器为实现自动持久化而设置的时间计数和次数计数就会被清零，并重新开始计数，因此多个策略的效果不会叠加。**

##### 触发机制

1）**save的规则满足的情况下** redis.conf中配置`save m n`，即在m秒内有n次修改时，自动触发bgsave生成rdb文件；

2）**主从复制时**，**从节点要从主节点进行全量复制**时也会触发bgsave操作，生成当时的快照发送到从节点；

3）**执行debug reload命令**重新加载redis时也会触发bgsave操作；

4）退出Redis，也会触发rdb规则 默认情况下**执行shutdown命令时**，如果没有开启aof持久化，那么也会触发bgsave操作；

5）**执行flushall命令**，也会触发rdb规则

##### 恢复rdb文件

只需将备份的rdb文件放在我们的redis启动目录即可，Redis启动的时候会自动检查dump.rdb文件并恢复其中的数据！

```
127.0.0.1:6379> config get dir
1) "dir"
2) "/usr/local/bin"  # 如果在这个目录下存在 dump.rdb 文件，启动就会自动恢复其中的数据
```

##### 优缺点

> **优点**：
> 1、适合大规模的数据恢复！
> 2、对数据的完整性要求不高！
> **缺点**：
> 1、需要一定的时间间隔进程操作！如果redis意外宕机了，这个最后一次修改数据就没有的了！
> 2、fork进程的时候，会占用一定的内容空间！
>
> ⑥总结：
> Redis会单独创建（fork）一个子进程来进行持久化，会先将数据写入到一个临时文件中，待持久化过程都结束了，再用这个临时文件替换上次持久化好的文件。整个过程中，主进程是不进行任何IO操作的。
> 这就确保了极高的性能。如果需要进行大规模数据的恢复，且对于数据恢复的完整性不是非常敏感，那RDB方式要比AOF方式更加的高效。RDB的缺点是最后一次持久化后的数据可能丢失。我们默认的就是RDB，一般情况下不需要修改这个配置！
>
> 在生产环境我们会将这个文件进行备份！
>

#### AOF（Append Only File）

> AOF 持久化会将 Redis 服务器**执行的每个写命令都追加到 AOF 文件中**。当 Redis 需要进行数据恢复时，只需要将 AOF 文件中的写命令重新执行一遍，就可以完全恢复 Redis 中的数据。
>
> 
>
> Redis 支持三种appendfsync刷盘策略（**为了提升写入效率**，**不会将内容直接写入到磁盘**中，而是**将其放到一个内存缓存区（aof_buf）中**）
>
> - always：每次写操作后都会执行 fsync() 将写入的数据立即写入磁盘，保证数据的安全性，但会对性能产生影响。
> - everysec(默认)：每秒钟执行一次 fsync()，在保证数据安全的同时尽可能减少 fsync() 的调用，提高性能。
> - no：将 fsync() 交给操作系统来处理，无法保证数据的完整性，但可以获得最好的性能。
>
> 
>
> AOF 持久化的优点
>
> - 数据安全：AOF 持久化能够确保 Redis 服务器在重启时能够完全恢复数据，避免数据丢失的风险。
> - 高可靠性：AOF 持久化记录了每个写命令，即使 Redis 服务器意外宕机，也可以通过 AOF 文件中的命令来恢复数据。
> - 灵活性：AOF 持久化可以根据需要选择三种不同的持久化方式，以平衡数据安全性和性能之间的关系。
> - 兼容性：AOF 持久化不会影响 Redis 的读写性能，因此可以与 Redis 的其他功能兼容。
>
> 
>
> AOF 持久化的不足
>
> - 文件体积：由于 AOF 文件需要记录每个写命令，因此可能会比 RDB 文件更大，导致存储空间浪费。
> - 性能问题：在 always 模式下，每次写入操作都需要执行 fsync()，这会对性能产生影响。即使使用 everysec 模式，仍然会有一定的 fsync() 延迟，可能会导致数据的丢失。
> - 重写问题：AOF 文件在不断追加写命令时，可能会变得很大，影响性能。为了解决这个问题，Redis 提供了 AOF 重写功能，可以对 AOF 文件进行压缩。但是，AOF 重写也会对性能产生影响（）。
>   - REWRITEAOF：进行 AOF 重写，但是会阻塞主进程，服务器将无法处理客户端发来的命令请求，通常不会直接使用该命令。
>   - BGREWRITEAOF：fork 子进程来进行 AOF 重写，阻塞只会发生在 fork 子进程的时候，之后主进程可以正常处理请求。



> 需要手动开启；可以通过配置：appendonly yes 开启
>
> **记录所有的写操作到.aof文件中**（保存 Redis 服务器所执行的所有写操作命令来记录数据库状态，服务器启动时，通过重新执行这些命令来还原数据集。）
>
> 每当有一个**修改数据库的命令**被执行时，服务器就**将命令写入到 appendonly.aof 文件中**，该文件**存储了服务器执行过的所有修改命令**，因此，**只要服务器重新执行一次 .aof 文件**，就可以实现**还原数据**的目的，这个过程被形象地称之为**“命令重演”**。
>
> **若RDB和AOF同时开启 系统会优先读.aof文件**

![image-20221130005653537](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130005653537.png)

##### 写入机制

**Redis 在收到**客户端**修改命令**后，先**进行相应的校验**，如果没问题，就**立即将该命令存追加到 .aof 文件中**，也就是**先存到磁盘中**，然后**服务器再执行命令**。这样就算遇到了突发的宕机情况情况，也只需将存储到 .aof 文件中的命令，进行一次“命令重演”就可以恢复到宕机前的状态。

在上述执行过程中，有一个很重要的环节就是命令的写入，这是一个 IO 操作。**为了提升写入效率**，它**不会将内容直接写入到磁盘**中，而是**将其放到一个内存缓存区（buffer）中**，等到**缓存区被填满时才真正将缓存区中的内容写入到磁盘里**。

> Linux 操作系统中为了提升性能，使用了页缓存（page cache）。当我们将 aof_buf 的内容写到磁盘上时，此时数据并没有真正的落盘，而是在 page cache 中，为了将 page cache 中的数据真正落盘，需要执行  fsync / fdatasync 命令来强制刷盘。这边的文件同步做的就是刷盘操作，或者叫文件刷盘可能更容易理解一些。

##### 重写机制★

> Redis 在长期运行的过程中，aof 文件会越变越长。如果机器宕机重启，“重演”整个 aof 文件会非常耗时，导致长时间 Redis 无法对外提供服务。因此就需要对 aof 文件做一下“瘦身”运动。
>
> 为了让 **aof 文件的大小控制在合理的范围内**，Redis 提供了 AOF 重写机制，手动执行`BGREWRITEAOF`命令，开始重写 aof 文件，如下所示：
>
> - REWRITEAOF：进行 AOF 重写，但是会阻塞主进程，服务器将无法处理客户端发来的命令请求，通常不会直接使用该命令。
>
> 
>
> - **BGREWRITEAOF：fork 子进程来进行 AOF 重写，阻塞只会发生在 fork 子进程的时候，之后主进程可以正常处理请求。**
>

```
127.0.0.1:6379> BGREWRITEAOF
Background append only file rewriting started
```



通过上述操作后，服务器会生成一个新的 aof 文件，该文件具有以下特点：

- 新的 aof 文件记录的数据库数据和原 aof 文件记录的数据库**数据完全一致**；
- 新的 aof 文件会使用**尽可能少的命令来记录数据库数据**，因此新的 aof 文件的**体积会小**很多；
- **AOF 重写期间**，服务器**不会被阻塞**，它可以正常处理客户端发送的命令。

![image-20221130010336666](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130010336666.png)

```
# 自动触发AOF重写
auto-aof-rewrite-percentage 100  #写入百分比
auto-aof-rewrite-min-size 64mb  #写入的文件最大值是多少，一般在实际工作中我们会将其设置为5gb左右！
```

###### AOF 后台重写存在的数据不一致问题

![image-20230412011707264](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230412011707264.png)

> Redis 引入了 **AOF 重写缓冲区（aof_rewrite_buf_blocks）**
>
> 
>
> 这个**缓冲区在服务器创建子进程之后开始使用**，当 Redis 服务器执行完一个写命令之后，它会同时将这个写命令追加到 AOF 缓冲区和 AOF 重写缓冲区。
>
> 1、**现有 AOF 文件的处理工作会如常进行**。这样即使在重写的中途发生停机，现有的 AOF 文件也还是安全的。
>
> 2、从创建子进程开始，也就是 **AOF 重写开始，服务器执行的所有写命令**会被**记录到 AOF 重写缓冲区里面**。
>
> 
>
> **当子进程完成 AOF 重写工作后**，**父进程（这一过程会导致主进程无法处理请求）**会在 serverCron 中检测到子进程已经重写结束，则会执行以下工作：
>
> 1、**将 AOF 重写缓冲区中的所有内容写入到新 AOF 文件中**，这时新 AOF 文件所保存的数据库状态将和服务器当前的数据库状态一致。
>
> 2、**对新的 AOF 文件进行改名，原子的覆盖现有的 AOF 文件**，完成新旧两个 AOF 文件的替换。
>
> 
>
> **之后，父进程就可以继续接受命令请求**了。

###### AOF 重写缓冲区内容过多

> **将 AOF 重写缓冲区的内容追加到新 AOF 文件**的工作是**由主进程完成**的，所以**这一过程会导致主进程无法处理请求**，如果**内容过多**，可能会**使得阻塞时间过长**，显然是无法接受的。
>
> 
>
> Redis 中已经针对这种情况进行了优化：
>
> 1、在**进行 AOF 后台重写时**，Redis 会**创建一组用于父子进程间通信的管道**，同时会**新增一个文件事件**，该文件事件会将写入 AOF 重写缓冲区的内容通过该管道发送到子进程。
>
> 2、在重写结束后，**子进程会通过该管道尽量从父进程读取更多的数据**，每次等待可读取事件1ms，如果一直能读取到数据，则这个过程最多执行1000次，也就是1秒。如果连续20次没有读取到数据，则结束这个过程。
>
> 
>
> 通过这些优化，**Redis 尽量让 AOF 重写缓冲区的内容更少，以减少主进程阻塞的时间。**

###### 重写机制的核心流程

![image-20230411150742833](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230411150742833.png)

##### 修复aof文件

```
redis-check-aof --fix appendonly.aof  #修复appendonly.aof文件
```

##### AOF策略配置

```
# appendfsync always # 每次修改都会 sync。消耗性能 
appendfsync everysec # 每秒执行一次 sync，可能会丢失这1s的数据！ # appendfsync no # 不执行 sync，这个时候操作系统自己同步数据，速度最快！

appendfilename "appendonly.aof" # 持久化的文件的名字
appendonly no # 默认是不开启aof模式的，默认是使用rdb方式持久化的，在大部分所有的情况下， rdb完全够用！
```

![image-20221130010521121](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130010521121.png)

- Always：服务器每写入一个命令，就调用一次 fsync 函数，将缓冲区里面的命令写入到硬盘。这种模式下，服务器出现故障，也不会丢失任何已经成功执行的命令数据，但是其执行速度较慢；
- Everysec（默认）：服务器每一秒调用一次 fsync 函数，将缓冲区里面的命令写入到硬盘。这种模式下，服务器出现故障，最多只丢失一秒钟内的执行的命令数据，通常都使用它作为 AOF 配置策略；
- No：服务器不主动调用 fsync 函数，由操作系统决定何时将缓冲区里面的命令写入到硬盘。这种模式下，服务器遭遇意外停机时，丢失命令的数量是不确定的，所以这种策略，不确定性较大，不安全。

注意：**Linux 系统**的 **fsync() 函数**可以**将指定文件的内容从内核缓存刷到硬盘中。**

由于是 fsync 是磁盘 IO 操作，所以它很慢！如果 Redis 执行一条指令就要 fsync 一次（Always），那么 Redis 高性能将严重受到影响。

**在生产环境的服务器中，Redis 通常是每隔 1s 左右执行一次 fsync 操作（ Everysec），这样既保持了高性能，也让数据尽可能的少丢失。**

最后一种策略（No），让操作系统来决定何时将数据同步到磁盘，这种策略存在许多不确定性，所以不建议使用。

从三种策略的运行速度来看，Always 的速度最慢，而 Everysec 和 No 都很快。

#### 混合持久化

> 混合持久化本质是**通过 AOF 后台重写（bgrewriteaof 命令）完成**的.
>
> 不同的是当开启混合持久化时，fork 出的子进程先将当前全量数据以 RDB  方式写入新的 AOF 文件，然后再将 AOF 重写缓冲区（aof_rewrite_buf_blocks）的增量命令以 AOF  方式写入到文件，写入完成后通知主进程将新的含有 RDB 格式和 AOF 格式的 AOF 文件替换旧的的 AOF 文件。
>
> 
>
> 描述：混合持久化并不是一种全新的持久化方式，而是对已有方式的优化。**混合持久化只发生于 AOF 重写过程**。使用了混合持久化，
>
> **重写后的新 AOF 文件前半段是 RDB 格式的全量数据，后半段是 AOF 格式的增量数据**。
>
> 
>
> 整体格式为：[RDB file --- AOF tail]
>
> 
>
> 开启：混合持久化的配置参数为 aof-use-rdb-preamble，配置为 yes 时开启混合持久化，在 redis 4 刚引入时，默认是关闭混合持久化的，但是在 redis 5 中默认已经打开了。
>
> 
>
> 关闭：使用 aof-use-rdb-preamble no 配置即可关闭混合持久化。

#### AOF和RDB★

| RDB持久化                                                    | AOF持久化                                    |
| ------------------------------------------------------------ | -------------------------------------------- |
| 全量备份，一次保存整个数据库。                               | 增量备份，一次只保存一个修改数据库的命令。   |
| 每次执行持久化操作的间隔时间较长。                           | 保存的间隔默认为一秒钟（Everysec）           |
| 数据保存为二进制格式，其还原速度快。                         | 使用文本格式还原数据，所以数据还原速度一般。 |
| 执行 SAVE 命令时会阻塞服务器，但手动或者自动触发的 BGSAVE 不会阻塞服务器 | AOF持久化无论何时都不会阻塞服务器。          |

如果进行数据恢复时，**既有 dump.rdb文件，又有 appendonly.aof 文件**，应该**先通过 appendonly.aof 恢复数据**，这能**最大程度地保证数据的安全性**。



> **混合使用 AOF 日志和内存快照**的方法。
> 简单来说，内存快照以一定的频率执行，在两次快照之间，使用 AOF 日志记录这期间的所有命令操作。
>
> 这样一来，快照不用很频繁地执行，这就避免了频繁 fork 对主线程的影响。而且，AOF 日志也只用记录两次快照间的操作，也就是说，不需要记录所有操作了，因此，就不会出现文件过大的情况了，也可以避免重写开销。
>
> 如下图所示，T1 和 T2 时刻的修改，用 AOF 日志记录，等到第二次做全量快照时，就可以清空 AOF 日志，因为此时的修改都已经记录到快照中了，恢复时就不再用日志了。



![image-20230328105232398](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230328105232398.png)

#### **总结**：

> 1、RDB 持久化方式能够在指定的时间间隔内对你的数据进行快照存储
> 2、AOF 持久化方式记录每次对服务器写的操作，当服务器重启的时候会重新执行这些命令来恢复原始的数据，AOF命令以Redis 协议追加保存每次写的操作到文件末尾，Redis还能对AOF文件进行后台重写，使得AOF文件的体积不至于过大。
> 3、**只做缓存**，如果你**只希望你的数据在服务器运行的时候存在**，你也**可以不使用任何持久化**
> 4、**同时开启两种持久化方式（RDB快照的形式进行备份保障，同时AOF保障最后一次快照后以及再一次快照开始前的写操作）**
>
> 
>
> 在这种情况下，**当redis重启的时候会优先载入AOF文件来恢复原始的数据**，因为在通常情况下**AOF文件保存的数据集要比RDB文件保存的数据集要完整**。
> RDB 的数据不实时，同时使用两者时服务器重启也只会找AOF文件，那要不要只使用AOF呢？建议不要，因为RDB更适合用于备份数据库（AOF在不断变化不好备份），快速重启，而且不会有AOF可能潜在的Bug，留着作为一个万一的手段。
>
> 因为RDB文件只用作后备用途，**建议只在Slave上持久化RDB文件**，而且只要**15分钟备份一次就够了**，**只保留 save 900 1 这条规则**。
> 如果Enable AOF ，好处是在最恶劣情况下也只会丢失不超过两秒数据，启动脚本较简单只load自己的AOF文件就可以了，代价一是带来了持续的IO，二是AOF rewrite 的最后将 rewrite 过程中产生的新数据写到新文件造成的阻塞几乎是不可避免的。只要硬盘许可，应该**尽量减少AOF rewrite的频率**，AOF重写的基础大小**默认值64M太小了，可以设到5G以上**，默认超过原大小100%大小重写可以改到适当的数值。
> 如果不Enable AOF ，仅靠 Master-Slave Repllcation 实现高可用性也可以，能省掉一大笔IO，也减少了rewrite时带来的系统波动。代价是如果Master/Slave 同时倒掉，会丢失十几分钟的数据，启动脚本也要比较两个 Master/Slave 中的 RDB文件，载入较新的那个，微博就是这种架构。

## Redis主从复制

![image-20221117194814622](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221117194814622.png)

![image-20221117194944449](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221117194944449.png)

**查看主从信息**

```
info replication
```

**复制原理：**
Slave 启动成功连接到 master 后会发送一个sync同步命令

Master 接到命令，启动后台的存盘进程，同时收集所有接收到的用于修改数据集命令，在后台进程执行完毕之后，master将传送整个数据文件到slave，并完成一次完全同步。

**全量复制：**而slave服务在接收到数据库文件数据后，将其存盘并加载到内存中。

增量复制： Master 继续将新的所有收集到的修改命令依次传给slave，完成同步但是只要是重新连接master，一次完全同步（全量复制）将被自动执行！ 我们的数据一定可以在从机中看到！


**可以看出主从模式下，数据的同步是自动完成的，这个数据同步的过程，又称为全量复制。**

### **使用命令实现**

使用命令在服务端搭建主从模式，其语法格式如下：

```
redis-server --port <slave-port> --slaveof <master-ip> <master-port>
```

执行以下命令：

```
#开启开启一个port为6300的从机，它依赖的主机port=6379
C:\Users\Administrator> redis-server --port 6300 --slaveof 127.0.0.1 6379
```

### 修改配置文件实现

每个 Redis 服务器都有一个与其对应的配置文件，通过修改该配置文件也可以实现主从模式，下面在 Ubuntu 环境下对该方法进行演练。

新建 redis_6302.conf 文件,并添加以下配置信息：

```
slaveof 127.0.0.1 6379 #指定主机的ip与port
port 6302 #指定从机的端口
```

启动 Redis 服务器，执行以下命令：

```
$ redis-server redis_6302.conf
```

客户端连接服务器，并进行简单测试。执行以下命令：

```
$ redis-cli -p 6302
127.0.0.1:6300> HSET user:username biangcheng
#写入失败
(error) READONLY You can't write against a read only slave.
```

提示：通过命令搭建主从模式，简单又快捷，所以不建议您使用修改配置文件的方法。

### 一主多从

**若主机宕机**不影响通过从机的读数据；此时**主机重启仍然为master**

此时**从机可以通过slaveof no one 指令成为master**；**主机重启后成为新主机的slave**



**若从机宕机**；由于是**命令行一次性指定** 因此**需要重新为从机配置master**

![image-20221130102638809](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130102638809.png)

复制多个配置文件

使用不同的配置文件启动不同的服务

![image-20221130101522355](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130101522355.png)

指定.rdb文件

![image-20221130101638981](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130101638981.png)

命令行配置（一次性配置）

```
#开启开启一个port为6380的从机，它依赖的主机port=6379
C:\Users\Administrator> redis-server --port 6380 --slaveof 127.0.0.1 6379

#开启开启一个port为6381的从机，它依赖的主机port=6379
C:\Users\Administrator> redis-server --port 6381 --slaveof 127.0.0.1 6379
```



配置文件配置

![image-20221130100728384](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130100728384.png)



### 薪火相传

![image-20221130100942224](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130100942224.png)

### 反客为主

如果主机断开了连接，我们可以使用

```java
 SLAVEOF no one
```

**让自己变成主机！**其他的节点就可以手动连接到最新的这个主节点（手动）！如果这个时候原来的**老大修复了**，那就**重新连接成为小弟！！**

**注意哦！！**
老大没挂，也可以使用这个命令直接让自己变成老大！

### 主从模式不足

主从模式并不完美，它也存在许多不足之处，下面做了简单地总结：

- **1)** Redis 主从模式不具备自动容错和恢复功能，如果主节点宕机，Redis 集群将无法工作，此时需要人为干预，将从节点提升为主节点。
- **2)** 如果主机宕机前有一部分数据未能及时同步到从机，即使切换主机后也会造成数据不一致的问题，从而降低了系统的可用性。
- **3)** 因为只有一个主节点，所以其写入能力和存储能力都受到一定程度地限制。
- **4)** 在进行数据全量同步时，若同步的数据量较大可能会造卡顿的现象。

## Sentinel哨兵模式

在 Redis 主从复制模式中，因为系统不具备自动恢复的功能，所以**当主服务器（master）宕机后**，**需要手动把一台从服务器（slave）切换为主服务器**。在这个过程中，不仅需要人为干预，而且还会造成一段时间内服务器处于不可用状态，同时数据安全性也得不到保障，因此主从模式的可用性较低，不适用于线上生产环境。

Redis 官方推荐一种**高可用方案**，也就是 **Redis Sentinel 哨兵模式**，它**弥补了主从模式的不足**。Sentinel 通过监控的方式获取主机的工作状态是否正常，**当主机发生故障时**， **Sentinel 会自动进行 Failover（即故障转移），并将其监控的从机提升主服务器（master），从而保证了系统的高可用性**。

![image-20221130111147964](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130111147964.png)

### 哨兵模式原理

Sentinel 负责监控主从节点的“健康”状态。当主节点挂掉时，自动选择一个最优的从节点切换为主节点。客户端来连接 Redis 集群时，会首先连接 Sentinel，通过 Sentinel 来查询主节点的地址，然后再去连接主节点进行数据交互。当主节点发生故障时，客户端会重新向 Sentinel 要地址，Sentinel 会将最新的主节点地址告诉客户端。因此应用程序无需重启即可自动完成主从节点切换。

![image-20221130014156595](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130014156595.png)

#### 1) 主观下线

主观下线，适用于主服务器和从服务器。如果在规定的时间内(配置参数：down-after-milliseconds)，Sentinel 节点没有收到目标服务器的有效回复，则判定该服务器为“主观下线”。比如 Sentinel1 向主服务发送了`PING`命令，在规定时间内没收到主服务器`PONG`回复，则 Sentinel1 判定主服务器为“主观下线”。

#### 2) 客观下线

客观下线，只适用于主服务器。 Sentinel1 发现主服务器出现了故障，它会通过相应的命令，询问其它 Sentinel 节点对主服务器的状态判断。如果超过半数以上的 Sentinel 节点认为主服务器 down 掉，则 Sentinel1 节点判定主服务为“客观下线”。

#### 3) 投票选举

投票选举，所有 Sentinel 节点会通过投票机制，按照谁发现谁去处理的原则，选举 Sentinel1 为领头节点去做 Failover（故障转移）操作。Sentinel1 节点则按照一定的规则在所有从节点中选择一个最优的作为主服务器，然后通过发布订功能通知其余的从节点（slave）更改配置文件，跟随新上任的主服务器（master）。至此就完成了主从切换的操作。

### 配置哨兵模式

#### 1) 安装sentinel

Sentinel 需要作为插件单独安装，安装方式如下：

```
sudo apt install redis-sentinel
```

#### 2) 搭建主从模式

接下来，在本地环境使用主从模式搭建一个拥有三台服务器的 Redis 集群，命令如下所示：

```
启动6379的redis服务器作为master主机:
sudo /etc/init.d/redis-server start

启动6380的redis服务器，设置为6379的slave:
redis-server --port 6380
$ redis-cli -p 6380
127.0.0.1:6380> slaveof 127.0.0.1 6379
OK

启动6381的redis服务器，设置为6379的salve
redis-server --port 6381
$ redis-cli -p 6381
127.0.0.1:6381> slaveof 127.0.0.1 6379
```

#### 3) 配置sentinel哨兵

首先新建 sentinel.conf 文件，并对其进行配置，如下所示：

```
port 26379
Sentinel monitor biancheng 127.0.0.1 6379 1
```

配置文件说明如下：

```
port 26379 #sentinel监听端口，默认是26379，可以更改
sentinel monitor <master-name> <ip> <redis-port> <quorum>
```

第二个配置项表示：让 sentinel 去监控一个地址为 ip:port 的主服务器，这里的 master-name 可以自定义；<quorum> 是一个数字，表示当有多少个 sentinel 认为主服务器宕机时，它才算真正的宕机掉，通常数量为半数或半数以上才会认为主机已经宕机，<quorum> 需要根据 sentinel 的数量设置。

#### 4) 启动sentienl哨兵

```
方式一: 
redis-sentinel sentinel.conf
方式二: 
redis-server sentinel.conf --sentinel
```

#### 4）测试

**搭建一主多从服务器**

![image-20221130105931861](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130105931861.png)

**配置和启动sentinel**

![image-20221130105809397](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130105809397.png)

**主机宕机测试**

![image-20221130105648611](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130105648611.png)

![image-20221130105636061](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130105636061.png)

![image-20221130105721091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130105721091.png)

### sentinel.conf配置项

如果您想开启多个哨兵，只需配置要多个 sentinel.conf 文件即可，一个配置文件开启一个。

下面对 Sentinel 配置文件的其他配置项做简单说明：

| 配置项                                      | 参数类型                   | 说明                                                         |
| ------------------------------------------- | -------------------------- | ------------------------------------------------------------ |
| dir                                         | 文件目录                   | 哨兵进程服务的文件存放目录，默认为 /tmp。                    |
| port                                        | 端口号                     | 启动哨兵的进程端口号，默认为 26379。                         |
| sentinel down-after-milliseconds            | <服务名称><毫秒数(整数)>   | 在指定的毫秒数内，若主节点没有应答哨兵的 PING 命令，此时哨兵认为服务器主观下线，默认时间为 30 秒。 |
| sentinel parallel-syncs                     | <服务名称><服务器数(整数)> | 指定可以有多少个 Redis 服务同步新的主机，一般而言，这个数字越小同步时间越长，而越大，则对网络资源要求就越高。 |
| sentinel failover-timeout                   | <服务名称><毫秒数(整数)>   | 指定故障转移允许的毫秒数，若超过这个时间，就认为故障转移执行失败，默认为 3 分钟。 |
| sentinel notification-script                | <服务名称><脚本路径>       | 脚本通知，配置当某一事件发生时所需要执行的脚本，可以通过脚本来通知管理员，例如当系统运行不正常时发邮件通知相关人员。 |
| sentinel auth-pass <master-name> <password> | <服务器名称><密码>         | 若主服务器设置了密码，则哨兵必须也配置密码，否则哨兵无法对主从服务器进行监控。该密码与主服务器密码相同。 |

```
# Example sentinel.conf 

# 哨兵sentinel实例运行的端口 默认26379 
port 26379 

# 哨兵sentinel的工作目录 
dir /tmp 

# 哨兵sentinel监控的redis主节点的 ip port 
# master-name 可以自己命名的主节点名字 只能由字母A-z、数字0-9 、这三个字符".-_"组成。 
# quorum 配置多少个sentinel哨兵统一认为master主节点失联 那么这时客观上认为主节点失联了 
# sentinel monitor <master-name> <ip> <redis-port> <quorum> sentinel monitor mymaster 127.0.0.1 6379 2 

# 当在Redis实例中开启了requirepass foobared 授权密码 这样所有连接Redis实例的客户端都要提供 密码
# 设置哨兵sentinel 连接主从的密码 注意必须为主从设置一样的验证密码 
# sentinel auth-pass <master-name> <password> 
sentinel auth-pass mymaster MySUPER--secret-0123passw0rd 

# 指定多少毫秒之后 主节点没有应答哨兵sentinel 此时 哨兵主观上认为主节点下线 默认30秒 
# sentinel down-after-milliseconds <master-name> <milliseconds> 
sentinel down-after-milliseconds mymaster 30000 

# 这个配置项指定了在发生failover主备切换时最多可以有多少个slave同时对新的master进行 同步
#这个数字越小，完成failover所需的时间就越长，
# 但是如果这个数字越大，就意味着越 多的slave因为replication而不可用。 
#可以通过将这个值设为 1 来保证每次只有一个slave 处于不能处理命令请求的状态。 
# sentinel parallel-syncs <master-name> <numslaves> 
sentinel parallel-syncs mymaster 1 


# 故障转移的超时时间 failover-timeout 可以用在以下这些方面： 
#1. 同一个sentinel对同一个master两次failover之间的间隔时间。 
#2. 当一个slave从一个错误的master那里同步数据开始计算时间。直到slave被纠正为向正确的master那 里同步数据时。 
#3.当想要取消一个正在进行的failover所需要的时间。 
#4.当进行failover时，配置所有slaves指向新的master所需的最大时间。不过，即使过了这个超时， slaves依然会被正确配置为指向master，但是就不按parallel-syncs所配置的规则来了 
# 默认三分钟 # sentinel failover-timeout <master-name> 
sentinel failover-timeout mymaster 180000 


# SCRIPTS EXECUTION #配置当某一事件发生时所需要执行的脚本，可以通过脚本来通知管理员，例如当系统运行不正常时发邮件通知 相关人员。 
#对于脚本的运行结果有以下规则： 
#若脚本执行后返回1，那么该脚本稍后将会被再次执行，重复次数目前默认为10 #若脚本执行后返回2，或者比2更高的一个返回值，脚本将不会重复执行。 
#如果脚本在执行过程中由于收到系统中断信号被终止了，则同返回值为1时的行为相同。 
#一个脚本的最大执行时间为60s，如果超过这个时间，脚本将会被一个SIGKILL信号终止，之后重新执行。 
#通知型脚本:当sentinel有任何警告级别的事件发生时（比如说redis实例的主观失效和客观失效等等）， 将会去调用这个脚本，这时这个脚本应该通过邮件，SMS等方式去通知系统管理员关于系统不正常运行的信 息。调用该脚本时，将传给脚本两个参数，一个是事件的类型，一个是事件的描述。如果sentinel.conf配 置文件中配置了这个脚本路径，那么必须保证这个脚本存在于这个路径，并且是可执行的，否则sentinel无 法正常启动成功。 
#通知脚本 
# shell编程 
# sentinel notification-script <master-name> <script-path> 
sentinel notification-script mymaster /var/redis/notify.sh 


# 客户端重新配置主节点参数脚本 
# 当一个master由于failover而发生改变时，这个脚本将会被调用，通知相关的客户端关于master地址已 经发生改变的信息。 
# 以下参数将会在调用脚本时传给脚本: 
# <master-name> <role> <state> <from-ip> <from-port> <to-ip> <to-port> 
# 目前<state>总是“failover”, 
# <role>是“leader”或者“observer”中的一个。 
# 参数 from-ip, from-port, to-ip, to-port是用来和旧的master和新的master(即旧的slave)通 信的
# 这个脚本应该是通用的，能被多次调用，不是针对性的。 
# sentinel client-reconfig-script <master-name> <script-path> 
sentinel client-reconfig-script mymaster /var/redis/reconfig.sh 
# 一般都是由运维来配置！
```

## Redis Cluster★

https://redis.io/docs/reference/cluster-spec/

https://juejin.cn/post/6949832776224866340#heading-11

> Redis Cluster 通过**分片（Sharding）**来进行数据管理；提供**主从复制(Master-Slave Replication)**，**故障转移(Failover)**等开箱即用的功能，
>
> **保障在Redis大数据量缓存下的服务高可用**。
>
> - **分布式存储：**
>   - Redis Cluster 将数据分散存储在多个节点中，可以有效地扩展数据存储能力。同时，它也可以自动地将**数据分片(哈希槽分片算法)**到不同的节点上，实现数据的负载均衡和高效访问。
> - **自动容错：**
>   - Redis Cluster 支持**主从复制**和**故障转移**，可以在**节点故障或网络异常时自动切换到备用节点**，保证系统的高可用性。
> - **节点间通信：**
>   - Redis Cluster **节点之间使用二进制协议通信(Gossip)**，可以高效地传输数据。同时，它也支持**节点间的握手和心跳机制**，保证节点之间的可靠通信。
> - **负载均衡：**
>   - Redis Cluster 可以自动将数据分配到不同的节点上，实现负载均衡。同时，它还可以使用**哈希槽分片算法**，确保**每个节点上的数据均匀分布，避免数据倾斜**。
> - **可扩展性：**
>   - Redis Cluster **支持动态添加和删除节点**，可以根据需求**灵活地扩展集群的规模和性能**。

![image-20230409143517003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409143517003.png)

![image-20230409143917916](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409143917916.png)

![image-20230409144150286](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409144150286.png)

![image-20230409144136619](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409144136619.png)

### Create a Redis Cluster

https://redis.io/docs/management/scaling/#create-a-redis-cluster

#### manually

Now that we have a number of instances running, you need to create  your cluster by writing some meaningful configuration to the nodes.

You can configure and execute individual instances manually or use the create-cluster script. Let's go over how you do it manually.

To create the cluster, run:

```
redis-cli --cluster create 127.0.0.1:7000 127.0.0.1:7001 \
127.0.0.1:7002 127.0.0.1:7003 127.0.0.1:7004 127.0.0.1:7005 \
--cluster-replicas 1
```

The command used here is **create**, since we want to create a new cluster. The option `--cluster-replicas 1` means that we want a replica for every master created.

The other arguments are the list of addresses of the instances I want to use to create the new cluster.

`redis-cli` will propose a configuration. Accept the proposed configuration by typing **yes**. The cluster will be configured and *joined*, which means that instances will be bootstrapped into talking with each other. 

Finally, if everything has gone well, you'll see a message like this:

```
[OK] All 16384 slots covered
```

This means that there is at least one master instance serving each of the 16384 available slots.

![image-20230409170418315](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230409170418315.png)

#### use commands

If you don't want to create a Redis Cluster by configuring and executing individual instances manually as explained above, there is a much simpler system (but you'll not learn the same amount of operational details).

Find the `utils/create-cluster` directory in the Redis distribution. There is a script called `create-cluster` inside (same name as the directory it is contained into), it's a simple bash script. In order to start a 6 nodes cluster with 3 masters and 3 replicas just type the following commands:

1. `create-cluster start`
2. `create-cluster create`

Reply to `yes` in step 2 when the `redis-cli` utility wants you to accept the cluster layout.

```bash
bash-3.2$ ./create-cluster start
Starting 30001
Starting 30002
Starting 30003
Starting 30004
Starting 30005
Starting 30006
bash-3.2$ ./create-cluster create -f
>>> Performing hash slots allocation on 6 nodes...
Master[0] -> Slots 0 - 5460
Master[1] -> Slots 5461 - 10922
Master[2] -> Slots 10923 - 16383
Adding replica 127.0.0.1:30005 to 127.0.0.1:30001
Adding replica 127.0.0.1:30006 to 127.0.0.1:30002
Adding replica 127.0.0.1:30004 to 127.0.0.1:30003
>>> Trying to optimize slaves allocation for anti-affinity
[WARNING] Some slaves are in the same host as their master
M: 685a75d2e26062231d4d8500747be44c64e8de9c 127.0.0.1:30001
   slots:[0-5460] (5461 slots) master
M: 42bfb59288e424124ee6942762dbb9047f93729c 127.0.0.1:30002
   slots:[5461-10922] (5462 slots) master
M: d7784261adb1df483605ccda5a07a876d4c18ebe 127.0.0.1:30003
   slots:[10923-16383] (5461 slots) master
S: b09ead29ce667b3be129af893b11617c65f31cda 127.0.0.1:30004
   replicates 685a75d2e26062231d4d8500747be44c64e8de9c
S: 8f9a0d90cf21ba35420ea7c0b7cc4317ad66c9f5 127.0.0.1:30005
   replicates 42bfb59288e424124ee6942762dbb9047f93729c
S: 3f6a47da15503bac7abb31f70a02c324df8d2248 127.0.0.1:30006
   replicates d7784261adb1df483605ccda5a07a876d4c18ebe
>>> Nodes configuration updated
>>> Assign a different config epoch to each node
>>> Sending CLUSTER MEET messages to join the cluster
Waiting for the cluster to join
.
>>> Performing Cluster Check (using node 127.0.0.1:30001)
M: 685a75d2e26062231d4d8500747be44c64e8de9c 127.0.0.1:30001
   slots:[0-5460] (5461 slots) master
   1 additional replica(s)
M: 42bfb59288e424124ee6942762dbb9047f93729c 127.0.0.1:30002
   slots:[5461-10922] (5462 slots) master
   1 additional replica(s)
S: 3f6a47da15503bac7abb31f70a02c324df8d2248 127.0.0.1:30006
   slots: (0 slots) slave
   replicates d7784261adb1df483605ccda5a07a876d4c18ebe
M: d7784261adb1df483605ccda5a07a876d4c18ebe 127.0.0.1:30003
   slots:[10923-16383] (5461 slots) master
   1 additional replica(s)
S: b09ead29ce667b3be129af893b11617c65f31cda 127.0.0.1:30004
   slots: (0 slots) slave
   replicates 685a75d2e26062231d4d8500747be44c64e8de9c
S: 8f9a0d90cf21ba35420ea7c0b7cc4317ad66c9f5 127.0.0.1:30005
   slots: (0 slots) slave
   replicates 42bfb59288e424124ee6942762dbb9047f93729c
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.
```

You can now interact with the cluster, the first node will start at port 30001 by default. When you are done, stop the cluster with:

1. `create-cluster stop`

Please read the `README` inside this directory for more information on how to run the script.

### Redis Cluster Expansion & Reduction

> Redis Cluster 是 Redis 的分布式集群实现，它支持动态的扩容和缩容。在 Redis Cluster 中，每个 Redis 实例被称为一个节点，每个节点负责部分数据。一个 Redis Cluster 可以包含多个节点，每个节点之间通过 Gossip 协议进行通信，保证集群的状态一致性。在扩容和缩容过程中，需要注意以下几点：
>
> - **Scale-out**
>
>   当需要扩容 Redis Cluster 时，需要添加新的节点。具体步骤如下：
>
>   https://cloud.tencent.com/developer/article/1906499
>
>   1. 部署新的 Redis 实例，并加入集群
>   2. 将新节点加入到集群中，可以使用 Redis Cluster 提供的 meet 命令添加新节点
>   3. 将部分数据从旧节点迁移到新节点，可以使用 Redis Cluster 提供的 reshard 命令进行数据迁移
>
> - **Scale-in**
>
>   当需要缩容 Redis Cluster 时，需要删除某些节点。具体步骤如下：
>
>   https://cloud.tencent.com/developer/article/2167377?from=article.detail.1906499&areaSource=106000.1&traceId=x8oVHakrhRgm7L4Pdoewo
>
>   1. 将要删除的节点上的数据迁移到其他节点，可以使用 Redis Cluster 提供的 reshard 命令进行数据迁移
>   2. 将要删除的节点从集群中删除，可以使用 Redis Cluster 提供的 forget 命令删除节点
>
> 需要注意的是，在进行扩容和缩容操作时，需要确保集群的状态一致性，避免数据丢失或数据不一致的情况。可以使用 Redis Cluster 提供的命令和工具来管理集群，比如 reshard 命令、meet 命令、forget 命令、cluster info 命令等。

## Redis缓存问题★

在实际的业务场景中，Redis 一般和其他数据库搭配使用，用来减轻后端数据库的压力，比如和关系型数据库 MySQL 配合使用。

Redis 会把 MySQL 中经常被查询的数据缓存起来，比如热点数据，这样当用户来访问的时候，就不需要到 MySQL 中去查询了，而是直接获取 Redis 中的缓存数据，从而降低了后端数据库的读取压力。如果说用户查询的数据 Redis 没有，此时用户的查询请求就会转到 MySQL 数据库，当 MySQL 将数据返回给客户端时，同时会将数据缓存到 Redis 中，这样用户再次读取时，就可以直接从 Redis 中获取数据。流程图如下所示：

![image-20230130115134977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130115134977.png)

在使用 Redis 作为缓存数据库的过程中，有时也会遇到一些棘手问题，比如常见缓存穿透、缓存击穿和缓存雪崩等问题。

### 缓存穿透

缓存穿透是指当用户查询某个数据时，**Redis 中不存在该数据**，也就是**缓存没有命中**，此时查询请求就会转向持久层数据库 MySQL，结果发现 **MySQL 中也不存在该数据**，MySQL 只能返回一个空对象，代表此次查询失败。如果这种类请求非常多，或者用户利用这种请求进行恶意攻击，就会给 MySQL 数据库造成很大压力，甚至于崩溃，这种现象就叫缓存穿透。

为了避免缓存穿透问题，下面介绍两种解决方案：

![image-20230510233620610](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230510233620610.png)

**1) 缓存空对象**

当 MySQL 返回空对象时， Redis 将该对象缓存起来，同时为其设置一个过期时间。当用户再次发起相同请求时，就会从缓存中拿到一个空对象，用户的请求被阻断在了缓存层，从而保护了后端数据库，但是这种做法也存在一些问题，虽然请求进不了 MSQL，但是这种策略会占用 Redis 的缓存空间。

**2) 布隆过滤器**

我们知道，布隆过滤器判定不存在的数据，那么该数据一定不存在，利用它的这一特点可以防止缓存穿透。

首先将用户可能会访问的热点数据存储在布隆过滤器中（也称缓存预热），当有一个用户请求到来时会先经过布隆过滤器，如果请求的数据，布隆过滤器中不存在，那么该请求将直接被拒绝，否则将继续执行查询。相较于第一种方法，用布隆过滤器方法更为高效、实用。其流程示意图如下：

![image-20230130115216664](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130115216664.png)

**缓存预热：**是指系统启动时，提前将相关的数据加载到 Redis 缓存系统中。这样避免了用户请求的时再去加载数据。

### 缓存击穿

缓存击穿是指用户查询的数据缓存中不存在，但是后端数据库却存在，这种现象出现原因是一般是由缓存中 key 过期导致的。比如一个热点数据 key，它无时无刻都在接受大量的并发访问，如果某一时刻这个 key 突然失效了，就致使大量的并发请求进入后端数据库，导致其压力瞬间增大。这种现象被称为缓存击穿。

缓存击穿有两种解决方法：

**1) 改变过期时间**

设置热点数据永不过期。

**2) 分布式锁**

采用分布式锁的方法，重新设计缓存的使用方式，过程如下：

- 上锁：当我们通过 key 去查询数据时，首先查询缓存，如果没有，就通过分布式锁进行加锁，第一个获取锁的进程进入后端数据库查询，并将查询结果缓到Redis 中。
- 解锁：当其他进程发现锁被某个进程占用时，就进入等待状态，直至解锁后，其余进程再依次访问被缓存的 key。

### 缓存雪崩

缓存雪崩是指缓存中大批量的 key 同时过期，而此时数据访问量又非常大，从而导致后端数据库压力突然暴增，甚至会挂掉，这种现象被称为缓存雪崩。它和缓存击穿不同，缓存击穿是在并发量特别大时，某一个热点 key 突然过期，而缓存雪崩则是大量的 key 同时过期，因此它们根本不是一个量级。

**解决方案**

缓存雪崩和缓存击穿有相似之处，所以也可以采用**热点数据永不过期**的方法，来减少大批量的 key 同时过期。

再者就是**为 key 设置随机过期时间**，**避免 key 集中过期。**

## Redis回收延迟（删除数据操作）★

> 当Redis中的**某个键被删除时**，Redis通常**不会立即将相应的内存释放给操作系统**。
>
> 相反，它会**将这些已经被删除的键的内存空间放到一个空闲链表中**，以便在以后用来存储新的键值对。
>
> 
>
> 这种行为称为内存**回收延迟（Memory Reclamation Latency）**，它可以**减少频繁的内存分配和释放操作，从而提高Redis的性能和效率**。在实际运行中，Redis通常会维护多个内存分配器，每个分配器对应不同大小的内存块，以便更高效地管理内存空间。
>
> 
>
> 当Redis**需要为新的键值对分配内存时，它会先尝试从空闲链表中获取一块可用的内存空间，而不是直接向操作系统请求新的内存分配**。如果Redis空闲链表中没有可用的内存空间，它将向操作系统请求新的内存。
>
> 
>
> 这种内存回收延迟的行为虽然可以提高Redis的性能，但也可能导致Redis占用更多的内存空间。如果需要释放Redis占用的内存空间，可以考虑使用命令FLUSHALL或者重启Redis实例。但需要注意的是，这样会删除所有的键值对，因此在使用之前需要谨慎考虑。

## Redis内存淘汰机制★

> 由于内存资源的有限性，当Redis使用的内存达到一定限制时，需要采用一定的淘汰机制来释放内存。Redis提供了多种内存淘汰机制来满足不同的需求。
>
> 如果达到设置的上限，Redis的写命令会返回错误信息（但是读命令还可以正常返回。）或者你可以**配置内存淘汰机制**，当Redis达到内存上限时会冲刷掉旧的内容。
>
> 在Redis中，可以通过配置参数来选择不同的淘汰策略。例如，在Redis的配置文件中可以设置`maxmemory-policy`参数来指定淘汰策略，其可选项包括noeviction（不淘汰）、allkeys-lru（全局LRU）、volatile-lru（基于过期时间的LRU）、allkeys-random（全局随机）、volatile-random（基于过期时间的随机）、volatile-ttl（基于过期时间的TTL）等。
>
> **Redis内存淘汰机制的常见类型：**
>
> - **LRU（Least Recently Used）算法**
>
> LRU算法根据最近使用时间来淘汰最少使用的键值对，即优先淘汰最近最少使用的数据，保留最近使用频率较高的数据。Redis中默认采用的就是LRU算法。
>
> - LFU（Least Frequently Used）算法
>
> LFU算法根据访问次数来淘汰最少使用的键值对，即优先淘汰访问次数最少的数据，保留访问频率较高的数据。
>
> - Random算法
>
> Random算法是一种随机淘汰算法，即随机选择一个键值对进行淘汰。
>
> - TTL（Time To Live）算法
>
> TTL算法根据键值对的过期时间来淘汰数据，即优先淘汰过期时间最早的数据，保留未过期的数据。

## Redis过期键的删除策略★

> - 在单机版Redis中，存在两种删除策略：
>
>   - **惰性删除**：服务器不会主动删除数据，只有当客户端查询某个数据时，服务器判断该数据是否过期，如果过期则删除。
>
>   - **定期删除**：服务器执行定时任务删除过期数据，但是考虑到内存和CPU的折中（删除会释放内存，但是频繁的删除操作对CPU不友好），该删除的频率和执行时间都受到了限制。
>
> - 在主从复制场景下：
>
>   :happy:Redis 3.2之后，**从节点在读取数据时，增加了对数据是否过期的判断：如果该数据已过期，则不返回给客户端**；将Redis升级到3.2可以解决数据过期问题。

## Redis 内存碎片★

可以将**内存碎片**简单地理解为那些**不可用的空闲内存**

### 产生的原因

> Redis 内存碎片产生比较常见的 2 个**原因**：
>
> 1. **Redis 存储存储数据的时候向操作系统申请的内存空间可能会大于数据实际需要的存储空间。（空间预分配）**
>
>    Redis 使用 `zmalloc` 方法(Redis 自己实现的内存分配方法)进行内存分配的时候，除了要分配 `size` 大小的内存之外，还会多分配 `PREFIX_SIZE` 大小的内存。
>
> 2. **频繁修改 Redis 中的数据也会产生内存碎片。**
>
>    当 Redis 中的某个数据删除时，Redis 通常不会轻易释放内存给操作系统。

### 查询内存碎片信息

> **查看**内存碎片
>
> 快速查看内存碎片率
>
> ```shell
> > redis-cli -p 6379 info | grep mem_fragmentation_ratio
> ```
>
> 使用 `info memory` 命令即可查看 Redis 内存相关的信息
>
> ![image-20230328113014456](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230328113014456.png)

### 清理内存碎片

> **清理** Redis 内存碎片
>
> Redis4.0-RC3 版本以后**自带内存整理**，可以避免内存碎片率过大的问题。
>
> 直接通过 `config set` 命令将 `activedefrag` 配置项设置为 `yes` 即可。
>
> ```shell
> config set activedefrag yes
> ```
>
> **具体什么时候清理**需要通过下面两个参数控制：
>
> ```bash
> # 内存碎片占用空间达到 500mb 的时候开始清理
> config set active-defrag-ignore-bytes 500mb
> # 内存碎片率大于 1.5 的时候开始清理
> config set active-defrag-threshold-lower 50
> ```
>
> 通过 Redis 自动内存碎片清理机制可能会对 Redis 的性能产生影响，我们可以通过下面两个参数来**减少对 Redis 性能的影响**：
>
> ```bash
> # 内存碎片清理所占用 CPU 时间的比例不低于 20%
> config set active-defrag-cycle-min 20
> # 内存碎片清理所占用 CPU 时间的比例不高于 50%
> config set active-defrag-cycle-max 50
> ```
>
> :imp:另外，**重启节点可以做到内存碎片重新整理**。如果你采用的是高可用架构的 Redis 集群的话，你可以将碎片率过高的主节点转换为从节点，以便进行安全重启

## 分布式锁★

由于现如今的部署**分布式集群**系统后；原本的单机部署情况下的并发控制锁策略将失效。

单纯的Java API无法实现分布式锁；

需要一种跨JVM的互斥机制来控制共享资源的访问；

因而需要**分布式锁**

![image-20221130182538186](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130182538186.png)

### 主流分布式锁实现方式

> 1）基于数据库实现分布式锁
>
> 2）基于缓存（Redis）实现分布式锁（高效）[Redis 如何解决集群情况下分布式锁的可靠性？实际项目中不建议使用 Redlock 算法，成本和收益不成正比。]
>
> 3）基于Zookeeper（稳定）

### Redis实现分布式锁

![image-20221130184120016](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221130184120016.png)

| **issue ：**                                                 | **solution：**                                      |
| ------------------------------------------------------------ | --------------------------------------------------- |
| 在**释放锁之前**的**业务出现异常**或者**服务宕机等**造成**锁未被释放** 	形成**死锁**的局面 | **使用同时上锁同时设置锁过期时间的方式 自动删除锁** |
| 在**业务执行过程中锁就过期**自动删除了                       | **①将过期时间设置久一点**     **②续期**             |
| **释放锁也要保证原子性** 要确保释放的是自己的锁 而不是释放别的线程的锁 | **结合lua脚本**保证释放锁操作的原子性               |

![image-20230130211954312](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130211954312.png)

```java
//上redis分布式锁SET Key Value NX EX Second
//TODO 原子性上锁
String uuid = UUID.randomUUID().toString();
Boolean isRedisLock = redisTemplate.opsForValue().setIfAbsent(//上锁的同时设置锁的expireTime 过期时间 避免并发情况下造成死锁
        "redisLock",
        uuid,
        300,
        TimeUnit.SECONDS);
if (isRedisLock) {//判断是否加锁成功
    log.info("获取redis分布式锁成功");
    //若加锁成功则进行后续操作 加锁成功后也同时要把锁进行删除
    Map<String, List<Catalog2Vo>> catalogJsonFromDB;
    try {
        catalogJsonFromDB = getCatalogJsonFromDB();//执行查库业务代码
    } finally {
        //TODO 原子性解锁 使用lua脚本
        String lua = "if redis.call(\"get\",KEYS[1]) == ARGV[1]\n" +
                "then\n" +
                "    return redis.call(\"del\",KEYS[1])\n" +
                "else\n" +
                "    return 0\n" +
                "end";
        redisTemplate.execute(
                new DefaultRedisScript<Long>(lua, Long.class),//脚本 并且指定返回值类型Long 【1删除成功 0删除失败】
                Arrays.asList("redisLock"),//key
                uuid);//value
        log.info("lua脚本释放redis分布式锁");
    }
```

#### 上锁

SETNX Key Value



**原子加锁**



 （**设置键的过期时间** **过期后释放锁**）**SETNX Key Second Value**		或 --**SET Key Value NX EX Second** --expire second

推荐**使用同时上锁同时设置过期时间的方式**

#### 释放锁

DEL Key



**原子解锁**

结合lua脚本

An example of unlock script would be similar to the following:

```lua
if redis.call("get",KEYS[1]) == ARGV[1]
then
    return redis.call("del",KEYS[1])
else
    return 0
end
```

### Redisson

https://github.com/redisson/redisson/wiki/Table-of-Content

**Redis分布式锁的Java实现框架**

![image-20230329120753805](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230329120753805.png)



> **超时时间：**如果拿到分布式锁的节点宕机，且这个锁正好处于锁住的状态时，会出现锁死的状态，为了避免这种情况的发生，锁都会设置一个过期时间,分布式锁的超时时间默认是30秒。
>
> **设置超时时间：**另外Redisson 还提供了可以指定leaseTime参数的加锁方法来指定加锁的时间。**超过这个时间后锁便自动解开**了，**不会延长锁的有效期**。
>
> 
>
> :dog:**watch dog自动延期机制：**这样也存在一个问题，如果一个线程拿到了锁设置了30s超时，在30s后这个线程还没有执行完毕，锁超时释放了，就会导致问题。Redisson提供了一个监控锁的看门狗，它的作用是在Redisson实例被关闭前，不断的延长锁的有效期，也就是说，**如果一个拿到锁的线程一直没有完成逻辑**，那么**看门狗会帮助线程不断的延长锁超时时间，锁不会因为超时而被释放**。默认情况下，看门狗**每隔10s就会进行一次续期,把锁重置成30秒**，也可以通过修改Config.lockWatchdogTimeout来另行指定。
>
> 1. 只有在**未指定锁超时时间时**才**会使用看门狗**；
> 2. 看门狗默认续租时间是 10s 左右，`internalLockLeaseTime / 3`；
> 3. 可以通过 Config 统一设置看门狗的时间，设置 `lockWatchdogTimeout` 参数即可。
>
> ![image-20230329121728159](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230329121728159.png)
>
> **尝试获取锁时间**：线程会尝试在一定时间内获取锁，如果超时则表示获取失败,返回false
>
> **宕机：**如果宕机了定时任务跑不了,就续不了期,那自然30秒之后锁就解开了
>
> **注意**：如果程序释放锁操作时因为异常没有被执行，那么锁无法被释放，所以释放锁操作一定要放到 finally {} 中；

pom

```xml
<!--Redisson 分布式锁框架-->
<dependency>
    <groupId>org.redisson</groupId>
    <artifactId>redisson-spring-boot-starter</artifactId>
    <version>3.19.1</version>
</dependency>
```

配置文件

```yaml
spring:
  redis:
    host: 192.168.199.181
    port: 6379
    database: 0
    redisson:
      file: classpath:redisson.yml #也可以直接将配置写在配置文件中 或者使用配置类的形式
```

redisson.yml

```yaml
singleServerConfig:
  address: "redis://192.168.199.181:6379" #//若安全连接使用 "rediss://" for SSL connection
  database: 0
threads: 16
nettyThreads: 32
codec: !<org.redisson.codec.FstCodec> {}
transportMode: "NIO"
```

![image-20230130214142510](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130214142510.png)

instance

![image-20230130221014909](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130221014909.png)

## 缓存数据一致性★

[缓存和数据库一致性问题，看这篇就够了 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzIyOTYxNDI5OA==&mid=2247487312&idx=1&sn=fa19566f5729d6598155b5c676eee62d&chksm=e8beb8e5dfc931f3e35655da9da0b61c79f2843101c130cf38996446975014f958a6481aacf1&scene=178&cur_album_id=1699766580538032128#rd)

> 缓存中的数据和数据库中的数据保存**数据一致性？**(**缓存多数应用在读多写少**的业务情况下)
>  * 1）**双写模式**(在数据库中进行了写操作 同时同步写到缓存中)
>  * 2）**失效模式**(在数据库中进行了写操作 将缓存中的数据及时的进行删除 下次进行查询就从数据库中获取最新的数据)
>
> 以上方法并发情况下仍然无法完全解决数据一致性问题
>
>  * 3)可以使用**读写锁**(读读情况下相当于无锁)
>  * 4)使用canal（alibaba的解决缓存数据一致性的工具 canal将自己伪装成mysql的从库 实时将binlog中的写操作更新执行到redis中）订阅数据库的binlog

![image-20230130220513829](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230130220513829.png)
