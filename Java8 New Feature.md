# Java8 New Feature

## Lambda表达式

### 概述

Lambda表达式是Java8新增的特性；（语法糖）。可以对**匿名内部类**的写法进行简化。

**针对的是函数式接口（只有一个抽象方法的接口）**

不用关系是什么对象进行操作 而是关注对数据的操作

### 核心原则

（参数类型）可推导 可省略

只关心参数和具体的操作

### 基本格式

```java
（参数列表） -> {代码操作}
```

### Lambda表达式省略规则

- 参数类型可以省略（可推导）
- 方法体只有一个return时 {} return ； 都可省略
- 方法只有一个参数时小括号可以省略

### Instance

可以先写匿名内部类的形式 再将代码修改成lambda表达式的形式 多多益善

```java
public static void main(String[] args) {
        new Thread(() -> System.out.println("这里是实现Runnable接口的run方法")).start();
    
//--------------------------------------------------------------------------------------        
        new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("这里是实现Runnable接口的run方法")
            }
        }).start();
    }
```

### 引用final的外层局部变量

![image-20230119224903766](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20230119224903766.png)

## Stream流

### 概述

Java8中Stream使用的是函数式编程的模式；用来对集合或者数组进行链状流形式的操作。

便利我们对数组和集合的操作

    1 . 不是数据结构，不会保存数据。
    
    2. 不会修改原来的数据源，它会将操作后的数据保存到另外一个对象中。（保留意见：毕竟peek方法可以修改流中元素）
    
    3. 惰性求值，流在中间处理过程中，只是对操作进行了记录，并不会立即执行，需要等到执行终止操作的时候才会进行实际的计算。

### Stream操作

**必须要有终结操作 中间操作的代码才会生效**

#### 创建Stream

***单列集合* `集合对象.stream()`**

```java
List<User> users = getUsers();//创建一个单列集合

//创建Stream
Stream<User> stream = users.stream();
```

***双列集合* 转换成两个单列集合后再创建**

```java
Map<String,Integer> map = new HashMap<>();
map.put("Eddie",22);
map.put("James",38);
map.put("Irving",33);

//转换成两个单列集合后再创建
Stream<Map.Entry<String,Integer>> stream = map.entrySet().stream();
```

***数组* `Arrays.stream(arr) 或者 Stream.of(arr)`**

```java
Integer [] arr = new Integer[]{11,51,1};

Stream<Integer> stream = Arrays.stream(arr);
Stream<Integer> stream1 = Stream.of(arr);
```

#### 中间操作

##### filter

可以对流中的元素进行条件过滤，符合过滤条件的才能继续留在流中

```java
List<User> users = getUsers();//单列结合对象

//打印age大于18的人员name
users.stream()
	 .filter(user -> user.getAge() > 18)//过滤操作进行条件判断 符合过滤条件的才能继续留在流中
	 .forEach(user -> System.out.println(user.getName()));
```

##### map

对流中的数据元素进行计算或者转换

```java
public static void main(String[] args) {
        List<Employee> employees = new ArrayList<>();
        employees.add(new Employee(1,"Eddie",22,25345.1d));
        employees.add(new Employee(2,"James",38,2534515135153.1d));
        employees.add(new Employee(3,"Eddie",33,253442443415.1d));

        employees.stream()
                .filter(employee -> employee.getAge() > 18)
                .map(employee -> employee.getName())//类型进行转换
                .map(username -> "map进行数据操作\t" + username)//进行数据的运算操作
                .forEach(System.out::println);
    }
```

![image-20221218160150972](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218160150972.png)

![image-20221218161028779](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218161028779.png)

##### distinct

去重操作

distict是**依赖Objec中的 equals() 方法来判断对象是否相同的**。所有**需要重写equals方法**

![image-20221218161528780](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218161528780.png)

##### sorted

对流中的数据元素进行排序（空参的需要流中的数据元素可比较实现了@Comparable接口）

![image-20221218162517544](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218162517544.png)

![image-20221218163001012](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218163001012.png)

![image-20221218163031865](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218163031865.png)

![image-20221218163230537](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218163230537.png)

##### limit

设置流的最大长度（限制作用）超出的部分将被抛弃

![image-20221218163427418](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218163427418.png)

##### skip

跳过流中的前n个元素，返回剩下的(如果	n	>=	总元素	则返回null)

![image-20221218163702066](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218163702066.png)

##### flatMap

flatMap能够将一个对象**转换成多个对象作为流的元素**（一个转多个）

区别于map----map只能将一个对象转换成另一个对象来作为流的元素。（一个转一个）

![image-20221218180854993](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218180854993.png)

![image-20221218180959885](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218180959885.png)

