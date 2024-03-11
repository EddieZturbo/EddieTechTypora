# Git&GitHub

## Git

Git是免费的**开源**的 **分布式版本控制系统**（区别去集中式） 可以快速且高效的处理小型或大型的各种项目

![image-20240219111403186](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240219111403186.png)

### Git介绍

![image-20221112171759454](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112171759454.png)

![image-20221211111622771](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221211111622771.png)

#### 版本控制

**个人开发过渡到团队协作**

![image-20221112172148983](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112172148983.png)

#### 分布式版本控制和集中式版本控制

![image-20221112171557283](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112171557283.png)

![image-20221112190100784](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112190100784.png)

![image-20221112190042870](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112190042870.png)

#### Git工作机制

![image-20221112191335086](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112191335086.png)

![image-20221113082945648](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113082945648.png)

![image-20221113082933852](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113082933852.png)

#### Git和代码托管中心

![image-20221112191116560](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112191116560.png)

### Git常用命令

![image-20230329094447847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230329094447847.png)

![image-20230329094605110](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230329094605110.png)

![image-20221112192838461](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112192838461.png)

![image-20221112192413869](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112192413869.png)

|              |                                                              |
| ------------ | ------------------------------------------------------------ |
| `git revert` | Create new commit that undo all of the changes mage in <commit> then apply it to current branch<br /><br />比如，我们commit了三个版本（版本一、版本二、 版本三），突然发现版本二不行（如：有bug），想要撤销版本二，但又不想影响撤销版本三的提交，就可以用 git revert 命令来反做版本二，生成新的版本四，这个版本四里会保留版本三的东西，但撤销了版本二的东西。 |

**查看所有的config配置项**

```bash
git config --list
```



**从 Git 仓库和文件系统中删除文件。**

```text
$ cd folder1

$  git rm file1
rm 'folder1/file1'
```

我们已经移动到 folder1 并从仓库和文件系统中删除了 file1。

我们可以检查删除的状态如下。

```text
$ git status
On branch main
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	deleted:    file1
```

**仅从仓库而不是从文件系统中删除文件。**

```text
$ git rm --cached file2

$ git commit -m "Removed file2 from repository only"

$ git push origin main
```

当我们使用 --cached 选项运行 git rm 命令时，文件会从仓库中删除，但不会从工作树（即）文件系统中删除。

**删除整个文件夹。**

为此，我们需要将选项 -r 添加到 git rm 命令，如下所示。

```text
$ git rm -r folder1
rm 'folder1/file2'

$ git commit -m "removed folder1"
[main dabfe02] removed folder1
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 folder1/file2
 
$ git push origin main
```


### Git上传文件超过100M

```bash
# 配置http.poseBuffer大小
git config http.postBuffer 524288000

# 查看所有config配置
git config -l
```

