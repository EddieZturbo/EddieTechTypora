# Data-Structure & Algorithm

> 程序 = 数据结构 + 算法
>
> **Programming = Data Structure + Algorithm**

![image-20230428193718480](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230428193718480.png)

## **时间 / 空间复杂度分析**

### 时间复杂度

**时间频度**：一个算法花费的时间与算法中语句的执行次数成正比例，哪个算法中语句执行次数多，它花费时间就多。**一个算法中的语句执行次数称为语句频度或时间频度**。记为T(n)

**一般情况下，算法中的基本操作语句的重复执行次数是问题规模n的某个函数，用T(n)表示，若有某个辅助函数f(n)，使得当n趋近于无穷大时，T(n) / f(n) 的极限值为不等于零的常数，则称f(n)是T(n)的同数量级函数。记作 T(n)=Ｏ( f(n) )，称Ｏ( f(n) ) 为算法的渐进时间复杂度，简称时间复杂度**

> //For instance **忽略常数项** **忽略低次项** **忽略最高次项系数**
>
> •用常数1代替运行时间中的所有加法常数 T(n)=n²+7n+6 => T(n)=n²+7n+1
>
> •修改后的运行次数函数中，只保留最高阶项 T(n)=n²+7n+1 => T(n) = n²
>
> •去除最高阶项的系数 T(n) = n² => T(n) = n² => **O(n²)**
>

![image-20220912102347896](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102347896.png)

![image-20220912102401927](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102401927.png)

![image-20220912102413958](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102413958.png)

![image-20220912102423725](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102423725.png)

![image-20220912102442189](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102442189.png)

![image-20220912102432569](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102432569.png)

![image-20220912102500060](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102500060.png)

### 空间复杂度

考虑到用户体验 更看重时间效率 **空间换时间概念**

空间和时间二者不可得兼

![image-20220912102738194](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912102738194.png)

## Data-Structure

https://www.javatpoint.com/data-structure-tutorial

### **Linear data structure**

#### 数组

##### 普通数组

##### 稀疏数组（**sparse-array**）

**介绍**

稀疏数组可以看做是**普通数组的压缩**，但是这里说的普通数组是值**无效数据量远大于有效数据量**的数组

当一个数组中大部分元素为０，或者为同一个值的数组时，可以使用稀疏数组来保存该数组

稀疏数组的处理方法是:

1)记录数组一共有几行几列，有多少个不同的值

2)把具有不同值的元素的行列及值记录在一个小规模的数组中，从而缩小程序的规模

![image-20220908231242344](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220908231242344.png)

- 原数组中存在**大量的无效数据**，占据了大量的存储空间，真正有用的数据却少之又少
- **压缩存储**可以**节省存储空间**以避免资源的不必要的浪费，在数据序列化到磁盘时，压缩存储可以**提高IO效率**

**存储方式**

**普通存储**

```java
    //第一行存储原始数据总行数，总列数，总的非0数据个数（有效数据个数）
	//接下来每一行都存储非0数所在行，所在列，和具体值
	rows cols n
    r1   c1   val1
    r2   c2   val2
    .    .     .
    .    .     .
    rn   cn   valn
        
	eg
	11 11 2
    1  2  1
    2  4  2        
```

```java
/**
 * 稀疏数组
 */
public class SparseArray {
    /**
     *     稀疏数组可以简单的看作为是压缩，在开发中也会使用到。比如将数据序列化到磁盘上，减少数据量，在IO过程中提高效率等等。
     *
     *         为什么要进行压缩？
     *              - 由于稀疏矩阵中存在大量的“空”值，占据了大量的存储空间，而真正有用的数据却少之又少，
     *              - 且在计算时浪费资源，所以要进行压缩存储以节省存储空间和计算方便。
     *
     */
    public static void main(String[] args) {
        /**
         * 初始化二维数组
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 1 0 0 0 0 0 0 0 0
         *     0 0 0 0 2 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         *     0 0 0 0 0 0 0 0 0 0 0
         */
        int [][] array = new int[11][11];
        array[1][2] = 1;
        array[2][4] = 2;
        for (int[] row: array) {
            for (int item : row) {
                System.out.printf("%d\t",item);
            }
            System.out.println();
        }

        System.out.println("-------------------------------------------------------------------------");
        //将二维数组转换成稀疏数组
        /*
        稀疏数组
        11 11 2
        1  2  1
        2  4  2
        //第一行存储原始数据总行数，总列数，总的非0数据个数（有效数据个数）
        //接下来每一行都存储非0数所在行，所在列，和具体值

        1.要遍历普通数组得到有多少有效数据的个数
        2.创建稀疏数组
        3.给稀疏数组赋值
         */
        //得到有效数据个数
        int sum = 0;
        for (int i = 0; i < 11; i++) {
            for (int j = 0; j < 11; j++) {
                if(array[i][j] != 0){
                    sum++;
                }
            }
        }
        System.out.println("array数组中共有 " + sum + " 个有效数据");
        //创建稀疏数组
        int[][] sparseArray = new int[sum+1][3];//行数是由有效数据的个数加上1 列数固定是3
        //给稀疏数组赋值--第一行
        sparseArray[0][0] = 11;//稀疏数组第一行第一列填写原数组的行数
        sparseArray[0][1] = 11;//稀疏数组第一行第二列填写原数组的列数
        sparseArray[0][2] = sum;//稀疏数组第一行第三列填写有效数据的个数

        //给稀疏数组赋值--第一行以后的有效数据行
        int count = 0;//标识第几个有效数据
        for (int i = 0; i < 11; i++) {
            for (int j = 0; j < 11; j++) {
                if(array[i][j] != 0){
                    count++;
                    sparseArray[count][0] = i;//稀疏数组有效数据行第一列填写所在原数组的行数
                    sparseArray[count][1] = j;//稀疏数组有效数据行第二列填写所在原数组的列数
                    sparseArray[count][2] = array[i][j];//稀疏数组有效数据行第三列填写有效数据的值
                }
            }
        }
        //遍历稀疏数组
        for (int [] rows :
                sparseArray) {
            for (int item :
                    rows) {
                System.out.printf("%d\t",item);
            }
            System.out.println();
        }

        System.out.println("----------------------------------------------------------------------------");
        //将稀疏数组转成普通数组
        //初始化二维数组 将稀疏数组中的第一行存储原始数据总行数，总列数作为二维数组的外层和内存的长度
        int [][] oldArray = new int[sparseArray[0][0]][sparseArray[0][1]];
        //将有效数据按照稀疏数组中的位置赋值到二维数组相应的位置中
        //遍历稀疏数组拿到有效数据的位置以及值的信息
        for (int i = 1; i <= count; i++) {//从稀疏数组的第二行遍历（稀疏数组中有效值具体信息从第二行开始）
            oldArray[sparseArray[i][0]][sparseArray[i][1]] = sparseArray[i][2];//将（稀疏数组中从第二行开始存储有效值的所在行，所在列，和具体值）赋给二维数组相应的位置
        }
        //遍历普通数组
        for (int[] rows :
                oldArray) {
            for (int item :
                    rows) {
                System.out.printf("%d\t",item);
            }
            System.out.println();
        }

        System.out.println("--------------------------------------------------------------------------------");
        // 将稀疏数组储存至磁盘中
//        sparseArrayToIo(sparseArray);
        System.out.println("--------------------------------------------------------------------------------");
        //将稀疏数组从磁盘中读取
        int[][] sparseArrayFromIo = sparseArrayFromIo("spareArray.txt");
        for (int[] row :
                sparseArrayFromIo) {
            for (int item :
                    row) {
                System.out.printf("%d\t",item);
            }
            System.out.println();
        }


    }
    /*
        将稀疏数组储存至磁盘中
     */
    public static void sparseArrayToIo(int[][] sparseArray){
        FileWriter fileWriter = null;//造流
        try {
            File file = new File("spareArray.txt");//指明要保存到的文件路径（可以是绝对路径 也可以是相对路径）
            if(!file.exists()){//判断文件是否已经存在 若不存在 则新建文件
                file.createNewFile();
            }
            fileWriter = new FileWriter(file);
            //遍历稀疏数组 并writer
            for (int i = 0; i < sparseArray.length; i++) {//外层数组的行数
                for (int j = 0; j < 3; j++) {//稀疏数组的列数固定是3列
                    fileWriter.write(sparseArray[i][j]);//将遍历的稀疏数组进行writer
                }
            }
            fileWriter.flush();//刷新
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {
        //释放资源
            if (fileWriter != null) {
                try {
                    fileWriter.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }
    /*
        将稀疏数组从磁盘中读取
     */
    public static int[][] sparseArrayFromIo(String pathName){
        FileReader fileReader = null;
        try {
            File file = new File(pathName);
            fileReader = new FileReader(file);//创建流 用于读取磁盘中的稀疏数组数据
            Map<Integer,Integer> map = new HashMap<>();//创建一个hashmap用来储存读取到的稀疏数组
            int k = 0;
            int v = 0;
            while((v = fileReader.read()) != -1){
                map.put(k,v);
                k++;
            }
            if(map.size() == 0){
                return null;
            }
            int [][] sparseArray = new int[map.size()/3][3];//创建一个数组 将hashmap的数据赋值到稀疏数组中
            int index = 0;
            for (int i = 0; i < map.size()/3; i++) {
                for (int j = 0; j < 3; j++) {
                    sparseArray[i][j] = map.get(index);
                    index++;
                }
            }
            map.clear();
            return sparseArray;
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {
        //释放资源
            if (fileReader != null) {
                try {
                    fileReader.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }

}
```

**链式存储**

普通链式存储

行式链式存储

十字链式存储

#### 字符串



#### 队列

**队列（queue）**是一种采用**先进先出**(FIFO)策略的抽象数据结构，它的想法来自于生活中排队的策略。顾客在付款结账的时候，按照到来的先后顺序排队结账，先来的顾客先结账，后来的顾客后结账

**Ø队列是一个有序列表，可以用数组或是链表来实现。**

**Ø遵循先入先出的原则。即：先存入队列的数据，要先取出。后存入的要后取出**

