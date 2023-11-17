# Operating System

![image-20230331111243020](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331111243020.png)

![image-20230402212614984](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230402212614984.png)

## Definition & Function

### Definition

> ### :happy:Definition:
>
> An operating system is a software which performs all the basic tasks  like `file management`, `memory management`, `process management`, `handling  input and output`, and `controlling peripheral devices` such as disk drives and printers.
>
> An operating system (OS) is the program that, after being initially loaded into the computer by a boot program, manages all of the other application programs in a computer. The application programs make use of the operating system by making requests for services through a defined application program interface (API). In addition, users can interact directly with the operating system through a user interface, such as a command-line interface (CLI) or a graphical UI (GUI).
>
> - **操作系统（Operating System，简称 OS）是管理计算机硬件与软件资源的程序，是计算机的基石。**
>
> - **操作系统本质上是一个运行在计算机上的软件程序 ，用于管理计算机硬件和软件资源。** 举例：运行在你电脑上的所有应用程序都通过操作系统来调用系统内存以及磁盘等等硬件。
>
> - **操作系统存在屏蔽了硬件层的复杂性。** 操作系统就像是硬件使用的负责人，统筹着各种相关事项。
>
> - **操作系统的内核（Kernel）是操作系统的核心部分，它负责系统的内存管理，硬件设备的管理，文件系统的管理以及应用程序的管理**。 **内核是连接应用程序和硬件的桥梁，决定着系统的性能和稳定性**。
>
> ![image-20230415010356040](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230415010356040.png)
>
> ![image-20230331112833627](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331112833627.png)

### Function

> ### :bulb:Function:
>
> - **Processor Management**
> - **Memory Management**
> - **Device Management**
> - **File Management**
> - Other Important Activities
>   - Security
>   - Control over system performance
>   - Job accounting
>   - Error detecting aids
>   - Coordination between other softwares and users
>
> ## Memory Management
>
> Memory management refers to management of Primary Memory or Main  Memory. Main memory is a large array of words or bytes where each word  or byte has its own address.
>
> Main memory provides a fast storage that can be accessed directly by  the CPU. For a program to be executed, it must in the main memory. An  Operating System does the following activities for memory management −
>
> - Keeps tracks of primary memory, i.e., what part of it are in use by whom, what part are not in use.
> - In multiprogramming, the OS decides which process will get memory when and how much.
> - Allocates the memory when a process requests it to do so.
> - De-allocates the memory when a process no longer needs it or has been terminated.
>
> ## Processor Management
>
> In multiprogramming environment, the OS decides which process gets  the processor when and for how much time. This function is called **process  scheduling**. An Operating System does the following activities for processor management −
>
> - Keeps tracks of processor and status of process. The program responsible for this task is known as **traffic controller**.
> - Allocates the processor (CPU) to a process.
> - De-allocates processor when a process is no longer required.
>
> ## Device Management
>
> An Operating System manages device communication via their respective drivers. It does the following activities for device management −
>
> - Keeps tracks of all devices. Program responsible for this task is known as the **I/O controller**.
> - Decides which process gets the device when and for how much time.
> - Allocates the device in the efficient way.
> - De-allocates devices.
>
> ## File Management
>
> A file system is normally organized into directories for easy  navigation and usage. These directories may contain files and other  directions.
>
> An Operating System does the following activities for file management −
>
> - Keeps track of information, location, uses, status etc. The collective facilities are often known as **file system**.
> - Decides who gets the resources.
> - Allocates the resources.
> - De-allocates the resources.
>
> ## Other Important Activities
>
> Following are some of the important activities that an Operating System performs −
>
> - **Security** −  By means of password and similar other techniques, it prevents unauthorized access to programs and data.
> - **Control over system performance** − Recording delays between request for a service and response from the system.
> - **Job accounting** − Keeping track of time and resources used by various jobs and users.
> - **Error detecting aids** − Production of dumps, traces, error messages, and other debugging and error detecting aids.
> - **Coordination between other softwares and users** −  Coordination and assignment of compilers, interpreters, assemblers and  other software to the various users of the computer systems.