> **上大招**
>
> 突破github限制，支持单个文件超出100M (使用 [Git LFS](https://github.com/git-lfs/git-lfs)) 
>
>  Git LFS的官方网址在这里： https://git-lfs.github.com/，官网上有很详细的说明。

### 版本穿梭

![image-20221112220725989](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112220725989.png)

![image-20221112221826954](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112221826954.png)

#### 回滚到指定历史版本

![image-20221112221809720](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112221809720.png)

#### 回滚当前仓库指向的版本

![image-20221112222127727](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112222127727.png)

![image-20221112222711698](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112222711698.png)

![image-20221112223225379](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223225379.png)





### Git 分支操作

#### 分支的介绍

![image-20221112223431665](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223431665.png)

![image-20221112223648618](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223648618.png)

#### 分支的好处

![image-20221112223831201](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223831201.png)

![image-20221112223704064](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223704064.png)

#### 分支的操作

![image-20221112223924008](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112223924008.png)

##### git branch -v 查看分支

![image-20221112224018367](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112224018367.png)

##### git branch 分支名 创建分支

![image-20221112224145241](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112224145241.png)

##### git checkout 分支名 切换分支

**修改分支** 在切换到的分支上更改项目代码 并从工作区中add到缓存中 再commit到本地库中

![image-20221112224406571](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112224406571.png)

![image-20221112224645182](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112224645182.png)

![image-20221112225319566](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112225319566.png)

##### 分支合并

**把指定的分支合并到当前分支上**

**git**  **merge** 指定要合并到当前分支上的分支

![image-20221112225700716](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112225700716.png)

##### 删除分支

![image-20221112231025914](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112231025914.png)

##### 合并冲突

**当前分支**和**要合并过来的分支**都**修改了同一个文件**的情况下 **git无法做出确定的合并判断** **需要手动进行合并**

![image-20221112233507727](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112233507727.png)

![image-20221112233823890](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112233823890.png)

### Git团队协作

#### 团队内协作

![image-20221112234123504](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112234123504.png)

#### 跨团队协作

![image-20221112234138078](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221112234138078.png)

#### 创建Git Hub远程库

![image-20221113000534054](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113000534054.png)

![image-20221113000549618](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113000549618.png)

![image-20221113000357088](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113000357088.png)

#### 远程库的别名

![image-20221113000457365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113000457365.png)

#### Push到Git Hub远程仓库

![image-20221113001420862](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113001420862.png)

#### 从Git Hub远程库中pull下来至本地库

![image-20240219112554486](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240219112554486.png)

![image-20240219135932327](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240219135932327.png)

![image-20240219135621856](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20240219135621856.png)

![image-20221113002225304](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113002225304.png)

#### Clone远程仓库到本地

**Clone远程仓库中的代码**
**1--拉取代码**
**2--初始化本地仓库**
**3--创建别名**

![image-20221113003256427](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113003256427.png)

![image-20221113003243637](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113003243637.png)

![image-20221113003805088](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113003805088.png)

#### Git Hub邀请成为团队伙伴

![image-20221113080907324](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113080907324.png)

#### SSH免密登录

![image-20221113114655495](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113114655495.png)

![image-20221113114706936](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113114706936.png)

![image-20221113114715120](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113114715120.png)

### IDEA集成Git

#### 配置Git忽略文件

![image-20221113142102249](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142102249.png)

![image-20221113142042088](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142042088.png)

**git.ignore**

```
.git
logs
rebel.xml
target/
!.mvn/wrapper/maven-wrapper.jar
log.path_IS_UNDEFINED
.DS_Store
offline_user.md

### STS ###
.apt_generated
.classpath
.factorypath
.project
.settings
.springBeans

### IntelliJ IDEA ###
.idea
*.iws
*.iml
*.ipr

### NetBeans ###
nbproject/private/
build/
nbbuild/
dist/
nbdist/
.nb-gradle/
generatorConfig.xml

### nacos ###
third-party/nacos/derby.log
third-party/nacos/data/
third-party/nacos/work/

file/
```

#### 定位Git程序

![image-20221113141751070](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113141751070.png)

#### 初始化本地库

![image-20221113142124484](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142124484.png)

#### add到暂存区

![image-20221113142133084](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142133084.png)

#### commit到本地库

![image-20221113142140998](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142140998.png)

![image-20221113142154355](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113142154355.png)

#### 切换版本

![image-20221113143338861](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113143338861.png)

![image-20221113143247629](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113143247629.png)

#### 切换分支

![image-20221113143758507](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113143758507.png)

#### 合并分支

##### 正常合并

![image-20221113145242260](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113145242260.png)

##### 冲突合并

![image-20221113150256414](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113150256414.png)

![image-20221113150306803](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113150306803.png)

![image-20221113150448525](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113150448525.png)

### IDEA集成Git Hub

#### 绑定Git Hub

![image-20221113151124226](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113151124226.png)

#### share项目代码到Git Hub

![image-20221113151904122](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113151904122.png)

![image-20221113152010857](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113152010857.png)

![image-20221113151953931](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113151953931.png)

#### 使用SSH方式Push到Git Hub

![image-20221113152759112](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113152759112.png)

#### 从Git Hub上pull下来项目代码

![image-20221113153423574](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113153423574.png)

#### 从Git Hub上Clone项目代码

![image-20221113161544096](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221113161544096.png)

## Git Hub

https://rahuldkjain.github.io/gh-profile-readme-generator/

**in:name**  关键词

**in:descripton** 关键词 

**in:readme** 关键词

stars:>3000 spring cloud

stars: 10..20 关键词

fork 数同理，将上面的 stars 换成 fork，其它语法相同