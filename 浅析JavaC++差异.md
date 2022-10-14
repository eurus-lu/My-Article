# 浅析Java/C++特性差异

——Java语言基础学习(4.22-4.29)  

## 概述

### 起源

- Java：基于C/C++
- C++：基于C语言

### 预处理命令

- Java：使用improt功能在程序中包括不同的类及其方法，如improt package
- C++：使用头文件的概念在程序中包含不同的库，如# header/# define



### 性能

- Java：开发较为简单，但是由于必须首先在运行时解释代码，因此速度也较慢。
- C++：被编译为二进制文件，因此它可以立即运行，因此比Java程序运行速度更快。

### 中间件

- Java：因开源，具有较多中间件。
- C++：除行业应用类，仅有boost。

### 反编译

- Java：可读性较高，易被破解
- C++：可读性较差

### C/C++ will be better than Java in these cases:

- Footprint (ex: embedded controllers)
- Reboot time (ex: pacemakers)
- Arrays reshaping is hard to do in Java
- Value types
- Direct machine access (ex: device drivers, FPS games)
- Direct code generation
- Destructors versus finalizers
- Destructors versus try/finally

### Java will beat C/C++ in these cases:

- Profiling
- Very large programs
- Garbage collection
- Multi-threading
- Tools for parallel coding and debugging



## 学习过程

- Java：
  - 《函数式编程思维》
  - 企业级开发框架SSM ，数据库MySQL
  - 底层特性 ：JVM虚拟机，并发特性等书籍
- C++：





## 基础语法

### 共同点

- 循环结构，类，定义变量和条件运算符非常相似。
- 程序启动时都会寻找主入口点，即编译器或解释器会查找需要从何处开始执行。
- 同为静态语言，可在编译器中纠错确保安全性 ，运行速度高于动态语言，更适合大型复杂系统。

### 关键字

- Java：

  - byte数据类型，对应C++中的unsigned char
  - interface，对应C++中纯虚函数类

- C++：

  - long long数据类型，8字节，对应Java中的long类型

  - unsigned，无符号概念
  - define，定义宏常量，对应Java全局静态属性

  - 支持structure/union
  - 存储类别auto/extren
  - goto语句

- **Type Semantics**
  - Supports consistent support between primitive and object types
  - Different from primitive and object types

### 关键字

- Java：
- C++：

### 指针

- Java：不支持指针，只能使用值引用来传递值。
- C++：指针是一种C ++构造，允许您直接在内存空间中管理值，此外支持structures、unions、 templates、operator overloading、pointers arithmetic。

### 重载

- Java：仅有方法重载，不支持运算符重载。

- C++：支持函数及运算符重载。

  - 举例：运算符重载以实现两个自定义数据类型相加的运算

  - 关键字 operator+

  ```c++
  Person operator+(const Person& p) {//实现两个类中m_A与m_B分别相加
  	Person temp;
  	temp.m_A = this->m_A + p.m_A;
  	temp.m_B = this->m_B + p.m_B;
  	return temp;
  }
  ```

  

### 析构函数

- Java：无析构函数，GC自动解决对象释放问题
- C++：对象销毁前会自动调用析构函数，可进行手动调用对析构函数进行重写，释放内存

```c++
//析构函数
	~Person() {//析构函数作用:释放堆区数据
		cout << "析构函数!" << endl;
		if (m_height != NULL)
		{
			delete m_height;
			m_height = NULL //防止野指针出现
		}
	}
```

### 虚函数

- Java：
- C++：virtual 支持多重继承

### 运算符

- Java：
  - . 使用单个点限定具有其来源名称空间的类
- C++：
  - :: 范围解析运算符，用于定义类外部的方法，约束类和命名空间，也可用于枚举的声明
  - -> 定义类空间

### 程序处理

- Java：所有方法和数据都驻留在类本身中。使用了概念od包。
- C++：方法和数据可以驻留在类之外。全局文件的概念，可用的命名空间范围

### 注释

- Java：支持文档注释/**  ... */
- C++：不支持文档说明



## 容器



### Library 

- Java：为各种高级服务提供广泛的类
  - 提供了一种将原语转换为它们对应的对象类型的方法，例如使用Integer类对象的整数对象等，并具备自动装修功能
- C++：相对可用，具有低级功能
  - 由于语言非常底层，当程序崩溃时想解决往往要读一些汇编，这时如果使用大量模板，如stl/boost，那么生成的汇编几乎完全不可读，stl源码十分晦涩，若想用一个c++库，不了解这个库的实现原理大概率会出错，c++的复杂度又很难让你理解那个库的原理。



## 泛型编程

### 

### 泛型/模版

- Java：不支持template，但可通过模版方法设计模式（TemplateMethod），基于抽象类的父类为多个子类提供设计模版
- C++：支持template，建立一个通用函数，其函数返回值类型和形参类型可以不具体制定，用一个虚拟的类型来代表。

```c++
template<typename T>
void mySwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}
void test01()
{
	int a = 10;
	int b = 20;
	//1、自动类型推导
	mySwap(a, b);
	//2、显示指定类型
	mySwap<int>(a, b);
}
```

## 面向对象

- Java：纯面向对象
- C++：需要向下兼容C，面向对象不纯粹

### 继承

