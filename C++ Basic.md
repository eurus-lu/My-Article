# C++ Basic

# 01入门

**1.1** 

创建项目：右键源文件-新建项

cout<<”hello world”<<endl;

system(“pause”);

 

**1.2** 

单行注释：// 描述信息

多行注释： /* 描述信息 */

 

**1.3**

C++在创建变量时，必须给变量一个初始值，否则会报错

 

**1.4**

常量：用于记录程序中不可更改的数据

\#define 宏常量： #define 常量名 常量值

const 数据类型 常量名 = 常量值

const int month = 12;

​     cout << "一年里总共有 " << month << " 个月份" << endl;

​     //month = 24; //报错，常量是不可以修改的

 

**2.1**

数据类型              占用空间           取值范围

short(短整型)           2字节          (-2^15 ~ 2^15-1)

int(整型)               4字节          (-2^31 ~ 2^31-1)

long(长整形)        Windows为4字节，  (-2^31 ~ 2^31-1)

Linux为4字节(32位)，8字节(64位)    

long long(长长整形)      8字节          (-2^63 ~ 2^63-1)

拓展：求次幂函数pow(x,y)求x^y

 

**2.2整型**

统计数据类型所占内存大小

sizeof( 数据类型 / 变量)

short < int <= long <= long long

```
cout << "short 类型所占内存空间为： " << sizeof(short) << endl;
```

 

**2.3实型（浮点型）：表示小数**

数据类型              占用空间           有效数字范围

float (单精度)            4字节             7位有效数字

double (双精度)         8字节             15～16位有效数字

 

**2.4字符型**

语法：char ch = 'a';

单引号且只能有一个字符

字符型变量只占用1个字节

并不是把字符本身放到内存中存储，而是将对应的ASCII编码放入到存储单元

```
         char ch = 'a';
         cout << (int)ch << endl;  //查看字符a对应的ASCII码
         ch = 97; //可以直接用ASCII给字符型变量赋值
```

ASCII 码大致由以下两部分组成：

ASCII 非打印控制字符： ASCII 表上的数字 0-31 分配给了控制字符，用于控制像打印机等一些外围设备。

ASCII 打印字符：数字 32-126 分配给了能在键盘上找到的字符，当查看或打印文档时就会出现。

32  (space)

48  0   57  9

65  A   90  Z

97  a   122 z

 

**2.5转义字符：用于表示一些不能显示出来的ASCII字符**

\n  换行(LF) ，将当前位置移到下一行开头  010（ASCII值）

\r   回车(CR) ，将当前位置移到本行开头   013

\t   水平制表(HT) （跳到下一个TAB位置） 009

\\   代表一个反斜线字符""               092

 

**2.6 字符串型**

C风格字符串： char 变量名[] = "字符串值"

C++风格字符串： string 变量名 = "字符串值"

（C++风格字符串，需要加入头文件#include<string>）

 

**2.7 布尔类型 bool**

布尔数据类型代表真或假的值

bool类型占1个字节大小

 

**2.8 数据的输入**

作用：用于从键盘获取数据

语法： cin >> 变量

 

**3.0运算符**

**运算符类型  作用**

算术运算符  用于处理四则运算

赋值运算符  用于将表达式的值赋给变量

比较运算符  用于表达式的比较，并返回一个真值或假值

逻辑运算符  用于根据表达式的值返回真值或假值

 

**3.1 算术运算符**

%   取模(取余)   10 % 3   1（只有整型变量可以进行取模运算）

++  前置递增    a=2; b=++a; a=3; b=3;（先加后运算或赋值）

++  后置递增    a=2; b=a++; a=3; b=2;（先运算或赋值后加）

--  前置递减    a=2; b=--a;  a=1; b=1;

--  后置递减    a=2; b=a--;  a=1; b=2;

在除法运算中，除数为0，报错

 

**3.3 比较运算符**

**作用：**用于表达式的比较，并返回一个真值或假值

!=  不等于  4 != 3   1（结果）

 

**3.4 逻辑运算符**

**作用：**用于根据表达式的值返回真值或假值

!   非  !a  如果a为假，则!a为真； 如果a为真，则!a为假。

 

**4.1 选择结构**

多条件的if语句：

if(条件1){ 条件1满足执行的语句 }

else if(条件2){条件2满足执行的语句}

... 

else{ 都不满足执行的语句}

 

**4.1.2 三目运算符**

作用： 通过三目运算符实现简单的判断

语法：表达式1 **?** 表达式2 **：**表达式3

如果表达式1的值为真，执行表达式2，并返回表达式2的结果；

如果表达式1的值为假，执行表达式3，并返回表达式3的结果。

 

**4.1.3 switch语句**

**作用：**执行多条件分支语句

```
switch (score)
         {
         case 10:
         case 9:
                 cout << "经典" << endl;
                 break;
         case 8:
                 cout << "非常好" << endl;
                 break;
         case 7:
         case 6:
                 cout << "一般" << endl;
                 break;
         default:
                 cout << "烂片" << endl;
                 break;
         }
```

注意1：switch语句中表达式类型只能是整型或者字符型

注意2：case里如果没有break，那么程序会一直向下执行

总结：与if语句比，对于多条件判断时，switch的结构清晰，执行效率高，缺点是switch不可以判断区间

 

**4.2 循环结构**

4.2.1 while循环语句

**作用：**满足循环条件，执行循环语句

语法： while(循环条件){ 循环语句 }

注意：在执行循环语句时候，程序必须提供跳出循环的出口，否则出现死循环

 

4.2.2 do...while循环语句

作用： 满足循环条件，执行循环语句

语法： do{ 循环语句 } while(循环条件);

**注意：**与while的区别在于==do...while会先执行一次循环语句==，再判断循环条件

 

4.2.3 for循环语句

作用： 满足循环条件，执行循环语句

语法： for(起始表达式;条件表达式;末尾循环体) { 循环语句; }

 

**4.3 跳转语句**

4.3.1 break语句

作用: 用于跳出==选择结构==或者==循环结构==

break使用的时机：

出现在switch条件语句中，作用是终止case并跳出switch

出现在循环语句中，作用是跳出当前的循环语句

出现在嵌套循环中，跳出最近的内层循环语句

 

4.3.2 continue语句

**作用：**在==循环语句==中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环

 

4.3.3 goto语句

**作用：**可以无条件跳转语句

语法： goto 标记;

**解释：**如果标记的名称存在，执行到goto语句时，会跳转到标记的位置

注意：在程序中不建议使用goto语句，以免造成程序流程混乱

```
cout << "1" << endl;
         goto FLAG;
         cout << "2" << endl;
         cout << "3" << endl;
         cout << "4" << endl;
         FLAG:
         cout << "5" << endl;
```

注意：标记无需定义，只需出现在下文中，且goto位置标记为冒号。

 

**5 数组**

**特点1：**数组中的每个==数据元素都是相同的数据类型==

**特点2：**数组是由==连续的内存==位置组成的

 

**5.2 一维数组**

一维数组定义的三种方式：

数据类型 数组名[ 数组长度 ];

数据类型 数组名[ 数组长度 ] = { 值1，值2 ...};

数据类型 数组名[ ] = { 值1，值2 ...};

总结1：数组中下标是从0开始索引

总结2：直接打印数组名，可以查看数组所占内存的首地址

总结3：对数组名进行sizeof，可以获取整个数组占内存空间的大小

注意：数组名是常量，不可以赋值

 

5.2.3 冒泡排序

作用： 最常用的排序算法，对数组内元素进行排序

比较相邻的元素。如果第一个比第二个大，就交换他们两个。

对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值。

重复以上的步骤，每次比较次数-1，直到不需要比较

 

**5.3 二维数组**

二维数组定义的四种方式：

数据类型 数组名[ 行数 ][ 列数 ];

数据类型 数组名[ 行数 ][ 列数 ] = { {数据1，数据2 } ，{数据3，数据4 } };

数据类型 数组名[ 行数 ][ 列数 ] = { 数据1，数据2，数据3，数据4};

数据类型 数组名[ ][ 列数 ] = { 数据1，数据2，数据3，数据4};

建议：以上4种定义方式，利用==第二种更加直观，提高代码的可读性==

 

**6 函数**

**作用：**将一段经常使用的代码封装起来，减少重复代码

函数的定义一般主要有5个步骤：

返回值类型 ：一个函数可以返回一个值。在函数定义中

函数名：给函数起个名称

参数列表：使用该函数时，传入的数据

函数体语句：花括号内的代码，函数内需要执行的语句

return表达式： 和返回值类型挂钩，函数执行完后，返回相应的数据

 

**6.3 函数的调用**

**功能：**使用定义好的函数

语法： 函数名（参数）

总结：函数定义里小括号内称为形参，函数调用时传入的参数称为实参

 

**6.4 值传递**

所谓值传递，就是函数调用时实参将数值传入给形参

值传递时，==如果形参发生变化，并不会影响实参==

当函数声明void时候，不需要返回值，可以不写return

 

**6.6 函数的声明**

作用： 告诉编译器函数名称及如何调用函数。函数的实际主体可以单独定义。

函数的声明可以多次，但是函数的定义只能有一次

 

**6.7 函数的分文件编写**

**作用：**让代码结构更加清晰

函数分文件编写一般有4个步骤

创建后缀名为.h的头文件

创建后缀名为.cpp的源文件

在头文件中写函数的声明

在源文件中写函数的定义

```
//swap.h文件
#include<iostream>
using namespace std;
 
//实现两个数字交换的函数声明
void swap(int a, int b);
//swap.cpp文件
#include "swap.h"
 
void swap(int a, int b)
{
         int temp = a;
         a = b;
         b = temp;
         cout << "a = " << a << endl;
         cout << "b = " << b << endl;
}
//main函数文件
#include "swap.h"
int main() {
         int a = 100;
         int b = 200;
         swap(a, b);
         system("pause");
         return 0;
}
```

 

**7 指针**

指针的作用： 可以通过指针间接访问内存

内存编号是从0开始记录的，一般用十六进制数字表示

可以利用指针变量保存地址

 

**7.2 指针变量的定义和使用**

指针变量定义语法： 数据类型 * 变量名；

普通变量存放的是数据,指针变量存放的是地址

指针变量可以通过" * "操作符，操作指针变量指向的内存空间，这个过程称为解引用

总结1： 我们可以通过 & 符号 获取变量的地址

总结2：利用指针可以记录地址

总结3：对指针变量解引用，可以操作指针指向的内存

总结4：所有指针类型在32位操作系统下是4个字节（int * char * float * double *）

 

**7.4 空指针和野指针**

空指针：指针变量指向内存中编号为0的空间

**用途：**初始化指针变量

**注意：**空指针指向的内存是不可以访问的

```
int * p = NULL;
```

野指针：指针变量指向非法的内存空间

```
int * p = (int *)0x1100;
```

总结：空指针和野指针都不是我们申请的空间，因此不要访问，访问报错。

 

**7.5 const修饰指针**

const修饰指针有三种情况：

const修饰指针 --- 常量指针

const修饰常量 --- 指针常量

const即修饰指针，又修饰常量

```
//const修饰的是指针，指针指向可以改，指针指向的值不可以更改
         const int * p1 = &a; 
         p1 = &b; //正确
         //*p1 = 100;  报错
         
 
         //const修饰的是常量，指针指向不可以改，指针指向的值可以更改
         int * const p2 = &a;
         //p2 = &b; //错误
         *p2 = 100; //正确
 
    //const既修饰指针又修饰常量
         const int * const p3 = &a;
         //p3 = &b; //错误
         //*p3 = 100; //错误
```

 

**7.6 指针和数组**

**作用：**利用指针访问数组中元素，数组元素地址连续

 

**7.7 指针和函数**

**作用：**利用指针作函数参数，可以修改实参的值

```
void swap2(int * p1, int *p2)
{
         int temp = *p1;
         *p1 = *p2;
         *p2 = temp;
}
 
void main() {
         int a = 10;
         int b = 20;
         swap2(&a, &b); //地址传递会改变实参
}
```

注意：当数组名传入到函数作为参数时，被退化为指向首元素的指针

```
void bubbleSort(int * arr, int len)  //int * arr 也可以写为int arr[]
{}
int main() {
         bubbleSort(arr, len);
}
```

 

**8 结构体**

结构体属于用户==自定义的数据类型==，允许用户存储不同的数据类型

语法：struct 结构体名 { 结构体成员列表 }；

通过结构体创建变量的方式有三种：

struct 结构体名 变量名

struct 结构体名 变量名 = { 成员1值 ， 成员2值...}

定义结构体时顺便创建变量

```
struct student
{
         //成员列表
         string name;  //姓名
         int age;      //年龄
         int score;    //分数
}stu3; //结构体变量创建方式3 
 
int main() {
         //结构体变量创建方式1
         struct student stu1; //struct 关键字可以省略
         stu1.name = "张三";
         stu1.age = 18;
         stu1.score = 100;
         //结构体变量创建方式2
         struct student stu2 = { "李四",19,60 };
         //结构体变量创建方式3
         stu3.name = "王五";
         stu3.age = 18;
         stu3.score = 80;
}
```

总结1：定义结构体时的关键字是struct，不可省略

总结2：创建结构体变量时，关键字struct可以省略

总结3：结构体变量利用操作符 ''.'' 访问成员

 

**8.3 结构体数组**

**作用：**将自定义的结构体放入到数组中方便维护

语法： struct 结构体名 数组名[元素个数] = { {} , {} , ... {} }

 

**8.4 结构体指针**

**作用：**通过指针访问结构体中的成员

利用操作符 -> 可以通过结构体指针访问结构体属性

```
struct student * p = &stu;
         p->score = 80; //指针通过 -> 操作符可以访问成员
```

 

**8.5 结构体嵌套结构体**

作用： 结构体中的成员可以是另一个结构体

 

**8.6 结构体做函数参数**

**作用：**将结构体作为参数向函数中传递

传递方式有两种：

值传递

地址传递

```
//值传递
void printStudent(student stu )
{
         stu.age = 28;
}
 
//地址传递
void printStudent2(student *stu)
{
         stu->age = 28;
}
 
int main() {
         student stu = { "张三",18,100};
         //值传递
         printStudent(stu);
         //地址传递
         printStudent2(&stu);
}
```