![img](https://ask.qcloudimg.com/http-save/yehe-5359587/uj2ybsqwq7.gif)

##### 数组实现

![image-20220912104856018](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912104856018.png)

**(使用循环数组)**

![image-20220912162626123](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912162626123.png)

思路如下:

\1. front 变量的含义做一个调整： front 就指向队列的第一个元素, 也就是说 arr[front] 就是队列的第一个元素

front 的初始值 = 0

\2. rear 变量的含义做一个调整：rear 指向队列的最后一个元素的后一个位置. 因为希望空出一个空间做为约定.

rear 的初始值 = 0

\3. 当队列满时，条件是 (rear + 1) % maxSize == front 【满】

\4. 对队列为空的条件， rear == front 空

\5. 当我们这样分析， 队列中有效的数据的个数  (rear + maxSize - front) % maxSize  // rear = 1 front = 0 

```java
/*
 * @Description 环形数组模拟队列 编写一个类
 * @Author EddieZhang
 * @Date 2022/9/12 10:51
 * @Since version-1.0
 */
class ArrayQueue {
    private int maxSize;//表示数组的最大容量
    private int front;//队列头 指向队列的第一个元素 初始值为0
    private int rear;//队列尾 指向队列的最后一个元素的后一个位置. 因为希望空出一个空间做为约定 默认值为0
    private int[] array;//数组 用来储存队列数据 模拟队列

    public ArrayQueue(int maxSize) {//构造器创造数组对象 传入数组的最大容量 maxSize
        this.maxSize = maxSize;
        array = new int[this.maxSize];
    }

    public boolean isFull() {//判断环形数组是否已经满
        if ((rear + 1) % maxSize == front) {
            return true;
        } else {
            return false;
        }
    }
    public boolean isEmpty(){//判断环形数组知否为空
        if(front == rear){
            return true;
        }else{
            return false;
        }
    }
    public void addQueue(int num){
        if(isFull()){//判断是否已满 未满可以添加数据
            System.out.println("队列已满，无法继续添加了哦~~");
            return;
        }
        //可以进行添加
        array[rear] = num;
        //将rear后移一个索引位置
        rear = (rear + 1) % maxSize;//考虑取模（保证在maxSize内循环）
    }
    public int getQueue(){
        if(isEmpty()){//判断是否队列是否为空
            throw new RuntimeException("队列为空 无法取出数据~~");
        }
        //将数据保存到临时变量中 将front后移一个索引位置 返回数据
        int temp = array[front];
        front = (front + 1)%maxSize;//考虑取模（保证在maxSize内循环）
        return temp;
    }
    public void showQueue(){
        if(isEmpty()){
            System.out.println("队列为空");
            return;
        }
        //遍历 从front开始遍历 考虑遍历多少个（遍历有效值个）
        for (int i = front; i < front + numQueue(); i++) {
            System.out.printf("array[%d]=%d\n",i % maxSize,array[i % maxSize]);
        }

    }
    /*
     * @Description 求队列中有多少个有效值
     * @Author EddieZhang
     * @Date 2022/9/12 15:19
     * @Param []
     * @Return int
     * @Since version-1.0
     */
    public int numQueue(){
        return (rear - front + maxSize)%maxSize;
    }
    public int getFront(){
        if(isEmpty()){
            throw new RuntimeException("队列为空");
        }
        return array[front];

    }


}
```

##### 链表实现

#### 栈

**栈（stack）是限定仅在表尾进行插入和删除操作的线性表**

我们把**允许插入和删除的一端**称之为**栈顶（top）**，另一端**固定的一端**称为**栈底（bottom）**，**不含任何数据元素的栈称为空栈**。

栈又称后进（push压栈）先出（pop弹栈）（Last In First Out）的线性表，简称**LIFO结构**。

![img](https://ask.qcloudimg.com/http-save/yehe-5359587/f1uyb7t5l4.gif)

![image-20220917211941913](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220917211941913.png)

![image-20220917212336802](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220917212336802.png)



#### 链表

**链表和数组的区别：**
**两者的区别：**

数组静态分配内存，链表动态分配内存。
数组在内存中是连续的，链表是不连续的。
数组利用下标定位，查找的时间复杂度是O(1)，链表通过遍历定位元素，查找的时间复杂度是O(N)。
数组插入和删除需要移动其他元素，时间复杂度是O(N)，链表的插入或删除不需要移动其他元素，时间复杂度是O(1)。
**数组的优点**
随机访问性比较强，可以通过下标进行快速定位。
查找速度快
**数组的缺点**
插入和删除的效率低，需要移动其他元素。
会造成内存的浪费，因为内存是连续的，所以在申请数组的时候就必须规定七内存的大小，如果不合适，就会造成内存的浪费。
内存空间要求高，创建一个数组，必须要有足够的连续内存空间。
数组的大小是固定的，在创建数组的时候就已经规定好，不能动态拓展。
**链表的优点**
插入和删除的效率高，只需要改变指针的指向就可以进行插入和删除。
内存利用率高，不会浪费内存，可以使用内存中细小的不连续的空间，只有在需要的时候才去创建空间。大小不固定，拓展很灵活。
**链表的缺点**
查找的效率低，因为链表是从第一个节点向后遍历查找

##### 单链表

![image-20220912163840700](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912163840700.png)



1)链表是以节点的方式来存储,是链式存储

2)每个节点包含 data 域， next 域：指向下一个节点.

3)如图：发现链表的**各个节点不一定是连续存储**.

4)链表分带头节点的链表和没有头节点的链表，根据实际的需求来确定

![image-20220912163530982](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912163530982.png)

![image-20220912163545966](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220912163545966.png)

