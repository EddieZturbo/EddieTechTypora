# I/O

> 在UNIX世界⾥⼀切皆⽂件，⽂件就是⼀串⼆进制流⽽已，其实不管是Socket ，还是FIFO （First InputFirst Output，先进先出队列））、管道、终端。对计算机来说，⼀切都是⽂件，⼀切都是流。在信息交换的过程中，计算机都是对这些流进⾏数据的收发操作，简称为I/O操作（Input and Output）。

## I/O交互的过程

> 通常⽤户进程中的⼀次完整I/O交互流程分为两阶段，⾸先是经过内核空间，也就是由操作系统处理；紧接着就是到⽤户空间，也就是交由应⽤程序。

![image-20230404210526467](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404210526467.png)

## 多种I/O通信模型

> **同步I/O**
>
> - 阻塞I/O模型、BIO
> - ⾮阻塞I/O模型、NIO
> - 多路复⽤I/O模型、
> - 信号驱动I/O模型、
>
> **异步I/O模型**
>
> - 异步I/O、AIO

![image-20230404211347823](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211347823.png)

### 阻塞I/O模型

![image-20230404211021851](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211021851.png)

### 非阻塞I/O模型

![image-20230404211103984](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211103984.png)

### 多路复⽤I/O模型

![image-20230404211133399](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211133399.png)

### 信号驱动IO模型

![image-20230404211218286](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211218286.png)

### 异步IO模型

![image-20230404211258819](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230404211258819.png)

## Java NIO

https://javadoop.com/post/java-nio

> Java 中的 NIO 于 Java 1.4 中引入，对应 `java.nio` 包，提供了 `Channel` , `Selector`，`Buffer` 等抽象。NIO 中的 N 可以理解为 Non-blocking，不单纯是 New。它是支持面向缓冲的，基于通道的 I/O 操作方法。 对于高负载、高并发的（网络）应用，应使用 NIO 。
>
> - **NIO 是非阻塞的**
> - **NIO 面向块，I/O 面向流**
>
> ## `Selector`
>
> **一个线程 Thread 使用一个选择器 `Selector`** 通过**轮询的方式去监听多个通道 `Channel` 上的事件**，从而让**一个线程就可以处理多个事件**。
>
> 通过配置监听的通道 Channel 为非阻塞，那么当 Channel 上的 IO 事件还未到达时，就不会进入阻塞状态一直等待，而是继续轮询其它 Channel，找到 IO 事件已经到达的 Channel 执行。
>
> ## `Channel`
>
> 通道 `Channel` 是**对应原 I/O 包中的流（Stream）**的模拟，可以通过它读取和写入数据。
>
> - **流只能在一个方向上移动**(一个流必须是 InputStream 或者 OutputStream 的子类)，
>
> - **Channel是双向的**，可以**用于读、写或者同时用于读写**。
>
> Java.nio 包中实现的以下几个 Channel：
>
> - FileChannel: 从文件中读写数据；
>
> - DatagramChannel: 通过 UDP 读写网络中数据；
>
> - SocketChannel: 通过 TCP 读写网络中数据；
>
> - ServerSocketChannel: 可以监听新进来的 TCP 连接，对每一个新进来的连接都会创建一个 SocketChannel。
>
>
> ## `Buffer`
>
> **不会直接对通道进行读写数据，而是要先经过缓冲区**。
>
> 发送给一个通道的所有数据都必须首先放到缓冲区中，同样地，从通道中读取的任何数据都要先读到缓冲区中。
>
> 缓冲区**实质上是一个数组，但它不仅仅是一个数组**。缓冲区提供了对数据的结构化访问，而且还可以跟踪系统的读/写进程。
>
> 
>
> 缓冲区包括以下类型:
>
> - **ByteBuffer**
> - CharBuffer
> - ShortBuffer
> - IntBuffer
> - LongBuffer
> - FloatBuffer
> - DoubleBuffer
>
> 缓冲区状态变量
>
> - capacity: 最大容量；
> - position: 当前已经读写的字节数；
> - limit: 还可以读写的字节数。

![image-20230424105440726](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230424105440726.png)

### Instance

#### Client

