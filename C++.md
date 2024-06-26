# C++

## 类和对象

### 	面向对象和面向过程的初步认识

#### 面向过程

C语言是面向过程，即分析求解问题的步骤，通过调用函数逐步解决问题。

#### 面向对象

 C++是基于面向对象，将一件事情拆分成不同的对象，靠对象进行交互完成。

### 类的引入

C语言的结构体只能定义变量。C++中，结构体不仅可以定义变量，还可以定义函数。

类的关键字<kbd>class</kbd>，在C++中更喜欢用<kbd>class</kbd>来替代。

### 类的定义

```cpp
class myclass
{
	//类体：用成员函数和成员变量组成
};//注意后面的分號
```

==myclass==为类的名字，<kbd>{}</kbd>中为类的主体，注意类后面的分号。

类体中的内容称为类的成员：类中的变量称类的属性或车成员变量；类中的函数称为类的方法或成员函数。

#### 类的两种定义方式

1. 声明和定义全放在类体中。注意：成员函数在类中定义，编译器有可能将其当成==内联函数==。

   ```cpp
   class myclass
   {
       public:
       	void Print()
       {
           cout<<"hello C++"<<endl;
       }
       private:
           int _a;
           int _b;
   };
   ```

   

2. 类声明放在<kbd>.h</kbd>文件中，成员函数放在<kbd>.cpp</kbd>中，**注意：须在成员函数名前加==类名::==。**

### 类的访问限定符及封装

> 封装：用类将对象的属性与方法结合一起，让对象更加完善，通过访问权限选择接口提供给用户使用。
>
> <img src="C:\Users\liang\AppData\Roaming\Typora\typora-user-images\image-20240408112336968.png" alt="image-20240408112336968" style="zoom: 67%;" />

【访问限定符说明】

- 访问权限的作用域是该访问限定符开始知道下一个访问限定符结束，如果后面没有访问限定符，作用域到类结束。
- <kbd>class</kbd>默认访问权限是<kbd>private</kbd>，<kbd>struct</kbd>的默认访问权限是<kbd>public</kbd>（因为<kbd>struct</kbd>需要兼容C语言）。

**注意：访问限定符仅在编译时有用，当数据映射到内容后，没有任何访问限定符上的区别**

#### 封装

**面向对象的三大特性：封装、继承、多态。**

封装：将数据与操作数据的方法进行有机结合，隐藏对象的属性和实现细节，仅对外公开接口和对象进行交互。

在C++中实现封装通过访问限定符来隐藏对象的实现细节。

### 类的作用域

类定义了一个作用域。类的所有成员都在类中的作用域中。在类外定义成员时，需在类型前加上类的作用域。

```cpp
class Person
{
public:
	void Print();	

private:
    int _a;
    int _b;
};

//类外定义
void Person::Print()
{
	cout<<"hello c++"<<endl;
    
}
```

### 类的实例化

> 使用类类型来创建对象的过程，称为类的实例化。

类可以实例化多个对象。

<img src="C:\Users\liang\AppData\Roaming\Typora\typora-user-images\image-20240408114742604.png" alt="image-20240408114742604"  />

### 类的存储方式

```cPP
#include <iostream>
using namespace std;

//具有成员函数和成员变量的类
class A
{
public:
	void Print(){
		cout << _a << endl;
	}
private:
	int _a;
};

//仅有成员函数的类
class B
{
public:
	void Print(){
		cout << " hello C++" << endl;
	}
};
//空类
class C
{};

int main()
{
	cout << "A 的大小是：" << sizeof(A) << endl; //4
	cout << "B 的大小是：" << sizeof(B) << endl; //1
	cout << "C 的大小是：" << sizeof(C) <<endl;  //1
	return 0;
}
```

**空类和仅有成员函数的类一样，都只占用1字节空间。**

为啥会占用一个字节空间的大小?

> 为了确保不同对象实例的地址是唯一的

结论：一个类的大小，实际就是该类中 “成员变量”之和，当然也要满足内存对齐规则。

#### 内存对齐规则

1.  第一个成员与结构体偏移量为==0==
2. 其他成员变量要对齐到某个数字（对齐数）的整数倍的地址处
   1. 对齐数 = 编译器默认的对齐数 与 该成员大小的==较小值==

3. 结构体总大小为：最大对齐数（所有变量类型最大者与默认对齐参数==取最小==）的整数倍
4. 如果嵌套了结构体的情况，嵌套的结构体对齐到自己的最大对齐数的整数倍处，结构体的整体大小就是所有最大对齐数（含嵌套结构体的对齐数）的整数倍。

### this指针特性

1. 只能在成员函数内部使用
2. <kbd>this</kbd>指针类型：==类类型*<kbd>const</kbd>==，不可以给<kbd>this</kbd>指针赋值
3. 本质是 ”成员函数” 的形参，当对象调用成员函数时，将对象地址作为实参传递给
   <kbd>this</kbd>形参。
4. 是 “成员函数” 隐含的指针形参。



### 类的6个默认成员函数

**注意：即使是空类，编译器会自动以下6个默认成员函数**

默认成员函数：用户没有显示实现，编译器生成的默认成员函数称为默认成员函数

<img src="C:\Users\liang\AppData\Roaming\Typora\typora-user-images\image-20240408230445806.png" alt="image-20240408230445806" style="zoom:67%;" />



