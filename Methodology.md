# Methodology

## High-quality code

`Maintainability`可**维护性**

`Reusability`可**复用性**

`Flexibility`/`Scalability`/`Extensibility`可**扩展性**

`Understandability`/`Readability`**可读性**

`Testability`可**测试性**

`High Cohesion Loose Coupling`**高内聚低耦合**

## Design Principle

S	`Single-Responsibility-Principle`	**单一职责**原则

O	`Open-Close-Principle`	**开闭**原则

L	`Liskov-Substitution-Principle`	**里氏替换**原则

I	`Interface-Segregation-Principle`	**接口隔离**原则

D	`Dependency-Inversion-Principle`	**依赖倒置**原则



`Low-Of-Demeter`	**迪米特法则**

`Composition/Aggregation-Reuse-Principle`	**组合复用**原则



### Single-Responsibility Principle

**单一职责**原则

> A class should **have one and only one reason to change**, meaning that **a class should have only one job.**
>
> **控制类的粒度 一个类只负责一份工作 对对象解耦提高其内聚性**

![image-20230206105136172](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206105136172.png)

### Open-Closed Principle

**开闭**原则

> Objects or entities should be **open for extension** but **closed for modification.**
>
> **对扩展开放 对修改关闭**

![image-20230206105116707](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206105116707.png)

### Liskov Substitution Principle

**里氏替换**原则

> Let q(x) be a property provable about objects of x of type T. Then q(y)  should be provable for objects y of type S where S is a subtype of T.
>
> **继承**必须**确保超类所拥有的性质(属性和方法)**在**子类中仍然成立**；（**继承后避免重写父类的方法** 而是**采用扩展方法的形式** **确保子类能完全替代父类**）

![image-20230206105051403](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206105051403.png)

### Interface Segregation Principle

**接口隔离**原则

> A client should never be forced to implement an interface that it  doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.
>
> 要**为各个类建立它们需要的专用接口**

### Dependency Inversion Principle

**依赖倒置**原则

> Entities must depend on abstractions, not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on abstractions.
>
> 要**面向接口编程**，不要面向实现编程

![image-20230206105547597](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206105547597.png)

### Low-Of-Demeter

**迪米特法则**

> Each unit should have only limited knowledge about other units: only units “closely” related to the current unit. Or: Each unit should only talk to its friends; **Don’t talk to strangers.**
>
> **只和"直接朋友"谈 不和"陌生人"谈**

![image-20230206105654903](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206105654903.png)

### Composition/Aggregation-Reuse-Principle

**组合复用**原则

> Inheritance should only be used when subclass is a superclass. Don t use inheritance to get code reuse. If there is no is a relationship, then use composition for code reuse.
>
> 尽量**先使用组合和聚合等关系**；**其次才考虑继承关系实现**

![image-20230206111036380](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206111036380.png)

## Design Pattern

https://javadoop.com/post/design-pattern

![image-20230327110324675](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230327110324675.png)

### Creational patterns

> These patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.
>
> **创建型模式：关于如何创建实例**

- 工厂方法模式-Factory Method pattern
- 抽象工厂-Abstract Factory
- 建造者模式---Builder pattern
- 单例模式-Singleton pattern
- 原型模式-Prototype pattern

#### 单例模式-Singleton pattern

> **Singleton** is a creational design pattern that lets you  ensure that a class has only one instance, while providing a global  access point to this instance.
>
> 单例模式试图解决的两个基本问题：**全局访问**和**实例化控制(线程安全控制)**，**公共静态属性**为访问实例**提供了一个全局访问点**

![image-20230206113544047](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206113544047.png)

![image-20230206121324459](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206121324459.png)

##### 懒汉式-线程不安全

> 好处：私有静态变量 uniqueInstance 被**延迟实例化**，这样做的好处是，如果**没有用到该类，那么就不会实例化 uniqueInstance**，从而**节约资源**
>
> 
>
> 弊端：这个实现在**多线程环境下是不安全的**，如果多个线程能够同时进入 `if (uniqueInstance == null)` ，并且此时 uniqueInstance 为 null，那么会有多个线程执行 `uniqueInstance = new Singleton();` 语句，这将**导致多次实例化 uniqueInstance**。

```java
public class Singleton {

    private static Singleton uniqueInstance;//私有静态属性 懒汉式很懒 先不new实例

    private Singleton() {//私有构造方法
    }

    public static Singleton getUniqueInstance() {//公共静态方法获取实例
        if (uniqueInstance == null) {//非空判断并new实例
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```

##### 饿汉式-线程安全

> 好处：采取**直接实例化** uniqueInstance 的方式就**不会产生线程不安全问题**
>
> 
>
> 弊端：**丢失了延迟实例化带来的节约资源的好处。**

```java
public class Singleton {

    private static Singleton uniqueInstance = new Singleton();//私有静态属性 饿汉式直接new实例

    private Singleton() {//私有构造方法
    }

    public static Singleton getUniqueInstance() {//公共静态方法获取实例
        return this.uniqueInstance;//直接返回实例
    }
}
```

##### 懒汉式完善-线程安全

