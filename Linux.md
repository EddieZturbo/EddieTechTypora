# Linux

![image-20230402212655427](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402212655427.png)

## Linux Commands Cheat Sheet

https://www.linuxcool.com/

https://phoenixnap.com/kb/linux-commands#ftoc-heading-1

![image-20230402163930439](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/Screenshot 2023-04-02 at 17-48-19 LinuxCommands (1) - linux-commands-cheat-sheet-pdf.pdf.png)

### Directory Navigation

![image-20230402200400184](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402200400184.png)

> `cd  [destination] `
>
> 切换到指定的路径
>
> `cd .. `
>
> 回退到上一层路径
>
> `pwd`
>
> Print Working Directory	打印出当前工作（当前所在）路径
>
> `ls [opt]`
>
> It will show the full list or content of your directory.
>
> `ll`
> It stands for long format.



**cd  [destination]** 

```bash
[root@localhost ~]# cd ~ 进入到root目录
[root@localhost ~]# pwd
/root
[root@localhost ~]# cd / 进入到/目录
[root@localhost /]# pwd
/
[root@localhost /]# cd /root 进入到指定路径的目录
[root@localhost ~]# 
```

**cd ..** 

```bash
[root@localhost ~]# pwd
/root
[root@localhost ~]# cd ..回退到上一层目录
[root@localhost /]# pwd
/
[root@localhost /]# 
```

**pwd**

```bash
[root@localhost disk]# pwd
/dev/disk
```



**ls**

```bash
[root@localhost /]# ls 列出当前目录下所有的目录
bin  boot  cat  -d  dev  -e  etc  home  lib  lib64  madata  media  mnt  mydata  opt  proc  root  run  sbin  srv  sys  tmp  usr  -v  var
[root@localhost /]# ll 列出当前目录下所有的目录并展示详细信息It stands for long format
total 36
lrwxrwxrwx.   1 root root    7 Jun 14  2022 bin -> usr/bin
dr-xr-xr-x.   5 root root 4096 Sep  8  2022 boot
[root@localhost /]# ls -al
total 48
dr-xr-xr-x.  19 root root 4096 Dec 16 00:03 .
dr-xr-xr-x.  19 root root 4096 Dec 16 00:03 ..
-rw-rw-rw-.   1 root root    0 Sep 11  2022 .authorelabel
-rw-r--r--    1 root root    0 Dec  6 03:42 .autorelabel
-rw-------.   1 root root  286 Sep 11  2022 .bash_history
lrwxrwxrwx.   1 root root    7 Jun 14  2022 bin -> usr/bin
dr-xr-xr-x.   5 root root 4096 Sep  8  2022 boot
```

### File Commands

**Types of Files:**

1.  **Regular files (-):** It contain programs, executable files and text files.
2. **Directory files (d):** It is shown in blue color. It contain list of files.
3. Special files
   - **Block file (b)**
   - **Character device file (c)**
   - **Named pipe file (p)**
   - **Symbolic link file (l)**
   - **Socket file (s)**

> `    mkdir <dirname>  `
>
> create a directory
>
> `rmdir <dirname>`
>
> delete a directory and a **directory has to be empty** to be deleted.
>
> `touch <filename.suffix>`
>
> create a new file
>
> `rm [option] <filename> `
>
> remove a file
>
> `cp <derive> <destination>`
>
> copy a file or directory to destination
>
> `mv <derive> <destination>`
>
> move file or directory to destination / rename
>
> `ln [-s] <original> <linkname>`
>
> ![image-20230402210050169](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402210050169.png)
>
> **Hard link**：硬连接指通过索引节点来进行连接。在 Linux 的文件系统中，保存在磁盘分区中的文件不管是什么类型都给它分配一个编号，称为索引节点号(Inode Index)。在 Linux 中，多个文件名指向同一索引节点是存在的。比如：A 是 B 的硬链接（A 和 B 都是文件名），则 A  的目录项中的 inode 节点号与 B 的目录项中的 inode 节点号相同，**即一个 inode  节点对应两个不同的文件名，两个文件名指向同一个文件**，**A 和 B 对文件系统来说是完全平等的**。**删除其中任何一个都不会影响另外一个的访问**。
>
> 
>
> **Soft link**：软链接文件有**类似于 Windows  的快捷方式**。它**实际上是一个特殊的文件**。在符号连接中，文件实际上是一个文本文件，其中包含的有另一文件的位置信息。比如：A 是 B 的软链接（A 和 B 都是文件名），A 的目录项中的 inode 节点号与 B 的目录项中的 inode 节点号不相同，**A 和 B 指向的是两个不同的  inode**，继而指向两块不同的数据块。但是 **A 的数据块中存放的只是 B 的路径名（可以根据这个找到 B 的目录项）**。A 和 B  之间是“主从”关系，**如果 B 被删除了，A 仍然存在**（因为两个是不同的文件），**但指向的是一个无效的链接**。