## Key concepts

### User Mode vs Kernel Mode

> 操作系统在启动时会运行在内核态，而应用程序则会运行在用户态。
>
> Moving between the user mode and the kernel mode is referred to as **context switching**. 
>
> - 用户态
>
> 在用户态下，应用程序只能访问自己的内存空间，无法直接访问操作系统内核的内存空间和硬件资源。应用程序在用户态下运行时，只能使用操作系统提供的服务（例如系统调用）来请求操作系统执行某些操作，操作系统会在接收到请求后从内核态切换到用户态，执行相应的操作，然后再返回结果。
>
> 在用户态下，应用程序能够执行的操作和访问的资源都受到一定的限制，这是为了保证应用程序的安全性和稳定性。
>
> - 内核态
>
> 在内核态下，操作系统可以访问所有的内存空间和硬件资源，可以执行任何指令，这是因为操作系统拥有最高的特权级别。在内核态下，操作系统可以对硬件进行直接操作，从而实现各种系统服务，例如**设备管理**、**进程通信**、**进程管理**、**文件管理**、**内存管理**等。
>
> 当应用程序需要访问系统资源或执行需要特权级别的操作时，需要通过系统调用等方式进入内核态，由操作系统来完成相应的操作。
>
> 
>
> 在操作系统运行过程中，用户态和内核态之间需要频繁地进行切换，这是因为应用程序需要不断地与操作系统进行交互。但是由于从用户态到内核态的切换涉及到一定的系统开销，因此**应该尽量减少用户态和内核态之间的切换次数**。

![image-20230331114704912](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331114704912.png)

![image-20230331114021917](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331114021917.png)

### Context Switching

> Context switching occurs when a user process makes a request to the underlying system API. The switch does not occur automatically; rather, an interrupt is generated. An interrupt handler then saves the state of the CPU, switches to the kernel mode where the CPU can execute the instructions, and then restores the state of the CPU and returns to user mode.
>
> Moving between the user mode and the kernel mode is referred to as **context switching**. 
>
> 上下文切换（Context Switch）是指操作系统（OS）在进行多任务处理时，将当前进程的上下文信息（如寄存器状态、内存映像等）保存起来，并恢复另一个进程的上下文信息，使得该进程能够继续执行。
>
> 在多任务处理系统中，多个进程可以同时运行。但是，由于 CPU 只有一个，因此操作系统需要通过时间片轮转等调度算法来切换进程的执行，从而实现多个进程并发执行的效果。
>
> 上下文切换的过程包括以下几个步骤：
>
> 1. 保存当前进程的上下文信息，包括寄存器、程序计数器、内存映像等。
> 2. 加载另一个进程的上下文信息，包括寄存器、程序计数器、内存映像等。
> 3. 切换内核栈，以便在内核模式下执行。
> 4. 将控制权转移到新进程的代码处，使得该进程能够继续执行。
>
> 由于上下文切换需要保存和恢复大量的上下文信息，因此它会带来一定的系统开销。为了尽量减少上下文切换的次数，操作系统会采用各种优化措施，如时间片轮转、进程优先级调度等，以提高系统的运行效率。
>
> ![image-20230331115036332](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331115036332.png)

### System Call in OS (Operating System)

