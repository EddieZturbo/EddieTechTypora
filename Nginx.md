# Nginx

![image-20230108220502330](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108220502330.png)

https://www.nginx.com/

![image-20230108220603891](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108220603891.png)

**——反向代理**

**——负载均衡**

**——HTTP服务器（动静分离）**

**——正向代理**

## Linux安装nginx

### Manually

> **在linux下安装nginx，首先需要安装 gcc-c++编译器。然后安装nginx依赖的pcre和zlib包。最后安装nginx即可。**

1.先安装gcc-c++编译器

```bash
yum install gcc-c++
yum install -y openssl openssl-devel
```

2.再安装pcre包

```bash
yum install -y pcre pcre-devel
```

3.再安装zlib包

```bash
yum install -y zlib zlib-devel
```

> **下面进行nginx的安装**

1.在/usr/local/下创建文件nginx文件

```bash
mkdir /usr/local/nginx
```

2.在网上下nginx包上传至Linux（https://nginx.org/download/），也可以直接下载

```bash
wget https://nginx.org/download/nginx-1.19.9.tar.gz
```

3.解压并进入nginx目录

```bash
tar -zxvf nginx-1.19.9.tar.gz
cd nginx-1.19.9
```

4.使用nginx默认配置

```bash
./configure
```

5.编译安装

```bash
make
make install
```

6.查找安装路径

```java
whereis nginx
```

7.进入sbin目录，可以看到有一个可执行文件nginx，直接**./nginx**执行就OK了。

```bash
./nginx
```

9.查看是否启动成功

```bash
ps -ef | grep nginx
```

![image-20230108232749175](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108232749175.png)

![image-20230108232809842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108232809842.png)

### Use EPEL Software Repository

> 1. **Adding the EPEL Software Repository**
>
>    ```bash
>    yum install epel-release
>    ```
>
> 2. **Installing Nginx**
>
>    ```bash
>    yum install nginx
>    ```
>
> 3. **Start Nginx**
>
>    ```bash
>    systemctl start nginx
>    ```
>
>    ![image-20240229152823347](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240229152823347.png)

## Nginx配置文件

