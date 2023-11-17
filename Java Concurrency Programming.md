# Java Concurrency Programming

## 理论基础

### CPU 缓存模型

> **CPU Cache 缓存的是内存数据用于解决 CPU 处理速度和内存不匹配的问题(CPU 处理速度和内存处理速度不对等)，**
>
> 内存缓存的是硬盘数据用于解决硬盘访问速度过慢的问题
>
> ![image-20230412004416756](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230412004416756.png)

![image-20230211100635374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211100635374.png)

![image-20230211095448065](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211095448065.png)

### **指令重排序**

> ==指令重排==:为了提升执行速度/性能，计算机在执行程序代码的时候，会对指令进行重排序.指令重排的前提是，重排指令不能影响结果
>
> - **编译器优化重排** ：==编译器==（包括 JVM、JIT 编译器等）在不改变单线程程序语义的前提下，重新安排语句的执行顺序。
> - **指令并行重排** ：现代==处理器==采用了指令级并行技术(Instruction-Level Parallelism，ILP)来将多条指令重叠执行。如果不存在数据依赖性，处理器可以改变语句对应机器指令的执行顺序。
>
> Java 源代码会经历 **编译器优化重排 —> 指令并行重排 —> 内存系统重排** 的过程，最终才变成操作系统可执行的指令序列。



> **对于编译器，**通过禁止特定类型的编译器重排序的方式来禁止重排序。
>
> **对于处理器，**通过插入内存屏障（Memory Barrier，或有时叫做内存栅栏，Memory Fence）的方式来禁止特定类型的处理器重排序。指令并行重排和内存系统重排都属于是处理器级别的指令重排序。
>
> - 内存屏障（Memory Barrier，或有时叫做内存栅栏，Memory Fence）是一种 CPU 指令，用来禁止处理器指令发生重排序（像屏障一样），从而保障指令执行的有序性。另外，为了达到屏障的效果，它也会使处理器写入、读取值之前，将主内存的值写入高速缓存，清空无效队列，从而保障变量的可见性。



> **指令重排序可以保证串行语义一致，但是没有义务保证多线程间的语义也一致** ，所以在多线程下，指令重排序可能会导致一些问题。

### 上下文切换

> 上下文切换：
>
> 多线程编程中一般线程的个数都大于 CPU 核心的个数，而一个 CPU 核心在任意时刻只能被一个线程使用，为了让这些线程都能得到有效执行，CPU 采取的策略是为每个线程**分配时间片**并**轮转**的形式。当一个线程的时间片用完的时候就会重新处于就绪状态让给其他线程使用，这个过程就属于一次上下文切换。概括来说就是：当前任务在执行完 CPU 时间片切换到另一个任务之前会先保存自己的状态，以便下次再切换回这个任务时，可以再加载这个任务的状态。
>
> **任务从保存到再加载的过程就是一次上下文切换**。
>
> **挂起线程**和**恢复线程**的操作**都需要转入内核态中完成**，这些操作对系统的并发性能带来了很大的压力
>
> 上下文切换通常是计算密集型的。也就是说，它需要相当可观的处理器时间，在每秒几十上百次的切换中，每次切换都需要纳秒量级的时间。所以，上下文切换对系统来说意味着消耗大量的 CPU 时间，事实上，可能是操作系统中时间消耗最大的操作。
>
> Linux 相比与其他操作系统（包括其他类 Unix 系统）有很多的优点，其中有一项就是，其上下文切换和模式切换的时间消耗非常少。

### 并发三要素

> ==可见性==: **CPU缓存**引起可见性：一个线程对共享变量的修改，另外一个线程能够立刻看到。
>
> ==原子性==: **CPU按时间片分时复用**（（线程切换））引起原子性：即一个操作或者多个操作 **要么全部执行**并且不会被任何因素打断，**要么就都不执行**。
>
> ==有序性==: **重排序**引起有序性：即程序执行的顺序按照代码的先后顺序执行。
>
> - 编译器优化的重排序。编译器在不改变单线程程序语义的前提下，可以重新安排语句的执行顺序。
> - 指令级并行的重排序。现代处理器采用了指令级并行技术（Instruction-Level Parallelism， ILP）来将多条指令重叠执行。如果不存在数据依赖性，处理器可以改变语句对应机器指令的执行顺序。
> - 内存系统的重排序。由于处理器使用缓存和读 / 写缓冲区，这使得加载和存储操作看上去可能是在乱序执行。

#### 可见性

> 当一个线程对共享变量进行了修改，那么另外的线程都是立即可以看到修改后的最新值。
>
> 在 Java 中，可以借助`synchronized` 、`volatile` 以及各种 `Lock` 实现可见性。
>
> 如果我们将变量声明为 `volatile` ，这就指示 JVM，这个变量是共享且不稳定的，每次使用它都到主存中进行读取

#### 原子性

> 一次操作或者多次操作，要么所有的操作全部**都得到执行**并且**不会受到任何因素的干扰**而中断，要么**都不执行**。
>
> 在 Java 中，可以借助`synchronized` 、各种 `Lock` 以及各种原子类实现原子性。
>
> `synchronized` 和各种 `Lock` 可以保证任一时刻只有一个线程访问该代码块，因此可以保障原子性。各种原子类是利用 CAS (compare and swap) 操作（可能也会用到 `volatile`或者`final`关键字）来保证原子操作。

#### 有序性

> 由于指令重排序问题，代码的执行顺序未必就是编写代码时候的顺序。
>
> Java 源代码会经历 **编译器优化重排 —> 指令并行重排 —> 内存系统重排** 的过程，最终才变成操作系统可执行的指令序列。
>
> 我们上面讲重排序的时候也提到过：
>
> > **指令重排序可以保证串行语义一致，但是没有义务保证多线程间的语义也一致** ，所以在多线程下，指令重排序可能会导致一些问题。
>
> 在 Java 中，`volatile` 关键字可以禁止指令进行重排序优化。
>
> 对于处理器重排序,JMM的处理器重排序规则会要求Java编译器在生成指令序列时,插入特定类型的内存屏障(Memory Barriers,Intel称之为Memory Fence)指令,通过内存屏障指令来禁止特定类型的处理器重排序。

### 线程安全的实现方法

> **同步方案**
>
> - **Mutex（阻塞）同步**
>   - synchronized 
>   - ReentrantLock...
> - **非阻塞同步**
>   - CAS（轻量级锁）
>   - AtomicInteter(原子类操作)
>
> **无同步方案**
>
> - 栈封闭
> - 线程本地存储(ThreadLocal Storage)

## 线程基础

## Java并发机制的底层实现原理

### Java Object Memory Layout

![image-20221024174142826](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221024174142826.png)

In Hotspot VM, the object layout in the heap can be divided into three parts,

1. Header
2. Instance Data
3. Padding

#### Header:eyes:

It saves two types of information.

1. Save the object self's runtime information, the officials call it `Mark Word`, such as HashCode, GC generation age, lock states, the lock that the thread holds, biased thread id, biased timestamp.
2. Save the type pointer, that's the pointer to the meta-type, Java VM used it  to determine which type of this object is, this is an optional  implementation in the VM.
   If the object is an array, there is a data in the header to save the array's length

##### Mark Word:eye:

![image-20230210154448670](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210154448670.png)

```
一个对象创建时：
如果开启了偏向锁（默认开启），那么对象创建后，markword 值为 0x05 即最后 3 位为 101，这时它的 thread、epoch、age 都为 0
偏向锁是默认是延迟的，不会在程序启动时立即生效，如果想避免延迟，可以加 VM 参数 
-XX:BiasedLockingStartupDelay=0 来禁用延迟
如果没有开启偏向锁，那么对象创建后，markword 值为 0x01 即最后 3 位为 001，这时它的 hashcode、age 都为 0，第一次用到 hashcode 时才会赋值

轻量锁和重量锁一个会把hashcode放在栈帧的锁记录，一个会放到monitor中（解锁的时候会还原回来）
而偏向锁没有额外的储存空间 当获取了hashcode则会弃用偏向锁（消除偏向状态） 重写markword

谨记偏向是指类偏向，而不是对象实例偏向；一个类只能有一个偏向
```

![image-20230210154116888](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210154116888.png)

![image-20230210145412031](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210145412031.png)



The 32 bit and 64 bit VM are different.

- 32-bit word

| Object              | Format                                                    |
| ------------------- | --------------------------------------------------------- |
| normal object       | hash: 25, age: 4, biased_lock: 1, lock: 2                 |
| biased object       | JavaThread*: 23, epoch: 2 age: 4, biased_lock: 1, lock: 2 |
| CMS free block      | 32 bits                                                   |
| CMS promoted object | PromotedObject*: 29, promo_bits: 3                        |

- 64-bit word

| Object                       | Format                                                       |
| ---------------------------- | ------------------------------------------------------------ |
| normal object                | unused: 25, hash: 31, unused: 1, age: 4, biased_lock: 1, lock: 2 |
| biased object                | JavaThread*: 54, epoch: 2, unused: 1, age: 4, biased_lock: 1, lock: 2 |
| CMS promoted object          | PromotedObject*: 61, promo_bits: 3                           |
| CMS free block               | 64 bits                                                      |
| COOPs && normal object       | unused: 25, hash: 31, cms_free: 1, age: 4, biased_lock: 1, lock: 2 |
| COOPs && biased object       | JavaThread*: 54, epoch: 2, cms_free: 1, age: 4, biased_lock: 1, lock: 2 |
| COOPs && CMS promoted object | narrowOop: 32, unused: 24, cms_free: 1, unused: 4, promo_bits: 3 |
| COOPs && CMS free block      | unused: 21, size: 35, cms_free: 1, unused: 7                 |