```java
/**
 * 单向链表
 */
public class SingleLinkedListDemo {
    public static void main(String[] args) {
        //创建几个HeroNode
        HeroNode node1 = new HeroNode(1, "Eddie", "张锦豪");
        HeroNode node2 = new HeroNode(2, "Irving", "欧文");
        HeroNode node3 = new HeroNode(3, "James", "詹姆斯");
        HeroNode node4 = new HeroNode(4, "Curry", "库里");
        HeroNode node5 = new HeroNode(1, "EddieZhang", "锦豪");
        HeroNode node6 = new HeroNode(3, "King James", "詹皇");
        HeroNode node7 = new HeroNode(6, "Durant", "杜小帅");
        HeroNode node8 = new HeroNode(7, "Harden", "火箭登");
        HeroNode node9 = new HeroNode(8, "Jordan", "篮球之神");

        //创建单向链表
        SingleLinkedList singleLinkedList = new SingleLinkedList();
        singleLinkedList.add2(node1);//添加
        singleLinkedList.add2(node4);
        singleLinkedList.add2(node3);
        singleLinkedList.add2(node2);
        singleLinkedList.showList();
        System.out.println("-------------------------------------------------------");
        singleLinkedList.replaceNode(node5);//替换
        singleLinkedList.showList();
        System.out.println("-------------------------------------------------------");
        singleLinkedList.modifyNode(node6);//修改
        singleLinkedList.showList();
        System.out.println("-------------------------------------------------------");
        singleLinkedList.selectNode(1);//查找
        System.out.println("-------------------------------------------------------");
        singleLinkedList.deleteNode(4);//删除
        singleLinkedList.showList();
        System.out.println("-------------------------------------------------------");
        int numNode = numNode(singleLinkedList.getHead());//求单链表中有效节点的个数
        System.out.printf("链表中的有效节点有\t%d\t个\n", numNode);
        System.out.println("-------------------------------------------------------");
        HeroNode searchNode = singleLinkedList.searchNode(2);//查找单链表中的倒数第k个结点 
        if (searchNode != null) {
            System.out.printf("倒数第\t%d\t个节点为\n" + searchNode, 2);
        }
        System.out.println();
        System.out.println("-------------------------------------------------------");
        singleLinkedList.reverseNode();//单链表的反转
        singleLinkedList.showList();
        System.out.println("-------------------------------------------------------");
        singleLinkedList.reversePrint();//从尾到头打印单链表 使用到stack（栈 特性是 先进后出）
        System.out.println("-------------------------------------------------------");
        singleLinkedList.reverseNode();
        singleLinkedList.add2(node8);

        singleLinkedList.showList();

        System.out.println("------------------------------------------------------------");
        SingleLinkedList singleLinkedList1 = new SingleLinkedList();
        singleLinkedList1.add2(node7);
        singleLinkedList1.add2(node4);
        singleLinkedList1.add2(node9);


        singleLinkedList1.showList();


        System.out.println("------------------------------------------------------------");
        SingleLinkedList concatList = SingleLinkedList.concatList(singleLinkedList, singleLinkedList1);//合并两个有序的单链表
        concatList.showList();

    }
}

/*
 * @Description 单向链表设计(管理节点) 有一个head节点 保留
 * @Author EddieZhang
 * @Date 2022/9/12 17:15
 * @Since version-1.0
 */
class SingleLinkedList {
    //有个head节点
    private HeroNode head = new HeroNode(0, null, null);

    public HeroNode getHead() {
        return head;
    }

    //添加节点--通过temp进行链表的遍历 找到最后一个节点
    public void addNode(HeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个零时节点
        HeroNode temp = head;
        //通过temp进行链表的遍历 找到最后一个节点
        while (true) {//一直寻找到最后的节点 将新的节点置为最后节点的next
            if (temp.next == null) {//说明temp以及到链表的最后了
                break;
            }
            //如果没有到最后
            temp = temp.next;//往后移动
        }
        //此时temp 已经在最后一个节点处 可以进行添加 将新的节点置为最后节点的next
        temp.next = node;
    }

    /*
     * @Description 按照指定的要求进行添加
     * @Author EddieZhang
     * @Date 2022/9/12 20:04
     * @Param []
     * @Return void
     * @Since version-1.0
     */
    public void add2(HeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个零时节点
        HeroNode temp = head;
        boolean flag = false;
        while (true) {
            if (temp.next == null) {//判断temp是不是最后一个
                break;
            }
            //查到有别的节点
            if (temp.next.no > node.no) {
                break;
            }
            if (temp.next.no == node.no) {//是否已经存在此节点
                flag = true;
                break;
            }
            temp = temp.next;//向后移动
        }
        if (flag) {
            System.out.printf("待插入的标号%d已经存在，无法进行添加\n", node.no);
        } else {//进行添加操作
            node.next = temp.next;
            temp.next = node;
        }
    }

    /*
     * @Description replace节点 根据no
     * @Author EddieZhang
     * @Date 2022/9/12 20:27
     * @Param []
     * @Return void
     * @Since version-1.0
     */
    public void replaceNode(HeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个零时节点
        HeroNode temp = head;
        boolean flag = false;
        while (true) {
            if (temp.next == null) {
                break;
            }
            //查到有节点
            if (temp.next.no == node.no) {//no是否能够匹配
                flag = true;
                break;
            }
            temp = temp.next;//向后移动
        }
        if (flag) {
            if (temp.next.next == null) {
                temp.next = node;
            } else {
                node.next = temp.next.next;
                temp.next = node;
            }
        } else {
            System.out.printf("未查询到\t%d\t所对应的数据\n", node.no);
        }


    }

    /*
     * @Description 修改节点
     * @Author EddieZhang
     * @Date 2022/9/12 21:04
     * @Param [node]
     * @Return void
     * @Since version-1.0
     */
    public void modifyNode(HeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个零时节点
        HeroNode temp = head;
        boolean flag = false;
        while (true) {
            if (temp.next == null) {
                break;
            }
            //查到有节点
            if (temp.next.no == node.no) {//no是否能够匹配
                flag = true;
                break;
            }
            temp = temp.next;//向后移动
        }
        if (flag) {
            temp.next.name = node.name;
            temp.next.nickName = node.nickName;
        } else {
            System.out.printf("未查询到\t%d\t所对应的数据\n", node.no);
        }
    }

    /*
     * @Description 删除节点 根据name
     * @Author EddieZhang
     * @Date 2022/9/12 21:08
     * @Param []
     * @Return void
     * @Since version-1.0
     */
    public void deleteNode(int no) {
        //要使用到head节点 由于head节点要保留 因此使用一个零时节点
        HeroNode temp = head;
        boolean flag = false;
        while (true) {
            if (temp.next == null) {
                break;
            }
            //查到有节点
            if (temp.next.no == no) {//no是否能够匹配
                flag = true;
                break;
            }
            temp = temp.next;//向后移动
        }
        if (flag) {
            if (temp.next.next == null) {//判断是不是位于最后一个位置的节点
                temp.next = null;
            } else {
                temp.next = temp.next.next;
            }
        } else {
            System.out.printf("未查询到\t%d\t所对应的数据\n", no);
        }
    }

    /*
     * @Description 查找节点 根据name
     * @Author EddieZhang
     * @Date 2022/9/12 21:17
     * @Param [node]
     * @Return void
     * @Since version-1.0
     */
    public void selectNode(int no) {
        //先判断链表是否为空
        if (head.next == null) {
            System.out.println("链表为空");
        }
        //不为空时候 由于head节点要保留 因此需要使用一个零时节点来遍历链表
        HeroNode temp = head.next;
        while (true) {
            if (temp.no == no) {//判断是否匹配
                System.out.println(temp);
                break;
            }
            //将temp后移
            temp = temp.next;
        }
    }

    /*
     * @Description 查找倒数第n个节点
     * @Author EddieZhang
     * @Date 2022/9/12 21:44
     * @Param []
     * @Return datastructure.linkedlist.HeroNode
     * @Since version-1.0
     */
    public HeroNode searchNode(int n) {
        if (head.next == null) {
            System.out.println("列表为空");
            return null;
        }
        HeroNode temp = head;
        int num = 0;//代表第几个有效元素
        while (true) {
            if (temp.next != null) {
                num++;
                temp = temp.next;//向后移动
            } else {
                break;
            }
        }
        //此时的num表示的是最后一个元素的位置
        HeroNode temp1 = head;
        if (n < 0 || n > num) {
            System.out.println("查不到此索引位置");
            return null;
        } else {
            //倒数第n个元素的位置为(num - (n -1))
            for (int i = 1; i <= (num - (n - 1)); i++) {
                temp1 = temp1.next;
            }

        }
        return temp1;
    }

    /*
     * @Description 节点反转
     * @Author EddieZhang
     * @Date 2022/9/13 8:29
     * @Param []
     * @Return void
     * @Since version-1.0
     */
    public void reverseNode() {
        if (head.next == null || head.next.next == null) {//判断是否没有节点或者只有一个节点 则不需要反转
            System.out.println("无需反转");
        }
        HeroNode temp = head;
        HeroNode reverseHead = new HeroNode(0,null,null);
        HeroNode temp1 = reverseHead;
        while(head.next != null){
            while (temp.next.next != null){
                temp = temp.next;
            }
            //此时temp为最后一个
            temp1.next = temp.next;
            temp1 = temp1.next;
            temp.next = null;
            temp = head;
        }
        head.next = reverseHead.next;

    }

    /*
     * @Description 从尾到头 反向打印输出链表 （借助于栈【先进后出】）
     * @Author EddieZhang
     * @Date 2022/9/13 11:02
     * @Param []
     * @Return void
     * @Since version-1.0
     */
    public void reversePrint(){
        if (head.next == null){
            System.out.println("链表为空");
        }
        //创建以一个Stack结构
        Stack<HeroNode> heroNodeStack = new Stack<>();
        //遍历链表 将链表中的每一个节点压入Stack中
        HeroNode temp = head.next;
        while(temp != null){
            heroNodeStack.push(temp);
            temp = temp.next;//向后移动
        }
        while(heroNodeStack.size() > 0){
            System.out.println(heroNodeStack.pop());
        }



    }
    /*
     * @Description 将两个链表进行连接 连接后依然按照顺序排列
     * @Author EddieZhang
     * @Date 2022/9/13 11:31
     * @Param [list1, list2]
     * @Return void
     * @Since version-1.0
     */
    public static SingleLinkedList concatList(SingleLinkedList list1,SingleLinkedList list2){
        //创建一个新的链表 接收两个链表的拼接（有序）
        SingleLinkedList singleLinkedList = new SingleLinkedList();
        if(list1.head.next == null && list2.head.next == null){
            System.out.println("链表为空");
        } else if (list1.head.next == null) {
            singleLinkedList = list2;
        } else if (list2.head.next == null) {
            singleLinkedList = list1;
        }
        //如果都不为空 以其中一个list1为前段 将list2的每个节点按序加入到list1链表中
        singleLinkedList = list1;
            //遍历list2的每一个节点 并add2到list1中
        //list2要保留 创建一个零时变量
        HeroNode temp = list2.head.next;
        HeroNode tempNode = null;
        while(temp != null){
            tempNode = temp;
            list2.head.next = tempNode.next;
            tempNode.next = null;
            singleLinkedList.add2(tempNode);
            temp = list2.head.next;//向后移动
        }
        return singleLinkedList;
    }

    /*
     * @Description 求有效节点的个数
     * @Author EddieZhang
     * @Date 2022/9/12 20:53
     * @Param []链表的头节点
     * @Return int
     * @Since version-1.0
     */
    public static int numNode(HeroNode head) {
        if (head.next == null) {
            return 0;
        }
        HeroNode temp = head;
        int num = 0;
        while (temp.next != null) {
            num++;
            temp = temp.next;//向后移动
        }
        return num;
    }

    //显示链表--通过temp进行链表的遍历
    public void showList() {
        //先判断链表是否为空
        if (head.next == null) {
            System.out.println("链表为空");
        }
        //不为空时候 由于head节点要保留 因此需要使用一个零时节点来遍历链表
        HeroNode temp = head.next;
        while (true) {
            if (temp == null) {//判断是否到链表的最后
                break;
            }
            System.out.println(temp);
            //将temp后移
            temp = temp.next;
        }
    }
}

/*
 * @Description 节点设计 节点需要有数据 以及next（指向下个节点）
 * @Author EddieZhang
 * @Date 2022/9/12 17:12
 * @Since version-1.0
 */
class HeroNode {
    //数据
    int no;//标号
    String name;//名称
    String nickName;//别称
    //next
    HeroNode next;//next节点

    public HeroNode(int no, String name, String nickName) {
        this.no = no;
        this.name = name;
        this.nickName = nickName;
    }

    public HeroNode() {
    }

    @Override
    public String toString() {
        return "HeroNode{" +
                "no=" + no +
                ", name='" + name + '\'' +
                ", nickName='" + nickName + '\'' +
                '}';
    }
}
```

##### 双向链表

![image-20220916003330603](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220916003330603.png)

**双链表 可以看作是单链表的演化 多了一个prev（指向上一个）**

单向链表，**查找的方向只能是一个方向**，而双向链
 表可以向前或者向后查找。

单向链表不能自我删除，需要靠辅助节点 ，而**双向
链表，则可以自我删除**，所以前面我们单链表删除
时节点，总是找到temp,temp是待删除节点的前一
个节点(认真体会)