> 系统调用（system call）是**操作系统提供给应用程序调用的一组接口**，可以用来请求操作系统执行某些特定的功能，例如打开、关闭文件，读写文件内容，创建或销毁进程等等。应用程序通常通过调用系统调用来使用操作系统提供的功能。
>
> 系统调用是应用程序与操作系统之间的接口，应用程序可以通过系统调用请求操作系统完成某些任务。在执行系统调用时，应用程序会进入内核空间，操作系统会为应用程序提供所需的服务，然后将控制权返回给应用程序。由于系统调用需要进入内核空间，所以其执行开销较大，但其具有重要的功能和高度的安全性。
>
> 常见的系统调用包括：文件操作相关的 open、close、read、write、lseek等；进程操作相关的fork、execve、wait等；网络操作相关的socket、connect、send、recv等等。
>
> ![image-20230331114639257](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331114639257.png)
>
> ![image-20230331114021917](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331114021917.png)
>
> ![image-20230331113848396](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331113848396.png)
>
> - 设备管理。完成设备的请求或释放，以及设备启动等功能。
>
> - 文件管理。完成文件的读、写、创建及删除等功能。
>
> - 进程控制。完成进程的创建、撤销、阻塞及唤醒等功能。
>
> - 进程通信。完成进程之间的消息传递或信号传递等功能。
>
> - 内存管理。完成内存的分配、回收以及获取作业占用内存区大小及地址等功能。
>
> ### Process Control
>
> Process control is the system call that is used to direct the  processes. Some process control examples include creating, load, abort,  end, execute, process, terminate the process, etc.
>
> ### File Management
>
> File management is a system call that is used to handle the files.  Some file management examples include creating files, delete files,  open, close, read, write, etc.
>
> ### Device Management
>
> Device management is a system call that is used to deal with devices. Some examples of device management include read, device, write, get  device attributes, release device, etc.
>
> ### Information Maintenance
>
> Information maintenance is a system call that is used to maintain  information. There are some examples of information maintenance,  including getting system data, set time or date, get time or date, set  system data, etc.
>
> ### Communication
>
> Communication is a system call that is used for communication. There  are some examples of communication, including create, delete  communication connections, send, receive messages, etc.

### Process vs Thread

![image-20230331120133495](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331120133495.png)

![image-20230331120152440](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331120152440.png)