总结：如果不想修改主函数中的数据，用值传递，反之用地址传递

 

**8.7 结构体中 const使用场景**

**作用：**用const来防止误操作

```
void printStudent(const student *stu) //加const防止函数体中的误操作
{
         //stu->age = 100; //操作失败，因为加了const修饰
}
```

 


 

 

# 02通讯录案例

Sizeof只能输出数组定义的长度，判断有效数位需加计数变量

添加：判断是否数组已满

显示、删除、查找、修改：判断检索位置是否为空

清空：计数变量置零，逻辑清空即可

```
system("cls");//清屏
```


 

 

 

# 03核心编程

本阶段主要针对C++==面向对象==编程技术做详细讲解，探讨C++中的核心和精髓

面向对象的编程方式使得每一个类都只做一件事。面向过程会让一个类越来越全能，就像一个管家一样做了所有的事。而面向对象像是雇佣了一群职员，每个人做一件小事，各司其职，最终合作共赢！

**面向过程：**

优点：性能比面向对象高，因为类调用时需要实例化，开销比较大，比较消耗资源;比如单片机、嵌入式开发、 Linux/Unix等一般采用面向过程开发，性能是最重要的因素。 

缺点：没有面向对象易维护、不易复用、不易扩展、耦合度高

**面向对象：**

优点：易维护、易复用、易扩展，由于面向对象有封装、继承、多态性的特性，可以设计出低耦合的系统，使系统 更加灵活、更加易于维护 

缺点：性能比面向过程低

 

**1 内存分区模型**

C++程序在执行时，将内存大方向划分为4个区域：

代码区：存放函数体的二进制代码，由操作系统进行管理的

全局区：存放全局变量和静态变量以及常量

栈区：由编译器自动分配释放, 存放函数的参数值,局部变量等

堆区：由程序员分配和释放,若程序员不释放,程序结束时由操作系统回收

 

**1.1 程序运行前**

在程序编译后，生成了exe可执行程序，未执行该程序前分为两个区域

代码区：

存放 CPU 执行的机器指令

代码区是共享的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可

代码区是只读的，使其只读的原因是防止程序意外地修改了它的指令

全局区：

全局变量和静态变量存放在此.

全局区还包含了常量区, 字符串常量和其他常量也存放在此.

==该区域的数据在程序结束后由操作系统释放==.

总结：

C++中在程序运行前分为全局区和代码区

代码区特点是共享和只读

全局区中存放全局变量、静态变量、常量

常量区中存放 const修饰的全局常量 和 字符串常量

 

**1.2 程序运行后**

栈区：

由编译器自动分配释放, 存放函数的参数值,局部变量等

```
int * func()
{
         int a = 10;//局部变量 存放在栈区 栈区数据在函数执行完后自动是否
         return &a;//返回局部变量地址（实际上是非法操作）
}
int main() {
         int *p = func();//接收函数返回值
         cout << *p << endl;//第一次正确打印是因为编译器做了一次保留
         cout << *p << endl;//第二次数据不再保留 打印乱码
}
```

注意事项：不要返回局部变量的地址，栈区开辟的数据由编译器自动释放

形参同样存放栈区，函数运行完毕也会释放，不要返回形参的值

堆区：

由程序员分配释放,若程序员不释放,程序结束时由操作系统回收

在C++中主要利用new在堆区开辟内存

```
int* func()
{//函数中栈区指针*a指向堆区数据10 即便*a释放 对应地址指向的10依旧存在
         int* a = new int(10);//重要区别 存放堆区 不释放则程序结束前一直保留
         return a;
}
```

总结：

堆区数据由程序员管理开辟和释放

堆区数据利用new关键字进行开辟内存

 

**1.3 new操作符**

C++中利用==new==操作符在堆区开辟数据

堆区开辟的数据，由程序员手动开辟，手动释放，释放利用操作符 ==delete==

语法： new 数据类型

利用new创建的数据，会返回该数据对应的类型的指针

```
int* func()
{
         int* a = new int(10);
         return a;
}
int main() {
         int *p = func();
         //利用delete释放堆区数据
         delete p;
         //cout << *p << endl; //报错，释放的空间不可访问
}
```

 

```
//堆区开辟数组
int main() {
         int* arr = new int[10];
         for (int i = 0; i < 10; i++)
         {
                 arr[i] = i + 100;
         }
         //释放数组 delete 后加 []
         delete[] arr;
}
```

关键字 delete 释放地址

**2 引用**

**作用： **给变量起别名

语法： 数据类型 &别名 = 原名

注意：引用必须初始化，引用在初始化后，不可以改变

 

**2.3 引用做函数参数**

**作用：**函数传参时，可以利用引用的技术让形参修饰实参

**优点：**可以简化指针修改实参

思想：更改别名数值即为更改原名数值

总结：通过引用参数产生的效果同按地址传递是一样的。引用的语法更清楚简单

引用可以命名与原参相同

 

**2.4 引用做函数返回值**

作用：引用是可以作为函数的返回值存在的

注意：不要返回局部变量引用

用法：函数调用作为左值

```
//返回静态变量引用
int& test02() {//引用函数 函数名前加 &
         static int a = 20;
         return a;
}
int main() {
         //如果函数做左值，那么必须返回引用
         int& ref2 = test02();
         cout << "ref2 = " << ref2 << endl;
         test02() = 1000;//左值赋值 因test02()运行结束返回a的引用 对返回a的引用进行操作 即对应更改a值 ref2 为别名
//如果函数的返回值是引用 这个函数调用可以作为左值
         cout << "ref2 = " << ref2 << endl;
}
```

 

**2.5 引用的本质**

本质：引用的本质在c++内部实现是一个指针常量.

指针常量：指针的指向是不可以修改的，指针的值可以修改的

编译器自动解引用 使用时直接当成同一值即可

```
//发现是引用，转换为 int* const ref = &a;
void func(int& ref){
         ref = 100; // ref是引用，转换为*ref = 100
}
int main(){
         int a = 10;
    //自动转换为 int* const ref = &a; 指针常量是指针指向不可改，也说明为什么引用不可更改
         int& ref = a; 
         ref = 20; //内部发现ref是引用，自动帮我们转换为: *ref = 20;
         cout << "a:" << a << endl;
         cout << "ref:" << ref << endl;
         func(a);
         return 0;
}
```

结论：C++推荐用引用技术，因为语法方便，引用本质是指针常量，但是所有的指针操作编译器都帮我们做了

 

**2.6 常量引用**

**作用：**常量引用主要用来修饰形参，防止误操作

在函数形参列表中，可以加==const修饰形参==，防止形参改变实参

用作打印 定值运算等操作

```
void showValue(const int& v) {
         cout << v << endl;
}
```

 

**3 函数提高**

在C++中，函数的形参列表中的形参是可以有默认值的。

语法： 返回值类型 函数名 （参数= 默认值）{}

注意：

\1. 如果某个位置参数有默认值，那么从这个位置往后，从左向右，必须都要有默认值

\2. 如果函数声明（仅有函数头）有默认值，函数实现（即函数名加大括号内容）的时候就不能有默认参数

\3. 如果有传入数据则使用传入数据，无传入则用默认值

 

**3.2 函数占位参数**

C++中函数的形参列表里可以有占位参数，用来做占位，调用函数时必须填补该位置

语法： 返回值类型 函数名 (数据类型){}

```
//函数占位参数 ，占位参数也可以有默认参数
void func(int a, int) {}
int main() {
         func(10,10); //占位参数必须填补
}
```

 

**3.3 函数重载**

**作用：**函数名可以相同，提高复用性

函数重载满足条件：

1.同一个作用域下

2.函数名称相同

3.函数参数类型不同 或者 个数不同 或者 顺序不同

注意: 函数的返回值不可以作为函数重载的条件

void func(){}

void func(int a) {}

void func(double a) {}

void func(int a ,double b){}

void func(double a ,int b){}

//函数返回值不可以作为函数重载条件

//int func(double a, int b){}

int main() {

​     func();

​     func(10);

​     func(3.14);

​     func(10,3.14);

​     func(3.14 , 10);//对应调取不同的函数

}

注意：

1.引用作为重载条件

2.函数重载碰到函数默认参数

```
void func(int &a) {}
void func(const int &a) {}
//2、函数重载碰到函数默认参数
void func2(int a, int b = 10) {}
void func2(int a){}
int main() {
         int a = 10;
         func(a); //调用无const
         func(10);//调用有const
         //func2(10); //碰到默认参数产生歧义，需要避免
}
```

 

**4 类和对象**

C++面向对象的三大特性为：==封装、继承、多态==

C++认为==万事万物都皆为对象==，对象上有其属性和行为

 

**4.1 封装**

封装意义一：

将属性和行为作为一个整体，表现生活中的事物

在设计类的时候，属性和行为写在一起，表现事物

 

语法： class 类名{ 访问权限： 属性 / 行为 };

```
const double PI = 3.14;
//封装一个圆类，求圆的周长
class Circle
{
public:  //访问权限  公共的权限
         //属性
         int m_r;//半径
         //行为
         double calculateZC()
         {
                 return  2 * PI * m_r;
         }
};
int main() {
         //通过圆类，创建圆的对象 c1就是一个具体的圆
         Circle c1;
         c1.m_r = 10; //给圆对象的半径 进行赋值操作
         cout << "圆的周长为： " << c1.calculateZC() << endl;
}
```

封装意义二：

类在设计时，可以把属性和行为放在不同的权限下，加以控制

访问权限有三种：

public 公共权限     成员 类内可以访问 类外可以访问

protected 保护权限   成员 类内可以访问 类外不可以访问 继承中子类可以访问夫类

private 私有权限     成员 类内可以访问 类外不可以访问 继承中子类不可以访问夫类

```
class Person
{
public: //姓名  公共权限
         string m_Name;
protected: //汽车  保护权限
         string m_Car;
private: //银行卡密码  私有权限
         int m_Password;
};
```

 

**4.1.2 struct和class区别**

在C++中 struct和class唯一的区别就在于 默认的访问权限不同

区别：

struct 默认权限为公共

class 默认权限为私有

```
class C1
{
         int  m_A; //默认是私有权限
};
struct C2
{
         int m_A;  //默认是公共权限
};
```

 

**4.1.3 成员属性设置为私有**

**优点1：**将所有成员属性设置为私有，可以自己控制读写权限

可读可写/只读/只写-通过公共权限行为操作

**优点2：**对于写权限，我们可以检测数据的有效性

公共权限行为操作时 可加以if判断 确认其是否有效 无效可赋初值 return；

 

**类与对象练习案例重点：**

1.类设计流程：创建类 设计属性（私有） 设计行为（公共） 实现功能（成员函数实现/全局函数实现）

2.函数调用类对象 void func(className c1)

3.类中属性可以为另一个类

4.大工程中不应所有类放在一个文件中 应写入其他文件 并用头文件调用

\#pragma once //防止头文件重复包含

头文件写类保留函数头做函数声明以及成员声明即可 行为可以全删掉

源文件中 包含头文件 留下行为（函数所有实现）即可 Class创建类以及成员属性都可删掉 但需要在成员函数前加作用域 void className：：func() 双冒号

Alt+/ 补全分号快捷键

 

**4.2 对象的初始化和清理**

c++利用了构造函数和析构函数解决对象的初始化和清理问题，这两个函数将会被编译器自动调用，完成对象初始化和清理工作。

若类行为不设定构造与析构，编译器自动提供的构造函数和析构函数是空实现（即函数大括号内无语句）。

 

构造函数：主要作用在于创建对象时为对象的成员属性赋值，构造函数由编译器自动调用，无须手动调用。

构造函数语法：类名(){}

构造函数，没有返回值也不写void

函数名称与类名相同

构造函数可以有参数，因此可以发生重载

程序在调用对象时候会自动调用构造，无须手动调用,而且只会调用一次

 

析构函数：主要作用在于对象销毁前系统自动调用，执行一些清理工作。

析构函数语法： ~类名(){}

析构函数，没有返回值也不写void

函数名称与类名相同,在名称前加上符号 ~

析构函数不可以有参数，因此不可以发生重载

程序在对象销毁前会自动调用析构，无须手动调用,而且只会调用一次

 

**4.2.2 构造函数的分类及调用**

两种分类方式：

按参数分为： 有参构造和无参构造（默认为无参）

按类型分为： 普通构造和拷贝构造

三种调用方式：括号法（推荐使用） 显示法 隐式转换法

```
class Person {
public:
         //无参（默认）构造函数
         Person() {}
         //有参构造函数
         Person(int a) {
                 age = a;
         }
         //拷贝构造函数
         Person(const Person& p) {
                 age = p.age;
         }
         //析构函数
         ~Person() {}
public:
         int age;
};
//调用构造函数
void test02() {
         //2.1  括号法，常用
         Person p; //调用无参构造函数
         Person p1(10); //调用有参构造函数
         Person p1(p); //调用拷贝构造函数
         //注意1：调用无参构造函数不能加括号，如果加了编译器认为这是一个函数声明
         //Person p2();
         //2.2 显式法
         Person p; 
         Person p2 = Person(10); 
         Person p3 = Person(p2);
         //Person(10)单独写就是匿名对象  当前行结束之后，马上析构
         //2.3 隐式转换法
         Person p; 
         Person p4 = 10; // Person p4 = Person(10); 
         Person p5 = p4; // Person p5 = Person(p4); 
         //注意2：不能利用 拷贝构造函数 初始化匿名对象 编译器认为是对象声明
         //Person p5(p4);
}
```

注意3：拷贝构造定义 加const 加&符号

**4.2.3 拷贝构造函数调用时机**

C++中拷贝构造函数调用时机通常有三种情况

使用一个已经创建完毕的对象来初始化一个新对象

值传递的方式给函数参数传值

以值方式返回局部对象