##### Class Metadata Address

指向该对象的所属类型



##### Is Array ? Array Length : nothing

#### Instance Data

The instance data saves the variables defined in the class, including the  variable defined in the parent class. The store sequence will be  impacted by the JVM argument `-XX:FieldsAllocationStyle` and the sequence defined in the class.

> The Hotspot's default allocation sequence is that,
>
> - longs/doubles
> - ints
> - shorts/chars
> - bytes/booleans
> - oops(Ordinary Object Pointers, OOP)

Also, if JVM argument `-XX:CompactFields` is true(default value), the thinner variable in the child class will be inserted into the gap of parent variables.

#### Padding

The HotSpot VM's auto memory management system requires the starting  address of the object must be 8-byte event digits, which means any  object's size muse be 8-byte event digits. So, if an object's instance  data doesn't align, it needs padding.



### JMM(Java 内存模型)

> 我们的程序运行在操作系统之上，操作系统屏蔽了底层硬件的操作细节，将各种硬件资源虚拟化。于是，操作系统也就同样需要解决内存缓存不一致性问题。
>
> 操作系统通过 **内存模型（Memory Model）** 定义一系列规范来解决这个问题。无论是 Windows 系统，还是 Linux 系统，它们都有特定的内存模型
>
> Java 语言是跨平台的，它需要**Java自己提供一套内存模型以屏蔽系统差异**
>
> **并发编程下要遵守的并发相关的原则和规范**
>
> [《JSR-133：Java Memory Model and Thread Specification》](http://www.cs.umd.edu/~pugh/java/memoryModel/CommunityReview.pdf)
>
> 
>
> Java内存模型（Java Memory Model，简称JMM）**定义了Java虚拟机如何管理Java程序中的内存，以及线程之间如何进行通信。**JMM的目标是保证Java程序在任何平台上都能够正确地执行，不受各种硬件和操作系统的影响。
>
> 
>
> JMM旨在**解决多线程编程中**的**可见性、原子性**和**有序性**等问题，**确保多线程环境下的程序行为是可预测且正确的**。
>
> 
>
> Java内存模型主要由以下三个部分组成：
>
> 1. **内存访问规则（Memory Access Rules）**：定义了Java程序中的变量在内存中的读取和写入规则，以及这些规则的可见性和原子性。
> 2. **线程之间的交互（Thread Interaction）**：定义了线程之间如何进行通信以及如何协作，以保证Java程序的正确性。
> 3. **Happens-Before关系（Happens-Before Relationship）**：定义了Java程序中不同操作之间的先后关系，以保证Java程序的正确性。
>
> 在**Java内存模型中**，**每个线程都有自己的工作内存**，线程**对变量的操作都是在工作内存中进行**的。**当线程需要读取共享变量的值时，需要从主内存中获取变量的值，当线程需要修改共享变量的值时，需要先在工作内存中修改变量的值，然后将修改后的值刷新到主内存中**。JMM规定了读取和写入操作的顺序以及可见性和原子性的要求，以保证多个线程之间对共享变量的操作不会产生冲突和数据不一致的问题。
>
> ![image-20230401000647251](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401000647251.png)
>
> 
>
> Happens-Before关系是Java内存模型中非常重要的一个概念，它用来保证Java程序中的操作按照一定的顺序执行。如果一个操作happens-before另一个操作，那么第一个操作的结果对于第二个操作是可见的。JMM规定了一些情况下的Happens-Before关系，例如线程的启动和结束，synchronized块的进入和退出等等。这些规定能够保证Java程序的正确性，避免出现一些奇怪的并发问题。
>
> **逻辑时钟并不度量时间本身，仅区分事件发生的前后顺序，其本质就是定义了一种 happens-before 关系。**
>
> ![image-20230401001125941](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401001125941.png)

### Memory Barrier

> 在Java中，屏障（barrier）通常指的是内存屏障，它们用于控制内存访问的顺序以确保多线程程序的正确性和可见性。有读屏障、写屏障、通用屏障和优化屏障等不同类型的内存屏障。
>
> 
>
> 这些屏障在Java中通常由编译器、虚拟机以及底层硬件来实现和管理，开发者在编写多线程程序时通常不需要直接操作这些屏障。相反，Java提供了高级的并发工具和关键字（例如`synchronized`和`volatile`）来帮助开发者编写线程安全的代码，而这些工具会隐含地使用内存屏障来确保正确的内存访问顺序和可见性。
>
>
> 
> 对于处理器重排序,JMM的处理器重排序规则会要求Java编译器在生成指令序列时,插入特定类型的内存屏障(Memory Barriers,Intel称之为Memory Fence)指令,通过内存屏障指令来禁止特定类型的处理器重排序。



> 1. 读屏障（Read Barrier）：
>    - 读屏障确保一个线程在读取变量的值之前，会从主内存中获取最新的值，而不是使用本地缓存中的旧值。
>    - 读屏障通常用于确保变量的可见性，防止出现脏读或不一致的数据访问。
> 2. 写屏障（Write Barrier）：
>    - 写屏障用于确保一个线程在写入变量的值之后，将这个写操作刷新到主内存中，以便其他线程可以看到最新的值。
>    - 写屏障通常用于确保变量的可见性，防止写入操作被重排序或延迟。
> 3. 通用屏障（Full Barrier）：
>    - 通用屏障是读屏障和写屏障的组合，它既确保一个线程在读取变量之前获取最新值，也确保在写入变量之后将写操作刷新到主内存。
>    - 通用屏障用于更严格的内存同步需求，例如在多线程之间建立 happens-before 关系。
> 4. 优化屏障（Optimization Barrier）：
>    - 优化屏障通常是一种编译器或运行时系统的优化技术，用于防止编译器对指令重排序或优化过度，从而影响多线程程序的行为。
>    - 优化屏障有助于维护多线程程序的语义一致性，确保程序不会出现意外的结果。

### Monitor

> **Each object and its class are associated with a monitor.**



> Java's monitor supports two kinds of thread synchronization: ==*mutual exclusion*== and ==*cooperation*==. 
>
> 
>
> ==*mutual exclusion*==, which is supported in the Java virtual machine via  object locks, enables multiple threads to **independently work on shared  data without interfering with each other**;**only one thread can "own" at any one time.**
>
> :lock:每个 Java 对象都可以关联一个 Monitor 对象，如果使用 synchronized 给对象上锁（重量级）之后，该对象头的Mark Word 中就被设置指向 Monitor 对象的指针
>
> 
>
> ==*cooperation*==, which is supported in the Java virtual machine via the ==wait== and ==notify== methods of class `Object`, **enables threads to work together towards a common goal.**
>
> | Method                                 | Description                                                  |
> | -------------------------------------- | ------------------------------------------------------------ |
> | `void wait();`                         | Enter a monitor's wait set until notified by another thread<br />This method should **only be called by** a thread that is the **owner of this object's monitor.** |
> | `void wait(long timeout); `            | Enter a monitor's wait set until notified by another thread or `timeout` milliseconds elapses |
> | `void wait(long timeout, int nanos); ` | Enter a monitor's wait set until notified by another thread or `timeout` milliseconds plus `nanos` nanoseconds elapses<br />**timeout** – the maximum time to wait in milliseconds.<br/>**nanos** – additional time, in nanoseconds range 0-999999. |
> | `void notify();`                       | Wake up one thread waiting in the monitor's wait set. (If no threads are waiting, do nothing.) |
> | `void notifyAll();`                    | Wake up all threads waiting in the monitor's wait set. (If no threads are waiting, do nothing.) |





![image-20230210222837992](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210222837992.png)

> - 刚开始 Monitor 中 Owner 为 null
> - （==上锁==）当 Thread-3 执行 synchronized(obj) 就会将 Monitor 的所有者 Owner 置为 Thread-3，Monitor中只能有一个 Owner
> - 在 Thread-3 上锁的过程中，如果 Thread-4，Thread-5，Thread-6 也来执行 synchronized(ObjectA)，就会进入 EntryList BLOCKED
> - （==解锁==）Thread-3 执行完同步代码块的内容会释放锁，将Owner置为null然后唤醒 EntryList 中等待的线程来竞争锁，竞争的时是非公平的
> - 图中 WaitSet 中的 Thread-1，Thread-2 是之前获得过锁，但条件不满足进入 WAITING 状态的线程

![image-20230210133507494](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210133507494.png)

### synchronized

#### synchronized底层实现

> **当一个线程试图访问synchronized同步代码块或方法时**，它首先**必须得到锁**;
>
> **退出或抛出异常时必须释放锁**
>
> 
>
> JVM基于进入和退出Monitor对象来实现方法同步和代码块同步
>
> 
>
> **代码块级别**的 JVM中==monitorenter==和==monitorexit==字节码指令依赖于底层的操作系统的**Mutex Lock**来实现的
>
> **方法级别**的 synchronized 不会在字节码指令中有所体现

```java
synchronized (this) {//--------monitorenter
	//critical section
}//----------------------------monitorexit
```

#### synchronized应用

> ==对象锁==
>
> In the Java virtual machine, **every object and class is logically associated with a ==monitor==.**
>
> 
>
> ==类锁==
>
> Class locks are actually implemented as object locks. As mentioned in earlier chapters, when the Java virtual machine loads a class file, it creates an instance of `class java.lang.Class.` When you lock a class, you are actually locking that class's Class object.



==应用于方法上==

```java
public synchronized void test2(String s) {//对象锁 默认为this对象
	...
}

public static synchronized void test3(String s) {//类锁 默认的锁就是当前所在的Class类
    /*Class locks are actually implemented as object locks. As mentioned in earlier chapters, when the Java virtual machine loads a class file, it creates an instance of class java.lang.Class. When you lock a class, you are actually locking that class's Class object. */
	...
}
```

==应用于代码块==

可以指定任意对象作为锁

```java
synchronized (this) {//对象锁
	...
}

synchronized (Person.class) {//类锁
    /*Class locks are actually implemented as object locks. As mentioned in earlier chapters, when the Java virtual machine loads a class file, it creates an instance of class java.lang.Class. When you lock a class, you are actually locking that class's Class object. */
	...
}
```

#### synchronized锁的升级

> Java SE 1.6里Synchronied同步锁，一共有四种状态：`无锁`、`偏向锁`、`轻量级锁`、`重量级锁`，它会**随着竞争**情况**逐渐升级**。锁可以升级但是**不可以降级**，
>
> 目的是为了**提高获取锁和释放锁的效率**。
>
> 可以通过-XX:-UseBiasedLocking=false来禁用偏向锁。
>
> 锁膨胀方向： 无锁 → 偏向锁 → 轻量级锁 → 重量级锁 (此过程是不可逆的)

| 锁       | 优点                                                         | 缺点                                                         | 使用场景                           |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| 偏向锁   | 加锁和解锁不需要CAS操作，没有额外的性能消耗，和执行非同步方法相比仅存在纳秒级的差距 | 如果线程间存在锁竞争，会带来额外的锁撤销的消耗               | 适用于只有一个线程访问同步块的场景 |
| 轻量级锁 | 竞争的线程不会阻塞，提高了响应速度                           | 如线程始终得不到锁竞争的线程，使用自旋会消耗CPU性能          | 追求响应时间，同步块执行速度非常快 |
| 重量级锁 | 线程竞争不适用自旋，不会消耗CPU                              | 线程阻塞，响应时间缓慢，在多线程下，频繁的获取释放锁，会带来巨大的性能消耗 | 追求吞吐量，同步块执行速度较长     |

##### 偏向锁

> 引入背景：在大多实际环境下，锁不仅不存在多线程竞争，而且总是由同一个线程多次获取，那么在同一个线程反复获取所释放锁中，其中并还没有锁的竞争，那么这样看上去，多次的获取锁和释放锁带来了很多不必要的性能开销和上下文切换。
>
> 
>
> **偏向锁**。当一个线程访问同步块并获取锁时，会在对象头和栈帧中的锁记录里存储锁偏向的线程ID，以后该线程在进入和退出同步块时不需要进行CAS操作来加锁和解锁。只需要简单的测试一下对象头的`Mark Word`里是否存储着指向当前线程的偏向锁。如果成功，表示线程已经获取到了锁；如果测试失败，则需要再测试一下Mark Word中偏向锁的标识是否设置成1（表示当前是偏向锁）：如果没有设置，则使用CAS竞争锁；如果设置了，则尝试使用CAS将对象头的偏向锁指向当前线程
>
> 
>
> 处于偏向锁的对象解锁后，线程 id 仍存储于对象头中
>
> 偏向是类偏向（整个类的对象可偏向或整个类的对象不可偏向）
>
> 
>
> **偏向锁的撤销**
>
>  偏向锁使用了一种等待竞争出现才会释放锁的机制。所以当其他线程尝试获取偏向锁时，持有偏向锁的线程才会释放锁。但是偏向锁的撤销需要等到全局安全点(就是当前线程没有正在执行的字节码)。它会首先暂停拥有偏向锁的线程，然后检查持有偏向锁的线程是否活着。如果线程不处于活动状态，直接将对象头设置为无锁状态。如果线程活着，JVM会遍历栈帧中的锁记录，栈帧中的锁记录和对象头要么偏向于其他线程，要么恢复到无锁状态或者标记对象不适合作为偏向锁。
>
> 
>
> 偏向锁是默认是延迟的，不会在程序启动时立即生效，如果想避免延迟，可以加 VM 参数 【-XX:BiasedLockingStartupDelay=0 】来禁用延迟
>
> 
>
> **几种会使偏向锁失效（撤销）的情况**
>
> - 调用对象 hashCode
> - -XX:-UseBiasedLocking
> - 当其他线程尝试获取偏向锁时；竞争出现
> - 调用wait/notify
>
> 
>
> **批量重偏向**
>
> 如果对象虽然被多个线程访问，但没有竞争，这时偏向了线程 T1 的对象仍有机会重新偏向 T2，重偏向会重置对象的 Thread ID当撤销偏向锁阈值超过 20 次后，jvm 会这样觉得，我是不是偏向错了呢，于是会在给这些对象加锁时重新偏向至加锁线程
>
> 
>
> **批量撤销**
>
> 当撤销偏向锁阈值超过 40 次后，jvm 会这样觉得，自己确实偏向错了，根本就不该偏向。于是**整个类的所有对象都会变为不可偏向的**，新建的对象也是不可偏向的
>
> 



![image-20230211204001023](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211204001023.png)

##### 轻量级锁

> 如果一个对象虽然有多线程要加锁，但加锁的时间是错开的（也就是没有竞争），那么可以使用轻量级锁来优化
>
> 
>
> **轻量级锁加锁**
>
> 在线程执行同步块之前，JVM会先在当前线程的栈帧中创建一个名为锁记录(`Lock Record`)的空间，用于存储锁对象目前的`Mark Word`的拷贝(JVM会将对象头中的`Mark Word`拷贝到锁记录中，官方称为`Displaced Mark Ward`)
>
> 创建锁记录（Lock Record）对象，每个线程的栈帧都会包含一个锁记录的结构，内部可以存储锁定对象的 Mark Word
> 让锁记录中 Object reference 指向锁对象，并尝试用 cas 替换 Object 的 Mark Word，将 Mark Word 的值存入锁记录
>
> - 成功：cas 替换成功，对象头中存储了锁记录地址和状态 00 ，表示由该线程给对象加锁
>
> - 失败:
>
>   ①自己执行了synchronized锁重入，添加一条Lock Record记录作为重入计数
>
>   ②其他线程已经持有了该对象Object的轻量级锁；表明存在竞争，锁进入膨胀状态（重量级锁）
>
>   ​	为Object对象申请Monitor锁，让Object（mark mord）指向重量级锁地址（monitor）；然后自己进入Monitor的Entry Set队列中阻塞
>
> **轻量级锁解锁**
>
> - 当退出 synchronized 代码块（解锁时）如果有取值为 null 的锁记录，表示有重入，这时重置锁记录，表示重入计数减一
>
> - 当退出 synchronized 代码块（解锁时）锁记录的值不为 null，这时使用 cas 将 Mark Word 的值恢复给对象头
>
>   ①解锁成功
>
>   ②轻量级锁进行了锁膨胀升级为重量级锁；进入重量级锁的解锁方式
>   	按照 Monitor 地址找到 Monitor 对象，设置 Owner 为 null，唤醒 EntryList 中 BLOCKED 线程

![image-20230211213238099](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211213238099.png)

![image-20230211213902673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211213902673.png)

![image-20230211214340673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211214340673.png)

![image-20230211214535858](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211214535858.png)

##### 自旋锁与自适应自旋锁

> ==自旋==
>
> 在**挂起线程和恢复线程的操作**都需要转入**内核态中完成**，这些操作对系统的并发性能带来了很大的压力**影响并发性**。同时HotSpot团队注意到在很多情况下，共享数据的锁定状态只会持续很短的一段时间，为了这段时间去挂起和回复阻塞线程并不值得。在如今多处理器环境下，完全可以让另一个没有获取到锁的线程在门外等待一会(自旋)，但不放弃CPU的执行时间。等待持有锁的线程是否很快就会释放锁。为了让线程等待，我们只需要让线程执行一个忙循环(自旋)
>
> - **自旋优势**
>   自旋锁本质上与阻塞并不相同，先不考虑其对多处理器的要求，如果锁占用的时间非常的短，那么自旋锁的性能会非常的好
>
> - **自旋弊端**
>   在线程自旋时，始终会占用CPU的时间片，如果锁占用的时间太长，那么自旋的线程会白白消耗掉CPU资源
>
> 自旋等待的时间必须要有一定的限度，如果自旋超过了限定的次数仍然没有成功获取到锁，就应该使用传统的方式去挂起线程了，在JDK定义中，自旋锁默认的自旋次数为10次，用户可以使用参数`-XX:PreBlockSpin`来更改
>
> ==自适应自旋==
>
> 在JDK 1.6中引入了自适应自旋锁。这就意味着**自旋的时间不再固定**了，而是**由前一次在同一个锁上的自旋 时间及锁的拥有者的状态来决定**的。如果在同一个锁对象上，自旋等待刚刚成功获取过锁，并且持有锁的线程正在运行中，那么JVM会认为该锁自旋获取到锁的可能性很大，会自动增加等待时间。比如增加到100此循环。相反，如果对于某个锁，自旋很少成功获取锁。那再以后要获取这个锁时将可能省略掉自旋过程，以避免浪费处理器资源。有了自适应自旋，JVM对程序的锁的状态预测会越来越准确，JVM也会越来越聪明

![image-20230211220538224](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230211220538224.png)

##### 重量级锁（锁膨胀）

> :lock:每个 Java 对象都可以关联一个 Monitor 对象，如果使用 synchronized 给对象上锁（重量级）之后，该对象头的Mark Word 中就被设置指向 Monitor 对象的指针
>
> - 刚开始 Monitor 中 Owner 为 null
> - （==上锁==）当 Thread-3 执行 synchronized(obj) 就会将 Monitor 的所有者 Owner 置为 Thread-3，Monitor中只能有一个 Owner
> - 在 Thread-3 上锁的过程中，如果 Thread-4，Thread-5，Thread-6 也来执行 synchronized(ObjectA)，就会进入 EntryList BLOCKED
> - （==解锁==）Thread-3 执行完同步代码块的内容会释放锁，将Owner置为null然后唤醒 EntryList 中等待的线程来竞争锁，竞争的时是非公平的
> - 图中 WaitSet 中的 Thread-1，Thread-2 是之前获得过锁，但条件不满足进入 WAITING 状态的线程

![image-20230210222837992](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230210222837992.png)

##### 锁消除（同步省略）

> 锁消除是指虚拟机即时编译器再运行时，对一些代码上要求同步，但是被检测到不可能存在共享数据竞争的锁进行消除。
>
> 锁消除的主要判定依据来源于==逃逸分析==的数据支持。意思就是：JVM会判断再一段程序中的同步明显不会逃逸出去从而被其他线程访问到，那JVM就把它们当作栈上数据对待，**认为这些数据是线程独有的，不需要加同步。此时就会进行锁消除**

### volatile 

> 如果一个字段被声明成volatile，Java线程内存模型确保所有线程看到这个变量的值是一致的。
>
> `volatile` 关键字可以**保证变量可见性**.
>
> 如果我们将变量声明为 **`volatile`** ，这就指示 JVM，这个变量是共享且不稳定的，**每次使用**它**都到主存中进行读取**
>
> 比synchronized的使用和执行成本更低，因为它不会引起线程上下文的切换和调度。
>
> 
>
> ==可见性==volatile **变量**的内存可见性是基于**内存屏障(Memory Barrier)**:又称内存栅栏，是一个 CPU 指令。
>
> - 对 volatile 变量的写指令后会加入写屏障
>   写屏障（sfence）保证在该屏障之前的，对共享变量的改动，都同步到主存当中
> - 对 volatile 变量的读指令前会加入读屏障
>   读屏障（lfence）保证在该屏障之后，对共享变量的读取，加载的是主存中最新数据
>
> ==有序性==volatile 有序性实现volatile 的 **happens-before 关系**
>
> - happens-before 规则中有一条是 volatile 变量规则：对一个 volatile 域的写，happens-before 于任意后续对这个 volatile 域的读。
> - volatile **禁止重排序**
>   写屏障会确保指令重排序时，不会将写屏障之前的代码排在写屏障之后
>   读屏障会确保指令重排序时，不会将读屏障之后的代码排在读屏障之前

### ThreadLocal

> ThreadLocal是一个将**在多线程中为每一个线程创建单独的变量副本的类**; 当使用ThreadLocal来维护变量时, ThreadLocal会为每个线程创建单独的变量副本, **做到线程隔离**，避免因多线程操作共享变量而导致的数据不一致的情况。**避免了出现线程安全问题**。
>
> 使用后记得调用ThreadLocal的(`remove(ThreadLocal<?> key)`)方法清除Entry即可**避免内存泄露**。
>
> 
>
> 如果你创建了⼀个ThreadLocal 变量，那么访问这个变量的每个线程都会有这个变量的本地副本。可以将ThreadLocal 类形象的⽐喻成存放数据的盒⼦，盒⼦中可以存储每个线程的私有数据。
>
> 看过代码之后就很清晰的知道了为什么ThreadLocal能够实现变量的多线程隔离了; 其实就是用了Map的数据结构给当前线程缓存了, 要使用的时候就从本线程的threadLocals对象中获取就可以了, key就是当前线程;
>
> ![image-20230510090357356](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230510090357356.png)
>
> 当然了在当前线程下获取当前线程里面的Map里面的对象并操作肯定没有线程并发问题了, 当然能做到变量的线程间隔离了;
>



**内部维护的是⼀个类似 Map 的==ThreadLocalMap== 数据结构**

> 本质上来讲, 它就是一个Map, 但是这个ThreadLocalMap与我们平时见到的Map有点不一样
>
> - 它没有实现Map接口;
> - 它没有public的方法, 最多有一个default的构造方法, 因为这个ThreadLocalMap的方法仅仅在ThreadLocal类中调用, 属于静态内部类
> - ThreadLocalMap的Entry实现继承了WeakReference<ThreadLocal<?>>
> - 该方法仅仅用了一个Entry数组来存储Key, Value; Entry并不是链表形式, 而是每个bucket里面仅仅放一个Entry;

![image-20230217100050423](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230217100050423.png)



> ThreadLocal 内部维护的是⼀个类似 Map 的ThreadLocalMap 数据结构（ThreadLocalMap是ThreadLocal的静态内部类），
> key 为当前对象的 Thread 对象（当前线程对象），值为 Object 对象。



> 最终的变量是放在了当前线程的 ThreadLocalMap 中（相当于当前线程维护了一个单独的变量副本，做到线程隔离），并不是存在 ThreadLocal 上，ThreadLocal 可以理解为只是ThreadLocalMap 的封装，传递了变量值。 

![image-20230217095849182](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230217095849182.png)

![image-20230217095515091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230217095515091.png)

#### ThreadLocal内存泄露

> **ThreadLocalMap使用ThreadLocal的弱引用作为key**
>
> 如果一个ThreadLocal没有外部强引用来引用它，那么系统 GC 的时候，这个ThreadLocal势必会被回收，**这样一来，ThreadLocalMap中就会出现key为null的Entry**，就没有办法访问这些key为null的Entry的value，**如果当前线程再迟迟不结束的话，这些key为null的Entry的value就会一直存在一条强引用链：Thread Ref -> Thread -> ThreaLocalMap -> Entry ->  value永远无法回收，造成内存泄漏。**
>
> - 使用static的ThreadLocal，延长了ThreadLocal的生命周期，可能导致的内存泄漏
>
> - 分配使用了ThreadLocal又不再调用get(),set(),remove()方法，那么就会导致内存泄漏
>
> 
>
> 对症下药，**每次使用完ThreadLocal调用`remove()`方法清理掉**就行了
>
> ### 为什么使用弱引用？
>
> 1. 如果使用强引用：我们知道，ThreadLocalMap的生命周期基本和Thread的生命周期一样，当前线程如果没有终止，那么ThreadLocalMap始终不会被GC回收，而ThreadLocalMap持有对ThreadLocal的强引用，那么ThreadLocal也不会被回收，当线程生命周期长，如果没有手动删除，则会造成kv累积，从而导致OOM
> 2. 如果使用弱引用：弱引用中的对象具有很短的声明周期，因为在系统GC时，只要发现弱引用，不管堆空间是否足够，都会将对象进行回收。而当ThreadLocal的强引用被回收时，ThreadLocalMap所持有的弱引用也会被回收，如果没有手动删除kv，那么会造成value累积，也会导致OOM
>
> 对比可知，使用**弱引用至少可以保证不会因为map的key累积从而导致OOM**，而**对应的value可以通过remove，get，set方法在下一次调用时被清除**。可见，内存泄露的根源不是弱引用，而是ThreadLocalMap的生命周期和Thread一样长，造成累积导致的

![image-20230414171941718](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230414171941718.png)

## JUC(Java Util Concurrency)

### AbstractQueuedSynchronizer

> AQS是一个用来构建锁和同步器的框架，使用AQS能简单且高效地构造出应用广泛的大量的同步器。
>
> ReentrantLock，Semaphore，ReentrantReadWriteLock，SynchronousQueue，FutureTask等等皆是基于AQS的.
>
> 
>
> Concurrent包是基于AQS (AbstractQueuedSynchronizer)框架的，AQS框架借助于两个类：
>
> - Unsafe（提供CAS操作）
> - LockSupport（提供park/unpark操作）

![image-20230424135301680](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424135301680.png)

#### **AQS核心思想**

> 如果被请求的共享资源空闲，则将当前请求资源的线程设置为有效的工作线程，并且将共享资源设置为锁定状态。
>
> 如果被请求的共享资源被占用，那么就需要一套线程阻塞等待以及被唤醒时锁分配的机制。
>
> 这个机制AQS是用CLH队列锁实现的，即将暂时获取不到锁的线程加入到队列中。

![image-20230424140729677](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424140729677.png)

![image-20230424140337398](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424140337398.png)

![image-20230801112058245](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230801112058245.png)

#### AQS结构

```java
// 头结点，你直接把它当做 当前持有锁的线程 可能是最好理解的
private transient volatile Node head;

// 阻塞的尾节点，每个新的节点进来，都插入到最后，也就形成了一个链表
private transient volatile Node tail;

// 这个是最重要的，代表当前锁的状态，0代表没有被占用，大于 0 代表有线程持有当前锁
// 这个值可以大于 1，是因为锁可以重入，每次重入都加上 1
private volatile int state;

// 代表当前持有独占锁的线程，举个最重要的使用例子，因为锁可以重入
// reentrantLock.lock()可以嵌套调用多次，所以每次用这个来判断当前线程是否已经拥有了锁
// if (currentThread == getExclusiveOwnerThread()) {state++}
private transient Thread exclusiveOwnerThread; //继承自AbstractOwnableSynchronizer
```

### Java 线程池

**池化技术的思想**主要是为了**减少每次获取资源的消耗**，**提高对资源的利用率**

- ==**降低资源消耗**==。通过重复利用已创建的线程降低线程创建和销毁造成的消耗。

- ==**提高响应速度**==。当任务到达时，任务可以不需要等到线程创建就能立即执行。

- ==**提高线程的可管理性**==。线程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以进行统一的分配，调优和监控。

### 线程池原理分析

![image-20230204232022514](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204232022514.png)

**线程池主要处理流程**

![image-20230204231928198](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204231928198.png)

```
1）如果当前运行的线程少于corePoolSize，则创建新线程来执行任务（注意，执行这一步骤
需要获取全局锁）。
2）如果运行的线程等于或多于corePoolSize，则将任务加入BlockingQueue。
3）如果无法将任务加入BlockingQueue（队列已满），则创建新的线程来处理任务（注意，执
行这一步骤需要获取全局锁）。
4）如果创建新线程将使当前运行的线程超出maximumPoolSize，任务将被拒绝，并调用
RejectedExecutionHandler.rejectedExecution()方法。
```

![image-20230204232431709](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204232431709.png)

```java
   // 存放线程池的运行状态 (runState) 和线程池内有效线程的数量 (workerCount)
   private final AtomicInteger ctl = new AtomicInteger(ctlOf(RUNNING, 0));

    private static int workerCountOf(int c) {
        return c & CAPACITY;
    }
    //任务队列
    private final BlockingQueue<Runnable> workQueue;

    public void execute(Runnable command) {
        // 如果任务为null，则抛出异常。
        if (command == null)
            throw new NullPointerException();
        // ctl 中保存的线程池当前的一些状态信息
        int c = ctl.get();

        //  下面会涉及到 3 步 操作
        // 1.首先判断当前线程池中执行的任务数量是否小于 corePoolSize
        // 如果小于的话，通过addWorker(command, true)新建一个线程，并将任务(command)添加到该线程中；然后，启动该线程从而执行任务。
        if (workerCountOf(c) < corePoolSize) {
            if (addWorker(command, true))
                return;
            c = ctl.get();
        }
        // 2.如果当前执行的任务数量大于等于 corePoolSize 的时候就会走到这里
        // 通过 isRunning 方法判断线程池状态，线程池处于 RUNNING 状态并且队列可以加入任务，该任务才会被加入进去
        if (isRunning(c) && workQueue.offer(command)) {
            int recheck = ctl.get();
            // 再次获取线程池状态，如果线程池状态不是 RUNNING 状态就需要从任务队列中移除任务，并尝试判断线程是否全部执行完毕。同时执行拒绝策略。
            if (!isRunning(recheck) && remove(command))
                reject(command);
                // 如果当前线程池为空就新创建一个线程并执行。
            else if (workerCountOf(recheck) == 0)
                addWorker(null, false);
        }
        //3. 通过addWorker(command, false)新建一个线程，并将任务(command)添加到该线程中；然后，启动该线程从而执行任务。
        //如果addWorker(command, false)执行失败，则通过reject()执行相应的拒绝策略的内容。
        else if (!addWorker(command, false))
            reject(command);
    }
```

### Executor 框架

`Executor` 框架是 Java5 之后引进的，在 Java 5 之后，通过 `Executor` 来启动线程比使用 `Thread` 的 `start` 方法更好，除了更易管理，效率更好（用线程池实现，节约开销）外，还有关键的一点：有助于避免 this 逃逸问题。

> 补充：this 逃逸是指在构造函数返回之前其他线程就持有该对象的引用. 调用尚未构造完全的对象的方法可能引发令人疑惑的错误。

`Executor` 框架不仅包括了线程池的管理，还提供了线程工厂、队列以及拒绝策略等，`Executor` 框架让并发编程变得更加简单。

#### Executor 框架结构(三大部分组成)

![image-20230205000128358](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230205000128358.png)

- 任务(`Runnable` /`Callable`)
- 任务的执行(`Executor`)
- 异步计算的结果(`Future`)

1. **主线程首先要创建实现 `Runnable` 或者 `Callable` 接口的任务对象。**
2. **把创建完成的实现 `Runnable`/`Callable`接口的 对象直接交给 `ExecutorService` 执行**: `ExecutorService.execute（Runnable command）`）或者也可以把 `Runnable` 对象或`Callable` 对象提交给 `ExecutorService` 执行（`ExecutorService.submit（Runnable task）`或 `ExecutorService.submit（Callable <T> task）`）。
3. **如果执行 `ExecutorService.submit（…）`，`ExecutorService` 将返回一个实现`Future`接口的对象**（我们刚刚也提到过了执行 `execute()`方法和 `submit()`方法的区别，`submit()`会返回一个 `FutureTask 对象）。由于 FutureTask` 实现了 `Runnable`，我们也可以创建 `FutureTask`，然后直接交给 `ExecutorService` 执行。
4. **最后，主线程可以执行 `FutureTask.get()`方法来等待任务执行完成。主线程也可以执行 `FutureTask.cancel（boolean mayInterruptIfRunning）`来取消此任务的执行。**

##### 任务(`Runnable` /`Callable`)

执行任务需要实现的 **`Runnable` 接口** 或 **`Callable`接口**。**`Runnable` 接口**或 **`Callable` 接口** 实现类都可以被 **`ThreadPoolExecutor`** 或 **`ScheduledThreadPoolExecutor`** 执行。

##### 任务的执行(`Executor`)

任务执行机制的核心接口 **`Executor`** ，以及继承自 `Executor` 接口的 **`ExecutorService` 接口。**

**`ThreadPoolExecutor`** 和 

**`ScheduledThreadPoolExecutor`** 

这两个关键类实现了 **ExecutorService 接口**。

![image-20230205000754985](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230205000754985.png)

##### 异步计算的结果(`Future`)

**`Future`** 接口以及 `Future` 接口的实现类 **`FutureTask`** 类都可以代表异步计算的结果。

当我们把 **`Runnable`接口** 或 **`Callable` 接口** 的实现类提交给 **`ThreadPoolExecutor`** 或 **`ScheduledThreadPoolExecutor`** 执行。（调用 `submit()` 方法时会返回一个 **`FutureTask`** 对象）

#### Executors工具类

> 使用线程池的好处是减少在创建和销毁线程上所消耗的时间以及系统资源开销，解决资源不足的问题。如果不使用线程池，有可能会造成系统创建大量同类线程而导致消耗完内存或者“过度切换”的问题。

另外，《阿里巴巴 Java 开发手册》中**强制**线程池**不允许使用** `Executors` 去创建，而是通过 `ThreadPoolExecutor` 构造函数的方式，这样的处理方式让写的同学更加明确线程池的运行规则，规避资源耗尽的风险



**通过 `Executor` 框架的工具类 `Executors` 来实现** 我们可以创建三种类型的 `ThreadPoolExecutor`：

- `FixedThreadPool`
- `SingleThreadExecutor`
- `CachedThreadPool`

### ThreadPoolExecutor★

> **线程池实现类 `ThreadPoolExecutor` 是 `Executor` 框架最核心的类**
>
> **推荐使用 `ThreadPoolExecutor` 构造函数创建线程池**
>
> 
>
> Parameters：
>
> - **int corePoolSize,//核心线程数**
> - **int maximumPoolSize,//线程池中最大线程数**
> - **long keepAliveTime,//线程池中非核心空闲线程的存活时间**
> - TimeUnit unit,//存活时间单位
> - BlockingQueue workQueue,//阻塞队列
> - ThreadFactory threadFactory,//线程工厂
> - RejectedExecutionHandler handler//拒接策略



**`ThreadPoolExecutor` 3 个最重要的参数：**

- **`corePoolSize`** : 核心线程数线程数定义了最小可以同时运行的线程数量。

- **`maximumPoolSize` :** 当队列中存放的任务达到队列容量的时候，当前可以同时运行的线程数量变为最大线程数。

- **`workQueue`:** 当新任务来的时候会先判断当前运行的线程数量是否达到核心线程数，如果达到的话，新任务就会被存放在队列中。**阻塞队列**
  
  - `ArrayBlockingQueue`：是一个基于数组结构的**有界**阻塞队列，此队列按FIFO（先进先出）原则对元素进行排序
  - `LinkedBlockingQueue`：一个基于链表结构的**默认无界**的（可选有界）阻塞队列，此队列按FIFO排序元素，**吞吐量通常要高于ArrayBlockingQueue**。静态工厂方法Executors.newFixedThreadPool()使用了这个队列。
  - `SynchronousQueue`：一个不存储元素的阻塞队列。每个插入操作必须等到另一个线程调用移除操作，否则插入操作一直处于阻塞状态，**吞吐量通常要高于Linked-BlockingQueue**，静态工厂方法Executors.newCachedThreadPool使用了这个队列。
  - `PriorityBlockingQueue`：一个具**有优先级的无限阻塞队列**。
  
  > 在Java线程池中，不同的阻塞队列有不同的使用场景。例如，
  >
  > - ArrayBlockingQueue适用于任务量比较小的情况，
  > - 而LinkedBlockingQueue适用于任务量比较大的情况，因为它可以自动扩容。
  > - SynchronousQueue适用于生产者和消费者速度相同的情况，
  > - 而PriorityBlockingQueue则适用于需要对任务进行优先级排序的情况。

`ThreadPoolExecutor`其他常见参数 :

1. **`keepAliveTime`**:当线程池中的线程数量大于 `corePoolSize` 的时候，如果这时没有新的任务提交，线程池中且核心线程外的线程不会立即销毁，而是会等待，直到等待的时间超过了 `keepAliveTime`才会被回收销毁；(**线程池中且核心线程外的线程空闲后，保持存活的时间**)

2. **`unit`** : `keepAliveTime` 参数的时间单位。

3. **`threadFactory`** :executor 创建新线程的时候会用到。

4. **`handler`** :饱和(拒绝)策略。关于饱和策略下面单独介绍一下。**`ThreadPoolExecutor` 饱和策略定义:**

   如果当前同时运行的线程数量达到最大线程数量并且队列也已经被放满了任务时，`ThreadPoolTaskExecutor` 定义一些策略:

   - `ThreadPoolExecutor.AbortPolicy` ：抛出 `RejectedExecutionException`来拒绝新任务的处理。(**抛异常**)
   - `ThreadPoolExecutor.CallerRunsPolicy` ：**用调用者所在线程来运行任务(直接执行run方法不启动新线程)**;调用执行自己的线程运行任务，也就是直接在调用`execute`方法的线程中运行(`run`)被拒绝的任务，如果执行程序已关闭，则会丢弃该任务。因此这种策略会降低对于新任务提交速度，影响程序的整体性能。如果您的应用程序可以承受此延迟并且你要求任何一个任务请求都要被执行的话，你可以选择这个策略。
   - `ThreadPoolExecutor.DiscardPolicy` ：不处理新任务，直接丢弃掉。(**丢弃新任务**)
   - `ThreadPoolExecutor.DiscardOldestPolicy` ： 此策略将丢弃最早的未处理的任务请求。（**丢弃老任务**）

```java
/**
     * 用给定的初始参数创建一个新的ThreadPoolExecutor。
     */
    public ThreadPoolExecutor(int corePoolSize,//线程池的核心线程数量
                              int maximumPoolSize,//线程池的最大线程数
                              long keepAliveTime,//当线程数大于核心线程数时，多余的空闲线程存活的最长时间
                              TimeUnit unit,//时间单位
                              BlockingQueue<Runnable> workQueue,//任务队列，用来储存等待执行任务的队列
                              ThreadFactory threadFactory,//线程工厂，用来创建线程，一般默认即可
                              RejectedExecutionHandler handler//拒绝策略，当提交的任务过多而不能及时处理时，我们可以定制策略来处理任务
                               ) {
        if (corePoolSize < 0 ||
            maximumPoolSize <= 0 ||
            maximumPoolSize < corePoolSize ||
            keepAliveTime < 0)
            throw new IllegalArgumentException();
        if (workQueue == null || threadFactory == null || handler == null)
            throw new NullPointerException();
        this.corePoolSize = corePoolSize;
        this.maximumPoolSize = maximumPoolSize;
        this.workQueue = workQueue;
        this.keepAliveTime = unit.toNanos(keepAliveTime);
        this.threadFactory = threadFactory;
        this.handler = handler;
    }
```

![image-20230204232022514](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204232022514.png)

#### 创建线程池

##### **方式一：通过`ThreadPoolExecutor`构造函数实现（推荐）**

```java
/**
 @author EddieZhang
 @create 2023-02-05 12:36 AM
 */
public class ThreadPoolExecutorTest {
    private static final int CORE_POOL_SIZE = 5;//核心线程数
    private static final int MAX_POOL_SIZE = 10;//线程池中最大线程数
    private static final int QUEUE_CAPACITY = 100;//阻塞队列的最大容量
    private static final Long KEEP_ALIVE_TIME = 1L;//线程池中非核心空闲线程的存活时间
    public static void main(String[] args) {
        /**
         * (
         *  int corePoolSize,//核心线程数
         *  int maximumPoolSize,//线程池中最大线程数
         *  long keepAliveTime,//线程池中非核心空闲线程的存活时间
         *  TimeUnit unit,//存活时间单位
         *  BlockingQueue<Runnable> workQueue,//阻塞队列
         *  ThreadFactory threadFactory,//线程工厂
         *  RejectedExecutionHandler handler//拒接策略
         *  )
         */
        //通过ThreadPoolExecutor构造函数自定义参数创建
        ThreadPoolExecutor threadPoolExecutor;
        threadPoolExecutor = new ThreadPoolExecutor(
                CORE_POOL_SIZE,
                MAX_POOL_SIZE,
                5,
                TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(QUEUE_CAPACITY),
                new ThreadPoolExecutor.CallerRunsPolicy());
        for (int i = 0; i < 10; i++) {
            Runnable thread = new Thread(() -> {
                System.out.println("这里是通过实现Runnable接口启动的新线程:" + Thread.currentThread().getName());
            });
            threadPoolExecutor.execute(thread);
        }
        //关闭线程池
        threadPoolExecutor.shutdown();
        //未将线程池关闭则死循环直至线程池关闭成功
        while (!threadPoolExecutor.isTerminated()) {
        }
        System.out.println("Finished all threads");
    }
}
```

##### **方式二：通过 `Executor` 框架的工具类 `Executors` 来实现** 我们可以创建三种类型的 `ThreadPoolExecutor`（**不推荐**；存在资源耗尽的风险）

#### 向线程池中提交任务

可以使用两个方法向线程池提交任务，分别为`execute()`和`submit()`方法。



`execute()`方法**用于提交不需要返回值的任务**，所以**无法判断任务是否被线程池执行成功**。

```java
public void execute(Runnable command) {
        if (command == null)
            throw new NullPointerException();
}
```



`submit()`方法用于**提交需要返回值的任务**。线程池**会返回一个`future`类型的对象**，通过这个future对象可以判断任务是否执行成功，并且**可以通过future的get()方法来获取返回值**，**`get()`方法会阻塞当前线程直到任务完成**，而使用get（long timeout，TimeUnit unit）方法则会阻塞当前线程一段时间后立即返回，这时候有可能任务没有执行完。

```java
Future<?> submit(Runnable task);
```

#### 关闭线程池

可以通过调用线程池的`shutdown()`或`shutdownNow()`方法来关闭线程池

- **`shutdown（）`** :关闭线程池，线程池的状态变为 `SHUTDOWN`。线程池不再接受新任务了，但是队列里的任务得执行完毕。

- **`shutdownNow（）`** :关闭线程池，线程的状态变为 `STOP`。线程池会终止当前正在运行的任务，并停止处理排队的任务并返回正在等待执行的 List。

```java
public List<Runnable> shutdownNow() {...}//线程池会终止当前正在运行的任务，并停止处理排队的任务并返回正在等待执行的 List。

public void shutdown() {...}//线程池不再接受新任务了，但是队列里的任务得执行完毕。
```

它们的**原理**是**遍历线程池中的工作线程**，然后**逐个调用线程的interrupt方法来中断线程**，所以**无法响应中断的任务可能永远无法终止**。

只要调用了这两个关闭方法中的任意一个，`isShutdown()`方法就会**返回true**。

当**所有的任务都已关闭后**，才表示**线程池关闭成功**，这时调用`isTerminaed()`方法会**返回true**。

```java
		//关闭线程池
        threadPoolExecutor.shutdown();
        //未将线程池关闭则死循环直至线程池关闭成功
        while (!threadPoolExecutor.isTerminated()) {
        }
        System.out.println("Finished all threads");
```

#### 几种常见的线程池

##### FixedThreadPool

`FixedThreadPool` 被称为**可重用固定线程数**的线程池。



源码可以看出新创建的 `FixedThreadPool` 的 `corePoolSize` 和 `maximumPoolSize` 都被设置为 **nThreads**，这个 nThreads 参数是我们使用的时候自己传递的。

```java
	/**
     * 创建一个可重用固定数量线程的线程池
     */
    public static ExecutorService newFixedThreadPool(int nThreads, ThreadFactory threadFactory) {
        return new ThreadPoolExecutor(nThreads, nThreads,
                                      0L, TimeUnit.MILLISECONDS,
                                      new LinkedBlockingQueue<Runnable>(),
                                      threadFactory);
    }
```

- 如果当前运行的线程数小于 corePoolSize， 如果再来新任务的话，就创建新的线程来执行任务；

- 当前运行的线程数等于 corePoolSize 后， 如果再来新任务的话，会将任务加入 `LinkedBlockingQueue`；

- 线程池中的线程执行完 手头的任务后，会在循环中反复从 `LinkedBlockingQueue` 中获取任务来执行；



![image-20230205144649029](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230205144649029.png)



**为什么不推荐使用`FixedThreadPool`？**



**`FixedThreadPool` 使用无界队列 `LinkedBlockingQueue`（队列的容量为 Integer.MAX_VALUE）作为线程池的工作队列会对线程池带来如下影响 ：**

1. 当线程池中的线程数达到 `corePoolSize` 后，新任务将在无界队列中等待，因此线程池中的线程数不会超过 corePoolSize；
2. 由于使用无界队列时 `maximumPoolSize` 将是一个无效参数，因为不可能存在任务队列满的情况。所以，通过创建 `FixedThreadPool`的源码可以看出创建的 `FixedThreadPool` 的 `corePoolSize` 和 `maximumPoolSize` 被设置为同一个值。
3. 由于 1 和 2，使用无界队列时 `keepAliveTime` 将是一个无效参数；
4. 运行中的 `FixedThreadPool`（未执行 `shutdown()`或 `shutdownNow()`）不会拒绝任务，在任务比较多的时候**会导致 OOM（内存溢出）**。

##### SingleThreadExecutor 

`SingleThreadExecutor` 是**只有一个线程的线程池**

源代码可以看出新创建的 `SingleThreadExecutor` 的 `corePoolSize` 和 `maximumPoolSize` **都被设置为 1**.其他参数和 `FixedThreadPool` 相同

```java
	/**
     *返回只有一个线程的线程池
     */
    public static ExecutorService newSingleThreadExecutor(ThreadFactory threadFactory) {
        return new FinalizableDelegatedExecutorService
            (new ThreadPoolExecutor(1, 1,
                                    0L, TimeUnit.MILLISECONDS,
                                    new LinkedBlockingQueue<Runnable>(),
                                    threadFactory));
    }
```

- 如果当前运行的线程数少于 `corePoolSize`，则创建一个新的线程执行任务；

- 当前线程池中有一个运行的线程后，将任务加入 `LinkedBlockingQueue`

- 线程执行完当前的任务后，会在循环中反复从`LinkedBlockingQueue` 中获取任务来执行



![image-20230205144906373](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230205144906373.png)

**为什么不推荐使用`SingleThreadExecutor`？**



`SingleThreadExecutor` **使用无界队列** `LinkedBlockingQueue` 作为线程池的工作队列（队列的容量为 Intger.MAX_VALUE）。`SingleThreadExecutor` 使用无界队列作为线程池的工作队列会对线程池带来的影响与 `FixedThreadPool` 相同。说简单点就是**可能会导致 OOM**，



##### CachedThreadPool

 `CachedThreadPool` 是一个会根**据需要创建新线程**的线程池



`CachedThreadPool` 的`corePoolSize` 被设置为空（0），`maximumPoolSize`被设置为 `Integer.MAX.VALUE`，即**最大线程数是无界**的，这也就意味着如果主线程提交任务的速度高于 `maximumPool` 中线程处理任务的速度时，`CachedThreadPool` 会不断创建新的线程。极端情况下，这样会导致耗尽 cpu 和内存资源



```java
	/**
     * 创建一个线程池，根据需要创建新线程，但会在先前构建的线程可用时重用它。
     */
    public static ExecutorService newCachedThreadPool(ThreadFactory threadFactory) {
        return new ThreadPoolExecutor(0, Integer.MAX_VALUE,
                                      60L, TimeUnit.SECONDS,
                                      new SynchronousQueue<Runnable>(),
                                      threadFactory);
    }
```

1. 首先执行 `SynchronousQueue.offer(Runnable task)` 提交任务到任务队列。如果当前 `maximumPool` 中有闲线程正在执行 `SynchronousQueue.poll(keepAliveTime,TimeUnit.NANOSECONDS)`，那么主线程执行 offer 操作与空闲线程执行的 `poll` 操作配对成功，主线程把任务交给空闲线程执行，`execute()`方法执行完成，否则执行下面的步骤 2；
2. 当初始 `maximumPool` 为空，或者 `maximumPool` 中没有空闲线程时，将没有线程执行 `SynchronousQueue.poll(keepAliveTime,TimeUnit.NANOSECONDS)`。这种情况下，步骤 1 将失败，此时 `CachedThreadPool` 会创建新线程执行任务，execute 方法执行完成；

![image-20230205145227932](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230205145227932.png)

 **为什么不推荐使用`CachedThreadPool`？**



`CachedThreadPool`允许创建的线程数量为 `Integer.MAX_VALUE` ，**可能会创建大量线程**，从而**导致 OOM**



##### ScheduledThreadPoolExecutor

**`ScheduledThreadPoolExecutor` 主要用来在给定的延迟后运行任务，或者定期执行任务。** 这个在实际项目中基本不会被用到，**也不推荐使用**，大家只需要简单了解一下它的思想即可



#### 合理地配置线程池

要想合理地配置线程池，就必须首先分析任务特性，可以从以下几个角度来分析。

- 任务的性质：**CPU密集型任务**、**IO密集型任务**和混合型任务。
- 任务的优先级：高、中和低。
- 任务的执行时间：长、中和短。
- 任务的依赖性：是否依赖其他系统资源，如数据库连接。



有一个简单并且适用面比较广的**经验之谈**：

- **CPU 密集型任务(N+1)：** 这种任务消耗的主要是 CPU 资源，可以将线程数设置为 N（CPU 核心数）+1，比 CPU 核心数多出来的一个线程是为了防止线程偶发的缺页中断，或者其它原因导致的任务暂停而带来的影响。一旦任务暂停，CPU 就会处于空闲状态，而在这种情况下多出来的一个线程就可以充分利用 CPU 的空闲时间。
- **I/O 密集型任务(2N)：** 这种任务应用起来，系统会用大部分的时间来处理 I/O 交互，而线程在处理 I/O 的时间段内不会占用 CPU 来处理，这时就可以将 CPU 交出给其它线程使用。因此在 I/O 密集型任务的应用中，我们可以多配置一些线程，具体的计算方法是 2N。

**如何判断是 CPU 密集任务还是 IO 密集任务？**

CPU 密集型简单理解就是利用 CPU 计算能力的任务比如你在内存中对大量数据进行排序。但凡涉及到网络读取，文件读取这类都是 IO 密集型，这类任务的特点是 CPU 计算耗费时间相比于等待 IO 操作完成的时间来说很少，大部分时间都花在了等待 IO 操作完成上。

#### 线程池的监控

监控线程池的时候可以使用以下属性。



- `taskCount`：线程池需要执行的任务数量。
- `completedTaskCount`：线程池在运行过程中已完成的任务数量，小于或等于taskCount。
- `largestPoolSize`：线程池里曾经创建过的最大线程数量。通过这个数据可以知道线程池是否曾经满过。如该数值等于线程池的最大大小，则表示线程池曾经满过。
- `getPoolSize`：线程池的线程数量。如果线程池不销毁的话，线程池里的线程不会自动销毁，所以这个大小只增不减。
- `getActiveCount`：获取活动的线程数。



通过扩展线程池进行监控。可以通过**继承线程池来自定义线程池**，**重写线程池**的`beforeExecute`、`afterExecute`和`terminated`方法，也可以在任务执行前、执行后和线程池关闭前执行一些代码来进行监控。例如，监控任务的平均执行时间、最大执行时间和最小执行时间等。这几个方法在线程池里是空方法。



### CompletableFuture异步编程

 Java 8 才被引入的一个非常有用的用于**异步编程的类**

```java
public class CompletableFuture<T> implements Future<T>, CompletionStage<T> {...}
```

**Future接口**

![image-20230204223419774](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204223419774.png)

- boolean `cancel(boolean mayInterruptIfRunning)` ：尝试取消执行任务。

- boolean `isCancelled()` ：判断任务是否被取消。

- boolean `isDone()` ： 判断任务是否已经被执行完成。

- `get()` ：等待任务执行完成并获取运算结果。会阻塞主线程

- `get(long timeout, TimeUnit unit)` ：多了一个超时时间。

**CompletionStage接口**

![image-20230204223644600](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204223644600.png)

`CompletionStage<T>` 接口中的方法比较多，`CompletableFuture` 的函数式能力就是这个接口赋予的。

**大量使用了 Java8 引入的函数式编程**



#### 创建 CompletableFuture

##### **一，通过 new 关键字。**

通过 new 关键字创建 `CompletableFuture` 对象这种使用方式可以看作是将 `CompletableFuture` 当做 `Future` 来使用。



```java
CompletableFuture completableFuture = new CompletableFuture();
```

##### **二，** 静态工厂方法

**基于 `CompletableFuture` 自带的静态工厂方法：`runAsync()` 、`supplyAsync()` 。**

###### `runAsync()` 无返回结果

```java
public static CompletableFuture<Void> runAsync(Runnable runnable,
                                                   Executor executor) {
    return asyncRunStage(screenExecutor(executor), runnable);
}
```

```java
	public static ExecutorService threadPool = Executors.newFixedThreadPool(20);//指定线程池

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        CompletableFuture.runAsync(()->{
            System.out.println("这里是通过CompletableFuture的静态方法runAsync启动的线程:" + Thread.currentThread().getName());
        },threadPool);
        
        threadPool.shutdown();
        while (!threadPool.isTerminated()){}//循环等待直到线程池关闭完成
        System.out.println("Finished all threads");
    }
```

###### `supplyAsync()` 有返回结果

```java
public static <U> CompletableFuture<U> supplyAsync(Supplier<U> supplier,
                                                       Executor executor) {
     return asyncSupplyStage(screenExecutor(executor), supplier);
}

public interface Supplier<T> {//有返回值的

    /**
     * Gets a result.
     *
     * @return a result
     */
    T get();
}
```

```java
public static ExecutorService threadPool = Executors.newFixedThreadPool(20);//指定线程池
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        CompletableFuture<String> supplyAsync = CompletableFuture.supplyAsync(() -> {
            return "Hello World";//有返回值
        }, threadPool);

        String result = supplyAsync.get();//获取线程执行后的返回值

        CompletableFuture.runAsync(()->{
            System.out.println(result);
        },threadPool);

        threadPool.shutdown();
        while (!threadPool.isTerminated()){}//循环等待指导线程池关闭完成
        System.out.println("Finished all threads");
    }
```

#### 处理异步结算的结果

- `thenApply()`进一步处理异步完成后的结果并返回处理结果
- `thenAccept()`进一步处理异步完成后的结果 无返回结果
- `thenRun()`进一步操作 无法获取异步完成后的结果 无返回结果
- `whenComplete()`进一步处理异步完成后的结果
  无法处理结果数据能够感知异常（`exceptionally()`可以感知到异常并对异常进行处理【当出现异常设置默认返回值】）并返回处理结果

```java
- `thenApply()`进一步处理异步完成后的结果并返回处理结果
- `thenAccept()`进一步处理异步完成后的结果 无返回结果
- `thenRun()`进一步操作 无法获取异步完成后的结果 无返回结果
    
public static ExecutorService threadPool = Executors.newFixedThreadPool(20);//指定线程池
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        CompletableFuture<String> supplyAsync = CompletableFuture.supplyAsync(() -> {
            return "Hello ";
        }, threadPool);
        supplyAsync.thenApply((result)->{return result + "World";})//进一步处理异步完成后的结果并返回处理结果
                .thenApply((result)->{return result + "--Eddie";})//进一步处理异步完成后的结果并返回处理结果
                
                .thenAccept(System.out::println)//进一步处理异步完成后的结果 无返回结果
                
                .thenRun(()->{//进一步操作 无法获取异步完成后的结果 无返回结果
                    System.out.println("我感知不到异步任务执行的任何结果");
                });

        threadPool.shutdown();
        while (!threadPool.isTerminated()){}//循环等待直到线程池关闭完成
        System.out.println("Finished all threads");
    }
```

```java
- `whenComplete()`进一步处理异步完成后的结果
无法处理结果数据能够感知异常（`exceptionally()`可以感知到异常并对异常进行处理【当出现异常设置默认返回值】）并返回处理结果
    
public static ExecutorService threadPool = Executors.newFixedThreadPool(20);//指定线程池
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        CompletableFuture<String> supplyAsync = CompletableFuture.supplyAsync(() -> {
            int num = 10 / 0;//模拟出现异常
            return "Hello ";
        }, threadPool);
        supplyAsync.whenComplete((result,exception)->{//当异步任务完成后
            System.out.println("上一步异步执行的结果是:" + result + "\t" + "上异步出现的异常是" + exception);
            //上一步异步执行的结果是:null	上异步出现的异常是java.util.concurrent.CompletionException: java.lang.ArithmeticException: / by zero
        }).exceptionally(throwable -> {//若异步任务完成时出现了异常
            System.out.println("出现的异常是" + throwable);
            //出现的异常是java.util.concurrent.CompletionException: java.lang.ArithmeticException: / by zero
            return "如果出现异常的话 这里返回一个默认值";
        }).thenAccept((result)->{
            System.out.println(result);//如果出现异常的话 这里返回一个默认值
        });

        threadPool.shutdown();
        while (!threadPool.isTerminated()){}//循环等待指导线程池关闭完成
        System.out.println("Finished all threads");
    }
```

#### 异步线程串行化

- `thenRunAsync`启动一个新的异步线程 串行上一个异步线程 无感知上个线程的结果 无返回结果
- `thenAcceptAsync`启动一个新的异步线程 串行并处理上个异步线程完成后的结果 无返回结果
- `thenApplyAsync`启动一个新的异步线程 串行并处理上个异步线程完成后的结果并返回处理结果

```java
一：`thenApplyAsync()`启动一个新的异步线程 串行并处理上个异步线程完成后的结果并返回处理结果
public <U> CompletionStage<U> thenApplyAsync
        (Function<? super T,? extends U> fn,
         Executor executor);
         
二：`thenAcceptAsync()`启动一个新的异步线程 串行并处理上个异步线程完成后的结果 无返回结果
public CompletionStage<Void> thenAcceptAsync(Consumer<? super T> action,
                                                 Executor executor);
    
三：`thenRunAsync()`启动一个新的异步线程 串行上一个异步线程 无感知上个线程的结果 无返回结果
public CompletionStage<Void> thenRunAsync(Runnable action,
                                              Executor executor);                                                 
```

#### 异常处理

- `handle()`处理任务执行过程中可能出现的抛出异常的情况
- `exceptionally()`可以感知到异常并对异常进行处理【当出现异常设置默认返回值】）并返回处理结果
- `completeExceptionally()`让结果就是异常

```java
一：`handle()`处理任务执行过程中可能出现的抛出异常的情况
    可以感知到异常并对异常进行处理【当出现异常设置默认返回值】）并返回处理结果
    
CompletableFuture<String> future
        = CompletableFuture.supplyAsync(() -> {
    if (true) {
        throw new RuntimeException("Computation error!");
    }
    return "hello!";
}).handle((res, ex) -> {
    // res 代表返回的结果
    // ex 的类型为 Throwable ，代表抛出的异常
    return res != null ? res : "world!";//若未出现异常则 返回正常返回结果 反之指定异常后返回的默认值
});

二：`exceptionally()`可以感知到异常并对异常进行处理【当出现异常设置默认返回值】）并返回处理结果
    
CompletableFuture<String> supplyAsync = CompletableFuture.supplyAsync(() -> {
            int num = 10 / 0;//模拟出现异常
            return "Hello ";
        }, threadPool);
        supplyAsync.whenComplete((result,exception)->{//当异步任务完成后
            System.out.println("上一步异步执行的结果是:" + result + "\t" + "上异步出现的异常是" + exception);
            //上一步异步执行的结果是:null	上异步出现的异常是java.util.concurrent.CompletionException: java.lang.ArithmeticException: / by zero
        }).exceptionally(throwable -> {//若异步任务完成时出现了异常
            System.out.println("出现的异常是" + throwable);
            //出现的异常是java.util.concurrent.CompletionException: java.lang.ArithmeticException: / by zero
            return "如果出现异常的话 这里返回一个默认值";
        }).thenAccept((result)->{
            System.out.println(result);//如果出现异常的话 这里返回一个默认值
        });

三：`completeExceptionally()`让结果就是异常
    
CompletableFuture<String> completableFuture = new CompletableFuture<>();
// ...
completableFuture.completeExceptionally(
  new RuntimeException("Calculation failed!"));
// ...
completableFuture.get(); // ExecutionException

```

#### 组合两个CompletableFuture

- `thenComposeAsync`**按顺序链接**两个 `CompletableFuture` 对象;**将前一个任务的返回结果作为下一个任务的参数**，它们之间存在着先后顺序
- `thenCombineAsync`会**在两个任务都执行完成后**，把**两个任务的结果处理后返回一个结果**。两个任务是并行执行的，它们之间并**没有先后依赖顺序**

**两个都完成**

- `runAfterBothAsync`两个异步线程都执行完后进行一些操作处理 **无法感知**两个线程的**执行结果** **无返回值**
- `thenAcceptBothAsync`两个异步线程都执行完后进行一些操作处理 **能够感知**两个线程的**执行结果** **无返回值**

**任一完成**

- `applyToEitherAsync`任意一个异步线程执行完成后进行一些操作处理 **能够感知**两个线程的**执行结果** **返回一个结果**
- `acceptEitherAsync`任意一个异步线程执行完成后进行一些操作处理 **能够感知**两个线程的**执行结果** **无返回值**
- `runAfterEitherAsync`任意一个异步线程执行完成后进行一些操作处理 **无法感知**两个线程的**执行结果** **无返回值**

#### 并行运行多个 CompletableFuture

可以通过 `CompletableFuture` 的 `allOf()`/`anyOf()`静态方法来并行运行多个 `CompletableFuture`

- `allOf()`**等到所有的 `CompletableFuture` 都运行完成之后再返回**
- 若线程A和B调用 `join()` 可以让程序等A和B线程 都运行完了之后再继续执行
- `anyOf()`**不会等待所有的 `CompletableFuture` 都运行完成之后再返回，只要有一个执行完成即可！**

```java
- 调用 `allOf()`**等到所有的 `CompletableFuture` 都运行完成之后再返回**
CompletableFuture<Void> task1 =
  CompletableFuture.supplyAsync(()->{
    //自定义业务操作
  });
......
CompletableFuture<Void> task6 =
  CompletableFuture.supplyAsync(()->{
    //自定义业务操作
  });
......
 CompletableFuture<Void> headerFuture=CompletableFuture.allOf(task1,.....,task6);//指定多个异步线程

  try {
    headerFuture.join();
  } catch (Exception ex) {
    ......
  }
System.out.println("all done. ");

- 调用 `join()` 可以让程序等`future1` 和 `future2` 都运行完了之后再继续执行
    
CompletableFuture<Void> completableFuture = CompletableFuture.allOf(future1, future2);
completableFuture.join();
assertTrue(completableFuture.isDone());
System.out.println("all futures done...");

- 调用 `anyOf()`**不会等待所有的 `CompletableFuture` 都运行完成之后再返回，只要有一个执行完成即可！**
CompletableFuture<Object> f = CompletableFuture.anyOf(future1, future2);
System.out.println(f.get());
```



