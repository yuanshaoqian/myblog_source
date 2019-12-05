---
title: C的变量与常量
date: 2019-02-23 21:04:16
tags: C语言
---

# 变量
使用<font color="blue">printf()</font>来打印变量的值。
要打印a中的值10：<font color="blue">printf("%d\n",a);</font>
<font color="red">%d</font>代表十进制输出一个整数。
### 变量值简单交换
```C
#include<stdio.h>
int main()
{
	int a,b,tmp;
	a = 1;
	b = 2;
	tmp = a;
	a = b;
	b = tmp;
	printf("a is %d\n",a);
	printf("b is %d\n",b);
	return 0;
}
```

# 常量
在程序执行过程中，其值不被改变的量

直接常量：直接引用的数字等；
符号常量：使用标识符来代替一个数字（常见的：宏定义常量 和 常变量）
宏定义：又称为宏代换，是定义一个标识符来代表一个值或一个表达式

```C
#define XXXX 10
```
宏定义也可定义表达式：
```C
#define ADD(a,b) (a)+(b)
#define MUL(a,b) (a)*(b)
```
<font color="red">注意：如果要使用宏定义来代替表达式，需要在每个表达式的变量都加上括号以防止出现计算错误</font>
```C
#include<stdio.h>
#define FUN1(a,b) a * b
#define FUN2(a,b) (a)*(b)
int main()
{
	int a=2;
	int b=3;
	printf("%d\n",FUN1(a+b,b+a));
	printf("%d\n",FUN2(a+b,b+a));
	return 0;
}
执行程序，输出：
13
25
答案：
FUN1的宏替换会变成：a+b*b+a
FUN2的宏替换会变成：(a+b)*(b+a)
因此两个宏替换会得到不同的结果。
```
# 常变量
变量值不可改变的量，使用const修饰
<font color="red">注意：const修饰后的变量会变成只读，因此无法再次赋值。因此初始化常变量需要在定义时直接赋值。</font>
<br>
常变量与宏定义常量的区别：宏定义常量是在预处理阶段，使用宏名来代替宏值。而常变量是在程序运行时，程序在内存分配的一个变量，只不过变量不允许再次赋值。
<br>
常量与后缀：
有时候我们需要显式地表示出常量的类型，这时候我们可以在常量后加后缀
u或U：unsigned类型，如123u
l或L：long类型，如123l
ll或LL：long long类型，如123456ll
f或F：float类型，如0.123f
<br>