> 好处：对 getUniqueInstance() 方法**加锁**，在一个时间点只能有一个线程能够进入该方法，避免了多次实例化 uniqueInstance 的问题。**解决线程安全问题**
>
> 
>
> 弊端：当一个线程进入该方法之后，其它试图进入该方法的线程都必须等待，因此**性能上有一定的损耗。**

```java
public class Singleton {

    private static Singleton uniqueInstance;//私有静态属性 懒汉式很懒 先不new实例

    private Singleton() {//私有构造方法
    }

    public static synchronized Singleton getUniqueInstance() {//公共静态方法获取实例 加锁保证线程安全
        if (uniqueInstance == null) {//非空判断并new实例
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```

##### 双重校验锁-线程安全 volatile限制指令重排

> 好处：uniqueInstance 只需要被实例化一次，之后就可以直接使用了。**加锁操作只需要对实例化那部分的代码进行即可**，只有当 uniqueInstance 没有被实例化时，才需要进行加锁。**性能相对于方法sync锁略优** 先判断 uniqueInstance 是否已经被实例化，如果没有被实例化，那么才对实例化语句进行加锁
>
> 同时对象属性上**添加volatile避免底层指令重排** 导致占用虚空内存
>
> 弊端：编写略繁琐

```java
public class Singleton {

    private volatile static Singleton uniqueInstance;//volatile避免底层指令重排 导致占用虚空内存

    private Singleton() {
    }

    public static Singleton getUniqueInstance() {
        if (uniqueInstance == null) {//先判断 uniqueInstance 是否已经被实例化，如果没有被实例化，那么才对实例化语句进行加锁
            synchronized (Singleton.class) {//加锁操作只需要对实例化那部分的代码进行
                if (uniqueInstance == null) {//双重校验 非空判断并new实例
                    uniqueInstance = new Singleton();
                }
            }
        }
        return uniqueInstance;
    }
}
```

##### 静态内部类实现

> 不仅具有延迟初始化的好处，而且由虚拟机提供了对线程安全的支持

```java
public class Singleton {

    private Singleton() {
    }

    private static class SingletonHolder {//当 Singleton 类加载时，静态内部类 SingletonHolder 没有被加载进内存。
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getUniqueInstance() {//触发SingletonHolder.INSTANCE时SingletonHolder才会被加载
        return SingletonHolder.INSTANCE;//初始化 INSTANCE 实例。
    }
}
```

##### 枚举实现

> **解决序列化**和**反射攻击**很麻烦，而枚举实现不会出现这两种问题，所以说**枚举实现单例模式是最佳实践**。
>
> **如果不使用枚举来实现单例模式**，**会出现反射攻击**，因为**通过 setAccessible() 方法可以将私有构造函数的访问级别设置为 public**，然后调用构造函数从而实例化对象。如果要防止这种攻击，需要在构造函数中添加防止实例化第二个对象的代码。

```java
public enum Singleton {
    uniqueInstance;
}
```

```java
public class Singleton implements Serializable {

    private static Singleton uniqueInstance;

    private Singleton() {
    }

    public static synchronized Singleton getUniqueInstance() {
        if (uniqueInstance == null) {
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```

#### 原型模式-Prototype pattern

> Also known as: Clone；**Prototype** is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.
>
> 原型模式(Prototype)，使用原型实例指定要创建对象的类型，通过复制这个原型来创建新对象
>
> 原型模式其实就是从一个对象再创建另外一个可定制的对象，而且不需知道任何创建的细节。

![image-20230206121100948](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206121100948.png)

![image-20230206122023719](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206122023719.png)

```java
//原型类
public abstract class Prototype {
    abstract Prototype myClone();
}
```

```java
//具体原型类
public class ConcretePrototype extends Prototype {

    private String filed;

    public ConcretePrototype(String filed) {
        this.filed = filed;
    }

    @Override
    Prototype myClone() {
        return new ConcretePrototype(filed);
    }

    @Override
    public String toString() {
        return filed;
    }
}
```

```java
public class Client {
    public static void main(String[] args) {
        Prototype prototype = new ConcretePrototype("abc");
        Prototype clone = prototype.myClone();
        System.out.println(clone.toString());
    }
}
```

#### 工厂方法模式-Factory Method pattern

> **Factory Method** is a creational design pattern that  provides an interface for creating objects in a superclass, but allows  subclasses to alter the type of objects that will be created.
>
> 工厂方法(Factory Method)，它**定义了一个创建对象的接口**，但由**子类决定要实例化哪个类**。工厂方法**把实例化操作推迟到子类**
>
> 
>
> 简单工厂模式（违背了开闭原则）工厂类中包含了必要的逻辑判断，根据客户端的选择条件动态实例化相关的类
>
> 
>
> 工厂方法模式变成了一个工厂抽象接口和多个具体生成对象的工厂，于是我们要增加‘求M数的N次方’的功能时，就不需要更改原有的工厂类了，只需要增加此功能的运算类和相应的工厂类就可以了。

![image-20230206142719864](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206142719864.png)

![image-20230206142746290](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206142746290.png)