```java
/*
\1) 遍历 方和 单链表一样，只是可以向前，也可以向后查找

\2) 添加 (默认添加到双向链表的最后)

(1) 先找到双向链表的最后这个节点

(2) temp.next = newHeroNode

(3) newHeroNode.pre = temp;

\3) **修改** 思路和 原来的单向链表一样.

\4) **删除**

(1) 因为是双向链表，因此，我们可以实现自我删除某个节点

(2) 直接找到要删除的这个节点，比如temp

(3) temp.pre.next = temp.next

(4) temp.next.pre = temp.pre;
*/
/*
  双链表的代码演示 双链表的节点操作
*/
public class DoubleLinkedListDemo {
    public static void main(String[] args) {
        //创建几个DoubleLinkedHeroNode节点
        DoubleLinkedHeroNode node1 = new DoubleLinkedHeroNode(1, "Eddie", "张锦豪");
        DoubleLinkedHeroNode node2 = new DoubleLinkedHeroNode(2, "Irving", "欧文");
        DoubleLinkedHeroNode node3 = new DoubleLinkedHeroNode(3, "James", "詹姆斯");
        DoubleLinkedHeroNode node4 = new DoubleLinkedHeroNode(4, "Curry", "库里");
        DoubleLinkedHeroNode node5 = new DoubleLinkedHeroNode(5, "Durant", "杜兰特");
        DoubleLinkedHeroNode node6 = new DoubleLinkedHeroNode(6, "Jordan", "乔丹");
        //创建双向链表
        DoubleLinkedList doubleLinkedList = new DoubleLinkedList();
        //向链表中添加节点
        doubleLinkedList.addNode(node1);
        doubleLinkedList.addNode(node2);
        doubleLinkedList.addNode(node3);
        doubleLinkedList.addNode(node4);

        System.out.println("----------------------------------遍历链表--------------------------------------------");
        //遍历链表
        doubleLinkedList.showDoubleLinkedList();

        System.out.println("----------------------------------update节点--------------------------------------------");
        //update节点
        DoubleLinkedHeroNode node = new DoubleLinkedHeroNode(1, "EddieZhang", "张锦豪");
        doubleLinkedList.updateDoubleLinkedNode(node5);
        doubleLinkedList.showDoubleLinkedList();

        System.out.println("----------------------------------delete节点--------------------------------------------");
        //delete节点
        doubleLinkedList.deleteDoubleLinkedNode("Curry");
        doubleLinkedList.showDoubleLinkedList();

        System.out.println("----------------------------------按照no的顺序添加或插入节点--------------------------------------------");
        //按照no的顺序添加或插入节点
        DoubleLinkedList doubleLinkedList1 = new DoubleLinkedList();
        doubleLinkedList1.addNodeByNo(node1);
        doubleLinkedList1.addNodeByNo(node3);
        doubleLinkedList1.addNodeByNo(node6);
        doubleLinkedList1.addNodeByNo(node5);
        doubleLinkedList1.addNodeByNo(node2);
        doubleLinkedList1.addNodeByNo(node4);
        doubleLinkedList1.addNodeByNo(node4);
        doubleLinkedList1.showDoubleLinkedList();
    }
}

//创建一个双向链表类
class DoubleLinkedList {
    //定义一个头节点
    DoubleLinkedHeroNode headNode = new DoubleLinkedHeroNode();

    //返回头结点
    public DoubleLinkedHeroNode getHeadNode() {
        return headNode;
    }

    //向双向链表的最后添加节点
    public void addNode(DoubleLinkedHeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个临时节点
        DoubleLinkedHeroNode temp = headNode;
        //通过temp进行链表的遍历 找到最后一个节点
        while (true) {//一直寻找到最后的节点 将新的节点置为最后节点的next
            if (temp.next == null) {//说明temp以及到链表的最后了
                break;
            }
            //如果没有到最后
            temp = temp.next;//往后移动
        }
        //此时temp 已经在最后一个节点处 可以进行添加 将新的节点置为最后节点的next 新节点的prev指向原链表中的最后一个节点
        temp.next = node;
        node.prev = temp;
    }

    //向双向链表中添加节点 （按照编号的大小顺序进行添加）
    public void addNodeByNo(DoubleLinkedHeroNode node) {
        //要使用到head节点 由于head节点要保留 因此使用一个临时节点
        DoubleLinkedHeroNode temp = headNode;
        Boolean flag = false;
        while(true){
            if(temp.next == null){//判断是不是最后一个 如果是 则直接退出循环进行插入操作
                temp.next = node;
                node.prev = temp;
                break;
            }
            //有节点
            //将与链表中的所有节点进行no的比较 并进行有序的添加
            if(node.no < temp.next.no){//按照顺序需要插入在前面
                node.next = temp.next;
                temp.prev = node;
                temp.next = node;
                node.prev = temp;
                break;
            }
            if (node.no == temp.next.no){
                flag = true;
                break;
            }
            temp = temp.next;
        }
        if(flag){
            System.out.printf("节点\t %S\t已经存在 无法进行添加操作\n",node.name);
        }
    }

    //遍历双向链表
    public void showDoubleLinkedList() {
        //判断链表是否为空
        if (headNode.next == null) {//链表的头节点的next为null表明是一个空链表
            System.out.println("链表是空的哦！！");
        }
        //链表不为空时 while循环遍历链表 由于要保留头节点 所以这里定义一个临时变量用来遍历链表上的每一个节点
        DoubleLinkedHeroNode temp = headNode;
        while (temp.next != null) {
            System.out.println(temp.next);
            //temp后移
            temp = temp.next;
        }
    }

    //修改 update节点
    public void updateDoubleLinkedNode(DoubleLinkedHeroNode newNode) {
        if (headNode.next == null) {//表明链表为空
            return;
        }
        //由于头节点要保留 因此这里定义一个临时变量用来遍历所有节点
        DoubleLinkedHeroNode temp = headNode;
        boolean flag = false;//用来判断while循环有没有找到可替换节点
        //遍历链表 查看是否有可替换的节点 根据节点的no进行判断
        while (true) {
            if (temp.next == null) {//直至遍历结束未找到
                break;
            }
            if (temp.next.no == newNode.no) {//表明找到了可替换的节点 根据节点的no进行判断
                flag = true;//找到了将flag置为true
                break;//找到了就结束循环
            }
            //temp后移
            temp = temp.next;
        }
        if (flag) {//至此 flag为true时 表明找到了就是这个节点 进行update操作
            temp.next.name = newNode.name;
            temp.next.nickName = newNode.nickName;
        } else {
            System.out.println("无可替换的节点~~");
        }
    }

    //从双向链表中删除指定节点 根据name
    public void deleteDoubleLinkedNode(String name) {
        if (headNode.next == null) {//判断链表是否为空
            System.out.println("连表是空的哦~~");
            return;
        }
        //遍历链表 寻找是否有指定要删除的节点 根据name判断
        //由于头节点要保留 因此这里定义一个临时变量 用来遍历链表
        DoubleLinkedHeroNode temp = headNode.next;
        //定义一个flag用来标记是否找到要删除的节点
        boolean flag = false;
        while (true) {
            if (temp == null) {
                break;
            }
            if (name.equals(temp.name)) {//表明找到了指定要删除的节点
                flag = true;//找到了 将flag标识置为true
                break;//同时退出while循环
            }
            //temp后移
            temp = temp.next;
        }
        if (flag) {
            temp.prev.next = temp.next;//如果要删除的节点是最后一个位置上的 只执行此行即可
            if (temp.next != null) {//要删除的节点非最后一个位置上的
                temp.next.prev = temp.prev;
            }
        } else {
            System.out.println("未找到指定要删除的节点哦~~");
        }

    }
}

//创建节点类
class DoubleLinkedHeroNode {
    //数据
    int no;//标号
    String name;//名称
    String nickName;//别称
    //next
    DoubleLinkedHeroNode next;//next节点

    //previous
    DoubleLinkedHeroNode prev;//previous节点


    public DoubleLinkedHeroNode(int no, String name, String nickName) {
        this.no = no;
        this.name = name;
        this.nickName = nickName;
    }

    public DoubleLinkedHeroNode() {
    }

    @Override
    public String toString() {
        return "HeroNode{" +
                "no=" + no +
                ", name='" + name + '\'' +
                ", nickName='" + nickName + '\'' +
                '}';
    }
}

```



##### **单向环形链表**

![image-20220916120546509](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220916120546509.png)

![image-20220916120555682](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220916120555682.png)

![image-20220916120608902](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220916120608902.png)

```java
/*
构建**一个单向的环形链表思路

\1. 先创建第一个节点, 让 first 指向该节点，并形成环形

\2. 后面当我们每创建一个新的节点，就把该节点，加入到已有的环形链表中即可.



**遍历**环形链表

\1. 先让一个辅助指针(变量) curBoy，指向first节点

\2. 然后通过一个while循环遍历 该环形链表即可 curBoy.next == first 结束
*/
//代码实现 和代码演示
/** 环形链表 单向
 @author EddieZhang
 @create 2022-09-16 9:59
 */
public class CirculateSingleLinkedListDemo {
    public static void main(String[] args) {
        CirculateSingleLinkedList circulateSingleLinkedList = new CirculateSingleLinkedList();
        circulateSingleLinkedList.addBoyNode(5);
        circulateSingleLinkedList.showList();
        System.out.println("-----------------------------------约瑟夫问题（默认从firstNode节点开始）-----------------------------------------------");
        circulateSingleLinkedList.outCircle(1);

        System.out.println("-----------------------------------约瑟夫问题（Ultimately）-----------------------------------------------");
        circulateSingleLinkedList.outCircleUltimately(1,5,2);

    }
}

//创建环形链表 单向的
class CirculateSingleLinkedList {
    //创建一个First节点 当前还没有编号
    private BoyNode firstNode = null;

    //添加一个节点 构建成环形链表
    public void addBoyNode(int numNode) {//numNode为要加入多少个节点的数量
        //校验numNode
        if (numNode < 1) {
            System.out.println("numNode的值不正确");
            return;
        }
        //进行循环添加
        //由于firstNode要保留 因此利用一个临时节点
        BoyNode temp = null;
        for (int i = 1; i <= numNode; i++) {
            BoyNode boyNode = new BoyNode(i);//创建对应数量的节点
            //创建环形链表的第一个节点
            if (i == 1) {
                firstNode = boyNode;
                firstNode.setNext(firstNode);//第一个节点也要构成”环状“
                temp = firstNode;//temp指向第一个节点
            } else {
                temp.setNext(boyNode);
                boyNode.setNext(firstNode);//每一个新添加的节点 即最后的节点的next都要指向头节点 形成循环
                temp = boyNode;//从第二个开始 temp指向每一个已经新添加进链表的节点
            }
        }
    }

    //遍历循环链表
    public void showList() {
        if (firstNode == null) {//表明链表为空
            System.out.println("链表是空的哦~");
            return;
        }
        //循环遍历每一个节点
        //由于firstNode要保留 此处使用一个临时遍历
        BoyNode temp = firstNode;
        while (true) {

            if (temp.getNext() == firstNode) {//表示已经遍历到最后一个节点
                System.out.println(temp);
                break;
            }
            //有两个及以上的节点
            System.out.println(temp);
            //temp后移
            temp = temp.getNext();
        }
    }

    //约瑟夫问题 根据用户输入的num数 计算出节点出圈的顺序（默认从firstNode开始）
    public void outCircle(int num) {
        if (num < 1) {
            System.out.println("输入的数字有误~~");
            return;
        }
        if (num == 1) {//如果数字为1 就相当于遍历环形链表
            showList();
            return;
        }
        //当输入的数字>=2时 循环按照规律进行出圈
        //定义一个临时变量 为要出圈节点的前一个节点 初始为链表的最后一个节点
        BoyNode temp = new BoyNode(-1);
        temp.setNext(firstNode);//初始为链表的最后一个节点
        while (true) {
            if (firstNode.getNext() == firstNode) {//只剩下最后一个节点
                System.out.println(firstNode);
                break;
            }
            for (int i = 1; i <= num - 1; i++) {
                firstNode = firstNode.getNext();//firstNode向后移动num位
                temp = temp.getNext();//temp向后移动num位
            }
            System.out.println(firstNode);//输出出圈节点
            //进行出圈操作 此时 first节点为要出圈的节点 temp节点为要出圈的前一个节点
            firstNode = firstNode.getNext();//让firstNode为出圈节点的下一个节点
            temp.setNext(firstNode);//temp节点的下一个继续为firstNode
            //经过以上操作 待出圈的节点没有指向 等待gc回收 即为出圈
        }
    }

    //约瑟夫问题 根据用户输入的num数 计算出节点出圈的顺序（完整版本）
    /*
     * @Description
     * @Author EddieZhang
     * @Date 2022/9/16 11:15
     * @Param [startNode 从第几个节点开始, sumNode 一共有多少个节点, num 每次报数的值]
     * @Return void
     * @Since version-1.0
     */
    public void outCircleUltimately(int startNode, int sumNode, int num) {
        //进行参数的值校验
        if (startNode < 0 || startNode > sumNode || startNode < 1 || num < 1) {
            System.out.println("输入的数值有误~~");
            return;
        }
        if (firstNode == null) {
            System.out.println("链表是空的哦~~");
        }
        //定义一个零时变量 为开始节点的前一个节点//先将临时变量置为first节点再找到环形链表的最后一个节点
        BoyNode temp = firstNode;
        while (true) {
            if (temp.getNext() == firstNode) {//此时temp为链表最后一个节点
                break;
            }
            //temp后移
            temp = temp.getNext();
        }
        //根据形参列表的startNode 从第几个节点开始 将firstNode与temp节点同步向后移动 startNode - 1 位
        for (int i = 1; i <= startNode - 1; i++) {
            //firstNode与temp节点同步向后移动 startNode - 1 位
            firstNode = firstNode.getNext();
            temp = temp.getNext();
        }
        if (num == 1) {//如果数字为1 就相当于遍历环形链表
            showList();
            return;
        }
        //当输入的数字>=2时 循环按照规律进行出圈
        while (true) {
            if (firstNode.getNext() == firstNode) {//只剩下最后一个节点
                System.out.println(firstNode);
                break;
            }
            for (int i = 1; i <= num - 1; i++) {
                firstNode = firstNode.getNext();//firstNode向后移动num位
                temp = temp.getNext();//temp向后移动num位
            }
            System.out.println(firstNode);//输出出圈节点
            //进行出圈操作 此时 first节点为要出圈的节点 temp节点为要出圈的前一个节点
            firstNode = firstNode.getNext();//让firstNode为出圈节点的下一个节点
            temp.setNext(firstNode);//temp节点的下一个继续为firstNode
            //经过以上操作 待出圈的节点没有指向 等待gc回收 即为出圈
        }


    }

}


//创建节点类
class BoyNode {
    private int no;//标号
    private BoyNode next;//指向next 默认为null

    public BoyNode(int no) {
        this.no = no;
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    public BoyNode getNext() {
        return next;
    }

    public void setNext(BoyNode next) {
        this.next = next;
    }

    @Override
    public String toString() {
        return "BoyNode{" +
                "no=" + no +
                '}';
    }
}
```

