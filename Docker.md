# Docker

[Docker: Accelerated, Containerized Application Development](https://www.docker.com/)

[GitHub - docker/docker-ce: This repository is deprecated and will be archived (Docker CE itself is NOT deprecated) see the https://github.com/docker/docker-ce/blob/master/README.md](https://github.com/docker/docker-ce)

![image-20221212210743682](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212210743682.png)

![image-20221213113557406](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213113557406.png)

[Docker Hub Container Image Library | App Containerization](https://hub.docker.com/)

## Docker 架构

Docker 使用**客户端-服务器 (C/S) 架构模式**，使用远程API来管理和创建Docker容器。

- **Docker 客户端(Client)** : Docker 客户端通过命令行或者其他工具使用 Docker SDK (https://docs.docker.com/develop/sdk/) 与 Docker 的守护进程通信。
- **Docker 主机(Host)** ：一个物理或者虚拟的机器用于执行 Docker 守护进程和容器。

![image-20230416100435961](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230416100435961.png)

Docker 包括**三个基本概念:**

- **镜像（Image）**：Docker 镜像（Image），就相当于是一个 root 文件系统。比如官方镜像 ubuntu:16.04 就包含了完整的一套 Ubuntu16.04 最小系统的 root 文件系统。
- **容器（Container）**：镜像（Image）和容器（Container）的关系，就像是面向对象程序设计中的类和实例一样，镜像是静态的定义，容器是镜像运行时的实体。容器可以被创建、启动、停止、删除、暂停等。
- **仓库（Repository）**：仓库可看成一个代码控制中心，用来保存镜像。

Docker 使用客户端-服务器 (C/S) 架构模式，使用远程API来管理和创建Docker容器。

Docker 容器通过 Docker 镜像来创建。

容器与镜像的关系类似于面向对象编程中的对象与类。

| Docker | 面向对象 |
| :----- | :------- |
| 容器   | 对象     |
| 镜像   | 类       |

![image-20221212231228057](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212231228057.png)

|          概念          | 说明                                                         |
| :--------------------: | :----------------------------------------------------------- |
|  Docker 镜像(Images)   | Docker 镜像是用于创建 Docker 容器的模板，比如 Ubuntu 系统。  |
| Docker 容器(Container) | 容器是独立运行的一个或一组应用，是镜像运行时的实体。         |
| Docker 客户端(Client)  | Docker 客户端通过命令行或者其他工具使用 Docker SDK (https://docs.docker.com/develop/sdk/) 与 Docker 的守护进程通信。 |
|   Docker 主机(Host)    | 一个物理或者虚拟的机器用于执行 Docker 守护进程和容器。       |
|    Docker Registry     | Docker 仓库用来保存镜像，可以理解为代码控制中的代码仓库。Docker Hub([https://hub.docker.com](https://hub.docker.com/)) 提供了庞大的镜像集合供使用。一个 Docker Registry 中可以包含多个仓库（Repository）；每个仓库可以包含多个标签（Tag）；每个标签对应一个镜像。通常，一个仓库会包含同一个软件不同版本的镜像，而标签就常用于对应该软件的各个版本。我们可以通过 **<仓库名>:<标签>** 的格式来指定具体是这个软件哪个版本的镜像。如果不给出标签，将以 **latest** 作为默认标签。 |
|     Docker Machine     | Docker Machine是一个简化Docker安装的命令行工具，通过一个简单的命令行即可在相应的平台上安装Docker，比如VirtualBox、 Digital Ocean、Microsoft Azure。 |

## Linux Cent OS 7 Install

**安装 Docker Engine-Community	使用 Docker 仓库进行安装**

卸载老版本

```
 sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

安装所需要的软件包

```
yum -y install gcc

yum -y install gcc-c++
```

设置仓库

```
阿里云
$ sudo yum-config-manager \
    --add-repo \
    http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    
清华大学源
$ sudo yum-config-manager \
    --add-repo \
    https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/docker-ce.repo
```

更新yum元件包索引

```
yum makecache fast
```

安装 Docker Engine-Community 最近版本

```
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

![image-20221212230745921](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212230745921.png)

启动 Docker

```
$ sudo systemctl start docker
```

![image-20221212230952197](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212230952197.png)

查看版本

```
[root@192 ~]# docker version
```

![image-20221212231058720](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212231058720.png)

Hello World

![image-20221212231915265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212231915265.png)

![image-20221213081230899](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213081230899.png)

## Docker 镜像加速

阿里云镜像获取地址：https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors，登陆后，左侧菜单选中镜像加速器就可以看到你的专属地址了

![image-20221212232640952](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212232640952.png)

可以通过修改daemon配置文件/etc/docker/daemon.json来使用加速器

```
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://6tkr32bt.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

**检查加速器是否生效**

```
docker info
```

![image-20221212232957453](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221212232957453.png)

## Docker常用命令★

[Docker 命令大全 | 菜鸟教程 (runoob.com)](https://www.runoob.com/docker/docker-command-manual.html)

![image-20221213105701021](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213105701021.png)

![image-20221213105733766](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213105733766.png)

### 帮助启动类命令

```
启动
systemctl start docker

停止
systemctl stop docker

重启
systemctl restart docker

查看状态
systemctl status docker

开启开机启动
systemctl enable docker

查看概要信息
docker info

帮助文档
docker --help

具体命令的帮助文档
docker 具体命令 --help
```

### 镜像命令

**docker images :** 列出本地镜像。

```
docker images [OPTIONS] [REPOSITORY[:TAG]]

-a :列出本地所有的镜像（含中间映像层，默认情况下，过滤掉中间映像层）；

--digests :显示镜像的摘要信息；

-f :显示满足条件的镜像；

--format :指定返回值的模板文件；

--no-trunc :显示完整的镜像信息；

-q :只显示镜像ID。
```

![image-20221213082943563](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213082943563.png)

列出本地镜像中REPOSITORY为ubuntu的镜像列表。

```
root@runoob:~# docker images  ubuntu
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              14.04               90d5884b1ee0        9 weeks ago         188 MB
ubuntu              15.10               4e3b13c8a266        3 months ago        136.3 MB
```

**docker search :** 从Docker Hub查找镜像

```
docker search [OPTIONS] TERM

--automated :只列出 automated build类型的镜像；

--no-trunc :显示完整的镜像描述；

-f <过滤条件>:列出收藏数不小于指定值的镜像。
```

从 Docker Hub 查找所有镜像名包含 java，并且收藏数大于 10 的镜像

```
runoob@runoob:~$ docker search -f stars=10 java
NAME                  DESCRIPTION                           STARS   OFFICIAL   AUTOMATED
java                  Java is a concurrent, class-based...   1037    [OK]       
anapsix/alpine-java   Oracle Java 8 (and 7) with GLIBC ...   115                [OK]
develar/java                                                 46                 [OK]
isuper/java-oracle    This repository contains all java...   38                 [OK]
lwieske/java-8        Oracle Java 8 Container - Full + ...   27                 [OK]
nimmis/java-centos    This is docker images of CentOS 7...   13                 [OK]

NAME: 镜像仓库源的名称

DESCRIPTION: 镜像的描述

OFFICIAL: 是否 docker 官方发布

stars: 类似 Github 里面的 star，表示点赞、喜欢的意思。

AUTOMATED: 自动构建。
```

只看前五个 使用--limit进行限制

```
[root@192 ~]# docker search --limit 5 redis
NAME                     DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
redis                    Redis is an open source key-value store that…   11651     [OK]       
redislabs/redisinsight   RedisInsight - The GUI for Redis                75                   
redislabs/redisearch     Redis With the RedisSearch module pre-loaded…   56                   
redislabs/redis          Clustered in-memory database engine compatib…   36                   
redislabs/rebloom        A probablistic datatypes module for Redis       21                   [OK]
```

**docker pull :** 从镜像仓库中拉取或者更新指定镜像

```
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
未指定tag的默认拉取最新的版本

-a :拉取所有 tagged 镜像

--disable-content-trust :忽略镜像的校验,默认开启
```

用于获取指定编译平台的镜像：

```
docker pull --platform=arm64|amd64... image_name
```

**docker push :** 将本地的镜像上传到镜像仓库,要先登陆到镜像仓库

```
docker push [OPTIONS] NAME[:TAG]

--disable-content-trust :忽略镜像的校验,默认开启
```

上传本地镜像myapache:v1到镜像仓库中。

```
docker push myapache:v1
```

**docker system df ：**查看镜像/容器/数据卷所占用空间

```
[root@192 ~]# docker system df
TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          1         1         13.26kB   0B (0%)
Containers      1         0         0B        0B
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
```

**docker rmi :** 删除本地一个或多个镜像。

```
docker rmi [OPTIONS] IMAGE [IMAGE...]

-f :强制删除；

--no-prune :不移除该镜像的过程镜像，默认移除；
```

强制删除本地镜像 runoob/ubuntu:v4。

```
root@runoob:~# docker rmi -f runoob/ubuntu:v4
Untagged: runoob/ubuntu:v4
Deleted: sha256:1c06aa18edee44230f93a90a7d88139235de12cd4c089d41eed8419b503072be
Deleted: sha256:85feb446e89a28d58ee7d80ea5ce367eebb7cec70f0ec18aa4faa874cbd97c73
```

删除所有本地镜像

```
[root@192 ~]# docker rmi -f $(docker images -qa)
Untagged: hello-world:latest
Untagged: hello-world@sha256:faa03e786c97f07ef34423fccceeec2398ec8a5759259f94d99078f264e9d7af
Deleted: sha256:feb5d9fea6a5e9606aa995e879d862b825965ba48de054caab5ef356dc6b3412
```

**docker prune 命令：**prune 命令用来删除不再使用的 docker 对象。

删除所有未被 tag 标记和未被容器使用的镜像:

```
$ docker image prune
WARNING! This will remove all dangling images.
Are you sure you want to continue? [y/N] y
```

删除所有未被容器使用的镜像:

```
$ docker image prune -a
```

删除所有停止运行的容器:

```
$ docker container prune
```

删除所有未被挂载的卷:

```
$ docker volume prune
```

删除所有网络:

```
$ docker network prune
```

删除 docker 所有资源:

```
$ docker system prune
```

### 容器命令

**docker run ：**创建一个新的容器并运行一个命令

```
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

-a stdin: 指定标准输入输出内容类型，可选 STDIN/STDOUT/STDERR 三项；

-d: 后台运行容器，并返回容器ID；

-i: 以交互模式运行容器，通常与 -t 同时使用；

-P: 随机端口映射，容器内部端口随机映射到主机的端口

-p: 指定端口映射，格式为：主机(宿主)端口:容器端口

-t: 为容器重新分配一个伪输入终端，通常与 -i 同时使用；

--name="nginx-lb": 为容器指定一个名称；

--dns 8.8.8.8: 指定容器使用的DNS服务器，默认和宿主一致；

--dns-search example.com: 指定容器DNS搜索域名，默认和宿主一致；

-h "mars": 指定容器的hostname；

-e username="ritchie": 设置环境变量；

--env-file=[]: 从指定文件读入环境变量；

--cpuset="0-2" or --cpuset="0,1,2": 绑定容器到指定CPU运行；

-m :设置容器使用内存最大值；

--net="bridge": 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型；

--link=[]: 添加链接到另一个容器；

--expose=[]: 开放一个端口或一组端口；

--volume , -v: 绑定一个卷
```

使用docker镜像Ubuntu容器；	交互式启动并在容器内执行/bin/bash（bash）命令;	指定name为myubuntu

```
[root@192 ~]# docker run --name myubuntu -it ubuntu bash
root@3988f7d93f0e:/# ls
bin   dev  home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  etc  lib   lib64  media   opt  root  sbin  sys  usr
```

```
[root@192 ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS         PORTS     NAMES
3988f7d93f0e   ubuntu    "bash"    3 minutes ago   Up 3 minutes             myubuntu
```

**exit：**从容其中退出并停止容器 **Ctrl + q + p：**从容器中退出不停止容器

```
root@3988f7d93f0e:/# exit
exit
[root@192 ~]# 
```

绑定容器的 8080 端口，并将其映射到本地主机 127.0.0.1 的 80 端口上。

```
$ docker run -p 127.0.0.1:80:8080/tcp ubuntu bash
```

使用镜像 nginx:latest，以后台模式启动一个容器,将容器的 80 端口映射到主机的 80 端口,主机的目录 /data 映射到容器的 /data。

```
docker run -p 80:80 -v /data:/data -d nginx:latest
```

![image-20221213093702964](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213093702964.png)

**docker rm ：**删除一个或多个容器。

```
docker rm [OPTIONS] CONTAINER [CONTAINER...]

-f :通过 SIGKILL 信号强制删除一个运行中的容器。

-l :移除容器间的网络连接，而非容器本身。

-v :删除与容器关联的卷。
```

删除所有已经停止的容器：

```
docker rm $(docker ps -a -q)
```

**docker ps :** 列出容器

```
docker ps [OPTIONS]

-a :显示所有的容器，包括未运行的。

-f :根据条件过滤显示的内容。

--format :指定返回值的模板文件。

-l :显示最近创建的容器。

-n :列出最近创建的n个容器。

--no-trunc :不截断输出。

-q :静默模式，只显示容器编号。

-s :显示总的文件大小。
```

**docker start** :启动一个或多个已经被停止的容器

**docker stop** :停止一个运行中的容器

**docker restart** :重启容器

```
docker start [OPTIONS] CONTAINER [CONTAINER...]
docker stop [OPTIONS] CONTAINER [CONTAINER...]
docker restart [OPTIONS] CONTAINER [CONTAINER...]
```

**docker kill** :杀掉一个运行中的容器。

```
docker kill [OPTIONS] CONTAINER [CONTAINER...]
```

**docker pause** :暂停容器中所有的进程。

**docker unpause** :恢复容器中所有的进程。

```
docker pause CONTAINER [CONTAINER...]
docker unpause CONTAINER [CONTAINER...]
```

**docker exec ：**在运行的容器中执行命令

```
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

-d :分离模式: 在后台运行

-i :即使没有附加也保持STDIN 打开

-t :分配一个伪终端
```

在容器 mynginx 中以交互模式执行容器内 /root/runoob.sh 脚本:

```
runoob@runoob:~$ docker exec -it mynginx /bin/sh /root/runoob.sh
http://www.runoob.com/
```

在容器 mynginx 中开启一个交互模式的终端:

```
runoob@runoob:~$ docker exec -i -t  mynginx /bin/bash
root@b1a0703e41e7:/#
```

也可以通过 **docker ps -a** 命令查看已经在运行的容器，然后使用容器 ID 进入容器。

查看已经在运行的容器 ID：

```
# docker ps -a 
...
9df70f9a0714        openjdk             "/usercode/script.sh…" 
...
```

第一列的 9df70f9a0714 就是容器 ID。

通过 exec 命令对指定的容器执行 bash:

```
# docker exec -it 9df70f9a0714 /bin/bash
```

**docker inspect 容器**：检阅容器

```
docker inspect redis
```

**容器自动启动**

```
docker udpate (containerId) --restart=always
```

## Docker镜像

**镜像**：是一种**轻量级，可执行的独立软件包**，它包含运行某个软件所需的所有内容，我们把应用程序和配置依赖打包好成一个可交付的运行环境（包括**代码，运行时需要的库，环境变量和配置文件**等），这个打包好的运行环境就是image镜像文件

![image-20221213112935552](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213112935552.png)

### 分层

![image-20221213115711428](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213115711428.png)

镜像采用分层的最大好处就是共享资源，方便复制迁移，就是为了复用

多个镜像都是由相同的base镜像构建而来，那么Docker Host只需在磁盘中保存一份base镜像；

同时内存中也只需加载一份base镜像，就可以为所有的容器服务。并且镜像每一层都可以被共享

**镜像层：只读层**

**容器层：可写层**

![image-20221213114830383](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213114830383.png)

### Docker镜像加载原理

![image-20221213115716043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221213115716043.png)

docker镜像实际是由一层一层的文件系统组成，这种层级的文件系统称之为UnionFS

BootFS（Boot File System）主要包含BootLoader和Kernel;BootLoader主要是引导加载kernel，Linux刚启动时会加载bootfs文件系统。

在Docker镜像的最底层是引导文件系统bootfs。这一层与典型的Linux系统一样，包含boot加载器和内核。当boot加载完成之后，整个内核就在内存中了，此时内存的是哟权已由bootfs转交给内核，此时系统也会卸载bootfs。

rootfs可以很小；只需要包括最基本的命令，工具和程序库即可；因为最底层直接使用了host宿主机的kernel，自己只需要提供rootfs即可；

例如不同的Linux发行版本，bootfs基本一致，rootfs会有差别，因此不同的发行版可以共用bootfs。

## 本地镜像发布到aliyun

![image-20221215100748194](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215100748194.png)

## 私服仓库

## 容器卷★

![image-20221215102642770](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215102642770.png)

![image-20221215102750514](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215102750514.png)

### 宿主机和容器之间添加映射容器卷

**tip:	--privileged（开启权限）**

```
dicker run --name redis -p 6379:6379 --privileged=true -v 宿主机路径目录:容器内路径目录 -d redis
```

### 读写规则rw/ro

**默认支持主机和容器互通读写**

```
dicker run --name redis -p 6379:6379 --privileged=true -v 宿主机路径目录:容器内路径目录:rw -d redis
```

**限制容器内的写**

**此时宿主机写入的内容可以同步到容器内**，容器可以读取到；容器不能写

![image-20221215103636796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215103636796.png)

### 容器卷的继承和共享

**使用	--volume-from 容器01**

**照搬容器01的映射卷规则**

![image-20221215104959713](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215104959713.png)

## Docker容器下的复杂安装



## DockerFile★

[Docker Dockerfile | 菜鸟教程 (runoob.com)](https://www.runoob.com/docker/docker-dockerfile.html)

> DockerFile 是一个用来构建镜像的文本文件
>

### Dockerfile指令

#### Dockerfile指令摘要：

- FROM- 镜像从那里来

- MAINTAINER- 镜像维护者信息

- RUN- 构建镜像执行的命令，每一次RUN都会构建一层

- CMD- 容器启动的命令，如果有多个则以最后一个为准，也可以为ENTRYPOINT提供参数

- VOLUME- 定义数据卷，如果没有定义则使用默认

- USER- 指定后续执行的用户组和用户

- WORKDIR- 切换当前执行的工作目录

- HEALTHCHECH- 健康检测指令

- ARG- 变量属性值，但不在容器内部起作用

- EXPOSE- 暴露端口

- ENV- 变量属性值，容器内部也会起作用

- ADD- 添加文件，如果是压缩文件也解压

- COPY- 添加文件，以复制的形式

- ENTRYPOINT- 容器进入时执行的命令

#### Dockerfile指令：

- FROM

构建镜像基于哪个镜像

- MAINTAINER

镜像维护者姓名或邮箱地址

- RUN

构建镜像时运行的指令

- CMD

运行容器时执行的shell环境

- VOLUME

指定容器挂载点到宿主机自动生成的目录或其他容器

- USER

为RUN、CMD、和 ENTRYPOINT 执行命令指定运行用户

- WORKDIR

为 RUN、CMD、ENTRYPOINT、COPY 和 ADD 设置工作目录，就是切换目录

- HEALTHCHECH

健康检查

- ARG

构建时指定的一些参数

- EXPOSE

声明容器的服务端口（仅仅是声明）

- ENV

设置容器环境变量

- ADD

拷贝文件或目录到容器中，如果是URL或压缩包便会自动下载或自动解压

- COPY

拷贝文件或目录到容器中，跟ADD类似，但不具备自动下载或解压的功能

- ENTRYPOINT

运行容器时执行的shell命令

### 使用 Dockerfile 定制Centos镜像

![image-20221216122145419](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216122145419.png)

![image-20221216122440141](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216122440141.png)

DockerFile文本文件

```yaml
FROM centos
MAINTAINER zzyy 
ENV MYPATH /usr/localWORKDIR 
$MYPATH 
#安装vim编辑器
RUN yum -y install vim
#安装ifconfig命令查看网络IP
RUN yum -y install net-tools
#安装java8及lib库
RUN yum -y install glibc.i686RUN mkdir /usr/local/java
#ADD 是相对路径jar,把jdk-8u171-linux-x64.tar.gz添加到容器中,安装包必须要和Dockerfile文件在同一位置
ADD jdk-8u171-linux-x64.tar.gz /usr/local/java/
#配置java环境变量
ENV JAVA_HOME /usr/local/java/jdk1.8.0_171
ENV JRE_HOME $JAVA_HOME/jre
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib:$CLASSPATHENV PATH $JAVA_HOME/bin:$PATH 
EXPOSE 80 
CMD echo $MYPATHCMD echo "success--------------ok"CMD /bin/bash 
```

### 将微服务构建成镜像

![image-20221216122148499](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216122148499.png)

将编写好的微服务打成jar包 发送至Linux中的MyDocker文件夹 

![image-20221216121900159](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216121900159.png)

并vim Dockerfile 编写构建文本文件的内容

![image-20221216121839375](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216121839375.png)

![image-20221216122200324](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216122200324.png)

![image-20221215165944872](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215165944872.png)

![image-20221215174134019](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215174134019.png)

## 虚悬镜像

### 查看虚悬镜像

```
docker image ls -f dangling=true
```

### prune掉虚悬镜像

```
docker image prune
```

![image-20221215173956773](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221215173956773.png)

## Docker部署实战★

### Java项目部署

![image-20221216082950543](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216082950543.png)

![image-20221216082153225](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216082153225.png)

![image-20221216082258222](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216082258222.png)

```bash
docker build -t springboot_demo1_docker:1.1 .
```

![image-20221216082336420](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216082336420.png)

![image-20221216082704103](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216082704103.png)

### MySQL部署

```shell
[root@localhost mysql]# pwd
/root/dockerMetaData/mysql
[root@localhost mysql]# ls
conf  Data  log

[root@localhost mysql]# docker run -d \
> -p 3306:3306 \
> -e MYSQL_ROOT_PASSWORD=root \
> -v $pwd/conf/my.cnf:/etc/mysql/my.cnf:rw \
> -v $pwd/Data:/var/lib/mysql \
> -v $pwd/log:/var/log/mysql \
> --name mysql8 \
> c71276df4a87
d30f2ce80fe03301e6e69cfdce57a680c98aecbe54e9a5c9f285e2f1add58673

[root@localhost mysql]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                  NAMES
d30f2ce80fe0   c71276df4a87   "docker-entrypoint.s…"   2 seconds ago   Up 2 seconds   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql8

[root@localhost redis]# docker exec -it mysql8 /bin/bash
bash-4.4# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 8.0.33 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

![image-20230609104012021](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230609104012021.png)

### Redis部署

> [raw.githubusercontent.com/redis/redis/7.0/redis.conf](https://raw.githubusercontent.com/redis/redis/7.0/redis.conf)
>
> 提前准备对应版本的 redis.conf 配置文件 用于配置和启动redis
>
> ![image-20230609163444847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230609163444847.png)

```shell
[root@localhost redis]# ls
conf  data
[root@localhost redis]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
mysql        8         c71276df4a87   4 days ago    565MB
redis        latest    0ec8ab59a35f   2 weeks ago   117MB

[root@localhost redis]# docker run -d \
> -p 6379:6379 \
> -v $pwd/conf/redis.conf:/etc/redis/redis.conf \
> -v $pwd/data:/data \
> --name redis 

> 0ec8ab59a35f \
> redis-server $pwd/conf/redis.conf

[root@localhost redis]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                  NAMES
8995fb9bbde6   0ec8ab59a35f   "docker-entrypoint.s…"   3 seconds ago   Up 2 seconds   0.0.0.0:6379->6379/tcp, :::6379->6379/tcp              redis
d30f2ce80fe0   c71276df4a87   "docker-entrypoint.s…"   6 hours ago     Up 6 hours     0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql8

[root@localhost redis]# docker exec -it redis /bin/bash
root@8995fb9bbde6:/data# 

[root@localhost redis]# docker exec -it redis redis-cli
127.0.0.1:6379> 
```

![image-20230609162444990](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230609162444990.png)

### MQ部署

### Nginx部署

```shell
[root@localhost nginx]# pwd
/root/dockerMetaData/nginx
[root@localhost nginx]# ll
total 0
drwxrwxrwx. 2 root root 6 Jun 13 23:00 conf
drwxrwxrwx. 2 root root 6 Jun 13 23:01 conf.d
drwxrwxrwx. 2 root root 6 Jun 13 23:00 html
drwxrwxrwx. 2 root root 6 Jun 13 23:00 logs
[root@localhost nginx]# 

[root@localhost nginx]# docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
759700526b78: Pull complete 
4fabad4a1317: Pull complete 
1150b893b52b: Pull complete 
e75fa5822000: Pull complete 
1595b4d83afa: Pull complete 
1810e754f450: Pull complete 
Digest: sha256:96b005578b567542e03c754ec1cb1dd9b1d57d5c5d4e50b8e8c59f00dfc9d99b
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
[root@localhost nginx]# docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    7d3c40f240e1   23 hours ago   143MB
mysql        8         c71276df4a87   9 days ago     565MB
redis        latest    0ec8ab59a35f   3 weeks ago    117MB
[root@localhost nginx]# 

[root@localhost nginx]# docker run -d --name nginx -p 80:80 nginx
7c1dc4ac30b52bfa15bd77f128aa2729d4f2a6657ec1bb75b00e99e8eabfd34c
[root@localhost nginx]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                  NAMES
7c1dc4ac30b5   nginx          "/docker-entrypoint.…"   4 seconds ago   Up 3 seconds   0.0.0.0:80->80/tcp, :::80->80/tcp                      nginx
d30f2ce80fe0   c71276df4a87   "docker-entrypoint.s…"   5 days ago      Up 4 hours     0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql8

[root@localhost nginx]# docker cp nginx:/etc/nginx/nginx.conf /root/dockerMetaData/nginx/conf/nginx.conf
Successfully copied 2.56kB to /root/dockerMetaData/nginx/conf/nginx.conf
[root@localhost nginx]# docker cp nginx:/etc/nginx/nginx.conf /root/dockerMetaData/nginx/conf/nginx.conf
Successfully copied 2.56kB to /root/dockerMetaData/nginx/conf/nginx.conf
[root@localhost nginx]# docker cp nginx:/etc/nginx/conf.d /root/dockerMetaData/nginx/conf.d
Successfully copied 1.54kB to /root/dockerMetaData/nginx/conf.d
[root@localhost nginx]# docker cp nginx:/usr/share/nginx/html /root/dockerMetaData/nginx/html
Successfully copied 1.54kB to /root/dockerMetaData/nginx/html

[root@localhost nginx]# ls
conf  conf.d  html  logs
[root@localhost nginx]# cd conf
[root@localhost conf]# ls
nginx.conf
[root@localhost conf]# 

[root@localhost conf]# docker stop nginx 
nginx
[root@localhost conf]# docker rm nginx 
nginx
[root@localhost conf]# 

[root@localhost nginx]# docker run -d \
> -p 80:80 \
> -v /root/dockerMetaData/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
> -v /root/dockerMetaData/nginx/conf.d:/etc/nginx/conf.d \
> -v /root/dockerMetaData/nginx/html:/usr/share/nginx/html \
> -v /root/dockerMetaData/nginx/logs:/var/log/nginx \
> --name nginx \
> nginx

d5b38fdc7048a5eab073bccf090c3a9e078e7e5a3413c0e1e9d5087d61f2da9d
[root@localhost nginx]# docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                  NAMES
d5b38fdc7048   nginx          "/docker-entrypoint.…"   3 seconds ago   Up 3 seconds   0.0.0.0:80->80/tcp, :::80->80/tcp                      nginx
d30f2ce80fe0   c71276df4a87   "docker-entrypoint.s…"   5 days ago      Up 5 hours     0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql8
[root@localhost nginx]# 

```



### Elasticsearch部署

## Docker NetWork★

[Docker：网络模式详解 - Gringer - 博客园 (cnblogs.com)](https://www.cnblogs.com/zuxing/articles/8780661.html)

![image-20221216114714529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216114714529.png)

安装Docker时，它会自动创建三个网络，bridge（创建容器默认连接到此网络）、 none 、host

host：容器将不会虚拟出自己的网卡，配置自己的IP等，而是使用宿主机的IP和端口。

Container：创建的容器不会创建自己的网卡，配置自己的IP，而是和一个指定的容器共享IP、端口范围。

None：该模式关闭了容器的网络功能。

Bridge：此模式会为每一个容器分配、设置IP等，并将容器连接到一个docker0虚拟网桥，通过docker0网桥以及Iptables nat表配置与宿主机通信。

以上都是不用动手的，真正需要配置的是自定义网络。

![image-20221216115110672](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115110672.png)

### Bridge模式☆

![image-20221216115303240](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115303240.png)

![image-20221216115239162](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115239162.png)



### 自定义模式☆

![image-20221216114853228](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216114853228.png)

![image-20221216115556439](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115556439.png)

![image-20221216115539819](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115539819.png)



### Host模式

![image-20221216115202752](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115202752.png)

### Container模式

![image-20221216115219706](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115219706.png)

### None模式

![image-20221216115230339](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216115230339.png)

## Docker Compose★

[Install the Compose standalone | Docker Documentation](https://docs.docker.com/compose/install/other/)

[Docker Compose | 菜鸟教程 (runoob.com)](https://www.runoob.com/docker/docker-compose.html)

### 安装

```
curl -SL https://github.com/docker/compose/releases/download/v2.14.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose

[root@192 nacos]# docker-compose version
Docker Compose version v2.14.0
```

### 卸载

If you used `curl` to install Compose CLI plugin, to uninstall it, run:

```
$ rm $DOCKER_CONFIG/cli-plugins/docker-compose
```

Or, if you have installed Compose for all users, run:

Remove for all users

```
$ rm /usr/local/lib/docker/cli-plugins/docker-compose
```

### 核心概念

#### 一个文件

docker-compose.yml

#### 两个要素

服务（service）：一个个的应用容器实例（mysql容器/redis容器/nginx容器）

工程（project）：由一组关联的应用容器组成的完整业务单元在docker-compose.yml中定义

### Docker-Compose常用命令

Compose常用命令



docker-compose -h              # 查看帮助



**docker-compose up**              # **启动**所有docker-compose服务



**docker-compose up -d**            # **启动**所有docker-compose服务并**后台运行**



docker-compose down             # 停止并删除容器、网络、卷、镜像。



docker-compose exec yml里面的服务id         # 进入容器实例内部 docker-compose exec docker-compose.yml文件中写的服务id /bin/bash



**docker-compose ps**           # **展示**当前docker-compose编排过的**运行的所有容器**



**docker-compose top**           # **展示**当前docker-compose**编排过的容器进程** 



**docker-compose logs yml里面的服务id**   # **查看容器输出日志**



docker-compose config   # 检查配置



**docker-compose config -q** # **检查配置，有问题才有输出**



**docker-compose restart**  # **重启**服务



**docker-compose start**   # **启动**服务



**docker-compose stop**   # **停止**服务 

### docker-compose.yml配置指令

**version**

指定本 yml 依从的 compose 哪个版本制定的。

**build**

指定为构建镜像上下文路径：

例如 webapp 服务，指定为从上下文路径 ./dir/Dockerfile 所构建的镜像：

```
version: "3.7"
services:
  webapp:
    build: ./dir
```

或者，作为具有在上下文指定的路径的对象，以及可选的 Dockerfile 和 args：

```
version: "3.7"
services:
  webapp:
    build:
      context: ./dir
      dockerfile: Dockerfile-alternate
      args:
        buildno: 1
      labels:
        - "com.example.description=Accounting webapp"
        - "com.example.department=Finance"
        - "com.example.label-with-empty-value"
      target: prod
```

- context：上下文路径。
- dockerfile：指定构建镜像的 Dockerfile 文件名。
- args：添加构建参数，这是只能在构建过程中访问的环境变量。
- labels：设置构建镜像的标签。
- target：多层构建，可以指定构建哪一层。

**cap_add，cap_drop**

添加或删除容器拥有的宿主机的内核功能。

```
cap_add:
  - ALL # 开启全部权限

cap_drop:
  - SYS_PTRACE # 关闭 ptrace权限
```

**cgroup_parent**

为容器指定父 cgroup 组，意味着将继承该组的资源限制。

```
cgroup_parent: m-executor-abcd
```

**command**

覆盖容器启动的默认命令。

```
command: ["bundle", "exec", "thin", "-p", "3000"]
```

**container_name**

指定自定义容器名称，而不是生成的默认名称。

```
container_name: my-web-container
```

**depends_on**

设置依赖关系。

- docker-compose up ：以依赖性顺序启动服务。在以下示例中，先启动 db 和 redis ，才会启动 web。
- docker-compose up SERVICE ：自动包含 SERVICE 的依赖项。在以下示例中，docker-compose up web 还将创建并启动 db 和 redis。
- docker-compose stop ：按依赖关系顺序停止服务。在以下示例中，web 在 db 和 redis 之前停止。

```
version: "3.7"
services:
  web:
    build: .
    depends_on:
      - db
      - redis
  redis:
    image: redis
  db:
    image: postgres
```

注意：web 服务不会等待 redis db 完全启动 之后才启动。

**deploy**

指定与服务的部署和运行有关的配置。只在 swarm 模式下才会有用。

```
version: "3.7"
services:
  redis:
    image: redis:alpine
    deploy:
      mode：replicated
      replicas: 6
      endpoint_mode: dnsrr
      labels: 
        description: "This redis service label"
      resources:
        limits:
          cpus: '0.50'
          memory: 50M
        reservations:
          cpus: '0.25'
          memory: 20M
      restart_policy:
        condition: on-failure
        delay: 5s
        max_attempts: 3
        window: 120s
```

可以选参数：

**endpoint_mode**：访问集群服务的方式。

```
endpoint_mode: vip 
# Docker 集群服务一个对外的虚拟 ip。所有的请求都会通过这个虚拟 ip 到达集群服务内部的机器。
endpoint_mode: dnsrr
# DNS 轮询（DNSRR）。所有的请求会自动轮询获取到集群 ip 列表中的一个 ip 地址。
```

**labels**：在服务上设置标签。可以用容器上的 labels（跟 deploy 同级的配置） 覆盖 deploy 下的 labels。

**mode**：指定服务提供的模式。

- **replicated**：复制服务，复制指定服务到集群的机器上。

- **global**：全局服务，服务将部署至集群的每个节点。

- 图解：下图中黄色的方块是 replicated 模式的运行情况，灰色方块是 global 模式的运行情况。

  ![img](https://www.runoob.com/wp-content/uploads/2019/11/docker-composex.png)

**replicas：mode** 为 replicated 时，需要使用此参数配置具体运行的节点数量。

**resources**：配置服务器资源使用的限制，例如上例子，配置 redis 集群运行需要的 cpu 的百分比 和 内存的占用。避免占用资源过高出现异常。

**restart_policy**：配置如何在退出容器时重新启动容器。

- condition：可选 none，on-failure 或者 any（默认值：any）。
- delay：设置多久之后重启（默认值：0）。
- max_attempts：尝试重新启动容器的次数，超出次数，则不再尝试（默认值：一直重试）。
- window：设置容器重启超时时间（默认值：0）。

**rollback_config**：配置在更新失败的情况下应如何回滚服务。

- parallelism：一次要回滚的容器数。如果设置为0，则所有容器将同时回滚。
- delay：每个容器组回滚之间等待的时间（默认为0s）。
- failure_action：如果回滚失败，该怎么办。其中一个 continue 或者 pause（默认pause）。
- monitor：每个容器更新后，持续观察是否失败了的时间 (ns|us|ms|s|m|h)（默认为0s）。
- max_failure_ratio：在回滚期间可以容忍的故障率（默认为0）。
- order：回滚期间的操作顺序。其中一个 stop-first（串行回滚），或者 start-first（并行回滚）（默认 stop-first ）。

**update_config**：配置应如何更新服务，对于配置滚动更新很有用。

- parallelism：一次更新的容器数。
- delay：在更新一组容器之间等待的时间。
- failure_action：如果更新失败，该怎么办。其中一个 continue，rollback 或者pause （默认：pause）。
- monitor：每个容器更新后，持续观察是否失败了的时间 (ns|us|ms|s|m|h)（默认为0s）。
- max_failure_ratio：在更新过程中可以容忍的故障率。
- order：回滚期间的操作顺序。其中一个 stop-first（串行回滚），或者 start-first（并行回滚）（默认stop-first）。

**注**：仅支持 V3.4 及更高版本。

**devices**

指定设备映射列表。

```
devices:
  - "/dev/ttyUSB0:/dev/ttyUSB0"
```

**dns**

自定义 DNS 服务器，可以是单个值或列表的多个值。

```
dns: 8.8.8.8

dns:
  - 8.8.8.8
  - 9.9.9.9
```

**dns_search**

自定义 DNS 搜索域。可以是单个值或列表。

```
dns_search: example.com

dns_search:
  - dc1.example.com
  - dc2.example.com
```

**entrypoint**

覆盖容器默认的 entrypoint。

```
entrypoint: /code/entrypoint.sh
```

也可以是以下格式：

```
entrypoint:
    - php
    - -d
    - zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20100525/xdebug.so
    - -d
    - memory_limit=-1
    - vendor/bin/phpunit
```

**env_file**

从文件添加环境变量。可以是单个值或列表的多个值。

```
env_file: .env
```

也可以是列表格式：

```
env_file:
  - ./common.env
  - ./apps/web.env
  - /opt/secrets.env
```

**environment**

添加环境变量。您可以使用数组或字典、任何布尔值，布尔值需要用引号引起来，以确保 YML 解析器不会将其转换为 True 或 False。

```
environment:
  RACK_ENV: development
  SHOW: 'true'
```

**expose**

暴露端口，但不映射到宿主机，只被连接的服务访问。

仅可以指定内部端口为参数：

```
expose:
 - "3000"
 - "8000"
```

**extra_hosts**

添加主机名映射。类似 docker client --add-host。

```
extra_hosts:
 - "somehost:162.242.195.82"
 - "otherhost:50.31.209.229"
```

以上会在此服务的内部容器中 /etc/hosts 创建一个具有 ip 地址和主机名的映射关系：

```
162.242.195.82  somehost
50.31.209.229   otherhost
```

**healthcheck**

用于检测 docker 服务是否健康运行。

```
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost"] # 设置检测程序
  interval: 1m30s # 设置检测间隔
  timeout: 10s # 设置检测超时时间
  retries: 3 # 设置重试次数
  start_period: 40s # 启动后，多少秒开始启动检测程序
```

**image**

指定容器运行的镜像。以下格式都可以：

```
image: redis
image: ubuntu:14.04
image: tutum/influxdb
image: example-registry.com:4000/postgresql
image: a4bc65fd # 镜像id
```

**logging**

服务的日志记录配置。

driver：指定服务容器的日志记录驱动程序，默认值为json-file。有以下三个选项

```
driver: "json-file"
driver: "syslog"
driver: "none"
```

仅在 json-file 驱动程序下，可以使用以下参数，限制日志得数量和大小。

```
logging:
  driver: json-file
  options:
    max-size: "200k" # 单个文件大小为200k
    max-file: "10" # 最多10个文件
```

当达到文件限制上限，会自动删除旧得文件。

syslog 驱动程序下，可以使用 syslog-address 指定日志接收地址。

```
logging:
  driver: syslog
  options:
    syslog-address: "tcp://192.168.0.42:123"
```

**network_mode**

设置网络模式。

```
network_mode: "bridge"
network_mode: "host"
network_mode: "none"
network_mode: "service:[service name]"
network_mode: "container:[container name/id]"
```

**networks**

配置容器连接的网络，引用顶级 networks 下的条目 。

```
services:
  some-service:
    networks:
      some-network:
        aliases:
         - alias1
      other-network:
        aliases:
         - alias2
networks:
  some-network:
    # Use a custom driver
    driver: custom-driver-1
  other-network:
    # Use a custom driver which takes special options
    driver: custom-driver-2
```

**aliases** ：同一网络上的其他容器可以使用服务名称或此别名来连接到对应容器的服务。

**restart**

- no：是默认的重启策略，在任何情况下都不会重启容器。
- always：容器总是重新启动。
- on-failure：在容器非正常退出时（退出状态非0），才会重启容器。
- unless-stopped：在容器退出时总是重启容器，但是不考虑在Docker守护进程启动时就已经停止了的容器

```
restart: "no"
restart: always
restart: on-failure
restart: unless-stopped
```

注：swarm 集群模式，请改用 restart_policy。

**secrets**

存储敏感数据，例如密码：

```
version: "3.1"
services:

mysql:
  image: mysql
  environment:
    MYSQL_ROOT_PASSWORD_FILE: /run/secrets/my_secret
  secrets:
    - my_secret

secrets:
  my_secret:
    file: ./my_secret.txt
```

**security_opt**

修改容器默认的 schema 标签。

```
security-opt：
  - label:user:USER   # 设置容器的用户标签
  - label:role:ROLE   # 设置容器的角色标签
  - label:type:TYPE   # 设置容器的安全策略标签
  - label:level:LEVEL  # 设置容器的安全等级标签
```

**stop_grace_period**

指定在容器无法处理 SIGTERM (或者任何 stop_signal 的信号)，等待多久后发送 SIGKILL 信号关闭容器。

```
stop_grace_period: 1s # 等待 1 秒
stop_grace_period: 1m30s # 等待 1 分 30 秒 
```

默认的等待时间是 10 秒。

**stop_signal**

设置停止容器的替代信号。默认情况下使用 SIGTERM 。

以下示例，使用 SIGUSR1 替代信号 SIGTERM 来停止容器。

```
stop_signal: SIGUSR1
```

**sysctls**

设置容器中的内核参数，可以使用数组或字典格式。

```
sysctls:
  net.core.somaxconn: 1024
  net.ipv4.tcp_syncookies: 0

sysctls:
  - net.core.somaxconn=1024
  - net.ipv4.tcp_syncookies=0
```

**tmpfs**

在容器内安装一个临时文件系统。可以是单个值或列表的多个值。

```
tmpfs: /run

tmpfs:
  - /run
  - /tmp
```

**ulimits**

覆盖容器默认的 ulimit。

```
ulimits:
  nproc: 65535
  nofile:
    soft: 20000
    hard: 40000
```

**volumes**

将主机的数据卷或着文件挂载到容器里。

```version
version: "3.7"
services:
  db:
    image: postgres:latest
    volumes:
      - "/localhost/postgres.sock:/var/run/postgres/postgres.sock"
      - "/localhost/data:/var/lib/postgresql/data"
```

### 运行实例

**1）将自己的微服务项目通过Dockerfile的形式构建成镜像**

![image-20221216120523673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120523673.png)

**2）编写docker-compose.yml文件**

![image-20221216120316245](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120316245.png)

![image-20221216120358566](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120358566.png)

![image-20221216120550430](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120550430.png)

```yaml
version: '3'

services: 
  microservice:
    image: springboot_demo1_docker:1.1
    container_name: ms01
    ports: 
      - "6001:6001"
    networks:
      - eddie_net
    depends_on:
      - redis
      - mysql

  redis:
    image: redis:latest
    container_name: redis_compose
    ports:
      - "6379:6379"
    volumes:
      - /mydata/redis_compose/data:/data
      - /mydata/redis_compose/conf/redis.conf:/etc/redis/redis.conf
    networks:
      - eddie_net
    command: redis-server /etc/redis/redis.conf

  mysql:
    image: mysql:8.0.18
    container_name: mysql_compose
    environment:
      MYSQL_ROOT_PASSWORD: 'root'
      MYSQL_ALLOW_EMPLY_PASSWORD: 'no'
      MYSQL_DATABASE: 'db2021'
      MYSQL_USER: 'eddie'
      MYSQL_PASSWORD: 'eddie'
    ports:
      - "3306:3306"
    volumes:
      - /mydata/mysql_compose/log:/var/log/mysql
      - /mydata/mysql_compose/data:/var/lib/mysql
      - /mydata/mysql_compose/conf:/var/etc/mysql
    networks:
      - eddie_net
    command: --default-authentication-plugin=mysql_native_password #解决外部无法访问

networks:
    eddie_net:
```

**3）启动docker-compose服务**

![image-20221216120618059](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120618059.png)

![image-20221216120643441](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120643441.png)

![image-20221216120818682](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221216120818682.png)
