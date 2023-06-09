## 第一部分： 基础知识

------

------

## 第二部分： 面向对象

### 1. 封装

类

```
	对一类事物抽象所得到的一个概念
```

对象

```
一个具体的事物
```

构造函数

```
不能有返回值
方法名与类名相同
可以有多个

默认生成无参无方法体无返回值的构造函数
自已一旦定义，编译器将不再生成默认的构造函数
生成一个类对象是能且只能调用其中的一个构造函数
```

static

```
凡是static修饰的成员都是静态成员
静态成员都是属于类的

非静态的可以静态的
静态的不可以访问非静态的

通过类名只能访问一个类中的非私有静态成员
私有静态成员也不可以通过对象名访问
```

this

```
非静态方法默认都含有一个this指针
this代表正在调用本方法的对象
```

final

```
修饰类：
-该类不能被继承
修饰方法：
-该方法可以被继承但不能被重写
修饰属性：
表示该属性能且只能被赋一次值，赋值方式有两种，并且只能选一种
1. 定义的同时显示的初始化
2. 构造函数的初始化
```

函数重载

```
同名不同参
返回值不能作为是否构成函数重载的依据
```



### 2. 继承

#### 定义

​	子类继承了父类的成员

#### 注意问题：

```
	非私有成员才可以被子类继承
  重写：
    重写方法必须和被重写方法具有相同的方法名称、参数列表、类型相同
    重写方法的访问权限不能小于被重写方法
```



### 3. 多态

#### 定义：

```
同一代码可以随上下文的不同运行不同的操作，俗称多态
即：
	一个父类的引用它既可以指向父类对象也可以指向子类对象
	它可以根据当前时刻指向的不同，自动调用不同对象的方法
```

#### 注意事项：

```
通过父类的引用只能访问子类从父类继承过来的成员
只有在父类的引用本身指向的就是一个子类对象时，我们才可以把父类的引用强制转化为子类的引用。
```

### 相关知识：

#### 	抽象类

```
定义：
如果一个类中没有包含足够的信息来描绘一个具体的对象，这样的类就是抽象类。
抽象类除了不能实例化对象之外，类的其它功能依然存在，成员变量、成员方法和构造方法的访问方式和普通类一样。
由于抽象类不能实例化对象，所以抽象类必须被继承，才能被使用。也是因为这个原因，通常在设计阶段决定要不要设计抽象类。
父类包含了子类集合的常见的方法，但是由于父类本身是抽象的，所以不能使用这些方法。
在 Java 中抽象类表示的是一种继承关系，一个类只能继承一个抽象类，而一个类却可以实现多个接口。
```



```
一个抽象类通常含义抽象方法
只重写了抽象类部分抽象方法的类也必须的被标记为abstract
不可以定义抽象类对象，但是抽象类可以实现多态
```

#### 	接口

```
接口中的方法都是public abstract
不可以定义接口对象，但接口却可以实现多台
重写接口方法时public不能省
举例：
-线程的创建
-事件的处理
-容器的组织方式
-serializable接口
```

------

------



## 第三部分： 高级部分

### 1. 异常

#### 定义

```
运行时的错误
```

#### 分类

```
无法处理的错误
可以处理的异常
	-必须处理的异常
			是Exception子类但是不RuntimeException的子类
	-可处理可不处理的异常
			是RuntimeException的子类
```

#### 注意问题

```java
finally{....}一定会执行
先捕获子类异常，在捕获父类异常，顺序不可颠倒
重写方法抛出异常的范围不能大于被重写方法抛出异常的范围
假设f方法抛出了A异常，则f方法有两种方式处理A异常
	1. throws A
	2. try{...}catch{...}
```

### 2. 线程

#### 定义：

```
一个程序运行时的不同执行路径。
```

#### 创建线程的方式

```
1. 继承Thread类
2. 实现Runnable接口
```

#### 线程的同步