[Full Example Configuration | NGINX](https://www.nginx.com/resources/wiki/start/topics/examples/full/)

![image-20230129095354392](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230129095354392.png)

![image-20230108233047491](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108233047491.png)

> - 1、**全局块**：配置影响nginx全局的指令。一般有运行nginx服务器的用户组，nginx进程pid存放路径，日志存放路径，配置文件引入，允许生成worker process数等。
> - 2、**events块**：配置影响nginx服务器或与用户的网络连接。有每个进程的最大连接数，选取哪种事件驱动模型处理连接请求，是否允许同时接受多个网路连接，开启多个网络连接序列化等。
> - 3、**http块**：可以嵌套多个server，配置代理，缓存，日志定义等绝大多数功能和第三方模块的配置。如文件引入，mime-type定义，日志自定义，是否使用sendfile传输文件，连接超时时间，单连接请求数等。
> - 4、**server块**：配置虚拟主机的相关参数，一个http中可以有多个server。
> - 5、**location块**：配置请求的路由，以及各种页面的处理情况。

```nginx
user nginx;  ## Default: nobody
worker_processes 5;  ## Default: 1
error_log logs/error.log;
pid logs/nginx.pid;
worker_rlimit_nofile 8192;

events {
  worker_connections  4096;  ## Default: 1024
}

http {
  include    conf/mime.types;
  include    /etc/nginx/proxy.conf;
  include    /etc/nginx/fastcgi.conf;
  index    index.html index.htm index.php;

  default_type application/octet-stream;
  log_format   main '$remote_addr - $remote_user [$time_local]  $status '
    '"$request" $body_bytes_sent "$http_referer" '
    '"$http_user_agent" "$http_x_forwarded_for"';
  access_log   logs/access.log  main;
  sendfile     on;
  tcp_nopush   on;
  server_names_hash_bucket_size 128; # this seems to be required for some vhosts

  server { # http server(Front-end)
    listen       9575;
    listen       [::]:9575;
    server_name  localhost;
    access_log   logs/domain1.access.log  main;
    root         html;

    location / {
      try_files $uri $uri/ /index.html;
    }
    location ^~ /JMS_Frontend {
      try_files $uri $uri/ /JMS_Frontend/index.html;
    }
  }

  server { # simple reverse-proxy
    listen       80;
    server_name  domain2.com www.domain2.com;
    access_log   logs/domain2.access.log  main;

    # serve static files
    location ~ ^/(images|javascript|js|css|flash|media|static)/  {
      root    /var/www/virtual/big.server.com/htdocs;
      expires 30d;
    }

    # pass requests for dynamic content to rails/turbogears/zope, et al
    location / {
      proxy_pass      http://127.0.0.1:8080;
    }
  }

  upstream big_server_com {
    server 127.0.0.3:8000 weight=5;
    server 127.0.0.3:8001 weight=5;
    server 192.168.0.1:8000;
    server 192.168.0.1:8001;
  }

  server { # simple load balancing
    listen          80;
    server_name     big.server.com;
    access_log      logs/big.server.access.log main;

    location / {
      proxy_pass      http://big_server_com;
    }
  }
}
```

## Nginx操作指令

![image-20230108233229741](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108233229741.png)

## Nginx进程模型

![image-20230108233321810](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108233321810.png)

在工作方式上，Nginx 分为**单工作进程**和**多工作进程**两种模式。

- **单工作进程模式**：除主进程外，还有一个工作进程，工作进程是单线程的；
- **多工作进程模式**：每个工作进程包含多个线程。Nginx 默认为单工作进程模式；

Nginx 在启动后，会有**一个 master 进程和多个 worker 进程**。

### master 进程

master 进程主要用来管理 worker 进程，包含：接收来自外界的信号，向各 worker 进程发送信号，监控 worker 进程的运行状态，当异常情况下 worker 进程退出后，会自动重新启动新的 worker 进程。 master 进程充当整个进程组与用户的交互接口，同时对进程进行监护。它**不需要处理网络事件，不负责业务的执行**，只会通过**管理 worker 进程**来实现重启服务、平滑升级、更换日志文件、配置文件实时生效等功能。 我们要控制 Nginx，只需要通过 kill 向 master 进程发送信号就行了。比如 kill -HUP pid，我们一般用这个信号来重启 Nginx，或重新加载配置。因为是从容地重启，因此服务是不中断的。master 进程在接收到 HUP 信号后是怎么做的呢？首先 master 进程在接到信号后，会先重新加载配置文件，然后再启动新的 worker 进程，并向所有老的 worker 进程发送信号，告诉他们可以光荣退休了。新的 worker 在启动后，就开始接收新的请求，而老的 worker 在收到来自 master 的信号后，就不再接收新的请求，并且在当前进程中的所有未处理完的请求处理完成后，再退出。

>  注： 直接给 master 进程发送信号，这是比较老的操作方式。Nginx 在 0.8 版本之后，引入了一系列命令行参数，来方便我们管理。比如： 

- `./nginx -s reload`：重启 nginx；
- `./nginx -s stop`：停止nginx的运行；

 如何做到的呢？我们还是拿 reload 来说，我们看到，执行命令时，我们是启动一个新的 nginx 进程，而新的 nginx 进程在解析到 reload 参数后，就知道我们的目的是控制 nginx 来重新加载配置文件了，它会向 master 进程发送信号，然后接下来的动作，就和我们直接向 master 进程发送信号一样了。 

### Worker

基本的网络事件，则是放在 worker 进程中来处理了。**多个 worker 进程之间是对等的**，他们同等竞争来自客户端的请求，各进程互相之间是独立的，**一个请求只可能在一个 worker 进程中处理**。worker 进程的个数是可以设置的，一般我们会**设置与机器 CPU 核数一致**，这里面的原因与 Nginx 的**进程模型**以及**事件处理模型**是分不开的。 worker 进程之间是平等的，每个进程，处理请求的机会也是一样的。当我们提供 80 端口的 HTTP 服务时，一个连接请求过来，每个进程都有可能处理这个连接，怎么做到的呢？步骤如下：

1.  每个 worker 进程都是从 master 进程 fork 过来，在 master 进程里面，建立好需要 listen 的 socket (listenfd) 之后； 
2.  fork 出多个 worker 进程； 
3.  所有 worker 进程的 listenfd 会在新连接到来时变得可读，为保证只有一个进程处理该连接，**所有 worker 进程在注册 listenfd 读事件前抢 accept_mutex**，抢到互斥锁的 worker 进程注册 listenfd 读事件；在读事件里调用 accept 接受该连接。 
4.  当一个 worker 进程在 accept 这个连接之后，就开始读取请求，解析请求，处理请求。产生数据后，再返回给客户端，最后才断开连接；

## 反向代理

### 正向代理与反向代理的区别：

反向代理和正向代理的区别就是：**正向代理代理客户端，反向代理代理服务器。**

**正向代理相对于目标服务器而言隐藏了客户端的真实IP地址**，因为对于目标服务器而言所有请求都是从正向代理服务器发出的，正向代理主要是为了突破网络访问限制，比如科学上网，还有就是隐藏客户端IP地址。

**反向代理对于客户端而言隐藏了目标服务器IP地址**，只需要知道代理服务器地址就能访问到目标服务器的资源。其主功能是可以做负载均衡和安全防护。不过，不管正向代理还是反向代理，都能加快客户端的访问速度，因为nginx服务器是一个高性能的http web服务器，其能够对代理中的数据作缓冲。

反向代理，其实客户端对代理是无感知的，因为客户端不需要任何配置就可以访问，我们只需要将请求发送到反向代理服务器，由反向代理服务器去选择目标服务器获取数据后，在返回给客户端，此时反向代理服务器和目标服务器对外就是一个服务器，暴露的是代理服务器地址，隐藏了真实服务器IP地址。

### 反向代理配置

![image-20230129110830740](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230129110830740.png)

#### 简单配置

```nginx
server {
    listen       80;
    server_name  www.zhengqing520.com;# 服务器地址或绑定域名

    location / { # 访问80端口后的所有路径都转发到 proxy_pass 配置的ip中
        root   /usr/share/nginx/html;
        index  index.html index.htm;
   		proxy_pass http://zhengqingya.gitee.io; # 配置反向代理的ip地址和端口号 【注：url地址需加上http:// 或 https://】
    }
}
```

#### 复杂配置

1. www.zhengqing520.com/api 转发到 http://www.zhengqing520.com:9528/api/
2. www.zhengqing520.com/blog/ 转发到 http://zhengqingya.gitee.io/blog/

```nginx
server {
    listen       80;
    server_name  www.zhengqing520.com;# 服务器地址或绑定域名
 
    location ^~ /api {  # ^~/api 表示匹配前缀为api的请求
        proxy_pass  http://www.zhengqing520.com:9528/api/;  # 注：proxy_pass的结尾有/， -> 效果：会在请求时将/api/*后面的路径直接拼接到后面
  
        # proxy_set_header作用：设置发送到后端服务器(上面proxy_pass)的请求头值  
            # 【当Host设置为 $http_host 时，则不改变请求头的值;
            #   当Host设置为 $proxy_host 时，则会重新设置请求头中的Host信息;
            #   当为$host变量时，它的值在请求包含Host请求头时为Host字段的值，在请求未携带Host请求头时为虚拟主机的主域名;
            #   当为$host:$proxy_port时，即携带端口发送 ex: $host:8080 】
        proxy_set_header Host $host; 
  
        proxy_set_header X-Real-IP $remote_addr; # 在web服务器端获得用户的真实ip 需配置条件①    【 $remote_addr值 = 用户ip 】
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;# 在web服务器端获得用户的真实ip 需配置条件②
        proxy_set_header REMOTE-HOST $remote_addr;
        # proxy_set_header X-Forwarded-For $http_x_forwarded_for; # $http_x_forwarded_for变量 = X-Forwarded-For变量
    }

    location ^~ /blog/ { # ^~/blog/ 表示匹配前缀为blog/后的请求
        proxy_pass  http://zhengqingya.gitee.io/blog/; 
  
        proxy_set_header Host $proxy_host; # 改变请求头值 -> 转发到码云才会成功
        proxy_set_header  X-Real-IP  $remote_addr;
        proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-NginX-Proxy true;
    }
}
```



## 负载均衡

负载均衡也是Nginx常用的一个功能，负载均衡其意思就是分摊到多个操作单元上进行执行，例如Web服务器、FTP服务器、企业关键应用服务器和其它关键任务服务器等，从而共同完成工作任务。简单而言就是当有2台或以上服务器时，根据规则随机的将请求分发到指定的服务器上处理，**负载均衡配置一般都需要同时配置反向代理，通过反向代理跳转到负载均衡**。而Nginx目前支持自带3种负载均衡策略，还有2种常用的第三方策略。

![image-20230108234753837](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230108234753837.png)

### 负载均衡策略

**1) 轮询（默认）**
每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。
2)、weight 权重
指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。
3)、ip_hash
每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，**可以解决session的问题[nginx反向代理导致session失效的问题处理 - 【雨歌】 - 博客园 (cnblogs.com)](https://www.cnblogs.com/spec-dog/p/13292111.html)**。
4)、fair（第三方）
按后端服务器的响应时间来分配请求，响应时间短的优先分配。
5)、url_hash（第三方）