- Java：不提供多重继承，仅能通过接口
- C++：支持多重继承



### 多态

- Java：Automatic uses static and dynamic binding，提供自动多态，并且可以通过禁止显式方法重写来对其进行限制。
- C++：Explicit for methods supports mixed hierarchies





## 网络

- Java：提供了对Internet的内置支持
- C++：不提供对Internet的内置支持，但支持可用于实现相同目的的套接字编程

## 内存管理

- Java：GC自动过程
- C++：程序员手动过程，易出现程序泄漏及段错误。

### 缓存

- Java：JVM有助于高效的代码优化，因此程序执行的性能优于C ++
- C++：

### 内存安全

- Java：一种内存安全的语言，这意味着如果您尝试在给定的数组参数之外分配值，则程序员会收到错误消息。
  - JVM
  - GC
- C++：将允许程序员在已分配的内存资源之外分配值，但这稍后可能会导致错误和运行时严重崩溃。
  - new/delete  malloc/free
  - 构造/析构 深拷贝/浅拷贝

## 异常

- Java：非原生语言的异常处理都是语言自定义异常

- C++：很多都是操作系统层异常（攻击windows异常处理机制SEH）

  - Windows中，一个简单的try-catch本以为可以抓到try中所有异常，但由于异常处理函数的指针保存在栈上，这时若出现栈溢出可能直接导致异常处理函数指针被覆盖，异常会出现在意想不到的地方。

  - 不推荐使用c++的异常处理 

### 错误检测机制

- Java：系统责任 System’s responsibility
- C++：程序员责任 Programmer’s responsibility

### 异常处理

- Java：使用try-catch必须声明它有可能引发的异常
- C++：无论是否有可能抛出异常，都可以用try-catch尝试排除



## 多线程

### 线程支持

- Java：内置支持线程，拥有java.lang.Thread类。
- C++：无内置支持，需要第三方库。

### 内存安全

- 

### 





## 跨平台

### 解释与编译

- Java：作为一种解释语言，意味着它在执行时被“翻译”为二进制。这使得它可以在任何操作系统上运行，无论它在哪里编写。
- C++：作为一种编译语言，意味着您的程序是在特定操作系统上编译的，并且只能在该特定操作系统上运行。如果要与其他操作系统兼容，则必须在其上编译程序。

### 虚拟机

- Java：有虚拟机，可以使程序编译一次到处执行（可移植性很强），并且内存回收也是在虚拟机里完成的。存在性能损失，虚拟机的启动时间、语言解释时间等
- C++：无虚拟机，到了不同的设备上要重新编译才能执行。

### 界面开发

- Java：
- C++：
  - MFC：只能在windows使用，饱受争议，不同win版本不通用，且文件很大。
  - WTL：只能在windows使用，文件小，多win版本通用。
  - Qt：降低C++开发难度，win装模拟器，linux装qt 写出界面，可通用于win和linux。

## 应用场景与生态

### 应用场景

- Java：
  - 框架技术 Spring/Springmvc/Mybatis/Jpa/Springdata
  - 分布式和微服务架构或技术Dubbo/FastDFS/Springboot/Springcloud/Docker/Zookeeper/RabbitMQ
  - 自动化部署技术K8s/Prometheus/Jenkins/Harbor
  - 大数据Spark/Hadoop 
  - 搜索引擎Elasticsearch
- C++：

### 新生命力注入

- Java：
  - 1.8：函数式编程思维，stream流式表达，lambda表达式
  - 1.9 ：加入模块化特性
  - 1.11 ：ZGC自动内存管理垃圾收集器
- C++：



## Android开发

- Java：用于开发应用程序的基础程序，作为安全性更高的语言，是高级应用程序的首选。
- C++：用于开发硬件和低级程序，如设备驱动程序和网络分析工具。此外，C ++最接近于机器语言，这使得它对于需要快速运行并且需要能够直接与计算机的内存，硬盘驱动器，CPU或其他设备一起工作的软件更加可行，如C ++在需要速度的游戏应用程序中也很常见。
- Kotlin：动态语言，变量不用定义，用起来方便，但相应的也没法通过编译来找出类型错误。开发Android很多时候确实比Java有优势。
- Golang：几乎可以胜任任何不带界面的开发，如Android等so库。



## 总结

--

加入表格

--

- Java配套设施完善，但内存占用有点难看。
- C ++几乎可以用于任何事物，但不一定总是需要使用它。Java通常就足够了，并且可以对您的项目更加有效。
- C++难点：
  - 作为跟C一样的偏底层语言，如果不理解代码背后出了什么问题，永远不知道错在哪 。
  - 一个没有垃圾回收的语言，不用智能指针很容易导致内存泄漏，错误地用了智能指针不但内存泄漏了以后不好解决，还容易导致提前释放问题。
  - 支持强制类型转换，但若转换前后内存结构不一样，很可能导致各种隐性问题。
  - 结论：C++强大，但必须使用的人也强大。如果团队中有不熟悉C++的新手 填坑的时间会比他写代码的时间还要多。此外， C++仍在不断增加特性，不建议新手学C++。

- C/C++一般只用来完成底层高性能模块，几乎所有出现C++的领域都可以用rust代替，大部分出现C++的领域可以用golang代替。