```
/2. 值传递的方式给函数参数传值
//相当于Person p1 = p;
void doWork(Person p1) {}//出现一次构建与析构
void test02() {
         Person p; //无参构造函数
         doWork(p);
}
//3. 以值方式返回局部对象
Person doWork2()
{
         Person p1;
         return p1;
}
void test03()
{
         Person p = doWork2();//因p1在doWork2()执行完毕被释放 p地址与p1不同
}
```

 

**4.2.4 构造函数调用规则**

默认情况下，c++编译器至少给一个类添加3个函数

1．默认构造函数(无参，函数体为空)

2．默认析构函数(无参，函数体为空)

3．默认拷贝构造函数，对属性进行值拷贝（进行默认拷贝不写赋值语句也会自动赋值）

构造函数调用规则如下：

如果用户定义有参构造函数，c++不在提供默认无参构造，但是会提供默认拷贝构造

（即定义中用户只定义Person(int a)，函数中调用Person p会报错）

如果用户定义拷贝构造函数，c++不会再提供其他构造函数

 

**4.2.5 深拷贝与浅拷贝**

深浅拷贝是面试经典问题，也是常见的一个坑

浅拷贝：简单的赋值拷贝操作

深拷贝：在堆区重新申请空间，进行拷贝操作

```
class Person {
public:
         //有参构造函数
         Person(int age ,int height) {
                 cout << "有参构造函数!" << endl;
                 m_age = age;
                 m_height = new int(height);//解决异常中断方法：在编译器同一个值在不同构造函数中创建不同的堆区地址存储，以免释放后再删问题
         }
         //拷贝构造函数  
         Person(const Person& p) {
                 cout << "拷贝构造函数!" << endl;
         //如果不利用深拷贝在堆区创建新内存，会导致浅拷贝带来的重复释放堆区问题
                 m_age = p.m_age;
                 m_height = new int(*p.m_height);
                 
         }
         //析构函数
         ~Person() {//析构函数作用:释放堆区数据
                 cout << "析构函数!" << endl;
                 if (m_height != NULL)
                 {
                          delete m_height;
                          m_height = NULL //防止野指针出现
                 }
         }
public:
         int m_age;
         int* m_height;
};
void test01()
{
         Person p1(18, 180); 
         Person p2(p1); //栈的先进后出会导致析构释放了堆区内存再调用的异常中断
}
 
int main() {
         test01();
}
```

总结：如果属性有在堆区开辟的，一定要自己提供拷贝构造函数，防止浅拷贝带来的问题

 

**4.2.6 初始化列表**

作用：

C++提供了初始化列表语法，用来初始化属性

语法：构造函数()：属性1(值1),属性2（值2）... {}

```
class Person {
public:
         ////传统方式初始化
         //Person(int a, int b, int c) {
         //       m_A = a;
         //       m_B = b;
         //       m_C = c;
         //}
         //初始化列表方式初始化
         Person(int a, int b, int c) :m_A(a), m_B(b), m_C(c) {}
private:
         int m_A;
         int m_B;
         int m_C;
};
```

 

**4.2.7 类对象作为类成员**

C++类中的成员可以是另一个类的对象，我们称该成员为 对象成员

例如：

```
class A {}
class B
{
    A a；
}// B类中有对象A作为成员，A为对象成员
//当类中成员是其他类对象时，我们称该成员为 对象成员
//构造的顺序是 ：先调用对象成员的构造，再调用本类构造
//析构顺序与构造相反
```

 

**4.2.8 静态成员**

静态成员就是在成员变量和成员函数前加上关键字static，称为静态成员

静态成员分为：

1.静态成员变量——所有对象共享同一份数据 在编译阶段分配内存 类内声明，类外初始化

2.静态成员函数——所有对象共享同一个函数 静态成员函数只能访问静态成员变量

```
class Person
{
public:
         static int m_A; //静态成员变量
private:
         static int m_B; //静态成员变量也是有访问权限的
};
int Person::m_A = 10;
int Person::m_B = 10;
void test01()
{
         //静态成员变量两种访问方式
         //1、通过对象
         Person p1;
         p1.m_A = 100;
         cout << "p1.m_A = " << p1.m_A << endl;//=100
         Person p2;
         p2.m_A = 200;
         cout << "p1.m_A = " << p1.m_A << endl; //共享同一份数据=200
         cout << "p2.m_A = " << p2.m_A << endl;//=200
         //2、通过类名
         cout << "m_A = " << Person::m_A << endl;//=200
         //cout << "m_B = " << Person::m_B << endl; //私有权限访问不到
}
```

 

```
class Person
{
public:
         static void func()
         {
                 cout << "func调用" << endl;
                 m_A = 100;// 静态成员函数只能访问静态成员变量
                 //m_B = 100; //错误，不可以访问非静态成员变量
         }
         static int m_A; //静态成员变量
         int m_B; // 
private:
         //静态成员函数也是有访问权限的
         static void func2()
         {
                 cout << "func2调用" << endl;
         }
};
int Person::m_A = 10;//静态成员变量特点：类内声明 类外初始化
void test01()
{
         //静态成员变量两种访问方式
         //1、通过对象
         Person p1;
         p1.func();
         //2、通过类名
         Person::func();//程序共享一个函数 不需要创建对象也可以访问
         //Person::func2(); //私有权限访问不到
}
```

 

**4.3 C++对象模型和this指针**

在C++中，类内的成员变量和成员函数分开存储

只有非静态成员变量才属于类的对象上（即占用对象的内存空间）

空对象占用内存空间为：1

原因：C++编译器会给每个空对象也分配一个字节空间，是为了区分空对象占内存的位置，每个空对象也应该有一个独一无二的内存地址，若有一个非静态成员变量如 int a 则占用空间变为4，不再需要内存空间1占位

 

**4.3.2 this指针概念**

this指针指向被调用的成员函数所属的对象

this指针是隐含每一个非静态成员函数内的一种指针

this指针不需要定义，直接使用即可

程序员编码规范：成员变量命名 m_XXX m代表menber 区别于成员函数形参 以防同名不读取成员变量产生问题

另一个解决问题方法：this指针

```
public:
         Person(int age)
         {
                 // age = age;//出现成员变量不读入函数的问题
                 // this指针指向被调用的成员函数所属的对象，此处指向p1
                 this->age = age;
         }
         Person& PersonAddPerson(Person p)//返回本体用引用方式进行返回，若返回的为值，则为拷贝构造函数多次创建新的p2对象存在不同地址（每次都返回p2=10）
         {
                 this->age += p.age;
                 //返回对象本身
                 return *this;
         }
         int age;//m_age
};
void test01()
{
         Person p1(10);
         cout << "p1.age = " << p1.age << endl;
         Person p2(10);
         //链式编程思想——可无限追加
         p2.PersonAddPerson(p1).PersonAddPerson(p1).PersonAddPerson(p1);
         //多次调用同一函数需明确每次返回为p2本身
         cout << "p2.age = " << p2.age << endl;
}
 
```

 

**4.3.3 空指针访问成员函数**

C++中空指针也是可以调用成员函数的，但是也要注意有没有用到this指针

如果用到this指针，需要加以判断保证代码的健壮性

```
class Person {
public:
         void ShowClassName() {
                 cout << "我是Person类!" << endl;
         }
         void ShowPerson() {
                 if (this == NULL) {//用到空指针调用应判断this 保证健壮性
                          return;
                 }
                 cout << mAge << endl;//this指针此处是默认指向mAge的，而在主函数中设为空指针后，空指针p->ShowPerson()调用则会导致空指针指成员变量而报错
         }
public:
         int mAge;
};
void test01()
{
         Person * p = NULL;
         p->ShowClassName(); //空指针，可以调用成员函数
         p->ShowPerson();  //但是如果成员函数中用到了this指针，就不可以了
}
```

 

**4.3.4 const修饰成员函数**

常函数：

成员函数后加const后我们称为这个函数为常函数

```
void ShowPerson() const {}
```

常函数内不可以修改成员属性，也不可更改常函数内this指针指向

```
//this = NULL; //this->mA = 100;//报错
```

成员属性声明时加关键字mutable后，在常函数中依然可以修改

```
mutable int m_B; //可修改 可变的
```

常对象：

声明对象前加const称该对象为常对象

```
const Person person; //常量对象                                      
//person.mA = 100; //常对象不能修改成员变量的值,但是可以访问
person.m_B = 100; //但是常对象可以修改mutable修饰成员变量
```

常对象只能调用常函数

 

**4.4 友元**

友元的目的就是让一个函数或者类 访问另一个类中私有成员

友元的关键字为 ==friend==

友元的三种实现：1全局函数做友元2类做友元3成员函数做友元

```
class Building
{
//告诉编译器 goodGay全局函数 是 Building类的好朋友，可以访问类中的私有内容，要放在类上方声明void goodGay(Building * building)函数才可以访问私有成员
         friend void goodGay(Building * building);
//告诉编译器 goodGay类是Building类的好朋友，可以访问到Building类中私有内容
         friend class goodGay;
//告诉编译器  goodGay类中的visit成员函数 是Building好朋友，可以访问私有内容
         friend void goodGay::visit();
public:
         Building()
         {
                 this->m_SittingRoom = "客厅";
                 this->m_BedRoom = "卧室";
         }
public:
         string m_SittingRoom; //客厅
private:
         string m_BedRoom; //卧室
};
void goodGay(Building * building)//指针或引用都可，全局函数
{
         cout << "好基友正在访问： " << building->m_SittingRoom << endl;
         cout << "好基友正在访问： " << building->m_BedRoom << endl;
}
void test01()
{
         Building b;
         goodGay(&b);//传地址给指针
}
```

 

**4.5 运算符重载**

运算符重载概念：对已有的运算符重新进行定义，赋予其另一种功能，以适应不同的数据类型

 

**4.5.1 加号运算符重载**

作用：实现两个自定义数据类型相加的运算

关键字 operator+

```
Person operator+(const Person& p) {//实现两个类中m_A与m_B分别相加
                 Person temp;
                 temp.m_A = this->m_A + p.m_A;
                 temp.m_B = this->m_B + p.m_B;
                 return temp;
         }
```

定义成员函数实现加号运算 将函数命名为关键字operator+ 即可简化调用过程

本质调用 Person p3 = p2.operaor+(p1);

简化后 Person p3 = p2 + p1;

```
Person operator+( Person& p1，Person& p1) {
                 Person temp;
                 temp.m_A = this->m_A + p.m_A;
                 temp.m_B = this->m_B + p.m_B;
                 return temp;
         }
```

定义全局函数实现重载 本质调用 Person p3 = operaor+(p1，p2);

总结： 运算符重载可以发生函数重载（同名定义形参不同）

总结1：对于内置的数据类型的表达式的的运算符是不可能改变的（如int相加不允许1+1=3）

总结2：不要滥用运算符重载（加号运算符函数里有减法运算，容易混乱）

 

**4.5.2 左移运算符重载**

作用：可以输出自定义数据类型（如输出对象名即可输出对象属性）

```
//全局函数实现左移重载 cout<<p  成员函数只能实现p<<cout 与想要的简化不符
//cout为输出流数据对象（类）ostream对象只能有一个 因此需要用引用
ostream& operator<<(ostream& out, Person& p) {
         out << "a:" << p.m_A << " b:" << p.m_B;
         return out;
}
void test() {
         cout << p1 << "hello world" << endl; 
//想实现链式编程，每次cout << p1都返回cout才能继续 若只单次输出cout<<p
//void& operator<<(ostream& out, Person& p)无需return
}
```

总结：重载左移运算符配合友元可以实现输出自定义数据类型（为访问私有属性）

endl 换行

 

**4.5.3 递增运算符重载**

作用： 通过重载递增运算符，实现自加的整型数据

```
         MyInteger& operator++() {//先++ 再返回
                 m_Num++;
                 return *this;
         }
         MyInteger operator++(int) {//先返回后++
                 MyInteger temp = *this; //记录当前本身的值，返回以前的值               m_Num++;//然后让本身的值加1
                 return temp;
         }
void test() {
         MyInteger myInt;
         cout << ++myInt << endl; //前置++ 先++ 再返回
         cout << myInt++ << endl; //后置++ 先返回 再++
}
```

总结： 前置递增返回引用，后置递增返回值

 

**4.5.4 赋值运算符重载**

c++编译器至少给一个类添加4个函数

1.默认构造函数(无参，函数体为空)

2.默认析构函数(无参，函数体为空)

3.默认拷贝构造函数，对属性进行值拷贝

4.赋值运算符 operator=, 对属性进行值拷贝

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题

```
class Person
{
public:
         Person(int age)
         {
                 //将年龄数据开辟到堆区
                 m_Age = new int(age);
         }
         //重载赋值运算符 
         Person& operator=(Person &p)
         {
                 if (m_Age != NULL)
                 {
                          delete m_Age;
                          m_Age = NULL;
                 }
                 //编译器提供的代码是浅拷贝
                 //m_Age = p.m_Age;
                 //提供深拷贝 解决浅拷贝的问题
                 m_Age = new int(*p.m_Age);
                 //返回自身
                 return *this;
         }
         ~Person()
         {
                 if (m_Age != NULL)
                 {
                          delete m_Age;
                          m_Age = NULL;
                 }
         }
         //年龄的指针
         int *m_Age;
};
void test01()
{
         Person p1(18);
         Person p2(20);
 
         Person p3(30);
         p3 = p2 = p1; //赋值操作，最终*p3.m_Age=*p2.m_Age=*p1.m_Age=18
}
```

 

**4.5.5 关系运算符重载**

**作用：**重载关系运算符，可以让两个自定义类型对象进行对比操作

```
         bool operator==(Person & p)
         {
                 if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
                 {
                          return true;
                 }
                 else
                 {
                          return false;
                 }
         }
         bool operator!=(Person & p)
         {
                 if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
                 {
                          return false;//注意判断式还是等号 等号成立!= false
                 }
                 else
                 {
                          return true;
                 }
         }
void test01()
{
         Person a("孙悟空", 18);
         Person b("孙悟空", 18);
         if (a == b)
         {        cout << "a和b相等" << endl;}
         else
         {        cout << "a和b不相等" << endl;}
         if (a != b)
         {        cout << "a和b不相等" << endl;}
         else
         {        cout << "a和b相等" << endl;}
}
```

 