```java
public abstract class Factory {
    abstract public Product factoryMethod();
    public void doSomething() {
        Product product = factoryMethod();
        // do something with the product
    }
}
public class ConcreteFactory extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct();
    }
}
public class ConcreteFactory1 extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct1();
    }
}
public class ConcreteFactory2 extends Factory {
    public Product factoryMethod() {
        return new ConcreteProduct2();
    }
}
```

#### 抽象工厂-Abstract Factory

> **Abstract Factory** is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.
>
> 抽象工厂(Abstract Factory)，抽象工厂模式创建的是对象家族，也就是很多对象而不是一个对象，并且这些对象是相关的，也就是说必须一起创建出来。而工厂方法模式只是用于创建一个对象，这和抽象工厂模式有很大不同

![image-20230206122845235](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206122845235.png)

![image-20230206124147267](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206124147267.png)

```java
public class AbstractProductA {//抽象产品
}
public class AbstractProductB {//抽象产品
}
public class ProductA1 extends AbstractProductA {//抽象产品的具体实现
}
public class ProductA2 extends AbstractProductA {//抽象产品的具体实现
}
public class ProductB1 extends AbstractProductB {//抽象产品的具体实现
}
public class ProductB2 extends AbstractProductB {//抽象产品的具体实现
}
public abstract class AbstractFactory {//抽象工厂
    abstract AbstractProductA createProductA();
    abstract AbstractProductB createProductB();
}
public class ConcreteFactory1 extends AbstractFactory {//具体的工厂
    @Override
    AbstractProductA createProductA() {
        return new ProductA1();
    }
	@Override
    AbstractProductB createProductB() {
        return new ProductB1();
    }
}
public class ConcreteFactory2 extends AbstractFactory {//具体的工厂
    @Override
    AbstractProductA createProductA() {
        return new ProductA2();
    }
	@Override
    AbstractProductB createProductB() {
        return new ProductB2();
    }
}
public class Client {
    public static void main(String[] args) {
        AbstractFactory abstractFactory = new ConcreteFactory1();
        AbstractProductA productA = abstractFactory.createProductA();
        AbstractProductB productB = abstractFactory.createProductB();
        // do something with productA and productB
    }
}
```

#### 建造者模式-Builder pattern

> **Builder** is a creational design pattern that lets you  construct complex objects step by step. The pattern allows you to  produce different types and representations of an object using the same  construction code.
>
> 建造者(Builder)，封装一个对象的构造过程，并允许按步骤构造

![image-20230206143928164](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206143928164.png)

![image-20230206153744425](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230206153744425.png)

```java
public class AbstractStringBuilder {//建造者
    protected char[] value;

    protected int count;

    public AbstractStringBuilder(int capacity) {
        count = 0;
        value = new char[capacity];
    }

    public AbstractStringBuilder append(char c) {
        ensureCapacityInternal(count + 1);
        value[count++] = c;
        return this;
    }

    private void ensureCapacityInternal(int minimumCapacity) {
        // overflow-conscious code
        if (minimumCapacity - value.length > 0)
            expandCapacity(minimumCapacity);
    }

    void expandCapacity(int minimumCapacity) {
        int newCapacity = value.length * 2 + 2;
        if (newCapacity - minimumCapacity < 0)
            newCapacity = minimumCapacity;
        if (newCapacity < 0) {
            if (minimumCapacity < 0) // overflow
                throw new OutOfMemoryError();
            newCapacity = Integer.MAX_VALUE;
        }
        value = Arrays.copyOf(value, newCapacity);
    }
}
public class StringBuilder extends AbstractStringBuilder {//具体建造者
    public StringBuilder() {
        super(16);
    }

    @Override
    public String toString() {
        // Create a copy, don't share the array
        return new String(value, 0, count);
    }
}
public class Client {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        final int count = 26;
        for (int i = 0; i < count; i++) {
            sb.append((char) ('a' + i));
        }
        System.out.println(sb.toString());
    }
}
/*
console ：
abcdefghijklmnopqrstuvwxyz
*/
```

### Structural patterns

> These patterns explain how to assemble objects and classes into larger  structures while keeping these structures flexible and efficient.
>
> **结构型模式：关于类及对象的复合关系**

- 适配器模式-Adapter pattern
- 桥接模式-Bridge pattern
- 装饰模式-Decorator
- 外观模式-Facade pattern
- 享元模式-Flyweight pattern
- 代理模式-Proxy pattern
- 组合模式-Composite pattern

### Behavioral patterns

> These patterns are concerned with algorithms and the assignment of responsibilities between objects.
>
> **行为型模式：对象之间如何通讯**

- 命令模式-Command pattern
- 中介者模式-Mediator pattern
- 观察者模式-Observer pattern
- 状态模式-State pattern
- 策略模式-Strategy pattern
- 责任链模式-Chain-of-responsibility pattern
- 解释器模式-Interpreter pattern
- 迭代器模式-Iterator pattern
- 备忘录模式-Memento pattern
- 模板方法模式-Template method pattern
- 访问者模式-Visitor

## Distributed Theory

### CAP

### BASE