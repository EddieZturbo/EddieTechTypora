# ElasticSearch

[Elasticsearch: The Official Distributed Search & Analytics Engine | Elastic](https://www.elastic.co/elasticsearch/)

![image-20230122235230676](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230122235230676.png)

ElasticSearch是一个**分布式，高性能、高可用、可伸缩、RESTful 风格**的**搜索和数据分析引擎**。通常作为**Elastic Stack的核心**来使用，Elastic Stack大致是如下这样组成的：

![image-20230122235306781](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230122235306781.png)

ES是一个近实时（NRT）的搜索引擎，一般从添加数据到能被搜索到只有很少的延迟（大约是1s），而查询数据是实时的。**一般我们可以把ES配合logstash,kibana来做日志分析系统，或者是搜索方面的系统功能，比如在网上商城系统里实现搜索商品的功能也会用到ES。**

## 基本概念

| ES                    | MySql    |
| --------------------- | -------- |
| 字段                  | 列       |
| 文档                  | 一行数据 |
| 类型（8.x版本已废弃） | 表       |
| 索引                  | 数据库   |

## 安装运行

### Docker安装ElasticSearch

#### 下载镜像文件

```
docker pull elasticsearch:7.4.2//存储和检索数据
docker pull kibana:7.4.2//可视化
```

![image-20230122235514842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230122235514842.png)

![image-20230123122112441](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123122112441.png)

#### 运行

![image-20230123122912828](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123122912828.png)

```bash
echo "http.host:0.0.0.0" >> /mydata/elasticsearch/config/elasticsearch.yml
```

![image-20230123123619937](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123123619937.png)

![image-20230123122932561](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123122932561.png)

![image-20230123122941577](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123122941577.png)

```shell
docker run --name elasticsearch -p 9200:9200 -p 9300:9300 \
-e "discovery.type=single-node" \
-e ES_JAVA_OPTS="-Xms64m -Xmx512m" \
-v /mydata/elasticsearch/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml \
-v /mydata/elasticsearch/data:/usr/share/elasticsearch/data \
-v /mydata/elasticsearch/plugins:/usr/share/elasticsearch/plugins \
-d elasticsearch:7.4.2
```

### Docker安装Kibana(可视化)

#### 下载镜像文件

![image-20230123141655674](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123141655674.png)

#### 运行

![image-20230123141713962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123141713962.png)

```shell
[root@localhost ~]docker run --name kibana -p 5601:5601 \
> -e ELASTICSEARCH_HOSTS=http://192.168.199.180:9200 \
> -d kibana:7.4.2
```

![image-20230123142057087](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123142057087.png)

![image-20230123142252027](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123142252027.png)

## 基本命令

### **_cat**

```
（GET请求）
http://192.168.199.180:9200/_cat/nodes		查看所有节点
http://192.168.199.180:9200/_cat/master		查看主节点
http://192.168.199.180:9200/_cat/indices	查看所有索引
http://192.168.199.180:9200/_cat/health		查看健康状况
```

**GET /_cat/indices**

```
yellow open bank                     dvXQqRC2R_KFK3ug7B4cMw 1 1 1000 0 414.3kb 414.3kb
green  open .kibana_task_manager_1   HPYZOUioSP2c20mSzG_eOg 1 0    2 1  37.1kb  37.1kb
green  open .apm-agent-configuration WHUXMN5fRzepeC93UBtExw 1 0    0 0    283b    283b
yellow open goods                    Gxd67eXLSYWHmLmZLbxiMg 1 1  216 0  44.7kb  44.7kb
green  open .kibana_1                QlMdB5mhQe-TWQVnzMp8eQ 1 0    8 0  27.2kb  27.2kb
yellow open eddie                    ydlcVrk2Tn6eDrfZ2lbS0g 1 1    1 0   4.9kb   4.9kb

    第一列：索引的健康状况，可以是green（健康）、yellow（部分副本不可用）或者red（主分片不可用）。
    第二列：索引的状态，可以是open（打开）、close（关闭）或者readonly（只读）。
    第三列：索引的名称。
    第四列：索引的UUID。
    第五列：索引的主分片数。
    第六列：索引的副本分片数。
    第七列：索引中文档的数量。
    第八列：索引中删除的文档的数量。
    第九列：索引在磁盘上占用的总空间。
    第十列：索引的主分片在磁盘上占用的空间。
    第十一列：索引的副本分片在磁盘上占用的空间。
```

**GET /_cat/nodes**

```
127.0.0.1 19 93 2 0.01 0.03 0.05 dilm * cdac51ee9ad5

172.31.1.223 32 89 2 0.00 0.00 0.00 mdi * es-node-1 Tflm5Fx
172.31.1.224 38 88 0 0.00 0.00 0.00 mdi - es-node-2 JD6p5U6
这个示例中，有两个节点。第一个节点的名称是“es-node-1”，角色是“master”和“data”，并且它的JVM堆内存使用率为32%，系统内存使用率为89%，CPU使用率为2%，可用磁盘容量为0，已用磁盘容量为0，总磁盘容量未知。第二个节点的名称是“es-node-2”，角色是“data”，它的JVM堆内存使用率为38%，系统内存使用率为88%，CPU使用率为0%，可用磁盘容量为0，已用磁盘容量为0，总磁盘容量未知
```

**GET /_cat/master**

```
c0W-QPE3TZyq7H3b4MmPWA 127.0.0.1 127.0.0.1 cdac51ee9ad5
id                     host      ip        node
    id: 主节点的唯一标识符。
    host: 主节点所在的主机名。
    ip: 主节点的 IP 地址。
    node: 主节点所在的节点名称。
```

**GET /_cat/health**

```
1680069632 06:00:32 elasticsearch yellow 1 1 6 6 0 0 3 0 - 66.7%
epoch timestamp cluster status node.total node.data shards pri relo init unassign pending_tasks max_task_wait_time active_shards_percent
    epoch: 集群状态变化的 Unix 时间戳（以毫秒为单位）。
    timestamp: 查询的 Unix 时间戳（以毫秒为单位）。
    cluster: 集群名称。
    status: 集群的健康状态，可能的值为 green、yellow 或 red。
    node.total: 集群中节点的总数。
    node.data: 包含数据的节点数。
    shards: 集群中分片的总数。
    pri: 集群中主分片的数量。
    relo: 正在重新分配的分片的数量。
    init: 正在初始化的分片的数量。
    unassign: 未分配的分片的数量。
    pending_tasks: 等待执行的任务数。
    max_task_wait_time: 等待最长的任务的时间（以毫秒为单位）。
    active_shards_percent: 当前分片的活动百分比。
```

### **索引一个文档(保存一条记录)**

发送多次（第二次开始是update操作）

**(PUT请求)一定要携带id**不然会报错(带的id若原本不存在则为create新增否则为update)

(POST请求)不带id或者带的id之前没数据则为create新增 带id则已存在数据则为update

```
保存一个数据，保存在那个索引的那个类型下，指定使用哪个唯一标识

(PUT请求)一定要携带id不然会报错(带的id若原本不存在则为create新增否则为update)
http://192.168.199.180:9200/customer/external/1

(POST请求)不带id或者带的id之前没数据则为create新增 带id则已存在数据则为update
http://192.168.199.180:9200/customer/external/1
```

![image-20230123143437957](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123143437957.png)

![image-20230123143446427](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123143446427.png)

### 查询索引

```
(GET请求)
http://192.168.199.180:9200/customer

GET /eddie
```

```
{
    "shopping": {//索引名
        "aliases": {},//别名
        "mappings": {},//映射
        "settings": {//设置
            "index": {//设置 - 索引
                "creation_date": "1617861426847",//设置 - 索引 - 创建时间
                "number_of_shards": "1",//设置 - 索引 - 主分片数量
                "number_of_replicas": "1",//设置 - 索引 - 主分片数量
                "uuid": "J0WlEhh4R7aDrfIc3AkwWQ",//设置 - 索引 - 主分片数量
                "version": {//设置 - 索引 - 主分片数量
                    "created": "7080099"
                },
                "provided_name": "shopping"//设置 - 索引 - 主分片数量
            }
        }
    }
}
```

![image-20230329140819089](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329140819089.png)

### **查询文档**

```
(GET请求)
http://192.168.199.180:9200/customer/external/1
```

![image-20230123144407211](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123144407211.png)

![image-20230123144415546](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123144415546.png)

### **更新文档**

```
(POST请求)
http://192.168.199.180:9200/customer/external/1/_update
会与原本的数据进行对比 若一致则不会改变数据

http://192.168.199.180:9200/customer/external/1
不会与原本的数据进行对比 直接进行改变

(PUT请求)
http://192.168.199.180:9200/customer/external/1
不会与原本的数据进行对比 直接进行改变
```

![image-20230124083356948](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124083356948.png)

![image-20230124083617148](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124083617148.png)

![image-20230124083706195](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124083706195.png)

### **删除文档和索引**

```
(DELETE请求)
删除索引
http://192.168.199.180:9200/customer/external/1

删除类型
http://192.168.199.180:9200/customer
```

![image-20230124084001740](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124084001740.png)

![image-20230124084030642](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124084030642.png)

### **bulk批量API**

```
语法格式
POST /XXX/XXX/_bulk
{action:{metadata}}
{requestBody}
{action:{metadata}}
{requestBody}

POST /customer/external/_bulk
{"index":{"_id":1}}
{"name":"Eddie"}
{"index":{"_id":2}}
{"major":"Java"}
```

![image-20230124085023749](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124085023749.png)

**批量导入样本数据进行test**

https://raw.githubusercontent.com/elastic/elasticsearch/7.4/docs/src/test/resources/accounts.json

![image-20230124090343216](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124090343216.png)

![image-20230124090542065](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124090542065.png)

## 进阶命令

### SearchAPI

**1）通过REST request URL 发送搜索参数(uti+检索参数)**

**2）另一个通过使用 REST request body 来发送他们（uri + 请求体）**

![image-20230124095659236](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124095659236.png)

![image-20230124095819525](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124095819525.png)

### Query DSL

https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl.html

## 自定义扩展词库

### 安装IK分词器

**中文分词**

https://github.com/medcl/elasticsearch-analysis-ik/releases/tag/v7.4.2

![image-20230124214709253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124214709253.png)



![image-20230124214652125](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124214652125.png)

```bash
unzip elasticsearch-analysis-ik-7.4.2.zip -d /mydata/elasticsearch/plugins/ik
```

![image-20230124220232716](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124220232716.png)



![image-20230124220053472](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124220053472.png)

![image-20230124220945099](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124220945099.png)

### Docker安装运行nginx

**启动nginx容器**

![image-20230124231649109](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124231649109.png)

**将容器中的配置cp出来**

```shell
[root@localhost nginx]# docker container cp nginx:/etc/nginx .
```

![image-20230124232925167](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124232925167.png)

**删除原先启动的容器 重启完整配置启动Nginx**

![image-20230124232049387](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124232049387.png)

```shell
[root@localhost nginx]# docker run --name nginx -p 80:80 \
> -v /mydata/nginx/html/:/usr/share/nginx/html \
> -v /mydata/nginx/logs/:/var/log/nginx \
> -v /mydata/nginx/conf/:/etc/nginx \
> -d nginx
```

**访问80端口**

![image-20230124233408103](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124233408103.png)

### 自定义es词库

**在nginx的html文件夹中编辑ES的分词的自定义的词库**

![image-20230124234223857](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124234223857.png)

![image-20230124234241762](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124234241762.png)

![image-20230124234349440](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124234349440.png)



**配置IK分词器**

![image-20230124234847920](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124234847920.png)

 ![image-20230124234755083](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124234755083.png)

### 测试

![image-20230124235224906](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230124235224906.png)

## Java操作ElasticSearch

https://www.elastic.co/guide/en/elasticsearch/client/java-rest/7.4/java-rest-high-search.html



**导入相关依赖**

![image-20230125001227384](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230125001227384.png)



**编写配置**

![image-20230125121918708](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230125121918708.png)

```java
@Configuration
public class ElasticSearchConfig {

    @Bean
    public RestHighLevelClient restHighLevelClient(){
        RestHighLevelClient restHighLevelClient = new RestHighLevelClient(
                RestClient.builder(
                        new HttpHost("192.168.199.180",9200,"http")
                )
        );
        return restHighLevelClient;
    }

    /**
     * 配置常规操作
     */
    public static final RequestOptions COMMON_OPTIONS;
    static {
        RequestOptions.Builder builder = RequestOptions.DEFAULT.toBuilder();
        COMMON_OPTIONS = builder.build();
    }
}
```

**Test**操作

![image-20230125002757121](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230125002757121.png)



**储存数据操作**

```java
@RunWith(SpringRunner.class)
@SpringBootTest
public class MallSearchApplicationTests {

    @Autowired
    private ElasticSearchConfig elasticSearchConfig;

    @Autowired
    private RestHighLevelClient client;

    @Test
    public void contextLoads() {
        System.out.println(elasticSearchConfig);
    }

    @Test
    public void test() throws IOException {

        IndexRequest indexRequest = new IndexRequest("users");//数据的Index
        indexRequest.id("1");//数据的id

        Person person = new Person();
        person.setName("Eddie");
        person.setGender('M');
        person.setAge(22);
        person.setMajor("Java");
        String jsonString = JSON.toJSONString(person);//定义一个对象并转成JSON字符串形式

        indexRequest.source(jsonString, XContentType.JSON);//要储存的数据

        IndexResponse index = client.index(indexRequest, elasticSearchConfig.COMMON_OPTIONS);//客户端进行data操作
        System.out.println(index);//输出执行响应结果
    }

    @Data
    class Person{
        private String name;
        private Character gender;
        private Integer age;
        private String major;
    }

}
```

**query数据操作**

```json
GET bank/_search
{
  "query": {
    "match_all": {}
  }
}
```



```java
@Test
public void test2() throws IOException {
    SearchSourceBuilder sourceBuilder = new SearchSourceBuilder();//构造query条件
    sourceBuilder.query(QueryBuilders.matchAllQuery());
    
    SearchRequest searchRequest = new SearchRequest();//search操作
    searchRequest.indices("bank");//指定要search的index
    searchRequest.source(sourceBuilder);//_source操作

    SearchResponse searchResponse = client.search(searchRequest, elasticSearchConfig.COMMON_OPTIONS);//执行search操作
    //结果获取&分析
    SearchHits hits = searchResponse.getHits();
    SearchHit[] searchHits = hits.getHits();
    for (SearchHit resultHit : searchHits) {
        String sourceAsString = resultHit.getSourceAsString();
        BankInfo bankInfo = JSON.parseObject(sourceAsString, BankInfo.class);
        System.out.println(bankInfo.toString());
        //MallSearchApplicationTests
        // .BankInfo(
        // account_number=1.0
        // , balance=39225.0
        // , firstname=Amber
        // , lastname=Duke
        // , age=32.0
        // , gender=M
        // , address=880 Holmes Lane
        // , employer=Pyrami
        // , email=amberduke@pyrami.com, city=Brogan, state=IL
        // )
        //...
    }
}


@Data
static class BankInfo{
    private float account_number;
    private float balance;
    private String firstname;
    private String lastname;
    private float age;
    private String gender;
    private String address;
    private String employer;
    private String email;
    private String city;
    private String state;
}
```

## Nested类型

对于**对应Java类的数据类型type要求为Nested**

```
PUT my_indix
{
  "mappings": {
    "properties": {
      "user":{
        "type": "nested"
      }
    }
  }
}
```

![image-20230126100518612](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230126100518612.png)



**避免对应Java类的数据被扁平化处理 导致出现错误的数据结果**

![image-20230126100409091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230126100409091.png)

## 结果分析

> `took` – Elasticsearch运行查询所花费的时间（以毫秒为单位）
>
> `timed_out` –搜索请求是否超时
>
> `_shards` - 搜索了多少个碎片，以及成功，失败或跳过了多少个碎片的细目分类。
>
> `max_score` – 找到的最相关文档的分数
>
> `hits.total.value` - 找到了多少个匹配的文档
>
> `hits.sort` - 文档的排序位置（不按相关性得分排序时）
>
> `hits._score` - 文档的相关性得分（使用match_all时不适用）

![image-20230123145016278](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230123145016278.png)

```json
"took" : 29,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 1000,
      "relation" : "eq"
    },
    "max_score" : null,
    "hits" : [
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "0",
        "_score" : null,
        "_source" : {
          "account_number" : 0,
          "balance" : 16623,
          "firstname" : "Bradshaw",
          "lastname" : "Mckenzie",
          "age" : 29,
          "gender" : "F",
          "address" : "244 Columbus Place",
          "employer" : "Euron",
          "email" : "bradshawmckenzie@euron.com",
          "city" : "Hobucken",
          "state" : "CO"
        },
        "sort" : [
          0
        ]
      },
```