> **进程:** 
>
> **A process is the execution of a program.** It includes  the program itself, data, resources such as files, and execution info  such as process relation information kept by the OS. The OS allows users to create, schedule, and terminate the processes via system calls.
>
> 是操作系统中的一个执行单元，它包括了程序代码、数据、打开的文件、分配的内存等资源。进程是一个独立的运行环境，它拥有自己的地址空间、系统资源和执行状态，与其他进程相互隔离。每个进程都有一个唯一的进程标识符（PID），用于在系统中唯一地标识该进程。
>
> 
>
> **线程:**
>
> **A thread is a semi-process.** It has its own stack and  executes a given piece of code. Unlike a real process, the thread  normally shares its memory with other threads. Conversely, processes  usually have a different memory area for each one of them.
>
> 是进程的一个执行单元，它是进程中的一部分，是程序执行的一条路径。一个进程可以包含多个线程，每个线程共享进程的地址空间、系统资源和执行状态。线程可以看做是轻量级进程，它比进程更容易创建和销毁，可以在同一进程内的不同线程之间进行数据共享和通信。每个线程都有自己的线程标识符（TID），用于在进程中唯一地标识该线程。
>
> 
>
> 进程和线程的区别在于：
>
> 1. 资源管理：进程是系统资源分配的最小单位，每个进程都拥有自己的地址空间、文件描述符、信号处理器等系统资源；而线程共享进程的资源，包括地址空间、文件描述符、信号处理器等。
> 2. 调度：进程是操作系统进行调度和分配资源的基本单位，每个进程都有独立的调度队列和调度策略；而线程是进程的执行单元，由操作系统调度和分配CPU资源。
> 3. 通信：进程间通信需要借助于操作系统提供的机制，如管道、消息队列、共享内存等；而线程间通信可以直接读写共享变量来进行数据交换。
>
> 
>
> **进程间的通信：**
>
> 进程间通信（IPC，Inter-Process Communication）是指在不同进程之间进行数据传输和交换的机制。它允许进程在需要时交换信息、协调行动和共享资源。
>
> 常见的进程间通信方法包括：
>
> 1. 管道（Pipe）：管道是一种单向通信机制，它允许一个进程向另一个进程发送数据。管道分为有名管道和无名管道，有名管道可以通过文件系统进行访问，无名管道只能在相关进程间进行通信。
> 2. 信号（Signal）：信号是一种异步通信机制，它允许一个进程向另一个进程发送一个信号，通知其发生了某个事件。接收进程可以捕获信号并执行相应的操作。
> 3. 共享内存（Shared Memory）：共享内存允许多个进程共享同一个物理内存区域，从而可以直接读写共享内存中的数据，而不需要通过复制和发送数据来实现进程间通信。
> 4. 消息队列（Message Queue）：消息队列是一种基于消息传递的通信机制，它允许一个进程向另一个进程发送一个消息，并将该消息放入消息队列中。接收进程可以从消息队列中读取该消息。
> 5. 套接字（Socket）：套接字是一种基于网络协议的通信机制，它允许不同主机间的进程进行通信。套接字可以用于本地进程间通信，也可以用于远程进程间通信。
>
> 
>
> **线程间的通信：**
>
> 线程是共享同一个进程的执行单元，因此它们可以使用相同的内存空间进行通信。常见的线程间通信方法包括：
>
> 1. 锁（Lock）：锁是一种同步机制，它允许线程独占共享资源，从而避免多个线程同时访问和修改共享数据的问题。线程可以使用锁来保证同步访问共享资源。
> 2. 条件变量（Condition Variable）：条件变量是一种同步机制，它允许线程等待某个条件的发生，并在条件满足时被唤醒。线程可以使用条件变量来等待其他线程的通知，从而避免忙等待的问题。
> 3. 信号量（Semaphore）：信号量是一种同步机制，它可以控制多个线程同时访问某个共享资源的数量。线程可以使用信号量来保证同步访问共享资源。
> 4. 屏障（Barrier）：屏障是一种同步机制，它可以让多个线程等待彼此达到一个共同点，然后再继续执行。线程可以使用屏障来同步它们的执行。
> 5. 共享内存（Shared Memory）：共享内存也可以用于线程间通信，同一进程中的线程可以使用共享内存直接读写共享数据，而不需要复制和发送数据。
> 6. 消息队列（Message Queue）：消息队列也可以用于线程间通信，线程可以向消息队列中发送消息，并从消息队列中读取消息。
>
> 以上是常见的几种线程间通信方法，选择合适的方法可以提高线程间通信的效率和可靠性。需要注意的是，在多线程编程中，线程间通信可能会出现竞争条件（Race Condition）等问题，需要使用合适的同步机制来避免这些问题的发生。

### Deadlock

> 死锁（Deadlock）是一种多进程或多线程并发程序中常见的问题，指的是两个或多个进程或线程因互相持有对方所需的资源而无法继续执行的状态。简单来说，**死锁就是多个进程或线程互相等待对方释放资源，导致程序无法继续执行。**
>
> 
>
> **产生死锁的四个条件：**
>
> 1. **互斥**：两个或多个进程或线程互斥地占用一些资源，一旦某个进程或线程占用了该资源，其他进程或线程就无法再次占用该资源。
> 2. **占有并等待**：一个进程或线程占用了一些资源，并请求其他进程或线程占用其他资源，但是它又不释放自己占用的资源，导致其他进程或线程无法继续执行。
> 3. **循环等待**：多个进程或线程形成一个循环等待的状态，每个进程或线程都在等待下一个进程或线程释放资源。
> 4. **非抢占**：已经分配给某个进程或线程的资源不能被强制性地剥夺，只有该进程或线程自己释放该资源才行。
>
> 
>
> **解决死锁问题的方法：**
>
> 1. **预防死锁**：通过**破坏死锁产生的四个必要条件中的任何一个来预防死锁的发生**。
> 2. 避免死锁：在程序运行时，通过预先计算资源的使用情况，避免进程或线程进入死锁状态。
> 3. 检测死锁：在程序运行时，检测是否存在死锁，并尝试通过回收资源来解除死锁状态。
> 4. 解除死锁：通过强制终止某些进程或线程、回收资源或者进行资源剥夺等方法，解除死锁状态。
>
> 一般比较实用的 **预防死锁的方法**，是通过考虑**破坏**第二个条件（**占有并等待**）和第四个条件（**非抢占**）。