**4.5.6 函数调用运算符重载**

函数调用运算符 () 也可以重载

由于重载后使用的方式非常像函数的调用，因此称为仿函数

仿函数没有固定写法，非常灵活

```
         void operator()(string text)//类1 MyPrint
         {
                 cout << text << endl;
         }
         int operator()(int v1, int v2)//类2 MyAdd
         {
                 return v1 + v2;
         }
void test01()
{
         //重载的（）操作符 也称为仿函数
         MyPrint myFunc;
         myFunc("hello world");
         MyAdd add;
         int ret = add(10, 10); //匿名对象调用 MyAdd()(100, 100)
}
```

 

**4.6 继承**

继承是面向对象三大特性之一

定义某些类时，下级别的成员除了拥有上一级的共性，还有自己的特性。

这个时候我们就可以考虑利用继承的技术，减少重复代码

​                                

class A : public B;

A 类称为子类 或 派生类

B 类称为父类 或 基类

派生类中的成员，包含两大部分：

一类是从基类继承过来的，一类是自己增加的成员。

从基类继承过过来的表现其共性，而新增的成员体现了其个性。

 

**4.6.2 继承方式**

继承的语法：class 子类 : 继承方式 父类

继承方式一共有三种：公共继承 保护继承 私有继承

```
class Base1
{
public: 
         int m_A;
protected:
         int m_B;
private:
         int m_C;
};
//公共继承
class Son1 :public Base1
{
public:
         void func()
         {
                 m_A; //可访问 public权限
                 m_B; //可访问 protected权限
                 //m_C; //不可访问
         }
}; //其他类只能访问到公共权限的m_A
//保护继承
class Son2:protected Base2
{
public:
         void func()
         {
                 m_A; //可访问 protected权限
                 m_B; //可访问 protected权限
                 //m_C; //不可访问
         }
}; //公共权限的m_A也不可访问
//私有继承
class Son3:private Base3//Son3是私有继承，所以继承Son3的属性都无法访问到
```

 

**4.6.3 继承中的对象模型**

父类中非静态成员都被子类继承下去了（sizeof得出全包含并加上子类自己的成员），只是私有成员由编译器给隐藏后访问不到

 

**C++检索工具操作**

开始-菜单-VS开发人员命令提示-定位对应盘 如F：-定位cpp文件夹位置 如 F：/…/text1-输入dir 检查cpp是否存在目录下-输入 cl /d1 reportSingerClassLayout 显示类空间成员

 

**4.6.4 继承中构造和析构顺序**

子类继承父类后，当创建子类对象，也会调用父类的构造函数

总结：继承中 先调用父类构造函数，再调用子类构造函数，析构顺序与构造相反

 

**4.6.5 继承同名成员处理方式**

访问子类同名成员 直接访问即可（成员对象及成员函数都如此）

访问父类同名成员 需要加作用域

```
class Base {
public:
         Base()
         {
                 m_A = 100;
         }
         void func()
         {
                 cout << "Base - func()调用" << endl;
         }
         void func(int a)
         {
                 cout << "Base - func(int a)调用" << endl;
         }
public:
         int m_A;
};
class Son : public Base {
public:
         Son()
         {
                 m_A = 200;
         }
         //当子类与父类拥有同名的成员函数，子类会隐藏父类中所有版本（无论是有参无参还是拷贝）的同名成员函数
         void func()
         {
                 cout << "Son - func()调用" << endl;
         }
public:
         int m_A;
};
void test01()
{
         Son s;
         s.func();
         //如果想访问父类中被隐藏的同名成员函数，需要加父类的作用域
         s.Base::func();
         s.Base::func(10);
}
```

访问方式有两种 通过对象访问及通过类名访问

```
//通过对象访问
         Son s;
         cout << "Son  下 m_A = " << s.m_A << endl;
         cout << "Base 下 m_A = " << s.Base::m_A << endl;
//通过类名访问
         cout << "Son  下 m_A = " << Son::m_A << endl;
         cout << "Base 下 m_A = " << Son::Base::m_A << endl;
```

静态成员和非静态成员出现同名，处理方式一致

访问子类同名成员 直接访问即可

访问父类同名成员 需要加作用域

 

4.6.7 多继承语法

C++允许一个类继承多个类

语法： class 子类 ：继承方式 父类1 ， 继承方式 父类2...

多继承可能会引发父类中有同名成员出现，需要加作用域区分

C++实际开发中不建议用多继承

 

**4.6.8 菱形继承**

菱形继承概念：

两个派生类继承同一个基类

又有某个类同时继承者两个派生类

这种继承被称为菱形继承，或者钻石继承

总结：

菱形继承带来的主要问题是子类继承两份相同的数据（基类），导致资源浪费以及毫无意义

利用虚继承可以解决菱形继承问题

```
//继承前加virtual关键字后，变为虚继承
//此时公共的父类Animal称为虚基类
class Sheep : virtual public Animal {};
class Tuo   : virtual public Animal {};
class SheepTuo : public Sheep, public Tuo {};
void test01()
{
         SheepTuo st;
         st.Sheep::m_Age = 100;
         st.Tuo::m_Age = 200;
         cout << "st.Sheep::m_Age = " << st.Sheep::m_Age << endl;
         cout << "st.Tuo::m_Age = " <<  st.Tuo::m_Age << endl;
         cout << "st.m_Age = " << st.m_Age << endl;//200将100覆盖掉
}
```

底层实现：运用虚继承后 该类对应存储两个父类内容的空间出现vbptr（virtual base pointer）虚基类指针 指向vbtable虚基类表 表中记录了偏移量 对应同一个数据

即虚继承后 两个父类的同名属性数据 只记录了一个 为后出现的数据值

  

 

**4.7 多态**

多态是C++面向对象三大特性之一

多态分为两类

静态多态: 函数重载（不同输入多次调用） 和 运算符重载（operator）属于静态多态，复用函数名

动态多态: 派生类和虚函数实现运行时多态

静态多态和动态多态区别：

静态多态的函数地址早绑定 - 编译阶段确定函数地址

动态多态的函数地址晚绑定 - 运行阶段确定函数地址

总结：

多态满足条件：1有继承关系 2子类重写父类中的虚函数

多态使用条件：父类指针或引用指向子类对象

重写：函数返回值类型 函数名 参数列表 完全一致称为重写

```
class Animal
{
public:
         //加上virtual Speak函数就是虚函数，若无virtual 函数地址在编译阶段就能确定，属于静态联编
         //编译器在编译的时候就不能确定函数调用了，函数地址在运行阶段才能确定，属于动态联编
         virtual void speak()
         {
                 cout << "动物在说话" << endl;
         }
};
class Cat :public Animal
{
public:
         void speak()
         {
                 cout << "小猫在说话" << endl;
         }
};
void DoSpeak(Animal & animal)//定义父类函数 无virtual则输出动物说话
{
         animal.speak();//父类调用子类 virtual虚函数后 输出小猫说话
}
void test01()
{
         Cat cat;
         DoSpeak(cat);
}
```

 

**4.7.2 多态案例一-计算器类**

多态的优点：1代码组织结构清晰2可读性强3利于前期和后期的扩展以及维护

传统计算器写法欲加入新的运算需要修改源码 多态直接加类进行拓展即可

开闭原则：对拓展进行开放，对修改进行关闭

总结：C++开发提倡利用多态设计程序架构，因为多态优点很多

```
//普通实现
class Calculator {
public:
         int getResult(string oper)
         {
                 if (oper == "+") {
                          return m_Num1 + m_Num2;
                 }
                 else if (oper == "-") {
                          return m_Num1 - m_Num2;
                 }
                 else if (oper == "*") {
                          return m_Num1 * m_Num2;
                 }//如果要提供新的运算，需要修改源码
         }
public:
         int m_Num1;
         int m_Num2;
};
//多态实现
class AbstractCalculator
{
public :
         virtual int getResult()
         {
                 return 0;
         }
         int m_Num1;
         int m_Num2;
};//特点 父类不作主要功能描述
```

 

**4.7.3 纯虚函数和抽象类**

在多态中，通常父类中虚函数的实现是毫无意义的，主要都是调用子类重写的内容

因此可以将虚函数改为纯虚函数

纯虚函数语法：virtual 返回值类型 函数名 （参数列表）= 0 ;

```
class Base
{
public:
         virtual void func() = 0;
};
```

当类中有一个纯虚函数，这个类就可称为==抽象类==

抽象类特点：

无法实例化对象

```
void test01()
{
         //base b；//错误，栈区抽象类无法实例化对象
         //base = new Base; // 错误，堆区抽象类无法实例化对象
}
```

子类必须重写抽象类中的纯虚函数，否则也属于抽象类

```
class Son :public Base
{
public:
         virtual void func(){};//必须重写 否则不允许子类创建
};
```

父类调用子类接口

```
         base * base = new Son;//多态技术：父类指针指向子类对象 调用接口
         base->func();
```

 

**4.7.4 多态案例二-制作饮品**

父类所有纯虚函数都要在子类中重写 重写即可加上{}描述具体实现

父类中可写工程函数，将纯虚类按使用顺序排列，调用该函数 运行的内部纯虚函数将在子类中找到对应实现，简化代码

创建堆区数据记得手动释放 以免空间浪费

```
void DoWork(AbstractDrinking* drink) {
// 形参AbstractDrinking* drink= 实参new Coffee 父类指针指向子类对象
         drink->MakeDrink();
         delete drink;
}
void test01() {
         DoWork(new Coffee);
         cout << "--------------" << endl;
         DoWork(new Tea);
}
```

 

**4.7.5 虚析构和纯虚析构**

多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码 造成堆区数据内存泄露

```
         base * base = new Son;//父类指针指向子类对象
         base->func();//父类在析构的时候不会调用子类的析构函数
```

解决方式：将父类中的析构函数改为虚析构或者纯虚析构 则会走子类的析构函数

```
virtual ~Animal(){}
virtual ~Animal() = 0;//声明之后，需要在类外写一个具体实现（区别：纯虚函数不用）
```

虚析构和纯虚析构共性：1可以解决父类指针释放子类对象2都需要有具体的函数实现

虚析构和纯虚析构区别：如果是纯虚析构，该类属于抽象类，无法实例化对象

虚析构语法： virtual ~类名(){}

纯虚析构语法： virtual ~类名() = 0; 类名::~类名(){}（类外写实现）

应用场景：子类中创建堆区成员需要释放，应用多态不会遇到该问题（多态外外部函数创建堆区数据并及时释放）

总结：

\1. 虚析构或纯虚析构就是用来解决通过父类指针释放子类对象

\2. 如果子类中没有堆区数据，可以不写为虚析构或纯虚析构

\3. 拥有纯虚析构函数的类也属于抽象类

 

**4.7.6 多态案例三-电脑组装**

编写步骤：

\1.   构建零件虚类作为父类

\2.   构建工程类，读入零件类数值，调用零件类函数，私有区存储零件类数值

\3.   继承单冒号

\4.   释放

if (m_cpu != NULL)

​       {

​           delete m_cpu;

​           m_cpu = NULL;

​       }

\5.   父类指针指向子类对象

 

**5 文件操作**

程序运行时产生的数据都属于临时数据，程序一旦运行结束都会被释放

通过文件可以将数据持久化

C++中对文件操作需要包含头文件 ==< fstream >==

文件类型分为两种：

文本文件 - 文件以文本的ASCII码形式存储在计算机中

二进制文件 - 文件以文本的二进制形式存储在计算机中，用户一般不能直接读懂它们

操作文件的三大类:

ofstream：写操作

ifstream： 读操作

fstream ： 读写操作

 

**5.1文本文件**

写文件步骤如下：

包含头文件 #include <fstream>

创建流对象 ofstream ofs;

打开文件 ofs.open("文件路径",打开方式);

写数据 ofs << "写入的数据";

关闭文件 ofs.close();

 

打开方式    解释

ios::in       为读文件而打开文件

ios::out     为写文件而打开文件

ios::ate      初始位置：文件尾

ios::app     追加方式写文件

ios::trunc    如果文件存在先删除，再创建

ios::binary   二进制方式

注意： 文件打开方式可以配合使用，利用|操作符

**例如：**用二进制方式写文件 ios::binary | ios:: out

```
#include <fstream>
void test01()
{
         ofstream ofs;
         ofs.open("test.txt", ios::out);
         ofs << "姓名：张三" << endl;
         ofs.close();//操作完毕，要关闭文件
}
```

 

读文件步骤如下：

包含头文件 #include <fstream>

创建流对象 ifstream ifs;

打开文件并判断文件是否打开成功 ifs.open("文件路径",打开方式);

读数据 四种方式读取

关闭文件 ifs.close();

```
//第一种方式 右移运算符放数据
         //char buf[1024] = { 0 };//创建字符数组初始化 大括号
         //while (ifs >> buf)// while读到头读不到数据返回假标志跳出循环
         //{
         //       cout << buf << endl;
         //}
//第二种 用ifs成员函数getline获取一行 参数1读取内容放的位置char* 参数2读几字节count
         //char buf[1024] = { 0 };
         //while (ifs.getline(buf,sizeof(buf)))//数组名指向元素的首地址
         //{
         //       cout << buf << endl;
         //}
//第三种 放到string字符串中 全局getline函数 参数1输入流对象ifs 参数2存储位置
         //string buf;
         //while (getline(ifs, buf))
         //{
         //       cout << buf << endl;
         //}
//第四种 不太推荐使用 文件数据一个个字符读 效率太低 速度慢
         char c;
         while ((c = ifs.get()) != EOF)//get成员函数每次读一个字符 判断是否独到文件尾 EOF – end of file
         {
                 cout << c;
         }
```

 

**5.2 二进制文件**

以二进制的方式对文件进行读写操作

打开方式要指定为 ==ios::binary==

 

写文件

二进制方式写文件主要利用流对象调用成员函数write

函数原型 ：ostream& write(const char * buffer,int len);//为防止调用问题 强转const char*

参数解释：字符指针buffer指向内存中一段存储空间 len是读写的字节数

注意：二进制写文件尽量用char 不用string 否则会出现一些问题