##### **双向环形链表**

![image-20220916120638303](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220916120638303.png)

##### 单向链表和双向链表的对比

1. **单链表**的每一个节点中**只有指向下一个结点的指针**，**不能进行回溯**，适用于节点的增加和删除。
2. **双链表的每一个节点**给中**既有指向下一个结点的指针，也有指向上一个结点的指针**，**可以快速的找到当前节点的前一个节点**，适用于需要双向查找节点值的情况

**双链表相对于单链表的优点：** 效率较高
  删除单链表中的某个节点时，一定要得到待删除节点的前驱，得到其前驱的方法一般是在定位待删除节点的时候一路保存当前节点的前驱，这样指针的总的的移动操作为2n次，如果是用双链表，就不需要去定位前驱，所以指针的总的的移动操作为n次。
  **查找时**也是一样的，**可以用二分法的思路**，**从头节点向后和尾节点向前同时进行**，这样效率也可以提高一倍，

**双链表相对于单链表的缺点：** 占用空间较大

但是为什么市场上对于单链表的使用要超过双链表呢？从存储结构来看，**每一个双链表的节点都比单链表的节点多一个指针**，如果长度是n，就需要n*lenght（32位是4字节，64位是8字节）的**空间**，这在一些追求时间效率不高的应用下就不适用了，因为他占的空间大于单链表的1/3，所以设计者就会一时间换空间



#### 哈希表

线性表(散列) - 哈希表

散列表（Hash table，也叫哈希表），是根据关键码值(Key value)而直接进行访问的数据结构。也就是说，它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫做散列函数，存放记录的数组叫做散列表







### **Non-linear data structure**







#### 树

树结构是一种**非线性存储结构**

存储的是具有“一对多”关系的数据元素的集合

![image-20221010152028939](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152028939.png)

![image-20221010154451755](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010154451755.png)

![image-20221010152344779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152344779.png)

##### 数的常用术语

**树的结点**

![image-20221010152521242](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152521242.png)

**子树和空树**

![image-20221010152554847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152554847.png)

**结点的度和层次**

![image-20221010152659121](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152659121.png)

**有序树和无序树**

![image-20221010152815796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152815796.png)

**森林**

![image-20221010152858635](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010152858635.png)

##### 二叉树

简单地理解，满足以下两个条件的树就是二叉树：

1. 本身是有序树；
2. 树中包含的各个节点的度不能超过 2，即只能是 0、1 或者 2

![image-20221010154832862](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010154832862.png)

![image-20221010153248256](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153248256.png)

###### 二叉树的性质

![image-20221010153824257](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153824257.png)

###### 满二叉树

如果二叉树中除了叶子结点，每个结点的度都为 2，则此二叉树称为满二叉树

![image-20221010153426515](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153426515.png)

![image-20221010153758795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153758795.png)

###### 完全二叉树

如果二叉树中除去最后一层节点为满二叉树，且最后一层的结点依次从左到右分布，则此二叉树被称为完全二叉树。

![image-20221010153513599](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153513599.png)

![image-20221010153544048](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010153544048.png)

###### 遍历

![image-20230206161616281](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206161616281.png)

- 前序遍历	**先访问根节点** 再访问左节点后访问右节点	10>6>4>8>14>12>16
- 中序遍历    先访问左节点 **再访问根节点**后访问右节点    4>6>8>10>12>14>16
- 后续遍历    先访问左节点 再访问右节点**后访问根节点**    4>8>6>12>16>14>10

###### 插入

###### 删除

###### 搜索

##### 二叉搜索树(BST)

在二叉查找树中:

- 若任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
- 任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
- 任意节点的左、右子树也分别为二叉查找树。
- 没有键值相等的节点。

![image-20230206162659954](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206162659954.png)

###### 遍历

- 前序遍历	**先访问根节点** 再访问左节点后访问右节点
- 中序遍历    先访问左节点 **再访问根节点**后访问右节点
- 后续遍历    先访问左节点 再访问右节点**后访问根节点**

###### 查找

```java
/*
 * (递归实现)查找"二叉树x"中键值为key的节点
 */
private BSTNode<T> search(BSTNode<T> x, T key) {
    if (x==null)
        return x;

    int cmp = key.compareTo(x.key);
    if (cmp < 0)
        return search(x.left, key);
    else if (cmp > 0)
        return search(x.right, key);
    else
        return x;
}

public BSTNode<T> search(T key) {
    return search(mRoot, key);
}
```

```java
/*
 * (非递归实现)查找"二叉树x"中键值为key的节点
 */
private BSTNode<T> iterativeSearch(BSTNode<T> x, T key) {
    while (x!=null) {
        int cmp = key.compareTo(x.key);

        if (cmp < 0) 
            x = x.left;
        else if (cmp > 0) 
            x = x.right;
        else
            return x;
    }

    return x;
}

public BSTNode<T> iterativeSearch(T key) {
    return iterativeSearch(mRoot, key);
}
```

###### 最大值和最小值

![image-20230206202922574](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206202922574.png)

```java
/* 
 * 查找最大结点: 返回tree为根结点的二叉树的最大结点。
 */
private BSTNode<T> maximum(BSTNode<T> tree) {
    if (tree == null)
        return null;

    while(tree.right != null)
        tree = tree.right;
    return tree;
}

public T maximum() {
    BSTNode<T> p = maximum(mRoot);
    if (p != null)
        return p.key;

    return null;
}
```

```java
/* 
 * 查找最小结点: 返回tree为根结点的二叉树的最小结点。
 */
private BSTNode<T> minimum(BSTNode<T> tree) {
    if (tree == null)
        return null;

    while(tree.left != null)
        tree = tree.left;
    return tree;
}

public T minimum() {
    BSTNode<T> p = minimum(mRoot);
    if (p != null)
        return p.key;

    return null;
}
```

###### 前驱和后继

> 若要**查询x节点的前驱和后继**；可以**采用中序方式遍历树** 那么遍历后**x的前后值分别就是x的前驱和后继**

- 查找前驱节点

```java
/* 
 * 找结点(x)的前驱结点。即，查找"二叉树中数据值小于该结点"的"最大结点"。
 */
public BSTNode<T> predecessor(BSTNode<T> x) {
    // 如果x存在左孩子，则"x的前驱结点"为 "以其左孩子为根的子树的最大结点"。
    if (x.left != null)
        return maximum(x.left);

    // 如果x没有左孩子。则x有以下两种可能: 
    // (01) x是"一个右孩子"，则"x的前驱结点"为 "它的父结点"。
    // (01) x是"一个左孩子"，则要查找"x的父节点F的父节点T（同时必须F是T的右子节点）"[x的右父节点的左父节点]
    
    BSTNode<T> y = x.parent;//先找到x的右父节点y
    //若x是父节点y的左子节点 则继续向上寻找 直至找到y的左父节点（y作为其父节点的右子节点）
    while ((y!=null) && (x==y.left)) {
        x = y;
        y = y.parent;
    }
	//若x是父节点y的右子节点 则父节点y就是要找的前驱节点 返回y即可
    return y;
}
```

- 查找后继节点

```java
/* 
 * 找结点(x)的后继结点。即，查找"二叉树中数据值大于该结点"的"最小结点"。
 */
public BSTNode<T> successor(BSTNode<T> x) {
    // 如果x存在右孩子，则"x的后继结点"为 "以其右孩子为根的子树的最小结点"。
    if (x.right != null)
        return minimum(x.right);

    // 如果x没有右孩子。则x有以下两种可能: 
    // (01) x是"一个左孩子"，则"x的后继结点"为 "它的父结点"。
    // (02) x是"一个右孩子"，则要查找"x的父节点F的父节点T（同时必须F是T的左子节点）"[x的左父节点的右父节点]
    
    BSTNode<T> y = x.parent;//先找到x的左父节点y
    //若x是父节点y的右子节点 则继续向上寻找 直至找到y的右父节点（y作为其父节点的左子节点）
    while ((y!=null) && (x==y.right)) {
        x = y;
        y = y.parent;
    }
	//若x是父节点y的左子节点 则父节点y就是要找的前驱节点 返回y即可
    return y;
}
```