**mkdir <dirname>**

```bash
[root@localhost ~]# mkdir commandTest 创建一个name为commandTest文件
[root@localhost ~]# ls
anaconda-ks.cfg  Desktop    HelloEddie.java  Music       MyDocker_Nacos_Cluster                      Pictures  Templates
clash_for_linux  Documents  java_project     myactivemq  mysql80-community-release-el7-3.noarch.rpm  postfile  Videos
commandTest      Downloads  maven            MyDocker    original-ks.cfg                             Public
[root@localhost ~]# cd commandTest/
```

**rmdir <dirname>**

```bash
[root@localhost ~]# rmdir commandTest/
rmdir: failed to remove ‘commandTest/’: Directory not empty
```

**touch <filename.suffix>**

```bash
[root@localhost commandTest]# touch eddieZhang.txt
[root@localhost commandTest]# ls
eddieZhang.txt
```

**rm [option] <filename>**

| Option          | Description                                 |
| --------------- | ------------------------------------------- |
| `rm *extension` | Used to delete files having same extension. |
| `rm -r or R`    | To delete a directory recursively.          |
| `rm -i`         | Remove a file interactively.                |
| `rm -rf`        | Remove a directory forcefully.              |

```bash
[root@localhost commandTest]# rm eddie1.txt 删除一个指定的文件
rm: remove regular empty file ‘eddie1.txt’? y
[root@localhost commandTest]# ls
eddie2.txt  eddie3.txt  eddieZhang.txt
[root@localhost commandTest]# rm -f eddie2.txt 强制删除一个指定的文件 不会提问
[root@localhost commandTest]# ls
eddie3.txt  eddieZhang.txt
[root@localhost commandTest]# rm *txt 删除以txt为后缀的所有文件
rm: remove regular empty file ‘eddie3.txt’? y
rm: remove regular empty file ‘eddieZhang.txt’? y
[root@localhost commandTest]# ls
[root@localhost commandTest]# rm -r eddieTest/ 递归删除指定文件夹下的所有子文件
rm: descend into directory ‘eddieTest/’? y
rm: descend into directory ‘eddieTest/eddie2’? y
rm: remove regular empty file ‘eddieTest/eddie2/eddie.txt’? y
rm: remove directory ‘eddieTest/eddie2’? y
rm: remove directory ‘eddieTest/’? y
[root@localhost commandTest]# ls
[root@localhost commandTest]# 
```

**cp <derive> <destination>**

```bash
[root@localhost commandTest]# cp eddie.txt ./eddie/eddieCopy.txt
[root@localhost commandTest]# cp eddie.txt ./eddie2.txt
[root@localhost commandTest]# ls
eddie  eddie2.txt  eddie.txt
[root@localhost commandTest]# 
```

**mv <derive> <destination>**

```bash
[root@localhost commandTest]# ls
eddie  eddie2.txt  eddie.txt
[root@localhost commandTest]# move eddie.txt ./eddie/ 将指定的文件移动到指定的路径
bash: move: command not found...
[root@localhost commandTest]# mv eddie.txt ./eddie/
[root@localhost commandTest]# ls
eddie  eddie2.txt
[root@localhost commandTest]# cd eddie
[root@localhost eddie]# ls
eddieCopy.txt  eddie.txt
[root@localhost commandTest]# ls
eddie  eddie2.txt
[root@localhost commandTest]# mv eddie2.txt eddie.txt 修改指定的文件的name
[root@localhost commandTest]# ls
eddie  eddie.txt
[root@localhost commandTest]# 
```



### File Compression

### File Permission

### System Management and Info

### Network Management

### Process Management

### Searching

### Hardware Information

### Package Installation

### User and Groups

### SSH Login

### File Transfer

### Disk Usage

### Variables

### Shell Command Management

## VIM Editor Commands

![image-20230402163930439](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402163930439.png)

### **Open/create a file**

```bash
vim test.txt
vi test.txt
```

### Main operation modes

​	**“Standard mode”** — movement in a file, text deletion  and other editing features. This is the main mode, which is used for  immediate switching to other modes. In order to return to the main mode  from any other mode:

```bash
<ESC>, sometimes two times;
<Ctrl-[>
```

​	 **“Input mode”** - text input. After the text is entered, the standard mode is immediately returned. Please, note that the text  is deleted and entered in two different modes. Switch to it from the  standard mode:

```bash
i
<Insert>
```

​	**“Command mode”** - Commands (operations with a file, search and replacement, editor configuring…). Switch to it from the standard mode:

```bash
:
```

​	**“Search mode”** - input of a search request. Switch to this mode from the standard mode

```bash
/ ,  Search forward for (N-th) matching line
? ,  Search backward for (N-th) matching line
```