创建流对象可以和打开文件合为一步

```
ofstream ofs("person.txt", ios::out | ios::binary);
```

 

读文件

二进制方式读文件主要利用流对象调用成员函数read

函数原型：istream& read(char *buffer,int len);

参数解释：字符指针buffer指向内存中一段存储空间。len是读写的字节数

 

 


 

 

# 04编程提高

## 1 模板

C++另一种编程思想称为 ==泛型编程== ，主要利用的技术就是模板

C++提供两种模板机制:函数模板和类模板

函数模板作用：建立一个通用函数，其函数返回值类型和形参类型可以不具体制定，用一个虚拟的类型来代表。

语法：

template<typename T>//函数声明或定义

解释：

template --- 声明创建模板

typename --- 表面其后面的符号是一种数据类型，可以用class代替

T --- 通用的数据类型，名称可以替换，通常为大写字母

```
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

注意事项：

自动类型推导，必须推导出一致的数据类型T,才可以使用

模板必须要确定出T的数据类型，才可以使用

 

普通函数与函数模板区别：

普通函数调用时可以发生自动类型转换（隐式类型转换）

函数模板调用时，如果利用自动类型推导，不会发生隐式类型转换

如果利用显示指定类型的方式，可以发生隐式类型转换（建议使用显示指定类型的方式，调用函数模板，因为可以自己确定通用类型T）

 

**1.2.5 普通函数与函数模板的调用规则**

如果函数模板和普通函数都可以实现，优先调用普通函数

可以通过空模板参数列表来强制调用函数模板

```
myPrint<>(a, b); //调用函数模板
```

函数模板也可以发生重载

如果函数模板可以产生更好的匹配,优先调用函数模板（输入类型不是普通函数类型）

总结：既然提供了函数模板，最好就不要提供普通函数，否则容易出现二义性

 

**1.2.6 模板的局限性**

```
template<class T>
         void f(T a, T b)
         { 
         a = b;
         }
```

在上述代码中提供的赋值操作，如果传入的a和b是一个数组，就无法实现了

如果T的数据类型传入的是像Person这样的自定义数据类型，也无法正常运行

因此C++为了解决这种问题，提供模板的重载，可以为这些特定的类型提供具体化的模板

```
template<class T>
bool myCompare(T& a, T& b)
{
         if (a == b)
         {
                 return true;
         }
         else
         {
                 return false;
         }
}//编译不通过 无法识别person处理
template<> bool myCompare(Person &p1, Person &p2)
{
         if ( p1.m_Name  == p2.m_Name && p1.m_Age == p2.m_Age)
         {
                 return true;
         }
         else
         {
                 return false;
         }
}
```

类似于运算符重载，额外加入比较函数定义做person自定义类型对比，系统优先调用该条件符合函数

 

**1.3 类模板**

作用：建立一个通用类，类中的成员 数据类型可以不具体制定，用一个虚拟的类型来代表

```
//类模板
template<class NameType, class AgeType> 
class Person
{
public:
         Person(NameType name, AgeType age)
         {
                 this->mName = name;
                 this->mAge = age;
         }
         void showPerson()
         {
                 cout << "name: " << this->mName << " age: " << this->mAge << endl;
         }
public:
         NameType mName;
         AgeType mAge;
};
void test01()
{
         // 指定NameType 为string类型，AgeType 为 int类型
         Person<string, int>P1("孙悟空", 999);
         P1.showPerson();
}
```

特点

类模板没有自动类型推导的使用方式

```
void test01()
{
         // Person p("孙悟空", 1000); //错误 类模板使用时候 不可以用自动类型推导
         Person <string ,int>p("孙悟空", 1000); //必须使用显示指定类型的方式，使用类模板
}
```

类模板在模板参数列表中可以有默认参数

```
template<class NameType, class AgeType = int> 
//调用时可以省略int也不会报错
Person <string> p("猪八戒", 999); //类模板中的模板参数列表 可以指定默认参数
```

 

**1.3.3 类模板中成员函数创建时机**

普通类中的成员函数一开始就可以创建

类模板中的成员函数在调用时才创建（未调用前不确定T为何类型，确定T后调用数据类型对应的函数才不会报错）

 

**1.3.4 类模板对象做函数参数**

类模板实例化出的对象，向函数传参的方式

一共有三种传入方式：

 

指定传入的类型 --- 直接显示对象的数据类型（最常用）

```
void printPerson1(Person<string, int> &p) 
```

参数模板化 --- 将对象中的参数变为模板进行传递

```
template <class T1, class T2>
void printPerson2(Person<T1, T2>&p)
```

整个类模板化 --- 将这个对象类型 模板化进行传递

```
template<class T>
void printPerson3(T & p)
```

 

**1.3.5 类模板与继承**

当类模板碰到继承时，需要注意一下几点：

当子类继承的父类是一个类模板时，子类在声明的时候，要指定出父类中T的类型

```
//class Son:public Base  //错误，c++编译需要给子类分配内存，必须知道父类中T的类型才可以向下继承
class Son :public Base<int> //必须指定一个类型
```

如果不指定，编译器无法给子类分配内存

如果想灵活指定出父类中T的类型，子类也需变为类模板

```
template<class T1, class T2>
class Son2 :public Base<T2>
```

 

类模板中成员函数类外实现时，需要加上模板参数列表

```
//构造函数 类外实现
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age) {}//参数列表
//成员函数 类外实现
template<class T1, class T2>
void Person<T1, T2>::showPerson() {}
```

 

**1.3.7 类模板分文件编写**

问题：

类模板中成员函数创建时机是在调用阶段，导致分文件编写时链接不到

解决：

解决方式1：直接包含.cpp源文件

```
#include "person.cpp"//cpp中自包含
```

解决方式2：将声明和实现写到同一个hpp文件中，并更改后缀名为.hpp，hpp是约定的名称，并不是强制

```
//解决方式2，将声明和实现写到一起，文件后缀名改为.hpp
#include "person.hpp"//cpp中包含
```

总结：主流的解决方式是第二种，将类模板成员函数写到一起，并将后缀名改为.hpp

 

**1.3.8 类模板与友元**

掌握类模板配合友元函数的类内和类外实现：

全局函数类内实现 - 直接在类内声明友元即可

```
template<class T1, class T2>
class Person
{
         //1、全局函数配合友元   类内实现
         friend void printPerson(Person<T1, T2> & p)
         {
               cout << "姓名： " << p.m_Name << " 年龄：" << p.m_Age << endl;
         }
public:
         Person(T1 name, T2 age)
         {
                 this->m_Name = name;
                 this->m_Age = age;
         }
private:
         T1 m_Name;
         T2 m_Age;
};
```

全局函数类外实现 - 需要提前让编译器知道全局函数的存在

```
//2、全局函数配合友元  类外实现 - 先做函数模板声明，下方在做函数模板定义，在做友元
template<class T1, class T2> class Person;// 函数模板声明
template<class T1, class T2>//函数模板定义
void printPerson2(Person<T1, T2> & p)
{
         cout << " ---- 姓名： " << p.m_Name << " 年龄：" << p.m_Age << endl;
}
template<class T1, class T2>
class Person
{
friend void printPerson2<>(Person<T1, T2> & p);//友元声明
}
```

 

**1.3.9 类模板案例**

注意事项：

1.创建在堆区应重写构造（创建堆区指针）、拷贝构造（堆区数据逐一赋值完成深拷贝）、析构函数（清空堆区数据）、operator=操作符（防止连等时浅拷贝导致的结果不变，赋值前先判断输入地址是否为空，为空清空数据）

2.重载中括号operator[] 以实现自创建数据的访问

 

## 2 STL初识

C++的面向对象和泛型编程思想，目的就是复用性的提升

为了建立数据结构和算法的一套标准,诞生了STL

 

**STL基本概念**

1.STL(Standard Template Library,标准模板库)

2.STL 从广义上分为: 容器(container) 算法(algorithm) 迭代器(iterator)

3.容器和算法之间通过迭代器进行无缝连接。

4.STL 几乎所有的代码都采用了模板类或者模板函数

 

**STL六大组件**

容器：各种数据结构，如vector、list、deque、set、map等,用来存放数据。

算法：各种常用的算法，如sort、find、copy、for_each等

迭代器：扮演了容器与算法之间的胶合剂。

仿函数：行为类似函数，可作为算法的某种策略。

适配器：一种用来修饰容器或者仿函数或迭代器接口的东西。

空间配置器：负责空间的配置与管理。

 

**容器**

STL容器就是将运用最广泛的一些数据结构实现出来

常用的数据结构：数组, 链表,树, 栈, 队列, 集合, 映射表 等

这些容器分为序列式容器和关联式容器两种:

序列式容器:强调值的排序，序列式容器中的每个元素均有固定的位置。 关联式容器:二叉树结构，各元素之间没有严格的物理上的顺序关系

 

**算法**

有限的步骤，解决逻辑或数学上的问题，这一门学科我们叫做算法(Algorithms)

算法分为:质变算法和非质变算法。

质变算法：是指运算过程中会更改区间内的元素的内容。例如拷贝，替换，删除等等

非质变算法：是指运算过程中不会更改区间内的元素内容，例如查找、计数、遍历、寻找极值等等

 

**迭代器**

提供一种方法，使之能够依序寻访某个容器所含的各个元素，而又无需暴露该容器的内部表示方式。

每个容器都有自己专属的迭代器

迭代器使用非常类似于指针，初学阶段我们可以先理解迭代器为指针

常用的容器中迭代器种类为双向迭代器，和随机访问迭代器

种类           功能                         支持运算

输入迭代器      对数据的只读访问               只读，支持++、==、！=

输出迭代器      对数据的只写访问               只写，支持++

前向迭代器      读写操作，并能向前推进迭代器    读写，支持++、==、！=

双向迭代器      读写操作，并能向前和向后操作    读写，支持++、--，

随机访问迭代器  读写操作，可以以跳跃的方式访问任意数据，功能最强的迭代器    读写，                                     支持++、--、[n]、-n、<、<=、>、>=

 

**2.5.1 vector存放内置数据类型**

容器： vector

算法： for_each

迭代器： vector<int>::iterator

```
#include <vector>//容器头文件
#include <algorithm>//调用标准算法库中for_each头文件
void MyPrint(int val)
{
         cout << val << endl;
}
 