###### 插入

> 类似于查找 直至找到叶子节点（子节点为null的节点）；插入作为此叶子节点的子节点

![image-20230206212902519](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206212902519.png)

```java
/**
     * BST的插入节点方法
     * @param key 节点的值
     */
    public void insert(T key) {
        BSTNode<T> z=new BSTNode<T>(key,null,null,null);//根据节点的值key初始化一个节点

        // 如果新建结点失败，则返回。
        if (z != null)
            insert(this, z);//传入一个BST 以及待插入节点z
    }

    /**
     * 
     * @param bst BST
     * @param z 待插入节点
     */
    private void insert(BinarySearchTree<T> bst, BSTNode<T> z) {
        int cmp;//用于比较大小的值
        BSTNode<T> y = null;//待插入节点z的父节点（没找到z的准确位置前 初始为null）
        BSTNode<T> x = bst.mRoot;//树的顶根节点

        // 查找z的插入位置
        while (x != null) {//判断树的顶根节点是否为null
            //若不为null则顺着根节点向下寻找要插入的位置
            y = x;//y始终为待插入节点的父节点
            cmp = z.key.compareTo(x.key);
            if (cmp < 0)//待插入的z节点<x根节点 则z作为x的左子节点继续循环下顺直至到叶子节点(遇到子节点为null的节点)
                x = x.left;
            else
                x = x.right;//待插入的z节点>=x根节点 则z作为x的右子节点继续循环下顺直至到叶子节点(遇到子节点为null的节点)
        }

        //遇到子节点为null的节点 可以将待插入节点z作为此节点的子节点
        z.parent = y;//y始终为待插入节点的父节点
        if (y==null)//若y为null 表明树的顶根节点是为null 表明是棵空树
            bst.mRoot = z;//直接将待插入节点z作为该BST的根节点
        else {//判断待插入节点应当作为其父节点y的左节点还是右节点
            cmp = z.key.compareTo(y.key);
            if (cmp < 0)//作为左节点插入
                y.left = z;
            else
                y.right = z;//作为右节点插入
        }
    }
```

###### 删除(待完善)

![image-20230206213151207](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206213151207.png)

```java
/* 
 * 删除结点(z)，并返回被删除的结点
 *
 * 参数说明: 
 *     bst 二叉树
 *     z 删除的结点
 */
private BSTNode<T> remove(BSTree<T> bst, BSTNode<T> z) {
    BSTNode<T> x=null;
    BSTNode<T> y=null;

    if ((z.left == null) || (z.right == null) )
        y = z;
    else
        y = successor(z);

    if (y.left != null)
        x = y.left;
    else
        x = y.right;

    if (x != null)
        x.parent = y.parent;

    if (y.parent == null)
        bst.mRoot = x;
    else if (y == y.parent.left)
        y.parent.left = x;
    else
        y.parent.right = x;

    if (y != z) 
        z.key = y.key;

    return y;
}

/* 
 * 删除结点(z)，并返回被删除的结点
 *
 * 参数说明: 
 *     tree 二叉树的根结点
 *     z 删除的结点
 */
public void remove(T key) {
    BSTNode<T> z, node; 

    if ((z = search(mRoot, key)) != null)
        if ( (node = remove(this, z)) != null)
            node = null;
}
```



#### 堆

#### 图

## Algorithm

### 排序

![image-20220921083214246](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220921083214246.png)

**排序也称为排序算法（SortAlgorithm），排序是将一组数据，依指定的顺序进行排列的过程**

**稳定** ：如果a原本在b前面，而a=b，排序之后a仍然在b的前面；
**不稳定** ：如果a原本在b的前面，而a=b，排序之后a可能会出现在b的后面；
**内排序** ：所有排序操作都在内存中完成；
**外排序** ：由于数据太大，因此把数据放在磁盘中，而排序通过磁盘和内存的数据传输才能进行；
**时间复杂度** ： 一个算法执行所耗费的时间。
**空间复杂度** ：运行完一个程序所需内存的大小

![image-20220921083118233](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220921083118233.png)

- 图片名词解释：
  - n: 数据规模
  - k: “桶”的个数
  - In-place: 占用常数内存，不占用额外内存
  - Out-place: 占用额外内存

比较和非比较的区别

**常见的快速排序、归并排序、堆排序、冒泡排序 等属于比较排序** 。在排序的最终结果里，**元素之间的次序依赖于它们之间的比较**。每个数都必须和其他数进行比较，才能确定自己的位置 。

在冒泡排序之类的排序中，问题规模为n，又因为需要比较n次，所以平均时间复杂度为O(n²)。在归并排序、快速排序之类的排序中，问题规模通过分治法消减为logN次，所以时间复杂度平均O(nlogn)。

**比较排序的优势**是，**适用于各种规模的数据**，也不在乎数据的分布，都能进行排序。可以说，**比较排序适用于一切需要排序的情况**。

**计数排序、基数排序、桶排序则属于非比较排序** 。非比较排序是通过确定每个元素之前，应该有多少个元素来排序。针对数组arr，计算arr[i]之前有多少个元素，则唯一确定了arr[i]在排序后数组中的位置 。

非比较排序只要确定每个元素之前的已有的元素个数即可，所以一次遍历即可解决。算法时间复杂度O(n)。

**非比较排序时间复杂度底**，但由于非比较排序需要占用空间来确定唯一位置。所以**对数据规模和数据分布有一定的要求**

#### 内部排序★

##### 插入排序

###### 直接插入排序

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvODQ5NTg5LzIwMTcxMC84NDk1ODktMjAxNzEwMTUyMjU2NDUyNzctMTE1MTEwMDAwMC5naWY)

**插入排序法思想:**

插入排序（Insertion Sorting）的**基本思想**是：把n个待排序的元素看成为**一个有序表**和**一个无序表**，**开始时有序表中只包含一个元素(索引为0的元素)**，**无序表中包含有n-1个元素**，排序过程中**每次从无序表中取出第一个元素**，把它的排序码**依次与有序表元素的排序码进行比较**，将它**插入到有序表中的适当位置**，使之**成为新的有序表**

```java
/**
 * 插入排序
 */
public class InsertionSort {
    @Test
    public void test1() {
        int[] nums = new int[]{-5, -8, -6, 8, -5, 9, -45, 6, 45, 91, 2, -9, 2, -8};
        //默认将数组分为两端 一段为有序（开始时默认第一个元素为有序） 一段为未排序

        for (int i = 0; i < nums.length - 1; i++) {//外层从无序段开始遍历每一个未排序的元素有序的插入到有序段
            int preNum = i;//有序段的最后一个元素的索引位置
            int current = nums[i + 1];//记录无序段的要插入的元素
            //无序段的要插入元素要与有序段从最后一个开始到有序段的第一个的每一个元素进行比较
            while (preNum >= 0 && nums[preNum] > current) {//如果有序段的元素>要插入的元素就后移
                nums[preNum + 1] = nums[preNum];
                preNum--;//有序段元素的前一个 直至第一个为止
            }
            //退出while循环表明待插入元素遇到不大于的了 即将待插入元素置于遇到的不大于的元素后一位
            nums[preNum + 1] = current;
        }
        for (int num :
                nums) {
            System.out.println(num);
        }
    }

}
```

###### 希尔排序

**又称为缩小增量排序**

**希尔排序法基本思想**

希尔排序是把记录按下标的一定增量分组，对每组使用直接插入排序算法排序；随着增量逐渐减少，每组包含的关键词越来越多，当增量减至1时，整个文件恰被分成一组，算法便终止

![image-20220921154433986](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220921154433986.png)


##### 选择排序

```java
//希尔排序
@Test
public void test2(){
    int[] nums = new int[]{-12, 56, 25, 98, 33, -65, 1, 3, 4, 6, -5, -999, 15, 2, 25, 33, 17};
    int gap = nums.length;//增量
    while(true){
        gap = gap >> 1;//增量每次逐渐减少为原来的二分之一
        //根据增量进行分组
        for(int i = 0;i < gap;i++){

            //对每组进行插入排序
            for (int j = i; j < nums.length - gap; j += gap) {
                int preNum = j;//有序段的末尾元素的索引
                int current = nums[j + gap];//待插入的元素值 位于有序段的末尾元素的后gap个
                while(preNum >= i && nums[preNum] > current){
                    nums[preNum + gap] = nums[preNum];
                    preNum -= gap;
                }
                nums[preNum + gap] = current;
            }
        }
        if(gap == 1){
            break;
        }
    }
    for (int num :
            nums) {
        System.out.println(num);
    }
}
```

###### 简单选择排序

![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvODQ5NTg5LzIwMTcxMC84NDk1ODktMjAxNzEwMTUyMjQ3MTk1OTAtMTQzMzIxOTgyNC5naWY)
  选择排序 是表现最稳定的排序算法之一 ，因为无论什么数据进去都是O(n2)的时间复杂度 ，所以用到它的时候，数据规模越小越好。唯一的好处可能就是不占用额外的内存空间了吧。理论上讲，选择排序可能也是平时排序一般人想到的最多的排序方法了吧。

选择排序(Selection-sort) 是一种简单直观的排序算法。它的工作原理：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕

理解为： 每个循环选择第几小的数 放在第几个索引位置上

```java
/**
 * 选择排序
 */
public class SelectionSort {
    @Test
    public void test1(){
        int [] nums = new int[]{-5,-89,-6,-8,5,9,45,6,-596,-456,888,-6,9};
        for (int i = 0; i < nums.length; i++) {//外层循坏 每次循环选择出第i小的数 然后放在第i位 后续类推
        int minIndex = i;//记录每次比较的最小值索引位置
            for (int j = i; j < nums.length; j++) {//内层循环 遍历每次循环中出第i小的数的索引位置
                if(nums[j] < nums[minIndex]){
                    minIndex = j;//最小数的索引
                }

            }
            //将第i小的数 放在i的索引位置上
            int temp = nums[minIndex];
            nums[minIndex] = nums[i];
            nums[i] = temp;
        }
        for (int num :
                nums) {
            System.out.println(num);
        }
    }
}
```

###### 堆排序

##### 交换排序

###### 冒泡排序