​	 **“Visual mode”** - text highlighting mode:

```bash
"v" and right or left arrows;
Shift+v mark line;
Ctrl+v rectangle, mark part of the text
```

### Movement in a file

​	After loading of Vim, a part of the downloaded text file will be  displayed on the screen. After loading, Vim is in the “command mode”,  which is one of main modes. It means that if you press on <l>  button (lowercase L), you will see that a cursor is shifted on one  character to the right instead of displaying “l” in the cursor place. In the command mode, characters, entered using the keyboard, are used as  commands for Vim, but not as characters, placed in the text. Movement  commands are one of the most important command types. There are several  of them:

```bash
For the cursor movement press keys h,j,k,l as shows below:
               ^
               k
           <h     l>
               j
               v

<Ctrl-f> - Forward  one window
<Ctrl-b> - Backward one window
<Ctrl-d> - Forward  one half-window
<Ctrl-u> - Backward one half-window
<Ctrl-y> - Backward one line
<Ctrl-e> - Forward  one line
0 (zero) - Move cursor to start of line
$        - Move cursor to end of line
w        - Move cursor right one word
b        - Move cursor left one word
W        - Move cursor right to the space after word
B        - Move cursor left to the space before word
gg       - go to the start of a file
G        - positions at the end of the file
<n>G     - Cursor goes to the specified (n) line
/<text><CR> - search for a "text"
?<text><CR> - search backwards for a "text"
n        - find the next occurrence of the same string
N        - repeats the last search the opposite direction
```

### Text input

​	The followinf commands switch the editor into the input mode:

```bash
i — Insert text before the current cursor position
a — Append text following current cursor position
I — Insert text at the beginning of the cursor line
А — Append text to the end of current line
o — Open up a new line following the current line and add text there
O — Open up a new line in front of the current line and add text there
s <n> - Change one character
S - Change a whole line
R — Begin overstrike or replace mode. Use ESC key to exit
r — Replace one character at the cursor position
```

### Deletion and insertion

​	The main text deletion and insertion commands are listed below:

```bash
x — Delete character under the cursor
X — Delete character left of the cursor
d — command may be followed by any motion command, and it deletes from the current location to the place where the cursor winds up. For example:
d4w - deletes four words
diw - delete word arrownd cursor
dd — delete a whole line
d<n>d или <n>dd — deletes n line
db - delete word backward
d0 - deletes character from the begining to cursor position
d$ or D - Delete to end of the line
с — The change operator
сс - changes a whole line
C - Change to end of the line
yy (or Y) — yanks current line (VI's copy commmand)
y<n>y — copy "n" lines from current to the clipboard
p — paste below cursor
P — paste above cursor
J — Join next line down to the end of the current line
```

### Change cancellation

```bash
u — Undo last change
U — Restore line
```

### Show Line Numbers in Vim

```shell
# set all line show number
:set nu
# To disable
:set nu!

#show current line number
:nu
```

### Search

​	Go to a line:

```bash
/abcdef - Find the first string "abcdef"
n - Find the next "abcdef"
N - Find the previous "abcdef"
```

### Exit

​	There is a pair of commands, which you should know:

```bash
:q! - Quit (no warning)
:wq - Write file to disk and quit the editor
```

​	Main features, required for operation, are described in this article.  Almost all Linux distributions are described in the manual on operation  with the editor. Just enter command vimtutor in the command line.

### Help

​	In order to call the help, containing the information about the editor, enter the following command in the terminal:

```bash
man vim
```

## Linux(Centos 7)

### Linux项目部署

#### 手动部署项目

**1）将编写好的springboot 项目的Java代码打包成.jar**

![image-20230106112309893](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106112309893.png)

**2）将.jar文件传输至Linux服务器指定位置**

![image-20230106112407676](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106112407676.png)

**3）开放Linux防火墙(项目使用到的端口)**

![image-20230106112649833](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106112649833.png)

**3）后台运行项目 并 指定日志输出文件**

![image-20230106113132554](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106113132554.png)

**4）访问项目**

![image-20230106113319155](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106113319155.png)

**5）停止项目**

![image-20230106114622797](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106114622797.png)

#### Shell 脚本自动部署项目

![image-20230107140648013](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107140648013.png)

1）安装git

使用yum install git

```
[root@192 java_project]# yum list git
[root@192 java_project]# yum install git
```

![image-20230107152059930](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107152059930.png)

使用git clone  代码

![image-20230107152738214](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107152738214.png)

2）安装maven

![image-20230107173353330](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107173353330.png)

配置环境变量

```
[root@192 etc]# vim profile
```



![image-20230107173200699](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107173200699.png)

```
[root@192 etc]# source /etc/profile
[root@192 etc]# mvn -version
-bash: /root/maven/apache-maven-3.6.3/bin/mvn: Permission denied
```