void test01() {
         vector<int> v;//尾插法向容器中放数据
         v.push_back(10);
         v.push_back(20);
         v.push_back(30);
         v.push_back(40);
//第一种遍历方式：
         vector<int>::iterator pBegin = v.begin();//v.begin()返回迭代器，这个迭代器指向容器中第一个数据
         vector<int>::iterator pEnd = v.end();//v.end()返回迭代器，这个迭代器指向容器元素的最后一个元素的下一个位置
         while (pBegin != pEnd) {
                 cout << *pBegin << endl;
                 pBegin++;
         }
//第二种遍历方式：
         for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
                 cout << *it << endl;
         }//将迭代器指向放在for循环定义里（常用）
         //第三种遍历方式：
         //使用STL提供标准遍历算法  头文件 algorithm
         for_each(v.begin(), v.end(), MyPrint);//起始位置、终点位置、函数
}
```

 

Vector存放自定义数据类型

```
//自定义数据类型
class Person {
public:
         Person(string name, int age) {
                 mName = name;
                 mAge = age;
         }
public:
         string mName;
         int mAge;
};
//存放对象
void test01() {
         vector<Person> v;
         //创建数据
         Person p1("aaa", 10);
         v.push_back(p1);
         for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)         {
         cout << "Name:" << (*it).mName << " Age:" << (*it).mAge << endl;
         }
}
//放对象指针
void test02() {
         vector<Person*> v;
         //创建数据
         Person p1("aaa", 10);
         v.push_back(&p1);
         for (vector<Person*>::iterator it = v.begin(); it != v.end(); it++)        {
         Person * p = (*it);
         cout << "Name:" << p->mName << " Age:" << (*it)->mAge << endl;
         }
}
```

 

Vector容器嵌套容器

```
void test01() {
         vector< vector<int> >  v;//大容器
         vector<int> v1;//小容器
for (vector<vector<int>>::iterator it = v.begin(); it != v.end(); it++) {
         for (vector<int>::iterator vit = (*it).begin(); vit != (*it).end(); vit++) {//it---- vector<int>需要再一次遍历
                          cout << *vit << " ";//通过嵌套循环输出容器内容
                 }
                 cout << endl;
         }
}
```

 

### 3.1 string容器

本质：

string是C++风格的字符串，而string本质上是一个类

string和char * 区别：

char * 是一个指针，string是一个类，类内部封装了char*，管理这个字符串，是一个char*型的容器。

特点：

string 类内部封装了很多成员方法

例如：查找find，拷贝copy，删除delete 替换replace，插入insert

string管理char*所分配的内存，不用担心复制越界和取值越界等，由类内部进行负责

 

**3.1.2 string构造函数**

构造函数原型：

string(); //默认构造 创建一个空的字符串 例如: string str; string(const char* s);//使用字符串s初始化

string(const string& str); //拷贝构造 使用一个string对象初始化另一个string对象

string(int n, char c); //使用n个字符c初始化 即n个c组成字符串

 

**3.1.3 string赋值操作**

赋值的函数原型：

string& operator=(const char* s); //char*类型字符串 赋值给当前的字符串

```
str1 = "hello world";
```

string& operator=(const string &s); //把字符串s赋给当前的字符串

```
str2 = str1;
```

string& operator=(char c); //字符赋值给当前的字符串

```
str3 = 'a';
```

string& assign(const char *s); //把字符串s赋给当前的字符串

```
str4.assign("hello c++");
```

string& assign(const char *s, int n); //把字符串s的前n个字符赋给当前的字符串

```
str5.assign("hello c++",5);
```

string& assign(const string &s); //把字符串s赋给当前字符串

```
str6.assign(str5);
```

string& assign(int n, char c); //用n个字符c赋给当前字符串

```
str7.assign(5, 'x');
```

 

**3.1.4 string字符串拼接**

功能描述：

实现在字符串末尾拼接字符串

函数原型：

string& operator+=(const char* str); //重载+=操作符

```
str1 += "爱玩游戏";
```

string& operator+=(const char c); //重载+=操作符

```
str1 += ':';
```

string& operator+=(const string& str); //重载+=操作符

```
str1 += str2;
```

string& append(const char *s); //把字符串s连接到当前字符串结尾

```
str3.append(" love ");
```

string& append(const char *s, int n); //把字符串s的前n个字符连接到当前字符串结尾

```
str3.append("game abcde", 4);
```

string& append(const string &s); //同operator+=(const string& str)

```
str3.append(str2);
```

string& append(const string &s, int pos, int n);//字符串s中从pos开始的n个字符连接到字符串结尾

```
str3.append(str2, 4, 3);
```

 

**3.1.5 string查找和替换**

功能描述：

查找：查找指定字符串是否存在

替换：在指定的位置替换字符串

函数原型：

int find(const string& str, int pos = 0) const; //查找str第一次出现位置,从pos开始查找

```
int pos = str1.find("de");//位置下标从0开始，找不到字符串返回-1
```

int find(const char* s, int pos = 0) const; //查找s第一次出现位置,从pos开始查找

int find(const char* s, int pos, int n) const; //从pos位置查找s的前n个字符第一次位置

```
int pos = str1.find("de",3);
```

int find(const char c, int pos = 0) const; //查找字符c第一次出现位置

int rfind(const string& str, int pos = npos) const; //查找str最后一次位置,从pos开始查找

```
pos = str1.rfind("de");//从右往左查   find从左往右
```

int rfind(const char* s, int pos = npos) const; //查找s最后一次出现位置,从pos开始查找

int rfind(const char* s, int pos, int n) const; //从pos查找s的前n个字符最后一次位置

int rfind(const char c, int pos = 0) const; //查找字符c最后一次出现位置

string& replace(int pos, int n, const string& str); //替换从pos开始n个字符为字符串str

```
str1.replace(1, 3, "1111");
```

string& replace(int pos, int n,const char* s); //替换从pos开始的n个字符为字符串s

 

**3.1.6 string字符串比较**

比较方式：字符串比较是按字符的ASCII码进行对比

= 返回 0

\> 返回 1

< 返回 -1

函数原型：

int compare(const string &s) const; //与字符串s比较

```
int ret = s1.compare(s2);
```

int compare(const char *s) const; //与字符串s比较

总结：字符串对比主要是用于比较两个字符串是否相等，判断谁大谁小的意义并不是很大

 

**3.1.7 string字符存取**

char& operator[](int n); //通过[]方式取字符

```
str[0] = 'x';
```

char& at(int n); //通过at方法获取字符

```
str.at(1) = 'x';
```

 

**3.1.8 string插入和删除**

功能描述：

对string字符串进行插入和删除字符操作

函数原型：

string& insert(int pos, const char* s); //插入字符串

```
str.insert(1, "111");
```

string& insert(int pos, const string& str); //插入字符串

string& insert(int pos, int n, char c); //在指定位置插入n个字符c

string& erase(int pos, int n = npos); //删除从Pos开始的n个字符

 

**3.1.9 string子串**

功能描述：

从字符串中获取想要的子串

函数原型：

string substr(int pos = 0, int n = npos) const; //返回由pos开始的n个字符组成的字符串

```
string subStr = str.substr(1, 3);
string subStr = str.substr(1);//返回从1开始到结尾的字符串
```

 

### 3.2 vector容器

功能：

vector数据结构和数组非常相似，也称为单端数组

vector与普通数组区别：

数组是静态空间，而vector可以动态扩展

动态扩展：

并不是在原空间之后续接新空间，而是找更大的内存空间，然后将原数据拷贝新空间，释放原空间，vector容器的迭代器是支持随机访问的迭代器

 

**3.2.2 vector构造函数**

功能描述：创建vector容器

函数原型：

vector<T> v; //采用模板实现类实现，默认构造函数

```
vector<int> v1; //无参构造
```

vector(v.begin(), v.end()); //将v[begin(), end())区间中的元素拷贝给本身。

```
vector<int> v2(v1.begin(), v1.end());
```

vector(n, elem); //构造函数将n个elem拷贝给本身。

```
vector<int> v3(10, 100);
```

vector(const vector &vec); //拷贝构造函数。

```
vector<int> v4(v3);
```

 

**3.2.3 vector赋值操作**

函数原型：

vector& operator=(const vector &vec);//重载等号操作符

```
v2 = v1;
```

assign(beg, end); //将[beg, end)区间中的数据拷贝赋值给本身。

```
v3.assign(v1.begin(), v1.end());
```

assign(n, elem); //将n个elem拷贝赋值给本身。

```
v4.assign(10, 100);
```

 

**3.2.4 vector容量和大小**

功能描述：对vector容器的容量和大小操作

函数原型：

empty(); //判断容器是否为空

```
v1.empty()//为空输出1
```

capacity(); //容器的容量

```
v1.capacity()
```

size(); //返回容器中元素的个数

```
v1.size()
```

resize(int num); //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除。

```
v1.resize(5); //若指定的更大 默认用0填充新位置 可以利用重载版本替换默认填充
```

resize(int num, elem); //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。//如果容器变短，则末尾超出容器长度的元素被删除

```
v1.resize(15,10);
```

 

**3.2.5 vector插入和删除**

功能描述：对vector容器进行插入、删除操作

函数原型：

push_back(ele); //尾部插入元素ele

```
v1.push_back(10);
```

pop_back(); //删除最后一个元素

```
v1.pop_back();
```

insert(const_iterator pos, ele); //迭代器指向位置pos插入元素ele

```
v1.insert(v1.begin(), 100);
```

insert(const_iterator pos, int count,ele);//迭代器指向位置pos插入count个元素ele

```
v1.insert(v1.begin(), 2, 1000);
```

erase(const_iterator pos); //删除迭代器指向的元素

```
v1.erase(v1.begin());
```

erase(const_iterator start, const_iterator end);//删除迭代器从start到end之间的元素

```
v1.erase(v1.begin(), v1.end());
```

clear(); //删除容器中所有元素

```
v1.clear();
```

 

**3.2.6 vector数据存取**

函数原型：

at(int idx); //返回索引idx所指的数据

```
v1.at(i)
```

operator[]; //返回索引idx所指的数据

```
v1[i]
```

front(); //返回容器中第一个数据元素

```
v1.front()
```

back(); //返回容器中最后一个数据元素

```
v1.back()
```

 

**3.2.7 vector互换容器**

功能描述：实现两个容器内元素进行互换

函数原型：

swap(vec); // 将vec与本身的元素互换

```
v1.swap(v2);
```

总结：swap可以使两个容器互换，可以达到实用的收缩内存效果（例如存入10000个数据会自动开辟容量138255空间以防空间不足，互换后收缩容量为存入数据量）

```
vector<int>(v).swap(v); //收缩内存 匿名对象
```

 

**3.2.8 vector预留空间**

功能描述：减少vector在动态扩展容量时的扩展次数

函数原型：

reserve(int len);//容器预留len个元素长度，预留位置不初始化，元素不可访问。

```
v.reserve(100000);
```

 

### 3.3 deque容器

功能：双端数组，可以对头端进行插入删除操作

deque与vector区别：

vector对于头部的插入删除效率低，数据量越大，效率越低

deque相对而言，对头部的插入删除速度会比vector快

vector访问元素时的速度会比deque快,这和两者内部实现有关

deque内部工作原理:

deque内部有个中控器，维护每段缓冲区中的内容，缓冲区中存放真实数据

中控器维护的是每个缓冲区的地址，使得使用deque时像一片连续的内存空间

deque容器的迭代器也是支持随机访问的

 

**3.3.2 deque构造函数**

函数原型：

deque<T> deqT; //默认构造形式

```
deque<int> d1; //无参构造函数
```

deque(beg, end); //构造函数将[beg, end)区间中的元素拷贝给本身。

```
deque<int> d2(d1.begin(),d1.end());
```

deque(n, elem); //构造函数将n个elem拷贝给本身。

```
deque<int>d3(10,100);
```

deque(const deque &deq); //拷贝构造函数

```
deque<int>d4 = d3;
```

**3.3.3 deque赋值操作**

函数原型：

deque& operator=(const deque &deq); //重载等号操作符

assign(beg, end); //将[beg, end)区间中的数据拷贝赋值给本身。

assign(n, elem); //将n个elem拷贝赋值给本身。

总结：deque赋值操作也与vector相同

 

**3.3.4 deque大小操作**

功能描述：

对deque容器的大小进行操作

函数原型：

deque.empty(); //判断容器是否为空

deque.size(); //返回容器中元素的个数

deque.resize(num); //重新指定容器的长度为num,若容器变长，则以默认值填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除。

deque.resize(num, elem); //重新指定容器的长度为num,若容器变长，则以elem值填充新位置。//如果容器变短，则末尾超出容器长度的元素被删除。

总结：与vector相比，deque没有容量capacity的概念，其余一致

 

**3.3.5 deque 插入和删除**

函数原型：

两端插入操作：

push_back(elem); //在容器尾部添加一个数据

push_front(elem); //在容器头部插入一个数据

pop_back(); //删除容器最后一个数据

pop_front(); //删除容器第一个数据

指定位置操作：

insert(pos,elem); //在pos位置插入一个elem元素的拷贝，返回新数据的位置。

insert(pos,n,elem); //在pos位置插入n个elem数据，无返回值。

insert(pos,beg,end); //在pos位置插入[beg,end)区间的数据，无返回值。

clear(); //清空容器的所有数据

erase(beg,end); //删除[beg,end)区间的数据，返回下一个数据的位置。

erase(pos); //删除pos位置的数据，返回下一个数据的位置。

总结：插入和删除提供的位置是迭代器pos！

 

**3.3.6 deque 数据存取**

函数原型：

at(int idx); //返回索引idx所指的数据

operator[]; //返回索引idx所指的数据

front(); //返回容器中第一个数据元素

back(); //返回容器中最后一个数据元素

 

**3.3.7 deque 排序**

算法：

sort(iterator beg, iterator end) //对beg和end区间内元素进行排序

总结：sort算法非常实用，使用时包含头文件 algorithm即可，默认从小到大升序，支持随机访问的迭代器的容器，都可以用sort算法直接排序

 

### 3.4 案例-评委打分

\1. deque与vector容器打印输出都可以使用：

```
void printDeque(const deque<int>& d) //deque可换为vector
{
         for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++) {
                 cout << *it << " ";
         }
         cout << endl;
}
```

\2. 总结：选取不同的容器操作数据，可以提升代码的效率

 

### 3.5 stack容器

概念：stack是一种先进后出(First In Last Out,FILO)的数据结构，它只有一个出口

栈中只有顶端的元素才可以被外界使用，因此栈不允许有遍历行为

栈中进入数据称为 --- 入栈 push

栈中弹出数据称为 --- 出栈 pop

 

**3.5.2 stack 常用接口**

功能描述：栈容器常用的对外接口

构造函数：

stack<T> stk; //stack采用模板类实现， stack对象的默认构造形式

stack(const stack &stk); //拷贝构造函数

 

赋值操作：

stack& operator=(const stack &stk); //重载等号操作符

 

数据存取：

push(elem); //向栈顶添加元素

pop(); //从栈顶移除第一个元素

top(); //返回栈顶元素

 

大小操作：

empty(); //判断堆栈是否为空

size(); //返回栈的大小

 

### 3.6 queue 容器

概念：Queue是一种先进先出(First In First Out,FIFO)的数据结构，它有两个出口

队列容器允许从一端新增元素，从另一端移除元素

队列中只有队头和队尾才可以被外界使用，因此队列不允许有遍历行为

队列中进数据称为 --- 入队 push

队列中出数据称为 --- 出队 pop

 

**3.6.2 queue 常用接口**

功能描述：队列容器常用的对外接口

构造函数：

queue<T> que; //queue采用模板类实现，queue对象的默认构造形式

queue(const queue &que); //拷贝构造函数

 

赋值操作：

queue& operator=(const queue &que); //重载等号操作符

 

数据存取：

push(elem); //往队尾添加元素

pop(); //从队头移除第一个元素

back(); //返回最后一个元素

front(); //返回第一个元素

 

大小操作：

empty(); //判断堆栈是否为空

size(); //返回栈的大小

 

### 3.7 list容器

**功能：**将数据进行链式存储

链表（list）是一种物理存储单元上非连续的存储结构，数据元素的逻辑顺序是通过链表中的指针链接实现的

链表的组成：链表由一系列结点组成

结点的组成：一个是存储数据元素的数据域，另一个是存储下一个结点地址的指针域

STL中的链表是一个双向循环链表

由于链表的存储方式并不是连续的内存空间，因此链表list中的迭代器只支持前移和后移，属于双向迭代器

list的优点：

采用动态存储分配，不会造成内存浪费和溢出

链表执行插入和删除操作十分方便，修改指针即可，不需要移动大量元素

list的缺点：

链表灵活，但是空间(指针域) 和 时间（遍历）额外耗费较大

List有一个重要的性质，插入操作和删除操作都不会造成原有list迭代器的失效，这在vector是不成立的。

总结：STL中List和vector是两个最常被使用的容器，各有优缺点

 

**3.7.2 list构造函数**

功能描述：创建list容器

函数原型：

list<T> lst; //list采用采用模板类实现,对象的默认构造形式：

```
list<int>L1;
```

list(beg,end); //构造函数将[beg, end)区间中的元素拷贝给本身。

```
list<int>L2(L1.begin(),L1.end());
```

list(n,elem); //构造函数将n个elem拷贝给本身。

```
list<int>L4(10, 1000);
```

list(const list &lst); //拷贝构造函数

```
list<int>L3(L2);
```

 

**3.7.3 list 赋值和交换**

函数原型：

assign(beg, end); //将[beg, end)区间中的数据拷贝赋值给本身。

```
L3.assign(L2.begin(), L2.end());
```

assign(n, elem); //将n个elem拷贝赋值给本身。

```
L4.assign(10, 100);
```

list& operator=(const list &lst); //重载等号操作符

```
L2 = L1;
```

swap(lst); //将lst与本身的元素互换。

```
L1.swap(L2);
```

 

**3.7.4 list 大小操作**

函数原型：

size(); //返回容器中元素的个数

```
L1.size()
```

empty(); //判断容器是否为空

```
L1.empty()
```

resize(num); //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。

//如果容器变短，则末尾超出容器长度的元素被删除。

```
L1.resize(10);
```

resize(num, elem); //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。

 

**3.7.5 list 插入和删除**

函数原型：

push_back(elem);//在容器尾部加入一个元素

```
L.push_back(10);
```

pop_back();//删除容器中最后一个元素

```
L.pop_back();
```

push_front(elem);//在容器开头插入一个元素

```
L.push_front(100);
```

pop_front();//从容器开头移除第一个元素

```
L.pop_front();
```

insert(pos,elem);//在pos位置插elem元素的拷贝，返回新数据的位置。

```
list<int>::iterator it = L.begin();
         L.insert(++it, 1000);
