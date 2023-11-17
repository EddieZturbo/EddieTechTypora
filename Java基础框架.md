

# Java Start

## 软件开发介绍

###  软件开发

软件，即一系列按照特定顺序组织的计算机数据和指令的集合。有系统软 件和应用软件之分。

#### 系统软件

#### 应用软件

### 人机交互方式

 图形化界面(Graphical User Interface GUI)这种方式简单直观，使用 者易于接受，容易上手操作。 

 命令行方式(Command Line Interface CLI)：需要有一个控制台，输 入特定的指令，让计算机完成一些操作。较为麻烦，需要记录住一些 命令。

Algorithms+Data structures=programs
算法+数据结构=应用程序
算法解决应用程序运行正确与否的问题
数据结构解决的是运行效率的问题

#### 图形化界面

#### 命令行方式

### 常用的DOS命令与快捷键

常用命令

**dir** : 列出当前目录下的文件以及文件夹 
**md** : 创建目录 rd : 删除目录 
**cd** : 进入指定目录
**cd..** : 退回到上一级目录 
**cd\**: 退回到根目录 
**del** : 删除文件 exit : 退出 dos 命令行 
 补充：echo javase>1.doc 

常用快捷键

 ← →：移动光标  ↑ ↓：调阅历史操作命令  Delete和Backspace：删除字符

## 计算机编程语言介绍

#### 第一代语言

 机器语言。指令以二进制代码形式存在。

#### 第二代语言

 汇编语言。使用助记符表示一条机器指令。

<img src="https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708220325990.png" alt="image-20220708220325990" style="zoom: 50%;" />

####  第三代语言：高级语言

C、Pascal、Fortran面向过程的语言
C++面向过程/面向对象
Java跨平台的纯面向对象的语言
.NET跨语言的平台
Python、Scala…







## Java语言概述

![image-20220723094937502](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723094937502.png)

#### Java语言特性

##### 面向对象

两个基本概念：类    对象
三大特性：  封装   继承   多态

##### 健壮性

吸收了C/C++语言的优点，但去掉了其影响程序健壮性的部分（如指针、内存的申请与
释放等），提供了一个相对安全的内存管理和访问机制

##### 跨平台性

![image-20230401003103996](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401003103996.png)

![image-20220708221148579](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221148579.png)

JVM（Java virtual machine）

![image-20220708220923951](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708220923951.png)

#### Java应用领域

![image-20220708221307699](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221307699.png)

##### 企业级应用

##### Android平台应用

##### 大数据开发

##### 移动领域应用

#### Java体系

![image-20220708221238425](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221238425.png)

##### Java  SE（Java Standard Edition）

##### Java  EE（Java Enterprise Edition）

##### Java  ME（Java Micro Edition）

##### Java  Card

#### Java两种核心机制及运行过程

##### Java虚拟机 (Java Virtal Machine) 

![image-20220708221343351](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221343351.png)

##### 垃圾收集机制 (Garbage Collection)

![image-20220708221458746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221458746.png)

##### 运行过程

![image-20220708221447505](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221447505.png)

#### Java语言的环境搭建

![image-20230401002143691](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230401002143691.png)

![image-20220708221756978](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221756978.png)

![image-20220708221643689](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221643689.png)

<img src="https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221815045.png" alt="image-20220708221815045" style="zoom: 80%;" />

![image-20220708221954636](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221954636.png)

![image-20220708221853749](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221853749.png)

![image-20220708221908539](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221908539.png)

![image-20220708221923080](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708221923080.png)

#### Java开发工具

![image-20220708222018033](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222018033.png)

#### Java注释

![image-20220708222116489](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222116489.png)

#####  单行注释 

格式： //注释文字

#####  多行注释 

格式：

 /* 

注释文字

 */

#####  文档注释 (java特有)

对于单行和多行注释，被注释的文字，不会被JVM（java虚拟机）解释执行。

多行注释里面不允许有多行注释嵌套。

![image-20220708222239305](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222239305.png)

#### Java API文档

API（Application Programming Interface,应用程序编程接口）

![image-20220708222404773](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222404773.png)







#### 开发体验 —HelloWorld

![image-20220708222900811](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222900811.png)

![image-20230408002625058](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230408002625058.png)

![image-20220708222719654](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222719654.png)

![image-20220708222754147](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222754147.png)

##### 编写

 步骤一：编写  选择最简单的编辑器：记 事本。  敲入代码 class Test{ } 将文件保存成Test.java，这个 文件是存放java代码的文件， 称为源文件。

##### 编译

 步骤二：编译  有了java源文件，通过编译器将其编译成JVM可以识别的字节码文件。 

 在该源文件目录下，通过javac编译工具对Test.java文件进行编译。 

 如果程序没有错误，没有任何提示，但在当前目录下会出现一个Test.class文 件，该文件称为字节码文件，也是可以执行的java的程序。

##### 运行

 步骤三：运行 

 有了可执行的java程序(Test.class字节码文件) 

 通过运行工具java.exe对字节码文件进行执行。 

 出现提示：缺少一个名称为main的方法。 

 因为一个程序的执行需要一个起始点或者入口，所以在Test类中的加入public static void  main(String[] args){ } 

 对修改后的Test.java源文件需要重新编译，生成新的class文件后，再进行执行。 

 发现没有编译失败，但也没有任何效果，因为并没有告诉JVM要帮我们做什么事情，也就是 没有可以具体执行的语句。 

 想要和JVM来个互动，只要在main方法中加入一句System.out.println(“Hello World");因为程 序进行改动，所以再重新编译，运行即可。

#### 常见问题及解决方法

总结： 学习编程最容易犯的错是语法错误。Java要求你必须按照语法规则编写代码。 如果你的程序违反了语法规则，例如：忘记了分号、大括号、引号，或者拼 错了单词，java编译器都会报语法错误。尝试着去看懂编译器会报告的错误 信息。

![image-20220708222931058](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708222931058.png)

#### 良好的编程风格

#####  正确的注释和注释风格

 使用文档注释来注释整个类或整个方法。  如果注释方法中的某一个步骤，使用单行或多行注释。

#####  正确的缩进和空白

 使用一次tab操作，实现缩进  运算符两边习惯性各加一个空格。比如：2 + 4 * 5。

#####  块的风格

 Java API 源代码选择了行尾风格

![image-20220708223117405](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708223117405.png)

# Java编程规则&规范

## 良好的编程风格

编程是一门技术，更加是一门艺术 ，不能只满足于写完代码运行结果正确就完事，

时常考虑如何让代码更加**简练**，更加**容易维护**，容易**扩展**和**复用**

## 规范命名 “见名知意”

### 标识符命名规则&规范

#### 规则

![image-20220708223826873](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708223826873.png)

不遵守 编译无法通过

#### 规范

![image-20220708223835568](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708223835568.png)

不遵守 编译可以通过

### 关键字和保留字

![image-20220708223852517](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220708223852517.png)

























# 基础语法（Java语言基础）★

![image-20220723094829271](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723094829271.png)



## 变量与常量

### 标识符

#### 定义：

标识符可以简单的理解为一个名字，用来标识的字符序列

#### 规范：

![image-20220723095517458](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723095517458.png)
![image-20220723095539103](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723095539103.png)

### 关键字

#### 定义：

keyword

被Java语言赋予了特殊含义，用做专门用途的字符串（单词）

#### 特点：

关键字中的所有字母都是小写的

### 保留字

保留字（reserve word）
 goto； const；
 Java保留字：现有Java版本尚未使用，但以后版本可能作为关键字使用，自己命名标识符时要避免使用这些保留字

### 变量

按照数据类型分类 **①基本数据类型** **②引用数据类型**

按照声明位置分类 

**①成员变量 可以不用显示赋值 有系统默认初始化值 在使用前 都经历过默认初始化**

1.静态变量（类变量）随着类的加载 在类加载过程的linking的prepare阶段 给类变量 赋默认初始化值 在initial阶段进行显示赋值

2.实例变量 随着对象的创建 会在堆空间中分配实例变量空间 并进行系统默认赋值

**②局部变量 必须显示赋值 无系统默认初始化值**

#### 概念

代码一块内存空间，使用变量名来访问和使用这块内存空间

#### 特点和作用

![image-20220723100343327](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723100343327.png)

#### 如何声明和使用变量

![image-20220723100627027](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723100627027.png)

![image-20220723100245590](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723100245590.png)

#### 变量的有效范围（成员变量和局部变量）

![image-20220723102034760](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723102034760.png)

#### 注意



**变量必须先声明 赋值 后可使用**
 **变量都定义在其作用域内 {} 离开作用域无效** 
 **同一作用域内不能定义重名变量**

#### 变量的分类（按照数据类型分类）

![image-20220723100548267](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723100548267.png)

##### **基本数据类型（primitive type）**

​      整数类型{byte、short、int、long}
 数值型
​      浮点类型{float、double}
 字符型{char}
 布尔型{boolean}

#####  **引用数据类型（reference type）**

 类{class}
 接口（interface）
 数组（[ ] array ）



## 数据类型

![image-20220723101055074](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101055074.png)

### 基本数据类型

#### 整数类型

![image-20220723101117173](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101117173.png)
![image-20220723101143615](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101143615.png)

#### 浮点型

![image-20220723101201130](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101201130.png)
![image-20220723101215226](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101215226.png)

#### 字符型

![image-20220723101242516](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101242516.png)
![image-20220723101305591](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101305591.png)

#### 布尔型

1个字节

![image-20220723101316352](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101316352.png)
![image-20220723101333525](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101333525.png)

### 引用数据类型

![image-20220723101347775](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101347775.png)

#### 类 class

##### string

![image-20220723102341374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723102341374.png)

string后接上  “ ”；

String = ---char---char---char---char---char---….
 string 为字符串 “”任意放字符
 char   为字符  ‘’有且只能放一个字符

引用数据类型：string 
 ****可以与8种基本数据类型进行连接运算 string无法转成int**
 **连接符号为 +** 
 值将转化为string类型**

**equals**

![image-20220723102706989](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723102706989.png)

![image-20220723102622319](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723102622319.png)

#### 接口 interface

#### 数组 [ ]

### 数据类型的转换

#### 基本数据类型的转换

##### 自动类型转换（隐式类型转换）

![image-20220723101658461](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101658461.png)

![image-20220723101539472](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101539472.png)
****此处的容量大小是：表示数的范围的大小。比如float容量>long的容量**
 并非指占用的storage大小**

##### 强制类型转换（显示类型转换）

![image-20220723101644390](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101644390.png)

![image-20220723101630136](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723101630136.png)



## 运算符

![image-20220723104710413](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104710413.png)

### 算数运算符

![image-20220723103252502](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103252502.png)
![image-20220723103311301](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103311301.png)
**自增和自减运算**

![image-20220723103536844](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103536844.png)

![image-20220723103439456](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103439456.png)

自增1不会改变数据类型
 在本身上自加1
 // N1++ (N直接自增1）

**取模%运算**

```java
//取模运算%
public static void main(String[] args) {
    int numb1 = 29;
    int numb2 = -15;
    int numb3 = 15;
    int numb4 = -6;
    System.out.println(numb1 % numb2);//14
    System.out.println(numb2 % numb4);//-3//同为负数的取模结果为负数
}
```

#### 数学函数与常量

##### Math类

```java
import static java.long.Math.*;//导包
//sqrt取平方根
double number1 = 4;
double number2 = Math.sqrt(number1);
System.out.println(number2);
//2.0

//pow幂运算
double number3 = 2;
double number4 = Math.pow(number3,3);
System.out.println(number4);
//8.0--number4为number3的三次方

//Math中的方法
Math.
    //三角函数类
    Math.sin
    Math.cos
    Math.tan
    Math.atan
    Math.atan2
	//指数函数以及反函数--自然对数以及以10为底的数
    Math.exp
    Math.log
    Math.log10
	//圆周率Π和e常量的近似值
    Math.PI
    Math.E
```



### 赋值运算符

![image-20220723103551423](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103551423.png)

![image-20220723103606589](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103606589.png)
![image-20220723103642651](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103642651.png)

```java
public static void main(String[] args) {
        int i = 1;
//      int c = i * 0.1;//编译不通过
        int d = i *= 0.1;
        System.out.println(d);//0
    }
```

### 比较运算符（关系运算符）

![image-20220723103733207](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103733207.png)
![image-20220723103746347](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103746347.png)

**== : 不仅可以使用在数值类型数据之间；还可以使用在引用类型数据之间（比较的是引用地址值）**

#### ==和equals的比较

**使用 == 比较**

**两个不同类型的引用不能进行 == 比较**

![image-20221007225021140](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007225021140.png)

Java中的**8种基本数据类型**（byte,short,char,int,long,float,double,boolean）比较他们之间的**值是否相等**。
**引用数据类型**，比较的是他们在**堆内存地址是否相等**。每新new一个引用类型的对象，会重新分配堆内存空间，使用==比较返回false。

因为 Java 只有值传递，所以，对于 == 来说，不管是比较基本数据类型，还是引用数据类型的变量，其本质比较的都是值，只是引用类型变量存的值是对象的地址

![image-20220925230054454](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220925230054454.png)

Integer是引用类型，int是基本类型。
基本类型i02 == i04时，引用类型i04自动拆箱，调用Integer的intValue()方法，返回是一个int类型。
2个基本类型的int相比当然相等了

**使用 equals 比较**

**用于引用数据类型** **基本数据类型需使用包装类**

**包装类全部都重写了equals方法，将其的地址比较改为了值比较**

equals方法是**Object类的一个方法**，Java当中所有的类都是继承于Object这个超类。
JDK1.8 Object类equals方法源码如下，即返回结果取决于两个对象的使用==判断结果。

```java
1. public boolean equals(Object obj) {
2.    return (this == obj);
3. }
```

在实际使用中，**一般会重写定义的class的equals方法**，如JDK1.8 java.lang.String类的equals源码。
即两个字符串使用 == 相等  或者  两个字符串的所有组成字符都相等返回true，其他情况返回false。这里就定义String根据equals方法判断是否相等的逻辑

```java
public boolean equals(Object anObject) {
	if (this == anObject) {
		return true;
	}
	if (anObject instanceof String) {
		String anotherString = (String) anObject;
		int n = value.length;
		if (n == anotherString.value.length) {
			char v1[] = value;
			char v2[] = anotherString.value;
			int i = 0;
			while (n-- != 0) {
				if (v1[i] != v2[i])
						return false;
				i++;
			}
			return true;
		}
	}
	return false;
}
```

 **== 的作用：**
　　**基本类型**：比较**值是否相等**
　　**引用类型**：比较内存**地址值是否相等**

**equals 的作用:**
　　**引用类型**：**默认情况下，比较内存地址值是否相等**。可以按照需求逻辑，**重写对象的equals方法**

==:对于基本类型，比较的是值是否相等；对于引用类型，比较的是地址是否相等
equals：比较的是对象是否相等（不能比较基本类型，因为equals是Object超类中的方法，而Object是所有类的父类）

Object类中默认的实现方式是  :  return this == obj  。那就是说，只有this 和 obj引用同一个对象，才会返回true。

而我们往往需要用equals来判断 2个对象是否等价，而非验证他们的唯一性。这样我们在实现自己的类时，就要重写equals.

- **对null**:  x.equals(null) 一定是false

- 

- ```java
  /*重写equals，也必须重写hashCode。*/
  这个方法返回对象的散列码，返回值是int类型的散列码。
  对象的散列码是/*为了更好的支持基于哈希机制的Java集合类，例如 Hashtable, HashMap, HashSet 等*/
  ```

#### 为什么重写 equals 还要重写 hashcode

hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等（即使这两个对象指向相同的数据

现在有两个Student对象：

    Student s1=new Student("小明",18);
    Student s2=new Student("小明",18);
此时s1.equals(s2)一定返回true

假如只重写equals而不重写hashcode，那么Student类的hashcode方法就是Object默认的hashcode方法，由于默认的hashcode方法是根据对象的内存地址经哈希算法得来的，显然此时s1!=s2,故两者的hashcode不一定相等。
然而重写了equals，且s1.equals(s2)返回true，根据hashcode的规则，两个对象相等其哈希值一定相等，所以矛盾就产生了，因此重写equals一定要重写hashcode，而且从Student类重写后的hashcode方法中可以看出，重写后返回的新的哈希值与Student的两个属性有关。

### 逻辑运算符

![image-20220723103943690](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103943690.png)
![image-20220723103954715](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723103954715.png)
![image-20220723104019261](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104019261.png)
![image-20220723104035659](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104035659.png)

### 位运算符★

![image-20220723104118189](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104118189.png)
![image-20220723104135886](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104135886.png)
![image-20220723104200729](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104200729.png)

<< & >> 运算

```java

//<< & >> 运算 
//<< x位 -- *2的x次方
//>> x位 -- /2的x次方
int num = 12,num1 = 13;
int result = num << 3;
System.out.println(result);//96-->12*2的三次方
int result1 = num1 >> 1;
System.out.println(result1);//6-->13/2的一次方
```



异或运算(^)

```java
public void main() {
    //位运算 ^ 异或位运算 
    //相同数^ 结果为0 
    //任何数与0^ 结果为任何数
    int num = 12,num1 = 12;
    int result = num ^ num1;
    System.out.println(result);//0
    
    int num = 0,num1 = 0;
    int result = num ^ num1;
    System.out.println(result);//0
    
    int num = 0,num1 = 12;
    int result = num ^ num1;
    System.out.println(result);//12
    
    int num = 0,num1 = 1;
    int result = num ^ num1;
    System.out.println(result);//1
    
}
```

### 三元运算符★

![image-20220723104340842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104340842.png)
![image-20220723104353648](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104353648.png)

```java
//三元运算 
//（条件表达式）？表达式1:表达式2 （表达式1&表达式2 为同种类型:int i = (3 < 4) ? 2 : (int) 5.5;）
//条件表达式为true 结果为表达式1
//条件表达式为false 结果为表达式2
int i = (3 < 4) ? 2 : 5;//条件表达式为true 结果为表达式1
System.out.println(i);//2
int i1 = (3 < 4) ? 2 : 5;//条件表达式为false 结果为表达式2
System.out.println(i1);//5
//表达式1 & 表达式2 为同种类型:int i = (3 < 4) ? 2 : (int) 5.5;
int i = (3 < 4) ? 2 : (int) 5.5;

//把 carry = sum / 10; 换成 carry = sum >9 ? 1 : 0 ; 这样 速度会快很多
//除法运算会需要更多的机器指令 速度上略慢于比较运算
```

![image-20220723104426793](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104426793.png)
![image-20220723104443231](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104443231.png)

### 运算符的优先级

![image-20220723104748698](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104748698.png)
![image-20220723104924135](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723104924135.png)
![image-20220723105016277](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723105016277.png)

## 流程控制★

![image-20220723113528530](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113528530.png)

### 顺序结构

![image-20220723113629388](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113629388.png)

### 分支结构

#### if - else

![image-20220723113806898](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113806898.png)
![image-20220723113903863](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113903863.png)
![image-20220723113920815](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113920815.png)

#### switch - case

**switch语句只支持int类型**

```java
以java8为准，switch支持10种类型 
基本类型：byte char short int 
对于包装类 ：Byte,Short,Character,Integer String enum 
2、实际只支持int类型 Java实际只能支持int类型的switch语句，那其他的类型时如何支持的 a、基本类型byte char short 原因：这些基本数字类型可自动向上转为int, 实际还是用的int。 b、基本类型包装类Byte,Short,Character,Integer 原因：java的自动拆箱机制 可看这些对象自动转为基本类型 c、String 类型 原因：实际switch比较的string.hashCode值，它是一个int类型 如何实现的，网上例子很多。此处不表。 d、enum类型 原因 ：实际比较的是enum的ordinal值（表示枚举值的顺序），它也是一个int类型 所以也可以说 switch语句只支持int类型
```

![image-20220723113821794](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723113821794.png)

![image-20220723114013852](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114013852.png)
![image-20220723114035119](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114035119.png)

![image-20220723114058581](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114058581.png)
![image-20220723114141798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114141798.png)

#### if 和 switch 对比

![image-20220723114234762](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114234762.png)

### 循环结构

好处：1.代码简洁 2.易修改

四要素：![image-20220723114433664](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114433664.png)

![image-20220723114326294](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114326294.png)

### for 循环

![image-20220723114710290](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114710290.png)

### For&Foreach

　foreach虽然是for循环的简化版本，但是并不是说foreach就比for更好用，foreach适用于循环次数未知，或者计算循环次数比较麻烦情况下使用效率更高，但是更为复杂的一些循环还是需要用到for循环效率更高。

　foreach适用于只是进行集合或数组遍历，for则在较复杂的循环中效率更高。

　　foreach不能对数组或集合进行修改（添加删除操作），如果想要修改就要用for循环。

　　所以相比较下来for循环更为灵活。

### while 循环

![image-20220723114747795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114747795.png)
![image-20220723114810385](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114810385.png)

### do-while 循环

![image-20220723114827903](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114827903.png)

### 嵌套循环（多重循环)

**外层循环决定行数；内层循环决定（列数）每一行的内容**

![image-20220723115257619](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723115257619.png)

![image-20220723114918768](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723114918768.png)

### 跳转

#### 关键字：break，continue，return

![image-20220723115308950](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723115308950.png)
![image-20220723115355968](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723115355968.png)
![image-20220723115415915](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723115415915.png)
![image-20220723115517953](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723115517953.png)

```java
public void main() {
    int i;
    for (i = 0;i < 10; i++) {
        if(i % 2 == 0){
            break;//终止本层循环
            }
        }
        System.out.println(i);//0
    }
	for (i = 0;i < 10; i++) {
  	    if(i % 2 == 0){
  	        continue;//终止本次循环
 	        }
 	    }
 	    System.out.println(i);//10
    }
}

```

## 数组★

### 数组概述

![image-20220723122826458](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723122826458.png)

![image-20220723122819238](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723122819238.png)

![image-20220723122808283](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723122808283.png)

![image-20220723122855599](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723122855599.png)

![image-20220723160809274](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723160809274.png)

### 一维数组

![image-20220723165954896](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165954896.png)

#### 一维数组的声明

![image-20220723123126264](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723123126264.png)

![image-20220723123520064](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723123520064.png)

#### 一维数组的初始化

![image-20220723123442993](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723123442993.png)

![image-20220723123201084](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723123201084.png)

![image-20220723160955689](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723160955689.png)



#### 一维数组的长度

![image-20220723160605921](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723160605921.png)



#### 一维数组的元素

![image-20220723160635431](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723160635431.png)
![image-20220723160649138](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723160649138.png)

#### 遍历一维数组

![image-20220723161018351](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161018351.png)

```java
public void main() {
    int[] arrayInt = new int[4];//动态初始化
    arrayInt[0] = 1;
    arrayInt[1] = 2;
    arrayInt[2] = 2;
    arrayInt[3] = 3;
   int[] arrayInt1 = new int[]{1,2,3,4,5,6,4,5,55,5,1};//静态初始化
    //数组一旦初始化 长度被确定
    //遍历一维数组
    for (int i = 0; i < arrayInt1.length; i++) {
        System.out.println(arrayInt1[i]);
    }

}
```

### 多维数组（二维数组）

![image-20220723170443907](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723170443907.png)

![image-20220723161158318](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161158318.png)

#### 二维数组的声明

![image-20220723161206965](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161206965.png)

#### 二维数组的初始化

![image-20220723161243363](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161243363.png)

```java
public void main() {
    int[][] arrayInt3 = new int[4][];//动态初始化二维数组
    //给二维数组中每个位置的一维数组赋值
    arrayInt3[0] = new int[]{1, 2, 1, 2};
    arrayInt3[1] = new int[]{5,2,3};
    arrayInt3[2] = new int[]{6,2,5}; 	
    arrayInt3[3] = new int[]{5,2,5};
    
    int[][] arrayInt2 = new int[][]{{1,2,1,2},{5,2,3},{6,2,5},{5,2,5}};//静态初始化二维数组
    //遍历二维数组
    for (int i = 0; i < arrayInt2.length; i++) {
        for (int j = 0; j < arrayInt2[i].length; j++) {
            System.out.println(arrayInt2[i][j]);
        }
    }
}
```

![image-20220723161304699](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161304699.png)

![image-20220723161346011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161346011.png)

#### 二维数组的长度

![image-20220723161319874](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161319874.png)

#### 二维数组的元素

![image-20220723161357501](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161357501.png)

#### 遍历二维数组

![image-20220723161430105](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161430105.png)

### 数组的排序算法

![image-20220723162203587](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723162203587.png)

#### 冒泡排序

![image-20220723161745472](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723161745472.png)

![image-20220723162023219](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723162023219.png)

#### 直接选择排序



#### 反转排序

![image-20220723162056501](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723162056501.png)

### 数组的基本操作&Array工具类的使用

![image-20220723164034506](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164034506.png)

![image-20220723163735830](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723163735830.png)

#### 遍历数组

![image-20220723164339244](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164339244.png)

```java
//遍历二维数组
    for (int i = 0; i < arrayInt2.length; i++) {
        for (int j = 0; j < arrayInt2[i].length; j++) {
            System.out.println(arrayInt2[i][j]);
        }
    }
}
```



#### 填充替换数组元素

![image-20220723164716886](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164716886.png)

```java
public void main() {
    int[] arrayInt1 = new int[5];
    Arrays.fill(arrayInt1,8);
    System.out.println(Arrays.toString(arrayInt1));
    //[8, 8, 8, 8, 8]
```

![image-20220723164734783](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164734783.png)

![image-20220723164747364](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164747364.png)

```java
 public void main() {
        int[] arrayInt1 = new int[]{1,2,3,4,5,6,4,5,55,5,1};//静态初始化
//        int[] arrayInt1 = new int[5];
        Arrays.fill(arrayInt1,2,9,8);
        System.out.println(Arrays.toString(arrayInt1));
        //[1, 2, 8, 8, 8, 8, 8, 8, 8, 5, 1]
    }
```

#### 对数组进行排序

![image-20220723164914208](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164914208.png)

```java
public void main() {
    int[] arrayInt1 = new int[]{1,2,3,4,5,6,4,5,55,5,1};//静态初始化
    Arrays.sort(arrayInt1);
    System.out.println(Arrays.toString(arrayInt1));
    //[1, 1, 2, 3, 4, 4, 5, 5, 5, 6, 55]
}
```

#### 复制数组

![image-20220723164959292](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164959292.png)

```java
public void main() {
    int[] arrayInt1 = new int[]{1,2,3,4,5,6,4,5,55,5,1};//静态初始化
    Arrays.sort(arrayInt1);
    System.out.println(Arrays.toString(arrayInt1));
    //[1, 1, 2, 3, 4, 4, 5, 5, 5, 6, 55]
    int[] copyOf = Arrays.copyOf(arrayInt1, 15);
    System.out.println(Arrays.toString(copyOf));
    //[1, 1, 2, 3, 4, 4, 5, 5, 5, 6, 55, 0, 0, 0, 0]
}
```

![image-20220723165423657](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165423657.png)

![image-20220723165443921](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165443921.png)

![image-20220723165456693](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165456693.png)

#### 查询数组

![image-20220723165541213](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165541213.png)

![image-20220723165601591](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165601591.png)

![image-20220723165625949](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165625949.png)

```java
public void main() {
    int[] arrayInt1 = new int[]{1,2,3,4,5,6,4,5,55,5,1};//静态初始化
    Arrays.sort(arrayInt1);//在使用binarySearch前需要通过调用sort（）方法对数组经行排序
    int binarySearch = Arrays.binarySearch(arrayInt1, 55);
    System.out.println(Arrays.toString(arrayInt1));
    System.out.println("通过binarySearch查找55的索引位置为:" + binarySearch);
    //[1, 1, 2, 3, 4, 4, 5, 5, 5, 6, 55]
    //通过binarySearch查找55的索引位置为:10
}
```

![image-20220723163921437](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723163921437.png)

### ![image-20220723164205070](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723164205070.png)数组中的常见的Exception

![image-20220723165854221](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723165854221.png)

### 数据结构

 



# Eclipse使用

### 常用快捷键

/*
 * Eclipse中的快捷键：
 * 1.补全代码的声明：alt + /
 * 2.快速修复: ctrl + 1  
 * 3.批量导包：ctrl + shift + o
 * 4.使用单行注释：ctrl + /
 * 5.使用多行注释： ctrl + shift + /   
 * 6.取消多行注释：ctrl + shift + \
 * 7.复制指定行的代码：ctrl + alt + down 或 ctrl + alt + up
 * 8.删除指定行的代码：ctrl + d
 * 9.上下移动代码：alt + up  或 alt + down
 * 10.切换到下一行代码空位：shift + enter
 * 11.切换到上一行代码空位：ctrl + shift + enter
 * 12.如何查看源码：ctrl + 选中指定的结构   或  ctrl + shift + t
 * 13.退回到前一个编辑的页面：alt + left 
 * 14.进入到下一个编辑的页面(针对于上面那条来说的)：alt + right
 * 15.光标选中指定的类，查看继承树结构：ctrl + t
 * 16.复制代码： ctrl + c
 * 17.撤销： ctrl + z
 * 18.反撤销： ctrl + y
 * 19.剪切：ctrl + x 
 * 20.粘贴：ctrl + v
 * 21.保存： ctrl + s
 * 22.全选：ctrl + a
 * 23.格式化代码： ctrl + shift + f
 * 24.选中数行，整体往后移动：tab
 * 25.选中数行，整体往前移动：shift + tab
 * 26.在当前类中，显示类结构，并支持搜索指定的方法、属性等：ctrl + o
 * 27.批量修改指定的变量名、方法名、类名等：alt + shift + r
 * 28.选中的结构的大小写的切换：变成大写： ctrl + shift + x
 * 29.选中的结构的大小写的切换：变成小写：ctrl + shift + y
 * 30.调出生成getter/setter/构造器等结构： alt + shift + s
 * 31.显示当前选择资源(工程 or 文件)的属性：alt + enter
 * 32.快速查找：参照选中的Word快速定位到下一个 ：ctrl + k
 * 33.关闭当前窗口：ctrl + w
 * 34.关闭所有的窗口：ctrl + shift + w
 * 35.查看指定的结构使用过的地方：ctrl + alt + g
 * 36.查找与替换：ctrl + f
 * 37.最大化当前的View：ctrl + m
 * 38.直接定位到当前行的首位：home
 * 39.直接定位到当前行的末位：end
 */



# IDEA使用



# JVM内存结构★

![image-20220822221928169](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220822221928169.png)



![image-20220826120002243](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826120002243.png)





# 面向对象编程★

## 面向对象

面向对象设计思想早已不是什么新鲜事物,在Java实际项目中也是主流的编程思想。 正是因为Java,C#天然就是支持面向对象的,反而很多童鞋并不能讲清楚什么是面向对象。我们只是这样在用而已...                

### 类和实例

- 把大象装进冰箱
- 初识面向对象
- 类和实例
  - 通俗理解
  - 进一步理解
  - 小试牛刀
- OOP三大特性
  - 封装
  - 继承
  - 多态
- 结语
- 参考

> 算法+数据结构=程序 ——图灵奖的Pascal之父(Niklaus Wirth)

### 把大象装进冰箱里

有一天,产品经理给我们提了一个需求:要把大象装进冰箱里。

作为程序员的我们,就会思考把大象装进冰箱里需要几步？

经过流程梳理,我们可以大致列了几个步骤：

- 第一步,把冰箱门打开。
- 第二步,把大象装进去。
- 第三步,把冰箱门关上。

上面每一个步骤，我们都可以定义一个**函数**，每个**函数**可以实现一个功能。

所有函数定义好了之后，依次调用就可以了：

- openTheDoor()；
- pushElephant()；
- closeTheDoor()；

至此,我们便轻松愉快的完成了产品经理的需求,然后哼着小曲儿去快乐的玩耍了。

但是,过了两天产品经理又提出了更加变态的需求

- 我要把大象装微波炉里
- 我要把狮子也装冰箱里
- 我要把大象装冰箱，但是门别关，敞着就行
- 。。。

面对这样“变态”的需求,如果继续使用上面的思路来实现代码功能,将会带来以下问题:

- 大量“重复”函数
- 代码可读性变差
- 不易维护
- 。。。。

以上就是通常所说的**面向过程**的编程方式。正是因为面向过程的带来的诸多问题,**面向对象**的编程思想逐渐流行起来,并在编程界风靡至今。

### 初识面向对象

> 没有人比我更懂面向对象。

面向对象起源于1967年在挪威设计的Simula编程语言。该语言拥有类、多态和即成等以往的编程语言没有的优良结构,被称为最早的面向对象编程语言(Object Oriented Programming  Language,OOP)。后来艾伦.凯率领的团队开发的smalltalk沿用了该结构,确立了面向对象的概念。 此后,具有相同结构的C++、Objective-C、Java、C#和Ruby等诸多编程语言被相继开发出来,并延续至今。

OOP使得大规模时使得大规模的可重(chóng)用构件群的创建成为可能,这些被称为类库或框架。

而创建可重用构件群时使用的固定设计思想被提炼成设计模式。(《面向对象是怎样工作的（第2版）》)

面向对象的基本思想就是重点关注各个构件,提高构件的独立性、重用性,把构件组合起来,实现系统整体的功能。当程序发生修改时,能够将影响范围降到最低。

**对象就是对事物的一种抽象描述。**  现实世界中的事物，都可以用【属性】和【能力】来描述。

回到上面产品经理的**将大象装进冰箱**需求，用面向对象来实现，我们会先定义一个**冰箱**对象，它的【属性】就是当前的冷冻温度，【能力】就是开门、关门。还有一个**大象**对象，它的【属性】可以是大象的智商、体积。然后我们依次：

- 向冰箱下达**开门**的命令。
- 向冰箱下达**存储**大象的命令。
- 向冰箱下达**关门**的命令。

所以,当我们将程序构件化之后,一旦遇到“我要把大象装冰箱，但是门别关，敞着就行”这样的变态需求,代码不用大改,只需要将先前定义好对象和能力按照新的需求组合即可。

#### 面向过程和面向对象思想的区别

- 面向过程就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候一个一个依次调用就可以了
- 面向对象是把构成问题事务分解成各个对象，建立对象的目的不是为了完成一个步骤，而是为了描叙某个事物在整个解决问题的步骤中的行为。

### 类和实例

> 类就是指一类事物，对象就是指这类事物中的某个具体的个体。

#### 通俗的解释

类是指一类事物，类是一种归纳和总结，是一种概括，是一个抽象的概念。

比如：我们把那些具有一定知名度、一定名气的人物称之为明星，说白了，类就是对一些具有相同特性的事物进行的归纳和总结。

再比如：我们把那些用胶片或存储卡记录的人物故事影像统称为电影，所以类就是对一些具有相同特性的事物进行的归纳和总结。

你最喜欢的明星是谁? 周杰伦。

这里,明星就是类,周杰伦就是实例。

#### 书面解释

> **类**指类型,实例指具体事物

**类**是面向对象的最基本的结构,与其对应

类的英文是class,含义是"种类","类型"等"同类的集合"。实例的英文是instance,含义是"具体的事物"。

比如，

- 车： 小汽车,大卡车,越野车...
- 国家：中国、美国、韩国...
- 运动员：姚明、马龙、张倩...

#### 编程示例

> 面向对象本质上不是一门技术而是一种思想。

面向对象本身不是一门技术而是一种思想。只有转变了思想,你才能在日常编程中应用自如。

这里依然沿用“把大象装进冰箱”需求,从需求中分析出有两个具体的事物*大象*和*冰箱*,抽出两个对象

```java
 复制代码
/**
 * Description: 大象类
 */
@Data
public class Elephant {

    private Object head;//头
    private List<Object> feets;//四肢
    private Object body;//躯干
    private Object tail;//尾巴

    public String toString(){
        return "大象";
    }
}
 复制代码/**
 * Description: 冰箱类
 */
@Data
public class Fridge {

    /**
     * 存储
     */
    public  void store(Object obj)
    {
        System.out.println("把"+obj.toString()+"放进冰箱");
    }

    /**
     * 开门
     */
    public  void  openTheDoor()
    {
        System.out.println("开门");
    }

    /**
     * 关门
     */
    public  void  closeTheDoor()
    {
        System.out.println("关门");
    }
}
```

Java使用具体的事物，需要通过new关键字来创建这个事物的具体实例。

我们可以方便的利用Springboot来写一个单元测试:

1.实例化对象

```java
 复制代码
//实例化一头大象
Elephant elephant=new Elephant();
 复制代码
//实体化一个冰箱
Fridge fridge=new Fridge();
```

2.调用冰箱的功能

```java
复制代码fridge.openTheDoor();
fridge.store(elephant);
fridge.closeTheDoor();
```

执行结果如下：



![image-20230203145546180](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230203145546180.png)



#### 面向对象的抽取心得

1、先按照名词提炼问题领域中的对象

2、对对象进行描述，其实就是在明确对象中应该具备的属性和功能

3、通过new的方式就可以创建该事物的具体对象

4、通过该对象调用它以后的功能。

### OOP三大特性

面向对象思想有三大特性，即封装、继承与多态。三大特性是面向对象编程的核心，对于初学者务必加强对三大特性的理解与领会。

#### 封装

举个例子吧,现代人都爱点外卖。你点一份回锅肉,然后外卖小哥给你送来的时候,已经是打包好的热乎的成品。如果你是自己做的话,需要上菜市去买肉,豆瓣酱,食用油,辣椒等。而外卖营隐藏了这些工序和细节,这就封装。

**封装**隐藏了类的内部实现机制，可以在不影响使用的情况下改变类的内部结构，同时也保护了数据。对外界它的内部细节是隐藏的,暴露给外界的只是它的访问方法。

是否暴露给外部,是通过访问修饰符控制,Java类中常用的访问修饰符如下:

| 修饰符      | 当前类 | 同一包内 | 子孙类(同一包) | 子孙类(不同包) | 其他包 |
| ----------- | ------ | -------- | -------------- | -------------- | ------ |
| `public`    | Y      | Y        | Y              | Y              | Y      |
| `protected` | Y      | Y        | Y              | Y/N            | N      |
| `default`   | Y      | Y        | Y              | N              | N      |
| `private`   | Y      | N        | N              | N              | N      |

#### 继承

比如, 前面产品经理提出了*狮子也装冰箱里*这样的需求,于是我们提取出*狮子*对象。

```java
 复制代码
/**
 * Description: 狮子对象
 */
public class Lion {
    private Object head;//头
    private List<Object> feets;//四肢
    private Object body;//躯干
    private Object tail;//尾巴

    public String toString(){
        return "狮子";
    }
}
```

按照面向对象的思想我们很快就写出了狮子类。

但是,不妨再观察一下,*大象*和*狮子*两个类是不是几乎一样,代码似乎有点重复啊~

能不能将不同类中相同的部分抽取出来公用呢? 继承特性就能做到。

**继承**要解决的就是代码重用的问题，利用继承性可以从已有的类继续派生出新的子类，也可以利用子类扩展出更多的功能。

*大象*和*狮子*都属于动物,因此在两个对象的基础上我们可以在抽象一个*动物*对象,然后*大象*和*狮子*都继承自动物。

动物类

```java
 复制代码
/**
 * Description: 动物
 */
@Data
public class Animal {

    private Object head;//头
    private List<Object> feets;//四肢
    private Object body;//躯干
    private Object tail;//尾巴
}
```

大象类继承自动物类

```java
 复制代码/**
 * Description: 大象类
 */
@Data
public class Elephant  extends  Animal{

    public String toString(){
        return "大象";
    }
}
```

狮子类继承自动物类

```java
 复制代码/**
 * Description: 狮子对象
 */
public class Lion  extends  Animal{
    public String toString(){
        return "狮子";
    }
}
 复制代码
//实例化一头狮子
Animal lion=new Lion();

//实体化一个冰箱
Fridge fridge=new Fridge();
fridge.store(lion);
fridge.store(lion);
fridge.closeTheDoor();
```

#### 多态

> 多态是同一个行为具有多个不同表现形式或形态的能力

还是借用上面的例子来探讨,比如产品经理说动物关进冰箱之前要先叫一声,主人会根据叫声类判断关进去的是什么动物。

动物都有叫的功能

```java
 复制代码
/**
 * Description: 动物
 */
@Data
public class Animal {

    private Object head;//头
    private List<Object> feets;//四肢
    private Object body;//躯干
    private Object tail;//尾巴

    public void Cry()
    {
        System.out.println("我被关进了冰箱!");
    }
}
```

但是不同动物叫声不同,所以需要增加各自叫的方法

```java
 复制代码
/**
 * Description: 狮子对象
 */
public class Lion  extends  Animal{

    // 覆盖（重写）方法
    public void cry() {
        System.out.println("吼~");
    }

    public String toString(){
        return "狮子";
    }
}\
 复制代码
/**
 * Description: 大象类
 */
@Data
public class Elephant  extends  Animal{

    // 覆盖（重写）方法
    public void cry() {
        System.out.println("哞~");
    }

    public String toString(){
        return "大象";
    }
}
```

测试用例走一波



![image-20230203145651586](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230203145651586.png)



以上我们通过编程实现了,不同的动物有各自的叫法,这就是多态的简单实现。

#### 多态的好处

- 可替换性（substitutability）。多态对已存在代码具有可替换性。
- 可扩充性（extensibility）。多态对代码具有可扩充性。增加新的子类不影响已存在类的多态性、继承性，以及其他特性的运行和操作。

### 结语

面向对象设计思想早已不是什么新鲜事物,在Java实际项目中也是主流的编程思想。

正是因为Java,C#天然就是支持面向对象的,反而很多童鞋并不能讲清楚什么是面向对象。我们只是这样在用而已...

> Notes: 尽管大牛们都倡导面向对象,但并不是说面向过程就不能使用。实际项目中，还是要根据需求和场景来选择,面向对象和面向对象都是解决问题的方式,二者并不冲突。

## 类及内部成员|对象

**一：创建类 设计类的成员（属性，constructor方法，方法，代码块，内部类）**

**二：创建对象**

**三：调用对象的结构**

![image-20220723171713272](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171713272.png)

对象 ：

定义：现实世界中随处可见的一种事物就是对象；对象是事物存在的实体。

**对象具有：属性，方法（行为）两个部分；**人们通过探讨对象的属性和观察对象的行为来了解对象。

可以将这些属性和行为封装起来；构成一个类；**类：实质就是封装对象属性和方法（行为）的载体**。对象是抽象出来的一个实例。

![image-20220723171352271](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171352271.png)

### 面向对象的理解

![image-20220723171845229](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171845229.png)

![image-20220723171632585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171632585.png)

### 类

![image-20220920111503324](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920111503324.png)

#### **类的加载顺序**

(1) 父类静态代码块(包括静态初始化块，静态属性，但不包括静态方法)

(2) 子类静态代码块(包括静态初始化块，静态属性，但不包括静态方法 )

(3) 父类非静态代码块( 包括非静态初始化块，非静态属性 )

(4) 父类构造函数

(5) 子类非静态代码块 ( 包括非静态初始化块，非静态属性 )

(6) 子类构造函数

**U M L类图**

![image-20220723211630841](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211630841.png)

**Java Bean**

![image-20220723211545168](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211545168.png)

#### 加载.class文件的方式

![image-20220920112309310](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920112309310.png)

#### 属性

![image-20220723211450931](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211450931.png)

<img src="https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190801499.png" alt="image-20220723190801499"  />

![image-20220723190246291](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190246291.png)

![image-20220723190309478](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190309478.png)

##### 成员变量

![image-20220801213711764](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213711764.png)

![image-20220723185727159](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723185727159.png)
![image-20220723190711006](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190711006.png)

##### 成员方法

![image-20220723185916477](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723185916477.png)

![image-20220723185901924](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723185901924.png)

##### 封装

![image-20220723190940020](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190940020.png)

![image-20220723191029219](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191029219.png)

#### 方法

![image-20220723191047540](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191047540.png)

![image-20220723191105843](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191105843.png)

![image-20220723191127886](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191127886.png)



##### 局部变量

![image-20220723212103523](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212103523.png)

##### 局部方法

![image-20220723212255705](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212255705.png)

##### this关键字

![image-20220723212503038](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212503038.png)

![image-20220723212525265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212525265.png) 

![image-20220723212550911](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212550911.png)

![image-20220723212604718](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212604718.png)

##### 方法的重载

两同：同一个类中；同类名

一不同：参数列表不同

![image-20220723191155091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191155091.png)

![image-20220723191208084](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723191208084.png)

##### 可变个数的形参

![image-20220723210322705](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723210322705.png)

![image-20220723210343502](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723210343502.png)

##### 方法参数的值传递机制

![image-20220929095056049](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929095056049.png)

![image-20220723210621502](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723210621502.png)

![image-20220723210733547](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723210733547.png)

**For instance**

```java
public class Hello {
    public static void main(String[] args) {
        Hello hello = new Hello();
        // 基本数据类型
        int i = 10;
        hello.pass(i);
        System.out.println("i = " + i);
    }

	public void pass(int pas) {
    	pas = 20;
    	System.out.println("pas = " + pas);
	}
}
//console
//pas = 20
//i = 10

public class Hello {
    public static void main(String[] args) {
        Hello hello = new Hello();
        // String类
        String s = "hello";
        hello.pass(s);
        System.out.println("s = " + s);
    }
 
    public void pass(String str) {
        str = "world";
        System.out.println("str = "+ str);
    }
}
//console
//str = world
//s = hello


public class Hello {
    public static void main(String[] args) {
        Hello hello = new Hello();
        // 对象
        User user = new User();
        user.setName("wang");
        hello.pass(user);
        System.out.println("main:"+user.getName());
    }
 
    public void pass(User user) {
        user.setName("java");
        System.out.println("The name is :" + user.getName());
    }
}
//console
//The name is : java
//main:java


public class Hello {
    public static void main(String[] args) {
        Hello hello = new Hello();
        User user2 = new User();
        user2.setName("li");
        hello.pass2(user2);
        System.out.println("main:"+user2.getName());
    }
 
    public void pass2(User user) {
        user = new User();
        user.setName("java new");
        System.out.println("The name is :" + user.getName());
    }
 
}
//console
//The name is java new
//main:li
```

##### 递归（recursion）方法

![image-20220723210819962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723210819962.png)



#### constructor方法（构造器）

**类和对象的分水岭**

![image-20220801212308884](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212308884.png)

![image-20220723211252218](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211252218.png)

![image-20220723211351262](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211351262.png)

![image-20220723211315158](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211315158.png)

![image-20220723211335566](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211335566.png)

![image-20220723211412725](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211412725.png)

**调用构造方法前要先初始化**

**构造方法调用构造方法用this关键词**

![image-20221007223113573](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007223113573.png)

![image-20221007223131862](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221007223131862.png)

#### 代码块

![image-20220801213621449](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213621449.png)
![image-20220801213638475](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213638475.png)

![image-20220801213554791](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213554791.png)
![image-20220801213739789](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213739789.png)

#### 内部类

成员内部内或局部内部类在编译后同样会生成.class的字节码文件

格式：

成员内部类：外部类$内部类名.class

局部内部类：外部类$数字 内部类名.class

![image-20220801214236233](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214236233.png)

![image-20220801213834309](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213834309.png)

![image-20220801213847932](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213847932.png)
![image-20220801213900676](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213900676.png)
![image-20220801213913604](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213913604.png)
![image-20220801213924197](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213924197.png)
![image-20220802172610858](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220802172610858.png)

![image-20220801213814542](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213814542.png)
![image-20220801213955743](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213955743.png)

![image-20220801214028339](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214130203.png)
![image-20220801214202779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214202779.png)

### 对象

**一个对象实例化过程：**
　　Person p = new Person();
　　1，JVM会读取指定的路径下的Person.class文件，并加载进内存，
    　　并会先加载Person的父类(如果有直接的父类的情况下).
　　2，在堆内存中的开辟空间，分配地址。
　　3，并在对象空间中，对对象中的属性进行默认初始化。
　　4，调用对应的构造函数进行初始化。
　　5，在构造函数中，第一行会先到调用父类中构造函数进行初始化。
　　6，父类初始化完毕后，在对子类的属性进行显示初始化。
　　7，在进行子类构造函数的特定初始化。
　　8，初始化完毕后，将地址值赋值给引用变量.

![image-20220723190211417](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723190211417.png)

![image-20220723212825446](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212825446.png)

![image-20220723212659944](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723212659944.png)

### 封装与隐藏

![image-20220723211129209](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211129209.png)

![image-20220723211207757](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211207757.png)



![image-20220723211153502](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723211153502.png)

## 三大特性

### 封装 ：

**安全性的体现**

![image-20220723171434027](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171434027.png)
![image-20220801202506418](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801202506418.png)
![image-20220801202545730](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801202545730.png)
![image-20220801202621151](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801202621151.png)
![image-20220801202631536](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801202631536.png)

将对象的属性和方法封装起来，其载体是类。**类：实质就是封装对象属性和方法（行为）的载体**

封装的思想：类通常对客户隐藏其实现细节，用户只需要调用就能直接使用其能实现的功能。

采用封装的思想：保证了类内部数据结构的完整性，使用类的用户不能轻易的直w接操作类的数据结构，只能执行类允许公开的数据。避免外部操作对内部数据的影响，提高程序的可维护性。

**封装的第一个作用就是为了不直接被外部使用，提高代码的安全性，第二个作用就是降低类的使用者的学习成本，不需要知道类的实现，只需要学会调用就好了代码模块化**

**高内聚**

类的内部数据操作detail自己完成，不允许外部干涉

**低耦合**

仅对外暴露少量的方法用于使用



### 继承：

**简洁性的体现**

![image-20220723171452999](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220723171452999.png)

![image-20220801203031556](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203031556.png)
![image-20220801203052280](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203052280.png)
![image-20220801203105907](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203105907.png)
![image-20220801203250011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203250011.png)
![image-20220801203312353](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203312353.png)

![image-20220801203205024](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203205024.png)

**继承是类与类之间关联的一种**；

**继承可以扩展已存在的代码模块**（类）

继承的基本思想：具有相同属性和方法的类可以直接拿来复用并可以补充一些属性和方法节省再次定义相同属性和方法类的时间；

使用继承思想：可以缩短软件开发的周期，复用那些已经定义好的类可以提高系统性能，减少系统在使用过程中出错的概率。

### 多态：

**通用性的体现**

**多态的三个条件:**

 **a.   继承的存在(继承是多态的基础,没有继承就没有多态).**
 **b.   子类重写父类的方法(多态下调用子类重写的方法).**
 **c.   父类引用变量指向子类对象(子类到父类的类型转换/向上转型).**

多态则是为了实现另一个目的——接口重用！多态的作用，就是为了类在继承和派生的时候，保证使用“家谱”中任一类的实例的某一属性时的正确调用。

1、“一个接口，多种方法”

同一操作作用于不同的对象，可以有不同的解释，产生不同的执行结果。

２、实现多态：

​		接口多态性。

​		继承多态性。

​		通过抽象类实现的多态性。

![image-20220801203848886](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203848886.png)
![image-20220801204450125](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801204450125.png)

![image-20220801203506256](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203506256.png)
![image-20220801203612736](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203612736.png)
![image-20220801203628019](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203628019.png)
![image-20220801203701900](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203701900.png)
![image-20220801203719016](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203719016.png)
![image-20220801203802303](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203802303.png)
![image-20220801203832710](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203832710.png)
![image-20220801203913945](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801203913945.png)

![image-20220801203946918](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801204003310.png)
![image-20220801204033579](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801204033579.png)

## 关键字

### 关键字：static★

**static 关键字主要有以下四种使用场景：**

1. **修饰成员变量和成员方法:** 被 static 修饰的成员属于类，不属于单个这个类的某个对象，被类中所有对象共享，可以并且建议通过类名调用。被 static 声明的成员变量属于静态成员变量，静态变量 存放在 Java 内存区域的方法区。调用格式：`类名.静态变量名` `类名.静态方法名()`
2. **静态代码块:** 静态代码块定义在类中方法外, 静态代码块在非静态代码块之前执行(静态代码块—>非静态代码块—>构造方法)。 该类不管创建多少对象，静态代码块只执行一次.
3. **静态内部类（static 修饰类的话只能修饰内部类）：** 静态内部类与非静态内部类之间存在一个最大的区别: 非静态内部类在编译完成之后会隐含地保存着一个引用，该引用是指向创建它的外围类，但是静态内部类却没有。没有这个引用就意味着：1. 它的创建是不需要依赖外围类的创建。2. 它不能使用任何外围类的非 static 成员变量和方法。
4. **静态导包(用来导入类中的静态资源，1.5 之后的新特性):** 格式为：`import static` 这两个关键字连用可以指定导入某个类中的指定静态资源，并且不需要使用类名调用类中静态成员，可以直接使用类中静态成员变量和成员方法。



**修饰成员变量和成员方法(常用)**

被 static 修饰的成员属于类，不属于单个这个类的某个对象，被类中所有对象共享，可以并且建议通过类名调用。被 static 声明的成员变量属于静态成员变量，静态变量 存放在 Java 内存区域的方法区。

方法区与 Java 堆一样，是各个线程共享的内存区域，它用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。虽然 Java 虚拟机规范把方法区描述为堆的一个逻辑部分，但是它却有一个别名叫做 Non-Heap（非堆），目的应该是与 Java 堆区分开来。

HotSpot 虚拟机中方法区也常被称为 “永久代”，本质上两者并不等价。仅仅是因为 HotSpot 虚拟机设计团队用永久代来实现方法区而已，这样 HotSpot 虚拟机的垃圾收集器就可以像管理 Java 堆一样管理这部分内存了。但是这并不是一个好主意，因为这样更容易遇到内存溢出问题。

调用格式：

- `类名.静态变量名`
- `类名.静态方法名()`

如果变量或者方法被 private 则代表该属性或者该方法只能在类的内部被访问而不能在类的外部被访问。

测试方法：



```java
public class StaticBean {
    String name;
    //静态变量
    static int age;
    public StaticBean(String name) {
        this.name = name;
    }
    //静态方法
    static void sayHello() {
        System.out.println("Hello i am java");
    }
    @Override
    public String toString() {
        return "StaticBean{"+
                "name=" + name + ",age=" + age +
                "}";
    }
}
```



```java
public class StaticDemo {
    public static void main(String[] args) {
        StaticBean staticBean = new StaticBean("1");
        StaticBean staticBean2 = new StaticBean("2");
        StaticBean staticBean3 = new StaticBean("3");
        StaticBean staticBean4 = new StaticBean("4");
        StaticBean.age = 33;
        System.out.println(staticBean + " " + staticBean2 + " " + staticBean3 + " " + staticBean4);
        //StaticBean{name=1,age=33} StaticBean{name=2,age=33} StaticBean{name=3,age=33} StaticBean{name=4,age=33}
        StaticBean.sayHello();//Hello i am java
    }
}
```

**静态代码块**

静态代码块定义在类中方法外, 静态代码块在非静态代码块之前执行(静态代码块 —> 非静态代码块 —> 构造方法)。 该类不管创建多少对象，静态代码块只执行一次.

静态代码块的格式是



```text
static {
语句体;
}
```

一个类中的静态代码块可以有多个，位置可以随便放，它不在任何的方法体内，JVM 加载类时会执行这些静态的代码块，如果静态代码块有多个，JVM 将按照它们在类中出现的先后顺序依次执行它们，每个代码块只会被执行一次。

![img](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/18-9-14/88531075.jpg)

静态代码块对于定义在它之后的静态变量，可以赋值，但是不能访问.

**静态内部类**

静态内部类与非静态内部类之间存在一个最大的区别，我们知道非静态内部类在编译完成之后会隐含地保存着一个引用，该引用是指向创建它的外围类，但是静态内部类却没有。没有这个引用就意味着：

1. 它的创建是不需要依赖外围类的创建。
2. 它不能使用任何外围类的非 static 成员变量和方法。

Example（静态内部类实现单例模式）



```java
public class Singleton {
    //声明为 private 避免调用默认构造方法创建对象
    private Singleton() {
    }
   // 声明为 private 表明静态内部该类只能在该 Singleton 类中被访问
    private static class SingletonHolder {
        private static final Singleton INSTANCE = new Singleton();
    }
    public static Singleton getUniqueInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

当 Singleton 类加载时，静态内部类 SingletonHolder 没有被加载进内存。只有当调用 `getUniqueInstance()`方法从而触发 `SingletonHolder.INSTANCE` 时 SingletonHolder 才会被加载，此时初始化 INSTANCE 实例，并且 JVM 能确保 INSTANCE 只被实例化一次。

这种方式不仅具有延迟初始化的好处，而且由 JVM 提供了对线程安全的支持。

**静态导包**

格式为：import static

这两个关键字连用可以指定导入某个类中的指定静态资源，并且不需要使用类名调用类中静态成员，可以直接使用类中静态成员变量和成员方法



```java
 //将Math中的所有静态资源导入，这时候可以直接使用里面的静态方法，而不用通过类名进行调用
 //如果只想导入单一某个静态方法，只需要将*换成对应的方法名即可
import static java.lang.Math.*;//换成import static java.lang.Math.max;具有一样的效果
public class Demo {
  public static void main(String[] args) {
    int max = max(1,2);
    System.out.println(max);
  }
}
```

**补充内容**



**静态方法与非静态方法**

静态方法属于类本身，非静态方法属于从该类生成的每个对象。 如果您的方法执行的操作不依赖于其类的各个变量和方法，请将其设置为静态（这将使程序的占用空间更小）。 否则，它应该是非静态的。

Example



```java
class Foo {
    int i;
    public Foo(int i) {
       this.i = i;
    }
    public static String method1() {
       return "An example string that doesn't depend on i (an instance variable)";
    }
    public int method2() {
       return this.i + 1;  //Depends on i
    }
}
```

你可以像这样调用静态方法：`Foo.method1()`。 如果您尝试使用这种方法调用 method2 将失败。 但这样可行



```java
Foo bar = new Foo(1);
bar.method2();
```

总结：

- 在外部调用静态方法时，可以使用”类名.方法名”的方式，也可以使用”对象名.方法名”的方式。而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。
- 静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），而不允许访问实例成员变量和实例方法；实例方法则无此限制

**`static{}`静态代码块与`{}`非静态代码块(构造代码块)**

相同点： 都是在 JVM 加载类时且在构造方法执行之前执行，在类中都可以定义多个，定义多个时按定义的顺序执行，一般在代码块中对一些 static 变量进行赋值。

不同点： 静态代码块在非静态代码块之前执行(静态代码块 -> 非静态代码块 -> 构造方法)。静态代码块只在第一次 new 执行一次，之后不再执行，而非静态代码块在每 new 一次就执行一次。 非静态代码块可在普通方法中定义(不过作用不大)；而静态代码块不行。

> **🐛 修正（参见： [issue #677open in new window](https://github.com/Snailclimb/JavaGuide/issues/677)）** ：静态代码块可能在第一次 new 对象的时候执行，但不一定只在第一次 new 的时候执行。比如通过 `Class.forName("ClassDemo")`创建 Class 对象的时候也会执行，即 new 或者 `Class.forName("ClassDemo")` 都会执行静态代码块。 一般情况下,如果有些代码比如一些项目最常用的变量或对象必须在项目启动的时候就执行的时候,需要使用静态代码块,这种代码是主动执行的。如果我们想要设计不需要创建对象就可以调用类中的方法，例如：`Arrays` 类，`Character` 类，`String` 类等，就需要使用静态方法, 两者的区别是 静态代码块是自动执行的而静态方法是被调用的时候才执行的.

Example：



```java
public class Test {
    public Test() {
        System.out.print("默认构造方法！--");
    }
    //非静态代码块
    {
        System.out.print("非静态代码块！--");
    }
    //静态代码块
    static {
        System.out.print("静态代码块！--");
    }
    private static void test() {
        System.out.print("静态方法中的内容! --");
        {
            System.out.print("静态方法中的代码块！--");
        }
    }
    public static void main(String[] args) {
        Test test = new Test();
        Test.test();//静态代码块！--静态方法中的内容! --静态方法中的代码块！--
    }
}
```

上述代码输出：



```text
静态代码块！--非静态代码块！--默认构造方法！--静态方法中的内容! --静态方法中的代码块！--
```

当只执行 `Test.test();` 时输出：



```text
静态代码块！--静态方法中的内容! --静态方法中的代码块！--
```

当只执行 `Test test = new Test();` 时输出：



```text
静态代码块！--非静态代码块！--默认构造方法！--
```

非静态代码块与构造函数的区别是： 非静态代码块是给所有对象进行统一初始化，而构造函数是给对应的对象初始化，因为构造函数是可以多个的，运行哪个构造函数就会建立什么样的对象，但无论建立哪个对象，都会先执行相同的构造代码块。也就是说，构造代码块中定义的是不同对象共性的初始化内容。



![image-20220801212105315](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212105315.png)

static关键字（静态）：

static表示静态的意思，既可以修饰成员变量，又可以修饰成员方法，还有一种特殊用法修饰类

(1)、修饰成员变量表示静态变量：static变量也称作静态变量，静态变量和非静态变量的区别是：静态变量被所有的对象所共享，在内存中只有一个副本，它当且仅当在类初次加载时会被初始化。而非静态变量是对象所拥有的，在创建对象的时候被初始化，存在多个副本，各个对象拥有的副本互不影响。static成员变量的初始化顺序按照定义的顺序进行初始化。static不能修饰局部变量。

(2)、修饰成员方法：static方法一般称作静态方法，由于静态方法不依赖于任何对象就可以进行访问，因此对于静态方法来说，是没有this的，因为它不依附于任何对象，既然都没有对象，就谈不上this了。并且由于这个特性，在静态方法中不能访问类的非静态成员变量和非静态成员方法，因为非静态成员方法/变量都是必须依赖具体的对象才能够被调用。

(3)static代码块：static关键字还有一个比较关键的作用就是 用来形成静态代码块以优化程序性能。static块可以置于类中的任何地方，类中可以有多个static块。在类初次被加载的时候，会按照static块的顺序来执行每个static块，并且只会执行一次。

特点：
    1）随着类的加载而加载
    2）优先于对象存在
    3）被所有的对象所共享
        该特点是我们使用static的条件

注意事项：
    1）在静态方法中，不能出现this／super
    2）静态方法只能访问静态成员；非静态方法既可以访问静态成员，也可以访问非静态成员
    3）工具类里面的成员一般来说是静态成员（目的：节约内存空间）

静态变量和成员变量的区别
1）所属不同
      静态变量属于类，也称为类变量
      成员变量属于对象，也称为实例变量
2）内存中位置不同
      静态变量存在方法区
      成员变量存在堆中
3）出现的时间不同
      静态变量随着类的加载而加载，随着类的消亡而消亡
      成员变量随着对象的创建而创建，随着对象的消失而消失
4）调用方式不同
      静态变量通过类名调用，也可以通过对象名调用（不建议）
      成员变量只能通过对象名调用
所以，成员变量可以称为对象的特有数据，静态变量称为对象的共享数据

成员变量与局部变量的区别
1）在类中的位置不同
       成员变量：在类中方法外面
       局部变量：在方法或者代码块中，或者方法的声明上（即在参数列表中）
2）在内存中的位置不同，可以看看Java程序内存的简单分析
       成员变量：在堆中（方法区中的静态区）
       局部变量：在栈中
3）生命周期不同
      成员变量：随着对象的创建而存在，随着对象的消失而消失
      局部变量：随着方法的调用或者代码块的执行而存在，随着方法的调用完毕或者代码块的执行完毕而消失
4）初始值
      成员变量：有默认初始值
      局部变量：没有默认初始值，使用之前需要赋值，否则编译器会报错（The local variable xxx may not have been initialized）

```java
package se01.day02;

//子父类静态代码块、构造代码块、构造方法
class Fu{
	String name;
	int age;
	

	{
		System.out.println("构造代码块Fu");
	}
	
	static{
		System.out.println("静态代码块Fu");
	}
	
	public Fu() {
		System.out.println("无参构造方法Fu");
	}
	 
	public Fu(String name, int age) {
		this.name = name;
		this.age = age;
		System.out.println("有参构造Fu");
	}

}
public class Zi extends Fu{
	int id;
	{
		System.out.println("构造代码块Zi");
	}
	static{
		System.out.println("静态代码块Zi");
	}
	public Zi() {
		System.out.println("无参构造方法Zi");
	}

	public Zi(String name, int age) {
		this.name = name;
		this.age = age;
		System.out.println("有参构造Zi");
	}
	public static void main(String[] args) {
		new Zi("小明",13);
	}

}

==========================执行结果为====================================
静态代码块Fu
静态代码块Zi
构造代码块Fu
无参构造方法Fu
构造代码块Zi
有参构造Zi

```

static特殊用法(static修饰类)：  如果一个类要被声明为static的，只有一种情况，就是静态内部类。如果在外部类声明为static，程序会编译都不会过。（在内部类中详细讲解）

Question：在什么情况下需对属性和方法加上static关键字？

在编写的代码中，static定义的属性出现几率不是特别高，一般只有在描述共享属性概念或者是不受实例化对象限制的属性时才会使用static定义属性，而大部分情况下依然都使用非static属性。

产生实例化对象是因为在堆内存中可以保存属性信息，所以如果一个类中没有属性产生，就自然也没有必要去开辟堆内存保存属性内容了，所以这个时候就可以考虑类中的方法全部使用static声明。

```java
NOTICE:在JDK1.7之前，Java一直存在一个Bug，可以先执行静态代码块来代替主方法。按照标准来说，所有的程序应该都是从主方法开始执行，但是下例却先执行静态代码块

public static void main(String[] args) {
		System.out.println("你好,世界");
	}
	

	static{
		System.out.println("Hello World");
	}

===========输出结果为==============
Hello World
你好,世界
//jdk18
    package Test;

public class Test1 {
    public static void main(String[] args) {
        System.out.println("这里是主方法");
    }
    static {
        System.out.println("这里是静态代码块");
    }


}
//console
这里是静态代码块
这里是主方法
```



### 关键字：final★

![image-20220801212119661](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212119661.png)

**final关键字：**

表示最终的意思，可以修饰类、成员变量、成员方法

- 修饰类：类不可以被继承
- 修饰成员变量：变量为常量，值不可以改变
- 修饰成员方法：方法不能被重写
- final还可以修饰局部变量：①修饰基本数据类型，值不能改变；②修饰引用数据类型，地址值不能改变；指向的对象的内容是可变的

**final 关键字，意思是最终的、不可修改的，最见不得变化 ，用来修饰类、方法和变量，具有以下特点：**

1. final 修饰的类不能被继承，final 类中的所有成员方法都会被隐式的指定为 final 方法；
2. final 修饰的方法不能被重写；
3. final 修饰的变量是常量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改；如果是引用类型的变量，则在对其初始化之后便不能让其指向另一个对象。

说明：使用 final 方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。在早期的 Java 实现版本中，会将 final 方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升（现在的 Java 版本已经不需要使用 final 方法进行这些优化了）。类中所有的 private 方法都隐式地指定为 final。

### 关键字：this★

this 关键字用于引用类的当前实例。 例如：



```java
class Manager {
    Employees[] employees;
    void manageEmployees() {
        int totalEmp = this.employees.length;
        System.out.println("Total employees: " + totalEmp);
        this.report();
    }
    void report() { }
}
```

在上面的示例中，this 关键字用于两个地方：

- this.employees.length：访问类 Manager 的当前实例的变量。
- this.report（）：调用类 Manager 的当前实例的方法。

此关键字是可选的，这意味着如果上面的示例在不使用此关键字的情况下表现相同。 但是，使用此关键字可能会使代码更易读或易懂。

### 关键字：super★

super 关键字用于从子类访问父类的变量和方法。 例如：



```java
public class Super {
    protected int number;
    protected showNumber() {
        System.out.println("number = " + number);
    }
}
public class Sub extends Super {
    void bar() {
        super.number = 10;
        super.showNumber();
    }
}
```

在上面的例子中，Sub 类访问父类成员变量 number 并调用其父类 Super 的 `showNumber（）` 方法。

**使用 this 和 super 要注意的问题：**

- 在构造器中使用 `super()` 调用父类中的其他构造方法时，该语句必须处于构造器的首行，否则编译器会报错。另外，this 调用本类中的其他构造方法时，也要放在首行。
- this、super 不能用在 static 方法中。

**简单解释一下：**

被 static 修饰的成员属于类，不属于单个这个类的某个对象，被类中所有对象共享。而 this 代表对本类对象的引用，指向本类对象；而 super 代表对父类对象的引用，指向父类对象；所以， **this 和 super 是属于对象范畴的东西，而静态方法是属于类范畴的东西**



**this与super关键字：**

1、this关键字代表当前对象

2、super可以理解为是指向自己超（父）类对象的一个指针，而这个超类指的是离自己最近的一个父类。  

 this与super对比

this.属性 操作当前对象的属性
this.方法 调用当前对象的方法 
引用构造函数：调用本类中另一种形式的构造函数（应该为构造函数中的第一条语句）。
普通的直接引用：与this类似，super相当于是指向当前对象的父类，这样就可以用super.xxx来引用父类的成员。
子类中的成员变量或方法与父类中的成员变量或方法名同名时，表示调用父类的成员
引用构造函数：调用父类中的某一个构造函数（应该为构造函数中的第一条语句）。默认在构造函数第一条语句是“super();”，无论写与否。
super(参数)：调用基类中的某一个构造函数（应该为构造函数中的第一条语句）
this(参数)：调用本类中另一种形成的构造函数（应该为构造函数中的第一条语句）
调用super()必须写在子类构造方法的第一行，否则编译不通过。每个子类构造方法的第一条语句，都是隐含地调用 super()，如果父类没有这种形式的构造函数，那么在编译的时候就会报错。
super() 和 this() 类似,区别是，super() 从子类中调用父类的构造方法，this() 在同一类内调用其它方法。
super() 和 this() 均需放在构造方法内第一行。
尽管可以用this调用一个构造器，但却不能调用两个。
this 和 super 不能同时出现在一个构造函数里面，因为this必然会调用其它的构造函数，其它的构造函数必然也会有 super 语句的存在，所以在同一个构造函数里面有相同的语句，就失去了语句的意义，编译器也不会通过。
this() 和 super() 都指的是对象，所以，均不可以在 static 环境中使用。包括：static 变量,static 方法，static 语句块。
从本质上讲，this 是一个指向本对象的指针, 然而 super 是一个 Java 关键字。

### 关键字：package、import

### 关键字：new

![image-20220801212139526](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212139526.png)

### 关键字：instanceof★

![image-20220801212707153](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212707153.png)
![image-20220801212735082](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212735082.png)![image-20220801213050770](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213050770.png)

![image-20220801212342005](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212342005.png)


### 关键字：extends★

![image-20220801213236011](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213236011.png)

```
**1. 只看尖括号里边的！！明确点和范围两个概念\
**2. 如果尖括号里的是一个类，那么尖括号里的就是一个点，比如List<A>,List<B>,List<Object>\
**3. 如果尖括号里面带有问号，那么代表一个范围，<? extends A> 代表小于等于A的范围，<? super A>代表大于等于A的范围，<?>代表全部范围
4. 尖括号里的所有点之间互相赋值都是错，除非是俩相同的点
5. 尖括号小范围赋值给大范围，对，大范围赋值给小范围，错。如果某点包含在某个范围里，那么可以赋值，否则，不能赋值
6. List<?>和List 是相等的，都代表最大范围
**7.补充：List既是点也是范围，当表示范围时，表示最大范围**
public static void main(String[] args) {
        List<A> a;
        List list;
        list = a;   //A对，因为List就是List<?>，代表最大的范围，A只是其中的一个点，肯定被包含在内
        List<B> b;
        a = b;      //B错，点之间不能相互赋值
        List<?> qm;
        List<Object> o;
        qm = o;     //C对，List<?>代表最大的范围，List<Object>只是一个点，肯定被包含在内
        List<D> d;
        List<? extends B> downB;
        downB = d;  //D对，List<? extends B>代表小于等于B的范围，List<D>是一个点，在其中
        List<?extends A> downA;
        a = downA;  //E错，范围不能赋值给点
        a = o;      //F错，List<Object>只是一个点
        downA = downB;  //G对，小于等于A的范围包含小于等于B的范围，因为B本来就比A小，B时A的子类嘛
    }
```

![image-20220801213151442](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213151442.png)

### 关键字：native

![image-20220801212129798](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801212129798.png)

## 继承和多态

**多态存在的三个必要条件**

- 继承
- 重写
- 父类引用指向子类对象
- **多态的访问方式：**
  (1)成员变量
     编译看左边，运行看左边
  (2)成员方法
     编译看左边，运行看右边
  (3)静态方法
     编译看左边，运行看左边

### **继承体系初始化**（子父类）

**在许多加载机制中，加载子类必须先加载父类，加载伴随着初始化，所以子类初始化前会先执行父类的初始化:**

**子类重写父类方法时访问权限只能增大不能减小**

**一个对象实例化过程：**

　　Person p = new Person();
　　1，JVM会读取指定的路径下的Person.class文件，并加载进内存，
    　　并会先加载Person的父类(如果有直接的父类的情况下).
　　2，在堆内存中的开辟空间，分配地址。
　　3，并在对象空间中，对对象中的属性进行默认初始化。
　　4，调用对应的构造函数进行初始化。
　　5，在构造函数中，第一行会先到调用父类中构造函数进行初始化。
　　6，父类初始化完毕后，在对子类的属性进行显示初始化。
　　7，在进行子类构造函数的特定初始化。
　　8，初始化完毕后，将地址值赋值给引用变量.

![image-20220911094616796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220911094616796.png)

```java
/**
 @author EddieZhang
 @create 2022-09-11 9:39
 */
public class StaticBlockTest {
    public static void main(String[] args) {
        System.out.println("******************************Person person = new Eddie();******************************");
    Person person = new Eddie();
        //我是父类的static代码块
        //我是子类的static代码块
        //我是父类的非static代码块
        //我是父类空参构造器
        //我是子类的非static代码块
        //我是子类的空参构造器
        System.out.println("******************************person.sleep();******************************");
    person.sleep();//我是子类的sleep方法
//        person.programming();编译不通过 编译时看左边 运行时看右边
        System.out.println("******************************Eddie eddie = new Eddie();******************************");
        Eddie eddie = new Eddie();
        System.out.println("******************************eddie.programming();******************************");
        eddie.programming();
        System.out.println("******************************eddie.sleep();******************************");
        /*
                @Override
            public void sleep() {
                super.sleep();
                System.out.println("我是子类的sleep方法");
            }
         */
        eddie.sleep();
        //我是父类的sleep方法
        //我是子类的sleep方法
        /*
        console显示
        ******************************Person person = new Eddie();******************************
        我是父类的static代码块
        我是子类的static代码块
        我是父类的非static代码块
        我是父类空参构造器
        我是子类的非static代码块
        我是子类的空参构造器
        ******************************person.sleep();******************************
        我是父类的sleep方法
        我是子类的sleep方法
        ******************************Eddie eddie = new Eddie();******************************
        我是父类的非static代码块
        我是父类空参构造器
        我是子类的非static代码块
        我是子类的空参构造器
        ******************************eddie.programming();******************************
        我是子类的programming方法
        ******************************eddie.sleep();******************************
        我是父类的sleep方法
        我是子类的sleep方法

        Process finished with exit code 0

        */

    }

}
class Eddie extends Person{
    private String major;
    static String homeAddress;
    static {
        System.out.println("我是子类的static代码块");
    }
    {
        System.out.println("我是子类的非static代码块");
    }

    public Eddie() {
        System.out.println("我是子类的空参构造器");
    }

    public Eddie(String major) {
        this.major = major;
        System.out.println("我是子类的有参构造器");
    }

    public Eddie(String name, String gender, int age, String major) {
        super(name, gender, age);
        this.major = major;
        System.out.println("我是子类的全参构造器");
    }

    @Override
    public void sleep() {
        super.sleep();
        System.out.println("我是子类的sleep方法");
    }
    public void programming(){
        System.out.println("我是子类的programming方法");
    }

    @Override
    public String toString() {
        return "Eddie{" +
                "major='" + major + '\'' +
                '}';
    }

    public String getMajor() {
        return major;
    }

    public void setMajor(String major) {
        this.major = major;
    }

    public static String getHomeAddress() {
        return homeAddress;
    }

    public static void setHomeAddress(String homeAddress) {
        Eddie.homeAddress = homeAddress;
    }
}
class Person{
    private String name;
    private String gender;
    private int age;
    static String nation;
    static {
        nation = "China";
        System.out.println("我是父类的static代码块");
    }
    {
        System.out.println("我是父类的非static代码块");
    }

    public Person() {
        System.out.println("我是父类空参构造器");
    }

    public Person(String name, String gender, int age) {
        this.name = name;
        this.gender = gender;
        this.age = age;
        System.out.println("我是父类带参构造器");
    }
    public void sleep(){
        System.out.println("我是父类的sleep方法");
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", gender='" + gender + '\'' +
                ", age=" + age +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getGender() {
        return gender;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public static String getNation() {
        return nation;
    }

    public static void setNation(String nation) {
        Person.nation = nation;
    }
}
```



## object类

![image-20220801215135656](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801215135656.png)
![image-20220801215147911](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801215147911.png)

## 重载和重写

![image-20220924133558144](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924133558144.png)
![image-20220924133652037](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924133652037.png)

![image-20220801213454436](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801213454436.png)

### 重载的本质

> 方法重载的要求是**两同一不同**：**同一个类中方法名相同**，**参数列表不同**。至于方法的其他部分，如方法返回值类型、修饰符等，与方法重载没有任何关系
>
> **重载就是同一个类中多个同名方法根据不同的传参来执行不同的逻辑处理（与返回值无关）。**

### 重写的本质

> **重写就是子类对父类方法的重新改造，外部样子不能改变，内部逻辑可以改变。**
>
> **方法名、参数列表必须相同**，子类方法返回值类型应比父类方法返回值类型更小或相等，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类。
>
> 如果父类方法访问修饰符为 `private/final/static` 则子类就不能重写该方法，但是被 `static` 修饰的方法能够被再次声明。
>
> 构造方法无法被重写
>



在重写方法时，需要**遵循下面的规则**：
总结：**参数列表相同**，**返回值类型小于或等于**，**访问权限大于或等于**，**抛出异常小于或等于**。

- 参数列表必须完全与被重写的方法**参数列表相同**。
- **返回的类型**必须与被重写的方法的返回类型相同（[Java](http://c.biancheng.net/java/)1.5 版本之前返回值类型必须一样，之后的 Java 版本放宽了限制，**返回值类型必须小于或者等于父类方法的返回值类型**）。
- 访问权限不能比父类中被重写方法的访问权限更低（public>protected>default>private）。
- 重写方法一定**不能抛出新的检査异常或者比被重写方法声明更加宽泛的检査型异常**。例如，父类的一个方法声明了一个检査异常 IOException，在重写这个方法时就不能抛出 Exception，只能拋出 IOException 的子类异常，可以抛出非检査异常。


另外还要注意以下几条：

- 重写的方法可以使用 @Override 注解来标识。
- 父类的成员方法只能被它的子类重写。
- 声明为 final 的方法不能被重写。
- 声明为 static 的方法不能被重写，但是能够再次声明。
- 构造方法不能被重写。
- 子类和父类在同一个包中时，子类可以重写父类的所有方法，除了声明为 private 和 final 的方法。
- 子类和父类不在同一个包中时，子类只能重写父类的声明为 public 和 protected 的非 final 方法。
- 如果不能继承一个方法，则不能重写这个方法。

![image-20220924133018523](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924133018523.png)

![image-20220924133027962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220924133027962.png)

## 包装类

**包装后让基本数据类型有了类的特点，进而可以面向对象**

**J D K 1.5之后 自动装箱 自动拆箱**
**Integer类型在-128-->127范围之间是被缓存了的，也就是每个对象的内存地址是相同的，赋值就直接从缓存中取，不会有新的对象产生，而大于这个范围，将会重新创建一个Integer对象，也就是new一个对象出来，当然地址就不同了**

**使用Integer a = 1;或Integer a = Integer.valueOf(1); 在值介于-128至127直接时，作为基本类型。**

**使用Integer a = new Integer(1); 时，无论值是多少，都作为对象。**

![image-20220926084940989](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926084940989.png)

```java
public class IntegerTest {
    public static void main(String[] args) {
        Integer integer1= -128;
        Integer integer2 = Integer.valueOf("-128");
        Integer integer3 = new Integer(-128);
        System.out.println(integer1 == integer2);
        System.out.println(integer2 == integer3);
        //true
        //false
    }
}
public class IntegerTest {
    public static void main(String[] args) {
        Integer integer1= 127;
        Integer integer2 = Integer.valueOf("127");
        Integer integer3 = new Integer(127);
        System.out.println(integer1 == integer2);
        System.out.println(integer2 == integer3);
        //true
        //false
    }
}
public class IntegerTest {
    public static void main(String[] args) {
        Integer integer1= 128;
        Integer integer2 = Integer.valueOf("128");
        Integer integer3 = new Integer(127);
        System.out.println(integer1 == integer2);
        System.out.println(integer2 == integer3);
        //false
        //false
    }
}
```

![image-20220801214805820](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214805820.png)
![image-20220801214846894](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214846894.png)

![image-20220801214900510](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214900510.png)
![image-20220801214912881](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801214912881.png)
![image-20220801215116174](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801215116174.png)





## 抽象类（abstract）★

 **继承性** **多态性** 的体现

**关键字abstract修饰的类**

**抽象类是用来被继承的** 

**抽象类不能被实例化**

**抽象类中一定会有构造器，便于子类实例化时调用（涉及子类对象实例化的全过程）**

**抽象(abstract)不能与那些关键字共存？**
1).**private** :因为一个abstract方法需要被重写，所以不能修饰为private;
2).**final**:因为一个abstract方法需要被重写。被final修饰的方法是不能被重写的，所以不能同final共存；
3).**static**:因为一个abstract方法没有方法体。静态方法需要对方法体执行内容分配空间，所以不能同static共存；（abstract是没有实现  的，不能产生对象，而是static是属于类的，类本身是已经存在的对象）
4).**synchronized**: 是同步的，然而同步需要具体的操作才能同步，但， abstract是只有声明没有实现的（即，使用synchronized关键字的是需要有具体的实现同步的操作的，但是使用abstract是只有声明而没有实现的，这样就产生了冲突）
5).**native**:他们本身的定义就是冲突的，native声明的方法是移交本地操作系统实现的，而abstract是移交子类对象实现的，同时修饰的话，导致不知道谁实现声明的方法

**特点：**
   1）抽象类不一定有抽象方法，但是有抽象方法的类一定是抽象类
   2）抽象类不可以实例化(不能用new关键字创建抽象类实例)
   3）抽象类的子类，可以是抽象类，也可以是具体类。如果子类是具体类，需要重写抽象类里面所有抽象方法

![image-20220801204702947](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801204702947.png)

![image-20220801204639626](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801204639626.png)
![image-20220801205035129](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205035129.png)
![image-20220801205055170](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205055170.png)
![image-20220801205111037](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205111037.png)
![image-20220802152252928](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220802152252928.png)

![image-20220801205213793](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205213793.png)
其中 **code();** 为不确定的部分 就暴露出去让子类实现

## 接口（interface）★

[【创建型模式一】简单工厂(Simple Factory) - 简书 (jianshu.com)](https://www.jianshu.com/p/a9f397c4ff98)

![image-20220801205701804](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205701804.png)

![image-20220801205751749](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801205854534.png)
![image-20220801210132997](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210132997.png)
![image-20220801210148169](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210148169.png)
![image-20220801210206298](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210206298.png)
![image-20220801210233191](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210233191.png)
![image-20220801210413665](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210413665.png)
![image-20220801210445492](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210445492.png)

## 抽象类和接口的区别：

1. 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。
2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 public static final 类型的。
3. 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

## 包

![image-20220801211312064](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211312064.png)
![image-20220801211334480](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211334480.png)
![image-20220801211352530](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211352530.png)

![image-20220801210744569](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210744569.png)
**Java包的命名规则是全部使用小写字母。**

![image-20220801210806970](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210806970.png)

![image-20220801210900754](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210900754.png)

![image-20220801210730185](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210730185.png)

![image-20220801210931512](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210931512.png)
![image-20220801211009338](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211009338.png)

![image-20220801210944003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801210944003.png)
![image-20220801211052263](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211052263.png)

**使用import关键字导入静态成员**

![image-20220801211128139](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220801211128139.png)



## 设计模式



# 应用程序开发★

## JDBC★

**（Java DataBase Connectivity）**

JDBC是一种可用于执行SQL语句的Java API

是连接**数据库**和Java应用程序的纽带

为什么要学习**数据库**
 **持久化**：将数据保存到可掉电式储存设备中以供后续使用。数据持久化意味着将内存中的数据保存到硬盘上加以“固化”。

**持久化的作用**：将内存中的数据储存在关系型数据库中。

### JDBC

**（Java Database Connectivity）& 数据库连接池**

#### JDBC概述

JDBC是一种可用于执行SQL语句的Java API（Application Programming Interface，应用程序设计接口），是连接数据库和Java应用程序的纽带

JDBC为访问不同的数据库提供了统一的接口，为使用者屏蔽了细节问题；

使用JDBC可以连接任何提供了JDBC驱动程序的数据库系统，从而可以完成对数据库的操作；

![image-20220907203413194](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220907203413194.png)

![image-20220907204147063](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220907204147063.png)

![image-20220907204209443](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220907204209443.png)

#### JDBC简单入门

**JDBC**的全称是Java DataBase Connectivity，是一套面向对象的应用程序接口，指定了统一的访问各种关系型数据库的标准接口。JDBC是一种底层的API，因此访问数据库时需要在业务逻辑层中嵌入SQL语句。SQL语句是面向关系的，依赖于关系模型，所以通过JDBC技术访问数据库也是面向关系的。JDBC技术主要完成以下几个任务：

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_ffa22309916341b98ab234a5bf966bb9.jpg)　与数据库建立一个连接。

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_1a7a1b578cda483d8f0bf78b20fc2d5a.jpg)　向数据库发送SQL语句。

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_dc2d26f461ae4a16987de3183fcd6492.jpg)　处理从数据库返回的结果。

需要注意的是，**JDBC并不能直接访问数据库**，必须**依赖于数据库厂商提供的JDBC驱动程序**。

##### JDBC程序编写的步骤

1.注册驱动————加载driver类

2.获取连接————得到Connection

3.执行增删改查——发送SQL 给mysql执行

4.释放资源————关闭相关的连接

```java
/**
 * JDBC--连接到mysql中的db01库中
 */
//前置工作--》将jar包复制粘贴到IDEA所用的项目下，放置jar包的目录可以是自己新建的，也可以和项目同在一个目录下。然后再：右键选择添加到add as Library下:
public class JavaConnectMysqlTest4 {
    @Test
    public void test() {
        Connection connection = null;
        Statement statement = null;
        try {
            //通过Properties对象Load配置信息（配置信息可以根据实际情况自行编辑）
            //user=root
			//password=root
			//url=jdbc:mysql://localhost:3306/db01?	rewriteBatchedStatements=TRUE
			//driver=com.mysql.cj.jdbc.Driver
            Properties properties = new Properties();
            properties.load(new FileInputStream(new File("src\\mysql.properties")));
            //获取配置文件信息内容
            String user = properties.getProperty("user");
            String password = properties.getProperty("password");
            String url = properties.getProperty("url");
            String driver = properties.getProperty("driver");
            //1.注册驱动--可以省略 建议写上
            Class.forName(driver);
            //2.取得连接
            connection = DriverManager.getConnection(url, user, password);
            //3.sql语句
            //3.1取得执行sql语句的对象
            statement = connection.createStatement();
            //3.2编写sql语句--执行sql语句
            int i = statement.executeUpdate("create table order2 (id int primary key auto_increment,`name` varchar(10) not null default '',`gender` enum ('男','女'))");//此处返回的是> Affected rows:
            int i1 = statement.executeUpdate("insert into order2 values (null,'EddieZhang','男'),(null,'Irving','男'),(null,'James','男')");//此处返回的是> Affected rows:
            if(i > 0){
                System.out.println("创建库指令完成~~");//创建表指令的//此处返回的是> Affected rows:为0 所有不会输出
            }
            if(i1 > 0){
                System.out.println("插入数据指令完成~~");//插入数据的指令//此处返回的是> Affected rows:大于0 会输出
            }
        } catch (IOException e) {
            throw new RuntimeException(e);
        } catch (ClassNotFoundException e) {
            throw new RuntimeException(e);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        //4.释放资源
            if (statement != null) {
                try {
                    statement.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
            if (connection != null) {
                try {
                    connection.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }
}
/**
 * 结果集 ResultSet
 *
 */
public class ResultSetTest {
    @Test
    public void test() throws IOException, ClassNotFoundException, SQLException {
        //连接到Mysql中的db01库中
        //根据获取配置文件信息的方法连接
        //通过Properties对象load配置文件信息（配置文件可以根据实际需求编写）
        Properties properties = new Properties();//new一个Properties对象
        properties.load(new FileInputStream(new File("src\\mysql.properties")));
        //对象调用getProperty（）方法获取相关值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");
        //1.注册驱动
        Class.forName(driver);
        //2.取得连接
        Connection connection = DriverManager.getConnection(url, user, password);
        //3.sql语句
        //获取执行sql语句的对象
        Statement statement = connection.createStatement();
        ResultSet resultSet = statement.executeQuery("select id,name,address from test1");//查询select语句调用executeQuery()方法会返回一个结果集ResultSet
        //想要获取ResultSet需要用到while循环
        while(resultSet.next()){//ResultSet对象中有next方法（读取每一行的列 如果遇到null行则返回false）一行接着下一行的读取
            int id = resultSet.getInt(1);//获取第某一列的值 要确定返回值类型
            String name = resultSet.getString(2);//获取第某一列的值 要确定返回值类型
            String address = resultSet.getString(3);//获取第某一列的值 要确定返回值类型
            System.out.println(id + "\t" + name + "\t" + address);
        }
        //4.释放资源
        resultSet.close();
        statement.close();
        connection.close();

    }
```

#### JDBC API★

##### DriverManager

建立一个指定到数据库的连接并返回一个Connection对象

```java
//方法
static Connection getConnection(String url,String user,String password)
//2.取得连接
        Connection connection = DriverManager.getConnection(url, user, password);//建立一个指定到数据库的连接并返回一个Connection对象
```

##### Connection

需要--.close（）

```java
//方法
Statement createStatement()
//创建Statement对象 可以用来执行sql语句
Statement statement = connection.createStatement();
```

##### PrepareStatement

需要--.close（）

解决Statement**存在sql注入风险**的方法：使用PrepareStatement（从Statement扩展而来）取代Statement

```java
//Statement

//需要--.close（）

//**存在sql注入风险**

//sql注入：利用某些系统没有对用户数据输入的数据进行充分的检测，而在输入数据中注入非法的sql语句段或命令，恶意攻击数据库
//方法
ResultSet executeQuery(String sqlQuery)
    //执行给定字符串中的sql语句，并返回一个用于查询结果的ResultSet对象
int executeUpdate(String sqlStatement)
    ///执行dml语句
long executeLargeUpdate(String sqlStatement)
    //执行字符串中指定的insert into，update，delete等sql语句还可以执行ddl语言如create table等 返回的是受影响的行数> Affected rows:
    //如果是没有更新计数的语句（受影响的行数为0）则返回0;
boolean execute(sql)
    //执行任意的语句 
```

```java
//PrepareStatement
//需要--.close（）
//方法
ResultSet executeQuery(String sqlQuery)
    //执行给定字符串中的sql语句，并返回一个用于查询结果的ResultSet对象
int executeUpdate(String sqlStatement)
    ///执行dml语句
long executeLargeUpdate(String sqlStatement)
    //执行字符串中指定的insert into，update，delete等sql语句还可以执行ddl语言如create table等 返回的是受影响的行数> Affected rows:
    //如果是没有更新计数的语句（受影响的行数为0）则返回0;
boolean execute(sql)
    //执行任意的语句 

/**
 * PrepareStatement
 * 解决Statement**存在sql注入风险**的方法：使用PrepareStatement（从Statement扩展而来）取代Statement
 */
public class PrepareStatementTest {
    @Test
    public void test() throws IOException, ClassNotFoundException, SQLException {
        Scanner scanner = new Scanner(System.in);
        System.out.print("请输入要查询的姓名:");
        String readName = scanner.nextLine();
        System.out.print("请输入要查询的姓别:");
        String readGender = scanner.nextLine();
        //通过Properties对象load相关的配置文件信息（根据需求可以编辑配置文件）
        Properties properties = new Properties();
        properties.load(new FileInputStream(new File("src\\mysql.properties")));
        //使用getProperty()方法得到配置文件中的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");
        //1.注册驱动
        Class.forName(driver);
        //2.取得连接
        Connection connection = DriverManager.getConnection(url, user, password);
        //3.sql语句
        PreparedStatement preparedStatement = connection.prepareStatement("select * from order2 where name = ? and gender = ?");//其中？是占位符
        //调用set xxx(第几个占位符)方法 给占位符设置值
        preparedStatement.setString(1,readName);
        preparedStatement.setString(2,readGender);

        ResultSet resultSet = preparedStatement.executeQuery();
        while(resultSet.next()){
            int id = resultSet.getInt(1);
            String name = resultSet.getString(2);
            String gender = resultSet.getString(3);
            System.out.println(id + "\t" + name + "\t" + gender);
        }
        //4.释放资源
        resultSet.close();
        preparedStatement.close();
        connection.close();
        scanner.close();
    }
}
```

##### ResultSet

需要--.close（）

```java
//方法
boolean next()
    //将结果集中的当前行向next移动一行。如果到达最后一行的后面，则返回false。初始情况下必须调此方法才能转到第一行
boolean previous()
    //将结果集中的当前行向prev移动一行。如果到达首行的前面，则返回false。
xxx getXxx(int columnNumber)
    //xxx表示数据类型 columnNumber表示第几列 返回的是此行中相对应的列信息
xxx getXxx(String columnLaber)
    //xxx表示数据类型 columnLabel – 使用 SQL AS 子句指定的列的标签。如果未指定 SQL AS 子句，则标签为列名 返回的是此行中相对应的列信息
    
/**
 * 结果集 ResultSet
 *
 */
public class ResultSetTest {
    @Test
    public void test() {
        Connection connection = null;
        Statement statement = null;
        ResultSet resultSet = null;//查询select语句调用executeQuery()方法会返回一个结果集ResultSet
        try {
            //连接到Mysql中的db01库中
            //根据获取配置文件信息的方法连接
            //通过Properties对象load配置文件信息（配置文件可以根据实际需求编写）
            Properties properties = new Properties();//new一个Properties对象
            properties.load(new FileInputStream(new File("src\\mysql.properties")));
            //对象调用getProperty（）方法获取相关值
            String user = properties.getProperty("user");
            String password = properties.getProperty("password");
            String driver = properties.getProperty("driver");
            String url = properties.getProperty("url");
            //1.注册驱动
            Class.forName(driver);
            //2.取得连接
            connection = DriverManager.getConnection(url, user, password);
            //3.sql语句
            //获取执行sql语句的对象
            statement = connection.createStatement();
            resultSet = statement.executeQuery("select id,name,address from test1");
            //想要获取ResultSet需要用到while循环
            while(resultSet.next()){//ResultSet对象中有next方法（读取每一行的列 如果遇到null行则返回false）一行接着下一行的读取
                int id = resultSet.getInt(1);//获取第某一列的值 要确定返回值类型
                String name = resultSet.getString(2);//获取第某一列的值 要确定返回值类型
                String address = resultSet.getString(3);//获取第某一列的值 要确定返回值类型
                System.out.println(id + "\t" + name + "\t" + address);
            }
        } catch (IOException e) {
            throw new RuntimeException(e);
        } catch (ClassNotFoundException e) {
            throw new RuntimeException(e);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        //4.释放资源
            if (resultSet != null) {
                try {
                    resultSet.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
            if (statement != null) {
                try {
                    statement.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
            if (connection != null) {
                try {
                    connection.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
        }

    }
}
```



#### JDBC Utils

封装JDBC Utils

在JDBC操作中，获取连接 和 释放资源 是频繁使用到的。可以将其封装至JDBC连接的工具类JDBC Utils中

```java
/**
 * JDBCUtils
 * 在JDBC操作中，获取连接 和 释放资源 是频繁使用到的。可以将其封装至JDBC连接的工具类JDBC Utils中
 */
public class JDBCUtils {
    //定义static的属性
    static String user;
    static String password;
    static String driver;
    static String url;

    //在静态代码块中初始化
    static {
        try {
            Properties properties = new Properties();
            properties.load(new FileInputStream(new File("src\\mysql.properties")));
            //获取配置文件的值并赋值给属性
            user = properties.getProperty("user");
            password = properties.getProperty("password");
            url = properties.getProperty("url");
            driver = properties.getProperty("driver");
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }
    //返回一个Connection连接
    public static Connection getConnection(){
        try {
            return DriverManager.getConnection(url,user,password);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }
    //资源释放的方法
    /*
     需要考虑到释放的资源 Connection connection, Statement statement, ResultSet resultSet
     */
    public static void closerResource(Connection connection, Statement statement, ResultSet resultSet){
        //判断是否为空 不为空时close()
        try {
            if(connection != null){
                connection.close();
            }
            if(statement != null){
                statement.close();
            }
            if(resultSet != null){
                resultSet.close();
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }


}
```

使用JDBCUtils测试

```java
/**
 * 测试创建的JDBCUtils工具类
 */
public class JDBCUtilsTest {
    @Test
    public void test(){
        Connection connection = null;
        PreparedStatement preparedStatement = null;
        try {
            //使用工具类JDBCUtils直接取得连接
            connection = JDBCUtils.getConnection();
            //sql语句
            preparedStatement = connection.prepareStatement("delete from order2 where id = ?");
            preparedStatement.setString(1,"1");
            int executeUpdate = preparedStatement.executeUpdate();
            if(executeUpdate > 0){
                System.out.println("sql语句执行成功~~");
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        //使用工具类JDBCUtils释放资源
        JDBCUtils.closerResource(connection,preparedStatement,null);
        }

    }
    
    /*
        测试select语句指令
     */
    @Test
    public void test1(){
        Connection connection = null;
        PreparedStatement preparedStatement = null;
        ResultSet resultSet = null;
        try {
            //使用工具类JDBCUtils直接取得连接
            connection = JDBCUtils.getConnection();
            //sql语句
            preparedStatement = connection.prepareStatement("select * from order2 where id between ? and ?");
            preparedStatement.setInt(1,2);
            preparedStatement.setInt(2,4);
            resultSet = preparedStatement.executeQuery();
            while(resultSet.next()){
                int id = resultSet.getInt("id");
                String name = resultSet.getString("name");
                String gender = resultSet.getString("gender");
                System.out.println(id + "\t" + name + "\t" + gender);
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        ////使用工具类JDBCUtils释放资源
        JDBCUtils.closerResource(connection,preparedStatement,resultSet);
        }

    }
}
```

#### 事务★

**ACID**

**事务是必须满足4个条件（ACID）：**

**原子性（Atomicity，或称不可分割性）**、**一致性（Consistency）**、**隔离性（Isolation，又称独立性）**、**持久性（Durability）**。

**原子性：**一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。

**一致性：**在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。

**隔离性：**数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。

**隔离级别：事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。**

**持久性：**事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。

![image-20220909160456888](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220909160456888.png)

**关闭默认值**

JDBC对事物进行编程：默认情况下，数据库连接处于自动提交模式（auto commit mode）即每个sql语句一旦被执行便被提交到数据库。一旦命令被提交，就无法进行回滚（rollback）操作。使用事物时，需要：**connection.setAutoCommit(false)**

![image-20220909160810847](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220909160810847.png)

**保存点**

![image-20220909160905942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220909160905942.png)

```java
/**
 * Transaction事物
 * JDBC对事物进行编程：
 * 默认情况下，数据库连接处于自动提交模式（auto commit mode）即每个sql语句一旦被执行便被提交到数据库。
 * 一旦命令被提交，就无法进行回滚（rollback）操作。使用事物时，需要：**connection.setAutoCommit(false)**
 */
public class TransactionTest {
    @Test
    public void test() {
        Connection connection = null;
        PreparedStatement preparedStatement = null;
        PreparedStatement preparedStatement1 = null;
        try {
            connection = JDBCUtils.getConnection();//通过JDBCUtils取得连接
            connection.setAutoCommit(false);//setAutoCommit(false)
            //sql语句
            preparedStatement = connection.prepareStatement("update account set balance = balance - 100 where name = '张锦豪'");
            preparedStatement = connection.prepareStatement("update account set balance = balance + 100 where name = '欧文'");
            int executeUpdate = preparedStatement.executeUpdate();
            if (executeUpdate > 0) {//
                System.out.println("sql语句执行成功~~");
            }

                connection.commit();//提交事物（事物一旦提交 就不能在进行回滚操作）

        } catch (SQLException e) {//如果在执行过程中发生了异常 就进行回滚
            try {
                connection.rollback();//回滚操作
            } catch (SQLException ex) {
                throw new RuntimeException(ex);
            }
            throw new RuntimeException(e);
        } finally {//释放资源
            if (preparedStatement != null) {
                try {
                    preparedStatement.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
            if (preparedStatement1 != null) {
                try {
                    preparedStatement1.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
            if (connection != null) {
                try {
                    connection.close();
                } catch (SQLException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }
}
```

#### 批处理

![image-20220909164619398](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220909164619398.png)

**JDBC连接Mysql时，使用批处理功能需要在url中添加参数:rewriteBatchedStatements=ture**

**常用方法**：

**addBatch()	:添加需要批量处理的sql语句或参数**

**executeBatch()	:执行批量处理语句**

**clearBatch()	:清空批处理包的语句**

Tip：**通常搭配prepareStatement使用**

```java
/**
 * batch
 * 批量处理
 */
public class BatchTest {
    /*
     * @Description 未使用batch批处理进行测试
     * @Author EddieZhang
     * @Date 2022/9/9 17:05
     * @Since version-1.0
     */
    @Test
    public void noBatchTest() throws SQLException {
        Connection connection = JDBCUtils.getConnection();
        long start = System.currentTimeMillis();
        String str = "insert into admin values (null,?,?)";
        PreparedStatement preparedStatement = connection.prepareStatement(str);
        int i1 = 0;
        for(int i  = 0;i < 10000;i++){
            preparedStatement.setString(1,"Eddie" + i);
            preparedStatement.setString(2,"password" + i);
            i1 = preparedStatement.executeUpdate();
        }
        if(i1 > 0){
            System.out.println("sql执行成功~~");
        }

        long end = System.currentTimeMillis();

        System.out.println("本次执行用时 " + (end - start) + "秒~~");
        preparedStatement.close();
        connection.close();


    }
    
    /*
     * @Description 使用batch批处理进行测试
     * @Author EddieZhang
     * @Date 2022/9/9 17:06
     * @Since version-1.0
     */
    @Test
    public void BatchTest() throws Exception{
        Connection connection = JDBCUtils.getConnection();
        long start = System.currentTimeMillis();
        String str = "insert into admin values (null,?,?)";
        PreparedStatement preparedStatement = connection.prepareStatement(str);

        for(int i  = 0;i < 100000;i++){
            preparedStatement.setString(1,"Eddie" + i);
            preparedStatement.setString(2,"password" + i);
            preparedStatement.addBatch();//将执行语句添加至Batch
            /*
                将sql语句放入批处理包中 源码分析--批量处理会减少我们发送 sql 语句的网络开销，而且减少编译次数，因此效率提高
                      ①创建一个Arraylist elementData=>Object[]
                      ②elementData=>Object[]（初始容量为10）存放preparedStatement预处理的sql语句
                      ③elementData=>Object[]（初始容量为10）满后就进行1.5倍扩容
                      ④当添加到指定的值后就进行executeBatch
             */
            if((i + 1) % 1000 == 0){//当执行的sql语句达到1000条时就批量执行一次
                preparedStatement.executeBatch();
                preparedStatement.clearBatch();//执行完之后要清空
            }
        }


        long end = System.currentTimeMillis();

        System.out.println("本次执行用时 " + (end - start) + "秒~~");
        preparedStatement.close();
        connection.close();
    }
}
```

#### 连接池★

**优点总结：**

**提高程序相应速度	减少了创建连接的相应时间**

**可重复使用	降低资源消耗**

**便于连接管理 可以配置相关参数**



![image-20220910200657635](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910200657635.png)

**解决传统开发中的数据连接问题，采用数据库连接池（connection pool）技术**

![image-20220910194217104](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910194217104.png)

**JDBC的数据库连接池**使用 java.sql.DataSource 来表示，DataSource只是一个接口，该接口通常由第三方提供实现【提供.jar】

**数据库连接池：**	**C3P0**	DBCP	Proxool	BoneCP	**Druid**（荐）

![image-20220910194417198](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910194417198.png)

C3P0

```java
/**
 * C3P0
 */
@SuppressWarnings(value = "all")//抑制警告
public class ConnectionPoolC3P0Test {
    /*
        方式一：
        在程序中指定相关参数
     */
    @Test
    public void C3P0Test() throws IOException, PropertyVetoException, SQLException {
        //创建一个数据源对象ComboPooledDataSource
        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();

        //通过配置文件获取相关连接信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String url = properties.getProperty("url");
        String driver = properties.getProperty("driver");

        //给数据源配置相关参数
        comboPooledDataSource.setDriverClass(driver);
        comboPooledDataSource.setJdbcUrl(url);
        comboPooledDataSource.setUser(user);
        comboPooledDataSource.setPassword(password);

        //设置初始化连接数以及最大连接数
        comboPooledDataSource.setInitialPoolSize(10);//设置初始化连接数
        comboPooledDataSource.setMaxPoolSize(50);//最大连接数

        //测试与数据库进行5000次连接
        long start = System.currentTimeMillis();
        for (int i = 0; i < 5000; i++) {
            Connection connection = comboPooledDataSource.getConnection();//getConnection()方法实现了DataSource接口
            connection.close();//关闭连接
        }
        long end = System.currentTimeMillis();
        System.out.println("本次运行用时:" + (end - start) + "毫秒");
    }

    /*
        方式二 通过配置文件
     */
    @Test
    public void C3P0Test1() throws SQLException {
        ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource("DataSource");
        long start = System.currentTimeMillis();
        for (int i = 0; i < 500000; i++) {
        Connection connection = comboPooledDataSource.getConnection();
        connection.close();
        }
        long end = System.currentTimeMillis();
        System.out.println("本次运行共计用时:" + (end - start) + "毫秒");
        //本次运行共计用时:772毫秒
    }
}
```

**Druid**（荐）

```java
/**
 * Druid
 */
public class ConnectionPoolDruidTest {
    @Test
    public void DruidTest() throws Exception {
        //使用Properties对象load相关配置文件信息
        Properties properties = new Properties();
        properties.load(new FileInputStream(new File("src\\druid.properties")));
        //使用DruidDataSourceFactory去createDataSource得到DataSource获取Druid的连接池
        DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
        //使用DataSource得到连接
        long start = System.currentTimeMillis();
        for (int i = 0; i < 500000; i++) {
            Connection connection = dataSource.getConnection();
            connection.close();
        }
        long end = System.currentTimeMillis();
        System.out.println("本次运行用时共" + (end - start) + "毫秒");


    }

    /**
     * 使用JDBCUtilsByDruid
     */
    @Test
    public void ConnectionPoolDruidTest() {
        long start = System.currentTimeMillis();
        for (int i = 0; i < 500000; i++) {
            Connection connection = JDBCUtilsByDruid.getConnection();//运行类型class com.alibaba.druid.pool.DruidPooledConnection
            try {
                connection.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
        long end = System.currentTimeMillis();

        System.out.println("本次运行共计用时:" + (end - start) + "毫秒");
    }
}

//JDBCUtilsByDruid
/**
 @author EddieZhang
 @create 2022-09-10 21:18
 */
@SuppressWarnings(value = "all")
public class JDBCUtilsByDruid {
    private static DataSource ds;

    //在静态代码块中完成ds的初始化
    static {
        Properties properties = new Properties();
        try {
            properties.load(new FileInputStream(new File("src\\druid.properties")));
            ds = DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            throw new RuntimeException(e);
        }

    }
    //getConnection的方法
    public static Connection getConnection(){
        try {
            return ds.getConnection();
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }
    //关闭连接--仅仅是把连接放回到连接池中   而不是真正的 断掉连接
    public static void close(ResultSet resultSet, Statement statement,Connection connection){
        if(resultSet != null){
            try {
                resultSet.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
        if(statement != null){
            try {
                statement.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
        if (connection != null){
            try {
                connection.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```

#### Apache---DB Utils

**commons-dbutils 是Apache 组织提供的一个开源的JDBC工具类，它是对JDBC的封装，使用dbutils能极大的简化JDBC编码的工作量**

**QueryRunner类:**该类封装了SQL的执行，是线程安全的。可以实现 增删改查插 批处理 

**使用QueryRunner类实现查询**

**ResultSetHandler**接口:该接口用于处理 java.sql.ResultSet,将数据按要求转换成为另一种形式

![image-20220910230004003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910230004003.png)

![image-20220910224405377](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220910224405377.png)

**将数据库中的每一条记录封装成对应的对象时 是通过反射机制 调用对象类的空参构造器 通过setXxx方法将数据库中的相应列赋值给类的属性**

![image-20220920184418130](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920184418130.png)

**tip：字段名需要和数据库表中的列名一致 如果出现重名的属性 可以通过sql语句中给数据库的列 as 别名 的方式**

```java
/**
 * Apache的DBUtils工具类 + druid（连接池） 完成对表的crud
 */
@SuppressWarnings(value = "all")
public class ApacheDBUtilsTest {
    @Test
    public void test() {
        Connection connection = null;
        try {
            //得到连接（druid）
            connection = JDBCUtilsByDruid.getConnection();
            //使用DBUtils 类和接口
            //创建QueryRunner类--该类封装了SQL的执行，是线程安全的。可以实现 增删改查插 批处理
            QueryRunner queryRunner = new QueryRunner();
            String sql = "select id,name,sex,borndate from actor where id >= ?";
            /*
                query方法就是执行sql语句，得到resultset --- 封装到 --> ArrayList 集合中 并返回集合
                形参列表解读
                query(Connection conn, String sql, ResultSetHandler<T> rsh, Object... params)

                Connection conn:连接
                String sql:sql语句
                ResultSetHandler<T> rsh:new BeanListHandler<>(Actor.class)将resultset -> Actor对象 -> 封装到ArrayList中
                    //底层用到反射机制 获取Actor的属性 然后进行封装
                Object... params:？的赋值 是可变形参 可以根据第几个(占位符)?进行赋值

                底层会自动关闭resultset资源以及prepareStaement资源
             */
            List<Actor> list = queryRunner.query(connection, sql, new BeanListHandler<>(Actor.class), 1);
            for (Actor actor :
                    list) {
                System.out.println(actor);
                //Actor{id=1, name='张锦豪', sex='男', borndate=2000-12-07, phone='null'}//可以指定查询列 没有查询的列就默认返回null
                //Actor{id=2, name='欧文', sex='男', borndate=1989-02-05, phone='null'}
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        //关闭资源（只用关闭connection）
        JDBCUtilsByDruid.close(null,null,connection);
        }


    }
}
```

```java
/*

* 分析 queryRunner.query 方法:
* public <T> T query(Connection conn, String sql, ResultSetHandler<T> rsh, Object... params) throws
SQLException {
* PreparedStatement stmt = null;//定义 PreparedStatement
* ResultSet rs = null;//接收返回的 ResultSet
* Object result = null;//返回 ArrayList
*
* try {
* stmt = this.prepareStatement(conn, sql);//创建 PreparedStatement
* this.fillStatement(stmt, params);//对 sql 进行 ? 赋值
* rs = this.wrap(stmt.executeQuery());//执行 sql,返回 resultset
* result = rsh.handle(rs);//返回的 resultset --> arrayList[result] [使用到反射，对传入 class 对象
                处理]
* } catch (SQLException var33) {
* this.rethrow(var33, sql, params);
* } finally {
* try {
* this.close(rs);//关闭 resultset
                            * } finally {
* this.close((Statement)stmt);//关闭 preparedstatement 对象
* }
* }
*
* return result;
* }
*/
```

```java
    /**
     * 使用Apache-DBUtils + Druid 完成 返回的结果是单行记录 （单个对象）
     */
    @Test
    public void test1(){
        Connection connection = null;
        try {
            //得到连接
            connection = JDBCUtilsByDruid.getConnection();
            //使用DBUtils 接口和类
            QueryRunner queryRunner = new QueryRunner();
            String sql = new String("select * from actor where id = ?");
            Actor query = queryRunner.query(connection, sql, new BeanHandler<>(Actor.class), 1);//返回的结果是单行记录 （单个对象）使用形参列表中使用的Handler 为new BeanHandler<>(Actor.class)
            System.out.println(query);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);//释放资源
        }

    }
    /**
     * 使用Apache-DBUtils + Druid 完成 返回的结果是单行单列的 返回的就是Object对象
     */
    @Test
    public void test2(){
        Connection connection = null;//取得连接
        try {
            connection = JDBCUtilsByDruid.getConnection();
            QueryRunner queryRunner = new QueryRunner();
            String sql = new String("select name from actor where id = ?");
            Object query = queryRunner.query(connection, sql, new ScalarHandler<>(), 2);//回的结果是单行单列的 返回的就是Object对象 使用形参列表中使用的Handler 为new ScalarHandler<>()
            System.out.println(query);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }


    }
}
```

```java
/**
     * 使用Apache-DBUtils + Druid 完成DML操作 update delete insert into
     */
    @Test
    public void test4(){
        Connection connection = null;
        try {
            //取得连接
            connection = JDBCUtilsByDruid.getConnection();
            //使用DBUtils的接口和类 执行sql语句
            QueryRunner queryRunner = new QueryRunner();
//            String sql = new String("update actor set name = ? where id = ?");
//            String sql1 = new String("insert into actor values (null,?,?,?,?)");
            String sql2 = new String("delete from actor where name = ?");

            //执行dml的queryRunner.update()
            //返回的结果是受影响的行数
//            int affectedRows = queryRunner.update(connection, sql, "Eddie", 1);
//            int affectedRows1 = queryRunner.update(connection, sql, "Irving", 2);
            int i = queryRunner.update(connection,sql2,"James");
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }


    }
```

#### DAO 增删改查--BasicDao★

**DAO(data access object) 数据访问对象**

这样的通用类称为BasicDao，是专门和数据库交互的，即完成对数据库表（表）的crud操作；

在BasicDao的基础上，实现一张表对应一个Dao，更好的完成功能

![image-20220911211022034](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220911211022034.png)

![image-20220919215714822](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220919215714822.png)

```java
/**
 * 开发BasicDAO 是其他DAO的父类
 *
 */
public class BasicDAO<T> {//泛型指定具体的类型
    private QueryRunner queryRunner = new QueryRunner();

    public int create(String sql){
        Connection connection = JDBCUtilsByDruid.getConnection();
        try {
            return queryRunner.update(connection,sql);
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }
    }

    //开发通用的呃dml方法
    public int update(String sql,Object... parameters){//形参列表传入sql语句 以及相关的参数
        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            int i = queryRunner.update(connection,sql, parameters);
            return i;
        } catch (Exception e) {
            throw new RuntimeException(e);
        } finally {
            JDBCUtilsByDruid.close(null,null,connection);
        }
    }
    //select返回多个对象（多行）针对 任意表
    public List<T> queryMultiply(String sql, Class<T> tClass,Object... parameters){//形参列表传入sql语句 一个类 的Class对象 以及相关的参数
        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            List<T> tList = queryRunner.query(connection, sql, new BeanListHandler<T>(tClass), parameters);
            return tList;
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }

    }
    //select返回单个（单行）针对 任意表
    public T querySingleRow(String sql,Class<T> tClass,Object... parameters){
        Connection connection = null;
        try {
            connection = JDBCUtilsByDruid.getConnection();
            T t = queryRunner.query(connection, sql, new BeanHandler<T>(tClass), parameters);
            return t;
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }

    }
    //select返回单个（单行单列）Object 针对 任意表
    public Object queryObject(String sql,Object... parameters){
        Connection connection = JDBCUtilsByDruid.getConnection();
        try {
            T t = queryRunner.query(connection, sql, new ScalarHandler<T>(), parameters);
            return t;
        } catch (SQLException e) {
            throw new RuntimeException(e);
        } finally {
        JDBCUtilsByDruid.close(null,null,connection);
        }

    }

}
//----------------------------------------------------------------------------------------------------------------------------
/**
 @author EddieZhang
 @create 2022-09-11 21:41
 */
public class ActorDAO extends BasicDAO<Actor>{
    //继承了BasicDAO 用有其所有方法
    //可以根据业务的相关需求定义其他方法
}

public class GoodsDAO extends BasicDAO<Goods>{
    //继承了BasicDAO中所有的方法
    //也可以根据需要定义自己的方法
}
//----------------------------------------------------------------------------------------------------------------------------
/**
 * 对ActorDAO的相关测试
 */
public class DAOTest {
    @Test
    public void test(){
        ActorDAO actorDAO = new ActorDAO();
        //查询多行
        List<Actor> actorDAOS = actorDAO.queryMultiply("select * from actor where id >= ?", Actor.class, 1);
        for (Actor actor :
                actorDAOS) {
            System.out.println(actor);
        }
        //查询单行
        Actor actor = actorDAO.querySingleRow("select * from actor where id = ?", Actor.class, 2);
        System.out.println(actor);
        //查询单行单列
        Object o = actorDAO.queryObject("select name from actor where id = ?", 2);
        System.out.println(o);

        //执行dml操作
        int i = actorDAO.update("insert into actor values (null,?,?,?,?)", "James", "男", "1986-08-09", "12233335555");
        if(i > 0){
            System.out.println("sql语句执行成功");

        }


    }
    @Test
    public void test1(){
        GoodsDAO goodsDAO = new GoodsDAO();
        int i = goodsDAO.create("create table goods (id int,name varchar(100),price double)character set utf8 collate utf8_bin engine innodb");
        int i1 = goodsDAO.update("insert into goods values (?,'华为手机',2000),(?,'苹果手机',3000),(?,'小米手机',2000),(?,'vivo手机',null),(?,'三星手机',2300),(?,'海尔手机',1800),(?,'IBM',5000),(?,'格力手机',null),(?,'格力手机',null)",10,20,30,40,50,60,70,80,80);
        if(i > 0){
            System.out.println("sql语句执行成功");
        }
        List<Goods> goodsList = goodsDAO.queryMultiply("select * from goods where id >= ?", Goods.class, 10);
        for (Goods goods :
                goodsList) {
            System.out.println(goods);
        }
    }
}
//----------------------------------------------------------------------------------------------------------------------------
//数据库连接池 Druid--JDBCUtilsByDruid
/**
 @author EddieZhang
 @create 2022-09-10 21:18
 */
@SuppressWarnings(value = "all")
public class JDBCUtilsByDruid {
    private static DataSource ds;

    //在静态代码块中完成ds的初始化
    static {
        Properties properties = new Properties();
        try {
            properties.load(new FileInputStream(new File("src\\druid.properties")));
            ds = DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            throw new RuntimeException(e);
        }

    }
    //getConnection的方法
    public static Connection getConnection(){
        try {
            return ds.getConnection();
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }
    //关闭连接--仅仅是把连接放回到连接池中   而不是真正的 断掉连接
    public static void close(ResultSet resultSet, Statement statement,Connection connection){
        if(resultSet != null){
            try {
                resultSet.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
        if(statement != null){
            try {
                statement.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
        if (connection != null){
            try {
                connection.close();
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }
    }
}
```



### MySQL★

**连接到MySQL数据库的操作**

1.服务启动--net start mysql(服务名) 服务关闭--net stop mysql(服务名)

2.登录（连接）--mysql -h 主机名 -P 端口 -u 用户名 -p密码 退出（断连）--exit

-p后不能出现空格

-p后没写密码的，回车会要求输入密码

如果没有写-h 主机，默认就是本机

如果没写-P 端口，默认就是3306

在实际工作中 端口一般会修改



![image-20220825205341677](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825205341677.png)

**SQL 分类 SQL语言在功能上主要分为如下3大类：** 

**DDL（Data Definition Languages、数据定义语言）**，这些语句定义了不同的数据库、表、视图、索 引等数据库对象，还可以用来创建、删除、修改数据库和数据表的结构。 

主要的语句关键字包括 **CREATE** 、 **DROP** 、 **ALTER** 等。 

**DML（Data Manipulation Language、数据操作语言）**，用于添加、删除、更新和查询数据库记 录，并检查数据完整性。 

主要的语句关键字包括 **INSERT** 、 **DELETE** 、 **UPDATE** 、 **SELECT** 等。 **SELECT**是SQL语言的基础，最为重要。 

**DCL（Data Control Language、数据控制语言）**，用于定义数据库、表、字段、用户的访问权限和 安全级别。 

主要的语句关键字包括 **GRANT** 、 **REVOKE** 、 **COMMIT** 、 **ROLLBACK** 、 **SAVEPOINT** 等

![image-20220901093814041](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220901093814041.png)

**SQL语言的规则与规范**

![image-20220901093857419](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220901093857419.png)

**数据导入指令**

![image-20220901093930942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220901093930942.png)

#### 数据库

```sql
#数据库操作
#create database db03 [IF NOT EXISTS] character set utf8 collate utf8_bin;
-- 创建一个数据空并使用 CHARACTER SER 指定字符集 同时使用 COLLATE 指定校验 
-- 其中[IF NOT EXISTS](开发中推荐使用)表示如果库已经存在就不创建 不存在就创建
#创建一个名为Eddie_db02的数据库
CREATE DATABASE Eddie_db02;
#删除数据库
DROP DATABASE Eddie_db02;
#创建一个使用utf8字符集的Eddie_db03数据库
CREATE DATABASE Eddie_db03 CHARACTER SET utf8;
#删除数据库
DROP DATABASE Eddie_db03;
#创建一个使用utf_8字符集，并带校对规则的Eddie_db04数据库
CREATE DATABASE Eddie_db04 CHARACTER SET utf8 COLLATE utf8_bin;
#删除数据库
DROP DATABASE Eddie_db04
#以下是表示查询sql语句；SELECT查询 *代表所有字段 FROM从哪个表中查询 WHRER表示从哪个字段查 NAME = 'Ivring' 表示查询名字为Ivring的
SELECT * FROM user1 WHERE NAME = 'Ivring';

#查看当前正在使用的库（当前在哪个库下）
SELECT DATABASE();
#查看有哪些数据库
SHOW DATABASES
#显示数据库的创建语句
SHOW CREATE DATABASE eddie_db03;
#删除数据库
DROP DATABASE eddie_db02;
#在创建数据库或者表的时候；为了规避关键字可以使用反引`CREATE`
CREATE DATABASE Eddie_db05 CHARACTER SET utf8 COLLATE utf8_bin
DROP DATABASE eddie_db05
SELECT * FROM user1
SELECT * FROM user1 WHERE NAME = 'Ivring';
CREATE DATABASE eddie_db05 CHARACTER SET utf8 COLLATE utf8_bin
CREATE TABLE 
```



##### 创建

```sql
#create database db03 [IF NOT EXISTS] character set utf8 collate utf8_bin;
-- 创建一个数据空并使用 CHARACTER SET 指定字符集 同时使用 COLLATE 指定校验 
-- （如果不指定默认字符集为utf-8 默认校对规则为 utf-8)_general_ci为不区分大小写）
-- 其中[IF NOT EXISTS](开发中推荐使用)表示如果库已经存在就不创建 不存在就创建
#在创建数据库或者表的时候；为了规避关键字可以使用反引`CREATE`
```

##### 查看，删除数据库

```sql
#查看有哪些数据库
SHOW DATABASES
#显示数据库的创建语句
SHOW CREATE DATABASE eddie_db03;

#删除数据库
DROP DATABASE eddie_db02;
-- For instance:
mysql> drop database db02;
Query OK, 4 rows affected (0.03 sec)

```

##### 备份，恢复数据库

```sql
#备份数据库:（注意要在DOS执行）命令行-*-这里备份数据库即把创建数据库的所有操作命令进行备份-->恢复数据库时即直接将所有操作命令运行一次即可
mysqldump -u root -p -B db02(数据库的名) >e:\\bal.sql(指定要备份到的磁盘路径 以及文件名.sql)
-- C:\WINDOWS\system32>mysqldump -u root -p -B db02 >e:\\bak2.sql
-- Enter password: ****
#恢复数据库:（注意要在Mysql命令执行）-*-这里备份数据库即把创建数据库的所有操作命令进行备份-->恢复数据库时即直接将所有操作命令运行一次即可
mysql> source e:\\bak2.sql
```



#### 表

##### 备份，恢复表

```sql
-- 备份表:（注意要在DOS执行）命令行-*-这里备份数据库的表即把创建数据库的表的所有操作命令进行备份-->恢复数据库时即直接将所有操作命令运行一次即可
mysqldump -u root -p db02(数据库的名) (表名)>e://backaccount.sql(指定要备份到的磁盘路径 以及文件名.sql)
-- C:\WINDOWS\system32>mysqldump -u root -p db01 account >e://backaccount.sql
-- Enter password: ****
#恢复表:（注意要在Mysql命令执行）-*-这里备份数据库的表即把创建数据库的表的所有操作命令进行备份-->恢复数据库时即直接将所有操作命令运行一次即可
mysql> source e://backaccount.sql;
```



```sql
CREATE TABLE [IF NOT EXISTS] 表名(
    字段1, 数据类型 [约束条件] [默认值], 字段2, 数据类型 [约束条件] [默认值], 字段3, 数据类型 [约束条件] [默认值], 
    …… 
    [表约束条件] );
    
    mysql> show tables from db02;-- 查看指定库中所有的表
+----------------+
| Tables_in_db02 |
+----------------+
| emp1           |
| employee1      |
| employee2      |
| employee3      |
+----------------+
4 rows in set (0.00 sec)

mysql> select * from emp1;-- 查看指定表中的完整数据
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
+------+------+------+------+
2 rows in set (0.00 sec)

mysql> show create table emp1;-- 查看指定表的创建结构
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table | Create Table                                                                                                                                                                               |
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| emp1  | CREATE TABLE `emp1` (
  `id` int DEFAULT NULL,
  `a` int DEFAULT NULL,
  `b` int DEFAULT NULL,
  `c` int GENERATED ALWAYS AS ((`a` + `b`)) VIRTUAL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 |
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> describe emp1;-- describe 查看表的详情描述
+-------+------+------+-----+---------+-------------------+
| Field | Type | Null | Key | Default | Extra             |
+-------+------+------+-----+---------+-------------------+
| id    | int  | YES  |     | NULL    |                   |
| a     | int  | YES  |     | NULL    |                   |
| b     | int  | YES  |     | NULL    |                   |
| c     | int  | YES  |     | NULL    | VIRTUAL GENERATED |
+-------+------+------+-----+---------+-------------------+
4 rows in set (0.00 sec)
```



##### 创建

```sql
#创建表指明表的字段
CREATE TABLE student4(
    id int,`name` VARCHAR(255),`password` VARCHAR(25),birthday DATE)
    CHARACTER SET utf8 COLLATE UTF8_bin ENGINE INNODB;
-- 使用CHARACTER SET 指明字符集 否则默认使用和表一样 使用COLLATE 指明校对规则 否则使用和表一样 使用ENGINE指明存储引擎
CREATE TABLE [IF NOT EXISTS] 表名(
    字段1, 数据类型 [约束条件] [默认值], 字段2, 数据类型 [约束条件] [默认值], 字段3, 数据类型 [约束条件] [默认值], 
    …… 
    [表约束条件] );
#创建表可以将另一个表的数据引用过来成为创建的新表的数据
-- 使用 AS subquery 选项，将创建表和插入数据结合起来
CREATE TABLE emp1 AS SELECT * FROM employees;-- 可以完全将一个表的数据作为新表的数据类似于复制了一份表-->也可以在命令中追加条件引用指定的数据
CREATE TABLE emp2 AS SELECT * FROM employees WHERE 1=2; -- 创建的emp2是空表
CREATE TABLE dept80
AS
SELECT employee_id, last_name, salary*12 ANNSAL, hire_date
FROM employees
WHERE department_id = 80;
-- 将另一个表的指定数据引用过来成为创建的新表的数据
mysql> create table emp2 as select id,a,b from emp1;
Query OK, 2 rows affected (0.02 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from emp2;
+------+------+------+
| id   | a    | b    |
+------+------+------+
|    1 |  100 |  200 |
|    2 | 1000 | 2000 |
+------+------+------+
2 rows in set (0.00 sec)
-- 将另一个表的指定数据并可以指定限定条件筛选后引用过来成为创建的新表的数据
mysql> create table emp3 select id,a,b from emp2 where b=2000;-- where后可指定限制条件
Query OK, 1 row affected (0.14 sec)
Records: 1  Duplicates: 0  Warnings: 0

mysql> select * from emp3;
+------+------+------+
| id   | a    | b    |
+------+------+------+
|    2 | 1000 | 2000 |
+------+------+------+
1 row in set (0.00 sec)

```

##### 修改 Alter

```sql
#MySQL ALTER命令
当我们需要修改数据表名或者修改数据表字段时，就需要使用到MySQL ALTER命令
#删除，添加或修改表字段
如下命令使用了 ALTER 命令及 DROP 子句来删除以上创建表的 i 字段：

mysql> ALTER TABLE testalter_tbl  DROP i;
如果数据表中只剩余一个字段则无法使用DROP来删除字段。

MySQL 中使用 ADD 子句来向数据表中添加列，如下实例在表 testalter_tbl 中添加 i 字段，并定义数据类型:

mysql> ALTER TABLE testalter_tbl ADD i INT;

#修改字段类型及名称
如果需要修改字段类型及名称, 你可以在ALTER命令中使用 MODIFY 或 CHANGE 子句 。

例如，把字段 c 的类型从 CHAR(1) 改为 CHAR(10)，可以执行以下命令:

mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);
使用 CHANGE 子句, 语法有很大的不同。 在 CHANGE 关键字之后，紧跟着的是你要修改的字段名，然后指定新字段名及类型。尝试如下实例：

mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;
mysql> ALTER TABLE testalter_tbl CHANGE j j INT;
ALTER TABLE 对 Null 值和默认值的影响
当你修改字段时，你可以指定是否包含值或者是否设置默认值
以下实例，指定字段 j 为 NOT NULL 且默认值为100 。

mysql> ALTER TABLE testalter_tbl 
    -> MODIFY j BIGINT NOT NULL DEFAULT 100;

#修改字段默认值
你可以使用 ALTER 来修改字段的默认值
你可以使用 ALTER 来修改字段的默认值，尝试以下实例：

mysql> ALTER TABLE testalter_tbl ALTER i SET DEFAULT 1000;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | 1000    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
你也可以使用 ALTER 命令及 DROP子句来删除字段的默认值，如下实例：

mysql> ALTER TABLE testalter_tbl ALTER i DROP DEFAULT;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
Changing a Table Type:

#修改表名
如果需要修改数据表的名称，可以在 ALTER TABLE 语句中使用 RENAME 子句来实现
尝试以下实例将数据表 testalter_tbl 重命名为 alter_tbl：

mysql> ALTER TABLE testalter_tbl RENAME TO alter_tbl;

#alter其他用途：

#修改存储引擎：修改为myisam

alter table tableName engine=myisam;
#删除外键约束：keyName是外键别名

alter table tableName drop foreign key keyName;
#修改字段的相对位置：这里name1为想要修改的字段，type1为该字段原来类型，first和after二选一，这应该显而易见，first放在第一位，after放在name2字段后面

alter table tableName modify name1 type1 first|after name2;
```



##### 删除

```sql
#在MySQL中，当一张数据表 没有与其他任何数据表形成关联关系 时，可以将当前数据表直接删除。
#数据和结构都被删除
#所有正在运行的相关事务被提交
#所有相关索引被删除
mysql> drop table [IF EXISTS] emp3;
-- DROP TABLE 语句不能回滚

#TRUNCATE TABLE语句：
#删除表中所有的数据
#释放表的存储空间
#举例：
TRUNCATE TABLE detail_dept;
-- TRUNCATE语句不能回滚，而使用 DELETE 语句删除数据，可以回滚
#delete from 表名
#删除表中所有的数据
mysql> delete from emp2;
Query OK, 2 rows affected (0.01 sec)

mysql> show tables from db02;
+----------------+
| Tables_in_db02 |
+----------------+
| emp1           |
| emp2           |
| employee1      |
| employee2      |
| employee3      |
+----------------+
5 rows in set (0.00 sec)

mysql> select * fm emp2;
Empty set (0.00 sec)


```



#### MySQL数据类型★

列类型/字段类型

![image-20220827203146462](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220827203146462.png)

![image-20220827203053920](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220827203053920.png)

![image-20220827203808253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220827203808253.png)

##### 数值类型

###### 整形

tInyint[一个字节]

smallint[两个字节]

mediumint[三个字节]

**int[四个字节]**

bigint[八个字节]

###### 小数类型

float（单精度）[四个字节]

**double（双精度）[八个字节]**

**decimal（M,D）[不确定大小]**

##### 文本类型（字符串类型）

**char(表数范围0-255)**

**varchar（表数范围0-65535【2^16-1】）**

**text(表数范围0-65535【2^16-1】)**

longtext(表数范围0-【2^32-1】)

##### 二进制数据类型

blob(表数范围0-65535【2^16-1】)

longblob(表数范围0-【2^32-1】)

##### 日期类型

date(日期 年月日)

time（时间 时分秒）

**datetime（日期时间 年月日 时分秒 YYYY-MM-DD hh:mm:ss）**

**timestamp(时间戳)**

year（年）

#### CRUD★

**Tip**: sql中的**null**值 查找使用 is

SELECT * FROM SOME_TABLE
**WHERE SOME_COLUMN `IS` NULL**

##### Insert

```sql
#SQL INSERT INTO 语句
INSERT INTO 语句用于向表中插入新记录

#INSERT INTO 语句可以有两种编写形式。
-- 第一种形式无需指定要插入数据的列名，只需提供被插入的值即可：没有指定要插入数据的列名的形式需要列出插入行的每一列数据:

INSERT INTO table_name
VALUES (value1,value2,value3,...);
-- 第二种形式需要指定列名及被插入的值：

INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);

-- 扩展
-- 通过 SQL，您可以从一个表复制信息到另一个表。INSERT INTO SELECT 语句从一个表复制数据，然后把数据插入到一个已存在的表中
INSERT INTO SELECT

-- For instance:
mysql> select * from emp2;-- 第一种形式无需指定要插入数据的列名，只需提供被插入的值即可：
Empty set (0.00 sec)

mysql> inert into emp2 values (1,22,33,55);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'inert into emp2 values (1,22,33,55)' at line 1
mysql> insert into emp2 values (1,22,33,55);
Query OK, 1 row affected (0.01 sec)

mysql> select * from emp2;
+------+------+------+------+
| id   | a    | b    | sum  |
+------+------+------+------+
|    1 |   22 |   33 |   55 |
+------+------+------+------+
1 row in set (0.00 sec)

mysql>

mysql> insert into emp1 (id,a,b,d) values (6,5223,544,1001);-- 第二种形式需要指定列名及被插入的值：
Query OK, 1 row affected (0.00 sec)

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 | NULL |
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 | NULL |
|    4 |  120 |  520 |  640 | NULL |
|    5 |  120 |  520 |  640 | NULL |
|    6 | 5223 |  544 | 5767 | 1001 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql>

#SQL INSERT INTO SELECT 语句
-- 通过 SQL，您可以从一个表复制信息到另一个表。INSERT INTO SELECT 语句从一个表复制数据，然后把数据插入到一个已存在的表中

mysql> insert into emp2 (id,a,b,sum) select id,a,b,c from emp1 where id between 2 and 6;
Query OK, 5 rows affected (0.00 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> select * from emp2;
+------+------+------+------+
| id   | a    | b    | sum  |
+------+------+------+------+
|    1 |   22 |   33 |   55 |
|    2 | 1000 | 2000 | 3000 |
|    3 |  120 |  520 |  640 |
|    4 |  120 |  520 |  640 |
|    5 |  120 |  520 |  640 |
|    6 | 5223 |  544 | 5767 |
+------+------+------+------+
6 rows in set (0.00 sec)

mysql>

mysql> update emp1 set d=(id * 10);
Query OK, 6 rows affected (0.15 sec)
Rows matched: 6  Changed: 6  Warnings: 0

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    4 |  120 |  520 |  640 |   40 |
|    5 |  120 |  520 |  640 |   50 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
6 rows in set (0.00 sec)
```

##### Update

```sql
#SQL UPDATE 语句
UPDATE 语句用于更新表中已存在的记录。
-- SQL UPDATE 语法
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;

-- For instance
mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 | NULL |
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 | NULL |
|    4 |  120 |  520 |  640 | NULL |
|    5 |  120 |  520 |  640 | NULL |
|    6 | 5223 |  544 | 5767 | 1001 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql> update emp1 set d=100 where c<=640;
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |  100 |
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 |  100 |
|    4 |  120 |  520 |  640 |  100 |
|    5 |  120 |  520 |  640 |  100 |
|    6 | 5223 |  544 | 5767 | 1001 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql> update emp1 set d=1002 where d;
Query OK, 5 rows affected (0.01 sec)
Rows matched: 5  Changed: 5  Warnings: 0

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 | 1002 |
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 | 1002 |
|    4 |  120 |  520 |  640 | 1002 |
|    5 |  120 |  520 |  640 | 1002 |
|    6 | 5223 |  544 | 5767 | 1002 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql> update emp1 set d=1002 where d is null;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 | 1002 |
|    2 | 1000 | 2000 | 3000 | 1002 |
|    3 |  120 |  520 |  640 | 1002 |
|    4 |  120 |  520 |  640 | 1002 |
|    5 |  120 |  520 |  640 | 1002 |
|    6 | 5223 |  544 | 5767 | 1002 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql>
```



##### Delete

```sql
#SQL DELETE 语句
DELETE 语句用于删除表中的行
-- SQL DELETE 语法
DELETE FROM table_name
WHERE some_column=some_value;-- WHERE 子句规定哪条记录或者哪些记录需要删除。如果您省略了 WHERE 子句，所有的记录都将被删除！

-- For instance
mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    4 |  120 |  520 |  640 |   40 |
|    5 |  120 |  520 |  640 |   50 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
6 rows in set (0.00 sec)

mysql> delete from emp1 where d between 40 and 50;
Query OK, 2 rows affected (0.01 sec)

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
4 rows in set (0.00 sec)

删除所有数据
可以在不删除表的情况下，删除表中所有的行。这意味着表结构、属性、索引将保持不变：

DELETE FROM table_name;
注释：在删除记录时要格外小心！因为您不能重来！
mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
4 rows in set (0.00 sec)

mysql> select * from emp2;
+------+------+------+------+
| id   | a    | b    | sum  |
+------+------+------+------+
|    1 |   22 |   33 |   55 |
|    2 | 1000 | 2000 | 3000 |
|    3 |  120 |  520 |  640 |
|    4 |  120 |  520 |  640 |
|    5 |  120 |  520 |  640 |
|    6 | 5223 |  544 | 5767 |
+------+------+------+------+
6 rows in set (0.00 sec)

mysql> delete from emp2;
Query OK, 6 rows affected (0.00 sec)

mysql> select * from emp2;
Empty set (0.00 sec)
```



##### Select★

###### 单表

```sql
基本的SELECT语句
#SELECT...
#SELECT 1; #没有任何子句
#SELECT 9/2; #没有任何子句
mysql> select * from emp1;
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
+------+------+------+------+
2 rows in set (0.00 sec)

mysql> select 2000;-- 没有任何子句
+------+
| 2000 |
+------+
| 2000 |
+------+
1 row in set (0.00 sec)

mysql> select database();
+------------+
| database() |
+------------+
| db02       |
+------------+
1 row in set (0.00 sec)

mysql>

#SELECT ... FROM--在select后面可以使用表达式对查询的列进行运算 同时可使用AS给列定义一个别名
SELECT 标识选择哪些列
FROM 标识从哪个表中选择
#select * from 表名 返回指定表的所有列
mysql> select * from emp1;
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
+------+------+------+------+
2 rows in set (0.00 sec)

#SELECT department_id, location_id,(列名),(列明) FROM departments（表名）where （条件）;-- 返回指定表中满足where后条件的的指定列
mysql> select id,a,b from emp1 where c=3000;
+------+------+------+
| id   | a    | b    |
+------+------+------+
|    2 | 1000 | 2000 |
+------+------+------+
1 row in set (0.00 sec)

#select id,(a + b)--可以进行运算 from emp2;-- 返回指定表中指定列且指定列之间运算的列-- 在select后面可以使用表达式对查询的列进行运算
mysql> select id,(a + b) from emp2;
Empty set (0.00 sec)

mysql> select id,(a + b) from emp1;
+------+---------+
| id   | (a + b) |
+------+---------+
|    1 |     300 |
|    2 |    3000 |
+------+---------+
2 rows in set (0.00 sec)

#select id,(a + b)可以进行运算 as 'sum' 通过AS给运算后的列定义一个'别名' from emp1;-- 返回指定表中指定列且指定列之间运算的定义别名后的列
mysql> select id,(a + b) as 'sum' from emp1;
+------+------+
| id   | sum  |
+------+------+
|    1 |  300 |
|    2 | 3000 |
+------+------+
2 rows in set (0.00 sec)

mysql>

-- 使用WHERE 子句，将不满足条件的行过滤掉
-- WHERE子句紧随 FROM子句
SELECT 字段1,字段2
FROM 表名
WHERE 过滤条件
-- For instance:
mysql> select * from emp1 where c>=640;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 | NULL |
|    4 |  120 |  520 |  640 | NULL |
|    5 |  120 |  520 |  640 | NULL |
+------+------+------+------+------+
4 rows in set (0.00 sec)

mysql>

#列的别名
-- 重命名一个列
-- 便于计算
-- 紧跟列名，也可以在列名和别名之间加入关键字AS，别名使用双引号，以便在别名中包含空格或特
-- 殊的字符并区分大小写。
-- AS 可以省略
-- 建议别名简短，见名知意
-- 举例
SELECT last_name AS name, commission_pct comm
FROM employees;
mysql> select id,(a + b) as 'sum' from emp1;
+------+------+
| id   | sum  |
+------+------+
|    1 |  300 |
|    2 | 3000 |
+------+------+
2 rows in set (0.00 sec)

SELECT last_name "Name", salary*12 "Annual Salary"
FROM employees;
mysql> select id,(a + b) as "SumNumber" from emp1;
+------+-----------+
| id   | SumNumber |
+------+-----------+
|    1 |       300 |
|    2 |      3000 |
+------+-----------+
2 rows in set (0.00 sec)

mysql>
-- 默认情况下，查询会返回全部行，包括重复行。

#去除重复行
#在SELECT语句中使用关键字DISTINCT去除重复行
SELECT DISTINCT department_id-- 此处的列表示要以哪些列以及几个列为条件判断是否为重复
FROM employees;

mysql> select * from emp1;
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
|    3 |  120 |  520 |  640 |
|    4 |  120 |  520 |  640 |
|    5 |  120 |  520 |  640 |
+------+------+------+------+
5 rows in set (0.00 sec)

mysql> select distinct * from emp1;
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
|    3 |  120 |  520 |  640 |
|    4 |  120 |  520 |  640 |
|    5 |  120 |  520 |  640 |
+------+------+------+------+
5 rows in set (0.00 sec)

mysql> select distinct a from emp1;
+------+
| a    |
+------+
|  100 |
| 1000 |
|  120 |
+------+
3 rows in set (0.00 sec)

mysql> select distinct id,a,b,c form emp1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'emp1' at line 1
mysql> select distinct id,a,b,c from emp1;
+------+------+------+------+
| id   | a    | b    | c    |
+------+------+------+------+
|    1 |  100 |  200 |  300 |
|    2 | 1000 | 2000 | 3000 |
|    3 |  120 |  520 |  640 |
|    4 |  120 |  520 |  640 |
|    5 |  120 |  520 |  640 |
+------+------+------+------+
5 rows in set (0.00 sec)

mysql> select distinct c from emp1;
+------+
| c    |
+------+
|  300 |
| 3000 |
|  640 |
+------+
3 rows in set (0.00 sec)

mysql>

#空值参与运算
-- 注意，在 MySQL 里面， 空值不等于空字符串。一个空字符串的长度是 0，而一个空值的长度是空。而且，在 MySQL 里面，空值是占用空间的
#所有运算符或列值遇到null值，运算的结果都为null
mysql> alter table emp1 add (d int);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from emp1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 | NULL |
|    2 | 1000 | 2000 | 3000 | NULL |
|    3 |  120 |  520 |  640 | NULL |
|    4 |  120 |  520 |  640 | NULL |
|    5 |  120 |  520 |  640 | NULL |
+------+------+------+------+------+
5 rows in set (0.00 sec)

mysql> select id,(c + d) as 'sum' from emp1;
+------+------+
| id   | sum  |
+------+------+
|    1 | NULL |
|    2 | NULL |
|    3 | NULL |
|    4 | NULL |
|    5 | NULL |
+------+------+
5 rows in set (0.00 sec)

mysql>

#着重号 ``
-- 我们需要保证表中的字段、表名等没有和保留字、数据库系统或常用方法冲突。如果真的相同，请在SQL语句中使用一对``（着重号）引起来
CREATE TABLE student5(
    id TINYINT,`name` VARCHAR(255),`password` VARCHAR(25),birthday DATA)
    CHARACTER SET utf8 COLLATE utf8_bin ENGINE INNODB

# 显示表结构
-- 使用DESCRIBE 或 DESC 命令，表示表结构
mysql> describe emp1;
+-------+------+------+-----+---------+-------------------+
| Field | Type | Null | Key | Default | Extra             |
+-------+------+------+-----+---------+-------------------+
| id    | int  | YES  |     | NULL    |                   |
| a     | int  | YES  |     | NULL    |                   |
| b     | int  | YES  |     | NULL    |                   |
| c     | int  | YES  |     | NULL    | VIRTUAL GENERATED |
| d     | int  | YES  |     | NULL    |                   |
+-------+------+------+-----+---------+-------------------+
5 rows in set (0.00 sec)

mysql>
#其中，各个字段的含义分别解释如下：
-- Field：表示字段名称。
-- Type：表示字段类型，这里 barcode、goodsname 是文本型的，price 是整数类型的。
-- Null：表示该列是否可以存储NULL值。
-- Key：表示该列是否已编制索引。PRI表示该列是表主键的一部分；UNI表示该列是UNIQUE索引的一部分；MUL表示在列中某个给定值允许出现多次。
-- Default：表示该列是否有默认值，如果有，那么值是多少。
-- Extra：表示可以获取的与给定列有关的附加信息，例如AUTO_INCREMENT等。

# 显示表的创建信息
mysql> show create from emp1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from emp1' at line 1
mysql> show create db01;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'db01' at line 1
mysql> show create table emp1;
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table | Create Table                                                                                                                                                                                                       |
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| emp1  | CREATE TABLE `emp1` (
  `id` int DEFAULT NULL,
  `a` int DEFAULT NULL,
  `b` int DEFAULT NULL,
  `c` int GENERATED ALWAYS AS ((`a` + `b`)) VIRTUAL,
  `d` int DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 |
+-------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```

###### **Select语句的where子句**

**where**可以指明约束条件-- WHERE 子句用于过滤记录。

```sql
#SQL WHERE 语法
SELECT column_name,column_name
FROM table_name
WHERE column_name operator value;-- 指明约束条件-- WHERE 子句用于过滤记录。

```

**where**子句中的运算符

![image-20220901125539476](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220901125539476.png)

![image-20220901130357689](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220901130357689.png)

```sql
Where +条件（筛选行）
条件：列，比较运算符，值

比较运算符包涵：= > < >= ,<=, !=,<> 表示（不等于）

Select * from emp where ename='SMITH';
例子中的 SMITH 用单引号引起来，表示是字符串，字符串要区分大小写。

逻辑运算
And:与 同时满足两个条件的值。

Select * from emp where sal > 2000 and sal < 3000;
查询 EMP 表中 SAL 列中大于 2000 小于 3000 的值。

Or:或 满足其中一个条件的值

Select * from emp where sal > 2000 or comm > 500;
查询 emp 表中 SAL 大于 2000 或 COMM 大于500的值。

Not:非 满足不包含该条件的值。

select * from emp where not sal > 1500;
查询EMP表中 sal 小于等于 1500 的值。

逻辑运算的优先级：

()  >  not    >    and    >     or
特殊条件
1.空值判断：判断是否为空 is null ☆******************☆

Select * from emp where comm is null;
查询 emp 表中 comm 列中的空值。

2.between and (在 之间的值)-- 是闭区间

Select * from emp where sal between 1500 and 3000;
查询 emp 表中 SAL 列中大于 1500 的小于 3000 的值。

注意：大于等于 1500 且小于等于 3000， 1500 为下限，3000 为上限，下限在前，上限在后，查询的范围包涵有上下限的值。

3.In-- 在（条件,条件，条件）里面的

Select * from emp where sal in (5000,3000,1500);
查询 EMP 表 SAL 列中等于 5000，3000，1500 的值。

4.like

Like模糊查询

Select * from emp where ename like 'M%';
查询 EMP 表中 Ename 列中有 M 的值，M 为要查询内容中的模糊信息。

 % 表示多个字值，_ 下划线表示一个字符；
 M% : 为能配符，正则表达式，表示的意思为模糊查询信息为 M 开头的。
 %M% : 表示查询包含M的所有内容。
 %M_ : 表示查询以M在倒数第二位的所有内容。
 
#不带比较运算符的 WHERE 子句：

WHERE 子句并不一定带比较运算符，当不带运算符时，会执行一个隐式转换。当 0 时转化为 false，1 转化为 true。例如：

SELECT studentNO FROM student WHERE 0
则会返回一个空集，因为每一行记录 WHERE 都返回 false。

SELECT  studentNO  FROM student WHERE 1
返回 student 表所有行中 studentNO 列的值。因为每一行记录 WHERE 都返回 true。

-- For instance
mysql> select * from emp1 where 0;
Empty set (0.00 sec)

mysql> select * from emp1 where 1;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
4 rows in set (0.00 sec)

mysql>
```

###### **Select**语句的**order by**子句

```sql
#SQL ORDER BY 关键字
ORDER BY 关键字用于对结果集按照一个列或者多个列进行排序。可以使用列的别名进行排序
ORDER BY 关键字默认按照升序(ascend)对记录进行排序。如果需要按照降序对记录进行排序，您可以使用 DESC （descend）降序关键字

ORDER BY 多列的时候，先按照第一个column name排序，在按照第二个column name排序；如上述教程最后一个例子：

 1）、先将country值这一列排序，同为CN的排前面，同属USA的排后面；
 2）、然后在同属CN的这些多行数据中，再根据alexa值的大小排列。
 3）、ORDER BY 排列时，不写明ASC DESC的时候，默认是ASC
 
 ORDER BY 多列的时候，eg:

order by A,B        这个时候都是默认按升序排列
order by A desc,B   这个时候 A 降序，B 升序排列
order by A ,B desc  这个时候 A 升序，B 降序排列
即 desc 或者 asc 只对它紧跟着的第一个列名有效，其他不受影响，仍然是默认的升序
 
-- SQL ORDER BY 语法
SELECT column_name,column_name
FROM table_name
ORDER BY column_name,column_name ASC|DESC;-- 默认使用ASC升序进行排序 可以指定排序方式

-- For instance-- 单列
mysql> select * from emp1 order by d;-- 默认使用ASC升序进行排序
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
4 rows in set (0.00 sec)

mysql>

mysql> select * from emp1 order by c desc;-- 默认使用ASC升序进行排序 可以指定排序方式
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    6 | 5223 |  544 | 5767 |   60 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    1 |  100 |  200 |  300 |   10 |
+------+------+------+------+------+
4 rows in set (0.00 sec)

mysql> select * from emp1 order by c DESC;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    6 | 5223 |  544 | 5767 |   60 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    7 | 1000 | 2000 | 3000 |   40 |
|    3 |  120 |  520 |  640 |   30 |
|    1 |  100 |  200 |  300 |   10 |
+------+------+------+------+------+
5 rows in set (0.00 sec)

-- For instance-- 多列

mysql> select * from emp1 order by c,d desc;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    1 |  100 |  200 |  300 |   10 |
|    3 |  120 |  520 |  640 |   30 |
|    7 | 1000 | 2000 | 3000 |   40 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    6 | 5223 |  544 | 5767 |   60 |
+------+------+------+------+------+
5 rows in set (0.00 sec)

mysql> select * from emp1 order by c desc,d desc;
+------+------+------+------+------+
| id   | a    | b    | c    | d    |
+------+------+------+------+------+
|    6 | 5223 |  544 | 5767 |   60 |
|    7 | 1000 | 2000 | 3000 |   40 |
|    2 | 1000 | 2000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |   30 |
|    1 |  100 |  200 |  300 |   10 |
+------+------+------+------+------+
5 rows in set (0.00 sec)

mysql>

#可以使用别名进行排序

mysql> select id,a,b,(a + b) as 'sum',c,d from emp1 order by sum desc;
+------+------+------+------+------+------+
| id   | a    | b    | sum  | c    | d    |
+------+------+------+------+------+------+
|    6 | 5223 |  544 | 5767 | 5767 |   60 |
|    2 | 1000 | 2000 | 3000 | 3000 |   20 |
|    7 | 1000 | 2000 | 3000 | 3000 |   40 |
|    3 |  120 |  520 |  640 |  640 |   30 |
|    1 |  100 |  200 |  300 |  300 |   10 |
+------+------+------+------+------+------+
5 rows in set (0.00 sec)

#综合where & AS & 双列 & 列运算 条件使用order by
mysql> select id,a,b,(a + b) as 'sum',c,d from emp1 where id between 2 and 6 order by sum desc,d desc;
+------+------+------+------+------+------+
| id   | a    | b    | sum  | c    | d    |
+------+------+------+------+------+------+
|    6 | 5223 |  544 | 5767 | 5767 |   60 |
|    2 | 1000 | 2000 | 3000 | 3000 |   20 |
|    3 |  120 |  520 |  640 |  640 |   30 |
+------+------+------+------+------+------+
3 rows in set (0.00 sec)
```

###### 单表查询加强

```sql
-- select语句顺序 group by - having - order by - limit
select '列名','列名'... from '表名'
group by `列`
having `condition`
order by `列`
limit `start`,`rows`;
-- For instance 统计各个部门的平均工资仅保留2位小数，并且>1000,平均工资按照降序排序，并取出前两行;
mysql> select format(avg(sal),2),deptno from emp
    -> group by deptno
    -> having avg(sal)>1000
    -> order by avg(sal) desc
    -> limit 0,2;
+--------------------+--------+
| format(avg(sal),2) | deptno |
+--------------------+--------+
| 2,916.67           |     10 |
| 2,443.75           |     20 |
+--------------------+--------+
2 rows in set (0.00 sec)


#结合where子句对date进行条件筛选
-- 查询1991-01-01后入职的员工
mysql> select ename,hiredate from emp where hiredate>'1992-01-01';
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| SCOTT  | 1997-04-19 |
| MILLER | 1992-01-23 |
+--------+------------+
2 rows in set (0.00 sec)

#Like模糊查询

Select * from emp where ename like 'M%';
查询 EMP 表中 Ename 列中有 M 的值，M 为要查询内容中的模糊信息。

 % 表示多个字值，_ 下划线表示一个字符；
 M% : 为能配符，正则表达式，表示的意思为模糊查询信息为 M 开头的。
 %M% : 表示查询包含M的所有内容。
 %M_ : 表示查询以M在倒数第二位的所有内容。
 
 -- For instance 显示姓名首字母为S的员工及其工资
 mysql> select ename,sal from emp where ename like 'S%';
+-------+---------+
| ename | sal     |
+-------+---------+
| SMITH |  800.00 |
| SCOTT | 3000.00 |
+-------+---------+
2 rows in set (0.00 sec)
-- For instance 显示姓名第三个字母为O的员工及其工资
mysql> select ename, sal from emp where ename like '__O%';
+-------+---------+
| ename | sal     |
+-------+---------+
| SCOTT | 3000.00 |
+-------+---------+
1 row in set (0.00 sec)

#is null 判断是否为null值
-- For instance 显示没有上级的员工信息（上级编号mgr为null的）
mysql> select * from emp where mgr is null;
+-------+-------+-----------+------+------------+---------+------+--------+
| empno | ename | job       | mgr  | hiredate   | sal     | comm | deptno |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7839 | KING  | president | NULL | 1991-11-17 | 5000.00 | NULL |     10 |
+-------+-------+-----------+------+------------+---------+------+--------+
1 row in set (0.00 sec)

#order by 排序-- 默认升序（不指明desc即为asc）
-- For instance
mysql> select * from emp order by sal asc;-- 默认升序（不指明desc即为asc）
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> select * from emp order by sal desc;-- 默认升序（不指明desc即为asc）
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

-- 先按照部门编号升序然后按照工资降序排序显示员工信息
mysql> select * from emp order by deptno asc , sal desc;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

#分页查询
-- 基本语法select...limit start，rows 从start + 1行开始 取出rows行 start从0开始计算
-- limit 每页显要显示的行数 *（第几页 - 1），每页显要显示的行数
-- 第1页
mysql> select * from emp order by sal desc limit 0,5;-- limit 每页显要显示的行数 *（第几页 - 1），每页显要显示的行数
+-------+-------+-----------+------+------------+---------+------+--------+
| empno | ename | job       | mgr  | hiredate   | sal     | comm | deptno |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7839 | KING  | president | NULL | 1991-11-17 | 5000.00 | NULL |     10 |
|  7788 | SCOTT | analyst   | 7566 | 1997-04-19 | 3000.00 | NULL |     20 |
|  7902 | FORD  | analyst   | 7566 | 1991-12-03 | 3000.00 | NULL |     20 |
|  7566 | JONES | manager   | 7839 | 1991-04-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE | manager   | 7839 | 1991-05-01 | 2850.00 | NULL |     30 |
+-------+-------+-----------+------+------------+---------+------+--------+
5 rows in set (0.00 sec)
-- 第二页
mysql> select * from emp order by sal desc limit 5,5;-- limit 每页显要显示的行数 *（第几页 - 1），每页显要显示的行数
+-------+--------+----------+------+------------+---------+--------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm   | deptno |
+-------+--------+----------+------+------------+---------+--------+--------+
|  7782 | CLARK  | manager  | 7839 | 1991-06-09 | 2450.00 |   NULL |     10 |
|  7499 | ALLEN  | salesman | 7698 | 1991-02-20 | 1600.00 | 300.00 |     30 |
|  7844 | TURNER | salesman | 7698 | 1991-09-08 | 1500.00 |   NULL |     30 |
|  7934 | MILLER | clerk    | 7782 | 1992-01-23 | 1300.00 |   NULL |     10 |
|  7521 | WARD   | salesman | 7698 | 1991-02-22 | 1250.00 | 500.00 |     30 |
+-------+--------+----------+------+------------+---------+--------+--------+
5 rows in set (0.00 sec)
-- 第三页
mysql> select * from emp order by sal desc limit 10,5;-- limit 每页显要显示的行数 *（第几页 - 1），每页显要显示的行数
+-------+--------+----------+------+------------+---------+---------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7654 | MARTIN | salesman | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7900 | JAMES  | clerk    | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7369 | SMITH  | clerk    | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.00 sec)

#分组函数&分组子句GROUP BY
-- For instance 显示每种岗位的雇员总数和平均工资
mysql> select count(*),avg(sal) from emp group by job;
+----------+-------------+
| count(*) | avg(sal)    |
+----------+-------------+
|        3 | 1016.666667 |
|        4 | 1400.000000 |
|        3 | 2758.333333 |
|        2 | 3000.000000 |
|        1 | 5000.000000 |
+----------+-------------+
5 rows in set (0.00 sec)
-- For instance 获取雇员总数以及获得了补助（comm不为null的）的雇员数
mysql> select count(*),count(comm) from emp;-- count（*）与count（列）的区别是count（列）会过滤列中的null值 而count（*）返回总列数
+----------+-------------+
| count(*) | count(comm) |
+----------+-------------+
|       13 |           3 |
+----------+-------------+
1 row in set (0.00 sec)
-- For instance 获取雇员总数以及没有补助（comm为null的）的雇员数
mysql> select count(*),count(if(comm is null,1,null)) from emp;
+----------+--------------------------------+
| count(*) | count(if(comm is null,1,null)) |
+----------+--------------------------------+
|       13 |                             10 |
+----------+--------------------------------+
mysql> select if(comm is null,1,null) from emp;
-- 其中 if(comm is null,1,null)
+-------------------------+
| if(comm is null,1,null) |
+-------------------------+
|                       1 |
|                    NULL |
|                    NULL |
|                       1 |
|                    NULL |
|                       1 |
|                       1 |
|                       1 |
|                       1 |
|                       1 |
|                       1 |
|                       1 |
|                       1 |
+-------------------------+
13 rows in set (0.00 sec)
1 row in set (0.00 sec)
-- else method
mysql> select count(*),count(*) - count(comm) from emp;
+----------+------------------------+
| count(*) | count(*) - count(comm) |
+----------+------------------------+
|       13 |                     10 |
+----------+------------------------+
1 row in set (0.00 sec)

-- For instance 显示员工中manager的总数
mysql> select count(job) as 'manager_count' from emp where job='manager';
+---------------+
| manager_count |
+---------------+
|             3 |
+---------------+
1 row in set (0.00 sec)

-- For instance 显示员工的工资最大差额
mysql> select max(sal) - min(sal) as '最大工资差额' from emp;
+--------------------+
| 最大工资差额       |
+--------------------+
|            4200.00 |
+--------------------+
1 row in set (0.00 sec)
```



###### 多表

```sql
#多表查询即基于两个或两个以上的表查询
#笛卡尔集
mysql> select count(*) from dept,emp,salgrade;
+----------+
| count(*) |
+----------+
|      260 |
+----------+
count（*）的结果为每个表的行数相X（乘）count（*）=dept.rows x emp.rows x salgrade 笛卡尔集
1 row in set (0.01 sec)
-- 避免出现笛卡尔集 Tip：多表查询的条件不能少于 表的个数 - 1；
mysql> select ename,sal,emp.deptno from emp,dept where emp.deptno=dept.deptno;-- 可以给两个表限制条件进行查询（思考过滤条件）
-- 如果多表中出现同名列 则需要使用 表名.列名 的形式指明列 否则系统无法识别会报错
+--------+---------+--------+
| ename  | sal     | deptno |
+--------+---------+--------+
| SMITH  |  800.00 |     20 |
| ALLEN  | 1600.00 |     30 |
| WARD   | 1250.00 |     30 |
| JONES  | 2975.00 |     20 |
| MARTIN | 1250.00 |     30 |
| BLAKE  | 2850.00 |     30 |
| CLARK  | 2450.00 |     10 |
| SCOTT  | 3000.00 |     20 |
| KING   | 5000.00 |     10 |
| TURNER | 1500.00 |     30 |
| JAMES  |  950.00 |     30 |
| FORD   | 3000.00 |     20 |
| MILLER | 1300.00 |     10 |
+--------+---------+--------+
13 rows in set (0.00 sec)

-- For instance 查询显示员工的姓名 工资 以及 工资等级
mysql> select ename,sal,grade from emp,salgrade where emp.sal between salgrade.losal and salgrade.hisal
    -> ;
+--------+---------+-------+
| ename  | sal     | grade |
+--------+---------+-------+
| SMITH  |  800.00 |     1 |
| ALLEN  | 1600.00 |     3 |
| WARD   | 1250.00 |     2 |
| JONES  | 2975.00 |     4 |
| MARTIN | 1250.00 |     2 |
| BLAKE  | 2850.00 |     4 |
| CLARK  | 2450.00 |     4 |
| SCOTT  | 3000.00 |     4 |
| KING   | 5000.00 |     5 |
| TURNER | 1500.00 |     3 |
| JAMES  |  950.00 |     1 |
| FORD   | 3000.00 |     4 |
| MILLER | 1300.00 |     2 |
+--------+---------+-------+
13 rows in set (0.00 sec)
```

##### 子查询

```sql
#子查询-- 嵌套查询
-- For instance
-- 查询和smith同一个部门的所有员工  先查出smith所在部门 然后查此部门的所有员工
mysql> select * from emp where deptno = (select deptno from emp where ename = 'SMITH');
+-------+-------+---------+------+------------+---------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal     | comm | deptno |
+-------+-------+---------+------+------------+---------+------+--------+
|  7369 | SMITH | clerk   | 7902 | 1990-12-17 |  800.00 | NULL |     20 |
|  7566 | JONES | manager | 7839 | 1991-04-02 | 2975.00 | NULL |     20 |
|  7788 | SCOTT | analyst | 7566 | 1997-04-19 | 3000.00 | NULL |     20 |
|  7902 | FORD  | analyst | 7566 | 1991-12-03 | 3000.00 | NULL |     20 |
+-------+-------+---------+------+------------+---------+------+--------+
4 rows in set (0.00 sec)

```

##### 多行子查询

```sql
#多行子查询 嵌套查询 子查询返回的是多行的情况-- Tip:where后的条件返回的是多行时 要使用关键字 IN 
-- For instance
-- 查询和20号部门的工作相同的雇员的 姓名 岗位 工资 部门号 但是不包含20号部门中的雇员
mysql> select ename,job,sal,deptno from emp
    -> where job IN (select distinct job from emp where deptno = 20) AND deptno <> 20
    -> ;
+--------+---------+---------+--------+
| ename  | job     | sal     | deptno |
+--------+---------+---------+--------+
| BLAKE  | manager | 2850.00 |     30 |
| CLARK  | manager | 2450.00 |     10 |
| JAMES  | clerk   |  950.00 |     30 |
| MILLER | clerk   | 1300.00 |     10 |
+--------+---------+---------+--------+
4 rows in set (0.00 sec)
```

##### 临时表

```sql
#子查询当作临时表来使用
-- For instance
-- 查询ecshop中各个类别中 价格最高的goods-- 可以将子查询作为一张临时表来使用
mysql> select goods_id,cat_id,goods_name,shop_price from ecs_goods;
+----------+--------+----------------------------------------+------------+
| goods_id | cat_id | goods_name                             | shop_price |
+----------+--------+----------------------------------------+------------+
|        1 |      4 | KD876                                  |    1388.00 |
|        4 |      8 | 诺基亚N85原装充电器                    |      58.00 |
|        3 |      8 | 诺基亚原装5800耳机                     |      68.00 |
|        5 |     11 | 索爱原装M2卡读卡器                     |      20.00 |
|        6 |     11 | 胜创KINGMAX内存卡                      |      42.00 |
|        7 |      8 | 诺基亚N85原装立体声耳机HS-82           |     100.00 |
|        8 |      3 | 飞利浦9@9v                             |     399.00 |
|        9 |      3 | 诺基亚E66                              |    2298.00 |
|       10 |      3 | 索爱C702c                              |    1328.00 |
|       11 |      3 | 索爱C702c                              |    1300.00 |
|       12 |      3 | 摩托罗拉A810                           |     983.00 |
|       13 |      3 | 诺基亚5320 XpressMusic                 |    1311.00 |
|       14 |      4 | 诺基亚5800XM                           |    2625.00 |
|       15 |      3 | 摩托罗拉A810                           |     788.00 |
|       16 |      2 | 恒基伟业G101                           |     823.33 |
|       17 |      3 | 夏新N7                                 |    2300.00 |
|       18 |      4 | 夏新T5                                 |    2878.00 |
|       19 |      3 | 三星SGH-F258                           |     858.00 |
|       20 |      3 | 三星BC01                               |     280.00 |
|       21 |      3 | 金立 A30                               |    2000.00 |
|       22 |      3 | 多普达Touch HD                         |    5999.00 |
|       23 |      5 | 诺基亚N96                              |    3700.00 |
|       24 |      3 | P806                                   |    2000.00 |
|       25 |     13 | 小灵通/固话50元充值卡                  |      48.00 |
|       26 |     13 | 小灵通/固话20元充值卡                  |      19.00 |
|       27 |     15 | 联通100元充值卡                        |      95.00 |
|       28 |     15 | 联通50元充值卡                         |      45.00 |
|       29 |     14 | 移动100元充值卡                        |      90.00 |
|       30 |     14 | 移动20元充值卡                         |      18.00 |
|       31 |      3 | 摩托罗拉E8                             |    1337.00 |
|       32 |      3 | 诺基亚N85                              |    3010.00 |
+----------+--------+----------------------------------------+------------+
31 rows in set (0.00 sec)

mysql> select goods_id,ecs_goods.cat_id,goods_name,shop_price
-- 此处from后的表可以使用select出的子查询作为临时表 并给临时表另名
    -> from (select cat_id,MAX(shop_price) as 'max_shop_price' from ecs_goods GROUP BY cat_id) temp,ecs_goods
    -> where temp.cat_id=ecs_goods.cat_id and max_shop_price = shop_price
    -> ;
+----------+--------+----------------------------------------+------------+
| goods_id | cat_id | goods_name                             | shop_price |
+----------+--------+----------------------------------------+------------+
|       16 |      2 | 恒基伟业G101                           |     823.33 |
|       22 |      3 | 多普达Touch HD                         |    5999.00 |
|       18 |      4 | 夏新T5                                 |    2878.00 |
|       23 |      5 | 诺基亚N96                              |    3700.00 |
|        7 |      8 | 诺基亚N85原装立体声耳机HS-82           |     100.00 |
|        6 |     11 | 胜创KINGMAX内存卡                      |      42.00 |
|       25 |     13 | 小灵通/固话50元充值卡                  |      48.00 |
|       29 |     14 | 移动100元充值卡                        |      90.00 |
|       27 |     15 | 联通100元充值卡                        |      95.00 |
+----------+--------+----------------------------------------+------------+
9 rows in set (0.00 sec)

```

##### all&any的使用

```sql
#all&any的使用
-- all 表示所有
-- For instance
-- 显示工资比部门30的所有员工都要高的员工的姓名，工资和部门号-- 相当于比最高还要高
mysql> select ename,sal,deptno from emp
    -> where sal > ALL(select sal from emp where deptno=30);
+-------+---------+--------+
| ename | sal     | deptno |
+-------+---------+--------+
| JONES | 2975.00 |     20 |
| SCOTT | 3000.00 |     20 |
| KING  | 5000.00 |     10 |
| FORD  | 3000.00 |     20 |
+-------+---------+--------+
4 rows in set (0.00 sec)

-- any 表示任何一个
-- For instance
-- 显示工资比部分30中的其中任意一个员工工资高的员工的姓名，工资和部门号-- 相当于只要比最低的到
mysql> select ename,sal,deptno from emp
    -> where sal > any(select sal from emp where deptno = 30);
+--------+---------+--------+
| ename  | sal     | deptno |
+--------+---------+--------+
| ALLEN  | 1600.00 |     30 |
| WARD   | 1250.00 |     30 |
| JONES  | 2975.00 |     20 |
| MARTIN | 1250.00 |     30 |
| BLAKE  | 2850.00 |     30 |
| CLARK  | 2450.00 |     10 |
| SCOTT  | 3000.00 |     20 |
| KING   | 5000.00 |     10 |
| TURNER | 1500.00 |     30 |
| FORD   | 3000.00 |     20 |
| MILLER | 1300.00 |     10 |
+--------+---------+--------+
11 rows in set (0.00 sec)
```

##### 多列子查询

```sql
#多列子查询
-- 子查询结果为多列的 --（列名，列名）= （子查询）
-- For instance
-- 查询和ALLEN的部门和岗位完全相同的所有雇员（并不包含ALLEN本人）
mysql> select * from emp
    -> where (deptno,job) = (select deptno,job from emp where ename = 'ALLEN') AND ename <> 'ALLEN'
    -> ;
+-------+--------+----------+------+------------+---------+---------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7521 | WARD   | salesman | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | salesman | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7844 | TURNER | salesman | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.00 sec)

-- For instance
-- 查询和宋江 数学，英语，语文成绩完全相同的同学
mysql> select * from student
    -> where (chinese,english,math) = (select chinese,english,math from student where name = '宋江');
+----+--------+---------+---------+------+
| id | name   | chinese | english | math |
+----+--------+---------+---------+------+
|  3 | 宋江   |      87 |      78 |   77 |
+----+--------+---------+---------+------+
1 row in set (0.00 sec)

-- For instance
-- -- 查询每个部门工资高于本部门平均工资水平的人的数据
select * from emp;
-- 首先列出每个部门的平均工资
select avg(sal) as '平均工资',deptno from emp GROUP BY deptno;
-- 将每个部门的平均工资和部门的多列结果作为子查询并命为临时表
select ename,emp.sal,emp.deptno,temp.`平均工资`
from emp,(select avg(sal) as '平均工资',deptno from emp GROUP BY deptno) temp 
where emp.deptno = temp.deptno and emp.sal > temp.`平均工资`
ORDER BY emp.deptno DESC;

mysql> select ename,emp.sal,emp.deptno,temp.`平均工资`
    -> from emp,(select avg(sal) as '平均工资',deptno from emp GROUP BY deptno) temp
    -> where emp.deptno = temp.deptno and emp.sal > temp.`平均工资`
    -> ORDER BY emp.deptno DESC;
+-------+---------+--------+--------------+
| ename | sal     | deptno | 平均工资     |
+-------+---------+--------+--------------+
| BLAKE | 2850.00 |     30 |  1566.666667 |
| ALLEN | 1600.00 |     30 |  1566.666667 |
| FORD  | 3000.00 |     20 |  2443.750000 |
| SCOTT | 3000.00 |     20 |  2443.750000 |
| JONES | 2975.00 |     20 |  2443.750000 |
| KING  | 5000.00 |     10 |  2916.666667 |
+-------+---------+--------+--------------+
6 rows in set (0.00 sec)

-- For instance
-- 显示每个部门的信息包括（部门名，编号，地址） 和人员的数量
-- 首先先显示部门的信息（部门名，编号，地址）
select dept.deptno,dept.dname,dept.loc from dept;

mysql> select dept.deptno,dept.dname,dept.loc from dept;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)
mysql> select dept.* from dept;-- select 列名.* from dept;表名将此表中的所有列的显示出来
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)

mysql>
select dept.deptno,dept.dname,dept.loc,temp.`部门的人员数量`
from dept,(select emp.deptno,count(emp.deptno) as '部门的人员数量' from emp GROUP BY emp.deptno) temp
where temp.deptno = dept.deptno;

mysql> select dept.deptno,dept.dname,dept.loc,temp.`部门的人员数量`
    -> from dept,(select emp.deptno,count(emp.deptno) as '部门的人员数量' from emp GROUP BY emp.deptno) temp
    -> where temp.deptno = dept.deptno;
+--------+------------+----------+-----------------------+
| deptno | dname      | loc      | 部门的人员数量        |
+--------+------------+----------+-----------------------+
|     10 | ACCOUNTING | NEW YORK |                     3 |
|     20 | RESEARCH   | DALLAS   |                     4 |
|     30 | SALES      | CHICAGO  |                     6 |
+--------+------------+----------+-----------------------+
3 rows in set (0.00 sec)


```

##### 表复制

```sql
#表复制-- 自我复制（蠕虫复制）
-- 创建一个和student表相同结构的my_student表
create table my_student1 like my_student;-- 可以使用create table 新表 like 需要引用结构的表
create table my_student (
  `id` int NOT NULL DEFAULT '1',
  `name` varchar(20) COLLATE utf8mb3_bin NOT NULL DEFAULT '',
  `chinese` float NOT NULL DEFAULT '0',
  `english` float NOT NULL DEFAULT '0',
  `math` float NOT NULL DEFAULT '0'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_bin
-- 将student表insert into进my_student表
insert into my_student select * from student;
-- my_student表进行多次的自我复制（蠕虫复制）
insert into my_student select * from my_student;
select count(*) from my_student;
mysql> select count(*) from my_student;
+----------+
| count(*) |
+----------+
|      224 |
+----------+
1 row in set (0.00 sec)

```

##### 表去重

```sql
#表去重
-- 思路 
-- ①创建一个临时表的结构与想要去重的表的结构一致 
-- ②对临时表进行distinct去重 
-- ③将想要去重的表的数据全部删除 
-- ④将临时表的数据insert into进原表 
-- ⑤drop零时表

-- 实现流程
-- 创建一个临时表的结构与想要去重的表的结构一致 
create table temp_table like my_student;
-- 对临时表进行distinct去重 
insert into temp_table select distinct * from my_student;
-- 将想要去重的表的数据全部删除
delete from my_student;
-- 将临时表的数据insert into进原表
insert into my_student select * from temp_table;
-- drop零时表
drop table temp_table;
```

##### UNION操作符 合并查询

```sql
#UNION
#MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。
#MySQL UNION 操作符语法格式：
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
#参数
expression1, expression2, ... expression_n: 要检索的列。

tables: 要检索的数据表。

WHERE conditions: 可选， 检索条件。

DISTINCT: 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。

ALL: 可选，返回所有结果集，包含重复数据
-- tip:
UNION 语句：用于将不同表中相同列中查询的数据展示出来；（不包括重复数据）

UNION ALL 语句：用于将不同表中相同列中查询的数据展示出来；（包括重复数据）

使用形式如下：

SELECT 列名称 FROM 表名称 UNION SELECT 列名称 FROM 表名称 ORDER BY 列名称；
SELECT 列名称 FROM 表名称 UNION ALL SELECT 列名称 FROM 表名称 ORDER BY 列名称；
```

#### 函数★

##### 统计函数

```sql
# SQL 函数

------

SQL 拥有很多可用于计数和计算的内建函数。

------

## SQL Aggregate 函数

SQL Aggregate 函数计算从列中取得的值，返回一个单一的值。

有用的 Aggregate 函数：

- AVG() - 返回平均值
- COUNT() - 返回行数
- FIRST() - 返回第一个记录的值
- LAST() - 返回最后一个记录的值
- MAX() - 返回最大值
- MIN() - 返回最小值
- SUM() - 返回总和

------
# SQL COUNT() 函数

------

COUNT() 函数返回匹配指定条件的行数。

------

### SQL COUNT(column_name) 语法

COUNT(column_name) 函数返回指定列的值的数目（NULL 不计入）：-- 统计满足条件的某列有多少个（会排除null）

SELECT COUNT(column_name) FROM table_name;

### SQL COUNT(*) 语法

COUNT(*) 函数返回表中的记录数：-- 返回满足条件的记录的行数

SELECT COUNT(*) FROM table_name;

### SQL COUNT(DISTINCT column_name) 语法

COUNT(DISTINCT column_name) 函数返回指定列的不同值的数目：

SELECT COUNT(DISTINCT column_name) FROM table_name;

**注释：**COUNT(DISTINCT) 适用于 ORACLE 和 Microsoft SQL Server，但是无法用于 Microsoft Access

-- For instance
mysql> select * from access1;
+------+---------+-------+------------+
| aid  | site_id | count | date       |
+------+---------+-------+------------+
|    1 |       1 |    45 | 2016-05-10 |
|    2 |       3 |   100 | 2016-05-13 |
|    3 |       1 |   230 | 2016-05-14 |
|    4 |       2 |    10 | 2016-05-14 |
|    5 |       5 |   205 | 2016-05-14 |
|    6 |       4 |    13 | 2016-05-15 |
|    7 |       3 |   220 | 2016-05-15 |
|    8 |       5 |   545 | 2016-05-16 |
|    9 |       3 |   201 | 2016-05-17 |
|   10 |       3 |  NULL | 2016-05-25 |
|   11 |       3 |  NULL | 2016-05-26 |
+------+---------+-------+------------+
11 rows in set (0.00 sec)

mysql> select count(*) from access1 where site_id=3;-- 返回满足条件的记录的行数
+----------+
| count(*) |
+----------+
|        5 |
+----------+
1 row in set (0.00 sec)

mysql> select count(count) from access1 where site_id=3;-- 统计满足条件的某列有多少个（会排除null）
+--------------+
| count(count) |
+--------------+
|            3 |
+--------------+
1 row in set (0.00 sec)

mysql> select count(distinct site_id) from access1 where site_id=3;-- 函数返回指定列的不同值（非重复）的数目：
+-------------------------+
| count(distinct site_id) |
+-------------------------+
|                       1 |
+-------------------------+
1 row in set (0.01 sec)

mysql> select count(site_id) from access1 where site_id=3;
+----------------+
| count(site_id) |
+----------------+
|              5 |
+----------------+
1 row in set (0.00 sec)

#AVG() 函数
AVG() 函数返回数值列的平均值。

SQL AVG() 语法
SELECT AVG(column_name) FROM table_name

-- For instance
mysql> select * from access1;
+------+---------+-------+------------+
| aid  | site_id | count | date       |
+------+---------+-------+------------+
|    1 |       1 |    45 | 2016-05-10 |
|    2 |       3 |   100 | 2016-05-13 |
|    3 |       1 |   230 | 2016-05-14 |
|    4 |       2 |    10 | 2016-05-14 |
|    5 |       5 |   205 | 2016-05-14 |
|    6 |       4 |    13 | 2016-05-15 |
|    7 |       3 |   220 | 2016-05-15 |
|    8 |       5 |   545 | 2016-05-16 |
|    9 |       3 |   201 | 2016-05-17 |
|   10 |       3 |  NULL | 2016-05-25 |
|   11 |       3 |  NULL | 2016-05-26 |
+------+---------+-------+------------+
11 rows in set (0.01 sec)

mysql> select average(count) from access1;
ERROR 1305 (42000): FUNCTION db02.average does not exist
mysql> select avg(count) as `CountAverage` from access1;
+--------------+
| CountAverage |
+--------------+
|     174.3333 |
+--------------+
1 row in set (0.00 sec)

mysql> select site_id from access1 where count >= (select avg(count) from access1);
+---------+
| site_id |
+---------+
|       1 |
|       5 |
|       3 |
|       5 |
|       3 |
+---------+
5 rows in set (0.13 sec)

mysql> select site_id,count from access1 where count >= (select avg(count) from access1);
+---------+-------+
| site_id | count |
+---------+-------+
|       1 |   230 |
|       5 |   205 |
|       3 |   220 |
|       5 |   545 |
|       3 |   201 |
+---------+-------+
5 rows in set (0.00 sec)

#SUM() 函数
SUM() 函数返回数值列的总数。

SQL SUM() 语法
SELECT SUM(column_name) FROM table_name;-- 仅对数值起作用

-- For instance
mysql> select * from student_score1;
+-----------+--------+------------+---------------+---------------+
| name      | number | Math_score | Chinese_score | English_score |
+-----------+--------+------------+---------------+---------------+
| 张锦豪    |   1001 |         99 |            95 |            91 |
| 欧文      |   1002 |         92 |            94 |            99 |
| 詹姆斯    |   1003 |         93 |            95 |            99 |
| 杜兰特    |   1004 |         92 |            91 |            99 |
| 库里      |   1005 |         92 |            92 |            98 |
| 哈登      |   1006 |         90 |            91 |            94 |
| 东七七    |   1007 |         91 |            93 |            98 |
+-----------+--------+------------+---------------+---------------+
7 rows in set (0.00 sec)

mysql> select sum(Math_score + Chinese_score + English_score) as sum_score from student_score1;
+-----------+
| sum_score |
+-----------+
|      1978 |
+-----------+
1 row in set (0.00 sec)

mysql> select sum(Math_score + Chinese_score + English_score) / count(*) as sum_score from student_score1;
+--------------------+
| sum_score          |
+--------------------+
| 282.57142857142856 |
+--------------------+
1 row in set (0.00 sec)

mysql>

#MAX() 函数
MAX() 函数返回指定列的最大值。

SQL MAX() 语法
SELECT MAX(column_name) FROM table_name;
#MIN() 函数
MIN() 函数返回指定列的最小值。

SQL MIN() 语法
SELECT MIN(column_name) FROM table_name;

-- For instance
mysql> select * from access1;
+------+---------+-------+------------+
| aid  | site_id | count | date       |
+------+---------+-------+------------+
|    1 |       1 |    45 | 2016-05-10 |
|    2 |       3 |   100 | 2016-05-13 |
|    3 |       1 |   230 | 2016-05-14 |
|    4 |       2 |    10 | 2016-05-14 |
|    5 |       5 |   205 | 2016-05-14 |
|    6 |       4 |    13 | 2016-05-15 |
|    7 |       3 |   220 | 2016-05-15 |
|    8 |       5 |   545 | 2016-05-16 |
|    9 |       3 |   201 | 2016-05-17 |
|   10 |       3 |  NULL | 2016-05-25 |
|   11 |       3 |  NULL | 2016-05-26 |
+------+---------+-------+------------+
11 rows in set (0.00 sec)

mysql> select max(Math_score + Chinese_score + English_score) as max_sum_score from student_score1;
+---------------+
| max_sum_score |
+---------------+
|           287 |
+---------------+
1 row in set (0.00 sec)

mysql>
mysql> select min(Math_score + Chinese_score + English_score) as min_sum_score from student_score1;
+---------------+
| min_sum_score |
+---------------+
|           275 |
+---------------+
1 row in set (0.00 sec)

mysql>

#SQL GROUP BY 语句
GROUP BY 语句
GROUP BY 语句用于结合聚合函数，根据一个或多个列对结果集进行分组。

SQL GROUP BY 语法
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
#SQL HAVING 子句
HAVING 子句
在 SQL 中增加 HAVING 子句原因是，WHERE 关键字无法与聚合函数一起使用。

HAVING 子句可以让我们筛选分组后的各组数据。

SQL HAVING 语法
SQL HAVING 语法
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name
HAVING aggregate_function(column_name) operator value;

-- For instance
mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | CLERK     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> CREATE TABLE salgrade
    -> (
    -> grade MEDIUMINT UNSIGNED NOT NULL DEFAULT 0, /*工资级别*/
    -> losal DECIMAL(17,2) NOT NULL, /* 该级别的最低工资 */
    -> hisal DECIMAL(17,2) NOT NULL /* 该级别的最高工资*/
    -> );
Query OK, 0 rows affected (0.01 sec)

mysql> INSERT INTO salgrade VALUES (1,700,1200);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (2,1201,1400);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (3,1401,2000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (4,2001,3000);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO salgrade VALUES (5,3001,9999);
Query OK, 1 row affected (0.00 sec)

mysql> select * from salgrade;
+-------+---------+---------+
| grade | losal   | hisal   |
+-------+---------+---------+
|     1 |  700.00 | 1200.00 |
|     2 | 1201.00 | 1400.00 |
|     3 | 1401.00 | 2000.00 |
|     4 | 2001.00 | 3000.00 |
|     5 | 3001.00 | 9999.00 |
+-------+---------+---------+
5 rows in set (0.00 sec)

mysql> select avg(sal) as `avg`,max(sal) as `max` from emp;
+-------------+---------+
| avg         | max     |
+-------------+---------+
| 2148.076923 | 5000.00 |
+-------------+---------+
1 row in set (0.00 sec)

mysql> select avg(sal),max(sal),deptno from emp group by deptno;-- group by 根据列进行分组
+-------------+----------+--------+
| avg(sal)    | max(sal) | deptno |
+-------------+----------+--------+
| 2443.750000 |  3000.00 |     20 |
| 1566.666667 |  2850.00 |     30 |
| 2916.666667 |  5000.00 |     10 |
+-------------+----------+--------+
3 rows in set (0.00 sec)

mysql> select avg(sal),max(sal),deptno from emp group by deptno having avg(sal)>2000.00;-- group by 根据列进行分组 having 条件筛选
+-------------+----------+--------+
| avg(sal)    | max(sal) | deptno |
+-------------+----------+--------+
| 2443.750000 |  3000.00 |     20 |
| 2916.666667 |  5000.00 |     10 |
+-------------+----------+--------+
2 rows in set (0.00 sec)


```



##### 时间日期

```sql
#CURDATE()	返回当前日期	
SELECT CURDATE();
-> 2018-09-19
#CURRENT_DATE()	返回当前日期	
SELECT CURRENT_DATE();
-> 2018-09-19

#CURRENT_TIME	返回当前时间	
SELECT CURRENT_TIME();
-> 19:59:02

#LAST_DAY   返回某个月的最后一天
mysql> select last_day(now());
+-----------------+
| last_day(now()) |
+-----------------+
| 2022-09-30      |
+-----------------+
1 row in set (0.00 sec)

mysql> select LAST_DAY('2022-08-04');
+------------------------+
| LAST_DAY('2022-08-04') |
+------------------------+
| 2022-08-31             |
+------------------------+
1 row in set (0.00 sec)

#CURTIME()	返回当前时间	
SELECT CURTIME();
-> 19:59:02

#CURRENT_TIMESTAMP()	返回当前日期和时间(时间戳)	
SELECT CURRENT_TIMESTAMP()
-> 2018-09-19 20:57:43

#DATE()	从日期或日期时间表达式中提取日期值	
SELECT DATE("2017-06-15");    
-> 2017-06-15
-- For instance
mysql> select current_timestamp();
+---------------------+
| current_timestamp() |
+---------------------+
| 2022-09-02 19:38:25 |
+---------------------+
1 row in set (0.00 sec)

mysql> select date(current_timestamp());
+---------------------------+
| date(current_timestamp()) |
+---------------------------+
| 2022-09-02                |
+---------------------------+
1 row in set (0.00 sec)

#DATE_ADD(d，INTERVAL expr type)	计算起始日期 d 加上一个时间段后的日期，type 值可以是：
MICROSECOND
SECOND
MINUTE
HOUR
DAY
WEEK
MONTH
QUARTER
YEAR
SECOND_MICROSECOND
MINUTE_MICROSECOND
MINUTE_SECOND
HOUR_MICROSECOND
HOUR_SECOND
HOUR_MINUTE
DAY_MICROSECOND
DAY_SECOND
DAY_MINUTE
DAY_HOUR
YEAR_MONTH
SELECT DATE_ADD("2017-06-15", INTERVAL 10 DAY);    
-> 2017-06-25

SELECT DATE_ADD("2017-06-15 09:34:21", INTERVAL 15 MINUTE);
-> 2017-06-15 09:49:21

SELECT DATE_ADD("2017-06-15 09:34:21", INTERVAL -3 HOUR);
->2017-06-15 06:34:21

SELECT DATE_ADD("2017-06-15 09:34:21", INTERVAL -3 MONTH);
->2017-04-15
-- For instance
mysql> select current_timestamp();
+---------------------+
| current_timestamp() |
+---------------------+
| 2022-09-02 19:43:51 |
+---------------------+
1 row in set (0.00 sec)
mysql> select date_add(current_timestamp(),interval 3 month);
+------------------------------------------------+
| date_add(current_timestamp(),interval 3 month) |
+------------------------------------------------+
| 2022-12-02 19:43:08                            |
+------------------------------------------------+
1 row in set (0.00 sec)

-- 开发中常用:判断是否于某个时间段内的
-- 查看员工表中工龄达到31year的员工及其入职日期



#DATE_SUB(date,INTERVAL expr type)	函数从日期减去指定的时间间隔。	
Orders 表中 OrderDate 字段减去 2 天：
SELECT OrderId,DATE_SUB(OrderDate,INTERVAL 2 DAY) AS OrderPayDate
FROM Orders
-- For instance
mysql> select current_timestamp();
+---------------------+
| current_timestamp() |
+---------------------+
| 2022-09-02 19:43:51 |
+---------------------+
1 row in set (0.00 sec)

mysql> select date_sub(current_timestamp(),interval 3 month);
+------------------------------------------------+
| date_sub(current_timestamp(),interval 3 month) |
+------------------------------------------------+
| 2022-06-02 19:46:16                            |
+------------------------------------------------+
1 row in set (0.00 sec)

#TIMEDIFF(time1, time2)	计算时间差值	单位是 时:分:秒
mysql> SELECT TIMEDIFF("13:10:11", "13:10:10");
-> 00:00:01
mysql> SELECT TIMEDIFF('2000:01:01 00:00:00',
    ->                 '2000:01:01 00:00:00.000001');
        -> '-00:00:00.000001'
mysql> SELECT TIMEDIFF('2008-12-31 23:59:59.000001',
    ->                 '2008-12-30 01:01:01.000002');
        -> '46:58:57.999999'

#DATEDIFF(d1,d2)	计算日期 d1->d2 之间相隔的天数	单位是 天
SELECT DATEDIFF('2001-01-01','2001-02-02')
-> -32
-- 假设活到80岁 看看从现在开始还能活几天
mysql> select datediff(date_add('2001-01-01',interval 80 year),current_date);
+----------------------------------------------------------------+
| datediff(date_add('2001-01-01',interval 80 year),current_date) |
+----------------------------------------------------------------+
|                                                          21306 |
+----------------------------------------------------------------+
1 row in set (0.00 sec)

#TO_DAYS(d)	计算日期 d 距离 0000 年 1 月 1 日的天数	
SELECT TO_DAYS('0001-01-01 01:01:01')
-> 366

#NOW()	返回当前日期和时间	
SELECT NOW()
-> 2018-09-19 20:57:43
-- For instance
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2022-09-02 19:50:49 |
+---------------------+
1 row in set (0.00 sec)

mysql> select year(now());
+-------------+
| year(now()) |
+-------------+
|        2022 |
+-------------+
1 row in set (0.00 sec)

mysql> select month(now());
+--------------+
| month(now()) |
+--------------+
|            9 |
+--------------+
1 row in set (0.00 sec)

mysql> select day(now());
+------------+
| day(now()) |
+------------+
|          2 |
+------------+
1 row in set (0.00 sec)

# unix_timestamp()返回1970年1月1日至此的毫秒数
mysql> select unix_timestamp();
+------------------+
| unix_timestamp() |
+------------------+
|       1662128229 |
+------------------+
1 row in set (0.00 sec)

# from_unixtime(一个时间戳,'指定格式')-- 可以把时间戳转成指定的格式
-- 在开发中会使用一个int来保存unix时间戳 然后进行转换
mysql> select from_unixtime(1662128229,'%y-%m-%d');-- 固定格式
+--------------------------------------+
| from_unixtime(1662128229,'%y-%m-%d') |
+--------------------------------------+
| 22-09-02                             |
+--------------------------------------+
1 row in set (0.00 sec)
mysql> select from_unixtime(1662128229,'%Y-%m-%d');-- 固定格式
+--------------------------------------+
| from_unixtime(1662128229,'%Y-%m-%d') |
+--------------------------------------+
| 2022-09-02                           |
+--------------------------------------+
1 row in set (0.00 sec)
mysql> select from_unixtime(1662128229,'%Y-%m-%d %H:%i:%s');-- 固定格式
+-----------------------------------------------+
| from_unixtime(1662128229,'%Y-%m-%d %H:%i:%s') |
+-----------------------------------------------+
| 2022-09-02 22:17:09                           |
+-----------------------------------------------+
1 row in set (0.00 sec)
```



##### 字符串函数

```sql
## SQL Scalar 函数

SQL Scalar 函数基于输入值，返回一个单一的值。

有用的 Scalar 函数：

- UCASE() - 将某个字段转换为大写
- LCASE() - 将某个字段转换为小写
- MID() - 从某个文本字段提取字符，MySql 中使用
- SubString(字段，1，end) - 从某个文本字段提取字符
- LEN() - 返回某个文本字段的长度
- ROUND() - 对某个数值字段进行指定小数位数的四舍五入
- NOW() - 返回当前的系统日期和时间
- FORMAT() - 格式化某个字段的显示方式

#UCASE() 函数
UCASE() 函数把字段的值转换为大写。

SQL UCASE() 语法
SELECT UCASE(column_name) FROM table_name;
用于 SQL Server 的语法
SELECT UPPER(column_name) FROM table_name;
-- For instance
mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> update emp set job=ucase(job) where job='salesman';
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

#LCASE() 函数
LCASE() 函数把字段的值转换为小写。

SQL LCASE() 语法
SELECT LCASE(column_name) FROM table_name;
用于 SQL Server 的语法
SELECT LOWER(column_name) FROM table_name;

-- For instance
mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> update emp set job=lcase(job) where job='SALESMAN';
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

#MID() 函数
-- MID() 函数用于从文本字段中提取字符。-- 相当于substr
SQL MID()
SELECT MID(column_name,start[,length]) FROM table_name;
-- 参数	       描述
-- column_name	必需。要提取字符的字段。
-- start	    必需。规定开始位置（起始值是 1）。
-- length	    可选。要返回的字符数。如果省略，则 MID() 函数返回剩余文本。

-- For instance
mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> select mid(hiredate,1,4) from emp;
+-------------------+
| mid(hiredate,1,4) |
+-------------------+
| 1990              |
| 1991              |
| 1991              |
| 1991              |
| 1991              |
| 1991              |
| 1991              |
| 1997              |
| 1991              |
| 1991              |
| 1991              |
| 1991              |
| 1992              |
+-------------------+
13 rows in set (0.00 sec)

mysql> select mid(hiredate,1) as 'HireDate' from emp;-- length	    可选。要返回的字符数。如果省略，则 MID() 函数返回剩余文本。
+------------+
| HireDate   |
+------------+
| 1990-12-17 |
| 1991-02-20 |
| 1991-02-22 |
| 1991-04-02 |
| 1991-09-28 |
| 1991-05-01 |
| 1991-06-09 |
| 1997-04-19 |
| 1991-11-17 |
| 1991-09-08 |
| 1991-12-03 |
| 1991-12-03 |
| 1992-01-23 |
+------------+
13 rows in set (0.00 sec)

mysql>

#LEN() 函数
LEN() 函数返回文本字段中值的长度。

SQL LEN() 语法
SELECT LEN(column_name) FROM table_name;
MySQL 中函数为 LENGTH():

SELECT LENGTH(column_name) FROM table_name;

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> select length(ename) as 'EmployeeNameLength' from emp;
+--------------------+
| EmployeeNameLength |
+--------------------+
|                  5 |
|                  5 |
|                  4 |
|                  5 |
|                  6 |
|                  5 |
|                  5 |
|                  5 |
|                  4 |
|                  6 |
|                  5 |
|                  4 |
|                  6 |
+--------------------+
13 rows in set (0.00 sec)

mysql>

#CONCAT(s1,s2...sn)	字符串 s1,s2 等多个字符串合并为一个字符串	
-- 合并多个字符串

SELECT CONCAT("SQL ", "Runoob ", "Gooogle ", "Facebook") AS ConcatenatedString;

-- For instance
mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> select concat(ename,"--",job) from emp where sal>=3000.00;
+------------------------+
| concat(ename,"--",job) |
+------------------------+
| SCOTT--analyst         |
| KING--president        |
| FORD--analyst          |
+------------------------+
3 rows in set (0.00 sec)

#CONCAT(s1,s2...sn)	字符串 s1,s2 等多个字符串合并为一个字符串 可以是运算或者日期加上字符串合并成一个字符串
mysql> select ename,CONCAT('已入职:',TRUNCATE((DATEDIFF(now(),hiredate)/365),0),'年',TRUNCATE((TRUNCATE((DATEDIFF(now(),hiredate)%365),0))/30,0),'月',
    -> TRUNCATE((TRUNCATE((DATEDIFF(now(),hiredate)%365),0))%30,0),'天') AS '入职年限' from emp;
+--------+---------------------------+
| ename  | 入职年限                  |
+--------+---------------------------+
| SMITH  | 已入职:31年9月1天         |
| ALLEN  | 已入职:31年6月26天        |
| WARD   | 已入职:31年6月24天        |
| JONES  | 已入职:31年5月15天        |
| MARTIN | 已入职:30年11月21天       |
| BLAKE  | 已入职:31年4月16天        |
| CLARK  | 已入职:31年3月7天         |
| SCOTT  | 已入职:25年4月26天        |
| KING   | 已入职:30年10月1天        |
| TURNER | 已入职:31年0月6天         |
| JAMES  | 已入职:30年9月15天        |
| FORD   | 已入职:30年9月15天        |
| MILLER | 已入职:30年7月24天        |
+--------+---------------------------+
13 rows in set (0.00 sec)

mysql> update emp set job=concat(upper(left(job,1)),mid(job,2));
-- 修改字段中的字符串将首字符改成小写
-- 1.使用left（列名，1）将字符串中的首字母拿到
-- 1.1使用upper（1）将拿到的字符串首字母转换成大写的
-- 2.使用mid（列名，2）将字符串中除了首字母的剩余字符拿到
-- 3.使用concat（1.1，2）将拿到的两个部分组合起来
-- 4.使用update 表名 set 列名=3；使用update方法进行修改
Query OK, 13 rows affected (0.01 sec)
Rows matched: 13  Changed: 13  Warnings: 0

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | Clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | Salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | Salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | Manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | Salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | Manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | Manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | Analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | President | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | Salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | JAMES  | Clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | Analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | Clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)

mysql> update emp set ename=concat(left(ename,1),lower(mid(ename,2)));
Query OK, 13 rows affected (0.00 sec)
Rows matched: 13  Changed: 13  Warnings: 0

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | Smith  | clerk     | 7902 | 1990-12-17 |  800.00 |    NULL |     20 |
|  7499 | Allen  | salesman  | 7698 | 1991-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | Ward   | salesman  | 7698 | 1991-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | Jones  | manager   | 7839 | 1991-04-02 | 2975.00 |    NULL |     20 |
|  7654 | Martin | salesman  | 7698 | 1991-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | Blake  | manager   | 7839 | 1991-05-01 | 2850.00 |    NULL |     30 |
|  7782 | Clark  | manager   | 7839 | 1991-06-09 | 2450.00 |    NULL |     10 |
|  7788 | Scott  | analyst   | 7566 | 1997-04-19 | 3000.00 |    NULL |     20 |
|  7839 | King   | president | NULL | 1991-11-17 | 5000.00 |    NULL |     10 |
|  7844 | Turner | salesman  | 7698 | 1991-09-08 | 1500.00 |    NULL |     30 |
|  7900 | James  | clerk     | 7698 | 1991-12-03 |  950.00 |    NULL |     30 |
|  7902 | Ford   | analyst   | 7566 | 1991-12-03 | 3000.00 |    NULL |     20 |
|  7934 | Miller | clerk     | 7782 | 1992-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
13 rows in set (0.00 sec)


#REPLACE(s,s1,s2)	将字符串 s2 替代字符串 s 中的字符串 s1	
-- 将字符串 abc 中的字符 a 替换为字符 x：

SELECT REPLACE('abc','a','x') --xbc

-- For instance
-- 将emp表中的job列的数据首字符的小写字母replace为大写字母
mysql> select replace(
    -> job,left(job,1),upper(left(job,1))
    -> ) from emp;
+-----------------------------------------------+
| replace(
job,left(job,1),upper(left(job,1))
) |
+-----------------------------------------------+
| Clerk                                         |
| SaleSman                                      |
| SaleSman                                      |
| Manager                                       |
| SaleSman                                      |
| Manager                                       |
| Manager                                       |
| AnAlyst                                       |
| President                                     |
| SaleSman                                      |
| Clerk                                         |
| AnAlyst                                       |
| Clerk                                         |
+-----------------------------------------------+
13 rows in set (0.00 sec)

```



##### 数学函数

```sql
#ABS(x)	返回 x 的绝对值　　	
-- 返回 -1 的绝对值：
SELECT ABS(-1) -- 返回1
-- For instance
mysql> select abs(-125);
+-----------+
| abs(-125) |
+-----------+
|       125 |
+-----------+
1 row in set (0.00 sec)

#BIN(x)	返回 x 的二进制编码	
-- 15 的 2 进制编码:
SELECT BIN(15); -- 1111
-- For instance
mysql> select bin(56);
+---------+
| bin(56) |
+---------+
| 111000  |
+---------+
1 row in set (0.00 sec)

#CONV(x,f1,f2)	返回 f1 进制数变成 f2 进制数	
SELECT CONV(15, 10, 2);
-> 1111

#CEILING(x)	返回大于或等于 x 的最小整数　
SELECT CEILING(1.5); -- 返回2
-- For instance
mysql> select ceiling(1.1);
+--------------+
| ceiling(1.1) |
+--------------+
|            2 |
+--------------+
1 row in set (0.00 sec)
mysql> select ceiling(-2.9);
+---------------+
| ceiling(-2.9) |
+---------------+
|            -2 |
+---------------+
1 row in set (0.00 sec)

#FLOOR(x)	返回小于或等于 x 的最大整数　　
-- 小于或等于 1.5 的整数：
SELECT FLOOR(1.5) -- 返回1
-- For instance
mysql> select floor(1.9);
+------------+
| floor(1.9) |
+------------+
|          1 |
+------------+
1 row in set (0.00 sec)
mysql> select floor(-1.1);
+-------------+
| floor(-1.1) |
+-------------+
|          -2 |
+-------------+
1 row in set (0.00 sec)

#TRUNCATE(x,y)	返回数值 x 保留到小数点后 y 位的值（最后一位不会进行四舍五入）
SELECT TRUNCATE(1.23456,3) -- 1.234

#FORMAT(x,n)	函数可以将数字 x 进行格式化 "#,###.##", 将 x 保留到小数点后 n 位，最后一位四舍五入。	
-- 格式化数字 "#,###.##" 形式：
SELECT FORMAT(250500.5634, 2);     -- 输出 250,500.56
-- For instance
mysql> select sal from emp;
+---------+
| sal     |
+---------+
|  800.00 |
| 1600.00 |
| 1250.00 |
| 2975.00 |
| 1250.00 |
| 2850.00 |
| 2450.00 |
| 3000.00 |
| 5000.00 |
| 1500.00 |
|  950.00 |
| 3000.00 |
| 1300.00 |
+---------+
13 rows in set (0.00 sec)
mysql> select format(sal,5) from emp;
+---------------+
| format(sal,5) |
+---------------+
| 800.00000     |
| 1,600.00000   |
| 1,250.00000   |
| 2,975.00000   |
| 1,250.00000   |
| 2,850.00000   |
| 2,450.00000   |
| 3,000.00000   |
| 5,000.00000   |
| 1,500.00000   |
| 950.00000     |
| 3,000.00000   |
| 1,300.00000   |
+---------------+
13 rows in set (0.00 sec)

#LEAST(expr1, expr2, expr3, ...)	返回列表中的最小值	
-- 返回以下数字列表中的最小值：
SELECT LEAST(3, 12, 34, 8, 25); -- 3
-- 返回以下字符串列表中的最小值：
SELECT LEAST("Google", "Runoob", "Apple");   -- Apple

#MOD(x,y)	返回 x 除以 y 以后的余数　	
-- 5 除于 2 的余数：
SELECT MOD(5,2) -- 1

#RAND()	返回 0 到 1 的随机数　　	
SELECT RAND() --0.93099315644334
-- RAND(seed) 在开发中指定了seed则会固定得到一个0-1的随机数
-- For instance
mysql> select rand();
+--------------------+
| rand()             |
+--------------------+
| 0.9477880121653788 |
+--------------------+
1 row in set (0.00 sec)
mysql> select rand();
+--------------------+
| rand()             |
+--------------------+
| 0.7799059001541752 |
+--------------------+
1 row in set (0.00 sec)

mysql> select rand(5);
+---------------------+
| rand(5)             |
+---------------------+
| 0.40613597483014313 |
+---------------------+
1 row in set (0.00 sec)
-- RAND(seed) 在开发中指定了seed则会固定得到一个0-1的随机数
mysql> select rand(5);
+---------------------+
| rand(5)             |
+---------------------+
| 0.40613597483014313 |
+---------------------+
1 row in set (0.00 sec)

mysql> select rand(5);
+---------------------+
| rand(5)             |
+---------------------+
| 0.40613597483014313 |
+---------------------+
1 row in set (0.00 sec)

#ROUND(x)	返回离 x 最近的整数	
SELECT ROUND(1.23456) --1

```

##### 系统函数&加密函数

```sql
#USER()	返回当前用户	
SELECT USER();
-> guest@%

#DATABASE()	返回当前数据库名	
SELECT DATABASE();   
-> runoob

# MD5（str） 为字符串算出一个MD5 char(32) 的字符串--用户密码加密
-- root 密码存入的是加密后的
mysql> select MD5('zjhzjhzjh');
+----------------------------------+
| MD5('zjhzjhzjh')                 |
+----------------------------------+
| 4192290b1061348ea435f0595e65e933 |
+----------------------------------+
1 row in set (0.00 sec)
mysql> insert into student4 values(1001,'张锦豪',MD5('zjh20001207'),current_date);
Query OK, 1 row affected (0.14 sec)

mysql> select * from student4;
+------+-----------+----------------------------------+------------+
| id   | name      | password                         | birthday   |
+------+-----------+----------------------------------+------------+
| 1001 | 张锦豪    | dd60ed8124010280d53bda4cfd3bb6a5 | 2022-09-02 |
+------+-----------+----------------------------------+------------+
1 row in set (0.00 sec)

```



##### 流程控制

```sql
#IF(expr,v1,v2)	如果表达式 expr 成立，返回结果 v1；否则，返回结果 v2。	
SELECT IF(1 > 0,'正确','错误')    
->正确

#IFNULL(v1,v2)	如果 v1 的值不为 NULL，则返回 v1，否则返回 v2。	
SELECT IFNULL(null,'Hello Word')
->Hello Word

#CASE expression
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
   ...
    WHEN conditionN THEN resultN
    ELSE result
	END	
CASE 表示函数开始，END 表示函数结束。如果 condition1 成立，则返回 result1, 如果 condition2 成立，则返回 result2，当全部不成立则返回 result，而当有一个成立之后，后面的就不执行了。	
SELECT CASE 
　　WHEN 1 > 0
　　THEN '1 > 0'
　　WHEN 2 > 0
　　THEN '2 > 0'
　　ELSE '3 > 0'
　　END
->1 > 0

-- For instance
mysql> select case
    ->     -> when job='clerk'
    ->     -> then '职员'
    ->     -> when job='manager'
    ->     -> then '经理'
    ->     -> when job='salesman'
    ->     -> when job='salesman'^C
mysql> select case
    -> when job='clerk' then '职员'
    -> when job='manager' then '经理'
    -> when job='salesman' then '销售'
    -> else job
    -> end
    -> from emp;
+---------------------------------------------------------------------------------------------------------------------+
| case
when job='clerk' then '职员'
when job='manager' then '经理'
when job='salesman' then '销售'
else job
end       |
+---------------------------------------------------------------------------------------------------------------------+
| 职员                                                                                                                |
| 销售                                                                                                                |
| 销售                                                                                                                |
| 经理                                                                                                                |
| 销售                                                                                                                |
| 经理                                                                                                                |
| 经理                                                                                                                |
| analyst                                                                                                             |
| president                                                                                                           |
| 销售                                                                                                                |
| 职员                                                                                                                |
| analyst                                                                                                             |
| 职员                                                                                                                |
+---------------------------------------------------------------------------------------------------------------------+
13 rows in set (0.00 sec)
```



#### 内连接

```sql
#自连接-- 把同一张表当作两张表来使用 需要给表命别名来区分 （表名 别名 表名 别名）列名不明确时要给列 AS 别名
#开发中常用
-- For instance
-- 把一张表当作两张表来使用 from后给同一张表命两个别名来作为两张表进行区分 列的输入使用 表别名.列的形式 条件限制找到关联处
mysql> select worker.ename as 'woker',leader.ename as 'leader' from emp worker,emp leader where worker.mgr=leader.empno;
+--------+--------+
| woker  | leader |
+--------+--------+
| FORD   | JONES  |
| SCOTT  | JONES  |
| JAMES  | BLAKE  |
| TURNER | BLAKE  |
| MARTIN | BLAKE  |
| WARD   | BLAKE  |
| ALLEN  | BLAKE  |
| MILLER | CLARK  |
| CLARK  | KING   |
| BLAKE  | KING   |
| JONES  | KING   |
| SMITH  | FORD   |
+--------+--------+
12 rows in set (0.00 sec)
```



#### 外连接★

```sql
#JOIN 按照功能大致分为如下三类：

INNER JOIN（内连接,或等值连接）：获取两个表中字段匹配关系的记录。
LEFT JOIN（左连接）：获取左表所有记录，即使右表没有对应匹配的记录。
RIGHT JOIN（右连接）： 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。

-- 
mysql> select * from tb1;
+------+---------------+--------------+------------+
| id   | title         | author       | date       |
+------+---------------+--------------+------------+
|    1 | 学习 PHP      | 菜鸟教程     | 2017-04-12 |
|    2 | 学习 MySQL    | 菜鸟教程     | 2017-04-12 |
|    3 | 学习 Java     | RUNOOB.COM   | 2015-05-01 |
|    4 | 学习 Python   | RUNOOB.COM   | 2016-03-06 |
|    5 | 学习 C        | FK           | NULL       |
+------+---------------+--------------+------------+
5 rows in set (0.00 sec)

mysql> select * from tb2;
+--------------+-------+
| author       | count |
+--------------+-------+
| 菜鸟教程     |    10 |
| RUNOOB.COM   |    20 |
| Google       |    22 |
+--------------+-------+
3 rows in set (0.00 sec)

#INNER JOIN（内连接,或等值连接）：获取两个表中字段匹配关系的记录。
-- For instance -- (inner) join on
mysql> select * from tb1 join tb2 on tb1.author = tb2.author;
+------+---------------+--------------+------------+--------------+-------+
| id   | title         | author       | date       | author       | count |
+------+---------------+--------------+------------+--------------+-------+
|    1 | 学习 PHP      | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    2 | 学习 MySQL    | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    3 | 学习 Java     | RUNOOB.COM   | 2015-05-01 | RUNOOB.COM   |    20 |
|    4 | 学习 Python   | RUNOOB.COM   | 2016-03-06 | RUNOOB.COM   |    20 |
+------+---------------+--------------+------------+--------------+-------+
4 rows in set (0.00 sec)
-- 相当于使用where子句
mysql> select * from tb1 ,tb2 where tb1.author = tb2.author;
+------+---------------+--------------+------------+--------------+-------+
| id   | title         | author       | date       | author       | count |
+------+---------------+--------------+------------+--------------+-------+
|    1 | 学习 PHP      | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    2 | 学习 MySQL    | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    3 | 学习 Java     | RUNOOB.COM   | 2015-05-01 | RUNOOB.COM   |    20 |
|    4 | 学习 Python   | RUNOOB.COM   | 2016-03-06 | RUNOOB.COM   |    20 |
+------+---------------+--------------+------------+--------------+-------+
4 rows in set (0.00 sec)

#LEFT JOIN（左连接）：获取左表所有记录，即使右表没有对应匹配的记录。
mysql> select * from tb1 left join tb2 on tb1.author = tb2.author;
+------+---------------+--------------+------------+--------------+-------+
| id   | title         | author       | date       | author       | count |
+------+---------------+--------------+------------+--------------+-------+
|    1 | 学习 PHP      | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    2 | 学习 MySQL    | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    3 | 学习 Java     | RUNOOB.COM   | 2015-05-01 | RUNOOB.COM   |    20 |
|    4 | 学习 Python   | RUNOOB.COM   | 2016-03-06 | RUNOOB.COM   |    20 |
|    5 | 学习 C        | FK           | NULL       | NULL         |  NULL |
+------+---------------+--------------+------------+--------------+-------+
5 rows in set (0.00 sec)

#RIGHT JOIN（右连接）： 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。
mysql> select * from tb1 right join tb2 on tb1.author = tb2.author;
+------+---------------+--------------+------------+--------------+-------+
| id   | title         | author       | date       | author       | count |
+------+---------------+--------------+------------+--------------+-------+
|    2 | 学习 MySQL    | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    1 | 学习 PHP      | 菜鸟教程     | 2017-04-12 | 菜鸟教程     |    10 |
|    4 | 学习 Python   | RUNOOB.COM   | 2016-03-06 | RUNOOB.COM   |    20 |
|    3 | 学习 Java     | RUNOOB.COM   | 2015-05-01 | RUNOOB.COM   |    20 |
| NULL | NULL          | NULL         | NULL       | Google       |    22 |
+------+---------------+--------------+------------+--------------+-------+
5 rows in set (0.00 sec)

```



#### 约束

```sql
#约束
-- SQL 约束（Constraints）
-- SQL 约束用于规定表中的数据规则。

-- 如果存在违反约束的数据行为，行为会被约束终止。

-- 约束可以在创建表时规定（通过 CREATE TABLE 语句），或者在表创建之后规定（通过 ALTER TABLE 语句）。

SQL CREATE TABLE + CONSTRAINT 语法
CREATE TABLE table_name
(
column_name1 data_type(size) constraint_name,
column_name2 data_type(size) constraint_name,
column_name3 data_type(size) constraint_name,
....
);
在 SQL 中，我们有如下约束：

NOT NULL - 指示某列不能存储 NULL 值。
UNIQUE - 保证某列的每行必须有唯一的值。
PRIMARY KEY - NOT NULL 和 UNIQUE 的结合。确保某列（或两个列多个列的结合）有唯一标识，有助于更容易更快速地找到表中的一个特定的记录。
FOREIGN KEY - 保证一个表中的数据匹配另一个表中的值的参照完整性。
CHECK - 保证列中的值符合指定的条件。
DEFAULT - 规定没有给列赋值时的默认值

-- 通过 show create table 表名 可以查看所有constraint -- 尤其是可以查看到忘记命名的constraint 系统自动生成的constraint命名
mysql> show create table student_test2;
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table         | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                               |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| student_test2 | CREATE TABLE `student_test2` (
  `id` int NOT NULL DEFAULT '0',
  `address` varchar(25) COLLATE utf8mb3_bin NOT NULL DEFAULT 'CHINA',
  `birthday` date NOT NULL DEFAULT '2000-01-01',
  KEY `fk_id` (`id`),
  CONSTRAINT `fk_id` FOREIGN KEY (`id`) REFERENCES `student_test1` (`id`),
  CONSTRAINT `chk_birthday` CHECK ((`birthday` between _utf8mb3'1983-01-01' and _utf8mb3'2002-01-01')),
  CONSTRAINT `student_test2_chk_1` CHECK ((`id` between 0 and 100))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_bin |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

```

##### not null

```sql
#not null
SQL NOT NULL 约束
#在默认的情况下，表的列接受 NULL 值。

SQL NOT NULL 约束
NOT NULL 约束强制列不接受 NULL 值。

NOT NULL 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录。

下面的 SQL 强制 "ID" 列、 "LastName" 列以及 "FirstName" 列不接受 NULL 值：

实例
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
#添加 NOT NULL 约束
在一个已创建的表的 "Age" 字段中添加 NOT NULL 约束如下所示：

实例
ALTER TABLE Persons
MODIFY Age int NOT NULL;
mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | YES  |     | NULL    |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> alter table student_test1 modify id int not null;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   |     | NULL    |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
#删除 NOT NULL 约束
在一个已创建的表的 "Age" 字段中删除 NOT NULL 约束如下所示：

实例
ALTER TABLE Persons
MODIFY Age int NULL;
mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   |     | 0       |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> alter table student_test1 modify id int null;
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | YES  |     | NULL    |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```



##### unique

```sql
#SQL UNIQUE 约束-- 如果没有指定not null 则unique字段可以有多个null；
-- 如果制定了not null 同时指定了unique 等同于primary key
UNIQUE 约束唯一标识数据库表中的每条记录。

UNIQUE 和 PRIMARY KEY 约束均为列或列集合提供了唯一性的保证。

PRIMARY KEY 约束拥有自动定义的 UNIQUE 约束。

请注意，每个表可以有多个 UNIQUE 约束，但是每个表只能有一个 PRIMARY KEY 约束。

CREATE TABLE 时的 SQL UNIQUE 约束
下面的 SQL 在 "Persons" 表创建时在 "P_Id" 列上创建 UNIQUE 约束：

MySQL：

CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
UNIQUE (P_Id)
)
#ALTER TABLE 时的 SQL UNIQUE 约束
当表已被创建时，如需在 "P_Id" 列创建 UNIQUE 约束，请使用下面的 SQL：

MySQL / SQL Server / Oracle / MS Access：

ALTER TABLE Persons
ADD UNIQUE (P_Id)
如需命名 UNIQUE 约束，并定义多个列的 UNIQUE 约束，请使用下面的 SQL 语法：

MySQL / SQL Server / Oracle / MS Access：

ALTER TABLE Persons
ADD CONSTRAINT uc_PersonID UNIQUE (P_Id,LastName)

mysql> alter table student_test1 add constraint unique (id);
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | NULL    |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

#撤销 UNIQUE 约束
如需撤销 UNIQUE 约束，请使用下面的 SQL：

MySQL：

ALTER TABLE Persons
DROP INDEX uc_PersonID
```



##### primary key

```sql
#主键
SQL PRIMARY KEY 约束
PRIMARY KEY 约束唯一标识数据库表中的每条记录。

主键必须包含唯一的值。

主键列不能包含 NULL 值。

每个表都应该有一个主键，并且每个表只能有一个主键

#单列主键
mysql> create table sutdennt_test1 
(`id` int not null default 0,`name` varchar(25) not null default "学生",`major` varchar(25) not null default "IT",
 primary key(id))
 character set utf8 collate utf8_bin;
Query OK, 0 rows affected, 2 warnings (0.15 sec)
mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | 0       |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
mysql> insert into student_test1 values(1002,'James','Basketball'),(1003,'Ivring','Basketball');
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from student_test1;
+------+------------+------------+
| id   | name       | major      |
+------+------------+------------+
| 1001 | EddieZhang | Java       |
| 1002 | James      | Basketball |
| 1003 | Ivring     | Basketball |
+------+------------+------------+
3 rows in set (0.00 sec)
mysql> insert into student_test1 values(1001,'Durant','Basketball');-- 主键的数据必须非空且唯一
ERROR 1062 (23000): Duplicate entry '1001' for key 'student_test1.PRIMARY'
mysql> insert into student_test1 values(1004,'Durant','Basketball');
Query OK, 1 row affected (0.00 sec)
#（复合主键）多列主键-- 将多个列作为主键 
#只有同时满足主键的多个列都相等时才会ERROR 1062 (23000): Duplicate entry '1001-EddieZhang' for key 'student_test1.PRIMARY'
mysql> alter table student_test1 add primary key(id,name);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | 0       |       |
| name  | varchar(25) | NO   | PRI | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
mysql> insert into student_test1 values(1001,'EddieZ','Java');
Query OK, 1 row affected (0.14 sec)

mysql> select * from student_test1;
+------+------------+------------+
| id   | name       | major      |
+------+------------+------------+
| 1001 | EddieZ     | Java       |
| 1001 | EddieZhang | Java       |
| 1002 | James      | Basketball |
| 1003 | Ivring     | Basketball |
| 1004 | Durant     | Basketball |
+------+------------+------------+
5 rows in set (0.00 sec)
mysql> insert into student_test1 values(1001,'EddieZhang','Java');
ERROR 1062 (23000): Duplicate entry '1001-EddieZhang' for key 'student_test1.PRIMARY'
mysql>
#alter table add主键
mysql> alter table student_test1 add primary key(id,name);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | 0       |       |
| name  | varchar(25) | NO   | PRI | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
#drop 删除主键
删除PRIMARY KEY约束时，不论约束条件为一列还是多列，对于MySQL，撤销都是

ALTER TABLE Persons
DROP PRIMARY KEY
由于PRIMARY KEY唯一性，MYSQL处理办法简单
mysql> insert into student_test1 values(1001,'EddieZhang','Java');
ERROR 1062 (23000): Duplicate entry '1001-EddieZhang' for key 'student_test1.PRIMARY'
mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | 0       |       |
| name  | varchar(25) | NO   | PRI | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> alter table student_test1 drop primary key;
Query OK, 5 rows affected (0.02 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> describe student_test1;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   |     | 0       |       |
| name  | varchar(25) | NO   |     | 学生    |       |
| major | varchar(25) | NO   |     | IT      |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

```

##### foreign key

```sql
#SQL FOREIGN KEY 约束-- 用于定义主表和从表之间的关系
-- 外键约束要定义在从表上，主表则必须具有主键约束或者unique约束。
-- 当定义外键后，要求外键列数据必须在在主表的主键列存在或者为null;
-- FOREIGN KEY 约束用于预防破坏表之间连接的行为。
-- FOREIGN KEY 约束也能防止非法数据插入外键列，因为它必须是它指向的那个表中的值之一
-- 表的engine必须是innodb 这样的表才支持外键;
-- 外键字段类型要与主键字段类型一致（长度可以不同）
一个表中的 FOREIGN KEY 指向另一个表中的 UNIQUE KEY(唯一约束的键)
-- 在创建外键约束时，必须先创建外键约束所依赖的表（先创建主表），并且该列为该表的主键
-- 子表：谁创建外键谁就是子表 父表：这个外键所依赖的表
一、删除时，未指定cascade时

  1）删除父表/数据

      a.因为子表与父表一一对应，删除父表数据时，需要先把子表对应数据删除否则无法删除

     b. 同理，删除表的时候，也需要先删除子表再删除父表

解决方案：

     a.指定cascade，删除父表、数据

        CASCADE指当删除主表中被引用列的数据时，级联删除子表中相应的数据行。

     b.禁用约束（子表的外键约束）

         ALTER TABLE 表名 disable constraint 约束名;

 2）删除子表：可以删除子表或者数据不报错

二、更新时

        a.更新父表会违反约束

        b.可以更新子表

        c.没有针对约束的级联更新

三、插入时

         a.父表可以插入

         b.子表插入会违反约束
         
#在创建表的时候指定外键约束

CREATE TABLE 表名
    (
        column1 datatype null/not null,
        column2 datatype null/not null,
        ...
        CONSTRAINT 外键约束名 FOREIGN KEY  (column1,column2,... column_n) 
        REFERENCES 外键依赖的表 (column1,column2,...column_n)
        ON DELETE CASCADE--级联删除
    );
    
    mysql> create table student_test2 (
    -> `id` int not null default 0,
    -> `address` varchar(25) not null default 'CHINA',
    -> `birthday` date not null default '2000-01-01',
    -> constraint fk_id foreign key (id) references student_test1 (id))
    -> character set utf8 collate utf8_bin;
Query OK, 0 rows affected, 2 warnings (0.03 sec)

#在创建表后增加外键约束

ALTER TABLE 表名
    ADD CONSTRAINT 外键约束名
    FOREIGN KEY (column1, column2,...column_n) 
    REFERENCES 外键所依赖的表 (column1,column2,...column_n)
    ON DELETE CASCADE;--级联删除
    
    mysql> alter table student_test2 add constraint fk_id foreign key (id) references student_test1 (id);
Query OK, 4 rows affected (0.15 sec)
Records: 4  Duplicates: 0  Warnings: 0
    
#撤销 FOREIGN KEY 约束
如需撤销 FOREIGN KEY 约束，请使用下面的 SQL：

MySQL：

ALTER TABLE Orders
DROP FOREIGN KEY fk_PerOrders

mysql> alter table student_test2 drop constraint fk_id;
Query OK, 0 rows affected (0.01 sec)


```



##### check

```sql
#check
SQL CHECK 约束
CHECK 约束用于限制列中的值的范围。

如果对单个列定义 CHECK 约束，那么该列只允许特定的值。

如果对一个表定义 CHECK 约束，那么此约束会基于行中其他列的值在特定的列中对值进行限制

#CREATE TABLE 时的 SQL CHECK 约束
MySQL：

CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
CHECK (P_Id>0)
)

mysql> create table student_test3 (
    -> `id` int not null default 0,
    -> `address` varchar(25) not null default 'CHINA',
    -> `birthday` date not null default '2000-01-01',
    -> constraint fk_student_test3_id foreign key (id) references student_test1 (id),
    -> constraint chk_id check (id between 0 and 100))
    -> character set utf8 collate utf8_bin engine innodb;
Query OK, 0 rows affected, 2 warnings (0.02 sec)

#ALTER TABLE 时的 SQL CHECK 约束
MySQL / SQL Server / Oracle / MS Access:

ALTER TABLE Persons
ADD CHECK (P_Id>0)

mysql> alter table student_test3
    -> add constraint chk_birth check (birthday between '1985-01-01' and '2002-01-01')
    -> ;
Query OK, 0 rows affected (0.04 sec)

#如需命名 CHECK 约束，并定义多个列的 CHECK 约束，请使用下面的 SQL 语法
CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
CONSTRAINT chk_Person CHECK (P_Id>0 AND City='Sandnes')
)

mysql> alter table student_test3 add constraint chk_student_test3 check (id between 0 and 100
    -> and birthday between '1985-01-01' and '2002-01-01');
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> show create table student_test3;
+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table         | Create Table                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| student_test3 | CREATE TABLE `student_test3` (
  `id` int NOT NULL DEFAULT '0',
  `address` varchar(25) COLLATE utf8mb3_bin NOT NULL DEFAULT 'CHINA',
  `birthday` date NOT NULL DEFAULT '2000-01-01',
  KEY `fk_student_test3_id` (`id`),
  CONSTRAINT `fk_student_test3_id` FOREIGN KEY (`id`) REFERENCES `student_test1` (`id`),
  CONSTRAINT `chk_student_test3` CHECK (((`id` between 0 and 100) and (`birthday` between _utf8mb3'1985-01-01' and _utf8mb3'2002-01-01')))
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_bin |
+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
#撤销 CHECK 约束
SQL Server / Oracle / MS Access：

ALTER TABLE Persons
DROP CONSTRAINT chk_Person

mysql> alter table student_test3
    -> add constraint chk_birth check (birthday between '1985-01-01' and '2002-01-01')
    -> ;
Query OK, 0 rows affected (0.04 sec)

```

![image-20220904211021997](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220904211021997.png)

```sql
#例题训练
create table goods (
goods_id int not null default 0 PRIMARY key,
goods_name varchar(25) not null default '',
unitprice double not null default 0,
category int not null default 0,
provider varchar(35) not null default '')
character set utf8 collate utf8_bin engine innodb;
alter table goods modify unitprice int not null default 0 constraint chk_price check (unitprice >= 1.0 and unitprice <= 9999.99);

create table customer (
customer_id int not null default 0 primary key,
`name` varchar(25) not null default '',
`address` varchar(55) not null default '',
`email` varchar(55) not null default '' unique,
`sex` enum ('男','女'),
card_id varchar(35) not null default '')
character set utf8 collate utf8_bin;

create table purchase (
order_id int not null default 0 primary key,
customer_id int not null default 0,
goods_id int not null default 0,
constraint fk_customer foreign key (customer_id) references customer (customer_id),
constraint fk_goods foreign key (goods_id) references goods (goods_id)
)character set utf8 collate utf8_bin engine innodb;

```



##### auto_increment

**清空数据表并且自增从头开始的sql命令**

**truncate** table table_name; *//table_name 该数据表名称* 

删除完还没有新增数据，即还没有出现不连贯的数据ID时，执行以下语句：

ALTER TABLE 表名 AUTO_INCREMENT = 1;
1
**如果已知下一条数据自增的ID（假设是10），可以直接写成ALTER TABLE 表名 AUTO_INCREMENT = 10;这样再插入数据时，自增ID会从10开始**，也可以用这个语法来跳过一些编号。此外，如果AUTO_INCREMENT 的值小于ID的最大值，那么ID是从MAX(ID)+1开始自增，所以当AUTO_INCREMENT = 1时，一般默认ID是从最大值加一开始自增的。

表中已经出现不连贯的数据ID时，执行以下语句进行修改

SET @auto_id = 0;
UPDATE 表名 SET 自增字段名 = (@auto_id := @auto_id + 1);
ALTER TABLE 表名 AUTO_INCREMENT = 1;


如果需要清空表的数据的话，最好使用TRUNCATE TABLE 表名来删除，这样新增的数据自增ID会从1开始，如果使用DELETE来删除，新增的数据会沿着之前的ID

```sql
#自增长 auto increment
#AUTO INCREMENT 字段
我们通常希望在每次插入新记录时，自动地创建主键字段的值。

我们可以在表中创建一个 auto-increment 字段。

用于 MySQL 的语法
下面的 SQL 语句把 "Persons" 表中的 "ID" 列定义为 auto-increment 主键字段：

CREATE TABLE Persons
(
ID int NOT NULL AUTO_INCREMENT,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
PRIMARY KEY (ID)
)
MySQL 使用 AUTO_INCREMENT 关键字来执行 auto-increment 任务。

默认地，AUTO_INCREMENT 的开始值是 1，每条新记录递增 1。

要让 AUTO_INCREMENT 序列以其他的值起始，请使用下面的 SQL 语法：

ALTER TABLE Persons AUTO_INCREMENT=100
要在 "Persons" 表中插入新记录，我们不必为 "ID" 列规定值（会自动添加一个唯一的值）：

INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen')
上面的 SQL 语句会在 "Persons" 表中插入一条新记录。"ID" 列会被赋予一个唯一的值。"FirstName" 列会被设置为 "Lars"，"LastName" 列会被设置为 "Monsen"

#给已经存在的colume添加自增语法：

ALTER TABLE table_name CHANGE column_name column_name data_type(size) constraint_name AUTO_INCREMENT;
比如：

ALTER TABLE student CHANGE id id INT( 11 ) NOT NULL AUTO_INCREMENT;

#在添加数据时给自增长字段列指定值；则以指定的值为准且后续的值按照指定值开始自增长
mysql> select * from student_test4;
+-----+-----------+
| id  | name      |
+-----+-----------+
| 100 | 张锦豪    |
| 101 | 欧文      |
| 102 | 詹姆斯    |
| 103 | 杜兰特    |
| 104 | 库里      |
+-----+-----------+
5 rows in set (0.00 sec)

mysql> insert into student_test4 values(660,'东七七');
Query OK, 1 row affected (0.00 sec)

mysql> insert into student_test4 (`name`) values('塔图姆');
Query OK, 1 row affected (0.12 sec)

mysql> select * from student_test4;
+-----+-----------+
| id  | name      |
+-----+-----------+
| 100 | 张锦豪    |
| 101 | 欧文      |
| 102 | 詹姆斯    |
| 103 | 杜兰特    |
| 104 | 库里      |
| 660 | 东七七    |
| 661 | 塔图姆    |
+-----+-----------+
7 rows in set (0.00 sec)
```



#### 索引★

```sql
MySQL索引的建立对于MySQL的高效运行是很重要的，索引可以大大提高MySQL的检索速度。只对创建了索引的列有效

打个比方，如果合理的设计且使用索引的MySQL是一辆兰博基尼的话，那么没有设计和使用索引的MySQL就是一个人力三轮车。

拿汉语字典的目录页（索引）打比方，我们可以按拼音、笔画、偏旁部首等排序的目录（索引）快速查找到需要的字。

索引分单列索引和组合索引。单列索引，即一个索引只包含单个列，一个表可以有多个单列索引，但这不是组合索引。组合索引，即一个索引包含多个列。

创建索引时，你需要确保该索引是应用在 SQL 查询语句的条件(一般作为 WHERE 子句的条件)。

实际上，索引也是一张表，该表保存了主键与索引字段，并指向实体表的记录。

上面都在说使用索引的好处，但过多的使用索引将会造成滥用。因此索引也会有它的缺点：虽然索引大大提高了查询速度，同时却会降低更新表的速度，如对表进行INSERT、UPDATE和DELETE。因为更新表时，MySQL不仅要保存数据，还要保存一下索引文件。

建立索引会占用磁盘空间的索引文件

```

![image-20220905074911013](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905074911013.png)

![image-20220905075120329](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905075120329.png)

![image-20220905102533069](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905102533069.png)

##### 主键索引

```sql
#主键索引
主键自动为主索引（类型primary key）
```

##### 唯一索引（UNIQUE）

```sql
#唯一索引
它与前面的普通索引类似，不同的就是：索引列的值必须唯一，但允许有空值。如果是组合索引，则列值的组合必须唯一。它有以下几种创建方式：

创建索引
CREATE UNIQUE INDEX indexName ON mytable(username(length)) 

create unique index index_emp on emp(empno);

修改表结构
ALTER table mytable ADD UNIQUE [indexName] (username(length))
创建表的时候直接指定
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
UNIQUE [indexName] (username(length))  
 
);  
使用ALTER 命令添加和删除索引
有四种方式来添加数据表的索引：

ALTER TABLE tbl_name ADD PRIMARY KEY (column_list): 该语句添加一个主键，这意味着索引值必须是唯一的，且不能为NULL。
ALTER TABLE tbl_name ADD UNIQUE index_name (column_list): 这条语句创建索引的值必须是唯一的（除了NULL外，NULL可能会出现多次）。
ALTER TABLE tbl_name ADD INDEX index_name (column_list): 添加普通索引，索引值可出现多次。
ALTER TABLE tbl_name ADD FULLTEXT index_name (column_list):该语句指定了索引为 FULLTEXT ，用于全文索引。
以下实例为在表中添加索引。

mysql> ALTER TABLE testalter_tbl ADD INDEX (c);
你还可以在 ALTER 命令中使用 DROP 子句来删除索引。尝试以下实例删除索引:

mysql> ALTER TABLE testalter_tbl DROP INDEX c;
使用 ALTER 命令添加和删除主键
主键作用于列上（可以一个列或多个列联合主键），添加主键索引时，你需要确保该主键默认不为空（NOT NULL）。实例如下：

mysql> ALTER TABLE testalter_tbl MODIFY i INT NOT NULL;
mysql> ALTER TABLE testalter_tbl ADD PRIMARY KEY (i);
你也可以使用 ALTER 命令删除主键：

mysql> ALTER TABLE testalter_tbl DROP PRIMARY KEY;
删除主键时只需指定 PRIMARY KEY，但在删除索引时，你必须知道索引名

```



##### 普通索引（INDEX）

```sql
#普通索引
创建索引
这是最基本的索引，它没有任何限制。它有以下几种创建方式：

CREATE INDEX indexName ON table_name (column_name)
如果是CHAR，VARCHAR类型，length可以小于字段实际长度；如果是BLOB和TEXT类型，必须指定 length

create index index_emp on emp (empno);

修改表结构(添加索引)
ALTER table tableName ADD INDEX indexName(columnName)

alter table emp.emp add index index_emp (empno);

创建表的时候直接指定
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
INDEX [indexName] (username(length))  
 
);  
删除索引的语法
DROP INDEX [indexName] ON mytable;

```



##### 全文索引

#### 事务

![image-20220905103719377](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905103719377.png)

![image-20220905104030470](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905104030470.png)

![image-20220905235904013](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905235904013.png)

![image-20220905104709042](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905104709042.png)

![image-20220905104832325](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905104832325.png)

##### 事务管理

##### save point

##### rollback

##### commit

##### 事务控制语句

```sql
BEGIN 或 START TRANSACTION 显式地开启一个事务；

COMMIT 也可以使用 COMMIT WORK，不过二者是等价的。COMMIT 会提交事务，并使已对数据库进行的所有修改成为永久性的；

ROLLBACK 也可以使用 ROLLBACK WORK，不过二者是等价的。回滚会结束用户的事务，并撤销正在进行的所有未提交的修改；

SAVEPOINT identifier，SAVEPOINT 允许在事务中创建一个保存点，一个事务中可以有多个 SAVEPOINT；

RELEASE SAVEPOINT identifier 删除一个事务的保存点，当没有指定的保存点时，执行该语句会抛出一个异常；

ROLLBACK TO identifier 把事务回滚到标记点；

SET TRANSACTION 用来设置事务的隔离级别。InnoDB 存储引擎提供事务的隔离级别有READ UNCOMMITTED、READ COMMITTED、REPEATABLE READ 和 SERIALIZABLE。
MYSQL 事务处理主要有两种方法：
1、用 BEGIN, ROLLBACK, COMMIT来实现

BEGIN 开始一个事务
ROLLBACK 事务回滚
COMMIT 事务确认
2、直接用 SET 来改变 MySQL 的自动提交模式:

SET AUTOCOMMIT=0 禁止自动提交
SET AUTOCOMMIT=1 开启自动提交
```



##### 隔离级别

![image-20220905105530766](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905105530766.png)

![image-20220905105812053](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905105812053.png)

##### ACID

```sql
事务是必须满足4个条件（ACID）：
原子性（Atomicity，或称不可分割性）、
一致性（Consistency）、
隔离性（Isolation，又称独立性）、
持久性（Durability）。

原子性：一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。

一致性：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。

隔离性：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。

持久性：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。
```



#### 视图

视图的理解

1.可以看作是一个虚拟的表，本身不存储数据 试图的可以理解为存储起来的select语句

2.试图创建时select语句设计的表 称之为基表

3.针对对视图进行的DML操作 会影响到基表 反之亦然

4.删除视图 不会导致到基表本身的数据被删除

5.视图的应用场景 针对于小型项目不建议使用视图 针对于大型项目推荐使用视图

6.视图的作用及优点 简化查询（将一次查询持久储存起来）；权限管理 （让不同权限的人员 看到表中不同范围的数据 控制数据的访问）

![image-20220905144613234](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220905144613234.png)

```sql
#SQL 视图（Views）
视图是可视化的表。

本章讲解如何创建、更新和删除视图。

SQL CREATE VIEW 语句
在 SQL 中，视图是基于 SQL 语句的结果集的可视化的表。

视图包含行和列，就像一个真实的表。视图中的字段就是来自一个或多个数据库中的真实的表中的字段。

您可以向视图添加 SQL 函数、WHERE 以及 JOIN 语句，也可以呈现数据，就像这些数据来自于某个单一的表一样。

SQL CREATE VIEW 语法

CREATE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition
注释：视图总是显示最新的数据！每当用户查询视图时，数据库引擎通过使用视图的 SQL 语句重建数据

-- For instance
mysql> create view view_emp1 as select empno,ename,job from emp where deptno = 30;
Query OK, 0 rows affected (0.00 sec)

mysql> select * from view_emp1;
+-------+--------+----------+
| empno | ename  | job      |
+-------+--------+----------+
|  7499 | ALLEN  | salesman |
|  7521 | WARD   | salesman |
|  7654 | MARTIN | salesman |
|  7698 | BLAKE  | manager  |
|  7844 | TURNER | salesman |
|  7900 | JAMES  | clerk    |
+-------+--------+----------+
6 rows in set (0.00 sec)

#SQL 更新视图
您可以使用下面的语法来更新视图：

SQL CREATE OR REPLACE VIEW 语法

CREATE OR REPLACE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition
现在，我们希望向 "Current Product List" 视图添加 "Category" 列。我们将通过下列 SQL 更新视图：

CREATE VIEW [Current Product List] AS
SELECT ProductID,ProductName,Category
FROM Products
WHERE Discontinued=No

-- For instance
mysql> create or replace view view_emp1 as select empno,ename,job,deptno from emp where deptno = 30;
Query OK, 0 rows affected (0.12 sec)

mysql> select * from view_emp1;
+-------+--------+----------+--------+
| empno | ename  | job      | deptno |
+-------+--------+----------+--------+
|  7499 | ALLEN  | salesman |     30 |
|  7521 | WARD   | salesman |     30 |
|  7654 | MARTIN | salesman |     30 |
|  7698 | BLAKE  | manager  |     30 |
|  7844 | TURNER | salesman |     30 |
|  7900 | JAMES  | clerk    |     30 |
+-------+--------+----------+--------+
6 rows in set (0.00 sec)

#SQL 撤销视图
您可以通过 DROP VIEW 命令来删除视图。

SQL DROP VIEW 语法
DROP VIEW view_name

-- For instance
mysql> drop view view_emp1;
Query OK, 0 rows affected (0.00 sec)

mysql> select * from view_emp1;
#ERROR 1146 (42S02): Table 'db02.view_emp1' doesn't exist


#视图的作用：

1、视图隐藏了底层的表结构，简化了数据访问操作，客户端不再需要知道底层表的结构及其之间的关系。

2、视图提供了一个统一访问数据的接口。（即可以允许用户通过视图访问数据的安全机制，而不授予用户直接访问底层表的权限）

3、从而加强了安全性，使用户只能看到视图所显示的数据。

4、视图还可以被嵌套，一个视图中可以嵌套另一个视图。
```

#### Mysql用户管理

```sql
#Mysql用户管理
-- 应用场景:当我们做项目开发时，可以根据不同的开发人员，赋给他们相应的Mysql操作权限	
-- Mysql数据库管理人员（root） 可以根据需要创建不同的用户，赋予相应的权限，供人员使用

#创建新的用户
create user 'EddieZ'@'localhost' identified by 'eddiez';
-- '用户名'@'指定端口号' identified by '密码'; -- Tip:存入到Mysql.user表时的密码是加密过的

#查看用户
select * from mysql.user-- 查看所有信息

mysql> select `user`,`host`,`authentication_string` from mysql.user;--查看指定信息

#删除用户
drop user 'EddieZ'@'localhost'

#登录
-- 不同的用户登录到数据库管理系统（DBMS）后，根据自身的相应权限，可以操作的数据库和数据对象（表，试图，触发器）都不一样。

#修改密码
-- 自己有权限修改自己的密码
set password = password('newpassword');
-- 非root无权修改别的用户的密码

-- root有权限修改别的用户的密码
set password for 'EddieZ'@'localhost' = password('newpassword');


```

不同的用户登录到数据库管理系统（DBMS）后，根据自身的相应权限，可以操作的数据库和数据对象（表，试图，触发器）都不一样。

![image-20220906135039895](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220906135039895.png)

![image-20220906142425068](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220906142425068.png)

```sql
mysql> create user eddiez;-- 创建用户的时候未指定host 则host为% 即表示所有的ip都有连接权限
Query OK, 0 rows affected (0.01 sec)

mysql> select `user`,`host` from mysql.user;
+------------------+-----------+
| user             | host      |
+------------------+-----------+
| eddiez           | %         |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+
5 rows in set (0.00 sec)

mysql> drop user eddiez;-- 如果删除的用户为指明端口 则只需要输入用户名即可
Query OK, 0 rows affected (0.01 sec)

mysql> create user 'eddiez'@'192.168.1.%';-- 创建用户的时候指定'192.168.1.%'端口号表示用户可以在192.168.1.*的ip（这个ip范围中）都可以登录
Query OK, 0 rows affected (0.12 sec)

mysql> select `user`,`host` from mysql.user;
+------------------+-------------+
| user             | host        |
+------------------+-------------+
| eddiez           | 192.168.1.% |
| mysql.infoschema | localhost   |
| mysql.session    | localhost   |
| mysql.sys        | localhost   |
| root             | localhost   |
+------------------+-------------+
5 rows in set (0.00 sec)

mysql> drop user 'eddiez'@'192.168.1.%';
Query OK, 0 rows affected (0.00 sec)-- 删除的用户指明了端口的 要输入用户完整的格式信息才能删除
```



#### Mysql权限管理

![image-20220906135412880](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220906135412880.png)

![image-20220906135605307](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220906135605307.png)

```sql
-- root用户给其他用户赋予权限
grant select,insert on db03.salgrade to 'EddieZ'@'localhost';
-- grant 权限列表 on 库.对象名 to 用户名 

-- root用户给其他用户增加权限
grant update on db03.salgrade to 'EddieZ'@'localhost';

-- root用户回收其他用户的权限
revoke update on db03.salgrade from 'Eddie'@'localhost';
revoke all on db03.salgrade from 'Eddie'@'localhost';-- 回收所有权限
-- root用户修改其他用户的密码
set password for 'EddieZ'@'localhost' = password('newpassword');

```



```sql
#test
#使用简单查询语句
-- 显示所有部门名称
select distinct dname from dept;
-- 显示所有雇员名以及其全年的收入 13月（工资加补助）指明别名 年收入
select ename,(sal + if((comm is null),0.0,comm))*13 as '年收入' from emp;
#限制查询语句
-- 显示工资超过2850的雇员的姓名和工资
select ename,sal from emp where sal > 2850;
-- 显示工资不在1500到2850之间的所有雇员名及其工资
select ename,sal from emp where NOT (sal between 1500 and 2850);
-- 显示编号为7566的雇员姓名及其所在部门编号
select ename,deptno from emp where empno = 7566;
-- 显示部门10和30中工资超过1500的雇员名及工资
select ename,sal from emp where 
(deptno = 10 or deptno = 30) and sal >= 1500;
-- 显示无管理者的雇员名及岗位
select ename,job from emp where mgr is null;
#排序数据
-- 显示在1991-02-01到1991-05-01之间雇佣的雇员名，岗位，及雇佣日期，并以雇佣日期进行排序
select ename,job,hiredate from emp where hiredate between '1991-02-01' and '1991-05-01' order by hiredate desc ;
-- 显示获得补助的所有员工名，工资及补助 并以工资降序排序
select ename,sal,comm from emp where comm is not null order by sal desc;
#6.
-- 1.
select * from emp where deptno = 30;
-- 2.
select ename,empno,deptno from emp where job = 'clerk';
-- 3.
select * from emp where comm > sal;
-- 4.
select * from emp where comm > (sal*0.6);
-- 5.
select * from emp where (deptno = 10 and job = 'manager') or (deptno = 20 and job = 'clerk');
-- 6.
select * from emp where (deptno = 10 and job = 'manager') or (deptno = 20 and job = 'clerk') or (job <> 'manager' and job <> 'clerk' and sal >= 2000);
-- 7.
select distinct job from emp where comm is not null;
-- 8.
select * from emp where comm is null or comm < 100;
-- 9.
select * from emp where DATEDIFF(LAST_DAY(hiredate),hiredate) <= 3;
-- 10.
select * from emp where DATE_ADD(hiredate,interval 31 YEAR) < NOW();
-- 11.
select CONCAT(LCASE(MID(ename,1,1)),(MID(ename,2))) from emp;
-- 12.
select ename from emp where LENGTH(ename) = 5;
-- 13.
select * from emp where ename not like '%R%';
-- 14.
select MID(ename,1,3) from emp;
-- 15.
select REPLACE(ename,'A','a') from emp;
-- 16.
select ename,hiredate from emp where DATE_ADD(hiredate,INTERVAL 12 year) <= NOW();
-- 17.
select * from emp ORDER BY ename DESC;
-- 18.
select ename,hiredate from emp order by hiredate asc;
-- 19.
select ename,job,sal from emp ORDER BY job desc , sal asc;
-- 20.
select ename,YEAR(hiredate),MONTH(hiredate),hiredate from emp order by MONTH(hiredate) , DAY(hiredate);
-- 21.
select TRUNCATE(sal/30,0) as '日薪资' from emp;
-- 22.
select * from emp where MONTH(hiredate) = 2;
-- 23.
select DATEDIFF(now(),hiredate) from emp;
-- 24.
select ename from emp where ename like '%A%';
-- 25.
select ename,CONCAT('已入职:',TRUNCATE((DATEDIFF(now(),hiredate)/365),0),'年',TRUNCATE((TRUNCATE((DATEDIFF(now(),hiredate)%365),0))/30,0),'月',
TRUNCATE((TRUNCATE((DATEDIFF(now(),hiredate)%365),0))%30,0),'天') AS '入职年限' from emp;
#7
-- 1.
select distinct emp.deptno from emp,dept where emp.deptno = dept.deptno;
select count(*) as 'num',deptno from emp group by deptno HAVING num >= 1;
-- 2.
select * from emp where sal > (select sal from emp where ename = 'SMITH');
-- 3.-- 把一张表看作是两张表来处理
select worker.ename as '员工名',worker.hiredate as '员工入职时间',leader.ename as '直接上级名',leader.hiredate as '上级入职时间'
			from emp as worker,emp as leader
			where worker.hiredate > leader.hiredate and worker.mgr = leader.empno;
-- 4.-- 使用外连接
select dept.dname,emp.*
			from dept LEFT JOIN emp on dept.deptno = emp.deptno;
-- 5.
select emp.ename,dept.dname
			from emp,dept where job = 'clerk' and emp.deptno = dept.deptno;
-- 6.
select distinct job from emp GROUP BY job HAVING min(sal) > 1500;
-- 7.
select ename from emp where deptno = 30;
-- 8.
select * from emp where sal > (select avg(sal) from emp);

#7
-- 9.
select * from emp where job = (select job from emp where ename = 'SCOTT');
-- 10.
select ename,sal from emp where sal > (select max(sal) from emp where deptno = 30);
-- 11.
select count(*) as '部门人数',avg(sal) as '平均工资',FORMAT(avg(DATEDIFF(NOW(),hiredate) / 356),1) as '平均服务期限（单位年）' from emp GROUP BY deptno;
-- 12.
select emp.ename,dept.dname,emp.sal
      from emp,dept
			where emp.deptno = dept.deptno;
-- 13.
select * from dept,(select count(*) as '部门人数',deptno from emp GROUP BY deptno) AS temp where temp.deptno = dept.deptno;
-- 14.
select job,min(sal) as '最低工资' from emp GROUP BY job;
-- 15.
select min(sal) as 'manager的最低工资' from emp where job = 'manager';
-- 16.
select ename,((sal + IFNULL(comm,0)) * 13) as yearsal from emp order by yearsal desc;

#8
create table `class` (
classid int not null default 0 primary key,`subject` varchar(15) not null default '',`deptname` varchar(15) not null default '',
enrolltime date not null default '2000-01-01')character set utf8 collate utf8_bin engine innodb;
desc class;
alter table class modify enrolltime YEAR;
alter table class add num tinyint not null default 0;
desc class;
insert into class values (101,'软件','计算机','1995',20),(102,'微电子','计算机','1996',30),(111,'无机化学','化学','1995',29),(112,'高分子化学','化学','1996',25),(121,'统计数学','数学','1995',20),(131,'现代语言','中文','1996',20),(141,'国际贸易','经济','1997',30),(142,'国际金融','经济','1996',14);
select * from class;
create table `student_table` (
`studentid` int not null default 0 primary key,`name` varchar(10) not null default '',`age` tinyint not null default 0,
classid int not null default 0,
constraint fk_classid foreign key (classid) references class (classid))character set utf8 collate utf8_bin engine innodb;
desc student_table;
insert into student_table values (8101,'张三',18,101),(8102,'钱四',16,121),(8103,'玉玲',17,131),(8105,'李飞',19,102),(8109,'赵四',18,141),(8110,'李可',20,142),(8201,'张飞',18,111),(8302,'周瑜',16,112),(8303,'王亮',17,111),(8305,'董庆',19,102),(8409,'赵龙',18,101),(8510,'李丽',20,142);
select * from student_table;
create table `department` (
departmentid int not null default 0 primary key,deptname varchar(15) not null default '',
constraint unique (deptname))character set utf8 collate utf8_bin engine innodb;
desc department;
insert into department values (001,'数学'),(002,'计算机'),(003,'化学'),(004,'中文'),(005,'经济');
select * from department;

#test
-- 1.
select * from student_table where name like '李%';
-- 2.
select distinct class.deptname from class,(select deptname,count(*) as num from class GROUP BY deptname) as temp_table where temp_table.num > 1 and 
temp_table.deptname = class.deptname;
-- 3.
select distinct department.departmentid,department.deptname,temp_table1.sum
			from department,(select class.deptname,sum(class.num) as sum from class GROUP BY deptname) as temp_table1 where department.deptname = temp_table1.deptname and temp_table1.sum >= 30;
-- 4.
insert into department values (006,'物理');
select * from department;
select * from class;
-- 5.-- 使用事务
-- 开启事务
start transaction;
-- 进行操作

update class set num = (num - 1) where classid = (select student_table.classid from student_table where student_table.`name` = '张三');-- 将班表中的人数变更
delete from student_table where student_table.`name` = '张三';-- 从学生表中删除
-- 确认无误 提交事务
commit;
select * from class;
select * from student_table;



-- 把系表中的id类型改为varchar(10)
delete from department;
alter table department MODIFY departmentid varchar(10) not null;
insert into department values ('001','数学'),('002','计算机'),('003','化学'),('004','中文'),('005','经济');
insert into department values ('006','物理');
desc department;
select * from department;
			



```



## 集合★

![image-20220815105857813](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815105857813.png)

![image-20220815105913796](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815105913796.png)

![image-20220815105930397](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815105930397.png)

![image-20220815105957948](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815105957948.png)

```java

```

![image-20220815110055757](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110055757.png)

```java

/**
 * Collection接口
 *  Collection接口：单列数据，定义了存取一组对象的方法的集合
 *  向Collection接口的实现类的对象中添加自定义的数据obj时 要求obj所在类对equals方法进行重写
 *
 *  * List：元素有序、可重复的集合
 *  * Set：元素无序、不可重复的集合--存放在Set容器中的对象，
 *                               对应的类一定要重写equals()和hashCode(Object obj)方法，以实现对象相等规则
 *
 *      ------List★
 *              ------ArrayList★---------------主要实现类 线程不安全的 效率较高 底层使用Object[]存储
 *
 *                          ------LinkedList----对于频繁的插入和删除操作-效率较高 底层使用双向链表存储
 *
 *              ------Vector--------------------古老实现类 -- since：jdk1.0 线程安全效率较低 底层使用Object[]存储
 *
 *      ------Set
 *              ------HashSet☆------------------主要实现类 线程不安全 可以存储null值 底层使用数组+链表储存
 *
 *                          ------LinkedHashSet--根据元素的 hashCode 值来决定元素的存储位置，但它同时使用双向链表维护元素的次序，
 *                                               这使得元素看起来是以插入顺序保存的 不允许集合元素重复
 *                                               LinkedHashSet插入性能略低于 HashSet，但在迭代访问 Set 里的全部元素时有很好的性能
 *
 *              ------TreeSet--------------------TreeSet 是 SortedSet 接口的实现类，TreeSet 可以确保集合元素处于排序状态。
 *                                               TreeSet底层使用红黑树结构存储数据
 *                                               TreeSet 两种排序方法：自然排序和定制排序。默认情况下，TreeSet 采用自然排序
 *                                                TreeSet和后面要讲的TreeMap采用红黑树的存储结构
 *                                                特点：有序，查询速度比List快
 *
 */
/*
        ArrayList底层源码debug
        底层使用Object[]数组
        开发中已知所需用集合容量的可以使用有参的构造器（指定ArrayList容量）进行实例化ArrayList--可以避免系统重复的扩容以及扩容检测--提高效率
     */
    @Test
    public void arrayListTest(){
        ArrayList arrayList = new ArrayList();//JDK8之后在new对象时并没有提供基本空间--
        // 在进行第一个add元素时候 初始化空间长度为10 在1-10的过程中每次都会判断是否要超出10 未超出直接添加元素在相应的位置上
        // 一旦进行第11个元素的add时候就在原有的空间长度上进行1.5倍的扩容
        //超过原本1.5倍扩容后的长度继续进行1.5倍扩容
        arrayList.add(1);
        arrayList.add(2);
        arrayList.add(3);
        arrayList.add(4);
        arrayList.add(5);
        arrayList.add(6);
        arrayList.add(7);
        arrayList.add(8);
        arrayList.add(9);
        arrayList.add(10);

        arrayList.add(11);
        arrayList.add(12);
        arrayList.add(13);
        arrayList.add(14);
        arrayList.add(15);
        arrayList.add(16);

    }
	/*
        Vector底层源码debug
        底层使用Object[]数组
     */
    @Test
    public void vectorTest(){
        Vector vector = new Vector();////在new对象时提供基本空间--初始化空间长度为10
        //public Vector() {
        //  this(initialCapacity 10);
        //}
        // 在1-10的过程中每次都会判断是否要超出10 未超出直接添加元素在相应的位置上
        // 一旦进行第11个元素的add时候就在原有的空间长度上进行2.0倍的扩容
        //超过原本2.0倍扩容后的长度继续进行2.0倍扩容
        vector.add(1);
        vector.add(2);
        vector.add(3);
        vector.add(4);
        vector.add(5);
        vector.add(6);
        vector.add(7);
        vector.add(8);
        vector.add(9);
        vector.add(10);
        //minGrowth = 1
        //prefGrowth = 10
        //prefLength = 20
        vector.add(11);
        vector.add(12);
        vector.add(13);
        vector.add(14);
        vector.add(15);
        vector.add(16);
        vector.add(17);
        vector.add(18);
        vector.add(19);
        vector.add(20);

        //minGrowth = 1
        //prefGrowth = 20
        //prefLength = 40
        vector.add(21);
    }

	/*
        linkedList底层源码debug
        底层使用Node数组+链表结构
     */
    @Test
    public void linkedListTest(){
        LinkedList linkedList = new LinkedList();
        //new对象的时候调用空参构造器
        //public LinkedList() {
        //}
        //调用add()方法添加元素
//        public boolean add(E e) {
//            linkLast(e);
//            return true;
//        }
        linkedList.add(1);//添加第一个元素时first和last都指向唯一的元素 元素的prev和next都为null 给第一个元素的位置赋值1
        //last = {LinkedList$Node@1156}
            // prev = null
            // next = null
            // item = {Integer@1155} 1
        //first = {LinkedList$Node@1156}
            // prev = null
            // next = null
            // item = {Integer@1155} 1
        linkedList.add(2);//添加第二个元素时 last指向后添加的第二个元素 新添加的元素的prev为前一个元素（即早于他添加的元素）next为null 给第二个元素赋值2
                                        //first指向第一个元素 第一个元素的prev为null next为新添加的元素
//        this = {LinkedList$Node@1148}
//        prev = {LinkedList$Node@1145}
//        item = {Integer@1144} 1
//        next = null
//        prev = null
//        element = {Integer@1142} 2
//        value = 2
//        next = null
//        this.next = null
//        this.prev = null

        //e = {Integer@1142} 2
        // value = 2
        //l = {LinkedList$Node@1145}
        // item = {Integer@1144} 1
        // next = {LinkedList$Node@1148}
        // prev = null
        //newNode = {LinkedList$Node@1148}
        // item = {Integer@1142} 2
        // next = null
        // prev = {LinkedList$Node@1145}
        //modCount = 1
        //l.next = {LinkedList$Node@1148}
        // item = {Integer@1142} 2
        // next = null
        // prev = {LinkedList$Node@1145}
        //size = 1

        linkedList.remove(0);//删除指定元素 指定删除的元素的prev&next为null 元素的值置空为null （等待GC处理）同时若指定删除元素有前后元素那么前后元素的prev&next置空并且相互指向
//        this = {LinkedList@1139}  size = 2
//        x = {LinkedList$Node@1149}
//        item = {Integer@1142} 1
//        next = null
//        prev = null
//        element = {Integer@1142} 1
//        value = 1
//        next = {LinkedList$Node@1150}
//        item = {Integer@1143} 2
//        next = null
//        prev = null
//        prev = null
//        modCount = 2
//        size = 2
//        x.item = {Integer@1142} 1
//        value = 1
//        x.next = null


    }


/**
 * Map接口
 * 双列数据，保存具有映射关系“key-value对”的集合
 *  Map与Collection并列存在。用于保存具有映射关系的数据:key-value
 *  Map 中的 key 和 value 都可以是任何引用类型的数据
 *  Map 中的 key 用Set来存放，不允许重复，即同一个 Map 对象所对应的类，须重写hashCode()和equals()方法
 *  常用String类作为Map的“键”
 *  key 和 value 之间存在单向一对一关系，即通过指定的 key 总能找到唯一的、确定的 value
 *  Map接口的常用实现类：HashMap、TreeMap、LinkedHashMap和Properties。其中，HashMap是 Map 接口使用频率最高的实现类
 *
 * Map接口---------------------------------双列数据，保存具有映射关系“key-value对”的集合
 *
 *      ----HashMap★---------------------线程不安全效率较高 可存储null的key/value 主要实现类
 *                                        底层储存（jdk7.0及之前）--数组+链表；
 *                                               （jdk8.0开始 ）--数组+链表+红黑树；
 *
 *              ----LinkedHashMap☆-------在遍历map元素时，可以按照添加的顺序遍历
 *                                        由于在原有的HashMap底层结构基础上，添加了一对 "指针" 指向前一个和后一个
 *                                        对于频繁的遍历操作，效率高于HashMap
 *
 *      ----TreeMap☆---------------------按照添加的key-value对进行排序，实现排序遍历 考虑的是key的自然排序/定制排序
 *                                        底层使用的红黑树的储存结构
 *
 *      ----Hashtable 古老的实现类----------线程安全效率较低 不可存储null的key/value
 *
 *              ----Properties☆----------常用来处理配置文件；key&value都是String类型
 *
 * Map结构的理解
 * Map中的key：------是无序的，不可重复的；使用Set储存所有的key------------->key所在的类要求要@override--equals（）& hashCode（）【 HashMap为例 】
 * Map中的value：----是无序的，可重复的；使用Collection储存所有的value----->value所在的类要求要@override--hashCode（）
 * 一个键值对（key-value）构成了一个Entry对象；key&value相当于Entry的两个属性
 * map中的Entry-----是无序的，不可重复的；使用Set储存所有的Entry
 *
 ***********************************************************************************************************************
 * HashMap底层实现原理：
 * jdk7.0为例：
 * HashMap hashMap1 = new HashMap();
 * 在实例化以后；底层创建了长度为16的一维数组 Entry[] table；
 * ...可能以及执行过一次或多次的put...
 * hashMap1.put(key1,value1);
 * 首先，调用key1所在类的hashCode()计算key1的哈希值；此哈希值经过某种算法计算以后，得到在Entry[]数组中的存放位置；
 * 如果在此位置上的数据为空，此时的key1-value1添加成功 ----情况一
 *                      如果此位置上的数据不为空（意味着此位置上存在一个或多个数据【以链表的形式存在】），----同位置上多个的数据以链表的形式储存
 *                      比较key1和已存在的一个或多个数据的哈希值；
 *                      如果key1的哈希值与已存在的一个或多个数据的哈希值都不相同，此时的key1-value1添加成功 ----情况二
 *                      如果key1的哈希值与已存在的某一个数据(key2,value2)的哈希值相同，继续比较；调用key1所在类的equals(key2),
 *                                                                                   如果equals(key2)结果返回false；
 *                                                                                   此时key1-value1添加成功 ----情况三
 *                                                                                   如果equals(key2)结果返回true；
 *                                                                                   使用value1替换value2。
 * 在不断添加的过程中会涉及到扩容的问题：
 * 默认的扩容方式--要超出 “临界值” 时候--扩容为原来容量的2倍；并将原有的数据copy过来。
 * ---------------------------------------------------------------------------------------------------------------------
 * jdk8.0相较于jdk7.0在底层实现方面的新特性
 * 1.在实例化时：HashMap hashMap1 = new HashMap();底层并没有直接创建长度为16的数组;
 * 2.底层数组为Node[]数组 而非jdk7.0中的Entry[];
 * 3.首次调用put()方法时底层创建长度为16的Node[]数组;
 * 4.jdk8.0中的底层结构为:数组+链表+红黑树;     jdk7.0中的底层结果为:数组+链表;
 *      当数组的某一个索引位置上以链表的形式储存的数据个数 > 8 同时当前数组的长度 > 64 ;
 *      此时此索引位置上的所有数据转成 红黑树 的储存结构;(遍历快速,方便查找)
 1.首次调用put()方法时底层创建长度为16的Node[]数组;
 		··newThr = 12//临界值
		 newCap = 16//初始容量
		loadFactor = 0.75//加载因子
		根据加载因子计算出一个容量的“临界值”
		要超出临界值时就进行扩容（扩容为原来的两倍）··达到临界值12（16*0.75）时扩容为32··达到临界值24（32*0.75）时扩容为64··以此类推
 //hashMap1.put(key1,value1);
 2.调用key1的hashCode()计算出key1的hash值；
 （return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);）--通过计算以后得到key1的hash即在Node[]数组中的存放位置
 		先判断计算以后得到key1的hash即在Node[]数组中的存放位置是否为null 若为null则直接添加成功
 		若不为null表明这个索引位置原本已有元素
 			将与此索引位置上的第一个元素进行hash值比较
 			if (p.hash == hash &&// p为这个索引位置的第一个元素
                ((k = p.key) == key || (key != null && key.equals(k))))
                若匹配上则表明是重复的元素··（无法添加）添加失败
            若与第一个元素不匹配则继续进行后续判断    
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
                判断该索引位置上的元素是否形成了红黑树结构··如果是则按照红黑树的方式进行判断
            若该索引位置上的元素未形成红黑树结构则继续进行后续判断
            else {
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            使用for循环与链表上除第一个外（由于第一次以及与第一个进行比较了··不匹配才走到此处所以不必再进行匹配）的每一个元素进行比较
            比较hash值与equals()
            	若不匹配则（进行添加）添加成功
            	若匹配则表明是重复的元素··（无法添加）添加失败
           	在把元素添加至链表后;会立即进行判断该链表是否达到8个结点
           		若达到第8个结点同时Node[]数组的长度已经到达64··则将该索引位置上的链表转化成红黑树结构
           		若达到第8个结点但Node[]数组的长度未到达64··则采用数组扩容机制先对Node[]数组进行扩容
           	
 
 
 ************************************************************************************************************************
 * LinkedHashMap底层实现原理(了解)
 * 底层使用 Entry[] 数组+双向链表
 * 在遍历map元素时，可以按照添加的顺序遍历由于在原有的HashMap底层结构基础上，添加了记录添加元素的先后顺序的操作--对于频繁的遍历操作，效率高于HashMap
 * 在源码中:
 *  static class Entry<K,V> extends HashMap.Node<K,V> {
 *         Entry<K,V> before, after;---------------------------//此操作记录添加元素的先后顺序！！
 *         Entry(int hash, K key, V value, Node<K,V> next) {
 *             super(hash, key, value, next);
 *         }
 *     }
 /*
        HashMap底层原理debug
        底层使用Node数组+链表+红黑树
     */
    @Test
    public void hashMapTest(){
//        HashMap hashMap = new HashMap();
//        hashMap.put("Eddie",99);
//        hashMap.put("Irving",95);
//        hashMap.put("James",98);
//        hashMap.put("Curry",94);
//        hashMap.put("Durant",93);
//        hashMap.put("Eddie1",99);
//        System.out.println(hashMap);

        Node[] table = new Node[16];//Map的底层是使用Node[]数组  +链表+红黑树
        Node node = new Node();
        node.item = "Eddie";
        Node node1 = new Node();
        node1.item = "Irving";
        table[0] = node;
        node.next = node1;
        Node node2 = new Node();
        node2.item = "James";
        table[1] = node2;
        /*
        //debug结构
this = {MapPracticeTest@1136} 
table = {MapPracticeTest$Node[16]@1137} 
 0 = {MapPracticeTest$Node@1208} 
  item = "Eddie"
  next = {MapPracticeTest$Node@1210} 
   item = "Irving"
   next = null
 1 = {MapPracticeTest$Node@1212} 
  item = "James"
  next = null
node = {MapPracticeTest$Node@1208} 
node1 = {MapPracticeTest$Node@1210} 
node2 = {MapPracticeTest$Node@1212} 
table[1] = {MapPracticeTest$Node@1212}
		*/
 */
```

![image-20220830155633976](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220830155633976.png)

### Java Collection FrameWork 

![image-20220928235935285](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220928235935285.png)

![image-20220929105145405](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220929105145405.png)

### Collection--Interface

![image-20230201122010792](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230201122010792.png)

```java
/**
 * Collection接口
 *  Collection接口：单列数据，定义了存取一组对象的方法的集合
 *  向Collection接口的实现类的对象中添加自定义的数据obj时 要求obj所在类对equals方法进行重写
 *
 *  * List：元素有序、可重复的集合
 *  * Set：元素无序、不可重复的集合--存放在Set容器中的对象，
 *                               对应的类一定要重写equals()和hashCode(Object obj)方法，以实现对象相等规则
 *
 *      ------List★
 *              ------ArrayList★---------------主要实现类 线程不安全的 效率较高 底层使用Object[]存储
 *
 *                          ------LinkedList----对于频繁的插入和删除操作-效率较高 底层使用双向链表存储
 *
 *              ------Vector--------------------古老实现类 -- since：jdk1.0 线程安全效率较低 底层使用Object[]存储
 *
 *      ------Set
 *              ------HashSet☆------------------主要实现类 线程不安全 可以存储null值 底层使用数组+链表储存
 *
 *                          ------LinkedHashSet--根据元素的 hashCode 值来决定元素的存储位置，但它同时使用双向链表维护元素的次序，
 *                                               这使得元素看起来是以插入顺序保存的 不允许集合元素重复
 *                                               LinkedHashSet插入性能略低于 HashSet，但在迭代访问 Set 里的全部元素时有很好的性能
 *
 *              ------TreeSet--------------------TreeSet 是 SortedSet 接口的实现类，TreeSet 可以确保集合元素处于排序状态。
 *                                               TreeSet底层使用红黑树结构存储数据
 *                                               TreeSet 两种排序方法：自然排序和定制排序。默认情况下，TreeSet 采用自然排序
 *                                                TreeSet和后面要讲的TreeMap采用红黑树的存储结构
 *                                                特点：有序，查询速度比List快
 *
 */
/*
        ArrayList底层源码debug
        底层使用Object[]数组
        开发中已知所需用集合容量的可以使用有参的构造器（指定ArrayList容量）进行实例化ArrayList--可以避免系统重复的扩容以及扩容检测--提高效率
     */
    @Test
    public void arrayListTest(){
        ArrayList arrayList = new ArrayList();//JDK8之后在new对象时并没有提供基本空间--
        // 在进行第一个add元素时候 初始化空间长度为10 在1-10的过程中每次都会判断是否要超出10 未超出直接添加元素在相应的位置上
        // 一旦进行第11个元素的add时候就在原有的空间长度上进行1.5倍的扩容
        //超过原本1.5倍扩容后的长度继续进行1.5倍扩容
        arrayList.add(1);
        arrayList.add(2);
        arrayList.add(3);
        arrayList.add(4);
        arrayList.add(5);
        arrayList.add(6);
        arrayList.add(7);
        arrayList.add(8);
        arrayList.add(9);
        arrayList.add(10);

        arrayList.add(11);
        arrayList.add(12);
        arrayList.add(13);
        arrayList.add(14);
        arrayList.add(15);
        arrayList.add(16);

    }
	/*
        Vector底层源码debug
        底层使用Object[]数组
     */
    @Test
    public void vectorTest(){
        Vector vector = new Vector();////在new对象时提供基本空间--初始化空间长度为10
        //public Vector() {
        //  this(initialCapacity 10);
        //}
        // 在1-10的过程中每次都会判断是否要超出10 未超出直接添加元素在相应的位置上
        // 一旦进行第11个元素的add时候就在原有的空间长度上进行2.0倍的扩容
        //超过原本2.0倍扩容后的长度继续进行2.0倍扩容
        vector.add(1);
        vector.add(2);
        vector.add(3);
        vector.add(4);
        vector.add(5);
        vector.add(6);
        vector.add(7);
        vector.add(8);
        vector.add(9);
        vector.add(10);
        //minGrowth = 1
        //prefGrowth = 10
        //prefLength = 20
        vector.add(11);
        vector.add(12);
        vector.add(13);
        vector.add(14);
        vector.add(15);
        vector.add(16);
        vector.add(17);
        vector.add(18);
        vector.add(19);
        vector.add(20);

        //minGrowth = 1
        //prefGrowth = 20
        //prefLength = 40
        vector.add(21);
    }

	/*
        linkedList底层源码debug
        底层使用Node数组+链表结构
     */
    @Test
    public void linkedListTest(){
        LinkedList linkedList = new LinkedList();
        //new对象的时候调用空参构造器
        //public LinkedList() {
        //}
        //调用add()方法添加元素
//        public boolean add(E e) {
//            linkLast(e);
//            return true;
//        }
        linkedList.add(1);//添加第一个元素时first和last都指向唯一的元素 元素的prev和next都为null 给第一个元素的位置赋值1
        //last = {LinkedList$Node@1156}
            // prev = null
            // next = null
            // item = {Integer@1155} 1
        //first = {LinkedList$Node@1156}
            // prev = null
            // next = null
            // item = {Integer@1155} 1
        linkedList.add(2);//添加第二个元素时 last指向后添加的第二个元素 新添加的元素的prev为前一个元素（即早于他添加的元素）next为null 给第二个元素赋值2
                                        //first指向第一个元素 第一个元素的prev为null next为新添加的元素
//        this = {LinkedList$Node@1148}
//        prev = {LinkedList$Node@1145}
//        item = {Integer@1144} 1
//        next = null
//        prev = null
//        element = {Integer@1142} 2
//        value = 2
//        next = null
//        this.next = null
//        this.prev = null

        //e = {Integer@1142} 2
        // value = 2
        //l = {LinkedList$Node@1145}
        // item = {Integer@1144} 1
        // next = {LinkedList$Node@1148}
        // prev = null
        //newNode = {LinkedList$Node@1148}
        // item = {Integer@1142} 2
        // next = null
        // prev = {LinkedList$Node@1145}
        //modCount = 1
        //l.next = {LinkedList$Node@1148}
        // item = {Integer@1142} 2
        // next = null
        // prev = {LinkedList$Node@1145}
        //size = 1

        linkedList.remove(0);//删除指定元素 指定删除的元素的prev&next为null 元素的值置空为null （等待GC处理）同时若指定删除元素有前后元素那么前后元素的prev&next置空并且相互指向
//        this = {LinkedList@1139}  size = 2
//        x = {LinkedList$Node@1149}
//        item = {Integer@1142} 1
//        next = null
//        prev = null
//        element = {Integer@1142} 1
//        value = 1
//        next = {LinkedList$Node@1150}
//        item = {Integer@1143} 2
//        next = null
//        prev = null
//        prev = null
//        modCount = 2
//        size = 2
//        x.item = {Integer@1142} 1
//        value = 1
//        x.next = null


    }
```

![image-20220815110218330](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110218330.png)

![image-20220815110231823](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110231823.png)

![image-20220815110245265](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110245265.png)

```java
public class CollectionTestTest {


    /**
     * 1、添加
     *  add(Object obj)
     *  addAll(Collection coll)
     * 向Collection接口的实现类的对象中添加自定义的数据obj时 要求obj所在类对equals方法进行重写
     */
    @org.junit.Test
    public void methodTest1() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
    }

    /**
     * 2、获取有效元素的个数
     *  int size()
     */
    @org.junit.Test
    public void methodTest2() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        // int size()
        System.out.println(coll.size());
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
        // int size()
        System.out.println(coll1.size());
    }

    /**
     * 3、清空集合
     *  void clear()
     */
    @org.junit.Test
    public void methodTest3() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        //void clear()
        coll.clear();
        System.out.println(coll);

    }


    /**
     * 4、是否是空集合
     *  boolean isEmpty()
     */
    @org.junit.Test
    public void methodTest4() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        //boolean isEmpty()
        System.out.println(coll.isEmpty());
        System.out.println(coll);
        //void clear()
        coll.clear();
        //boolean isEmpty()
        System.out.println(coll.isEmpty());
        System.out.println(coll);

    }


    /**
     * 5、是否包含某个元素
     *  boolean contains(Object obj)：是通过元素的equals方法来判断是否
     * 是同一个对象
     *  boolean containsAll(Collection c)：也是调用元素的equals方法来比
     * 较的。拿两个集合的元素挨个比较。
     * 自定义的类 调contains（）方法 要重写equals方法
     */
    @org.junit.Test
    public void methodTest5() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = Arrays.asList("詹姆斯", "欧文", "库里", "杜兰特");
        //addAll(Collection coll)
//        coll1.addAll(coll);
//        coll1.add("詹姆斯");
//        coll1.add("欧文");
//        coll1.add("库里");
//        coll1.add("杜兰特");
        System.out.println(coll1);

        System.out.println("---------------------------------------------");
        //boolean contains(Object obj)：是通过元素的equals方法来判断是否
        boolean contains = coll1.contains("欧文");
        System.out.println(contains);

        //boolean containsAll(Collection c)：也是调用元素的equals方法来比较的。拿两个集合的元素挨个比较。
        boolean containsAll = coll1.containsAll(coll);
        System.out.println(containsAll);
    }


    /**
     * 6、删除
     *  boolean remove(Object obj) ：通过元素的equals方法判断是否是
     * 要删除的那个元素。只会删除找到的第一个元素
     *  boolean removeAll(Collection coll)：取当前集合的差集
     */
    @org.junit.Test
    public void methodTest6() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);

        System.out.println("---------------------------------------------");
        //boolean remove(Object obj) ：通过元素的equals方法判断是否是要删除的那个元素。只会删除找到的第一个元素
        boolean remove = coll.remove('Z');
        System.out.println(remove);
        System.out.println(coll);
        //boolean removeAll(Collection coll)：取当前集合的差集
        boolean removeAll = coll1.removeAll(coll);
        System.out.println(removeAll);
        System.out.println(coll1);

    }


    /**
     * 7、取两个集合的交集
     *  boolean retainAll(Collection c)：把交集的结果存在当前集合中，不
     * 影响c
     */
    @org.junit.Test
    public void methodTest7() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);

        System.out.println("---------------------------------------------");
        //boolean retainAll(Collection c)：把交集的结果存在当前集合中，不影响c
        System.out.println(coll1.retainAll(coll));
        System.out.println(coll1);
    }

    /**
     * 8、集合是否相等
     *  boolean equals(Object obj)
     */
    @org.junit.Test
    public void methodTest8() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
        Collection coll2 = Arrays.asList("Eddie", "zjh", 123, 'Z');
        System.out.println(coll2);

        System.out.println("---------------------------------------------");
        //boolean equals(Object obj)
        System.out.println(coll1.equals(coll));//false

        System.out.println(coll.equals(coll2));//true
    }


    /**
     * 10、获取集合对象的哈希值
     *  hashCode()
     */
    @org.junit.Test
    public void methodTest9() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
        Collection coll2 = Arrays.asList("Eddie", "zjh", 123, 'Z');
        System.out.println(coll2);

        System.out.println("---------------------------------------------");
        //hashCode()
        System.out.println(coll.hashCode());
        System.out.println(coll1.hashCode());
        System.out.println(coll2.hashCode());
    }

    /**
     * 9、转成对象数组
     *  Object[] toArray()
     */
    @org.junit.Test
    public void methodTest10() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
        Collection coll2 = Arrays.asList("Eddie", "zjh", 123, 'Z');
        System.out.println(coll2);

        System.out.println("---------------------------------------------");
        //Object[] toArray() ArrayList集合 转成Object[]数组
        Object[] objects = coll.toArray();
        Object[] objects1 = coll1.toArray();
        Object[] objects2 = coll2.toArray();
        System.out.println(objects);
        System.out.println(objects1);
        System.out.println(objects2);

        System.out.println(Arrays.toString(objects));
        System.out.println(Arrays.toString(objects1));
        System.out.println(Arrays.toString(objects2));

        System.out.println("---------------------------------------------");
        //ArrayList asList() Object[]数组 转成ArrayList集合
        List<Object> objectList = Arrays.asList(objects);
        List<Object> objectList1 = Arrays.asList(objects1);
        List<Object> objectList2 = Arrays.asList(objects2);
        System.out.println(objectList);
        System.out.println(objectList1);
        System.out.println(objectList2);

        System.out.println("---------------------------------------------");
        //ArrayList asList() Object[]数组 转成ArrayList集合
        List<Integer> integers = Arrays.asList(new Integer[]{1, 2});//在new基本数据类型数组的时候注意写成包装类
        System.out.println(integers);
        System.out.println(integers.size());
        //
        List<Integer> integers1 = Arrays.asList(1, 2);//或者直接填写基本数据类型
        System.out.println(integers1);
        System.out.println(integers1.size());
    }
```

**Iterator**--**Interface**

Iterator迭代器接口--使用 Iterator 接口遍历集合元素

![image-20220815110419837](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110419837.png)

![image-20220815110431778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110431778.png)

![image-20220815110441172](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110441172.png)

![image-20220815110452631](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110452631.png)

```java
     *  iterator()：返回迭代器对象，用于集合遍历
     * <p>
     * iterator.hasNext()//判断下面还有没有元素
     * iterator.next()//指针下移 然后将下移到的位置的元素值返回
     */
    @org.junit.Test
    public void methodTest11() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        System.out.println(coll);
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");
        System.out.println(coll1);
        Collection coll2 = Arrays.asList("Eddie", "zjh", 123, 'Z');
        System.out.println(coll2);

        System.out.println("---------------------------------------------");
        //iterator()：返回迭代器对象，用于集合遍历
        Iterator iterator = coll1.iterator();
        System.out.println(iterator);
        //
        while (iterator.hasNext()) {//iterator.hasNext()//判断下面还有没有元素
            System.out.println(iterator.next());//iterator.next()//指针下移 然后将下移到的位置的元素值返回
        }

        System.out.println("---------------------------------------------");
        //remove()
        Iterator iterator1 = coll1.iterator();
        while(iterator1.hasNext()){
            Object next = iterator1.next();
            if(next.equals(123)){
                iterator1.remove();
            }

        }
        iterator1 = coll1.iterator();
        while(iterator1.hasNext()){
            System.out.println(iterator1.next());

        }


    }

}
```



foreach **循环遍历集合元素**

** Java 5.0 提供了 foreach 循环迭代访问 Collection和数组。**

** 遍历操作不需获取Collection或数组的长度，无需使用索引访问元素。** 

** 遍历集合的底层调用Iterator完成操作。** 

** foreach还可以用来遍历数组。**

![image-20220815110615742](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815110615742.png)

```java
 /**
     * 集合
     * 使用Foreach循环
     */
    @Test
    public void test1() {
        Collection coll = new ArrayList();//new接口的实现类 动态数组ArraysList
        //add(Object obj)
        coll.add("Eddie");
        coll.add("zjh");
        coll.add(123);
        coll.add('Z');
        Collection coll1 = new ArrayList();
        //addAll(Collection coll)
        coll1.addAll(coll);
        coll1.add("詹姆斯");
        coll1.add("欧文");
        coll1.add("库里");
        coll1.add("杜兰特");

        //使用Foreach
        for (Object o :
                coll) {
            System.out.println(o);
        }
        System.out.println("-------------------------------------");
        for (Object o1 :
                coll1) {
            System.out.println(o1);
        }


    }


    /**
     * 数组
     * 使用Foreach循环
     */
    @Test
    public void test2() {
        int[] arrayInt1 = new int[]{1, 2, 33, 5, 22, 5, 2, 555, 6, 656, 5, 23, 321};
        for (int array1 :
                arrayInt1) {
            System.out.println(array1);
        }
    }


    @Test
    public void test3() {
        String[] str = new String[5];
        for (String myStr : str) {//foreach循环给到一个新的数组
            myStr = "atguigu";
            System.out.println(myStr);
            //atguigu
            //atguigu
            //atguigu
            //atguigu
            //atguigu
        }
        for (int i = 0; i < str.length; i++) {
            System.out.println(str[i]);
            //null
            //null
            //null
            //null
            //null
        }
    }
}
```



#### List--Interface

**有序性**

**可重复性**

![image-20220815111234930](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111234930.png)

![image-20220815111245993](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111245993.png)

![image-20220815111257820](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111257820.png)

![image-20220815111307944](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111307944.png)

![image-20220815111324841](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111324841.png)

![image-20220815111334801](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111334801.png)

![image-20220815111346527](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111346527.png)

```java
/**
 * Collection接口：单列数据，定义了存取一组对象的方法的集合
 * List：元素有序、可重复的集合
 * Set：元素无序、不可重复的集合
 */

/**
 * List接口
 添加的对象，所在的类要重写equals方法
 * JDK API中List接口的实现类常用的有：
 * ArrayList、★主要实现类 线程不安全的 效率较高 底层使用Object[]存储
 * LinkedList  对于频繁的插入和删除操作-效率较高 底层使用双向链表存储
 * 和Vector。 古老实现类 -- since：jdk1.0 线程安全效率较低 底层使用Object[]存储
 * 三个类都实现了List接口 存储数据的特点相同 ：有序的 可重复的
 *
 */
/**
     * List中的常用方法
     * List除了从Collection集合继承的方法外，List 集合里添加了一些根据索引来
     * 操作集合元素的方法
     * ArrayList、★主要实现类 线程不安全的 效率较高 底层使用Object[]存储
     * 常用方法 着重放在：
     * 增 :void add(Object obj)
     * 删 :Object remove(int index):移除指定index位置的元素，并返回此元素
     * 删 :boolean remove(Object obj):移除指定元素，并返回此元素
     * 改 :Object set(int index, Object ele):设置指定index位置的元素为ele
     * 查 :Object get(int index):获取指定index位置的元素
     * 插 :void add(int index, Object ele):在index位置插入ele元素
     * 长度 :int size()
     * 遍历 :1.iterator迭代器
     *      2.foreach(增强for循环)
     *      3.普通的循环
     *		4.遍历public void forEach(Consumer<? super E> action)--default方法
     */
    @Test
    public void test1() {
        ArrayList arrayList = new ArrayList();
        arrayList.add(123);
        arrayList.add("zjh");
        arrayList.add('Z');
        arrayList.add("张锦豪");
        arrayList.add(123);
        System.out.println(arrayList);

        System.out.println("-------------------------------------------------");
        //void add(int index, Object ele):在index位置插入ele元素
        arrayList.add(1,"欧文");
        System.out.println(arrayList);

        System.out.println("-------------------------------------------------");
        //boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
        List<? extends Serializable> serializables1 = Arrays.asList(123, "zjh", "张锦豪", 'O');
        arrayList.addAll(serializables1);
        System.out.println(arrayList);
        System.out.println(arrayList.size());

        System.out.println("-------------------------------------------------");
        //Object get(int index):获取指定index位置的元素
        System.out.println(arrayList.get(0));


        System.out.println("-------------------------------------------------");
        //int indexOf(Object obj):返回obj在集合中首次出现的位置
        System.out.println("在集合中首次出现的位置: " + arrayList.indexOf("zjh"));

        System.out.println("-------------------------------------------------");
        //int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
        System.out.println("在当前集合中末次出现的位置: " + arrayList.lastIndexOf("zjh"));

        System.out.println("-------------------------------------------------");
        //Object remove(int index):移除指定index位置的元素，并返回此元素
        System.out.println(arrayList.remove(0));
        System.out.println(arrayList);

        System.out.println("-------------------------------------------------");
        //boolean remove(Object obj):移除指定元素，并返回此元素
        arrayList.remove("zjh");
        System.out.println(arrayList);

        System.out.println("-------------------------------------------------");
        //Object set(int index, Object ele):设置指定index位置的元素为ele
        arrayList.set(0,"凯里欧文");
        System.out.println(arrayList);

        System.out.println("-------------------------------------------------");
        //List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合 前闭后开[ fromIndex , toIndex )
        System.out.println(arrayList.subList(2, 5));

        System.out.println("-------------------------------------------------");
        //遍历--Iterator迭代器方式
        Iterator iterator = arrayList.iterator();
        while(iterator.hasNext()){
            System.out.println(iterator.next());
        }


        System.out.println("-------------------------------------------------");
        //遍历--foreach(增强for循环)方式
        for (Object obj1 :
                arrayList) {
            System.out.println(obj1);
        }
        System.out.println("-------------------------------------------------");
        //遍历--普通for循环方式
        for (int i = 0; i < arrayList.size(); i++) {
            System.out.println(arrayList.get(i));

        }
        
        System.out.println("-------------------------------------------------");
        //遍历public void forEach(Consumer<? super E> action)--default方法
        arrayList.forEach(System.out::println);

    }
}
```

#### Set--Interface

**无序性：不等于随机性 存储的数据在底层数组中并非按照数组的索引顺序添加的 是根据数据的hash值决定的没有索引**

**不可重复性：保证添加的元素按照equals方法判断时，不能返回true 即：相同的元素只能添加一个**

![image-20220815111625697](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111625697.png)

![image-20220815111657746](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111657746.png)

![image-20220815111745516](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111745516.png)

![image-20220815111755545](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111755545.png)

![image-20220815111810144](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111810144.png)

![image-20220815111823365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111823365.png)

![image-20220815111841460](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111841460.png)

![image-20220815111916758](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111916758.png)

![image-20220815111955382](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815111955382.png)

![image-20220815112008977](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815112008977.png)

![image-20220815112024281](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815112024281.png)

![image-20220815112053707](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815112053707.png)

![image-20220815112103243](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220815112103243.png)

### Map--Interface

![image-20230201122028698](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230201122028698.png)

```java
/**
 * Map接口
 * 双列数据，保存具有映射关系“key-value对”的集合
 *  Map与Collection并列存在。用于保存具有映射关系的数据:key-value
 *  Map 中的 key 和 value 都可以是任何引用类型的数据
 *  Map 中的 key 用Set来存放，不允许重复，即同一个 Map 对象所对应的类，须重写hashCode()和equals()方法
 *  常用String类作为Map的“键”
 *  key 和 value 之间存在单向一对一关系，即通过指定的 key 总能找到唯一的、确定的 value
 *  Map接口的常用实现类：HashMap、TreeMap、LinkedHashMap和Properties。其中，HashMap是 Map 接口使用频率最高的实现类
 *
 * Map接口---------------------------------双列数据，保存具有映射关系“key-value对”的集合
 *
 *      ----HashMap★---------------------线程不安全效率较高 可存储null的key/value 主要实现类
 *                                        底层储存（jdk7.0及之前）--数组+链表；
 *                                               （jdk8.0开始 ）--数组+链表+红黑树；
 *
 *              ----LinkedHashMap☆-------在遍历map元素时，可以按照添加的顺序遍历
 *                                        由于在原有的HashMap底层结构基础上，添加了一对 "指针" 指向前一个和后一个
 *                                        对于频繁的遍历操作，效率高于HashMap
 *
 *      ----TreeMap☆---------------------按照添加的key-value对进行排序，实现排序遍历 考虑的是key的自然排序/定制排序
 *                                        底层使用的红黑树的储存结构
 *
 *      ----Hashtable 古老的实现类----------线程安全效率较低 不可存储null的key/value
 *
 *              ----Properties☆----------常用来处理配置文件；key&value都是String类型
 *
 * Map结构的理解
 * Map中的key：------是无序的，不可重复的；使用Set储存所有的key------------->key所在的类要求要@override--equals（）& hashCode（）【 HashMap为例 】
 * Map中的value：----是无序的，可重复的；使用Collection储存所有的value----->value所在的类要求要@override--hashCode（）
 * 一个键值对（key-value）构成了一个Entry对象；key&value相当于Entry的两个属性
 * map中的Entry-----是无序的，不可重复的；使用Set储存所有的Entry
 *
 ***********************************************************************************************************************
 * HashMap底层实现原理：
 * jdk7.0为例：
 * HashMap hashMap1 = new HashMap();
 * 在实例化以后；底层创建了长度为16的一维数组 Entry[] table；
 * ...可能以及执行过一次或多次的put...
 * hashMap1.put(key1,value1);
 * 首先，调用key1所在类的hashCode()计算key1的哈希值；此哈希值经过某种算法计算以后，得到在Entry[]数组中的存放位置；
 * 如果在此位置上的数据为空，此时的key1-value1添加成功 ----情况一
 *                      如果此位置上的数据不为空（意味着此位置上存在一个或多个数据【以链表的形式存在】），----同位置上多个的数据以链表的形式储存
 *                      比较key1和已存在的一个或多个数据的哈希值；
 *                      如果key1的哈希值与已存在的一个或多个数据的哈希值都不相同，此时的key1-value1添加成功 ----情况二
 *                      如果key1的哈希值与已存在的某一个数据(key2,value2)的哈希值相同，继续比较；调用key1所在类的equals(key2),
 *                                                                                   如果equals(key2)结果返回false；
 *                                                                                   此时key1-value1添加成功 ----情况三
 *                                                                                   如果equals(key2)结果返回true；
 *                                                                                   使用value1替换value2。
 * 在不断添加的过程中会涉及到扩容的问题：
 * 默认的扩容方式--要超出 “临界值” 时候--扩容为原来容量的2倍；并将原有的数据copy过来。
 * ---------------------------------------------------------------------------------------------------------------------
 * jdk8.0相较于jdk7.0在底层实现方面的新特性
 * 1.在实例化时：HashMap hashMap1 = new HashMap();底层并没有直接创建长度为16的数组;
 * 2.底层数组为Node[]数组 而非jdk7.0中的Entry[];
 * 3.首次调用put()方法时底层创建长度为16的Node[]数组;
 * 4.jdk8.0中的底层结构为:数组+链表+红黑树;     jdk7.0中的底层结果为:数组+链表;
 *      当数组的某一个索引位置上以链表的形式储存的数据个数 > 8 同时当前数组的长度 > 64 ;
 *      此时此索引位置上的所有数据转成 红黑树 的储存结构;(遍历快速,方便查找)
 1.首次调用put()方法时底层创建长度为16的Node[]数组;
 		··newThr = 12//临界值
		 newCap = 16//初始容量
		loadFactor = 0.75//加载因子
		根据加载因子计算出一个容量的“临界值”
		要超出临界值时就进行扩容（扩容为原来的两倍）··达到临界值12（16*0.75）时扩容为32··达到临界值24（32*0.75）时扩容为64··以此类推
 //hashMap1.put(key1,value1);
 2.调用key1的hashCode()计算出key1的hash值；
 （return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);）--通过计算以后得到key1的hash即在Node[]数组中的存放位置
 		先判断计算以后得到key1的hash即在Node[]数组中的存放位置是否为null 若为null则直接添加成功
 		若不为null表明这个索引位置原本已有元素
 			将与此索引位置上的第一个元素进行hash值比较
 			if (p.hash == hash &&// p为这个索引位置的第一个元素
                ((k = p.key) == key || (key != null && key.equals(k))))
                若匹配上则表明是重复的元素··（无法添加）添加失败
            若与第一个元素不匹配则继续进行后续判断    
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
                判断该索引位置上的元素是否形成了红黑树结构··如果是则按照红黑树的方式进行判断
            若该索引位置上的元素未形成红黑树结构则继续进行后续判断
            else {
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            使用for循环与链表上除第一个外（由于第一次以及与第一个进行比较了··不匹配才走到此处所以不必再进行匹配）的每一个元素进行比较
            比较hash值与equals()
            	若不匹配则（进行添加）添加成功
            	若匹配则表明是重复的元素··（无法添加）添加失败
           	在把元素添加至链表后;会立即进行判断该链表是否达到8个结点
           		若达到第8个结点同时Node[]数组的长度已经到达64··则将该索引位置上的链表转化成红黑树结构
           		若达到第8个结点但Node[]数组的长度未到达64··则采用数组扩容机制先对Node[]数组进行扩容
           	
 
 
 ************************************************************************************************************************
 * LinkedHashMap底层实现原理(了解)
 * 底层使用 Entry[] 数组+双向链表
 * 在遍历map元素时，可以按照添加的顺序遍历由于在原有的HashMap底层结构基础上，添加了记录添加元素的先后顺序的操作--对于频繁的遍历操作，效率高于HashMap
 * 在源码中:
 *  static class Entry<K,V> extends HashMap.Node<K,V> {
 *         Entry<K,V> before, after;---------------------------//此操作记录添加元素的先后顺序！！
 *         Entry(int hash, K key, V value, Node<K,V> next) {
 *             super(hash, key, value, next);
 *         }
 *     }
 /*
        HashMap底层原理debug
        底层使用Node数组+链表+红黑树
     */
    @Test
    public void hashMapTest(){
//        HashMap hashMap = new HashMap();
//        hashMap.put("Eddie",99);
//        hashMap.put("Irving",95);
//        hashMap.put("James",98);
//        hashMap.put("Curry",94);
//        hashMap.put("Durant",93);
//        hashMap.put("Eddie1",99);
//        System.out.println(hashMap);

        Node[] table = new Node[16];//Map的底层是使用Node[]数组  +链表+红黑树
        Node node = new Node();
        node.item = "Eddie";
        Node node1 = new Node();
        node1.item = "Irving";
        table[0] = node;
        node.next = node1;
        Node node2 = new Node();
        node2.item = "James";
        table[1] = node2;
        /*
        //debug结构
this = {MapPracticeTest@1136} 
table = {MapPracticeTest$Node[16]@1137} 
 0 = {MapPracticeTest$Node@1208} 
  item = "Eddie"
  next = {MapPracticeTest$Node@1210} 
   item = "Irving"
   next = null
 1 = {MapPracticeTest$Node@1212} 
  item = "James"
  next = null
node = {MapPracticeTest$Node@1208} 
node1 = {MapPracticeTest$Node@1210} 
node2 = {MapPracticeTest$Node@1212} 
table[1] = {MapPracticeTest$Node@1212}
		*/
 */
```



## 泛型

### 泛型背后的类型擦除

![image-20221029103653388](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029103653388.png)

**泛型的类型擦除原则**是：

- 消除类型参数声明，即删除`<>`及其包围的部分。
- 根据类型参数的上下界推断并替换所有的类型参数为原生态类型：如果类型参数是无限制通配符或没有上下界限定则替换为Object，如果存在上下界限定则根据子类替换原则取类型参数的最左边限定类型（即父类）。
- 为了保证类型安全，必要时插入强制类型转换代码。
- 自动产生“桥接方法”以保证擦除类型后的代码仍然具有泛型的“多态性”。

#### **如何进行擦除的**

- 擦除类定义中的类型参数 - 无限制类型擦除

当类定义中的类型参数没有任何限制时，在类型擦除中直接被替换为Object，即形如`<T>`和`<?>`的类型参数都被替换为Object。

![image-20221029103829158](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029103829158.png)

- 擦除类定义中的类型参数 - 有限制类型擦除

当类定义中的类型参数存在限制（上下界）时，在类型擦除中替换为类型参数的上界或者下界，比如形如`<T extends Number>`和`<? extends Number>`的类型参数被替换为`Number`，`<? super Number>`被替换为Object。

![image-20221029103853389](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029103853389.png)

- 擦除方法定义中的类型参数

擦除方法定义中的类型参数原则和擦除类定义中的类型参数是一样的，这里仅以擦除方法定义中的有限制类型参数为例。

![image-20221029103932005](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221029103932005.png)

### 泛型的使用

Java **泛型（generics）**是 **JDK 5** 中引入的一个新特性, 泛型提供了**编译时类型安全检测机制**，该机制允许程序员**在编译时检测到非法的类型**

**泛型的本质是参数化类型**，即给类型指定一个参数，然后在使用时再指定此参数具体的值，那样这个类型就可以在使用时决定了。这种参数类型可以用在类、接口和方法中，分别被称为**泛型类**、**泛型接口**、**泛型方法**
**要用泛型 就一路用到底**

```java
1. 只看尖括号里边的！！明确点和范围两个概念
2. 如果尖括号里的是一个类，那么尖括号里的就是一个点，比如List<A>,List<B>,List<Object>
3. 如果尖括号里面带有问号，那么代表一个范围，<? extends A> 代表小于等于A的范围，<? super A>代表大于等于A的范围，<?>代表全部范围
4. 尖括号里的所有点之间互相赋值都是错，除非是俩相同的点
5. 尖括号小范围赋值给大范围，对，大范围赋值给小范围，错。如果某点包含在某个范围里，那么可以赋值，否则，不能赋值
6. List<?>和List 是相等的，都代表最大范围
7.补充：List既是点也是范围，当表示范围时，表示最大范围
```

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923002431378.png)

![image-20220923002224458](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923002224458.png)

### 泛型通配符

![image-20220923002548374](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220923002548374.png)

// 1：表示类型参数可以是任何类型

public class Apple<?>{} 

// 2：表示类型参数必须是A或者是A的子类

public class Apple<T extends A>{} 

// 3: 表示类型参数必须是A或者是A的超类型

public class Apple<T supers A>{}

**常见泛型参数名称有如下：**

E：Element (在集合中使用，因为集合中存放的是元素)
T：Type（Java 类）
K：Key（键）
V：Value（值）
N：Number（数值类型）
？：表示不确定的java类型

## IO|NIO★



## 类库（Java常用类）

### String字符串相关类

![image-20220811084041686](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084041686.png)

**三者的效率**--StringBuilder > StingBuffer > String

**转换：**

 String-->StringBuilder|StingBuffer **调构造器** StringBuilder（）|StingBuffer（）

StringBuilder|StingBuffer -->String **调构造器** String （）|StringBuilder&StingBuffer的toString方法



在没有多线程同时处理共享数据的情况（考虑线程安全问题）优先使用高效率的StringBuilder；

```java
 @org.junit.Test
    public void stringTest4() {
        String str = null;
        StringBuffer sb = new StringBuffer();
        sb.append(str);
     
        System.out.println(sb.length());//4
        System.out.println(sb);//"null"
        StringBuffer sb1 = new StringBuffer(str);//java.lang.NullPointerException: Cannot invoke "String.length()" because "str" is null//异常 
        System.out.println(sb1);  
    }
//
		String str = null;
        StringBuffer sb = new StringBuffer();
        sb.append(str);
        System.out.println(sb.length());//4
        System.out.println(sb);//null
以下是原因 通过查看 append() 源码
// public AbstractStringBuilder append(String str) {
        if (str == null) {
            return appendNull();
        }
     			//private AbstractStringBuilder appendNull() {
        ensureCapacityInternal(count + 4);
        int count = this.count;
        byte[] val = this.value;
        if (isLatin1()) {
            val[count++] = 'n';
            val[count++] = 'u';
            val[count++] = 'l';
            val[count++] = 'l';
        } else {
            count = StringUTF16.putCharsAt(val, count, 'n', 'u', 'l', 'l');
        }
        this.count = count;
        return this;
    }
```



### String

![image-20220920083049782](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220920083049782.png)

**JDK9以后底层使用byte[ ]数组储存**

![image-20220927162237933](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220927162237933.png)

![image-20220811084110171](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084110171.png)

![image-20220811084151529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084151529.png)

![image-20220811084213376](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084213376.png)

![image-20220811084245491](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084245491.png)

![image-20220811084258090](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084258090.png)

![image-20220811084317007](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084317007.png)

![image-20220811084359529](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084359529.png)

![image-20220811084412636](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084412636.png)

![image-20220811084928769](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084928769.png)

![image-20220811084944708](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811084944708.png)

#### String常用方法

```java
 int length()：返回字符串的长度： return value.length
 char charAt(int index)： 返回某索引处的字符return value[index]
 boolean isEmpty()：判断是否是空字符串：return value.length == 0
 String toLowerCase()：使用默认语言环境，将 String 中的所有字符转换为小写
 String toUpperCase()：使用默认语言环境，将 String 中的所有字符转换为大写
 String trim()：返回字符串的副本，忽略前导空白和尾部空白
 boolean equals(Object obj)：比较字符串的内容是否相同
 boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大
小写
 String concat(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+”
 int compareTo(String anotherString)：比较两个字符串的大小
 String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从
beginIndex开始截取到最后的一个子字符串。
 String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字
符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。
    
    
 boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束
 boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始
 boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的
子字符串是否以指定前缀开始

 boolean contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列
时，返回 true
 int indexOf(String str)：返回指定子字符串在此字符串中第一次出现处的索引
 int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出
现处的索引，从指定的索引开始
 int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引
 int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后
一次出现处的索引，从指定的索引开始反向搜索
注：indexOf和lastIndexOf方法如果未找到都是返回-1
    
 String replace(char oldChar, char newChar)：返回一个新的字符串，它是
通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。
 String replace(CharSequence target, CharSequence replacement)：使
用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。
 String replaceAll(String regex, String replacement) ： 使 用 给 定 的
replacement 替换此字符串所有匹配给定的正则表达式的子字符串。
 String replaceFirst(String regex, String replacement) ： 使 用 给 定 的
replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
    
 boolean matches(String regex)：告知此字符串是否匹配给定的正则表达式。
    
 String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。
 String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此
字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。
    
//Instance：    
String str = "12hello34world5java7891mysql456";
//把字符串中的数字替换成,，如果结果中开头和结尾有，的话去掉
String string = str.replaceAll("\\d+", ",").replaceAll("^,|,$", "");
System.out.println(string);

String str = "12345";
//判断str字符串中是否全部有数字组成，即有1-n个数字组成
boolean matches = str.matches("\\d+");
System.out.println(matches);
String tel = "0571-4534289";
//判断这是否是一个杭州的固定电话
boolean result = tel.matches("0571-\\d{7,8}");
System.out.println(result);



String str = "hello|world|java";
String[] strs = str.split("\\|");
for (int i = 0; i < strs.length; i++) {
System.out.println(strs[i]);
}
System.out.println();
String str2 = "hello.world.java";
String[] strs2 = str2.split("\\.");
for (int i = 0; i < strs2.length; i++) {
System.out.println(strs2[i]);
}


```

#### String与基本数据类型转换

![image-20220811085626213](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811085626213.png)

#### String与字符数组转换

![image-20220811085636355](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811085636355.png)

#### String与字节数组转换

![image-20220811085648859](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811085648859.png)

##### 编码：

##### 字符串-->字节码（二进制数据）

##### 解码：

##### 字节码（二进制数据）-->字符串

**编码与解码过程中  编码集与解码集  要保持一致 否侧会出现乱码**

#### String重写equals

String重写了Object的equals方法

![image-20220926082602443](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926082602443.png)

![image-20220926082754438](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926082754438.png)

![image-20220926083415468](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926083415468.png)

#### String的intern（）方法

**intern()方法：**
public String intern()返回字符串对象的规范化表示形式。
一个初始时为空的字符串池，它由类 String 私有地维护。

**当调用 intern 方法时**，如果池已经包含一个等于此 String 对象的字符串（该对象由 equals(Object) 方法确定），则返回池中的字符串。否则，将此 String 对象添加到池中，并且返回此 String 对象的引用。
它遵循对于任何两个字符串 s 和 t，当且仅当 s.equals(t) 为 true 时，s.intern() == t.intern() 才为 true

![image-20220926084300676](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220926084300676.png)

### StringBuffer

![image-20220811091032492](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811091032492.png)

![image-20220811091050760](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811091050760.png)

```java
//StringBuffer & StringBuilder略同
@Test
    public void test1(){
        StringBuilder stringBuilder = new StringBuilder();
        /*在new对象时就初始化capacity为16
        	public StringBuilder() {
    			super(capacity:16);
			}
		*/
        System.out.println(stringBuilder.length());//0
        //public int length() {//length返回的是count值（已存在的char数量）
        //    return count;
        //}
        stringBuilder.append("张锦豪1");
        stringBuilder.append("张锦豪2");
        //public StringBuilder append(String str) {
        //   super.append(str);
        //   return this;
        //}
        stringBuilder.append("张锦豪3");
        stringBuilder.append("张锦豪4");//至此已占用16个char容量 即:miniCapacity为16 oldCapacity为16
        stringBuilder.append("张锦豪5");//此处即将占用20个char容量 即:miniCapacity为20 oldCapacity为16
        //——>进行扩容newCapacity
        if (minimumCapacity - oldCapacity > 0) {//此处为ture进去条件体进行newCapacity扩容
            value = Arrays.copyOf(value,
                    newCapacity(minimumCapacity) << coder);
        }
        //newCapacity方法如下
        /*
        private int newCapacity(int minCapacity) {
        int oldLength = value.length;
        int newLength = minCapacity << coder;
        int growth = newLength - oldLength;
        int length = ArraysSupport.newLength(oldLength, growth, oldLength + (2 << coder));
        if (length == Integer.MAX_VALUE) {
            throw new OutOfMemoryError("Required length exceeds implementation limit");
        }
        return length >> coder;
    	}
    	*/

```

#### StringBuffer类的常用方法

```java
StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接
StringBuffer delete(int start,int end)：删除指定位置的内容
StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str
StringBuffer insert(int offset, xxx)：在指定位置插入xxx
StringBuffer reverse() ：把当前字符序列逆转

```

![image-20220811091224226](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811091224226.png)

```java
public int indexOf(String str)
public String substring(int start,int end)
public int length()
public char charAt(int n )
public void setCharAt(int n ,char ch)

```



### StringBulider

![image-20220811091302717](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220811091302717.png)

### String StringBuffer StringBuilder三者比较

String、StringBuffer和StringBuilder的异同？
相同点：**底层都是通过char数组实现的**
不同点：

**String对象一旦创建**，其**值是不能修改的**，如果要修改，会重新开辟内存空间来存储修改之后的对象；而StringBuffer和StringBuilder对象的值是可以被修改的；
**StringBuffer**几乎所有的方法都使用**synchronized实现了同步**，**线程比较安全**，在多线程系统中可以保证数据同步，但是**效率比较低**；而**StringBuilder** 没有实现同步，**线程不安全**，在多线程系统中不能使用 StringBuilder，但是**效率比较高**。
如果我们在实际开发过程中需要对字符串进行**频繁的修改**，**不要使用String**，否则会造成**内存空间的浪费**；当需要考虑线程安全的场景下使用 StringBuffer，如果不需要考虑线程安全，追求效率的场景下可以使用 StringBuilder。

### 日期API

#### JDK8之前日期API

![image-20220814174158359](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814174158359.png)

##### System类中的 currentTimeMillis（）

![image-20220814175407816](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814175407816.png)

```java
/**
 * System中提供的public static native long currentTimeMillis()方法用来
 * 返回当前时间与1970.01.01.00.00.00之间以毫秒为单位的时间差
 * 时间戳是指格林威治时间1970年01月01日00时00分00秒(北京时间1970年01月01
 * 日08时00分00秒)起至现在的总秒数
 * 计算世界时间的主要标准有
 * UTC(Coordinated Universal Time)
 * GMT(Greenwich Mean Time)
 * CST(Central Standard Time)
 */
public class SystemCurrentTimeMillisTest {
    public static void main(String[] args) {
        //System中提供的public static native long currentTimeMillis()
        long currentTimeMillis = System.currentTimeMillis();
        //返回当前时间与1970.01.01.00.00.00之间以毫秒为单位的时间差
        System.out.println(currentTimeMillis);//1660470429596
    }
}
```

##### java.util.Date & java.sql.Date

![image-20220814175420839](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814175420839.png)

```java
/**
 * 2. java.util.Date类
 * 表示特定的瞬间，精确到毫秒
 * 构造器：
 *  Date()：使用无参构造器创建的对象可以获取本地当前时间。
 *  Date(long date)
 * 常用方法
 *  getTime():时间戳 ：返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象
 * 表示的毫秒数。
 *  toString():把此 Date 对象转换为以下形式的 String： dow mon dd
 * hh:mm:ss zzz yyyy 其中： dow 是一周中的某一天 (Sun, Mon, Tue,
 * Wed, Thu, Fri, Sat)，zzz是时间标准。
 */
public class DateClassTest {
    //创建java.util.Date类的对象
    public static void main(String[] args) {
        //构造器： Date():使用无参构造器创建的对象可以获取本地当前时间。
        Date date1 = new Date();
        System.out.println(date1);//Sun Aug 14 17:55:58 CST 2022
        //常用方法：getTime():返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数。
        long date1Time = date1.getTime();
        System.out.println(date1Time);//1660471077048
        //常用方法：toString():把此 Date 对象转换为以下形式的 String： dow mon dd
        String toString = date1.toString();
        System.out.println(toString);//Sun Aug 14 18:00:04 CST 2022

        System.out.println("--------------------------------------------------------------");
        //构造器：Date(long date):创建一个创建指定毫秒数的Date对象
        Date date2 = new Date(1660471077048L);
        System.out.println(date2);//Sun Aug 14 17:57:57 CST 2022
        long date2Time = date2.getTime();
        System.out.println(date2Time);//1660471077048
        
        //        创建java.sql.Date类的对象
        java.sql.Date date3 = new java.sql.Date(1660471077048L);
        System.out.println(date3);//2022-08-14
        
        
        //如何将java.util.Date类的对象-->java.sql.Date类的对象
        Date date5 = new Date();//new一个java.sql.Date类的对象
        long date5Time = date5.getTime();//调用getTime()方法获得java.sql.Date类的对象的时间戳
        java.sql.Date date6 = new java.sql.Date(date5Time);//将java.sql.Date类的对象的时间戳放入构造器中
        //--java.sql.Date(java.sql.Date类的对象的时间戳)
        
    }
}
```

##### SimpleDateFormat

![image-20220814181620667](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814181620667.png)

```java
/**
 * java.text.SimpleDateFormat类
 *  Date类的API不易于国际化，大部分被废弃了，java.text.SimpleDateFormat类是一个不与语言环境有关的方式来格式化和解析日期的具体类。
 *  它允许进行格式化：日期文本、解析：文本日期
 *  格式化：
 *  SimpleDateFormat() ：默认的模式和语言环境创建对象
 *  public SimpleDateFormat(String pattern)：该构造方法可以用参数pattern指定的格式创建一个对象，该对象调用：
 *  public String format(Date date)：方法格式化时间对象date
 *  解析：
 *  public Date parse(String source)：从给定字符串的开始解析文本，以生成一个日期。
 */
public class SimpleDateFormatClassTest {
    public static void main(String[] args) {
//--------------------------SimpleDateFormat() ：默认的模式和语言环境创建对象------------------------------------------------
        Date date1 = new Date();//new一个java.util.Date类的对象空参构造器返回当前时间
        System.out.println(date1);//Sun Aug 14 18:19:31 CST 2022\
        //进行格式化（format）日期-->字符串
        SimpleDateFormat simpleDateFormat1 = new SimpleDateFormat();//SimpleDateFormat() ：默认的模式和语言环境创建对象
        String format = simpleDateFormat1.format(date1);
        System.out.println(format);//2022/8/14 下午6:21
        //进行解析（parse）格式化的逆过程 字符串-->日期
        String strDate1 = "2022/8/14 下午6:21";
        try {
            Date parseDate = simpleDateFormat1.parse(strDate1);
            System.out.println(parseDate);//Sun Aug 14 18:21:00 CST 2022
        } catch (ParseException e) {
            System.out.println(e.getMessage());//Unparseable date: "2022/8/14 午6:2"
        }
        System.out.println("*******************************************************************************************");
        //-----------public SimpleDateFormat(String pattern)：该构造方法可以用参数pattern指定的格式创建一个对象-----------------
        SimpleDateFormat simpleDateFormat2 = new SimpleDateFormat("yyyy年MM月dd日 EEE HH:mm:ss");
        //进行格式化（format）日期-->字符串
        String format1 = simpleDateFormat2.format(date1);
        System.out.println(format1);//2022年08月14日 周日 18:39:15
        //进行解析（parse）格式化的逆过程 字符串-->日期
        try {
            Date parseDate2 = simpleDateFormat2.parse(format1);
            System.out.println(parseDate2);//Sun Aug 14 18:41:34 CST 2022
        } catch (ParseException e) {
            System.out.println(e.getMessage());//Unparseable date:
        }
        
        System.out.println("*******************************************************************************************");
        //字符串String strDate3 = "2020-09-08";转换成java.sql.Date
        String strDate3 = "2020-09-08";
        //simpleDateFormat3.parse(strDate3)解析成Date（java.util.Date）
        SimpleDateFormat simpleDateFormat3 = new SimpleDateFormat("yyyy-MM-dd");
            Date parseDate3 = simpleDateFormat3.parse(strDate3);
            parseDate3.getTime();

            //java.util.Date转成java.sql.Date
        java.sql.Date sqlDate1 = new java.sql.Date(parseDate3.getTime());
        System.out.println(sqlDate1);
    }

    }
```

##### Calendar

```java
/**
 * java.util.Calendar(日历)类
 *  Calendar是一个抽象基类，主用用于完成日期字段之间相互操作的功能
 *  获取Calendar实例的方法
 *  使用Calendar.getInstance()方法
 *  调用它的子类GregorianCalendar的构造器
 *  一个Calendar的实例是系统时间的抽象表示，
 * 通过get(int field)方法来取得想
 * 要的时间信息。比如YEAR、MONTH、DAY_OF_WEEK、HOUR_OF_DAY 、
 * MINUTE、SECOND
 *  public void set(int field,int value)
 *  public void add(int field,int amount)
 *  public final Date getTime() Calendar类-->Date类
 *  public final void setTime(Date date)
 *  注意:
 *  获取月份时：一月是0，二月是1，以此类推，12月是11
 *  获取星期时：周日是1，周二是2 ， 。。。。周六是7
 */
public class CalendarClassTest {
    public static void main(String[] args) {
        //获取Calendar实例的方法
//        Calendar.getInstance()方法
        Calendar calendar1 = Calendar.getInstance();
        //通过get(int field)方法来取得想要的时间信息。比如YEAR、MONTH、DAY_OF_WEEK、HOUR_OF_DAY 、MINUTE、SECOND
        int dayOfYear = calendar1.get(DAY_OF_YEAR);
        System.out.println("现在是2022年的第: " + dayOfYear + " 天");//现在是2022年的第: 226 天
        int weekOfYear = calendar1.get(WEEK_OF_YEAR);
        System.out.println("现在是2022年的第: " + weekOfYear + " 周");//现在是2022年的第: 34 周
        //从一个Calendar对象中获取Date对象
        Date calendar1Time = calendar1.getTime();
//        calendar1.setTime设置calendar1时间
        calendar1.setTime(calendar1Time);
        System.out.println(calendar1Time.toString());
//        public void set(int field,int value)
        calendar1.set(calendar1.DAY_OF_YEAR,8);
        System.out.println("8天后的日期为:" + calendar1.getTime());

    }
}
```

#### JDK8之后日期API

![image-20220814204715984](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814204715984.png)

![image-20220814204743462](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814204743462.png)

![image-20220814204808962](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814204808962.png)
![image-20220814204828263](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814204828263.png)
![image-20220814205539533](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814205539533.png)
![image-20220814211701689](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814211701689.png)
![image-20220814211712198](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814211712198.png)

##### Instant★

类似于java.util.Date

##### LocalDate

##### LocalTime

##### LocalDateTime ★

☆高频使用 类似于Calendar

```java
/**
 * java.time – 包含值对象的基础包★
 *
 * 本地日期（LocalDate）、
 * 本地时间（LocalTime）、
 * 本地日期时间（LocalDateTime）、☆高频使用 类似于Calendar
 *
 * method--------------------------------------------------------------describe
 * now() / * now(ZoneId zone) -----------------------------------------静态方法，根据当前时间创建对象/指定时区的对象
 * of() ---------------------------------------------------------------静态方法，根据指定日期/时间创建对象
 * getDayOfMonth()/getDayOfYear() -------------------------------------获得月份天数(1-31) /获得年份天数(1-366)
 * getDayOfWeek() -----------------------------------------------------获得星期几(返回一个 DayOfWeek 枚举值)
 * getMonth() ---------------------------------------------------------获得月份, 返回一个 Month 枚举值
 * getMonthValue() / getYear() ----------------------------------------获得月份(1-12) /获得年份
 * getHour()/getMinute()/getSecond() ----------------------------------获得当前对象对应的小时、分钟、秒
 * withDayOfMonth()/withDayOfYear()/withMonth()/withYear() ------------将月份天数、年份天数、月份、年份修改为指定的值并返回新的对象
 * plusDays(), plusWeeks(),plusMonths(), plusYears(),plusHours() ------向当前对象添加几天、几周、几个月、几年、几小时
 * minusMonths() / minusWeeks()/minusDays()/minusYears()/minusHours() -从当前对象减去几月、几周、几天、几年、几小时
 *
 *
 * 用 ISO-8601日历系统 它们的实例是不可变的对象
 * ISO-8601日历系统是国际标准化组织制定的现代公民的日期和时间的表示法，也就是公历
 *
 * 时区（ZonedDateTime）
 * 和持续时间（Duration）的类
 * java.time.chrono – 提供对不同的日历系统的访问
 * java.time.format – 格式化和解析时间和日期★
 * java.time.temporal – 包括底层框架和扩展特性★
 * java.time.zone – 包含时区支持的类
 *
 * 瞬时：Instant 类似于java.util.Date
 * Instant：时间线上的一个瞬时点。 这可能被用来记录应用程序中的事件时间戳。
 * method---------------------------------describe
 * now() ---------------------------------静态方法，返回默认UTC时区的Instant类的对象
 * ofEpochMilli(long epochMilli) ---------静态方法，返回在1970-01-01 00:00:00基础上加上指定毫秒数之后的Instant类的对象
 * atOffset(ZoneOffset offset) -----------结合即时的偏移来创建一个 OffsetDateTime
 * toEpochMilli() 返回1970-01-01 00:00:00--到当前时间的毫秒数，即为时间戳
 *
 * 它只是简单的表示自1970年1月1日0时0分0秒（UTC）开始的秒数
 * 在Java中从1970年开始以毫秒为单位
 * 时间戳是指格林威治时间1970年01月01日00时00分00秒(北京时间1970年01月01日08时00分00秒)起至现在的总秒数
 */
public class NewDateClass {
    public static void main(String[] args) {
//        瞬时：Instant 类似于java.util.Date
        Instant now = Instant.now();
        System.out.println(now);//2022-08-14T13:10:40.912953900Z
        long epochSecond = now.getEpochSecond();//返回1970-01-01 00:00:00--到当前时间的毫秒数，即为时间戳
        System.out.println(epochSecond);//1660482698

//        本地日期时间（LocalDateTime）、☆高频使用 类似于Calendar
        LocalDateTime localDateTime = LocalDateTime.now();//静态方法，根据当前时间创建对象/指定时区的对象
        System.out.println(localDateTime);//2022-08-14T21:10:40.928954800
        DayOfWeek dayOfWeek = localDateTime.getDayOfWeek();
        System.out.println(dayOfWeek);//SUNDAY
        Month localDateTimeMonth = localDateTime.getMonth();
        System.out.println(localDateTimeMonth);//AUGUST
        LocalDateTime localDateTime1 = LocalDateTime.of(2000, 12, 07, 00, 00, 00, 00);//静态方法，根据指定日期/时间创建对象
        System.out.println(localDateTime1);//2000-12-07T00:00
    }
}
```

##### DateTimeFormatter

格式化与解析日期或时间

![image-20220814212836355](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814212836355.png)

![image-20220814212847903](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814212847903.png)

```java
/**
 * java.time.format.DateTimeFormatter 类：
 * 该类提供了三种格式化方法：
 *  预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME
 *  本地化相关的格式。如：ofLocalizedDateTime(FormatStyle.LONG)
 *  自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
 *
 * method------------------------describe
 * ofPattern(String pattern) ----静态方法 ， 返 回 一 个 指 定 字 符 串 格 式 的DateTimeFormatter
 * format(TemporalAccessor t) ---格式化一个日期、时间，返回字符串
 * parse(CharSequence text) -----将指定格式的字符序列解析为一个日期、时间
 */
public class DateTimeFormatterClass {
    public static void main(String[] args) {
//        自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
        DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
        String format = dateTimeFormatter.format(LocalDateTime.now());//format(TemporalAccessor t) ---格式化一个日期、时间，返回字符串
        System.out.println(format);//2022-08-14 09:26:19
        TemporalAccessor parse = dateTimeFormatter.parse(format);
        System.out.println(parse);
    }
}
```



### 新老日期API对比转换

![image-20220814212951284](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814212951284.png)

### Java比较器

在Java中经常会涉及到对象数组的排序问题，那么就涉及到对象之间 的比较问题。

Java中的对象；正常情况下只能进行：==  或  != 的比较；不能使用 > 或 <的

但在开发场景中 我们需要对 多个对象 进行排序，表明要比较对象的大小

**实现的方法是使用 Comparable 接口& Comparator 接口**

**Comparable 接口& Comparator 接口 的对比**

Comparable--接口的方式一旦确定，保证Comparable 接口实现类的对象在任何位置都可以比较大小

Comparator --接口属于临时性的比较



#### 自然排序：java.lang.Comparable

![image-20220814213711756](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814213711756.png)

![image-20220814213819991](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814213819991.png)

```java
/**
 * 自然排序：java.lang.Comparable
 * Comparable 的典型实现：(默认都是从小到大排列的)
 * String：按照字符串中字符的Unicode值进行比较
 * Character：按照字符的Unicode值来进行比较
 * 数值类型对应的包装类以及BigInteger、BigDecimal：按照它们对应的数值
 * 大小进行比较
 * Boolean：true 对应的包装类实例大于 false 对应的包装类实例
 * Date、Time等：后面的日期时间比前面的日期时间大
 *
 *  实现 Comparable 的类必须实现 compareTo(Object obj) 方法，两个对象即通过 compareTo(Object obj) 方法的返回值来比较大小。
 * 如果当前对象this大于形参对象obj，则返回正整数，如果当前对象this小于形参对象obj，则返回负整数，如果当前对象this等于形参对象obj，则返回零
 */
public class ComparableTest {


    public static void main(String[] args) {
        Person1[] person1s = new Person1[6];//创建Person1[]数组存储Person1类对象 动态初始化数组
        //给数组赋值
        person1s[0] = new Person1("张锦豪",21,"Java");
        person1s[1] = new Person1("詹姆斯",37,"Basketball");
        person1s[2] = new Person1("欧文",32,"Basketball");
        person1s[3] = new Person1("库里",34,"Basketball");
        person1s[4] = new Person1("杜兰特",34,"Basketball");
        person1s[5] = new Person1("哈登",34,"Basketball");
//        Arrays.sort(Object obj)方法给Person1[]数组进行排序
        Arrays.sort(person1s);
        //输出数组
        System.out.println(Arrays.toString(person1s));

        //foreach遍历数组
        for (Person1 person2 :
                person1s) {
            System.out.println(person2);
        }
        System.out.println("-------------------------------------------------------------------------------------");
    }

}
/**
 * 自定义类实现Comparable接口 可进行排序比大小
 * 1.implements Comparable接口
 * 2.@Override--Comparable接口中的compareTo(Object o)方法
 * 3.在compareTo(Object o)方法体中定义如何进行排序
 */
class Person1 implements Comparable {
    private String name;
    private int age;
    private String major;

    public Person1() {
    }

    public Person1(String name, int age, String major) {
        this.name = name;
        this.age = age;
        this.major = major;
    }

    //按照年龄比较Person1类的大小
    @Override
    public int compareTo(Object o) {
        if (o instanceof Person1) {
            Person1 otherPerson1 = (Person1) o;
            return Integer.compare(this.age,otherPerson1.age);//推荐方式
//            if (this.age > otherPerson1.age) {
//                return 1;
//            } else if (this.age < otherPerson1.age) {
//                return -1;
//            } else {
////                return 0;
//                return this.getMajor().compareTo(otherPerson1.getMajor());//
//            }
        }
        throw new RuntimeException("输入的数据类型不一致！！");
    }

    @Override
    public String toString() {
        return "Person1{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", major='" + major + '\'' +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getMajor() {
        return major;
    }

    public void setMajor(String major) {
        this.major = major;
    }
}
```



#### 定制排序：java.util.Comparator

![image-20220814213917232](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220814213917232.png)

```java
/**
 * 定制排序：java.util.Comparator
 *  当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，
 * 或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，
 * 那么可以考虑使用 Comparator 的对象来排序，强行对多个对象进行整体排序的比较
 *  重写compare(Object o1,Object o2)方法，比较o1和o2的大小：如果方法返
 * 回正整数，则表示o1大于o2；如果返回0，表示相等；返回负整数，表示
 * o1小于o2。
 *  可以将 Comparator 传递给 sort 方法（如 Collections.sort 或 Arrays.sort），
 * 从而允许在排序顺序上实现精确控制。
 *  还可以使用 Comparator 来控制某些数据结构（如有序 set或有序映射）的
 * 顺序，或者为那些没有自然顺序的对象 collection 提供排序。
 */

public class ComparatorTest {


    public static void main(String[] args) {
        Person2[] person2s = new Person2[6];//创建Person1[]数组存储Person1类对象 动态初始化数组
        //给数组赋值
        person2s[0] = new Person2("张锦豪", 21, "Java");
        person2s[1] = new Person2("詹姆斯", 37, "Basketball");
        person2s[2] = new Person2("欧文", 32, "Basketball");
        person2s[3] = new Person2("库里", 34, "Basketball");
        person2s[4] = new Person2("杜兰特", 34, "Basketball");
        person2s[5] = new Person2("哈登", 34, "Basketball");
//        定制排序：java.util.Comparator
        Arrays.sort(person2s, new Comparator<Person2>() {
            @Override
            public int compare(Person2 o1, Person2 o2) {
                if (o1 instanceof Person2 && o2 instanceof Person2) {
                    Person2 person1 = (Person2) o1;
                    Person2 person2 = (Person2) o2;
                    //按照年龄从大到小排序 年龄相同时按照name排序
                    if (person1.getAge() == person2.getAge()) {
                        return person1.getName().compareTo(person2.getName());
                    } else {
                        return -Integer.compare(person1.getAge(), person2.getAge());
                    }
                }
                throw new RuntimeException("输入的数据类型不一致！！");
            }

        });
        System.out.println(Arrays.toString(person2s));

        System.out.println("------------------------------------------------------");
        for (Person2 person2 :
                person2s) {
            System.out.println(person2);
//            Person1 {name='詹姆斯', age=37, major='Basketball'}
//            Person1{name='哈登', age=34, major='Basketball'}
//            Person1{name='库里', age=34, major='Basketball'}
//            Person1{name='杜兰特', age=34, major='Basketball'}
//            Person1{name='欧文', age=32, major='Basketball'}
//            Person1{name='张锦豪', age=21, major='Java'}
        }


    }

}
```

### System类

### Math类

### BigInteger与BigDecimal



## 多线程★

### 程序|进程|线程（线程简介）

> **现代操作系统调度的最小单元是线程**
>
> 
>
> In modern systems a process can actually consist of multiple execution units, called threads, each running in the context of the process and sharing the same code and global data.
>
> 在现代系统中，一个进程实际上可以由多个执行单元组成，称为线程，每个线程都在进程的上下文中运行，并共享相同的代码和全局数据。
>
> 
>
>
> Threads are an increasingly important programming model because of the requirement for concurrency in network servers, because it is easier to share data between multiple threads than between multiple processes, and because threads are typically more efficient than processes. Multi-threading is also one way to make programs run faster when multiple processors are available.
>
> 线程是一个越来越重要的编程模型，因为网络服务器对并发性的要求，因为在多个线程之间共享数据比在多个进程之间共享数据更容易，也因为线程通常比进程更有效率。多线程也是在有多个处理器的情况下使程序运行得更快的一种方法。

![image-20220810222017059](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222017059.png)

![image-20220810222034607](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222034607.png)

![image-20220810222053410](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222053410.png)

![image-20220810222120846](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222120846.png)

![image-20220810223656172](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223656172.png)

![image-20220810222136193](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222136193.png)

![image-20220810222145839](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810222145839.png)

### 线程的创建 ★

#### 继承Thread体系结构|实现Runnable接口

![image-20220810223237308](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223237308.png)

![image-20220810223405778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223405778.png)

![image-20220810223427429](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223427429.png)

![image-20220810223251427](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223251427.png)

![image-20220810223258993](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223258993.png)

![image-20220810223440551](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223440551.png)

![image-20220810223451982](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223451982.png)

![image-20220810223316090](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223316090.png)

![image-20220810223332134](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223332134.png)

##### 继承Thread体系结构

```java
/**
 * 多线程的创建
 * 方式一：继承于Thread类
 * ①：创建一个继承于Thread类的子类
 * ②：重写Thread类中的run方法-->此线程要执行的操作重写在run方法的方法体中
 * ③：创建继承于Thread类的子类的对象-->需要在主线程（main方法）中操作
 * ④：通过此对象 调用start（）方法-->①线程开始要执行 调用当前线程的 ②run（）
 */

class MyThread1 extends Thread {//①：创建一个继承于Thread类的子类

    @Override
    public void run() {//②：重写Thread类中的run方法
        for (int i = 0; i < 100; i++) {//遍历100内的所有偶数
            if (i % 2 == 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}

public class ThreadTest {
    public static void main(String[] args) {
        /**
         * 启动一个线程 --> 创建继承于Thread类的子类的对象 通过此对象 调用start（）方法
         */
        MyThread1 t1 = new MyThread1();//③：创建继承于Thread类的子类的对象
        t1.start();//④：通过此对象 调用start（）方法-->线程开始要执行 调用当前线程的 run（）

        /**
         * 再启动一个线程 --> 再创建一个继承于Thread类的子类的对象 通过此对象 调用start（）方法 tip:(一个线程对象只能调用一次start()方法启动)
         */
        MyThread1 t2 = new MyThread1();//再创建一个继承于Thread类的子类的对象
        t2.start();//通过此对象 调用start（）方法-->线程开始要执行 调用当前线程的 run（）

        //以下操作在主线程 main（）中执行
        for (int i = 0; i < 100; i++) {
            if (i % 2 != 0) {
                System.out.println(Thread.currentThread().getName() + ":" + i + "main()");
            }
        }
    }
}

//相当于主线程 main（）和 MyThread线程 同时在进行
```



##### 实现Runnable接口

```java
/**
 * @author EddieZhang
 * @create 2022-08-08 22:29

/**
 *创建三个卖票的窗口 三个同时进行的线程
 * 一共100张票
 * 使用实现Runnable接口的方式
 * 目前存在线程安全问题 待解决...
 */

/**
 * 使用实现Runnable接口的方式
 * ①：实现Runnable接口
 * ②：实现Runnable接口的abstract方法 run（）
 * ③：创建实现类的对象
 * ④：创建Thread对象 并将实现类的对象放入Thread的构造器中
 * ⑤：通过Thread对象调用start（）方法
 */

class WindowsTicket implements Runnable {//①：实现Runnable接口
    private int ticket2 = 100;

    @Override
    public void run() {//②：实现Runnable接口的abstract方法 run（）
        while (true) {
            if (ticket2 > 0) {
                System.out.println(Thread.currentThread().getName() + " " + "唱票：" + ticket2-- + " 张票");
            } else {
                break;
            }
        }
    }
}
public class WindowsTicketTest1 {
    public static void main(String[] args) {
        WindowsTicket windowsTicket1 = new WindowsTicket();//③：创建实现类的对象

        Thread thread1 = new Thread(windowsTicket1); //④：创建Thread对象 并将实现类的对象放入Thread的构造器中
        Thread thread2 = new Thread(windowsTicket1);
        Thread thread3 = new Thread(windowsTicket1);

        thread1.setName("一号窗口");//通过setName给线程命名
        thread2.setName("二号窗口");
        thread3.setName("三号窗口");
        
        thread1.start();//⑤：通过Thread对象调用start（）方法
        thread2.start();//⑤：通过Thread对象调用start（）方法
        thread3.start();//⑤：通过Thread对象调用start（）方法

    }
}
```



#### J D K 5.0后new--实现Callable接口|线程池

##### 实现Callable接口

![image-20220810225228097](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810225228097.png)

![image-20220810225251091](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810225251091.png)

```java
/**
 * JDK5.0 新增线程创建方式
 * 实现Callable接口
 * 1.实现Callable接口
 * 2.@override--Callable中的call（）方法 执行的操作声明在方法体中
 * 3.new一个实现了Callable接口的对象
 * 4.new一个FutureTask类的对象，将实现了Callable接口的对象放入构造器中
 * 5.new一个Thread类的对象，FutureTask类的对象放入构造器中 通过Thread类的对象调用start（）方法 启动线程
 * .需要查看返回值可使用FutureTask类的对象调用get（）方法 同时处理异常
 * 
 *  与使用Runnable相比， Callable功能更强大些
 *  相比run()方法，可以有返回值
 *  方法可以抛出异常
 *  支持泛型的返回值
 *  需要借助FutureTask类，比如获取返回结果
 *
 * Future接口
 *  可以对具体Runnable、Callable任务的执行结果进行取消、查询是否完成、获取结果等。
 *  FutrueTask是Futrue接口的唯一的实现类
 *  FutureTask 同时实现了Runnable, Future接口。它既可以作为
 * Runnable被线程执行，又可以作为Future得到Callable的返回值
 */
class CallableThread1 implements Callable {//实现Callable接口

    @Override
    public Object call() throws Exception {//@override--Callable中的call（）方法 执行的操作声明在方法体中
        int sum = 0;
        for (int i = 0;i < 100 ;i++){
            if (i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + " " + i);
                sum += i;
            }
        }
        return sum;//可以有返回值
    }
}

public class CallableThreadTest {
    public static void main(String[] args) {
        CallableThread1 callableThread1 = new CallableThread1();//new一个实现了Callable接口的对象
        FutureTask futureTask1 = new FutureTask(callableThread1);//new一个FutureTask类的对象，将实现了Callable接口的对象放入构造器中
        Thread thread1 = new Thread(futureTask1);//new一个Thread类的对象，FutureTask类的对象放入构造器中
        thread1.start();//通过Thread类的对象调用start（）方法 启动线程

        //需要查看返回值可使用FutureTask类的对象调用get（）方法 同时处理异常
        try {
            Object numberSum = futureTask1.get();
            System.out.println(Thread.currentThread().getName() + "  遍历100内所有的偶数和为: " + numberSum);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        } catch (ExecutionException e) {
            throw new RuntimeException(e);
        }
    }
}
//输出如下
//Thread-0 0
//......
//Thread-0 98
//main  遍历100内所有的偶数和为: 2450

//创建多个线程
//需要创建FutureTask对象将线程类的对象作为参数传入构造器中--再创建多个Thread类的对象将FutureTask对象作为参数传入构造器中
FutureTask futureTask1 = new FutureTask(myThread6);//创建多个线程--创建多个FutureTask对象将线程类的对象作为参数传入构造器中
        Thread thread1 = new Thread(futureTask1);//创建多个线程--创建多个Thread类的对象将FutureTask对象作为参数传入构造器中
        thread1.setName("线程二");
        thread1.start();
```

##### 线程池

![image-20220810225320431](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810225320431.png)

![image-20220810225333526](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810225333526.png)



### 线程的生命周期

![image-20220810223844585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223844585.png) 

是否释放锁：

join等待加入，释放

join()底层就是调用wait()方法的，wait()释放锁资源，故join也释放锁资源

wait释放。是obj方法，

对应的notify, yeild优先级，不释放，随时回来，

sleep不释放。

![image-20220914214325888](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214325888.png)

![image-20220810223854276](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223854276.png)

### 线程的状态

![image-20230204194751551](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230204194751551.png)

![image-20220914213946380](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914213946380.png)

![image-20220914214530929](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214530929.png)

**新建线程New**

![image-20220914214133250](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214133250.png)

**可运行Runnable**

![image-20220914214213176](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214213176.png)

**阻塞和等待状态以及计时等待Block&Waiting&Timed waiting**

![image-20220914214625183](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214625183.png)

![image-20220914214753965](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214753965.png)

**线程终止**

![image-20220914214820450](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914214820450.png)

### 线程的属性

#### 中断线程☆

![image-20220914215429443](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914215429443.png)

**interrupted（）方法**

当一个线程调用interrupt（）方法时，就会设置线程的中断状态。这是每个线程都有的boolean标致。每个线程都应该时不时检测这个标致。

**public boolean isInterrupted()**方法
测试线程是否已经中断。线程的中断状态 不受该方法的影响。 
线程中断被忽略，因为在中断时不处于活动状态的线程将由此返回 false 的方法反映出来。 
返回：
如果该线程已经中断，则返回 true；否则返回 false。

![image-20220914215627185](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914215627185.png)

如果线程被阻塞就无法检测中断状态。就要引入InterruptedException异常。

**当一个被sleep或wait调用阻塞的线程上调用interrupt方法时，阻塞调用（即sleep|wait调用）将被一个InterruptedException异常中断。**

**抛出异常是为了线程从阻塞状态醒过来，并在结束线程前让程序员有足够的时间来处理中断请求**

对于处于sleep，join等操作的线程，如果被调用interrupt()后，会抛出InterruptedException，然后线程的中断标志位会由true重置为false，因为线程为了处理异常已经重新处于就绪状态

（有些阻塞I/O流调用不能被中断）

**不可中断的操作**，包括进入synchronized段以及Lock.lock()，inputSteam.read()等，调用interrupt()对于这几个问题无效，因为它们都不抛出中断异常。如果拿不到资源，它们会无限期阻塞下去



#### 守护线程☆

**t.setDaemon(boolean isDaemon)方法**--true表示设置成守护线程 

标识该线程为守护线程或用户线程。这一方法必须在线程启动之前调用

#### 线程名

![image-20220914220845023](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914220845023.png)

#### 未捕获异常的处理器

![image-20220914220914585](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914220914585.png)

### 线程的优先级

![image-20220810223548232](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223548232.png)

![image-20220914220943261](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914220943261.png)

![image-20220810223800435](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223800435.png)

![image-20220810223828990](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223828990.png)

### 线程的同步 ★

![image-20220810223912756](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223912756.png)

![image-20220810223928463](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810223928463.png)

##### Synchronized（同步机制）

寻找monitor锁

　　　　这里先不甩结论，接下来我们一步一步搜寻monitor锁。

　　　　之前使用synchronized的时候知道，java中的每个对象都可以作为锁。

1. 1. 普通同步方法，锁是当前实例对象。
   2. 静态同步方法，锁是当前类的class对象。
   3. 同步代码块，锁是括号中的对象。

![image-20220810224117249](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224117249.png)

**第一种：同步代码块**
灵活

synchronized(线程共享对象){
	同步代码块;
}
**第二种：在实例方法上使用synchronized**
表示共享对象一定是 this 并且同步代码块是整个方法体。

**第三种：在静态方法上使用synchronized**
表示找 **类锁。类锁永远只有1把**。

就算创建了100个对象，那类锁也只有1把。

注意区分：

对象锁：1个对象1把锁，100个对象100把锁。
类锁：100个对象，也可能只是1把类锁

![image-20220810224131682](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224131682.png)

![image-20220810224236195](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224236195.png)

![image-20220810224541018](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224541018.png)

###### 同步代码块

```java
/**
 * @Description 线程安全的懒汉式单例设计模式
 * @Author EddieZhang
 * @Date 2022/8/10 11:30
 * @Since version-1.0
 */
class SecuritySingleDesignMode {
    //私有构造器
    private SecuritySingleDesignMode() {
    }

    //私有静态对象--懒汉式不new先
    private static SecuritySingleDesignMode securitySingleDesignMode;

    //公共静态方法
    public static SecuritySingleDesignMode getInstance() {
        if (securitySingleDesignMode == null) {//相当于在口处立个标识提高效率
            synchronized (SecuritySingleDesignMode.class) {//同步代码块
                if (securitySingleDesignMode == null) {
                    securitySingleDesignMode = new SecuritySingleDesignMode();
                }
            }
        }
        return securitySingleDesignMode;
    }
}
```

###### 同步方法

```java
//创建线程方式：implements于Runnable接口  解决线程安全问题的方法：synchronized（）--》同步机制：同步代码块/同步方法

/**
 implements于Runnable接口
 *创建实现于Runnable的实现类
 * 重写Runnable中的抽象方法run（）
 * 创建实现类的对象
 * 创建Thread类的对象并将实现类放进构造器中
 * 通过Thread对象调用start（）方法
 */
class AccountThread implements Runnable {//创建实现于Runnable的实现类
    private double balance = 0;

    public synchronized void deposit(double amount) {//同步方法
        balance += amount;
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
        System.out.println(Thread.currentThread().getName() + ":进行存钱操作 余额为：" + balance + "$");
    }

    @Override
    public void run() {//重写Runnable中的抽象方法run（） 方法体中写要进行的操作
        for (int i = 0; i < 3; i++) {
            deposit(1000);
        }
    }
}

public class ThreadSecurityTest {
    public static void main(String[] args) {
        AccountThread accountThread = new AccountThread();//创建实现类的对象
        Thread thread = new Thread(accountThread);//创建Thread类的对象并将实现类放进构造器中
        Thread thread1 = new Thread(accountThread);//创建Thread类的对象并将实现类放进构造器中
        thread.setName("张锦豪");
        thread1.setName("张锦豪的对象");
        thread.start();//通过Thread对象调用start（）方法
        thread1.start();//通过Thread对象调用start（）方法
    }
}
```

##### lock（锁）

![image-20220810224622750](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224622750.png)

![image-20220810224633694](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224633694.png)

##### Synchronized & lock对比

![image-20220810224729606](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224729606.png)

**监视器概念monitor**

![image-20220914223634787](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914223634787.png)

**volatile字段**

在访问volatile变量时**不会执行加锁操作**，因此也就**不会使执行线程阻塞**，因此volatile变量是一种**比sychronized关键字更轻量级的同步机制**

**当一个变量定义为 volatile 之后，将具备两种特性：**

1.保证此变量对所有的线程的可见性，这里的“可见性”，如本文开头所述，当一个线程修改了这个变量的值，volatile 保证了新值能立即同步到主内存，以及每次使用前立即从主内存刷新。但普通变量做不到这点，普通变量的值在线程间传递均需要通过主内存来完成。

2.禁止指令重排序优化。有volatile修饰的变量，赋值后多执行了一个“load addl $0x0, (%esp)”操作，这个操作相当于一个**内存屏障**（指令重排序时不能把后面的指令重排序到内存屏障之前的位置），只有一个CPU访问内存时，并不需要内存屏障；（什么是指令重排序：是指CPU采用了允许将多条指令不按程序规定的顺序分开发送给各相应电路单元处理）

**volatile 性能：**

volatile 的读性能消耗与普通变量几乎相同，但是写操作稍慢，因为它需要在本地代码中插入许多内存屏障指令来保证处理器不发生乱序执行

![image-20220914223658782](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914223658782.png)

**final变量**

![image-20220914224746645](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220914224746645.png)

### 线程的通信

#### wait() | notify() | notifyAll()

![image-20220810224754057](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224754057.png)

![image-20220810224800486](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224800486.png)

![image-20220810224810028](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810224810028.png)

![image-20220810225415522](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220810225415522.png)

```java
/**
 * @author EddieZhang
 * @create 2022-08-09 20:30
 */

/**
 * 例 题
 * 使用两个线程打印 1-100。线程1, 线程2 交替打印(涉及到Thread通信)
 */
//创建线程
class ThreadCommunicate implements Runnable {//实现Runnable接口类
    private int number = 1;

    @Override
    public void run() {//重写Runnable接口中的abstract方法run（）方法体中写要进行的操作
        while (true) {
            synchronized (this) {
                this.notify();
                if (number <= 100) {
                    System.out.println(Thread.currentThread().getName() + " , " + number + "  *");
                    number++;
                } else {
                    break;
                }
                    try {
                        this.wait();
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
            }
        }
    }
}

public class ThreadCommunicationTest {
    //创建实现类的对象
    public static void main(String[] args) {
        ThreadCommunicate threadCommunicate = new ThreadCommunicate();
        //创建Thread类的对象 将实现类的对象放进构造器中
        Thread thread = new Thread(threadCommunicate);
        Thread thread1 = new Thread(threadCommunicate);
//        通过Thread对象调用setName（）方法 给线程命名
        thread.setName("线程一");
        thread1.setName("线程二");
        //通过Thread对象调用start（）方法 启动线程 调动当前线程的run（）方法
        thread.start();
        thread1.start();

    }
}
```

**sleep() 和 wait() 的区别**

sleep() 和 wait() 的区别就是 调用**sleep方法的线程不会释放对象锁**，而调用**wait() 方法会释放对象锁**

wait和notify方法**不是线程对象的方法**，是普通java对象都有的方法。**object的方法**

**wait方法和notify方法建立在 `线程同步` 的基础之上**。**必须使用在synchronize中**

wait方法作用：o.wait() 让正在o对象上活动的线程t进入等待状态，并且**释放掉t线程之前占有的o对象的锁**

notify方法作用：o.notify() 让正在o对象上等待的线程唤醒，**只是通知，不会释放o对象上之前占有的锁**

## 异常

https://cdn.discordapp.com/attachments/277819356795109378/1050375308295012424/Java_Exception_Handling_Cheat_Sheet.png

```
                     ┌───────────┐
                     │  Object   │
                     └───────────┘
                           ▲
                           │
                     ┌───────────┐
                     │ Throwable │
                     └───────────┘
                           ▲
                 ┌─────────┴─────────┐
                 │                   │
           ┌───────────┐       ┌───────────┐
           │   Error   │       │ Exception │
           └───────────┘       └───────────┘
                 ▲                   ▲
         ┌───────┘              ┌────┴──────────┐
         │                      │               │
┌─────────────────┐    ┌─────────────────┐┌───────────┐
│OutOfMemoryError │... │RuntimeException ││IOException│...
└─────────────────┘    └─────────────────┘└───────────┘
                                ▲
                    ┌───────────┴─────────────┐
                    │                         │
         ┌─────────────────────┐ ┌─────────────────────────┐
         │NullPointerException │ │IllegalArgumentException │...
         └─────────────────────┘ └─────────────────────────┘
```

> **Error（错误）**表示运行应用程序中较严重问题。**大多数错误与代码编写者执行的操作无关**，**程序对此一般无能为力** ，而表示代码运行时 JVM（Java 虚拟机）出现的问题。例如，当 JVM 不再有继续执行操作所需的内存资源时，将出现 **OutOfMemoryError**。
>
> - `OutOfMemoryError`：内存耗尽
> - `NoClassDefFoundError`：无法加载某个Class
> - `StackOverflowError`：栈溢出
>
> 
>
> **Exception（异常）是应用程序中可能的可预测、可恢复问题。**
>
> - **Checked Exception**（**非Runtime Exception**）/编译时异常**必须要对其进行处理**，否则**无法通过编译** 
>   - `IOException`：I/O操作中出现的异常，例如文件读写、网络连接等。
>   - `SQLException`：与数据库相关的异常，例如连接数据库、执行SQL语句等。
>   - `ClassNotFoundException`：当尝试加载类时，找不到类的异常。
>   - `InterruptedException`：当线程处于等待状态时，被中断时抛出的异常。
>   - `InvocationTargetException`：反射调用时，被调用方法抛出异常而未被捕获时抛出的异常。
>   - `NoSuchMethodException`：当使用反射调用一个不存在的方法时，抛出的异常。
>   - `ParseException`：当解析字符串时遇到不能识别的字符时，抛出的异常。
>   - `CloneNotSupportedException`：当尝试克隆一个不支持克隆的对象时，抛出的异常。
>
> 
>
> - **Unchecked Exception**（**Runtime Exception**）/运行时异常
>
>   - `NullPointerException`(空指针错误)
>
>   - `IllegalArgumentException`(参数错误比如方法入参类型错误)
>
>   - `NumberFormatException`（字符串转换为数字格式错误，`IllegalArgumentException`的子类）
>
>   - `ArrayIndexOutOfBoundsException`（数组越界错误）
>
>   - `ClassCastException`（类型转换错误）
>
>   - `ArithmeticException`（算术错误）
>
>   - `SecurityException` （安全错误比如权限不够）
>
>   - `UnsupportedOperationException`(不支持的操作错误比如重复创建同一用户)
>
>     ......

### 异常处理

Java语言中的异常处理包括**声明异常**、**抛出异常**、**捕获异常**和**处理异常**四个环节。



**throw**用于**手动抛出异常**。



**throws**关键字可以在方法上声明该方法要**向上抛出异常交由调用该方法的进行异常处理**，同时可以在方法内部可以通过throw手动抛出异常对象。



**try**是用于**检测被包住的语句块是否出现异常**，如果有异常，则抛出异常，并执行catch语句。



**cacth**用于**捕获从try中抛出的异常并作出处理**。



**finally**语句块是**不管有没有出现异常都要执行的内容**

![image-20221012080735003](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221012080735003.png)

![image-20221012080634779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221012080634779.png)

## 反射★



![image-20220825163327704](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825163327704.png)

```java
/**
 * Reflection反射
 *      Reflection（反射）是被视为动态语言的关键，反射机制允许程序在执行期
 *      借助于Reflection API取得任何类的内部信息，并能直接操作任意对象的内部属性及方法
 *      加载完类之后，在堆内存的方法区中就产生了一个Class类型的对象（一个类只有一个Class对象），这个对象就包含了完整的类的结构信息。
 *      我们可以通过这个对象看到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，我们形象的称之为：反射
 *      反射的特征:动态性
 *
 */
```

### 反射机制★

**Reflection（反射）是被视为 动态 语言的关键，**

**反射机制允许程序在执行期借助于Reflection API取得任何类的内部信息，并能直接操作任意对象的内部属性及方法**

**加载完类之后，在堆内存的方法区中就产生了一个Class类型的对象（一个类只有一个Class对象），这个对象就包含了完整的类的结构信息。**

**我们可以通过这个对象看到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，我们形象的称之为：反射**

<u>**反射的特征:动态性**</u>

**反射是框架底层的核心**

缺点：使用反射基本是解释执行；对执行速度有影响

**反射调优优化**：**关闭访问检查--setAccessible（）方法**

setAccessible的作用是启动和禁用访问安全检查的开关

当参数值设置为true时：反射的对象在使用时取消访问检查，提高反射的效率。参数值为false反之；

```Java
public class ReflectionTest {
    /*
        使用Reflection前;常规操作
     */
    @Test
    public void test(){
        //创建类的对象
        Person person = new Person("张锦豪",21,"Java",true);
        //通过类的对象调用类的相关结构
        person.setName("EddieZhang");
        person.showInformation();
        //Name: EddieZhangAge: 21Major: JavaIs Male: true
        System.out.println(person.toString());
        //Person{name='EddieZhang', age=21, major='Java', isMale=true}

        //无法通过类的对象对类内部为private的结构进行调用
    }

    /*
        使用Reflection;

            可以调用(运行时)类中的private结构
     */
    @Test
    public void test1() throws Exception{
        Class<Person> personClass = Person.class;

        Constructor<Person> constructor = personClass.getConstructor(String.class,int.class,String.class,boolean.class);
        Person newInstance = constructor.newInstance("张锦豪", 21,"Java", true);
        System.out.println(newInstance.toString());
        //Person{name='张锦豪', age=21, major='Java', isMale=true}
        newInstance.setName("EddieZhang");
        System.out.println(newInstance.toString());
        //Person{name='EddieZhang', age=21, major='Java', isMale=true}


        System.out.println("----------------------------------通过反射调用private结构-----------------------------------");
        //通过反射可以调用类中的private结构

        //调用私有构造器
        Constructor<Person> declaredConstructor = personClass.getDeclaredConstructor(String.class, int.class, boolean.class);
        declaredConstructor.setAccessible(true);//setAccessible(true)
        Person person = declaredConstructor.newInstance("Eddie", 21, true);
        System.out.println(person.toString());
        //Person{name='Eddie', age=21, major='null', isMale=true}

        //调用私有的方法
        Method showPrivateInformation = personClass.getDeclaredMethod("showPrivateInformation");
        showPrivateInformation.setAccessible(true);//setAccessible(true)
        Object invoke = showPrivateInformation.invoke(person);//invoke()
        //Name: EddieAge: 21Is Male: true

        //调用私有属性
        Field name = personClass.getDeclaredField("name");
        name.setAccessible(true);
        name.set(person,"EddieZhang");
        System.out.println(person);
        //Person{name='EddieZhang', age=21, major='null', isMale=true}
    }
}
```

### Class类★

**java.long.Class:代表一个类，Class对象表示某个类加载后在堆空间中的对象**

1.Class也是类。因此也继承于Object类

2.Class类对象不是new出来的，而是系统创建的

​		类加载器（classLoader）加载完类之后，

​		在堆内存的方法区中就产生了一个Class类型的对象（一个类只有一个Class对象）

3.对于某个Class类的对象（Class的实例对应着一个运行时类），在内存中有且只有一份（在加载过程中通过同步机制），因为**类只加载一次**

4.每个类的实例都会记得自己是由哪一个Class实例所生成的

5.通过Class对象可以完整地得到一个类（Class的实例对应着一个运行时类）的完整结构，通过一系列的API

6.Class对象储存于堆中

7.类的字节码二进制数据（元数据）是储存于方法区中

![image-20220826082344838](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826082344838.png)

![image-20220826082400253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826082400253.png)

```java
/** package java.lang;
 *      Class类
 *          反射的”源头“
 *      加载过程:
 *          程序经过java.c命令后;会生成一个或多个的字节码文件(.class)
 *              --接着使用java.exe命令;对字节码文件进行解释运行;相当于将某个字节码文件加载到内存中。--（类的加载）--只会加载一次
 *              加载到内存中的类叫做运行时类;此运行时类就作为Class的一个实例
 *              Class的实例对应着一个运行时类（唯一存在）
 *              加载到内存中的运行时类会缓存一段时间--在此期间我们可以通过不同的方式获取Class的运行时类
 *          加载完类之后，在堆内存的方法区中就产生了一个Class类型的对象（一个类只有一个Class对象），这个对象就包含了完整的类的结构信息。
 *  *      我们可以通过这个对象看到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以，我们形象的称之为：反射
 *  *      反射的特征:动态性
 *
 *  万物皆对象--加载完的类(运行时类)也是Class的对象
 */
/*
        对于某个类的Class对象，在内存中只会有一份;缘由是类只加载一次
     */
    @Test
    public void test1() throws Exception{
        //调用Class的静态方法:forName(String classPath)★
        Class<?> aClass = Class.forName("javalangclasstest.Person1");//参数为全类名
        System.out.println(aClass.hashCode());
        //同一个类进行第二次加载test
        Class<?> aClass1 = Class.forName("javalangclasstest.Person1");//参数为全类名
        System.out.println(aClass1.hashCode());
        //209813603
        //209813603
        //结果显示内存中只存在唯一一份某个类的Class对象;
```

**获取Class的实例**--调用Class的静态方法:forName(String classPath)★

```java
public class ClassTest {
    /*  获取Class的实例
            Class的实例对应着一个运行时类（唯一存在）
               加载到内存中的运行时类会缓存一段时间--在此期间我们可以通过不同的方式获取Class的运行时类
            1.调用运行时类的属性.class--Class<Person> class1 = Person.class;
            2.通过运行时类的对象.getClass()--Class<? extends Person> personClass1 = person.getClass();
            3.调用Class的静态方法:forName(String classPath)★
            4.使用类的加载器 ClassLoader（了解）
     */
    @Test
    public void test() throws ClassNotFoundException {
        //1.调用运行时类的属性.class--Class<Person> class1 = Person.Class;
        Class<Person> personClass = Person.class;
        System.out.println(personClass);
        //class reflectiontest.Person

        //2.通过运行时类的对象.getClass()--Class<? extends Person> personClass1 = person.getClass();
        Person person = new Person();
        Class<? extends Person> personClass1 = person.getClass();
        System.out.println(personClass1);
        //class reflectiontest.Person

        //3.调用Class的静态方法:forName(String classPath)★
        Class<?> forName = Class.forName("reflectiontest.Person");
        System.out.println(forName);
        //class reflectiontest.Person

        //4.使用类的加载器 ClassLoader（了解）
        ClassLoader classLoader = ClassTest.class.getClassLoader();
        Class<?> loadClass = classLoader.loadClass("reflectiontest.Person");
        System.out.println(loadClass);
        //class reflectiontest.Person

        System.out.println(personClass == personClass1);//true
        System.out.println(personClass1 == forName);//true
        System.out.println(forName == loadClass);//true

    }
}
```

### 类加载★

![image-20220827105406030](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220827105406030.png)

![image-20220826082736376](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826082736376.png)

![image-20220826082827840](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826082827840.png)

**ClassLoader--类加载器**

![image-20220826083307561](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826083307561.png)

![image-20220826083350593](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826083350593.png)

![image-20220826122011108](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220826122011108.png)

### 反射获取类的结构信息★

#### Class

#### Filed

#### Method

#### Constructor

#### 访问属性

![image-20220827105716925](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220827105716925.png)

#### 访问方法

### 反射相关类

java.long.reflaction中

**java.long.Class**

代表一个类；Class对象表示某个类加载后在堆中的对象

**java.long.reflact.Method**

代表类的方法；Method对象表示某个类的方法

**java.long.reflact.Field**

代表类的成员变量；Field对象表示某个类的成员变量（字段）

**java.long.reflact.Constructor**

代表类的构造方法；Constructor对象表示某个类的构造器

### 反射调用性能优化

### Class类常用方法



## 网络

### 网络基本概念

![image-20220828083731033](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828083731033.png)

![image-20220828083751842](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828083751842.png)

#### 局域网和互联网

为了实现两台计算机的通信，必须用一个网络线路连接两台计算机

 ![image-20220828083953885](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828083953885.png)

服务器：是指提供信息的计算机或程序，

客户机：是指请求信息的计算机或程序。

网络：用于连接服务器与客户机，实现两者间的相互通信。

有时在某个网络中很难将服务器与客户机区分开。

局域网（Local Area Network，LAN），就是一群通过一定形式连接起来的计算机。它可以由两台计算机组成，也可以由同一区域内的上千台计算机组成。将LAN延伸到更大的范围，这样的网络称为广域网（Wide Area Network，WAN）。

因特网（Internet），就是由无数的LAN和WAN组成的

#### 网络协议

![image-20220828084543444](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084543444.png)

![image-20220828084702074](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084702074.png)

![image-20220828084711724](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084711724.png)

![image-20220828085042243](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085042243.png)

![image-20220828084307985](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084307985.png)

![image-20220828084408051](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084408051.png)

#### 端口和套接字

![image-20220828085413959](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085413959.png)

![image-20220828085423824](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085423824.png)

![image-20220828085440807](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085440807.png)

### TCP/IP协议簇

![image-20220828084427356](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084427356.png)

![image-20220828084440310](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084440310.png)

![image-20220828084900228](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084900228.png)

![image-20220828084930580](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084930580.png)

![image-20220828084941313](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084941313.png)

![image-20220828084956730](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828084956730.png)

![image-20220828085009675](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085009675.png)

#### InetAddress地址类

![image-20220828085944888](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085944888.png)

![image-20220828085951766](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085951766.png)

![image-20220828090308095](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828090308095.png)

```java
public class InternetAddressTest {
        public static void main(String[] args) {
        try {
            InetAddress inetAddress = InetAddress.getByName("192.168.10.08");//IP
            System.out.println(inetAddress);
            InetAddress inetAddress1 = InetAddress.getByName("www.youtube.com");//域名
            System.out.println(inetAddress1);
            InetAddress inetAddress2 = InetAddress.getByName("127.0.0.1");//本机
            System.out.println(inetAddress2);
            InetAddress localHost = InetAddress.getLocalHost();//本机
            System.out.println(localHost);
            //localHost.getHostName()
            String hostName = localHost.getHostName();
            System.out.println(hostName);
            //localHost.getHostAddress()
            String hostAddress = localHost.getHostAddress();
            System.out.println(hostAddress);

        } catch (UnknownHostException e) {
            throw new RuntimeException(e);
        }
    }

    /*
        InetAddress类
     */
    @Test
    public void test() throws UnknownHostException {
        InetAddress inetAddress = InetAddress.getByName("127.0.0.1");
        System.out.println(inetAddress);
        // /127.0.0.1
        InetAddress localHost = InetAddress.getLocalHost();
        System.out.println(localHost);
        //LAPTOP-EFT0K1UP/192.168.199.1
        String hostAddress = localHost.getHostAddress();
        String hostName = localHost.getHostName();
        System.out.println("主机名:" + hostName + "\t主机地址:" + hostAddress);
        //主机名:LAPTOP-EFT0K1UP  主机地址:192.168.199.1
    }
}
```

#### ServerSocket服务器套接字类

![image-20220828090121323](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828090121323.png)

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_d0c10404007446a1965e8f3431df9bf0.jpg)ServerSocket()：创建非绑定服务器套接字。

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_d0934365017148c8b5afca8d64354a66.jpg)　ServerSocket(int port)：创建绑定到特定端口的服务器套接字。

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_777839b25998440391fe4300aec751c7.jpg)　ServerSocket(int port, int backlog)：利用指定的backlog创建服务器套接字，并将其绑定到指定的本地端口号上。

![img](http://localhost:8000/52da9674-5bf6-443b-b562-44a304f2f6fb/OEBPS/Images/image_da9fd34ed3c64cb39fbcf45f567a4590.jpg)　ServerSocket(int port, int backlog, InetAddress bindAddress)：使用指定的端口、侦听backlog和要绑定到的本地IP地址创建服务器。这种情况适用于计算机上有多块网卡和多个IP地址的情况，用户可以明确规定ServerSocket在哪块网卡或哪个IP地址上等待客户的连接请求

![image-20220828090251649](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828090251649.png)

**注意**

**accept()方法**会**阻塞**线程的继续执行，直到接收到客户的呼叫。如果没有客户呼叫服务器，那么System.out.println("连接中")语句将不会执行。语句如果没有客户请求，accept()方法没有发生阻塞，肯定是程序出现了问题。通常是使用了一个被其他程序占用的端口号，ServerSocket绑定没有成功。



#### TCP

![image-20220828085103397](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085103397.png)

![image-20220828085113805](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085113805.png)

![image-20220828085124382](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085124382.png)

![image-20220828085143144](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085143144.png)

![image-20220828085152114](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085152114.png)

```java
/**
 * 实现TCP的网络编程
 *  For instance 1:
 *      客户端发送信息给服务端，服务端将数据显示在控制台;
 */
public class TCPTest {
    /*  服务器端
            //1.实例化ServerSocket指明自己的端口
            //2.调用accept()方法表明接收来自客户端的socket
            //3.实例化流
            //4.操作数据
            //5.关闭资源

     */
    @Test
    public void server() {
        ServerSocket serverSocket = null;
        Socket socket = null;
        InputStream socketInputStream = null;
        ByteArrayOutputStream byteArrayOutputStream = null;
        try {
            serverSocket = new ServerSocket(8899);//1.实例化ServerSocket指明自己的端口
            socket = serverSocket.accept();//2.调用accept()方法表明接收来自客户端的socket
            socketInputStream = socket.getInputStream();//3.实例化流

            byteArrayOutputStream = new ByteArrayOutputStream();//4.操作数据 ByteArrayOutputStream()接收客户端数据
            byte[] bytes = new byte[5];
            int len;
            while ((len = socketInputStream.read(bytes)) != -1) {
                byteArrayOutputStream.write(bytes, 0, len);
            }
            System.out.println(byteArrayOutputStream.toString());
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {//5.关闭资源
            if (byteArrayOutputStream != null) {
                try {
                    byteArrayOutputStream.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (socketInputStream != null) {
                try {
                    socketInputStream.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (socket != null) {
                try {
                    socket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (serverSocket != null) {
                try {
                    serverSocket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }


    /*  客户端
            //1.实例化Socket指明服务器的IP和端口
            //2.实例化流
            //3.操作数据
            //4.关闭资源
     */
    @Test
    public void client() {
        Socket socket = null;
        OutputStream socketOutputStream = null;
        try {
            InetAddress inetAddress = InetAddress.getByName("127.0.0.1");
            socket = new Socket(inetAddress, 8899);//1.实例化Socket指明服务器的IP和端口

            socketOutputStream = socket.getOutputStream();//2.实例化流
            socketOutputStream.write("你好我是客户端".getBytes());//3.操作数据
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {//4.关闭资源
            if (socketOutputStream != null) {
                try {
                    socketOutputStream.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
            if (socket != null) {
                try {
                    socket.close();
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }

}
```

#### UDP

![image-20220828085212951](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085212951.png)

![image-20220828085228900](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220828085228900.png)



## 正则表达式

**正则表达式是处理文本的利器**		**正则表达式技术是对字符串进行模式匹配的技术**

**正则表达式是对字符串操作的一种逻辑公式，就是用事先定义好的一些特定字符、及这些特定字符的组合，组成一个"规则字符串"，这个"规则字符串"用来表达对字符串的一种过滤逻辑**

给定一个正则表达式和另一个字符串，我们可以达到如下的目的：

-  \1. 给定的字符串是否符合正则表达式的过滤逻辑（称作"匹配"）；
-  \2. 可以通过正则表达式，从字符串中获取我们想要的特定部分。

正则表达式的特点是：

-  \1. 灵活性、逻辑性和功能性非常的强；
-  \2. 可以迅速地用极简单的方式达到字符串的复杂控制。
-  \3. 对于刚接触的人来说，比较晦涩难懂。

注意：正则表达式写好后，没有错对之分，返回结果只是true和false

\1. 任意一个字符表示匹配任意对应的字符，如a匹配a，7匹配7，-匹配-。

\2. []代表匹配中括号中其中任一个字符，如[abc]匹配a或b或c。

\3. -在中括号里面和外面代表含义不同，如在外时，就匹配-，如果在中括号内[a-b]表示匹配26个小写字母中的任一个；[a-zA-Z]匹配大小写共52个字母中任一个；[0-9]匹配十个数字中任一个。

\4. ^在中括号里面和外面含义不同，如在外时，就表示开头，如^7[0-9]表示匹配开头是7的，且第二位是任一数字的字符串；如果在中括号里面，表示除了这个字符之外的任意字符(包括数字，特殊字符)，如[^abc]表示匹配出去abc之外的其他任一字符。

\5. .表示匹配任意的字符。

\6. \d表示数字。

\7. \D表示非数字。

\8. \s表示由空字符组成，[ \t\n\r\x\f]。

\9. \S表示由非空字符组成，[^\s]。

\10. \w表示字母、数字、下划线，[a-zA-Z0-9_]。

\11. \W表示不是由字母、数字、下划线组成。

\12. ?: 表示出现0次或1次。

\13. +表示出现1次或多次。

\14. *表示出现0次、1次或多次。

\15. {n}表示出现n次。

\16. {n,m}表示出现n~m次。

\17. {n,}表示出现n次或n次以上。

\18. XY表示X后面跟着Y，这里X和Y分别是正则表达式的一部分。

\19. X|Y表示X或Y，比如"food|f"匹配的是foo（d或f），而"(food)|f"匹配的是food或f。

\20. (X)子表达式，将X看做是一个整体

### **Pattern和Matcher**类

#### Matcher 几个常用方法

| 名称        | 说明                                                        |
| ----------- | ----------------------------------------------------------- |
| find()      | 返回目标字符串中是否包含与 Pattern 匹配的子串               |
| group()     | 返回上一次与 Pattern 匹配的子串                             |
| start()     | 返回上一次与 Pattern 匹配的子串在目标字符串中的开始位置     |
| end()       | 返回上一次与 Pattern 匹配的子串在目标字符串中的结束位置加 1 |
| lookingAt() | 返回目标字符串前面部分与 Pattern 是否匹配                   |
| matches()   | 返回整个目标字符串与 Pattern 是否匹配                       |
| reset()     | 将现有的 Matcher 对象应用于一个新的字符序列。               |

```java
//正则表达式
public class FindGroup {
    public static void main(String[] args) {
        // 使用字符串模拟从网络上得到的网页源码
        String str = "我想找一套适合自己的JAVA教程，尽快联系我13500006666" + "交朋友，电话号码是13611125565" + "出售二手电脑，联系方式15899903312";
        // 创建一个Pattern对象，并用它建立一个Matcher对象
        // 该正则表达式只抓取13X和15X段的手机号
        // 实际要抓取哪些电话号码，只要修改正则表达式即可
        Matcher m = Pattern.compile("((13\\d)|(15\\d))\\d{8}").matcher(str);
        // 将所有符合正则表达式的子串（电话号码）全部输出
        while (m.find()) {
            System.out.println(m.group());
        }
    }
}

//instance
/**
 * RegularExpression正则表达式
 * **正则表达式是处理文本的利器**		**正则表达式技术是对字符串进行模式匹配的技术**
 *
 */
public class ReExpTest {
    public static void main(String[] args) {
        //文本内容
        String content = "1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年" +
                " 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年";

        String str = "(\\d\\d)(\\d\\d)";//编写正则表达式的格式内容 格式中有()表示分组 整体为大组 第一个()为小组1 第二个()为小组2
        //将字符串编译成pattern对象
        Pattern pattern = Pattern.compile(str);
        //pattern对象创建一个matcher匹配器对象
        Matcher matcher = pattern.matcher(content);//将要查询的内容传入匹配器
        while(matcher.find()){//循环进行find
            System.out.println("文本中出现的年份有\t" + matcher.group());//group默认0 表示 大组 [0,1) 整体的子字符串
            System.out.println("文本中出现的年份(前两个数值)有\t" + matcher.group(1));//表示小组1 [2,3)
            System.out.println("文本中出现的年份(后两个数值)有\t" + matcher.group(2));//表示小组2 [4,5)
//            System.out.println("文本中出现的年份(后两个数值)有\t" + matcher.group(3));//表示小组2 [6,7)
                //...不能取没有的小组 否则报越界的异常 Exception in thread "main" java.lang.IndexOutOfBoundsException: No group 3
            //以下是底层源码 
            /*
            public String group(int group) {
                if (first < 0)
                    throw new IllegalStateException("No match found");
                if (group < 0 || group > groupCount())
                    throw new IndexOutOfBoundsException("No group " + group);
                if ((groups[group*2] == -1) || (groups[group*2+1] == -1))
                    return null;
                return getSubSequence(groups[group * 2], groups[group * 2 + 1]).toString();
            }
             */
        }
        /*
        content = "1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年"
        str = "(\d\d)(\d\d)"
        pattern = {Pattern@752} "(\d\d)(\d\d)"
        matcher = {Matcher@753} "java.util.regex.Matcher[pattern=(\d\d)(\d\d) region=0,755 lastmatch=1166]"
         parentPattern = {Pattern@752} "(\d\d)(\d\d)"
         groups = {int[20]@860} [0, 4, 0, 2, 2, 4, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1]
          0 = 0
          1 = 4
          2 = 0
          3 = 2
          4 = 2
          5 = 4
          6 = -1
          7 = -1
          8 = -1
          9 = -1
          10 = -1
          11 = -1
          12 = -1
          13 = -1
          14 = -1
          15 = -1
          16 = -1
          17 = -1
          18 = -1
          19 = -1
         */


    }
```

##### matches 和 lookingAt 方法

**matches 和 lookingAt 方法都用来尝试匹配一个输入序列模式**。它们的不同是 **matches 要求整个序列都匹配**，而lookingAt 不要求

##### replaceFirst 和 replaceAll 方法

**replaceFirst 和 replaceAll 方法用来替换匹配正则表达式的文本**。不同的是，**replaceFirst 替换首次匹配**，**replaceAll 替换所有匹配**

##### appendReplacement 和 appendTail 方法

**Matcher 类也提供了appendReplacement 和 appendTail 方法用于文本替换**

### PatternSyntaxException 类

**PatternSyntaxException 是一个非强制异常类，它指示一个正则表达式模式中的语法错误。**

PatternSyntaxException 类提供了下面的方法来帮助我们查看发生了什么错误。

| **序号** | **方法及说明**                                               |
| -------- | ------------------------------------------------------------ |
| 1        | **public String getDescription()** 获取错误的描述。          |
| 2        | **public int getIndex()**  获取错误的索引。                  |
| 3        | **public String getPattern()** 获取错误的正则表达式模式。    |
| 4        | **public String getMessage()** 返回多行字符串，包含语法错误及其索引的描述、错误的正则表达式模式和模式中错误索引的可视化指示 |



### **正则表达式的元字符**

|      元字符 分类       |
| :--------------------: |
|        1.限定符        |
|      2.字符匹配符      |
| 3.分组组合和反向引用符 |
|       4.特殊字符       |
|      5.选择匹配符      |
|        6.定位符        |

##### 限定符

| 符号 | 表示             | 示例   | 解释                                           |
| ---- | ---------------- | ------ | ---------------------------------------------- |
| [ ]  | 可接收的字符列表 | [efgn] | e,f,g,n中任意的一个字符                        |
| [^]  | 不接收的字符列表 | [^abc] | 除了a,b,c之外的任意一个字符 包括数字和特殊字符 |
| -    | 连字符           | A-Z    | 任意单个大写字母                               |

```java
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=";
        Pattern compile = Pattern.compile("[abf-]");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "\t");
            //a	f	a	f	a	f	f	-	
        }
    }
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=";
        Pattern compile = Pattern.compile("[^abf-]");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "");
            //shkjhkjhkudhkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+289420()=
        }
    }
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=";
        Pattern compile = Pattern.compile("[A-Z]");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "");
            //DKJSAHDKJAHSKDJHAKJHSDKJA
        }
    }
```

##### 字符匹配符

| 符号 | 表示                                                 | 示例 | 解释 |
| ---- | ---------------------------------------------------- | ---- | ---- |
| .    | 匹配除了\n外的任何字符                               | a..b |      |
| \\d  | 匹配单个数字字符 相当于[0-9]                         |      |      |
| \\D  | 匹配单个非数字字符 相当于[ ^0-9 ]                    |      |      |
| \\w  | 匹配单个数字 大小写字母字符 相当于 [0-9a-zA-Z_ ]     |      |      |
| \\W  | 匹配单个非数字 大小写字母字符 相当于 [ ^0-9a-zA-Z_ ] |      |      |
| \\s  | 匹配任何空白字符 空格或者制表符(相当于多个空格)      |      |      |
| \\S  | 匹配任何非空白字符 ,和\\s 刚好相反                   |      |      |

```java
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=";
        Pattern compile = Pattern.compile(".");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "");
            //sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=
        }
    }
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=aiub ajkb af-b dusb a--b";
        Pattern compile = Pattern.compile("a..b");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "\t");
            //aiub	ajkb	af-b	a--b
        }
    }
```

##### **选择匹配符**

| 符号 | 表示                               | 示例   | 解释   |
| ---- | ---------------------------------- | ------ | ------ |
| \|   | 表示 或 匹配”\|“之前或之后的表达式 | ab\|cd | ab或cd |

```java
public void test(){
        //内容文本
        String content = "sahfkjahfkjahfkudhfkihdkDKJSAHDKJAHSKDJHAKJHSDKJA1231534213545+*+-289420()=aiub ajkb af-b dusb a--b zjh1277408666@qq.com zjh20001207@icloud.com";
        Pattern compile = Pattern.compile("\\*|-|b");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.print(matcher.group(0) + "\t");
            //*	-	b	b	-	b	b	-	-	b	
        }
    }
```

##### 限定符

**用于指定其前面的字符和组合项连续出现多少次** Java匹配属于贪婪匹配 尽可能匹配多的

| 符号  | 表示                                     | 示例 | 解释 |
| ----- | ---------------------------------------- | ---- | ---- |
| *     | 指定字符重复0到n次（相当于无要求）零到多 |      |      |
| +     | 指定字符重复1或n次（至少1次）一到多      |      |      |
| ?     | 指定字符重复0次或1次（最多1次）0到1      |      |      |
| {n}   | 只能输入n个字符                          |      |      |
| {n,}  | 指定至少n个匹配                          |      |      |
| {n,m} | 指定至少n个但不多于m个匹配               |      |      |

##### 定位符

| 符号 | 表示                                                  | 示例 | 解释 |
| ---- | ----------------------------------------------------- | ---- | ---- |
| ^    | 指定起始字符                                          |      |      |
| $    | 指定结束字符                                          |      |      |
| \\b  | 匹配目标字符串边界（有空格间隔的结尾或者 文本的结尾） |      |      |
| \\B  | 匹配目标字符串的非边界                                |      |      |

```java
public void test1(){
        //内容文本
        String content =  "1-akuh -1-a211111aaaaaahello eddie2 eddie irving eddie 3eddie2";
        Pattern compile = Pattern.compile("eddie\\B");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.println(matcher.group(0));
            //eddie
            //eddie
        }
    }
public void test1(){
        //内容文本
        String content =  "1-akuh -1-a211111aaaaaahello eddie2 eddie2 irving eddie2 3eddie2";
        Pattern compile = Pattern.compile("eddie\\B");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.println(matcher.group(0));
            //eddie
            //eddie
            //eddie
            //eddie
        }
    }
```

##### 分组组合和反向引用

**分组 捕获 反向引用**

”(\\d\\d)(\\d)(\\d)“

分组：使用（）组成一个比较复杂的匹配模式 一个（）里面的部分可以看作是一个子表达式（一个分组）

捕获：把正则表达式中分组匹配的内容，保存到内存中以数字编号或者显示命名的组里，方便后面的引用；以分组的（）为标致 第一个出现的（）组号为1，

第二个为2 后续类推 组0代表整个正则式

反向引用：（）中的内容被捕获后，可以在这个括号后被使用，从而写出一个比较实用的匹配模式，即为反向引用；

这个引用可以在正则表达式内部 也可在正则表达式外部 内部反向引用：\\分组号，外部反向引用：$分组号；

```java
//要匹配两个连续相同的数字
(\\d)\\1
//要匹配五个连续相同的数字
(\\d)\\1{4}
//要匹配个位与千位相同，十位与百位相同的数 5225，1551
(\\d)(\\d)\\1\\2
    
//要匹配前是一个五位数 然后一个-符号 后面是九位数 连续的每三位要相同
//分组 捕获 反向引用
    @Test
    public void test6() {
        //内容
        String regularStr = "12315-555666888 54354-488315646 54641-555666999 48546-464444888 44644555666888";
        Pattern compile = Pattern.compile("\\d{5}-(\\d)\\1{2}(\\d)\\2{2}(\\d)\\3{2}");
        Matcher matcher = compile.matcher(regularStr);
        while(matcher.find()){
            System.out.println("找到 :" + matcher.group(0));
        }

    }
//将 我....我要...学学学学....编程java! 通过正则表达式修改成    我要学编程java!
    @Test
    public void test7() {
        //内容
        String regularStr = "我....我要...学学学学....编程java!";
        Pattern compile = Pattern.compile("\\.");
        Matcher matcher = compile.matcher(regularStr);
        regularStr = matcher.replaceAll("");//先将文本中的所有.替换掉
        System.out.println("处理.后的:\t" + regularStr);
        //我我要学学学学编程java!

        //找到文本中与第一次出现的一个字符有重复的所有重复字符
        Pattern compile1 = Pattern.compile("(.)\\1+");
        Matcher matcher1 = compile1.matcher(regularStr);
        while (matcher1.find()) {
            System.out.println(matcher1.group(0));
            //我我
            //学学学学
        }
        //使用反向引用
        regularStr = matcher1.replaceAll("$1");
        //反向引用正则表达式中的组一（第一次出现的一个字符）
        // 替换掉 文本中与第一次出现的一个字符有重复的所有重复字符 
        // 即为使用 (.) 取代所有的 (.)\1+
        System.out.println("处理重复后的:\t" + regularStr);
        //我要学编程java!
        
        //regularStr = Pattern.compile("(.)\\1+").matcher(regularStr).replaceAll("$1");//可以使用此精简写法
    }
```



| 常用分组构造形式                                    | 说明                                                         |
| --------------------------------------------------- | ------------------------------------------------------------ |
| (pattern)                                非命名捕获 | 捕获匹配的子字符串，编号为零的第一个捕获是由整个正则表达式模式匹配的文本（大组），其他捕获结果根据左括号的顺序从1开始自动编号（小组1小组2...） |
| (?<name>pattern)                命名捕获            | 将匹配的子字符串捕获到一个组名称或编号名称中，用于name的字符串不能包含任何标点符号，不能以数字开头，可以使用引号代替尖括号（？'name'） |
| 非捕获匹配                                          |                                                              |
| (?:pattern)                                         | 匹配 pattern 但是不捕获该匹配的子表达式 不储存供以后使用的匹配。对于（ \| ）或 字符的更经济的表达式 |
| (?=pattern)                                         | 例如 windows(?=95\|98\|NT \| 2000)匹配pattern中的windows 但不匹配 windows 3.1中的windows |
| (?!pattern)                                         | 上面的取反 pattern为要排除的内容 例如 windows(?=95 \| 98 \| NT \| 2000)不匹配pattern中的windows 匹配 windows 3.1中的windows |

```java
/**
     * 非命名捕获
     */
    @Test
    public void test2(){
        //内容文本
        String content = "1-akuh -1-a211111aaaaaahello eddie2 eddie irving eddie 3eddie2";
        Pattern compile = Pattern.compile("([a-z][a-z])([a-z])([a-z][a-z])");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.println("得到大组\t" + matcher.group(0));
            System.out.println("得到小组1\t" + matcher.group(1));
            System.out.println("得到小组2\t" + matcher.group(2));
            System.out.println("得到小组3\t" + matcher.group(3));
//            System.out.println("得到小组4\t" + matcher.group(4)); java.lang.IndexOutOfBoundsException: No group 4
//            得到大组	aaaaa
//            得到小组1	aa
//            得到小组2	a
//            得到小组3	aa
//            得到大组	ahell
//            得到小组1	ah
//            得到小组2	e
//            得到小组3	ll
//            得到大组	eddie
//            得到小组1	ed
//            得到小组2	d
//            得到小组3	ie
//            得到大组	eddie
//            得到小组1	ed
//            得到小组2	d
//            得到小组3	ie
//            得到大组	irvin
//            得到小组1	ir
//            得到小组2	v
//            得到小组3	in
//            得到大组	eddie
//            得到小组1	ed
//            得到小组2	d
//            得到小组3	ie
//            得到大组	eddie
//            得到小组1	ed
//            得到小组2	d
//            得到小组3	ie

        }
    }


	/**
     * 命名捕获 可以给分组命名
     */
    @Test
    public void test3(){
        //内容文本
        String content = "1-akuh -1-a211111aaaaaahello eddie2 eddie irving eddie 3eddie2";
        Pattern compile = Pattern.compile("(?<g1>[a-z][a-z])(?<g2>[a-z])(?<g3>[a-z][a-z])");
        Matcher matcher = compile.matcher(content);
        while(matcher.find()){
            System.out.println("得到大组\t" + matcher.group(0));
            System.out.println("得到小组1\t" + matcher.group("g1"));//可以通过名称来取
            System.out.println("得到小组2\t" + matcher.group("g2"));//可以通过名称来取
            System.out.println("得到小组3\t" + matcher.group("g3"));//可以通过名称来取
//            System.out.println("得到小组4\t" + matcher.group(4)); java.lang.IndexOutOfBoundsException: No group 4
            //得到大组	aaaaa
            //得到小组1	aa
            //得到小组2	a
            //得到小组3	aa
            //得到大组	ahell
            //得到小组1	ah
            //得到小组2	e
            //得到小组3	ll
            //得到大组	eddie
            //得到小组1	ed
            //得到小组2	d
            //得到小组3	ie
            //得到大组	eddie
            //得到小组1	ed
            //得到小组2	d
            //得到小组3	ie
            //得到大组	irvin
            //得到小组1	ir
            //得到小组2	v
            //得到小组3	in
            //得到大组	eddie
            //得到小组1	ed
            //得到小组2	d
            //得到小组3	ie
            //得到大组	eddie
            //得到小组1	ed
            //得到小组2	d
            //得到小组3	ie
        }
    }

-------------------------------------------------------------------------------------------------------------------------------

/**
     * 非捕获匹配 匹配 pattern 但是不捕获该匹配的子表达式 不储存供以后使用的匹配 不能使用System.out.println("得到小组1\t" + matcher.group("g1"));
     */
    @Test
    public void test4() {
        //内容文本
        String content = "windows95 windows98 windowsNT windows2000 windows3.1";
//        Pattern compile = Pattern.compile("window95|windows98|windowsNT|windows2000|windows3.1");
        Pattern compile = Pattern.compile("windows(?:95|98|NT|2000|3.1)");

        Matcher matcher = compile.matcher(content);
        while (matcher.find()) {
            System.out.println("得到大组\t" + matcher.group(0));
//            得到大组	windows95
//            得到大组	windows98
//            得到大组	windowsNT
//            得到大组	windows2000
//            得到大组	windows3.1
        }
    }

/**
     * 非捕获匹配 匹配 pattern 但是不捕获该匹配的子表达式 不储存供以后使用的匹配 不能使用System.out.println("得到小组1\t" + matcher.group("g1"));
     */
    @Test
    public void test4() {
        //内容文本
        String content = "windows95 windows98 windowsNT windows2000 windows3.1";
//        Pattern compile = Pattern.compile("window95|windows98|windowsNT|windows2000|windows3.1");
        Pattern compile = Pattern.compile("windows(?=95|98|NT|2000)");

        Matcher matcher = compile.matcher(content);
        while (matcher.find()) {
            System.out.println("得到大组\t" + matcher.group(0));
            //得到大组	windows
            //得到大组	windows
            //得到大组	windows
            //得到大组	windows
        }
    }
/**
     * 非捕获匹配 匹配 pattern 但是不捕获该匹配的子表达式 不储存供以后使用的匹配 不能使用System.out.println("得到小组1\t" + matcher.group("g1"));
     */
    @Test
    public void test4() {
        //内容文本
        String content = "windows95 windows98 windowsNT windows2000 windows3.1";
//        Pattern compile = Pattern.compile("window95|windows98|windowsNT|windows2000|windows3.1");
        Pattern compile = Pattern.compile("windows(?!95|98|NT|2000)");

        Matcher matcher = compile.matcher(content);
        while (matcher.find()) {
            System.out.println("得到大组\t" + matcher.group(0));
            //得到大组	windows
        }
    }
```

##### 非贪婪匹配

 **Java默认匹配属于贪婪匹配 尽可能匹配多的**

| ?    | 当此字符紧随任何其他限定符（*、+、?、{*n*}、{*n*,}、{*n*,*m*}）之后时，匹配模式是"非贪心的"。"非贪心的"模式匹配搜索到的、尽可能短的字符串，而默认的"贪心的"模式匹配搜索到的、尽可能长的字符串。例如，在字符串"oooo"中，"o+?"只匹配单个"o"，而"o+"匹配所有"o" |
| ---- | ------------------------------------------------------------ |



```java
//Java默认贪婪匹配
@Test
    public void test5() {
        //内容文本
        String content = "JavaJavaJavaJavaJava";
        Pattern compile = Pattern.compile("[Java]+");

        Matcher matcher = compile.matcher(content);
        while (matcher.find()) {
            System.out.print("得到大组\t" + matcher.group(0));
            //得到大组	JavaJavaJavaJavaJava
        }
    }
//非贪婪匹配（尽可能匹配少的） Java默认是贪婪匹配 尽可能匹配多的
    @Test
    public void test5() {
        //内容文本
        String content = "JavaJavaJavaJavaJava";
        Pattern compile = Pattern.compile("[Java]+?");

        Matcher matcher = compile.matcher(content);
        while (matcher.find()) {
            System.out.print("得到大组\t" + matcher.group(0));
            //得到大组	J得到大组	a得到大组	v得到大组	a得到大组	J得到大组	a得到大组	v得到大组	a得到大组	J得到大组	a得到大组	v得到大组	a得到大组	J得到大组	a得到大组	v得到大组	a得到大组	J得到大组	a得到大组	v得到大组	a
        }
    }

```



##### 转义字符

![](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220917112644709.png)

![image-20220917112750946](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220917112750946.png)

### String 使用正则表达式 

##### 进行 匹配 分割 替换

**String 的相关正则表达式的方法 顶层使用到pattern类和matcher类的方法实现**

```java
public boolean matches(String regex) {//匹配
        return Pattern.matches(regex, this);
    }
public String[] split(String regex) {//分割
        return split(regex, 0);
    }
public String replaceAll(String regex, String replacement) {//替换 
    //Tip：String属于不可变字符串 这里返回的是一个新的字符串 并不是改变原本的字符串
    //若想要让原本的字符串引用改变 可以将新的字符串的引用赋给原本的字符串
        return Pattern.compile(regex).matcher(this).replaceAll(replacement);
    }
```

String 中的matches方法 是整体匹配

```java
/**
 * String 使用正则表达式 进行匹配
 */
@Test
public void test8(){
    //查看是否是合格的手机号码格式(是否是138/139/139开头的11位)
    String str = "19880895771";
    String str1 = "13927437612";
    if (str.matches("1(37|38|39)\\d{8}")) {
        System.out.println("合格");
    }else {
        System.out.println("不合格");
    }
    //不合格
    if (str1.matches("1(37|38|39)\\d{8}")) {
        System.out.println("合格");
    }else {
        System.out.println("不合格");
    }
    //合格
}
/**
	* String 使用正则表达式 进行替换
*/
    @Test
    public void test9(){
        String str = "1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年" +
                " 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 1531年 1166年 " +
                "1531年 1166年 1531年 1166年 1531年 1166年 1531年 ";
        str = str.replaceAll("[1166]{4}","2000");
        System.out.println("替换后的str :" + str);
        //替换后的str :2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 2000年 1531年 
        // 2000年 1531年 
    }
/**
     * String 使用正则表达式 进行分割
     */
    @Test
    public void test10(){
        //按照要求 出现 # 或者 - 或者 ~ 或者 数字 就进行分割
        String str = "1-aku-h-1-a21#11~11aa4aa2aah-el#loeddie2eddieirvingeddie3eddie2";
        String[] split = str.split("#|~|_|-|\\d+");
        for (String splitStr :split) {
            System.out.print(splitStr + " ");
            //  aku h   a     aa aa aah el loeddie eddieirvingeddie eddie
        }
    }

```

### 正则表达式的实例练习

```java

/**
     * 验证电子邮件
     * 要求
     * 只能有一个@
     * @前面是用户名，可以是a-z A-Z 0-9 _字符
     * @后面是域名 域名只能是英文字母 icloud.com
     *
     */
    @Test
    public void test11(){
        String email = "20001207@icloud.com";
        if (email.matches("^[\w-]+@([a-zA-Z]+\.)+[A-Za-z]+$")){
            System.out.println("是个email");
        }else {
            System.out.println("非法的email");
        }
    }
	/**
     * 验证是否是正数或负数的小数
     */
    @Test
    public void test12(){
        String[] strings = new String[]{"+123","-345","34.89","-87.9","-1.01","0.45"};
        for (int i = 0; i < strings.length; i++) {
            if (strings[i].matches("^(-|\\+)?([1-9]\\d*|0)(\\.\\d*)?$")) {
                System.out.println("匹配成功");
            }else {
                System.out.println("匹配失败");
            }

        }

    }
	/**
     * 对一个url进行解析
     * https://www.bilibili.com:8080/video/BV1fh411y7R8?p=903&spm_id_from=pageDriver&vd_source=714abe81613c048c13e8afe87725981a
     * 1.协议头   https
     * 2.域名     www.bilibili.com
     * 3.端口     8080
     * 4.文件名    BV1fh411y7R8?p=903&spm_id_from=pageDriver&vd_source=714abe81613c048c13e8afe87725981a
     */
    @Test
    public void test13(){
        String url = "https://www.bilibili.com:8080/video/BV1fh411y7R8?p=903&spm_id_from=pageDriver&vd_source=714abe81613c048c13e8afe87725981a";
        Pattern compile = Pattern.compile("^([a-zA-Z]+)://([a-zA-Z.]+):(\\d+)[\\w-/]+([\\w.?=&]+)$");
        Matcher matcher = compile.matcher(url);
        if(matcher.matches()){
                System.out.println("整体匹配:" + matcher.group(0));
                System.out.println("协议头:" + matcher.group(1));
                System.out.println("域名:" + matcher.group(2));
                System.out.println("端口:" + matcher.group(3));
                System.out.println("文件名:" + matcher.group(4));
        }
    }
```



# **Java新特性**

## 范解

## 元注解

## 装箱|拆解

## 枚举★

**当需要定义一组常量时，强烈建议使用枚举类**

**使用枚举类型的优势**：

**1.类型安全**

**2.紧凑有效的数据定义**

**3.可以和程序其他部分完美交互**

**4.运行效率高**

**枚举类型声明出某种数据类型所有可能出现的值**

![image-20220825092912550](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825092912550.png)

![image-20220825092950809](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825092950809.png)

###  JDK1.5之前自定义枚举类 

```java
/**
 * 自定义一组常量的时候 考虑自定义枚举类
 * 自定义枚举类（enumeration）
 * 1.   属性 private final
 *      构造器 private,并给属性进行初始化
 *      对象 public static final
 *
 * 2.   提供属性的get方法
 *
 * 3.   重写toString（）方法
 */
class EnumerationSeason{
    //属性 private final
    private final String seasonName;
    private final String seasonDesc;

    //构造器 private,并给属性进行初始化
    private EnumerationSeason(String seasonName, String seasonDesc) {
        this.seasonName = seasonName;
        this.seasonDesc = seasonDesc;
    }

    //对象 public static final
    public static final EnumerationSeason SPRING = new EnumerationSeason("春天","万物复苏");
    public static final EnumerationSeason SUMMER = new EnumerationSeason("夏天","烈日炎炎");
    public static final EnumerationSeason AUTUMN = new EnumerationSeason("秋天","秋高气爽");
    public static final EnumerationSeason WINTER = new EnumerationSeason("冬天","寒风刺骨");

    //提供属性的get方法

    public String getSeasonName() {
        return seasonName;
    }

    public String getSeasonDesc() {
        return seasonDesc;
    }

    //重写toString（）方法

    @Override
    public String toString() {
        return "EnumerationSeason{" +
                "seasonName='" + seasonName + '\'' +
                ", seasonDesc='" + seasonDesc + '\'' +
                '}';
    }
}
public class EnumerationTest {
    public static void main(String[] args) {
        System.out.println(EnumerationSeason.SPRING);
        System.out.println(EnumerationSeason.SUMMER);
        System.out.println(EnumerationSeason.AUTUMN);
        System.out.println(EnumerationSeason.WINTER);
        System.out.println("-------------------------------------------");
        System.out.println(EnumerationSeason2.AUTUMN_ONE.toString());//toString()方法 未重写时默认：常量的名称

        System.out.println(EnumerationSeason2.valueOf("WINTER_ONE"));//valueOf()方法

        EnumerationSeason2[] enumerationSeason2s = EnumerationSeason2.values();//values()方法
        System.out.println(Arrays.toString(enumerationSeason2s));

    }
}
```

###  使用关键字enum定义枚举类 

```java
/*
使用说明
    使用 enum 定义的枚举类默认继承了 java.lang.Enum类，因此不能再继承其他类
    枚举类的构造器只能使用 private 权限修饰符
    枚举类的所有实例必须在枚举类中显式列出(, 分隔 ; 结尾)。列出的实例系统会自动添加 public static final 修饰
    必须在枚举类的第一行声明枚举类对象
JDK 1.5 中可以在 switch 表达式中使用Enum定义的枚举类的对象作为表达式, case 子句可以直接使用枚举值的名字, 无需添加枚举类作为限定
*/
/**
 * 使用enum自定义枚举类
 * 定义的enum枚举类 默认继承于java.long.Enum类
 * 1.   创建enum类
 * enum EnumerationSeason2{
 *
 * }
 * 2.   创建对象
 * AUTUMN_ONE("秋天","秋高气爽"),
 * WINTER_ONE("冬天","东暖花开");
 * 3.   声明属性 private final
 * 4.   声明构造器 private
 * 5.   提供属性的get方法
 * 6.   根据需要重写toString()方法--默认是常量的名
 */
//创建 enum 类
enum EnumerationSeason2 {//和普通Java类一样 枚举类可以实现一个或多个interface
    SPRING_ONE("春天","春暖花开"),
    //可以单独对象单独实现接口中的方法 独立调用
        SUMMER_ONE("夏天","夏日炎炎"),
    //可以单独对象单独实现接口中的方法 独立调用
            AUTUMN_ONE("秋天","秋高气爽"),
    //可以单独对象单独实现接口中的方法 独立调用
                WINTER_ONE("冬天","东暖花开");
    //设计属性 声明为 private final
    private final String seasonName1;
    private final String seasonDesc1;

    //设计构造器 声明为private
    private EnumerationSeason2(String seasonName1, String seasonDesc1) {
        this.seasonName1 = seasonName1;
        this.seasonDesc1 = seasonDesc1;
    }

    //提供属性的get方法

    public String getSeasonName1() {
        return seasonName1;
    }

    public String getSeasonDesc1() {
        return seasonDesc1;
    }
    //根据需要重写toString()方法 默认是常量名

    @Override
    public String toString() {
        return "EnumerationSeason2{" +
                "seasonName1='" + seasonName1 + '\'' +
                ", seasonDesc1='" + seasonDesc1 + '\'' +
                '}';
    }

    //可以实现接口中的方法 供所有对象共用 也可单独对象单独实现方法



}
```

###  Enum类的主要方法 

![image-20220825094032673](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825094032673.png)

###  实现接口的枚举类

![image-20220825094048253](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20220825094048253.png)

## 可变参数

## Lambda表达式★

## Stream API★

Stream 是 Java8 中处理集合的关键抽象概念，它可以指定你希望对集合进行的操作，可以执行非常复杂的查找、过滤和映射数据等操作。使用Stream API 对集合数据进行操作，就类似于使用 SQL 执行的数据库查询。也可以使用 Stream API 来并行执行操作。简而言之，Stream API 提供了一种高效且易于使用的处理数据的方式。

![image-20221218124854447](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218124854447.png)

特点：

        1 . 不是数据结构，不会保存数据。
    
        2. 不会修改原来的数据源，它会将操作后的数据保存到另外一个对象中。（保留意见：毕竟peek方法可以修改流中元素）
    
        3. 惰性求值，流在中间处理过程中，只是对操作进行了记录，并不会立即执行，需要等到执行终止操作的时候才会进行实际的计算。
![image-20221218124808871](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218124808871.png)

![image-20221218105140667](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218105140667.png)

    无状态：指元素的处理不受之前元素的影响；
    
    有状态：指该操作只有拿到所有元素之后才能继续下去。
    
    非短路操作：指必须处理所有元素才能得到最终结果；
    
    短路操作：指遇到某些符合条件的元素就可以得到最终结果，如 A || B，只要A为true，则无需判断B的结果。
### Stream流的常用方法

  Stream流的常用方法：

                终结方法：返回值类型不再是Stream接口本身类型的方法，例如：forEach方法和count方法
    
                非终结方法/延迟方法：返回值类型仍然是Stream接口自身类型的方法，除了终结方法都是延迟方法。例如：filter,limit,skip,map,conat
| 方法名称 | 方法作用   | 方法种类 | 是否支持链式调用 |
| -------- | ---------- | -------- | ---------------- |
| count    | 统计个数   | 终结方法 | 否               |
| forEach  | 逐一处理   | 终结方法 | 否               |
| filter   | 过滤       | 函数拼接 | 是               |
| limit    | 取用前几个 | 函数拼接 | 是               |
| skip     | 跳过前几个 | 函数拼接 | 是               |
| map      | 映射       | 函数拼接 | 是               |
| concat   | 组合       | 函数拼接 | 是               |

```java
package java8newfeaturetest;

/**
 @author EddieZhang
 @create 2022-08-24 14:27
 */

import java8newfeaturetest.methodconstructorreferences.Employee;
import java8newfeaturetest.methodconstructorreferences.EmployeeData;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.DoubleStream;
import java.util.stream.IntStream;
import java.util.stream.Stream;

/**
 * Stream:
 * 是数据渠道;用于操作数据源（集合，数组等）所生产的元素序列
 * Stream和Collection集合的区别:Collection是一种静态的内存数据结构，而Stream是有关计算的。前者主要面向内存，储存在内存中。后者主要面向CPU，通过CPU实现计算。
 * ”集合将讲的是数据,Stream讲的是计算“
 * 1.Stream自己不会储存元素
 * 2.Stream不会改变源对象。相反，会返回一个持有结果的新Stream。
 * 3.Stream操作是延迟执行的，这意味着他们会等到需要结果的时候才执行
 *      ①创建Stream（创建Stream--一个数据源（如：集合，数组）获取一个Stream）（数据源）-->
 *      ②中间操作（filter过滤，map映射，...对数据源进行处理的操作）-->
 *      ③ 终止操作(终端操作)（一旦执行终止操作，就执行中间的操作链。产生结果后，不再会被使用）
 *
 * Stream的创建方式
 * 1.通过集合
 * 2.通过数组
 * 3.通过Stream的of()
 * 4.创建无限流
 *      可以使用静态方法 Stream.iterate() 和 Stream.generate()
 *
 * Stream的中间操作--
 *      多个中间操作可以连接起来形成一个流水线，除非流水线上触发终止操作，否则中间操作不会执行任何的处理！而在终止操作时一次性全部处理，称为“惰性求值”
 * 1.筛选与切片
 *      filter(Predicate p) 接收 Lambda ， 从流中排除某些元素
 *      distinct() 筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素
 *      limit(long maxSize) 截断流，使其元素不超过给定数量
 *      skip(long n)跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一个空流。与 limit(n) 互补
 * 2.映射
 * 3.排序
 *
 */
public class StreamAPITest {
    /*
        创建Stream
            Stream的创建方式
            1.通过集合
                Java8 中的 Collection 接口被扩展，提供了两个获取流的方法
                    default Stream<E> stream() : 返回一个顺序流
                    default Stream<E> parallelStream() : 返回一个并行流
            2.通过数组
                Java8 中的 Arrays 的静态方法 stream() 可以获取数组流：重载形式，能够处理对应基本类型的数组
                    static <T> Stream<T> stream(T[] array): 返回一个流
            3.通过Stream的of()
                可以调用Stream类静态方法 of(), 通过显示值创建一个流。它可以接收任意数量的参数
                    public static<T> Stream<T> of(T... values) : 返回一个流
            4.创建无限流--帮助我们来创造数据
                可以使用静态方法 Stream.iterate() 和 Stream.generate(), 创建无限流
                    迭代:public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f)
                    生成:public static<T> Stream<T> generate(Supplier<T> s)
     */
    @Test
    public void test(){
        //1.通过集合
        List<Employee> employeeList = EmployeeData.getEmployees();
            //default Stream<E> stream() : 返回一个顺序流
        Stream<Employee> employeeStream = employeeList.stream();
            //default Stream<E> parallelStream() : 返回一个并行流
        Stream<Employee> parallelStream = employeeList.parallelStream();
        //2.通过数组
        int[] numberArray = new int[]{1,2,5,6,8,-5,4,5,33,546,3};
        String[] stringsArray = new String[]{"Eddie","James","Irving","Curry","Durant"};
        double[] longsArray = new double[]{12.5,56.4,553.5,66.5,54654.5};
            //static <T> Stream<T> stream(T[] array): 返回一个流;重载形式，能够处理对应基本类型的数组：
        IntStream intStream = Arrays.stream(numberArray);
        Stream<String> stringStream = Arrays.stream(stringsArray);
        DoubleStream doubleStream = Arrays.stream(longsArray);
        //3.通过Stream的of()
            //public static<T> Stream<T> of(T... values) : 返回一个流
        Stream<Integer> integerStream = Stream.of(1,5,3,5,1,2,5,8,4,54,56,5);
        Stream<String> stringStream1 = Stream.of("Eddie", "Irving", "James", "Curry", "Durant");
        //4.创建无限流
            //迭代:public static<T> Stream<T> iterate(final T seed, final UnaryOperator<T> f)
            Stream.iterate(0,t -> t + 2).limit(10).forEach(System.out::println);//遍历前十个偶数
            //迭代条件----------------------------迭代限制----------------终止操作
            //生成:public static<T> Stream<T> generate(Supplier<T> s)
            Stream.generate(Math::random).limit(10).forEach(System.out::println);//随机生成10个数
            //生成条件----------------------------迭代限制----------------终止操作


    }

    /*
        Stream的中间操作
            1.筛选与切片
            2.映射
            3.排序
     */
    @Test
    public void test1(){
        //1.筛选与切片
        List<Employee> employees = EmployeeData.getEmployees();
        System.out.println("------------------------------------映射-------------------------------");
            //filter(Predicate p) 接收 Lambda ， 从流中排除某些元素
        employees.stream().filter(employee -> employee.getSalary() > 7000).forEach(System.out::println);
        //创建流--------------中间操作（filter筛选）------------------------------终止操作
            //Employee{id=1002, name='马云', age=12, salary=9876.12}
            //Employee{id=1004, name='雷军', age=26, salary=7657.37}
            //Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}
        System.out.println("-------------------------------------------------------------");
            //limit(long maxSize) 截断流，使其元素不超过给定数量
         employees.stream().limit(3).forEach(System.out::println);//--注意以上Stream已经执行终止操作；不可再次使用；而需要新造一个Stream。
        //创建流-------中间操作（limit(long maxSize) 截断流）---终止操作
            //Employee{id=1001, name='马化腾', age=34, salary=6000.38}
            //Employee{id=1002, name='马云', age=12, salary=9876.12}
            //Employee{id=1003, name='刘强东', age=33, salary=3000.82}
        System.out.println("--------------------------------------------------------------");
            //skip(long n)跳过元素，返回一个扔掉了前 n 个元素的流。若流中元素不足 n 个，则返回一个空流。与 limit(n) 互补
        employees.stream().skip(3).forEach(System.out::println);
        //创建流--------中间操作（skip(long n)跳过元素）---终止操作
            //Employee{id=1004, name='雷军', age=26, salary=7657.37}
            //Employee{id=1005, name='李彦宏', age=65, salary=5555.32}
            //Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}
            //Employee{id=1007, name='任正非', age=26, salary=4333.32}
            //Employee{id=1008, name='扎克伯格', age=35, salary=2500.32}
        System.out.println("--------------------------------------------------------------");
            //distinct() 筛选，通过流所生成元素的 hashCode() 和 equals() 去除重复元素
        employees.add(new Employee(1010,"张锦豪",21,16000));//向集合中添加几个相同的数据
        employees.add(new Employee(1010,"张锦豪",21,16000));
        employees.add(new Employee(1010,"张锦豪",21,16000));
        employees.add(new Employee(1010,"张锦豪",21,16000));
        employees.add(new Employee(1010,"张锦豪",21,16000));
        employees.stream().distinct().forEach(System.out::println);
        //创建流--------中间操作（distinct() 筛选）---终止操作
        //Employee{id=1001, name='马化腾', age=34, salary=6000.38}
        //Employee{id=1002, name='马云', age=12, salary=9876.12}
        //Employee{id=1003, name='刘强东', age=33, salary=3000.82}
        //Employee{id=1004, name='雷军', age=26, salary=7657.37}
        //Employee{id=1005, name='李彦宏', age=65, salary=5555.32}
        //Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}
        //Employee{id=1007, name='任正非', age=26, salary=4333.32}
        //Employee{id=1008, name='扎克伯格', age=35, salary=2500.32}
        //Employee{id=1010, name='张锦豪', age=21, salary=16000.0}
        System.out.println("------------------------------------映射-------------------------------");
        //2.映射
        List<String> stringList = new ArrayList<>();
        stringList.add("apple");
        stringList.add("google");
        stringList.add("amazon");
        stringList.add("microsoft");
            //map(Function f)接收一个函数作为参数，该函数会被应用到每个元素上，并将其映射成一个新的元素
        stringList.stream().map(str -> str.toUpperCase()).forEach(System.out::println);
        //创建流---------------中间操作（map(Function f)接收一个函数作为参数）-----------终止操作
        //APPLE
        //GOOGLE
        //AMAZON
        //MICROSOFT
        System.out.println("----------------------------------------------------------------------");
        //practice获取员工name长度大于三的员工数据
        List<Employee> employeeList = EmployeeData.getEmployees();//创建集合将员工数据储存进集合中
        Stream<String> namesStream = employeeList.stream().map(employee -> employee.getName());//创建员工数据流-->使用中间操作映射map（）方法获取员工的姓名Steam
        Stream<String> stream = namesStream.filter(names -> names.length() > 3);//使用中间操作filter()筛选出名字长度大于三的员工姓名
        stream.forEach(System.out::println);//终止操作
        //比尔盖茨
        //扎克伯格
        System.out.println("---------------------------------------------------------------------");
            //flatMap(Function f)接收一个函数作为参数，将流中的每个值都换成另一个流，然后把所有流连接成一个流--集合中含集合的优先使用
                    //类似于addAll(arrayList)将添加的集合所有元素打散添加于一个集合中--区别于add(arrayList)将加入的集合按照一个元素进行添加
        List arrayList = new ArrayList();
        arrayList.add(1);
        arrayList.add(2);
        arrayList.add(3);
        List arrayList1 = new ArrayList();
        arrayList1.add(1);
        arrayList1.add(2);
        arrayList1.add(3);
        arrayList.add(arrayList1);
        System.out.println(arrayList);//[1, 2, 3, [1, 2, 3]]//将加入的集合看作一个元素进行添加
        arrayList.addAll(arrayList1);
        System.out.println(arrayList);//[1, 2, 3, [1, 2, 3], 1, 2, 3]//将添加的集合所有元素打散添加于一个集合中
        System.out.println("---------------------------------------------------------------");
        //将字符串中的多个字符构成的集合转换为对应的Stream的实例
        Stream<Character> characterStream = stringList.stream().flatMap(StreamAPITest::fromStringToStream);//方法引用--类::静态方法名
        characterStream.forEach(System.out::println);

        System.out.println("------------------------------------排序-------------------------------");
        //3.排序
        List<Integer> integerList = new ArrayList<>();
        integerList.add(56);
        integerList.add(5);
        integerList.add(-68);
        integerList.add(546);
        integerList.add(-648);
        integerList.add(-35);
        integerList.add(0);
        integerList.add(354);

        List<Employee> employeeList1 = EmployeeData.getEmployees();
        Stream<Employee> employeeStream = employeeList1.stream();
        //sorted() 产生一个新流，其中按自然顺序排序
        integerList.stream().sorted().forEach(System.out::println);

        //sorted(Comparator com) 产生一个新流，其中按比较器顺序排序
        employeeStream.sorted((e1,e2) -> {//Lambda表达式写法
            int compare = Integer.compare(e1.getAge(), e2.getAge());
            if(compare != 0){
                return compare;
            }else{
                return -Double.compare(e1.getSalary(), e2.getSalary());
            }
        }).forEach(System.out::println);//按照年龄进行升序排序--若年龄相等按照工资进行降序排序

//        employeeStream.sorted(new Comparator<Employee>() {--标准写法
//            @Override
//            public int compare(Employee o1, Employee o2) {
//                int compare = Integer.compare(o1.getAge(), o2.getAge());
//                if(compare != 0){
//                    return compare;
//                }else{
//                    return -Double.compare(o1.getSalary(),o2.getSalary());
//                }
//            }
//        }).forEach(System.out::println);//按照年龄进行升序排序--若年龄相等按照工资进行降序排序




    }
    /*
        //将字符串中的多个字符构成的集合转换为对应的Stream的实例
     */
    public static Stream<Character> fromStringToStream(String str1){
        List<Character> characterList = new ArrayList<>();
        for (Character charList :
                str1.toCharArray()) {
            characterList.add(charList);
        }

        return characterList.stream();
    }

    /*
        Stream的终止操作
            1.匹配与查找
            2.归约
            3.收集
     */
    @Test
    public void test2(){
        List<Employee> employeeList = EmployeeData.getEmployees();
        //1.匹配与查找
        //匹配
        System.out.println("---------------------------------匹配---------------------------------------------");
            //allMatch(Predicate p) 检查是否匹配所有元素
        System.out.println(employeeList.stream().allMatch(employee -> employee.getAge() > 18));//检查所有员工的年龄是否都大于18
        //false
        System.out.println(employeeList.stream().allMatch(employee -> employee.getSalary() > 2000));//检查所有员工的工资是否都大于5000
        //true
        System.out.println("------------------------------------------------------------------------------");
            //noneMatch(Predicate p) 检查是否没有匹配所有元素
        System.out.println(employeeList.stream().noneMatch(employee -> employee.getName().startsWith("雷")));//检查所有员工中是否没有一个姓雷的
        //false
        System.out.println("------------------------------------------------------------------------------");
            //anyMatch(Predicate p) 检查是否至少匹配一个元素
        System.out.println(employeeList.stream().anyMatch(employee -> employee.getName().startsWith("马")));//检查所有员工中是否至少有一个姓马的
        //true

        //查找
        System.out.println("---------------------------------查找---------------------------------------------");
            //findFirst() 返回第一个元素
        System.out.println(employeeList.stream().findFirst());//查找所有员工中第一个员工的信息
        //Optional[Employee{id=1001, name='马化腾', age=34, salary=6000.38}]
            //findAny() 返回当前流中的任意元素
        System.out.println(employeeList.stream().findAny());//其中stream()为串行流（顺序流）--通常随机返回第一个
        //Optional[Employee{id=1001, name='马化腾', age=34, salary=6000.38}]
        System.out.println(employeeList.parallelStream().findAny());//其中parallelStream()为平行流--通常不按照顺序随机返回
        //Optional[Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}]

        //元素总数
        System.out.println("---------------------------------元素总数---------------------------------------------");
            //count() 返回流中元素总数
        System.out.println(employeeList.stream().count());
        //8
            //count() 返回流中工资大于5000的元素个数
        //5
        System.out.println(employeeList.stream().filter(employee -> employee.getSalary() > 5000).count());


        //最大值
        System.out.println("---------------------------------最大值---------------------------------------------");
            //max(Comparator c) 返回流中最大值
        Stream<Double> doubleStream = employeeList.stream().map(employee -> employee.getSalary());//获取员工的工资流
        System.out.println(doubleStream.max((s1, s2) -> Double.compare(s1, s2)));//max()获取最大的工资金额
        //Optional[9876.12]

        //最小值
        System.out.println("---------------------------------最小值---------------------------------------------");
            //min(Comparator c) 返回流中最小值
        System.out.println(employeeList.stream().min((p1, p2) -> Double.compare(p1.getSalary(), p2.getSalary())));//按照员工的salary进行升序排序 min()返回最小值
        //Optional[Employee{id=1008, name='扎克伯格', age=35, salary=2500.32}]

        //内部迭代
        System.out.println("---------------------------------内部迭代---------------------------------------------");
            //forEach(Consumer c)内部迭代Stream API 使用内部迭代——它帮你把迭代做了--使用 Collection 接口需要用户去做迭代，称为外部迭代。
        employeeList.stream().forEach(System.out::println);//遍历流
        //Employee{id=1001, name='马化腾', age=34, salary=6000.38}
        //Employee{id=1002, name='马云', age=12, salary=9876.12}
        //Employee{id=1003, name='刘强东', age=33, salary=3000.82}
        //Employee{id=1004, name='雷军', age=26, salary=7657.37}
        //Employee{id=1005, name='李彦宏', age=65, salary=5555.32}
        //Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}
        //Employee{id=1007, name='任正非', age=26, salary=4333.32}
        //Employee{id=1008, name='扎克伯格', age=35, salary=2500.32}

        //2.归约
        System.out.println("---------------------------------归约---------------------------------------------");
            //reduce(BinaryOperator b) 可以将流中元素反复结合起来，得到一个值。返回 Optional<T>
        Stream<Double> doubleStream1 = employeeList.stream().map(employee -> employee.getSalary());//map()映射出所有员工的工资流
        System.out.println(doubleStream1.reduce(Double::sum));//reduce(初始值,操作数据)将流中的合结合起来得到一个总和
//        System.out.println(doubleStream1.reduce((d1, d2) -> d1 + d2));//手动写的
        //48424.08
            //reduce(T iden, BinaryOperator b) 可以将流中元素反复结合起来，得到一个值。返回 T
        List<Integer> integerList = Arrays.asList(1,2,3,4,5,6,7,8,9,10);
        System.out.println(integerList.stream().reduce(0, Integer::sum));//遍历自然数1-10的和
        //55

        //3.收集
        //collect(Collector c)将流转换为其他形式。接收一个 Collector接口的实现，用于给Stream中元素做汇总的方法
        //Collectors 实用类提供了很多静态方法，可以方便地创建常见收集器实例
//        toList List<T> 把流中元素收集到List
//        List<Employee> emps= list.stream().collect(Collectors.toList());
//        toSet Set<T> 把流中元素收集到Set
//        java.util.Set<Employee> emps= list.stream().collect(Collectors.toSet());
//        toCollection Collection<T> 把流中元素收集到创建的集合
//        java.util.Collection<Employee> emps =list.stream().collect(Collectors.toCollection(ArrayList::new));

        System.out.println("---------------------------------收集---------------------------------------------");
        List<Employee> collect = employeeList.stream().filter(employee -> employee.getSalary() > 6000).collect(Collectors.toList());//将工资大于6000的员工收集于List中
        collect.forEach(System.out::println);
        //Employee{id=1001, name='马化腾', age=34, salary=6000.38}
        //Employee{id=1002, name='马云', age=12, salary=9876.12}
        //Employee{id=1004, name='雷军', age=26, salary=7657.37}
        //Employee{id=1006, name='比尔盖茨', age=42, salary=9500.43}


    }
}

```



## Date|Time API



