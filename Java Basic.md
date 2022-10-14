# **Java 入门**

## 基础常识

[Markdown语法](https://www.jianshu.com/p/191d1e21f7ed)


### 人机交互界面
- 图形化界面(Graphical User Interface, GUI)
- 命令行方式(Command Line Interface, CLI)

### 常用DOS命令
[terminal常用命令](https://www.jianshu.com/p/f79c3c77935f)
- touch 创建文件
- open 打开文件
- rm 删除目录/文件



### 第三代程序语言
- C/Pascal/Fortran 面向过程
- C++ 面向过程/对象
- Java 跨平台纯面向对象
- .NET 跨语言平台

### Java语言特点
- 继承C++语言面向对象技术核心 强制面向对象 
   - 面向对象优势 在抽象层面分析问题 实现上可极大的复用之前代码
- 舍弃C语言中容易引起错误的指针/运算符重载/多重继承等特性
- 增加了垃圾回收功能 释放不再使用的引用对象内存
- JDK5.1引入泛型编程/类安全的枚举/不定长参数/自动装拆箱 
- 分布式：拥有JavaNet/RMI
- 健壮性：强类型机制/异常处理/垃圾自动回收等
- 安全性：防止恶意代码攻击的安全机制
- 跨平台性：体系结构中立.class可在任何系统中运行（Java Virtual Machine, JVM）
- 解释型：先编译后解释
- 性能略高：相较于解释型的高级脚本语言 较于C/C++内存回收不及时
- 原生支持多线程


##### android平台应用
- android开发水平的高低很大程度取决于Java语言核心能力是否扎实

### Java技术体系平台
- Java SE（Standard Edition）支持面向桌面级应用 提供完整的Java核心API
- Java EE（Enterprise Edition）为开发企业环境下的应用程序提供一套解决方案
- Java ME（Micro Edition）支持移动终端平台运行
- Java Card 支持Java Applets运行在小内存设备平台

### Java核心机制
- 虚拟机（Java Virtual Machine, JVM）层次：用户-字节码文件-JVM-操作系统-硬件
- 垃圾回收机制（Garbage Collection, GC）开了一个系统集线程自动检测

### JDK/JRE
- JDK(Java Development Kit)Java开发工具包：包含Java开发工具——JRE/编译工具javac.exe/打包工具jar.exe等
- JRE(Java Runtime Environment)Java运行环境：包含JVM/核心类库等

### 通过terminal.app/dos写测试案例
- touch text.java 创建文件
- open text.java 打开文本文件
- 输入hellow world代码保存

```
public class Text{
	public static void main(String[] args){
		System.out.print("hello world");
	}

}
```

- javac text.java 进行编译
- java text 即可运行

### 注释习惯
```
/**
*文档注释 在文档开头l
*@作者
*@版本号
*/
/*多行注释*/
//单行注释	
```

## Android Studio 运行Java程序测试
- 创建empty activity
- 右键主项目名-New-Module-Java or Kotlin Library
- 路径 主程序名/lib/src/main/java/com.example.lib/新建java程序名
- 运行点击代码栏左边运行键

## 基本语法

### 关键字
- 较为陌生 interface/enum/byte/default
- 保留字 可能在未来版本中成为关键字 byValue/cast/future/generic/inner/operator/outer/rest/var/goto/const

### 软件开发程序
- IDEA/eclipse/vscode

### 命名规范
- 包名 所有字母小写 xxxyyyzzz
- 类名/接口名 首字母大写 XxxYyyZzz
- 变量名/方法名 第一个单词首字母小写随后单词首字母大写 xxxYyyZzz
- 常量名 所有字母大写下划线连接单词 XXX_YYY_ZZZ

### 变量
- 先声明后使用
- 初始化必须赋值
- 大括号范围为局部变量作用域
- 通过变量名访问内存中的存储区域

### 数据类型
- 基本数据类型仅有8种：
   - 整数数据类型（1字节=8比特/bit）
      - byte	1字节 -128～127
	  - short	2字节 -2^15~2^15-1
	  - int		4字节 -2^31~2^31-1
	  - long	8字节 -2^63~2^63-1 ~~（注意 该类型变量赋值需在数字末尾加字母L）~~
   - 浮点类型
	  - float 4字节 -2^128~2^128-1 7位有效数字（注意 该类型变量赋值需在数字末尾加字母f)
	  - double 8字节 -2^1024~2^1024-1 14位有效数字
      - 注意 浮点常量两种表示形式
         - 必须有小数点 5.12 512.0f .512
         - 科学计数法形式 5.12e2 512E2 100E-2
   - 字符类型
	  - char 2字节 英文单引号扩起来的单个字符 ‘n’
	  - 转义字符 单引号反斜杠 \b \n \r \t \\" \\' \\\
   - 布尔类型
	  - 与C语言区别 不可用0和1替代 只能用true和false 无null
- 引用类型
   - 该类型初始化时都可以赋值为null
   - 类 class
   - 接口 interface
   - 数组 []

```
//String类 介绍与c/c++差异
//内存中在字符串常量池中只会出现一个hello 其地址被s1 s2共同引用
	String s1="hello";
	String s2="he“+”ll“+”o";
```

### 数据类型补充
- 自动类型转换 
   - 容量小的类型可自动转换为容量大的类型 
   - byte/char/short之间不可相互转换 运算转换为int后进行运算 两个相同类型相加结果也为int型
   - char和数字相加为其对应ascii码数值相加
   - 任何基本类型和字符串相加自动转换为字符串类型
   - 多类型求和有从左到右的优先顺序
- 强制类型转换(小括号)
   - 将容量大的数据类型转换为容量小的类型
   - 容易造成精度降低或溢出
   - 字符串不能直接转换基本类型 需通过包装类转换 如Integer.parseInt()
   - bool 类型不可以转换为其他数据类型

```
	int i=1;
	byte j=(byte)i;
	String a="12";
	int i=Integer.parseInt(a);
	i=2147483647;//2^15-1
	System.out.println(i+20);//不报错 结果为-2147483630 溢出
```

### 运算符
- 算数运算符
   - % 取模运算符 结果符号与被除数相同
- 赋值运算符
   - = 赋值顺序为从右到左 可以连续赋值
   - 拓展赋值运算符 -= += *= /= %= 会进行强制类型转换为当前类型
- 比较运算符
   - 比较运算符结果都是boolean型
- 逻辑运算符
   - ^ 异或运算符 不作为指数符号
   - || 短路与 相较于| 左边为真 右边不参与运算
   - && 短路或 相较于& 左边为假 右边不参与运算
- 位运算符
   - 补码 负数的二进制=反码+1 
   - \>> 负数右移最高位补1
   - \>>> 无符号右移 右移后最高位补0 不存在无符号左移
   - ~ 反码 如 ~6=-7
- 三目/三元运算符
   - （条件表达式）？ 表达式1：表达式2

### 运算符补充
- 优先级  从上到下为从高到低 常用小括号提升优先级
```
   - () []
   - ! + - ~ ++ -- //从右到左
   - * / %
   - + -
   - << >> >>>
   - < >= > >= instanceof
   - == !=
   - &
   - ^
   - |
   - &&
   - ||
   - ?:  //从右到左
   - = += -= *= /= %= &= |= ^= ~= <<= >>= >>>=  从右到左 
```
- 运算方向 只有单目/三目/赋值运算符从右向左 其余均为从左向右

### 程序流控制
- 顺序结构 定义成员变量采用合法的向前引用
- 分支语句 if-else/switch-case-default-break
   - switch 若不加break则从匹配位置运行到最后
   - switch 只能判断byte/short/char/int/enum/String 而if只要结果boolean均可使用
- 循环结构
   - for循环 for(;;){}
   - while循环 while(){}
   - do-while循环 do{}while();
   - 代码规范
	  - 嵌套循环尽量外层循环次数小于内层循环次数
- 特殊流程控制语句
   - break/continue
   - return 用于结束方法 return生效后下方代码不再执行

### 数组
- 声明方式 type[] var;/type var[];
- 初始化
   - 动态 声明数组大小 不赋值 对象初始化默认值为null
   - 静态 直接赋值 值数量确定数组大小
```
	int[] arr = new int[3];//默认初始化为0
	int[] a = new int[]{3,9,8};//引用下标从0开始
```
- 多维数组初始化
```
//动态
int[][] arr = new int[3][2];
int[][] arr = new int[3][];
//int[][] arr = new int[][2];//非法
//静态
int[][] arr = new int[][]{{1,2,3},{4,5},{6,7,8,9}};
//数组长度
int len = arr.length;//多维数组总元素个数
int len = arr[i].length;//二维数组第一列元素个数
```
   - 特殊写法 int[] x,y[];//x一维 y二维
   - Java数组不必都为规则矩阵形式
- 数组运算中赋值需遍历
- 数组常见异常（编译不报错运行报错） 数组下标越界异常/空指针异常

## 面向对象编程

### 基础思维
- 类和类的成员
   - 属性 成员变量 Field
   - 行为/成员方法 函数 Method
- 类语法和格式
```
修饰符class类名{
	属性声明；//可先声明不用初始化 默认值null或0
	方法声明；//驼峰命名 有返回值方法数据类型与方法定义需一致
}
```
- 类的实例化 使用new关键字 采用 对象名.对象成员 进行访问
- 属性修饰符 
   - private/public/protected 对应实例变量 存在堆中 前者只能由该类的方法访问 
   - static 对应类变量 不需要类实例化对象就可使用 类名.静态对象成员
- 局部变量 形参/方法局部变量/代码块局部变量
   - 无默认值必须显式初始化 不指定权限修饰符
   - 存在栈中 作用范围结束自动释放
- 方法 Method
   - 只有被调用的时候才被执行
   - 不可在方法内部定义方法 同一类中可以直接调用方法无需new
- 对象
   - char 默认初始值为'\u0000' 表示为空 boolean-false long-0.0L float-0.0F double-0.0D
   - 匿名对象 不用把创建对象赋值 用于 只需进行一次方法调用/作为实参传递给一个方法调用 的场景
```
new Student().showInfo();//匿名对象
//上下等同；
Student s = new Student();
Student.showInfo();
```
- 类的访问机制 类中static方法不可访问非static成员变量
- 方法重载 同名方法参数个数或参数数据类型不相同即可
- **可变参数传递**

```
//法1 用数组方式传递
public void printInfo(String[] args){
	for(int i=0;i<args.length;i++){
		System.out.println(args[i]);
	}
}
p1.printInfo(null);//无参调用与法2有区别 需加null

//法2 Java特有的...方式
public void printInfo(String s,int... args){}
//若有多个参数 可变参数声明放在最后
p2.printInfo();//无参调用
```
- Java传参机制只有一种 值传递 即变量在栈内存中的值 基本数据类型即为对应实参值 对象则为对应堆中的地址
- JVM内存区域
   - 堆heap 所有对象 包括自己定义的对象和字符串对象
   - 栈stack 基础数据类型和对象的引用/地址
   - 方法区 所有的class和static变量
- 包 package 
   - 类似于文件夹 用于解决命名冲突问题（不同包允许同名文件）并归类 
   - 运用.可以进行多层次建包 包名通常用小写字母
   - import 引包 在代码首部输入.路径 若使用同一个包下的类可以省略
```
import a.b.*//a.b包中全量引

a.b.C text = new a.b.C();//可不用import
```
- JDK主要包介绍
   - java.lang 包含一些核心类 如String/Math/Integer/System/Thread
   - java.net 包含执行与网络相关操作的类和接口
   - java.io 包含提供多种输入/输出功能的类
   - java.util 包含一些实用工具类 如定义系统特性/接口集合框架类/使用与日期日历相关函数
   - java.text 包含一些格式化相关类
   - java.sql 包含进行JDBC数据库编程的相关类/接口
   - java.awt 包含构成抽象窗口工具集(abstract window toolkits)的多个类 该类用于构建和管理GUI
   - java.applet 包含applet运行所需的一些类
### 封装 Encapsulation
- private 变量声明私有 类内部可使用
   - 隐藏类中不需要对外提供的细节
   - 使用getXxx()/setXxx()方法实现对属性操作 限制不合理操作
   - 便于修改 增强代码可维护性
- default（缺省） 类内部/同一个包可使用
- protected 类内部/同一个包/子类可使用
- public 任何地方均可使用
- class的权限修饰仅有public和default两种 同一个文件中可以有多个class 但只允许有一个public
- 构造器 new对象的根本原理 通过类的构造方法
   - 默认为隐式无参构造器 默认构造器的修饰符与所属类一致
   - 显式定义一个（无参）/多个（有参）构造器 存在显式系统不再提供默认构造器
   - 一个类可创建多个重载的构造器 为灵活创建不同需要的对象
   - 父类的构造器不可被子类继承

```
Person per = new Person();//若为显式 则new以后属性有值

public class Person{
	public Person(){
		age = 1;
		name = "zhangsan";
	}//显式构造 默认构造相当于大括号中无内容
	public int age;
	public String name;
}
```

```
Person per = new Person(1,"zhangsan");//带参数构造

public class Person{
	public Person(int a,String n){
		age = a;
		name = n;
	}//显式构造 默认构造相当于大括号中无内容
	public int age;
	public String name;
}


```
- this 关键字 方法内需要调用到该方法的对象时使用 增强可阅读性
   - 方法内部使用 为该方法所属对象的引用
   - 构造器内部使用 为该构造器所初始化的对象 this(); 必须放构造器首行 不能出现构造器自调用（相互调用保证至少一个构造器不用this 即调用回自己）
   - 若本类中无此属性则从父类中继续查找

- JavaBean 规范
   - 类是公共的 又一个无参的公共构造器 有属性（一般私有）及其对应的get/set方法
   - 自动生成私有属性的get和set 右键-generate/control+N

### 继承 Inheritance
- 作用 提高代码复用性 为多态提供前提
- 父类/基类/超类 多个类中存在相同属性和行为时 将共性抽取出来形成父类 实际需求的子类在继承父类的基础上写自己特有代码后继承父类即可
- extends 构成父子类关系 子类不是父类的子集而是拓展
```
class Subclass extents Superclass{}
```
- Java只支持单继承 不允许一个子类继承多个父类
- 方法重写 子类重写父类方法并覆盖
   - 与父类方法同名/同参数列表/同返回值类型
   - 重写方法访问权限不可比被重写方法严格
   - 重写与被重写同为static 或 同为非static
   - 子类方法抛出异常不可大于被重写父类方法异常
- suoer 关键字 用于子类调用父类中的指定操作
   - 作用 访问父类属性/成员方法 调用父类构造器
   - 注意 子父类出现同名成员可用super区分 追溯不仅限于直接父类 类似于this 代表父类内存空间标识
- 构造器调用关系
   - 子类所有构造器默认访问父类中空参数构造器
   - 若父类只有显式构造无空参数构造器时 子类需通过this/super指定调用本类或父类构造器 调用应放在构造器第一行（this与super只能二选一 因都要占据首行）
- 类对象实例化
   - 简单类实例化 Xxx x = new Xxx(); 从上到下依次进行
	  - 加载Xxx.class(方法区)
	  - 栈中申请空间声明变量x（栈内存）
	  - 堆中开辟空间分配x的地址（堆内存）
	  - 对象属性进行默认初始化/默认初始化后若为显式构造则对属性进行赋值（堆内存）
	  - 构造函数方法进栈并初始化（栈内存）
	  - 将堆内存地址赋值给x后构造方法出栈（栈内存）
   - 子类实例化 Student std = new Student();//extends Person()
	  - 方法区中先加载Person.class 再加载Student.class
	  - 栈中申请空间声明变量stu
	  - 堆中开辟内存 分配地址
	  - 堆中对对象属性及父类属性进行默认初始化
	  - 栈中子类构造函数方法进栈
	  - 堆中显式初始化父类的属性
	  - 栈中父类构造方法进栈 执行完毕出栈
	  - 堆中显式初始化子类的属性
	  - 栈中将堆内存地址赋值给stu 子类构造方法出栈
### 多态 Polymorphism
- 多态性
   - 方法的重载(overload)和重写(overwrite)
   - 对象的多态性
	  - 引用变量类型一 编译时类型 由声明该变量时使用的类型决定
	  - 引用变量类型二 运行时类型 由实际赋给该变量的对象决定
	  - 当变量两个类型不一致时 出现多态
- 对象的多态
   - 一个变量只能有一种确定的数据类型
   - 一个引用类型变量可能指向/引用多种不同类型的对象
```
//正常指向
Person p = new Person();
Student s = new Student();
//多态
Person e = new Student();//父类引用对象可以指向子类实例
//上下等同 向上转型（upcasting）子类可看作特殊父类 即父类拓展
Person p = new Person();
p = new Student();//当执行该行代码 p栈中内存覆盖为Student地址
/*注意 
此处p不可调用Student()中添加的属性和方法
因属性于编译时确定（确定为Person()）没有Student()中的成员变量
*/
```
- 虚拟方法调用(Virtual Method Invocation)
```
Person e = new Student();
e.showInfo();//动态绑定 与栈区指向堆中对于内存相关
//Java方法运行在栈中 运行时会动态进栈出栈
//两个类中同时存在showInfo()函数时 调用的为Student()中的方法
//若Person()中无该方法仅有Student()中存在则报错
```
- 多态小结
   - 前提 需要存在继承或实现关系
   - 成员方法 编译时查看引用变量所属类是否有所调用方法 运行时调用实际对象所属类的重写方法 即成员方法多态性也称为动态绑定 需建立在方法重写之上
   - 成员变量 不具备多态性 仅看引用变量所属类

### 高级类特性

- instanceof 操作符 x instanceof A
   - 作用 检验x是否为类A的对象 返回值为boolean型
   - 要求 x与类A必须有继承关系 否则编译错误
```
System.out.println(x instanceof A);
//判断A是否为x的所属类或其父类 若是输出true 若为所属类子类输出false
```

- Object类 为所有Java类的根父类（最顶层）
   - 若类的声明中未用extends指明其父类 则默认父类为Object类
   - 设置于形参中则可接收任何类作为其参数 用于不确定形参要设计何种类型的情况
   - Object类中的主要方法
	  - public Object() 构造方法
	  - public boolean equals(Object obj) 对象比较 判断是否为同一个
	  - public int hashCode() 取得Hash码
	  - public String toString() 对象打印时调用

```
public void test(Object obj){}

public static void main(String[] args){
	Test t = new Test();
	Person p = new Person();
	t.test(p);
	t.test(new Student());//隐式对象 只用一次情况

	System.out.println(t.equals(p));//输出false
	System.out.println(hashCode(p));//Hash码 如17225372
	System.out.println(toString(p));//输出该引用对象所在地址
}
```
- 对象类型转换（Casting）/造型
   - 规范 转换之前应用instanceof先对继承关系进行判断
```
//Student extands Person 类似于基本类型转换

Person p = new Person();
Student s = new Student();
p = s;//从子类到父类的转换可以自动进行
s = (Student)p;//父类到子类的类型转换必须通过强制类型转换实现
//无继承关系的引用类型间的转换是非法的
```
- equals() 为Object类中的方法 所有类可继承 
   - 相较于“==”仅能应用于对象的比较 比较对象的内存地址
   - 特例 File类/String类/Date类/WrapperClass包装类 对equals()方法进行了重写 比较则为类型及内容 而非是否同一对象 而特殊类“==”仍为比较是否同一对象

- String对象创建 底层内存变化区别
   - 堆中存在特定内存称为 字符串常量池
```
//字面量创建
String s1 = "abc";//检索堆中字符串常量池中不存在abc 创建abc
String s2 = "abc";//发现字符串常量池中存在abc 存储对应地址于栈
//不再重新创建 s1 s2 指向同一地址

//new创建
String s3 = new String("def");//检索常量池 若无def常量池中创建 
//在堆中常量池外同时创建值为def的对象s3 返回常量池外创建的地址
String s4 = new String("def");//检索存在 不再于常量池中创建
//堆中常量池外创建值为def的对象s4 返回不同于s3的s4创建地址
//s3 s4 指向不同地址

String s5 = "x"+"y";//经过JVM优化 常量池中创建“xy”对象

String s6 = new String("1")+new String("1")+new String("2");
//通过StringBuilder实现 常量池中创建“1”和“2”两个对象
//常量池外创建“112”对象 返回常量池外的地址
```
- 包装类（Wrapper） 装箱/拆箱
   - 将八种基本类型包装成类为装箱 反之为拆箱
   - 对应写法 基本数据类型-包装类 int-Integer/char-Character/其余均为首字母大写
   - 主要应用 String类转换为基本数据类型/基本数据类型转换成String类 
```
Integer i = new Integer(112);//装箱
int j = i.intValue();//拆箱
//JDK1.5版本后支持自动装拆箱
Integer a = 112;//自动装箱
int b = a;//自动拆箱

//String类转换
int i = new Integer("123");//通过包装类构造器实现
int i = Integer.parseInt("123");//通过包装类parseXxx的静态方法
String istr = String.valueOf(i);//调用字符串重载的valueOf()方法
String istr = i+"";//直接方式
```
- toString() 为Object类中的方法 输出对象地址
   - 常作为打印对象调用 对该方法进行重写以打印所需String信息


- static 关键字
   - 区别于实例化变量（instance variable） 类变量可让同一类中所有实例共享数据 无需实例化 属于类的一部分 也称为 静态变量
   - 类属性设计思想 分析哪些属性不因对象的不同而改变
   - 类方法设计思想 方法不因对象不同而改变 即与调用者无关如工具函数 
   - 使用范围 属性/方法/代码块/内部类
   - 特点 随着类加载而加载/优先于对象存在/修饰的成员被所有对象共享/访问权限允许时可以不创建对象直接使用 类名.方法()
   - 运用举例 判空/计数
   - 方法内部不允许有this/super 重载方法必须同为static或同不为
   - 共享类数据 一处变化类所有对象变化 谨慎更改
- 单例（Singleton）设计模式
   - 设计模式 经过大量实践总结与理论化后优选的代码结构/编程风格/解决问题的思考方式 即解决问题的套路
   - 单例 整个软件系统运行过程中该类仅被实例化一次(只会new一次) 用于实例化对象需要消耗大量时间和资源的情况
   - 饿汉式单例/懒汉式单例
```
//饿汉式——类加载后先new一个对象 以后不论谁来调用getInstance即可
public class Lazy{
	private Lazy(){
		//构造私有化 调用该类不能直接用new创建对象
	}
	private static Lazy lazy = new Lazy();
	public static Lazy getInstance(){
		return lazy;
	}
}
//懒汉式——有第一个人调用时才new一个对象
public class Hunger{
	private Hunger(){
		//构造私有化 调用该类不能直接用new创建对象
	}
	private static Hunger hunger = null;
	public static Hunger getInstance(){
		if(hunger == null){
			hunger = new Hunger();
		}
		return hunger;
	}
}
```
- main方法语法
   - public权限 因Java虚拟机需要调用类main()的方法
   - static 因Java虚拟机在执行main()方法时不必创建对象
   - String类型数组参数 数组保存执行Java命令时传递给所运行类的参数
- 代码块 对Java对象进行初始化
   - new对象的执行顺序 类的属性默认初始化——类属性显式初始化——执行代码块的代码——执行构造器的代码
   - 静态代码块 只能使用静态static修饰的属性和方法 区别于非静态代码块 new多少次都只执行一次
   - 代码块运行顺序 静态优先于非静态执行 同级别从上至下
```
public class Person(){
	String name;
	static int age;
	
	{
		this.name = "zhangsan";
		System.out.println("非静态代码块")
	}
	static{
		age = 1;
		System.out.println("静态代码块")
	}//实际开发中使用静态代码块较多 用于初始化类的静态属性

}
//特殊场景应用 匿名内部类
	Person p = new Person(){//出现大括号即为匿名子类内容创建
		{//此处p为对象名 原匿名类仅为 new Person();
			super.name = "lisi";//代码块代替构造方法
		}
		@Override//重写即为匿名类内容
		public void test(){
			System.out.println("无类名Person子类")
		}//无类名无法运用构造器显式初始化属性 此时运用代码块
	}//难点P73 代码块不可替代的作用
```
- final 修饰符 代表最终
   - 修饰变量 即为常量 只能赋值一次 不可被改变
   - 修饰方法 子类不能重写
   - 修饰类 不能被继承
```
public final calss Person(){//修饰类 不可被继承
	final int AGE; = 1;//修饰变量 常量必须显式赋值
	final String PERSON_NAME = "";//static一起修饰 全局变量
	//常量命名规则 全大写 多词汇下划线连接
	public final void test(){}//修饰方法 不可被重写
}
```
- abstract 修饰符 抽象化
   - 应用 模型化父类无法确定的全部实现 由子类提供实现
   - 不能修饰属性/私有方法/构造器/静态方法/final方法
   - 抽象方法 只有方法声明 没有方法实现 以分号结束
   - 抽象类（abstract class）
	  - 含有抽象方法的类必须被声明为抽象类
	  - 不能被实例化 用于作为父类被继承 自累必须重写提供方法体 若子类未重写全部的抽象方法 仍为抽象类
	  - 可以定义构造器 只是不能直接创建抽象类实例化对象
```
public abstract class Employee {
	public abstract void work();
}
public class Manager extends Employee {
	@Override
	public void work(){
		System.out.println("这是领导")；
	}
}
```
- 模版方法设计模式（TemplateMethod）
   - 基于抽象类的模版模式设计 为多个子类提供设计模版
	  - 功能内部一部分实现确定 一部分不确定 可以将不确定的部分暴露出去让子类实现
	  - 父类提供多个子类通用方法之外 将一个或多个方法留给子类实现

- 接口(Interface) 用于实现多重继承
   - 内部有常量/方法定义 无变量/方法实现
   - 一个类可实现多个接口 接口也可继承其他接口
   - 若一个类未实现接口的所有方法 就要定义为抽象类
   - 面向接口编程 接口的主要用途就是被实现类实现
   - 区别于抽象类 接口对于不稳定的抽象 子类可有选择进行更改 换言之 抽象类是对一类事物的高度抽象（属性/方法） 接口是对一系列动作的抽象（方法）
	  - 应用1 涉及多层继承有可能污染中间层内容 建立行为接口有选择性读取 可保证无关类不必建立继承关系
	  - 应用2 接口与实现之间存在多态性
```
//接口特点
public interface Person{//使用interface定义
	//接口没有构造器 采用多层继承机制
	int age = 1;//成员变量默认由public static final修饰
	//即等同于 public static final int age = 1;
	void showInfo();//方法默认由public abstract修饰
}
public class Student implements Person,Person1{
//接口用implements继承
//子类只能继承一个父类 类可以有多个接口 多个接口用,分隔
	@Override
	public void showInfo(){}
	public void showInfo1(){}
	
}
//若一个类既有继承又有实现 则先写继承后写实现
public class Student extands Person implements Person1(){}
//接口多态性
Person p = new Student();
p.showInfo();
```
- 工厂方法(FactoryMethod)设计模式——应用最为广泛的模式
   - 作用通过工厂将new对象隔离 通过产品接口可以接受不同实际产品的实现类 实现类类名或其他改变 不影响其他合作开发人员的编程
   - 通过面向对象的手法（创建工作简单/创建时机重要） 将具体对象的创建工作延迟到子类 提供了一种扩展策略以解决紧耦合关系问题
```
//开发人员A
/**file BMW.java
*宝马产品接口
*/
public interface BMW{
	void showInfo();
}
//构建具体车的类
class BMW3 implements BMW{
	@Override
	public void showInfo(){
		System.out.println("这是宝马3系车")；
	}
}
/**file BMWFactory.java
*汽车生产工厂接口
*/
public interface BMWFactory{
	BMW productBWM();
}
//实现具体车型的生产工厂
public BMW3Factory implements BMWFactory{
	@Override
	public BMW productBWM(){
		System.out.println("生产宝马3系车")；
		return new BWM3();
	}
}
//——————————————————————————————————————————
//开发人员B
/**file Test.java
*汽车信息打印
*/
public class Test{
	public static void main(String[] args){
		BWM b3 = new BWM3Factory().productBWM();
		b3.showInfo();
	}
}//此时 开发人员A改变BMW3类命名/productBMW()函数体等 不影响开发B
```
- 内部类 变相实现类的多重继承
   - Java中允许一个类声明在另一个类的内部 可用外部类的属性/方法
   - 分类
	  - 成员内部类 写在类内部
	  - 匿名内部类 写在方法内部 用new方式写 参见代码块
   - 可以声明为final 类命名不能与外部类相同
   - 区别于外部类 内部类可以声明为private/protected
   - 可声明为static 则不可调用外层类的非static成员变量
   - 可以声明为abstract类 可被其他内部类继承

```
class A{
	public void testA(){};
}
class B{
	public void testB(){};
}
//class C extends A,B{}不允许
class C{
	private int i;
	class SetTest(){
		int i;//内部类属性可以与外部类同名
		public void setC(){
			C.this.i = 1;//内部类访问外部成员i
		}
		public void set(){
			this.i = 2;//设定内部类的i
		}
	}

	public void testA(){
		new InnerA().testA();
	}
	public void textB(){
		new InnerB().testB();
	}
	private class InnerA extends A{
		@Override
		public void testA(){
			System.out.println("C获取A方法并重写");
		}
	}
	private class InnerB extends B{
		@Override
		public void testB(){
			System.out.println("C获取B方法并重写");
		}
	}
}
public class test(){
	public static void main(String[] args){
		C c = new C();
		c.testA();
		c.testB();
	}
}//C类获得A类B类的方法 并重写 实现多重继承

```

## 异常处理

### 分类
- Error 错误 JVM系统内部错误/资源耗尽等严重情况
   - VirtulMachineError 虚拟机错误
	  - StackOverFlowError 栈溢出
	  - OutOfMemoryError 内存溢出
   - AWTError
- Exception 异常 其他因编程错误或偶然的外在因素导致的一般性问题 如试图读取不存在的文件/网络连接中断
   - IOException 文件读写异常
	  - EOFException 越过文件结尾继续读取
	  - FileNotFoundException 从不存在文件读取数据
	  - 连接一个不存在的URL
   - RuntiomeException 运行时异常
	  - ArrithmeticException 错误运算
	  - MissingResourceException
	  - ClassNotFoundException
	  - NullPointerException 空指针访问
	  - IllegalArgumentException
	  - ArrayIndexOutOfBoundsException 数组越界
	  - UnkownTypeException

### 捕获异常
- 将异常处理的程序代码集中在一起 与正常的程序代码分开 保证程序简洁 提高可读性 易于维护
- 捕获 用try{}括住有可能出现异常的代码段
- 抛出 用catch(){}写入可能捕获的异常类型 不确定可用异常父类Exception
- finally{} 捕获异常体系最终一段会执行的部分 常用于io操作/JDBC
```
public class Test(){
	public static void main(String[] args){
		int i = 0;
		try{
			System.out.println(1);//正常打印
			System.out.println(3/i);
			System.out.println(2);//不打印
//捕获异常后不再运行后方代码 若不解决前方异常无法确定后方程序是否存在异常
		}
		catch(Exception e){//异常父类 包含所有可能异常
			e.printStackTrace();//显示异常 追踪位置
			System.out.println(e.getMessage);
			//打印异常提示信息
			System.out.println(3);
			//捕获到异常才会正常打印
		}
		//catch(){}//可以连接多个catch
		finally{}//也可以不写 无条件执行语句
		System.out.println("done");
		//出现除0异常依旧可运行到最后
	}
}//通常只能处理Exception 对Error无能为力
```
### 声明抛出异常
- throws 方法后抛出异常 
- 可连续抛出 若在main继续用throws则错误将抛入虚拟机 无法处理
- 子类重写方法不能抛出比父类被重写范围更大的异常类型 范围可见分类

```
public class Test(){
	public static void main(String[] args){
		A a = new A();
		try{
			a.test();
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
}
class A{
	int i = 0;
	public void test() throws Exception{
	//在代码处抛出异常 在调用方法捕获处理
		System.out.println(3/i);
	}
}
```
### 人工抛出异常
- throw new Exception(""); 不满足运行条件情况下自定义异常
### 创建自定义异常类
- 用户自己的异常类必须继承现有的异常类 很少使用

## 集合

### 概述
- 存放于java.util包中 用来存放对象的容器
   - 只能存放对象 如存入int值会自动转换为Integer类后存入
   - 集合存放多个对象的引用 对象本身还是存放在堆中
   - 集合可以存放不同类型 不限数量的数据类型
- 三大体系
   - Set 无序/不可重复
   - List 有序/可重复
   - Map 具有映射关系
- 最基本集合接口 Collection Set/List/Map都为其继承
- JDK5后 加入泛型 可记住容器中对象的数据类型

### HashSet
- Set接口的典型实现 大多数时候Set集合通常指HashSet
- 按Hash算法存储集合中元素 具有较好的存取/查找性能
- 特点
   - 不能保证元素的排列顺序 存储位置取决于hashCode值
   - 不可重复 相同元素不不重复存 不同元素hashCode不相同
   - 不是线程安全的
   - 集合元素可以使null 可以存null
   - 集合判断两个元素相等的标准 两个对象equal()相等且hashCode相等
- 应用
```
import java.util.Set;
import java.util.HashSet;
import java.util.Iterator;

public class Test(){
	public static void main(String[] args){
		Set set = new HashSet();

		set.add(1);//添加
		set.remove(1);//移除
		System.out.println(set.contains(1));
		//判断是否包含元素
		System.out.println(set.size());
		//获取集合元素个数
		set.clear();//清空集合

		//使用迭代器遍历集合
		Iterator it = set.iterator();
		while(it.hasNext()){
			System.out.println(it.next());
		}

		//使用for each遍历集合 推荐使用这种
		for(object obj : set){
///把set的每一个值取出 赋值给obj 直到循环set所有值
			System.out.println(obj);
		}

		//使用泛型 可指定集合只能存同样类型的对象
		Set<String> set1 = new HashSet<String>();
	}
}
```
### TreeSet
- 可以确保集合元素处于排序状态 调用compareTo(Object obj)方法比较元素大小 集合元素按升序排列
- 自然排序/定制排序 默认为自然排序
- 必须放入同样类的对象 否则出现类型转换异常
```
//定制排序 Comparator接口
import java.util.Set;
import java.util.TreeSet;

public class Test(){
	public static void main(String[] args){
		Person p1 = new Person("zhangsan",23);
		Person p2 = new Person("lisi",16);
	Set<Person> set = new TreeSet<Person>(new Person());
		set.add(p1);
		set.add(p2);
		for(Person p :set){
			System.out.println(p.name+" "+p.age);
		}
	}
}
//将Person对象存到TreeSet中按年龄排序
class Person implements Comparator<Person>{
		int age;
		String name;

		public Person(){}
		public Person(String name, int age){
			this.name = name;
			this.age = age;
		}

		@Override
		public int compare(Person p1,Person p2){
			if(p1.age > p2.age){//升序排列
				return 1;
			}else if(p1.age < p2.age){
				return -1;
			}else(p1.age > p2.age){
				return 0;
			}
		}
	}
```
### ArrayList
- ArrayList 线程不安全 可用其他方法保证安全 建议使用
- Vector 线程安全 较为古老 即便使List线程安全也不建议使用
- ArrayList用法
```
import java.util.ArrayList;
import java.util.List;

public class Test{
	public static void main(String[] args){
		List<String> list = new ArrayList<String>();
		list.add("a");//加入元素 第一个索引下标0
		list.add(1,"a");//在指定下标位置插入元素 允许重复
		list.addAll(1,list1);//在指定位置插入集合
		System.out.println(list.get(0));
		//通过索引来访问指定位置元素集合
		System.out.println(list.indexOf("a"));
		//获取指定元素在集合第一次出现的下标
		System.out.println(list.lastIndexOf("a"));
		//获取指定元素在集合最后一次出现的下标
		list.remove(2);//根据索引移除元素
		list.set(1,"aa");//根据索引修改元素
		List<String> subList = list.subList(2,4);
		//根据索引截取元素形成新的集合 包含起始不包含结束位置
		System.out.println(list.size());//集合长度
	}
}
```
### HashMap
- Hashtable 同为对于Map接口的典型实现 较为古老 线程安全但不建议使用 不允许null作为key/value
- HashMap 线程不安全 允许null作为key/value
- 与HashSet类似 两者均不能保证元素顺序一致
- HashMap用法
```
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class Test{
	public static void main(String[] args){
		Map<String,Integer> map = new HashMap<String,Integer>();
		map.put("a",1);//添加数据
		System.out.println(map.get("a"));//根据key取值
		map.remove("a");//根据key移除键值对
		System.out.println(map.size());//集合长度
		System.out.println(map.containsKey("a"));
		//判断集合是否包含指定key
		System.out.println(map.containsValue("1"));
		//判断集合是否包含指定的value
		map.clear();//清空集合
		
		map.keySet();//获取map集合的key集合
		map.values();//获取集合所有value值
		//通过map.keySet()遍历集合
		Set<String> keys = map.keySet();
		for(String key : keys){
			System.out.println(key+" "+map.get(key));
		}
		//通过map.entrySet()遍历集合
		Set<Entry<String,Integer>> entrys = map.entrySet();
		for(Entry<String,Integer> en : entrys){
			System.out.println(en.getKey()+" "+en.getValue());
		}
	}
}
```
### TreeMap
- 根据Key进行排序 自然排序/定制排序 通常不使用复杂对象作为key
- 当key值为字符串时 自然排序为英文字典排序

### Collections 操作集合工具类
- 提供大量方法对集合元素进行排序/查询/修改/设置对象不可变/对集合对象实现同步控制等
- 排序 Collections.xxx(List)
   - reverse(List) 反转元素顺序
   - shuffle() 随机排序
   - sort(List) 字典升序排序
   - sort(List,Comparator) 指定Comparator产生顺序排序
   - swap(List,int,int) i处元素和j处交换
- 查找/替换 Collections.xxx(List)
   - Object max(Collection) 根据自然顺序返回最大元素
   - Object max(Collection,Comparator) 根据Comparator返回最大元素
   - Object min(Collection)
   - Object min(Collection,Comparator)
   - int frequency(Collection,Object) 返回指定元素出现次数
   - boolean replaceAll(List,oldVal,newVal) 新值替换所有旧值
- 同步控制 synchronizedXxx()方法
   - 将指定集合包装成线程同步的集合 以解决多线程并发访问集合时线程安全问题

## 泛型

### 概述
- Java中的泛型 只在编译阶段有效 泛型信息不会进入到运行阶段
- 类型安全 指定类型添加到集合中
- 便捷 读取出来的对象不需要强转
- 代码简洁/健壮 编译时若无警告 运行时不会有ClassCastException异常
### 泛型类
- new过程中不指定泛型 则相当于指定Object类
- 同样的类不同泛型类型指定 不能相互赋值
```
public class Test{
	public static void main(String[] args){
		A<String> a = new A<String>();
	//new处指定泛型类型为String 对象形参于返回值均确定为String
	}
}

class A<T>{//泛型T可任意取名 一般使用T 意为type
	private T key;
	public void setKey(T key){
		this.key = key;
	}
	public T getKey(){
		return this.key;
	}

}
```

### 泛型接口
- 实现接口时指定接口的具体类型 则实现接口所有方法的位置都要使用具体指定的数据类型
```
public class Test{
	public static void main(String[] args){
		A1<Object> a = new A<Object>();
//若在类中已传入实参指定泛型 此处再指定泛型反而报错
		//A2 a = new A2;//已传实参无需再指定
	}
}

interface A<T>{
	T test(T t);
}

//未传入泛型实参时 声明时将与泛型类相同的声明加入到类中
class A1<T> implments A<T>{
//class A1 implements A<T>{}//报错
//class A1 implements A<String>{}//传入实参 不报错
	@verrride
	public T test(T t){
		reutn t;
	}
}
```
### 泛型方法
- 在public后面指定想要用的泛型 即可在方法中的任何位置使用泛型
- 静态方法不能使用类定义泛型 只能使用静态方法自己定义的泛型
- 调用前没有固定的数据类型 调用是传入的参数时声明类型 就会把泛型固定为对应类型
```
public class Test{
	public static void main(String[] args){
		A<Object> a = new A<Object>();
		a.test1(1);//固定为Integer
		a.test1("abc");//固定为String
	}
}

//class A{//可定义常规类
class A<E>{
	private E e;//可在类上定义泛型 在普通方法中使用
	public <T> void test1(T s){//无返回值泛型方法
		T t = s;
		System.out.println(this.e);//类上泛型使用
	}
	public <T> T test2(T s){//有返回值泛型方法
		return s;
	}
	public <T> void test3(T... strs){//可变参数泛型方法
		for(T s : strs){
			System.out.println(s);
		}
	}
	public static <T> void test4(T t){}//静态类型方法

}
```
### 通配符
- ? 集合中不确定元素数据类型 用?表示所有类型
- ？用于有限制的通配符 类及其子类/类及其弗雷/接口及其实现类


```
public class Test{
	public static void main(String[] args){
		A a = new A();
		List<String> l1 = new ArrayList<String>();
		List<Integer> l2 = new ArrayList<Integer>();
		a.test(l1);//可存String
		a.test(l2);//可存Integer

		List<D> ld = new ArrayList<D>();
		a.test1(ld);//D为C子类 满足限制 此处若为lb则报错

		List<IAImpl> lia = new ArrayList<IAImpl>();
		a.test3(lia);//lia为IA实现类 满足限制 其他类报错
	}
}

class A{
//test方法中的list集合参数不确定其存的数据类型
	public void test(List<?> list){	}
//test1方法 list参数的元素类型为 C及其子类
	public void test1(List<? extends C> list){}
//test2方法 list参数的元素类型为 C及其父类
	public void test2(List<? supers C> list){}
//test3方法 list参数的元素类型为 IA的实现了类
	public void test3(List<? extends IA> list){}

}

class B extends A{}
class C extends B{}
class D extends C{}

interface IA{}

class IAImpl implements IA{}

```

## 枚举和注解

### 枚举
- enum 关键字 用于定义枚举类
- 枚举类与普通类的区别
   - 使用enum定义枚举类 默认继承java.lang.Enum类
   - 构造器只能用private权限
   - 所有实例必须在类中显式列出 ,分隔 ;结尾
   - 所列出的实例系统会自动添加 public static final修饰
   - 提供了一个value方法 用于遍历所有枚举值
- 枚举类与普通类一样可以实现接口
- 枚举类方法 valueOf/toString/equals/hashCode/getDeclaringClass/name/ordinal/compareTo/clone
- JDK1.5后 switch表达式可使用枚举类的对象 case子句可直接为枚举类名字
```
public class Test{
	public static void main(String[] args){
		//获取一个Season对象
		Season spring = new Season.SPRING;
		spring.showInfo();
		Season spring1 = new Season.SPRING;
		System.out.println(spring.equals(srping1));
		//结果为true 每次执行Season.SPRING获得相同的对象
		//即枚举类中每个枚举都是单例模式 仅一次创建 多次使用
	}
}

enum Season{
	SPRING("春天","春暖花开"),
	SPRING("夏天","夏日炎炎"),
	SPRING("秋天","秋高气爽"),
	SPRING("冬天","寒风凛冽");/注意符号

	private final String name;
	private final String desc;
	
	private Season(String name,String desc){
		this.name = name;
		this.desc = desc;
	}//有参构造 每一个小枚举的写法都调用一次
	
	public void showInfo(){
		System.out.println(this.name+" "+this.desc);
	}
}
```
### 注解 Annotation
- JDK5.0 Java增加了对元数据(MetaData)的支持 即注释
- 可视为代码中的特殊标记 标记可在编译/类加载/运行时被读取并执行相应的处理 程序员常使用Annotation在不改变原有逻辑的基础上在源代码文件中嵌入一些补充信息
- 可视为修饰符 修饰包/类/构造器/方法/成员变量/参数/局部变量的声明 信息保存在Annotation的"name-value"对中
- 可用于为程序元素（类/方法/成员变量等）设置元数据
- 使用时在注释前增加@符号 举例基本Annotation
   - @override 限定重写父类方法
   - @Deprecated 用于表示某个程序元素已过时
   - @SuppressWarnings 抑制编译器警告
- 自定义注解 暂作为了解 做到开源项目才会遇到

```
class A{
	@TestAnn(id=100,desc="姓名")//Target约束下只能给属性注解
	String name;
}

@Target(ElementType.FIELD)//属性 注明注解是对应类的方法/属性/其他
@Retention(RetentionPolicy.RUNTIME)//整个程序运行过程 生命周期
@Documented//放入文档中
@interface TestAnn{
	public int id() default 0;
	//注解值不填时 定义默认值用default
	public String desc() default "";
}
```
## IO流
### 概述
- io流用来处理设备之间的数据传输 java.io包下提供了各种流类接口
- 输入 input 读取磁盘/光盘/其他存储设备的尾部数据到程序/内存中
- 输出 output 将程序/内存数据输出到外部存储设备中
- java.io.File类 管理计算机操作系统中的文件/文件夹
- IO操作通常存在异常 需捕获
- 分类方式
   - 按数据单位
	  - 字节流 8bit InputStream/OutputStream
	  - 字符流 16bit Reader/Writer
   - 按流向 输入流/输出流
   - 按角色 节点流/处理流
- 流分类 传输的数据集即为数据流
   - 文件流 基于文件的操作 FileInputStream/FileOutputStream/FileReader/FileWriter
   - 缓冲流 基于内存的操作 BufferedInputStream/BufferedOutputStream/BufferedReader/BufferedWriter
   - 转换流 InputStreamReader/OutputStreamWriter
   - 打印流 PrintStream/PrintWriter
   - 数据流 DataInputStream/DataOutputStream
   - 对象流 涉及序列化/反序列化 ObjectInputStream/ObjectOutputStream
   - 随机存取文件流 随机意为可自主选取存储位置 RandomAccessFile

### File类
- File能创建/删除/重命名 文件/目录 但不能访问文件内容(输入/输出流)
- File对象可作为参数传给流的构造函数
- 访问文件名
   - getName() 获取文件/文件夹名
   - getPath() 获取new file时文件路径
   - getAbsoluteFile() 获取文件带磁盘号的绝对路径
   - getAbsolutePath() 返回用当前文件绝对路径构建的file对象
   - getParent() 返回文件/文件夹父级路径
   - renameTo(File newName) 给文件/文件夹重命名
- 文件检测
   - exists() 判断文件是否存在
   - canWrite() 判断文件是否可写
   - canRead() 判断文件是否可读
   - isFile() 判断当前对象是否为文件
   - isDirectory() 判断当前对象是否为文件夹/目录
- 获取常规文件信息
   - lastModify() 获取文件最后修改时间 返回毫秒数
   - Length() 获取文件长度 返回字节数
- 文件操作相关
   - createNewFile() 创建一个新的文件
   - delete() 删除一个文件
- 目录相关操作
   - mkdir() 创建单层目录
   - mkdirs() 创建多层目录
   - list() 返回文件夹子集的名称 包括目录和文件
   - listFiles() 返回文件夹子集的file对象 包括目录和文件
```
import java.io.File

public class Test{
	public static void main(String[] args){
		//四种分隔方法写文件路径
		File f1 = new File("D:\\test\\t.txt");
		//此时对象f1即为t.txt 第一个\为转译符第二个\为分隔符
		File f2 = new File("D:/test/t.txt");
		File f3 = new File("D:"+File.separator+"test\\t.txt");
		File f4 = new File("D:\\test","t.txt");//少用

		String[] f = f1.list();
		for(String s : f){
			System.out.println(s);
		}

		file testf = new File("D:\\test");
		new Test().test(f);
	}

	//递归遍历文件
	public void test(File file){
		if(file.isFile){
			System.out.println(file.getAbsolutePath());
		}else{
			System.out.println(file.getAbsolutePath());
			//若为文件夹 获取子文件夹/子文件的file对象
			File[] fs = file.listFiles();
			if(fs != nnull &&fs.length >0){
				for(File ff : fs){
					test(ff);
				}
			}
		}
	}
}
```

### 文件字节流
- 非常通用 可操作字符文档/图片/压缩包等任何类型文件 因底层引用字节流直接使用二进制
```
import java.io.FileInputStream
import java.io.FileOutputStream

public class Test{
	public static void main(String[] args){
		Test.testFileInputStream();
		Test.testFileOutputStream();
	}

	//文件字节输入流FileInputStream
	public static void testFileInputStream(){
		try{
			FileInputStream in = new FileInputStream("D:\\test\\t.txt");
			byte[] b = new byte[10];
			int len = 0;
//.read方法返回值为读取数据的长度 若读到最后一个数据仍向后读 则返回-1
			while((len = in.read(b)) != -1){
				System.out.println(new String(b,0,len));
//String此处 参数一为缓冲数据的数组 二为字符串转换起始位置 三为总转换字节数

				//out.write(in,0,len);
//将读取的数据写入内存进行复制
//循环外前方创建FileOutputStream out
//循环外后方 有 out.flush(); out.close();
			}
			in.close();//注意 流使用完毕后一定要关闭
		}catch(Exception e){
			e.printStackTrace();
		}
	}

	//文件字节输出流FileOutputStream
	public static void testFileOutputStream(){
		try{
			FileOutputStream out = new FileOutputStream("D:\\test\\tt.txt");
			String[] str = "abc123";
			out.write(str.getBytes());//把数据写到内存
			out.flush();//把内存中的数据刷写到硬盘
			out.close();//关闭流
		}catch(Exception e){
			e.printStackTrace();
		}
	}

}
```
### 文件字符流
- 与文件字节流差别 其余相同
   - 只适合操作内容是字符的文件
   - 对象为 FileReader/FileWriter 字节流为FileInputStream
   - 存放临时数组为 char[]  字节流为byte[]
- 注意
   - 写入文件 同名将被覆盖
   - 读取文件 必须保证文件已存在 否则有异常
   - 路径分隔 常用\\或/

### 缓冲流
- 文件流基于硬盘/磁盘 受到硬盘性能读写速度的制约 速度较慢 
- 缓冲流基于内存 通过缓冲流将数据传入内存 再从内存中进行io操作 其速度约为基于硬盘的75000倍
- 以字节流举例 缓冲字符流与字节流区别同文件流
```
import java.io.BufferedInputStream
import java.io.BufferedOutputStream
import java.io.FileInputStream
import java.io.FileOutputStream

public class Test{
	public static void main(String[] args){
		try{
			Test.copyFile();
		}catch(Exception e){
			e.printStackTrace();
		}

	}
}
	//缓冲流实现文件复制
	public static void copyFile() throws Exception{
		//输入缓冲流 把文件字节流放入缓冲字节流对象
		FileInputStream in = new FileInputStream("D:\\test\\t.txt");
		BufferedInputStream br = new BufferedInputStream(in);
		//输出缓冲流
		BufferedOutputStream bo = new BufferedOutputStream(new FileOutputStream("D:\\test\\tt.txt"));
		byte[] b = new byte[1024];
		int len = 0;
		while(len = in.read(b) != -1){
			bo.write(b,0,len);//写到内存
		}
		bo.flush();//刷到硬盘
			
		bo.close();//后创建的先关闭
		br.close();
		in.close();//先创建的后关闭
	}

}
```

### 转换流
- 提供字节流与字符流之间的转换
- 使用场景 当字节流中数据均为字符时 转换为字符处理效率更高
- 所有文件都有其编码格式 txt与Java文件通常有三种编码
   - ISO8859-1 西欧编码 纯粹英文编码 不适用于汉子
   - GBK和UTF-8 适用于中文与英文 通常采用UTF-8编码 
- 转换字符流时 设置的字符集编码要与读取文件的数据编码一致
```
public static void testInputStream() throws Exception{
	FileInpputStream fs = new InputStream("D:\\test\\t.txt");
	FileInputStreamReader in = new FileInputStreamReader(fs,"GBK");
	//参数1为字节流 参数2为编码
}
```
### 标准输入输出流
- System.in/System.out 对应为InputStream/OutputStream子类 分别代表系统标准的输入输出设备 默认输入设备为键盘/输出设备为显示器
```
//把控制台输入的内容写到指定的txt文件中 当接收到字符串over 结束程序运行
public static void writeTXT() throws Exception{
	//创建一个接收键盘收入数据的输入流
	InputStreamReader is = new InputStreamReader(System.in);
	//把输入流放到缓冲流里
	BuffereddReader br = new BufferedReader(is);
	BufferedWriter out = new BufferedWriter(new FileWriter("D:\\test\\t.txt"));
	String line = "";
	//readLine读一整行
	while((line = br.readLine()) != null){
		if(line.equals("over")){
			break;
		}
		//读取的每一行都写到指定的TXT文件
		out.write(line);
	}
	out.flush();

	out.close();
	br.close();
	is.close();
}
```
### 打印流
- 输出信息最方便的类
- PrintStream字节打印流/PrintWriter字符打印流
   - 输出不会抛出异常
   - 有自动flush功能
   - System.out返回PrintStream实例
### 数据流
- 专门用于读写基本数据类型的数据
- 用数据输出流写到文件的数据上乱码的 需要数据输入流进行读取 读取时要保证于写入类型一致
```
//把控制台输入的内容写到指定的txt文件中 当接收到字符串over 结束程序运行
public static void testDataOutputStream() throws Exception{
	DataOutputStream out = new DataOutputStream(new FileOutputStream("D:\\test\\t.txt"));
	out.writeBoolean(true);

	out.flush();
	out.close();

	//读取选用对应类型
	//DataInputStream in
	//System.out.println(in.readBoolean());
}
```

### 对象流
- 用于存取对象的处理流 将对象写入数据源并可还原 将对象转换为二进制通过网络传输
- ObjectInputStream 序列化 将Java对象写入IO流中
- ObjectOutputStream 反序列化 从IO流中恢复Java对象
- 不能序列化static和transient修饰的成员变量 
- 仅针对类实例化后对象的属性 不包括类的属性
- 对象序列化 作为远程方法调用(Rmote Method Invoke,RMI)的实现机制 序列化机制是JavaEE平台的基础 令对应类可序列化 必须实现两个接口之一 Serializable/Externalizable
   - Serializable接口 该接口都有一个表示序列化版本标识符的静态变量 serialVersionUID用于表明不同版本之间的兼容性 该变量相同可兼容 不同则可区别不同版本间不兼容

```
//Java可根据类细节自动生成 但serialVersionUID建议显式声明 
private static final long serialVersionUID = 1L;
//因源码若发生修改 serialVersionUID可能发生变化

//对象的序列化
pubulc static void testSerialize() throws Exception{
	//定义对象输出流 把对象序列化后放到指定文件中
	ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("D:\\test\\t.txt"));
	
	Person p = new Person();
	p.name = "zhangsan";
	p.age = 11;

	out.writeObject(p);
	out.flush();
	out.close();
}

//对象反序列化
//注意反序列化使用的类要严格一致 包名/类名/类结构等
pubulc static void testSerialize() throws Exception{
	//创建对象输入流对象 从指定的文件中把序列化后的流读取出来
	ObjectInputStream in = new ObjectInputStream(new FileInputStream("D:\\test\\t.txt"));

	Object obj = in.readObject();
	Person p = (Person)obj;

	System.out,println(p.name);
	System.out,println(p.age);
	in.close();
	
```
### RandomAccessFile类
- 支持随机访问方式 可以跳到文件任意位置读写文件
- 对象包含一个记录指针 用以标示当前读写处位置 可自由移动记录指针
   - long getFilePointer() 获取文件记录指针当前位置
   - void seek(long pos) 将文件记录指针定位到pos位置
- 创建类实例需要指定mode参数 指定访问模式
   - r 只读
   - rw 读写
   - rwd 读写/同步文件内容的更新
   - rws 读写/同步文件内容和元数据的更新

```
//构造器
public RandomAccessFile(File file,String mode);
public RandomAccessFile(String name,String mode);

//参数1文件路径 参数2访问模式
RandomAccessFile ra = new RandomAccessFile("","");

ra.seek(ra.length());//设置写的起始点 单位为字节数 此处代表文件结尾追加
ra.write("你好".getBytes());//字符串转换为byte 写文件位置若有内容则覆盖
```
### 流的小结
- 流用于处理数据
- 处理数据时 先明确数据源（文件/键盘）/数据目的地（文件/显示器或其他设备）
- 主要帮助数据进行传输 并对数据进行处理

## 反射
### 概述
- Java反射前提 已经加载过这个类 则可通过类名找到这个类所有的相关系信息
- 被视为动态语言的关键 反射机制允许程序在执行期借助Reflection API取得任何类的内部信息 并能直接操作任意对象内部的属性及方法
- Java反射机制提供功能
   - 在运行时判断任意一个对象所属的类
   - 在运行时构造任意一个类的对象
   - 在运行时判断任意一个类所具有的成员变量及方法
   - 在运行时调用任意一个对象的成员变量及方法
   - 生成动态代理
- 反射相关的主要API
   - Java.lang.Class 代表一个类
   - Java.lang.reflect.Method 代表类的方法
   - Java.lang.reflect.Field 代表类的成员变量
   - Java.lang.reflect.Constructor 代表类的构造方法
- 基本上类所包含的全部内容都可被反射
   - Interface 实现的全部接口
   - Superclass 所继承的父类
   - Constructor 全部的构造器
   - Method 全部的方法
   - Field 全部的属性
   - Annotation 全部的注解
### Class类
- JRE为每个类都保留一个不变的Class类型对象
- Class本身也是一个类 一个类在JVM中只会有一个Class实例
- Class对象仅能由系统建立 对应的是一个加载到JVM中的.class文件
- 每个类的实例都会记得自己是由哪个Class实例所生成
- 通过Class可以完整地得到一个类中的完整结构
- Class类常用方法
   - static Class forName(String name) 根据类的全类名（包名.类名）获取Class对象
   - Object newInstance() 创建目标类对象
   - getName() 获取全类名
   - Class getSuperclass() 获取所有的父类的Class对象
   - Class[] getInterfaces() 获取所有实现的接口
   - ClassLOader getClassLoader() 获取类的加载器
   - Class getSuperclass() 获取父类的Class对象
   - Constructor[] getConstructors() 获取所有的构造器
   - Field[] getDeclaredFields() 获取所有的属性
   - Method getMethod(String name,Class ... paramTypes) 获取对应的方法
- 实例化Class类对象方法
```
public class Test{
	public static void main(String[] args){
		Person p = new Person();

		//法1 通过类名.class创建指定类的Class实例
		Class c1 = Person.class;
		//法2 通过getClass()方法 获取对应实例对象的类Class实例
		Class c2 = p.getClass();
		//法3 静态方法forName(String className)获取 最常用方式
		try{
			Class c3 = Class.forName("test.Person");
		}catch(Exception e){
			e.printStackTrace();
		}
		//法4 ClassLoader 最不常用
		//ClassLoader cl = this.getClass().getClassLoader();
		//Class clazz = cl.loadClass("类的全类名");

		//c1/c2/c3/c4对象中包含对象p所属Person类的所有信息
	}
}
```
### 反射获取一个类的父类和接口
- public Class<?>[] getInterfaces() 实现的全部接口
- public Class<? Super T> getSuperclass() 所继承的父类
```
public class Test{
	public static void main(String[] args){
		try{
			Class cl = Class.forName("test.Student");
			
			Class superCl = cl.getSuperclass();//获取父类
			System.out.println(superCl.getName());

			Class interfa = cl.getInterfaces();//获取当前类所有接口
			for(Class c: interfa){
				System.out.println(c.getName());
			}
		}catch(Exception e){
			e.printStackTrace();
		}

	}
}
```
### 获取一个类的全部构造器
- public Constructor<T>[] getConstructors() 返回类所有publlic构造方法
- public Constructor<T>[] getDeclaredConstructors() 返回类声明所有构造方法
- Construction类中
   - public int getModifiers(); 取得修饰符 返回数字1表示public 2代表private
   - publicc String getName(); 取得方法名称
   - public Class<?>[] getParameterTypes(); 取得参数类型
```
improt java.lang.reflect.Constructor;

	Constructor[] cons1 = cl.getConstructors();
	Constructor[] cons2 = getDeclaredConstructors();
```
### 通过反射的构造方法创建对象
```
//方法1 调用public无参构造
Object obj = cl.newInstance();
Student stu1 = ()Student obj;

//方法2 调用public有参构造
Constructor c = cl.getConstructor(String.class);//一个参数
Student stu2 = (Student)c.newInstance("第一中学");
System.out.println(stu2.school)；

//方法3 通过反射强制调用private构造方法
Constructor c = cl. getDeclaredConstructors(String.class,int.class);//两个参
c.setAccessible(true);//解除私有封装
Student stu3 = (Student)c.newInstance("zhangsan",12);
```
### 获取类的方法
- public Method[] getDeclaredMethods() 获取所有方法
- public Method[] getMethods() 获取public方法
- Method类中
   - public Class<?> getReturnType() 取得全部返回值
   - public Class<?>[] getParameterTypes() 取得全部参数
   - public int getModifiers() 取得修饰符
```
Method[] ms = cl.getMethods();//获取所有public方法
```
### 获取类的属性
- public Field[] getFields() 公有属性 包含父类公有属性
- public Field[] getDeclaredFields() 本类全部属性 不包含父类
- Field方法中
   - Public int getModifiers() 修饰符 返回整数形式
   - public Class<?> getType() 属性类型
   - public String getName() 名称
### 调用类中的指定方法
```
Constructor con =cl.getConstructor();//获取无参构造
Object obj = con.newInstance();//使用无参构造创建对象

//调用公有方法
method m =cl.getMethod("setInfo",String.class,String.class);
//取得名称为setInfo 参数为String，String等
m.invoke(obj,"张三","第一中学")；
//参数1位实例化对象 参数2位调用方法等实际参数

//调用私有方法
method m =cl.getMethod("test", String.class);
m.setAccessible(true);//解除私有封装
m.invoke(obj,"李四");

//调用重载方法
method m =cl.getMethod("setInfo", Int.class);
m.invoke(obj,1);

//调用有返回值的无参方法
method m =cl.getMethod("getSchool");
m.invoke(obj);

```
### 调用类中的指定属性
- public Field getField(String name) 返回类或接口指定的public属性
- public Field getDeclaredField(String name) 返回指定的属性
- Field中
   - public Object get(Object obj) 获取指定对象上的属性内容
   - public void set(Object obj,Object value) 设置指定属性内容
   - public void setAccessible(true) 访问私有属性时让属性可见
```
Field f = cl.getDeclaredField("school");//获取名称为school的属性
//f.setAccessible(true);//若为私有属性 解除私有封装
f.set(stu,"第三中学")；//对stu对象的school属性设置为“第三中学”
String school = (String)f.get(stu);//获取对象的school属性的值
```
### Java动态代理
- Proxy 专门完成代理的操作类 时所有动态代理的父类 可为一个或多个接口动态生成实现类
- static Object newProxyInstance(ClassLoader loader,Class<?>[] interfaces,InvocationHandler h) 直接创建一个动态代理对象
- 步骤
   - 创建一个实现接口InvocationHandler的类 该类必须实现invoke方法以完成代理的具体操作
   - 创建被代理的类以及接口
   - 通过Proxy的静态方法newProxyInstance创建一个接口代理
   - 通过Subject代理调用RealSubject实现类的方法
```
/**文件ITestDemo
*建立接口
*/
public interface ITestDemo{
	void test1();
	void test2();
}


/**文件TestDemoImpl
*接口实现类
*/
public class TestDemoImpl implements ITestDemo{
	@Override
	public void test1(){
		System.outprintln("执行test1()方法")
	}

	@Override
	public void test1(){
		System.outprintln("执行test2()方法")
	}
}

/**文件Test
*main方法 在test1 test2 运行前后统一加入打印语句
*注意 如果一个对象要通过Proxy.newProxyInstance方法被代理
*	  这个对象的类一定要有相应的接口
*	  本例中为ITestDemo接口和实现类TestDemoImpl
*/
import java.lang.reflect.InvocationHandler;
import java.lang.reflect

public classTest{
	public static void main(String[] args){
		//接口多态 用接口类型取接收实际的对象
		ITestDemo test = new TestDemoImpl();
		

		//对象的多态 创建代理对象用接口接收
		InvocationHandler handler = new ProxyDemo(test);

//参数1为代理对象的类加载器 2为被代理的对象接口 3为代理对象 返回值为成功代理后的对象（此处为test） 类型为Object
		ITestDemo t = (ITestDemo)Proxy.newProxyInstance(handler.getClass().getClassLoader(),test.getClass().getInterfaces(),handler);

		test.test1();
		test.test2();

	}
}

/**文件ProxyDemo
*动态代理类 实现invoke方法
*/
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;

public class ProxyDemo implements InvocationHandler{
	Object obj;//被代理对象

	public ProxyDemo(){//创建构造方法用于赋值
		this.obj = obj;
	}

	@Override
	public Object invoke(Object proxy,Method method,Object[] args)
			throws Throwable{
		System.out.println(method.getName()+"方法开始执行");

		//执行指定代理对象指定方法 方法可能有返回值
		Object result = method.invoke(this.obj,args);

		System.out.println(method.getName()+"方法执行完毕");
		return result;
	}
}
```

## 线程
### 概述
- N核CPU 代表一个瞬时时间能处理N个任务 对应为N个进程 单核运行多个程序通过主频在极短时间内频繁切换多个进程
- 程序 为完成特定任务 用某种语言编写的一组指令集合 即静态代码/静态对象
- 进程 程序的一次执行过程/正在运行的程序 动态过程
- 线程 进程的分化 多线程即为一个进程可以并行执行多个线程
- 多线程需求场景
   - 程序需要同时执行两个或多个任务
   - 程序需要实现一些需要等待的任务 如用户输入/文件读写/网络操作/搜索
   - 需要一些后台运行等程序时
- 假设进程上运行的为main函数 当其中有一行代码开启线程 则开启后的新线程与main函数并行（互不相干）
- 多线程优点
   - 提高应用程序的相应 增强图形化界面中的用户体验
   - 提高计算机系统CPU利用率
   - 改善程序架构 既长又复杂的进程分解为多线程独立运行 有利于理解与修改

### 多线程创建和启动
- JVM允许多线程 通过java.lang.Thread类实现
- Thread类特性
   - run()方法 方法里写入想要开启的多线程运行的代码逻辑
   - start()方法 用于启动线程 运行run()方法
- Thread类构造方法
   - Thread() 创建新的Thread对象
   - Thread(String threadname) 创建线程并指定线程实例名
   - Thread(Runnable target) 指定创建线程的目标对象 实现Runnable接口中的run方法
   - Thread(Runnable target,String name) 创建新的Thread对象
- 创建线程方式一 继承Thread类
   - 定义子类继承Thread类
   - 子类中重写Thread类中的run方法
   - 创建Thread子类对象 即线程对象
   - 调用线程对象strat方法 启动线程/调用run方法
```
public class Test{
	public static void main(String[] args){
		Thread t = new TestThread();
		t.start();
		System.out.println("主程序运行的代码");
//主程序打印与线程打印顺序不再固定 因两者运行无关 多线程异步
	}
}


public class TestThread extends Thread{
	@Override
	public void run(){
		System.out.println("多线程运行的代码");
	}
}
```
- 创建线程方式二 实现Runnable接口
   - 定义子类实现Runnable接口
   - 子类中重写Runnable接口中的run方法
   - 通过Thread类含参构造器创建线程对象
   - 将Runnable接口子类对象作为实际参数传入Thread类构造方法中
   - 创建Thread子类对象 即线程对象
   - 调用Thread类的strat方法 启动线程/调用Runnable子类接口的run方法
```
public class Test{
	public static void main(String[] args){
		//在Thread中传入Runnable实例
		Thread t = new Thread(new TestRunnable());
	//Thread t = new Thread(new TestRunnable(),"name");
	//可有参数2 线程名称

		t.start();
		System.out.println("主程序运行的代码");
	}
}


public class TestRunnable implements Runnable{
	@Override
	public void run(){
		System.out.println("多线程运行的代码");
	//可通过Thread.currentThread().getName()打印线程名称
	}
}
```
### 继承与实现方式的联系与区别
- 线程代码存放位置 Thread子类里/接口子类里
- run方法 重写/实现
- 实现方法优势 更为常用
   - 避免单继承的局限性（类仍可继承其他父类及多接口）
   - 多线程可共享同一个接口实现类的对象 非常适合多个相同线程处理同一份资源
```
public class Test{
	public static void main(String[] args){
		Runnable run = new TestRunnable();

		Thread t1 = new Thread(run,"t1");
		t1.start();
		Thread t1 = new Thread(run,"t1");
		t2.start();
		//共享run一个接口对象 同时处理run实例中的资源
	}
}
```
### Thread类的相关方法
- 常规
   - void start() 启动线程并执行run方法
   - run() 线程在被调度时执行的操作
   - String getName() 返回线程名称
   - void setName(String name) 设置该线程名称
   - static currentThread() 返回当前线程
- 优先级 线程创建时继承父线程优先级 低1-10高 默认5 仅仅能增大优先概率 并不能确保一定优先运行
   - getPriority() 返回线程优先级
   - setPriority(int newPriority) 改变线程优先级
- 其他
   - static void yield() 线程让步 暂停当前正在执行的线程
	  - 将执行机会让给优先级相同或更高的线程(降低自己的运行概率) 
	  - 若队列中无相同优先级则忽略此方法
   - join() 调用线程阻塞 
	  - 直至join方法加入的进程执行完为止 
	  - t.join()即将t进程run内容插入到该位置同步运行 运行完毕才往下运行 优先级低低进程也可执行
   - static void(long millis) 
	  - 令当前活动线程在指定时间段内放弃对CPU的控制 时间到后重排队 
	  - 单位毫秒 抛出InterruptedException异常 
	  - Thread.sleep(1000)程序每隔一秒运行一次 可减慢程序运行速度
   - stop() 强制线程声明周期结束 停止线程
   - BOOLean isAlive() 判断线程是否活着 返回boolean
### 线程生命周期
- 新建
- 就绪 start() 将进入线程队列等待CPU时间片 具备了运行条件
- 运行 被调度并获得处理器资源
- 阻塞 被挂起或执行输入输出操作时 让出CPU并临时中止自己的执行
- 死亡 自然死亡（执行完毕或触发异常）/强制死亡（.stop/断电）
- 周期变化
   - 新建->就绪 start()
   - 就绪->运行 获得CPU执行权
   - 运行->就绪 失去CPU执行权/yield() 唯一可双向转化
   - 运行->阻塞->就绪 关键点
	  - sleep()->阻塞->sleep()时间到
	  - 获取同步锁->阻塞->等待同步锁
	  - wait()/join()->阻塞->notify()/notifyAll()
	  - suspend()->阻塞->resume()
   - 运行->死亡 正常执行完run() Error/Exception处理 stop()
### 线程同步
- 解决问题 一个线程方法未执行完毕 另一个线程又开始执行该方法
   - 多线程执行顺序不确定性造成结果不稳定
   - 多线程数据共享产生的操作不完整性 破坏数据
- Synchronized 同步锁
   - 同步方法 针对对象加同步锁
	  - public synchronized void show(String name){} 
	  - 普通方法 锁的是当前方法对应的整个对象（如两个不同的方法调用的是同一个类的属性 则属性对应的实例化对象全部加锁 若为两个不同对象则为不一样的锁）
	  - 静态方法 所有的对象都是同一个锁
   - synchronized(对象){} 针对某一段代码加同步锁
	  - 代码块加入this同步锁 相同锁
	  - 代码块加入不同对象同步锁 不同锁
```
public void test(int i){
	synchronized(this){//表示当前对象的代码块被加了同步锁
		//代码块内部代码
	}
//用this锁代码块代表锁当前对象 
//同一对象其他方法也有synchronized(this)代码块使用的是同一个同步锁
}

public void test(int i,Object obj){
	synchronized(obj){//obj若为不同对象则为不同锁
		//代码块内部代码
	}
}
```
### 线程死锁
- 死锁四个必要条件
   - 互斥 一个资源每次只能被一个进程使用
   - 占有且等待 一个进程因请求资源而阻塞时 对已获得的资源保持不放
   - 不可占有 进程已获得的资源 在末使用完之前 不能强行剥夺
   - 循环等待:若干进程之间形成一种头尾相接的循环等待资源关系
- 解决方法 打破其中一个条件
   - 设定专门的算法/原则 如加锁顺序一致
   - 尽量减少同步资源的定义 避免锁未释放的场景

### 线程通信
- wait() 将当前线程挂起
- notify() 唤醒正在排队等待的同步资源呢 优先级最高者结束等待
- notifyAll() 唤醒排队等待的所有运行资源结束等待
- java.lang.Object提供的三个方法只有在Synchronize方法/代码块中才能使用 否则报java.lang.IllegalMonitorStateException异常

## 快捷键

### Control+/ 注释
### Control+N 生成get set函数
### Fn+O 方法重写
### Win+R 运行

## 疑问
- io流/反射等很多情况下报异常  加上try-catch后又不会显示异常?
   - 编译器提示为提防有可能异常进行兜底