![img](https://img-blog.csdnimg.cn/20210611113132421.gif#pic_center)
冒泡排序的原理：
每一趟只能确定将一个数归位。即第一趟只能确定将末位上的数归位，第二趟只能将倒数第 2 位上的数归位，依次类推下去。如果有 n 个数进行排序，只需将 n-1 个数归位，也就是要进行 n-1 趟操作。

而 “每一趟 ” 都需要从第一位开始进行相邻的两个数的比较，将较大的数放后面，比较完毕之后向后挪一位继续比较下面两个相邻的两个数大小关系，重复此步骤，直到最后一个还没归位的数

![image-20220921104005078](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220921104005078.png)

```java
/**
 * 冒泡排序
 */
public class BubbleSort {
    @Test
    public void test1() {
        //冒泡排序 代码原始版
        int[] numbers = new int[]{-9, -8, -7, -6, -5, -4, -3, -2, 1, 5, 6, 8};
        int count = 0;
        for (int i = 0; i < numbers.length - 1; i++) {//大循环一共执行数组的长度 - 1 次
            for (int j = 0; j < numbers.length - 1 - i; j++) {//小循环在每个大循环中一共执行（数组长度 - 1 - i（确定最大的个数））次
                if (numbers[j] > numbers[j + 1]) {
                    int temp = numbers[j];
                    numbers[j] = numbers[j + 1];
                    numbers[j + 1] = temp;
                }
                count++;
            }
        }
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
        System.out.println("count = " + count);//count = 66 需要进行优化 若在一次循环中发现并未发生交换 则表明数组已有序 直接退出循环
    }

    @Test
    public void test2() {
        //冒泡排序 代码优化版
        int[] nums = new int[]{-9, -8, -7, -6, -5, -4, -3, -2, 1, 5, 6, 8};
        int count1 = 0;
        for (int i = 0; i < nums.length - 1; i++) {
            boolean flag = true;//每一个次大循环 的标记为true
            for (int j = 0; j < nums.length - 1 - i; j++) {
                if (nums[j] > nums[j + 1]) {
                    int temp1 = nums[j];
                    nums[j] = nums[j + 1];
                    nums[j + 1] = temp1;
                    count1++;
                    flag = false;//如果本次大循环有交换就将 标记改为false 表明继续下一个大循环
                }
            }
            if (flag) {
                break; 
            }
        }
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
        System.out.println("count1 = " + count1);//0
    }

    @Test
    public void test3() {
        //冒泡排序 代码最终版
        int[] nums = new int[]{-5, 5, 1, -5, -95, 1, 2, 3, 4, 5, 6};//前段为乱序 需要进行交换 后端为有序 无需再进行交换
        int count = 0;
        int theLastChangeIndex = 0;//记录最后一次交换的索引位置 用来确定有序区的范围
        int sortBorder = nums.length - 1;//无序数列的边界，每次比较只需要比到这里为止
        for (int i = 0; i < nums.length - 1; i++) {
            boolean flag = true;//每一个次大循环 的标记为true
            for (int j = 0; j < sortBorder; j++) {//只需遍历无序区
                if (nums[j] > nums[j + 1]) {
                    flag = false;
                    int temp = nums[j];
                    nums[j] = nums[j + 1];
                    nums[j + 1] = temp;
                    count++;
                    theLastChangeIndex = j;
                }
            }
            sortBorder = theLastChangeIndex;//根据最后一次交换的索引位置 确定有序区的范围
            if (flag) {
                break;
            }
        }
        for (int i = 0; i < nums.length; i++) {
            System.out.println(nums[i]);
        }
        System.out.println("count = " + count);
    }
}
```

###### 快速排序

快速排序 的基本思想：通过一趟排序将待排记录分隔成独立的两部分，其中一部分记录的关键字均比另一部分的关键字小，则可分别对这两部分记录继续进行排序，以达到整个序列有序。

算法描述

快速排序使用分治法来把一个串（list）分为两个子串（sub-lists）。具体算法描述如下：
步骤1：从数列中挑出一个元素，称为 “基准”（pivot ）；
步骤2：重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作；
步骤3：递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序
**演示**

在初始状态下，数字6在序列的第1位。我们的目标是将6挪到序列中间的某个位置，假设这个位置是k kk。现在就需要寻找这个k kk，并且以第k位为分界点，左边的数都≤ 6 \le6≤6，右边的数都≥ 6 \ge6≥6。那么如何找到这个位置k kk呢？

我们要知道，快速排序其实是冒泡排序的一种改进，冒泡排序每次对相邻的两个数进行比较，这显然是一种比较浪费时间的。

而快速排序是分别从两端开始”探测”的，先从右往左找一个小于6的数，再从左往右找一个大于6的数，然后交换他们。这里可以用两个变量i ii和j jj，分别指向序列最左边和最右边。我们为这两个变量起个好听的名字“哨兵i ii”和“哨兵j jj”。刚开始的时候让哨兵i ii指向序列的最左边，指向数字6。让哨兵j jj指向序列的最右边，指向数字8

![image-20220922000526112](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922000526112.png)
![image-20220922000727151](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922000727151.png)
![image-20220922000740177](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922000740177.png)
![image-20220922000749602](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922000749602.png)
![image-20220922000758293](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220922000758293.png)

```java
/**
 * 快速排序
 */
public class QuickSort {
    @Test
    public void test1(){
        int[] nums = new int[]{-12, 56, 25, 98, 33, -65, 1, 3, 4, 6, -5, -999, 15, 2, 25, 33, 17};
        sort(nums,0, nums.length - 1);
        for (int num :
                nums) {
            System.out.println(num);
        }

    }

//快速排序
    public void sort(int[] array, int left, int right) {
        if (right < left) {
            return;
        }
        int temp = array[left];//基准 默认为 数组的第一个元素
        int leftIndex = left;
        int rightIndex = right;


        //寻找 基准的准确索引位置 通过 左 右 指针 分别向数组中间移动寻找
            //最右边的指针向左遍历 发现是大于等于基准的元素 就继续向左移
                //发现小于基准的元素 就赋给最左边指针所在索引位置
            //最左边的指针向右遍历 发现是小于等于基准的元素 就继续向左移
                //发现小于基准的元素 就赋给最右边的指针所在位置
        //直至 左 右 指针 相遇处 即基准的准确索引位置
        //应该以上操作 保证基准元素的左侧都是小于等于基准的 右侧都是大于等于基准的

        while(leftIndex != rightIndex){//while循环结束表明 左 右 指针 相遇处 即基准的准确索引位置
            //由于定的基准在最左侧 因此要从最右侧开始先

        while (leftIndex < rightIndex && array[rightIndex] >= temp) {//右边指针
            //最右边的指针向左遍历 发现是大于等于基准的元素 就继续向左移
            rightIndex--;
        }//发现小于基准的元素 就赋给最左边指针所在索引位置
        array[leftIndex] = array[rightIndex];

        while(leftIndex < rightIndex && array[leftIndex] <= temp){//左边指针
            leftIndex++;//最左边的指针向右遍历 发现是小于等于基准的元素 就继续向左移
        }//发现小于基准的元素 就赋给最右边的指针所在位置
        array[rightIndex] = array[leftIndex];
        }

        //while循环结束表明 左 右 指针 相遇处 即基准的准确索引位置
        //将基准赋值在准确的索引位置上
        array[leftIndex] = temp;

        //至此 第一轮找到整个数组的基准准确位置 基准的左侧均为小于等于的值 右侧均为大于等于的值
        //递归调用 对基准的左侧和右侧进行同上操作
        sort1(array,left, leftIndex- 1);//基准的左侧
        sort1(array,leftIndex + 1,right);//基准的右侧
    }
```

##### 归并排序

![image-20220923132350182](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923132350182.png)

 **归并排序** 是建立在**归并操作**上的一种有效的排序算法。该算法是采用**分治法（Divide and Conquer）**的一个非常典型的应用。归并排序是一种稳定的排序方法。将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为2-路归并

![image-20220923135256769](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923135256769.png)
**合并原理：**
首先要有一个临时数组temp 以及2个索引分别指向2个数组的首地址 让2个索引对应的值进行比较 谁对应的值小 把值小的放入temp 然后当前索引++ 再循环比较 肯定会有一个数组索引先到头 在对另一个数组剩下的元素遍历放入temp即可

然后再把合并好的数组放会原数组对应的为止 就算完成此次合并

以 {3,4,6,10} {2,5,7,8} 为例作图给大家演示下：

两个数组索引对应的值进行比较 小的放进临时数组 索引++ 然后继续比较

![image-20220923223827614](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923223827614.png)
此时 其中一个数组索引已经到头了 然后直接对另一个数组剩余元素进行遍历放入temp即可

可能有些童鞋会有疑问为什么剩下的直接放进去就行？

因为2个数组都是有序数组 此数组当前索引对应的值比另一个数组最大值都大 此数组剩余元素值肯定大于另一个数组而且还是从小到大排列的 所以直接放入temp

![image-20220923223932104](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923223932104.png)

```java
/**
 * 归并排序
 */
public class MergeSort {
    public static void main(String[] args) {
        int[] array = new int[]{5, 1, 3, 7, 11, 2, 52, 9};
        int[] temp = new int[array.length];
        MergeSort mergeSort = new MergeSort();
        mergeSort.mergingSort(array, 0, array.length - 1, temp);
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }

    public void mergingSort(int[] beforeArray, int left, int right, int[] tempArray) {
        if (left == right) {//当划分到一个元素一组时就结束递归
            return;
        }
        //将原数组进行递归划分 将数组划分为左右两段
        int mid = (left + right) / 2;//mid为数组的中线 左段的最后一个元素
        //进行左段的递归划分
        mergingSort(beforeArray, left, mid, tempArray);
        //进行右段的递归划分
        mergingSort(beforeArray, mid + 1, right, tempArray);

        //将划分的数组进行排序合并
        merge(beforeArray, left, mid, right, tempArray);

    }

    //将划分的数组进行排序合并
    public void merge(int[] array, int left, int mid, int right, int[] temp) {
        int l0 = left;//指向左段首元素索引的指针
        int r0 = mid + 1;//指向右段首元素索引的指针
        int temp0 = 0;//指向temp数组首元素索引的指针
        //进行排序合并
        while (l0 <= mid && r0 <= right) {
            if (array[l0] < array[r0]) {
                temp[temp0++] = array[l0++];
            } else {
                temp[temp0++] = array[r0++];
            }
        }
        //如果左段已经排序完毕 而右段仍有元素 则将有段的剩余元素依次放入temp数组中
        while (r0 <= right) {
            temp[temp0++] = array[r0++];
        }
        //如果右段已经排序完毕 而左段仍有元素 则将左段的剩余元素依次放入temp数组中
        while (l0 <= mid) {
            temp[temp0++] = array[l0++];
        }

        //将temp中的元素copy至原数组中
        temp0 = 0;
        int tempLeft = left;
        while (tempLeft <= right) {
            array[tempLeft] = temp[temp0];
            temp0 += 1;
            tempLeft += 1;
        }
    }
}
```

##### 基数排序

#### 外部排序

### 双指针

### 查找

#### 线性查找

**不要求有序**

**线性查找又称顺序查找，是一种最简单的查找方法，它的基本思想是从第一个记录开始，逐个比较记录的关键字，直到和给定的K值相等，则查找成功；若比较结果与文件中n个记录的关键字都不等，则查找失败**

```java
/**
 * 线性查找
 * 遍历数组按照下标进行查找 找到就返回该元素的索引 找不到就返回-1
 */
public class SeqSearchTest {
    public static void main(String[] args) {
        int[] nums = new int[]{12,56,21,12,55,6484,12,3,0};
        SeqSearchTest seqSearchTest = new SeqSearchTest();
        ArrayList arrayList = seqSearchTest.seqSearch(nums, 1000);
        if(arrayList.get(0).equals(-1)){
            System.out.println("数组中未查询到value哦~");
        }else {
        System.out.println("数值在数组中的索引位置为:" + arrayList.toString());
        }


    }
    //查找指定的数 找到就返回在数组中的索引位置 找不到就返回-1
    public ArrayList seqSearch(int [] nums, int values){
        ArrayList arrayList = new ArrayList();
        for (int i = 0; i < nums.length; i++) {
            if(values == nums[i]){
                arrayList.add(i);
            }

        }
        if (arrayList.isEmpty()){
            arrayList.add(-1);
        }
        return arrayList;

    }

}
```

#### 二分查找

**前提是有序的**

二分查找也称为折半查找，**每次都能将查找区间减半** 先判断目标在中间界限的左边还是右边 每次能排除一半的范围

二分查找算法的具体实现过程为：
\1) 初始状态下，搜索区域是整个序列。找到搜索区域内的中间元素。指定区域内中间元素的位置可以套用如下公式求出：