### 负载均衡配置

```nginx
upstream cluster{#负载均衡配置 可以指定负载均衡规则
	ip_hash;
        server 192.168.199.181:8080;
        server 192.168.199.181:8081;
    }
    server {
        listen       80;
        server_name localhost;
        #charset koi8-r;
        #access_log  logs/host.access.log  main;
        location / {
            #root   html;
            #index  index.html index.htm;
            proxy_pass http://cluster;
        }
    }
    server {
        listen       80;
        server_name localhost;
        #charset koi8-r;
        #access_log  logs/host.access.log  main;
        location / {
            #root   html;
            #index  index.html index.htm;
            proxy_pass http://cluster;
        }
    }
```



## **动静分离&HTTP服务器**

### 动静分离

动静分离是让动态网站里的动态网页根据一定规则把不变的资源和经常变的资源区分开来，动静资源做好了拆分以后，我们就可以根据静态资源的特点将其做缓存操作，这就是网站静态化处理的核心思路

```nginx
upstream test{  
       server localhost:8080;  
       server localhost:8081;  
    }   

    server {  
        listen       80;  
        server_name  localhost;  

        location / {  
            root   e:\wwwroot;  
            index  index.html;  
        }  

        # 所有静态请求都由nginx处理，存放目录为html  
        location ~ \.(gif|jpg|jpeg|png|bmp|swf|css|js)$ {  
            root    e:\wwwroot;  
        }  

        # 所有动态请求都转发给tomcat处理  
        location ~ \.(jsp|do)$ {  
            proxy_pass  http://test;  
        }  

        error_page   500 502 503 504  /50x.html;  
        location = /50x.html {  
            root   e:\wwwroot;  
        }  
    }
```

这样我们就可以吧HTML以及图片和css以及js放到wwwroot目录下，而tomcat只负责处理jsp和请求，例如当我们后缀为gif的时候，Nginx默认会从wwwroot获取到当前请求的动态图文件返回，当然这里的静态文件跟Nginx是同一台服务器，我们也可以在另外一台服务器，然后通过反向代理和负载均衡配置过去就好了，只要搞清楚了最基本的流程，很多配置就很简单了，另外localtion后面其实是一个正则表达式，所以非常灵活

### HTTP服务器

Nginx本身也是一个静态资源的服务器，当只有静态资源的时候，就可以使用Nginx来做服务器，同时现在也很流行动静分离，就可以通过Nginx来实现，首先看看Nginx做静态资源服务器



```nginx
server {
        listen       80;                                                         
        server_name  localhost;                                               
        client_max_body_size 1024M;

        location / {
               root   e:\wwwroot;
               index  index.html;
        }
}
```

这样如果访问http://localhost 就会默认访问到E盘wwwroot目录下面的index.html，如果一个网站只是静态页面的话，那么就可以通过这种方式来实现部署。