```java
package nio.client;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.SocketChannel;
import java.text.SimpleDateFormat;
import java.util.Scanner;

/**
 @author EddieZhang
 @create 2023-04-13 10:56 PM
 */
public class ClientZero {
    public static void main(String[] args) throws IOException {
        //Open a SocketChannel and indicate server IP and Port
        SocketChannel socketChannel = SocketChannel.open(new InetSocketAddress("127.0.0.1", 9956));
        //Choose non-block mode
        socketChannel.configureBlocking(false);
        //prepare buffer
        ByteBuffer buf = ByteBuffer.allocate(1024);
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNext()){
            String str = scanner.nextLine();
            //obtain inputData and write to buffer
            buf.put((new SimpleDateFormat("yyyy/MM/dd HH:mm:ss").format(System.currentTimeMillis())
                    + "\n" + str).getBytes());
            buf.flip();
            //write buf to channel
            socketChannel.write(buf);
            buf.clear();
        }
        //5. Close channel
        socketChannel.close();
    }
}

```

#### Server

```java
package nio.server;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.SelectionKey;
import java.nio.channels.Selector;
import java.nio.channels.ServerSocketChannel;
import java.nio.channels.SocketChannel;
import java.util.Iterator;

/**
 @author EddieZhang
 @create 2023-04-13 10:56 PM
 */
public class ServerZero {
    public static void main(String[] args) throws IOException {
        ServerSocketChannel serverSocketChannel = ServerSocketChannel.open();//open a ServerSocketChannel
        serverSocketChannel.configureBlocking(false);//choose non-block mode
        serverSocketChannel.bind(new InetSocketAddress(9956));//binding a port
        Selector selector = Selector.open();//obtain a selector

        System.out.println("ServerZero Ready");
        //register channel to selector and indicate accept events
        serverSocketChannel.register(selector, SelectionKey.OP_ACCEPT);
        while (selector.select() > 0){
            System.out.println("New Round");
            //obtain all the  selectionKeys
            Iterator<SelectionKey> iterator = selector.selectedKeys().iterator();
            //Iterate over each one
            while (iterator.hasNext()){
                //obtain the event
                SelectionKey selectionKey = iterator.next();
                //What type of event it is
                if(selectionKey.isAcceptable()){
                    SocketChannel socketChannel = serverSocketChannel.accept();
                    socketChannel.configureBlocking(false);
                    socketChannel.register(selector, SelectionKey.OP_READ);
                }else if(selectionKey.isReadable()){
                    SocketChannel socketChannel = (SocketChannel)selectionKey.channel();
                    //read data
                    ByteBuffer bf = ByteBuffer.allocate(1024);
                    int len = 0;
                    while ((len = socketChannel.read(bf)) > 0){
                        bf.flip();
                        System.out.println(new String(bf.array(), 0, len));
                        bf.clear();
                    }
                }
            }
            iterator.remove();
        }

    }
}
```

#### Group Client

```java
package nio.client;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.SelectionKey;
import java.nio.channels.Selector;
import java.nio.channels.SocketChannel;
import java.nio.charset.StandardCharsets;
import java.util.Iterator;
import java.util.Scanner;
import java.util.Set;
import java.util.concurrent.TimeUnit;

/**
 @author EddieZhang
 @create 2023-04-14 3:23 PM
 */
public class GroupChatClientZero {
    //define property
    private static final String HOST = "127.0.0.1";
    private static final int PORT = 9556;
    private Selector selector;
    private SocketChannel socketChannel;
    private String username;

    //constructor method initial
    public GroupChatClientZero() {
        try {
            socketChannel = SocketChannel.open(new InetSocketAddress(HOST, PORT));
            socketChannel.configureBlocking(false);
            selector = Selector.open();
            socketChannel.register(selector, SelectionKey.OP_READ);

            username = socketChannel.getLocalAddress().toString().substring(1);
            System.out.println("Client\t" + username + "\tready");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * sent msg to server method
     * @param msg data
     */
    public void sentMessage(String msg) {
        msg = username + "\t talk: \t" + msg;
        try {
            socketChannel.write(ByteBuffer.wrap(msg.getBytes(StandardCharsets.UTF_8)));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * Receive information from the server
     */
    public void readInfo() {
        try {
            int readableChannels = selector.select();
            if (readableChannels > 0) {
                //get all the selectionKeys
                Set<SelectionKey> selectionKeys = selector.selectedKeys();
                //iterate all each selectionKey
                Iterator<SelectionKey> iterator = selectionKeys.iterator();
                while (iterator.hasNext()) {
                    SelectionKey key = iterator.next();
                    if (key.isReadable()) {
                        SocketChannel socketChannel = (SocketChannel) key.channel();
                        //prepare a buffer
                        ByteBuffer byteBuffer = ByteBuffer.allocate(1024);
                        socketChannel.read(byteBuffer);
                        String receiveMsg = new String(byteBuffer.array());
                        System.out.println(username + "\treceive msg from server: " + receiveMsg.trim());
                    }
                }
                iterator.remove();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static void main(String[] args) {
        GroupChatClientZero groupChatClientZero = new GroupChatClientZero();
        //start one thread to receive msg from server (Once / 3s)
        new Thread(() -> {
            while (true) {
                groupChatClientZero.readInfo();//receive msg from server
                try {
                    TimeUnit.SECONDS.sleep(3);//sleep 3s
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }).start();

        //send msg to server
        Scanner scanner = new Scanner(System.in);
        while (scanner.hasNextLine()) {
            String msg = scanner.nextLine();
            groupChatClientZero.sentMessage(msg.trim());
        }
    }
}

```