**Mid = ⌊ Begin + (End - Begin) / 2 ⌋**

**关键是找到中间界限 公式：int mid = (right - left) / 2 + left;**

![image-20221010110701146](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110701146.png)

> End 表示搜索区域内最后一个元素所在位置，Begin 表示搜索区域内第一个元素所在的位置，Mid 表示中间元素所在的位置。

图 1 中，所有元素的位置分别用 0~9 表示，中间元素的位置为 ⌊ 0 + (9 - 0) / 2 ⌋ = 4，如下图所示：



![image-20221010110050297](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110050297.png)


中间元素 27 < 31，可以断定 [0, 4] 区域内绝对没有 31，目标元素只可能位于 [5, 9] 区域内，如下图所示：

![image-20221010110114327](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110114327.png)


\2) 在 [5, 9] 区域内，中间元素的位置为 ⌊ 5 + (9 - 5) / 2 ⌋ = 7，如下图所示：

![image-20221010110127995](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110127995.png)


中间元素 35 > 31，可以断定 [7, 9] 区域内绝对没有 31，目标元素只可能位于 [5,6] 中，如下图所示：

![image-20221010110138115](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110138115.png)


\3) 在 [5, 6] 区域内，中间元素的位置为 ⌊ 5 + (6- 5) / 2 ⌋ = 5，中间元素就是 31，成功找到目标元素。

```java
/**
 * 二分查找算法
 * 思路 对有序数组进行二分法查找
 * 将数组分成左右两段 中间值为key 如果要找的值为key就直接返回 如果要找的值小于key 就在左边进行遍历查找 如果要找的值大于key就在右边进行遍历查找
 * 左端和右段可以继续按照上诉情况继续进行二分查找
 * 当全部遍历完成后未发现有值是和要找的值相等的 就返回-1表明找不到
 */
public class BinarySearch {
    public static void main(String[] args) {
        int[] nums = new int[]{1,2,3,4,5,6,7,8,9};
        BinarySearch binarySearch = new BinarySearch();
        System.out.println(binarySearch.binarySearch(nums, 0, nums.length - 1, 10));
        System.out.println(binarySearch.binarySearch(nums, 6));
    }

    //递归方法
    public int binarySearch(int [] nums,int left,int right,int value){
        if(left > right){
            return -1;
        }

        int mid = (left + right)/2;
        if(nums[mid] == value){
            return mid;
        }else if(value < nums[mid]){
            return binarySearch(nums,left,mid - 1,value);
        }else {
            return binarySearch(nums,mid + 1,right,value);
        }
    }

    //非递归
    public int binarySearch(int [] nums,int value){
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] == value){
                return mid;
            } else if (nums[mid] < value) {
                left = mid + 1;
            }else {
                right = mid - 1;
            }
        }
        return -1;
    }

}

/**
     * 二分查找算法优化
     * 查找有序数组中指定值的位置 所有的值
     * 返回结果在一个集合中
     */
    @Test
    public void test2() {
        int[] nums = new int[]{1, 2, 3, 4, 5, 6, 7,7,7,7,7,8, 9};
        List<Integer> integers = BinarySearch2(nums, 7);
        System.out.println(integers);


    }

    /**
     *
     * @param nums 一个有序数组
     * @param target 指定要查找的值
     * @return 返回查找到的所有的值的位置 返回一个List集合中
     */
    public List<Integer> BinarySearch2(int[] nums, int target) {
        int left = 0;//数组的左边界
        int right = nums.length - 1;//数组的右边界
        List<Integer> list = new ArrayList<>();
        while (left <= right) {
            int middle = (right - left) / 2 + left;//将数组进行二分的中间界
            if (target < nums[middle]) {//如果目标在中间界的左边 则将数组的右边界更新为中间界-1
                right = middle - 1;
            } else if (target > nums[middle]) {//如果目标在中简界的右边 则将数组的左边界更新为中间界+1
                left = middle + 1;
            } else {//表明找到了
                //目标也许不止一个 找到一个后继续进行左右的搜索 找到所有的
                //向左边搜索
                int temp = middle - 1;
                while(true){
                    if (temp < left || nums[temp] != target){
                        break;
                    }else {
                        list.add(temp);
                        temp-=1;
                    }
                }
                list.add(middle);
                //向右边搜索
                int temp1 = middle + 1;
                while(true){
                    if(temp1 > right || nums[temp1] != target){
                        break;
                    }else {
                        list.add(temp1);
                        temp1+=1;
                    }
                }
                return list;
            }
        }
        list.add(-1);
        return list;
    }
```

#### 插值查找

插值查找算法又称插值搜索算法，是在**二分查找算法的基础上改进**得到的一种查找算法

**前提是有序的** **针对于均匀分布的序列插值查找效率优于二分查找**

插值查找算法只适用于有序序列，换句话说，它只能在升序序列或者降序序列中查找目标元素。作为“改进版”的二分查找算法，当有序序列中的元素呈现均匀分布时，插值查找算法的查找效率要优于二分查找算法；反之，**如果有序序列不满足均匀分布的特征，插值查找算法的查找效率不如二分查找算法**

![image-20221010105751433](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010105751433.png)

**关键点是中间界限的查找公式:**

![image-20221010110707763](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010110707763.png)

```java
int left = 0;
int right = nums.length - 1;
//中间界限
int mid = left + (right - left) * (target - nums[left]) / (nums[right] - nums[left]);
```

```java
public class InterpolationSearch {

    /**
     * 插值插值
     * 相对于二分查找的改变
     * 前提是有序的序列 对于分布均匀的序列 使用插值插值效率优于二分查找 反之
     * 查找思路与二分查找相同 关键点在于求中间界限的公式不同
     * int mid = left + (right - left) * (target - nums[left]) / (nums[right] - nums[left]);
     */
    @Test
    public void test1() {
        int[] nums = new int[100];
        for (int i = 0; i < nums.length; i++) {
            nums[i] = i + 1;
        }
        int search = search(nums, 100);
        System.out.println(search);
    }

    public static int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        if (target < nums[left] || target > nums[right]) {
            return -1;
        }
        while (left <= right) {
            int mid = left + (right - left) * (target - nums[left]) / (nums[right] - nums[left]);
            if (target < nums[mid]) {
                right = mid - 1;
            } else if (target > nums[mid]) {
                left = mid + 1;
            } else {
                return mid;
            }
        }
        return -1;
    }

}
```

#### 斐波那契查找

斐波那契查找同样是查找算法家族中的一员，**它要求数据是有序的**（升序或降序）。斐波那契查找采用和[二分查找](https://so.csdn.net/so/search?q=二分查找&spm=1001.2101.3001.7020)/插值查找相似的区间分割策略，都是通过**不断的分割区间缩小搜索的范围**

斐波那契查找就是在**二分查找的基础上**根据斐波那契额列进行分割的

在数学上，斐波那契数列被以如下递推的方法定义

![image-20221010145826960](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221010145826960.png)

### 分治

### 动态规划

### 递归

递归就是方法**自己调用自己**,每次调用时传入不同的变量.递归有助于编程者解决复杂的问题,同时可以让代码变得简洁

**递归必须具备两个条件:**①**调用自己**	②**有终止条件**（并且**终止条件必须是在递归最开始的地方**）



```java
//递归模板
public void recursion(参数0) {
    if (终止条件) {//②**有终止条件**（并且**终止条件必须是在递归最开始的地方**）
        return;
    }
	可能有一些逻辑运算
	recursion(参数1)//①**调用自己**
	可能有一些逻辑运算
	recursion(参数2)
        ……
	recursion(参数n)
	可能有一些逻辑运算
}
```
**对递归的理解**是**先往下一层层传递**，**当碰到终止条件的时候会反弹**，**最终会反弹到调用处**

![image-20220910170719265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910170719265.png)



![image-20220910145236820](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910145236820.png)

**实例分析**--**斐波那契数列**

```java
//斐波那契数列fibonacci
//1,1,2,3,5,8,13……
public int fibonacci(int n) {
    if (n == 1 || n == 2)//终止条件
        return 1;
    return fibonacci(n - 1) + fibonacci(n - 2);//调用自己
}

```



### 回溯

### 贪心

### 位运算

### DFS

### BFS

### 图