配置setting.xml

![image-20230107173731217](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107173731217.png)

![image-20230107173938931](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107173938931.png)

![image-20230107174024106](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107174024106.png)

3）编写Shell脚本(拉取代码 编译 打包 启动)

bootstart.sh

```shell
#!/bin/sh
echo =================================
echo  Automatic deployment project
echo =================================

echo 停止原来运行中的工程
APP_NAME=Project_Practice_Reggie

tpid=`ps -ef|grep Project_Practice_ReggieTakeout-1.0-SNAPSHOT.jar|grep -v grep|grep -v kill|awk '{print $2}'`
if [ ${tpid} ]; then
    echo 'Stop Process...'
    kill -9 $tpid
fi
sleep 2
tpid=`ps -ef|grep Project_Practice_ReggieTakeout-1.0-SNAPSHOT.jar|grep -v grep|grep -v kill|awk '{print $2}'`
if [ ${tpid} ]; then
    echo 'Kill Process!'
    kill -9 $tpid
else
    echo 'Stop Success!'
fi

echo 准备从Git仓库拉取最新代码
cd /root/java_project/reggie_takeout/automatic_deployment_project/Project_Practice_Reggie

echo 开始从Git仓库拉取最新代码 完全覆盖本地代码
git reset --hard
git pull origin master
echo 代码拉取完成

echo 开始打包
output=`mvn clean package -Dmaven.test.skip=true`

cd target

echo 启动项目
nohup java -jar Project_Practice_ReggieTakeout-1.0-SNAPSHOT.jar &> Project_Practice_Reggie.log &

echo 项目启动完成
```

4）xxx.sh 赋予权限

![image-20230107175215451](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107175215451.png)

5）执行shell脚本

![image-20230107175733129](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107175733129.png)

![image-20230107180849229](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230107180849229.png)

### Linux开放防火墙端口

```
install防火墙
yum install firewalld firewall-config

operate防火墙
service firewalld restart 重启
service firewalld start 开启
service firewalld stop 关闭

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

### 设置静态IP

![image-20230106122514848](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106122514848.png)

![image-20230106123527934](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106123527934.png)

![image-20230106123502472](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106123502472.png)

![image-20230106125240201](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230106125240201.png)

## Linux(Ubuntu)

1、Ubuntu查看防火墙的状态
在Ubuntu系统进行安装的时候默认安装了ufw防火墙

查看防火墙的状态

命令：

       sudo ufw status



系统提示： “Status: inactive”状态：不活跃

上面提示表示没有开启防火墙，并不是没有安装防火墙

如果没有安装可以使用命令安装

命令：

       sudo sudo apt-get install ufw

2、Ubuntu开启防火墙

开启防火墙，

命令：

       sudo ufw enable          //开启防火墙



注意：Command may disrupt existing ssh connections. Proceed with operation (y|n)?

表示：命令可能会中断现有的ssh连接。继续操作(y|n)?

因为是在远程的Xshell进行连接开启防火墙的，有的系统是没有将SSH的22端口设置为public的，所以会有这样的提示，这里分为两种情况，如果开启防火墙时在防火墙之中检测到22端口已添加为防火墙的开放端口，那么输入y继续操作以后，当前Xshell会自动断开连接；相反，如果开启防火墙时在防火墙之中没有检测到22端口，那么输入y继续操作以后22端口将会不再支持其他连接，只支持当前已有的这个连接，保持当前连接的原因是可以通过该连接开放22端口。

这里之前没有设置过，直接输入y继续执行



系统提示：“防火墙是活动的，并在系统启动时启用”

表示防火墙已经开启

查看防火墙的状态

命令：

       sudo ufw status           //查看防火墙的状态



可以看到系统只对外开放了80端口

在这里通常会有些错觉，22端口没有开放，但是依然是连接状态，这是系统做的人性化优化，便于远程管理服务器，虽然22端口没有开放，但是用户通过当前的连接开启防火墙后，该连接依然处于连接状态，只要不关闭当前连接还是可以在当前连接中正产操作的。如果是重新开启一个连接是连不上的



在windows上进行telnet也是不通的



所以在远程管理服务器时，如果开启了防火墙先查看SSH的22端口有没有开放，如果没有开放，第一时间开放22端口（如果为了安全也可以指定ip开放22端口）

3、Ubuntu添加开放SSH端口

命令：

       sudo ufw allow 22        //开放22端口



开启完成，需要重启防火墙生效

命令：

       sudo ufw reload           //重启ufw防火墙



重启成功

再查看防火墙的状态

命令：

       sudo ufw status           //查看防火墙的状态



22端口已经开放

查看22端口的监听状态

命令：

       sudo netstat -tunlp | grep 22            //查看22端口信息



22端口属于监听状态，在Windows下能够telnet通

命令：

       telnet 192.168.121.135 22