```
多个线程操作同一资源，并且要求这些操作中的若干个操作不能被中断，这时就需要考虑线程同步的问题
线程同步是通过synchronized来实现的、
synchronized可以修饰两种：
	1，代码块
	2，方法(默认锁定的是this)
示例：
	买票
```

#### 线程的通信

```
有时多个线程只有彼此相互协作才可以完成某个功能，这是就需要线程的通信
实现方式：
	wait 和 notify()/notifyAll()
示例：
	生产和消费
```

### 3. 包

#### 包的生产与运行：

```
package 语句必须是第一条语句
类名是包名和类名的组合
只有在整个包的最上层目录才可以运行
```

#### 同包：

#### 不同包的相互访问：

#### jar包的生成与jar包的使用

```
	普通jar包的生成
		jar -cvf 要生成的jar包的名字.jar *
	可运行jar包的生成：
		jar cvfm 要生成的jar包的名字.jar 1.txt *
```

​		

### 4.GUI

#### 容器和组件的关系：

```
容器是组件，但组件不一定是容器
```

#### 常见的布局管理器：

```
BorderLayout   --Frame
FlowLayout     --Panel
GridLayout
```

#### 事件模型：

```
必须要明白哪些操作是编号编译器自动完成的，哪些操作是程序员手动
程序员只需要做两件事：
	告诉事件源可以产生哪些事件
	设计好可以处理这些事件的事件监听器
```

#### 内部类

```
在一个类内部定义的类叫做内部类
内部类的方法可以访问外部类的所有成员
外部类的方法不可以直接访问内部类的所有成员

一定要明白产生内部类的原因：
	如果一个类A要使用B类的所有成员，并且A类不需要被除B以外的其他类访问，则我们可以把A定义为B的内部类
	
	因此几乎不存在直接生成内部类对象的问题
	因此几乎不存在外部类需要访问内部类成员的问题
```

#### 匿名类

```
匿名类是内部类的一种极端表现形式
匿名类可以访问外部类的所有成员和包裹本匿名类方法的final类型的局部变量
```

### 5. IO

#### 定义：

```
如果一个类是用来完成程序和设备之间的数据传输，
```

流和类的关系

分类：

```
输入流   输出流
原始流		包裹流
```

常用流介绍

##### 四大基本抽象流

```
InputStream 		OutputStream
Reader					Writer

字节流和字符流的区别：
	字节流可以处理所有格式的文件
	字符流只能处理文本格式的文件
```

文件流

```
FileInputStream					FileOutputStream
FileReader							FilWriter
```

缓冲流

```
BufferedInputStream						BufferedOutputStream
BufferedReader								BufferedWriter
缓冲流可以提高数据传输的速度
```

转化流

```
OutputStreamWriter					InputStreamReader
例子：
	编程实现把用户从键盘输入的字符保存到一个String对象中
```

数据流

```
DataInputStream							DataOutStream
数据流
例子：
	编程实现
```

Object流

```
ObjectInputStream						ObjectOutputStream
Object流可以把一个对象直接写入或读出
```

### 5. 容器

定义：

```
如果一个类是专门用来存放其他类对象的，则这个类有另外一种特殊的词叫做容器。
```

容器和类的关系：

```
容器一定是类，但类不一定是容器
```

#### Collection 接口

##### Set 接口

```
	无序， 不允许重复
	实现类：
		TreeSet		HashSet
```


List 接口
	有序， 允许重复
	实现类：
		ArrayList		LinkedList

```
	有序， 允许重复
	实现类：
		ArrayList		LinkedList
```

##### List 接口

#### Map 接口

定义：

```
既保存数据本身，也保存数据的主键的一种接口
实现类：
	HashMap		TreeMap
```

##### hashCode() 和 equals() 方法

```

```

##### Collections类

```
该类提供了对Collection 接口实现类的排序，倒置，查找等功能。
```

##### Comparable接口

```
通过该接口的方法可以制订出对象之间比较的标准
凡是需要进行对象的比较排序的场合均可以考虑实现该接口
```

##### Iterator 接口

```
利用该接口提供的方法我们可以遍历所有容器中的元素
```