```

insert(pos,n,elem);//在pos位置插入n个elem数据，无返回值。

insert(pos,beg,end);//在pos位置插入[beg,end)区间的数据，无返回值。

clear();//移除容器的所有数据

```
L.clear();
```

erase(beg,end);//删除[beg,end)区间的数据，返回下一个数据的位置。

erase(pos);//删除pos位置的数据，返回下一个数据的位置。

```
it = L.begin();
         L.erase(++it);
```

remove(elem);//删除容器中所有与elem值匹配的元素。

```
L.remove(10000);
```

 

**3.7.6 list 数据存取**

函数原型：

front(); //返回第一个元素。

```
L1.front()
```

back(); //返回最后一个元素。

```
L1.back()
```

总结：

list容器中不可以通过[]或者at方式访问数据 

list容器的迭代器是双向迭代器，不支持随机访问

 

**3.7.7 list 反转和排序**

函数原型：

reverse(); //反转链表

```
L.reverse();
```

sort(); //链表排序

```
L.sort(); //默认的排序规则 从小到大
bool myCompare(int val1 , int val2)
{
         return val1 > val2;
}
L.sort(myCompare); //指定规则，从大到小
```

总结：

对于自定义数据类型，必须要指定排序规则，否则编译器不知道如何进行排序

高级排序只是在排序规则上再进行一次逻辑规则制定，并不复杂

 

### 3.8 set/ multiset 容器

简介：所有元素都会在插入时自动被排序

本质：set/multiset属于关联式容器，底层结构是用二叉树实现。

set和multiset区别：

set不允许容器中有重复的元素

multiset允许容器中有重复的元素

```
#include <set>
```

 

 

**3.8.2 set构造和赋值**

构造：

set<T> st; //默认构造函数：

```
set<int> s1;
```

set(const set &st); //拷贝构造函数

```
set<int>s2(s1);
```

赋值：

set& operator=(const set &st); //重载等号操作符

```
s3 = s2;
```

 

**3.8.3 set大小和交换**

函数原型：

size(); //返回容器中元素的数目

empty(); //判断容器是否为空

swap(st); //交换两个集合容器

 

**3.8.4 set插入和删除**

函数原型：

insert(elem); //在容器中插入元素。

```
s1.insert(10);
```

clear(); //清除所有元素

erase(pos); //删除pos迭代器所指的元素，返回下一个元素的迭代器。

erase(beg, end); //删除区间[beg,end)的所有元素 ，返回下一个元素的迭代器。

erase(elem); //删除容器中值为elem的元素。

 

**3.8.5 set查找和统计**

函数原型：

find(key); //查找key是否存在,若存在，返回该键的元素的迭代器；若不存在，返回set.end();

```
set<int>::iterator pos = s1.find(30);
         if (pos != s1.end())
         {
                 cout << "找到了元素 ： " << *pos << endl;
         }
         else
         {
                 cout << "未找到元素" << endl;
         }
```

count(key); //统计key的元素个数

```
int num = s1.count(30);
```

 

**3.8.6 set和multiset区别**

区别：

set不可以插入重复数据，而multiset可以

set插入数据的同时会返回插入结果，表示插入是否成功

multiset不会检测数据，因此可以插入重复数据

```
set<int> s;
         pair<set<int>::iterator, bool>  ret = s.insert(10);
         if (ret.second) {
                 cout << "第一次插入成功!" << endl;
         }
         else {
                 cout << "第一次插入失败!" << endl;
         }
```

ret.second 

set的带有一个键参数的insert版本函数返回pair类型对象，该对象包含一个迭代器和一个bool值，迭代器指向拥有该键的元素，而bool值表明是否添加了元素。这里的second即是返回的pair里的bool值。

 

**3.8.7 pair对组创建**

功能描述：成对出现的数据，利用对组可以返回两个数据

两种创建方式：

pair<type, type> p ( value1, value2 );

pair<type, type> p = make_pair( value1, value2 );

```
void test01()
{
         pair<string, int> p(string("Tom"), 20);
         cout << "姓名： " <<  p.first << " 年龄： " << p.second << endl;
         pair<string, int> p2 = make_pair("Jerry", 10);
         cout << "姓名： " << p2.first << " 年龄： " << p2.second << endl;
}
```

 

**3.8.8 set容器排序**

学习目标：set容器默认排序规则为从小到大，掌握如何改变排序规则

主要技术点：利用仿函数，可以改变排序规则

```
class comparePerson
{
public:
         bool operator()(const Person& p1, const Person &p2)
         {
                 //按照年龄进行排序  降序
                 return p1.m_Age > p2.m_Age;
         }
};
void test01()
{
         set<Person, comparePerson> s;
         Person p1("刘备", 23);
         Person p2("关羽", 27);
         Person p3("张飞", 25);
         Person p4("赵云", 21);
         s.insert(p1);
         s.insert(p2);
         s.insert(p3);
         s.insert(p4);
         for (set<Person, comparePerson>::iterator it = s.begin(); it != s.end(); it++)
         {
         cout << "姓名： " << it->m_Name << " 年龄： " << it->m_Age << endl;
         }
}
```

 

### 3.9 map/ multimap容器

简介：

map中所有元素都是pair

pair中第一个元素为key（键值），起到索引作用，第二个元素为value（实值）

所有元素都会根据元素的键值自动排序

本质：

map/multimap属于关联式容器，底层结构是用二叉树实现。

优点：

可以根据key值快速找到value值

map和multimap区别：

map不允许容器中有重复key值元素（非value）

multimap允许容器中有重复key值元素

 

**3.9.2 map构造和赋值**

构造：

map<T1, T2> mp; //map默认构造函数:

```
map<int,int>m; //默认构造
```

map(const map &mp); //拷贝构造函数

```
map<int, int>m2(m); //拷贝构造
```

赋值：

map& operator=(const map &mp); //重载等号操作符

```
m3 = m2; //赋值
```

总结：map中所有元素都是成对出现，插入数据时候要使用对组

 

**3.9.3 map大小和交换**

函数原型：

size(); //返回容器中元素的数目

empty(); //判断容器是否为空

swap(st); //交换两个集合容器

```
m.swap(m2);
```

 

**3.9.4 map插入和删除**

函数原型：

insert(elem); //在容器中插入元素。

```
//第一种插入方式m.insert(pair<int, int>(1, 10));
//第二种插入方式m.insert(make_pair(2, 20));
//第三种插入方式m.insert(map<int, int>::value_type(3, 30));
//第四种插入方式m[4] = 40; 
```

clear(); //清除所有元素

erase(pos); //删除pos迭代器所指的元素，返回下一个元素的迭代器。

```
m.erase(m.begin());
```

erase(beg, end); //删除区间[beg,end)的所有元素 ，返回下一个元素的迭代器。

erase(key); //删除容器中值为key的元素。

```
m.erase(3);
```

 

**3.9.5 map查找和统计**

函数原型：

find(key); //查找key是否存在,若存在，返回该键的元素的迭代器；若不存在，返回set.end();

```
map<int, int>::iterator pos = m.find(3);
         if (pos != m.end())
         {
                 cout << "找到了元素 key = " << (*pos).first << " value = " << (*pos).second << endl;
         }
         else
         {
                 cout << "未找到元素" << endl;
         }
```

count(key); //统计key的元素个数

```
int num = m.count(3);
         cout << "num = " << num << endl;
```

总结：查找 --- find （返回的是迭代器，查找的也是key而非value）

 

**3.9.6 map容器排序**

主要技术点:

利用仿函数，可以改变排序规则

```
class MyCompare {
public:
         bool operator()(int v1, int v2) {
                 return v1 > v2;
         }
};
 
map<int, int, MyCompare> m;
for (map<int, int, MyCompare>::iterator it = m.begin(); it != m.end(); it++) {
                 cout << "key:" << it->first << " value:" << it->second << endl;
         }
```

 

**3.10案例**

1.vector函数数值调用应加引用

```
void setGroup(vector<Worker>&v,multimap<int,Worker>&m)
```

2.string可以用+=自拼接后续文字

```
worker.m_Name = "员工";
worker.m_Name += nameSeed[i];
```

3.rand()%10000随机范围0~9999  rand()%3随机范围0 1 2

4.#define name 0 后续则可以用name代表0

5.应用系统时间做真实随机

```
#include <ctime>
srand((unsigned int)time(NULL));
```

\6.   将vector值赋给multimap

```
void setGroup(vector<Worker>&v,multimap<int,Worker>&m)
{
         for (vector<Worker>::iterator it = v.begin(); it != v.end(); it++)
         {
                 //产生随机部门编号
                 int deptId = rand() % 3; // 0 1 2 
                 //将员工插入到分组中
                 //key部门编号，value具体员工
                 m.insert(make_pair(deptId, *it));
         }
}
```

\7.   输出分组数据

```
cout << "策划部门：" << endl;
//找到索引为key的首地址值
         multimap<int,Worker>::iterator pos = m.find(CEHUA);
//统计同一key值的数量
         int count = m.count(CEHUA); // 统计具体人数
         int index = 0;
         for (; pos != m.end() && index < count; pos++ , index++)//双条件
         {
                 cout << "姓名： " << pos->second.m_Name << " 工资： " << pos->second.m_Salary << endl;
         }
```

 

## 4 STL- 函数对象

概念：

重载函数调用操作符的类，其对象常称为函数对象

函数对象使用**重载的()**时，行为类似函数调用，也叫仿函数

本质：

函数对象(仿函数)是一个类，不是一个函数

特点：

函数对象在使用时，可以像普通函数那样调用, 可以有参数，可以有返回值

```
class MyAdd
{
public :
         int operator()(int v1,int v2)
         {
                 return v1 + v2;
         }
};
void test01()
{
         MyAdd myAdd;
         cout << myAdd(10, 10) << endl;
}
```

函数对象超出普通函数的概念，函数对象可以有自己的状态

```
class MyPrint
{
public:
         MyPrint()
         {
                 count = 0;
         }
         void operator()(string test)
         {
                 cout << test << endl;
                 count++; //统计使用次数
         }
         int count; //内部自己的状态
};
void test02()
{
         MyPrint myPrint;
         myPrint("hello world");
         cout << "myPrint调用次数为： " << myPrint.count << endl;
}
```

函数对象可以作为参数传递

```
void doPrint(MyPrint &mp , string test)
{
         mp(test);
}
void test03()
{
         MyPrint myPrint;
         doPrint(myPrint, "Hello C++");//即myPrint可当函数对象传递
}
```

 

**4.2 谓词**

概念：

返回bool类型的仿函数称为谓词

如果operator()接受一个参数，那么叫做一元谓词

```
bool operator()(int val) {
                 return val > 5;
         }
```

如果operator()接受两个参数，那么叫做二元谓词

```
bool operator()(int num1, int num2)
         {
                 return num1 > num2;
         }
```

 

**4.3 内建函数对象**

概念：STL内建了一些函数对象

分类:

算术仿函数、关系仿函数、逻辑仿函数

用法：

这些仿函数所产生的对象，用法和一般函数完全相同

使用内建函数对象，需要引入头文件 #include<functional>

 

**4.3.2 算术仿函数**

功能描述：

实现四则运算

其中negate是一元运算，其他都是二元运算

仿函数原型：

template<class T> T plus<T> //加法仿函数

```
void test02()
{
         plus<int> p;
         cout << p(10, 20) << endl;
}
```

template<class T> T minus<T> //减法仿函数

template<class T> T multiplies<T> //乘法仿函数

template<class T> T divides<T> //除法仿函数

template<class T> T modulus<T> //取模仿函数

template<class T> T negate<T> //取反仿函数

```
void test01()
{
         negate<int> n;
         cout << n(50) << endl;
}
```

 

**4.3.3 关系仿函数**

功能描述：实现关系对比

仿函数原型：

template<class T> bool equal_to<T> //等于

template<class T> bool not_equal_to<T> //不等于

template<class T> bool greater<T> //大于

```
sort(v.begin(), v.end(), greater<int>());//排序从大到小
```

template<class T> bool greater_equal<T> //大于等于

template<class T> bool less<T> //小于

template<class T> bool less_equal<T> //小于等于

总结：关系仿函数中最常用的就是greater<>大于

 

**4.3.4 逻辑仿函数**

函数原型：

template<class T> bool logical_and<T> //逻辑与

template<class T> bool logical_or<T> //逻辑或

template<class T> bool logical_not<T> //逻辑非

```
transform(v.begin(), v.end(),  v2.begin(), logical_not<bool>());
//搬运元素并取非
```

 

**5 STL- 常用算法**

概述:

算法主要是由头文件<algorithm> <functional> <numeric>组成。

<algorithm>是所有STL头文件中最大的一个，范围涉及到比较、 交换、查找、遍历操作、复制、修改等等

<numeric>体积很小，只包括几个在序列上面进行简单数学运算的模板函数

<functional>定义了一些模板类,用以声明函数对象。

 

### 5.1 常用遍历算法

算法简介：

for_each //遍历容器

transform //搬运容器到另一个容器中

函数原型：

for_each(iterator beg, iterator end, _func);

// 遍历算法 遍历容器元素

// beg 开始迭代器

// end 结束迭代器

// _func 函数或者函数对象

```
class print02 
{
 public:
         void operator()(int val) 
         {
                 cout << val << " ";
         }
};
//for_each算法基本用法
void test01() {
         vector<int> v;
         for (int i = 0; i < 10; i++) 
         {
                 v.push_back(i);
         }
         //遍历算法
         for_each(v.begin(), v.end(), print02());
}
```

 

5.1.2 transform

功能描述：

搬运容器到另一个容器中

函数原型：

transform(iterator beg1, iterator end1, iterator beg2, _func);

//beg1 源容器开始迭代器

//end1 源容器结束迭代器

//beg2 目标容器开始迭代器

 

//_func 函数或者函数对象

```
         vector<int>vTarget; //目标容器
         vTarget.resize(v.size()); // 目标容器需要提前开辟空间
         transform(v.begin(), v.end(), vTarget.begin(), TransForm());
