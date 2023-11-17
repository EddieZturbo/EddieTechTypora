# Java Virtual Machine

> JVM stands for Java Virtual Machine. It is a software that provides a runtime environment for executing Java programs.
>
> Java is a high-level programming language that can run on multiple platforms, such as Windows, Linux, and macOS, without needing to be recompiled for each platform. JVM is responsible for making this possible by providing an abstraction layer between the Java program and the underlying hardware and operating system.
>
> When a Java program is compiled, it is transformed into a platform-independent bytecode format that can be executed by the JVM. The JVM then translates the bytecode into machine code that can be understood by the host operating system.
>
> The JVM also provides a number of other features, 
>
> such as **automatic memory management (garbage collection&memory allocation)**, **dynamic class loading**, and **security management**, 
>
> which make it easier to develop and run Java applications.
>
> ![image-20230403103945508](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403103945508.png)

![image-20230401002339258](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401002339258.png)

![image-20230401002814894](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401002814894.png)



## JVM Structure

![image-20220927101506965](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101506965.png)

### **JVM的架构模型 基于栈式架构**

![image-20220920102914097](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920102914097.png)

![image-20220920102933595](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920102933595.png)

### JVM生命周期

**启动——执行——退出**

![image-20220920103222871](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920103222871.png)

![image-20220920103234998](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920103234998.png)

## JVM Parameters Setting

https://www.oracle.com/java/technologies/javase/vmoptions-jsp.html

> ### **heap memory management**
>
> | Option and Default Value                    | Description                                                  |
> | ------------------------------------------- | ------------------------------------------------------------ |
> | -Xmx [Unit]                            | Maximum use memory size(default 1/4 system memory)           |
> | -Xms [Unit]                            | Minimum use memory size(default 1/64 system memory)          |
> | -XX:NewSize= [Unit]                    | Young generation heap size                                   |
> | -XX:MaxNewSize= [Unit]                 | Young generation max heap size                               |
> | -XX:NewRatio=n                              | Ratio of old/new generation sizes. The default value is 2.   |
> | -XX:SurvivorRatio=n                         | Ratio of eden/survivor space size. The default value is 8.   |
> | -XX:MaxPermSize= [Unit]                | Permanent generation max heap size                           |
> | -XX:PermSize= [Unit]                   | Permanent heap size                                          |
> | -XX:MaxMetaspaceSize=metaspace size[unit] | Size is not defined. JVM automatically increases it.We can set Metaspace size |
> | -XX:MaxDirectMemorySize=1g                  | Sets the maximum size of direct memory.                      |
> | -XX:MaxHeapSize=1g                          | Sets the maximum size of heap memory.                        |
> | -XX:MaxHeapFreeRatio=70                     | Maximum percentage of heap free after GC to avoid shrinking. |
> | -XX:MinHeapFreeRatio=30                     | sets the minimum percentage of heap free after GC to avoid expansion. |
> | -XX:+UseTLAB                                | Use thread-local allocation buffer                           |
>
> ### GC Logging
>
> | Option and Default Value      | Description                                                  |
> | ----------------------------- | ------------------------------------------------------------ |
> | -XX:+PrintGCDetails           | Print GC details Messages                                    |
> | -XX:+PrintGCDateStamps        | Can be used for the printing of a date stamp at every GC     |
> | -Xloggc:/home/DATA/filename | Log GC verbose output to specified file. The verbose output is controlled by the normal verbose GC flags. |
> | -XX:+UseGCLogFileRotation     | Enabled GC log rotation                                      |
> | -XX:NumberOfGClogFiles=1      | Set the number of files to use when rotating logs, default value is 1 and it should be always >=1 |
> | -XX:GCLogFileSize=8K          | The size of the log file at which point the log will be rotated, must be >= 8K.default will be set to 512K |
>
> ### Class information tracking
>
> | Option and Default Value       | Description                                                  |
> | ------------------------------ | ------------------------------------------------------------ |
> | -verbose className           | Displays detailed information about the class loading, including the ClassLoader to which the class name is loaded. |
> | -XX:+TraceClassLoading         | Trace loading of classes.                                    |
> | -XX:+TraceClassUnloading       | Trace unloading of classes.                                  |
> | -XX:+PrintClassLoaders         | Displays information about all classloaders , including ClassLoader types and parent-child relationships |
> | -XX:+PrintClassHistogram       | Print a histogram(JVM中所有已加载类的统计信息，包括类的数量、大小等) of class instances. |
> | -XX:-TraceClassResolution      | Trace constant pool resolutions.                             |
> | -XX:+PrintCompilation          | 打印JIT编译器编译的方法的详细信息，包括编译时间、编译级别等  |
> | -XX:+PrintTenuringDistribution | Print tenuring age information.                              |
>
> ### Garbage Collection
>
> | Option and Default Value   | Description                                  |
> | -------------------------- | -------------------------------------------- |
> | -XX:+UseSerialGC           | Use Serial Collector                         |
> | –XX:+UseParallelGC         | Use Parallel Collector                       |
> | XX:+USeParNewGC            | Use ParNew Collector                         |
> | XX:+USeG1GC                | Use G1 Collector                             |
> | -XX:+UseAdaptiveSizePolicy | Enable an adaptive garbage collection policy |
> | -XX:-DisableExplicitGC     | Disable explicit GC such:System.gc()         |
>
> ### Thread Paramerters
>
> | Option and Default Value | Description                                                  |
> | ------------------------ | ------------------------------------------------------------ |
> | -XX:ThreadStackSize=512  | Thread Stack Size                                            |
> | -XX:ParallelGCThreads=n  | Sets the number of garbage collection threads in the young and old parallel garbage collectors. |

## Look up JVM information

### CMD

![image-20230608145450876](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230608145450876.png)

```shell
D:\IDEA_2019_1_3\WorkSpace\statistics-analysis>jps
19504 CepreiApplication
21312 Launcher
4432 Jps
8740 KotlinCompileDaemon
12088 RemoteMavenServer
18540

D:\IDEA_2019_1_3\WorkSpace\statistics-analysis>jinfo -flags 19504
Attaching to process ID 19504, please wait...
Debugger attached successfully.
Server compiler detected.
JVM version is 25.162-b12
Non-default VM flags: -XX:-BytecodeVerificationLocal -XX:-BytecodeVerificationRemote -XX:CICompilerCount=12 -XX:InitialHeapSize=532676608 -XX:+ManagementServer -XX:MaxHeapSize=851443712
0 -XX:MaxNewSize=2837970944 -XX:MinHeapDeltaBytes=524288 -XX:NewSize=177209344 -XX:OldSize=355467264 -XX:TieredStopAtLevel=1 -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+
UseFastUnorderedTimeStamps -XX:-UseLargePagesIndividualAllocation -XX:+UseParallelGC
Command line:  -XX:TieredStopAtLevel=1 -Xverify:none -Dspring.output.ansi.enabled=always -Dcom.sun.management.jmxremote -Dspring.jmx.enabled=true -Dspring.liveBeansView.mbeanDomain -Dsp
ring.application.admin.enabled=true -javaagent:D:\IDEA_2019_1_3\IntelliJ IDEA 2019.1.3\lib\idea_rt.jar=52294:D:\IDEA_2019_1_3\IntelliJ IDEA 2019.1.3\bin -Dfile.encoding=UTF-8

D:\IDEA_2019_1_3\WorkSpace\statistics-analysis>

```

### Debug/Run Configurations(IDEA Interface)

> -XX:+PrintCommandLineFlags

![image-20230608145750396](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230608145750396.png)

![image-20230608145825948](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230608145825948.png)

## Class Loading Subsystem

### 类加载器和类的加载过程

![image-20220920104243326](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920104243326.png)



![image-20220920104757585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920104757585.png)

![image-20220920104740671](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920104740671.png)

![image-20220920110604499](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920110604499.png)

![image-20220920110910892](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920110910892.png)

![image-20220920110924167](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920110924167.png)

### 类的加载过程

![image-20220920111431881](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920111431881.png)

一个Java文件从编码完成到最终运行，一般会经历两个阶段：编译期、运行期。编译，即通过javac命令，将Java文件转化为二进制字节码文件，即.class文件；运行，则是将.class文件交给JVM执行。而本文所说的类加载过程就是将.class文件中类的元信息加载进内存，创建Class对象并进行解析、初始化类变量等的过程
        JVM并不是一开始就会将所有的类加载到内存，而是用到某个类，才会去加载，只加载一次，后续会说到类的加载时机

2. 类加载详解
       类加载分为三个部分：加载、连接、初始化
3. ![image-20220920112538821](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920112538821.png)

#### 加载

加载
        **类的加载主要的职责为将.class文件的二进制字节流读入内存**(JDK1.7及之前为JVM内存(方法区)，JDK1.8及之后为本地内存(元空间))，并**在堆内存中为之创建Class对象**，**作为.class进入内存后的数据的访问入口**。

**在这里只是读入二进制字节流，后续的验证阶段就是要拿二进制字节流来验证.class文件，验证通过，才会将.class文件转为运行时数据结构**

![image-20220920160057893](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920160057893.png)

​        **++拓展**： 在**JDK1.7及以前**，Hot Spot JVM(普遍在用的JVM)存在一块叫做**方法区**的内存，也称之为**永久代**，这块区域用于存放类的元数据信息，包括类的字段，版本，方法等，这块区域，可以理解为.class文件进入内存后的位置。在**JDK1.8**，取消了方法区，取而代之的是**元数据区**，该元数据区并非JVM内存，而是**本地内存**。此外在JDK1.7时，将常量池从方法区移除，在堆内存开辟了一块空间作为常量池，有人说这是为取消方法区做的准备。更多请点我看思维导图总结
​        **++加分项： 为何取消方法区**？
​        官方说法为：**移除永久代是为融合HotSpot JVM与 JRockit VM而做出的努力**，**因为JRockit没有永久代**，不需要配置永久代
​        现实使用中存在问题：方法区存储类的元数据信息，我们不清楚一个程序到底有多少类需要被加载，且方法区位于JVM内存，我们不清楚需要给方法区分配多大内存，太小容易PermGen OOM，太大，在触发Full GC时又极其影响性能，同时还存在一些内存泄露的问题

#### 链接

##### 验证