#### 终结操作

使用Stream一定要使用终结操作；中间操作才会执行

##### forEach

对流中的数据元素进行遍历操作 ；我们通过传入的参数去指定对遍历到的元素进行具体的（输出/运算输出）操作

![image-20221218181500008](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218181500008.png)

##### count

（计数）获取当前流中的数据元素的个数

![image-20221218181840942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218181840942.png)

##### max&min

取最值（最大值&最小值）

![image-20221218192832728](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218192832728.png)

##### collect

把流中的数据元素转换成集合

**转换成List**

![image-20221218193359736](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218193359736.png)

**转换成Set**

![image-20221218193437073](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218193437073.png)

**转换成Map**

要指定	转换成key	转换成value	的规则

注意 转换成key的时候一定要确保**key值不能重复**（key值要去重）

![image-20221218194729048](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218194729048.png)

![image-20221218194430541](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218194430541.png)

##### reduce归并

对流中的数据按照指定的计算方式计算出一个结果（缩紧操作）

把stream中的元素组合起来，我们传入一个初始值，它会按照我们的计算方式依次拿流中的元素和在初始化值的基础上进行计算，计算结果再和后面的元素进行计算。

**两个参数的重载方法**

自己指定初始化值以及运算逻辑

![image-20221218204325368](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218204325368.png)

![image-20221218204108542](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218204108542.png)

![image-20221218203330084](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218203330084.png)

**一个参数的重载方法**

拿stream中的第一个元素作为初始值 只需定义运算逻辑

![image-20221218205129738](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218205129738.png)

```

     boolean foundAny = false;
     T result = null;
     for (T element : this stream) {
         if (!foundAny) {
             foundAny = true;
             result = element;
         }
         else
             result = accumulator.apply(result, element);
     }
     return foundAny ? Optional.of(result) : Optional.empty();
 
```

**三个参数的重载方法**

#### 查找与匹配

##### anyMatch

是否有任意一个元素符合匹配条件（返回boolean类型）

##### allMatch

是否全部都符合匹配条件（返回boolean类型）

##### noneMatch

是否都不符合匹配条件 若都不符合返回true（返回boolean类型）

##### findAny

获取流中的任意一个元素（无法保证获取的是流中的第一个元素）

随机抽取一名幸运元素

##### findFirst

获取流中的第一个元素

### Stream的注意事项

1. 不是数据结构，不会保存数据。（流是一次性的）

2. 不会修改原来的数据源，它会将操作后的数据保存到另外一个对象中。（保留意见：毕竟peek方法可以修改流中元素）

3. 惰性求值，流在中间处理过程中，只是对操作进行了记录，并不会立即执行，需要等到执行终止操作的时候才会进行实际的计算。

## Optional

更优雅的**避免空指针异常`NullPointException`**

```java
if(data != null){
	System.out.println(data.info());
}
```

Optional类似于包装类；可以将我们具体的数据封装进Optional对象内部。

然后我们去使用Optional中封装好的数据就可以优雅的避免空指针异常了

### 使用

#### 创建对象

一般使用Optional的静态方法**ofNullable()**来把数据封装成一个Optional对象

无论传入的参数是否为null都不会出现`NullPointException`

```java
Author author = getAuthor();
Optional<Author> = Optional.ofNullable(author);
```

如果其中的**数据为null** 则**不会执行后续的消费代码**

![image-20221218215046702](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218215046702.png)

#### 安全消费值

获取了Optional对象后进行使用；

调用`ifPresent()`方法来消费其中的数据

如果其中的**数据为null** 则**不会执行后续的消费代码**

```java
Optinal<Data> dataOptional = Optional.ifNullable(getData());
dataOptional.ifPresent(data -> System.out.println(data.getInfo()));//若数据为null 则不会执行后续操作
```

#### 安全获取值

```java
.orElseGet()//数据为null则返回我们指定的值 数据不为null 则返回数据
```

![image-20221218215617303](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218215617303.png)

```java
orElseThrow()//如果数据不为null 则获取该数据 如果为null则根据我们指定的异常进行抛出
```

![image-20221218220922601](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218220922601.png)

#### 过滤

```java
.filter()//根据指定的过滤条件进行过滤 若不满足则返回一个新的Optional.empty对象
```

![image-20221218221610548](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218221610548.png)

#### 判断

```java
isPresent()//判断数据是否存在（返回值为boolean类型）
```

![image-20221218221914040](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218221914040.png)

![image-20221218222121365](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218222121365.png)

#### 数据转换

`.map()`//根据定义的规则对数据进行转换

![image-20221218222303506](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221218222303506.png)

## 函数式接口

## 方法引用

## 高级方法