```

总结： 搬运的目标容器必须要提前开辟空间，否则无法正常搬运

 

### 5.2 常用查找算法

算法简介：

find //查找元素

find_if //按条件查找元素

adjacent_find //查找相邻重复元素

binary_search //二分查找法

count //统计元素个数

count_if //按条件统计元素个数

 

**5.2.1 find**

函数原型：

find(iterator beg, iterator end, value);

// 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

// beg 开始迭代器

// end 结束迭代器

// value 查找的元素

```
class Person {
public:
         Person(string name, int age) 
         {
                 this->m_Name = name;
                 this->m_Age = age;
         }
         //自定义数据重载==
         bool operator==(const Person& p) 
         {
                 if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) 
                 {
                          return true;
                 }
                 return false;
         }
public:
         string m_Name;
         int m_Age;
};
void test02() {
         vector<Person> v;
         //创建数据
         Person p1("aaa", 10);
         Person p2("bbb", 20);
         Person p3("ccc", 30);
         Person p4("ddd", 40);
         v.push_back(p1);
         v.push_back(p2);
         v.push_back(p3);
         v.push_back(p4);
         vector<Person>::iterator it = find(v.begin(), v.end(), p2);
         if (it == v.end()) 
         {
                 cout << "没有找到!" << endl;
         }
         else 
         {
                 cout << "找到姓名:" << it->m_Name << " 年龄: " << it->m_Age << endl;
         }
}
```

总结： 利用find可以在容器中找指定的元素，返回值是迭代器

 

5.2.2 find_if

功能描述：按条件查找元素

函数原型：

find_if(iterator beg, iterator end, _Pred);

// 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

// beg 开始迭代器

// end 结束迭代器

// _Pred 函数或者谓词（返回bool类型的仿函数）

```
class GreaterFive//返回大于5的值
{
public:
         bool operator()(int val)
         {
                 return val > 5;
         }
};
void test01() {
 
         vector<int> v;
         for (int i = 0; i < 10; i++) {
                 v.push_back(i + 1);
         }
         vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());
         if (it == v.end()) {
                 cout << "没有找到!" << endl;
         }
         else {
                 cout << "找到大于5的数字:" << *it << endl;
         }
}
```

 

**5.2.3 adjacent_find**

函数原型：

adjacent_find(iterator beg, iterator end);

// 查找相邻重复元素,返回相邻元素的第一个位置的迭代器

// beg 开始迭代器

// end 结束迭代器

```
vector<int>::iterator it = adjacent_find(v.begin(), v.end());
         if (it == v.end()) {
                 cout << "找不到!" << endl;
         }
         else {
                 cout << "找到相邻重复元素为:" << *it << endl;
         }
```

总结：面试题中如果出现查找相邻重复元素，记得用STL中的adjacent_find算法

 

**5.2.4 binary_search**

函数原型：

bool binary_search(iterator beg, iterator end, value);

// 二分法查找指定的元素，查到 返回true 否则false

// 注意: 在无序序列中不可用

// beg 开始迭代器

// end 结束迭代器

// value 查找的元素

```
bool ret = binary_search(v.begin(), v.end(),2);
         if (ret)
         {
                 cout << "找到了" << endl;
         }
         else
         {
                 cout << "未找到" << endl;
         }
```

 

**5.2.5 count**

函数原型：

count(iterator beg, iterator end, value);

// 统计元素出现次数

// beg 开始迭代器

// end 结束迭代器

// value 统计的元素

```
int num = count(v.begin(), v.end(), 4);
         cout << "4的个数为： " << num << endl;
//自定义数据类型
class Person
{
public:
         Person(string name, int age)
         {
                 this->m_Name = name;
                 this->m_Age = age;
         }
         bool operator==(const Person & p)
         {
                 if (this->m_Age == p.m_Age)
                 {
                          return true;
                 }
                 else
                 {
                          return false;
                 }
         }
         string m_Name;
         int m_Age;
};
void test02()
{
         vector<Person> v;
         Person p1("刘备", 35);
         Person p2("关羽", 35);
         Person p3("张飞", 35);
         Person p4("赵云", 30);
         Person p5("曹操", 25);
         v.push_back(p1);
         v.push_back(p2);
         v.push_back(p3);
         v.push_back(p4);
         v.push_back(p5);
         Person p("诸葛亮",35);
         int num = count(v.begin(), v.end(), p);
         cout << "num = " << num << endl;
}
```

总结： 统计自定义数据类型时候，需要配合重载 operator==

 

**5.2.6 count_if**

函数原型：

count_if(iterator beg, iterator end, _Pred);

// 按条件统计元素出现次数

// beg 开始迭代器

// end 结束迭代器

// _Pred 谓词

```
class AgeLess35
{
public:
         bool operator()(const Person &p)
         {
                 return p.m_Age < 35;
         }
};
void test02()
{
         vector<Person> v;
         Person p1("刘备", 35);
         Person p2("关羽", 35);
         Person p3("张飞", 35);
         Person p4("赵云", 30);
         Person p5("曹操", 25);
         v.push_back(p1);
         v.push_back(p2);
         v.push_back(p3);
         v.push_back(p4);
         v.push_back(p5);
         int num = count_if(v.begin(), v.end(), AgeLess35());
         cout << "小于35岁的个数：" << num << endl;
}
```

 

### 5.3 常用排序算法

算法简介：

sort //对容器内元素进行排序

random_shuffle //洗牌 指定范围内的元素随机调整次序

merge // 容器元素合并，并存储到另一容器中

reverse // 反转指定范围的元素

 

**5.3.1 sort**

函数原型：

sort(iterator beg, iterator end, _Pred);

// 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

// beg 开始迭代器

// end 结束迭代器

// _Pred 谓词

```
void myPrint(int val)
{
         cout << val << " ";
}
void test01() {
         vector<int> v;
         v.push_back(10);
         v.push_back(30);
         v.push_back(50);
         v.push_back(20);
         v.push_back(40);
         //sort默认从小到大排序
         sort(v.begin(), v.end());
         for_each(v.begin(), v.end(), myPrint);
         cout << endl;
         //从大到小排序
         sort(v.begin(), v.end(), greater<int>());
         for_each(v.begin(), v.end(), myPrint);
         cout << endl;
}
```

**总结：**sort属于开发中最常用的算法之一，需熟练掌握

 

**5.3.2 random_shuffle**

功能描述：

洗牌 指定范围内的元素随机调整次序

函数原型：

random_shuffle(iterator beg, iterator end);

// beg 开始迭代器

// end 结束迭代器

```
random_shuffle(v.begin(), v.end());
```

**总结：**random_shuffle洗牌算法比较实用，使用时记得加随机数种子

```
#include <ctime>
srand((unsigned int)time(NULL));
```

 

**5.3.3 merge**

功能描述：

两个容器元素合并，并存储到另一容器中

函数原型：

merge(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);

// 容器元素合并，并存储到另一容器中

// 注意: 两个容器必须是有序的

// beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

```
         //目标容器需要提前开辟空间
         vtarget.resize(v1.size() + v2.size());
         //合并  需要两个有序序列
         merge(v1.begin(), v1.end(), v2.begin(), v2.end(), vtarget.begin());
```

**总结：**merge合并的两个容器必须的有序序列

 

**5.3.4 reverse**

功能描述：

将容器内元素进行反转

函数原型：

reverse(iterator beg, iterator end);

// 反转指定范围的元素

// beg 开始迭代器

// end 结束迭代器

```
reverse(v.begin(), v.end());
```

**总结：**reverse反转区间内元素，面试题可能涉及到

 

### 5.4 常用拷贝和替换算法

学习目标：

掌握常用的拷贝和替换算法

算法简介：

copy // 容器内指定范围的元素拷贝到另一容器中

replace // 将容器内指定范围的旧元素修改为新元素

replace_if // 容器内指定范围满足条件的元素替换为新元素

swap // 互换两个容器的元素

 

**5.4.1 copy**

功能描述：

容器内指定范围的元素拷贝到另一容器中

函数原型：

copy(iterator beg, iterator end, iterator dest);

// 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

// beg 开始迭代器

// end 结束迭代器

// dest 目标起始迭代器

```
         vector<int> v2;
         v2.resize(v1.size());
         copy(v1.begin(), v1.end(), v2.begin());
```

 

**5.4.2 replace**

功能描述：

将容器内指定范围的旧元素修改为新元素

函数原型：

replace(iterator beg, iterator end, oldvalue, newvalue);

//将区间内旧元素 替换成 新元素

// beg 开始迭代器

// end 结束迭代器

// oldvalue 旧元素

// newvalue 新元素

```
//将容器中的20 替换成 2000
         replace(v.begin(), v.end(), 20,2000);
```

 

5.4.3 replace_if

功能描述:

将区间内满足条件的元素，替换成指定元素

函数原型：

replace_if(iterator beg, iterator end, _pred, newvalue);

// beg 开始迭代器

// end 结束迭代器

// _pred 谓词

// newvalue 替换的新元素

```
class ReplaceGreater30
{
public:
         bool operator()(int val)
         {
                 return val >= 30;
         }
};
void test01()
{
         vector<int> v;
         v.push_back(20);
         v.push_back(30);
         v.push_back(20);
         v.push_back(40);
         v.push_back(50);
         v.push_back(10);
         v.push_back(20);
         //将容器中大于等于的30 替换成 3000
         replace_if(v.begin(), v.end(), ReplaceGreater30(), 3000);
}
```

 

**5.4.4 swap**

功能描述：

互换两个容器的元素

函数原型：

swap(container c1, container c2);

// 互换两个容器的元素

// c1容器1

// c2容器2

```
swap(v1, v2);
```

**总结：**swap交换容器时，注意交换的容器要同种类型

 

### 5.5 常用算术生成算法

注意：

算术生成算法属于小型算法，使用时包含的头文件为 #include <numeric>

算法简介：

accumulate // 计算容器元素累计总和

fill // 向容器中添加元素

 

**5.5.1 accumulate**

功能描述：

计算区间内 容器元素累计总和

函数原型：

accumulate(iterator beg, iterator end, value);

// beg 开始迭代器

// end 结束迭代器

// value 起始值

```
         int total = accumulate(v.begin(), v.end(), 0);
         cout << "total = " << total << endl;
```

**总结：**accumulate使用时头文件注意是 numeric，这个算法很实用

 

**5.5.2 fill**

功能描述：

向容器中填充指定的元素

函数原型：

fill(iterator beg, iterator end, value);

// 向容器中填充元素

// beg 开始迭代器

// end 结束迭代器

// value 填充的值

```
         v.resize(10);
         fill(v.begin(), v.end(), 100);
```

 

### 5.6 常用集合算法

算法简介：

set_intersection // 求两个容器的交集

set_union // 求两个容器的并集

set_difference // 求两个容器的差集

 

**5.6.1 set_intersection**

功能描述：

求两个容器的交集

函数原型：

set_intersection(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);

// 注意:两个集合必须是有序序列

// beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

```
         vector<int> vTarget;
         //取两个里面较小的值给目标容器开辟空间
         vTarget.resize(min(v1.size(), v2.size()));
         //返回目标容器的最后一个元素的迭代器地址
         vector<int>::iterator itEnd = 
        set_intersection(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
```

 

**5.6.2 set_union**

功能描述：

求两个集合的并集

函数原型：

set_union(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);

// 注意:两个集合必须是有序序列

// beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

```
         vector<int> vTarget;
         //取两个容器的和给目标容器开辟空间
         vTarget.resize(v1.size() + v2.size());
         //返回目标容器的最后一个元素的迭代器地址
         vector<int>::iterator itEnd = 
        set_union(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
```

 

**5.6.3 set_difference**

功能描述：

求两个集合的差集

注意差集定义 如求V1和V2的差集指在V1中存在而V2中不存在的值（与V2中存在V1中不存在的值无关）

函数原型：

set_difference(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);

// 注意:两个集合必须是有序序列

// beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

```
         for (int i = 0; i < 10; i++) {
                 v1.push_back(i);
                 v2.push_back(i+5);
         }
         vector<int> vTarget;
         //取两个里面较大的值给目标容器开辟空间
         vTarget.resize( max(v1.size() , v2.size()));
         //返回目标容器的最后一个元素的迭代器地址
         cout << "v1与v2的差集为： " << endl;
         vector<int>::iterator itEnd = set_difference(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());//结果为0 1 2 3 4
         cout << "v2与v1的差集为： " << endl;
         itEnd = set_difference(v2.begin(), v2.end(), v1.begin(), v1.end(), vTarget.begin());//结果为 10 11 12 13 14
```

 

**6演讲比赛系统**

1.头文件.h创建类只需写声明无需写实现，在源文件.cpp中写实现。若cpp写实现调用的为头文件中的类函数，则需加作用域  类名：：函数名（）{} 格式写实现

2.子函数中system（“pause”）；exit（0）；按任意键即可结束程序 退出系统

3.防止头文件重复包含 #pragma once

4.作用域下函数实现常为 this->函数名() this->成员变量()

 

 

 

 


 

 

# Tip 疑难问题

1.如何在函数中通过改变数组指针的指向实现数组的赋值

常规数组不可实现，可用vector等容器实现

2.如何在堆区创建二维数组

Double (*p)[n]=new double[m][n]

 