该阶段主要是为了**保证加载进来的字节流符合JVM的规范**，**不会对JVM有安全性问题**。其中有对元数据的验证，例如检查类是否继承了被final修饰的类；还有对符号引用的验证，例如校验符号引用是否可以通过全限定名找到，或者是检查符号引用的权限(private、public)是否符合语法规定等。

![image-20220920160256311](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920160256311.png)

主要包括四种验证：**文件格式验证** **元数据验证** **字节码验证** **符号引用验证**

##### 准备

准备阶段的主要任务是**为类的类变量（static）开辟空间并赋默认值**。

1、静态变量是基本类型（int、long、short、char、byte、boolean、float、double）的默认值为0
2、静态变量是引用类型的，默认值为null
3、静态常量默认值为声明时设定的值

**例如：public static final int i = 3; 在准备阶段，i的值即为3**

**static final 在编译的时候就分配 准备阶段会显示初始化**

```java
public class ClassLoadingTest {
    public static final int num1 = 3;//prepare:num = 3;//static final在准备阶段就显示初始化
    public static int num = 1;//prepare:num = 0;initial:num = 1;准备阶段的主要任务是**为类的类变量（static）开辟空间并赋默认值**
    @Test
    public void test1(){
        System.out.println(num);
    }
}
```

**这里不会为实例变量分配初始化，** **类变量会分配在方法区中，而实例变量会随着对象一起分配到Java堆中**

##### 解析

**该阶段的主要职责为将Class在常量池中的符号引用转变为直接引用**，

此处针对的是**静态方法及属性和私有方法与属性**，**因为这类方法与私有方法不能被重写**，静态属性在运行期也没有多态这一说，即**在编译器可知，运行期不可变，所以适合在该阶段解析**，譬如类方法main替换为直接引用，为静态连接，区别于运行时的动态连接(后续我会写关于JVM内存结构的文章，在讲解栈帧时会介绍动态链接)。
**符号引用即字符串，说白了可以是一个字段名，或者一个方法名**；**直接引用即偏移量**，**说白了就是类的元信息位于内存的地址串**，例如，一个类的方法为test()，则符号引用即为test，这个方法存在于内存中的地址假设为0x123456，则这个地址则为直接引用

![image-20220927090611262](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927090611262.png)

![image-20220927090624171](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927090624171.png)

#### 初始化

类的**初始化顺序**：先执行父类静态变量赋值、父类静态初始化块，再执行子类静态属性赋值、静态初始化块

**执行类的构造器方法（clinit（））的过程（负责给static属性显示赋非默认值）**

**此方法不需要定义 是javac编译器自动收集类中的所有 类变量（static）的赋值动作和静态代码块中的语句合并而来**

**clinit（）构造器方法中的指令语句是按照源文件中出现的顺序**

![image-20220920130631247](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920130631247.png)

![image-20220920130824249](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920130824249.png)

```java
public class ClassLoadingTest1 {
    public static int num = 1;//类变量
    static {//静态代码块
        num = 2;
        number = 20;
    }
    public static int number = 10;

    public static void main(String[] args) {
        System.out.println(num);//2
        System.out.println(number);//10

    }
}
```

**clinit()方法是javac编译器自动收集类中的所有 类变量（static）的赋值动作和静态代码块中的语句合并而来**

**如果没有类变量（static）的赋值动作和静态代码块** **就不会有clinit()方法**

![image-20220920131249704](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920131249704.png)

**任何一个类生声明后，内部至少存在一个类的构造器**

若该类有父类：**JVM保证子类的clinit()方法执行前 父类的clinit()方法已经执行完毕**

![image-20220920132635850](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920132635850.png)

```Java
//父类先加载 其次加载子类 静态先行
public class ClassLoadingTest2 {
    static class Father{//父类先加载
        static int num = 1;
        static {
            num = 2;
        }
    }
    static class Son extends Father{//其次加载子类
        static int number = num;
    }

    public static void main(String[] args) {
        //父类先加载 其次加载子类 静态先行
        System.out.println(Son.number);//2
    }
}
```

**JVM必须保证一个类的clinit()方法在多线程下被同步加锁**

**保证clinit()方法只加载一次**

**clinit()方法** **clinit()方法是javac编译器自动收集类中的所有 类变量（static）的赋值动作和静态代码块中的语句合并而来**

**如果没有类变量（static）的赋值动作和静态代码块** **就不会有clinit()方法**

### 类加载器

**引导类加载器（Bootstrap ClassLoader）**

**自定义类加载器（User-Defined ClassLoader）**

**所有派生于抽象类ClassLoader的类加载器划分为自定义类加载器**

了解自定义类加载器：

通过前面的分析可知，**实现自定义类加载器需要继承ClassLoader或者URLClassLoader**，**继承ClassLoader则需要自己重写findClass()方法并编写加载逻辑**，**继承URLClassLoader则可以省去编写findClass()方法以及class文件加载转换成字节码流的代码**。那么**编写自定义类加载器的意义**何在呢？

简单来讲:**隔离加载类**，**修改类加载方式**，**扩展加载源**，**防止源码泄露**

1.当class文件不在ClassPath路径下，默认系统类加载器无法找到该class文件，在这种情况下我们需要实现一个自定义的ClassLoader来加载特定路径下的class文件生成class对象。

2.当一个class文件是通过网络传输并且可能会进行相应的加密操作时，需要先对class文件进行相应的解密后再加载到JVM内存中，这种情况下也需要编写自定义的ClassLoader并实现相应的逻辑。

3.当需要实现热部署功能时(一个class文件通过不同的类加载器产生不同class对象从而实现热部署功能)，需要实现自定义ClassLoader的逻辑。

#### 引导类加载器（Bootstrap ClassLoader）

启动类加载器**主要加载的是JVM自身需要的类**，这个类加载**使用C++语言实现**的，是**虚拟机自身的一部分**，它**负责将 <JAVA_HOME>/lib路径下的核心类库或-Xbootclasspath参数指定的路径下的jar包加载到内存中**，注意由于**虚拟机是按照文件名识别加载jar包的，如rt.jar，如果文件名不被虚拟机识别，即使把jar包丢到lib目录下也是没有作用的**(出于**安全考虑，Bootstrap启动类加载器只加载包名为java、javax、sun等开头的类**)。

#### 扩展类加载器（Extension ClassLoader）

扩展类加载器是指Sun公司(已被Oracle收购)实现的sun.misc.Launcher$ExtClassLoader类，由**Java语言实现**的，是**Launcher的静态内部类**，它**负责加载<JAVA_HOME>/lib/ext目录下或者由系统变量-Djava.ext.dir指定位路径中的类库**，开发者可以直接使用标准扩展类加载器。

#### 系统类加载器（System ClassLoader）

也称应用程序加载器是指 Sun公司实现的sun.misc.Launcher$AppClassLoader。它**负责加载系统类路径java -classpath或-D java.class.path 指定路径下的类库**，也就是我们经常用到的**classpath路径**，开发者可以直接使用系统类加载器，**一般情况下该类加载器是程序中默认的类加载器，通过ClassLoader#getSystemClassLoader()方法可以获取到该类加载器**。

```java
public class ClassLoadingTest3 {
    public static void main(String[] args) {
        //系统类加载器获取
        ClassLoader systemClassLoader = ClassLoader.getSystemClassLoader();
        System.out.println(systemClassLoader);
        //jdk.internal.loader.ClassLoaders$AppClassLoader@27c170f0

        //系统类加载器获取其上层 扩展类加载器
        ClassLoader systemClassLoaderParent = systemClassLoader.getParent();
        System.out.println(systemClassLoaderParent);
        //jdk.internal.loader.ClassLoaders$PlatformClassLoader@4f3f5b24

        //扩展类加载器获取其上层 引导类加载器 --获取不到
        ClassLoader systemClassLoaderParentParent = systemClassLoaderParent.getParent();
        System.out.println(systemClassLoaderParentParent);//null

        //对于自定义类加载器 默认使用系统类加载器进行加载
        System.out.println(ClassLoadingTest3.class.getClassLoader());
        //jdk.internal.loader.ClassLoaders$AppClassLoader@27c170f0同系统类加载器

        //String类的类加载器查看 引导类加载器加载 系统的核心类库都是使用引导类加载器进行加载的
        System.out.println(String.class.getClassLoader());
        //null
    }
```

![image-20220920134602495](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920134602495.png)

**获取ClassLoader的方式**

![image-20220920144548977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920144548977.png)

#### 类加载器间的关系

我们进一步了解类加载器间的关系(并非指继承关系)，主要可以分为以下4点

**启动类加载器**，由C++实现，嵌套在JVM内部 加载Java核心类库 没有父类。