#### Group Server

```java
	package nio.server;

import java.io.IOException;
import java.net.InetSocketAddress;
import java.nio.ByteBuffer;
import java.nio.channels.*;
import java.nio.charset.StandardCharsets;
import java.util.Iterator;

/**
 @author EddieZhang
 @create 2023-04-14 3:22 PM
 */
public class GroupChatServerZero {
    //define property
    private Selector selector;
    private ServerSocketChannel serverSocketChannel;
    private static final int PORT = 9556;

    //constructor initial
    public GroupChatServerZero() {
        try {
            serverSocketChannel = ServerSocketChannel.open();
            serverSocketChannel.configureBlocking(false);
            serverSocketChannel.bind(new InetSocketAddress(PORT));

            selector = Selector.open();
            serverSocketChannel.register(selector, SelectionKey.OP_ACCEPT);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    //listening method
    public void listening() {
        System.out.println("listening ready");
        try {
            while (selector.select() > 0) {
                System.out.println("begin handle event");
                //iterate all the events
                Iterator<SelectionKey> iterator = selector.selectedKeys().iterator();
                while (iterator.hasNext()) {
                    //obtain one of the events
                    SelectionKey selectionKey = iterator.next();
                    //judge what is the event?
                    if (selectionKey.isAcceptable()) {
                        //Gets the channel of the currently connected client
                        SocketChannel socketChannel = serverSocketChannel.accept();
                        socketChannel.configureBlocking(false);
                        System.out.println(socketChannel.getRemoteAddress() + "\t" + "online");
                        //register this channel to selector
                        socketChannel.register(selector, SelectionKey.OP_READ);
                    } else if (selectionKey.isReadable()) {
                        //handle reading...
                        readData(selectionKey);
                    }
                }
                iterator.remove();//completed remove current event
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

    }

    /**
     * reading data method
     * @param selectionKey current event
     */
    public void readData(SelectionKey selectionKey) {
        SocketChannel channel = null;
        try {
            //get current channel
            channel = (SocketChannel) selectionKey.channel();
            //create a buffer and indicate capacity
            ByteBuffer byteBuffer = ByteBuffer.allocate(1024);
            //reading
            int read = channel.read(byteBuffer);
            if (read > 0) {
                //buffer‘s byte[] transfer to String
                String msg = new String(byteBuffer.array());
                System.out.println("from client data : " + msg.trim());

                //sent data to else client except current client
                sentDataToOtherClient(msg, channel);
            }

        } catch (IOException e) {
            e.printStackTrace();
            try {
                System.out.println(channel.getRemoteAddress() + "\t" + "down");
                selectionKey.cancel();//cancel register
                channel.close();//close channel
            } catch (IOException ex) {
                ex.printStackTrace();
            }
        }
    }

    /**
     * sent data to else client except current client
     * @param msg data
     * @param currentChannel current client channel
     */
    public void sentDataToOtherClient(String msg, SocketChannel currentChannel) throws IOException {
        System.out.println(Thread.currentThread().getName() + "\t server transfer the data to other client");
        //iterate all the socketChannels and except current channel
        for (SelectionKey key : selector.keys()) {
            //获取socketChannel
            Channel channel = key.channel();
            //judge whether isn't current channel
            if (channel instanceof SocketChannel && channel != currentChannel) {
                SocketChannel destSocketChannel = (SocketChannel) channel;
                //write msg to destination
                ByteBuffer byteBuffer = ByteBuffer.wrap(msg.getBytes(StandardCharsets.UTF_8));
                destSocketChannel.write(byteBuffer);
            }
        }
    }

    public static void main(String[] args) {
        GroupChatServerZero groupChatServerZero = new GroupChatServerZero();
        groupChatServerZero.listening();
    }
}

```

