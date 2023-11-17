# Java程序执行过程

```java
//reference
https://blog.csdn.net/qq_40653180/article/details/88874987//Java程序运行全过程
https://blog.csdn.net/moneyshi/article/details/53033577//JVM结构、GC工作机制详解
https://blog.csdn.net/java2000_wl/article/details/8030172//Java虚拟机学习 - 垃圾收集器
https://blog.csdn.net/tonytfjing/article/details/47212291//深入分析ClassLoader
```

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/202012120855371.jpg)

- **步骤 1： 写源代码，源代码将以.java的文件格式保存在电脑硬盘中。**
- **步骤 2： 编译器（compiler）检查是否存在编译期错误（例如缺少分号，关键字拼写错误等）。若通过检测，编译器就会将源代码翻译成字节码（bytecode），以.class的文件格式保存在电脑硬盘中。**
- **步骤 3： 若要运行此Java程序，JVM中会有一个叫类加载器（class loader）的内置程序把字节码从硬盘载入到正位于内存中的JVM里去。**
- **步骤 4： JVM中还有一个叫字节码校验器（bytecode verifier）的内置程序检测是否存在运行期错误（例如栈溢出）。若通过检测，字节码校验器就会将字节码传递给解释器（interpreter）。**
- **步骤 5： 解释器会对字节码进行逐行翻译，将其翻译成当前所在系统可以理解的机器码（machine code），**
- **步骤 6：将机器码交给操作系统，操作系统会以main方法作为入口开始执行程序。至此，一个Java程序就这样运行起来了。**

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/202012120855382.png)

- 情况 1： 解释器对代码进行逐行解释，正如我们在步骤中所介绍的。
- 情况 2： 这是JIT编译器参与进Java执行过程的情况，JIT编译器会扫描所有代码并对其进行优化。例如此时它发现最后一行代码是重复多余的，就会将其移除，只传递前4行代码给解释器。这样解释器就能运行地更快速高效，毕竟少了一行多余的代码需要翻译。

当然，这只是JIT编译器的优化手段之一，不同公司设计的JIT编译器对Java程序的运行会有不同的优化方式。此外需要知道的是，JIT编译器并不是每次都会参与到执行过程中来

![image-20220719172710846](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220719172710846.png)

![image-20220719172746680](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220719172746680.png)





# 内存机制



通常，在载入内存后，一个Java程序所占用的内存会被大致分为3块区域：堆（heap），栈（stack）和方法区（method area）。

**堆：存放new出来的东西。**

**栈：存放局部变量。**

**方法区：类型信息，字段信息，常量池（constant pool），静态变量，方法信息等。**

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/202012120855393.jpg)

**PC寄存器**：存放将要执行的指令的地址。（因为机器的脑子不灵活，所以需要一块专门的区域帮他记住执行到哪一步，不然它会忘记）

![image-20220713181611656](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220713181611656.png)

**本地方法栈**：与JVM栈所发挥的作用是非常相似的，其区别不过是JVM栈为Java方法服务，而本地方法栈则是为使用到的Native方法服务。有的虚拟机（例如Sun HotSpot虚拟机）甚至直接就把本地方法栈和虚拟机栈合二为一。

每个线程拥有各自独立的（虚拟机）栈、PC寄存器和本地方法栈。而堆和方法区则是所有线程共享的。

最后让我们通过一个小例子来理解Java程序执行时内存的变化。

![image-20220713181654661](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220713181654661.png)

首先，在stack中申请了一块内存，这块内存区域名字叫Tom，此时区域里存储的内容为null。

接着，调用Person的构造方法，方法的参数属于局部变量，因此在stack中有两块区域分别存放id1和age1。

通过构造方法，可以new出来一个Person的对象，这个对象连带着其成员变量会被存放在heap中。成员变量id和age的值由存放在stack中的局部变量id1和age1赋予。

最后，将这个对象的引用值（类似于地址）传递给Tom，通过引用值我们就可以找到这个对象。

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/202012120855404.png)

（注意：位于stack中的id1和age1会随着构造方法调用的结束而消失，这里为了更好地表现全过程，因此保留在图中。）









# 关于栈和堆的其他小知识

- 栈和堆的大小都是固定为一个默认值的，它们作为jvm的参数设定好了，不同的jvm设定的参数不同，相应的栈和堆的大小也就不同。
- 栈是运行时的单位：里面存储的信息都是跟当前线程相关的，包括局部变量、程序运行状态、方法返回值等；而堆是存储的单位：它只负责存储对象。
- 当一个方法调用结束后，方法里的局部变量会随之消失，不会在stack中继续占用空间。栈与堆的分离使得不同线程可以访问同一个对象，这是一种有效的数据交互方式（共享内存）；此外也节省了空间，因为堆中的共享常量和缓存可以被所有栈访问。