**拓展类加载器(ExtClassLoader)**，派生于ClassLoader 由Java语言实现，父类加载器为启动类加载器（null 获取不到）

 (Java程序默认加载器）**系统类加载器(AppClassLoader)**，派生于ClassLoader 由Java语言实现，父类加载器为扩展类加载器ExtClassLoader 

**自定义类加载器**，父类加载器肯定为AppClassLoader。



#### 双亲委派模式

 在Java的**日常应用程序开发中**，**类的加载几乎是由引导（Bootstrap）类加载器、扩展（Extension）类加载器、系统（System）类加载器（也称应用类加载器）3种类加载器相互配合执行的**，在必要时，我们还可以自定义类加载器，需要注意的是，Java虚拟机对class文件采用的是按需加载的方式，也就是说当需要使用该类时才会将它的class文件加载到内存生成class对象，而且加载某个类的class文件时，**Java虚拟机采用的是双亲委派模式即把请求交由父类处理**，它**一种任务委派模式--双亲委派模式**

**非继承关系**

双亲委派模式要求**除了顶层的启动类加载器外**，**其余的类加载器都应当有自己的父类加载器**，请注意双亲委派模式中的父子关系**并非通常所说的类继承关系**，而是**采用组合关系来复用父类加载器的相关代码**，类加载器间的关系如下：

![image-20220920134602495](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920134602495.png)

**双亲委派模式是在Java 1.2后引入的**，**其工作原理的是，如果一个类加载器收到了类加载请求，它并不会自己先去加载，而是把这个请求委托给父类的加载器去执行，如果父类加载器还存在其父类加载器，则进一步向上委托，依次递归，请求最终将到达顶层的启动类加载器，如果父类加载器可以完成类加载任务，就成功返回，倘若父类加载器无法完成此加载任务，子加载器才会尝试自己去加载，这就是双亲委派模式，即每个儿子都很懒，每次有活就丢给父亲去干，直到父亲说这件事我也干不了时，儿子自己想办法去完成.**

##### 双亲委派模式优势

###### 避免重复加载

**采用双亲委派模式的是好处是Java类随着它的类加载器一起具备了一种带有优先级的层次关系，通过这种层级关可以避免类的重复加载，当父亲已经加载了该类时，就没有必要子ClassLoader再加载一次。**

###### 安全因素-沙箱安全机制

**防止核心API被随意篡改**（对核心源码的保护）

**其次是考虑到安全因素，java核心api中定义类型不会被随意替换，假设通过网络传递一个名为java.lang.Integer的类，通过双亲委托模式传递到启动类加载器，而启动类加载器在核心Java API发现这个名字的类，发现该类已被加载，并不会重新加载网络传递的过来的java.lang.Integer，而直接返回已加载过的Integer.class，这样便可以防止核心API库被随意篡改。**

![image-20220920154750258](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920154750258.png)

**可能你会想，如果我们在classpath路径下自定义一个名为java.lang.SingleInterge类(该类是胡编的)呢？该类并不存在java.lang中，经过双亲委托模式，传递到启动类加载器中，由于父类加载器路径下并没有该类，所以不会加载，将反向委托给子类加载器加载，最终会通过系统类加载器加载该类。但是这样做是不允许，因为java.lang是核心API包，需要访问权限，强制加载将会报出如下异常**

![image-20220920152230945](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920152230945.png)

java.lang.SecurityException: Prohibited package name: java.lang

**所以无论如何都无法加载成功的**

##### 从代码层面了解几个Java中定义的类加载器及其双亲委派模式的实现

![image-20220920151406561](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920151406561.png)

![image-20220920140502286](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920140502286.png)

**从图可以看出顶层的类加载器是ClassLoader类，它是一个抽象类，其后所有的类加载器都继承自ClassLoader（不包括启动类加载器）**

##### 线程上下文类加载器

在Java应用中存在着很多服务提供者接口（Service Provider Interface，SPI），这些接口允许第三方为它们提供实现，如常见的 SPI 有 JDBC、JNDI等，这些 SPI 的接口属于 Java 核心库，一般存在rt.jar包中，由Bootstrap类加载器加载，而 SPI 的第三方实现代码则是作为Java应用所依赖的 jar 包被存放在classpath路径下，由于SPI接口中的代码经常需要加载具体的第三方实现类并调用其相关方法，但SPI的核心接口类是由引导类加载器来加载的，而Bootstrap类加载器无法直接加载SPI的实现类，同时由于双亲委派模式的存在，Bootstrap类加载器也无法反向委托AppClassLoader加载器SPI的实现类。在这种情况下，我们就需要一种特殊的类加载器来加载第三方的类库，而线程上下文类加载器就是很好的选择。
    线程上下文类加载器（contextClassLoader）是从 JDK 1.2 开始引入的，我们可以通过java.lang.Thread类中的getContextClassLoader()和 setContextClassLoader(ClassLoader cl)方法来获取和设置线程的上下文类加载器。如果没有手动设置上下文类加载器，线程将继承其父线程的上下文类加载器，初始线程的上下文类加载器是系统类加载器（AppClassLoader）,在线程中运行的代码可以通过此类加载器来加载类和资源，如下图所示，以jdbc.jar加载为例

![image-20220920152641999](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920152641999.png)

从图可知**rt.jar核心包是有Bootstrap类加载器加载的**，**其内包含SPI核心接口类，由于SPI中的类经常需要调用外部实现类的方法，而jdbc.jar包含外部实现类(jdbc.jar存在于classpath路径)无法通过Bootstrap类加载器加载**，因此只能**委派线程上下文类加载器把jdbc.jar中的实现类加载到内存以便SPI相关类使用**。显然这种线程上下文类加载器的加载方式破坏了“双亲委派模型”，**它在执行过程中抛弃双亲委派加载链模式，使程序可以逆向使用类加载器，当然这也使得Java类加载器变得更加灵活**。为了进一步证实这种场景，不妨看看DriverManager类的源码，DriverManager是Java核心rt.jar包中的类，该类用来管理不同数据库的实现驱动即Driver，它们都实现了Java核心包中的java.sql.Driver接口，如mysql驱动包中的com.mysql.jdbc.Driver，这里主要看看如何加载外部实现类，在DriverManager初始化时会执行如下代码

```java
//DriverManager是Java核心包rt.jar的类
public class DriverManager {
	//省略不必要的代码
    static {
        loadInitialDrivers();//执行该方法
        println("JDBC DriverManager initialized");
    }

//loadInitialDrivers方法
 private static void loadInitialDrivers() {
     sun.misc.Providers()
     AccessController.doPrivileged(new PrivilegedAction<Void>() {
            public Void run() {
				//加载外部的Driver的实现类
                ServiceLoader<Driver> loadedDrivers = ServiceLoader.load(Driver.class);
              //省略不必要的代码......
            }
        });
    }
```

在DriverManager类初始化时执行了loadInitialDrivers()方法,在该方法中通过ServiceLoader.load(Driver.class);去加载外部实现的驱动类，ServiceLoader类会去读取mysql的jdbc.jar下META-INF文件的内容，如下所示
![image-20220920153320008](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920153320008.png)

很明显了确实通过线程上下文类加载器加载的，实际上**核心包的SPI类对外部实现类的加载都是基于线程上下文类加载器执行的**，通过这种方式实现了**Java核心代码内部去调用外部实现类**。我们知道**线程上下文类加载器默认情况下就是AppClassLoader**，

那**为什么不直接通过getSystemClassLoader()获取类加载器来加载classpath路径下的类**的呢？其实是可行的，但这种直接使用getSystemClassLoader()方法获取AppClassLoader加载类有一个缺点，那就是代码**部署到不同服务时会出现问题**，如把代码部署到Java Web应用服务或者EJB之类的服务将会出问题，因为**这些服务使用的线程上下文类加载器并非AppClassLoader，而是Java Web应用服自家的类加载器，类加载器不同**。，所以我们应用该少用getSystemClassLoader()。总之不同的服务使用的可能默认ClassLoader是不同的，但**使用线程上下文类加载器总能获取到与当前程序执行相同的ClassLoader，从而避免不必要的问题**

#### **ClassLoader卸载Class**

JVM中的Class只有满足以下三个条件，才能被GC回收，也就是该Class被卸载（unload）：

- 该类所有的实例都已经被GC。
- 加载该类的ClassLoader实例已经被GC。
- 该类的java.lang.Class对象没有在任何地方被引用。

**GC的时机我们是不可控的，那么同样的我们对于Class的卸载也是不可控的**

### JVM中判断class对象相同的标准

**1.类的完整类名必须一致 包括包名**

**2.加载这个类的ClassLoader（指类加载器的实例对象）必须相同**

换言之 在JVM中 即使两个类对象（class对象）来源于同一个class文件，被同一个虚拟机所加载，但只要加载他们的ClassLoader实例对象不同，那么这两个类对象也是不同。

### 类加载器的引用

JVM必须知道一个类的类型是由启动类加载器加载还是由用户类加载器加载。

**若由用户类加载器加载**：**JVM会将这个类加载器的一个引用作为类信息的一部分保存在方法区（jdk8元空间）中**；当解析一个类型到另一个类型的引用的时候，JVM需要保证两个类型的类加载器是相同的。

### Java程序对类的使用方式

会不会**导致类的初始化** 决定是主动使用还是被动使用

#### 主动使用

1.创建类的实例

2.访问某个类或接口的静态变量，或者对该静态变量赋值

3.调用类的静态方法

4.反射（Class.forName(“全类名”)）

5.初始化一个类的子类

6.Java虚拟机启动时被表明为启动类的类

7.JDK7开始提供的动态语言支持：

![image-20220922102407895](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922102407895.png)

#### 被动使用

除了主动使用的7种情况 其他使用Java类的方式都被看作是对类的**被动使用**，**都不会导致类的初始化**。



## JVM Runtime Memory Area

https://www.digitalocean.com/community/tutorials/java-jvm-memory-model-memory-management-in-java

**内存** 是**硬盘**和**CPU**的**中间仓库及桥梁** **承载着操作系统和应用程序的实时运行**。

**JVM**内存布局规定了Java在运行过程中**内存申请，分配，管理的策略**。**保证JVM的高效稳定运行**

**不同的JVM对于内存的划分方式和管理机制存在着部分差异。**

**根据《Java 虚拟机规范(Java SE 7 版)》规定**

![image-20230402223725954](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402223725954.png)
![image-20220922103933396](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922103933396.png)
![image-20220922104555434](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922104555434.png)红色的为多个线程共享，灰色的为单个线程私有的，即

**线程间共享：堆，对外内存。**

**每个线程：独立包括程序计数器，栈，本地方法栈**
![image-20220922104700100](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922104700100.png)

### 程序计数器（PC Regisster）

**Program Counter Register**	程序计数寄存器

**作用：PC 寄存器 用来储存指向下一条指令的地址，也即将要执行的指令代码。由执行引擎读取下一条指令。**

![image-20220922114918122](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922114918122.png)

![image-20220922112757011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922112757011.png)
![image-20220922114457556](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922114457556.png)

**内存空间小，线程私有**。**字节码解释器工作**是就是**通过改变这个计数器的值来选取下一条需要执行指令的字节码指令**，**分支、循环、跳转、异常处理、线程恢复等基础功能都需要依赖计数器完成**

**如果线程正在执行一个 Java 方法**，这个计数器记录的是**正在执行的虚拟机字节码指令的地址**；

**如果正在执行的是 Native 方法**，这个计数器的值则为 **(Undefined)**。

**此内存区域是唯一一个在 Java 虚拟机规范中没有规定任何 OutOfMemoryError 情况的区域**程序计数器的特点

　　1.线程隔离性，每个线程工作时都有属于自己的独立计数器。
　　2.执行java方法时，程序计数器是有值的，且记录的是正在执行的字节码指令的地址（参考上一小节的描述）。
　　3.执行native本地方法时，程序计数器的值为空（Undefined）。因为native方法是java通过JNI直接调用本地C/C++库，可以近似的认为native方法相当于C/C++暴露给java的一个接口，java通过调用这个接口从而调用到C/C++方法。由于该方法是通过C/C++而不是java进行实现。那么自然无法产生相应的字节码，并且C/C++执行时的内存分配是由自己语言决定的，而不是由JVM决定的

![image-20220922103004735](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922103004735.png)

#### 程序计算器常见问题

![image-20220922115103658](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922115103658.png)
![image-20220922115138514](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922115138514.png)
![image-20220922115320841](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922115320841.png)

#### CPU时间片 ![image-20220922115459403](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922115459403.png)

#### **CPU 并行 并发**

**并发：CPU单个核心同时处理多个线程**（各个线程争夺CPU时间片，在各个线程间来回高频的切换）

**并行：CPU多个核心处理多个线程**

### 虚拟机栈（JVM Stack）

**线程私有，生命周期和线程一致。**描述的是 Java 方法执行的内存模型：**每个方法在执行时都会床创建一个栈帧(Stack Frame)**用于**存储局部变量表、操作数栈、动态链接、方法出口等信息**。**每一个方法从调用直至执行结束，就对应着一个栈帧从虚拟机栈中入栈到出栈的过程**。**负责管理Java程序的运行**

**局部变量表**：存放了编译期可知的各种基本类型(boolean、byte、char、short、int、float、long、double)、对象引用(reference 类型)和 returnAddress 类型(指向了一条字节码指令的地址)

**StackOverflowError：线程请求的栈深度大于虚拟机所允许的深度。**
**OutOfMemoryError：如果虚拟机栈可以动态扩展，而扩展时无法申请到足够的内存**

![image-20220922121032602](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922121032602.png)

![image-20220922121325647](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922121325647.png)

![image-20220922121415970](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922121415970.png)

![image-20220922120356973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922120356973.png)
![image-20220922120446022](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922120446022.png)
![image-20220922120737732](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922120737732.png)

#### 栈可能会出现的异常

![image-20220922121753369](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922121753369.png)

#### 设置栈固定的内存大小

![image-20220922121856779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922121856779.png)

#### 栈的储存单位-栈帧

**基本单位:栈帧** **线程上正在执行的每个方法对应一个栈帧**
**栈 遵循先进后出的原则 只有push压栈 pop弹出栈**

![image-20220922122019231](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922122019231.png)

![image-20220922122228725](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922122228725.png)

![image-20220922122243126](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922122243126.png)

#### 栈帧的内部结构

**每一个栈帧**都包括了**局部变量表**、**操作数栈**、动态连接、方法返回地址和一些额外的附加信息。 **在编译Java程序源码的时候**，**栈帧中需要多大的局部变量表，需要多深的操作数栈就已经被分析计算 出来**，并且**写入到方法表的Code属性之中**[2]。换言之，一个栈帧需要分配多少内存，并不会受到程序 运行期变量数据的影响，而仅仅取决于程序源码和具体的虚拟机实现的栈内存布局形式
![image-20220922153214796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922153214796.png)

![image-20220922133628454](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922133628454.png)
![image-20220922140150860](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922140150860.png)

##### 局部变量表

![image-20220922140309136](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922140309136.png)
![image-20220922144053348](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144053348.png)

![image-20220922141344440](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922141344440.png)

![image-20220922141157285](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922141157285.png)

###### slot槽 重复利用

![image-20220922144036851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144036851.png)

![image-20220922144108124](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144108124.png)

![image-20220922144120973](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144120973.png)

![image-20220922144135710](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144135710.png)

###### 静态变量和局部变量的对比

**局部变量必须显性初始化** 

![image-20220922144310733](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144310733.png)
![image-20220922144332069](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144332069.png)

###### 静态方法&非静态方法的局部变量表

**静态方法的局部变量表中无this变量 因此静态方法中无法使用this.**

![image-20220922145200405](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922145200405.png)

![image-20220922144804451](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144804451.png)

**非静态方法中默认都存在this变量**
![image-20220922145236412](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922145236412.png)

![image-20220922144828044](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922144828044.png)

##### 操作数栈

操作数栈（Operand Stack）也常被称为操作栈，它是一个后入先出（Last In First Out，LIFO） 栈。同局部变量表一样，**操作数栈的最大深度也在编译的时候被写入到Code属性的max_stacks数据项 之中**。

![image-20220922153608081](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922153608081.png)

![image-20220922150755930](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922150755930.png)

![image-20220922150447171](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922150447171.png)

![image-20220922150457435](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922150457435.png)
![image-20220922150557178](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922150557178.png)
![image-20220922150921447](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922150921447.png)

**代码演示**

![image-20220922151651694](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922151651694.png)

![image-20220922151601001](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922151601001.png)

![image-20220922151610177](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922151610177.png)

![image-20220922151618655](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922151618655.png)

![image-20220922151630355](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922151630355.png)

##### 栈顶缓存技术

![image-20220922152641277](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922152641277.png)

##### 动态链接

![image-20220924115541013](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924115541013.png)

![image-20220924115552912](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924115552912.png)

##### 方法的调用

###### 非虚方法

**早在编译期就确定了 在运行时是不可变的**

![image-20220924130607798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130607798.png)

![image-20220924130718490](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130732990.png)
![image-20220924130747487](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130747487.png)

###### 虚方法

![image-20220927090842602](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927090842602.png)

![image-20220924130821628](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130821628.png)

![image-20220924130804702](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130804702.png)
![image-20220924130858208](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924130858208.png)

###### 普通调用指令

![image-20220924131136904](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924131136904.png)

###### 动态调用指令

![image-20220924131144565](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924131144565.png)
![image-20220924131227943](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924131227943.png)
![image-20220924131239943](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924131239943.png)

##### 方法返回地址

**方法返回**

　　　　当一个方法开始执行的时候，可能有**正常退出**和**异常退出**两种情况。

　　　　**正常退出**是指方法正常完成操作并退出，没有抛出任何异常，如果当前方法正常完成，则根据当前方法返回的字节码指令进行处理。该方法返回的字节码指令中有可能存在返回值，也可能不存在返回值。

　　　　**异常退出**是指方法执行过程中遇到异常，并且这个异常在方法体内部没有得到处理，导致方法退出。也就是说无论是Java虚拟机抛出的异常还是代码中使用throw产生的异常，只要在本方法的异常表中没有找到对应的异常处理器，就会导致方法退出。

　　　　无论方法采用何种方式退出，**在方法退出后都需要返回到方法被调用的位置，程序才能继续执行**，方法返回时可能需要在当前栈帧中保存一些信息，用来帮它恢复其上层方法的执行状态。**方法退出过程实际上等同于把当前栈帧出栈**，因此退出可以执行的操作有：**恢复上层方法的局部变量表和操作数栈，如果有返回值，需要将返回值压入调用者的操作数栈中**，同时**调整PC计数器的值以指向方法调用指令后的下一条指令**。

　　　　一般来说，**方法正常退出时，调用者的PC计数器值可以作为返回地址**，栈帧中可能保存此计数值，**而方法异常退出时，返回地址是通过异常处理器表确定的**，栈帧中一般不会保存此部分信息

##### 附加信息

#### 方法的结束-栈的pop

```java
/**
 * 虚拟机栈的查看
 * 方法的结束分为两种 一种是正常的函数返回(return) 一种是抛出异常的结束 都会导致栈帧pop
 */
public class ClassLoadingTest6 {
    public static void main(String[] args) {
        try {
            ClassLoadingTest6 classLoadingTest6 = new ClassLoadingTest6();
            System.out.println(classLoadingTest6.method1());
        } catch (Exception e) {
            throw new RuntimeException(e);
        } finally {
        System.out.println("Eddie");
        }
    }
    public int method1(){
//        System.out.println(10/0);
        return method2();
    }
    public int method2(){
        return method3();
    }
    public int method3(){
        System.out.println("Hello");
        return 10;
    }
}
```

#### 虚拟机栈相关面试题

**①：举例栈溢出的情况？（溢出异常：StackOverFlowError）**

​	通过-Xss设置栈的大小

**②：调整栈的大小，就能保证不出现栈溢出吗？**

​	无法保证；比如递归调用无归情况时；

**③：分配的栈内存越大越好吗？**

​	只是避免过早的出现溢出异常：StackOverFlowError 

​	栈内存大了 会影响线程数的数量 会挤占别的内存空间

**④：垃圾回收会涉及到虚拟机栈吗？**

​	不会的；进栈出栈

**⑤：方法中定义的局部变量是否线程安全？**

​	具体问题具体分析

​	比如StringBuilder 线程不安全 

​	StringBuffer线程安全 



### 本地方法栈（Native Method Stack）

**本地方法栈是用于管理本地方法的调用**

**当一个线程调用了一个本地方法时，它就进入了一个全新的并且不再受虚拟机限制的世界。它和虚拟机有同样的权限。**



![image-20220924141814214](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924141814214.png)

#### 本地方法

Native标识 本地方法

一个Native Method就是一个Java调用非Java代码的接口。

**为了和Java环境外交互**

![image-20220924141918126](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924141918126.png)

例如线程在调用Start（）方法来启动线程时 实际是系统调用本地方法start0（）来启动线程

![image-20220924142141419](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924142141419.png)

### 堆（heep）

![image-20230131120051541](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230131120051541.png)

##### 分区

![image-20220927101930526](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101930526.png)

![image-20220927101843595](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101843595.png)

![image-20220927102014262](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927102014262.png)

![image-20220927101916109](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101916109.png)

##### 分区思想

研究表明：不同的对象 生命周期不同 百分之70-百分之90的对象都是临时对象（朝生夕死）

新生代：有Eden区和两个幸存者区Survivor0以及Survivor1（from以及to）构成；to总为空。

老年代：存放在新生代中经历多次GC（阈值默认15）仍然存活的对象

**分区的唯一理由就是优化GC的性能**

##### 新生代

新对象和没达到一定年龄的对象都在新生代

**Survivor0和Survivor1永远只有一个在被使用 两个不会同时使用 ** 	即有一个幸存者空间总是空的

![image-20220927101941987](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101941987.png)

##### 老年代

被长时间使用的对象，老年代的内存空间应该要比年轻代更大

![image-20220927101954168](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927101954168.png)

##### 元空间（非堆）

（JDK1.8 之前叫永久代）：像一些方法中的操作临时对象等，JDK1.8 之前是占用 JVM 内存，JDK1.8 之后直接使用物理内存

![image-20220927102003408](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927102003408.png)

##### 设置堆内存大小和 OOM

##### 手动设置

开发中建议将初始堆内存 和 最大堆内存设置为一样的值

-Xms6000m -Xmx6000m

![image-20220927103311050](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927103311050.png)

![image-20220927102743735](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927102743735.png)

##### 默认情况

```java
public static void main(String[] args) {

    //返回 JVM 堆大小
    long initalMemory = Runtime.getRuntime().totalMemory() / 1024 /1024;
    //返回 JVM 堆的最大内存
    long maxMemory = Runtime.getRuntime().maxMemory() / 1024 /1024;

    System.out.println("-Xms : "+initalMemory + "M");
    System.out.println("-Xmx : "+maxMemory + "M");

    System.out.println("系统内存大小：" + initalMemory * 64 / 1024 + "G");
    System.out.println("系统内存大小：" + maxMemory * 4 / 1024 + "G");
    //-Xms : 254M
    //-Xmx : 4064M
    //系统内存大小：15G
    //系统内存大小：15G
}
```

##### 查看 设置的参数

两种方式

①:cmd--jps--jstat -gc 进程id

![image-20220927105415037](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927105415037.png)

②:-XX:+PrintGCDetails

![image-20220927105528630](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927105528630.png)

![image-20220927105607060](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927105607060.png)

##### 查看 JVM 堆内存分配

![image-20220927110813485](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927110813485.png)

##### 对象在堆中的生命周期

我们的很多对象都是朝生夕死的

一般情况下，新创建的对象都会被分配到Eden区(一些大对象特殊处理)

这些对象经过第一次Minor GC后，如果仍然存活，将会被移到Survivor区。对象在Survivor区中每熬过一次Minor GC，年龄就会增加1岁，当它的年龄增加到一定程度时，就会被移动到年老代中

![image-20220927111435033](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927111435033.png)

![image-20220927113802658](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927113802658.png)

![image-20220927114247641](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927114247641.png)

##### 对象的分配过程

其中 幸存者区的from区和to区复制（复制算法）之后进行交换 谁空谁为to

一GC一交换 谁空谁是to

关于GC：频繁在新生代中收集 很少在老年代中收集，几乎不在永久代/元空间中收集

![image-20220927114457272](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927114457272.png)



![image-20220927134856686](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927134856686.png)

##### 对象的分配过程的特殊情况

![image-20220927121647339](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927121647339.png)

##### GC 垃圾回收简介

**我们的很多对象都是朝生夕死的**	**因此Minor GC会频繁的触发**

 **Minor GC是Eden区满时触发（Survivor区满不会触发Minor GC）**

![image-20220927124003012](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927124003012.png)

Major GC的速度 比 Minor GC通常 要慢10倍以上 从而STW的时间更长 

**调优时要减少Major GC的触发次数 Full GC的触发次数**

##### 内存分配策略（对象Promotion策略）

![image-20220927141828861](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927141828861.png)

![image-20220927141855732](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927141855732.png)

**大对象直接分配到老年代（新生代无法承载的大对象 直接分配到老年代）**

![image-20220927142308928](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927142308928.png)

##### 堆空间的参数设置

![image-20220927154321104](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927154321104.png)

![image-20220927153736307](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927153736307.png)

##### 空间分配担保

**目前来讲jdk7以来 空间分配担保 默认为true** 

**即：检测到老年代的最大可用的连续空间大于新生代所有对象的总空间（最坏情况下新生代的所有对象都存活下来要晋升到老年代）**

​			**检测到老年代的最大可用连续空间是否大于历次晋升到老年代的对象的平均大小（按照往次的晋升统计）**

​		**都会进行Minor GC 否则进行Full GC**

![image-20220927153800393](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927153800393.png)

##### TLAB

![image-20220927151535365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927151535365.png)

##### 堆是分配对象存储的唯一选择吗

![image-20220927155518020](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927155518020.png)

##### 逃逸分析





![image-20220927164118327](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927164118327.png)

逃逸分析在JIT编译器使用

执行引擎是解释器和JIT编译器混合使用的

**Hotspot虚拟机没有栈上分配 因此是通过标量替换实现的；** **标量替换将聚合量（对象）打散成标量（基本数据类型以及对象的引用）**

换言之：在Hotspot虚拟机中 通过逃逸分析 发现了未发生逃逸的对象 可以进行标量替换 将其存储于栈帧中的局部变量表里。减轻堆空间的压力（GC的频率）

**逃逸分析(Escape Analysis)\**是目前 Java 虚拟机中比较前沿的优化技术\**。这是一种可以有效减少 Java 程序中同步负载和内存堆分配压力的跨函数全局数据流分析算法**。通过逃逸分析，Java Hotspot 编译器能够分析出一个新的对象的引用的使用范围从而决定是否要将这个对象分配到堆上。

**JDK7以来默认开启逃逸分析；**

**开发中  能使用局部变量的就尽量不在方法外定义；**

逃逸分析的基本行为就是分析对象动态作用域：

- **当一个对象在方法中被定义后，对象只在方法内部使用，则认为没有发生逃逸。**
- **当一个对象在方法中被定义后，它被外部方法所引用，则认为发生逃逸。例如作为调用参数传递到其他地方中，称为方法逃逸。**

例如：

```java
public static StringBuffer craeteStringBuffer(String s1, String s2) {
   StringBuffer sb = new StringBuffer();
   sb.append(s1);
   sb.append(s2);
   return sb;
} 
```

`StringBuffer sb`是一个方法内部变量，上述代码中直接将sb返回，这样这个 StringBuffer 有可能被其他方法所改变，这样它的作用域就不只是在方法内部，虽然它是一个局部变量，但是其逃逸到了方法外部。甚至还有可能被外部线程访问到，譬如赋值给类变量或可以在其他线程中访问的实例变量，称为线程逃逸。

上述代码如果想要 `StringBuffer sb`不逃出方法，可以这样写：

```java
public static String createStringBuffer(String s1, String s2) {
   StringBuffer sb = new StringBuffer();
   sb.append(s1);
   sb.append(s2);
   return sb.toString();
}
```

不直接返回 StringBuffer，那么 StringBuffer 将不会逃逸出方法。

**参数设置：**

- 在 JDK 6u23 版本之后，HotSpot 中默认就已经开启了逃逸分析
- 如果使用较早版本，可以通过`-XX"+DoEscapeAnalysis`显式开启

开发中使用局部变量，就不要在方法外定义。

##### **使用逃逸分析，编译器可以对代码做优化：**

**基于逃逸分析：****逃逸分析是以下三个操作的大前提**

**对未发生逃逸的对象：**

**栈上分配** 即分配到栈帧中的局部变量表中（局部变量表中只存储基本数据类型以及对象的引用）；

因此要对未发生逃逸的对象进行**标量替换**将**聚合量（对象）打散成标量（基本数据类型以及对象的引用）**

- **栈上分配**：将堆分配转化为栈分配。如果一个对象在子程序中被分配，要使指向该对象的指针永远不会逃逸，对象可能是栈分配的候选，而不是堆分配
- **同步省略**：如果一个对象被发现只能从一个线程被访问到，那么对于这个对象的操作可以不考虑同步
- **分离对象或标量替换**：有的对象可能不需要作为一个连续的内存结构存在也可以被访问到，那么对象的部分（或全部）可以不存储在内存，而存储在 CPU 寄存器（Java的Hotspot中的栈）--**标量替换可以视为栈上分配的一种特例**；

JIT 编译器在编译期间根据逃逸分析的结果，发现如果一个对象并没有逃逸出方法的话，就可能被优化成栈上分配。分配完成后，继续在调用栈内执行，最后线程结束，栈空间被回收，局部变量对象也被回收。这样就无需进行垃圾回收了。

常见栈上分配的场景：成员变量赋值、方法返回值、实例引用传递

**代码优化之同步省略（锁消除）**

- 线程同步的代价是相当高的，同步的后果是降低并发性和性能
- 在动态编译同步块的时候，JIT 编译器可以借助逃逸分析来判断同步块所使用的锁对象是否能够被一个线程访问而没有被发布到其他线程。如果没有，那么 JIT 编译器在编译这个同步块的时候就会取消对这个代码的同步。这样就能大大提高并发性和性能。这个取消同步的过程就叫做**同步省略，也叫锁消除**。

```java
public void keep() {
  Object keeper = new Object();
  synchronized(keeper) {
    System.out.println(keeper);
  }
}    
```

如上代码，代码中对 keeper 这个对象进行加锁，但是 keeper 对象的生命周期只在 `keep()`方法中，并不会被其他线程所访问到，所以在 JIT编译阶段就会被优化掉。优化成：

```java
public void keep() {
  Object keeper = new Object();
  System.out.println(keeper);
}   
```

**代码优化之标量替换**

**标量**（Scalar）是指一个无法再分解成更小的数据的数据。Java 中的原始数据类型就是标量。

相对的，那些的还可以分解的数据叫做**聚合量**（Aggregate），Java 中的对象就是聚合量，因为其还可以分解成其他聚合量和标量。

在 JIT 阶段，通过逃逸分析确定该对象不会被外部访问，并且对象可以被进一步分解时，JVM 不会创建该对象，而会将该对象成员变量分解若干个被这个方法使用的成员变量所代替。这些代替的成员变量在栈帧或寄存器（Java的Hotspot中的栈）上分配空间。这个过程就是**标量替换**。

通过 `-XX:+EliminateAllocations` 可以开启标量替换，`-XX:+PrintEliminateAllocations` 查看标量替换情况。

```java
public static void main(String[] args) {
   alloc();
}

private static void alloc() {
   Point point = new Point（1,2）;
   System.out.println("point.x="+point.x+"; point.y="+point.y);
}
class Point{
    private int x;
    private int y;
}     
```

以上代码中，point 对象并没有逃逸出 `alloc()` 方法，并且 point 对象是可以拆解成标量的。那么，JIT 就不会直接创建 Point 对象，而是直接使用两个标量 int x ，int y 来替代 Point 对象。

```java
private static void alloc() {
   int x = 1;
   int y = 2;
   System.out.println("point.x="+x+"; point.y="+y);
}      
```

**代码优化之栈上分配**

我们通过 JVM 内存分配可以知道 JAVA 中的对象都是在堆上进行分配，当对象没有被引用的时候，需要依靠 GC 进行回收内存，如果对象数量较多的时候，会给 GC 带来较大压力，也间接影响了应用的性能。为了减少临时对象在堆内分配的数量，JVM 通过逃逸分析确定该对象不会被外部访问。那就通过标量替换将该对象分解在栈上分配内存，这样该对象所占用的内存空间就可以随栈帧出栈而销毁，就减轻了垃圾回收的压力。

##### **逃逸分析总结：**

![image-20220927164103083](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927164103083.png)

关于逃逸分析的论文在1999年就已经发表了，但直到JDK 1.6才有实现，而且这项技术到如今也并不是十分成熟的。

**其根本原因就是无法保证逃逸分析的性能消耗一定能高于他的消耗。虽然经过逃逸分析可以做标量替换、栈上分配、和锁消除。但是逃逸分析自身也是需要进行一系列复杂的分析的，这其实也是一个相对耗时的过程。**

一个极端的例子，就是经过逃逸分析之后，发现没有一个对象是不逃逸的。那这个逃逸分析的过程就白白浪费掉了。

虽然这项技术并不十分成熟，但是他也是即时编译器优化技术中一个十分重要的手段。

### 方法区（Method Area）

#### 方法区的理解

**方法区是一种规范** 不用的JVM版本的方法区的

**具体实现不同** 

比如**JDK8以前的永久代**以及**JDK8以来的元空间**

虽然 Java 虚拟机规范把方法区描述为堆的一个逻辑部分，但是它却有一个别名叫做 **Non-Heap（非堆）**，目的应该是与 Java 堆区分开来。所以，方法区可以看作是一块**独立**于 Java 堆的内存空间。

方法区与 Java 堆一样，是各个线程共享的内存区域。方法区在 JVM 启动时就会被创建，并且它的实际的物理内存空间是可以**不连续**的，关闭 JVM 就会释放这个区域的内存

方法区是所有线程共享的内存，在java8以前是放在JVM内存中的，由永久代实现，受JVM内存大小参数的限制，在java8中移除了永久代的内容，方法区由元空间(Meta Space)实现，并直接放到了本地内存中，不受JVM参数的限制（当然，如果物理内存被占满了，方法区也会报OOM），并且将原来放在方法区的字符串常量池和静态变量都转移到了Java堆中

#### 方法区在 JDK6、7、8中的演进细节

![image-20221024232451041](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024232451041.png)

#### 为什么要去永久代

**合并HotSpot和JRockit--为了兼容JRocket虚拟机（无永久代概念）**

JRockit从来没有所谓的永久代，也不需要开发运维人员设置永久代的大小，但是运行良好。同时也不用担心运行性能问题了,在覆盖到的测试中, 程序启动和运行速度降低不超过1%，但是这点性能损失换来了更大的安全保障

**为永久代设置空间大小是很难确定的。**

在某些场景下，如果动态加载类过多，容易产生 Perm 区的 OOM。如果某个实际 Web 工程中，因为功能点比较多，在运行过程中，要不断动态加载很多类，经常出现 OOM。而元空间和永久代最大的区别在于，元空间不在虚拟机中，而是使用本地内存，所以默认情况下，元空间的大小仅受本地内存限制

**对永久代进行调优较困难**

#### **StringTable 为什么要调整**

因为**永久代的回收效率很低**，在 **full gc 的时候才会触发**。而 full GC 是老年代的空间不足、永久代不足时才会触发。这就**导致了`StringTable` 回收效率不高**。而我们开发中会有大量的字符串被创建，回收效率低，导致永久代内存不足。**放到堆里，能及时回收内存**

#### 方法区（Method Area）的内部结构

方法区用于存储已被虚拟机加载的**类信息**、**常量**、**静态变量**、**即时编译器编译后的代码缓存**等

![image-20221024233701796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024233701796.png)

**类型信息**

对每个加载的类型（ 类 class、接口 interface、枚举 enum、注解 annotation），JVM 必须在方法区中存储以下类型信息：

1. 这个类型的完整有效名称（全名=包名.类名）
2. 这个类型直接父类的完整有效名（对于 interface 或是 java. lang.Object ，都没有父类）
3. 这个类型的修饰符（ public ， abstract， final 的某个子集）
4. 这个类型直接接口的一个有序列表

**域（Field）信息**

- JVM必须在方法区中保存类型的所有域（field，也称为属性）的相关信息以及域的声明顺序；
- 域的相关信息包括：域名称、 域类型、域修饰符（public， private，protected， static， final， volatile， transient 的某个子集）

**方法（Method）信息**

JVM 必须保存所有方法的以下信息，同域信息一样包括声明顺序：

- 方法名称
- 方法的返回类型（或void）
- 方法参数的数量和类型（按顺序）
- 方法的修饰符（public， private， protected， static， final，synchronized， native ， abstract 的一个子集）
- 方法的字节码（bytecodes）、操作数栈、局部变量表及大小（ abstract 和 native 方法除外）
- 异常表（ abstract 和 native 方法除外）每个异常处理的开始位置、结束位置、代码处理在程序计数器中的偏移地址、被捕获的异常类的常量池索引

**运行时常量池**

- 在加载类和结构到虚拟机后，就会创建对应的运行时常量池
- 常量池表（Constant Pool Table）是 Class 文件的一部分，用于存储编译期生成的各种字面量和符号引用，**这部分内容将在类加载后存放到方法区的运行时常量池中**
- JVM 为每个已加载的类型（类或接口）都维护一个常量池。池中的数据项像数组项一样，是通过索引访问的
- 运行时常量池中包含各种不同的常量，包括编译器就已经明确的数值字面量，也包括到运行期解析后才能够获得的方法或字段引用。此时不再是常量池中的符号地址了，这里换为真实地址
  - 运行时常量池，相对于 Class 文件常量池的另一个重要特征是：**动态性**，Java 语言并不要求常量一定只有编译期间才能产生，运行期间也可以将新的常量放入池中，String 类的 `intern()` 方法就是这样的
- 当创建类或接口的运行时常量池时，如果构造运行时常量池所需的内存空间超过了方法区所能提供的最大值，则 JVM 会抛出 OutOfMemoryError 异常。

运行时常量池（Runtime Constant Pool）是方法区的一部分，理解运行时常量池的话，我们先来说说字节码文件（Class 文件）中的常量池（常量池表）

**常量池**

一个有效的字节码文件中除了包含类的版本信息、字段、方法以及接口等描述信息外，还包含一项信息那就是常量池表（Constant Pool Table），包含各种字面量和对类型、域和方法的符号引用。

常量池可以看作是一张表，虚拟机指令根据这张常量表找到要执行的**类名**、**方法名**、**参数类型**、**字面量等类型**

#### 方法区的具体实现（具体JVM版本具体分析）

**JDK8**

![image-20221024231619374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024231619374.png)

![image-20221025000437132](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221025000437132.png)

![image-20221024235559325](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024235559325.png)

#### 方法区的参数设置

- 永久代：OutOfMemoryError:PermGen space
- 元空间：OutOfMemoryError:Metaspace

##### JDK8以前

```java
-XX:PermSize=N //方法区 (永久代) 初始分配空间，默认值为 20.75M
-XX:MaxPermSize=N //方法区 (永久代) 最大可分配空间。32位机器默认是64M，64位机器默认是82M
```

##### JDK8以来

```java
-XX:MetaspaceSize=N //方法区 (元空间) 初始分配空间，如果未指定此标志，则元空间将根据运行时的应用程序需求动态地重新调整大小。
-XX:MaxMetaspaceSize=N //方法区 (元空间) 最大可分配空间，默认值为 -1，即没有限制
```

#### 方法区的垃圾回收

方法区的垃圾收集主要回收两部分内容：**常量池中废弃的常量和不再使用的类型**。

先来说说方法区内常量池之中主要存放的两大类常量：字面量和符号引用。字面量比较接近 Java 语言层次的常量概念，如文本字符串、被声明为 final 的常量值等。而符号引用则属于编译原理方面的概念，包括下面三类常量：

- 类和接口的全限定名
- 字段的名称和描述符
- 方法的名称和描述符

HotSpot 虚拟机对常量池的回收策略是很明确的，只要常量池中的常量没有被任何地方引用，就可以被回收

判定一个类型是否属于“不再被使用的类”，需要同时满足三个条件：

- 该类所有的实例都已经被回收，也就是 Java 堆中不存在该类及其任何派生子类的实例
- 加载该类的类加载器已经被回收，这个条件除非是经过精心设计的可替换类加载器的场景，如 OSGi、JSP 的重加载等，否则通常很难达成
- 该类对应的 java.lang.Class 对象没有在任何地方被引用，无法在任何地方通过反射访问该类的方法

Java 虚拟机被允许堆满足上述三个条件的无用类进行回收，这里说的仅仅是“被允许”，而并不是和对象一样，不使用了就必然会回收。是否对类进行回收，HotSpot 虚拟机提供了 `-Xnoclassgc` 参数进行控制，还可以使用 `-verbose:class` 以及 `-XX:+TraceClassLoading` 、`-XX:+TraceClassUnLoading` 查看类加载和卸载信息。

在大量使用反射、动态代理、CGLib 等 ByteCode 框架、动态生成 JSP 以及 OSGi 这类频繁自定义 ClassLoader 的场景都需要虚拟机具备类卸载的功能，以保证永久代不会溢出

## Java Object

==**Every object has associated a monitor**==

### 创建对象的方式

![image-20221024161545402](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024161545402.png)



### 创建对象的步骤

![image-20221024165832529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024165832529.png)

**----加载类元信息**

**----为对象分配内存**

**----处理并发问题**

**----属性的默认初始化（零值初始化）**

**----设置对象头信息**

**----init()方法进行初始化 显示初始化 代码块中初始化 构造器初始化**

1.判断对象对应的类是否完成加载

虚拟机在遇到一条new指令，首先检查这个指令的参数是否能在MetaSpace的常量池中定位到一个类的符号引用，并且检查这个符号引用代表的类是否已经被加载解析初始化（即判断类元信息是否存在）。如果没有，那么在双亲委派模式下，使用当前类加载器以ClassLoader+包名+类名（全类名）为key进行查找对应的.class文件。如果没有找到文件 则会抛出ClassNotFoundException异常。如果找到，则进行类加载，并在堆空间生成对应的Class对象

2.为对象分配内存

2.1内存规整--指针碰撞

![image-20221024171423090](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024171423090.png)

2.2内存不规整

### 内存布局

![image-20221024174142826](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024174142826.png)

例子

![image-20221024174859555](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024174859555.png)

![image-20221024174521816](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024174521816.png)

![image-20221024174554702](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024174554702.png)

### 访问定位

![image-20221120140242580](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221120140242580.png)

两种方式

**直接引用（Hotspot虚拟机采用）**

![image-20221120140736479](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221120140736479.png)

句柄访问

![image-20221120140810444](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221120140810444.png)

## JVM Garbage Collection

> Java 中的垃圾回收（Garbage Collection）是自动进行的，这意味着程序员不必手动管理内存。Java 虚拟机（JVM）通过垃圾回收器（Garbage Collector）自动检测和清除无用的对象，从而释放内存空间，以便应用程序可以继续运行。
>
> 主要是在Heap Area进行
>
> 垃圾回收器是一个独立的线程，负责回收不再被引用的对象。当垃圾回收器发现一个对象没有被引用时，它会将其标记为可回收的，然后释放其占用的内存空间。



![image-20230402225441859](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402225441859.png)

### Heap Area

![image-20230131120051541](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230131120051541.png)

### Memory allocation strategy

> Java技术体系的自动内存管理，最根本的目标是自动化地解决两个问题：自动给对象分配内存以及自动回收分配给对象的内存。
>
> - **对象优先在Eden园区进行分配**
>
>   - Eden园区有一块很小的区域TLAB：当一个线程需要创建一个对象时，JVM首先为该线程分配一个TLAB，并将该线程的TLAB指向Eden区。然后，该**线程可以在自己的TLAB中分配对象，无需和其他线程竞争Eden区的空间，这样可以减少锁的争用，提高对象分配效率。**
>
> - **大对象直接进入老年代**
>
> - **超过年龄阈值-XX：MaxTenuringThreshold默认15的对象将进入老年代**
>
> - **动态对象年龄判定**如果在Survivor空间中相同年龄所有对象大小的总和大于
>   Survivor空间的一半，年龄大于或等于该年龄的对象就可以直接进入老年代
>
> - **空间分配担保-XX：HandlePromotionFailure**
>
>   检测到老年代的最大可用的连续空间大于新生代所有对象的总空间（最坏情况下新生代的所有对象都存活下来要晋升到老年代）
>
>   检测到老年代的最大可用连续空间是否大于历次晋升到老年代的对象的平均大小（按照往次的晋升统计）都会进行Minor GC 否则进行Full GC
>
>**对象的分配过程：**
> 
>1. 首先，当程序需要创建一个对象时，JVM会在堆区中查找是否有足够的内存空间来存储该对象。如果有足够的内存空间，则进行下一步；否则，会触发垃圾收集器来回收一些不再使用的对象，以腾出足够的内存空间。
> 2. 接下来，JVM会将该对象所需的内存分配给它，此时还未初始化该对象的成员变量。
> 3. 然后，JVM会调用该对象的构造方法，初始化其成员变量。
> 4. 最后，JVM返回该对象的引用，使程序可以通过该引用来操作该对象。
> 
>![image-20220927114457272](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927114457272.png)
> 
>![image-20220927114247641](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927114247641.png)
> 
>

### Minor GC，Major GC，Full GC

> 在 Java 中，Partial GC 和 Full GC 是两种不同的垃圾回收方式。
>
> 
>
> Partial GC 
>
> 是指只对 Java 堆内存的部分区域进行垃圾回收，比如只对新生代或老年代进行回收。Partial GC 通常可以分为两种类型：Young GC 和 Old GC。Young GC（或称为 Minor GC）是针对新生代内存区域的垃圾回收，而 Old GC（或称为 Major GC）是针对老年代内存区域的垃圾回收。在执行 Partial GC 时，只有相应的内存区域会被回收，而其他内存区域则不会受到影响。因此，Partial GC 的执行时间通常比 Full GC 更短，并且不会导致应用程序的暂停。
>
> - Minor GC
> - Major GC
> - Mixed GC（Only G1）
>
> Full GC 
>
> 是指对整个 Java 堆内存进行垃圾回收，包括新生代和老年代。Full GC 的执行时间通常比 Partial GC 更长，并且需要暂停应用程序。在 Full GC 执行期间，所有应用程序线程都会被阻塞。由于 Full GC 需要扫描整个 Java 堆内存，因此其执行时间和频率都应该尽量降低，以保证应用程序的性能和稳定性。



![image-20220927124003012](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927124003012.png)

### Trigger conditions for GC

> 在 Java 中，垃圾回收器会根据一定的策略和条件来触发垃圾回收。下面列举了一些触发 GC 的情况：
>
> 1. 系统空闲时：当系统空闲时，垃圾回收器可能会被触发以回收无用的对象，以便释放内存供系统使用。
> 2. 内存不足时：当 JVM 发现当前的内存不足以支持程序运行时，垃圾回收器可能会被触发以回收无用的对象，以腾出更多的空间。
> 3. 程序调用 System.gc() 方法：程序可以调用 System 类的静态方法 gc() 来请求垃圾回收器立即运行。但是，实际上该方法只是向垃圾回收器发送了一个请求，垃圾回收器是否会立即回收对象，仍然由垃圾回收器自行决定。
> 4. 程序调用 Runtime.getRuntime().gc() 方法：与 System.gc() 方法类似，程序也可以调用 Runtime 类的 gc() 方法来请求垃圾回收器立即运行。
> 5. 对象创建时：Allocation Failure,垃圾回收器可能会被触发以回收无用的对象。（对象最初先分配到Eden区 若分配时Eden园区满了就触发MinorGC）
> 6. 对象存活时间：当程序中的对象已经存在一定时间，或者对象达到了一定的年龄（阈值），垃圾回收器可能会被触发以回收无用的对象。Survivor==>OG
>
> 需要注意的是，虽然程序可以通过调用 System.gc() 或者 Runtime.getRuntime().gc() 方法来请求垃圾回收器立即运行，但是实际上垃圾回收器是否会立即回收对象，还是由垃圾回收器自行决定。因此，在开发中，应该避免过多地依赖垃圾回收器的运行来释放资源，而是要合理地使用内存，及时释放不再需要的对象，以保证程序的性能和稳定性。

### Garbage collection algorithm

> Java 中的垃圾收集算法主要有以下几种：
>
> - ***标记-清除算法（Mark-Sweep Algorithm）***
>
> 标记-清除算法是最简单、最基础的垃圾收集算法。
>
> 它**分为标记和清除两个阶段：**
>
> 标记阶段从根节点开始，遍历所有可达对象并打上标记；
>
> 清除阶段则从头到尾遍历整个堆空间，清除所有没有标记的对象。
>
> 这个算法的**缺点是会产生大量的内存碎片，从而降低内存利用率**。
>
> ![image-20230403001405673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403001405673.png)
>
> - ***复制算法（Copying Algorithm）***
>
> 复制算法将堆空间**划分为两个区域，每次只使用其中一个区域**。当该区域的内存用尽时，将其中存活的对象复制到另外一个区域中，然后清空原来的区域。
>
> 这种算法实现简单，不会产生内存碎片，
>
> 但是**会浪费一半的内存空间**。
>
> ![image-20230403001436434](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403001436434.png)
>
> - ***标记-整理算法（Mark-Compact Algorithm）***
>
> 标记-整理算法是在标记-清除算法的基础上做了一些优化。
>
> 它**同样分为标记和清除两个阶段**：
>
> 标记阶段遍历所有可达对象并打上标记；
>
> 清除阶段将所有存活的对象移动到堆的一端，然后清理掉堆空间的另一端。
>
> 这种算法可以避免内存碎片的产生，
>
> 但是**移动存活的对象需要耗费额外的时间和空间**。
>
> ![image-20230403001416453](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403001416453.png)
>
> - ***分代收集算法（Generational Collection Algorithm）***
>
> 分代收集算法是当前 Java 垃圾回收器中**最常用的算法之一**。
>
> 它将堆空间分为新生代和老年代两个区域，
>
> 新生代中大多数对象是短暂的，因此可以使用复制算法来进行垃圾回收；
>
> 老年代中的对象则更加稳定，因此可以使用标记-整理算法来进行垃圾回收。
>
> 分代收集算法利用不同年龄段对象的生命周期的不同，提高垃圾回收的效率。
>
> - ***增量式收集算法（Incremental Collection Algorithm）***
>
> 增量式收集算法将垃圾回收过程分为多个小阶段，在每个小阶段之间允许程序执行一段时间。这种算法可以让垃圾回收的过程逐渐进行，不会造成长时间的停顿。但是这种算法需要对程序运行的状态做出一些假设，如果这些假设出现错误，可能会导致垃圾回收的不完整。因此，增量式收集算法并不是所有场景都适用。

### Garbage Collector

> HotSpot has four garbage collectors:
>
> - **Serial:** All garbage collection events are conducted serially in one thread. JVM executes the compaction after each garbage collection.
> - **Parallel:** JVM uses multiple threads for minor  garbage collection. It uses a single thread for major garbage collection and Old Generation compaction. Alternatively, the Parallel Old variant  uses multiple threads for major garbage collection and Old Generation  compaction.
> - **CMS (Concurrent Mark Sweep):** Multiple threads are  used for minor garbage collection using the same algorithm as Parallel.  Major garbage collection is multi-threaded, like Parallel Old. Still CMS runs concurrently alongside application processes to minimize “stop the world” events (i.e., when the garbage collector running stops the  application). Here, the JVM does not perform compaction of memory.
> - **G1 (Garbage First):** The newest garbage collector is intended as a replacement for CMS. It is parallel and concurrent, like  CMS. However, it works quite differently under the hood than older  garbage collectors.
>
> 
>
> **Till java 8, `parallel` GC was default algorithm.===>Since java 9, `G1` has been set as default GC algorithm.**



> **Serial**:
>
> Serial（串行）收集器是最基本、历史最悠久的垃圾收集器了。大家看名字就知道这个收集器是一个单线程收集器了。它的 **“单线程”** 的意义不仅仅意味着它只会使用一条垃圾收集线程去完成垃圾收集工作，更重要的是它在**进行垃圾收集工作的时候必须暂停其他所有的工作线程**（ **"Stop The World"** ），**直到它收集结束**。
>
> **新生代采用标记-复制算法，老年代采用标记-整理算法。**
>
> 
>
> 它**简单而高效（与其他收集器的单线程相比）**。Serial 收集器由于没有线程交互的开销，自然可以获得很高的单线程收集效率。Serial 收集器对于运行在 Client 模式下的虚拟机来说是个不错的选择。
>
> ![image-20230403003634648](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403003634648.png)



> **Parallel Scavenge**:
>
> **JDK1.8 默认收集器**
>
> **Parallel Scavenge 收集器关注点是吞吐量（高效率的利用 CPU）。CMS 等垃圾收集器的关注点更多的是用户线程的停顿时间（提高用户体验）。所谓吞吐量就是 CPU 中用于运行用户代码的时间与 CPU 总消耗时间的比值。** Parallel Scavenge 收集器提供了很多参数供用户找到最合适的停顿时间或最大吞吐量，如果对于收集器运作不太了解，手工优化存在困难的时候，使用 Parallel Scavenge 收集器配合自适应调节策略，把内存管理优化交给虚拟机去完成也是一个不错的选择。
>
> **新生代采用标记-复制算法，老年代采用标记-整理算法。**
>
> ![image-20230403003100936](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403003100936.png)



> **CMS（Concurrent Mark Sweep）**:
>
> **以获取最短回收停顿时间为目标的收集器。它非常符合在注重用户体验的应用上使用。**
>
> **CMS（Concurrent Mark Sweep）收集器是 HotSpot 虚拟机第一款真正意义上的并发收集器，它第一次实现了让垃圾收集线程与用户线程（基本上）同时工作。**
>
> 
>
> 主要优点：**并发收集、低停顿**。
>
> 
>
> 明显的缺点：
>
> - **对 CPU 资源敏感；**
> - **无法处理浮动垃圾；**
> - **它使用的回收算法-“标记-清除”算法会导致收集结束时会有大量空间碎片产生。**
>
> **Mark Sweep**这两个词可以看出，CMS 收集器是一种 **“标记-清除”算法**实现的，它的运作过程相比于前面几种垃圾收集器来说更加复杂一些。整个过程分为四个步骤：
>
> - **初始标记：** 暂停所有的其他线程，并记录下直接与 root 相连的对象，速度很快 ；
> - **并发标记：** 同时开启 GC 和用户线程，用一个闭包结构去记录可达对象。但在这个阶段结束，这个闭包结构并不能保证包含当前所有的可达对象。因为用户线程可能会不断的更新引用域，所以 GC 线程无法保证可达性分析的实时性。所以这个算法里会跟踪记录这些发生引用更新的地方。
> - **重新标记：** 重新标记阶段就是为了修正并发标记期间因为用户程序继续运行而导致标记产生变动的那一部分对象的标记记录，这个阶段的停顿时间一般会比初始标记阶段的时间稍长，远远比并发标记阶段时间短
> - **并发清除：** 开启用户线程，同时 GC 线程开始对未标记的区域做清扫。
>
> ![image-20230403003741563](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403003741563.png)



> **G1 (Garbage-First)** :
>
> **一款面向服务器的垃圾收集器,主要针对配备多颗处理器及大容量内存的机器. 以极高概率满足 GC 停顿时间要求的同时,还具备高吞吐量性能特征.**
>
> 具备以下特点：
>
> - **并行与并发**：G1 能充分利用 CPU、多核环境下的硬件优势，使用多个 CPU（CPU 或者 CPU 核心）来缩短 Stop-The-World 停顿时间。部分其他收集器原本需要停顿 Java 线程执行的 GC 动作，G1 收集器仍然可以通过并发的方式让 java 程序继续执行。
> - **分代收集**：虽然 G1 可以不需要其他收集器配合就能独立管理整个 GC 堆，但是还是保留了分代的概念。
> - **空间整合**：与 CMS 的“标记-清除”算法不同，G1 从整体来看是基于“标记-整理”算法实现的收集器；从局部上来看是基于“标记-复制”算法实现的。
> - **可预测的停顿**：这是 G1 相对于 CMS 的另一个大优势，降低停顿时间是 G1 和 CMS 共同的关注点，但 G1 除了追求低停顿外，还能建立可预测的停顿时间模型，能让使用者明确指定在一个长度为 M 毫秒的时间片段内。
>
> G1 收集器的运作大致分为以下几个步骤：
>
> - **初始标记**
> - **并发标记**
> - **最终标记**
> - **筛选回收**
>
> **G1 收集器在后台维护了一个优先列表，每次根据允许的收集时间，优先选择回收价值最大的 Region(这也就是它的名字 Garbage-First 的由来)** 。这种使用 Region 划分内存空间以及有优先级的区域回收方式，保证了 G1 收集器在有限时间内可以尽可能高的收集效率（把内存化整为零）。
>
> ![image-20230403003811253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230403003811253.png)

### Judgment of the object of death

> 在 Java 中，死亡对象是指无法再被应用程序访问到的对象。Java 垃圾回收器会定期扫描内存，找到这些死亡对象，并将其回收释放内存空间。Java 中判断一个对象是否为死亡对象的方法有以下两种：
>
> 1. **引用计数法**：每个对象都有一个引用计数器，当有引用指向该对象时，计数器加 1，当引用被销毁时，计数器减 1。当计数器的值为 0 时，该对象被判定为死亡对象。但是，引用计数法无法解决循环引用的问题(**垃圾相互引用问题**)，即两个或多个对象之间互相引用，导致它们的引用计数器的值永远不为 0，这样这些对象就会一直存在于内存中而无法被回收。
>
> 2. **可达性分析算法**：**可达性分析算法是一种常用的垃圾回收算法**，其基本思想是通过一系列的“GC Roots”对象作为起点，从这些根对象开始遍历整个对象图，找到所有可达的对象，未被遍历到的对象即为死亡对象。Java 中的 **GC Roots** 对象包括：
>
>    - 虚拟机栈中引用的对象
>    - 方法区中类静态属性引用的对象
>    - 方法区中常量引用的对象
>    - 本地方法栈中 JNI（Java Native Interface）引用的对象
>
>    ![image-20230402234130605](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402234130605.png)
>
> 可达性分析算法可以处理循环引用的问题，因为它能够识别出不再与 GC Roots 对象相连的一组对象，即为不可达对象，这些对象会被判定为死亡对象并进行回收。



### The reference type of the object

> 在 Java 中，引用类型用于描述一个对象在内存中的使用情况和引用方式，Java 中共有四种引用类型，分别是：
>
> 1. **强引用（Strong Reference）**：最常见的引用类型，也是默认的引用类型。**如果一个对象具有强引用**，**垃圾回收器就不会回收**它，即使该对象已经没有被任何变量所引用。当程序中的某个对象拥有强引用时，该对象就一直存在于内存中，直到该引用被显式地设置为 null 或者被赋值为其他对象。
> 2. **软引用（Soft Reference）：**用于描述一些有用但非必须的对象。如果一个对象只有软引用，那么在**内存不足时，垃圾回收器可能会回收它**，释放内存空间。当程序需要该对象时，可以通过软引用重新获取它。在 Java 中，软引用通常用于缓存。
> 3. **弱引用（Weak Reference）：**用于描述一些非必须的对象，比软引用更加弱化。如果一个对象只有弱引用，那么在垃圾回收时，**无论内存是否充足，都会被回收**，释放内存空间。弱引用通常用于解决内存泄漏问题，比如在对象与其它对象之间存在循环引用的情况下，使用弱引用可以解除这种循环引用。
> 4. **虚引用（Phantom Reference）：**用于**描述那些已经被回收的对象**。虚引用无法通过它直接访问到对象的实例，也无法通过它获取对象的状态或者执行任何操作。**虚引用主要用于跟踪对象被垃圾回收的状态**，提供一种在对象被回收时收到系统通知的机制，可以用来进行资源清理或者其他清理操作。

### A class that is judged to be useless

> 在 Java 中，类对象通常会被加载器持有，因此判断一个类是否是无用的类需要从类加载器入手。JVM 中每个类加载器都维护了一个加载的类的列表，如果一个类不再被引用，那么该类就可以被卸载。
>
> 在垃圾回收器扫描内存时，它会从根集开始，遍历所有可达的对象，将不可达的对象标记为垃圾，然后进行回收。类加载器也是从根集开始遍历，判断是否有引用指向该类，如果没有则认为该类可以被卸载。
>
> 具体来说，JVM 中对于一个类的卸载，需要满足以下三个条件：
>
> 1. 该类的**所有实例都已经被 GC 回收**，即**没有任何实例引用了该类**。
> 2. 该类的 **Class 对象已经被 GC 回收**。
> 3. 该类的 **ClassLoader 已经被 GC 回收**。
>
> 只有当以上三个条件都满足时，该类才可以被卸载。



> **判断一个常量是废弃常量**
>
> 在 Java 中，常量池是 JVM 用于存储常量的区域，包括编译器生成的常量和手动添加的常量。在判断一个常量是否是废弃常量时，需要从常量池入手。
>
> 常量池中的常量分为两种类型：字面量和符号引用。字面量包括字符串、数字等常量，而符号引用包括类和方法的引用。对于一个废弃的常量，可以理解为其对应的字面量或符号引用没有被使用。
>
> 在垃圾回收器扫描内存时，会从根集开始，遍历所有可达的对象，将不可达的对象标记为垃圾，然后进行回收。常量池中的常量也是从根集开始遍历，判断是否有引用指向该常量，如果没有则认为该常量可以被回收。
>
> 具体来说，JVM 中对于一个常量的回收，需要满足以下条件：
>
> 1. 该**常量所在的类没有被加载，或者该常量所在的类已经被卸载**。
> 2. 该**常量没有被任何对象引用**。
>
> 只有当以上两个条件都满足时，该常量才可以被回收。



## JVM Out Of Memory



## JVM Performance Optimization