### Concurrency and Parallelism

![image-20230331120302744](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230331120302744.png)

> 并发和并行是计算机科学中两个重要的概念，它们都与多任务处理相关，但具有不同的含义。
>
> 
>
> **并发（Concurrency）**
>
> 是指系统中存在多个独立的任务，并且这些任务在一段时间内都得到了执行，它们之间的执行顺序不确定。在一个并发系统中，多个任务可以交替执行，每个任务都会执行一段时间，然后暂停，等待其他任务执行。并发通常是通过多线程、协程、事件驱动等机制来实现的。
>
> 
>
> **并行（Parallelism）**
>
> 是指系统中同时存在多个独立的任务，并且这些任务在同一时刻可以被执行，它们之间的执行顺序确定。在一个并行系统中，多个任务可以同时执行，每个任务都会占用一部分系统资源，如CPU、内存等。并行通常是通过多处理器、多核处理器等机制来实现的。
>
> 
>
> 并发和并行的区别在于：
>
> 1. 执行方式：并发是交替执行的，而并行是同时执行的。
> 2. 资源利用率：并发可以提高系统资源的利用率，多个任务可以共享同一系统资源；而并行可以提高系统处理能力，多个任务可以在多个处理器上并行执行，加快处理速度。
> 3. 开销：并发通常比并行更容易实现，但也可能会带来额外的开销，如上下文切换、线程同步等；而并行实现起来比较复杂，需要考虑任务之间的依赖关系、负载均衡等问题。

### Zero Copy

> **零拷贝（Zero Copy）**技术是一种用于**减少计算机系统中数据传输时CPU的消耗的技术**。
>
> 零拷贝技术的思想是避免这种复制过程（**避免在⽤户态与内核态之间来回拷⻉数据**），直接**将数据从源内存映射到目的地内存中**，**避免了不必要的复制过程，从而减少了CPU的消耗**，提高了系统的效率。
>
> 在Linux系统中，使用零拷贝技术可以通过mmap()系统调用实现。mmap()函数将文件映射到内存中，并将该文件的内容直接映射到用户空间中，从而实现零拷贝技术。
>
> 除了在文件传输中使用，**零拷贝技术还可以用于网络数据传输中，可以通过使用RDMA（Remote Direct Memory Access）技术来实现**，
>
> **避免了数据在传输过程中CPU的中介操作。**
>
> 总的来说，零拷贝技术通过减少CPU的消耗，提高了系统的效率和性能，广泛应用于高性能计算、云计算、存储和网络等领域。



![image-20230414132248722](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230414132248722.png)



> **实现零拷贝技术**需要硬件和软件的支持。
>
> - 在**硬件方面**，操作系统**需要支持DMA（Direct Memory Access）技术，使得设备可以直接读写内存**。
> - 在**软件方面**，操作系统**需要提供相关的API和框架，使得应用程序可以使用零拷贝技术。**
>
> 
>
> **DMA**（Direct Memory Access）
>
> 直译过来是“直接内存访问”。DMA是一种硬件技术，它允许外部设备（如硬盘、网卡等）直接访问系统内存，而不需要通过CPU进行数据传输。这样可以减少CPU的工作负担，提高数据传输效率。
>
> 在传统的I/O过程中，数据的传输是由CPU负责的，数据从外部设备到达I/O控制器，再由I/O控制器将数据传输到CPU内存中。而在使用DMA技术时，数据传输的过程被分成两个步骤：首先，外部设备将数据传输到DMA控制器的缓冲区中；然后，DMA控制器将数据直接传输到内存中，而不需要CPU的参与。
>
> 通过使用DMA技术，可以减少CPU的工作负担，提高数据传输效率

![image-20230414130523566](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230414130523566.png)

## Process Management

## Memory Management

## Input / Output

## File System